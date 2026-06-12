---
title: "HELP:  Lost Grub &amp; cannot reinstall it to MBR"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by zong1 on 2009-01-31
I am trying to get GRUB back onto the disc after I installed Solaris 10 (I wish I had not) onto a free partition.  

Solaris placed its own incompatible grub bit onto the MBR with no entries for my Ubuntu, which has my CV on it, which I have to get off for Monday for a job interview.  

/boot for Ubuntu is a separate partition on /dev/sda5. This is standard ext3. No encryption.

All Ubuntu root and swap are on a blowfish encrytped LVS partition that at present is inaccessible.

I have a copy of PuppyLinux live CD that works.

I read that if I ran grub and did this & replaced the hd0 with my disc (sd) then all would be well, but sadly not:

Restore Ubuntu GRUB:
Taken from [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
grub
find /boot/grub/stage1
root (sd?,?)
setup (sd0)
quit

However, I got:
grub> find /boot/grub/stage1
Error 15: File not found

Note: I tried this with /dev/sda5 mounted as /boot and unmounted.
The files are there such as the menu.lst and the file stage1 is there:
# find /boot -name stage1
/boot/grub/stage1

How can I get Linux grub pointing to /boot (sda5) back onto the MBR?  

I physically feel ill at present. I shall montior this thread all evening.

Best wishes.

---

### Post by MarblePanther on 2009-01-31
Have you been to the site in my signature? (supergrubdisk)

---

### Post by zong1 on 2009-01-31
I am reading it now.

Quickly looking at it, do I have to burn this from a CD and boot from it or is there a Linux version?  I see USB boot versions and Windows ones.  I'm a little lost which one I ought to d/l?

---

### Post by MarblePanther on 2009-01-31
Just download the CDROM iso and burn it to a cd.

Then boot it like you would a livecd.  It includes instructions on the disk.

---

### Post by zong1 on 2009-01-31
I have noticed that I have misunderstood grub by looking at the process of recover.  Your wiki states that there are really three stages:  
1) Work out  what the sd / hd bit should be
2) Tell grub which /boot he should look for
3) Tell grub which root partition to boot.


However, I might have shot myself in the foot:  I want to use the menu.lst that I already have in the /boot (sda5) partition and do not wish to clobber this with a new one.
  Not So Quick solution

   1. GRUB => MBR & !LINUX! (>2) MANUAL |8-)
   2. Choose the partition where the Linux GRUB you want to recover is located.
   3. Choose the partition where the Linux GRUB you want to boot is located.

---

### Post by zong1 on 2009-01-31
I have no CDs or DVDs and I cannot guaretee the burner s/w will work.  Nor have I a USB drive to copy it to.
/edit: And I live in Southern Spain = shops are closed from 2pm on Saturday and won't open until Monday so I cannot buy one either & I do not have a car to get to one if these were open.

---

### Post by MarblePanther on 2009-01-31
Try booting your puppy cd. There is an option for restoring grub to MBR in the puppy menu.  I haven't used puppy in a while so i cant remember the exact name.

Try that out first.







here is a puppy wiki entry that might help you: 

