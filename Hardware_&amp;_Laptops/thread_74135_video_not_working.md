---
title: "video not working"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by nsnook on 2005-10-11
I am very new to ubuntu & linux. I tried installing: Ubuntu 5.10 and 5.04 Live i386 editions on older computers (300mhz 256mb ram 13gb hdd) and let ubuntu partition and setup the drives

the computer boots with 2 errors:
t_kernel_font: Invalid Argument [Fail]
ror: Temporary failure in name resolution [fail]

I see the nice pretty ubuntu screen during the driver load and then the screen freezes and the monitor goes blank (as if it is set incorrectly)

I tried changing the video settings at boot to: 
video=vesa
video=vesa-tng
video=771

based on diff posts i have seen. I dont know how to change it to boot to basic video settings any more than I have.

it is extremely frustrating. 

the video card is some generic old video card 16mg ram and has always worked with Windows without installing anything special.

I assume the video is the problem because of the monitor "blinking" out.. it would do that when i set the video capability too high or the refresh rate too high on windows.

Any suggestions would be extremely welcome. Any guidance or explination as well. I have very little understanding and nobody I know to talk with, so I could use any help.

---

### Post by Zelut on 2005-10-11
When you boot to the installation CD press F1 instead of ENTER and look around in there.  I know there are some alternate installation commands that can help with some video/hardware issues.  Hope those give you some ideas or get you closer... keep posting if you continue to be stuck.

---

### Post by nsnook on 2005-10-11
i did try to look there, but it was pretty overwhelming. I will take a look again.

I installed the defaults onto another computer and it is stopping at the "starting periodic command scheduler"

if I hit C-Alt-Delete, it will kill all the processes & restart, but I cant get it to go past that point. it has the same issues as the other one, "T_kernal" and "ror: Temporary failure"


Are there any hardware help areas that that have helped anyone reading this? like they installed a certain driver & it worked, etc.

Thanks,
Nathan

---

### Post by nsnook on 2005-10-11
I tried the following entries before boot:

vga=771 noapic nolapic
video=771 noapic nolapic
video=vesa noapic nolapic


i could see a tiny brown flash screen right before the screen went blank and the monitor zoned out, but that was about the extent of the difference.

for what it is worth: the hard drive light keeps going after the screen blanks out, so i feel like somthing is going on, i just cant see it.

---

