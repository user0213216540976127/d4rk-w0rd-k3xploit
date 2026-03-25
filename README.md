# DarksSword Kernel Exploit

Reimplemented in Objective-C. 

Supposed to support iOS 15.0 - 26.0.1.

Offsets hardcoded for 15.x(?)

# https://nicram-bio.vercel.app - my bio site

# https://github.com/opa334/darksword-kexploit - The original repository may be deleted

-------------------------------------------------------------------------------------------------

# Kernel Exploit — Execution Guide by https://github.com/citizenblack/darksword

⚠️ **Disclaimer**
This code is a kernel exploit targeting iOS. Running it may crash your device or cause instability. Use only on test devices.

---

# 📱 Requirements

* macOS with Xcode installed
* iPhone/iPad (ARM64 / ARM64e)
* iOS version potentially vulnerable
* Ability to run unsigned or sideloaded binaries:

  * Xcode run
  * Jailbreak + SSH
  * TrollStore (optional)

---

# 🧰 Dependencies

The code requires:

* `Foundation.framework`
* `IOSurface.framework`

---

# ⚙️ Build Instructions (Xcode)

1. Open Xcode

2. Create a new project:

   * **Command Line Tool**
   * Language: Objective-C

3. Replace `main.m` content with the exploit source code

4. Add framework:

   * Go to **Build Phases**
   * Link Binary With Libraries
   * Add `IOSurface.framework`

5. Build the project

---

# ⚙️ Build via Command Line

```bash
clang exploit.m -o exploit \
-framework Foundation \
-framework IOSurface
```

---

# 🚀 Execution Methods

## Method 1 — Run via Xcode

1. Connect iPhone to Mac
2. Select device in Xcode
3. Press **Run**
4. Check debug console output

---

## Method 2 — Jailbreak + SSH

Copy binary:

```bash
scp exploit root@iphone:/var/root/
```

SSH into device:

```bash
ssh root@iphone
```

Make executable:

```bash
chmod +x exploit
```

Run:

```bash
./exploit
```

---

## Method 3 — TrollStore (Optional)

1. Convert binary into iOS app bundle
2. Sign with TrollStore
3. Install on device
4. Launch app

---

# 📊 Expected Output

If successful, console should display something like:

```
[+] Running on non-A18 device
[+] highestSuccessIdx: ...
[+] successReadCount: ...
win??
```

`win??` indicates successful kernel primitive acquisition.

---

# ⚠️ Possible Failures

* Device not supported
* iOS version patched
* Wrong kernel offsets
* Sandbox restrictions
* Memory layout differences

---

# 💥 Risks

* Kernel panic
* Device reboot
* Freeze
* Potential bootloop (rare)

---

# 🧪 Notes

* Designed for research/testing
* May require entitlement bypass
* Behavior differs across SoC (A17/A18)
* Exploit relies on race conditions (non-deterministic)

---

# 🧹 Cleanup

After testing:

```bash
rm exploit
```

---

# 📌 Summary

1. Build binary
2. Transfer to device
3. Execute
4. Watch for "win??"
5. Reboot if unstable
