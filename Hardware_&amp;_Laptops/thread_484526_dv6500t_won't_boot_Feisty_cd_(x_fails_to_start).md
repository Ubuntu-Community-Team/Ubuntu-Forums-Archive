---
title: "dv6500t won't boot Feisty cd (x fails to start)"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by Scotty562 on 2007-06-25
The specs of my machine are Intel Core Two Duo 2.0 Ghz, 2 gig, 120 gig hdd, and a geforce 8400. X fails to start and won't even boot... :(. I'm really depressed, I was hoping I woudln't be forced to use Windows. Any advice?

---

### Post by Ayuthia on 2007-06-26
You probably need to add 'noapic nolapic' to the boot parameters to get it to start.  

For the CD, when the boot screen comes up, press F6 to edit.  Between the words quiet and splash, add the following:
noapic nolapic
I am not for sure if location of the wording is critical, but that is always where I have put it and it has been happy.

If you choose to install, you will also have to add those options to /boot/grub/menu.lst in the kernel line.  When you come to that step and you want assistance, just come back here and someone would be more than happy to assist.

---

### Post by Scotty562 on 2007-06-26
I just tried your suggestion but x still fails to start :(.

---

### Post by Ayuthia on 2007-06-27
Have you tried the safe graphics option?  I looked around last night and was pretty sure that Feisty has been installed on a dv6500t so there is hope.  I just haven't found out how they got started.

---

### Post by Scotty562 on 2007-06-27
I got it, thanks for the help. Feisty is now installed. My wireless doesn't work and I'd neeed to use ndiswrapper to get it to work. I tried a few of the guides on the forum and nothing seemed to work for me so I think I'll just wait till Intel releases a driver in the second quarter.

---

### Post by l-fever on 2007-07-04
> **Scotty562 said:**
> I got it, thanks for the help. Feisty is now installed. My wireless doesn't work and I'd neeed to use ndiswrapper to get it to work. I tried a few of the guides on the forum and nothing seemed to work for me so I think I'll just wait till Intel releases a driver in the second quarter.

I'm having the same problem. How did you get it to work?

HP Pavilion dv6500t CTO with:

- Intel(R) Core(TM) 2 Duo T7300 (2.0GHz/4MB L2Cache)
- 15.4" WXGA BrightView Widescreen (1280x800)
- 2GB DDR2 System Memory (2 Dimm)
- NVIDIA GeForce 8400M GS
- HP Imprint Finish (Radiance) + Microphone
- Intel(R) PRO/Wireless 3945ABG Network Connection
- 120GB 5400RPM SATA Hard Drive

And using the 7.04 64 bit alternate install cd, the install runs ok, it just boots up to a blank screen. Any ideas!

Thanks!

Steve

---

### Post by Scotty562 on 2007-07-04
We have the EXACT same system ;). I'm using the 32 bit regular feisty cd. When you boot highlight the first option and press F6. add all_generic_ide to the boot options list. That's all there is too it. Good luck! The sound is a pain but if you follow this link [http://ubuntuforums.org/showthread.php?t=489757](http://ubuntuforums.org/showthread.php?t=489757) that should help you out. It got my sound working.

---

### Post by l-fever on 2007-07-04
> **Scotty562 said:**
> We have the EXACT same system ;). I'm using the 32 bit regular feisty cd. When you boot highlight the first option and press F6. add all_generic_ide to the boot options list. That's all there is too it. Good luck! The sound is a pain but if you follow this link [http://ubuntuforums.org/showthread.php?t=489757](http://ubuntuforums.org/showthread.php?t=489757) that should help you out. It got my sound working.

Thanks, I tried the 32bit live fiesty cd with all_generic_ide added to the kernel boot options. This got me a little further along. Now, I get the error"(EE) NV(0): No display devices found and (EE) Screen(s) found, but none have a usable configuration.

Do you have the same graphics card? What version is your system bios? I'm at F .09 

I will keep digging and trying to get the xserver to work.

---

### Post by l-fever on 2007-07-05
I went back to version f.08 on the system bios, now it just boots to a black screen and hangs. Fun! I like a challenge!:o

---

### Post by Scotty562 on 2007-07-05
Sorry, I didn't get back to you sooner. I have whatever the newest version of the bios is. I also have the Geforce 8400M GS. I don't know what else to tell you though. That monitor issue looks nasty. I coudln't get my wireless working so I will be putting Ubuntu on the backburner until the driver is integrated into a kernel release :(.

---

### Post by lavinia on 2007-07-05
I HAVE SAME PROBLEM

waiting ubuntu 7.10 :(

---

### Post by l-fever on 2007-07-05
> **Scotty562 said:**
> Sorry, I didn't get back to you sooner. I have whatever the newest version of the bios is. I also have the Geforce 8400M GS. I don't know what else to tell you though. That monitor issue looks nasty. I coudln't get my wireless working so I will be putting Ubuntu on the backburner until the driver is integrated into a kernel release :(.


Yeah, It could be bios related or ?????. I had another hp laptop before this one that I returned. I had to use the ndiswrapper to get wireless to work on 7.04. I may have to wait until 7.10. I will keep trying. Thanks for the response!

Steve

---

### Post by stchman on 2007-07-05
> **Scotty562 said:**
> The specs of my machine are Intel Core Two Duo 2.0 Ghz, 2 gig, 120 gig hdd, and a geforce 8400. X fails to start and won't even boot... :(. I'm really depressed, I was hoping I woudln't be forced to use Windows. Any advice?

Did you try the "Safe graphics Mode" on the LiveCD menu?

---

### Post by l-fever on 2007-07-06
> **Scotty562 said:**
> We have the EXACT same system ;). I'm using the 32 bit regular feisty cd. When you boot highlight the first option and press F6. add all_generic_ide to the boot options list. That's all there is too it. Good luck! The sound is a pain but if you follow this link [http://ubuntuforums.org/showthread.php?t=489757](http://ubuntuforums.org/showthread.php?t=489757) that should help you out. It got my sound working.

Thanks for the help! I used the 32 bit(1386) Live cd and used the f6 and added all_generic_ide to the kernel boot options. After booting, I got the x-server screens not found message. So, when asked to diagnose the xserver problem, I selected no. Logged in, and ran sudo nano /etc/X11/xorg.conf and changed the driver from "nv" to "vesa" saved. You should backup the xorg.conf first. I then ran sudo killall gdm. Then sudo gdm and bam I was into the graphical environment with the generic vesa driver. I then configured my wireless card when prompted. and ran the install from the live cd. I then let ubuntu update and I ran the envy script to install the latest Nvidia display driver! Now all I need to do is to get the sound working! Thanks to Scotty562 for the help!

Steve

---

### Post by Lester Cottrell on 2007-07-06
I have been running fiesty as a dual boot with w2000 since it first came available.  I am using a dell dimension 2350 with 524 megs of ram and 120 meg hard drive split 60-60.  Yesterday after using w2000 it wont boot ubuntu.  I choose ubuntu, it says "starting up   loading, please wait"  then nothing but a black screen.

---

### Post by mooseboy on 2007-07-14
I ordered a dv6500t with all the trimmings (webcam, microphones, remote, fingerprint reader, etc) today. I'll post a thread with a HOWTO on any and all components I get working. Should take a good two weeks before I have it in my hands though. Good hacking!

---

### Post by l-fever on 2007-07-14
> **mooseboy said:**
> I ordered a dv6500t with all the trimmings (webcam, microphones, remote, fingerprint reader, etc) today. I'll post a thread with a HOWTO on any and all components I get working. Should take a good two weeks before I have it in my hands though. Good hacking! 

Cool! Good Luck! There are a few that have a little headstart! You will love your laptop! I like mine a lot! Welcome to the forums!

Steve

---

### Post by mooseboy on 2007-07-25
Yesterday came and went... and I got a wonderful new laptop. Problem was, it was somebody else's, so back to the factory it goes. Now I wait another 2 weeks to hopefully get the one I ordered. Maybe the herds of Gutsy Gibbon will be more polished by then and I can use it as my primary OS. We'll see. In the meantime I read more about the webcam and fingerprint reader -- both things I really want to see working on this.

> **l-fever said:**
> Cool! Good Luck! There are a few that have a little headstart! You will love your laptop! I like mine a lot! Welcome to the forums!

Steve

---

### Post by l-fever on 2007-07-26
> **mooseboy said:**
> Yesterday came and went... and I got a wonderful new laptop. Problem was, it was somebody else's, so back to the factory it goes. Now I wait another 2 weeks to hopefully get the one I ordered. Maybe the herds of Gutsy Gibbon will be more polished by then and I can use it as my primary OS. We'll see. In the meantime I read more about the webcam and fingerprint reader -- both things I really want to see working on this.


Well that sucks! I hope your laptop arrives soon! I didn't order the webcam/fingerprint reader option.

---

### Post by Scotty562 on 2007-07-27
They sent you someone elses laptop O.o? What in the world is going on at HP? heh. You'll love the laptop by the way. I coudln't be happier with mine.

I got the graphics, sound, webcam, and wireless all working on gutsy. A growing number of  others have also had success so you will be surrounded by allot of advice.

About the fingerprint reader. I haven't found any way to get the thing working. The only program that I could even find was for lavino's (sp??) only. I agree though, I would really like to see something like vista's fingerprint reading abilities brought to ubuntu. That was one of the things I enjoyed most about Vista.

Good luck!

---

