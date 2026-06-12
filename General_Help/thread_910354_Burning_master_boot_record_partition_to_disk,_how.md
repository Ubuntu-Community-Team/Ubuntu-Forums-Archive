---
title: "Burning master boot record partition to disk, how?"
date: 2008-09-04
forum: General Help
---

### Post by corkyo4 on 2008-09-04
Hi,

ive just put win4lin on my machine and i now need to install a version of windows, however the version i have on my laptop is buried in a partition that i cant access. But i need to create a cd that i can install xp from, is there a way of accessing this partition and then burning it to disk or is it locked away somewhere i cant get to??

Thanks in advance

Tom

---

### Post by Titan8990 on 2008-09-04
XP discs are plentiful. Ask around your work, school, etc. Someone has one. You can image the partition using something like Clonezilla or DD but you will not be able to make a reinstall disc for a XP install.

---

### Post by bodhi.zazen on 2008-09-04
I guess I am missing the relation of win4lin, the MBR, mounting a windows partition, and making a Windows XP installation disc.

what are you trying to do exactly ?

---

### Post by rbmorse on 2008-09-04
Sounds like he's trying to create a XP virtual machine from a restore partition instead of an installation CD. 

Sorta curious to see if this can be done, myself.

---

### Post by bodhi.zazen on 2008-09-04
> **rbmorse said:**
> Sounds like he's trying to create a XP virtual machine from a restore partition instead of an installation CD. 

Sorta curious to see if this can be done, myself.

FYI : You can restore the windows MBR from Knopix or Ubuntu or almost any live Linux distro.

From the Ubuntu Live CD:

    1. Boot live CD, open a terminal.

    2. Enable The Universe repositories (System->Administation->Software Sources : tic "Community maintained Open Source software (universe)"

    3. Install  ms-sys
        ```
sudo apt-get update && sudo apt-get install ms-sys
```

    4. Restore MBR

        Set up your windows partition :
        ```
ms-sys -p /dev/sda1
```

        Write to MBR :

            2000/XP/2003 :

                ```
ms-sys -m /dev/sda
```

            DOS/Windows 98/NT : 

                ```
ms-sys -w /dev/sda
```




        ```
ms-sys -p /dev/sda1 && ms-sys -m /dev/sda
```
            *change /dev/sda1 and /dev/sda to your windows partition and MBR


        ```
ms-sys -p /dev/<drive>
```
        <drive> = your windows hard partition (/dev/hda1 or /dev/sda1)

        How to : [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
    man page : [http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

    ms-sys -p = write to windows partition
    ms-sys -w = write Microsoft DOS/Windows NT to MBR
    ms-sys -m = write Microsoft 2000/XP/2003 to MBR


From Knoppix :  sudo install-mbr /dev/hda

---

