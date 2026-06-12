---
title: "Re: Driver support for monitor"
date: 2018-09-14
forum: Hardware
---

### Post by iamtheeggman2 on 2018-09-14
Dear all,

 would like to buy a dell monitor with the following spec 
[h=1]DELL 2007FPB ULTRASHARP TFT LCD[/h][h=1]1600x1200  20"  MONITOR 4:3 VGA DVI 4 USB[/h]
However I cant find a dell hardware support library, I found [https://opensource.dell.com/](https://opensource.dell.com/) but it seems a little confusing as to what it offers in terms of vdu support. Can anyone please advise? I have issues with my current monitor being too bright but having plugged an lg monitor in I can see it is likely the monitor going bad which is kind of unusual because the monitor worked fine before i switched graphics card.
Thanks in advance.

Well I've been having a play around with some ideas.

My monitor is too bright to be seen on my new graphics card.

However if I plug my monitor into my windows laptop the brightness is fine suggesting it is not a monitor setting on the  monitor itself.

If I plug another lg monitor into my graphics card on my pc the monitor shows appropriate colours.

Therefore it is not the card or the settings itself.

It therefore seems a weird mismatch between the monitor and the card. This must be a drivers issue then? Though having said that, I didnt need to install any more drivers to switch to the test monitor I plugged into my computer. I have to buy another monitor then?? 

Is it possible I can try installing drivers that aren't necessarily directly listed for the graphics / monitor card but would be usable none the less?

---

### Post by Autodave on 2018-09-14
Why don't you go into the settings that are in the monitor itself: there is usually a brightness option there.  One of the buttons on the monitor should get you into the settings.

---

### Post by iamtheeggman2 on 2018-09-14
> **Autodave said:**
> Why don't you go into the settings that are in the monitor itself: there is usually a brightness option there.  One of the buttons on the monitor should get you into the settings.

I have tried both settings on the monitor and the computer for brightness and contrast etc. Like I say the monitor itself looks fine when I plug into the laptop and the new monitor I connect to the linux install looks fine so it is clearly something to do with the setup of drivers for card or monitor. However I am not used to swapping monitors around since I rarely get issues with them.

---

### Post by ajgreeny on 2018-09-14
What graphic card do you have and what driver is being used?

---

### Post by iamtheeggman2 on 2018-09-15
> **ajgreeny said:**
> What graphic card do you have and what driver is being used?

the card I have is ASUS Radeon HD 4350 (512 MB) SILENT HDMI PCI Express Video CardI have only just installed Lubuntu, nothing beyond a standard installatin and it has gstreamer codecs installed.

I thought this command tells you which driver is in use but i am not so sure

sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:27 memory:d0000000-dfffffff memory:fdff0000-fdffffff ioport:e000(size=256) memory:c0000-dffff

Now why does this say i need to run as superuser when i did use sudo command???

$ sudo modinfo -F filename `lshw -c video | awk '/configuration: driver/{print $2}' | cut -d= -f2`
WARNING: you should run this program as super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
/lib/modules/4.15.0-33-generic/kernel/drivers/gpu/drm/radeon/radeon.ko

$ lspci -nnk | grep -i vga -A3
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] [1002:954f]
    Subsystem: ASUSTeK Computer Inc. RV710 [Radeon HD 4350/4550] [1043:02a8]
    Kernel driver in use: radeon
    Kernel modules: radeon

I remember in windows a long time ago i was able to use a monitor driver that was different to the one specific for the monitor, can i try this in linux to see if this helps with the brightness issue?

---

### Post by P-I H on 2018-09-15
In my settings there is a setting "Adjust for TV". When I enable this setting brightness is substantial lower.

---

### Post by iamtheeggman2 on 2018-09-16
> **P-I H said:**
> In my settings there is a setting "Adjust for TV". When I enable this setting brightness is substantial lower.

well i'm not sure thats available in lubuntu, its using xfce. What is that program called?

---

### Post by P-I H on 2018-09-16
It's gnome-control-center, but I don't know if it is available or possible to install in Lubuntu.  I tried to run it from the terminal on an old eePC with Lubuntu and got the message to install. However the installation didn't succeed.

---

### Post by iamtheeggman2 on 2018-09-16
> **P-I H said:**
> It's gnome-control-center, but I don't know if it is available or possible to install in Lubuntu.  I tried to run it from the terminal on an old eePC with Lubuntu and got the message to install. However the installation didn't succeed.

:o

Is this tv option likelt to be present on live dvds? Thanks in advance

---

### Post by P-I H on 2018-09-22
I tried with an Ubuntu 18.04.1 live "usb" and the setting is available. However my information that the screen brightness is changed was perhaps not correct.

---

### Post by him610 on 2018-09-22
Hey iamtheeggman2,

> cant find a dell hardware support library

How much effort did you put into your search? Dell has one of the best support sites on the internet. Check this link...
[https://www.dell.com/support/home/us/en/19/product-support/product/dell-2007fp/research](https://www.dell.com/support/home/us/en/19/product-support/product/dell-2007fp/research)

---

### Post by iamtheeggman2 on 2018-09-23
> **him610 said:**
> Hey iamtheeggman2,



How much effort did you put into your search? Dell has one of the best support sites on the internet. Check this link...
[https://www.dell.com/support/home/us/en/19/product-support/product/dell-2007fp/research](https://www.dell.com/support/home/us/en/19/product-support/product/dell-2007fp/research)

Well in my experience the manufacturers never provide support for linux, however I was looking for a site more like this one with a hardware list for me to look for it to double check it  was supported for proper use in the first place.

Anyway, I have installed gnome and will see what happens when i disconnect my hdmi cable and just use the monitor. I tried to do it with the cable in but when the cmoputer rebooted the screen of the monitor and the tv via the hdmi cable looked all messed up.

---

### Post by iamtheeggman2 on 2018-09-23
Having rebooted lubuntu in gnome mode with the hdmi cable out i have fond the settings dont appear to be changing the monitor to make it normal colouring,. there is no tv setting frm what i can see but oddly enough it refers to the monitor as a vht 17" device - i get it to mirror display for the actual tv being fed the hdmi cable but still the tv is a proper colour but the monitor is too bright. it has some colour profile options but it doesnt seem to be giving manual options like when you are in gimp and you change things like the r g b or hue etc

---

### Post by iamtheeggman2 on 2018-10-21
Hi I still have this issue, is there really nothing i can do radically to change my setup so I can use both my monitor and tv? why wont my fedora install work ok with the tv but does so with the monitor? why does ubuntu work fine on the hdmi connection to the tv but not the vga monitor? is there a different set of drivers for the different outputs of the graphics card?

---

### Post by iamtheeggman2 on 2018-10-29
Hi I decided to but another graphics card, this one is a geforce one, so do i simpyl remove the old radeon put the new one in and let the computer figure it out or is there a process to follow? Thanks in advance

---

