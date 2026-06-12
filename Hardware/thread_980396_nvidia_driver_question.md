---
title: "nvidia driver question"
date: 2008-11-12
forum: Hardware
---

### Post by subfire91 on 2008-11-12
i use intrepid and i just wanted to know some information. i downloaded nvidia 177.80 and installed them. installation was completed without any problems. do i have to enable the proprietary driver in Hardware drivers or it is not needed as the 177.80s are installed? what is their difference?? 

thnx in advance

---

### Post by tvtech on 2008-11-12
yes you have to enable them 

they are installed that just means that all the packages and dependencies have been written to your drive and are ready for use, but they are currently not being used by your X session manager.

The difference is this.  The standard Vesa driver selected automatically by X on installation does not enable the more advanced features of your video card, 3D exceleration, overclocking, etc.... 

Enabling the Proprietary Nvidia driver allows these advanced features to be accessed, however, if it has bugs they must be fixed by Nvidia, as this is proprietary software and is not supported by any Linux distro, other than it has been compiled and is installable. so really no difference than installing the driver in windows versus not installing it.  you get the extra bells and whistles and gripe when it doesn't work right.

---

### Post by phidia on 2008-11-12
> **subfire91 said:**
> i use intrepid and i just wanted to know some information. i downloaded nvidia 177.80 and installed them. installation was completed without any problems. do i have to enable the proprietary driver in Hardware drivers or it is not needed as the 177.80s are installed? what is their difference?? 

thnx in advance

How did you install-what method did you use? 

The preferred way to set up the driver is to click on System > Admin > Hardware drivers and select enable (click the enable box beside the driver for your card) Doing that is suppose to download an enable the driver.

Hope that helps.

---

### Post by subfire91 on 2008-11-12
> **phidia said:**
> How did you install-what method did you use? 

The preferred way to set up the driver is to click on System > Admin > Hardware drivers and select enable (click the enable box beside the driver for your card) Doing that is suppose to download an enable the driver.

Hope that helps.

i downloaded 177.80 from nvidia, killed x and installed them by writing the commands and following onscreen instructions.

tvtech, before enabling the proprietary driver, by just installing the ones from the nvidia my resolutions were working fine(resolution was limited to 800*600 prior to installing them) and x server settings were listing 177.80s as the drivers used, nothing significant changed by enabling the proprietary driver. Maybe a little bit of performance during browsing..

---

### Post by athaki on 2008-11-12
in that case you'll want to go try to open the nvidia configuration settings. If it says that the driver is not enabled then you will just have to run the command it shoudl prompt you to run (I think nvidia-xconfig or something similar) and you'll have the same results as if you had done the hardware drivers way.  So no, you don't need the hardware drivers since you did it yourself.

---

### Post by subfire91 on 2008-11-12
> **athaki said:**
> in that case you'll want to go try to open the nvidia configuration settings. If it says that the driver is not enabled then you will just have to run the command it shoudl prompt you to run (I think nvidia-xconfig or something similar) and you'll have the same results as if you had done the hardware drivers way.  So no, you don't need the hardware drivers since you did it yourself.

where are these settings? What i ve done so far is that i installed 177.80s manually but also enabled the proprietary driver. Does that mean that my 177.80's installation was overridden? Is this fine?

