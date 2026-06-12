---
title: "No fix found online for UBUNTU 14.04 AND NVIDIA GTX 960M driver! Help!"
date: 2017-02-08
forum: Hardware
---

### Post by nvn.bny on 2017-02-08
Hi, 


I recently installed Ubuntu 14.04.01 with Windows 10 (Dual Boot) and am facing issues with the graphics card with both Nouveau and Nvidia despite multiple tries to fix them 


My system has the below config:
DELL Inspiron 7559
Intel Core i7-6700HQ CPU @ 2.60GHz
8 GB DDR3L SDRAM
64-bit OS, x64 based processor
NVIDIA GeForce GTX 960M 4GB GDDR5
1 TB HDD + 8 GB SSD Hybrid Drive Storage


The problems faced by me are 
1. Using Nvidia drivers I face issues such as Login loops (Everytime I enter my password, it keeps returning to the login screen again; log file screen shot [here]("http://imgur.com/a/S7WH9")) and Random freezes.


2. With Nouveau drivers my system does not shutdown and freezes at the Ubuntu Splash screen. I tried 'shutdown -r now' on terminal and also 'Alt-Ctrl-F1/F2' during the freeze but did not help (Terminal screen shot [here]("http://imgur.com/a/1IBfE"))


I also tried below solutions:
1. Purged all previous versions and tried all versions of nvidia drivers
2. Changing .Xauthority file
3. Changing display manager from lightdm to gdm
4. This [solution]("https://ubuntuforums.org/showthread.php?t=2263316") worked for many people but I still got login loop after this. I did get some version compatibility issues while installing the version of nvidia (though it installed completely), don't know if that is the issue.


Can someone suggest some alternate solution! Have been stuck for a week!

---

### Post by Autodave on 2017-02-08
May I ask why you are using 14.04? 16.04 is the most current long term release. I have 2 machines running with higher end Nvidia cards and nothing was done except to install the lastest driver from the repositories.

---

### Post by nvn.bny on 2017-02-09
A few softwares that I need aren't supported by 16.04 So have to stick to 14.04 :(

---

### Post by soulrx403 on 2017-02-24
I used to have ubuntu 14.04 with an Nvidia card and I believe I used the Nvidia proprietary drivers for best performance from here:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

as linked from here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

But then I got a nicer AMD card and upgraded to Ubuntu 16.04 which uses a Linux kernel that doesn't (and will never?) support the proprietary (best performance) fglrx driver and learned the hard way that I specifically needed Ubuntu *14.04[COLOR=#ff0000]**.2**[/COLOR]* and no higher. Not sure if the Linux Kernel versions in the 14.04.x releases play a role with Nvidia though. 

[http://old-releases.ubuntu.com/releases/14.04.2/](http://old-releases.ubuntu.com/releases/14.04.2/)

Might be worth looking into.

---

### Post by cariboo on 2017-02-25
Usually with newer hardware, it is better to go with the latest LTS version, your best solution may be to upgrade to 16.04

---

