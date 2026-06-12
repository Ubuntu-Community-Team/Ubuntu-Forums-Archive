---
title: "differences between installing ubuntu via Wubi and installing UBuntu directly !"
date: 2008-11-04
forum: General Help
---

### Post by anhvu2875 on 2008-11-04
the title said but not all , i wanna ask more :
Ubuntu via Wubi will contain **all** functions of Ubuntu like directly installed Ubuntu ?
THANKS !

---

### Post by mikewhatever on 2008-11-04
Here you go [http://wubi-installer.org/faq.php#internals](http://wubi-installer.org/faq.php#internals).

---

### Post by gnuvistawouldbecool on 2008-11-04
Using Wubi only slows ubuntu down a bit.  Other than that it is exactly the same in almost every way.  It also eliminates the chances of the user wiping the entire disc and losing everything, as it makes a virtual disc instead.

A drawback of this is that to my knowledge you can't make a /home virtual disc, so you can't reinstall and keep the same home folder.  Another drawback is that anything that can screw with the Windows boot loader will make Wubi unavailable as well, as it needs the Windows bootloader to work.  AFAIK (I haven't tried it) the distribution upgrades are a little risky as well.

But if you're only trying Ubuntu, and don't want the risk of deleting everything, use Wubi.

Also, if your computer has a broken/no CD drive, Wubi will still work as it can download the disc.

---

### Post by ago on 2008-11-04
> **gnuvistawouldbecool said:**
> 
A drawback of this is that to my knowledge you can't make a /home virtual disc, so you can't reinstall and keep the same home folder.
Yes you can, there is even a script in the wubi guide. If you want to do it manually from a terminal:

#create a large empty file
dd if=/dev/zero of=/host/ubuntu/disks/home.disk bs=1M count=2000

#format it
mkfst.ext3 -F /host/ubuntu/disks/home.disk

#move the old /home
sudo mv /home /home.old
sudo mkdir /home

#mount it
sudo mount -o loop /host/ubuntu/disks/home.disk /home

#copy over all the files
sudo cp -a /home.old/* /home

#add a new line /etc/fstab
echo "/host/ubuntu/disks/home.disk /home ext3 loop 0 0" | sudo tee -a /etc/fstab

---

