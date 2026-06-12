---
title: "Nvidia GeForce 7150M / nForce 630M"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by wneet on 2009-04-19
Hello,


How are you ?


I installed Ubuntu 8.10 few days ago on my Laptop (AMD Turion 64)

I am student (IT College)
And We start learning on this new environment -Linux- (For us)

I faced a problem with the device driver 
I tried to find a solution through the internet but I did not find.
Also I download the drivers that are available in nvidia.com, but I do not know are they the correct drivers or not because they did not work with me 

My problem is with this device : 
Nvidia GeForce 7150M / nForce 630M

I could not find a driver
My lecturer told me to write here and you will help me (Willing God)

And I hope you will give me the solution 


Thank you in Advance,
Ahmed

---

### Post by tommcd on 2009-04-20
Are you currently able to boot to the desktop? If you are, open a terminal (applications > accessories > terminal) and run:
```
aptitude show nvidia-glx-180
```
You will find the Geforce 7150M / nforce 630M in the long list of supported video cards. To install the driver using the most fail safe method, hit ctrl + alt + F2 to get to a virtual terminal. Then login and run these commands:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get update
sudo /etc/init.d/gdm stop
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo /etc/init.d/gdm start

```
These commands backup your xorg.conf, update your repositories, stop the X server, install the 180 driver, configure the driver, and restart the X server.

If you can not get to a working desktop, then boot to recovery mode and just run:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get update
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo reboot

```
If you installed any driver from nvidia.com **uninstall it** before running these commands.

And welcome to the Ubuntu forums!

---

### Post by ptn107 on 2009-04-20
Try this...
1. Open a terminal window (Applications -> Accessories -> Terminal).
2. Type the following:
```
sudo apt-get install nvidia-180-kernel-source nvidia-common nvidia-glx-180 nvidia-settings -y && sudo nvidia-xconfig
```
When the command is finished, restart your computer.

---

### Post by wneet on 2009-04-20
Thank you so much Guys 

I will try one 
then I will tell you what happened with me 

Again .. Thank you so nuch

---

### Post by wneet on 2009-04-20
> **ptn107 said:**
> Try this...
1. Open a terminal window (Applications -> Accessories -> Terminal).
2. Type the following:
```
sudo apt-get install nvidia-180-kernel-source nvidia-common nvidia-glx-180 nvidia-settings -y && sudo nvidia-xconfig
```
When the command is finished, restart your computer.

Hello ptn107 

I used your way because it is short and easy 
but I could not enter my System (Ubuntu) again 

After I enter the Username and Password and then press the button (Login), a black screen occure and no think more appear 

Now, I am not able to see the desktop of my Ubuntu or any thing except the form of Login in the begining 


What I have to do NOW !?!?



Regards,
Ahmd

---

### Post by tommcd on 2009-04-20
This is why I recommended stopping the X server first before configuring the driver. I can't say for sure that it would have prevented your current problem; but it is safer to do it that way.

Try booting to recovery mode. Then run:
```
aptitude show nvidia-glx-180
```
A letter "i" before nvidia-glx-180 will verify that nvidia-glx-180 is installed. If there is a "p" before the package it is not installed.
If it is not installed, then install it with:
```
sudo apt-get install nvidia-glx-180
```
Then after you verify that nvidia-glx-180 is installed, run:
```
sudo nvidia-xconfig
```
This will reconfigure the driver without X running, since you are in recovery mode. Then run:
```
sudo reboot
```
and see if you can get to the desktop.

---

### Post by wneet on 2009-04-21
Hello,

I installed Ubunto again on my Laptop after th problem of the black screen

Then I start to do your way in     post[2]

I wrote 
> aptitude show nvidia-glx-180

but it said : ubable to .... etc


What I have to do ... !?!?

---

### Post by inobe on 2009-04-21
first run the system updates **"very important"** then reboot, upon startup check system> administration> hardware drivers.

if no hardware drivers are in use let us know.

---

### Post by tommcd on 2009-04-21
> **wneet said:**
> Hello,
I installed Ubunto again on my Laptop after th problem of the black screen
Then I start to do your way in     post[2]
I wrote 
aptitude show nvidia-glx-180 
but it said : ubable to .... etc
What I have to do ... !?!?
Get the updates as Inobe suggested and reboot. Also, make sure you have the universe and multiverse repositories enabled; although they should be enabled by default:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Then run:
```
sudo apt-get update
```
You can enable the nvidia driver from: system > administration > Hardware Drivers as Inobe also suggested. I like to configure the driver without X running. It is not strictly necessary though; but if you have problems, then consider installing the driver as I described in my earlier post.

In any case, if you now have a working desktop with the 2D "nv" driver, back up your xorg.conf first before enabling the nvidia driver:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by wneet on 2009-04-21
Hello,

I used the following way 1 hour ago 
but NOW I am not able to enter the Desktop 
Just only I hwatch Black Screen 


this is the way that I used :

> **tommcd said:**
> Are you currently able to boot to the desktop? If you are, open a terminal (applications > accessories > terminal) and run:
```
aptitude show nvidia-glx-180
```
You will find the Geforce 7150M / nforce 630M in the long list of supported video cards. To install the driver using the most fail safe method, hit ctrl + alt + F2 to get to a virtual terminal. Then login and run these commands:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get update
sudo /etc/init.d/gdm stop
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo /etc/init.d/gdm start

