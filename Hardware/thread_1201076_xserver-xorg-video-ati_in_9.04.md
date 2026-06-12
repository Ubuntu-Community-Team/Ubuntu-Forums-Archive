---
title: "xserver-xorg-video-ati in 9.04"
date: 2009-06-30
forum: Hardware
---

### Post by bjdodo on 2009-06-30
Hello Guys

I have a dell inspiron 1501 laptop, my video card is ATI IGP Xpress 1150. Until around 2 months ago I was using fglrx for the card in Kubuntu 8.10 but I have read that (K)ubuntu 9.04 uses the new xorg server and the latest version of fglrx does not anymore support my video card. To make a long story short I have tried the open source driver to see if I should upgrade to Kubuntu 9.10 and it is amazing in 8.10. glxgears gives such results:

4322 frames in 5.0 seconds = 864.341 FPS
5385 frames in 5.0 seconds = 1076.935 FPS
4850 frames in 5.0 seconds = 969.939 FPS
5370 frames in 5.0 seconds = 1073.947 FPS
4622 frames in 5.0 seconds = 924.328 FPS

and Torcs works at 15-20 FPS.

Then I installed Kubuntu 9.04 on a different partition and glxgears gives around 320-350 FPS, Torcs works at 5-10 FPS -> unplayable. Okay, I use my laptop for different purposes as well, but I love Torcs, it is good if I just want to waste some time.

I have tried to google my problem and have found some tips for the xorg.conf file but none of them helped. Actually in 8.10 I also have hacked my xorg.conf and here are my settings:

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
EndSection

Section "Monitor"
        Identifier      "Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Neither these nor other settings I found by google seem to increase the glxgears FPS above 350 on Kubuntu 9.04.

glxinfo on 8.10:

OpenGL vendor string: DRI R300 Project                                        
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL   
OpenGL version string: 1.3 Mesa 7.2                                           
OpenGL extensions:

glxinfo on 9.04:

OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:

So my question: do you have a suggestion about what else I could try on Kubuntu 9.04 to get similar good 3d performance?

Thank you for all answers!!

Regards,
Jozsi

---

### Post by zeusz4u on 2009-08-13
I have the same configuration, Dell Inspiron 1501, with Radeon Xpress 1150, and have the same problem with 3D acceleration :(. I tried to find something that can help me increase performance but nothing i could find. 

The thruth is that the open-source driver gives me better performance for compiz, and films play much better in fullscreen, and i can even use suspend mode (with fglrx i couldn't wake my laptop up from suspend, and had a blinking screen in 3D apps while compiz was active). The only problem is that i have only 6-7-8 FPS in fullscreen apps, too.

So please let mi know if you found anything to solve this problem. I say again: ATI sucks, i have my laptop for 1.5 years, and they say that the Xpress cards are "old" cards so they don't support them :confused:. And I've read something that they published the source code for those old drivers, so that linux distros can support them later on in new distros.

In fact there would be a hack: to recompile the old Xorg for Jaunty, but that's not the thing i want to do, and as i said the fglrx has some major bugs too. There must be some other way to optimize Mesa DRI drivers fro my Xpress card...

---

### Post by mvartic on 2009-08-15
Apparently there is a solution to make the ATI drivers work in 9.04.
Maybe you can find some informations here :

[http://ubuntuforums.org/showthread.php?p=7674928#post7674928](http://ubuntuforums.org/showthread.php?p=7674928#post7674928) 

Personally I didn't tried it yet, for the instance I gave up and revert to 8.10, where everything is is running fine.

I'm disappointed about this and I hate that almost at each release there is something that happens

---

### Post by ssri on 2009-08-17
> **mvartic said:**
> Apparently there is a solution to make the ATI drivers work in 9.04.
Maybe you can find some informations here :

[http://ubuntuforums.org/showthread.php?p=7674928#post7674928](http://ubuntuforums.org/showthread.php?p=7674928#post7674928) 

Personally I didn't tried it yet, for the instance I gave up and revert to 8.10, where everything is is running fine.

I'm disappointed about this and I hate that almost at each release there is something that happens

Doesn't work for 3D games, thanks for playing.  If you want full 3D acceleration and opengl 2 support (if your card supports opengl 2), then you have to either downgrade to 08.10 or downgrade xserver in 9.04 and install catalyst 9.3 as I did.  You can find the link in one of my posts...

---

### Post by zeusz4u on 2009-08-18
Is there any possibility to have these ATI drivers included in the next Ubuntu release (karmic)? 

I tried to contact those guys from Mesa 3d, but i wasn't able to post on their forums, neither could i send them mail. So i'll probably have to wait and use Windows, again :(. And all because of ATI.

I found something about downgrading the Xserver in Jaunty, but i don't like to hack my system, then something might go wrong and i end up with no desktop. For now the current release works fine, however there are a few new features in Jaunty that i'd like to have in 8.10.

Do you know anything about other distros, such as openSuse?? Are they changing Xserver too?

This problem of ATI cards has a long story in Fedora... fedoara isn't supported by ati since version 6 or 7.

---

