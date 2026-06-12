---
title: "Samsung N210 Brightness, Suspend, Hibernate"
date: 2010-12-22
forum: Hardware
---

### Post by DaltonAdair on 2010-12-22
Hi all,

I have a Samsung N210 I installed 10.10 Netbook on, and I'm having two issues with it:

1. I can't resume from Suspend or Hibernate. I did some searching, and I already tried installing the "hibernate" package and editing GRUB like was suggested by other users, alas, to no avail.

2. The brightness adjustment keys dont work! When I press Fn+up or down, Ubuntu will show me a brightness slider and it changes as I press the buttons. However, the brightness of the display does not change. 

Can anyone point me to a fix for these issues?

I've set it to simply blank the screen when the lid is closed as a sort of temporary bandaid, but that somewhat defeats the idea of battery longevity... :(

---

### Post by peterpall on 2011-01-04
Could not have described the problem better. Already filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/691425](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/691425) for this.
Adding a file (e.G. using sudo gedit) named

/etc/pm/sleep.d/99_LightsOn

with the following contents:

#!/bin/sh
case "$1" in
 resume|thaw)
  /usr/bin/setpci -s 00:02.0 f4.b=50
  ;;
esac

should work as a temporary fix for the resume issue. doing a

sudo setpci -s 00:02.0 f4.b=<some number between 00 and ff>

sets the brightness manually. On some models you might have to use 00.02.1 or similar after the -s parameter, though. But perhaps you want to go to my bug report first and click on the "bug affects me" button so the bug gains any importance at all; Another thread that talks about this problem is here: [http://ubuntuforums.org/showthread.php?p=9517612](http://ubuntuforums.org/showthread.php?p=9517612)

---

### Post by samo615 on 2011-01-04
Thanks for submitting this bug. I have a Samsung NB30 with the exact same issues. I hope they fix it soon. Both are important features for a netbook.
 
> **peterpall said:**
> Could not have described the problem better. Already filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/691425](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/691425) for this.
Adding a file (e.G. using sudo gedit) named
 
/etc/pm/sleep.d/99_LightsOn
 
with the following contents:
 
#!/bin/sh
case "$1" in
resume|thaw)
/usr/bin/setpci -s 00:02.0 f4.b=50
;;
esac
 
should work as a temporary fix for the resume issue. doing a
 
sudo setpci -s 00:02.0 f4.b=<some number between 00 and ff>
 
sets the brightness manually. On some models you might have to use 00.02.1 or similar after the -s parameter, though. But perhaps you want to go to my bug report first and click on the "bug affects me" button so the bug gains any importance at all; Another thread that talks about this problem is here: [http://ubuntuforums.org/showthread.php?p=9517612](http://ubuntuforums.org/showthread.php?p=9517612)

---

### Post by Bojanglez on 2011-06-27
I was having issues with the suspend feature and tried every solution in various forums. The best workaround I have found was DarrellKavanagh's post from here [http://www.voria.org/forum/viewtopic.php?t=523]("http://www.voria.org/forum/viewtopic.php?t=523") which basically suggests disabling the  "Wake on lid open" in the BIOS.

The only (minor) downside of this is that you have to hit the power button to resume from a suspend rather than it automatically doing so when you open the lid, but that is a very minor price to pay.

---

