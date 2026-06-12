---
title: "ASUSTeK A8Js-4S014P compatible?"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by jackn on 2006-12-31
I'd be grateful for some info on running Ubuntu on the ASUSTeK A8Js-4S014P laptop.

Specs: Intel Core 2 Duo T7200, 2 Gb RAM, 120 Gb hard disk, 14" TFT, Nvidia GeForce GO 7700.

[Here's]("http://www.rothlaender.net/a8js.html") one site with plenty of info, but I thought there'd be enough interest in a thread for sharing user experiences

To what extent does the hardware run under Ubuntu, and what tweaking is called for? References to other info, too, are welcome.

I would also appreciate hardware comments based on first hand experience. Though generally highly favourable, the reviews I've seen also include some disparaging of the screen and the sound.

Thank you kindly.

---

### Post by veratyr on 2007-02-02
[http://ubuntuforums.org/showthread.php?t=310508&highlight=asus+a8js](http://ubuntuforums.org/showthread.php?t=310508&highlight=asus+a8js)

also from the gentoo wiki [http://gentoo-wiki.com/HARDWARE_Asus_A8Js](http://gentoo-wiki.com/HARDWARE_Asus_A8Js)

I just recently purchased an A8js and will try to run ubuntu on it. I'll let you know how it goes. Interesting that 3d acceleration works but nvidia does not say the 7700 go is supported.

---

### Post by jackn on 2007-02-02
Thanks a bunch, Veratyr.

Please note [link]("http://www.rothlaender.net/a8js.html") added to first post.

Let's have some back and forth on Ubuntu on this machine in this thread.

Jackn

---

### Post by veratyr on 2007-02-06
My laptop just arrived tonight. It's my first laptop but I can say it is a very nice machine. There is a little flex in the screen but I don't plan on twisting it to try and break the thing. I installed edgy on it.

First task was getting 3d and the 1440x900 resolution working. Edgy detected the screen up to 1024x768. 3d works with the latest nvidia driver just fine. I had to disable the "nv" module in [FONT=monospace][/FONT]linux-restricted-modules-common and add the resolution to xorg.conf. I already have beryl installed with aiglx. Works great. 

I'll have to go through the[FONT=monospace][/FONT] list and try and get everything working. I havn't tested wireless yet cause I will have to first set up my linksys router to do wireless. I'll post more as I progress.

---

### Post by veratyr on 2007-02-06
I got sound working now too. Ubuntu does not seem to have /etc/modules.d/alsa so instead I added the following line to /etc/modprobe.d/alsa-base

```
options snd-hda-intel position_fix=1 model=3stack
```

---

### Post by veratyr on 2007-02-07
Edgy seems to detect the touchpad as a wacom tablet. I commented out the sections for wacom and added one for synaptics touchpad per this how to:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I also added some settings based on some recommendations I found. Vertical scroll could still work a little better. I'll have to play with the settings more.

```
Section "InputDevice"
    Identifier      "Synaptics Touchpad"
    Driver          "synaptics"
    Option         "SendCoreEvents" "True"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "VertScrollDelta" "100"
    Option         "SHMConfig" "on"
    Option         "LeftEdge"    "1700"
    Option         "RightEdge"    "5300"
    Option        "TopEdige"    "1700"
    Option        "BottomEdge"    "4200"
    Option        "FingerLow"    "25"
    Option        "FingerHigh"    "30"
    Option        "MaxTapTime"    "180"
    Option        "MaxTapMove"    "220"
    Option        "MinSpeed"    "0.09"
    Option        "MaxSpeed"    "0.18"
    Option        "AccelFactor"    "0.0015"
EndSection
```Having difficulties getting wireless to work. I have tested my wireless network with a windows laptop and it works fine. wifi radar can see my network and says its connected with an ip, but it still can't seem to connect to anything.

---

### Post by veratyr on 2007-02-07
It seems wifi-radar was the problem. I uninstalled it and installed network-manager isntead. Configured it to connect to my network and poof, connected and replying wirelessly.

[I]Update:
[/I]I followed this guide to get network manager working properly and wpa working

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by veratyr on 2007-02-08
Got the webcam working. Picture quality is kind of grainy. Don't know if that's the camera or the driver but here's what I did.

Get the driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

You want gspcav1-20070110.tar.gz

Make sure you have build-essential installed
```
sudo apt-get install build-essential
```Unpack it and cd to the directory it's in and...
```
make
```then...
```
sudo make install
```restart and it should work. I tested it with Camorama from the repos.

---

### Post by wundel on 2007-02-11
Thanks veratyr for your post!

My Asus works fine and 100% now :)

---

### Post by OvelhaNegra on 2007-02-15
Thanks for the information! I have the same laptop and I will install ubuntu on it, but I intended to use 6.06.

Any comments on that? Is it ok to install 6.06 rather than 6.10 on Asus A8JS machine?

What about the bits? Should I install 32bit version of ubuntu 6.06 or the 64bit is stable enough to run on Asus?

Thanks!

---

### Post by veratyr on 2007-02-15
Sorry, I didn't test dapper so I can't say. CPU scalling definatly won't work unless you use the new 2.6.20 kernel. I just upgraded mine to Feisty for the cpu scalling and to try out KVM. As for 32 vs 64 bit; that's entirely up to you. I installed 32 bit because it's my understanding that 64 bit is more of a pain from a lack of 64 bit software (codecs, flash plugin, ect). There are workarounds, but I just didn't want the extra hassle for a performance increase that you probably wont be able to notice. I'm waiting for the 64 bit side of things to mature more.

---

### Post by OvelhaNegra on 2007-02-17
Thank you for the reply!

I entirely agree about the 32 vs 64 bits issues... About the ubuntu version, I was prone to install 6.06 because of some fortran compilers that work fine with this kernel version, but are problems with 6.10...

About that, what is the "CPU scalling" you mention? Is it a critical issue for the asus a8js? Does it affect the performance of the machine?  

Thanks!

---

### Post by darrenism on 2007-02-18
Thanks for the info Veratyr.  I'm still having some issues with the sound, it seems to cut out when adjusting the volume via keyboard controls but aside from that everything seems to be okay.  Your touchpad settings are spot on and control is much better.

---

### Post by veratyr on 2007-02-18
Cpu scalling will throttle the processor speed down when it's not needed and back up when it is to save battery power. With feisty my core 2 duo slows down to about 1GHz and back up to 2GHz when it's needed. It may work with an older bios on 6.10. The latest kernel in feisty has a workaround for the bios/cpu scalling issue I think.

---

### Post by live4fun on 2007-03-07
Hi,
I just found this thread and I am happy to get closer to get full linux support for my machine.

I could get an image of my webcam but it is very noisy. 

Kopete has an option to auto configure colors. Without that it is not only noisy and dissorted but also too green and blue. 

Did you experience the same problem?

In Ekiga e.g. I didn't find a setup for resolution or an auto color adjustment at all. Do you know how I can get the quality I have experienced in windows with this cam to use it for video chats with linux?

Best Regards,
Chris

---

### Post by veratyr on 2007-03-08
Yes I have the same problem with the webcam being grainy. I suspect its the experimental driver we are using. I'm not sure how to fix it.

---

### Post by mrfuzzemz on 2007-03-08
I've everything working except for suspend to ram.  Has anybody got this working? If so, how? 

And does anyone else get an occasional black flash on the screen?

Thanks!

---

### Post by veratyr on 2007-03-09
I have yet to get suspend working as well. Havn't noticed any black flashes though.

---

### Post by mrfuzzemz on 2007-03-09
Maybe it has to do with Beryl.  Have you been using it?

---

### Post by veratyr on 2007-03-09
Yes I have Beryl running. Are you talking about suspend not working or the black flashing?

---

### Post by mrfuzzemz on 2007-03-09
The black flashing. 

I'd like to get the suspend to ram working--would you know what we could try?

---

### Post by mrfuzzemz on 2007-03-11
I think I may have figured out the black flashing.  I'm using Feisty ( I don't think that is the problem per se, but I thought it might be important to note.) What refresh rate are you using?  In System Preferences > Screen Resolution- What does it say? Also what is the refresh rate setting in your NVidia driver settings?
Thanks

---

### Post by live4fun on 2007-03-18
I still have a issue with the build in sound.

When I plug in an external mic (headset) it is not used. The build in one is still active. 

Does anybody of you experience the same behavior?
Do you know a solution?

I wan't to use the full benefit of my headset for internet telephony.

Some else I noticed:
The sound is not conrolled by the main control in kmixer (the one displayed in the taskbar) but controlled by the headphone slidebar.

I appreciate any help on how to get my external mic working.

Best Regards,
Chris

---

### Post by mrfuzzemz on 2007-03-18
I've been using Ubuntu Feisty so I don't the amount that I can try and assist you, but I can assure you configuring sound channels has certainly improved in Feisty.  You can select which channel your Function keys control.  I also haven't used my microphone for anything.

---

### Post by hapablap on 2007-03-18
veratyr, could you help me figure out why my touchpad scroll isnt working ? I've got an asus f3jm and I tried to use your sample code and commented out the wacom stuff but I still get an error when I try to restart gnome. I've attached some of my xorg code. Let me know if theres something wrong. Thanks! Btw, im using edgy.

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier      "Synaptics Touchpad"
    Driver          "synaptics"
    Option         "SendCoreEvents" "True"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "VertScrollDelta" "100"
    Option         "SHMConfig" "on"
    Option         "LeftEdge"    "1700"
    Option         "RightEdge"    "5300"
    Option        "TopEdige"    "1700"
    Option        "BottomEdge"    "4200"
    Option        "FingerLow"    "25"
    Option        "FingerHigh"    "30"
    Option        "MaxTapTime"    "180"
    Option        "MaxTapMove"    "220"
    Option        "MinSpeed"    "0.09"
    Option        "MaxSpeed"    "0.18"
    Option        "AccelFactor"    "0.0015"
EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
  #  Identifier     "stylus"
   # Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "stylus"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
  #  Identifier     "eraser"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "eraser"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
  #  Identifier     "cursor"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "cursor"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
```

---

### Post by mrfuzzemz on 2007-03-18
Make sure you've got synaptics in your server layout like so:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Synaptics Touchpad"
EndSection
```

---

### Post by hapablap on 2007-03-19
I completely forgot about that. Thanks!!

---

### Post by hapablap on 2007-03-20
Is there a way to configure back/forward tapping zones on the touchpad? I tried using qsynaptics but it doesnt seem to have that option. Is there a different program to configure this option or can it be done by editing xorg.conf ? Thanks.

---

### Post by mrfuzzemz on 2007-03-22
I know you can use two-finger-tap as middle button click and three fingers as right click without any further configuration.  Double-tap-drag should also work.  These are the only functions I use. 

After a little searching I thought you could check this out:
[http://ubuntuforums.org/showthread.php?t=113927&highlight=touchpad+options](http://ubuntuforums.org/showthread.php?t=113927&highlight=touchpad+options)

Let me know how that goes.

On a completely separate note I would like to let everyone with an A8Js know that with the most recent updates for Feisty I have been able to SUCCESSFULLY RESUME FROM SUSPENDING TO RAM.  So look forward to the release in April.

---

### Post by hapablap on 2007-03-30
I recently upgraded to feisty as well, but I lost my nvidia twinview settings. Could someone post their proper xorg settings for dual monitor setup? Thanks!!

---

### Post by live4fun on 2007-03-31
Same problem here. Twinview doesn't work any more. Xorg.conf is still the same as before the update. It was not replaced by installing a newer packages.
You can start 
>nvidia-settings 
and get a beautiful UI to setup your monitors.
I have two problems with it so far:
1) It doesn't allow me to set my external display to its native resolution 1440x900 (just not available in the resolution options)
2) When i have the screens spawn (even with an less then optimal resolution for my external lcd) a window set to fullscreen is streched over both of them. Not very usable.