```
These commands backup your xorg.conf, update your repositories, stop the X server, install the 180 driver, configure the driver, and restart the X server.

If you can not get to a working desktop, then boot to recovery mode and just run:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get update
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo reboot

```
If you installed any driver from nvidia.com **uninstall it** before running these commands.

And welcome to the Ubuntu forums!

---

### Post by tomthumb99 on 2009-04-21
I am running 8.10 with  Nvidia 7600 GT using the 177 drivers, it was working fine before I installed Webcam packages.  Now also am getting a black X-win screen after login (base OS is full up, tty session (alt-cntl-F1) work fine). I also found that the a power-button reboot brings up an X-Win reboot menu, pops up with icons present.  So, I am logged into Gnome/X-Win successfully just not see the graphics in main panel with no menu at top, all black.   I  have re-installed the ubuntu-desktop twice with new 177 Nivia install, no luck.  Also re-instledd the session-manages ( metacity then compiz, back to metacity), no luck.  {One odd occurrence, the Gnome login screen is now a bunch of paint brushes with 'Utumbu Studio' is aqua text, did I jump back a version installing old packages???}

As mentiond, my Base OS Ubuntu-64 8.10 is fine( rebooted 20x, can get to log file), just the X-Win client has problems.  Hate to go back to CD rebuild, any ideas...

Note: I had the 177 Nvidia drivers were fully working under 8.10.  Are the 180 drivers worth it or am I getting into 'gray' area?  I am not a gammer, just java/SQL hack  

Thanks for your time...

---

### Post by tomthumb99 on 2009-04-21
Folks, I discovered what 'Ubuntu Studio' is and the paint brushes on login. I will now work to get back to base 8.10 ubuntu.  {Life is complicated enough, I do not need multi-media version with its problems.} 

Wow, just playing with a few Webcam installs under the Synaptic manager can jump you a whole different version.  I would think there would be a warning or CD required...

---

### Post by wneet on 2009-04-23
I downloaded the whole UPDATES (very important)
And I went to (System > Administration > Hardware Drivers)

And I found (Nvidia Driver there)
I tried to active it .. but I got this message:
SystemError : Failed to lock /var/cache/apt/archives/lock



What I have to do NOW ... !?!
Please help me 
I have to submit the assignment on Sunday
PLease Please

---

### Post by tommcd on 2009-04-23
> **wneet said:**
> I downloaded the whole UPDATES (very important)
And I went to (System > Administration > Hardware Drivers)
And I found (Nvidia Driver there)
I tried to active it .. but I got this message:
SystemError : Failed to lock /var/cache/apt/archives/lock

So you are able to boot to the graphical desktop. 
Didn't you already install the nvidia driver by running "sudo apt-get install nvidia-glx-180"?

I'm not sure why the nvidia driver is not working for you.
If you had installed any driver from nvidia.com, you should have removed that before installing the driver from the Ubuntu repos.

Can you post the output of:
```
aptitude search nvidia-glx
```
Also post your /etc/X11/xorg.conf file.
And post the output of:
```
glxinfo | grep -i direct
```

---

### Post by wneet on 2009-04-24
Hello tommcd, 

the driver is already Installed 
I noticed that when the shape of the screen change to a wide one 

but I can not see the desktop (only black screen) after I enter the Username and the password

---

### Post by wneet on 2009-04-24
Okay see my brother

> **tommcd said:**
> 
Can you post the output of:
```
aptitude search nvidia-glx
```

> v   nvidia-glx                      -                                           
p   nvidia-glx-173                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-173-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-177                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-177-dev              - NVIDIA binary Xorg driver development file
i   nvidia-glx-180                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-180-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-71                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-71-dev               - NVIDIA binary Xorg driver development file
p   nvidia-glx-96                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-96-dev               - NVIDIA binary Xorg driver development file
v   nvidia-glx-dev                  -






> **tommcd said:**
> 
Also post your /etc/X11/xorg.conf file.

you can see the attached file (code)




> **tommcd said:**
> 
And post the output of:
```
glxinfo | grep -i direct
```

> direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord,


Regards,
Ahmed

---

### Post by wneet on 2009-05-01
Hello, 

Is there any body HERE 

I want your help

---

### Post by tommcd on 2009-05-01
> **wneet said:**
> 
direct rendering: Yes
GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 

This means that the driver is installed and *should be* working.

---

### Post by tommcd on 2009-05-01
> **wneet said:**
> 
the driver is already Installed 
I noticed that when the shape of the screen change to a wide one 
but I can not see the desktop (only black screen) after I enter the Username and the password
So you see the gdm login screen on bootup, then after you enter your user name and password the screen goes black. Is that correct?

I am not sure why that is happening. Your xorg.conf looks ok as near as I can tell. Perhaps you could try adjusting the horizontal and vertical refresh rates rates in your xorg.conf according to your monitor's specifications. Backup your xorg.conf before you do this.

Did you install the driver from the terminal as I had suggested in post #2 of this thread? And if so, did you run the command: **sudo nvidia-xconfig** to configure the driver and reboot? 

Did you happen to also install a driver from nvidia.com? If so, you need to remove that before you install the driver from the Ubuntu repos.
I am not sure what else you could try at this point.

---

### Post by wneet on 2009-05-02
I reinstall Ubuntu again 

and now I have a new system 
I installed all the updates from :
System > Administration > Update Manager

You adviced me before to this 
install all the updates and then install the driver 

Now 
I will follow the steps in you first post:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get update
sudo /etc/init.d/gdm stop
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo /etc/init.d/gdm start


After I use the above commands 
then I will tell you the results 


Regards,
Ahmed

---