[[IMG]http://img83.imageshack.us/img83/8241/xserverme1.th.jpg[/IMG]](http://img83.imageshack.us/my.php?image=xserverme1.jpg)[[IMG]http://img83.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by subfire91 on 2008-11-13
?:confused:?:confused:?
anyone??

---

### Post by Skripka on 2008-11-13
> **subfire91 said:**
> where are these settings? What i ve done so far is that i installed 177.80s manually but also enabled the proprietary driver. Does that mean that my 177.80's installation was overridden? Is this fine?

[[IMG]http://img83.imageshack.us/img83/8241/xserverme1.th.jpg[/IMG]](http://img83.imageshack.us/my.php?image=xserverme1.jpg)[[IMG]http://img83.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)


If you see that in Nvidia-settings, you should be good to go.

---

### Post by Mardoct909 on 2008-11-13
I'd recommend using envy next time.

```
sudo apt-get install envyng-gtk
```

---

### Post by Jackie999 on 2008-11-13
Okay I've installed the envy - now what? Does it work with intrepid?

---

### Post by Mardoct909 on 2008-11-13
It'll be in the menus. On Gnome, I believe it's Applications-> Utilities. Look for it, and run it.

And yes, it'll work just fine with Intrepid.

---

### Post by Jackie999 on 2008-11-13
I wasn't able to find it in menu but the "envyng -t" in terminal worked .....tells me :
```
 +---------------------------------------------------------------------------------+
 | Number | Candidate Version    | Installed Version    | Compatible | Recommended |
 |---------------------------------------------------------------------------------|
 | 0      | 177.80-0ubuntu3      | -                    | -          | -           |
 |---------------------------------------------------------------------------------|
 | 1      | 173.14.12-1-0ubuntu5 | 173.14.12-1-0ubuntu5 | +          | +           |
 |---------------------------------------------------------------------------------|
 | 2      | 96.43.09-0ubuntu1    | -                    | +          | -           |
 |---------------------------------------------------------------------------------|
 | 3      | 71.86.04-0ubuntu10   | -                    | +          | -           |
 +---------------------------------------------------------------------------------+

```So looks like I'm up to date - my card is a GeForce FX 5500 -  still can't enable desktop effects :(

---

### Post by Mardoct909 on 2008-11-13
Did you reboot? X needs to restart for all this to work out.

---

### Post by Jackie999 on 2008-11-13
When I ticked "pre-released updates - intrepid proposed" in software sources the 173.14.12 downloaded and installed/enabled. I have since shut-down and restarted a few times. I'm assuming thats an X restart?

---

### Post by Mardoct909 on 2008-11-13
You only needed one...

Anyways, I'm assuming this means it is still not working. That puts me up against that wall. The last suggestion I can really think of would be removing the driver and trying the 96.43.09 one.

---

### Post by Jackie999 on 2008-11-13
Thanks Mardoct909 that solved it for me - I didn't realize I could use the 96...I'm now able to enable desktop effects :)

---

### Post by Mardoct909 on 2008-11-13
No problem. 

Notice the middle column there that "compatible" and the plus sign. Means you can use it.

---

### Post by Cool G5 on 2008-11-14
Sorry for hijacking the thread, but as the thread OP is finished solving his query. I will put my similar query here.

I have an AGP 7300GT Nvidia card. Under Ubuntu 8.04, I want to install it to get those effects and all.

I downloaded the offical Nvidia driver NVIDIA-Linux-x86-177.80-pkg1.run. I copied it on desktop, but how do I run it?

I tried doing 

> sh NVIDIA-Linux-x86-177.80-pkg1.run 

But it failed.

---

### Post by oldsoundguy on 2008-11-14
No, Envy does not work in intrepid yet.

---

### Post by Cool G5 on 2008-11-14
> **oldsoundguy said:**
> No, Envy does not work in intrepid 
yet.

Sorry, I did not get you.
BTW I am using hardy not intrepid.

---

### Post by subfire91 on 2008-11-14
> **Cool G5 said:**
> Sorry for hijacking the thread, but as the thread OP is finished solving his query. I will put my similar query here.

I have an AGP 7300GT Nvidia card. Under Ubuntu 8.04, I want to install it to get those effects and all.

I downloaded the offical Nvidia driver NVIDIA-Linux-x86-177.80-pkg1.run. I copied it on desktop, but how do I run it?

I tried doing 



But it failed.

you have to kill X first


1) Press **ctrl + alt + F1** 
2) then type **sudo /etc/init.d/gdm stop**
3) proceed with instructions at nvidia site

---

### Post by Mardoct909 on 2008-11-14
Unless it's changed from when I did it when you kill X by what's mentioned above and run the package from the terminal (I renamed it "Driver.run" and put it on the desktop.)

```
./home/USERNAME/Desktop/Driver.run
```

you get some message about not having something. It was "lib-something-or-other-here-". Get back to the GUI by rebooting or restarting X and install that from synaptic. Then kill X, run it again and it should be able to run just fine from there.

---

### Post by oldsoundguy on 2008-11-14
> **Cool G5 said:**
> Sorry, I did not get you.
BTW I am using hardy not intrepid.

Then you are OK as Envy DOES have a program for Hardy.

Those of us that have moved over to Intrepid are still waiting for the program. (and running very limited, albeit viewable, video.)

---

### Post by Cool G5 on 2008-11-15
> **subfire91 said:**
> you have to kill X first


1) Press **ctrl + alt + F1** 
2) then type **sudo /etc/init.d/gdm stop**
3) proceed with instructions at nvidia site

I get an invalid login error. The password is correct, I tried it number of time.

---

### Post by Cool G5 on 2008-11-18
Help guys !!!
I am still stuck with the driver on desktop.

---

