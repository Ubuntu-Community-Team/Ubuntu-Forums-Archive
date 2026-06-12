---
title: "Ubuntu Warty on Omnibook XE3"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by smarttaz on 2005-03-25
After having tried Ubuntu 4.10 on a desktop PC, and after having run on my old HP Omnibook: Slackware 10.1 and SimpleMEPIS 2004.06, I decided to get rid of any KDE and switch to Ubuntu (and GNOME).

Here are my problems with Ubuntu 4.10 on Omnibook XE3 (Celeron/850, 256 MB RAM, 10 GB HDD).

A. The Synaptics Touchpad scrolling could be enabled like said in the SynapticsTouchpadHowto. 

A1.  However, there is a behavior NOT encountered in KDE nor WinXP (only in... Win98se!): 
  If I connect a PS/2 mouse, I can only use that mouse (unless I reboot); removing the mouse does NOT re-activate the touchpad; more than that, I will remain without any pointing device working, and reinserting the mouse does NOT fix anything!!  ](*,) 

A2. Also, booting with the "synaptics" driver loaded by X gives me, for at least 30 seconds (ore more? :-k) both the correct and functional mouse pointer AND the "big X" screen-centered pointer! Should  I unload smth from XF86config-4?  :shock: 

B. Dial-up external serial modem. My [TRENDnet](http://www.trendnet.com/en/products/TFM-560X.htm) external "very hardware" modem, which worked instantaneously (/dev/ttyS0) under Mepis and Slack, did not work under none of pppconfig, wvdial, gnome-ppp, even after linking 'ln -s /dev/ttyS0 /dev/modem', UNTIL...
...it happened to have the modem ON and Connected to the RS-232 during the kernel's boot time!
Is that normal?! Shouldn't be a smarter rc.d/* script somewhere? :-k 

C. Gnome Battery Applet: acpid is working, however Gnome Battery Applet believes that I'm always running on battery (no matter if I'm on AC or not), also telling me "0%"!
  In KDE (Mepis), I remember the corresponding kde applet always said "100% and charging", and "still have 3 hours to run", no matter what was the truth.
  Is there someone who managed to get his/her battery recognized on some Omnibook models, and how?

Radu-Cristian

---

### Post by Datenknecht on 2005-03-25
I face the exact same problems with my HP Omnibook 6000 and warty 4.10

Regards
Greg

p.s. the battery app seems to work fine from the live cd

---

### Post by smarttaz on 2005-03-25
[QUOTE=Datenknecht]p.s. the battery app seems to work fine from the live cd[/QUOTE]
Of course, the LiveCD behaves quite differently -- quite a different distro, I'd say :)

Actually, correction: if the external modem is ON and connected while booting, Warty hangs with a registry dump!
I have to reboot in recovery mode to load (?!) modem support, then 'init 3' and then it can run with it.

Very wunderlich... I really **want** to switch to Ubuntu (nice thing, Gnome! I'm überdrüssig by KDE), but the way it piss me off with a very straightforward modem...

'pon' or "Modem Lights" will indefinitly try to reconnect after each 'poff'... so I **must** use wvdial... 8-[

R.

---

### Post by mitchell7 on 2006-11-25
I can only help out with a couple of things here, sorry. I hope that the problems you've had haven't made you try another OS entirely, but I'll post here anyway...
I can tell you that the XE3 has always had problems with the trackpad/mouse. Waaay back when I was still using Windows, it had the annoying tendency to lock up (or more accurately, start ignoring) the mouse, trackpad, AND the keyboard if they were used too much. Like a buffer had overflowed or something. That stopped when I made the junp to Ubuntu. Suggestion #1: Next time you reboot, send the unit into "setup" mode at the HP logo. Basically, if you're not aware (and if you are, sorry for assuming), this lets you fiddle the BIOS settings. One of the options lets you change how the system deals with the trackpad and mouse. You can leave it at the default, which is to autodetect when there's a mouse plugged in, and disable the trackpad, or, you can set it as I did when I was using Windows; to enable both of them at the same time. I just turn it off using the button above the pad itself. I can turn it on and off at will, even after migrating to Ubuntu, and the scroll toggle works just as it should. In fact, I was a little surprised to read that you were having issues.
As far as the other items are concerned, I can't be of any help, I'm afraid. I don't use an external modem (cable for me), and I don't even have an internal modem, having yanked it out a long time ago. I also don't have any input about the Power Management because my battery went belly up about a year before I switched over (I just use the computer on my desk, and to index my music when I DJ at the club, so both environments require AC). Sorry! I hope I could help a little bit, anyway...

---

### Post by christal on 2007-08-29
Hy Guys!
If you don't know how to make the battery app. work, here is a little help.
I searched almost the whole google to solve this. I had the same prob. on my omnibook xe3 GC.
Hewlet-Packard didn't cared about the bios so the bios on these machines are dated to 1992.Shame on you HP.:mad: But the linux kernel only enables ACPI on bios-es after 2000.You just have to force the ACPI function to kernel.

You should edit the grub menu list file under /boot/grub/

Use this command : 'sudo gedit /boot/grub/menu.lst
After that enter your admin. pass.

And there are 2 lines telling 'UBUNTU [version number] quiet splash'
and the other 'UBUNTU [version number] (recovery mode) simple'

Be careful!
There are other similar lines but its just guide for writing and editing this file!

So the two lines should look like this:
'UBUNTU [version number] quiet splash acpi=force'
'UBUNTU [version number] (recovery mode) simple acpi=force'

The other way is to recompile the kernel turning ACPI on and changing the date of ACPI detection to 1992 or way back.:) It's a time travel.:lolflag:

---

