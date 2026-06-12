---
title: "Grub &amp; Windows XP"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by ubseamus on 2009-06-28
Hi guys,

I'm new to the ubuntu family. Exciting...

Anyway. I have a new 64bit notebook from MSI & I'm running Ubuntu 9.04. The machine came with Vista, & I installed 8.04 along side vista & was booting both for a while. I also loaded XP64 and wanted to upgrade to ubuntu 9.04. Did a clean install not an upgrade & I also wanted to get rid of vista & ubntu 8.04. So I deleted the partitions for what I didn't want & added a new one for Ubuntu 9.04.

Grub is loading Ubuntu, but it doesn't see XP. The partition is still there & I can mount it from Ubuntu, but I can't boot in XP. 

Can I setup grub to load windows with my current setup? or is this going to call for an os install again?

Thanks guys, hope sombody can help?

):P

---

### Post by Saint_ on 2009-06-28
Yeah, do this by going into the terminal and typing ```
sudo kate /boot/grub/menu.lst
```From there scroll to the bottom of the file and put the following after ### END DEBIAN AUTOMAGIC KERNELS LIST
```
**title Windows XP** 
**root (hd0,1)** 
**makeactive** 
**chainloader +1** 

```

Now reboot and hit ESC when the grub boot loader launches and you'll see Windows XP at the bottom of the list.

Edit: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

That's the url with step by step instructions along with pictures, just incase ya need it.

---

### Post by merlinus on 2009-06-28
Since the OP is running ubuntu, better do this:

```

gksudo gedit /boot/grub/menu.lst

```

Also, to be certain which partition xp is on, post results of:

```

sudo fdisk -l

```

---

### Post by telescopic on 2009-06-29
I want to join in. I had similar problem as Ubseamus. The worst is that the xp partition (drive) does not even appear in Ubuntu. How to mount the XP partition in command line of Ubuntu? I tried following 1): 

mkdir /media/window
mount -t ntfs /dev/sda1 /media/window

it gives:

''Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around? ''

2) I also corrected the menu.lst file, as I reboots in Grub, and choose to load XP, it gives error message:

"Error 13: Invalid or unsupported executable format"

3) I tried the XP recovery disk, get a F:\windows prompte, execute "fixmbr" then reboot. It just comes out the word 'Grub' at left upper corner and stops.

What can I do to at least to retreive some files from my XP partition? 

:KS

---

### Post by merlinus on 2009-06-29
IIRC, mount commands need to be prefaced with sudo, e.g.

```
sudo mount -t ntfs /dev/sda1 /media/windows
```Also, does the partition show up with gparted?

And what are the results of:

```
sudo fdisk -l
```

---

### Post by telescopic on 2009-06-29
XP was in /dev/sda1. When I install Ubuntu and was asked to install Grub, I went ahead even XP window is not on the list of detection. 
Under reboot, the Grub gives me option to load Ubuntu and it works fine; it has no option to load XP. So I change the /boot/grub/menu.lst file as mentionned above. I reboot again with XP option. It does goes back to the Grub list.


1) use XP recovery disk and get to F:\window and run "fixmbr", and reboot, It stops with a Grub prompt. So I have to use Xubuntu alternative CD to get back the Grub list.


2) I had some experience with Gparted before. This time, I run Gparted live-cd and it did not load the program, as there is lot of error on hda or hd0 something during the loading process. I think it fail because not recognizing the /dev/sda1


3)So, Xubuntu works well but cannot mount the /dev/sda1 where my XP sits.



Here is some info.

root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8142    65400583+   7  HPFS/NTFS
/dev/sda2   *        8143        8148       48195   82  Linux swap / Solaris
/dev/sda3            9599        9729     1052257+  d7  Unknown
/dev/sda4            8149        9598    11647125   83  Linux

Partition table entries are not in disk order

root@ubuntu:~# cd /media/window
root@ubuntu:/media/window# cd /

root@ubuntu:/# sudo mount -t ntfs /dev/sda1 /media/window
"Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"



grub> find /boot/grub/stage1
 (hd0,3)

4)Does above mean Grub stage1 is in /dev/sda3 ? I am not sure what is in /dev/sda3, would the MBR sits at there? or, MBR has to be in /dev/sda1?


5) I will try Super Grub disk later, but I doubte it would help. I just want at least to retrieve some files from XP partition.

Appreciate any suggestion.

---

### Post by merlinus on 2009-06-29
One problem I can inmmediately see is that there is a boot flag on your swap partition.  It needs to be on sda1 in order for xp to boot.  Linux does not need boot flags.

