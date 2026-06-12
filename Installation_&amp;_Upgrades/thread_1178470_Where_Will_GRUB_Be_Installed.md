---
title: "Where Will GRUB Be Installed?"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Russell_S on 2009-06-04
Hi, Hopefully someone can give me some advice please.

I want to install Ubuntu 9.04 onto a desktop PC that is currently running Windows. I have installed a second HDD for the Ubuntu Install so none of it will be touching the Windows HDD.

I have gone through the installer up to the disk partitioner part and told it to use the entire disk and selected the second disk.

What I want to know is where will this put the GRUB bootloader. The reason I ask is that I already use a bootloader called Boot-US to select between different Windows installs on the first disk and want to use it to select Ubuntu as well. For this reason I need GRUB to be on the second disk with the Ubuntu install and not on the first disk.

I hope this makes sense.

Regards

Russell

---

### Post by jbruced on 2009-06-04
Hi Russel, be careful.

It'll overwrite the mbr, then install part on the Ubuntu partition, probably break your current configuration.

Read up on the the supergrub website, it'll even show how to make a boot record backup in case things get screwed up. 

My opinion says you'll be better off using grub and replacing what you have now.


Not specific I know, just trying to give an overview opinion.

GL
Bruce

---

### Post by logos34 on 2009-06-04
Jbruced is right, it'll probably overwrite the Boot-US or whatever on the first disk...But it's easy to prevent: when you come the "Ready to install" screen (#7?), press 'Advanced' button lower right and change the location for Grub bootloader from the default '(hd0)' to **/dev/sdb**, or whatever the drive with ubuntu is.  That'll allow you to chainload grub from the windows/boot-us bootloader, AND be able to boot the ubuntu disk directly from the Bios in a pinch.

---

### Post by Russell_S on 2009-06-04
Many thanks to both of you.

I've already installed on a laptop and I didn't remember seeing an option to specify where to put GRUB. However, I didn't look in the advanced options in screen #7.

I'll give it a go and see. What's the worst that can happen :cry:


I'll let you know how it goes. Thanks once again.


Russell

---

### Post by logos34 on 2009-06-04
> **Russell_S said:**
> 
I've already installed on a laptop and I didn't remember seeing an option to specify where to put GRUB. However, I didn't look in the advanced options in screen #7.


I doublechecked.  **Advanced** button lower right (hardly anybody notices it) .  Here:

[IMG]http://www.psychocats.net/ubuntu/images/installingjaunty11.png[/IMG]

---

### Post by Russell_S on 2009-06-04
Hi again,

Yes that worked fine. I'm actually writing this post from the new Ubuntu install. Also, it hasn't screwed up the windows install, which is a bonus.

At the moment I'm booting into Ubuntu using the BIOS boot menu and selecting the second disk. I now just need to configure my Boot-US bootmanager and everything should be hunky dory.


Thanks for you help yet again.


Russell

---

### Post by logos34 on 2009-06-04
ok, enjoy

---