[http://www.puppylinux.org/wiki/how-tos/general/grub](http://www.puppylinux.org/wiki/how-tos/general/grub)

---

### Post by zong1 on 2009-01-31
Found the one in Puppy.  I am trying to work it out now.  Cheers.

---

### Post by zong1 on 2009-01-31
Puppy is a no go, because it refuses to write to the MBR because it does not recognise it. Must be good old Solaris' own MBR.

---

### Post by zong1 on 2009-01-31
Is there a simple way of installing only a new MBR and telling it to go to sda5 to look for the grub stuff?

e.g Will this write to the MBR and point it to /dev/sda5 (there is only one disc in my laptop)


# grub
root (sd0,4)
setup (sd0)
quit
#

Or is it:
grub-install /dev/sda

---

### Post by caljohnsmith on 2009-01-31
Do you have internet access from your Puppy Live CD? If so, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Puppy desktop, open a terminal and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and maybe give some insight why you are having problems reinstalling Grub.

---

### Post by MarblePanther on 2009-01-31
> Linux and OpenSolaris

    * This installation is more dangerous than Windows and OpenSolaris, because OpenSolaris can't detect Linux OSes. Make sure the person knows about the dangers and he has a backup of his data.
    * Make a backup copy of Linux GRUB boot loader configuration (/boot/grub/menu.lst). Do not attempt to install if the users uses any other boot manager.
    * Create a new primary partition using GParted (after Linux).
    * Install OpenSolaris. MBR will get overwritten.
    * Add the instructions from the Linux GRUB boot loader into the OpenSolaris GRUB configuration (/rpool/boot/grub/menu.lst) and reboot. Do not try to use Linux's GRUB because it can't boot into ZFS.
    * More detailed instructions to be added based on future experiences.


^
from the opensolaris wiki

So basically boot into opensolaris and edit /rpool/boot/grub/menu.lst to include your linux partition.

---

### Post by zong1 on 2009-01-31
This failed.

grub> root (sd0,4)

Error 23: Error while parsing number

---

### Post by zong1 on 2009-01-31
One can chainload from Linux Grub into Solaris Grub, which is what I intend to do instead.  I won't ever update Solaris grub, but Ubuntu kernel changes certainly shall.

I have attached the RESULTS.TXT because I cannot copy and paste at present.

//EDIT: removed attachment as it contains too mcuh detail about my discs for the public at large

---

### Post by caljohnsmith on 2009-01-31
According to the script (which is usually quite accurate), your HDD doesn't even have a valid partition table right now. I would suggest downloading [Testdisk 6.10]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") to your Puppy desktop, and then do:
```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing if you would like a hand recovering your partitions. We can work from there if you want.

---

### Post by zong1 on 2009-01-31
OK. Testdisk is in progress.

---

### Post by zong1 on 2009-01-31
I cannot copy and paste between the applications so cannot paste the results of the testdisk.  Still working in this hitch.

/edit: Enabled the logging option. Will be back soon.

---

### Post by zong1 on 2009-01-31
I have attached the log file.
testdisk.txt

/edit. I am running this again because I had not done the deepsearch option.

Out of interest, why can the system simply write a new MBR to the disc.  I can see the partitions and mount these from Puppy!

//EDIT: removed attachment as it contains too mcuh detail about my discs for the public at large

---

### Post by caljohnsmith on 2009-01-31
Have you posted the results with the deep search? Also, what is the current output of:
```
fdisk -lu
```

---

### Post by zong1 on 2009-01-31
Attached fdisk -lu

sda6 has some errors.  It looks like the ntfsresize I ran on it before I installed Solaris had not completed correctly, even though gparted said that it had.  I ran a Check on it from gparted and it rerun the ntfsresize on it. It would not mount afore, and now it does.

//EDIT :removed attachment as it contains too mcuh detail about my discs for the public at large

---

### Post by caljohnsmith on 2009-01-31
OK, how about posting the output of:
```
mkdir /mnt/sda3 /mnt/sda5
mount /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3 /mnt/sda3/grub /mnt/sda3/boot/grub
mount /dev/sda5 /mnt/sda5 && ls -l /mnt/sda5 /mnt/sda5/grub /mnt/sda5/boot/grub
```

---

### Post by zong1 on 2009-01-31
I have attached the log file from the deepscan with the P listings.
I have had to split the file into two.
The first is called 1aa.txt

The next one will appear in the next post because of the forum restictions

---

### Post by zong1 on 2009-01-31
There the second one.  (there is actually third)

---

### Post by zong1 on 2009-01-31
Here is the third.

/edit: removed attachment as it contains too mcuh detail about my discs for the public at large

---

### Post by zong1 on 2009-01-31
> **caljohnsmith said:**
> OK, how about posting the output of:
```
mkdir /mnt/sda3 /mnt/sda5
mount /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3 /mnt/sda3/grub /mnt/sda3/boot/grub
mount /dev/sda5 /mnt/sda5 && ls -l /mnt/sda5 /mnt/sda5/grub /mnt/sda5/boot/grub
```

Attached txt file.  sda3 is LUKS so this failed to mount as expected.

sda3 lists all the right grub files.

//EDIT: removed attachment as it contains too mcuh detail about my discs for the public at large

---

### Post by caljohnsmith on 2009-01-31
OK, what happens when you try:
```
grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```

---

### Post by TheLaughingMan84 on 2009-01-31
If the CV is your only concern, you could just boot with puppylinux and mount the disk?

---

### Post by zong1 on 2009-01-31
> **TheLaughingMan84 said:**
> If the CV is your only concern, you could just boot with puppylinux and mount the disk?

Its on a LUKS / LVS encrypted partition and I have no idea how to load the drivers from grub to boot it.

However, we have what looks like success:

grub> root (hd0,4)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)

 Checking if "/boot/grub/stage1" exists ... no
 Checking if "/grub/stage1" Exists ... yes
 Checking if "/grub/stage2" exists .... yes
 Checking if "/grub/e2fs_stage1_5" exists ... yes
 Running "embed /grub/e2fs_stage1_5 {hd0)" ... 16 sectors are embedded. succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/grub/stage2 /grub/menu.lst" ... succeeded
 Done.

---

### Post by zong1 on 2009-01-31
I have rebooted & the original grub came back.  

Many many thanks to caljohnsmith and MarblePanther for your help and patience.  I really do appricate this.  If you want me to send you something for your time then PM me your paypal addresses.  I know you do this for love, but the offer is there anyway.

Meanwhile, back to Solaris ;)

I think that if I add this to the menu.lst then it ought to chainload the Solaris GRUB.  The disc partition is sda4, so I presume that this would translate into hd0,3 - Would it?

```

# Solaris 10 U1 or later:
title Solaris 10U1
	rootnoverify (hd0,3)
        chainloader +1

```

The rootnoverify is for filesystems unbeknownst to Linux GRUB such as ZFS UFS.
Perhaps, one has to add makeactive for Solaris to boot. I read this had to be done in Solaris 9. but I don't know with Solaris 10.

---

### Post by caljohnsmith on 2009-01-31
That's great news, glad you could boot into Ubuntu again. About Solaris, I've seen the syntax you have used, so that would probably work, but I've also seen where people boot Solaris by booting the boot sector of the partition:
```
title Solaris 10U1
rootnoverify (hd0,3)
chainloader +1
```
You might want to give that a try. Let me know how it goes.

EDIT: I see you all ready edited your post to use the same Grub entry. :)

---

### Post by zong1 on 2009-01-31
That worked perfectly well. 

Now system has WinXP Ubuntu & Solaris living in harmony.  Solaris has not settled in yet as I have to add the nvidea modile and the NIC module, but that is for another day.

Cheers.

---

### Post by caljohnsmith on 2009-01-31
Glad to hear that worked OK; cheers and good luck with Solaris. :)

---

