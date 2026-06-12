---
title: "Grub2 and Windows XP Bootloader (NTLDR)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Sk1nnyMan on 2009-10-29
Hey,

I have a boot issue, basically I want to use grub2 from Windows XP's NTLDR boot loader.
First of all my system is as follows :

HDD 1 : Windows XP with NTLDR boot loader and Windows MBR
HDD 2 : Backup disk
HDD 3 : Ubuntu 9.10 with swap space

I installed Ubuntu 9.10 from a liveCD, I also opted to install the new Grub2 bootloader on the same disk as the root partition for Ubuntu 9.10.

Next I did a dd of the first 512 bytes of the Ubuntu partition and placed it on my Windows XP disk and edited my boot.ini so that it pointed to the correct path as an option for the NTLDR boot menu.

I can boot into Windows XP just fine, however when I try and boot into Ubuntu through NTLDR I get a black screen with the word GRUB in the top left corner.


I have spent the day googling how to fix this and have come up empty, someone please help!! 
I still have access to the disk itself through a liveCD.

---

### Post by Sk1nnyMan on 2009-10-29
Bump, since my post vanished almost instantly

---

### Post by Ghiepo on 2009-10-30
I have exactly the same problem; the first 512 byts of the Karmik partition seems empty, any help?

---

### Post by Sk1nnyMan on 2009-10-30
The first 512 bytes of the drive appear to contain the boot information, but the first 512 bytes of the root partition don't have anything in them.

Can anybody help? Or at least tell me it is impossible so I can think again?

---

### Post by Wizard13 on 2009-10-30
Same here! Xp is in /dev/sda1 and root partition of Karmic in /dev/sda6. The first sector of root partition seems empty. Any ideas how to make it work with NT loader?

---

### Post by Sk1nnyMan on 2009-10-31
I caved and installed Grub2 to the MBR and chainloaded it to NTLDR, now it works.

I don't consider this to be solved, I would rather have NTLDR doing all heavy lifting!

---

### Post by Mark Phelps on 2009-10-31
NTLDTR stands for Windows NT Loader, even though it also boots XP. Sorry, but NTLDR can't do all the "heavy lifting".  It simply has no way to boot other OSs.  

For example, the Wubi install creates a file inside MS Windows for Ubuntu, adds a line to the boot.ini file, and adds GRUB4DOS -- so that you can then use the MS Windows OS menu to select Ubuntu.

But ... and this is important ... NTLDR is NOT booting Ubuntu, the MS Windows loader entry is handing off control to GRUB4DOS -- and THAT is booting Ubuntu.

---

### Post by pft42 on 2009-11-11
Hi,

actually this Mark's post made me take the fnal step to register to this forum after using opensuse for years, being annoyed by reduced support cycles and thus starting to play with ubuntu.

Actually I have the same problem and was really upset about Mark's post.
While technically it is not wrong it is complete nonsense and off topic IMHO.

Of course you can boot any linux through NTLDR. The trick is chainloading, that is NTLDR calls grub because as it cannot boot linux directly.  (Mark, it is this small word you missed and that was actually never asked for).

Now the problem is that the typical procedure that worked so far for many linux distros (all?) does not work with karmic/grub2.

The "normal" procedure is to install grub boot sector to the partition and not the disk, i.e. /dev/sdxN instead of /dev/sdx (actally it is never used there, it is just to keep MBR untouched), then reading the boot sector from that partition into a file and give this file to NTLDR.

In karmic you get a warning that this is a bad thing (well - worked for years) and even worse it just does not write any boot code.
While there is plenty of hints I found not all worked.
Notably the trick to reinstall grub with the "--forced" option did not help.

The way that worked for me was this:

[LIST=1]
[*]boot karmic live CD
[*]read MBR to file1 (with dd, iniital 512 bytes of disk)
[*]mount karmic partition and /dev and chroot to it (hints how to do it without chroot did not work for me! so don't waste your time)
[*]reinstall grub, this time to MBR (!) ("grub-setup /dev/sdx" is enough)
[*]read MBR to file2
[*]reinstall MBR from file1
[*]give file2 to NTLDR (boot.ini)
[*]bingo
[/LIST]
Hope this brief description is fine for you - I didn't give exact commands. If not let me know.

My summary is that this is a dual pain and shame:
1. refusing correct work without an error message is fully unaaceptable;
2. the windos install behaviour to overwrite other boot code (like linux) was always considered very bad behaviour in linux community, so why does grub2 go that way now? Yes I know grub2 can boot windows as well but it is clearly bad behavior to touch q foreign system - and finally it is completely unecessary

---

### Post by blackhawk55 on 2009-11-15
> **pft42 said:**
> Hope this brief description is fine for you - I didn't give exact commands. If not let me know.

Hi,

Could you explain more detailed what you did in step 3?

---

### Post by pft42 on 2009-11-17
ok, here are the details on step3

I assume you have installed karmic on /dev/sda6 as its root partition and a separate boot partition on /dev/sda7 (otherwise omit line 2)
```
sudo mount /dev/sda6 /mnt
sudo mount /dev/sda7 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```and continue with step4
do not forget to exit chroot mode afterwards

---

### Post by sibble-comp on 2009-11-17
Okay, after fighting with this myself for the past few days, I thought I'd post some specfics on how to accomplish this,  since I've been messing about with this for the last 3 days, there may be a step or 2 missing, please report back if this doesn't work for you.

In my case this is on an Asus EEE PC netbook, with windows installed in

/dev/sda1
/dev/sda5
/dev/sda6

Unbuntu is installed in

/dev/sda7  (single root partition)
/dev/sda8 (swap)

Currently when machine is started it boots right into windows with no option for linux.

1) boot karmic live CD
no problem there, however I open a terminal and type "sudo -s" so I don't have to keep typing sudo before any of the commands below.

2)read MBR to file1 (with dd, iniital 512 bytes of disk)

I mounted a sdcard as /media/scdard1

dd if=/dev/sda of=/media/sdcard1/xp.mbr bs=512 count=1

note, to verify you have a proper file (my first attempts came out blank), run

xxd filename.mbr

it the result is all zeros you did it wrong, you should see lots of hex codes and in the asci text to the right you see mention of missing operating system and things like that.

3) mount karmic partition and /dev and chroot to it (hints how to do it without chroot did not work for me! so don't waste your time)

chroot is NOT necessary, however you will have to mount the root partition, in my case

mkdir /media/sda7
mount /dev/sda7 /media/sda7

NOTE: when a friend and I were looking at this, we found that the stage1, stage1_5 and stage2 files were missing from /boot/grub directory, I had to manually copy them (from memory) from /usr/share/grub, this might not be necessary.

4) reinstall grub, this time to MBR (!) ("grub-setup /dev/sdx" is enough)

based on #3

grub-install --root-directory=/media/sda7 /dev/sda[INDENT]Optional
if you reboot at this point, grub should come up, since I didn't have a menu.lst file setup, I had to type the following to load it up, taken pretty much verbatim from the Grub Grotto site at 
[/INDENT][INDENT][http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know](http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know)
[/INDENT][INDENT][INDENT]
grub> [COLOR=#990000]root (hd0,6)[/COLOR]
grub> [COLOR=#000099]kernel /vmlinuz[/COLOR] [COLOR=#006600]root=/dev/sda7[/COLOR]
grub> boot[/INDENT][/INDENT]This is what I added to my menu.lst file

timeout 2
default 0

title Ubuntu 9.1.0
root (hd0,6)
kernel /boot/vmlinuz-2.6.31-14-generic root=/dev/sda7


5) read MBR to file2

again using mounted sd card

dd if=/dev/sda of=/media/sdcard1/ubuntu.mbr bs=512 count=1

6) reinstall MBR from file1

