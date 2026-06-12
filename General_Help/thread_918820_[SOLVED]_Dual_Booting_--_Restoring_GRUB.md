---
title: "[SOLVED] Dual Booting -- Restoring GRUB"
date: 2008-09-13
forum: General Help
---

### Post by VivaLaEva on 2008-09-13
Hey there.
Now, I've ganked up my OS more times than I can remember by tinkerin' around with it, but one thing is for sure: Every time, I've done the same thing, and it's always worked:
-Clean install Hardy Heron 8.04
-50 trillion updates
-Partition HD with gParted LiveCD
-Throw in either TinyVista or XP [been flip-flopping, went with XP this time]
-Install
-Follow this awesome tutorial on restoring GRUB: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

Now, this has worked for me every single time.  Flawlessly.  Up until right now.

HERE'S THE PROBLEM:
When I go to restore the GRUB boot loader, it says to type in:
sudo gedit /boot/grub/menu.lst

And I do.
But it just shows up as a blank screen, and claims that the file does not exist.
Now, I have not done a single thing differently from usual.
Any ideas on where this thing is, how I can restore/find it...?
Please and thank you!

---

### Post by northern lights on 2008-09-13
If the file doesn't exist yet, just create it anew.

Further, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") might be worth a look.

And, as an aside, please **never** run graphical applications with sudo. If a graphical app needs to be run a superuser, use gksu/gksudo/kdesu instead. See [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") for references.

---

### Post by VivaLaEva on 2008-09-13
Well, the original file...is supposed to exist.  And I don't know how to make a new one, especially 'cause when I attempted to copy/paste just the new information it wouldn't allow me, specifically citing the cause that the file did not exist.

And when attempting to go through the new link you just gave me...well...:

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

I do believe something is amiss here, these random files being all...gone..and things.
Any other ideas?

Thank you for the quick response.

---

### Post by Predator106 on 2008-09-13
Well I haven't used that LiveCD, because I see no point in not using the Ubuntu LiveCD, but wouldn't you actually have to mount the disk? Because in the normal LiveCD, it would actually just be pointing to the file on the disk, which probably doesn't exist, in which case you would have to mount the disk in question, and then type in /media/disk-1 (or whatever disk it is), followed by the /boot/.....etc...

Tell me if I'm wrong or not, as I don't actually know what is on the CD you are using.

---

### Post by caljohnsmith on 2008-09-13
> **VivaLaEva said:**
> Well, the original file...is supposed to exist.  And I don't know how to make a new one, especially 'cause when I attempted to copy/paste just the new information it wouldn't allow me, specifically citing the cause that the file did not exist.

And when attempting to go through the new link you just gave me...well...:

grub> find /boot/grub/stage1
find /boot/grub/stage1
 [COLOR="red"](hd0,0)[/COLOR]
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

I do believe something is amiss here, these random files being all...gone..and things.
Any other ideas?

Thank you for the quick response.
The whole idea of using that "find /boot/grub/stage1" command in Grub is to find your Ubuntu partition, which it did as (hd0,0), and then you use that result in the subsequent commands. :) So you should do:
```
grub> root (hd0,0)
grub> setup (hd0)
```
That will reinstall Grub to the HDD's master boot record (MBR). Also, if you run this command from the Live CD:
```
gksudo gedit /boot/grub/menu.lst
```
It is looking for the Live CD's menu.lst, which doesn't exist. :) You'll need to mount your Ubuntu partition, and then open up its menu.lst to edit it. First do:
```
sudo fdisk -l
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Post the results of that and we can help you modify your menu.lst, or if you want to try and do it yourself:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
Let us know how it goes, or if you need more details/info.

---

### Post by lswb on 2008-09-13
Try the grub-install command and update-grub script which will create a default menu.lst. Start up with your live CD and in a terminal type "man grub-install" and "man update-grub" for details.

---

### Post by northern lights on 2008-09-13
> **caljohnsmith said:**
> the whole idea of using that "find /boot/grub/stage1" command in grub is to find your ubuntu partition, which it did as (hd0,0), and then you use that result in the subsequent commands. :) so you should do:
```
grub> root (hd0,0)
grub> setup (hd0)
```
that will reinstall grub to the hdd's master boot record (mbr). Also, if you run this command from the live cd:
```
gksudo gedit /boot/grub/menu.lst
```
it is looking for the live cd's menu.lst, which doesn't exist. :) you'll need to mount your ubuntu partition, and then open up its menu.lst to edit it. First do:
```
sudo fdisk -l
```
post the results of that, and also figure which is your ubuntu partition in the form sdxy (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdxy /mnt
cat /mnt/boot/grub/menu.lst
```
post the results of that and we can help you modify your menu.lst, or if you want to try and do it yourself:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
let us know how it goes, or if you need more details/info.
+1

---

### Post by VivaLaEva on 2008-09-13
Oh, thank you all for your replies, but caljohnsmith, that was PERFECT.
Everything's good.

Thanks again~!

---

### Post by VivaLaEva on 2008-09-13
Urgh, spoke too soon...now I get an error 13, invalid executable command, when trying to boot into XP [but Ubuntu works just fine]...any ideas? I re-checked my spelling and all [I've missed a parenthasis before], but alas -- I copied it properly.

EDIT

Oops, hah, I forgot that there's a partition inbetween Ubuntu and XP [for other Linux OSes], so it'd be (hd0,2) instead of (hd0,1). My bad!! ^-^;;

---

### Post by caljohnsmith on 2008-09-13
So is everything working Grub-wise? :)

---

