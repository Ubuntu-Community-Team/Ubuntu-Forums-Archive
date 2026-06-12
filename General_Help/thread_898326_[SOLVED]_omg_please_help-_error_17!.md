---
title: "[SOLVED] omg please help- error 17!"
date: 2008-08-23
forum: General Help
---

### Post by Garratt on 2008-08-23
**_issue solved using super grub disk --> and searching super grub forums_**


I just reinstalled Ubuntu using live cd, the comp is dual boot with vista, i selected the correct HDD partitions and everything, exactly the same install as i did when i first installed ubuntu.

only this time on restart when i get to grub and select ubuntu i get error 17: Unable to mount partition.

so i freak out grab the alternate disk and insert that, restart and do an install using alternate, check the ubuntu hdd tell it to delete partitions reformat, blah blah and set up new partitions.

install, restart, get to grub and choose ubuntu, error 17: unable to mount partition... i choose vista longhorn, error 13:unsupported format

what the hell did i do?, the install cd's can see that i have a windows partition on the 600gb HDD, and I partition on the 80g normal ubuntu setup...

so this is all because grub doesn't like to be reinstalled? whats the deal?

---

### Post by meindian523 on 2008-08-23
Run a filesystem check on your partitions.Verify whether the root (hdx,y) for each of your OSs is correct.

---

### Post by Garratt on 2008-08-23
huh?
i cant do ****

i got grub boot loader, if you know commands for it can you please list them here

---

### Post by Garratt on 2008-08-23
ok the ubuntu root is (hd1,0)
kernal /boot/vmlinuz-2.6.24-19-generic root=uuid=fiw3eqnbt34 etc
intrid /boot/intrid.img-2.6.24-19-generic

vista is:

root (hd0,0)
savedefault
makeactive
chainloader +1


im guessing it's not correct seeing as it doesn't fkn work

but wat is correct? or how am i supposed to figure that out

---

### Post by meindian523 on 2008-08-23
Where did you find that info from?/boot/grub/menu.lst?Post ```
sudo fdisk -l
```

---

### Post by Garratt on 2008-08-23
that info is just from hitting 'e' (edit) at grub boot loader while highlighted OS.

that command does nothing when i press 'C' to go into command line.

error: unsupported command.

im not using the same computer to type this obviously... 

so I am unable to get to any terminal interface from grub, as far as i know... 

i downloaded and burned to disk super grub, but i get the same errors.

i checked bios settings and it doesn't seem to display what the hdd settings are exactly, everthing is just set to auto.

---

### Post by caljohnsmith on 2008-08-23
Garratt, try booting up your Ubuntu Live CD, open a terminal, and do the following:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> geometry (hd0)
```
That will give us some useful info to help troubleshoot your problem.

---

### Post by meindian523 on 2008-08-23
e at the GRUB menu just gives the info as present,which is obviously wrong since your GRUB does not boot.Do what caljohnsmith said to provide more info.

---

### Post by Bucky Ball on 2008-08-23
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Go there, download the iso, make a disc, boot from it and there is a strong possibility it will work out the grub for you. Then once you are up and running you can learn more about how grub operates.

Or, you can go for a crash course in grub right now.

---

### Post by Garratt on 2008-08-23
how do i enter terminal via the cd?

i tried the option load from first boot drive, it seemed to load for about 5 mins and nothing was happening so i reset.

---

### Post by Garratt on 2008-08-23
> **Bucky Ball said:**
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Go there, download the iso, make a disc, boot from it and there is a strong possibility it will work out the grub for you. Then once you are up and running you can learn more about how grub operates.

Or, you can go for a crash course in grub right now.

been there done that...

---

### Post by meindian523 on 2008-08-23
Meaning you are not getting to the desktop?

---

### Post by Garratt on 2008-08-23
i entered via live cd, i get what you ment now duh :P


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7bf97bf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149902514    74951226   83  Linux
/dev/sda2       149902515   156360644     3229065    5  Extended
/dev/sda5       149902578   156360644     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87fd86ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1250260991   625129472    7  HPFS/NTFS
ubuntu@ubuntu:~$ 



       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find boot/grub/stage1

Error 15: File not found

grub> geometry (hd0)
drive 0x80: C/H/S = 9733/255/63, The number of sectors = 156368016, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub>

---

### Post by meindian523 on 2008-08-23
It's ```
find [Color="Red"]/[/COLOR]boot/grub/stage1
```
Please post the appropriate results.

---

### Post by Garratt on 2008-08-23
AHHH

it's  (hd0,0) 

i think thats the vista HDD eh?

---

### Post by meindian523 on 2008-08-23
Nopes,it's the Linux root partition.The problem is that your entries for Vista and Linux have got interchanged.Did you interchange your hard disks?If yes,interchange them back,if not,change Ubuntu in the menu.lst to read
> root    (hd0,0)
and the Vista entry to read
> root    (hd1,0)
Note that you will have to mount your /boot before you make any changes,otherwise you would be only editing the Live CD's menu.lst,which being in RAM is pretty useless for solving the problem.

---

### Post by Garratt on 2008-08-23
i typed in stage2 for shts and giggles, says same thing. now wat?


EdIT: ok so type in terminal sudo edit /boot/grub/menu.lst ?

ok so i go into the 80g drive and goto into the boot menu from there? will that save it?

---

### Post by Bucky Ball on 2008-08-23
If you're talking about super grub disk, you don't. Start computer, go into bios, set to boot from cd, insert cd, hit f10 to save changes and exit and you will boot from the cd which will take you to the supergrub GUI and take it from there. :)

Update: sorry, was looking at earlier post. :}

---

### Post by Garratt on 2008-08-23
thanks for your help bucky but like i have stated twice already super grub is a super pos, 

meindin knows what he is doing from the sounds of it.
i do appriciate your help tho.

---

### Post by Bucky Ball on 2008-08-23
Super pos? Not sure what that means, but good luck in your explorations. :)

---

### Post by Garratt on 2008-08-23
@ bucky:  super peice of shieeeet...
i went through every option in it to restore correct values and did  the file switch thingy it reccommends for dual HDD's but nothing worked...


--------------------------
@meindian: yea anyway, i go into menu.lst but it tells me i can't change it and i can't work out how to do it as root. or so that it will actually save!

---

### Post by meindian523 on 2008-08-23
File switch thingy?Do you need step-by-step instructions?

---

### Post by Garratt on 2008-08-23
no ignore what i said about super grub its godly i'm sure.(there was a hd switcher thingy inside super grub to do exactly what you are telling me to do...but it did not work).


yes i need instructions to save menu.lst, 

like i know how to do it just change vista to 1.0 and vice versa for ubuntu, but it tells me i cannot save as i do not have permissions.

---

### Post by meindian523 on 2008-08-23
You need ```
gksudo gedit /boot/grub/menu.lst
```
Are you sure you are editing the menu.lst on your hard disk,and not the one on the CD,that is have you mounted your / partition?

---

### Post by meindian523 on 2008-08-23
I got to go,so here are instructions for mounting your / partition,incase you haven't already done so:
```

