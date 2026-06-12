---
title: "Problems upgrading kernel on flash drive"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by squeakysnail on 2009-02-20
hello, i know that this topic has been posted at other places

([http://kubuntuforums.net/forums/index.php?topic=3089474.new#new](http://kubuntuforums.net/forums/index.php?topic=3089474.new#new)) for example, but they all are giving the same solution to the problem i have and sadly it's just not working for me... 

i am currently running xubuntu 8.10 (i believe) on a 32gig flashdrive, and I am trying to update it so that I can use the video card on the computer im connected to / run compiz and all of that wonderful stuff.

so basically here's the problem, 

I type in 

sudo apt-get upgrade

and upon doing that terminal spits out:

jake@ubuntu:~$ sudo su
root@ubuntu:/home/jake# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
dont **** up please
Failed to symbolic-link boot/initrd.img-2.6.27-7-generic to initrd.img.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/jake# 

i was instructed to use root priveleges to do this from the other forum which i liked further up on my post.

I tried the solutions provided in the tut. and it did not work, if there is any other information I need ot provide please let me know, and if this problem has been solved in a way other than the one I have found, then I am sorry for reposting but i've been searching for over an hour and couldnt find any alternatives. 

thank you very much in advance

---

### Post by squeakysnail on 2009-02-20
p.s. I'll be honest im sort of a noob with xubuntu... i know some basics but i'm not great with it.

---

