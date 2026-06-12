---
title: "Why does boot screen report keyboard error w/wired USB keyboard, but not w/wireless?"
date: 2022-05-20
forum: Hardware
---

### Post by geeky-1 on 2022-05-20
I setup and reconfigured a computer that I was given with a Microsoft wireless keyboard then pulled the dongle and plugged in my ergonomic Microsoft keyboard and get a keyboard error on the boot screen that shows memory before entering setup. I tried plugging it into every USB port without success; however, once the computer boots into Windows, the wired keyboard works fine. Why doesn't the wired keyboard work during the boot cycle? (This was frustrating as I couldn't get into setup with the wired keyboard to select my Ubuntu drive to boot to instead of Windows and finally solved the problem by switching back to the wireless keyboard, which is not my preference.)

---

### Post by tea for one on 2022-05-20
> **geeky-1 said:**
> once the computer boots into Windows, the wired keyboard works fine. Why doesn't the wired keyboard work during the boot cycle? 
Quite an unusual event.
Usually, wired devices yield fewer problems than wireless.

If the PC was pre-configured to only work with Windows and this Microsoft Wireless keyboard, then perhaps the donor can offer some advice.

I would have a look through all the UEFI settings (especially USB & Peripherals/Devices)

```
get a keyboard error on the boot screen that shows memory before entering setup
```
I'm not clear what you mean here by [COLOR="#0000FF"]shows memory[/COLOR]?

---

### Post by geeky-1 on 2022-06-18
I'm pretty sure the computer did not come with the MS wireless keyboard as it's an HP ENVY.

"boot screen that shows memory" is the screen displaying computer status including how much memory where it allows one to enter setup.

I gave up on trying to keep this computer as a dual boot since I couldn't get it to boot to Ubuntu by default and just pulled the Windows drive since I would only need to boot to Windows less than 1% of the time. (I actually put the Windows 10 drive in another computer, but Windows would not work there since it locks to the computer hardware [not just the drive!] so I gave up on Windows, reformatted with Ubuntu and am once again a Windowless house!) So I reset the time to wait to allow user to enter setup to the minimal amount and reattached the wired keyboard and it still shows the keyboard error before booting (to Ubuntu). I guess I'll have to keep the wireless keyboard around if I ever need to change the setup.

---

