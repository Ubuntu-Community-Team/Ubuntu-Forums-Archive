---
title: "Installing on Asus eee"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by pbewig on 2009-05-01
I want to install xubuntu 9.04 on an Asus eee 900.  I do not want to use the netbook remix, just standard xubuntu.  What packages must I add to the standard xubuntu install to use get the Asus power management, wifi, mousepad, and function-key features?

Many thanks,

Phil

---

### Post by aysiu on 2009-05-01
I don't know about Xubuntu, but in Ubuntu 9.04 on my Eee 701, I just installed it as is. Power management, wireless, touchpad, and function keys all worked out of the box (except for the wireless on/off key, but I never use that key and actually prefer it not to work).

No additional packages necessary.

---

### Post by blackened on 2009-05-01
The vast majority of the ACPI stuff has been incorporated into default kernel modules. The rest you can get by installing eee-control from here -> [http://greg.geekmind.org/eee-control/deb/]("http://greg.geekmind.org/eee-control/deb/")

---

### Post by pbewig on 2009-05-01
Thanks.  I'll try it this evening and report what happens.

How do I use the .deb file?  Do I copy the file to my home directory and then say

sudo apt-get install eee-control_0.9.2_all~jaunty.deb

Thanks again,

Phil

---

### Post by aysiu on 2009-05-01
> **pbewig said:**
> Thanks.  I'll try it this evening and report what happens.

How do I use the .deb file?  Do I copy the file to my home directory and then say

sudo apt-get install eee-control_0.9.2_all~jaunty.deb

Thanks again,

Phil
No, you just double-click it, and GDebi will install it for you.

---

### Post by pbewig on 2009-05-01
Most things seem to be working.  I got all the normal codecs.  But sound doesn't work.  I think everything is set up properly.  But no sound.

Any suggestions?

Many thanks,

Phil

---

### Post by pbewig on 2009-05-02
Okay.  I've got it now.  Thanks to all.

Phil

---

### Post by aysiu on 2009-05-02
> **pbewig said:**
> Okay.  I've got it now.  Thanks to all.

Phil
Do you want to explain what you did, in case another Xubuntu Eee user stumbles upon this thread?

---

### Post by steve_d on 2009-05-03
On my Asus Eee 1000H I did the following:

System -> Preferences -> Sound

The sound devices were set to auto, which I believe was trying to use pulseaudio and the tests play back as static/buzz. I switched the devices to
HDA Intel ALC269 Analog (OSS) and the sound test played the tone normally.

Hopefully this is similar to other eee's and it helps someone.

Steve

---

### Post by heardamir on 2009-06-09
[FONT=Trebuchet MS][SIZE=2]This is how I installed on an ASUS EEE PC that came with windows WITHOUT an external CD drive. 

You'll need: 
[/SIZE][/FONT]
[LIST]
[*][FONT=Trebuchet MS][SIZE=2]your ASUS EEE PC[/SIZE][/FONT]
[*][FONT=Trebuchet MS][SIZE=2]USB Key (>= 1gb free)[/SIZE][/FONT]
[*][FONT=Trebuchet MS][SIZE=2](x)Ubuntu ISO file
[/SIZE][/FONT]
[*][FONT=Trebuchet MS][SIZE=2]unetbootin for windows[/SIZE][/FONT]
[/LIST]
[FONT=Trebuchet MS][SIZE=2]
**Step 1. **
Download the ISO, do the hash check etc. 
**Step 2.**
Downoad "unetbootin-windows-344"
**Step 3.**
Boot XP,  plug in your USB, open unetbootin, select "DISK IMAGE", browse for the ISO, select USB drive and path, click OK. Upon completion restart your machine. 
**Step 4.**
Jump into BIOS, and select your USB as primary boot disk, save and exit.
**Step 5.**
Select "Default" option. Ubuntu will load (trial) from USB. Run the "Install" that is sitting on your desktop. Follow the prompts. 
**Step 6.** Reboot and jump back into bios.. Change your boot settings back.
DONE!

Note: booting back to XP may require you to change boot settings in BIOS, depending on the settings selected in the Install. 

Happy Ubuntu-ing BAM!
Andy[/SIZE][/FONT]

---

