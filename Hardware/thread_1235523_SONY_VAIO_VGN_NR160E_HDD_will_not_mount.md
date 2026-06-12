---
title: "SONY VAIO VGN NR160E HDD will not mount"
date: 2009-08-09
forum: Hardware
---

### Post by rw2003 on 2009-08-09
Hi...

A new UBUNTU user needs a little help using the OS to get to my NTFS formatted HDD.

My wife's Sony Vaio VGN NR160E/Vista laptop machine is having a problem.  It won't boot up anymore - it just goes into the SAFE MODE, etc screen. When I try to boot in a safe mode or any other choice, I just get the same screen back... sort of like a loop.  The blue sceen flashes by quickly each time.

My guess is that I have HDD issue... Maybe some bad sectors,etc???

So I created a Ubuntu 8.04 boot disk and booted her laoptop up and ran from the CD (no install).  Loaded just fine except I was hoping to be able to see her HDD.  Apparently UBUNTU cannot "MOUNT" the drive.  The error msg mentions that the disk is NTFS and was not dismounted(?) correctly??

My goal is to get to the bad HDD and transfer the data to an external drive.  Then replace/reformat the drive and reload the Vista OS, etc.  (I do have a back up of her data files but it is not recent and there are some files on her HDD that I do need to save.)

Any help is appreciated.

Thanks
Rob

---

### Post by esalnoj on 2009-08-09
Did you try mounting the drive from terminal? If not:

In live CD, go to applicatons>accessories>terminal and run the following:

```
sudo mkdir /media/vista
sudo mount /dev/sda1 /media/vista
```

That should get you access to the drive.

To unmount, open terminal and run:

```
sudo umount /dev/sda1
sudo rmdir /media/vista
```

The "a" in /dev/sda1 means which physical drive number, from a to z.
The "1" in /dev/sda1 means first partition on physical drive, from 1 up.

---

### Post by rw2003 on 2009-08-09
Thanks, I'll give it a try.  Is there any danger to the drive to force it to mount manually?

Update..
I issued the above commands to mount the drive and I received an error msg stating that the drive is MARKED FOR USE BY NTFS.  It suggested that I go into VISTA and use the Remove Hardware funtion to release the drive OR I could FORCE the MOUNT in UBUNTU.

Will FORCING the mount create any issues?

Thanks

---

### Post by esalnoj on 2009-08-09
Try the following mount command instead of the first one:
```
sudo mount -a -t ntfs /dev/sda1 /media/vista
```

I'm not sure if forcing the mount will create any issues.

---

### Post by rw2003 on 2009-08-09
> **esalnoj said:**
> Try the following mount command instead of the first one:
```
sudo mount -a -t ntfs /dev/sda1 /media/vista
```I'm not sure if forcing the mount will create any issues.

Ok, I think I successfully got it mounted!  I used your command, but UBUNTU came back with an error msg stating that I needed to FORCE the mount and it suggested an alternate version of the command, which I then proceeded to enter.  The drive mounted and now I can see all of the files that I intend to backup before I attempt to fix the HHD.  Now I will connect and (hopefully) mount an external USB drive to receive the files.  

Thank you very much for responding and helping me through my first UBUNTU encounter.  My next UBUNTU project will be to install on an older Pentium-class machine to see if I can get it up and running for web browsing and email.

Thanks again.
Rob

---

### Post by esalnoj on 2009-08-09
Your welcome. By the way, I forgot to say "welcome to the community".

---