dd if=/media/sdcard1/xp.mbr of=/dev/sda bs=512 count=1 

7) give file2 to NTLDR (boot.ini)

as per this slashdot article

[http://linux.slashdot.org/comments.pl?sid=160345&cid=13422290](http://linux.slashdot.org/comments.pl?sid=160345&cid=13422290)

I enter the following at the bottom of boot.ini

C:\ubuntu.mbr = "Ubuntu 9.1.0"

copy the ubuntu.mbr file to the root of c: drive

8) reboot, now the NTloader menu has both a windows and a linux option, choosing the linux option, gets you to the grub menu and a few seconds later boots up Ubuntu

---

### Post by darkod on 2009-11-17
With all the respect and the possibility of having stones thrown my way, all of this procedure just to avoid grub2 booting both windows and ubuntu?
I understand everyone has his reasons but this just creates more possibilities for problems. Not to mention it's far from understandable for newbies (not that grub2 is :) ). And it really enlarges the procedure you need to perform to get you bootloader back in case there is problem with it.

---

### Post by sibble-comp on 2009-11-17
Sure, that's true if you assume there is no other reason for not booting with grub, in my case using PGP WDE (whole disk encryption) means having the PGP BootGuard bootloader/authenticator in the mbr, it does not work the other way with grub in the mbr

