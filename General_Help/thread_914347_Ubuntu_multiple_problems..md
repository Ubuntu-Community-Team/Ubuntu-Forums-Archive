---
title: "Ubuntu multiple problems."
date: 2008-09-08
forum: General Help
---

### Post by l33t p1mp on 2008-09-08
First time use of ubuntu on wifi, and second time use of ubuntu ever, so I am a huge noob. :lolflag: Heres my problem. I am using wifi with ubuntu this time, ubuntu sees the connections near my houes, including my house (unsecured). I am currently on roaming mode. When I connect to it, it connects, and when I open up firefox, it just shows page can not be displayed.

Second question, I need the video drives installed for the compiz fusion, and the effects to work, right? How do I install them, and where do I get them from?

Thats it for now.
Thanks.
-l33t p1mp

---

### Post by ad_267 on 2008-09-08
I don't know about the wifi problem but for installing video drivers it depends on what video card you have. If you have an Intel the drivers are open source so are installed already. If you have Nvidia or ATI you can go to System - Administration - Hardware Drivers and then enable the drivers. There's a sticky about desktop effects here that explains everything: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by amedac on 2008-09-08
If you want help, you must provide some informations about your configuration. What Ubuntu version? What wireless card? What graphic card?
After you provide this informations, someone will help you. Greetings from Croatia, amedac

---

### Post by l33t p1mp on 2008-09-08
I am using an 8800 gts 512, and for the wifi, I said I was on discovery mode. I am using a WMP54G for a card, and a WRT54GX2 for a router.

---

### Post by ad_267 on 2008-09-08
Ok so you should be able to go to System - Administration - Hardware Drivers to enable Nvidia drivers.

---

### Post by l33t p1mp on 2008-09-08
Cool, thanks ad_267, I will go try it right now.

---

### Post by l33t p1mp on 2008-09-08
Ok, I tried what you said, and first off, there is no Hardware Drivers button under there. There is only one that says drivers, and it is restricted drivers. When I press it, it says I have no need for restricted drivers. Also, I am on 7.04 ubuntu 32 bit edition.

---

### Post by ad_267 on 2008-09-08
Ok I think that's because that version of Ubuntu doesn't have the up to date drivers that support your video card. I would recommend updating to the latest version, 8.04.

---

### Post by l33t p1mp on 2008-09-08
I would download it, but that takes me ages, and I am having problems burn the ISO's to cd...any alternative way? Postage takes way too long though. :(

Edit: I am downloading 8.04 from this site.
[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)
It claims to be a .iso, and a .rar file at the same time. Do I extract it for burning? Is it supposed to be many folders, or a single .iso file? What program should I use to burn it?

---

### Post by ad_267 on 2008-09-08
It should be a single .iso file. I'm not sure what burning software comes with 7.04, it's probably GnomeBaker. There should be something under applications - sound and video that you can use and select "burn image" to burn the .iso file. After you burn the cd it should come out as a lot of files and folders on the disc.

If that's too slow to download you could try with the torrent download.

---

### Post by panhandle on 2008-09-08
If you have a USB drive large enough, you can use that.

Here's a link: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by l33t p1mp on 2008-09-08
@panhandle
I was planning on doing that lol, I am out of cd's. :p

---

### Post by l33t p1mp on 2008-09-08
@ad_267
When I download, it is a rar folder that says its a .iso. Should I extract it, or burn it as is? What burner do I use with windows?

---

### Post by ad_267 on 2008-09-08
There is a page here that explains how to burn the cd using InfraRecorder for Windows: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
You can also use Nero or something similar if you have that.

Another option is that you might be able to find a Linux magazine that comes with an Ubuntu CD.

---

### Post by l33t p1mp on 2008-09-08
Thanks ad_267. I will install it tonight and post again if it doesnt work.

---

### Post by l33t p1mp on 2008-09-08
There, I now have ubuntu 8.04 installed. I fixed the internet problem (and this post is my first from ubuntu os). Thanks for all the help guys.

---

### Post by ad_267 on 2008-09-08
Awesome that's good to hear! Have fun and if you need any help just ask in the forums.

