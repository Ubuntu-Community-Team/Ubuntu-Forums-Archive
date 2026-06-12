---
title: "Continuing netbook issues"
date: 2011-10-24
forum: Hardware
---

### Post by interacter on 2011-10-24
Hi all

Still having problems with the Acer Aspire One.

Had Jolicloud, moved to Ubuntu 11.04.  Upgraded to 11.10 and it all went wrong.

Tried to put Jolicloud back on -would boot only on USB.  Wouldn't load without.

Ubuntu wouldn't even install.

Tried again with Jolicloud this morning, get an input/output error.  Something about a hard disk problem (which I was wondering about as it took 1hr+ to install Jolicloud yesterday).

I'm wondering if my hdd has died on me.  Would explain a lot of things.  

Is there any way to reformat without an OS loading?  I think some of the installations might have confused the HDD somewhat.

Looking around the web, also seeing info about flashing the BIOS.  But I'm not sure if I need to or how I can do it!

If you can help, I would really appreciate it!  All ISOs are freshly downloaded and I've tried two different USB key creators in case the issues have been in there.  

Cheers
Neil

---

### Post by mikewhatever on 2011-10-24
Can you be a lot less vague about the errors. They may be very useful in troubleshooting, so, as soon as you see any, take a screenshot, write down or memorize the error text and post here.

To answer the question, you must load something to format the hdd. It doesn't have to be an OS, could be a disk management program, but something must run first, before it can format. That aside, formatting won't solve a dead hdd problem. If that's the case, you'll need to buy a new one.

---

### Post by interacter on 2011-10-24
Hiya

I totally agree about the descriptions - did my best!

Thought I would give Jolicloud one last go.  Managed to boot from USB OK.  Shut down with the intention of going for one last install.

Tried to boot from USB, black screen.

Tried to boot normally, black screen.

Hmm methinks if could be dead!  Completely out of ideas now as it won't boot from USB at all.  

If there's anything you can suggest, would greatly appreciate it!

Neil

---

### Post by mikewhatever on 2011-10-24
What do you mean by 'Tried to boot normally'? Is booting from a USB stick supposed to be not normal?
You'll have to give us something more substantial then 'tried to boot ... black screen', also, if you want help with Jolicloud, try their forum instead of here.

---

### Post by ajgreeny on 2011-10-24
You do not need a hard disk in the machine to boot to a live system from a USB, as the hard disk will only be needed when you try to install, though a live system would use a swap partition if one exists.

Are you certain the jolicloud USB is a good one and made from a good iso file?

Either way I suggest you try again to boot again to a live Ubuntu system, then use gparted from that to reformat, or at least delete all partitions found on the disk.  You may then be able to reinstall.

When using the live system you can easily see if all the files you expect to be present are there, and you can also run ```
sudo fdisk -l
``` in terminal to see what partitions exist at the moment.

---

### Post by interacter on 2011-10-24
Hiya

I'm as certain as I can be that the Jolicloud is a good ISO - downloaded it direct from them this morning and got one good boot out of it (using the Try... option).

I'll have to give a full Ubuntu a try again later.  It's all very odd - tried twice with a fresh download of 11.10 last night and this morning, and it just doesn't like it...

Trouble is, sometimes it seems to work, then won't boot.  Other times it just won't boot.

It's as though the little bit of magic that says to the system "Run me to boot up and work normally" goes AWOL...

Sorry for the non-tech speak...  Completely confused by it all!  The only time I've ever had problems like this was with an old Windows install when the HDD collapsed.  I assumed that this didn't happen earlier as I was running Jolicloud OK (ish) from the USB...

Thanks again
Neil

---

