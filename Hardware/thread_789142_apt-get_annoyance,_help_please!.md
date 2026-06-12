---
title: "apt-get annoyance, help please!"
date: 2008-05-10
forum: Hardware
---

### Post by H_a_D_3_z on 2008-05-10
when I install Ubuntu and then try to install new packages, I get this annoying message:

Media change: please insert the disc labeled
‘Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)’
in the drive ‘/cdrom/’ and press enter 

To fix that message, click on 

System->Administration->Software Sources and uncheck the “CD-ROM/DVD” option at the bottom of the menu:

HERE IS MY ?:
I don't have internet access running, and i need to get those files off the cd then what do i do.  I have the cd in the drive, I don't understand.

---

### Post by huler on 2008-05-10
It's simple, my english is very poor I hope you understand me.

You write on terminal:

   sudo gedit /etc/apt/sources.list

when the text editor is opened you will put # before all the lines except 
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted


 You save the file and you put the cd you put on the terminal

  sudo apt-get update

And at the first it would be run

---

