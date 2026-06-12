---
title: "USB peripherals are slow"
date: 2009-12-25
forum: Hardware
---

### Post by Tadpolio on 2009-12-25
I have a very odd problem. All of my USB peripherals work, they are simply slow. It is unbearably so seeing as how my keyboard won't keep up with me and my mouse jumps so I really would like to resolve this. The problem started when I went from an Nvidia graphics card to an ATI Radeon hd 4670. I do not believe it is xorg related or driver related because direct rendering works and an old ps/2 keyboard works perfectly. 

I am currently running a very clean install of Ubuntu 9.04  

I know that it is not power related because I have a dual-boot with windows 7 and everything works fine there. Why would ps/2 peripherals be ok and my USB ones be so slow?

---

### Post by Tadpolio on 2009-12-30
Ok, this is a bump for help, plus new information.

The problem might be power related. I tried running the mouse and keyboard off a powered usb hub and there was a noticeable improvement. Still not good enough though. I have done a lot of reading and I am wondering if this problem could be caused by linux not supporting my BIOS' ACPI. I cannot disable it in the BIOS so I don't know a way to test this or if it would even solve my problem without creating a million new ones. Still, any help in this direction (or any direction at this point) would be greatly appreciated.

---

### Post by bbob on 2009-12-30
Sorry to say I can't help, but I have the same problem on a fresh install of 9.10.  

USB mouse pointer movement is very slow and insensitive, and is seemingly unaffected by acceleration and sensitivity settings.  Scrolling and clicking seem to be normal however.  USB keyboard response can't keep up unless I type v-e-r-y  s-l-o-w-l-y  a-n-d  d-e-l-i-b-e-r-a-t-e-l-y.

PS/2 keyboard and mouse work fine in Ubuntu, and both USB and PS/2 keyboards and mice work fine in XP.  (My machine is dual-boot.)  So the problem seems to be just with USB input devices in Ubuntu.

I thought the problem might be my KVM switch, but plugging the USB devices directly into USB ports on the computer resulted in little to change.

I've searched the forums and found lots of mouse issues, but none exactly like this.

For whatever it's worth, "cat /dev/input/mouse2" produces lots of funny little symbols with PS/2 mouse movement, but "cat /dev/input/mouse3" produces a much smaller quantity of those same funny little symbols with  USB mouse movement.

Anybody out there with any suggestions?

---

### Post by OpenSourceOfAwesomeness on 2009-12-31
Ok, this is an old thread, but I thought I'd chime in in case anyone had figured anything out.

I actually don't have any issue with my USB keyboard or mouse but I do notice that my external storage devices are really slow. Copying files to my external harddrive, which is usb 2.0 is noticeably slower than on windows, and copying music to my droid - also 2.0 - is almost impossible. With the droid I'm getting less than 500 KB/s

Someone mentioned a BIOS setting. Would that make a difference?

AMD X2 5400+
4GB DDR2
Karmic Koala 9.10

---

### Post by Tadpolio on 2009-12-31
So I figured out how to turn acpi on and off. Unfortunately that crashes my system (should've known) and isn't a viable solution. I think the problem is that my BIOS' ACPI is sorta supported so it works but just delivers power less efficiently than my Win 7 install. I am wondering if a larger PSU would supply enough power to the USB as well as my vid card even with the bad support.

---

### Post by Tadpolio on 2010-01-01
I tried using a 650 watt power supply (100 more than my current) and that made no difference. At this point the only solution I see is to just use USB -> PS2 adapters for the mouse and keyboard. I do hope someone finds a solution to this but I have tried pretty much everything I can think of.

---

### Post by GuiGuy on 2010-01-02
For what it's worth; I have been dogged by slow USB and SATA performance across a range of hardware for nearly a year now. I think it started with 9.04. 

Anyway, I recently upgraded a Ubuntu 9.10 box around an ASUS M4A785TD-V-EVO mobo. Initially same old, same old. File transfer times were measured in days, not seconds or minutes. 

I then noticed that the BIOS gave a number of options on how USB memory and storage devices should be treated. One of the options is HDD, ie hard disk drive. The default was FDD (floppy disk drive). I changed the setting to HDD. 

**File transfers now positively blaze along. **

That leaves the crappy SATA performance, which is now slower than USB... <sigh>

---

### Post by mouratos1a on 2010-01-04
Dear all,
I had a similar problem with lan printer was very slow...
After discussion with a friend computer expert he gave me the idea...
The drivers are not 100% compatible with the hardware... I found some driver (not the default) and the problem now is fixed... not a power problem or some other...
Just Linux issue...No offense but since drivers are built from people outside the hardware companies it is expected to be less than 100% compatible with the devices...I also have this Slow USB problem...but since now no solution...

---

### Post by bbob on 2010-01-25
I'm not sure if anyone's still following this thread, but in case it helps here is how I solved my slow USB mouse and keyboard issue.

[LIST=1]
[*]In the GRUB menu, choose the kernel you want to use, and press 'e' to edit.
[*]Find the kernel line, and add the following switches to the kernel parameters:
[/LIST]
```
noapictimer irqpoll
``` 
So for example, your kernel line will look similar to this:
```
kernel	/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash noapictimer irqpoll
```
Press Crtl-x to boot, and see if your problems disappear.

If they do not, you might try some different kernel parameters, as suggested by P4man in the thread where I stole this from: [HTML]http://ubuntuforums.org/showthread.php?t=1236267&highlight=slow+%2B+USB+%2B+mouse[/HTML]  

If this solves your problem, you will need to make the changes permanent, by editing the /etc/default/grub file to change settings, then run update-grub to apply.

---