I recommend you give this a read first as it explains installing software for Ubuntu. The process is a bit different to Windows. [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Also it's a good idea to install the ubuntu-restricted-extras package so you get the adobe flash player and mp3 and other useful codecs.

---

### Post by l33t p1mp on 2008-09-09
Wtf...I posted like 2 messages and they are gone...I was saying that my driver borked, and it is displaying a max of 800x600, instead of 1680x1050...now, it is even worst than before. Please help.

Here is the detailed story. I installed the driver, all went fine during installation. It tells me to reboot, so I reboot it. On boot, it gives me an error saying that it can only display in low-quality mode, and gives me a list of lcds and gpus. I choose my lcd, native resolution, and gpu from the list, and press continue. It boots up in 800x600, and it wont let me put the resolution any higher...after that, it told me I needed to reboot again, so I did, and same thing. I put in my information again, and booted. Still 800x600, and I have no clue what to do...

---

### Post by ad_267 on 2008-09-09
Press Alt-F2 and run "gksu nvidia-settings"

You should be able to set your resolution from there. Make sure you select "Save to X Configuration File" so that the settings stick.

You might have to install nvidia-settings if it isn't already installed.

---

### Post by l33t p1mp on 2008-09-09
Tried the alt+f2 thing, but it just keeps on booting as normal...what am I doing wrong?'

Oh wait, gotcha, you meant IN ubuntu lol...

Edit again: Still not working...when I do what you said, it just closes and goes to my firefox...

---

### Post by ad_267 on 2008-09-09
So it doesn't open nvidia-settings at all? Check that it's installed by going to System - Administration - Synaptic Package Manager and search for nvidia-settings and install it if it isn't already.

---

### Post by l33t p1mp on 2008-09-09
I had nvidia glx new installed. Should I install the nvidia glx isntead?

I think I should stay with new because it is for the newer cards...mine is semi-new now lol.

---

### Post by ad_267 on 2008-09-09
Yeah keep the new drivers. I thought nvidia-settings was installed with the drivers but maybe not. When you get that running it should be able to set the resolution, I think there's issues with nvidia-drivers and the normal screen resolution tool.

---

### Post by l33t p1mp on 2008-09-09
So...what do I do now? :p

---

### Post by ad_267 on 2008-09-09
Is nvidia-settings installed? You should be able to press alt-f2 to bring up the run dialog and run "gksu nvidia-settings" but if that doesn't work try running it from a terminal (applications - accessories - terminal) and typing "gksu nvidia-settings"

---

### Post by l33t p1mp on 2008-09-09
It is not installed, but I am downloading it atm with synaptic package manager.

---

### Post by l33t p1mp on 2008-09-09
Ok, I downloaded it, and typed what you said for gksu. It opens the X server settings, and gives me this error. "You do not appear to be using the NVIDIA X driver. Please edit your X config file (just run nvidia-xconfig as root) and restart the X server.

Problem is, X is only for the older gpu driver update...

---

### Post by ad_267 on 2008-09-09
If you have the nvidia-glx-new drivers then yeah you should be using the nvidia X drivers. Is the nvidia-driver still enabled under System - Administration - Hardware Drivers?

If it isn't then enable it and log in and out again. Otherwise try doing what it says about running nvidia-xconfig. Go to applications - accessories - terminal and run "sudo nvidia-xconfig" and then log out and back in again and try to run "gksu nvidia-settings" again.

---

### Post by l33t p1mp on 2008-09-09
No, whenever I enable it, it asks for a restart, I restart, it gives error on boot, then goes into 800x600 and gives me all that crap again...thats where the problem is at lol. Every time I reboot, it is disabled btw.

WHAT THE HELL?
Logging in then out worked! THANK YOU!!!!!!!!!!!!!!! :D:D:D:D::D:D:D

---

### Post by l33t p1mp on 2008-09-09
Last question. Compiz is working atm, but how do I change the settings for it? I put it on extra atm btw.

---

### Post by ad_267 on 2008-09-09
Ok awesome! So you managed to get into nvidia-settings and change the resolution? Make sure you select "Save to X configuration file" otherwise the changes will be lost.

---

### Post by l33t p1mp on 2008-09-09
Check, and check. How do I get the desktop cube to work? It is activated, but doesnt work lol. Also, where do I get more animations for my desktop?

---

### Post by ad_267 on 2008-09-09
To enable the cube you need to install compizconfig-settings-manager in Synaptic and then you can go to System - Preferences - Advanced Desktop Effects Settings.

You need to change the horizontal virtual size to 4 under General Options - Desktop Size. Then you need to enable the desktop cube and rotate cube plugins.

There's a sticky here that explains everything: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by l33t p1mp on 2008-09-10
Thanks again. I saved everything last night, but when I rebooted it gave me the low-quality error again. *facepalm* In the X server, it says I am not running it and bla bla bla. In the driver thing, it says that the driver is in use and working fine...
Damn it, penguin!

---

### Post by l33t p1mp on 2008-09-10
Crap...now my driver is REALLY ****** up...when it boots into ubuntu with the logo, it is fine, when it gets to the log in screen and everything else, the pictures are moved around, doubled up, reflected, blurry, etc etc...HELP :confused: :(

---

### Post by ad_267 on 2008-09-10
Bah I dunno man, I haven't had problems like that before.

You could try reconfiguring X to use the default drivers by entering this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then just log in and enable the nvidia-drivers and then log out and in again and run "gksu nvidia-settings" and set up your screens correctly and select "Save to X Configuration File". 

That way you know that nothing else could be messing with the configuration.

---

### Post by l33t p1mp on 2008-09-10
I would try, but the screen is completely messed up. I can not see anything. Its all out of whack. Reinstalling would be nice, but not possible atm...:( *dvd reader is shot, flash drive is too small*

---

### Post by ad_267 on 2008-09-10
When you first turn on the computer there should be an option from the boot menu to boot into recovery mode. You can select that and you will get a root terminal where you can enter:

```
dpkg-reconfigure -phigh xserver-xorg
```

Another option is a program called envy that will download and install the latest drivers from the Nvidia website. The package to install is envyng-gtk and there's some instructions here: [https://help.ubuntu.com/community/NvidiaManual#Installation%20with%20Envy/EnvyNG](https://help.ubuntu.com/community/NvidiaManual#Installation%20with%20Envy/EnvyNG)

I haven't used that method myself but a lot of people recommend it if you're having problems with the Nvidia drivers in Ubuntu.

---

### Post by l33t p1mp on 2008-09-12
Thanks a lot, I am going to try that.

---

