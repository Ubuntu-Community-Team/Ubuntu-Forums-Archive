---
title: "HP Pavillion dv6000 livecd doesn't work?"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by glebrial on 2006-10-22
So I got this HP notebook with the belief it should run linux because it seemed to have all sorts of supported hardware (nvidia, amd, etc) but I can't figure out why the livecd won't work.

If there's any information you need me to fetch for you, I think  I can do that... I have next to no idea about linux but I do know C/C++ fairly well. I just realized that in order to be a true marxist you gotta be using linux :)

thanks in advance :)
-G

---

### Post by Arby on 2006-10-22
When you say the live CD won't work what do you actually mean? If you put the CD in the machine and then reboot what happens?

Does it ignore the liveCD and boot to your current system, does it try to to boot and fails?

To be able to help you we need some information to go on.:)

---

### Post by maia on 2006-10-22
Maybe your CD has CRC errors, or your BIOS isn't configured to boot first from CD (rather than HDD).

---

### Post by glebrial on 2006-10-22
Yeah, what I meant by "doesn't work" is that it will boot to a point and then just hang... there were no problems getting the CD to boot tho :)

---

### Post by joergenlie on 2006-10-23
when you see the boot options for the live cd, press f6(other options or something)). Then you schould see a command line with some commands. add "noapic nolapic" at the end and press enter. This worked for me.

Jørgen

---

### Post by juhizz on 2006-10-23
> when you see the boot options for the live cd, press f6(other options or something)). Then you schould see a command line with some commands. add "noapic nolapic" at the end and press enter. This worked for me.

adding **noapic** did the work for me (expect some problems with videocard). I dont know your specs well, but I have compaq presario v6000, with amd and nvidia (GeForce Go 6150) The driver isn´t supported yet (too new)

check this: [http://www.ubuntuforums.org/showthread.php?t=248168&highlight=compaq+laptop]("http://www.ubuntuforums.org/showthread.php?t=248168&highlight=compaq+laptop")

---

### Post by thaibox on 2007-06-09
Same Laptop, same problem.  The command entry worked immediately.  Wow I'm jealous that I don't know all this stuff.  I guess that is part of being a complete nub when it comes to Linux in general.  Oh well, at least there is plenty of help for free online.

I had no idea of what Linux was all about until recently.  The idea of people developing software and granting others full access to it really impresses me.  So does the Beryl 3d desktop...;)

---

### Post by Kingsley on 2007-06-09
I have the same the laptop and the LiveCD booted just fine for me. Try burning another copy.

---

### Post by Lifespent on 2007-08-24
I have the same laptop and I was having the same issue. I put "noapic nolapic" in the cmd line after hitting f6 and it worked perfect!

---

### Post by EXCiD3 on 2007-08-24
> **Kingsley said:**
> I have the same the laptop and the LiveCD booted just fine for me. Try burning another copy.

Just download the Alternate CD. It will work better and will give you the same results as installing from the regular cd. It does not load the xserver in order for installation so it should be just fine. Try it then give us your results.

---

### Post by HelgiFreyr on 2007-08-31
Awesome, had been trying to get this to work for a few hours when I saw this, worked instantly. I've got a HP Pavillion dv6000 laptop.

---

### Post by SirDennis30 on 2007-10-31
Thanks for the tip. I was having problems with this as well. It works fine now. I just have 1 question and do not know wear to look for the answer. I want to know if my wireless card ill work with this version. I have a Broadcom Corporation BCM94311 MCG Wlan mini-PCI. Will it work with this version? Or will it be a pain in the **** to make it work?

---

### Post by kupje on 2007-11-12
It is because of High Resolution Timer Support and Dynamic Tickless System - it is incompatible with a lot of nVIDIA-based laptops. And these things have been enabled by default in Ubuntu 7.10.

Try booting with the kernel parameters "highres=off nohz=off", it should work.
My HP Pavilion dv6111 will completely freeze after ~30 seconds if I don't disable it, and a friend of mine who has a Compaq with the same chipset (nVidia MCP51) has the exact same problem (and solution).

---

### Post by Seti on 2007-11-18
Can anyone confirm getting Gutsy working on one of these HP laptops? Including wireless as well as Nvidia driver??

---

### Post by jasorn on 2007-12-02
I can confirm this laptops works in fiesty.  Even the webcam(driver on net).  Wireless worked with ndis.  In fiesty the only two things I know I couldn't get to work were the suspend stuff.  I kinda gave up trying on suspend in linux in general.  And switching users isn't working for me for some reason.  I'm installing gutsy now and will report back.

---

### Post by Ayuthia on 2007-12-02
I have an HP dv6338se and I am able to get Gutsy running under Ubuntu and Kubuntu for 32-bit (Ubuntu) and 64-bit(Kubuntu).

---

### Post by anjanesh on 2008-04-30
Tried Live CD on a HP dv6000 series notebook having Vista & on my HP dc7100CMT PC having XP - same results on both:

booted from CD, on hitting the enter key for *Use Ubuntu without changing your computer*, nothing happened. I thought it was the enter key thats not being detected, but that wasnt it - enter key was working for *Boot from 1st hard-disk*.

Is there any other way to run LiveCD ?

Thanks

---

