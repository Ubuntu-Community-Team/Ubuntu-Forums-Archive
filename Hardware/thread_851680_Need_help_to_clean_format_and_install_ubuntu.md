---
title: "Need help to clean format and install ubuntu"
date: 2008-07-06
forum: Hardware
---

### Post by abinesh on 2008-07-06
The answer to my question prolly somewhere already but i cant seem to find the right thread. Pls help direct me if its somewhere.

I have been using vista on my notebook and i recently was converted to ubuntu and im loving it!!

I have a old noebook which runs xp home which i want to install ubuntu. The problem is im having trouble doing a clean format of that notebook to only have ubuntu installed. The stubborn xp home just wont go!!

When i put in the ubuntu cd and restarted my pc, it gave me 3 options(demo,install on xp or help). I want to do a total clean up before installing ubuntu..

Im a amateur at all this, any help would be appreciated!!

---

### Post by scragar on 2008-07-06
restart the computer with the disk in to be able to install over windows, just make sure to back up anything and everything you want to keep, since they will be erased over(unless they are already on a seperate disk or partition)

---

### Post by abinesh on 2008-07-06
Hi,

I have done that, unfortunately it does not give me a option to format the system .I have the data backed up so there are no problems with that bit. 

The funny thing is that, when ubuntu installs..after a few steps it ask me to remove the cd and re-start..When i do that, XP loads again!!

Thats is why i want to format it clean and install ubuntu..HELP :S

---

### Post by ladr0n on 2008-07-06
Hi, and welcome to the community!

If you use the demo option, it will boot a "live" ubuntu environment from the CD.  From this live environment, you can install ubuntu.  Simply start the installer (I believe it has an icon on the desktop and can also be found in System > Administration), and let it guide you through the process.  When you get to the section on formatting the hard drive, choose "Guided - Use entire disk" and the installer should automatically clean your hard drive out for you.  
Have fun, and feel free to post any additional questions you have.

--edit--

That's odd that it's still booting to Windows.  Are you sure your computer is actually booting from the CD when you restart?

---

### Post by Yuki_Nagato on 2008-07-06
My flavor of Linux installation starts with the DBAN.

_[http://dban.sourceforge.net/]("http://dban.sourceforge.net/")_

Not only will you find links to the software that will completely destroy all data on your computer, but will introduce you to the idea of "booting" to a disk.  It sounds like you are trying to install Linux inside of XP.  What you need to do is "boot" to the Linux install disk instead.

_[Booting]("http://dban.sourceforge.net/download/readme.txt")_

Search for "3.0" on that text file.  

After DBAN has run, you simply boot to the Ubuntu disk and install using the on-screen instructions.  If you are new, use default options and "guided" partitioning.  If given the option, say "yes" to installing GRUB.  Installing GRUB will allow your computer to boot to Ubuntu every time, instead of you having to do it manually.

But the whole point is, look closely at the screen that pops up immediately after you press the power button "on."  It should tell you the key to press to access the "boot options."

---

### Post by abinesh on 2008-07-06
Awesome, ill have a go at it and let you folks know how i go ;)

Cheers

---

