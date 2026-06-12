---
title: "put 8800GT into PC, now Ubuntu Feisty wont go to X."
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by bill_dotson on 2007-11-27
I booted Ubuntu and it would not load X.  I had anticipated this, so I just did sudo dpkg-reconfigure xserver-xorg and tried both the nv and the nvidia driver and neither time did it work and successfully boot into X.  So then I went to nvidia's site and downloaded the latest non-beta driver for *nix systems.  I then went it and ran the installer and it installed the driver, then redid the xorg.conf.  Then I tried to boot, and I got a bunch of lines, the noticeable ones saying:
"could not open device file /dev/nvidia0 (Input/Output Error)"
...
:XIO: fatal IO error 104 on X server ":0.0"

At this point I had the nv driver in xorg.conf.  SO I dpkg-reconfigured again and set it to nvidia.  Rebooted and started it.  Ran all my bootup scripts (just backing up files) but then wouldn't load X. I can't remember or not if I got the same messages as earlier, but X would not load.

---

### Post by foolsh on 2007-11-27
post your /etc/X11/xorg.conf and /var/log/Xorg.0.log files so we can see more details please.

---

### Post by bill_dotson on 2007-11-27
the attached text files contain xorg.conf and the xlog (had to split xlog up, it is big)

---

### Post by foolsh on 2007-11-27
your x_log1.txt ,I am asumming is the Xorg.0.log and not Xorg.0.log.old, looks like it started normally. -scroll to the end no errors-
edit: opps should have read your post more carefully. split the file you say.

run lspci and see if BusID "PCI:1:0:0" is where your card is, mine always mistakes my ati for my intel chip and I have to set BusID manually.

---

### Post by foolsh on 2007-11-27
try this xorg.conf file it is configured to run in vesa mode but it will atleast let you no if the card actually works and has the right busid
don't forget to back up your old one first

---

### Post by bill_dotson on 2007-11-29
Here is the xorg.conf that actually allowed me to boot into X.  I copied the xorg you provided then did a sudo dpkg-reconfigure xserver-xorg and chose vesa.  Now Beryl does not work (for obvious reasons).  Also, I do not think it is an issue really, but whenever the screen flashes right before the splash screen comes up the top 1/4 of the screen is a green pixel-ly grid.  

Then, when I booted into X it flashed up almost the whole screen and then went to the Ubuntu login screen.
I had an 8800GTS that would artifact randomly (green randomness, etc.) while the BIOS screen was loading, and even though this 8800GT does not do that at the BIOS screen or in any of the Windows stuff it does the aforementioned things with Ubuntu, so I am probably just being overly cautious.  Kind of weird though, now when I start my computer up for the first second or two the fans (or maybe just one or two) spin noticeably faster (you can hear them) than right after when they slow down to normal.

---

### Post by jespdj on 2007-11-29
Which video driver are you using?

nVidia recently released version 169.04 in which support for the 8800GT was added:
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

(if you're running 64-bit look [here](http://www.nvidia.com/object/linux_display_amd64_169.04.html)).

---

### Post by bill_dotson on 2007-11-29
I was using this one: [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)   I did a search for the latest 8800GT Linux driver and got that...

---

### Post by bill_dotson on 2007-11-29
OK, I just installed the 169.04 driver.  Then I rebooted and X would not start.  So then I did a sudo dpkg-reconfigure xserver-xorg and did all the normal stuff and set the driver to nvidia.  Then rebooted and X still did not start.  I am going to attach the xorg.conf and part1 and part2 of the X.log (it is too big to fit into one file), but I have to switch back to XP to do it so just a moment.

---

### Post by bill_dotson on 2007-11-29
here are the files.

---

### Post by Radon on 2007-11-29
I've also ordered a 8800GT and should be here next week!   \\:D/  It's going to be a huge improvement over the 7600GT AGP I am using now in my HTPC.  Too bad it doesn't have OpenGL 2.1.

Anyways, checkout [Phoronix.com]("http://www.phoronix.com").  It is one of my favourite Linux websites!  "It's a technology website that offers product reviews, Linux distribution screenshots, interviews, and news while maintaining a pure Linux orientation. Phoronix was started in June 2004 by Michael Larabel, who currently serves as the owner and editor-in-chief."

[Here]("http://www.phoronix.com/forums/showthread.php?t=3777") is a thread in their forums about problems with the 8xxx series drivers.  But that's what you get for being an early adopter.

---

