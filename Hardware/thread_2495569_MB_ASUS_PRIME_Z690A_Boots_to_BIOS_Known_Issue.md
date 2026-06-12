---
title: "MB: ASUS PRIME Z690A: Boots to BIOS: Known Issue??"
date: 2024-02-23
forum: Hardware
---

### Post by Kurt_Alan on 2024-02-23
Hello All,

This mb is out of the case on an anti-static mat. The mb has a power button and lights to indicate stages in the boot process.

A new issue suddendly appeared: Upon power on, the OS fails to load, and my output is the BIOS. When I exit BIOS the OS successfully loads. When I am in a session and I reboot from CLI the OS successfully loads. It's only from a cold start that I go directly to the BIOS.

Does anyone know if this is a known issue with this mb??

Thanks.

---

### Post by oldfred on 2024-02-23
I had an MSI 690a system and had no issues.
Updates to most current UEFI from vendor were important. 
Check your UEFI version and vendors web site for latest firmware.
Also update SSD firmware. Even new hardware may have update available.
udisksctl status
inxi -d
Samsung has update ISO by model, Magician only works with Windows. 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

Did you install in UEFI boot mode?
Is motherboard set to default boot in UEFI mode? Some have legacy/BIOS/CSM and/or UEFI or both separately. And UEFI only may be better. But you have to test.
I am not sure setting on your Asus

These were settings on my old z97 Asus and I think yours may be similar, just with a few more features.
Asus z97 UEFI screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by Kurt_Alan on 2024-02-24
Happy to see you are still around @oldfred! Thanks much for your many leads. I will follow up.

---

### Post by Kurt_Alan on 2024-02-29
This is an update to my troubleshooting steps:

(1) I said that the Q-LED's on the mb indicated steps in the boot process. This is incorrect. I revisited the mb manual. These LED lights are hardware component checks, evidently taking the place of POST beep (error codes), where, in the case of the LED's: red = cpu; yellow = RAM; white = VGA; yellow-green = BOOT. When a light STOPS that indicates an error. My light stops on BOOT, so I have a boot error.
(2) IT IS INTERESTING THAT I BOOT SUCCESSFULLY FROM OS REBOOT BUT NOT FROM A COLD START. This fact should indicated a particular problem. Any ideas??
(3) I thought that the problem was due to my ssd and or mb/BIOS.
(4) I first checked the ssd. I ran ```
sudo smartctl -t long
``` and the result was PASSED. I then swapped in a second ssd to a second M.2 slot and tried a cold boot to that ssd. SAME BOOT PROBLEM. So I conclude that the problem is NOT with the SSD.
(5) I then downloaded an updated UEFI BIOS and flashed the BIOS successfully. The BOOT problem remains. In fact, it is worse than before but this may be an independent variable. Now from a cold boot and F10 the system does not load the OS. I need a second try from BIOS F10 to load the OS.
(6) If I can continue to load the OS I'm OK. I AM NOT IN A BOOT LOOP. I AM IN A 1/2 BOOT LOOP. 

I conclude that the mb is defective at one year and 10 months. On Amazon this board had 10% 1 star review but for other reasons. 

Any divergent ideas from my assessment?? Any clue to #2 above?? Much appreciated. For now, I'm not shutting down my pc and running 24/7, hoping for the best.

---

### Post by him610 on 2024-02-29
Consider sending Asus a message describing the issue with your motherboard, and the repairs you have attempted unsuccessfully. I am sure you will get a response from them.

---

### Post by oldfred on 2024-02-29
An UEFI update, reset many settings back to defaults.
If you changed any settings to allow your Ubuntu install, you may have to redo them.

Check boot mode and install. Both should be UEFI.
And use UEFI only, some systems have UEFI/BIOS UEFI preferred that may not always work right.

---

### Post by Kurt_Alan on 2024-03-01
> **oldfred said:**
> An UEFI update, reset many settings back to defaults.
If you changed any settings to allow your Ubuntu install, you may have to redo them.

Check boot mode and install. Both should be UEFI.
And use UEFI only, some systems have UEFI/BIOS UEFI preferred that may not always work right.

I did not change any settings when I installed Ubuntu, so UEFI update and reset should not be an issue. 

I'm confused about "boot mode and install; both should be UEFI." When I enter BIOS it is named "UEFI BIOS" or "BIOS UEFI" -- I don't remember which. I don't see any option in menu settings to change from BIOS UEFI to UEFI only but I will look again. 

