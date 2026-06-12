---
title: "Dual-booting problems..."
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by maxxag on 2006-02-02
Ok, so I wanted to dual-boot Ubuntu Linux and Windows. I tried just installing Ubuntu over my 80GB HDD that was inside my tower, but not part of my dual 120GB HDD RAID array (240GB comjoined by the RAID setup). Unfortunately, as I now realize a little late, the computer shop I bought my computer from set the 80GB HDD as the master HDD I believe, and the RAID array as a slave. However, that setup proved very strange.  Essentially, when I booted Windows, I was given the option to boot into the 80GB HDD, from which the RAID array wasn't even detected.  I also had the ability to boot from the RAID array, but could not execute/open files from the 80GB HDD. So, from time to time I would copy data from the 80GB HDD to the RAID array. I only accessed the 80GB hard drive occasionally, as it was the old HDD from my previous PC.

Today I was reading some literature on Slashdot that confirmed some of my suspicions about M$'s potentially dangerous ways, so I decided to install Ubuntu. However, I think I may have wiped out my MBR. I think the 80GB HDD had the MBR, and the Ubuntu install may have destroyed it. There is salvagable data on the other hard drives I think, but am not sure.

My computer specs are as follows:

AMD64 3200+ CPU
1GB DDR RAM
nVidia GeForce 6800GT

My goal is to either salvage my Windows install thats on the RAID Array; OR find a way to use the current Ubuntu install, salvage the Windows data, and use GRUB to choose which OS to boot from. If there are utilities to help in this, I know of none off hand.

---

### Post by Sutekh on 2006-02-02
[QUOTE=maxxag]
Today I was reading some literature on Slashdot that confirmed some of my suspicions about M$'s potentially dangerous ways, so I decided to install Ubuntu. However, I think I may have wiped out my MBR. I think the 80GB HDD had the MBR, and the Ubuntu install may have destroyed it. There is salvagable data on the other hard drives I think, but am not sure.

My computer specs are as follows:

AMD64 3200+ CPU
1GB DDR RAM
nVidia GeForce 6800GT

My goal is to either salvage my Windows install thats on the RAID Array; OR find a way to use the current Ubuntu install, salvage the Windows data, and use GRUB to choose which OS to boot from. If there are utilities to help in this, I know of none off hand.[/QUOTE]
Wiping out the MBR won't affect your data at all, the MBR is separate from the main part of the disc.  

If you have a Windows XP install CD, pop it in and choose recovery console(press R?).  When you finally get to a prompt
```

fixmbr
```
will put the windows bootloader on the MBR.


If you want GRUB on the MBR, pop in the Ubuntu install CD and follow this (top section);
[Ubuntu Wiki - Recovering GRUB]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")


OR pop in a Live CD; Ubuntu will do, Mepis I hear is good, and follow this;
[Ubuntu Forums - Howto Restore GRUB if your MBR is messed up]("http://ubuntuforums.org/showthread.php?t=24113") - posts 2 and 5 pertain to LiveCD use.

Keep in mind, the Windows bootloader won't help you out and list Ubuntu n its options, GRUB however will discover ALL OS's and allow you to choose which one you want to boot.

---

### Post by maxxag on 2006-02-03
Thanks for the help so far.

When Reboot my computer and try and select an OS from the GRUB menu, Windows isnt an option.  How can I add my windows install to that list? I would like to have both Ubuntu and Windows available at boot.  Thanks!

---

### Post by Sutekh on 2006-02-03
[QUOTE=maxxag]Thanks for the help so far.

When Reboot my computer and try and select an OS from the GRUB menu, Windows isnt an option.  How can I add my windows install to that list? I would like to have both Ubuntu and Windows available at boot.  Thanks![/QUOTE]

Too easy, allI need to know is the layout of your partitions.

If you type (in a terminal window)
```

sudo fdisk -l
```
we will be able to see where Windows resides.  Then we can edit the GRUB menu to reflect that.

---

