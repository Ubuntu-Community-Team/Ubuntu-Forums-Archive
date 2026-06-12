---
title: "Printer: HP 690C doesn't print in color (Xubuntu)"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by eeried on 2006-10-09
Hello,
I read the thread about HP 690C won't print but I have a lesser problem.

I've installed Xubuntu on a friend's computer. I've installed the HP 690C printer which worked perfectly with Ubuntu Hoary out of the bow without any tweaking).

With Xubuntu, I have the following problem: I can't get it to print the test page in color (or any other page).

I used CUPS web interface I chose HPLIP 0.9.7 as the driver (is it outdated?)

I set the device URI to what Cups said: "hp:/par/DESKJET_690C" and the Devcie to /dev/parport0 (something wrong here?) 

I set the printer settings "Print out mode" to "normal" and  "Resolution, Quality (etc)" to 300 DPI, color, black+Color cartr.

The test page come out in black and grey and white.

Is the Xubuntu doc up-to-date:
> 
Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups

Select the group shadow and click Properties.

Add the user cupsys to the group.

Restart CUPS with this command:

$sudo /etc/init.d/cupsys restart

I couldn't find any shadow group in the graphical app so I edited the group file in which I could find shadow. I'll check if I did something wrong there but as the user can print, the permissions should be all right, shouldn't they?

Many thanks for your help in advance!

---

### Post by eeried on 2006-10-15
> Select the group shadow and click Properties.

Add the user cupsys to the group.

I've checked this -- it's all right.

I even added my friend's username to the lp group but I don't think it's necessary.

Anyway the test page is in black and white.

I set the printer option to normal and 300dpi black + color cartr
The Cups home local page ([http://localhost:631/](http://localhost:631/)) states:
> Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing). /usr/share/doc/cupsys/README.Debian.gz describes the details and how to reenable it again.

Would this be a clue?

Here's the printer page:
> Description: HP DESKJET 690C
Location:
Make and Model: HP DeskJet 690C Foomatic/hpijs (recommended) - HPLIP 0.9.7
Printer State: idle, accepting jobs, published.
Device URI: hp:/par/DESKJET_690C?device=/dev/parport0

Anything wrong there?

Your help would be very much appreciated!

---

### Post by eeried on 2006-11-06
Doesn't anybody has a clue?

This printer worked fine with Hoary. I'd install Dapper but the computer is only PII, 300Mhz, about 200MB RAM

---

