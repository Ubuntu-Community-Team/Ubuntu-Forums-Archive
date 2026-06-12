---
title: "Xubuntu 3d support issues"
date: 2012-04-16
forum: Hardware
---

### Post by Killerghost on 2012-04-16
See I not new As a  user of ubuntu but to the terminal aspect yes.  

See i have a Old Laptop its a whitebox from 1999 In windows i have 3d support in opengl and in direct 3d.   

but in Ubuntu no opengl  and of course windows makes direct3d.


The thing is I am wonderding if i can enable 3d support or better support of this Chipset  SIS 630/730  IGP.   

Can't Really afford a new pc 

This pc has 512 Mbs of Memory Shared with the video card From 8mbs to 64mbs.


The thing is i can watch youtube video in windows with out lag at all an in ubuntu   HOLY Craptastic Lag City no matter what its doing from booting up to sitting idle  And the cpu usage is off the chart.    


I have the linux Driver on a Flash Drive At this moment Directly From the web site of sis.  [http://w3.sis.com/download/download_step1.php](http://w3.sis.com/download/download_step1.php)     


I have no ideal if this could  Fix the lag issues but i know it not giving any Kind of Acceleration.    


Any ideal Would be greatly Apprecated.  Pardon my Spelling havent Sleep in like 20 hours.....  Thanks to the craptastic  Reformates i had to do.       



Specifications of this Pc

pos Pentuim 3 1ghz 
2.5 inch Travlestar ibm 10 gb Pos hdd IDE
Ram 512 MBs  or Sd Ram 133 Mhz 
Wireless Card Doesnt Work in side ubuntu ethier d-link air premier  Model: DWL-Ag660  Says it a atheros And trys to connect to network an fails Every time.  




Honestly If i could Afford To upgrade to a new Computer I would but It isn't Going to happen.       



Thanks for looking And offering help.   

I do not have blank cds to go to a older version of ubuntu ethier  

Besides this thing doesnt Burn Cds  it only reads them.

---

### Post by Killerghost on 2012-04-16
Second Post to the one above..   Ill State this once Again some people Try to force somethings that cannot happen.   


I cannot upgrade.... To a Newer PC 
I am new to this so please bare in mind you have to Go threw Every Step by Step.

Other then that Look forward to figuring out how to solve this... I am  on windows As of right now to take notes Kinda hard to do when you pc Lags out in the os you want to use.

---

### Post by Killerghost on 2012-04-16
I have A computer With the following specs.

Pentuim 3  1GHZ/998MHz
512 Megs of Ram
10 Gb IDE 2.5 inch hdd

GPU/IGP  sis 630/730 Chipset

For some reason it seems That there is no 3d/Open Gl Support.

I try to watch youtube And it lags
Resolutions Chages Don't Work 

I can Afford  A new system Don't Say upgrade.


Windows Pisses me off it the only thing that works.


Ill Take any help I can get So Shoot me a Pm or Reply to this.

---

### Post by mörgæs on 2012-04-16
With a computer from 1999 I think you should simply be happy to have something running, not demand the latest 3D effects. 

Lubuntu would be a better (=lighter) choice than Xubuntu. You can add it with 

```
sudo apt-get install lubuntu-desktop
```


Edit: And please don't post multiple times. I have merged your threads.

---

### Post by Killerghost on 2012-04-16
> **mörgæs said:**
> With a computer from 1999 I think you should simply be happy to have something running, not demand the latest 3D effects. 

Lubuntu would be a better (=lighter) choice than Xubuntu. You can add it with 

```
sudo apt-get install lubuntu-desktop
```

Ok But the thing is Videos an Such are all i want to work nothing Fancy.

---

### Post by Killerghost on 2012-04-16
Also will that Take some of the lag down?

---

### Post by Killerghost on 2012-04-16
Well on xubuntu now an i type in the command correctly and it fails aaron@ubuntu:~$ sudo apt-get install lubuntu-desktop
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lubuntu-desktop

---

### Post by Yellow Pasque on 2012-04-16
> I try to watch youtube and it lags
Video drivers will not help this because Flash doesn't use video acceleration. Try the Flashvideoreplacer plugin (or use something like minitube)

> lubuntu-desktop
In anything earlier than Ubuntu 12.04, the package is called lubuntu-meta
```
sudo apt-get install lubuntu-meta
```

---

### Post by Belfry on 2012-04-16
With regard to the 3d issue, first do not install that video driver from SIS. It's 10 years old and probably only works with obsolete kernels.

To see if the open source 3d graphics driver will work with that machine, open a terminal:

```
sudo apt-get install mesa-utils libgl1-mesa-dri
```

Answer "y" when prompted. Reboot and post the output of the following terminal command here.

```
glxinfo|grep rend
```

---

### Post by LinuxFan999 on 2012-04-16
> **Killerghost said:**
> Well on xubuntu now an i type in the command correctly and it fails aaron@ubuntu:~$ sudo apt-get install lubuntu-desktop
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lubuntu-desktop
Installing Lubuntu on top of Xubuntu is a bad idea, because the two can conflict with each other.
Try installing LXDE (not lubuntu), then remove XFCE.
```
sudo apt-get update
sudo apt-get install lxde
sudo apt-get remove xfce
```
It is not necessary to remove XFCE, but you may want to do it in order to free up hard disk space (your laptop has only 10 GB).

---

