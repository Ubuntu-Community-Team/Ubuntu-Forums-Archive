---
title: "Crash when logging off!"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by KmooreUSN on 2007-04-23
I am running Ubuntu Feisty 7.04 on a Dell Inspiron 9300 with ATI Radeon Mobility x300, after installing an updated driver from the ATI official website, when I log off Ubuntu seems to crash.  It flashes a bunch of text too quick to see, then shows the "loading screen" for ubuntu, but its just a black bar, it will sit like that for maybe a minute, then go to a black screen with just the cusor _ blinking.  I can type in text freely, but no command works.  Please help.

---

### Post by sudo_nym on 2007-04-24
Hmm, right after an upgrade...  Do you still have the older version?  If it worked before, maybe you should stick with that one.  You might also want to go look at [this thread](http://ubuntuforums.org/showthread.php?p=2522928), which describes the same problem exactly.

But please note that I don't really know what I'm talking about.  Just a guess, based on what you've both said.


Hope it works though,

Patrick.

---

### Post by KmooreUSN on 2007-04-24
That post definately sounds close, I've been researching this all day yesterday and today, seems to be 1 common factor, the ATI driver,  go figure!.  Hillarious part about it is that ATI knows about this bug for at least the last 5releases of there driver, and have yet to do anything about it, some say they've seen it as far back as 13 releases. On there forum, ATI said they solved it with a workaround, but if you read through it, the workaround didnt work fo them, nor for me, but they still say the bug has been solved. 

I found a forum that someone said they installed a SUSE ati driver, and it solved their problem, but didnt state where he got the driver from, or how to install it, if anyone knows can you please let me know.

V/R,

PO2 Kevin Moore, USN

---

### Post by KmooreUSN on 2007-04-25
Well after server attempts of different ways to install the ATI official driver on Feisty, i finally found a post that actuall worked for me, it was MindRiot's reply to this post on page 2:

[http://ubuntuforums.org/showthread.php?t=414768&page=2&highlight=fglrx](http://ubuntuforums.org/showthread.php?t=414768&page=2&highlight=fglrx)

Here is his post:

> **MindRiot said:**
> I want to add a few more comments about installing the ATI 8.36.5 binary driver in either edgy or feisty.

You can follow the instructions for 6.10 in the ATI Binary Driver Howto.

See: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2")

Under the section Modifying xorg.conf

Ignore both sudo aticonfig --initial and aticonfig --overlay-type=Xv

Run the following commands, then reboot

```
sudo /sbin/lrm-manager
sudo depmod -a
```

Once you're logged back in, open the terminal and enter

```
sudo gedit /etc/X11/xorg.conf
```

Under Section "Device" change

```
Driver      "vesa"

```

to

```
Driver      "fglrx"
```

Save the file, then reboot the computer.

When you log back in run in the terminal

```
sudo aticonfig --overlay-type=Xv
```

Ignore running aticonfig --initial.

Your Section "Device" in /etc/X11/xorg.conf should look like this:

```
Section "Device"
	Identifier  "ATI Technologies, Inc. ATI default card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```

Only difference was my xorg.conf had "ati" rather than "vesa", so I changed "ati" to "fglrx"
Thanks again MindRiot

---

### Post by sudo_nym on 2007-04-27
> **KmooreUSN said:**
> That post definately sounds close, I've been researching this all day yesterday and today,

[...]

You sure have been, and I'm glad it paid off.  :-)  Also hope inportb [from the linked thread] caught this, and found a use for it.


Cheers,

Patrick.

---

### Post by inportb on 2007-04-28
Indeed, I've seen this solution. However, it just won't work for me. The moment I reboot with "fglrx," I get the log-off symptom. Oh, well. Still searching... getting ***-raped by ATI sure is fun. I must say, I am very grateful for the help I've been getting. Thank you.

It's been fixed =D and I've posted details in my thread.

---

