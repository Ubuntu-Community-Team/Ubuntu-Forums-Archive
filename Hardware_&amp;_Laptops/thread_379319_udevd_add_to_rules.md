---
title: "udevd add_to_rules"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by Fenix-TX on 2007-03-08
Hi! Today when i've run my computer i've had this issue on boot:

```

udevd[2135]: add_to_rules : unknown Key 'ATTRS{idVendor}'
udevd[2135]: add_to_rules : unknown Key 'ATTRS{idProduct}'

```

And my printer doesn't work, i can see my printer on USB.

---

### Post by Fenix-TX on 2007-03-08
Well, i found the problem, it's the file /etc/udev/rules.d/45-libgphoto2.rules
I've made a backup of this file on my home, deleted the file and i've restarted my computer and now i don't have the problem and my printer works again.

This is the content of the file, if someone see the problem (i don't know if i did the correct deleting the file, i'm sure that there is a bad line on the file):

[45-libgphoto2.rules]("http://webs.ono.com/jesusvpct/45-libgphoto2.rules")

The file have the date of today, so it's possible that it was installed on some package update.

---

### Post by torekiki on 2007-03-08
i have the same issue to!

---

### Post by jlm3030 on 2007-03-08
Just did a update and got the same issue.

---

### Post by amelyst on 2007-03-09
I had the same problems after upgrading and installing the backport of libgphoto2 from feisty to edgy.

The problem is, that the udev system does no longer setup the /dev/usblpxx node with the correct permissions and ownerships.

The problem derives from the already mentioned file /etc/udev/rules.d/45-libgphoto2.rules.

This file gets activated from the udev system to find a macthing rule for any newly attached usb device to setup the corrsponding /dev device node entry.
The syntax used in this file does obviously no correspond to the udev version used in edgy, hence the error messages and furthermore the wrong setup of the /dev/usblpxx node with group ownership to plugdev instead of lp.

As stated in the changelog for the backport:

 > * Automated backport upload; no source changes.

this is clearly an oversight from the packager.

The solution to remove the file  /etc/udev/rules.d/45-libgphoto2.rules completely is **not** advised, since you will certainly have problems accessing any usb camera.

My solution is the following:

[LIST]
[*]edit the file  /etc/udev/rules.d/45-libgphoto2.rules
[*]replace all occurances of ATTRS with SYSFS
[*]save the file
[/LIST]


To check out, that this works you just have to check out the permissions and ownerships of the /dev/usblpxx (xx stands for 0, 1 etc depending on how many usb printers you have turned on)

The group should be set to lp. The wrong setup had set it to plugdev.

This seems to me again a quick and not thoroughly tested backport, resulting in disabling main parts of the whole system

I hope this helps to workaround the problem for you too.

cheers

---

### Post by mrcanard on 2007-03-09
Sanity check for this ordinary user please.

1) Updated Ubuntu 6.1 A.M. 2007 03 08
2) P.M. 2007 03 08 noticed printer took poop

To fix I should find and replace ATTRS with SYSFS in /etc/udev/rules.d/45-libgphoto2.rules then save.

Should the printer be removed or disconnected before doing this?

This version of Ubuntu has worked very good until now and I'm trying not to make a bad thing worse.

Thanks for your patience.

---

### Post by foormea on 2007-03-09
i'm not an expert but i can help you for what you wanna do though

open a terminal, then
> 
cd /etc/udev/rules.d/
sudo cp 45-libgphoto2.rules 45-libgphoto2.rules.backup

then edit as root the file:
> 
gksudo gedit 45-libgphoto2.rules

and make the changes.

if that doesn't work like that, you can still revert changes by renaming the backup file to its original name

---

### Post by lolwhites on 2007-03-10
Am having the same problem - my HP Laserjet 5L hasn't printed anything since I upgraded to Edgy. Reinstalling the printer and drivers doesn't make any difference.

I tried amelyst's solution, but the phrase ATTRS is nowhere in the relevant file - it's already SYSFS so that can't be the problem.

---

### Post by mrcanard on 2007-03-10
I did the replace ATTRS with SYSFS in /etc/udev/rules.d/45-libgphoto2.rules then save thing.
After restarting the printer it prints just fine now.
Regards,

---

### Post by catfishy on 2007-03-11
So, I just had the same issue after an update apparently.  But my issue is with an external usb drive and amarok.  After doing the editting of that file mentioned above, the message at startup disappeared, but Amarok is now buggy.  When Amarok tries to "update collection" it tries to re-build the whole collection, not just updating the new stuff.  It doesn't seem like I've lost permissions on the collection because I can still browse and play anything on the drive.  Really strange.  I'm glad you've made your printer work, but does anyone have suggestions about this external drive problem?  It worked perfectly before this udevd fiasco.  Thanks!!!!

edit: even after an update to libgphoto2, the usb external drive data isn't being updated in amarok.... oh well

---

### Post by wobster on 2007-03-11
I just made a dist-upgrade and libgphoto2 was updated fine, correcting the values.

---

### Post by precinto on 2007-03-12
Synaptics TouchPad is still not working for me!

---

### Post by bmenge on 2007-08-12
ok so my printer stopped working today...I got it working with my wifes school district provided ibook... Gave it another look and found that error parallel port busy.  So I searched the forum got pointed here when I took a look at the file

I got about 600+ lines that look like this.

ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0403", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0404", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="08ca", ATTRS{idProduct}=="0111", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="120a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="2770", ATTRS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="093a", ATTRS{idProduct}=="010f", MODE="0660", GROUP="plugdev

It seems that to change all these is a bit out of the question?

Thanks

---

