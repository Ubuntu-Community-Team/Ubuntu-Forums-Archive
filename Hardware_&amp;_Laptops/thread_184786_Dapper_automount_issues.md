---
title: "Dapper automount issues"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by PapaWiskas on 2006-05-30
Last night I did an upgrade via text installer cd via what aysiu suggested.

All was fine and dandy until today when I really started using Dapper.

When I insert a DVD or CD the icon does not show up on the desktop.  Neither does my USB pendrive, I cant even access it.  The DVDs I can access by fiddling around with Totem, and eventually an icon appears.

I just want the icons to show up on the desktop when I put a disc or plug in my pendrive

Now as far as group permissions go everything appears normal, meaning HAL belongs to the right groups etc.

Upon further reading, it seems that for some reason some things got uninstalled during the upgrade and not put back in place or something.  When I get home tonight for the usb and cdrom automount I am going to install the following packages since for some reason they are not installed now.

devfsd (1.3.25-23)
liblockfile1 (1.06)
lockfile-progs (0.1.10)
usbmount (0.0.12)
usbview (1.0-6ubuntu1)

So am I on the right track by putting the above packages in?

I also noticed I can no longer use K3B in gnome anymore, it is totally gone.  So does this mean I need install the RC of KUBUNTU as well?
And my Open Office was totally gone, had to reinstall that last night, along with Evolution.  

I noticed during the Dapper update it was deleting some of these things, but I had assumed it would also be putting them back, obviously that didn't happen.  Is there anything else I should be checking out?

I am impressed with Dapper, and I really dont want to re-install everything.  I think what I am experiencing can be fixed with enough guidance and patience.

Thanks everyone.

---

### Post by Dreaden on 2006-05-30
[QUOTE=PapaWiskas]Lhen I insert a DVD or CD the icon does not show up on the desktop.  Neither does my USB pendrive, I cant even access it.  The DVDs I can access by fiddling around with Totem, and eventually an icon appears.

I just want the icons to show up on the desktop when I put a disc or plug in my pendrive
[/QUOTE]

I've got the same problem, my usb-external disk won't mount. My device is not listed as /dev/sd*. 
dmesg|tail shows:
```
[4339928.387000] USB Universal Host Controller Interface driver v2.3
[4340760.382000] Initializing USB Mass Storage driver...
[4340760.382000] usbcore: registered new driver usb-storage
[4340760.382000] USB Mass Storage support registered.
```
But when I plug my usb-disk in and out, no new messages appear in dmesg.

A couple of days ago, everything worked perfectly.

---

### Post by PapaWiskas on 2006-05-30
OK here is what I did to fix my issue. 
This is all taken from my history in synaptic....keep in mind, I am not an expert, but I did fix my problem after reading and trying a bunch of stuff on automounting that did not work....so I did this myself, now my USB and CDROMS/DVDS automount fine and show icons on the desktop.

Here is the first thing I did...

Completely removed the following packages:
hal

Removed the following packages:
gnome-power-manager
gnome-session
hal-device-manager
hwdb-client

Then I did the following...
Installed the following packages:
gnome-power-manager (2.14.3-0ubuntu11)
gnome-session (2.14.1-0ubuntu11)
gnome-utils (2.14.0-0ubuntu5)
gnome-volume-manager (1.5.15-0ubuntu10)
hal (0.5.7-1ubuntu18)
hal-device-manager (0.5.7-1ubuntu18)
hwdb-client (0.6-0ubuntu10)

And now everything works again, dont ask me how or why because I dont know.

---

### Post by blz on 2006-06-22
Thank you, PapaWiskas! I've done the things that you pointed and now everything works =) (automounting usb, writing to usb, etc.)

---

### Post by daveg on 2006-06-28
Dammit, that didn't work for me :'(

---

### Post by mkjana on 2006-06-28
Thank you PapaWiskas,
I tried your trick. Now the CDROM appears :-D  but after clicking on CD /DVD creator under places. Still I cannot see my pendrive :( . Any suggestions.

jana

---

### Post by mkjana on 2006-06-28
In addition to my last posting - My old habit of rebooting the system helped me. After installing whatever PapaWiskas has suggested, I could not see any signs of automounting of CDROM and USB pendrive. After rebooting they are automounting like a breeze.

Thanks!
jana

---

### Post by xinelo on 2006-08-09
> **PapaWiskas said:**
> OK here is what I did to fix my issue.
This is all taken from my history in synaptic....keep in mind, I am not an expert, but I did fix my problem after reading and trying a bunch of stuff on automounting that did not work....so I did this myself, now my USB and CDROMS/DVDS automount fine and show icons on the desktop.

Here is the first thing I did...

Completely removed the following packages:
hal

Removed the following packages:
gnome-power-manager
gnome-session
hal-device-manager
hwdb-client

Then I did the following...
Installed the following packages:
gnome-power-manager (2.14.3-0ubuntu11)
gnome-session (2.14.1-0ubuntu11)
gnome-utils (2.14.0-0ubuntu5)
gnome-volume-manager (1.5.15-0ubuntu10)
hal (0.5.7-1ubuntu1
hal-device-manager (0.5.7-1ubuntu1
hwdb-client (0.6-0ubuntu10)

And now everything works again, dont ask me how or why because I dont know.

It seems it also worked for me. Weird methods for weird problemes. 

Thanks, xinelo

---

### Post by bestiarosa on 2006-08-12
Thanks!
This also fixed a weird problem I had with the trashbin. \\:D/

---

### Post by dumpster25 on 2006-10-13
I did this procedure. I rebooted to an older kernel and the automount feature started working again. Then I rebooted with the newer kernel again and it kept working. I did not reinstall any packages at all. Well it works now anyway :D

---

### Post by PcDude on 2007-02-20
Just wanted to mention how I got it to work.  I just marked for reinstallation...

gnome-power-manager (2.14.3-0ubuntu11)
gnome-session (2.14.3-0ubuntu11)
gnome-utils (2.14.0-0ubuntu5)
gnome-volume-manager (1.5.15-0ubuntu10)
hal (0.5.7-1ubuntu1)
hal-device-manager (0.5.7-1ubuntu1)
hwdb-client (0.6-0ubuntu10)

...Note:  a restart was required afterwards.

To shorten the fix even more just mark the following TWO packages for reinstallation:

hal (0.5.7-1ubuntu1)
hal-device-manager (0.5.7-1ubuntu1)

...and restart.  I'm betting these two packages are at the heart of the problem.  Post your success/ failure trying this!

---

