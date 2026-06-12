---
title: "editing   &quot;/boot/grub/menu.lst&quot;   to dual boot vista"
date: 2008-11-17
forum: General Help
---

### Post by Glace on 2008-11-17
I'm a noob so sorry in advance.

I have two sata HDDs, one with vista and now one with ubuntu.
I can no longer boot up in Vista since installing ubuntu, vista is on the hard drive called "sda1".

I tried adding the following to /boot/grub/menu.lst
```

title        Vista
root         (sd0,0)
chainloader  +1
```

It says
Error 23: Error while parsing number

I suspect (sd0,0) is not what I was suppose to put in, how can I fix this?

---

### Post by rakris on 2008-11-17
```
title vista
rootnoverify (sd0,0)
makeactive
chainloader  +1
```

try this :O

---

### Post by Glace on 2008-11-17
It still retuns the same error

---

### Post by philinux on 2008-11-17
Post the output of this.

[FONT=Trebuchet MS]sudo fdisk -l[/FONT]

---

### Post by jesuisbenjamin on 2008-11-17
I also have dual boot with Vista, installing went fine though.
Here is a copy of the end of my menu.lst, it may help you fix that although we may not have the same partition distribution, so watch out. Don't forget to backup your menu.lst before you make changes.

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a48f2bb1-d10f-4b53-80d1-3d4e97a7e9ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a48f2bb1-d10f-4b53-80d1-3d4e97a7e9ff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a48f2bb1-d10f-4b53-80d1-3d4e97a7e9ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a48f2bb1-d10f-4b53-80d1-3d4e97a7e9ff ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a48f2bb1-d10f-4b53-80d1-3d4e97a7e9ff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

---

### Post by Glace on 2008-11-17
(Vista is installed on the 500 GB)

$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3bad3ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9d5531f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38157   306496071   83  Linux
/dev/sdb2           38158       38913     6072570    5  Extended
/dev/sdb5           38158       38913     6072538+  82  Linux swap / Solaris

---

### Post by Glace on 2008-11-17
jesuisbenjamin, if i copy yours i get a no such partition error, and if i replace (hd0,2) with (sd0,0) I get the same as the original error

---

### Post by jesuisbenjamin on 2008-11-17
> **Glace said:**
> jesuisbenjamin, if i copy yours i get a no such partition error, and if i replace (hd0,2) with (sd0,0) I get the same as the original error

i am afraid i am not qualified enough to help you further, i suspect sd0 i not the correct syntax but rather hd0.
i'll be watching this thread and hope to learn along ;)

---

### Post by neu2buntu on 2008-11-17
try    (hd0,0)

---

### Post by neu2buntu on 2008-11-17
just realised your bootloader is on sdb...so i think (hd1,0) should do the trick

---

### Post by philinux on 2008-11-17
> **chrissy.mc.1@hotmail.co.u said:**
> try    (hd0,0)
+1 replace sda with (hd0,0) in your grub.

At least sda1 it's shown as bootable thats the *. Also looks better with code tags around it. more readable.
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3bad3ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9d5531f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38157   306496071   83  Linux
/dev/sdb2           38158       38913     6072570    5  Extended
/dev/sdb5           38158       38913     6072538+  82  Linux swap / Solaris
```

---

### Post by Glace on 2008-11-17
> **chrissy.mc.1@hotmail.co.u said:**
> try    (hd0,0)
it give the error "NTLDR is missing"

---

### Post by Glace on 2008-11-17
> **chrissy.mc.1@hotmail.co.u said:**
> just realised your bootloader is on sdb...so i think (hd1,0) should do the trick
It gives "Error 13: Invalid or unsupported executable format"

---

### Post by neu2buntu on 2008-11-17
its been so long since i have dual booted ubuntu and vista, i did it all on the same hdd.....  im a bit of a noob also.....    because you are using 2 hdd it may be that you dont need the chainloader option...  and i think the grub boot loader needs to stay on the linux partition...let me know how u get on anyway...

---

### Post by Glace on 2008-11-17
Tried all of the above w/o the chainloader, it does nothing.
I think the boot loader is on the linux partition

---

### Post by Glace on 2008-11-17
Tried all of the above w/o the chainloader, it does nothing.
I think the boot loader is on the linux partition

---

### Post by neu2buntu on 2008-11-17
print nout the output of command: sudo fdisk -l 
please

---

### Post by TeXtonyx on 2008-11-17
Quote:
Originally Posted by [email]chrissy.mc.1@hotmail.co[/email].u View Post
try (hd0,0)
----------------------------
it give the error "NTLDR is missing"

-------------------

That means you have the correct root entry (hd0,0) = sda1
Sometimes a more complex entry involving "map" is needed. 

title Windows Vista
root(hd0,1))
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

You could try the above first before proceeding to stronger measures.

------------------------------------------

I have Vista on sdb1, which has a more complex entry:
# on /dev/sdb1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

That entry actually is working for me but my Vista is on the second 
drive. So it needs to be edited for the first drive which I presented first.

------------------------------------------------

Because that is a windows error message, so grub has connected
to the Windows bootloader = ntldr
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

If you have a Vista install cd/dvd you can run Startup Repair.
[http://www.besttechie.net/forums/Vistas-System-Recovery-Console-t12840.html](http://www.besttechie.net/forums/Vistas-System-Recovery-Console-t12840.html)

If you don't have a Vista install cd you can download a rescue cd
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Make sure Vista boots up ok. You can download Easybcd which is
an easy to use boot manager for Vista. Run Easybcd and add 
Ubuntu under its Linux add OS window. Vista has been reinstalled
to the MBR replacing Ubuntu's grub installed to the MBR.
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) has pictures

If Easybcd doesn't work or you prefer the grub boot menu options,
then you can reinstall grub to the MBR. This will add Vista to
the Ubuntu grub boot menu. Vista will likely work this time around. 
My practice is to install grub to the Ubuntu /boot partition (sdb1)
before I run Easybcd in order to add Ubuntu to the boot menu.

---

### Post by philinux on 2008-11-17
I'd give the supergrub disk a go.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by jesuisbenjamin on 2008-11-17
[I]Hey guys, i've been watching this thread so as to learn along. Could you explain what hd and sd are? i am getting confused about the two to be honest...
Thanks[/I]

---

### Post by caljohnsmith on 2008-11-17
Glace, to help clarify your setup, please post the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one. The above output will determine which is your correct Grub entry for booting Windows, and also whether you are missing your Windows boot files.

---

### Post by neu2buntu on 2008-11-17
this is confusing for me too... but having tried to dual boot before i believe...

(hd0,0) = sda1
so this is the first hard drive and first partition

(hd0,2) = sda3
and this is also the first hard drive,but the third partition

where if you have usb drive plugged in this wouldbe.... (hd1,0) or sdb1   and if this usb has seperate partitions(say for swap) then  they would be  (hd1,1) or sdb2           .do you see the idea

---

### Post by Glace on 2008-11-17
> **caljohnsmith said:**
> Glace, to help clarify your setup, please post the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one. The above output will determine which is your correct Grub entry for booting Windows, and also whether you are missing your Windows boot files.


Like this: ?
```
glace@glace-main:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
glace@glace-main:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

