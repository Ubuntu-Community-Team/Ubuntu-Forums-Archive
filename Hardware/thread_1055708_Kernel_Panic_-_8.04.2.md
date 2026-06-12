---
title: "Kernel Panic - 8.04.2"
date: 2009-01-31
forum: Hardware
---

### Post by wordslinger on 2009-01-31
I have been very happy with Ubuntu until I updated my Acer Aspire One Netbook with 
**linux-image-2.6.24-23-generic *(linux kernel image for version 2.6.24 [17MB])*** that was done via the Update Manager.

The next thing was a requirement to restart my netbook, which I did and then all went to HELL.

My Netbook restarted but crashed and the only thing I see on the screen was - *Kernel panic - not syncing: Attempted to kill init!*

Right now, I am using PCLinuxOS from my desktop to post this.

Has anyone any idea what is going on? Is there a way around this. I can't use my Netbook at all. Not at all.

---

### Post by Toddy on 2009-01-31
Same thing happened to me this morning with my Acer Aspire One.  From the GRUB menu, I was able to select the previous "Ubuntu 8.04.2, kernel 2.6.24-22-generic" entry to get back into a working version.

---

### Post by wordslinger on 2009-01-31
The things is I can't even do that. I simply can't use my Acer Netbook at all. I wonder why the Ubuntu Team is not doing something about this. Is this not a serious flaw for them?

---

### Post by Hauke_1 on 2009-02-01
Hello!

I have the same problem with my Aspire One. 

When booting I pressed ESC to get into GRUB-loader-menu. Then I was able to select an older kernel (i. e. 2.6.24-22). This worked out for me!

---

### Post by Toddy on 2009-02-01
I see that this bug has been documented:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322867]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322867").

It is noted that booting with acpi=off does seem to allow the computer to boot.

---

### Post by LeeU on 2009-02-01
> **Hauke_1 said:**
> Hello!

I have the same problem with my Aspire One. 

When booting I pressed ESC to get into GRUB-loader-menu. Then I was able to select an older kernel (i. e. 2.6.24-22). This worked out for me!

Is there a way to change permanently to the previous kernel so that we don't have to keep doing the above each time at boot-up?

---

### Post by ajayre on 2009-02-02
Same thing just happened to me...thanks a lot Canonical...

---

### Post by theozzlives on 2009-02-02
> **LeeU said:**
> Is there a way to change permanently to the previous kernel so that we don't have to keep doing the above each time at boot-up?

Assuming the Ubuntu on Net Books is the same as P.C.s, install startup-manager (it'll be in System > Administration), there you can select which kernel you want as default.

---

### Post by Richard Mathie on 2009-02-04
as Dan Smith says here:[https://answers.launchpad.net/ubuntu/+question/59086](https://answers.launchpad.net/ubuntu/+question/59086)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list.backup
```

then 

If you open the /boot/grub/menu.lst in a text editor 
(```
sudo gedit /boot/grub/menu.lst
```)
you should see the following:

title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=760a8640-4d3a-4240-9e13-04571cb97e80 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=760a8640-4d3a-4240-9e13-04571cb97e80 ro single
initrd /boot/initrd.img-2.6.24-23-generic

..
..
.older kernel images
..
Comment it out to look like the following:

#title Ubuntu 8.04.2, kernel 2.6.24-23-generic
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=760a8640-4d3a-4240-9e13-04571cb97e80 ro quiet splash
#initrd /boot/initrd.img-2.6.24-23-generic
#quiet

#title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=760a8640-4d3a-4240-9e13-04571cb97e80 ro single
#initrd /boot/initrd.img-2.6.24-23-generic

..
..
.older kernel images ect ect
..

:D

besides now might be a good time to upgrade to intrepid! :S
[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L) (the SSD version)

though i here 2.6.27-11 breaks the wired Ethernet,

---

### Post by sycho on 2009-02-04
Same problem here with Xubuntu on AAO after the kernel update :(

---

### Post by wordslinger on 2009-02-13
Good Bye People..... and Keep Well....

---

### Post by wordslinger on 2009-02-13
I give up. I had to. I can't be using PCLinuxOS to do serious work in the office. Now, I'm back on Windows XP Professional (Service Pack 3) after almost 2 years on Linux.

Ubuntu let me down. The problem with 8.10 is the wireless and wired connectivity. The problem with 8.04.2 is the unreliability.

I feel humiliated running back to Windows. Sigh....

---

