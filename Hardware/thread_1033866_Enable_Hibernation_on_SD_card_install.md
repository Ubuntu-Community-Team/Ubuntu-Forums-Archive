---
title: "Enable Hibernation on SD card install"
date: 2009-01-07
forum: Hardware
---

### Post by KenBW2 on 2009-01-07
I've heard that Hibernation works on the eeepc (701, since you ask). I've got Ubuntu installed onto an SD card so I don't get this benefit. I can only assume the SD card isn't being mounted in time (although I don't see why that's an issue since the internal SSD isn't involved at boot time). The internal SSD is only 2GB so that's not really an option.

Thanks in advance for any help

---

### Post by KenBW2 on 2009-01-08
*bump*

---

### Post by sdennie on 2009-01-08
What is the output of:

```

free -m

```

---

### Post by KenBW2 on 2009-01-08
```

kenneth@kenneth-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           493        400         93          0          6        160
-/+ buffers/cache:        233        260
Swap:         1011          0       1011

```

If you're tryng to see if I have swap it's on the same SD card as /.

---

### Post by KenBW2 on 2009-01-08
No ideas?

---

### Post by KenBW2 on 2009-01-09
None?

---

### Post by sdennie on 2009-01-09
I'm not sure I understand your problem completely but, it could be a problem with the initrd image.  Try:

```

lsmod | grep mmc

```

Look at the left column and add all those modules to /etc/initramfs-tools/modules.  Then run:

```

sudo update-initramfs -u

```

Hibernate and see if it works.

---

### Post by sdennie on 2009-01-09
Thinking about it, you should also do a:

```

blkid

```

Find the swap partition UUID and make sure it's the same as what you see in /etc/initramfs-tools/conf.d/resume.  If not, change it and use the update-initramfs command above.

---

### Post by starcannon on 2009-01-09
I have never tried to hibernate either of my eee 701's, nor my eee 702; I do however use suspend regularly, and require it to be able to bring /home back from the SD card. The easiest way would be to grab the custom kernel from [Array.org]("http://array.org/ubuntu/setup.html") these kernels are built specifically for the Eee and follow sdennie's advice. I am running 8.10 on my eee's and using the lean kernel, it is very very nice; I would recommend trying that, and I would be very interested to hear how it turns out.

GL and have fun.

P.S. I recommend puppeee for the 2g, [http://www.linux.com/feature/131070](http://www.linux.com/feature/131070), I had the 2g for awhile and this was in my opinion the best solution for that machine; though I will say that I never tried it with the array.org kernels. It was pretty cool, the entire puppeee OS fit in under 800mb leaving plenty of room on the 2g internal SSD for more pups and then I used an 8g SD card for a semi permanent sort of thumb drive where I kept all of my documents, pictures, etc... kinda like /home but a bit more tedious.

---

### Post by KenBW2 on 2009-01-09
@sdennie

I seem to be having a few problems with your commands - there's nothing in lsmod | grep mmc. Here's the output of all the things you suggested:
```

kenneth@kenneth-laptop:~$ lsmod | grep mmc
kenneth@kenneth-laptop:~$ cat /etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
kenneth@kenneth-laptop:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="8c847a80-86d7-4794-9a01-c0528af4cfd9" TYPE="ext2" 
/dev/sdb1: SEC_TYPE="msdos" UUID="4898-454B" TYPE="vfat" 
/dev/sdc1: UUID="4812-88ED" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb2: UUID="b46d0906-e14d-4654-ba34-8f54528d6053" TYPE="swap" 
/dev/sdb3: UUID="6c95fe0f-773b-4927-a3ef-154a17c19794" TYPE="ext2" 
kenneth@kenneth-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=b46d0906-e14d-4654-ba34-8f54528d6053
kenneth@kenneth-laptop:~$ 

```

/dev/sda is the internal SSD
/dev/sdb is the SD card
not sure what sdc and loop0 are...

Hope this helps

@ starcannon

I have eeeXubuntu installed on the internal SSD, had a similar setup for files (it was /media/disk). I have the array.org kernel installed but I can't say it's provided much improvement tbh

---

