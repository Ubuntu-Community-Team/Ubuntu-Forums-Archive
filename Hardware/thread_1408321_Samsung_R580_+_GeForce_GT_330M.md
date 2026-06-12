---
title: "Samsung R580 + GeForce GT 330M"
date: 2010-02-16
forum: Hardware
---

### Post by scathlock on 2010-02-16
Hello, 
recently I've bought Samsung R580 with GeForce 330. Latest Nvidia drivers don't support this gpu but I've installed them. Everything is moreless ok but sometimes occurs artifacts and I can't change screen brightness. Can I do anything with at least brigthness? It is set to maximum and my eyes can't stand it.

edit:
I really need to solve this somehow. Any ideas?

---

### Post by pleymob on 2010-03-01
Hi scathlock

I own the same laptop and had the same issue wich is not fully resolved yet.
What I've done so far :

Upgrade to the lastest nvidia ( **[COLOR=Red][COLOR=Black]195.36.08[/COLOR] [/COLOR]***)* drivers using the information on :
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

then use the nvidia X server settings (in System/Preferences) -> X screen 0 -> x server color correction -> brightness slider to adjust the brightness.

Don't forget to click the "XX seconds to confirm" button ;)

For now, it seems that you have to launch Nvidia X server settings each time you start ubuntu to apply your settings !
I'll keep looking for a better way to save my eyes ! :shock:

By the way, the new driver gives you also a true hardware acceleration according to XBMC :D
And an artefact free resume on suspend !

Good luck and sorry for my english !

---

### Post by scathlock on 2010-03-06
[http://www.nvnews.net/vbulletin/announcement.php?a=39](http://www.nvnews.net/vbulletin/announcement.php?a=39)

So, we will wait...

---

### Post by pleymob on 2010-03-08
I've seen that.
But still, my laptop doesn't seem affected.

I guess I'm not too demanding since I dont' play nor watch hi def movies since I can't output sound via HDMI on my TV screen !

Now, I'm waiting after Nvidia AND Alsa :-k

---

### Post by scathlock on 2010-03-09
In order to adjust brightness you should add following line in xorg.conf in device section:

Option  "RegistryDwords" "EnableBrightnessControl=1"

Function keys (fn+up&down) doesn't work yet but gnome brightness applet works.

---

### Post by jsdp on 2010-03-09
Hey guys !
I've bought this laptop too and ubuntu does not see my wireless card. What can i do ?

---

### Post by pleymob on 2010-03-11
Thx scathlock, I'll give it a try !

jsdp : I've followed this post to setup my wifi connection : [http://ubuntuforums.org/showthread.php?t=1239342&highlight=r580](http://ubuntuforums.org/showthread.php?t=1239342&highlight=r580) (post #10)
The linux driver wasn't working for me.

Good luck !;)

---

### Post by michae1 on 2010-03-11
Hi guys,
 
I to am looking at buying this model of laptop (it's red so it must go faster.....right?)
 
Anyway I have been using Ubuntu for a couple of years now and am wondering how you like it on the Samsung, (other than the issuses raised in this thread of course).
 
cheers,
michae1

---

### Post by pleymob on 2010-03-12
Hi michae1
Yeah, much faster :D

Besides the nvidia driver issues, ubuntu is great on this laptop.
But I guess it 's up to your needs.

I use it for web surfing, coding and, when a proper driver is released, watching movies with xbmc on my TV screen through HDMI.

I'm sure the R580 will be almost perfect for me in the near future.
A higher screen resolution and USB3 support would have been nice though...

---

### Post by michae1 on 2010-03-13
> **pleymob said:**
> Hi michae1
Yeah, much faster :D

Besides the nvidia driver issues, ubuntu is great on this laptop.
But I guess it 's up to your needs.

I use it for web surfing, coding and, when a proper driver is released, watching movies with xbmc on my TV screen through HDMI.

I'm sure the R580 will be almost perfect for me in the near future.
A higher screen resolution and USB3 support would have been nice though...

I found the U community to be pretty quick with fixing issues so.......it's a done deal, I have decided to fork out and buy the R580.

USB3 would be good for an external hd. Maybe in the future ;). I can live with the resolution but agree that a higher one would give me more real estate.....however i'm getting older every day and itty bitty fonts etc are getting harder to see, lol