I couldn't find out which config file to tweak to make nvidia-settings allow 1440x900. Perhaps there is some failure when it tries to detect my monitor as it states it's maximum possible resolution would be 1400x1050.

---

### Post by live4fun on 2007-03-31
> **mrfuzzemz said:**
> ...You can select which channel your Function keys control. 

Where can you do this? I experienced that since feisty skype shows OSS and ALSA available.

---

### Post by mrfuzzemz on 2007-03-31
Go to System > Preferences > Sound.

Under 'Default Mixer Tracks' you can select the default channel.

---

### Post by live4fun on 2007-04-01
I could resolve the resolution [issue.]("http://ubuntuforums.org/showthread.php?p=2386090#post2386090")

---

### Post by live4fun on 2007-04-05
I got so used to two external screens at work I would love to have this at home.

I wounder if it is possible to have one screen connected to the DVI port and one to the VGA port.
I know I can use the laptop and one external screen at the same time. 
But as view angle, brightness and size differe a lot I would like to have two dedicated LCD screens.

Does anybody know how to find out?

---

### Post by mrfuzzemz on 2007-04-05
> **live4fun said:**
> I got so used to two external screens at work I would love to have this at home.

I wounder if it is possible to have one screen connected to the DVI port and one to the VGA port.
I know I can use the laptop and one external screen at the same time. 
But as view angle, brightness and size differe a lot I would like to have two dedicated LCD screens.

