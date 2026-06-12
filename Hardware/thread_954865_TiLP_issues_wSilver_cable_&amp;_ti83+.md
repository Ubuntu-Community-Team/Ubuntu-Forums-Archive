---
title: "TiLP issues w/Silver cable &amp; ti83+"
date: 2008-10-21
forum: Hardware
---

### Post by zmjjmz on 2008-10-21
Ok, so I open TiLP and when I try to connect (after entering the info; SilverLink and TI83+ etc.) I get an error, something about nodes and whatnot.
Here's a pastebin: [http://pastebin.com/fa85ec5c](http://pastebin.com/fa85ec5c)
I've been asking around in #tcpa, and I've been told that it looks like a libusb problem. Does anyone know a way around this?

---

### Post by jluda on 2008-12-18
me too i am having the same problem have you figured it out?

---

### Post by zmjjmz on 2008-12-18
> **jluda said:**
> me too i am having the same problem have you figured it out?

I resorted to using TiLP2 with my Windows machine, and whenever I tried to send an Assembly program it said "Error: NACK received) or something similar.

---

### Post by Samnsparky on 2008-12-19
Hello! I seem to have found an answer to this problem. What I did was I went to [http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/](http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/) and installed the following packages:
[LIST]
[*]libticables2-1_1.2.0-1_i386.deb
[*]libticonv3_1.1.0-1_i386.deb
[*]libtifiles2-5_1.1.1-1_i386.deb
[*]tilp2_1.12-1_i386.deb
[/LIST]

Once everything was complete, I went to a terminal and typed in gksu tilp, pressed CTRL-D, selected my settings (silver link with a 84+), clicked the "Ready?" button, and finally clicked on Dirlist.

Good luck,
Sam

---

### Post by zmjjmz on 2008-12-20
> **Samnsparky said:**
> Hello! I seem to have found an answer to this problem. What I did was I went to [http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/](http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/) and installed the following packages:
[LIST]
[*]libticables2-1_1.2.0-1_i386.deb
[*]libticonv3_1.1.0-1_i386.deb
[*]libtifiles2-5_1.1.1-1_i386.deb
[*]tilp2_1.12-1_i386.deb
[/LIST]

Once everything was complete, I went to a terminal and typed in gksu tilp, pressed CTRL-D, selected my settings (silver link with a 84+), clicked the "Ready?" button, and finally clicked on Dirlist.

Good luck,
Sam
Were you able to successfully send assembly programs?

---

### Post by Samnsparky on 2008-12-20
Yes, well at least so far so good ;)

---

### Post by zmjjmz on 2008-12-20
Well it's not working for me :/
Whenever I try to put it in the Apps folder, I get an error along thelines of "NACK Received".
Anyone know what that means?
EDIT: It means "Negative Acknowledgment".
This does not help me.

---

### Post by RU-In? on 2008-12-27
Hi all,

Samnsparky's solution is the workaround that I used for my TI84+ with the 'directlink' cable. That is the USB cable that comes with the TI84+, from what I have read on the web, and according to samnsparky too, this will work for the 'silverlink' cable too.

There are a lot of people who have this issue w/ Ubuntu and there TI 83/84 Graphing Calculators. I am going to post a 'how to get tilp2 working under Ubuntu' thread, so it will be easier to find w/ a Google search. I have also posted the workaround at Launchpad.

**[http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/](http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/)**

zmjjmz, I think you are having some different issues, from what I could tell by this thread, you are actually connecting to your calculator but are having issues with certain transfers? If not you should post some more info, like your Ubuntu version and is it 64 or 32 bit. Are you running it on your mac? Also you need to run tilp as root. 'sudo tilp' in a term will do the trick if all is running well according to samnsparky's instructions.

Here is my more drawn out solution:

This is what I did to get tilp2 working on my Intrepid (32bit) install...

1. If you still have the tilp2 (and dependencies) installed from the repos, open synaptic and remove them.

2. Then goto this site and get the packages needed...

**[http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/](http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/)**

NOTE: For a description of each package, click on the 'Packages' link in the directory at this site, you
can download the description file by downloading 'Packages.gz' file)

For this workaround, download the following packages and install them in the order listed...

[B]libticonv3_1.1.0-1_i386.deb
libtifiles2-5_1.1.1-1_i386.deb
libticalcs2-7_1.1.3-1_i386.deb
libticables2-1_1.2.0-1_i386.deb

gfm_1.02-1_i386.deb
tilp2_1.12-1_i386.deb[/B]

NOTE: I installed all of these in the order listed above (just double click them and deb package manager will open)

After successful install of the above packages you will have to open a terminal and run tilp as sudo

$ sudo tilp

also gfm will run as regular user, just type 'gfm' in a terminal (no quotes :) ). It is a file grouper/ungrouper for the TI backups

---

### Post by zmjjmz on 2008-12-30
> **RU-In? said:**
> Hi all,
zmjjmz, I think you are having some different issues, from what I could tell by this thread, you are actually connecting to your calculator but are having issues with certain transfers? If not you should post some more info, like your Ubuntu version and is it 64 or 32 bit. Are you running it on your mac? Also you need to run tilp as root. 'sudo tilp' in a term will do the trick if all is running well according to samnsparky's instructions.


I'm running 32-bit Ubuntu 8.04, on my lpia Dell Mini. I had the same problems with Windows XP Pro 32-bit on a Pentium III, so I don't think it has anything to do with that. I have been running tilp as root.

---

