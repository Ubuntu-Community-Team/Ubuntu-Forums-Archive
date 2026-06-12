---
title: "Problems running Xubuntu 10.4 on Toshiba 1800"
date: 2011-10-17
forum: Hardware
---

### Post by Strugglintoworkit on 2011-10-17
Hi,

I'm a complete newb to any form of Linux so please be patient.;)

I've got an old Toshiba satellite 1800 and I'm having problems running Xubuntu 10.4.
I've managed to install it as a dual boot with Win XP which is more than I managed with 11.10.

The problem is that I get a Welcome message in text, followed by a blank screen and nothing more.

I've scanned the forums and there is quite a bit of info on a common issue relating to display issues in relation to xorg.conf.

From copying what I've read, the xorg.conf should be in /etc/X11 or /etc/xorg?
I've tried numerous posted solutions and all I get is no such file or directory.:(

I've been choosing the 2nd option on the boot menu (recovery mode) which is the only way I can edit anything. I don't know if this is right but I don't know any better.

Please, please can someone talk me through this step by step?

---

### Post by roger_1960 on 2011-10-17
Hi

Look at psts no 12 and 20 in this thread:

[http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835)

The mousepad or gedit command in post #20 will create the xorg.conf file if it does not exist already.  If you can edit using gedit from recovery mode, then do so.  Once edited and saved, try reboot.

---

### Post by Strugglintoworkit on 2011-10-17
Hi Roger_1960,

Thanks for the advice.  I'd already looked at this thread but have since tried again.

When I enter the command line in post#20 to edit xorg.config I get  "**Gtk-WARNING **: cannot open display**" :confused:

Am I being a newbie idiot here and missing something?

All help and advice greatly appreciated.

---

### Post by Penguinnerd on 2011-10-17
This is because it is unable to open mousepad, a graphical program.

You might try using nano instead of mousepad. (Text based, so no need for any GUI to be working properly)

Edit: What screen are you seeing when you try to enter this command? Do you actually have a GUI at all?

Good luck!

---

### Post by Strugglintoworkit on 2011-10-18
Hi,

I have no GUI at all.

Yes, I can open NANO but it's looks like I don't have a xorg.conf file at all so I'm gonna have to read up to figure out how to copy from a floppy or usb to create xorg.conf.

Thanks to all for assistance so far.

---

### Post by Strugglintoworkit on 2011-10-18
Hi,

Xorg.conf successfully copied and Xubuntu now running!

Thank you all for your help! :KS

(Note to Administrators: How do I mark this SOLVED please?)

---

