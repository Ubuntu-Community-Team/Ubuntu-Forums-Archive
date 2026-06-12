---
title: "Grub problem adding 3rd OS"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Rambar on 2009-11-06
I dual boot in Vista and Ubuntu, but this morning I tried to make a little Debian partition to experiment and learn more about Linux. So, I shrunk my Data parition *ntfs so I can acces via Win and Linux*, left 6gb and proceeded to install Debian.
Here comes the first problem. I rebooted the comp and grub told me *Invalid filesystem*. So I think 'No worries, the Debian installer will recognise Ubuntu and write over Grub'. I used my spare 6gb to make an EXT3 filesystem, and told the installer to use Ububtu Swap partition as swap. But it didnt work. In fact, I cant even mount my Ubuntu partition because its EXT4. Windows and Debian do  work though, although I havent still managed to get Debian online.
Id like to repair my Grub so that I can boot again into Ubuntu. If not, I guess I could reinstall ubuntu over its old partition, but my bootable pendrive stopped working after I installed Debian. Here's my HD status.

```

dev/sda1 Windows Recovery partition
dev/sda2 Windows Partition
dev/sda3 extended
  dev/sda5 Ubuntu filesystem
  dev/sda6 Swap space
  dev/sda7 ntfs data partition
  dev/sda8 Debian EXT3 partition

```


I hope someone can help me correcting this issue. I have acces to the Fedora 12 Beta Livecd to repair this, but Ubuntu CD and USB mem dont work ><.

Thanks!

---

### Post by Rambar on 2009-11-06
no help at all? :(

---

### Post by presence1960 on 2009-11-06
what version of ubuntu are you running? Also do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Rambar on 2009-11-06
I cant do that, as I have no working ubuntu livecd. I'll try doing it from Debian, the active Grub is in there.

Thanks for the help, I'll be done in a min

---

### Post by presence1960 on 2009-11-06
you really should make a Live CD/USB as how are you going to do needed repair functions (such as now)? I would burn one and keep it handy.

---

### Post by Rambar on 2009-11-06
I have a Fedora LiveCD. Its just that Ubuntu USB stopped working misteriously.

Anyways Im having issues to do this, Fedora wont let me, something happened in RL and suddently I have to be in the other side of the town in half and hour, so I fear this will have to wait *sorry*.

Thanks a lot for the help, I hope I can fix tomorrow after solving this.

---

