---
title: "[SOLVED] HDD access permissions"
date: 2008-08-23
forum: Hardware
---

### Post by 73ckn797 on 2008-08-23
Here is the deal:

I have a 40 gig drive that I was using for backup purposes under Windows XP. I have switched to Ubuntu. I reformatted the drive (sdb) to ext2. Now I cannot write to the drive. I find no way to change the permissions since I am not the root. I tried several things after reading about "chmod" and commanded read/write permission to all. That command seemed to be accepted but when I go to "Computer" to access the drive I still only have read permission.

The drive, after formatting, has a "lost-found" directory. Where does that come from? When I try to look in the directory I am not allowed access. I tried to log on as root but cannot. It seems that is the only way in. I have used "sudo" and can "cd" to the drive. That was how I was able to enter R/W commands. I also rebooted the system but no luck. I have also lost R/W access to a second drive where I have the Ubuntu 64 bit loaded. I have the same problem in there also.

This is getting frustrating. I like Ubuntu, despise Windows, but with all of the little issues that come up I am about to trash it all and put up with XP. I am a newbie and am trying to learn but I do have other things to do besides sit here all day.

---

### Post by silkstone on 2008-08-23
When you formatted the drive with gparted, you had to enter your password to log on as root. Therefore by default the drive is owned by root.

You can change this easily if you know where the drive is mounted, or the name of the drive.

If you open a terminal and...

sudo fdisk -l

(Note: that's a lower-case L.)

... you should see your new drive. Let's say it's at /dev/sdb1

Then...

sudo chown -R username:username /dev/sdb1

Please make sure you have identified the correct drive!

That will make you the owner of the drive and all the files on it.

P.S. The Lost & Found folder is where the system puts any lost files following a disk check. You can ignore it.

---

### Post by 73ckn797 on 2008-08-23
I did the fdisk and know that info. The drive is not new except in the sense of now being formated ext2. the problem began after the formatting. I was able to R/W prior to that.

"sudo chown -R username:username /dev/sdb1"
The "username:username" part, will I enter just the name (ie ... ralph:ralph) in both places or is there something else? Ralph is not my name and no offense intended to all of the Ralph's out there!

I did the command with username:username and it returned no errors. but I still have no access to R/W. Will I need to reboot?

The fdisk info on the drive is:
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b230d97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

What say you?

---

### Post by silkstone on 2008-08-23
Sorry - yes you have to either unmount and remount the drive, or reboot for the new ownership to take effect.

Substituting your real username for 'username' should have worked!

---

### Post by cariboo on 2008-08-23
You probably won't be able to change ownership of your hard drive, but you can change the permissions of your mount point for example if you drive is mounted on /media/backups then you would issue the command:

```
sudo chmod -R 777 /media/backups
```

after you have mounted /dev/sdb1 eg:

```
sudo mount /dev/sdb1 /media/backups
```

Jim

---

### Post by 73ckn797 on 2008-08-23
I have tried all options given and nothing is working. Since I did all of that my internet will not work on the desktop. I made certain that all commands were exactly typed. I did fail to mention that when I initiallY went to format the drive to ext2 it displayed an error and after that the Lost-found directory appeared every time I tried to format it. MaKes me thinks it has a bad sector. It seemed to get very noisy when formatting to ext2 but not back to NTFS. Go figure that!! I will run disk check on it.

I booted the system with the Ubuntu LiveCD and reformatted the /dev/sdb back to NTFS and can now read and write with no problems. It got to where Ubuntu would not give me the option of a NTFS format.

I tried all options for the internet but nothing worked. I removed the ethernet card and connected into the MOB LAN and the internet connects. Guess that the card died while fooling with the other stuff.

Goes to show that if something ain't broke, don't fix it. Being a 33 year auto tech should have made me apply that to my desktop computer.

---

### Post by sammcnair on 2008-11-13
> **73ckn797 said:**
> Here is the deal:

I have a 40 gig drive that I was using for backup purposes under Windows XP. I have switched to Ubuntu. I reformatted the drive (sdb) to ext2. Now I cannot write to the drive. I find no way to change the permissions since I am not the root. I tried several things after reading about "chmod" and commanded read/write permission to all. That command seemed to be accepted but when I go to "Computer" to access the drive I still only have read permission.

The drive, after formatting, has a "lost-found" directory. Where does that come from? When I try to look in the directory I am not allowed access. I tried to log on as root but cannot. It seems that is the only way in. I have used "sudo" and can "cd" to the drive. That was how I was able to enter R/W commands. I also rebooted the system but no luck. I have also lost R/W access to a second drive where I have the Ubuntu 64 bit loaded. I have the same problem in there also.

This is getting frustrating. I like Ubuntu, despise Windows, but with all of the little issues that come up I am about to trash it all and put up with XP. I am a newbie and am trying to learn but I do have other things to do besides sit here all day.

i have the same problem to this i have tryed every thing when i tryed  sudo chown -R sam@sam/dev/sda5

it says sam@sam-laptop:~$ sudo chown -R sam:sam/dev/sda3
chown: missing operand after `sam:sam/dev/sda3'

can ya help please 

sam

---

