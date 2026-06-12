---
title: "Usb Drive"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by mila80 on 2005-04-05
Hi,
   I have an usb HD driver but I can't use it with ubuntu bucause I can't read and write in it.
I tried with mount command, to mount it in the media dirctory.
I can read it but I can't write. 
When I reboot my system I must redo the mount comman.
I'd like to solve this problem but I'm not able. Is there a way  to make my usb hd works?
Why doesn't my system view the drive if I connect it after the boot???

Marco

---

### Post by lorap on 2005-04-06
hi friend!
it'll work!
first of all create a directory,say "usb-hd" in your home directory this way:

sudo mkdir /home/YourUserName/usb-hd

now let's get your hd connected:

sudo mount /dev/sr0 /home/YourUserName -t vfat -o umask=000

that's all :-)

now somw important tips:
i.if you're runnung not warty but hoary then you'll need to change "sr0" to "sda0".
ii.if you've formatted your usb hard drive as "ntfs" you'll need to write "ntfs" instead of "vfat".
have a nice day friend!
pavel

---

### Post by mila80 on 2005-04-07
Hi Pavel,
   tanks for your halp, but there is a problem: 
root@ubuntu:/home/marco # sudo mount /dev/sr0 /home/marco -t ntfs -o umask=000marct
mount: special device /dev/sr0 does not exist

What means???
Marco

---

### Post by mila80 on 2005-04-07
Ok, I'm sorry, I tryed with
root@ubuntu:/home/marco # sudo mount /dev/sda1 /home/marco -t ntfs -o umask=000marct

and return this error,

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       or too many mounted file systems
so I Think that the fs is fat and so

root@ubuntu:/home/marco # sudo mount /dev/sda1 /home/marco -t vfat -o umask=000marct
but it doesn't work
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       or too many mounted file systems


What I can do?

MArco

---

### Post by lorap on 2005-04-08
hi mila!
after umask=000 shouldn't be written anything!
i saw you've written markt but it shouldn't be there.
something else,if you run hoary as i see then you've to choose "sda0" driver but not "sr0".moreover,are you sure your usb drive's a ntfs patition?
let me know all this,even today.
have a nice day!
pavel

---

### Post by mila80 on 2005-04-10
Hi, ok, now I can mount and read it, but I have not write permission... What can I do to make it works???
Marco

---

### Post by lorap on 2005-04-11
hi mila!
that's the problem.
as soon as you've a ntfs system,there's still no released kernel to write to ntfs partitions.the versions available aren't still the stable ones.so i don't propose you deal with them.
have a nice day!
pavel

---

### Post by mila80 on 2005-04-11
So I can't use my hd both with ubuntu then in windows???
And if I use Horay and not warty can I solve my problem???
Marco

---

### Post by lorap on 2005-04-13
hi marco!
nope,it's still unsafe to make any changes to ntfs partitions from linux.
there's a possibility but it's unsafe.
have a nice day!
pavel

p.s.:
if it's at your home you can marco just reinstall windows and format it as fat32.
i'd the same problem some time ago.now i just don't run windows anymore.
but if it's at your work,them it wouldn't be a good idea to play with the fire :-)

---

