---
title: "This newbie can't start XSane -- &quot;Error during I/O&quot; (vague!)"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by Giggity on 2006-09-22
So, Ubuntu prints via HPLIP quite nicely, but:

I thought that I might use my PSC 2110's scanning functions today, but I can't get either XSane, GiMP, or Kooka to recognize/use my scanner.  All of the error messages are vague at best.  Attached is the error message from GiMP and XSane (the same error), and the one in the corner of Kooka.

Does anyone know what commands I should run to find out what the problem is?  I'm guessing it might have something to do with the recent kernel upgrade, which pretty much demolished every other function on my computer ([I still haven't figured out how to get bridged networking back up and running on VMWare...]("http://www.ubuntuforums.org/showthread.php?t=258872"), and yes I have updated my kernel headers).

So, what information do you require, and how can I get it for you?

Here's a start, as I gather you'll need this!
```
rob@rob-desktop:~$ uname -r
2.6.15-27-386
```

Also, my xSane version is 0.97

---

### Post by Giggity on 2006-10-15
Does anyone have any suggestions?  It would be nice not to have to reboot into Windows just to scan an image.

---

### Post by teyster2 on 2006-11-05
Same problem here.  Worked fine in 6.06, but not working in Edgy. Hope we get an answer soon.

---

### Post by teyster2 on 2006-11-06
[http://ftp.us.debian.org/debian/pool....97-3_i386.deb](http://ftp.us.debian.org/debian/pool....97-3_i386.deb)
[http://ftp.us.debian.org/debian/pool...0.97-3_all.deb](http://ftp.us.debian.org/debian/pool...0.97-3_all.deb)

I used synaptic to uninstall xsane and xsane-common.  I then installed the two files above.  Yeah, I know, working backwards.  It worked though, after logging out and back in.  Then naturally I got the upgrade message on the control panel.  Leary at first I did the upgrade - Logged out and back in and it still works like a champ.  I have the officejet 5600.  Hope this helps.

---

### Post by Giggity on 2006-11-20
Thank you.  I had pretty much given up on this and switched back to Windows permanently about a month ago, but if this works, I just might go back to being a dedicated Ubuntite.

I'm in the middle of something in Windows right now, but I'll give this a shot when I'm done and let you know how things pan out.

---

### Post by Giggity on 2006-11-20
Well, that little scheme didn't work at all.  Still the same error.  Thanks for trying, but it's back to Windows for me.  It might be slow, but it does what I ask it to do.

---

### Post by philipgm on 2006-12-18
I just put an officejet 5600 on my Edgy box and I didn't have to change anything! So much nicer than those awful HP printer software installs!

---

