---
title: "Acer Aspire 3023 WLMi help (noob)"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by AlexBryan on 2006-06-05
Hi guys,
This is my first post. I'm a complete linux virgin but I've wanted to try it for a while. I thought I'd try Ubuntu 6.06 because it looks really neat and might be a good place to learn the ropes. I ran the live CD and after going through all the driver loads etc. the screen just goes black. I'm guessing there are no drivers for my laptop's LCD monitor on the CD, so what do I do now? The only distro that has been properly tested on my laptop is Fedora Core 4, and some french guys got a few others to work, but the instructions are in french. Should I try those or can I get this distro working on my laptop? As I said I'm a complete Linux virgin so sorry if this question seems stupid!
Cheers

---

### Post by mihai.ile on 2006-06-05
do you hear a sound when the screen goes blank?
anyway you should try this, i have the same graphic card and it worked:
whan the screen is blank do ctrl+alt+f1
then login and type
$ sudo pico /etc/X11/xorg.conf
in the file find a part that says 
something like
[B]Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
[/B]
and add one line ( **Option          "MonitorLayout" "LVDS,Auto"** ) in that part:
[B]Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "MonitorLayout" "LVDS,Auto"
EndSection
[/B]

then exit (ctrl+x) and save the file.
restart gnome by doying:
$ sudo /etc/init.d/gdm restart
voila ;)

---

### Post by haman on 2006-06-13
I've sucessfully installed ubuntu dapper onto a 3023wlmi.

Everything is working but, being new to all of this, it took a while to get the WLAN up and running but got it working using ndiswrapper and acerhk.
  
1. make sure that acerhk is added to the modules file so that it starts automatically when the machine starts.

