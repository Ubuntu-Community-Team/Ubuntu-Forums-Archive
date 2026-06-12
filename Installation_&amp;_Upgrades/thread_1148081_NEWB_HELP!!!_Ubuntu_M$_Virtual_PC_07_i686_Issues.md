---
title: "NEWB HELP!!! Ubuntu M$ Virtual PC 07 i686 Issues"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Stry8993 on 2009-05-04
Hi there all,

I'm on Vista x64 right now, yuck, I know. I'm very VERY new to the whole Linux jazz, but, I've been reading all I can, and am hoping to get into it. I am unable at this time, to install Linux as a whole OS, or to coincide on a partition with Windows Vista, so I am using it in a Virtual Environement to 1) Learn the basics, 2) Protect anything from my newb-like tendancy to explore/tamper/tinker and what not.

I set up Microsoft Virtual PC 2007 SP1, give the VPC 256MB's of RAM, 16GB's for its Virtual Disk, and the rest as default.

I use the ISO, mount it with Daemon Tools in H:, use that as the source disc, and all bodes well.

I then select English, and you know, install, good to go.

The error is get is something to the effect, here, I'll just do it again and write it out as it shows:  

> This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU.Maybe this is an issue with M$ VPC 07... but I mean, everything seems to bode well, and fine when I've googled the topic in varying degrees for everybody else.

I downloaded Ubuntu from the website, x64 Version

My Specs are as follows
> 
ASUS M3N78-Pro nForce 720a GeForce 8300
AMD Phenom X3 8750 Black Edition, 2.4GHz OC'd ~ 3.0GHz
2GB's Mushkin DDR2 800MHz 
BFG Tech nVidia GeForce GTX 260 Core 216 55nm 796MB 
Seagate 1TB 32MB Cache (not the funky crapped out ones, thank god)

I think thats all the crucial info.

Windows Vista Ultimate 64-Bit SP1 All Updates
Device Drivers and whatnot's are up-to-date.
I'm not sure if anyone in these circumstances has had the same issue, VPC, and this error, but I mean, I'd love to become a full fledged user, I'm just taking baby steps.

Any assitance would be GREATLY appreciated. Thanks in advance.

Marc
Linux/Ubuntu Newb... for now! DUN DUN DUHHHH!!!!

[IMG]http://i96.photobucket.com/albums/l169/mbe102/UbuntuMSVPC07SP1.jpg[/IMG]

---

### Post by lovinglinux on 2009-05-04
As far as I understand, the Virtual PC is emulating a 32-bit CPU and you are trying to install a 64-bit Ubuntu version.

You could use [Virtualbox](http://www.virtualbox.org/) instead of Virtual PC. I think is the most used virtual machine software here in the forums. It works great on Ubuntu Jaunty and can also be installed on Windows. I have also used Virtual PC before, but I like Virtualbox more.

You also might wanna take a look at the [Virtualization](http://ubuntuforums.org/forumdisplay.php?f=308) forum.

---

### Post by Stry8993 on 2009-05-04
Okay, thank you very much.:P

---

