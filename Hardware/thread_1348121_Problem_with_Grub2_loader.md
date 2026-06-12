---
title: "Problem with Grub2 loader"
date: 2009-12-06
forum: Hardware
---

### Post by pancho2 on 2009-12-06
URGENTLY NEED HELP!!!

I've seen a lot of threads addressing this, but as of yet they haven't really helped solve my grub problem.

GNU GRUB version 1.97 beta4

[ Minimal BASH-like editing is supported. For the first world, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>_

That's all I have. I installed Vista first, and then ubuntu, if that helps any. I'm currently on 9.10.

---

### Post by lidex on 2009-12-06
Did you install ubuntu with wubi?

---

### Post by oldfred on 2009-12-06
Try reinstalling grub per these instructions, you probably do not have to edit /etc/default/grub

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by pancho2 on 2009-12-07
Got as far as this:

sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by pancho2 on 2009-12-07
Correction: Tried it again (after rebooting) and got this instead.

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected

---

### Post by pancho2 on 2009-12-07
Ok, continued through, did the entire how-to, and discovered that I still get the same command line as before:

GNU GRUB version 1.97 beta4

[ Minimal BASH-like editing is supported. For the first world, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>_

What now??

---

### Post by oldfred on 2009-12-07
Herman knows a whole lot more than I. 

See this thread:
See herman's comments on OP with sh:grub and using command line
[http://ubuntuforums.org/showthread.php?t=1347583](http://ubuntuforums.org/showthread.php?t=1347583)

Herman's site - page on grub2:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by pancho2 on 2009-12-07
Ok, I got onto the 9.10 login screen tty1.

Logged onto the console. Now what?

I should mention I'm very new at ubuntu. Thank you for any help!!

---

### Post by pancho2 on 2009-12-07
When I try to sudo anything I get

sudo: must be setuid root

any ideas?

---

### Post by lidex on 2009-12-07
Try 
```
startx
```
command at prompt.

---

### Post by pancho2 on 2009-12-07
New set of issues:

followed Herman's directions (thanks oldfred) and managed to boot (kinda). After ubuntu 9.10 splashscreen, I get

could not update ICEauthority file /var/lib/gdm/.ICEauthority

then

There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

Any suggestions??

---

### Post by pancho2 on 2009-12-07
should also add that I'm gven a login screen now with my user name, but logging in causes to reload ubuntu and repeat everything previously listed. On the third attempt, the CPU screen stays black.

Help please!

---

### Post by lidex on 2009-12-07
At the tty try:
```
gdmsetup
```

---

### Post by oldfred on 2009-12-07
I would try to boot to a command line using the recovery choice or manually editing in grub the boot line and run these lines to see if it updates anything. I am not sure what the errors are related to perhaps something did not install correctly from the liveCD (unlikely but?)

sudo apt-get update 
sudo apt-get upgrade

---

### Post by pancho2 on 2009-12-07
OK, well I have a livecd which I'm using to boot ubuntu right now and am running the commands you gave me, oldfred. Once it's done, what should I do?

PS - I'm also from Chicago 'burbs. Gotta love this city :).

lixex, I tried gdmsetup but it returned this:

(gdmsetup: 3837): Gtk-WARNING **: cannot open display:

---

### Post by lidex on 2009-12-07
> (gdmsetup: 3837): Gtk-WARNING **: cannot open display:
[http://anaaman.blogspot.com/2007/01/gtk-warning-cannot-open-display.html]("http://anaaman.blogspot.com/2007/01/gtk-warning-cannot-open-display.html")
[http://www.linuxquestions.org/questions/linux-newbie-8/gtk-warning-cannot-open-display-187901/](http://www.linuxquestions.org/questions/linux-newbie-8/gtk-warning-cannot-open-display-187901/)

---

### Post by oldfred on 2009-12-07
If you are running from the liveCD you will have to chroot into your system and include the extra command for internet access which a lot of the chroot lists I have seen do not include:

Of course you must first know what partition you want to mount, in this example I'm using sda5:

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf  #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe #good to run "df- H" and "cat /etc/issue" to be certain you mounted #the correct partition).

apt-get update
apt-get upgrade
When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

