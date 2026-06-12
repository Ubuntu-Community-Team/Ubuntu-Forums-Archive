---
title: "Making Canon printer work with 32 bit ubuntu"
date: 2012-06-05
forum: Hardware
---

### Post by forbajato on 2012-06-05
Had some bad hardware luck lately and now trying to get my Canon LBP2900 printer working with an old eeePC with Ubuntu 12.04 (32 bit) installed.

I followed Sivella's excellent tutorial here:
[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

When I run the test with ```
captstatusui -P LBP2900
``` I get a connection error.  The printer is on and the cables are connected - is this a problem with my printer or in the OS?  When I check for /dev/usb/lp0 I notice it doesn't exist either when the printer is plugged in or when it is not.  Doing ```
lsusb
``` results in a list of USB devices that includes the printer.

Any ideas are appreciated.

thomas

---

### Post by Sivella on 2012-06-06
Hello,

Due to a new cups update, it seems that usblp module is now blacklisted (as it was with 11.10).
So the printer is not mounted in /dev/usb/lp0.

The solution is to cancel this blacklist.

Edit this file : /etc/modprobe.d/blacklist-cups-usblp.conf

Comment (#) the line : blacklist usblp
Here is my file :
> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp                      Good luck.

---

### Post by forbajato on 2012-06-06
Works like a charm!  Thanks again, Sivella.

thomas

---

### Post by pdc on 2012-07-02
I followed your tutorial Sivella to install my LBP3100; it worked well and printed; however; on re-booting, it will no longer work 

in a terminal

> captstatusui -P LBP3100 gives the message on the screenshot

I should have mentioned I am using Mint13: based on Ubuntu 12.04 and it does not have the file /etc/modprobe.d/blacklist-cups-usblp.conf

so I did not need to blacklist the line "blacklist usblp"

In my first reboot, the file to be printed showed as "processing"

now, on my second reboot, the "to be printed" icon rapidly disappears, as though the page is to be printed, but nothing happens.........

---

### Post by forbajato on 2012-07-02
Is ccpd running?  You can make sure by typing ```
sudo service ccpd start
``` in the terminal.

---

### Post by pdc on 2012-07-03
yes; I believe it is running; I also used the command you suggested;

at each time, the icon for document gone to printer shows and then disappears; as though successful; but no printing

---

### Post by forbajato on 2012-07-04
This is really acting like you have the printer blacklisted.  I don't use Mint so I don't know what could be doing this.  Have you tried doing a find (or locate) command looking for any files with blacklist in the name?

---

### Post by pdc on 2012-07-04
thanks for the suggestion; screenshot enclosed; I used gedit to look through the files: no mention of a printer there

---

### Post by mojo risin on 2012-07-04
I don't have a problem with the printer showing up-- but atm I have a problem with the printer starting pages and then it stops and seems to be stuck after only about 1/6 of the page is printed.

---

### Post by forbajato on 2012-07-04
pdc - I don't see a likely culprit there either, since Mint apparently handles this issue in a very different way than Ubuntu, maybe you would have more luck finding someone in a Mint forum that can help?

mojo risin - is it a Canon printer?  That sounds like a very different problem than was discussed in this thread, may need a thread of its own to attract people who know what they are talking about!

thomas

---

### Post by mojo risin on 2012-07-04
Posted a thread  in case you are interested at looking at it :lol:

---

