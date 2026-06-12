---
title: "Nvidia Problems"
date: 2004-11-12
forum: Hardware &amp; Laptops
---

### Post by redman5087 on 2004-11-12
I'm trying to install the 'nvidia-glx' drivers.
I did this by the following document
'http://www.ubuntulinux.org/wiki/BinaryDriverHowTo'
I checked that the linux-restricted modules were matching the kernel.
Then I did 'sudo apt-get install nvidia-glx'. This installed the driver.
Then I did 'sudo modprobe nvidia'.
Then I did 'sudo dpkg-reconfigure xserver-xfree86'. I selected the nvidia
driver from the first screen. I kepted all defaults until the modules. I
disabled GLCore, dri and enabled glx.
Then I added 'nvidia' to modules.

So, when I restart linux or my xserver it just hangs when the nvidia logo
should appear.
With th 'nv' driver, it works fine but with the 'nvidia' driver it goes wrong.
My horiz. and vert. sync of my tft are correct.
I tried to change it to a different resolution and depth but nothing works.
It just keeps hanging.

I added the XFree86.0.log.old and XF86Config-4


Kind regards
Patrick

---

### Post by FLeiXiuS on 2004-11-12
[QUOTE=redman5087]I'm trying to install the 'nvidia-glx' drivers.
I did this by the following document
'http://www.ubuntulinux.org/wiki/BinaryDriverHowTo'
I checked that the linux-restricted modules were matching the kernel.
Then I did 'sudo apt-get install nvidia-glx'. This installed the driver.
Then I did 'sudo modprobe nvidia'.
Then I did 'sudo dpkg-reconfigure xserver-xfree86'. I selected the nvidia
driver from the first screen. I kepted all defaults until the modules. I
disabled GLCore, dri and enabled glx.
Then I added 'nvidia' to modules.

So, when I restart linux or my xserver it just hangs when the nvidia logo
should appear.
With th 'nv' driver, it works fine but with the 'nvidia' driver it goes wrong.
My horiz. and vert. sync of my tft are correct.
I tried to change it to a different resolution and depth but nothing works.
It just keeps hanging.

I added the XFree86.0.log.old and XF86Config-4


Kind regards
Patrick[/QUOTE]


Forgot 1 single most important thing.
```
sudo nvidia-glx-config enable
```

---

### Post by redman5087 on 2004-11-12
I also tried nvidia-glx-config enable but that doesn't change anything.
I still have the same problem.
Patrick

---

### Post by Marauder1 on 2004-11-12
Myself too had problem on install.
Because i edited the XF86Config-4 file manually and comment the
glcore ans dri,  the driver would not work.
Had to do a new install of ubuntu and follow these instructions :

NVIDIA Graphics Card
Note: requires linux-restricted modules >= 2.6.8.1.1-3
1. sudo apt-get install nvidia-glx
2. sudo nvidia-glx-config enable

Note (optional): the nvidia-settings package provides a control panel to configure graphics card options such as gamma correction.
sudo install nvidia-settings
then on a console call : nvidia-setting

Note: If you wish to use these drivers and run the XMMS music player, you should be aware of this bug.

"Unless libmikmod2 is installed, xmms fails to start"

sudo install ibmikmod2

-------------------------------------------------------------------------------------------------------------------------------

To remove nvidia boot splash, insert in your /etc/X11/XF86Config-4 :

option "NoLogo" "true"

within your nvidia device block.

Hope it helps !!!
 ;)

---

### Post by Razvan on 2004-11-13
i believe that the new 6111 driver from nvidia doesnt work withot the glcore or dri or both (dunno, u have to try) because the nvidia-glx-config enable script does nothing but changing the nv driver to nvidia

...jupp, i just checked my config...it has glcore and dri enabled

```
Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection
```

and

```
Section "Device"
	Identifier	"00e6"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection
```

welcome

---

### Post by redman5087 on 2004-11-13
I tried a fresh install en then did apt-get install nvidia-glx
                                       and then nvidia-glx-config enable
But I still get the same problem. 
I think this is not a configuration problem.
I tried everything: glcore and dri disabled, i also tried it with enabled.
My version of restricted-modules is 2.6.8.1-13. I think this one should work.
When you see the log it stops when switching resolution.

Could anybody help please?

Patrick

---

