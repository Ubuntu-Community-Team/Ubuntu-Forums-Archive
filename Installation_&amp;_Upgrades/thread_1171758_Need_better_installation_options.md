---
title: "Need better installation options"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by ehrichweiss on 2009-05-27
First of all, I really like Ubuntu on my Dell laptop....


BUT I can't install it because whoever created the Installer(including the alternate) has utterly missed 95% of the options I'm accustomed to using...

Here's the issue I have and I'm certain that others have had at least some of the same...

1) My drive is setup with the first partition being XP. When I go to install Ubuntu it will not under any circumstances simply give me the option to install it onto the free space on the drive or remove the existing linux partitions and replace them. In order to do anything of the sort I have to tell it to resize my XP partition which is 250+ gig which means I could wait over an hour for it to finish something that dangerous so I'm not keen on seeing if it'll kill that much data all at once. It won't simply leave the damn thing alone and install to the free space. THAT is my biggest issue. 

2) LUKS encrypted partitions *and* swap. Fedora will easily allow me to create an encrypted partition and encrypted swap. If I even try to mess with encryption which only seems usable with the alternate installer, it will let me encrypt the root partition but it refuses to let me encrypt swap for some odd reason. If I can't encrypt the swap partition, I might as well not encrypt anything since the swap is a definite attack vector. NO, I do not want just my /home partition encrypted. I know that's a suggestion but it's not for me. 

So now imagine trying to install Ubuntu to the free drive space on your computer with an encrypted root and swap partition. I'm under the impression it simply cannot be done in the installer's current state. 

I *attempted* to see if I could get Fedora to create the partitions(with encryption) and then let Ubuntu install onto them and failed miserably since it didn't seem to understand LUKS being a part of an LVM(which is how Fedora handles the root/swap with encryption and has worked awesomely thusfar). 

I'd either like some feedback as to how I could accomplish this without having to spend an hour trying to get the installer to accept what I'm telling it to do, or see if someone can work on some better installation options. 

A friend who has been a hardcore Ubuntu fan asked me the other day if Fedora would allow installation to freespace because he had the same issues and was getting sick of it. I gave him my Fedora Live CD and he was thrilled. 

Some come on..someone fix this mess of an installer.

---

### Post by presence1960 on 2009-05-27
If you want to install to free space at the partitioner screen choose the "manual" option. see attached photo.  The next screen will display all your drives and their partitions. Highlight the free space and click Edit. Set the parameters for your new partition and follow the rest of the prompts to install.

If the free space won't display as it should, use the Live CD to create a partition or gparted Live CD to do the same. then try manual install.

---

### Post by ehrichweiss on 2009-06-01
Thanks. That'll help. I was sure I tried that but I could be thinking about 8.10. Any ideas how to get the encryption to work with this?

---

