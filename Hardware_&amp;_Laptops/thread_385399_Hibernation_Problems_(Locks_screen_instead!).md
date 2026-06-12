---
title: "Hibernation Problems (Locks screen instead!)"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by ziadoz on 2007-03-15
I can't seem to get hibernation to work on my laptop (Compaq Presario v5000). When I try to hibernate the machine, the screen goes black and the command line cursor comes up blinking, and then the Ubuntu cursor comes back and the screen is locked. It never actually hibernates. 

How can I get it working?

Cheers all :)

---

### Post by vadriaan on 2007-03-15
Hibernation is using swap space to store a 'snapshot' of your memory and it should load this when coming out of hibernation. I am not an expert on this but hibernation does not seem to work properly. I can get hibernation to work, but when I come out of hibernation my [COLOR="Red"]swap partition is gone[/COLOR]. When going into hibernation without a swap partition, you get the result you have experiencing.  

Use *cat /proc/swaps* tp see if your swap space is active,
       *sudo swapon -a* to activate it
       *mkswap /dev/hdax *to make it.

At this stage I need to make and turn swap space on after each return from hibernation.

---

### Post by ziadoz on 2007-03-16
I tried what you recommended.

*cat /proc/swap* gave me no results.
*sudo swapon -a* gave me:
```

swapon: cannot stat /dev/disk/by-uuid/7a45e6bf-7ab6-45d5-a1a6-5f5cf0e8348c: No such file or directory
```

I ran *fdisk -l* and it shows I have a swap partition:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/sda2            7013        9409    19253902+  83  Linux
/dev/sda3            9410        9729     2570400    5  Extended
/dev/sda5            9410        9729     2570368+  82  Linux swap / Solaris

```

---

### Post by vadriaan on 2007-03-17
Having a swap partition and getting Linux to use it seems to be  two different problems.  If  sudo swapon -a gives you an error message eg 'invalid parameters - /dev/hda3' , your swap partition is not recognized by the OS. Try actually making the partition (as far as the Os is concerned) using mkswap before turning it on using swapon.

pre: having a swap/Solaris partition
first : kmswap /dev/hdax
then: swapon -a
then to test it: cat /proc/swaps (notice 's')

/proc/swaps gives me: 
Filename                                Type            Size    Used    Priority
/dev/hda3                               partition       635032  75628   -1

---

### Post by gardara on 2007-03-18
I had a simelar problem but got my hibernation working... Check out this thread: [http://ubuntuforums.org/showthread.php?t=332100](http://ubuntuforums.org/showthread.php?t=332100)

Hopefully it will help you :)

---

