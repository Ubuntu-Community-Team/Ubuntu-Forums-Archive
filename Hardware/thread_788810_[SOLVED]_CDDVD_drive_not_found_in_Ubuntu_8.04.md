---
title: "[SOLVED] CD/DVD drive not found in Ubuntu 8.04"
date: 2008-05-10
forum: Hardware
---

### Post by avhlza on 2008-05-10
Hello,
I have a Zepto Znote 6625WD laptop with a Samsung DVD-RW slot-in drive.
When running Ubuntu 8.04 and trying to play a CD or DVD nothing happens.
I suspect that the drive isn't recognized because the command 'sudo lshw | grep cdrom' (without the '') doesn't yield any results.
Anyone know what to do?
Thanks in advance :)

---

### Post by logos34 on 2008-05-10
check

Nautilus File mgmt prefs>Media tab>enable 'browse media when inserted'

Anything?

Post your /etc/fstab file

ls -l /dev | grep cd

ls -l /dev | grep dvd

---

### Post by avhlza on 2008-05-10
contents of /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=266459a5-3ce8-4a5b-a33c-9ec4dcd9c759 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=7eada3c4-7a08-4982-abb7-df6a6ca542dd /home           ext3    relatime        0       2
# /dev/sda4
UUID=9c29e402-12dc-4f6b-b296-3dd473287f50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660, udf user,noauto,exec,utf8 0       0

ls -l /dev | grep cd:
> crw-rw-rw-  1 root   tty       2, 221 2008-05-10 09:27 ptycd
crw-rw-rw-  1 root   tty       3, 221 2008-05-10 09:27 ttycd

ls -l /dev | grep dvd returns nothing

---

### Post by logos34 on 2008-05-10
Here's mine:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0

$ lshw -C disk
> *-cdrom
       product: ASUS DRW-1608P2
       physical id: 0
       bus info: ide@1.0
       **logical name: /dev/hdc**
       capabilities: packet


$ ls -l /dev | grep cd
lrwxrwxrwx  1 root   root           3 2008-05-10 10:35 cdrom -> hdc
lrwxrwxrwx  1 root   root           3 2008-05-10 10:35 cdrw -> hdc
brw-rw----+ 1 root   cdrom    22,   0 2008-05-10 10:35 hdc
crw-rw-rw-  1 root   tty       2, 221 2008-05-10 10:35 ptycd
crw-rw-rw-  1 root   tty       3, 221 2008-05-10 10:35 ttycd

$ ls -l /dev | grep dvd
lrwxrwxrwx  1 root   root           3 2008-05-10 10:35 dvd -> hdc
lrwxrwxrwx  1 root   root           3 2008-05-10 10:35 dvdrw -> hdc

So it would appear you're missing the symlinks in /dev, maybe because linux isn't detecting the drive.  Does the cdrom show upin Bios?

---

### Post by avhlza on 2008-05-10
Thank you for your help, I appreciate it.

This is actually really weird:
I also have a Vista installation, which I've had since I bought my laptop, so I checked if the drive worked in Vista, and (surprisingly) it didn't.
Well, I've only had Ubuntu for about 2 weeks and before that the drive worked flawlessly. 
So, this is the weird part, I then tried booting from my Ubuntu live CD and it booted without problems. :confused:
Since I haven't actually used the drive after I installed Ubuntu I was wondering if GRUB (because it now loads the Windows loader) maybe could be screwing something up?

---

### Post by avhlza on 2008-05-11
Bump. Anyone got a clue?

Edit:
I reinstalled the Windows Vista loader to the MBR with EasyBCD (and in the process overwriting GRUB). This made my drive work under Vista, so now I'm sure it have something to do with GRUB.

Edit2:
So I used this excellent tutorial ([http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)) to chainload GRUB from the Windows bootloader 
(and not the other way around as it was before) which fixed the problem with using my drive on my Vista installation.
This, however, didn't fix my drive under Ubuntu...

---

### Post by avhlza on 2008-05-12
Bumpity bump.
I think my problem is the same as this bug: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)

Then I think the problem lies in GRUB incorrectly identifying my drives.