### Post by candymanobh3 on 2004-11-13
GoTo this website: [http://kanotix.com/files/](http://kanotix.com/files/) 

Scroll down till you see "Install scripts for graphic cards after HD install" 

Download the nvidia script and remember where you downloaded it to. 

Press/Hold Ctrl+Alt+F1 

Login @ the prompt. 

Now you are logged in change to the directory that you downloaded the scripts to: 
```
cd /your/download/location/
``` 

next to run script type "sudo sh nameofscript.sh" e.g: 

```
sudo sh install-nvidia-6629-debian.sh
``` 

This script will download, compile, and install the nvidia driver of your choosing. 

When process is complete and you are back at the prompt -if not automatic- type "startx" and you will be back in familiar territory. 

If this is confusing please let me know as I am working completely from memory here. My own computer's power supply is dead. 

--Good luck.

---

### Post by candymanobh3 on 2004-11-13
GoTo this website: [http://kanotix.com/files/](http://kanotix.com/files/) 

Scroll down till you see "Install scripts for graphic cards after HD install" 

Download all nvidia scripts and remember where you downloaded them to. 

Press/Hold Ctrl+Alt+F1 

On the keyboard @ login prompt type "root" and then when prompted your password. 

Now you are logged in change to the directory that you downloaded the scripts to: 
"cd /your/download/location/" 

next to run script type "sh nameofscript.sh" e.g: 

"sh install-nvidia-6629-debian.sh" 

This script will download, compile, and install the nvidia driver of your choosing. 

When process is complete and you are back at the prompt -if not automatic- type "startx" and you will be back in familiar territory. 

If this is confusing please let me know as I am working completely from memory here. My own computer's power supply is dead. 

--Good luck.

---

### Post by candymanobh3 on 2004-11-13
GoTo this website: [http://kanotix.com/files/](http://kanotix.com/files/) 

Scroll down till you see "Install scripts for graphic cards after HD install" 

Download the nvidia script and remember where you downloaded it to. 

Press/Hold Ctrl+Alt+F1 

On the keyboard @ login prompt type "root" and then when prompted your password. 

Now you are logged in change to the directory that you downloaded the scripts to: 
"cd /your/download/location/" 

next to run script type "sh nameofscript.sh" e.g: 

"sh install-nvidia-6629-debian.sh" 

This script will download, compile, and install the nvidia driver of your choosing. 

When process is complete and you are back at the prompt -if not automatic- type "startx" and you will be back in familiar territory. 

If this is confusing please let me know as I am working completely from memory here. My own computer's power supply is dead. 

--Good luck.

---

### Post by redman5087 on 2004-11-14
I tried it with Debian script file.
When Installed and I start the X-server I get the message
 fatal server error. no screens found

Can you help me with this problem?
Patrick

---

### Post by candymanobh3 on 2004-11-14
I'm gonna assume you tried restarting?

---

### Post by redman5087 on 2004-11-14
Yup, I restarted the x server!

---

### Post by redman5087 on 2004-11-14
it's actually the same problem as the original driver from the nvidia site.
When it tries to compile it gives an error.
Something saying that some parts of the kernel-source don't match
the kernel or headers.
However the the kernel source that I downloaded are matching the kernel.
So, i don't know what the problem is 
with the debian scripts.

Patrick

---

### Post by candymanobh3 on 2004-11-14
Have you tried any of the old scripts? I tried install-nvidia-6111-debian.sh with luck. Oh!... Have you recompiled your kernel & downloaded the same headers? I had already done that. I can't give you a base example to work with, well... 'cause I don't really feel like installing the standard kerenl image & gumming things up. I dunno, that's what I'd suggest though. Compile yourself a kernel & have the headers ready.

---

### Post by redman5087 on 2004-11-15
I've got the problem finally resolved,
Adding the option "NvAGP" "0" has solved the problem!!
Just wanne let you know!!

Patrick

---

### Post by rayrayray on 2004-11-15
I've been struggling with the same problems. I finally reinstalled Ubuntu,  verified that 'restricted modules' was installed, did "apt-get install nvidia-glx" and "nvidia-glx-config enable", then rebooted. I came back up with the nvidia driver running. Only problem is that I get about 780 fps from glxgears - whereas I used to get about 1300 with my Mandrake 9.0 install. 

Any ideas about why performance is so low??

---

### Post by Marauder1 on 2004-11-16
You mean you added this option in your XF86Config-4 file
and it solved the problem ?
What does it mean redman5087?
Do you have a pci base video card ?
We want to know so others with the same prob can fix it.
Great to know your on GUI.  =D>

---

### Post by redman5087 on 2004-11-19
There are 4 combinations possible!
option "NvAGP" "0"         |            disabled
option "NvAGP" "1"         |            use NVIDIA's internal AGP support, if possible
option "NvAGP" "2"         |            use AGPGART, if possible
option "NvAGP" "3"         |            use any agp support

By default it uses number 3 but I don't know why but it sometimes it crashes.
You have to use NVIDIA's internal AGP support (number 1).

You better only use option 0 to test the system. If It works you can try number 1!

Put the option in your Device section in your XF86Config file
Patrick

---

### Post by jomohke on 2004-11-19
I have a very similar problem.

It appears to freeze on the nvidia logo, but if I leave it long enough it will eventually get to the login screen. From here it seems like the login screen has frozen, but eventually it will work too. Entering my username/password is responsive until I press the final enter button for the password, when it once again appears to hang for a while until -eventually- getting to the desktop. The mouse is responsive, and I can click a menu then it will hang for a while before the menu comes down. Moving up and down the menu with my mouse is responsive, it's just when I click on something that it once again hangs and takes ages.

When I say it hangs, I'm not saying it's just lagged - I'm saying I literaly have to go and make some tea or watch tv for a while before coming back.

This all started happening after installing the nvidia driver on a completely fresh intstall of ubuntu.

Doing ctrl+alt+f1 I can get to the command line, but after putting in my username it just appears to hang - I only did this recently and it's still sitting there while I wait for the password field to come up (if it does).

---

### Post by jdong on 2004-11-19
Does *dmesg* show anything peculiar?

---

