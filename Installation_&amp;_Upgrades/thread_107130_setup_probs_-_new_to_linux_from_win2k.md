---
title: "setup probs - new to linux from win2k"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by bdd4 on 2005-12-22
i'm brand new to linux. have these questions:

my system:1.5GHz Athlon,40GB HD,1GB ram

1. how do i setup/adjust screen size for my ati 9600 video card only get 640/480 ?

2. how do i make clamav-0.87 antivirus program i downloaded run ? 

3. how do i access the command prompt ?

4. how can i find and print a copy of my setup configuration e.g. /root /boot /swap memory sizes etc ?

5. how can i load/install/run  my windows 2000 applications ?

thx

bdd4

---

### Post by rjwood on 2005-12-22
1) from terminal:sudo dpkg-reconfigure xserver-xorg--then accept the default's.
2)either from terminal or command line or 'run application'---type: clamav
3)applications>accessories>terminal
4)system>admisistration>device manager is one way
5)sorry-can't help you there---I don't use windows

---

### Post by localzuk on 2005-12-22
1: Take a look at [http://www.ubuntuforums.org/showthread.php?t=106239&highlight=change+resolution](http://www.ubuntuforums.org/showthread.php?t=106239&highlight=change+resolution) and [http://www.ubuntuforums.org/showthread.php?t=107067&highlight=change+resolution](http://www.ubuntuforums.org/showthread.php?t=107067&highlight=change+resolution) for information about resolution changing.

2: The easiest way to get clamav installed is to use synaptic. Take a look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) on how to enable the 'universe' and 'multiverse' repositories (bear in mind this is for hoary, so change the references to breezy where required). Then just select clamav from in synaptic.

I will question why you want anti-virus software though?

3: Press Alt+F2 and type 'gnome-terminal' or select it from the Applications/Accessories menu.

4: Type ```
fdisk -l
``` This will display the partition tables. To put it into a text file type ```
fdisk -l > partition.txt
``` This will put the output into a file called partition.txt in the current directory. If you wish to look at the space on the disks type ```
df -h
``` and again, if you want to put it in a file just use the > out.txt format.

5: You may be able to run some of your windows applications using 'wine' take a look at their website [http://www.winehq.com/](http://www.winehq.com/) for information about it. You will not be able to use all windows applications.

Hope this helps.

---

### Post by bdd4 on 2005-12-22
Thank you very much. Microsoft would
never answer so promptly.

The best to you....

bdd4

[QUOTE=rjwood]1) from terminal:sudo dpkg-reconfigure xserver-xorg--then accept the default's.
2)either from terminal or command line or 'run application'---type: clamav
3)applications>accessories>terminal
4)system>admisistration>device manager is one way
5)sorry-can't help you there---I don't use windows[/QUOTE]

---

### Post by bdd4 on 2005-12-22
Thank you so much for your help.
Why antivirus ? - I asked a ubuntu user friend 
what antivirus program is available. He said he
uses clamav. I have heard viruses have not
been a prob with linux. I am coming from win2k 
and a most recent problem - virus forced my system
into a boot loop. I can't reinstall Win2k. I installed 
ubuntu on a clean 40GB drive. Soon I will reconnect 
my two virus infected 120GB HDs. I want to try to rescue
my files from them. Before my ubuntu installation 
i had lindows (linux) installed and could "see"
my win2k files from linux. 

I want to have an antivirus program running in ubuntu in
case the virus attempts to infect the ubuntu drive.

Thoughts ?

---

### Post by localzuk on 2005-12-22
Do not worry about a windows virus infecting ubuntu - they can't they are fundamentally different. The only issue you may have is some of your files may be infected (if they are executable files anyway). Personally, I would not install anti-virus on linux.

---