Does anybody know how to find out?

Have you tried booting with two screens attached?

---

### Post by buntu_hugenewbie11 on 2007-04-06
I recently got an A8Js and decided to put Ubuntu "fiesty" on it. (I am a newbie)
Over the weeks I have slowly been trying to get full functionality going but it takes some time.Search
My latest troublespots include: 
1) hibernate locking up from kde: I hibernate and then upon reactivation the system locks up.
2) Alsa mixer sound disappearing: I use amarok and after making a change in alsamixer I need to reboot the computer to make the sound work again.
3) After getting my graphics card working my menu fonts (location file etc) for Kronequer are HUGE is there anyway to adjust this?
4) I installed the webcam driver but I was wondering what utility I should install to use it and check if it works (preferably kde compatible)?
5) Is it worth trying to get the function key to work? I would love to be able to make quick sound adjustments via keyboard shortcuts without having to open alsamixer?
6) How can I underclock and overclock the vid card easily? Is there a utility? This would help save battery life when on the road?
7) Is there a utility for KDE that shows how much battery life is left?

Sorry about all the issues especially if they're trivial- I'm very new to this all. If you have any answers to these questions and problems it would be helpful.
Thanks

---

### Post by mrfuzzemz on 2007-04-06
> **buntu_hugenewbie11 said:**
> I recently got an A8Js and decided to put Ubuntu "fiesty" on it. (I am a newbie)
Over the weeks I have slowly been trying to get full functionality going but it takes some time.Search
My latest troublespots include: 
1) hibernate locking up from kde: I hibernate and then upon reactivation the system locks up.
2) Alsa mixer sound disappearing: I use amarok and after making a change in alsamixer I need to reboot the computer to make the sound work again.
3) After getting my graphics card working my menu fonts (location file etc) for Kronequer are HUGE is there anyway to adjust this?
4) I installed the webcam driver but I was wondering what utility I should install to use it and check if it works (preferably kde compatible)?
5) Is it worth trying to get the function key to work? I would love to be able to make quick sound adjustments via keyboard shortcuts without having to open alsamixer?
6) How can I underclock and overclock the vid card easily? Is there a utility? This would help save battery life when on the road?
7) Is there a utility for KDE that shows how much battery life is left?

