---
title: "Trouble with maximum screen resolution"
date: 2010-04-06
forum: Hardware
---

### Post by Karandr on 2010-04-06
Hi,
just installed Ubuntu on a desktop today and most everything is going alright. We've applied all the updates and are just tweaking it to our needs. The only issue we're having is setting the screen resolution. On a previous installation of Windows XP, the maximum resolution was 1024 x 768. However, in the Display settings dialog in Ubuntu, the maximum screen resolution is 800 x 600.

Dell was no help in regards to drivers or support for Ubuntu, so we're hoping someone else has used the same monitor/knows what to do.

We've tried a few guides and resources found through Google, but none of them have really helped us. This is our first time using Ubuntu, let alone configuring a monitor. If anyone could help us set the monitor up to the correct resolution, it'd be greatly appreciated.

The monitor in question is a Dell E193FP.

Thanks.

EDIT:
Updated to 10.04 Lucid Lynx today and all is working fine. Looks like the problem has been solved in the latest release.

---

### Post by jordansands89 on 2010-04-06
I had the same problem with my Dell computer. I haven't figured anything out.


…..

[scheduling software](http://employeeschedulingsoftware.blogsavy.com/)

---

### Post by CLEARviewF on 2010-04-06
That always happen with some CRT old monitors. I had one of them and never could set it ok with Ubuntu. Mandriva, openSUSE works fine with old hardware, maybe you want to try them. If not, just have to look hard for hours on the web and try anything to see if you could fix that :D

regards!

Note: Now I only have LCD monitors :D and no problems at all.

---

### Post by cascade9 on 2010-04-06
The Dell E193FP should do up 1280x1024@60Hz  (prefered resolution) or 1280x1024 @75Hz (suprising that it didnt do that with windows) 

[http://support.dell.com/support/edocs/monitors/E193FP/En/specs.htm](http://support.dell.com/support/edocs/monitors/E193FP/En/specs.htm)

Being limited to 800x600 sounds like a video driver problem. What video card are you using?

---

### Post by Karandr on 2010-04-06
> **cascade9 said:**
> The Dell E193FP should do up 1280x1024@60Hz  (prefered resolution) or 1280x1024 @75Hz (suprising that it didnt do that with windows) 

[http://support.dell.com/support/edocs/monitors/E193FP/En/specs.htm](http://support.dell.com/support/edocs/monitors/E193FP/En/specs.htm)

Being limited to 800x600 sounds like a video driver problem. What video card are you using?
The video card is an nVidia    	 	 	 	 	NV15GL [Quadro2 Pro].

---

### Post by cascade9 on 2010-04-06
You have installed the drivers for it?

With unbuntu, system->administration->hardware drivers

---

### Post by Karandr on 2010-04-06
"No proprietry drivers are in use on this system."
We have the driver downloaded as a .run file, but we're having some trouble running it as root.

---

### Post by cascade9 on 2010-04-07
You should be able to install it from system->administration->hardware drivers

see here- 

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Karandr on 2010-04-07
System>Administration>Hardware Drivers:
[[IMG]http://i633.photobucket.com/albums/uu51/kar0010/th_Screenshot.png[/IMG]](http://s633.photobucket.com/albums/uu51/kar0010/?action=view&current=Screenshot.png)

---

### Post by cascade9 on 2010-04-07
Hmm.... AFAIK that should work. Well, heres somethign else to try- 

[http://technologycrowd.com/2009/11/10/add-nvidia-driver-190-42-to-64-bit-ubuntu-karmic/](http://technologycrowd.com/2009/11/10/add-nvidia-driver-190-42-to-64-bit-ubuntu-karmic/)

Yeah, I know, it says '64bit' but it should work for 32bit as well.

---

### Post by Karandr on 2010-04-07
Thanks for the link. Managed to install the drivers fine, but upon restarting, we got this upon going to System>Preferences>Display.
[[IMG]http://i633.photobucket.com/albums/uu51/kar0010/th_Screenshot-1.png[/IMG]](http://s633.photobucket.com/albums/uu51/kar0010/?action=view&current=Screenshot-1.png)
(note: before this, we were asked if we wanted to use the built-in display config tool or the driver manufacturers.)

We also tried the built in Display dialog, but the maximum resolution was still 800 x 600.

Running nvidia-xcofig gave us this result:
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

---

### Post by cascade9 on 2010-04-07
Heh, almost done! 

go to terminal, and -

gksudo nvidia-xconfig 

I think you can do it with gksudo (graphical sudo), its better if you can... if not then just use sudo. ;)

---

### Post by Karandr on 2010-04-07
Got:
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```
Is that right?

---

### Post by cascade9 on 2010-04-07
Should be right....if you still arent getting 1024x768 or 1280x1024 as avaible resolutions, then I'd restart x. Either by restarting the computer, or from command line- 

/etc/init.d/gdm stop
 
then once x stoops and you get booted back into comand line, relog in and to restart x-

/etc/init.d/gdm start 

startx might work as well..been a awhile since I've done this.

---

### Post by Karandr on 2010-04-07
Thing have taken a turn for the interesting. Restarted as you suggested only to be met with an error message telling us that there were no usable drivers available. It then gave us a list of options, none of which worked aside from "Run Ubuntu in low graphics mode for just one session"

Upon getting to the desktop, we now have even less resolution options - 600 x 800 and 640 x 480.

---

### Post by cascade9 on 2010-04-07
*slaps forhead* :| 

OK...should have checked something before I told you to follow a link :( 
 
That card wont work with the 190.xx drivers. It needs much older drivers. Remove the 190.xx drivers, and install the 71.xx drivers. 

Sorry about that.

---

### Post by Karandr on 2010-04-07
It's fine, we're just glad to get some help.
So, complete newbies here (24 hours into Ubuntu), how do we go about replacing the current drivers with the appropriate ones?

---

### Post by cascade9 on 2010-04-07
24hrs in? Nice. Sorry this has been so hard, nvidia driver installion should be really easy, but sometimes thats the way the cookie crumbles, eh? 

Very similar to the way you got them actually- 

System -> Administration -> Synaptic Package Manager, then search 'nvidia'. Find the 190.xx drivers (will have a green checkbox that means 'installed') and then right click-> mark for complete removal.

Then find the nvidia-glx-legacy-71xx, right click-> mark for installation. Apply.  

BTW, it should also give you these packages- 

nvidia-kernel-2.6-xx
nvidia-kernel-common
nvidia-kernel-source

I'm pretty sure it marks them when you marks any nvidia-glx (they are dependancies for nvidia-glx) but if it doesnt, you will need to mark them as well.

---

### Post by Karandr on 2010-04-07
Thanks :D
Marked the 190 ones for complete removal, but can't find the GLX-Legacy ones. Furthermore, there's nothing with a 7 in front of it.

*Curiouser and curiouser*

---

### Post by realzippy on 2010-04-07
Can you post your /etc/X11/xorg.conf file made by nvidia-xconfig?

```
gedit /etc/X11/xorg.conf
```

---

### Post by Karandr on 2010-04-07
Sure thing.
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Tue Dec  8 21:04:28 PST 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by cascade9 on 2010-04-07
$&$^*^&*(%##

After pokin around the foums, it appears that the 'old nvidia chipsets are not suppotred on the current ubuntu'. 

I never knew that, but it explains why you cant find them...and why the easy way didnt work :|  Also, it appears to be unworkable from what I can see. OK, unimpressed. But these things happen. 

All I can suggest is trying this from command line- 

sudo apt-get install xserver-xorg-video-nouveau

You will have to manualy edit xorg.conf and replace 'nv' with 'noveau' - 

sudo nano /etc/X11/xorg.conf

Replace 

Driver         "nv"

with 

Driver         "noveau"

(just change that line, yuo can navigate down to where is says '"nv" with the keyboard, then delete the nv" part (easiest to just leave the initial ") and put in noveau". Control-x to save the file.)

*edit- delete out  VendorName     "NVIDIA Corporation", and where I initially said "nv" make that "nvidia" 

Reference thread for in case anybody else is watching this-

[http://ubuntuforums.org/showthread.php?t=1338124](http://ubuntuforums.org/showthread.php?t=1338124)
[FONT=monospace]

[/FONT]

---

### Post by realzippy on 2010-04-07
Yep,Cascade9 is right.
Your graphics card has a NV15GL chipset,same as geforce2 cards.
Pretty old... no way.The free nouveau driver is your choice...

---

### Post by Karandr on 2010-04-07
I can't find a field that says Driver "nv".
Do I just change VendorName to "nvidia"?

---

### Post by cascade9 on 2010-04-07
@realzippy- I'm glad its not just me. I'm unimpressed that the old cards dont get the support anymore, but not much I can do about it. 

@Karandr- Once you have done this- 

sudo apt-get install xserver-xorg-video-nouveau

Edit xorg.conf and this is what your xorg.conf should look like- 

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Tue Dec  8 21:04:28 PST 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "noveau"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```BTW, it should be possible to put in Dell E193FP at some point, but its better to not even try that now IMO. You shouldnt have to anyway, depeding on how the noveau drivers work, so deal with he drivers 1st. ;)

---

### Post by Karandr on 2010-04-07
I'll restart and let you know how everything went.
Thanks for both of your help :D

---

### Post by realzippy on 2010-04-07
...small typo:

Driver         "[COLOR="Red"]noveau[/COLOR]"


should be "nouveau" of course...

---

### Post by Karandr on 2010-04-07
Ah. So that typo would explain 
```
Ubuntu is running in low graphics mode

The following error was encountered. You may need to update your configuration to solve this. 

(EE) Failed to loaf module "noveau" (module does not exist, 0)
(EE) No drivers available.
```
Hi-ho, hi-ho, it's off to the terminal we go.

---

### Post by cascade9 on 2010-04-07
:| 

Thanks for noticing that....stupid dyslexia :|  One reason why I dont use th command line as much as a lot of linux users. ;) 

I think you've got the idea though Karandr, fix up my mistake and hopefully everything works fine. Good luck ;)

---

### Post by realzippy on 2010-04-07
*Hi-ho, hi-ho, it's off to the terminal we go*

..at least you are having fun  ;-)

---

### Post by Karandr on 2010-04-07
Oh, *hello.*
Uhm, saw the motherboard screen, "GRUB LOADING" then the small Ubuntu logo in the middle and now nothing. I'm writing from my brother's laptop.

Isn't this fascinating?

---

### Post by realzippy on 2010-04-07
...o.k.,something is messed up.Boot in recovery mode,drop to root shell and type:

```
rm /etc/X11/xorg.conf
```

and reboot in low graphics mode.
Did you formerly run a nvidia driver installer?(*sudo sh NVIDIAXXXX.run  ??*)

---

### Post by cascade9 on 2010-04-07
> **Karandr said:**
> Isn't this fascinating?

I can think of other words starting with 'F' that I'd be using. 

I'm hopeful your 'arggh!!!' levels dont go up as fast as mine...I would be on the point of reinstalling by now. It should be fixable, thought you might have to use a liveCD to do it, but old windows habits die hard.

I'm just glad I'm on this end of the internets. 

Welcome to the deep end, anyway...if you can deal with this and not get mad, you've got a better temper than me.

---

### Post by Karandr on 2010-04-07
Tried holding down shift during boot to get into the boot menu. Unfortunately, this time the computer didn't even activate the monitor -- the screen stayed dormant. In other news, the computer tower is emitting a slightly concerning hum it wasn't making before.

I manage not to get frustrated for quite a while. This is an entirely new type of computer issue -- I'm used to XP drivers literally disappearing and printers bringing half a gb of bloatware with them. Installing drivers in Ubuntu is just a lot more calm and, dare I say it, enjoyable.

---

### Post by realzippy on 2010-04-07
*the computer tower is emitting a slightly concerning hum it wasn't making before*

Unplug it totally for a few seconds and try again.If it still fails,can you boot from LiveCD?


edit. Can you hit "shift" blindly?

---

### Post by Karandr on 2010-04-07
Hey, now we're cooking with gas.
I have two recover mode options:
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
and
Ubuntu, Linux 2.6.31-14-generic (recovery mode)

Which one?

---

### Post by realzippy on 2010-04-07
First (newest kernel) one...

---

### Post by Karandr on 2010-04-07
Okay. Dropped to root shell promt, typed in "rm /etc/X11/xorg.conf"
Should I have gotten a response, or not?

---

### Post by realzippy on 2010-04-07
No response.Type ```
reboot
```

---

### Post by Karandr on 2010-04-07
Thanks. It's taken me to the boot manager by default. Do I start "Ubuntu, Linux 2.6.31-20-generic"? ie, not the recovery mode one?

---

### Post by realzippy on 2010-04-07
Now it should start without "recovery mode"...hit first one.(Ubuntu, Linux 2.6.31-20-generic)...will be (hopefully)low graphics mode again...

---

### Post by Karandr on 2010-04-07
Cool, I see a desktop. In a (maybe) unrelated note, upon each boot, the displayed image has been about a centimetre too far to either the left or right. I'd rather focus on the resolution, though, hehe.

I'm going to take a quick break, should be back shortly.

---

### Post by realzippy on 2010-04-07
*displayed image has been about a centimetre too far to either the left or right*

...forget about that in the moment.
I have to admit that I do not know if the free nouveau driver supports your ancient graphics card,but we will check out by trial and error.

Conceiving suspicion that your nouveau installation attempt conflicts with the formerly installed (not working) NVIDIA driver,you should ensure to uninstall the NVIDIA driver before installing the nouveau driver.
1.
Open "synaptic" and uninstall everything with "nouveau",then reboot.
2.
Have you (asked before) run something like:

*sudo sh NVIDIAxxxdriver.run*  ??

---

### Post by cascade9 on 2010-04-07
It should support the card-

[http://nouveau.freedesktop.org/wiki/HwIntroduction](http://nouveau.freedesktop.org/wiki/HwIntroduction)

Well, Ok, it doesnt specify the Quadro2 but it supports the same series Geforce cards (same architecture) then it should work. Hopefully.

---

### Post by Karandr on 2010-04-07
I assume that's "Mark for complete removal"?
And we ran something earlier tonight called NVIDIA-Linux-x86-1.0-6111-pkg1.run
That's the only other relevant thing I remember running.

---

### Post by realzippy on 2010-04-07
yes,complete removal.But have a look at the packages that gonna be removed;sometimes synaptic removes important other stuff also.
If this is done,reboot again and run the same command with *--uninstall* at the end,e.g.

**sudo sh NVIDIA-Linux-x86-1.0-6111-pkg1.run --uninstall**

then reboot,then open synaptic and install "nouveau" stuff again;reboot.

---

### Post by Karandr on 2010-04-07
Alright, removed. Once again, thanks for the continued help.

EDIT:
Just ran the uninstall command. 
"There is no NVIDIA driver currently installed"
I guess it never installed?

---

### Post by cascade9 on 2010-04-07
> **Karandr said:**
> I assume that's "Mark for complete removal"?
And we ran something earlier tonight called NVIDIA-Linux-x86-1.0-6111-pkg1.run
That's the only other relevant thing I remember running.

I dont think I told you to do that one, but honestly, I've been awake for about, ohh, 30 hrs now and my brain is just about mush. If I did, I'm really sorry.....that looks like its 6 years old. 

I think I need a coffee or something, I cant go to sleep for a while yet (long story). I'll try to avoid making any more silly posts and typos. :)

---

### Post by Karandr on 2010-04-07
Hur hur, coffee. -snickers-
I'm not sure where I got that file from, but it's no biggie on account of it didn't even install.

---

### Post by realzippy on 2010-04-07
Hm.Strange thing that "nvidia-settings" is installed.
Just to be sure,run:

```
sudo apt-get --purge remove nvidia-glx nvidia-settings linux-restricted-modules-`uname -r` nvidia-kernel-common
```

reboot,then
reinstall the "nouveau" stuff with synaptic,reboot, and see what happens..

---

### Post by realzippy on 2010-04-07
OFFTOPIC:

@cascade9

isn't brisbane the city with the river and the sharks??Go fishing to stay awake...

---

### Post by Karandr on 2010-04-07
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package nvidia-glx is not installed, so not removed
E: Couldn't find package linux-restricted-modules-uname -r
```
I'll just reboot now, then.

---

### Post by cascade9 on 2010-04-07
> **Karandr said:**
> Hur hur, coffee. -snickers-
I'm not sure where I got that file from, but it's no biggie on account of it didn't even install.

At risk of being lynched- I dont normally drink coffee, so when I do its a bit of a rush. should keep me awake for the 4-5 hours I need to stay awake for. 

> **realzippy said:**
> OFFTOPIC:

@cascade9

isn't brisbane the city with the river and the sharks??Go fishing to stay awake...

Sharks in the brisbane river, yep, thats right. Not that many, but I've seen a shark fin myself in there. Never seen one of the mythical crocodiles though. :D

---

### Post by Karandr on 2010-04-07
@cascade9:
I just thought your mention of coffee was funny considering the user ranking system. I'm easily amused, as you may have guessed.

Okay, so I'm in Synaptic. The Nouveau stuff to install is..
libdrm-nouveau1
libdrm-nouveau1-dbg
xserver-xorg-video-nouveau
nouveau-kernel-source
(there's also a French translation of the Debian New Maintainers' Guide, but *something* tells me that's unrelated XD)

---

### Post by realzippy on 2010-04-07
xserver-xorg-video-nouveau

should install it's dependencies itself...

---

### Post by cascade9 on 2010-04-07
Easy amused is a good thing. ;) 

> **realzippy said:**
> Hm.Strange thing that "nvidia-settings" is installed.

That would be from the 190.xx drivers that Karandr installed via synaptic (and removed because I was too stupid to remember to check what version the hardware actually needed before getting Karandr to install them).

---

### Post by Karandr on 2010-04-07
Okay, xserver-xorg-video-nouveau didn't mark "libdrm-nouveau1-dbg", so I'll leave it out.

Installing... Done!
Rebooting... Done!

---

### Post by realzippy on 2010-04-07
libdrm-nouveau1-dbg  is only needed for debugging...

So rebooted...and what happens?

---

### Post by cascade9 on 2010-04-07
Beat me to it realzippy. 

Its working...right? *crosses fingers* 

Still stuck at 800x600?

---

### Post by Karandr on 2010-04-07
Absolutely nothing. I'm staring at a very good-natured desktop right now. Shall I venture into the display settings?

EDIT:
Hey-o, what's all this, then?
System>Preferences>Display
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?"

No>Default display settings dialog
Yes>nVidia display settings. What. The. Hell.

---

### Post by cascade9 on 2010-04-07
Yes, you should :)

*edit- nothing in this case is good. It means there are no issues with the nouveau driver..well, so far anyway, lets see if I can stuff it up again :)

---

### Post by realzippy on 2010-04-07
???

Have you not purged nvidia-settings???!

```
sudo apt-get autoremove nvidia-settings
```

Can you open display settings?Still stuck to 800x600?

---

### Post by Karandr on 2010-04-07
I'm certain I did that a while ago. Let's try again for good measure.
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nvidia-settings
```

I can get into the default display settings, but I'm still stuck at 800 x 600.

---

### Post by realzippy on 2010-04-07
Have to go out for some shopping,will be back in 40 minutes...


Meanwhile,if you have a fast internet,you could download:

Ubuntu Lucid beta (10.04),because nouveau is implemented,and:

Ubuntu 8.04 LTS,because it uses an older Xorg version;there might be a chance that there is an NVIDIA driver in System/Administration/restricted drivers...

While downloading,try to set higher resolution with xrandr.
First run:

```
rm /home/yourusername/.config/monitors.xml
```

replace yourusername with your users name...

```
xrandr
```

post output please

```
cvt 1024 768
```

post output please

---

### Post by cascade9 on 2010-04-07
Try this in terminal-

glxinfo | grep Nouveau

Paste the response back in here

Hmmm.....I wonder, would nouveau use xorg.conf? If it still existed and was being used them I would modify it, but xorg.conf has been removed.

*edit- I'm, pretty sure that 8.04 is the last version of ubuntu to have the 71.xx drivers. That would work. 

Also, do you want 1024x768, or 1280x1024? Personally, I prefer 1280x1024, but I know people who dont.

---

### Post by realzippy on 2010-04-07
*Hmmm.....I wonder, would nouveau use xorg.conf?*

Me too.Maybe you should create a minimal one:

```
gksudo gedit /etc/X11/xorg.conf
```


if file is empty,paste this:

[B]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nouveau"
EndSection[/B]

if it is not empty,replace "nv" with "nouveau"

---

### Post by Karandr on 2010-04-07
**@realzippy:**
Might go for Lucid. Will consult with my brother on that one.
Running "rm /home/yourusername/.config/monitors.xml"... No response...

Running "xrandr"...
```
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
  800x600     60.0*     56.0
  640x480     60.0       
  400x320     60.0       56.0
  320x240     60.0    

```

Running "cvt 1024 768"...
```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk; 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024  1072  1176  1328  768  771  775  798  -hsync +vsync
```

**@cascade9:**
Running "glxinfo | grep Nouveau"... No response...

---

### Post by Karandr on 2010-04-07
(sorry for double post)
[B]@cascade9:
[/B]In that case, we might go for 8.04. 
As for resolution, either is fine. It's just that at 800 x 600, the bottoms of a lot of windows are cut off, and it's hard to use in general.

**@realzippy:**
Running "gksudo gedit /etc/X11/xorg.conf"
File empty. Pasting to file... Done!
And save, yes?

---

### Post by realzippy on 2010-04-07
*And save, yes?*

Yes,save and reboot.Maybe you cannot boot then,in this case:

recovery mode,and again:

```
rm /etc/X11/xorg.conf
```

---

### Post by cascade9 on 2010-04-07
glxinfo | grep Nouveau-  no response? Then I dont think the driver is being used. 

I would try to save the xorg.conf file, cant hurt, and it might be what you need to make the nouveau drivers work. 

You'll need to restart x afterward. 

I'm not 100% sure that 8.04 is the last to have have the 71.xx drvers, but its probably not that bad a choice. 10.04 would be where I would go though.

---

### Post by Karandr on 2010-04-07
It's working! 1024 x 768!
[IMG]http://jamesbnyc.files.wordpress.com/2010/01/yes-this-pleases-gaga.jpg[/IMG]
Thank you both so, so much.

EDIT:
I lie. It's actually 1152 x 864. Never heard of that one before. 
And woah, it goes up to 1360 x 768.
On account of one of the users of this computer doesn't have great vision, let's see how 1024 x 768 does look.

---

### Post by realzippy on 2010-04-07
@Karandr

Working?Why?  ;-)

Did you use the suggested minimal xorg.conf?
If so,please mark thread as solved (Threadtools) and have fun ....


@cascade9


Have fun &
go to bed...

---

### Post by realzippy on 2010-04-07
*On account of one of the users of this computer doesn't have great vision*


The file *monitors.xml* is created when using display settings..
Every user has its own in /home/username/.config/
Deleting this file sometimes helps;it sometimes limits the available resolutions..

---

### Post by Karandr on 2010-04-07
I think I spoke too soon.
So, changing to 1024 x 768 took me to a command line. I rebooted and got the same blank screen I described earlier. After waiting a bit, I rebooted *again* and got the boot commander thing, you know, recovery mode or non-recovery mode.

---

### Post by realzippy on 2010-04-07
So the edited xorg.conf does not work.
Recovery mode,then delete it,

```
rm /etc/X11/xorg.conf
```

---

### Post by cascade9 on 2010-04-07
Hooray! Cookies all round! \\:D/

Glad to have helped....and thanks to realzippy, I leant a new command or 2. 

1152 x 864 has been around for a long time, its just pretty rare to see it used. 1360 x 768? Now, that is interesting, thats wider than the manufacturers specifications. Probably look pretty awful. 

BTW, heres a trick you might not know- with firefix you can hint 'control' and '+' and it will zoom in, and 'control' and '-' will zoom out. Handy, especially if you have slightly dodgy eyes. ;)

Edit- doh, spoke too soon..... :| Ohh well, its getting there, slowly ;)

