---
title: "5 questions that need answers"
date: 2005-11-26
forum: General Help
---

### Post by Fittersman on 2005-11-26
i have a few question i need answering for version 5.10 not 5.04:

1. how do i get my windows files (like music over to ubuntu from windows XP using a dual boot system.

2. how do i get ubuntu to use my radeon 7500 graphics card instead of my intel one on my motherboard.

3.I NEED an internet connection because switching from ubuntu to windows to see what you have to say is not cool.

4. I need to find a way to see all of my system specs

5. need to know how to find my IP address

---

### Post by aysiu on 2005-11-26
[QUOTE=Fittersman]
1. how do i get my windows files (like music over to ubuntu from windows XP using a dual boot system.[/quote] [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

I know the guide says it's for 5.04, but the instructions for mounting Windows partitions are the same.

> 
3.I NEED an internet connection because switching from ubuntu to windows to see what you have to say is not cool. Try System > Administration > Networking > Eth0 > Properties > Configuration > DHCP

> 
4. I need to find a way to see all of my system specs Applications > Accessories > Terminal and type ```
top
```

---

### Post by Fittersman on 2005-11-26
[QUOTE=aysiu][http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

I know the guide says it's for 5.04, but the instructions for mounting Windows partitions are the same.
[/QUOTE]


i cant understand that stuff i got it mounted and al that but i need to know how to get the files to ubuntu

---

### Post by aysiu on 2005-11-26
[QUOTE=Fittersman]i cant understand that stuff i got it mounted and al that but i need to know how to get the files to ubuntu[/QUOTE] Once it's mounted, it'll appear as a folder in Ubuntu. Just browse to the files in that folder--treat it as you would any other folder... with the exception of it being read-only (you cannot write or save files on an NTFS partition from Linux).

This is me browsing my NTFS partition in Ubuntu, mounted at the folder /xp
(see screenshot)

---

### Post by ozorba on 2005-11-26
[QUOTE=Fittersman]i have a few question i need answering for version 5.10 not 5.04:

1. how do i get my windows files (like music over to ubuntu from windows XP using a dual boot system.
[/QUOTE]
You need to have a shared disk between the Windows and Linux. Create one.
[QUOTE=Fittersman]3.I NEED an internet connection because switching from ubuntu to windows to see what you have to say is not cool.
[/QUOTE]
What type of internet connection? Generally Ubuntu is very good at supporting the ethernet cable and wireless connections (I have not tested the modem). You can access it from GNOME Menu. System->Administration->Networking
[QUOTE=Fittersman]4. I need to find a way to see all of my system specs
[/QUOTE]
Applications->System Tools->Ubuntu Device Database

[QUOTE=Fittersman]5. need to know how to find my IP address[/QUOTE]
sudo /sbin/ifconfig
and then enter your password. This will give you all the information you want including the MAC addresses if you have more than one network device.

Enjoy Ubuntu.

---

### Post by Fittersman on 2005-11-26
how do i get ubuntu to detect my modem? ive tried sudo wvdialconf /etc/wvdial.conf but that doesnt detect it and does anyone know how to get it to use my radeon card instead?

o ya and how do i modify grub loader so that windows is first and ubuntu last because my dad is ready to get rid of ubuntu becuase he is too lazy to press 5 buttons to get windows running instead of ubuntu

---

### Post by atoponce on 2005-11-26
[quote=Fittersman]i have a few question i need answering for version 5.10 not 5.04:

1. how do i get my windows files (like music over to ubuntu from windows XP using a dual boot system.

2. how do i get ubuntu to use my radeon 7500 graphics card instead of my intel one on my motherboard.

3.I NEED an internet connection because switching from ubuntu to windows to see what you have to say is not cool.

4. I need to find a way to see all of my system specs

5. need to know how to find my IP address[/quote] 
1. Edit your /etc/fstab to add the following for FAT32 (assuming your XP partition is located at /dev/hda1):
```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
``` ... or for NTFS:
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` 
2. Can't help, as my video card is built-in to the motherboard.  Is ATI Radeon, and I'm using the driver, just not sure how.  :???:

3. What are the results of:
```
sudo ifconfig
``` You may want to try:
```
sudo ifup eth0
``` or
```
sudo ifconfig eth0 up
``` 
4. At the terminal:
```
top
``` 
5. Try [What is my IP?]("http://www.whatismyip.com")

---

### Post by dsjas297 on 2005-11-26
If your using a dial-up modem and Ubuntu doesn't detect it, it is probably a softmodem. Softmodems don't use hardware of their own, and instead rely on the operating system to function. They are a pain to get to work on non-Windows OSes. Can you check what kind of modem you have?

---

### Post by Fittersman on 2005-11-26
how do i find out what type of a modem i have?

---

### Post by dsjas297 on 2005-11-26
In Windows, right click on My Computer, and then click on properties. Go to the "Hardware" tab and click on "Device Manger." It lists all hardware on  your computer.

---

### Post by Ptero-4 on 2005-11-26
If it says Conexant. Be ready to either cash out some money (the official driver for Conexant modems is commercial and costs some big money) or accept something around 28k or lower since the opersource driver for those modems is quite experimental and can't use the full speed of those modems. If it's Lucent go search a 2.4 kernel AFAIK lucent modems don't go along quite well with the 2.6 variety of kernels.

---

### Post by Fittersman on 2005-11-26
my modem is an agere win modem

---

### Post by Fittersman on 2005-11-26
if someone could just give me specific directions it would be greatly appreciated because all the links people give me are spoken in nerd and i dont understand :s

---

### Post by Bachstelze on 2005-11-26
For the modem-thing, get here : 
[http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

---

### Post by Fittersman on 2005-11-26
im sorry but im not quite following that link it is confusing me

---