thanks for tghe reply.

---

### Post by pleymob on 2010-03-16
Hi guys.

Nvidia has released an updated driver that should fix the fan problems :
[http://www.nvnews.net/vbulletin/showthread.php?p=2209577](http://www.nvnews.net/vbulletin/showthread.php?p=2209577)

Cheers !

---

### Post by felace on 2010-04-12
Hi, 

Is there a way to actually turn down the backlight ? Nvidia panel does that as if you change color balance of a picture, it won't turn the lights down.

---

### Post by mcguire on 2010-04-16
> **felace said:**
> Hi, 

Is there a way to actually turn down the backlight ? Nvidia panel does that as if you change color balance of a picture, it won't turn the lights down.

Using scathlock tips :

> **scathlock said:**
> In order to adjust brightness you should add  following line in xorg.conf in device section:

Option  "RegistryDwords" "EnableBrightnessControl=1"

Function keys (fn+up&down) doesn't work yet but gnome brightness  applet works.

you can then adjust backlight using Gnome brightness applet, KDE power settings or directly in the /proc filesystem with the file /proc/acpi/video/NVID/LCD/brightness

@Scathlock :
where did you find this option ? I've searched in Nvidia documentation and RegistryDwords isn't mentioned.

---

### Post by n-ice on 2010-04-30
Reporting that adding option for backlight doesn't work for me on lucid x86

---

### Post by scathlock on 2010-05-08
> **mcguire said:**
> 
where did you find this option ? I've searched in Nvidia documentation and RegistryDwords isn't mentioned.

I've contacted with nvidia support and some man helped me giving this option.

---

### Post by n-ice on 2010-05-08
It seems brightness working, but brightness gnome indicator goes crazy, but it responds to mouse wheel.

---

### Post by jatinps on 2010-05-10
does anyone know how to get sound output from hdmi? I can't do it on base ubuntu lucid system or xbmc.

---

### Post by Stampede on 2010-05-10
Hello! I have another laptop (satellite a500-1ek) but I have the same nvidia card (gt330m) and the same problem about sound output from hdmi... Installed nvidia driver 195.36.24. Any idea? Thx!

---

### Post by jatinps on 2010-05-15
I have the r580 with the 310m and I somehow managed to get 2.0 pcm audio out of hdmi only after playing around a lot with asound.conf and hda-intel.conf files.
Also for mplayer I need to use the -ao option to point to the card as well as -ac hwac3 (or -ac hwdts) for multi-channel audio.

Hope there will be some update on the nvidia drivers which will allow out of the box multi-channel audio support for nvidia 300m series.

---

### Post by felace on 2010-06-05
> **mcguire said:**
> Using scathlock tips :

you can then adjust backlight using Gnome brightness applet, KDE power settings or directly in the /proc filesystem with the file /proc/acpi/video/NVID/LCD/brightness


It's not working for me, saying <not supported>

Could you post your Xorg.0.log ? It seems mine can't use acpi stuff so I wonder if that's the reason.

---

### Post by maz00 on 2010-06-07
Hi guys, 

Sorry for posting this message here but I can't find another forum with people owning Samsung R580. I just bought mine 3 days ago except I can't create recovery disk (no option besides copy all the harddisk). I talked to Samsung and they said a Recovery CD should've been in the box. Did any of yours come with a recovery cd? any way to create it? Mine didn't come with a recovery CD. 

Thanks
Maz

---

### Post by dugh on 2010-06-12
I'm also interested in getting this laptop, but not if it doesn't work well in Ubuntu.

Another one at best buy is the asus g60JX - and it appears everything works fine in it, or else there are fixes/workarounds already posted.  But it's $70 more and no bluray (I can live w/out bluray though).

---

### Post by n-ice on 2010-06-13
> **dugh said:**
> I'm also interested in getting this laptop, but not if it doesn't work well in Ubuntu.

Another one at best buy is the asus g60JX - and it appears everything works fine in it, or else there are fixes/workarounds already posted.  But it's $70 more and no bluray (I can live w/out bluray though).

Hi dugh,  I have r580 and lucid working pretty well on it. I have x86 (32bit) version of ubuntu with PAE kernel and have 4gb memory available.

---

### Post by prezeus on 2010-06-26
> **pleymob said:**
> Hi scathlock

I own the same laptop and had the same issue wich is not fully resolved yet.
What I've done so far :

Upgrade to the lastest nvidia ( **[COLOR=Red][COLOR=Black]195.36.08[/COLOR] [/COLOR]***)* drivers using the information on :
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

then use the nvidia X server settings (in System/Preferences) -> X screen 0 -> x server color correction -> brightness slider to adjust the brightness.

Don't forget to click the "XX seconds to confirm" button ;)

For now, it seems that you have to launch Nvidia X server settings each time you start ubuntu to apply your settings !
I'll keep looking for a better way to save my eyes ! :shock:

By the way, the new driver gives you also a true hardware acceleration according to XBMC :D
And an artefact free resume on suspend !

Good luck and sorry for my english !


My eyes thanks you, i'm still tryng to find a real solution for change the brightness, in my case xbacklight (a little terminal program) doesn't work but maybe in your case...

In the case that xbacklight work for you, you can add a xbacklight command in the ubuntu shortcut tool...

Thank you again, by the way, how can i know the driver version of my nvidia card?

---

### Post by prezeus on 2010-06-26
> **scathlock said:**
> In order to adjust brightness you should add following line in xorg.conf in device section:

Option  "RegistryDwords" "EnableBrightnessControl=1"

Function keys (fn+up&down) doesn't work yet but gnome brightness applet works.

Works for me, gnome applet works with the mouse wheel, so, is a start... for the ubuntu noobs i can say the file "xorg.conf" is in /etc/X11/xorg.conf. So, for editing this file you can enter in the terminal: 

      sudo gedit /etc/X11/xorg.conf

I have problems with skype, my webcam works in other applications, but in skype, i can't see my friends webcams mine neither but my friends receive my webcam...

So, the webcam works, but my skype call windows doesnt show it...

Sorry for my english...

---

### Post by dsmex on 2010-07-19
Just a quick summary of what I did to setup my Samsung R580. Hopefully somebody will find it useful.

Specs are core i5 and GeForce GT 330M.

I installed Kubuntu 10.04. Almost everything worked out of the box. Wireless, bluetooth and sound worked right away. Had to toggle some settings in Kmix to get microphone working for skype.

The screen brightness was not working initally. Changing "screen brightness" in the power managment made the brightness jump irradically.

Installed latest driver from [www.nvidia.com](www.nvidia.com)

After downloading the driver, I booted into shell using the recovery boot option and ran the install script.

After installing the nvidia driver I could not change the screen brightness at all. Adding:
"RegistryDwords" "EnableBrightnessControl=1"
... as mentioned before in this thread fixed it.

Everything seem to be working perfectly now.

---

### Post by felace on 2010-07-27
I can also confirm this.

If you had modified your menu.lst so you'd boot with acpi_backlight=vendor, revert it, download the latest nvidia driver and you're done.

---

### Post by pd12 on 2010-08-26
> **felace said:**
> I can also confirm this.

If you had modified your menu.lst so you'd boot with acpi_backlight=vendor, revert it, download the latest nvidia driver and you're done.
This sound about right. 

You can check out [http://www.voria.org/forum/index.php](http://www.voria.org/forum/index.php) 
for samsung-tools. 

A very useful step-by-step (great for noobs like me)  walkthrough to enabling most of the features (worked on my r580) is here: [http://what-ho.posterous.com/linux-hotkey-support-on-samsung-laptops](http://what-ho.posterous.com/linux-hotkey-support-on-samsung-laptops)


> I installed Kubuntu 10.04. Almost everything worked out of the box.  Wireless, bluetooth and sound worked right away. Had to toggle some  settings in Kmix to get microphone working for skype.

I was going to ask how to do it in GNOME but I figured out my microphone was just muted. ;) (System->Preferences->Sound) It's very soft though.

---

### Post by jmols on 2011-03-06
I'm using a samsung R590 laptop (wich is quite similar to the R580) and I got my brightness controls to work on ubuntu 10.10 like this:

**Prologue: **
I first installed the samsung-tools these fixed all of my other fn buttons. This is just a tip and not necessary (i think) for the funcionality of the brightness buttons. [HTML]http://ubuntu-tweak.com/app/samsung-tools/[/HTML]

**Part 1: install drivers**
1. Disable previous drivers (System/Additional drivers)
2. Download drivers from [www.nvidia.com](www.nvidia.com) (use save as)
3. Reboot in a recovery shell
4. ```
sudo sh ./<downloaded file>
```
5. Follow install instructions. (If previously installed the standard nvidia drivers, you should let the setup create a textfile wich will disable the previous drivers. After that, you should reboot and try again form step 3.)

**Part 2: adjust grub**
1. ```
sudo gedit /etc/default/grub
```
2. Add acpi_backlight=vendor to the default command line, the line should then look like this: [HTML]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"[/HTML]
3. ```
sudo update-grub
```

**Part 3: enable screen adjustments**
1. ```
sudo gedit /etc/X11/xorg.conf
```
2. Add the following line in the device section: Option "RegistryDwords" "EnableBrightnessControl=1"
My own section looked like this:
[HTML]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection[/HTML]

**Part 4: reboot and everything should work**

Have fun!

---

### Post by robertor on 2011-08-01
> **scathlock said:**
> In order to adjust brightness you should add following line in xorg.conf in device section:

Option  "RegistryDwords" "EnableBrightnessControl=1"

Function keys (fn+up&down) doesn't work yet but gnome brightness applet works.


Thanks a lot. It works perfectly in Samsung RF410 too.
Roberto

---

### Post by Mich3lin on 2012-08-29
> **jmols said:**
> I'm using a samsung R590 laptop (wich is quite similar to the R580) and I got my brightness controls to work on ubuntu 10.10 like this:

**Prologue: **
I first installed the samsung-tools these fixed all of my other fn buttons. This is just a tip and not necessary (i think) for the funcionality of the brightness buttons. [HTML]http://ubuntu-tweak.com/app/samsung-tools/[/HTML]

**Part 1: install drivers**
1. Disable previous drivers (System/Additional drivers)
2. Download drivers from [www.nvidia.com](www.nvidia.com) (use save as)
3. Reboot in a recovery shell
4. ```
sudo sh ./<downloaded file>
```
5. Follow install instructions. (If previously installed the standard nvidia drivers, you should let the setup create a textfile wich will disable the previous drivers. After that, you should reboot and try again form step 3.)

**Part 2: adjust grub**
1. ```
sudo gedit /etc/default/grub
```
2. Add acpi_backlight=vendor to the default command line, the line should then look like this: [HTML]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"[/HTML]
3. ```
sudo update-grub
```

**Part 3: enable screen adjustments**
1. ```
sudo gedit /etc/X11/xorg.conf
```
2. Add the following line in the device section: Option "RegistryDwords" "EnableBrightnessControl=1"
My own section looked like this:
[HTML]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection[/HTML]

**Part 4: reboot and everything should work**

Have fun!

Thank you sooooooo much! Works for me!

My sys info:
NVIDIA 304.43 (Old 276* (*I'm not sure about version) didn't worked, so I made update and its working)
Samsung R780
Ubuntu 12.04

---

