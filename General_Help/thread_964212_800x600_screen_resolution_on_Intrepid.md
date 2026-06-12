---
title: "800x600 screen resolution on Intrepid"
date: 2008-10-30
forum: General Help
---

### Post by somersetsimon on 2008-10-30
OK, so I've now installed Intrepid! The first thing I always had to do with previous versions is to sort out the screen resolution. I had to use displayconfig-gtk to set my monitor resolution. Started up Intrepid and, of course, the screen resolution is 800x600. Nothing available in the 'Screen Resolution' menu item, so I tried to run displayconfig-gtk and it said there was no such thing! How do I change my screen resolution now?

Thanks

Simon

---

### Post by xreaper on 2008-10-30
Hey, I had the same problem with mine last night, but managed to fix it manually. have you enabled restricted drivers? and what is your hardware?

---

### Post by somersetsimon on 2008-10-30
> **xreaper said:**
> Hey, I had the same problem with mine last night, but managed to fix it manually. have you enabled restricted drivers? and what is your hardware?

I have a Toshiba laptop with a Trident Cyberblade graphics card. How do you enable restricted drivers? In this new version I can't even find where my graphics card is identified like in display-config!

---

### Post by xreaper on 2008-10-30
I installed mine on a desktop computer, so this might be a bit different.. but try to navigate your way to hardware drivers via System> Administration > Hardware drivers, and install the latest driver available. Usually identified by a (recommended) next to it.

---

### Post by xreaper on 2008-10-30
Sorry, I have to go now, I'm only on this site for one hour (at school now.) Heres is the link to the solved problem that sounds similar to yours:
 
