---
title: "Problem installing modem driver"
date: 2010-08-29
forum: Hardware
---

### Post by dede468 on 2010-08-29
I have downloaded the official modem driver for an Aztech modem for Linux from the Aztech website but am having problems installing it.

I have decompressed it and read the README file which is where I come unstuck.

Instructions are to change the path to headers like so:

"Note: Probably you will need to correct in Makefile path to your
         local linux kernel header files:

         	KERNEL_INCLUDES=/path/to/linux/include"

I am using 10.04 and the path appears to be /usr/src......but then there are a couple of header directories and the /linux/include files become confusing and don't work.

I have tried making sense of this by following a route through the header directories but whichever path I try results in failure big time like this when I ask it to "make" so I can't get any further:

/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:62: error: &#8216;_NSIG_BPW&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h: In function &#8216;sigfindinword&#8217;:
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:67: warning: implicit declaration of function &#8216;ffz&#8217;
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h: In function &#8216;sigisemptyset&#8217;:
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:75: error: &#8216;_NSIG_WORDS&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:77: error: request for member &#8216;sig&#8217; in something not a structure or union
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:77: error: request for member &#8216;sig&#8217; in something not a structure or union
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:78: error: request for member &#8216;sig&#8217; in something not a structure or union
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:78: error: request for member &#8216;sig&#8217; in something not a structure or union
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:80: error: request for member &#8216;sig&#8217; in something not a structure or union
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:80: error: request for member &#8216;sig&#8217; in something not a structure or union
/usr/src/linux-headers-2.6.32-21/include/linux/signal.h:82: error: request for member &#8216;sig&#8217; in something not a structure or union

and so on. 

As this is the official driver it should work, has anyone any idea what the path should be please?

I can post any of the original files.

---

### Post by IcarusR on 2010-08-29
Post a link to the driver you downloaded & I'll have a look.
And post details of modem, model etc.

---

### Post by dede468 on 2010-08-29
Jambo, 

Thanks for the reply. Link to the download is here:

[http://www.lostmydrivers.com/driver/download/7204/Aztech/Modem-Drivers/aztech-modem-external-um-9800-driver-2.8.3-linux](http://www.lostmydrivers.com/driver/download/7204/Aztech/Modem-Drivers/aztech-modem-external-um-9800-driver-2.8.3-linux).

As you can see, the modem details are on the download address.

Asante Sana - Thanks again for the reply,

---

### Post by IcarusR on 2010-08-29
That is an old version of slmodem. 

Is your modem actually an external one as the download link states ?

sl-modem is available in the 10.04 repositories so no need to compile it.

I have an slmodem supported modem in my laptop & when I installed 10.04 it asked to install slmodem as a proprioritory driver. If your modem is supported I would expect the same to have happened.

Failing that the Linmodems page has info on how to get (assuming it will) modem to work.

[http://www.linmodems.org/]("http://www.linmodems.org/")

&

[http://132.68.73.235/linmodems/index.html#scanmodem]("http://132.68.73.235/linmodems/index.html#scanmodem")

---

### Post by dede468 on 2010-08-29
Yes I knew it was an old version but I had been hoping it may have worked if the kernel requirement wasn't too different. I hadn't found the one in the repo.. odd?

Yes it's external USB and yes it does work on windows clap-trap.

Linmodems.org - spent two days trying to get a modem driver from that site to work with this modem and comp but got nowhere near. Scanmodem found and reported on it which didn't help as something [I forget what now] was no longer available and their Installer download wouldn't run - terminal output was that it couldn't run a file which was called "installer.run" [the full name of the installer file]

I'll take a look at the 10/04 repo but no. it didn't detect the modem at all or I would certainly have gone down that route.

Thanks once again for the info and the help

PS

Just had a search in 10.04 repo and can't find a slmodem driver. What name is it under?

---

### Post by dede468 on 2010-08-29
Found the slmodem driver - source code was not enabled in software sources however, it has made no difference.  The modem is only detected by lsusb in terminal but GPPP says there is no modem installed on the comp.

---

### Post by IcarusR on 2010-08-29
External USB is a completely different thing. Fraid I have no idea how to get it working. I think slmodem is only for internal modems.
Traditional serial modems just needed serial port driver & commands could be sent to them directly from terminal.

Is there any thing in the log files now slmodem is installed ??

---

### Post by dede468 on 2010-08-29
according to the install data, sl-modem works for both internal AND usb modems.  Having installed it, there's a new problem. Without the modem plugged in, typing lsusb in terminal displays all the usb ports and usage.  Plug the modem in the usb port [any] and lsusb stops working - entering lsusb interminal freezes the cursor and my mouse. Seems to suggest that they are both trying to use the same irq or something like that so there must be a way to check that out I guess.

---

### Post by IcarusR on 2010-08-29
assigned irqs should be listed in the log files with the info on hardware.
dmesg in terminal to view.

Not got any other suggestions.

Have to go now.
Good luck.

---

