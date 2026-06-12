---
title: "Backup Ubuntu installation"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by melopsittacus on 2008-12-26
Hello!

I am looking for a solution to back up my working environment on a custom install CD from which I can reinstall it quickly and easily in case of crashes. I thought I would make a copy of the system about once a month onto a CD. I intend to back up only the operating environment: my data and work is stored on a separate partition (accesible through /media/somedir), and I would back it up in another way (because it is much more large and would not fit on the CD of the working environment).

The needed requirements are the following:
- keep EXACTLY the installed packages:
    there are some packages on the default install CD that I do not need, but there are some packages installed later that are needed
in addition not all packages are installed from the official repository: some were available only as .dpkg and were installed manually

- keep the installed version for each package:
    so that there is no need to do any upgrade in case of reinstall

- keep custom configuration and settings for each package:
    for instance the /etc/* and /home/USERNAME/.* files

- do not store any unnecessary files:
    for instance contents of /tmp

The question is, which is the best approach to achieve this?

Those I found so far are the following:

- mirror the contents of the system partition with dd command (perhaps excluding the unneeded directories)
   disadvantages: uses a lot of space, and maybe I am not able to correctly guess the needed items (there may be unneeded items other than /tmp)

- get the list of currently insatalled packages (sudo dpkg -get-selections > packages.txt) and invoke dpkg with those packages (sudo dpkg -set-selections)
   disadvantages: it does not save the packages themselves, only a list of them, so that I would actually need to redownload them which may take a lot of time; it does not save custom settings and this solution does not deal with packages added "manually" (through dpkg -i <packagename.deb>) -- of course these packages would appear in the list, but they would not be available for install as they are stored locally

- use a special utility (called remastersys) to clone an existing installation
   this seems the best solution so far, however:
   it has been reported not to work correctly in some cases (see: [http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html)) -- it does not save the restricted drivers of nvidia, and it does not cope with Hardy.

To summarize, my question is the following:

Is there a tool like "remastersys" but working absolulte correctly with Intrepid Ibex (or Hardy)?
Or is there a better way to make working environment backup than those I have found so far?

------------------------------------------------------------------------

Other question:

The system is set up on an encrypted partition. I do not think there is a way to automatically restore the system within the encrypted partition other than copying the whole partition with dd.

So the reinstall process would look something like this:
- recreate the encrypted partition and encrypted swap manually 
- install all the packages from the custom install CD

For this purpose I would need to create a custom install CD like the "Alternate Installation CD"

However if this is not possible, I am ready to do without encryption and just create an install CD like the "Normal" one.


Thanks for any help

---

### Post by albinootje on 2008-12-26
> **melopsittacus said:**
> 
Those I found so far are the following:

- mirror the contents of the system partition with dd command (perhaps excluding the unneeded directories)
   disadvantages: uses a lot of space, and maybe I am not able to correctly guess the needed items (there may be unneeded items other than /tmp)

I like CloneZilla for making disk images.
It features compressing those images during/after the cloning.

It can do whole disk cloning, or per partition.
If you choose the latter, then you will need to create similar partition (like /dev/hda1 /dev/hda2) as you have made backups of, and you need to think about the partition-sizes as well.

The interface and way of working might take you some time to get used to it.
Why don't you test CloneZilla inside VirtualBox with a few virtual hard disks first ?

---

### Post by dragos_iliescu_2005 on 2008-12-26
Try webmin.

---

### Post by Hydrid on 2008-12-26
Try this System Imager i think that it will do your job.

[http://www.howtoforge.com/how-to-back-up-an-ubuntu-8.10-system-with-systemimager](http://www.howtoforge.com/how-to-back-up-an-ubuntu-8.10-system-with-systemimager)

---

### Post by melopsittacus on 2008-12-27
Albinootje: thanks for the tip -- this seems an easy solution, I'll experiment as soon as I have time

Dragos_iliescu_2005, Hydrid: thank you both for the suggestions, I had a look at the home pages of the mentioned solutions -- however they seem a little difficult to set up. Have you already been using them and if so, about how much time and effort did it take to get them running?

---

