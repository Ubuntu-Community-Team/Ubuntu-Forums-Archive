---
title: "Problem with booting in Ubuntu Jaunty"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by DieUbunt on 2009-09-16
Hi,  All started when I decided to install python3.0 and disinstall python2.6. Now I can't boot rightly and I have the following problem : 

kinit:/olev/disk/by-uuid/.......cad kinit: No resume image, doing normal boot image and start asking login and password in tty1. No Ubuntu desktop and normal graphic interface. I have only shell.  

I tryed to give commands : 

sudo apt-get autoremove
sudo apt-get purge vim vi
sudo apt-get update upgrade

sudo apt-get -f install but I have the following messages :

Configure vim (2:7.2.079-1ubuntu5) ... update-alternatives: impossible create symbolic link /usr/share/man/pl.UTF-8/man1/vi.1.gz.dpkg-tmp to /etc/alternatives/vi.pl.UTF-8.1.gz: No file or directory dpkg: error processing vim (--configure):  the sub-process post-installation script gave back an error code 2 Configure vim-gnome (2:7.2.079-1ubuntu5) ... update-alternatives: impossible create symbolic link /usr/share/man/pl.UTF-8/man1/vi.1.gz.dpkg-tmp to /etc/alternatives/vi.pl.UTF-8.1.gz: No file or directory dpkg: error processing vim-gnome (--configure):  the sub-process post-installation script gave back an error code 2 Occurred any errors processing:  vim  vim-gnome E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to give commands :

ls -ld /etc
ls -ld /etc/alternatives
ls -ld /etc/alternatives/vi.pl.UTF-8.1.gz

and the output by previous order is :

1. drwxr-xr-x 160 root root 12288 2009-09-16 10:48 /etc
2. drwxr-xr-x 2 root root 12288 2009-09-15 12:47 /etc/alternatives
3. ls:Impossible accessing to /etc/alternatives/vi.pl.UTF-8.1.gz:no file or directory

 Could Somebody help me? Could I resolve these problems without reinstallation? Alternatively could I fresh my Ubuntu Installation without losing settings and data on it? Thanks in advance

---