---

### Post by Karandr on 2010-04-07
I mean, I wasn't stuck at 800 x 600 a few minutes ago (see Gaga post), but it sort of flopped sideways when I tried to change it to 1024 x 768.

Alright. I'm in recovery mode.
Dropping to root shell prompt.
rm /etc/X11/xorg.conf
Done!
Rebooting.
EDIT:
And back to 800 x 600. Hello, old friend.

---

### Post by realzippy on 2010-04-07
Try:

```
xrandr --newmode "1024x768_60.00"   63.50  1024  1072  1176  1328  768  771  775  798  -hsync +vsync  
```

then

```
xrandr --addmode default 1024x768
```

```
xrandr --output default --mode 1024x768
```

---

### Post by Karandr on 2010-04-07
First command worked without incident, second one...
```
xrandr: cannot find mode "1024x768"
```

---

### Post by realzippy on 2010-04-07
try

```
xrandr --addmode default 1024x768_60
```


or

```
xrandr -s 1024x768
```

---

### Post by realzippy on 2010-04-07
Or,again without _60 :

```
xrandr --newmode "1024x768" 63.50  1024  1072  1176  1328  768  771  775  798  -hsync +vsync
```

```
xrandr --addmode default 1024x768
```

```
xrandr -s 1024x768
```

