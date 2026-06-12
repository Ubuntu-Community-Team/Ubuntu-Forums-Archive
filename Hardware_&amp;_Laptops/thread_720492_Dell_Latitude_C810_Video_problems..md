---
title: "Dell Latitude C810 Video problems."
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by lawentzel on 2008-03-10
I just got a laptop from work.  Pentium 3 Dell Latitude C810.  It was having the mouse lagging issues which also causes the sound to skip and such.  I was able to resolve that thanks to this post:

[http://ubuntuforums.org/showthread.php?t=491301]("http://ubuntuforums.org/showthread.php?t=491301")

All that is left is to get the video working.  The graphics card in there is a GeForce2 GO.  When I enable the nVidia drivers in the "Restricted drivers" option, I wasn't able to enable my desktop effects.  So, to me, it didn't appear to have recognized the drivers properly.

Found another post that showed manually installing the nVidia drivers, so I tried that.  (After uninstalling the first set.)  This hosed things up real good.  Got a message that it didn't know what video card I had and would only show 800 x 600 maximum resolution.  In there I selected my video card and clicked on the "Test" button and had a black screen with absolutely nothing happening.

So right now, I am in the process of reloading the laptop yet again.  I will be doing the above fix.  Afterwards, I will want to enable the video card and take advantage of desktop effects.  The specs on my laptop can be found at:

[http://support.dell.com/support/edocs/systems/latc810/en/ug/specs.htm]("http://support.dell.com/support/edocs/systems/latc810/en/ug/specs.htm")

Your help in this matter would be greatly appreciated.  Thanks!

---

### Post by lawentzel on 2008-03-10
Restore is done.  Skip fix is done.  I've installed the restricted nVidia drivers, then looked in xorg.conf.  They showed up in there, and everything appears fine.  I have then attempted to enable desktop effects, only to have it fail.

Still looking for help, thanks.

---

### Post by sixteensix on 2008-03-13
Lawentzel,

I am having exactly the same problem, I have even installed the drivers from the Nvidia but to no avail.

The only thing that works for me is the OS 2D drivers. I did manage to get the driver to work in 7.04, but this changed when I migrated to 7.10.

I am still searching, maybe 8.04 will cure the problem.

Sixteensix

---

### Post by lawentzel on 2008-03-13
Thank you.  Looking around it seems to be a memory ammount issue.  That laptop starts with 32M or up to 64M of RAM.  I am able to see some of the cooler 3D screen savers without any problem.  My other laptop which has NO 3D graphics capability at all, runs as slow as a three legged turtle.  So, I think it is sort of working, just no desktop effects.

---

### Post by sixteensix on 2008-03-14
lawentzel,

Have you tried using Envy? Its a script that installs the correct driver for Nvidia and ATI cards.

You can find it here [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

I have but it still did not work, though I only used the automatic detection of the driver and not a manual installation.

Let me know how you get on!

Cheers

Sixteensix

---

### Post by sixteensix on 2008-03-14
I have got the 3D driver working with using Envy!!!

Lawentzel, you will need to install Envy, once that is completed start Envy and install the Nvidia Driver manually, selecting version 71.86.04. Let Envy complete the  installation process, then select to automatically update your xorg.conf and restart the computer. Ubuntu will boot with the Nvidia driver. 

The only trouble I am having now is the enabling of the visual effects. They will only enable if I download the driver from the Ubuntu repositories! This is annoying as in 'restricted drivers' the Nvidia driver is in use but not enabled ](*,)

Arggghh....

---

### Post by lawentzel on 2008-03-17
I am pretty sure I have the drivers successfully installed.  I've tested 3D screen savers and they are fast which leaves me to believe they are installed and running.  Just can't get the desktop effects running.  Thank you for your help.

---

