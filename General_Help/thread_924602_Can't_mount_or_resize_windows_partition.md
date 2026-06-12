---
title: "Can't mount or resize windows partition"
date: 2008-09-19
forum: General Help
---

### Post by GB2732 on 2008-09-19
First of all, I have a duel boot system with Ubuntu Hardy Heron, and windows xp sharing the same HDD. 

My problem started when I transferred a large folder of songs from Ubuntu to windows xp, using Dolphin. Afterward, I attempted to boot into windows, but my computer crashed during boot. 

It turns out that I used up all the disk space on the hda1 (windows) partition.

It appears that my only two options are to either delete some windows files, or resize the NTFS partition.

I used Gparted from live CD, and was able to reduce the size of the ext3 partition. However, I'm not able to increase the size of the NTFS partition. When I try, I get an error message saying :

[COLOR="Red"]$LogFile indicates unclean shutdown (0, 0)
....
Mount is denied because NTFS is marked to be in use.[/COLOR]

 
I've tried to force mount the partition, but that doesn't work either. 


As it stands now, I can't boot windows, I can't mount windows partition under Ubuntu, and I can't resize using Gparted.

Any help is appreciated.

---

### Post by stickmangumby on 2008-09-19
Can you use your Windows XP CD to boot into the recovery console, and remove some files that way?

What errors do you get when you try to force mount your NTFS partition?

---

### Post by oilchangeguy on 2008-09-19
remove the hard drive, and slave it in another windows computer. you should be able to get your data.

---

### Post by oilchangeguy on 2008-09-19
> **stickmangumby said:**
> Can you use your Windows XP CD to boot into the recovery console, and remove some files that way?

What errors do you get when you try to force mount your NTFS partition?

please tell us how you get "some" files from using the recovery console. what if the user wants all of their files. and the error(s) that shows up when trying to force mount mean nothing. if the partition can't be mounted, it can't be mounted.

---

### Post by GB2732 on 2008-09-19
Sorry, I didn't mention that have a laptop, so removing the drive isn't an option. I also can't use the windows xp CD, because it doesn't "install" xp, it uses Norton Ghost to load the HDD.


This is the full error that pops up when I try to mount it using Gparted.

[B][COLOR="Red"]$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda1 /media/windows xp -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda1 /media/windows xp ntfs-3g force 0 0[/COLOR][/B]

I tried both choices to force the partition to mount, and neither one works

---

### Post by oilchangeguy on 2008-09-19
" also can't use the windows xp CD, because it doesn't "install" xp, it uses Norton Ghost to load the HDD."

ah, you're using pirated software. that's a no,no in this forum. you get to look elsewhere for your answer.

---

### Post by babybugs1980 on 2008-09-19
Norton Ghost doesn't mean pirated software, it's likely a work laptop.  We use Norton ghost to install crashed pc's all the time.  There's likely at least one original disk around somewhere but since we just buy licences the disk never gets used.

Please keep feeding out answers because I am in a similar situation.  I have an 80 GB WD drive that was killed due to my motherboard's ram controllers flaking out and it left my drive in the state of not reaching Windows.  The only other machine I have to slave it to is my darling, trudge through anything, always work Ubuntu machine but it in no way has the same hardware so if I let my Windows drive boot on this machine it's going to want to be activated.  Is that far enough for me to be able to then slave it and pull my info off?

TIA!

Nevermind for me, this command worked:

sudo ntfs-3g -o force,rw /dev/sdb1 /media/windows after I created the /media/windows folder. 

I am a happy camper now!

---

### Post by GB2732 on 2008-09-19
> **oilchangeguy said:**
> " also can't use the windows xp CD, because it doesn't "install" xp, it uses Norton Ghost to load the HDD."

ah, you're using pirated software. that's a no,no in this forum. you get to look elsewhere for your answer.


It's not pirated, it's what came with the computer.

---

### Post by oilchangeguy on 2008-09-19
> **GB2732 said:**
> It's not pirated, it's what came with the computer.

if it uses norton ghost to install, it's pirated. it's for sure not oem, and it's not retail, so it's pirated.

---

### Post by GB2732 on 2008-09-19
> **babybugs1980 said:**
> Norton Ghost doesn't mean pirated software, it's likely a work laptop.  We use Norton ghost to install crashed pc's all the time.  There's likely at least one original disk around somewhere but since we just buy licences the disk never gets used.

Please keep feeding out answers because I am in a similar situation.  I have an 80 GB WD drive that was killed due to my motherboard's ram controllers flaking out and it left my drive in the state of not reaching Windows.  The only other machine I have to slave it to is my darling, trudge through anything, always work Ubuntu machine but it in no way has the same hardware so if I let my Windows drive boot on this machine it's going to want to be activated.  Is that far enough for me to be able to then slave it and pull my info off?

TIA!

Nevermind for me, this command worked:

sudo ntfs-3g -o force,rw /dev/sdb1 /media/windows after I created the /media/windows folder. 

I am a happy camper now!

[solved] My mistake was originally naming my windows file "windows xp". When I renamed the file 'windows', removing the "xp", and ran the command sudo ntfs-3g -o force,rw /dev/hda1 /media/windows it mounted correctly.

Thanks for the replies!! :cool:

---

### Post by rodriguez24 on 2008-09-22
> **oilchangeguy said:**
> if it uses norton ghost to install, it's pirated. it's for sure not oem, and it's not retail, so it's pirated.
Just to clarify this. My Toshiba Qosmio F25 comes with recovery CDs and it is using Norton Ghost. It did not come with an XP CD. So just because it uses ghost does not mean it is pirated. In this type setup the key is located (and embedded) in the laptop itself.

---

