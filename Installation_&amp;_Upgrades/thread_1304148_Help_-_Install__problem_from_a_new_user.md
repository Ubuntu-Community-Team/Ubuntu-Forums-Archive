---
title: "Help - Install  problem from a new user"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by DJChung on 2009-10-29
Help,

I am new to Linux/Ubuntu and I have the following problem:

First, the hardware:

Asus CUV4X MB
Pentium III  800 MHz
512 MB memory
AGP Voodoo 3dfx video card connected to a Samsung 21.4 inch LCD monitor (1600x1200)
WD Caviar 80 GB blank drive (no Windows; no data; the HD did have partitions and Win XP installed, but I removed all logical drives, removed all partitions, etc. and "blanked out" the drive)
MS mouse and keyboard
nothing fancy

Then, Ubuntu:

Got Ubuntu 9.04 Desktop ISO, burned a CD, and had trouble installing on HD; 
so I got the alternate desktop install ISO, burned a CD, and successfully installed on the HD.

When I boot from HD, I get the Ubuntu slash screen, then the screen blanks out, flashes several times (sometimes with a small white circuit in the middle), and nothing else happens.

What can I do to bring up Ubuntu?  Thanks for your help.


Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

### Post by lrcaballero on 2009-10-29
If you are dual-booting, Try running Ubuntu from a Live Cd first, tested and make sure you feel comfortable with the OS, then install it from the Live Cd. try it! see if it works!!!

Good Luck

Luis

---

### Post by Aemaeth on 2009-10-29
you can always drop to a text based interface to begin troubleshooting the problem try ctrl+alt+f1

if you get a terminal then atleast the sytem has started...

---

### Post by bribera on 2009-10-29
This sounds like a video card driver issue. Try hitting Ctrl+Alt+F1 like Aemaeth suggested to see if the boot process is completing successfully.

If you can log in to the terminal, please post the contents of /var/log/Xorg.0.log

---

### Post by DJChung on 2009-10-30
Thank you all for your suggestions and comments.

I just downloaded and installed 9.10 and all the (previous) install problems (with 9.04) were gone.  9.10 installed cleanly without a hitch.

However, a new issue surfaced.  During the 9.04 install, the install process detected my Linksys Wireless card, prompted for the WEP password (during the install process), and, presumably, made the network connection with my home WiFi.  I say "presumably" because following the install, Ubuntu never really came up from the HD, and I could not test the network connection.

During the 9.10 install, no such prompts were provided and no such connection was made.  Now I have Ubuntu up and running, how do I connect to my home WiFi to connect to the Internet?

Sorry for beginner questions, but I do not know where-else to ask.

Thanks again.

---

### Post by blazemore on 2009-10-30
There's a wireless icon in the notification area, click it and a list of wireless networks will appear.

Click the name of the one you wish to join.

---

### Post by DJChung on 2009-10-30
Thank you blaze for the info., especially with a screen capture.

When I click on the wireless icon, it displays the drop down menu as you illustrate; however, in the drop down menu, there are no wireless networks that I can select from.

In a WinXP machine (located in the same room as the Ubuntu machine and having the same PCI wireless card as the Ubuntu machine), shows at least three networks - my home wireless network and a couple from neighbors' networks.

In the Unbuntu machine, do I need to install drivers?  Can I make it "scan" and look for networks?  What do I do?

Are there documentation or FAQ where I can search for answers to these stupid newbie questions without having to bother the forum members?

---

### Post by DJChung on 2009-10-30
Problem solved by a clean re-install.  Now, the wireless icon, when clicked, shows my WiFi.  Don't know what happened, but the re-install fixed it.

---