If I can sort that, then I'll confirm that both boot mode and the installed version should read UEFI only.

However, one fact militates against your suggestion for a settings change. From the time of clean install of Ubuntu to the BOOT error, I have made no changes in settings. I always used "optimized." If a BOOT error suddenly occured, and I never changed settings, then this indicates a hardware problem with the board and not a problem with settings, no?

---

### Post by oldfred on 2024-03-01
Optimized may mean "Windows"?
Did you install with Secure Boot on?

What version of Ubuntu?

Some UEFI updates on newer systems may make changes, not just fix issues. Or you may have a new setting or two.

---

### Post by Kurt_Alan on 2024-03-02
> **oldfred said:**
> Optimized may mean "Windows"?
Did you install with Secure Boot on?

What version of Ubuntu?

Some UEFI updates on newer systems may make changes, not just fix issues. Or you may have a new setting or two.

Ubuntu 22.04.04 LTS Pro

I wiill read mb manual to see if there is a secure boot option. I went through all UEFI BIOS settings and don't remember this option. And if I did install with Secure Boot on versus off, what is the ramification?

Meanwhile, to be safe, I'm not shutting down  and running 24/7. I don't want to risk further deterioration. I remember when I was doing distrubuted computing I had a machine that ran for one year without shutting down.
Here in the D.R. I may have a power outage, however.

Meanwhile, I can read the BIOS part of the mb manual without having to eyeball the actual BIOS. I will see if a Secure Boot option exists. I will also check to see if there is any choice between BIOS or UEFI as you suggested.
Also, in my next inadvertent power off or reboot to BIOS, I'm going to run a full mem test. It may be unrelated, but why not try it? Further I'll try starting the computer from jumping the PWR pins on the Front Control Panel rather than using the power on button that's on the board and see if that makes a difference. I think that the more permutation I can throw at the problem, the better.

---

### Post by Kurt_Alan on 2024-03-03
OP Follow-up: I implied that I wouldn't be entering BIOS for maybe a year! Ha! Ha! I spoke too soon. I read the BIOS part of the mb manual and found a QR code to another more detailed manual. Sure enough, there are Secure Boot settings under BOOT. I had missed them because one must scroll down and because I only go to BOOT to change the sequence. Under Secure Boot State, I found OS Type where the choices are "Other OS" and "Windows UEFI Mode." The default was already set to "Other OS," so that's the correct setting, right? (Unfortunately, this doesn't give me an explanation for the problem if the setting is already correct). @oldfred had mentioned something to the effect of "BIOS" versus "UEFI." I think we're talking about the same thing, where "Other OS" means legacy BIOS and UEFI is the newish Microsoft security standard "Windows UEFI Mode." Is that correct?

Meanwhile, while in the BIOS, I ran MemTest85. The last time I did that 15 years ago, I aborted as I did not want to wait! This time I waited the nearly full one hour. My result is "PASSED" with zero erros so I can exclude RAM as possible cause of failure. The MemTest is pretty impressive. I didn't realize that it tests cpu L1-L3 cache besides RAM. The summary sheet is very detailed, giving even the minimum, maximum, and average CPU and RAM temps. during testing. Even though I initiated that program from the BIOS, when I exited, it did not return me to the BIOS but re-booted. In the re-boot, as usual, the BOOT error did not exist and my OS loaded. The BOOT STOP error only happens from a cold start. That's the Million Dollar Question. Meanwhile, because I'm risk averse, I'm running the machine 24/7 and hoping for the best.

---

### Post by oldfred on 2024-03-03
Windows is Secure boot, OtherOS is not Secure boot.
My older motherboard did explain when installing Windows 7 in UEFI (or BIOS mode) you have to use Other OS. Windows 7 could be installed in UEFI boot mode, but did not support Secure Boot. So that really is Secure boot on or off.
Whether you boot in UEFI or old BIOS is then a separate setting. When Secure Boot is on, there is no setting for BIOS/CSM/Legacy. When Secure Boot is off, you should have a default setting for UEFI or BIOS for installed system.
If system default boot mode does not match install, system may have issues booting. Older systems required you to manually change setting, most newer systems seem to let you boot an install in UEFI or BIOS when selected from UEFI one time boot menu. But may show some sort of error/warning.

But how you boot USB flash drive is often separate from default boot, which applies to installed system.
Some also require you to turn on USB boot or full USB support as booting from USB is not "Secure".  Not sure if USB boot off & Windows needs fixes when fast start up is on, how you are supposed to boot Windows repair or install flash drive.

---

