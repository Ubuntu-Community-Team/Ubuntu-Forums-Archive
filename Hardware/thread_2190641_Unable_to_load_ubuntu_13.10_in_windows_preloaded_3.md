---
title: "Unable to load ubuntu 13.10 in windows preloaded 3rd generation laptop"
date: 2013-11-28
forum: Hardware
---

### Post by himadric91 on 2013-11-28
Hi,

We have two laptops model is G500s 3037 with preloaded Windows 8 single edition, and its run with UEFI Mode. now when we try to install ubuntu 13.10 on that system. laptop unable to provide access dvd drive or pen drive. when we change the mode in legacy type then we access the usb port and dvd drive option..after install the ubuntu 13.10 it created multi loader both ubuntu and windows 8 but when we select windows option in that multi loader on that time windows 8 unable to boot. but when we change the bios in UEFI mode then windows boot automatically but ubuntu boot loader is not shown, 

We need dual boot for these laptops. 

Please provide solution.
 
Thanks
Himadri

---

### Post by himadric91 on 2013-12-02
Hi,

we are waiting for solution.

Thanks,
Himadri

---

### Post by oldfred on 2013-12-02
If Windows is UEFI and Ubuntu in BIOS/Legacy/CSM mode you can only dual boot from UEFI/BIOS menu. Once you start booting in one mode you cannot switch in grub menu as they are not compatible.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by himadric91 on 2013-12-03
Hi,

Can we start the above process in legacy mode because in UEFI mode we are unable to get access bootable drive.
Secondly in one of the laptop we installed windows 7 in legacy mode and how can we create duel boot in legacy mode because when we start load ubuntu from usb bootable then ubuntu unable to detect the windows partition table. it shows entire HDD drive as unknown drive.
 
waiting for your solution.

Thanks,
Himadri

---

### Post by oldfred on 2013-12-03
Are we talking about two different systems with different issues? 
Only one per thread or we all get too confused.
Is Windows 7 hibernated?
 Have you resized from inside Windows and rebooted so it can run chkdsk and make repairs. 
Does it have all 4 primary partitions used?

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by himadric91 on 2013-12-04
Hi,

This is our second laptop in that laptop we load windows 7 in a legacy mode. and when we install ubuntu as a duel booting phase then [COLOR=#000000]ubuntu unable to detect the windows partition table. it shows entire HDD drive as unknown drive.

please provide solution.

Thanks,
Himadri[/COLOR]

---

### Post by oldfred on 2013-12-04
Please post this from live DVD or flash drive installer's terminal.

sudo parted -l

---

