---
title: "Installing Ubuntu 8.10 on eeepc"
date: 2009-04-15
forum: Hardware
---

### Post by Epidemic_HardyBoy on 2009-04-15
I have a 64gb partition open for it and I want to dual boot with windows, but it is saying that it cannot install on the 64g partition because 

"No root file system is defined.

Please correct this from the partitioning menu."

The menu looks like this

Edit a Partition
  New partition size in megabytes 65711 (64g)
  use as "Do not use the partition." (I tried changing it to ntfs.. No dice)
  Format the partition "Unchecked Box" (I can't check either way.)
  Mount Point "None" (/dos and /windows are the choices)

I am booting the live install off of a 1gb SD card using unetbootin

HELPPPP

---

### Post by MaindotC on 2009-04-15
You can find information on setting up the partition in the Ubuntu installation documentation: [https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)

---

### Post by Epidemic_HardyBoy on 2009-04-15
Ive read through this and it still makes no sense, can somebody dumb it down for me?

---

### Post by Epidemic_HardyBoy on 2009-04-15
and remember! I AM TRYING TO DUAL BOOT ON AN EEEPC

---

### Post by Epidemic_HardyBoy on 2009-04-15
Noticed, I need to use the manual one of course because I want to dual boot, but the 2nd partition will not allow me to install (None of them actually) Any other ideas?

---

### Post by tavzz on 2009-04-15
> **Epidemic_HardyBoy said:**
> and remember! I AM TRYING TO DUAL BOOT ON AN EEEPC

OK...I am a dual boot like you. Here is what I did:

1. I installed Windows and all the software I want.
2. I RE SIZED my hardisk using Partition Magic. After I a realized that I cannot live without Linux on my PC. 

Note: During partitioning the hardisk, decide what sizes you want for your system. I did 4 partitions for the sake of system drive for Windows, Data Storage, Swap Drive for Linux ( small size ) and another for the Linux system.

3. Install the Ubuntu and read carefully the prompts until you get to the prompt on the location of where to install your Ubuntu - it is wise to use the guided resizing wizard or option.

4. Just follow the guided prompts.

You can change the boot options later if you want. 


Cheers...I hope to hear from you soon

---

### Post by Epidemic_HardyBoy on 2009-04-15
> Note: During partitioning the hardisk, decide what sizes you want for your system. I did 4 partitions for the sake of system drive for Windows, Data Storage, Swap Drive for Linux ( small size ) and another for the Linux system.

Explain, I have the 900HA, so for a reason it came with a 64gb open drive partition.(D:) So I dont know if I use partition magic what would happen.

> 
3. Install the Ubuntu and read carefully the prompts until you get to the prompt on the location of where to install your Ubuntu - it is wise to use the guided resizing wizard or option.

Guided installs on the whole right? Im not sure, maybe we can talk through msn

---

### Post by MaindotC on 2009-04-15
Tell me what part of the documentation doesn't make sense.

---

### Post by snowpine on 2009-04-15
> **Epidemic_HardyBoy said:**
> I have a 64gb partition open for it and I want to dual boot with windows, but it is saying that it cannot install on the 64g partition because 

"No root file system is defined.

Please correct this from the partitioning menu."

The menu looks like this

Edit a Partition
  New partition size in megabytes 65711 (64g)
  use as "Do not use the partition." (I tried changing it to ntfs.. No dice)
  Format the partition "Unchecked Box" (I can't check either way.)
  Mount Point "None" (/dos and /windows are the choices)

I am booting the live install off of a 1gb SD card using unetbootin

HELPPPP

Easy. Assuming you are editing the right partition of course. :)
Change "Use as" to a Linux filesystem (ext2 or ext3)--You can't install Linux on ntfs.
Change "format the partiton" to "yes" (obviously).
Change "mount point" to / (which means your root filesystem; this will put Ubuntu in a single partition, which I think is what you want).
You might get a warning about no swap partition, which you can safely ignore.

Good luck!

---

