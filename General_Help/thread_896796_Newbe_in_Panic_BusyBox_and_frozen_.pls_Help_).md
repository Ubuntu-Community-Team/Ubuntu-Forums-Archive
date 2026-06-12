---
title: "Newbe in Panic: BusyBox and frozen .pls Help :)"
date: 2008-08-21
forum: General Help
---

### Post by josolu on 2008-08-21
Hi,

I installed a couple of months ago Ubuntu 8.04 TLS in my laptop.
Everything smooth until yesterday.

I made a few of the automatic updates and everything went fine.
When I boot it this morning, after the Ubuntu logo with the sliding bar below it went to a terminal screen with the message:

Busy Box v1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in shell (ash).

I can not make it go out of there.

If I CTRL+ALT+F1 I get another terminal with the following:
"
Starting up ...
Loading, please wait...
kinit: name_to_devt(/dev/disk/by-uuid/cb109a58-3aea-40f9-965e-5ca5a833cc54) = sda5(8,5)
kinit:trying to resume from /dev/disk/byuuid/cb109a58-3aea-40f9-965e-5ca5a833cc54
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init
_
"


I have tried to boot from the Ubuntu CD but it does not even read the CD ...

Please, can anyone help me to boot it up again, if possible without loosing the contents of the HD ?

Really thanks a lot in advance :confused:](*,)!!

---

### Post by Stemp on 2008-08-21
Did you try to boot up with the recovery choice in Grub or even with an older kernel ?

---

### Post by josolu on 2008-08-22
> **Stemp said:**
> Did you try to boot up with the recovery choice in Grub or even with an older kernel ?
Yes.
I booted up with all the existing and different kernels in Grub, normal and recovery, but exactly the same result --> no result.

Thanks.

---

### Post by Stemp on 2008-08-22
> I have tried to boot from the Ubuntu CD but it does not even read the CD ...

That's a big problem, without a live-cd I don't know what to do :(

---

### Post by josolu on 2008-08-23
Hi Stemp, thanks a lot.
After playing for a while with the Bios set-up I managed to start the laptop up from the live CD.

Can we give it another try? How can I restore my machine with the live CD?

Thnaks a lot for your help (your last comment made me almost jump out of the window /though the laptop away ;) ).
Regards,

jose

---

### Post by Stemp on 2008-08-23
My first advice is to backup your importants data.
Then to try : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#From%20Inside%20Ubuntu](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#From%20Inside%20Ubuntu)

---

### Post by josolu on 2008-08-24
> **Stemp said:**
> My first advice is to backup your importants data.
Then to try : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#From%20Inside%20Ubuntu](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#From%20Inside%20Ubuntu)
How do I do the backup?Thnx

---

### Post by josolu on 2008-08-24
> **josolu said:**
> How do I do the backup?Thnx
Whn I open a terminal from the liveCD, I can not find anything of my previous system.

Within the home directory there is only an ubuntu user, and not those I had in my HD.

How can I access that to make the backup?

Thnx

---

### Post by Stemp on 2008-08-24
Something like that :
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

Just forget the windows (ntfs/fat32) part ;)

---

### Post by josolu on 2008-08-24
Hi again Stemp,
first of all a 1000 thanks to you. You can not imagine how relieving it is to know that there is someone there with a lot more of experience and knowledge to guide me...THANKS !

I think I am doing something wrong because it did not work:

I made the following:

sudo mkdir /mnt/linux (OK)
sudo mount /dev/sda1 /mnt/linux (OK) --> All my previous system is then there at /mnt/linux !

cd /mnt/linux/sbin (OK)
sudo ./grub --> FAILED. I do not have a "grub" file there. I have a 'grub-install' instead.
When I run it it asks me for parameters:

grub-install [options] install_device

I try the following:

sudo ./grub-install sda1

and it tells me "format of install device not recognized"

???

Again thanks a lot.

---

### Post by Stemp on 2008-08-24
grub doesn't use sda1 sdx etc.... it use a different system.

[https://help.ubuntu.com/community/GrubHowto#Command%20line](https://help.ubuntu.com/community/GrubHowto#Command%20line)

---