### Post by maxxag on 2006-02-03
heres the results of that fdisk:


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9356    75152038+  83  Linux
/dev/hda2            9357        9729     2996122+   5  Extended
/dev/hda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29185   234428481    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by akiro.yamamoto on 2006-02-03
This is taken from my own set-up..... ;)
[QUOTE=akiro.yamamoto]
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/QUOTE]
So in your case you could probably use
root         (sd0,0) 
instead of (hd0,0) .
Hope this helps.

---

### Post by Sutekh on 2006-02-03
[QUOTE=maxxag]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29185   234428481    7  HPFS/NTFS

[/QUOTE]
Well sda1 looks lke WindowsXP (NTFS), strange how there isn't an asterisk for the 'Boot' option.

First you should backup the GRUB menu and device.map
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo cp /boot/grub/device.map /boot/grub/device.map_backup

```

Then edit the device.map - this tell GRUB how the devices are mapped (?!)
```

sudo gedit /boot/grub/device.map

```

You will need to add one line, hopefully there will already be one line that says
```

(hd0) /dev/hda
```
if so then add the following line

```

**(hd1) /dev/sda**
```
This tells GRUB that /dev/sda (the SATA disc) should be known as hd1

Then edit the GRUB menu in a text editor
```
sudo gedit /boot/grub/menu.lst
```
Then at the bottom of the menu.lst there should be a line that says

> 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

Then add the following lines
```

# GRUB Entry for WinXP
title		Microsoft Windows XP
**root		(hd1,0)**
savedefault
makeactive
chainloader	+1

```

Click you heels three times, throw some salt over your shoulder, I hope this gets it working.

Edit: akiro, I'm pretty sure root (sd0,0) won't work, hence the device.map which maps sda to hd1.  I could be wrong though.

---

### Post by maxxag on 2006-02-03
Thanks again, problem however:

I keep trying to put the first line into the terminal, but it dosent do anythig, it just returns the origional prompt, like this:

max@Max:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
max@Max:~$ sudo cp /boot/grub/device.map /boot/grub/device.map_backup
max@Max:~$

do you know whats happening?

Edit: BTW, I'm sorry, im a total newb at this, so bear with me.

Edit again:  the rest worked, i got into the grub options to the point where i can add the new boot options.  i havent done anything yet, but at least i can get to it.

in the first menue

"if so then add the following line

Code:

(hd1) /dev/sda"

that was already in the list... is this different than what you expected?

anyway, im not gonna do anything yet, so i await your response.

---

### Post by akiro.yamamoto on 2006-02-03
The mapping you specified I think is just the long way of doing the same thing.
As far as I know Grub views all the drives and the first PATA drive is hd0 similarly the first SATA is sd0. They are two separate entities! 
So from the mapping all your saying is " Listen let's call the 1st SATA drive hd1 instead of sd0 OK?!." ;)
Maybe I have it all wrong so i'll do some checking on it. ;)

---

### Post by Sutekh on 2006-02-03
[QUOTE=akiro.yamamoto]The mapping you specified I think is just the long way of doing the same thing.
As far as I know Grub views all the drives and the first PATA drive is hd0 similarly the first SATA is sd0. They are two separate entities! 
So from the mapping all your saying is " Listen let's call the 1st SATA drive hd1 instead of sd0 OK?!." ;)
Maybe I have it all wrong so i'll do some checking on it. ;)[/QUOTE]
On thinking about it I'm sure you're right.  I guess I like the extra formality!

---

### Post by akiro.yamamoto on 2006-02-03
That's correct!
The terminal will only give feedback for ERRORS!

---

### Post by Sutekh on 2006-02-03
[QUOTE=maxxag]Thanks again, problem however:

I keep trying to put the first line into the terminal, but it dosent do anythig, it just returns the origional prompt, like this:

max@Max:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
max@Max:~$ sudo cp /boot/grub/device.map /boot/grub/device.map_backup
max@Max:~$

do you know whats happening?

Edit: BTW, I'm sorry, im a total newb at this, so bear with me.[/QUOTE]
It's okay, you won't see anything.  If you want to check that the files where copied and backup, use the list command - ls
```

