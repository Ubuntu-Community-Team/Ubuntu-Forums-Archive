---
title: "Ubuntu 11.04 freezes every time while installing"
date: 2011-05-31
forum: Hardware
---

### Post by Maarten Baert on 2011-05-31
A few weeks ago I installed Ubuntu on this computer with Wubi, and even though it crashed a few times it seemed to work. The last time is booted Ubuntu was about two weeks ago. Today I tried to use Ubuntu again, but I got a black screen while booting. I tried using 'recovery mode', but then it just freezes while displaying the recovery menu (i.e. the menu with different boot options, like 'fail-safe graphics'). I tried some options like 'nomodeset', but that didn't work either (it seems like the LCD backlight is on with 'nomodeset' when it freezes, but it's still black).

Since there were no important files on the virtual disk anyway, I decided to simply uninstall Ubuntu and reinstall it completely. But Ubuntu now freezes during the installation process. I get the purple splash screen with the Ubuntu logo and the orange dots, but after a few seconds the animation stops and nothing happens. If I boot in 'safe graphics mode', it freezes at random times. The first time it froze right after 'stopping save udev log and update rules    [OK]'. The second time after 'Enabling additional executable binary formats binfmt support    [OK]'. The third time after 'samed disabled; edit /etc/default/saved'.

I've already tried uninstalling and reinstalling Ubuntu again, but I get exactly the same problem.

I noticed I always get this error message a few seconds before the computer freezes in safe graphics mode:
intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
I don't get any messages in normal mode.

The computer is a Dell Studio 1749.
Processor: Intel i5 M540
Video card: ATI Mobility Radeon HD 5650
RAM: 4GB
OS: Windows 7 64 bit

Does anyone know how to fix this?

---

### Post by dnns on 2011-06-04
Maarten,

This might be of help:

I wanted to upgrade my Dell Studio 1749 to 11.04 via a fresh install.

But, I could not for the life of me figure out why the Natty 11.04 Live CD would not boot on my Dell Studio 1749.

32 bit, 64 bit, alternate CD, nothing worked. I eventually upgraded to 11.04 from within 10.10 (64 bit). The upgrade installation completed without errors, but tragedy struck again, after a reboot I could not boot the 2.8.38 kernel!

Long story short: THIS IS THE SOLUTION: 
The Dell Studio had the A05 BIOS installed. I upgraded to the A08 BIOS and now everything works!

---

### Post by Maarten Baert on 2011-06-05
I just updated the BIOS, but Ubuntu still doesn't boot. I also tried resetting the BIOS to its default settings, but that didn't help either.

dnns, did you change anything else besides the BIOS update?

EDIT: Two months later I finally found out what was wrong. Apparently Ubuntu fails to boot if the wireless receiver is turned off. Anyway, turning it on in Windows and rebooting solved the problem. I haven't turned it off again to see if it will crash again, but I'm quite sure this was the cause.

---

### Post by petermecheng on 2011-09-02
Maarten Baert you're a genius! I've been trying to get Ubuntu to load successfully for ages but with no such luck. However when I read your comment about switching the wireless receiver on I tried that and it now works beautifully! :D :D :D

Thank you so much!

---

### Post by Changoman on 2011-10-07
Hi guys, i'm having the same problem now, but I can't apply Maarten's solution because I don't have dual boot.

I do have access to the console thought.

Can anybody help me with that?

Thanks!

---

### Post by Redblade20XX on 2011-10-07
> **Changoman said:**
> Hi guys, i'm having the same problem now, but I can't apply Maarten's solution because I don't have dual boot.

I do have access to the console thought.

Can anybody help me with that?

Thanks!

Check if your BIOs is updated and if it has any options dealing with the wifi switch.

-Red

---