---

### Post by Karandr on 2010-04-07
Neither work.
The first..
```
xrandr: cannot find mode "1024x768_60"
```
The second..
```
Size 1024x768 not found in available modes

```

---

### Post by realzippy on 2010-04-07
[http://ubuntuforums.org/showpost.php?p=9087692&postcount=82](http://ubuntuforums.org/showpost.php?p=9087692&postcount=82)

---

### Post by Karandr on 2010-04-07
Mkay. 
*xrandr --newmode "1024x768"   63.50  1024  1072  1176  1328  768  771  775  798  -hsync +vsync*
worked, as did 
* xrandr --addmode default 1024x768*

No response, though. Is that expected?

---

### Post by realzippy on 2010-04-07
Yes,no response.If you now type

```
xrandr
```

there (hopefully) should be 1024x768 listed....is it?
Try setting it if exists:

```
xrandr -s 1024x768
```

---

### Post by Karandr on 2010-04-07
Yes, it's listed.
Let's try setting it...
```
Failed to change the screen configuration!
```
Oh.

EDIT:
And trying to change it from System > Pref > Display gives this:
[[IMG]http://i633.photobucket.com/albums/uu51/kar0010/th_Screenshot-2.png[/IMG]](http://s633.photobucket.com/albums/uu51/kar0010/?action=view&current=Screenshot-2.png)

---

### Post by realzippy on 2010-04-07
arrgh.
Restart Xserver or reboot,and try again please...

---

### Post by Karandr on 2010-04-07
```
Size 1024x768 not found in available modes
```
xrandr says it's not listed, so I'll add it again.
Added. xrandr read-out says
```

   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1024x768       59.9  

```

So, let's try and select it...
```
Failed to change the screen configuration!
```

Urp.

---

### Post by realzippy on 2010-04-07
Sorry,I have no idea why mode cannot be set.
As mentioned earlier I also do not know if the nouveau driver needs
an xorg.conf nor if its working on your system.
May I ask why you want to make this ancient graphic card work?
Is it "sport" or can't you afford some newer stuff?
(Do not get me wrong please)  ;-)

---

### Post by Karandr on 2010-04-07
Hehe. I honestly have no idea. I suppose we could get a newer one, but we had no idea how old this one is. My brother is the one who usually does the computer fixing, but he's been out today. We're actually setting this up for our parents -- it's a huge improvement from XP. If we can't find a solution, I guess we'll either give Lucid a try or get a newer graphics card.

Again, I truly appreciate all the help you've given me. I'll leave the thread as unsolved, but I'm off for tonight.
Thanks again!

---

### Post by realzippy on 2010-04-07
Yes,try Lucid because of the implemented nouveau,and try 8.04 LTS 'cause of old Xorg version.You not need to install them;the resolution or driver installation could be done in LiveCD mode also.
BTW,
if you had an pci express mainboard,I could send you my GF's old graphics card,for free.Her nephew did not want it *"What?Only 256 Mb video ram?Crap!"*
But the card works great under linux;better someone uses it than wasting in the cellar.

---

### Post by cascade9 on 2010-04-08
OK, now I've slept and my brain is working again ;)

Quadro 2s are circa 2001 cards. Its the same GPU as found in the Geforce2 GTS. It should be an AGP card (I've never seen a PCI quardo 2 pro, but maybe they exist?). Alomst no chance of a motherboard with an AGP slot having a PCIe slot as well, though there are a few...so the nice cheap PCIe cards (and realzippys offer) are out. 

You could get a PCI card, but really, they cost a bit. AGP cards are thin on the ground these days, theer are some around be to be hoenst the majority of them arent that much better than the quadro 2. 

There is the chance that the xorg problem has been fixed, but he ubuntu driver selection process hasnt been updated. You could try the manual way- like really manual. 

Dl the 71.xx drivers from nvidias site, the easiest way to find them is to go 'legacy' then select 'tnt and tnt2'...and yes, they are the rigth drivers for the quadro 2 pro. 
Then go to command line- 

/etc/init.d/gdm stop

to stop x, then navigate to where the drivers are, then run this- 

sh NVIDIA (use the full filename, 'tab' auto completes the name) 

/etc/init.d/gdm start 

to restart x. 

If somethign goes wrong or you want to remove the manually installed nvidia driver for any reason, the command is-

nvidia-installer --uninstall

BTW, from what I know, even running that wont revert all the changes the nvidia installer makes. 

I dont know if it will work, but there is a good chance that it might. 

(no offence at the following) 

I actually find it amusing that it would be easier to get this card, and quite posible a lot of the other older nvidia cards going with debain (which is traditionally 'hard' to install the nvidia drivers on) than it would be with ubutnu. 

Also, yeah, its an old card realzippy. Better than any intergrated intel IMO, and it should be fine for anything except for gaming and heavy video use (like 720p and up, it would eb fine for DVDs, avis, mkvs etc). 

Just a pity that the nouveau setup didnt work right, but thats probably just because its an older version of nouveau in 9.10 than current. I cant be sure of that, I'm always running the nvidia binary, and havign ever tried the nouveau driver with ubuntu, just other distros.

---

### Post by Karandr on 2010-04-08
Hey! So, we updated to Lucid just before in the hopes that the improved nVidia and Nouveau integration would help. It did! The monitor still comes up as unknown, but we're able to display at 1024 x 768. I'll be marking the thread as solved, the problem seems to be fixed in Lucid. Once again, thanks for all your help.

---

### Post by cascade9 on 2010-04-08
Excelent. Sorry it was such a muck around. 

BTW, some monitors have dodgy EDID (Extended display ID) I'm suprised that a dell has this problem (I'm no great fan of dell, but they do make some really nice monitors) but as long as the resolution works, all is good. 

Hopefully your partents enjoy the new setup ;)

---

