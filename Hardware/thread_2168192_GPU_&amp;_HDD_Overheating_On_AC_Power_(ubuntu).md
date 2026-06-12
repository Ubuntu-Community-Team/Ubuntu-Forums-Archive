---
title: "GPU &amp; HDD Overheating On AC Power (ubuntu)"
date: 2013-08-16
forum: Hardware
---

### Post by candi2 on 2013-08-16
[FONT=Times New Roman][SIZE=3]I'mkinda new to Linux still and a racking my brain in this issue myover-heating issue.[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Hereis my set up:[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3][COLOR=#000000]Mycurrent setup is an HPDV6000 Laptop[/COLOR]
[COLOR=#000000]AMDTuron 64 bit processor [/COLOR]
[COLOR=#000000]NvidiaGforceToGO 7200 [/COLOR]
[COLOR=#000000]3gbof memory [/COLOR]
[COLOR=#000000]160gb hdd[/COLOR][/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3][COLOR=#000000]CurrentVideo driver ver [/COLOR][COLOR=#000000]Linuxdriver ver 173.14.36[/COLOR]
[COLOR=#000000]Itdual boots windows 7 and ubuntu lts 12.04 x64[/COLOR][/SIZE][/FONT]




[FONT=Times New Roman][SIZE=3]Ioriginally installed Ubuntu 12.04 and it worked for a while and thenstarted to get real hot and hang where the only thing that would workwas my usb mouse. The only thing I could do with the usb mouse whenthat happened was move it around. The system did not respond to anyclicks so I was forced to shut down. In this version of Ubuntu itdefaulted to a proprietary video driver and would not let me swap it. I tried to do a kernel update and then it ceased to even boot.(Please see [COLOR=#000000]myprevious post when running ubuntu 12.04: [/COLOR][COLOR=#000000]“RandomFreezes and other errors”[/COLOR][COLOR=#000000][http://ubuntuforums.org/showthread.php?t=2167724](http://ubuntuforums.org/showthread.php?t=2167724)[/COLOR][COLOR=#000000])[/COLOR][/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]I read about how Lubuntu was supposed to work better on older systemsand laptops so installed that. (I let it completely remove the oldubuntu 12.04)[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Ilet it run all the updates and noticed it was still getting hot Iinstalled the Psensors and it showed my GPU was getting to 130c +barely doing any thing (watching a youtube vid) [/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Ichecked the drivers that lubuntu had auto installed. It was the opensource drivers so I then tried installing the proprietary nvidiadrivers. That brought the temp down to any where from mid 60's c to100+c. I noticed that when im on battery it hovers around 65-80c(still way too hot) but when I plug in the ac power it sky rockets to100+ on idol. I have read about this issue being something to do withthe acpi drivers but have found no definitive way to fix it. If Ileave it on ac power it over heats till the system freezes and Isee artifacts on my screen. The hard drive and the touch pad (underwhich is my memory and wi fi card) also gets smoking hot on ac power.Also if you look at the first pic below you will see the Nvidiapanel. See how it reads battery. I was plugged into AC power at thattime. No battery was even in the system. When the battery is in thelubuntu battery monitor does tell me when I'm plugged into ac power.Shouldn't it reflect in the nvidia panel??[/SIZE][/FONT]


Ive tried setting the acpi on  boot in grub per the instructions here [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

GPU temp change Results with each setting were:

**acpi=**
On login temp was 101c
After 10 min it was 98c

**acpi=Linux**
On login temp 99c
after 10 min 94c

**acpi=Windows 2006**
On login temp 97c
after 10 min 97c

***These is just idol temps with nothing running but psensor*


[FONT=Times New Roman][SIZE=3]Ialso installed laptop-mode and set it to also run on ac power (assuggested in  a few other posts) and it did not help.[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Itseems like its a software issue. I don't know where else to check.  Icant seem to do much with my fan settings and nothing seems to beable to get to them.[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]TheBios is the latest version but HP has this bios so locked down theonly thing I can change is boot options and time. I also cant seemuch at all about the fan unless I run the tools in linux. [/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Thelaptop fan was cleaned out 2 months ago prior to having Ubuntuinstalled. The fan is spinning nice and quietly.[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Doyou think re flowing the graphics chip and adding a  thermal copperpad (Shim) would help at all?[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]Another thing I noticed is that my wall paper dosen't show up any more the desk top stays black. Once or twice during all this the wall paper randomly showed up but I totally unsure what is causing that.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Alsooutside the power issues I would like Lubuntu to auto mount the mainhdd so I so not have to enter a pas word if I want to get into it. (I did not have this issue in Ubuntu 12.0)

*****[COLOR=#0000ff]*Please note that in the psensor graphic the temps are labeled *[/COLOR][/SIZE][/FONT][COLOR=#0000ff][I]Fahrenheit but after looking in the settings and then comparing them to what was in the nvidia panel setting psenspr to display Fahrenheit will still reflect the temperatures in Celsius but with an f to the side. This may be a bug in the tool. 
[/I][/COLOR][SIZE=3]
[FONT=Times New Roman, serif]If you cant see the pictures below please go here: [/FONT][/SIZE]https://plus.google.com/photos/113683985417185661435/albums/5912905397452409217?authkey=CNCevJmB27qXvwE[SIZE=3]
[/SIZE]

[ATTACH=CONFIG]245425[/ATTACH][FONT=Times New Roman][SIZE=3]

[/SIZE][/FONT][ATTACH=CONFIG]245427[/ATTACH][FONT=Times New Roman][SIZE=3]


[/SIZE][/FONT][ATTACH=CONFIG]245424[/ATTACH]

---

