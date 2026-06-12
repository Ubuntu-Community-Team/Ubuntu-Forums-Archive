---
title: "Grub very slow booting"
date: 2004-12-21
forum: General Help
---

### Post by alci on 2004-12-21
Hi,

I've just installed Ubuntu Warty on my parents PC, trying to give them the best and most user friendly of libre software... but I encounter quite a few problems :

1) first and most visible : Grub is very slow to boot (about 90 seconds before it fires Linux boot up).
I first get a "Grut booting ..." (several seconds)
then a "Grub *stage1.5" (another bunch of seconds)
then 3 seconds timeout for menu, and then Linux boots...

I've only got 1 HDD (17GB), and only Ubuntu is installed (default partitionning).

Any hint on that ?

2) My other problem is with usb and a canon powershot A80 digital camera... gthumg freeze on import (gphoto2 command line insterface as well).
In the syslog, I got :
Dec 19 13:27:29 localhost kernel: ohci_hcd 0000:00:07.4: wakeup
Dec 19 13:27:29 localhost kernel: usb 1-2: new full speed USB device
using address 2
Dec 19 13:27:31 localhost usb.agent[3575]:      libgphoto2: loaded
successfully
Dec 19 13:27:31 localhost usb.agent[3575]:      usbcam: loaded
successfully
Dec 19 13:27:58 localhost kernel: usb 1-2: usbfs: interface 0 claimed
while 'gthumb' sets config #1
Dec 19 13:28:03 localhost kernel: usb 1-2: bulk timeout on ep1in

Lost again (found nothing on google for both points)... The PC is quite "old" (2-3 years), this might come from bios config ?????

Thanks for your help,

Franck

---

### Post by trigg on 2005-03-17
[QUOTE=alci]Hi,

I've just installed Ubuntu Warty on my parents PC, trying to give them the best and most user friendly of libre software... but I encounter quite a few problems :

1) first and most visible : Grub is very slow to boot (about 90 seconds before it fires Linux boot up).
I first get a "Grut booting ..." (several seconds)
then a "Grub *stage1.5" (another bunch of seconds)
then 3 seconds timeout for menu, and then Linux boots...

I've only got 1 HDD (17GB), and only Ubuntu is installed (default partitionning).

Any hint on that ?

2) My other problem is with usb and a canon powershot A80 digital camera... gthumg freeze on import (gphoto2 command line insterface as well).
In the syslog, I got :
Dec 19 13:27:29 localhost kernel: ohci_hcd 0000:00:07.4: wakeup
Dec 19 13:27:29 localhost kernel: usb 1-2: new full speed USB device
using address 2
Dec 19 13:27:31 localhost usb.agent[3575]:      libgphoto2: loaded
successfully
Dec 19 13:27:31 localhost usb.agent[3575]:      usbcam: loaded
successfully
Dec 19 13:27:58 localhost kernel: usb 1-2: usbfs: interface 0 claimed
while 'gthumb' sets config #1
Dec 19 13:28:03 localhost kernel: usb 1-2: bulk timeout on ep1in

Lost again (found nothing on google for both points)... The PC is quite "old" (2-3 years), this might come from bios config ?????

Thanks for your help,

Franck[/QUOTE]

I am having a similar problem - though I didn't have the problem with other versions of linux (gentoo, suse, etc. . .).  What format is your root partition (or boot and root if they are different).  I am using reiserfs.  I also have ubuntu on a laptop, but it boots very quickly (grub instantly launches the kernel boot process - whereas on my desktop it takes about a minute) even though the laptop is "slower" and has less memory  (256 vice 512) than my desktop.  My latop, however, uses ext3 vice reiserfs - maybe the initrd is spending time trying to use ext3 vs. reiserfs??

Anyone else having this problem?

trigg

---

### Post by Bicet on 2005-03-17
[QUOTE=trigg]I am having a similar problem - though I didn't have the problem with other versions of linux (gentoo, suse, etc. . .).  What format is your root partition (or boot and root if they are different).  I am using reiserfs.  I also have ubuntu on a laptop, but it boots very quickly (grub instantly launches the kernel boot process - whereas on my desktop it takes about a minute) even though the laptop is "slower" and has less memory  (256 vice 512) than my desktop.  My latop, however, uses ext3 vice reiserfs - maybe the initrd is spending time trying to use ext3 vs. reiserfs??

Anyone else having this problem?

trigg[/QUOTE]
 I've got the same problem, using reiserfs

---

### Post by trigg on 2005-03-18
[QUOTE=Bicet]I've got the same problem, using reiserfs[/QUOTE]

Are you running Warty or Hoary?   I am running Hoary, so I just wondered if the problem exists in Warty.

---

### Post by Bicet on 2005-03-19
I'm also running hoary ;)

---

### Post by trigg on 2005-03-20
[QUOTE=Bicet]I'm also running hoary ;)[/QUOTE]

I see that there a much more versatile section for Hoary now - so I suppose that this thread should be moved there since it appears that those involved are using that version- though I am not sure it is singularly related to hoary vice warty.  Anyhow, I modified the mkinitrd/mkinitrd.conf to stipulate that it should check for and use only the necessary modules (dep), then  attempted to recreate the initrd with the command:

```
sudo mkinitrd -o initrd.img-2.6.10-5-k7.trigg
``` 

but no initrd.im.blah-blah-blah was created so I am not sure if I am doing it correctly. I  have the headers installed but not the source - so I don't know if that has anything to do with it. . . anyway if anyone has some advice on creating a new initrd.img off of an already existing base kernel - please advice. 


trigg

---

### Post by pirast on 2005-10-23
If you still have this problem please help solving it:

[https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245](https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245)

---

