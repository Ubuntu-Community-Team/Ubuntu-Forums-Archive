---
title: "ThinkPad x41 Tablet Problems"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by choban on 2006-06-04
I'm having trouble getting my pen to work with my ThinkPad x41 Tablet. I've followed instructions from [this]("http://ubuntuforums.org/showthread.php?t=152118&highlight=wacom+x41") post. The only part I struggled with was using the wacdump, I wasn't sure how that was suppose to help. I even tried using some ports used in a few Red Hat tutorials for the x41. Even after fighting this for a couple hours I can't get the pen to work at all. If anyone has any ideas on where to go from here or has successfully set up the x41 before, help would be great.

---

### Post by rbalfour on 2006-06-04
wacdump is for Wacom tablet support.
Do some research and find out if the x41 is a wacom tab or clone wacom.

---

### Post by K0LO on 2006-06-13
I had my X41 Tablet working perfectly with Kubuntu Breezy 5.10, but when I upgraded to Dapper the pen stopped working.

After reading all of the wiki articles and much experimenting, I found the fix to be quite simple. Start with this article: [http://ubuntuforums.org/showthread.php?t=152118&highlight=wacom+x41]("http://ubuntuforums.org/showthread.php?t=152118&highlight=wacom+x41")

There are three sections in /etc/X11/xorg.conf to enable the wacom devices (cursor, stylus, and eraser). Each section references the serial device as "/dev/ttyS0". This is the serial port number that used to work for me using Breezy.

I found by experimenting that if you change the device to "/dev/ttyS4" that everything starts working again. I did not have to initialize the serial port using setserial; it seems to be already detected and configured.

So, simple solution. Just change every occurrence of "ttyS0" to "ttyS4" in your xorg.conf file.

---

### Post by Belathor on 2006-06-14
That is odd. All I had to do was sudo apt-get install wacom-tools and it worked in Ubuntu. Screen rotation is another story, though:( . I have gnome-randr-applet installed with xrandr but X freezes every time I try to rotate the screen.

---

### Post by K0LO on 2006-06-14
Hi, Belathor!

Yes, I found it odd too.

I originally had Kubuntu 5.10 and tried to do a distribution upgrade to 6.60, but the upgrade failed, so I started over by leaving my home partition but deleting the partitions for root and swap and doing a clean install. Sometimes things turn out different if you upgrade versus install fresh.

Also, there are slight differences between Ubuntu and Kubuntu.

Perhaps one of these two factors result in the serial port assignment turning out different (ttyS4 versus ttyS0).

I also just ran across another post that said the same thing; the wacom serial port was now on ttyS4. I wonder why???

---

### Post by choban on 2006-06-14
I changed the serial ports to ttyS4 and everything worked.

Thanks for the help.

---

