---
title: "noob - installation problems"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by jemmar on 2009-04-26
Hi,

Sorry this is so long, please excuse my ignorance :)

I'm having some problems installing ubuntu 9.04 on my samsung nc10. I have the installation on my usb drive. I wanted to install it side by side with XP, so selected the option to do that and let it sort out the partition sizes by itself.  During the installation I got a message saying 'grub-install /dev/sda' failed'. I clicked OK and the installation finished. Everything seemed fine, as I didn't know what grub was at the time. When I restarted my comp, I didnt get any option to choose ubuntu or xp and it went straight into xp.
I looked on the forums and found out what grub is, and how to fix it. I restarted again and was faced with the grub cli instead of the menu to choose an os. I don't know any commands for the cli, so I was stuck. I restarted again and booted from the usb so I could use the disc version.
My stepdad suggested re-installing ubuntu, seeing as grub was fixed and we thought it would write over the previous installation. Instead it created another partition, and I still got the error about grub.
Now I have two installations of ubuntu and I can't get into either of them, or xp. My stepdad said to delete the partitions with ubuntu on and start again, but as the only thing I can get onto is the disc version of ubuntu, I can't delete the partitions cos they say they are in use!

Can anyone help? I've ballsed it up entirely!

---

### Post by marsrover on 2009-04-26
OK chill dude download partionlogic from another computer and burn the iso to a disk (you are realy a noob if you don;t know how tu do that) 

then boot the broke pc with partion logic (graphial interface) ok now delete both partions from the failed versions of ubuntu

try booting into windows again

if it don't work.....................

somewhere in partion logic there is a option to write a boot menu
make the boot menu so it boots from (eg. partion 1 sata nfts or hpfts) somthing like that

enjoy windows

redownload ubuntu

install

enjoy

ahhhhhhhhhhhhhhhhhh:KS


> **jemmar said:**
> Hi,

Sorry this is so long, please excuse my ignorance :)

I'm having some problems installing ubuntu 9.04 on my samsung nc10. I have the installation on my usb drive. I wanted to install it side by side with XP, so selected the option to do that and let it sort out the partition sizes by itself.  During the installation I got a message saying 'grub-install /dev/sda' failed'. I clicked OK and the installation finished. Everything seemed fine, as I didn't know what grub was at the time. When I restarted my comp, I didnt get any option to choose ubuntu or xp and it went straight into xp.
I looked on the forums and found out what grub is, and how to fix it. I restarted again and was faced with the grub cli instead of the menu to choose an os. I don't know any commands for the cli, so I was stuck. I restarted again and booted from the usb so I could use the disc version.
My stepdad suggested re-installing ubuntu, seeing as grub was fixed and we thought it would write over the previous installation. Instead it created another partition, and I still got the error about grub.
Now I have two installations of ubuntu and I can't get into either of them, or xp. My stepdad said to delete the partitions with ubuntu on and start again, but as the only thing I can get onto is the disc version of ubuntu, I can't delete the partitions cos they say they are in use!

Can anyone help? I've ballsed it up entirely!

---

### Post by bacardiandwatermelon on 2009-04-26
I think you might be able to rebuild grub following these instructions... May fix things for ya.

[http://ubuntuforums.org/showpost.php?p=1308395]("http://ubuntuforums.org/showpost.php?p=1308395")

---

