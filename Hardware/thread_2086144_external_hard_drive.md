---
title: "external hard drive"
date: 2012-11-20
forum: Hardware
---

### Post by Jacob-Gates on 2012-11-20
i recently reinstalled ubuntu on my computer (went from 32 bit to 64 bit). The installation was successful but I had backed up all my personal files onto an external hard drive and now when I plug it in it won't mount. The disk app shows it's there, gparted shows it's there but it's flagged for boot and it says "unknown" with a black square. I don't know gparted very well so let me know if there is something else you need to know about that.

I tried doing plugging it up in my windows side and windows says it needs to be formatted. And of course I don't want to do that because it has my personal files that I want to transfer to ubuntu. Is there any way I can save these files?

---

### Post by ahallubuntu on 2012-11-20
What was the format of the external drive?  NTFS?  FAT32?  Or a Linux format like EXT4?

How did you make the backup?

If a Windows format, you might try a file recovery tool like Recuva (free, google for it) on your Windows computer and see if it can find any of your files.

---

### Post by Jacob-Gates on 2012-11-20
> **ahallubuntu said:**
> What was the format of the external drive?  NTFS?  FAT32?  Or a Linux format like EXT4?

How did you make the backup?

If a Windows format, you might try a file recovery tool like Recuva (free, google for it) on your Windows computer and see if it can find any of your files.

in gparted it does say, I have no idea. All i did was plug it up to my old ubuntu and copied the files over, I even looked through it after to make sure everything transferred fine. I actually already tried recuva but it said there was no device... but windows had it in my computer.

in gparted it says:
file system: unknown
path: /dev/sdb1
status: unmounted

is the status important in this? is there a way i can force it to mount or something?

---

### Post by Bucky Ball on 2012-11-20
Right click that partition in gparted and mount it ...

What happens? Is the option dimmed or okay?

---

### Post by Jacob-Gates on 2012-11-20
> **Bucky Ball said:**
> Right click that partition in gparted and mount it ...

What happens? Is the option dimmed or okay?

it's dimmed and won't let me click it.

---

### Post by Bucky Ball on 2012-11-20
Open a terminal and try this:
```

sudo blkid
```

... with the hard drive plugged in and on.

Post the result here, please.

---

### Post by Jacob-Gates on 2012-11-20
> **Bucky Ball said:**
> Open a terminal and try this:
```

sudo blkid
```

... with the hard drive plugged in and on.

Post the result here, please.

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="ECF07E84F07E54B4" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="1A0601230601018D" TYPE="ntfs" 
/dev/sda5: UUID="74a6a754-32f8-4a80-bf01-ae7665796727" TYPE="ext4" 
/dev/sda6: UUID="7804fd74-b410-4fec-8a46-5a9de8ad27a6" TYPE="swap" 

```

edit: yes the external hdd is in and on... i don't see it in the results.

---

### Post by Bucky Ball on 2012-11-20
Hmm, not there. Could have tried mounting from the terminal. Okay, in Gparted, does it show that it is /dev/sda* something? If so, try in a terminal:

```
sudo mkdir /mnt/external
```This will create a mount point in /mnt for the partition. You can call that what you want, not necessarily 'external'. Then:

```

sudo mount /dev/sda* /mnt/external
```Of course, replacing the * with the number of the partition. ;)

What happened?

---

### Post by Jacob-Gates on 2012-11-20
> **Bucky Ball said:**
> Hmm, not there. Could have tried mounting from the terminal. Okay, in Gparted, does it show that it is /dev/sda* something? If so, try in a terminal:
```

sudo mount /dev/sda*
```

Of course, replacing the * with the number of the partition. ;)

well I have a lot of sda*'s in my internal hard drive but the external is /dev/sdb with sdb1 and 2mg of unallocated.

---

### Post by Bucky Ball on 2012-11-20
Just a question: you appear to have five partitions there. Do you have any in an extended partition? If they are all primary there could be a problem with UFI or dynamic disks or something. Not my area. 

You could only have four primary partitions on one physical hard drive without the use of an extended partition containing logical drives but UFI seems to do something different.

---

### Post by ahallubuntu on 2012-11-20
What's the point in trying to mount partitions on /dev/sda if the ext hard drive is on /dev/sdb (and not showing up)?

I'd check the external drive's S.M.A.R.T. status just to see if the drive has experienced some sort of failure.  Install smartmontools and/or GSmartControl (graphic version) and check the drive.  Report the results here.

---

### Post by Bucky Ball on 2012-11-20
> **Jacob-Gates said:**
> well I have a lot of sda*'s in my internal hard drive but the external is /dev/sdb with sdb1 and 2mg of unallocated.

Well then, create the mount point:

```
sudo mkdir /mnt/sdb1
```

Then:

```
sudo mount /dev/sdb1 /mnt/sdb1
```

---

### Post by Bucky Ball on 2012-11-20
> **ahallubuntu said:**
> What's the point in trying to mount partitions on /dev/sda if the ext hard drive is on /dev/sdb (and not showing up)?
Obviously there isn't one. Now attempting to mount the right one in the hopes the error might throw some light on the issue. Smartmontools is worth a whirl also if the object is to ascertain whether the HD is dead or dying, which is possible as it appears to have been working fine previously.

---

### Post by Jacob-Gates on 2012-11-20
> **Bucky Ball said:**
> Just a question: you appear to have five partitions there. Do you have any in an extended partition? If they are all primary there could be a problem with UFI or dynamic disks or something. Not my area. 

You could only have four primary partitions on one physical hard drive without the use of an extended partition containing logical drives but UFI seems to do something different.

there should be 6 partitions. the sda3 is my windows but there is sda4 that is extended then sda5 is the ext4 and sda 6 is swap. it is all shown in gparted but not in terminal for some reason.

---

### Post by Jacob-Gates on 2012-11-20
> **ahallubuntu said:**
> What's the point in trying to mount partitions on /dev/sda if the ext hard drive is on /dev/sdb (and not showing up)?

I'd check the external drive's S.M.A.R.T. status just to see if the drive has experienced some sort of failure.  Install smartmontools and/or GSmartControl (graphic version) and check the drive.  Report the results here.

i just noticed your post, my bad. I'll do this now.

---

### Post by Jacob-Gates on 2012-11-20
> **ahallubuntu said:**
> What's the point in trying to mount partitions on /dev/sda if the ext hard drive is on /dev/sdb (and not showing up)?

I'd check the external drive's S.M.A.R.T. status just to see if the drive has experienced some sort of failure.  Install smartmontools and/or GSmartControl (graphic version) and check the drive.  Report the results here.

okay i install it and it shows up in the menu but when I click it I get this message:

Device open failed, or device did not return an IDENTIFY DEVICE structure.

---

### Post by Jacob-Gates on 2012-11-21
anyone have anything else to try?

---

