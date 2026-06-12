---
title: "Ubuntu 8.10 Nvidia Driver Issue"
date: 2009-04-04
forum: Hardware
---

### Post by Ianisyourmaster on 2009-04-04
I just upgraded from Ubuntu 8.04, everything was working fine in 8.04, all the drivers were working. I upgraded to 8.10 Intrepid Ibex today and I've been having nothing but trouble with my Nvidia Driver. I have read just about every post anywhere about Nvidia Drivers not working. I've tried all the Nvidia Drivers in the list of Hardware Drivers, 173, 177, 180. I've downloaded the driver off of the Nvidia website and installed it, nothing is working, I can run the screen at the right resolution, but I cant get it to activate any of the Hardware Drivers for my Graphics Card. I have a Toshiba X205-SLI5, it has Dual 8600m GT's that run in SLI. Whenever it seems like the Driver is going to activate, I restart X and then it says that it cant find any screens, then I have to restart and set the Display back to Default Generic and then it runs at 1440x900 again but without the Nvidia Drivers on. Any help would be great, if I'm missing something please let me know, or if there are any links you could provide to helping me please post. I've read almost every single one but anything helps, thanks.

---

### Post by norwoods on 2009-04-04
nvidia has an extensive README file for each driver version.  google nvidia README version.number(nvidia README 180.44) it find the correct README file and look for information related to sli in the README file.

---

### Post by Ianisyourmaster on 2009-04-04
> **norwoods said:**
> nvidia has an extensive README file for each driver version.  google nvidia README version.number(nvidia README 180.44) it find the correct README file and look for information related to sli in the README file.

I've found the README and I've read through it, the problem that I get is that it cant find a kernel for me and cant compile one for me. I'm pretty new to Linux so I get a little confused from time to time. I'm just stuck now trying to figure this Kernel thing out, after I exit X and run the Nvidia file, then it tries to find the Kernel, it cant, tries to download it, it cant, then it just quits out there.

---

### Post by Ianisyourmaster on 2009-04-04
I swear, I don't think this is ever going to work, every single thing I try, everything I read, every forum I check, I try to follow the instructions to every single one, and either I get that Kernel error when I try to install the driver off the nvidia website, or, I use the Hardware Driver 180.44 and then restart and then it fails to load the nvidia kernel module, I'm not sure why this is so difficult, I'm guessing its because I have dual 8600m gt's in sli, cause I know a ton of laptops have 8600m's and I dont think those people are having problems. I guess what I should be asking is how to compile a Kernel for my Nvidia driver that will work with my 8600's so I can play games and use compiz and all that great stuff again. Once again, I do search alot on google and the forums, so if you find something, please send a link instead of having me search if you can cause I dont have alot of extra time right now and I would really appreciate it, also thanks to everyone who does help, sorry I'm so new to this stuff

---

### Post by Ianisyourmaster on 2009-04-05
Ok guys, I figured it out, I read an article written by some guy that was made in 2006 on how to build a kernel for nvidia, i just changed some things to make it for the 180 driver, then got it working, so this is solved

---

