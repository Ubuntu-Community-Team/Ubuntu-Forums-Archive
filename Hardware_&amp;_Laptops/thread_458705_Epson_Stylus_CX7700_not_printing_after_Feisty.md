---
title: "Epson Stylus CX7700 not printing after Feisty"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by organelas on 2007-05-29
Hello,

I have a usb Epson Stylus CX7700 which worked smoothly on Edgy, but after upgrading to Feisty it stopped printing (scanner is working fine)!

After sending a job it justs spits out blank pages infinitely, until I turn it off (canceling or pausing do not stop it).

I have already reinstalled the printer, the cups drivers and also installed drivers from [http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX7700]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX7700"). After the last one the printer simply stopped, no more blank pages are coming out when printing. Then I reinstalled everything again, and it started with blank pages again...

Any ideas?! it was so easy in old edgy...

cheers!

ps: I running on a toshiba satellite a100 laptop

---

### Post by danf_1979 on 2007-08-03
Hi! 

did you find (or anyone) a fix for this? I'm experiecing the same problem :(

---

### Post by organelas on 2007-08-03
nope, not yet... and I still did not have time to report a bug, hope it will be fixed on the next ubuntu release!

---

### Post by organelas on 2007-08-04
Just today there was an update that might solve the problem.

  * Add debian/patches/02_dbus-launch_close_pipe.patch:
    - _dbus_get_autolaunch_address(): When calling dbus-launch fails,
       close the reading end of the pipe.
    - This caused a serious fd leak in programs like cups when they repeatedly
      try to send dbus messages, dbus is not running, and dbus-launch is not
      available or otherwise fails to execute.

[the bug]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/112803")

I will only be able to check out on the next week... I'll post any changes here

---

### Post by organelas on 2007-12-26
I finally managed to solve the problem!

I followed this guide:

[http://forums.linux-foundation.org/read.php?26,594,3776](http://forums.linux-foundation.org/read.php?26,594,3776)

I simply adapted to Epson Stylus CX7700 and the printer worked immediatly! Finally...!

So here it goes:

1. Go to [www.avasys.jp]("http://www.avasys.jp") and select your printer's model.

2. Get the printer driver pipslite (the one I got was pips-scx7700-cups-2.6.3-1.i386.rpm)

3. Use [alien]("http://kitenet.net/~joey/code/alien/") to convert the RPM to a .deb and install it.
```

$ alien -c pips-scx7700-cups-2.6.3-1.i386.rpm
$ sudo dpkg -i pips-scx7700-cups-2.6.3-1.i386.deb
```

4. Now it is time for some configuration

open /etc/ekpdrc with a text editor and replace "/dev/usb/lp0" with "/dev/usblp0" which is
where the device is actually created. (If you have the printer plugged in by USB, then just $ ls /dev/usb* to see what it comes up as.)

5. Now you need to run some scripts in /usr/local/EPKowa/SCX7700/scripts
```

$ cd /usr/local/EPKowa/SCX7700/scripts/
$ sudo ./setup-cups.sh
```

follow the setup process until the end then run

```
$ sudo ./inst-cups-post.sh install
```

6. Make the PPD file:

```
$ cd /usr/local/EPKowa/SCX7700/
$ sudo ./inst-rc_d.sh install
```

7. After that, you add the new printer via an admin tool (eg. [http://localhost:631](http://localhost:631)), and you'll need to manually add the PPD file that the install program should have placed in /usr/share/cups/model/

And that's it, worked for me... :0)

---

### Post by danf_1979 on 2008-04-10
Great!!!! THANKS!!! :-)

It worked here too...

At last :)

---

### Post by organelas on 2008-04-10
In other machines I tried, steps 1, 2 and 3 (see above) are sufficient to get the printer working...!!!

If you are getting "device not found" when trying to use XSane, download and install the scanner driver from Avasys. It will work too..!

However, apparently, I'm not being able to print paper sizes other than A4... Has anyone reported this before?

---

