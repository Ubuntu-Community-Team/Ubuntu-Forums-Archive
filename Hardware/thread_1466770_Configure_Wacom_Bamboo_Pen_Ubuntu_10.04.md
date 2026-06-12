---
title: "Configure Wacom Bamboo Pen Ubuntu 10.04"
date: 2010-04-30
forum: Hardware
---

### Post by sakisds on 2010-04-30
I just installed Ubuntu 10.04 and i can say i am very impressed, they work really nice but i have a problem: i can't get my bamboo pen to work. Its model number is CTL-460. Anyone can point me to a solution? (Running 64-bit)

---

### Post by sakisds on 2010-04-30
Never mind, i found out that i needed to compile a newer version of the wacom module. Used the following commands: 

```

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2

tar -xf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1
./configure --enable-wacom
cd src/2.6.30/
make
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
sudo rmmod wacom
sudo modprobe wacom
```You can also add wacom to /etc/modules so you won't have to load it each time.

---

### Post by ElSlunko on 2010-04-30
Thanks for this. I actually had an issue where my cursor would constantly fly to the corner with my Wacom pad plugged in, pretty much making it useless.

Compiled the newer version & the issue is gone.

---

### Post by freeway on 2010-04-30
hi ElSlunko,

i have the same problem, but not solved compiling the newer driver (linuxwacom-0.8.6), can you explain how you did it?

thanks
jb

---

### Post by halst on 2010-04-30
I've just installed Ubuntu 10.4 for the first time. My Wacom Bamboo Fun does not work : (
I entered all the listed commands into the Terminal, rebooted but nothing changed.

May be I'm doing something wrong?
My experience with Linux is approx. zero.

Thanks in advance.

---

### Post by ElSlunko on 2010-04-30
Hello!

Did you get any errors along the way? It's absolutely necessary that you get all the packages in the first command so you can build it properly.

If you were able to go through all the steps properly without an error then finally add **wacom** to /etc/modules using

```
sudo gedit /etc/modules
```

Edit : And you shouldn't need to reboot, just log out then back in.

---

### Post by freeway on 2010-04-30
Hello!

thanks for your help, the menssage of error is:

'WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.'

Can this be the problem?

---

### Post by halst on 2010-04-30
Thanks alot [ElSlunko]("http://ubuntuforums.org/member.php?u=558698")! Now my Bamboo started working!

The only bug is that when I put my pen to the border of the tablet's sensitive area, the cursor suddenly  jumps to another place. And all in all behaves strange near the borders. What could that be?

And where to configure buttons on pen and tablet?

---

### Post by nalinib on 2010-05-01
> **ElSlunko said:**
> Thanks for this. I actually had an issue where my cursor would constantly fly to the corner with my Wacom pad plugged in, pretty much making it useless.

Compiled the newer version & the issue is gone.

The same thing is happening to me for iball pen tablet.

What is the solution?

---

### Post by ElSlunko on 2010-05-01
> **freeway said:**
> Hello!

thanks for your help, the menssage of error is:

'WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.'

Can this be the problem?

Seems like it. Was this a fresh install or upgrade?

---

### Post by ElSlunko on 2010-05-01
> **nalinib said:**
> The same thing is happening to me for iball pen tablet.

What is the solution?

I did all the steps in the first post plus adding wacom to /etc/modules.

---

### Post by mikeg113 on 2010-05-02
I'm getting a "404" error when I try to wget the linuxwacom file.
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
--2010-05-02 04:16:51--  http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-05-02 04:16:52 ERROR 404: Not Found.

```
Has the link changed?

---

### Post by sakisds on 2010-05-02
> **mikeg113 said:**
> I'm getting a "404" error when I try to wget the linuxwacom file.
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
--2010-05-02 04:16:51--  http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-05-02 04:16:52 ERROR 404: Not Found.

```Has the link changed?


Yeah, its [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2) now.
I will update the first post too. (Tested, works normally with the new link)

---

### Post by mikeg113 on 2010-05-02
Thanks! By the way, you may want to add the "-1" to the rest of the commands to avoid confusion.:)

---

### Post by freeway on 2010-05-02
> Seems like it. Was this a fresh install or upgrade?

was upgrade....

---

### Post by sakisds on 2010-05-03
> **mikeg113 said:**
> Thanks! By the way, you may want to add the "-1" to the rest of the commands to avoid confusion.:)

Yeah good point, i completely forgot about the other commands :P

---

### Post by ionospheric on 2010-05-10
> **ElSlunko said:**
> Thanks for this. I actually had an issue where my cursor would constantly fly to the corner with my Wacom pad plugged in, pretty much making it useless.

Compiled the newer version & the issue is gone.

More thanks to sakisds from here. And I also had the experience that problem in Ubuntu 9.10 with the cursor jumping to the left corner no longer exists. The solution was to restart X after the driver install (logout and back in)  


The only problem I am having now is that I don't know how to get a single tap to be recognized as a mouse click. I am using the tablet as a mouse replacement.

Xsetwacom works, for example:

```
xsetwacom set "Wacom Bamboo 2FG Finger pad" Button4 core key CTRL plus
```

and button 4 on the pad will lead to the zooming feature.

But how do I get the driver to recognize a tap with the finger as a mouse event, specifically a left mouse click?

---

### Post by ProgramErgoSum on 2010-10-18
I just noticed a [Wacom input driver in Synaptic]("https://help.ubuntu.com/community/Wacom"). Wouldn't installing it serve all configuration requirements ?

Also, there is a [Linux Wacom sourceforge project]("http://linuxwacom.sourceforge.net/index.php/main"). Has anyone used it to do installation ?

I had been meaning to purchase the [Bamboo pen]("http://www.wacom.com/bamboo/bamboo_pen.php"). I do not want to go through all this hassle especially when my success rate with hardware is not impressive.

---

### Post by Zidaps on 2011-04-07
That link no longer works. The best instructions i've found that worked are:

[http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077](http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077)

---

### Post by mylhause on 2012-06-12
Ok guys, i don't even know how to use this maling list, but i'm here to try some 
helping

I got problems like this, my pen could hover and move the cursor, but when i 
touch the table, the cursor stuck. This happend when i installed an update to 
ubuntu Kernel. 
I'm very newb and i'm just beginning in Linux, so i can't say clearly how this 
hppens, but i got the solution after some days of researching.
I solved my problem by downgrading the xorg to the following version:

xserver-xorg-input-wacom ver.1:0.10.5-0ubuntu4

The problematic version was xserver-xorg-input-wacom ver.1:0.10.11-0ubuntu7, and 
i uninstalled it and forced the installation of the older version. It worked as 
a glove when i restarted my computer

So, if you are experiencing this kind of problem on Lucid, try this and pass 
this message forward.

Cya guys

(sorry my bad english)

---