[http://ubuntuforums.org/showthread.php?t=963288](http://ubuntuforums.org/showthread.php?t=963288)
 
Hope this helps. Good luck.

---

### Post by paulvandenberg on 2008-10-30
This is very frustrating! Both the Beta and the Release Candidate seemed to pick up the 'nv' driver. I got the proper resolution. Now with the final release, we are back to 800x600, using the VESA driver! This was fixed and is broken again at the last minute. I know I can use the restricted driver as I have an Nvidia Geforce 6100 integrated chipset, but what if I'd rather use the open source 'nv' driver? We can't configure by using 'dpkg-reconfigure xserver-xorg' or 'displayconfig-gtk' anymore. How are we supposed to change drivers? Also, as I understand, there are no legacy nvidia drivers for this version of xserver. I would be really screwed if I had a legacy chip/card.

---

### Post by Baul on 2008-10-30
I install the RC candidate of Intrepid when it came out - and was abit puzzled as to the lack of;

sudo displayconfig-gtk

and
my old favourite (which got me to use the CLI)

sudo dpkg-reconfigure xserver-xorg

I seemed to get around it with messing with the NVIDIA X Server Settings and the Screen Resolution feature from preference menu. (What works for me is 1024 x 768 - i.e old Samsung SncMaster 750s and MSI  NX6200 video card.

However:

I like to have wobbly windows and compiz enabled - if I leave metacity or default Ubuntu settings when compiz is enabled- they are always bugs with inkscape and open office panels especially the  max,minor close, interaction.

One work around I now use is emerald andit's  buttonless theme - Not perfect but works for me.

Overall I think Ubuntu and all the upgrades (especially the fact they give so much interest and refreshing debate are great!).

Problem shooting aside - to be given such a great tool of an O/S for nothing except some encouragement of feed-back to the real guys and gals who all make all free Open Source (and Ubuntu)so progressive and increasingly candidates for top of the class!


P.S.  paulvandenberg - I felt your frustration and and abit perplexed as to why "sudo displayconfig-gtk" is not included now.  I am a user not a developer but that command did give flexibility - which worked for me in Hardy (especially as it appears hard to edit X-config by the terminal  Perhaps if there was a way to update people who have different hardware troubles in the forum - then this would be appropriate.  

At the end I have tried many distros and respect them all but I've always found with some trouble-shooting Ubuntu just works for me - and I am quite respectful for open source in general.

All the best
B

---

### Post by somersetsimon on 2008-10-31
> **xreaper said:**
> I installed mine on a desktop computer, so this might be a bit different.. but try to navigate your way to hardware drivers via System> Administration > Hardware drivers, and install the latest driver available. Usually identified by a (recommended) next to it.

When I go to Hardware Drivers, I get a message saying 'Searching for drivers' then the the Hardware Drivers window that says 'No proprietary drivers are in use on this system' and there is nothing for me to select.

---

### Post by somersetsimon on 2008-10-31
> **xreaper said:**
> Sorry, I have to go now, I'm only on this site for one hour (at school now.) Heres is the link to the solved problem that sounds similar to yours:
 
[http://ubuntuforums.org/showthread.php?t=963288](http://ubuntuforums.org/showthread.php?t=963288)
 
Hope this helps. Good luck.

Thanks for your help. It looks like editing my xorg.conf file seems the way to go, but it seems odd that the latest version of the software appears to have less control over the graphics card that the previous version!

---

### Post by somersetsimon on 2008-10-31
> **somersetsimon said:**
> Thanks for your help. It looks like editing my xorg.conf file seems the way to go, but it seems odd that the latest version of the software appears to have less control over the graphics card that the previous version!

Thanks again for everyone's help. It seems like editing my xorg.conf was the solution. I still think it would be more helpful to have some utility to help you do this

---

### Post by bscbrit on 2008-10-31
Same problem here!

The removal of displayconfig-gtk without having a suitable replacement is a retrograde step.  The alternate installation on my laptop has failed to recognise the LCD (1024x720) or the Trident Blade.  It is stuck in 800x600 and there is no obvious way for me to change it.  Surely we haven't gone back a full decade to editing xorg.conf by hand to get bog-standard displays working again, have we?

I would be grateful if anyone has any bright ideas, please....

---

### Post by L8erG8er on 2008-10-31
I'm having the same problem.  Only thing is, that without any drivers showing up in the Hardware config, it doesn't do any good to try to edit the xorg.conf file.

Anyone have an answer to this?

---

### Post by kabloink on 2008-10-31
I ran into the same problems as others, being stuck at 800x600. I was able to run the displayconfig on another linux box to get the needed settings for my monitor on the 8.10 box. This was done after searching online trying to find the needed settings to no avail. Without the other box, I most likely would have downgraded this one to 8.04. 

You can do the same if you still have a 8.04 livecd. Just run the displayconfig(sudo displayconfig-gtk) after booting the livecd and either copy to a usb flash drive or mail the file(/ect/X11/xorg.conf) to an email account in order to get the needed xorg.conf settings for 8.10.

I know we can file bug reports to get the monitors added, but that doesn't solve the immediate problem for those unable to find the correct settings for their xorg.conf. This is a potential show stopper for many people.

---

### Post by L8erG8er on 2008-10-31
> **kabloink said:**
> I ran into the same problems as others, being stuck at 800x600. I was able to run the displayconfig on another linux box to get the needed settings for my monitor on the 8.10 box. This was done after searching online trying to find the needed settings to no avail. Without the other box, I most likely would have downgraded this one to 8.04. 

You can do the same if you still have a 8.04 livecd. Just run the displayconfig(sudo displayconfig-gtk) after booting the livecd and either copy to a usb flash drive or mail the file(/ect/X11/xorg.conf) to an email account in order to get the needed xorg.conf settings for 8.10.

I know we can file bug reports to get the monitors added, but that doesn't solve the immediate problem for those unable to find the correct settings for their xorg.conf. This is a potential show stopper for many people.

Yep, I tried editing my xorg.conf with info from Hardy.  Here's the problem:  I have an older Nvidia TNT graphics card (in the release notes, by the way, I just thought they'd give me some way to cheat it) so without a driver, edits to the xorg.conf are absolutely meaningless.

Oh well, back to Hardy.

---

### Post by L8erG8er on 2008-10-31
Kabloink, that is what I was thinking exactly.

This will absolutely affect many new potential Linux users, and they will not get past it.  Our Linux evangelism is shot to hell.

---

### Post by bscbrit on 2008-10-31
I reported earlier that I was having problems with the screen resolution being stuck at 800x600.  I went back to 8.04, copied xorg.conf, and reinstalled 8.10.  For me, it was worth the hassle.  I now have a working screen on my laptop and I can begin to explore Intrepid - perhaps I will have no further problems but we shall see.  At least my machine is usable.

This does not, of course, help those who are having problems with lack of drivers.  It might be worth moving the necessary drivers from 8.04 - you will not be any the worse off than you are at present.  To take away the configuration tools is a stupid move.

I'll also add my support to those who are saying that this will not help Ubuntu appear as a slick and user-friendly distro for anyone who has not got the most recent hardware.  My laptop is only 4 years old.  To me, that is not something that should be resigned to the scrap heap.

---

### Post by bscbrit on 2008-11-02
[http://ubuntuforums.org/showpost.php?p=6085570&postcount=5](http://ubuntuforums.org/showpost.php?p=6085570&postcount=5)

This has worked for me but USE AT YOUR OWN RISK.

---

