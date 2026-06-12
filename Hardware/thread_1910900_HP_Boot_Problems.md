---
title: "HP Boot Problems"
date: 2012-01-18
forum: Hardware
---

### Post by jabeamer on 2012-01-18
I installed Ubuntu 11.10 as a dual boot with win7 on a friends HP computer.  Everything worked fine until I installed compizconfig settings manager and was going over the settings of it the top everything left the screen except the settings window.  When I closed that then I was left with nothing.  So I had to hold the power button down to shut it off.  Now when I start the computer back up the monitor stays black until Ubuntu comes up.  I don't see the HP logo or the grub.  I have tried to get into the bios but I can't even get into that.

I hate to tell him that he is going to have to reinstall everything because Ubuntu.  Give me something here.  What info do you need from me that you can help me.

---

### Post by MoreOrLess on 2012-01-18
You can't get into the BIOS?! That has nothing to do with the OS. You should be able to do that with the hard disk unplugged. It could be the video card gone bad or the video cable loose.

---

### Post by Mark Phelps on 2012-01-18
Please tell me you did NOT use the Ubuntu installer to install Ubuntu side-by-side by dragging a slider, right?  Because, if you did, you likely trashed Win7 and rendered it unbootable -- but that is a different problem ...

You're only seeing Ubuntu because it overwrote the MBR and now launches by default.

Boot back into Ubuntu, open a terminal and enter "sudo update-grub". That will regenerate the default GRUB menu and should add an entry for Win7.  What while it works and confirm that you see something along the lines of "Windows (Loader) on xxx".

Then, when you reboot, you should then get a GRUB menu.\

IF that works and you can then get into Ubuntu, reboot and see if you can get back into Win7.  IF you can't, you trashed the partition and will have to repair the Win7 boot loader -- which will remove boot capability for Ubuntu.

---

### Post by jabeamer on 2012-01-18
The funny thing is that after installing Ubuntu everything worked fine for a few days.  I could get into both win7 and Ubuntu.

The steps that brought me here is:
Installed Compiz and opened up settings window, checked wobble and that worked great.  checked cube but it said that wall or something can do the same thing so I unchecked it.

I then installed ATI 3rd party driver and restarted the computer and it still worked fine.

Went back into Compiz and checked one more thing but for the life of me I don't remember what it was but after seeing that it didn't do anything I unchecked it and that is when the desktop lost all the icons and top bar.  The only thing I could do was hold down the power button to shut it off.  When it came back up the screen was black until the login for Ubuntu came up.

---

### Post by marcellux on 2012-01-18
Hi,

I had once a similar problem. And it happened right after I enabled the 3rd. party driver for ATI. By booting, everything turned black until Ubuntu came out! So , I decided to disable that driver. 

After that, I was able to normally dualboot between Windows and Linux.

---

### Post by jabeamer on 2012-01-18
Thank you, I will try that when I get home from work.

---

### Post by jabeamer on 2012-01-19
I uninstalled the driver and it helped some but it did not fix the problem.  I now can see the Ubuntu logo when it starts up and when it shuts down that I didn't see before.

I tried reinstalling Ubuntu but that didn't even help.  Without going for a big search, where is the grub file located at because I didn't see it.  Ubuntu shows drive "System" and "OS" drives other than the Ubuntu drive.

I still need help.

---

### Post by jabeamer on 2012-01-19
I checked the grub.cfg file and it has the win7 loader in it.  I have even reinstalled and it still does not work.  I guess the computer has messed up some how.  I still can't get into the bios.

---

### Post by jabeamer on 2012-01-24
OK I have got a little closer to solving this problem.  This is not my computer so I did know much about the hardware but I did find out that it does have 2 monitor outs on the onboard video (HDMI and VGA).

For some reason the HDMI has dropped out on boot-up so the VGA picks up.  I don't know how to switch it from VGA to HDMI so if anyone has a suggestion please let me know.

I did go into the bios and the only thing that is in it is to choose onboard or PCI-E.

---

### Post by jabeamer on 2012-01-26
This is solved.
For anyone whose monitor goes to sleep when the computer boots but when the OS comes up it works fine please check your cable if you have HDMI. If the cable is out enough the computer will not see it at start up but will come when the OS comes up.

---