sudo mkdir /media/slash
mount /dev/sdb1 /media/slash
gksudo gedit /media/slash/boot/grub/menu.lst

```
Then do the edits as mentioned above.

---

### Post by Garratt on 2008-08-23
ermm didn't work

i didn't get errors or anything, but the last line: gksudo edit /media/slash/boot/grub/menu.lst just dropped down to next line of command..


EDIT woops typo, supposed to be gedit :P

---

### Post by Garratt on 2008-08-23
ok so doing what you said, it kept opening up a blank menu.lst document, so i went into media/slash/ it is all my windows files


so that is obviously the wrong drive i need to enter what to change it? 

sudo mount /dev/sdb2 ? or sudo mount /dev/sdb0 ?

---

### Post by Garratt on 2008-08-23
i can not:$ unmount /dev/sdb1 /media/slash

bash: unmount: command not found

---

### Post by Garratt on 2008-08-23
ok so i just restarted cause i was getting problems...
and did fdisk again```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87fd86ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1250260991   625129472    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7bf97bf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   149902514    74951226   83  Linux
/dev/sdb2       149902515   156360644     3229065    5  Extended
/dev/sdb5       149902578   156360644     3229033+  82  Linux swap / Solaris

```

now it seems to be backwards wtf?

---

### Post by Garratt on 2008-08-23
WOHBOOOOO

fixed hopefully!

brb

---

### Post by Garratt on 2008-08-23
well it kinda worked...

i had to use super grub bootloader cd to load ubuntu.... seems grub has disapeared. alll i got at startup was a black screen with a cursor.

I'm hoping after i do all updates etc it will fix it. if not i can live with SBL in my cd drive.

---

### Post by Garratt on 2008-08-24
BUMP...


Grub still is not fixed, i tried sudo apt-get install grub, but i have the newest version...

should i do a remove/install in same session to see if that will fix it?

---

### Post by Garratt on 2008-08-26
This is my menu.lst it seems to have changed a bit cause i tried using QgrubEditor, but i think only comments have been edited out so should be ok...

for some reason this still is not working and im not sure why...
if anyone has any ideas let me know, cause looks to me like it should work!

```
default 0
timeout 20

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f47a88a8-6205-4a90-afb7-dc6c6c9548a7 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f47a88a8-6205-4a90-afb7-dc6c6c9548a7 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd1,0)
chainloader +1
savedefault
makeactive
```

...
```
garratt@ubuntu:~$ sudo fdisk -lu
[sudo] password for garratt: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7bf97bf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149902514    74951226   83  Linux
/dev/sda2       149902515   156360644     3229065    5  Extended
/dev/sda5       149902578   156360644     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87fd86ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1250260991   625129472    7  HPFS/NTFS
garratt@ubuntu:~$ gksudo gedit /boot/grub/menu.lst


```

...
```
   [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)

grub> geometry (hd0)
drive 0x80: C/H/S = 9733/255/63, The number of sectors = 156368016, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> 



```

---