cat /boot/grub/device.map:
(hd0)	/dev/sda

my boot order from BIOS:
1: IDE CD (my cd/dvd-rom drive)
2: USB KEY
3: IDE HDD (my harddrive)

the rest of the boot order I think is unnecessary, but added anyway: 
4: USB FDC 
5: PCI BEV (my 3-in-1 SD card reader)
6: USB HDD
7: USB CDROM

could anyone please help/confirm/say if I'm on the right track or something so I can use my cd-drive in Ubuntu?

---

### Post by avhlza on 2008-05-15
So I've finally got a solution thanks to mrrangerman from LQ. :D
Here's the link to my thread at LQ: [http://www.linuxquestions.org/questions/linux-newbie-8/cd-drive-not-found-grub-problem-641861/](http://www.linuxquestions.org/questions/linux-newbie-8/cd-drive-not-found-grub-problem-641861/)
and here's the link with the solution that mrrangerman found: [http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dvdr-drive-doesnt-work-593123/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dvdr-drive-doesnt-work-593123/)

---

### Post by Dondorp on 2008-06-09
Same problem, same laptop im testing your stuff now.
[B]
[COLOR="RED"]--Confirmed--[/COLOR][/B]
Stunning way to do this, but disabling cdrom in bios main menu enables it in ubuntu & windows xp too (without any modifications)

---

### Post by Jeanpaul145 on 2008-06-18
> **Dondorp said:**
> Same problem, same laptop im testing your stuff now.
[B]
[COLOR="RED"]--Confirmed--[/COLOR][/B]
Stunning way to do this, but disabling cdrom in bios main menu enables it in ubuntu & windows xp too (without any modifications)

Indeed, I have a Zepto 6625WD as well, and I've been having exactly the same problem. I've sent a bug report to Zepto a couple of weeks ago, because AFAIk the BIOS is responsible. Therefore, Zepto should fix it.

---

### Post by elendrum on 2008-06-28
Hey People,

I had a issue like this just recently as well. I lost access to my cdroms on my server. I tried to mount them but, it stated that the /dev/hdc did not exist. I did a 'ls /dev/hd*' and sure enough there where no entries.

I tried to do a 'lsmod' thinking that the system may have just forgotten the modules or something. But, its been forever since I hacked a system together from the ground up. 

I had a working version of 8.04 desktop and checked the '/etc/fstab' and the cdrom was pointed to '/dev/scd0' not '/dev/hdc' like my 8.04 server was. I checked the '/dev/scd*' and found two entries for both of my cdroms. I edited the fstab on the server and peformed a mount for the '/media/cdrom0' and up jumps my connection and a quick 'ls' of the /media/cdrom0 showed the contents of the cdrom. 

Not sure how it went from a working install with cdroms working just fine to what I assume is an altered /etc/fstab. 

But, all is good with the world again. I hope this helps someone out. I know it a simple fix but, I forgot which modules should be loaded when the kernal id's the ide channel for my cdroms.

Eric

Now back to that oracle install i was trying to do :-)

---

### Post by gbutler69 on 2008-10-14
I used the solution here (that is mentioned earlier in this Thread) to fix a similar problem I was having on a Pangolin V3 from System76 upgraded from 7.04 -> 7.10 -> 8.04 -> 8.10. The CD/DVD hasn't worked since I upgraded to 7.10 from 7.04. The only recommendation I had received was to reinstall. Unfortunately, due to my work-load, I could not afford any down-time on my laptop to perform such an installation.

Anyway, I guess patience paid off (I didn't really NEED the DVD/CD anyway -- Isn't that weird that we're so connected that I can say that).

I finally came across this thread which led me to this thread:

    [https://answers.launchpad.net/ubuntu/+question/10747](https://answers.launchpad.net/ubuntu/+question/10747)

Which about 1/2 way down the page has a solution of editing "/etc/modules" and adding the following lines to it:

    lib_ata
    ata_piix
    piix

 Doing the above and then rebootin totally fixed my problem.

Can someone with a little more knowledge of the details of this provide a better explanation as to why this fixes the issue?

Hope this helps the next guy (or gal).

---