May I suggest you run from the live cd, open gparted, and change the boot flag.

The other thing is that you must create the mountpoint for sda1 first.

```

sudo mkdir /media/windows

```then

```

sudo mount -t ntfs /dev/sda1 /media/windows

```

---

### Post by GrandpaK1939 on 2009-06-29
I  have a Dell 1525 laptop running Vista.  I installed Ubuntu 9.04 in a previously partitioned portion of my drive.  It worked well.  At some point it malfunctioned.  I could not fix it so I uninstalled it.  I tried Xubuntu.  It worked well so I thought I would uninstall it and tried to redo Ubuntu.  
Now I get a dual boot screen.  When choosing Ubuntu, I get a sent to grub> .  From there I get the message that grub/root/stage1 does not exist.  I have tried several installs and online proposed fixes.  None seem to work reporting various files missing and error notes.
I am currently downloading a new copy in order to try to redo the whole thing.
Any ideas. (other than I seem to be a bit flakey)?
LeRoy 
[email]grandpak1939@charter.net[/email]

---

### Post by telescopic on 2009-06-29
[ATTACH]119388[/ATTACH]


I run gparted inside Xubuntu, i believe it works the same. The first thing appears is the message: Fail to mount "1G volumne".

I chose "manage flags" , so now the boot flag move to /dev/sda1

[ATTACH]119389[/ATTACH]
 
The info on the /dev/sda1 show the partition can not be mounted.

Close the program and reboot, XP still won't boot.

:KS

-Telescopic

---

### Post by telescopic on 2009-06-29
@GrandpaK1939,  twice I messed up with the Grub boot, and stalled at Grub>, I booted with the _Alternative-cd_ where there is an option of Recovery. Then it asks you where to make a /root drive. I tried by error to choose anyone from the list as /root until it accepts. Then it gives you option to re-install Grub. This at least fix the Ubuntu option at reboot.

---

### Post by ubseamus on 2009-06-30
Thanks for the info guys.

Didn't have much look tough. 

I ran fdisk & got:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7825fcd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6972    56002558+   5  Extended
/dev/sda3           27879       38914    88638464    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5               1         498     4000122   82  Linux swap / Solaris
/dev/sda6             499        6972    52002373+  83  Linux


So it looks like XP is on /dev/sda3 as it is the only NTFS dir, But I was not sure if I should be using "Id" or "Device" as root root in menu.lst so I tried a few different combinations....

title Windows XP (hd0,7)
root (hd0,7) 
makeactive 
chainloader +1

title Windows XP (hd0,3)
root (hd0,3) 
makeactive 
chainloader +1

title Windows XP (hd3,7)
root (hd3,7) 
makeactive 
chainloader +1

title Windows XP (hd3,1)
root (hd3,1) 
makeactive 
chainloader +1

all returned "Error, no such partition"

What did I do wrong?

& what is that cylinder boundary message? Is it because there is still some unpartitioned space on the disk?

Thanks

---

### Post by merlinus on 2009-06-30
title Windows XP 
root (hd0,2) 
makeactive 
chainloader +1

Also, try removing the boot flag from sda1 and activating it on sda3.

---

### Post by ubseamus on 2009-07-21
Thanks Merlin,

I think that worked to find the partition, but still not loading windows. "NTLDR is missing"  :(...

That says to me Windows is broken. Any Ideas?

Sorry for being two weeks, busy, busy, busy, but help is appreciated.

---

### Post by merlinus on 2009-07-21
Try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

It can fix the NTLDR problems.

---

### Post by ubseamus on 2009-07-21
Sounds good,,

anybody got a blank CD i can use  ;)

---

### Post by oldfred on 2009-07-21
You seem to have installed Windows into an extended partition. Windows should really only be installed in a primary partition.

A previous thread has this info, Herman has an answer #17 that may be a solution for you.
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

---

### Post by ubseamus on 2009-07-25
I could not figure out how to fix the NTLDR problem on the existing installation, & I was getting tired of messing with it, so I repaired XP using the installation cd. I was unsure what would happen to GRUB after doing this, & as I feared, the machine booted windows directly [without grub] & I could not load Ubuntu.

Using the supergrub cd I burned from [http://supergrubdisk.org]("http://supergrubdisk.org/") [thanks Merlin], I was able to reinstall grub & after an edit to boot/grub/menu.list I can now load XP & Ubuntu as wished.

Thanks everybody, problem solved =D>

---

