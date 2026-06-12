---
title: "New Linux user needs help"
date: 2008-07-29
forum: General Help
---

### Post by forumz360com on 2008-07-29
Hey guys
finally i ve decided to switch from windows to linux , so i ve tried installing Ubuntu 8.04 - the Hardy Heron - released in April 2008.
i ve installed it on an old dell desktop with PIII and 512RAM. i ve removed xp which was originaly on the system and installed ubuntu over it.
at the begining it was runnug fine and smooth.. when i ve started browsing the internet and exploring the system settings and programs i ve faced some issuse and problems , and i wonder if somebody can help me with them or some of them if possible :

- internet videos are extremly slow (youtube,metacafe,google videos) (Note: videos where running perfectly on the same computer without issues when i had windows) ... i did install firefox flash plugins , actually it prompted me to install 
- where i can find a Device manager so i can see if HD drivers are installed properly.
- i ve tried to download an antiviruse software (for free) and i couldnt install it , i googled it and i found out that i need to do a lot of scripting and commands to install it . ( is this required for installing any software on linux??)

---

### Post by lordadi on 2008-07-29
Hi,


If you are looking for a free antivirus for ubuntu (not that one's needed) you can look for clamtk in the repositories. You generally do not need to do a lot of scripting work to install stuff because it should be available in the repositories or as a .deb file. 

If you still need to install stuff from source, you generally need only a few commands which have been documented widely.

Sorry I cannot answer the questions about the Internet videos as I do not know enough.


> - where i can find a Device manager so i can see if HD drivers are installed properly.
What do you mean to ask as I have not understood your question. Are you talking about some windows explorer type thing?



Cheers,


Lordadi.

---

### Post by WRDN on 2008-07-29
Regarding your first question about internet videos, have you installed the nonfree flash plugin, or the gnash plugin? I've noticed that flash video's don't load as fast as when running Windows on my PC, but it isn't a major problem.
To find about your devices, use the command "lshw" in the Terminal. The drivers should have installed properly if there are no issues.
Finally, you don't really need antivirus if you only use Linux on the machine, and don't send/ forward files to Windows users. If you want a program though, install ClamAV (it can be found in the repo(s). Click System > Administration > Synaptic Package Manager and then click the Search button, then search for clamtk).

---

### Post by Vivaldi Gloria on 2008-07-29
Welcome to ubuntu. I suggest you learn a couple of things before you do anyting.


**1)** Installing Programs. For this use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.


**2)** Learn the basics of a terminal from

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

This is important because quite a bit of help in this forums requires you to enter commands in a terminal. You start a terminal from

Applications > Accessories > Terminal 

or press Alt+F2 and start

```
gnome-terminal
```


**3)** There isn't a device manager included. I remember seeing one called sysinfo in synaptic. Search & install it. But there are a lot of commands you can use in terminal: see the below post. Don't forget to check the hardware drivers application which is in System menu > Admin.


**4)** Ubuntu does not need any antivirus software. There are a lot of threads about this. Search for them.

---

### Post by Vivaldi Gloria on 2008-07-29
There are a number of (terminal) commands that give general info about your hardware:

```
lshw
hwinfo
dmidecode
```

If any of these are not installed then search & install them using synaptic.

Preferably use these (and the ones at the end of this post) with sudo:

```
sudo lshw
```

etc. (Sudo gives administrative rights.)

These spit out so much info that it may be better to save the output into a text file:

```
sudo lshw > info1.txt
sudo hwinfo  > info2.txt
sudo dmidecode  > info3.txt
```

Start by using the short versions

```
sudo lshw -short
sudo hwinfo --short
```

They have flags to restrict the output to certain hardware. For example

```
sudo lshw -class system
```

gives a basic info and motherboard. To learn more about these flags see their man pages:

```
man lshw
```

etc.

Some other commands:

```
lspci (Lists PCI devices including Audio, VGA, Ethernet etc.)
aplay -l (sound info)
uname -a (kernel info)
lsusb (list USB devices)
ls /dev/disk/* -lah (disk info)
fdisk -l (disk info)
df -h (disk usage info)
free -m (memory info)
cat /proc/swaps (swap file/partition info)

```

and the list goes on and on.

---

### Post by Diabolis on 2008-07-29
You picked the worst title for a thread. Use more descriptive titles.

You don't need a firewall for linux.

Hard drives are not installed, they are mounted. You can see your drives with gparted.
Install gparted with this command:
```
sudo apt-get install gparted
```

Are just videos slow or pages load slowly in general?

---

### Post by Potatoj316 on 2008-07-29
i know there is a way to see all of your attached hardware, I just forgot where it is.  I can almost guarantee its under System->Administration.

---

### Post by forumz360com on 2008-07-29
thanks for the help guys, i am sorry about the title of the post , not a big deal though ..

i will try all the good stuff you provided

also i wrote HD by mistake , i meant HW:hardware

as for the videos on youtube , they are slow not browsing , actually browsing is really fast and smooth.

---

### Post by lordadi on 2008-07-31
Hi,


I second the suggestion to use sysinfo. It's great, easy and automatically refreshes! :D


Cheers,


Lordadi.

---

### Post by linux_tech on 2008-07-31
I've had good luck with Gecho mplayer-
see this for more detail-PART 2/5, AUDIO & VIDEO STREAMING--
OPTION 1, GECKO MEDIA PLAYER
- [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by john test on 2008-07-31
Don't hhink I'd spend a whole lot of time sweating the relative merits of your title/Subhect line!
Look at all of the Excellent Answers you have elicited.
Good Stuff!!

---

### Post by steveneddy on 2008-07-31
The best thing you can do is to follow the three links in my sig.

They should help you with most if not all of the issues you are experiencing.

These will educate you about Ubuntu and how things work in that new OS you just installed.

---

### Post by lavinog on 2008-07-31
> **forumz360com said:**
> 
- internet videos are extremly slow (youtube,metacafe,google videos) (Note: videos where running perfectly on the same computer without issues when i had windows) ... i did install firefox flash plugins , actually it prompted me to install 

It is likely your video driver is not loaded.
What type of video card do you have? (ATI / nVidia / Intel...)

can you open a terminal and type this in:
```
glxinfo|head
```
see if you have direct rendering.
if it says "direct rendering: no" the video driver would be the issue

---

