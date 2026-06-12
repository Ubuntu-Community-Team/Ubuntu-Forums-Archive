---
title: "jaunty - /dev/disk/by-uuid problem and solution"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by hg21 on 2009-04-25
I post this in case others have the same problem

I upgraded to 9.04 and it failed with message :-
/dev/disk/by-uuid/f38de6a2-e5c9-45cc-b717-8685b6bf does not exist.

Doing ls /dev/disk/by-uuid/, in the shell it dropped to, I found f38de6a2-e5c9-45cc-b717-8685b6bf indeed did not exist but
f38de6a2-e5c9-45cc-b717-8685b6bfbf0 did exist
I added bf0 to the UUID in grub menu and jaunty then worked. 

It would seem the auto set up of the grub menu by 9.04 did not work correctly.

---

### Post by ralewis on 2009-04-25
I'm having the same problem, but when I drop into busybox, it tells me that the folder /dev/disk does not exist.

Also, I booted into a live CD, chroot'd into my mounted hard drive, and still could not find a /dev/disk folder.

I have checked my UUID by other means though, and it does match the one found in my menu.lst, i just think ubuntu is complaining because the folder is not actually there.

Do you know if there is something simple that I'm overlooking?

---

### Post by ralewis on 2009-04-26
Nevermind, I fixed it.

In a separate install partition, I chroot'd into my broken partition and did an apt-get upgrade and apt-get dist-upgrade.  This finished the upgrade to Jaunty, and fixed booting the partition.

---

### Post by crusty_collins on 2009-04-26
I had the same issue with uuid.  a sudo apt-get dist-upgrade did the trick for booting but still having issues with kdm

---

### Post by Aevorn on 2009-04-26
> **hg21 said:**
> I post this in case others have the same problem

I upgraded to 9.04 and it failed with message :-
/dev/disk/by-uuid/f38de6a2-e5c9-45cc-b717-8685b6bf does not exist.

Doing ls /dev/disk/by-uuid/, in the shell it dropped to, I found f38de6a2-e5c9-45cc-b717-8685b6bf indeed did not exist but
f38de6a2-e5c9-45cc-b717-8685b6bfbf0 did exist
I added bf0 to the UUID in grub menu and jaunty then worked. 

It would seem the auto set up of the grub menu by 9.04 did not work correctly.
_Problem_
After upgrading, upon a reboot I had the following error:
Mounting /dev/disk/by-uuid/[UUID]
Failed: Invalid argument

_Solution_
1.) As suggested by [http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250) I downloaded an iso of my ubuntu and made a CD. Booting from CD.
2.) Open Places|Computer, right-click the icon for my primary HDD and choose "mount". Having just one disk at that time made it easy. You'll see your CD Drive, File System (The Live CD one) and your HDD.
3.) Right-click the icon for the HDD, on the Desktop, when it appears. Choose Volume and after "media/" add a suitable name, e.g. "System". Press "OK", then unmount the volume and mount it again, for the change to take effect.
4.) Open Applications|Accessories|Terminal.
5.) Type sudo su - [ENTER]
6.) Type chroot /media/System [ENTER]
7.) apt-get upgrade
8.) apt-get dist-upgrade
9.) Reboot, remove the CD.

And now it's working.

I'm no guru to this, which is why I'm making this detailed explaination for others in a similar situation.

It worked for me. It may work for you, but please verify that my commands aren't damaging to your system and try to do a backup before you follow the above.

---