ls /boot/grub

```
And you should be able to see the original files; menu.lst, and the backup files; menu.lst_backup

---

### Post by maxxag on 2006-02-03
ok i added that new entry to the grub boot list, now i just save and reboot, correct?

---

### Post by Sutekh on 2006-02-03
Yep, when you reboot, you should have the option of Ubuntu and Windows.

---

### Post by maxxag on 2006-02-03
it didnt work, all it did was repeat the stuff we put in the boot list and then say "unknown file type" or somthign to that effect, i let it sit for liek 30 secs before i rebooted back into ubuntu

---

### Post by akiro.yamamoto on 2006-02-03
I found some info....

> Grub nomenclature is a bit different from all others AFAIK.  There's
> some explanation in the grub manual and I think in the Hurd install
> guide as well.  In short, grub uses the bios and therefore only knows
> about bios drives.  All hard drives are hd, and they are numbered by
> the bios.  So if you have (in Linux nomenclature) hda and hdc
> installed, then hda is hd0 for grub, and hdc is hd1.

GRUB will NOT recognize the sd0, ONLY the linux kernel and support system will recognize that. So to ensure reliable grub set-up you HAVE to USE the Device Map..... :smile:
I guess you learn something new everyday. ;)
Thanks Sutekh.
Akiro

---

### Post by maxxag on 2006-02-03
does the fact that its a raid array affect anything?

its raid0 btw

edit again: the sudo gedit /boot/grub/device.map thing that that command brought up ended up looking like this:

(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb

i dunno if this matters or not, just though ide throw in as much info as possable

---

### Post by akiro.yamamoto on 2006-02-03
Sorry I'm checking for win raid grub info.....

---

### Post by akiro.yamamoto on 2006-02-03
I just saw a little info.. it seems that you have to map grub to a raid set NOT to a partition. 
Check this out:
[http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Bios_(Onboard)_RAID](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Bios_(Onboard)_RAID)
Just info ;)

---

### Post by akiro.yamamoto on 2006-02-03
Some Light at the end of the tunnel ;)
It seems that someone else on this forum had a similar problem........
Check this out...
[http://ubuntuforums.org/showthread.php?p=115364](http://ubuntuforums.org/showthread.php?p=115364)
Check the links that TheGodFather has in his Sig......
I hope this helps ;)
Akiro

---

### Post by maxxag on 2006-02-03
i see... so i need lilo? or can i still use grub?  and how do i set this up?

---

### Post by akiro.yamamoto on 2006-02-03
No! Using a combination of the ideas posted you can use dmraid tools to map your raid partitions. Then use GRUB's map file to specify the partitions to boot from for each OS. 
So you could after the raid tools and device mapper software is installed:

#ls /dev/mapper
crw-rw----  1 root root  10, 62 Aug 22 01:35 control
brw-------  1 root root 254,  0 Aug 21 21:46 sil_afaidcaafaci

#cfdisk /dev/mapper/your_raid_set
and set it to type 83 for linux partition or 07 for NTFS

#dmsetup mknodes
To create the nodes else GRUB complains about unknow partitions

Edit grub device map and add something like...
hd0,0 /dev/mapper/your_raid_set1
hd0,1 /dev/mapper/your_raid_set2
This maps the raid set for GRUB.
Then modify the drub menu.lst to reflect where each OS boots from....

### Note ALL the info here is merely info I got from various sourcers specifically
### This site: 
[http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Bios_(Onboard)_RAID](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Bios_(Onboard)_RAID)
Which is a Gentoo Setup so BE AWARE YMMV....

Hope this helps point you in the right direction.
I've never had this problem, so this really is a best guess. 
Hence the vague directions ;) .

BTW: 
I'm assuming that your XP RAID 0 set-up was done using software tools, right?
Or did you use a hardware solution, this info might help us narrow it down.
Hopefully some Linux RAID Guru will step in and lend a hand...... :smile:

---

### Post by maxxag on 2006-02-03
keep in mind im nearly totally new at this... could you boil that down into some easy-to-follow instructions?  thanks!

---

### Post by akiro.yamamoto on 2006-02-03
I was browsing through the forums and came across this.:
[http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557)
If you follow this you can get through most of the prep work, then all you'll have 
to do is set-up grub properly.

---

### Post by akiro.yamamoto on 2006-02-03
Someone reported good results using the debian raid package instead of the
red-hat package. You can find it here:
[http://packages.debian.org/unstable/admin/dmraid](http://packages.debian.org/unstable/admin/dmraid)

Akiro

---

### Post by maxxag on 2006-02-03
how do i make dmraid load on startup?

---

### Post by maxxag on 2006-02-03
ok, my "activateraid" script has an error or so it says, heres the script:

dmraid -ay -v
mount -t <ntfs> -o users,owner,ro,umask=000 dev/mapper/<via_ddccdijegj> /</dev/sda>
mount -t <ntfs> -o users,owner,ro,umask=000 dev/mapper/<via_ddccdijegj1> /</dev/sdb>

and heres what it spits out:

max@Max:~$ sudo ./activateraid
RAID set "via_ddccdijegj" already active
INFO: Activating stripe RAID set "via_ddccdijegj"
RAID set "via_ddccdijegj1" already active
INFO: Activating partition RAID set "via_ddccdijegj1"
./activateraid: line 2: syntax error near unexpected token `newline'
./activateraid: line 2: `mount -t <ntfs> -o users,owner,ro,umask=000 dev/mapper/<via_ddccdijegj> /</dev/sda>'
max@Max:~$

sugestions?

---

### Post by akiro.yamamoto on 2006-02-03
those <what-ever> has to be replaced with info from your actual system!
They are only place holders. ;) . Also there is an error in that snippet of code it should read /dev/mapper not dev/mapper.. see the difference, that slash is VERY important.
so 
mount -t ntfs -o users,owner,ro,umask=000 /devmapper/<what you have on your system> /dev/<what you want to use>

---

### Post by akiro.yamamoto on 2006-02-03
Remove the < and > from your file ;)

---

### Post by maxxag on 2006-02-03
ok, so what do i put in "what i want to use?" the /dev /sda and /dev /sdb?

i know in the first set of blanks i put the drive numbers "the VIA_xxxx"

---

### Post by akiro.yamamoto on 2006-02-03
CODE:
dmraid -r 
or
ls /dev/mapper

You should see something like this:
via_xxx  -- the raw raid volume
via_xxx1 -- the NTFS partition
Then you put that in until you have somthing like this:

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/via_xxx1 /dev/hdb1

Then to find the geometry
fdisk -l /dev/mapper/via_xxx

Then start the grub console with:
grub
grub> device (hd1) /dev/mapper/via_xxx
grub> geometry (hd1) 9001 255 63

Then exit grub.
Now modify menu.lst in the /boot folder
Add your win system:

title Windows XP 
  rootnoverify (hd1,0)
  chainloader +1

save and exit.
For a more indepth look to setup this see this:
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

I hope this helps.
Akiro

---

### Post by maxxag on 2006-02-03
this is helping tremendously, thank you very much for your continued support.

a few questions:  what is the geometry in this, and whats the exact formatting i use to put it into grub?

Disk /dev/mapper/via_ddccdijegj: 240.0 GB, 240068246528 bytes
255 heads, 63 sectors/track, 29186 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                     Device Boot      Start         End      Blocks   Id  System
/dev/mapper/via_ddccdijegj1   *           1       29185   234428481    7  HPFS/N TFS
max@Max:~$

Does the grub consol mean i have to reboot then enter grub with esc?

Also, do i need to specify my drives as hd1, hda1 or one of the s-ones?  you make use of both hda1 and hd1 in your examples.

also can you specify EXACTLY what i need to put into the grub menu file? with formatting, i think formatting is where im getting stuck alot.

thanks!

---

### Post by maxxag on 2006-02-03
ok i get to this point and get this error:


    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> device (sda) /dev/mapper/via_ddccdijegj

Error 23: Error while parsing number

grub>

im at a loss

---