Sorry about all the issues especially if they're trivial- I'm very new to this all. If you have any answers to these questions and problems it would be helpful.
Thanks

I will try and help with some of these:

2.  Be sure to enter the sound card "fix" for the sound card in this notebook.  It is listed elsewhere in the thread, but here it is again.  You'll want to add:

```
options snd-hda-intel position_fix=1 model=3stack
```
 to > /etc/modprobe.d/alsa-base
and reboot.  That should take care of that.

4.  I used Camorama to test the camera.

5.  These seem to work in GNOME just fine.  All I had to do was change the channel they control in the sound settings (I don't know what this might be like in KDE, but you could have a look around.)

6.  Easiest (Graphical) way to underclock (I would grealy advise AGAINST overclocking) would be to edit your /etc/X11/xorg.conf and add 
```
Option "Coolbits" "1"
``` 
under your graphics like so:
```

Section "Device"
    Identifier  "Generic Graphics"
    Driver      "nvidia"
    Option "DynamicClocks" "1"
    Option "Coolbits" "1" # Add it here
EndSection
```

This is just an example, don't add or delete anything else unless you know what you are doing.

Once you do that you can go to NVidia settings in the menu or type nvidia-settings in a terminal and lower the clock speed there.

7.  You should be able to right click on a panel and find a power meter to add.

Hope this helps some!!

---

### Post by buntu_hugenewbie11 on 2007-04-06
thanks for the help.
But camorama does not find my video device does this mean the camera driver did not get installed?
And I do not seem to have a power applet I can add to panel is there one I need to install?
Thanks again

---

### Post by mrfuzzemz on 2007-04-06
> **buntu_hugenewbie11 said:**
> thanks for the help.
But camorama does not find my video device does this mean the camera driver did not get installed?
And I do not seem to have a power applet I can add to panel is there one I need to install?
Thanks again

Search the package manager for "power" or "battery" and see what comes up.

You may want to follow through with another install of gspca (camera driver) and see if that helps.  I've had the camera on this thing working with Ubuntu and Sabayon (KDE).

---

### Post by buntu_hugenewbie11 on 2007-04-07
I've tried reinstalling and still get the error msg:
"Could not connect to device (dev/video0/)...
So obviously does nor install so I must be reinstalling incorrectly. Does anyone have an idea of how to reinstall gspcav? I've noticed fiesty has a distro for this should I just update?

---

### Post by mrfuzzemz on 2007-04-07
> **buntu_hugenewbie11 said:**
> I've tried reinstalling and still get the error msg:
"Could not connect to device (dev/video0/)...
So obviously does nor install so I must be reinstalling incorrectly. Does anyone have an idea of how to reinstall gspcav? I've noticed fiesty has a distro for this should I just update?

Here are the exact instructions for the driver.  If this doesn't work, then I'm not 

[http://ubuntuforums.org/showthread.php?p=2126584#post2126584](http://ubuntuforums.org/showthread.php?p=2126584#post2126584)

Above is everything you should have to do to get it working.

---

### Post by buntu_hugenewbie11 on 2007-04-07
It does not work. How can I check that there is not some dependency issue? I don't understand what could be wrong. when I use the tar command I use -xvf as the option commands should I try something different? Is there a way I can delete all relevant other drivers and then reinstall.
Sorry about this especially if it is trivial.

---

### Post by mrfuzzemz on 2007-04-07
> **buntu_hugenewbie11 said:**
> It does not work. How can I check that there is not some dependency issue? I don't understand what could be wrong. when I use the tar command I use -xvf as the option commands should I try something different? Is there a way I can delete all relevant other drivers and then reinstall.
Sorry about this especially if it is trivial.

Hmmm.... If you didn't get any errors while compiling and installing then you could try this:
```
sudo modprobe gspca
```

This should load the kernel module for the camera.  Report any errors and we'll see where we can go from there.

---

### Post by buntu_hugenewbie11 on 2007-04-08
Still same error- I can't seem to get this cam to work. :-(

---

### Post by buntu_hugenewbie11 on 2007-04-09
Anyone have any idea what I can do to clear my camera drivers?? That way I could maybe reinstall. The modprobe command does not work at all for me either is that weird??

---

### Post by buntu_hugenewbie11 on 2007-04-10
Okay it was because i had gspca-source installed. I just had to autoremove this.
So my cam works thanks people.
So on to my next obstacle: How do you get the quick buttons to work?
Also for the wireless I just use knetwork manager is it better to set it up similar to [http://www.rothlaender.net/a8js.html?](http://www.rothlaender.net/a8js.html?)
Does ubuntu have an emerge command?
Sorry about the newbie Q's.

---

### Post by mrfuzzemz on 2007-04-10
> **buntu_hugenewbie11 said:**
> Okay it was because i had gspca-source installed. I just had to autoremove this.
So my cam works thanks people.
So on to my next obstacle: How do you get the quick buttons to work?
Also for the wireless I just use knetwork manager is it better to set it up similar to [http://www.rothlaender.net/a8js.html?](http://www.rothlaender.net/a8js.html?)
Does ubuntu have an emerge command?
Sorry about the newbie Q's.


Emerge is part of the Gentoo package manager Portage. It is probably possible, but not really necessary to install for Ubuntu.  Synaptic and aptitude do the trick great.  Use Synaptic for a gui interface or use apt-get at the command-line.

To install a program:

```
sudo apt-get install PROGRAM
```

to remove:

```
sudo apt-get remove PROGRAM
```

to update:
```

sudo apt-get update 
sudo apt-get upgrade or sudo apt-get dist-upgrade
```

There are plenty of other places you can look to find out more about Synaptic and Aptitude.

---

### Post by jackn on 2007-04-11
OK, so I'm working on installing Edgy on the a8js.

Thanks to guides here and elsewhere, I'm making headway. Got Nvidia, Beryl and sound (except for the controls... for the time being), for example, to work. But it's still a work in progress. At this point, rather than have recourse to the forum for every step, I'd rather struggle with it and learn something in the process. Moreover, I'm waiting for the final release of Feisty in about a week, as mrfuzzemz says the suspend to RAM depends on it, and veratyr says the CPU scaling does.

The purpose of this post is rather to suggest a how-to, or a Wiki post on Ubuntu on a8js. It looks like some of us have managed a full working setup. There is no detailed and up-to-date how-to for Ubuntu on the a8js. There is one for [gentoo]("http://http://www.willempen.org/asus-a8jc-on-linux/"), which is probably very informative, but doesn't quite cut it for another distro, especially if you still have a lot to learn... A how-to for [Ubuntu]("http://www.willempen.org/asus-a8jc-on-linux/") does exist, but it runs Dapper, it must have the older, (CPU scaling-) compatible BIOS version, it is for the a8jc, and it is skimpy on detail. There is no a8js entry in the Ubuntu hardware list.

Now, I love writing and I'd love to write a how-to myself, and if need be I will, but right now I just don't know enough to do it. As I've said, I'm still struggling with my own setup. 
Could somebody undertake to do this? 

It's perfectly alright if others can't, I will definitely do it myself then, as best I can, but what with the wait for Feisty and how much time I can devote to setting up, it can easily take more than a month. 

What do others think of the need for such a how-to? If I do end up working on this, can I have some input on drafts from others?

Thanks for all the input so far.

Thanks for the attention,
Jackn

---

### Post by jackn on 2007-04-12
I've tried Veratyr's protocol for the webcam.

After downloading the package, untarring it, and cd-ing into the newly-created directory, I ran 'make':

```
~/my_tarballs/gspcav1-20070110$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jacknn/my_tarballs/gspcav1-20070110 CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
Makefile:450: .config: No such file or directory
  Building modules, stage 2.
/lib/modules/2.6.17-11-386/build/scripts/Makefile.modpost:38: .config: No such file or directory
make[2]: *** No rule to make target `.config'.  Stop.
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [default] Error 2

```

I'm not sure what this means.

Indeed, a .config file is expected in the file 'Makefile.modpost' mentioned in the above output:

```
include .config
```

(taken from Makefile.modpost)
Is it a .config file belonging to the webcam package being built? 

Among the files of the untarred package there is no 'config':
```

gspcav1-20070110$ ls
changelog  Etoms         gspca.h    Pixart   Sunplus-jpeg  Vimicro
Conexant   gspca_build   Makefile   Sonix    Transvision
decoder    gspca_core.c  Mars-Semi  Sunplus  utils
```


I guess a .config file is not necessary in this case, and, indeed, contrary to the usual building from source routine, veratyr starts directly from 'make', with no 'config' step.

Yet, the sysem seems to expect a 'config'.

There is no Readme file in the package.

Help?


Jackn

---

### Post by phatdood9 on 2007-04-21
Hi, has anyone else had problems with the wlan on feisty 7.04?

here is some info:

```
$ lsmod | grep 3945
ipw3945               118816  0 
ieee80211              50412  1 ipw3945

```

modprobe ipw3945 returns nothing
the wireless led on the laptop is activated

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

lshw truncated:
```
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0
                resources: iomemory:fe0ff000-fe0fffff irq:16

```

ifconfig:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F3:F3:5A:76  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fef3:5a76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12771970 (12.1 MiB)  TX bytes:1639102 (1.5 MiB)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1776 (1.7 KiB)  TX bytes:1776 (1.7 KiB)

```

/etc/iftab has only 1 entry, eth0, which is my regular wired nic

network-manager only shows the wired ethernet connection and the modem

thanks :KS

---

### Post by phatdood9 on 2007-04-22
fixed! forgot to update generic drivers when switching kernels :KS

---

### Post by buntu_hugenewbie11 on 2007-04-30
Ok so I might be the most regular poster here.

I have a new problem that seems quite unique. I am using feisty 7.04 and using kde.
Now when I start up the system cannot find my wired connection under eth0 though through knetworkmanager my wireless works fine.
I just don't have the choice to use the wired connection.
Though when I use the manual configuration in knetwrokmanager it says it sees my ethernet card?!?
And the error I get is something along the lines of:
eth0: Link is not Ready
And yes my cables are fine- actually windows is working fine the wired network.
So I'm wondering if anyone else has had this problem? Or if they know of how to fix it!!
Please help me. :-(

---

### Post by wtruong on 2007-05-01
Is there anyone that has a disfunctional brightness increase key, aka fn+f6.  my fn+f5 works though.  So any ideas guys?

---

### Post by mrfuzzemz on 2007-05-01
Yeah.  I've seen people mention that problem before.  It doesn't bother me as I don't change the brightness often, but I do have the brightness control appet in my gnome panel up top.  You could also probably quite easily map the key, but I just haven't had a problem with it.

---

### Post by veratyr on 2007-05-01
Seems with a clean install of feisty I'm unable to get my webcam working. It was working back with the beta and the gspcav driver. Now I get "could not connect to device (/dev/video0)" when launching camorama. Ekiga can't detect a device either. I've tried reinstalling the driver.

---

### Post by live4fun on 2007-05-03
> **mrfuzzemz said:**
> I will try and help with some of these:
...
6.  Easiest (Graphical) way to underclock (I would grealy advise AGAINST overclocking) would be to edit your /etc/X11/xorg.conf and add 
```
Option "Coolbits" "1"
``` 
under your graphics like so:
```

Section "Device"
    Identifier  "Generic Graphics"
    Driver      "nvidia"
    Option "DynamicClocks" "1"
    Option "Coolbits" "1" # Add it here
EndSection
```

This is just an example, don't add or delete anything else unless you know what you are doing.

Once you do that you can go to NVidia settings in the menu or type nvidia-settings in a terminal and lower the clock speed there.
...


I added the coolbits option as adviced but can't see an entry for changing the clock speed in the nvidia-settings ui. I am running feisty with all current updates applied (apt-get upgrade/ apt-get dist-upgrade don't want to install anything more recent)

Cheers
live4fun

---

### Post by mrfuzzemz on 2007-05-03
It is "Clock Frequencies" under GPU.  For the Go 7700 you must have the 1-.9755 driver installed (this is nvidia-glx-new in Synaptic).  Any older driver will not have clocking support for this card.

---

### Post by live4fun on 2007-05-03
Now I have CPU underclocking. Thx :)

I was a little surprised that restarting the xserver was not sufficient. Complained about an unmatching kernel module. After rebooting everything worked fine. I was to lazy to experiment which module I would have to have reloaded.

Thx for your fast response.

---

### Post by fyllekajan on 2007-05-16
I'm having problems reading some data dvds on my a8js.. most dvds work fine though.. and there's nothing wrong with these disks I have tested them on my old laptop.. but on this laptop nautilus hangs when browsing the directories, well sometimes it just says no disk. Maybe I'm missing some drivers or something? Anyone else experiencing this? Thanks

---

### Post by alienvenom on 2007-05-18
> **wtruong said:**
> Is there anyone that has a disfunctional brightness increase key, aka fn+f6.  my fn+f5 works though.  So any ideas guys?

I just recently bought an ASUS A8Js and it came with BIOS 213 (not even on ASUS' website yet). Either way, BIOSs > 205 cause issues with the LCD brightness. According to ASUS in newer versions of the BIOS, the brightness is controlled by the ATK driver which you will see in Windows.

I was a little hesitant at first, but I downgraded to 203 as mentioned on the following website to get cpu scaling to work (without fudging with the kernel source), brightness controls and some serial ATA issues.

[http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html)

ASUS A8Js Version 203 BIOS: [http://zeus.dogtoe.com/files/a8js/A8JsvAS.203.zip](http://zeus.dogtoe.com/files/a8js/A8JsvAS.203.zip)

(Note: It will probably only work with ASUS A8Js model laptops.)

---

### Post by mrfuzzemz on 2007-05-18
Is the only issue with the brightness key in the newer BIOS?  I get around that by having a brightness applet in my gnome-panel.  Does cpu scaling not work with Fiesty with the latest versions of the BIOS?

---

### Post by queen_yoshi on 2007-05-22
I just bought my A8JS last week and have the newer bios, and CPU scaling on Feisty worked out the box, not worried about screen brightness so cant say about that.

After reading this thread I got the right drivers installed and resolution sorted so also want to say thanks :D

---

### Post by buntu_hugenewbie11 on 2007-05-29
veratyr,
Did you ever get the camera working as I have the same problem??

---

### Post by live4fun on 2007-05-30
Hi,

I can use the nvidia-settings tool to underclock my GPU when I have an external monitor attached and the internal display deactivated.

Can anybody of you underclock the internal display? This would be quite useful to get an extra bunch of battery life on the go.

I have two more issues:
1) How to read current CPU temperature? Looks like the fan is running very often without the notebook getting too warm at all.
2) The microphone plug still doesn't work for me. Can anybody of you plug in a mic and test if is used instead of the internal one? E.g. Plug it in and skype or make a recording while temporarily covering the internal mic with a finger. So if this doesn't affect the recording you know that really the plugged in mic is used.

I got a lot of complains about bad mic quality when using skype.

Thanks for any hints.

P.S.: How much battery life do you get?

---

### Post by live4fun on 2007-05-30
I kept up experimenting with alsa.
[http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html)
According to rothlaender you can use either

options snd-hda-intel model=3stack
to have everything working with the internal mic.

or 

options snd-hda-intel model=laptop
to have everything working with external mic.

The first has both mics activated at a time. So while using skype my conversation partner hears my fan and typing.
With model=laptop only the external plugged in mic is working but when i plugin headphones into the headphone jack the internal speakers mute and I have no output on the headphones.

I build the lattest alsa driver against the current kernel image.
Following this howto [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I can also use 
options snd-hda-intel model=ref
which gives me an individual volume control for front (=internal speakers) and headphone. But still both mics (plugged in and internal are working at a time).

I found out that you can display cup temp with
acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 51.0 degrees C
  AC Adapter 1: on-line

I am currently trying to build a vanilla kernel to see if i can achive what [http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html)
discribes.

Any ideas appreciated.

---

### Post by Nilelith on 2007-05-31
Hey all, thx to this thread ive been able to get almost everything working apart from the Analog Modem. Has anyone had any luck at all getting it working, if so could they post guide? :)

ive seen [http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html) but i dont really understand what his taking about. still learning my way around.

The guide ive already tried is this one, but still didnt detect the modem on ttySL0 :(

EDIT, ive managed to get the scanModem script to detect the modem now i think, after installing alsa-driver-1.0.14rc4.tar.bz2 utils and lib

Modprobe snd-intel8x0m
FATAL: Module snd-intel8x0m not found

not sure how to fix that.

Any help would be great.
Cheers

---

### Post by LUNITIC on 2007-07-08
Purchased the same laptop last April. New to LINUX, most of what I’m reading seems way over my head but eager to learn. Been over seas and experimenting with different Distros and UBUNTU seems to do most of what I need right out of the box.

q: Is there a way to compile all the different driver strings, into one complete load for this particular computer for say someone like myself? It's interesting that so much work has been done on this particular machine. Is it possible to say download one complete update, from the work that's been tested and UBUNTU updates?

Forgive me, like I say, I'm new to this but very familiar to computers.

---

### Post by mrfuzzemz on 2007-08-02
I just wanted to say that for those who care about being able to suspend:

I've been able to successfully suspend twice in a row with the latest NVidia driver (100.14.11).

---

### Post by erikringmar on 2007-09-17
Dear all, 

I keep on having problems with the sound on my Asus (which I otherwise adore).  I followed advice here and added:

options snd-hda-intel position_fix=1 model=3stack

to the relevant file.  The computer is making horrible high-pitched sounds and the speakers in the front seem to be heating up.  What's going wrong?

yours,

Erik

---

### Post by mrfuzzemz on 2007-09-17
> **erikringmar said:**
> Dear all, 

I keep on having problems with the sound on my Asus (which I otherwise adore).  I followed advice here and added:

options snd-hda-intel position_fix=1 model=3stack

to the relevant file.  The computer is making horrible high-pitched sounds and the speakers in the front seem to be heating up.  What's going wrong?

yours,

Erik

Did you say the speakers are heating up? And it's an A8Js?  The fix you mentioned seems to have worked for everyone else.
Here is some great A8Js linux info:
[http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html)

The screeching could possibly be that you have playback enabled for the microphone.  This causes feedback.

---

### Post by buntu_hugenewbie11 on 2007-10-20
So I am using Feisty and Kubuntu.
I tried to use the KDE system setiings to try and get 2 monitors working.
Unfortunately it changed my entire xorg.conf file.
I was wondering if someone could post their xorg.conf file for the A8Js?
Please please please.

---

### Post by buntu_hugenewbie11 on 2007-11-08
So I figured out the twinview.
But sure enough I decided to upgrade my distribution to gutsy.
Has anyone had trouble with the nvidia drivers?
Is it better to use the nvidia-glx-new drivers or to stick with nvidia's proprietary driver?
Can you still underclock and overclock with glx?
Currently I am having trouble starting the xserver and it seems to be a driver issue.
Anybody else experiencing success or problems with Gutsy and the asus A8js?

---

### Post by forevertheuni on 2008-01-02
can anyone record from microphone?I'm using gutsy and I can't use ekiga openwengo etc etc. It used to work.
I removed the 3stack option and everything works the same

---

