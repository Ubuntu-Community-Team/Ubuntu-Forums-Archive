---
title: "How to upgrade firmware of DVD burner/rewriter"
date: 2006-04-28
forum: Hardware &amp; Laptops
---

### Post by robenroute on 2006-04-28
Greetings, fellow Ubuntarians!

Looking for a decent DVD burner, I stumbled across the following issue: I'm currently building a system (hardware) from scratch and want to have only Linux running on it. From past experience, I know that upgrading CD-rewriter firmware was impossible without reverting to Wwwwwindows :-& 

As you can guess, that might cause a few problems running Linux only. Are there any DVD burners that support upgrading its firmware without the need for Wwwww.....? (sorry, can't get it over my lips) ;) 

I've already had a look on the BeeWee (Big Web), but it's kind of difficult finding flashing instructions for specific drives.

Thanks a bunch!

Rob

<edited for typos>

---

### Post by futz on 2006-04-28
I just ran into that problem last weekend. My Benq DW1640 had been reading and writing errors. Went to get a firmware update and it was all .exe's. Damn! 

I fiddled with it for half an hour or so (with Wine and such), and then got impatient, unscrewed it and quickly connected it to a spare windows box to update the firmware. Problem solved. :mrgreen: 

Without a spare windows box handy updating firmware becomes a bit more difficult...

I have the same drive in my Fedora box and I really don't want to pull the drive out. What do 100% linux users do about this problem???

---

### Post by erik_boi on 2006-04-28
If you are looking to buy a new drive it appears that some of the plextor burners firmware can be updated. 
A quick howto I found.

[http://www.linuxquestions.org/linux/answers/Hardware/Upgrade_Plextor_Firmware_with_UDEV_and_pxupdate_How_to]("http://www.linuxquestions.org/linux/answers/Hardware/Upgrade_Plextor_Firmware_with_UDEV_and_pxupdate_How_to")

-Erik

---

### Post by robenroute on 2006-04-28
Good Lord! It's almost a joke, the way hardware manufacturers ride the Wwwww-only train. What do companies with Unix/Linux servers do? Screw the DVD burner out of the box and fiddle it into a Www :-& box, just to upgrade the firmware? What on earth is wrong with these hardware manufacturers?

How about an auto update CD? Just write the firmware file to a CD (CD-RW/DVD/whatever) and power up the DVD burner. Burner recognizes this special file and flashes its EEPROM (or whatever silicon is holding its firmware). Simple solution, and most of all: completely OS independent!

I know, I know, barking up the wrong tree here. It's just so damn frustrating having to deal with half-wits, nitwits and other dimwits....

Sorry, couldn't resist.

Rob

---

### Post by robenroute on 2006-05-10
Hi there,

Just found a web site describing different ways of flashing BIOS (should also work for DVD/CD burners, I guess). Haven't tried it yet, since I still haven't got a DVD burner (moving to a new city, different job, different house, etc. No time for anything at the moment).

Hope this helps someone out there....

Rob

web site: [http://colt.projectgamma.com/bios/flashing.html]("http://colt.projectgamma.com/bios/flashing.html")

---

