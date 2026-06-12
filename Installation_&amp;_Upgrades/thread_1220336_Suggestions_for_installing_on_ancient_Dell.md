---
title: "Suggestions for installing on ancient Dell"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by stocktiki on 2009-07-22
**The situation:** Getting stuck trying to install 9.04 on a Dell Inspirion 8000 laptop with 700 MHz CPU and 128 MB of RAM. PC previously had Windows ME installed. Has an ATI M4 video controller with 8 MB of video RAM. Equipped with a 10 GB hard drive.
 
**The symptom:** Install CD starts up and presents the installation options. The nice Ubuntu logo displays very nicely on the screen -- just to tease me. I hear the startup sound. 
 
But then, I get a patchy brown screen that flicker a little bit and installation halts.
 
**What I've tried:** Validated the CD to see if that's the problem. Checked out OK. Also, booted the PC into Windows ME (retro, I know) to test the equipment. It started fine. 
 
**Questions: **
1. Is there an easy solution for this? I checked the forums, but found nothing. 
2. Will 9.04 run on a PC with 128 MB of RAM. Would upgrading RAM fix this problem? 
 
Anyone have any suggestions? Been curious to try Ubuntu for some time -- and finally got a machine to try it on... 
 
Thanks!

---

### Post by Mark Phelps on 2009-07-23
> **stocktiki said:**
> 2. Will 9.04 run on a PC with 128 MB of RAM. Would upgrading RAM fix this problem? 
The desktop CD won't even install with that little RAM. You need 512MB for that to work.

The alternate CD (text-based) might install, but I've only seen cases where that worked with 192MB of RAM or more.  Plus, even if it does install, you won't be able to use the default GNOME desktop (not enough RAM).  Don't know if Xubuntu or XFCE desktops will work, again, only seen them work with 192MB of RAM or more

The limited RAM isn't the only problem, the CPU is likely to be very slow as well.  Tried out Ubuntu versions on an HP laptop running an PIII 1000, 256MB of RAM, and while Xubuntu would install, it was so slow as to be useless.

You would do better checking distrowatch.com for minimal installations like Puppy or DSL.

---

### Post by spcwingo on 2009-07-23
+1 for Puppy.  It'll run nicely on those specs...much better than WinME.

---

### Post by stocktiki on 2009-07-23
Thanks for the suggestion on Puppy. I'll try it.
 
Been a little surprised at Ubuntu's system requirements. Just for an experiment, pulled out an old copy of Windows XP I wasn't using. Installed well and runs pretty fast.

---

### Post by Sef on 2009-07-23
Check out [xubuntu]("http://xubuntu.org") also.

---

### Post by raymondh on 2009-07-23
Or crunchbanglinux (which works well on a pentium3, 256MB, 500mhz system I have).

---

