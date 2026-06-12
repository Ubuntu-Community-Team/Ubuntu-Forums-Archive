---
title: "No serial devices work"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Midas on 2005-06-30
I've just installed Ubuntu and find that nothing connected to my serial ports works, not even a mouse :(  I previously tried Mandrake and a serial mouse and my Wacom ArtPad both functioned fully, as they do in Windows.

The only thing I've found in this forum that might be applicable is to change a line in /etc/X11/xorg.conf from /dev/mouse/generic to /dev/ttyS0, but I don't have that line in my file, the only one refering to a mouse I can find is /dev/input/mice; changing this makes no difference.

Can anyone offer any further help with both getting my mouse to work and being able to use my Wacom tablet - please bear in mind that I'm a *total* beginner with Linux?  I've looked at the Linux Wacom Project pages to try to find out how to get that working, but it might as well be written in double-dutch!

---

### Post by ksmurf on 2005-07-05
Hey Ya.  I just spent 3 wks getting my wacom going so my loss is your gain.  I'm new to linux as well but I'll try and get you through it quick and dirty.  

1> Make sure to " apt-get install build-essential " and "apt-get install wacom-kernel-source" and "apt-get install wacom tools" and "apt-get install Xinput"

You will need others (tk Tcl and devs) as well depending on how the ./configure goes.

2> Download the wacom package from the linux wacom project website.  Extract it and go to your terminal.  cd D* then cd (location of the extracted package).  type sudo ./configure.  Use you arrow keys to find out the errors and correct them.  Keep running ./configure until the only error you have is the one about Xorg SDK( I have not Idea what this means)

3>next sudo make

4>next sudo make install

5>now backup your /etc/X11/xorg.conf file.  You will be editing this

6>sudo gedit /etc/X11/xorg.conf and add the lines on this page [HTML]http://meeg.elvenrealms.net/wacomlinux.html[/HTML] to it.  Do not pay attention to the stuff on the bottom of the page about copying the wacom driver over.

7> Restart X (Cnrl alt Backspace I think) .  If X does not start then just archive that xorg.conf and restore the one u backed up.  I know I'm crap at writing HOWTO's but hey I'm only an electrician ;>.  Hope this gets you started.

---

