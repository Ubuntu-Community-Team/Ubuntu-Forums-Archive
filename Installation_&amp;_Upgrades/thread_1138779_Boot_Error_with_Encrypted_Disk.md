---
title: "Boot Error with Encrypted Disk"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by jsroth on 2009-04-26
Hi folks,

my problem is similar to [this one]("http://ubuntuforums.org/showthread.php?t=1136896") but it's not quite the same.

I installed the Intrepid Ibex from the CD and upgraded to Jaunty today. I used the encrypt the whole disk option when I installed Intrepid. Now my system isn't booting any more, no matter which kernel (2.6.27 and 2.6.28) I'm using. It just wont do anything more than this:
```
Enter passphrase to unlock the disk (sda2_crypt):
key slot 0 unlocked
Command successful
cryptsetup: sda2_crypt setup successfully
Begin: Waiting for encrypted source device ...

```
Then it freezes and wont to anything no matter how long you wait.

I can boot into a live system, install lvm2 and cryptsetup and then the partition is perfectly mountable and I'm able to read and write on it.

I'm having the adventurous guess that it could be related to the [LUKS failing automount in Jaunty bug](https://bugs.launchpad.net/ubuntu/+bug/363426) but that's just I guess and I have no idea how to get around it.

Do you need any more information, have you got any ideas that could eventually save me?

---

### Post by jsroth on 2009-04-27
Absolutely no ideas?

Do you think it would be worth a try creating an (unencrypted) image from the encrypted partition and use that again? I think I'm going to try that with a virtual machine and see what happens.

---

### Post by fieus on 2009-04-27
I'm having exactly the same problem. Solution found, thumbs up to zabuzzman ;)

---

### Post by fieus on 2009-04-27
OK! I was able to fix it.

My setup: 
/dev/sda1 boot partition (unencrypted)
/dev/sda5 root partition (encrypted)
/dev/sda6 swap partition (encrypted)

Boot a live-cd.
# Become root
sudo su
# Mount the boot partition temporarily somewhere
mount /dev/sda1 /mnt
# make a temp directory to extract the initrd image
mkdir /tmp/image 
# Copy your current initrd image to tmp/image (check this in /mnt/grub/menu.lst)
cp /mnt/initrd.img-2.6.28-11-generic /tmp/image/initrd.img-2.6.28-11-generic.orig

cd /tmp/image
# extract the initrd image
gzip -d < initrd.img-2.6.28-11-generic.orig | cpio --extract --verbose --make-directories --no-absolute-filenames
vi conf/conf.d/cryptroot

>> There you will see something like
target=sda5_crypt,source=/dev/disk/by-uuid/blahdiblah,key=none

Change this to: 
target=sda5_crypt,source=/dev/sda5,key=none

find . | cpio -H newc --create --verbose | gzip -9 > initrd.img-2.6.28-11-generic

cp initrd.img-2.6.28-11-generic /mnt

Reboot and enjoy the Jaunty bitch :)

---

### Post by jsroth on 2009-04-27
Thank you so much! It does boot now, did what you described there and that was just what needed to be done! Perfect! Can't thank you enough.


Now I have no sound, but I think I'll fix that and I'll be able to listen to the guitar :guitar:

---

### Post by Kissell on 2013-05-05
Didn't work for me.  

I upgraded Ubuntu 12.04.02 LTS kernel from 3.2 to 3.9 and when I rebooted I got this error...  my root partition is encrypted.

I tried these steps, looked promising the whole way through...  but didn't work.  :(

---