2. ensure that you add the BCM43xx driver to the startup blacklist (sorry I don't remember the details of how to do this). 


There are numerous instructions out there on how to get the X700 graphics card working properly, and at the proper resolution (1280 x 800).  

The only gripe I have with ubuntu is that my laptop runs extremely hot...much hotter than with WinXP.  CPU is scaling correctly and the fan does come on, but the laptop still feels much hotter than what I'm confortable with.  For this reason alone, I might have to go back to using XP.

Good luck.

---

### Post by Tom20 on 2006-06-13
Could anyone give me advice to set up my wireless please. I have a 3023 and im completely new to linux and just dont have a clue what to do to get wireless working. 
Any help would be appreciated.
Thanks.

---

### Post by haman on 2006-06-13
1. Download the latest version of acerhk at [http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/)

Install it:

I used the instructions on [http://folk.uio.no/krisvh/linux/cl56.html](http://folk.uio.no/krisvh/linux/cl56.html) but modified them slightly for v0.5.33.

Search for the heading 'Built in wireless card' and follow the instructions from there onwards:

$ wget [http://www.informatik.hu-berlin.de/~tauber/acerhk/archives/acerhk-0.5.22.tar.bz2](http://www.informatik.hu-berlin.de/~tauber/acerhk/archives/acerhk-0.5.22.tar.bz2)
$ tar xvjf acerhk-0.5.22.tar.bz2
$ cd acerhk-0.5.22
$ make
$ sudo make install

etc...

(obviously substituting 0.5.22 with 0.5.33)

- I think you need to install the build-essential package and a few others...

- Because it's v.33 you don't need the extra parameters when you run modprobe...



2. Blacklist the bcm43xx driver

Run the following in the terminal:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist



3. Install ndiswrapper.

I used the instructions from this page (heading 2.5)

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-641f02d713cfad8d50253292a3672dc3fc89998e](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-641f02d713cfad8d50253292a3672dc3fc89998e)


There may be other bits I did in between, I really don't remember but I think this is all that was required.

Hopefully, when you reboot the red light should come on and you'll be able to connect to your network.  If you have a red light, but can't connect, try disabling WEP / WPA on your router.  If that works, at least you'll know that the wireless is working and you can tackle the encryption seperately.

Good luck.

---

### Post by Tom20 on 2006-06-14
Thanks for the help. Got my wireless working perfectly now :D Gonna try sort out the x700. Is their anything else i need toe 'fix'?
Thanks.

---

### Post by haman on 2006-06-15
Although I'm still not 100% happy with the laptop temperature under linux (vs. XP), I found this tip very useful for controlling the fan on the 3023wlmi:

[http://www.ubuntuforums.org/showpost.php?p=190445&postcount=11](http://www.ubuntuforums.org/showpost.php?p=190445&postcount=11)

---

### Post by theophane on 2006-07-22
> **haman said:**
> 1. Download the latest version of acerhk at [http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/)

Install it:

I used the instructions on [http://folk.uio.no/krisvh/linux/cl56.html](http://folk.uio.no/krisvh/linux/cl56.html) but modified them slightly for v0.5.33.

Search for the heading 'Built in wireless card' and follow the instructions from there onwards:

$ wget [http://www.informatik.hu-berlin.de/~tauber/acerhk/archives/acerhk-0.5.22.tar.bz2](http://www.informatik.hu-berlin.de/~tauber/acerhk/archives/acerhk-0.5.22.tar.bz2)
$ tar xvjf acerhk-0.5.22.tar.bz2
$ cd acerhk-0.5.22
$ make
$ sudo make install

etc...

(obviously substituting 0.5.22 with 0.5.33)

- I think you need to install the build-essential package and a few others...

- Because it's v.33 you don't need the extra parameters when you run modprobe...



2. Blacklist the bcm43xx driver

Run the following in the terminal:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist



3. Install ndiswrapper.

I used the instructions from this page (heading 2.5)

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-641f02d713cfad8d50253292a3672dc3fc89998e](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-641f02d713cfad8d50253292a3672dc3fc89998e)


There may be other bits I did in between, I really don't remember but I think this is all that was required.

Hopefully, when you reboot the red light should come on and you'll be able to connect to your network.  If you have a red light, but can't connect, try disabling WEP / WPA on your router.  If that works, at least you'll know that the wireless is working and you can tackle the encryption seperately.

Good luck.

Hi there,

I own an Acer Aspire 3023 like you guys, and I can't get my wlan working.
I can't even install acerhk, here is what I get :

```
theo@tux:~/Desktop/acerhk-0.5.33$ sudo make install
awk: cannot open /lib/modules/2.6.15-26-386/build/include/linux/version.h (No such file or directory)
awk: cannot open /lib/modules/2.6.15-26-386/build/include/linux/version.h (No such file or directory)
cc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acerhk.o acerhk.c
acerhk.c:38:26: erreur: linux/config.h : Aucun fichier ou répertoire de ce type
acerhk.c:2973:2: erreur: #error This driver is only available for X86 architecture

```

If someone could tell me what to do, that would be nice, because I'm kind of lost :neutral: 

Cheers 8)

---

### Post by soopadoubled on 2006-07-28
theophane,

I too am a 3023 owner, and as my first experience of Linux I decided to install Ubuntu on my laptop.

I had the same problem, but have fixed it, and here's how. (Any problems just ask as this is the first time I have written anything like this!)

The problem stems from the fact that you won't have the correct kernel-headers for you module, and thus when you try to compile acerhk, it say's it cannot find the required folders! 

If you haven't already I suggest you get the latest K7 kernel:

```
sudo apt-get instal linux-k7
```

Then you need the headers for this version...which is referenced [here.]("http://packages.ubuntulinux.org/dapper/source/linux-source-2.6.15")

The current version being 2.6.15-26, so in terminal execute

```
sudo apt-get install linux-headers-2.6.15-26-k7
```

Once this installs you should now have a 'build' folder in your '/lib/modules/2.6.15-26/' directory.

You should now be able to follow haman's instructions to install acerhk!

Cheers,

Ian

---

### Post by theophane on 2006-08-03
Thanks for your reply.

I seem to be done with the compilation of acerhk, even if I don't know how to check if everything is working.
I am now trying to setup the wireless card, but after 

```
zless /usr/share/doc/bcm43xx-fwcutter/README.gz
```

the terminal is giving me a list of drivers i don't know what to do with, i don't even know which one i have to pick, or even how to pick it... :???: 

And by the way, I have two other questions :

- My laptop seems to be very hot under ubuntu, is that normal ?
- my booting process takes a lot of time, especially when "cheking all filesystems", is there anything I can do to reduce the booting time...?

Once again, thanks !

8)

---

### Post by mdoube on 2006-08-04
You can also choose to boot in safe graphics mode, at the startup menu.

Mike

---

