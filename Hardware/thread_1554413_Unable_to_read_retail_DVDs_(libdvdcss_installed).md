---
title: "Unable to read retail DVDs (libdvdcss installed)"
date: 2010-08-16
forum: Hardware
---

### Post by nicebloke on 2010-08-16
Hi,

I have a problem where I am unable to even mount any store purchased DVDs (both game and film). I can hear the drive trying to read the disc, but it just gives up after a few attempts.

I've looked in /var/log/messages and can't see anything that says the read was even attempted. If I put any burned DVD (backups obviously) ;) it reads them just fine and I can watch movies and play games.

I'm not sure which info you need, but here is some:



root@grubber:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=79917791-57f9-43c6-a2f1-cbb495a86134 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a630166c-7122-4638-b07f-6cfb3e076de1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /home/nicebloke/Downloads        ext3    defaults        0       0

root@grubber:~# uname -a
Linux grubber 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

I'm running 64bit 10.04. My drive is a Sony Optiarc AD-7200A with the latest firmware.

I've run /usr/share/doc/libdvdread4/install-css.sh  (but I don't think that's the problem).

Any help would be great. Thanks in advance,

---

### Post by Nick_Jinn on 2010-08-16
In Mint its not a problem but in regular Ubuntu you have to install Medibuntu.

[http://medibuntu.org/](http://medibuntu.org/)

Directions are simple. Run the commands and you can watch DVDs.



I dont know when Ubuntu is going to get with it and add it to Multiverse. 



Alternately you can probably add the repository and add the files from Synaptic.

---

### Post by nicebloke on 2010-08-16
Hi, 

Thanks for responding so quickly, however I already have the Medibuntu repository added already using those instructions.

---

### Post by Nick_Jinn on 2010-08-16
You installed the whole thing or just libdvdcss? I believe there are 2 or more files you might need but I could be mistaken since Im not really a geek. I know everything always works in Mint.

What player are you using?

---

### Post by nicebloke on 2010-08-16
I followed the instructions on this page: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I ran the big command under "Adding the Repository" and let it update everything it needed to. I then ran the amd64 commands under the sections "Playing Encrypted DVDs" and "Playing Non-Native Media Formats".

I'm using VLC, mplayer and xine. None of which can access the DVD because its not even being recognised. I'm assuming that even if I didn't have libdvdcss installed the DVD would still be mounted.

If you think I've missed installing something, let me know and I'll try it.

---

### Post by Nick_Jinn on 2010-08-16
I use Linux Mint and DVDs work out of the box every time. Its one less headache. Otherwise its a near clone of Ubuntu with some useful tweaks.


Did you also install Win32 or Win64 codecs or just Libdvdcss?

---

### Post by ericartman on 2010-08-16
I have been using quickstart for years now.
[http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop)
, yeah I can do it by hand but Im too lazy. Oh and it works in 64 and 10.04

Cart

---

### Post by Nick_Jinn on 2010-08-16
Is that going to help him watch DVDs?

---

### Post by nicebloke on 2010-08-17
I've installed the codecs as directed in the instructions. However, I doubt very much is a dvdcss problem because the drive doesn't read purchased game DVDs either.

I'm guessing its something hardware related, which is why I posted in this category and not the media one.

(this morning I have removed all the Medibuntu stuff and reinstalled it all, just in case)

@ericartman Thanks for the info, but I don't think it'll help in this case.

---

### Post by hansdown on 2010-08-17
Hi nicebloke.

You may need this.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by nicebloke on 2010-08-17
Hey thanks for the tip.

Sadly, "ubuntu-restricted-extras is already the newest version." :(

---

### Post by Nick_Jinn on 2010-08-17
Does it even recognize that there is a disk in your optical drive? Can you browse the files like its a folder?

---

### Post by Automat2 on 2010-08-17
> **Nick_Jinn said:**
> Does it even recognize that there is a disk in your optical drive? Can you browse the files like its a folder?
Not in my case. I have my primary drive unable to read/mount any CD or DVD. Ubuntu detects de drive  but not the disk inside any more.

---

### Post by Nick_Jinn on 2010-08-17
Thats a problem. It should at least be able to detect it even if it cant play or execute it.



You dont happen to have an external optical drive do you? I have 2 optical drives in my desktop. I wonder if you could try playing it while running Mint main edition from CD. Otherwise you could use a USB drive to free up the optical drive. I suggest mint because DVDs should work out of the box. 


If that doesnt work, it must be hardware related.

---

### Post by nicebloke on 2010-08-17
> **Nick_Jinn said:**
> Thats a problem. It should at least be able to detect it even if it cant play or execute it.

Exactly, that's my problem - its not detecting there is anything in the drive. But, that's only with original discs.

I should be able to get hold of a second drive tomorrow which I'll put in the PC along side my one to see if discs can be read in that one. I'm just surprised that there are no logs anywhere (that I can find) saying it can't read the disc.

---

