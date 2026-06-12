---
title: "DVD filesystems not mounted."
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by Armagguedes on 2006-04-27
Hello.


         _**SUMMARY:**_ i can't read burned data discs (CD/DVD) when encoded with **ISO9660** and the **Joliet** filesystem extensions. Below i will try to detail my problem the best i can.

   I have this god-awful annoying problem, that is seriously screwing my Kubuntu (Dapper) experience and that, if i recall correctly, affected Kubuntu Breezy as well. I'm currently running a fully-updated Kubuntu Dapper Drake, doing daily updates and Ctrl-Alt-Backspace'ing after each update.

   Hardware-wise, i'm on an _Acer Travelmate 4002WLMi_, with a _Pioneer DVR-K14RA_ disc drive, being it a single-layer-only DVD-R/+R/+RW drive with gay write speeds - 4x - for both formats (burns 4x and 8x media at 4x and 16x media at 2x for some reason).

   Now, onward with my (**serious**) problem.

   I burn all my DVDs from my WinXP box with Nero 6 in the absolutely standard ISO9660 filesystem, with the Joliet extension (to allow bigger filenames, and wtv), with "_No Multisession_". "_*Rock Ridge* extensions_" and "_*Joliet* extensions_" are generated, but "_UDF structures_" are not. "_ISO level_" is set to "_3_".  

   Because of said write-speed problem on my laptop, i avoid burning stuff here, but when i do, i use "_Untranslated ISO9660_" and "_103 character Joliet filenames_" in k3b. However, this is where the proverbial feces hit the fan. I have k3b set to "_Verify written data_". After burning, when said verification begins, k3b stops it and returns an error, ejects the disc tray, saying it can't access the disc. UPDATE: apparently the disc /can/ be accessed, i just need to way a bit (~30sec?) in order to let the disc become "available" (?).

   Regarding "non-home" media, my _Painkiller Black Edition_ (it's a DVD, "legal", bought from a store, and previously installed here under XP), is accessed, though it failed once (i'm assuming user error). Other "_oficial_" discs are opened with no problems whatsoever, and burned _CDs_ (of any kind apparently) have no problems as well. Burned games, whether from *.ISO's or some that i unpacked from ISO files for some reason or another and then burned onto CD or DVD (not as *.ISOs, but rather dragging and dropping) are accessed as well.

   As far as i can tell, it seems only burnded data DVDs with video files (for backups of anime and such, which also include checksum files and occasionally music files) seem to be unreadable, and i'm completely at a loss of what the problem might be. I HAVE NO IDEA WHAT IS WRONG WITH MY COMPUTER. My WinXP installs have never had any problems.

   Also, i've burned a Dual Layer disc, and i know it works, with the ISO for Command & Conquer: the 1st Decade. When i insert that thing into my laptop (to install w/ WINE), i get this error:[INDENT]Could not mount device.
The reported error was:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

[/INDENT]   I was advised to manually mount the drive/disc, instead of using automount, using the following commands:[INDENT]sudo mkdir /mnt/cdrom
sudo mount -t iso9660 /dev/hdc /mnt/cdrom
(assuming /dev/hdc is your CD/DVD drive...)
df[/INDENT]   This returned an error:[INDENT]mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/INDENT]   As you can see, it's the same error i get with automount.

   Like i've said, i'm completely beffudled as to what might be going on here under the hood. Can someone please help me? I'm kinda desperate here.
   Thanks in advance.

---

### Post by taurus on 2006-04-27
Instead of using automount, try to see if you can mount the CD/DVD from a terminal as (Applications -> Accessories -> Terminal),
```

sudo mkdir /mnt/cdrom
sudo mount -t iso9660 /dev/hdc /mnt/cdrom
(assuming /dev/hdc is your CD/DVD drive...)
df

```

---

### Post by Armagguedes on 2006-04-28
(added to first post for clearance and stuff)

---

### Post by Armagguedes on 2006-05-01
(added to first post for clearance and stuff)

---

### Post by fguizar on 2006-05-02
I am a newbie and just added a DVD-ROM.  I have the same error and get the same error message when I try to mount by hand. I am using a Samsung DVD-ROM SD-612. Any ideas how I should proceed.

I used hdd instead of hdc because Totem referred to it as hdd but I got the same error nonetheless.

---

### Post by frootstripe on 2006-05-10
Hi,

I'm having the exact same problem as Armagguedes. Any help, suggestions would be greatly appreciated.

---

### Post by jonsson on 2006-05-10
Any solutions yet? I've had this problem for a while on my fully updated Kubunty Breezy system. At first, everything I threw at it was auto mounted, then nothing was auto mounted and now it auto mounts USB disks but not CDs or DVDs. CDs can be mounted manually but not DVDs. I get the same error as above.

---

### Post by Armagguedes on 2006-05-10
Still no info.

I'm thinking of digging up my Linux-questions.org account and check there (though i'll only do this during the weekend).

---

### Post by TrinitronX on 2006-05-13
hmm... i just magically managed to mount a data dvd (udf filesystem).
Here's what I did:
```
sudo mkdir /media/dvd
sudo mount -t udf /dev/dvd/ /media/dvd
```

Maybe when a dvd is in the drive, hdc and /dev/cdrom don't work... and instead /dev/dvd must be used?
Perhaps this is due to how the drive must access the actual media... cds and dvds must be read using different devices?

If your disk is iso9660, try substituting it in the mount command for 'udf'.

I'll also try adding a line to my fstab to see if automount works with these.

---

### Post by jonsson on 2006-05-15
Nope, does not work here. :-(

---

### Post by Armagguedes on 2006-05-19
TrinitronX's post did not work for me.

I checked out IRC, namely #ubuntu's official channel.

To solve the problem, do "sudo nano /etc/fstab".

Search for your cdrom/dvdrom device(s) and in the "<type>" column,
replace what you've got there with "auto" (i had "udf,iso9660").
It should look like this:

/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

Please note that stuff like "user" or "noauto" actually belong to the "<options>" column, but the formatting is all over the place.

[Credits to ompaul @ #ubuntu, for editing this post to make it clearer and with more info and to Kyral, for actually giving me the answer (and to putting up with some n00bity).]

---

### Post by jonsson on 2006-09-16
Aargh! I gave up on this a while ago and yesterday I did a complete reinstall (for other reasons) and now have a fully updated Kubuntu Dapper system. And I still cannot read DVDs! :mad: 

CDs work fine. :confused:

---