[https://pgp.custhelp.com/app/answers/detail/a_id/679/kw/dual%20boot/r_id/105251](https://pgp.custhelp.com/app/answers/detail/a_id/679/kw/dual%20boot/r_id/105251)

---

### Post by pft42 on 2009-11-22
Well, if fully admit that grub2 in the more powerful bootloader and can handle everthing much better than NTLDR.

Nevertheless there are three not so newbie like arguments:

1. the linux community kept blaming MS for fiddling around with an installed linux during windows install. So it a shame that ubuntu does exactly this without option to avoid. That ubuntiu does integrate windows into grub and keep it bootable is not an excuse. For me personally I have working XP system I use heavily for serious stuff. If I play with ubunutu etc. on another partition I does like to have my workhorse affected and I do not trust anybody not even ubuntu. Its a question of principles. And they should be the same for everybody.
The really bad thing is that you tell ubuntu to install into boot partition instead of MBR and it just does not do it without error message.

2. As XP is the stable OS and workhorse while linux is changed frequently it would be painful t rely on a boot loader that is suddenly gone with the linux and leaves the preexisting windows unavailabe.

3. I have regularly other people from the family working on the PC (using XP). Confronting them with an unknown boot screen

And BTW @darkod: I guess you better be careful calling other people newbies. There is life outside THIS forum as well which you don't no much about

---

### Post by jtGohan on 2009-11-24
This works like a charm.  I would have to add that if you have only 1 hard drive (not sure about the case when ubuntu is installed on a separate drive) that you should do the following.

1. Create the partitions for ubuntu using some partitioning utility that supports linux swap and ext3 before backing up the mbr for ntldr (gparted will probably suffice).

2. back up your mbr using dd in the live cd session and save to a usb drive or a shared fat32 partition to file 1

3. install ubuntu using live cd to those partitions and set your respective mount points.

4. when installations is complete don't restart machine just continue with live cd session

5. Then proceed with step 3 posted by pft42

> **pft42 said:**
> 

The way that worked for me was this:

[LIST=1]
[*]boot karmic live CD
[*]read MBR to file1 (with dd, iniital 512 bytes of disk)
[*]mount karmic partition and /dev and chroot to it (hints how to do it without chroot did not work for me! so don't waste your time)
[*]reinstall grub, this time to MBR (!) ("grub-setup /dev/sdx" is enough)
[*]read MBR to file2
[*]reinstall MBR from file1
[*]give file2 to NTLDR (boot.ini)
[*]bingo
[/LIST]



I say this because if you don't create the partitions first.. upon restoring the mbr for ntldr the partitions for ubuntu will vanish.  Well it did in my case on my laptop.


I'm been trying to get ntldr to boot kubuntu for a while with no success so I stuck with fedora since I was always able to get ntldr to chainload to grub.  Now that I can chainload and boot kubuntu I am eager to see what this distro is all about.

I see there is much more support and forums like these for ubuntu than for fedora.

---

### Post by jtGohan on 2009-11-24
> **pft42 said:**
> Well, if fully admit that grub2 in the more powerful bootloader and can handle everthing much better than NTLDR.

Nevertheless there are three not so newbie like arguments:

1. the linux community kept blaming MS for fiddling around with an installed linux during windows install. So it a shame that ubuntu does exactly this without option to avoid. That ubuntiu does integrate windows into grub and keep it bootable is not an excuse. For me personally I have working XP system I use heavily for serious stuff. If I play with ubunutu etc. on another partition I does like to have my workhorse affected and I do not trust anybody not even ubuntu. Its a question of principles. And they should be the same for everybody.
The really bad thing is that you tell ubuntu to install into boot partition instead of MBR and it just does not do it without error message.

2. As XP is the stable OS and workhorse while linux is changed frequently it would be painful t rely on a boot loader that is suddenly gone with the linux and leaves the preexisting windows unavailabe.

3. I have regularly other people from the family working on the PC (using XP). Confronting them with an unknown boot screen

And BTW @darkod: I guess you better be careful calling other people newbies. There is life outside THIS forum as well which you don't no much about


You are so right.... and hit this on the nail.   Especially the part when you tell ubuntu to install grub to a boot partition instead of mbr.  When I installed grub to the boot partition in fedora then used the dd command on that partition and then gave that file to ntldr it always worked.  When I did this with ubuntu upon selecting it in ntldr I would get a GRUB _ on the screen with no response.  Basically it does nothing.  Still, your arguments for sticking with ntldr really do hit it on the nail.  With all that said I ask now what is the advantage or reason to have a separate /boot partition in ubuntu.  With fedora the reason was clear (installing the boot loader) with ubuntu since the boot loader will only install to the MBR then whats the point of a /boot partition?

---

### Post by mdarnold on 2009-12-07
I had a similar problem - the load process stopped with a blinking cursor.
Supposedly the boot sector was all zeros.

Turns out that grub2 uses 1-based numbering for the partitions, which is obviously different from the previous 0-based counting.

This confusion resulted in my grub install partition being off by one.
Using the correct partition for grub install fixed the problem for me.
(I reinstalled the whole OS from scratch - instructions for how to reinstall just grub2 are elsewhere).

Hopefully that fixes it for other people too.

---

### Post by darkod on 2009-12-07
> **jtGohan said:**
> This works like a charm.  I would have to add that if you have only 1 hard drive (not sure about the case when ubuntu is installed on a separate drive) that you should do the following.

1. Create the partitions for ubuntu using some partitioning utility that supports linux swap and ext3 before backing up the mbr for ntldr (gparted will probably suffice).

2. back up your mbr using dd in the live cd session and save to a usb drive or a shared fat32 partition to file 1

3. install ubuntu using live cd to those partitions and set your respective mount points.

4. when installations is complete don't restart machine just continue with live cd session

5. Then proceed with step 3 posted by pft42




I say this because if you don't create the partitions first.. upon restoring the mbr for ntldr the partitions for ubuntu will vanish.  Well it did in my case on my laptop.


I'm been trying to get ntldr to boot kubuntu for a while with no success so I stuck with fedora since I was always able to get ntldr to chainload to grub.  Now that I can chainload and boot kubuntu I am eager to see what this distro is all about.

I see there is much more support and forums like these for ubuntu than for fedora.

Can you please be more specific when saying YOU SHOULD DO THE FOLLOWING? The threads are read by many people not all of whom wish to chainload grub2 to windows bootloader. And if they are new to dual booting this is definitely much extra work than they need because grub2 will just work for them unless they have specific requirements to keep windows bootloader.
Plus your advice of creating ext3 partitions in advance will not let them use ext4, the latest filesystem with 9.10 version and also will additionally confuse someone new to linux and dual booting because that doesn't work like in windows. For windows if you create ntfs partition in advance you just tell it to use it. Because linux works with mount points, it will consider any existing partitions as unavailable. You would need to go into manual partitioning and reselect them again. And most people new to ubuntu do not even want to go in manual partitioning.
The above can get someone in lot of trouble if they think this is what they SHOULD do...

---

### Post by Clydeuk on 2010-07-02
Ok, can anyone help me with this one. It is along the same lines as the above posts. I wish to use Windows XP NTLDR to boot Kubuntu 10.04. Here's my setup. 2 x 40 gig hard drives, first HD Windows XP, second HD Kubuntu. Reported by Linux as /dev/sda (Windows) and /dev/ sdb (Kubuntu). Kubuntu installed as follows: /dev/sdb1 (boot), /dev/sdb5 ( / ), /dev/sdb6 (swap).
 
I wish to chainload Grub2 from NTLDR, however the methods I've tried don't work (dd if....... etc), I either end up with a flashing cursor, or a grub prompt.
 
I have tested my Kubuntu installation by altering the BIOS settings to boot from the second hard disk, this works fine. How do I get a copy of the second HD's MBR into a file so that I can copy this to the Windows root directory and instruct boot.ini to load Kubuntu?
 
I installed Grub in the MBR of /dev.sdb as it was suggested by the partitioner, however I am starting to think I shouldn't have done this, is there a way to get around it without having to reinstall from the Live CD again?
 
I'm at my wits end as I've tried all sorts and so far have installed and reinstalled Kubuntu 5 times trying different locations for the Grub files. most of the time I break the Linux installation and have to reinstall from the Live CD, this takes ages!
 
Any help?

---

### Post by Clydeuk on 2010-07-02
By the way, I installed Kubuntu on a Vista laptop and used EasyBCD to adjust Vista's BCD to boot Kubuntu, this worked great, and I'm loving Kubuntu!

---

### Post by Clydeuk on 2010-07-02
By the way, my only reason for using NTLDR is that I have other people who use Windows who may get a bit confused when they see the Grub loader, I intend to set a short timeout before automatically booting Windows. That and I myself am a bit of a Newbie to Ubuntu and am unfamiliar with the commands to add/edit the Grub options.

---

### Post by Clydeuk on 2010-07-02
Once again, it's gone wrong!
 
Tried all the above only now somehow I have grub2 as my bootloader, from here it will boot Kubuntu or XP fine, if I select XP i get NTLDR with the options, including Kubuntu, it will load XP correctly, only now if I select Kubuntu it gives me "error no such device: (some UID string) and then proceeds to a prompt "grub rescue>"
 
I presume I should be able to do something from here, however commands listed in previous posts (root (sd1,1)) etc. return "unknown command 'root'
 
I have a feeling the above posts are in relation to grub and not grub2, or there something different about kubuntu's implementation of grub2?

---

### Post by artemyv on 2010-07-02
> **pft42 said:**
> 
My summary is that this is a dual pain and shame:
1. refusing correct work without an error message is fully unaaceptable;
2. the windos install behaviour to overwrite other boot code (like linux) was always considered very bad behaviour in linux community, so why does grub2 go that way now? Yes I know grub2 can boot windows as well but it is clearly bad behavior to touch q foreign system - and finally it is completely unecessary

I do not know about 1, but second issue is being addressed right now

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/07/02#2010-07-02-grub2-with-luck](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/07/02#2010-07-02-grub2-with-luck)

So if you'd like something to be fixed in the next version of the grub you could comment on that post and give your suggestions.

---