glace@glace-main:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
glace@glace-main:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
0000

glace@glace-main:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy
glace@glace-main:~$ ls -l /mnt
total 4499335
-rwxrwxrwx 1 root root         24 2006-09-19 07:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-11-17 21:53 backups (.tib)
-rwxrwxrwx 3 root root         10 2006-09-19 07:43 config.sys
drwxrwxrwx 1 root root       4096 2008-11-17 22:01 documents
drwxrwxrwx 1 root root          0 2006-11-03 00:00 Documents and Settings
drwxrwxrwx 1 root root       8192 2008-11-18 01:41 games
drwxrwxrwx 1 root root       4096 2008-11-17 19:03 game stuff
-rwxrwxrwx 1 root root 2146623488 2008-11-18 06:04 hiberfil.sys
drwxrwxrwx 1 root root       4096 2008-11-18 01:37 installers
drwxrwxrwx 1 root root          0 2007-12-16 15:03 Intel
drwxrwxrwx 1 root root      45056 2008-11-17 11:50 movies
drwxrwxrwx 1 root root       8192 2008-11-17 17:59 music
drwxrwxrwx 1 root root       4096 2008-11-17 12:12 notes
drwxrwxrwx 1 root root          0 2008-11-18 02:00 other
-rwxrwxrwx 1 root root 2460549120 2008-11-18 06:04 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-11-17 21:51 pictures
drwxrwxrwx 1 root root       4096 2008-11-08 13:43 ProgramData
drwxrwxrwx 1 root root      12288 2008-11-17 10:30 Program Files
drwxrwxrwx 1 root root          0 2007-12-22 09:21 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-01-01 04:45 RECYCLER
-rwxrwxrwx 1 root root        575 2007-12-16 14:01 RHDSetup.log
-rwxrwxrwx 2 root root        268 2008-11-11 19:24 sqmdata00.sqm
-rwxrwxrwx 2 root root        244 2008-11-11 19:24 sqmnoopt00.sqm
drwxrwxrwx 1 root root       8192 2008-11-17 15:44 System Volume Information
drwxrwxrwx 1 root root       4096 2007-12-22 09:21 Users
drwxrwxrwx 1 root root      28672 2008-11-18 06:04 Windows
glace@glace-main:~$ 

```

btw nearly finished downloading the recovery disk, I'll tell everyone how it goes.

---

### Post by caljohnsmith on 2008-11-17
EDIT: Thought Glace had XP when it really was Vista, so deleted this post as irrelevant.

---

### Post by mab1376 on 2008-11-17
I doubt you'd want to re-install but all i had to do was install the bootloader on the vista drive/partition and it recognized it fine and works.

---

### Post by Glace on 2008-11-17
TeXtonyx's method of using the vista restore cd worked!
After following the prompts from the cd ubuntu was still the default os but selecting vista now works too.

Thanks everyone for the quick replies and the help.  
:)

---

### Post by jesuisbenjamin on 2008-11-17
Hurrray! Let's mark this thread as solved! ;)

:D

---

