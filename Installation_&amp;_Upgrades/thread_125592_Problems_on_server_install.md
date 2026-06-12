---
title: "Problems on server install"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by spyke01 on 2006-02-04
ive installed ubuntu before, wiping a hard drive clean in the process, and had no problems, and ive alkso used the live cd oin the system im doing now. heres my system stats:
abit ic7-g skt 478 motherboard
celleron processor(my p4 died)
160gb western digital hard drive
chaintech geforce mx440 video card

ok, i did a server install and got into the shell and then did the following commands in order:

sudo nano /etc/apt/sources.list
--uncommented universe lines
--saved file
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install xubuntu-desktop gdm update manager
sudo /etc/init.d/gdm start

ive done this twice now, the first time i tried gnome not xfce and both times whenever i run X my screen just cuts on and off constantly, nothing gets displayed

i took the defaults on the xconfig where the highest resolution was 1024x768

also when i did the installation heres the partitions i did:
/NOTSURE windows
/boot 50MB
/swap 1GB
/ 20GB

i couldnt do a /var because when i tried making a 10gb / is said the other 10 was unusable so i added that to the / partition

does anyone know what may be causing this, im really wanting to learn to do a server setup in nix, but i cant erase the data on my drive

---

### Post by spyke01 on 2006-02-04
lloks like my problem is that you can only have 4 partitions per disk, do i need /var to get the os to work?

---

