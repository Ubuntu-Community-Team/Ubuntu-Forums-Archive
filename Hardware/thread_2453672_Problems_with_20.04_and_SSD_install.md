---
title: "Problems with 20.04 and SSD install"
date: 2020-11-15
forum: Hardware
---

### Post by Sigma1 on 2020-11-15
Hello to all,
I made a clean install of 20.04 on a new and newly formatted SSD drive, with 30GB for / and the remaining 450GB for /home. Things appear to run well, but after a day or two of use, /var/log/ fills up, in particular kern.log and syslog. I could not easily identify the error messages, but I did get a fifo error on shutdown. I can keep things running by removing kern.log and syslog, recreating the files and making them read-only wuth chattr... but it's not really a solution and, after two more attempted installations, I've gone back to 18.04.
I did wonder if the SSD might be at fault, but there are no problems with 20.04. Conversely, 20.04 runs fine if I install it on the standard HD.
I haven't seen this issue raised elsewhere; any help would be appreciated... even if, for the time being, I'm happy to stick with 18.04.
G.

---

### Post by oldfred on 2020-11-15
What brand/model system?
Have you updated UEFI and SSD firmware?

Some systems have this type of issue:
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by Sigma1 on 2020-11-15
Thanks for your answer, oldfred.
Brand: A Dell Precision 1700. Would sudo lshw be any help?
As for the SSD update, is this something I would via the BIOS?
I'm using legacy boot, so I'm not sure whether UEFI update is relevant.
It looks, from my quick perusal of the links you gave me, as if the "pci=nomsi" grub option might be worth exploring.
Many thanks for this. Will update the thread with feedback if I advance.

---

### Post by oldfred on 2020-11-15
If an update is available, you should install it.
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Newer Dell can install updated directly from Linux. Older ones either from Windows or download update file to FAT32 partition and run update from inside UEFI. 

And most SSD need firmware update. 
My Samsung NVMe drive had a bootable ISO. But Samsungs firmware update tool Magician is primarily a Windows tool. The Linux version is hidden and only in the commercial area of support and did not work or work well with my system.

Did you install the video driver for your system?
lspci -vnn | grep VGA -A 12
sudo lshw -c display
#What is installed
dkms status

---

