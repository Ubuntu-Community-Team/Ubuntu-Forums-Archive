---
title: "Nvidia driver won't work at all..."
date: 2009-08-05
forum: Hardware
---

### Post by hockey97 on 2009-08-05
Hi, I just installed a nvidia driver.

I went to nvidia's website. I have a geforce fx5500 nvidia graphic card.

I went to nvidias website and searched for the driver. I used the driver under the geforce FX 5. 

This driver is NVIDIA-Linux-x86-173.14.20-pkg1.run 

I shutdown x server by pressing alt ctrl and F1. I went in text mode and made  sure x server is off. I then ran the installer. The nvidia installer installed the driver. It showed no problems or anything. After it was done and showed me a message saying it was successful. I then restarted the computer by pressing alt ctrl and delete. In the text mode this started a restart process.

Then when I restart and it gets passed the loading screen. I get a black  screen with text. It shows like some image not found and this will blink 3 times then I get a window saying ubuntu will start in low resolution.
I clicked ok and then it goes back to the black window with text and blinks once and then ubuntu loads but looks kinda ulgy. I log in and then go see the desktop. I notice icons and text are small. I find out I am in 800x600 display mode. I got that and one other resolution smaller that the 800x600.

Why is the driver not installing. I redid the steps above and notice when I tried to install it again it prompts me that the nvidia driver is already installed would you like to uninstall it and then install the driver you are trying to install. I hit ok. This second time is the same exact thing. The results is still the same.

What driver should I be using for a geforce fx5500 256mb pci  graphic card.
it's a nvidia. 

I did try what ubuntu provides but does the same.


Yes I did try looking at system->admin->hardware drivers.

I get empty list and text saying no proprietary drivers used on this system.

---

### Post by TMAN 1 on 2009-08-05
Is it showing up in Hardware Drivers?And if so,is it active?

---

### Post by hockey97 on 2009-08-05
> **TMAN 1 said:**
> Is it showing up in Hardware Drivers?And if so,is it active?

No it's showing nothing in the Hardware Drivers. 

right now I can only get into low resolution mode.

I just installed Envy and tried that and nothing happened.

What else can I try?

---

### Post by hockey97 on 2009-08-05
Hi, I got it to work for only resolutions. I can now use higher resoultions. 


all I did was to delete every nvidia driver I installed by using the purge command in terminal. 

I now have no graphics driver for my card. I can't open blender or any application that uses opengl. 

I can't figure out why I can't install my graphics card properly. 

I followed nvidia linux graphics driver instructions on their website.

I went to geforce fx 5  and downloaded that driver according to them that driver should of worked. Yet it didn't work. I mean the installer installed it and if I installed another nvidia driver it would detect that their is one already installed which is the 173.14.20 version.

Now I removed every nvidia driver installed that also includes the ubuntu ones... Now my graphics sorta works. I can get resolution back to normal.

Yet still can't open any opengl apps. Do you think it's still my graphics card? Or do I need to download special files for opengl. I already do have such libs installed already. I am thinking to reinstall them and see what happens.

---

### Post by hockey97 on 2009-08-07
I got the nvidia driver to work. I now just have problems with resolutions.

I see only options offering that is lower then 800x600. 

I know my monitor and graphic card can do higher then 800x600.

I don't know how to fix this. I searched ubuntu fourms and google and found many people have had this problem. They fixed it by making changes to the xorg.conf file but I tried what they did and it would then cause ubuntu to not use the nvidia driver and go to low level resolutions and use a default open source graphics driver. 

this is getting frustrating. I googled around some more and found out that the monitor is a small computer. It creates information and communicates with the pc. It sends a EDID binary file to the pc and that has information of what the monitor is who made it and also the binary information where it tells the comptuter the resulutions it can handle and clocks and signal/frequencies. 

I heard a guy fixed this problem by using some linux tool that extracted the EDID binary file and made a copy. He added a line to  the xorg.conf to use that EDID. This worked for him. 

The problem is that he forgot the name of the tool. Do anyone here know what is that tool?

I need help on getting higher resolutions higher then 800x600. I know my monitor can handel such resolutions. It's a dell flat screen. 

Dell E228wfp  to be exact.

Any Ideas? I spent so far 3 days on this. I did had higher resolutions before with ubuntu but never had a nvidia driver installed because I had problems with it. I installed open source drivers. Now I want to get nvidia's drivers working. 

Right now nvidia's driver works. I can open up blender and any opengl apps.

It's just now I am stuck in resolutions lower then 800x600. I don't even have 800x600 as a option. 

Thanks for your time.

---

