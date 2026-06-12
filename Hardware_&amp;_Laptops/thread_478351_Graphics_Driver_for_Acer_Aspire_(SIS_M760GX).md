---
title: "Graphics Driver for Acer Aspire (SIS M760GX)"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by jamesdivine on 2007-06-19
Hello all,


   Noob question here.  I'm a recent convert from the Windows world and so far the transition has been a bit rocky, but I'm sticking with it.  I'm trying to get the graphics card on my laptop working properly (currently limited to 1024x768 res).  I tried following the directions from this post:

[http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty)

  But ran into problems right away:

1. I have no option for an ATI Driver in Restricted Drivers Manager (all I have there are two vmware related drivers)
2. The xorg.conf file in /etc/Xll is read only and I don't know how to make it read/write. 

  Can anyone help a noob out here?

thanks,
-James

---

### Post by carlossl on 2007-06-28
Hey whats up!
I'm a noob too, I have an Acer Aspire 5000 with the same graphics driver, and this is what I did:

```

sudo dpkg-reconfigure xserver-xorg

```

Follow the instructions, just read carefully when you get to the part where you have to select your resolution (1280x800). If for some reason you make a mistake, run the code again to configure it one more time :) .

By the way, which distribution did you use? Feisty32 or Feisty64? Because I installed Feisty64 and as far as I know, XGL is not ready yet for that distribution.

By the way, this graphics card is a really crappy, i hate it, it gives me problems in Windows and in Linux, just to give you an example, you won't be able to use Desktop Effects. I hope somebody tells us how to do this, and if we're lucky enough to be able to use XGL, hope somebody tells us too.

Good luck!

---

### Post by KC9EVP on 2007-08-23
I am sorry if with post I give noobs a bad name, but I am a noob's noob. I have an Acer Aspire 5000 as well. I understand command line in DOS so I can negotiate in Ubuntu. My graphics card is the SiS M760GX. I looked at your posts but I am honestly lost after typing "sudo dpkg-reconfigure xserver-xorg" at the terminal. I go to the option SiS and the next screen is where I get lost:

 Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The X server configuration file associates your video card with a name    &#9474;  
 &#9474; that you may provide.  This is usually the vendor or brand name followed  &#9474;  
 &#9474; by the model name, e.g., "Intel i915", "ATI RADEON X800", or "NVIDIA      &#9474;  
 &#9474; GeForce 6600".                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Identifier for your video card:                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Generic Video Card_______________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>            


I input SiS M760GX as thats the model but I get this:

Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.                            &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  

I have no idea what this means or how to change the resolution. Can anyone that had this issue give me step by step instructions?

-Signed "Loves Ubuntu But Really Lost"

---

### Post by w4ett on 2007-08-23
From the command line interface (CLI) type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "sis" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

to restart X.

---

### Post by EXCiD3 on 2007-08-24
If you want a program to install and configure your graphics drivers try ENVY: [albertomilone.com/nvidia_scripts1.html]("http://ubuntuforums.org/albertomilone.com/nvidia_scripts1.html")
It works with both NVIDA and ATI and will configure it correctly for you! No extra work needed!

---

### Post by likemindead on 2007-08-25
Everything with my SiS M760GX is working great *except for when I hook it up to a data projector*. I followed the above instructions and still, when I reboot with the data projector connected, the system freezes up before it even gets to the login screen. Please help?

---

### Post by likemindead on 2007-08-25
Well, I got it working, but it was weird. Advice is still welcome. Here's what happened:
[LIST=1]
[*]I booted up without having the projector plugged in to my laptop.
[*]After I was up and running I plugged in the projector to my laptop.
[*]I opened a Terminal window and typed "sudo /etc/init.d/gdm stop"
[*]I typed "sudo /etc/init.d/gdm start"
[*]The computer didn't do anything (I don't think?)
[*]I manually powered it off and back on.
[*]Both my monitor screen and the projector screen were up--ta da!
[/LIST]

So.... uh.... :confused:

---

### Post by likemindead on 2007-08-26
I could *really* use some help on this. Anyone? Please?

It seems that another issue is that if I have my wireless on when booting back up (after going through all the aforementioned steps) I get a system freeze at the login screen. So I have to disable my wireless hardware, plug in the VGA cable, reboot X, and then I get a working monitor and projector screen. Most of the time....

Any known fixes? Advice? Guess? Help?

---

### Post by KC9EVP on 2008-05-18
I bought a faster PC and donated my old one to a young lady in need of a PC for school. Tax write off. Anywho I have moved from noob to basic user. Getting more experience everyday. Going to be doing Linux from scratch. I strongly recommend to any noob to get more experience. I bought a new PC and Hardy works 100% out of the box. I have a Lenovo T61.

---

