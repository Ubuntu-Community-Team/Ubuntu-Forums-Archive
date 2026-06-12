---
title: "X defaulting to xorg.conf.failsafe"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by Winterhart on 2008-02-04
I'm running 7.10 on my Dell Latitude laptop, with the video out through DRI to a 22" widescreen monitor.  From what I can tell (based on the monitor's (also Dell) website, my refresh rates and default resolution are correct.

The problem is that X refuses to stop using xorg.conf.failsafe.  I've gone so far as to copy xorg.conf right over xorg.conf.failsafe, and even that won't stop it.  Both Xorg.0.log and Xorg.0.log.old have the failsafe logs in them; I can't seem to find a way to get the original xorg.conf log to find out what the heck is making it fail.

This looks stunningly like [http://ubuntuforums.org/showthread.php?t=584078](http://ubuntuforums.org/showthread.php?t=584078).

I can force the monitor into 1680x1050 if I start up, log in, change the monitor manually in System Administration -> Screen and Graphics Preferences (it won't stick if I try to change it before I log in, for some reason), and then change my resolution in System Preferences -> Screen Resolutions.  I *know* that it can handle 1680x1050@60 - clearly - so that's not the problem.

Anyone know a way to make it stop defaulting to the failsafe config, so that I can find out what in xorg.conf it doesn't like??

---

### Post by magd1319 on 2008-02-21
Are you by any chance using an nVidia graphics card? I'm having a similar problem; every time I try to use the nvidia driver in my xorg.conf file, it forces the xorg.conf.failsafe to be used instead. 

If i use the nv driver, then it works straight away, but this causes other problems; for example I have weird flashing colours on my second monitor. 

In short, does anyone know how to get the nvidia drivers to work, or what might be preventing them from working? 

I have tried envy, i have tried using the restricted drivers manager, and I have tried installing the packages from synaptic, from the command line, and using the drivers from the nvidia website. Can anyone please help?!?!

Cheers,

D

---

### Post by magd1319 on 2008-02-21
Bump...

---

### Post by PmDematagoda on 2008-02-21
First thing is first, remove the nvidia-glx packages using:-
```
sudo apt-get purge nvidia-glx-new nvidia-glx-legacy nvidia-glx
```

Then open a modules file for editing usng:-
```
gksudo gedit /etc/default/linux-restricted-modules-common
```

and edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"

```
save the file and then reinstall the Nvidia driver using the installer obtained from the Nvidia web site, after that is done reconfigure the X-Server(through the CLI) using:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the choices that match your system and VGA card, also choose the driver as "nvidia". After that is done reboot the system and see if that solves your problem.

---

### Post by magd1319 on 2008-02-21
I'm afraid it doesn't; I get a big cross mouse pointer and told that it can't detect my monitor etc. I then have to boot again in low res mode using xorg.conf.failsafe again. 

For some reason, the nvidia driver doesn't seem to be able to cope. Any ideas?

---

### Post by oldsoundguy on 2008-02-21
I have the same xorg "fail safe" on one monitor.  The only issue I see is that it makes it impossible to edit the basic xorg file without importing it into the failsafe file, but the display works fine.  Should I be concerned with the issue?

---

### Post by magd1319 on 2008-02-21
No; if it ain't broke don't fix it. 

Any more suggestions for how to get the nvidia drivers working???

---

### Post by PmDematagoda on 2008-02-21
> **magd1319 said:**
> I'm afraid it doesn't; I get a big cross mouse pointer and told that it can't detect my monitor etc. I then have to boot again in low res mode using xorg.conf.failsafe again. 

For some reason, the nvidia driver doesn't seem to be able to cope. Any ideas?

What is the VGA card you are using?

Also, did you select the proper resolution and refresh rates for the monitor?

---

### Post by sourabhsharma149 on 2008-02-21
I faced similar problems I tried :

1) nvidia-xconfig --> Nothing Happenet..

2) sudo /etc/init.d/gdm stop2
sudo dpkg-reconfigure -phigh xserver-xorg --followed screen
sudo shutdown -r now --> good graphics resrotered BUT Ubuntu now does NOT use nvidia restricted graphics

3) Installed nvidia-glx-new again good graphics with nvidia glx new installed but in next reboot it stuck at rc.local and poor resolution.....

etc etc...But at last ENVY done the trick....

Now I am running all full fledged features without any problem...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

go for it may help..

---

### Post by magd1319 on 2008-02-21
sourabsharma149: I've already tried ENVY and it doesn't work for me. Cheers for the suggestion though.

PmDematagoda: I am using the nVidia  Geforce 7300Gt video card. I am using the proper refresh rates (55-75) and resolutions for this monitor (1400x1050). 

The main monitor worked fine when I used the nv driver that comes with the 7.10 distro, but I want to make use of both monitors, and for that I need to use the nvidia drivers.

---

### Post by PmDematagoda on 2008-02-21
> **magd1319 said:**
> sourabsharma149: I've already tried ENVY and it doesn't work for me. Cheers for the suggestion though.

PmDematagoda: I am using the nVidia  Geforce 7300Gt video card. I am using the proper refresh rates (55-75) and resolutions for this monitor (1400x1050). 

The main monitor worked fine when I used the nv driver that comes with the 7.10 distro, but I want to make use of both monitors, and for that I need to use the nvidia drivers.

I am afraid I do not know much about setting up dual-screens using the Nvidia driver, sorry.

---

### Post by magd1319 on 2008-02-21
No I'm not worried about that at all (yet)! 

I just want to get the nvidia driver working with one monitor first of all! Any help you can give with that would be much appreciated!

What should my next idea be?

D

---

### Post by sourabhsharma149 on 2008-02-21
I am also having NVIDIA GEforce 7300 GL card...

I faced same issues..the thing ENVY did it removed the NVIDIA*86*169* driver from kernell saying it was corrupted then fetched some 70 MB stuff from net then configured,..

Make sure the nVIDIA driver you are using is good in shape..

---

### Post by meditatingfrog on 2008-04-22
Does anyone know how to look at the Source Code for ENVY?  I think that may be the only way I'm going to figure out how to get my card working.  So far, after reading everything I could get my hands on, my card still won't work with the nvidia driver (as opposed to the nv driver).  Apparently, performance will improve considerably (according to people I spoke with in the #ubuntu chatroom on irc.freenode.net)  So it is something I will continue to pursue...as time permits...

I will probably try ENVY one more time, then work on it more leisurely.

I have a Geforce2 GTS card 32MB. I tried Restricted Drivers.  No luck (though restricted drivers does say it's enabled and "in use".  I tried ENVY.  No luck.   I tried installing the legacy driver downloaded from Nvidia (sudo sh *.run).  No luck. I tried nvidia-xconfig to create a brand new xorg.conf file.  No luck.  I tried editing the xorg.conf file myself.  No luck.  Without someone to tell me how it all is pieced together, I figure I won't be able to get this working...

Things I haven't tried:  

[www.x.org](www.x.org) forum.
spending more time in the irc channel.

EDIT:

Just had a thought.  I'll try manually installing each possible version in ENVY.  Last thing to try, really.  If it's not this, could it possibly be a bug?  Perhaps a conflict with my chipset and the Gutsy Kernel?  From what I understand, the Nvidia Driver gets compiled into the kernel, so that it can be called from the xorg.conf file.  Hmmmmmmm...

---

### Post by mnmleon on 2008-05-22
i have the same problem, did you manage to get it working?

---

### Post by magd1319 on 2008-05-22
Well, a partial solution. I have just upgraded to Hardy Heron, and now i can delete my xorg.conf file, and it just sorts itself out. No compiz-fusion or anything, and no second monitor (this is a  nightmare for me), but at least I can get one monitor going at normal resolution! 


Still can't get the nvidia driver to load whatever i do though. 


D

---

