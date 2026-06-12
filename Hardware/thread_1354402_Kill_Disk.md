---
title: "Kill Disk"
date: 2009-12-13
forum: Hardware
---

### Post by kakashi_12 on 2009-12-13
I got it working finally and found out afterwards, that the free version only allows 1 pass. Are any of you aware of a freeware or open source bootable program that will do the same, but allow multiple passes (4, 7, or 24 passes, etc)? Either DOS or Linux based, whatever as long as it's bootable. Thanks to all for any input.

---

### Post by Agent ME on 2009-12-13
> **kakashi_12 said:**
> I got it working finally and found out afterwards, that the free version only allows 1 pass.
What is "it"? The free version of what?

From the topic title, I'm guessing you're talking about some sort of program to wipe a disk. The standard linux command "shred" can do this.

To wipe a hard drive with 3 passes of random data, this following command will work. Change /dev/sda for your own if your setup differs. You probably should have the disk completely unmounted first.
**Warning: Running this command will permanently erase all data on the chosen hard drive. Seriously, do not run this unless you really want to.**
```
sudo shred /dev/sda
```

---

### Post by kakashi_12 on 2009-12-13
> **Agent ME said:**
> What is "it"? The free version of what?
 
From the topic title, I'm guessing you're talking about some sort of program to wipe a disk. The standard linux command "shred" can do this.
 
To wipe a hard drive with 3 passes of random data, this following command will work. Change /dev/sda for your own if your setup differs. You probably should have the disk completely unmounted first.
**Warning: Running this command will permanently erase all data on the chosen hard drive. Seriously, do not run this unless you really want to.**
```
sudo shred /dev/sda
```
 
it means the subject line (kill disk free version).
 
Sweet, a linux command. Even better. Now, I can't do this with the linux ox booted. What should I do insert my Ubuntu disc and boot off that, then go to a terminal from the disc somehow, then use that command above? I want to erase the entire disk (all partitions). Yes, I do have it backed up.

---

### Post by blackened on 2009-12-13
> **kakashi_12 said:**
> it means the subject line (kill disk free version).
 
Sweet, a linux command. Even better. Now, I can't do this with the linux ox booted. What should I do insert my Ubuntu disc and boot off that, then go to a terminal from the disc somehow, then use that command above? I want to erase the entire disk (all partitions). Yes, I do have it backed up.

Yes, boot from the live cd and run the command from the terminal. Make sure you take out any other removable media (USB sticks, SD cards, etc.) so as to avoid confusion with drive designations.

---

### Post by kakashi_12 on 2009-12-13
Ok, so this command will do the ENTIRE drive. Not just one partition?
 
what does each of these words/cmd mean?
 
sudo shred /dev/sda
 
I understand sudo means super-user
shred is self-explanatory
dev must mean device?
sda= something drive a?

---

### Post by steve161 on 2009-12-13
[http://www.dban.org/](http://www.dban.org/)

Another option.  Boot into it, type "autonuke" at the prompt, go to bed, and in the morning you will have a wiped (3 pass) drive.  There are also other wiping options available from the disk.

---

### Post by Agent ME on 2009-12-14
> **kakashi_12 said:**
> Ok, so this command will do the ENTIRE drive. Not just one partition?
 
what does each of these words/cmd mean?
 
sudo shred /dev/sda
 
I understand sudo means super-user
shred is self-explanatory
dev must mean device?
sda= something drive a?
"dev" is a special linux directory that has all of the system devices in it. Inside the dev directory, the disk drives are given filenames starting with "sd" or "hd". The third letter, the "a", means the first disk drive. ("sdb" would refer to the second disk drive, etc.)

There may also be files representing the individual partitions of the disk drives; "sda1" would refer to the first partition of sda, and so on. (There may be gaps in the numbering: I have an sdb1, sdb2, and sdb5. I think the swap partition often gets a higher number for the heck of it.)

You can choose to shred the whole drive ("sudo shred /dev/sda"), an individual partition ("sudo shred /dev/sda3") or several partitions ("sudo shred /dev/sda1 /dev/sda3 /dev/sda4", or in a shorter notation, "sudo shred /dev/sda{1,3,4}" -- /dev/sda2 is left untouched in both of these).

---

### Post by kakashi_12 on 2009-12-14
Thanks so much!!! I totally understand now!

---

