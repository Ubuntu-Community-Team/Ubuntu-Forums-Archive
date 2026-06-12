---
title: "Errors and hard drive problems"
date: 2008-11-06
forum: General Help
---

### Post by Stalker72 on 2008-11-06
1. I have 2 Western Digital SE16 500GB hard drives set up as RAID 0 using the Nvidia MediaShield utility and enabling RAID in the BIOS.

2. At the partitioning part of the installation, there were several options. I tried the option which installs Ubuntu on the entire disk. Both hard drives were found, one empty and one with 8.04 already installed.

3. After installation, I got an error on boot saying "GRUB Hard Disk Error". I tried to reinstall Ubuntu.

4. After reinstallation, I got another error saying "GRUB loading, please wait... Error 21".

Does Ubuntu support RAID 0? If not, what do you recommend I do with 2 hard drives?

**Thanks for help!**

Stalker72

---

### Post by Stalker72 on 2008-11-07
Bump!

Stalker72

---

### Post by mtausig on 2008-11-07
If you really got a hardware raid controller, you actually should not see two hard disks in the installation routine, but one big disk.
To me, this appears to be either a BIOS-configuration error.

---

### Post by Stalker72 on 2008-11-07
> **mtausig said:**
> If you really got a hardware raid controller, you actually should not see two hard disks in the installation routine, but one big disk.
To me, this appears to be either a BIOS-configuration error.
What is a hardware RAID controller?

What should I do in the BIOS except enabling RAID?

Stalker72

---

### Post by mtausig on 2008-11-07
For the difference between hardware- and software RAIDS, see [the Wikipedia article on RAIDs]("http://en.wikipedia.org/wiki/RAID").

Well, I do not know your BIOS, so I cannot give you a walkthrough. But somewhere, there has to be a point, where you have to tell the BIOS which disks you want to use in the raid, I doubt that it automatically takes all disks available.

One more thing: I would suggest, that you reconsider using a raid at all. Having a raid without sufficient knowledge about it, can be dangerous (to your data). So if you do not have any real good reason for using one, I would leave it.

---

### Post by Stalker72 on 2008-11-09
I went for a RAID 1 setup. Also, I managed to fix every problem and I'm running Ubuntu fine! Thanks! :)

Stalker72

---

