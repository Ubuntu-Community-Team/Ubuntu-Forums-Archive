---
title: "[SOLVED] Installing Video Driver - Root - X Server HELP"
date: 2008-07-16
forum: General Help
---

### Post by jmorris1161 on 2008-07-16
Ok, I am totally new to Ubuntu, just put 8.04.1 on my system with a dual boot combined with xp. Install went fine but my video can only go to 800x600 the detail looks good the resolution sucks I can't live with scrolling right all the time and I have a huge monitor so I need at least 1024x768. I got the driver from NVIDI for Linux it says to install it as such

sh NVIDIA-Linux-x86-96.43.05-pkg1.run

When I do this it says I need to run as root

So when I log in as root in terminal it then says it appears that X server is running and it cannot run must shut down x server

The only way I found to do this is 'sudo init 1' 

I copied the file over to root and do sudo init 1 then go to command prompt

run the install and now it says it needs to be in a GUI

Any help please?!?!?!?!

All NVIDIA Says is this 

To download and install the drivers, follow the steps below:

STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download - NVIDIA-Linux-x86-96.43.05-pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-96.43.05-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

---

### Post by tuxxy on 2008-07-16
Just install it from the restricted hardware drivers menu, Ubuntu comes with the driver but you have to enable it as its a proprietry driver.

Go system > adminisitration > hardware driver or restricted hardware drivers

or another method if you cannot find it on the menu would be from the terminal type;

```
sudo jockey-gtk
```


once you run this you will see the nVidia driver, simply enable it from here and you may need a reboot :)

---

### Post by jmorris1161 on 2008-07-16
Thanks for the reply, but that just gets me a whopping 640x480 display. I really need this new driver installed not that one.

---

### Post by jonian_g on 2008-07-16
Installing the driver from the nvidia website is a really bad idea.
The best way to do it is with the Restricted Drivers Manager or EnvyNG (has newer versions of the driver).

Why it's a bad idea? Because every time you get a kernel update (three times till now after Hardy released), you have to reinstall the driver.

To install it with Restricted Drivers Manager follow tuxxy's advice.

To install it with EnvyNG open a terminal and type:

sudo apt-get install envyng-gtk

Then go to Applications>System Tools>EnvyNG and install the driver.

---

### Post by jonian_g on 2008-07-16
Maybe you can't change the resolution because your monitor model is not recognized. To recognize it try this:

Open a terminal and type

sudo displayconfig-gtk

Click where it says "Model" and at the screen that comes up choose your monitor model. If not in the list click add and locate the *.inf file in the cd-rom that came with your monitor. Then select you monitor model and press ok. If you don't have the cd choose a general model with your resolution.

You can also install NVIDIA X Server Settings, type:

sudo apt-get install nvidia-settings

Once installed go to System>Admin>NVIDIA X Server Settings, and change your resolution from there (I recommend it). Press the "Save to X configuration file" to save your settings.

---

### Post by jmorris1161 on 2008-07-16
Thanks Jonian, something in there did the trick. The xServer is nice a lot like the windows one I have. Now I can see once again LOL On to my next problem. Maybe one of you know this on it can't be to hard. I don't want to spam the forum with a lot of little questions.

I run my own web servers, windows based right now but plan to change them soon. Any way on a client in windows I would go to windows\system32\drivers\etc\host and edit that file and reference the domain name and ip address. Does anyone know where you go to do this in Ubuntu? I will fish around some and see if I can come with the answer.

---

