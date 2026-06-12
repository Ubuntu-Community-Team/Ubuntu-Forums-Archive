---
title: "new to ubuntu and problems already?"
date: 2008-09-26
forum: General Help
---

### Post by Churchie-the-dinosaur on 2008-09-26
Ok i am new to ubuntu and linux alltogether.

i have a friend who has been using ubuntu for a while and suggested it to me when he replaced my hdd.

I have an advent 7096. but now with (I think) a toshiba 120Gb hdd.
it is partioned (uncorrectly :( ) to windows xp M.E, Ubuntu, and free space. so it should be (I think) 30Gb each for xp and linux and 50Gb free, but either ubuntu or xp is 50Gb which leaves me 30Gb free space.:confused:

anyway the problems i am having...

my friend finally managed to find the wireless driver for linux, but havent found it for xp :confused: 

desktop drapes doesnt seem to want to work no matter how many times i have tried, installing, re-installing and completely removing and installing again.

when i watch a video i cannot actually watch it and just get a black screen, also when i scroll through some web pages it is extremelly jumpy, i turned off smooth scrolling and is slightly better. but i am thinking this is telling me that my graphics card is not installed properley, i have Envyng and have installed the graphics card (ATI) twice just to make sure. but still same results.

occasionally when i turn on ubuntu, the bar at the top of applications decides to either not show or hide itself behind the top taskbar.

AWN sometimes makes the items in its bar about an inch high from the bar, which baffled me, so i hid the bar when not in use and this seems to have fixed it, i just found it odd :confused:

and now the worst of them all, synaptic package manager has failed i get this error message EVERY time 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so i found on another forum to updat and get upgrade i did and got this message 
church@WOOD:~$ sudo dpkg -- confiure -a
[sudo] password for church: 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
church@WOOD:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release     
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release [58.5kB]      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages [312kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages [6636B]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources [89.5kB]        
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources [908B]    
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages [93.8kB]   
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources [24.4kB]   
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages [20.1kB]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources [2795B]  
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [58.7kB]       
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]  
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [13.7kB]        
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]    
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [31.0kB]   
Get: 18 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [5713B]     
Get: 19 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8222B]  
Get: 20 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]     
Fetched 792kB in 6s (119kB/s)                                                  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
church@WOOD:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i am completely baffled beyond beleif. and to make things worse. my n key has fallen off so i keep having to press a bit of rubber  :lolflag:

but yea, ubuntu seemed happy and good despite drapes, but it jus keeps getting worse and worse, i know ubuntu is well made and works for nearly everyone, so what have i done any help would be so much appreciated

Church

P.S i have no idea what the prefix is so i just put all varients:confused:

---

### Post by pedro_orange on 2008-09-26
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Have you actually tried doing:

```
sudo dpkg --configure -a
```

? That would solve that problem most likely. 

With regards to display drivers, don't use EnvyNG - Use the restricted drivers manager built into Ubuntu. System > Administration > Hardware Drivers.

I find Envy doesn't configure my xorg.conf very well.

With regards to video, have you installed the codecs? 
What kind of video we talking about? Flash? 

If you just wanna install flash, mp3, video codecs in one command try:

```
sudo apt-get install ubuntu-restricted-extras
```

Enjoy Linux.

---

### Post by kokkus on 2008-09-26
You should install the Premium Edition of Ubuntu insted. It has all you need wit hplugins, addons for all kind of video and flash etc.

Here's the iso file link [http://scumbox.com/ubuntu/804pe.iso](http://scumbox.com/ubuntu/804pe.iso)

This is a live cd you can install from, The live CD is in Norwegian so you have to chose english (or whatever) when you install it.

This is a DVD cd so you need a DVD burner on your PC.

---

### Post by SunnyRabbiera on 2008-09-26
> **kokkus said:**
> You should install the Premium Edition of Ubuntu insted. It has all you need wit hplugins, addons for all kind of video and flash etc.

Here's the iso file link [http://scumbox.com/ubuntu/804pe.iso](http://scumbox.com/ubuntu/804pe.iso)

This is a live cd you can install from, The live CD is in Norwegian so you have to chose english (or whatever) when you install it.

This is a DVD cd so you need a DVD burner on your PC.

Eh not needed, if codecs are needed they can try linux mint:
[http://www.linuxmint.com/](http://www.linuxmint.com/)
as not all have DVD burners.

---

