---
title: "No-cd install - bcdedit problem ?"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by eukristian on 2009-09-10
[SIZE=2]Hi .
This is my first post . I decided to install and stay with Kubuntu after trying it in a virtual machine . The problem is that I don't want to waste another CD as I have already wasted a few DVDs with distros like OpenSuse and Linux Mint . I heard about methods like Netboot install [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) , but I have a problem when I reboot . 

The message I get is grldr cannot be found or something similar . 

I tried with "bcdedit /set {id} path [/SIZE][FONT=monospace]\grldr" and[/FONT] [SIZE=2]"bcdedit /set {id} path C:[/SIZE][FONT=monospace]\grldr"[/FONT].What am I doing wrong ?
[SIZE=2]
I'm running Windows 7 OEM installed (I already partitioned my HDD and left around 50 GB for the Kubuntu install (I didn't thought about swap partitions though) ) .

Most guides online don't offer solutions for Vista and Win 7 , which don't use boot.ini . You can't simply add [/SIZE][FONT=Verdana]c:\grldr="Install Ubuntu" anymore . [/FONT][FONT=Verdana][SIZE=2]But I managed to solve the problem after encountering some difficulties with bcdedit . 

Thanks for your help . I hope I will be able to give something back to the community in the future. 
[/SIZE][/FONT]

---

