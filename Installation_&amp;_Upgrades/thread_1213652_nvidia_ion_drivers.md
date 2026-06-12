---
title: "nvidia ion drivers"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by tg1 on 2009-07-15
Hi!

I'm struggling a bit with the drivers for my nvidia ion card. I've bought this: [http://www.aleutia.com/products/ion-htpc](http://www.aleutia.com/products/ion-htpc) ..and plan to use it as a media server with xbmc.

However, I can't seem to get the graphics card installed. I tried installing the drivers from nvidia.com, but X just hangs on startup afterwards. I've now uninstalled it, but strangely, some nvidia-stuff seem to be still there (nvidia-settings for instance).

(I also tried running xbmc afterwards, but it runs extreeemely slowly.)

(In the end, I want to run 1920x1080, but I've set it up with a smaller monitor (1600x1200) for testing, temporarily.)

If anyone could point me in the right direction, it would be greatly appreciatied. :)

---

### Post by tg1 on 2009-07-15
Follow up info:
dmesg outputs "NVRM: API mismatch: the client has the version 185.18.14, but this kernel module has the version 180.44. Please make sure that this kernel module and all NVIDIA driver components have the same version."

---

### Post by 3rdalbum on 2009-07-15
Your Nvidia Ion platform should be supported by the driver supplied in the Hardware Drivers program (System > Administration > Hardware Drivers).

If you are going to install the 185.xx driver from Nvidia.com, you should remove the "nvidia-180" package from Synaptic Package Manager.

1920x1080 resolution is well accomplishable, but, at least in the 180.xx driver, you need to specify it in the xorg.conf file or the setting won't stick. Odd.

---

### Post by truant on 2009-07-15
You have a mismatch between your module (driver) version and your kernel version. This isn't uncommon when using the nvidia binary drivers off nvidia.com

It's a bit hard to solve without knowing a bit more about your system. 

You could try the following:

```
sudo dpkg-reconfigure nvidia-kernel-common
```
```
sudo dpkg-reconfigure linux-restricted-modules-`uname -r`
```

You might also try re-installing the nvidia drivers from their website - that should check versions and will give you an option to recompile the module if required.  You'll need to re-run nvidia-setup (or whatever it's called, can't remember right now) every time you install a new kernel package though.

Question for you - what are you using/going to use to control this machine?  I'm hoping to get my multiply-falling-apart (but still in-warranty) Aleutia machine replaced with an F1 (if they ever answer any of my emails), so it can go in the front room and plug right into the TV.  I don't fancy messing about with a mouse/keyboard setup, so was thinking about maybe using some local laptop(s) and [Synergy2](http://synergy2.sourceforge.net/) (<--clicky).  Or maybe some kind of bluetooth thingy.  Possibly a PS3 or Wii controller.

---

### Post by tg1 on 2009-07-18
Sorry about the delayed reply.

I've now done a clean install of ubuntu, and installed the nvidia apt-packages. The only problem now is that the computer completely freezes within the first couple of minutes after starting X. :o (I don't get the version mismatch message anymore, though.)

I also installed the lasted RC of Win7 (x64), just for fun. Same problem there also. :confused:

Is this most likely a driver issue, hardware issue, or pebcak issue? ;)

truant: i guess a fancy remote control would be nice, but I guess I'll just buy a nice small bluetooth keyboard (w/touchpad), or something. That Synergy thing looks cool, though. :)

---

### Post by zeronothing on 2009-07-18
What I do with my HTPC is do a clean install. Then instead of using the ubuntu repository Nvidia drivers is to download the Nvidia website driver instead. the 185.18.14 drivers is so much better than the one supplied in ubuntu 9.04. just make sure you install build-essentials, and dkms packages before you install the official nvidia drivers. those packages I mentioned above can be installed using synaptic.

by the way I have a nvidia 7950 GT

---

### Post by tg1 on 2009-07-18
Okay, I guess I could try one more clean install and install the 185.18.14 drivers. (For the record: I used 186.18 drivers in win7)

build-essential and dkms packages are all that's needed before installing the drivers, then?

---

### Post by tg1 on 2009-07-18
Ok, I've now done another clean install, updated the system with all updates, installed build-essential and dkms, then installed 185.18.14 nvidia drivers.
...but the system still completely locks up within the first minute. :?

---

### Post by zeronothing on 2009-07-19
When you say your computer locks up, you mean, keystrokes, mouse, nothing works. You cant hit like ctrl + alt+ f2 to drop down to console screen? I'm just trying to figure out if Xserver is just crashing or if the whole system is crashing? Since that is an nvidia Ion system, is it running the intel atom cpu?

---

### Post by tg1 on 2009-07-19
The whole system crashes, nothing works. (Doesn't respond to ctrl-alt-f*, ping, keystrokes, mouse, whatever..)
Yeah, Intel Atom 330 Dual Core 1.6GHz.

Edit: Also tried updating the bios, didn't help.

---

### Post by tg1 on 2009-07-20
Update: I tried removing one of the memory modules, and it seems to work flawlessly then. I've tried both the modules in both slots, and it seems to run just fine.
I'll let memtest86 run a couple of hours now, and see if it reports any errors.

(I've also ordered new ram (2x2gig), just in case.)

---

### Post by zeronothing on 2009-07-20
Its good to hear you finally solved the mystery.

---

### Post by tg1 on 2009-07-20
Hehe, yeah :-)
Anyway, I think I've found the faulty memory module, the computers locks up randomly with one of the modules installed, but not with the other one.

1080p playback in xbmc is not entirely smooth though, but I'm running only 1gig ram now (and 256meg of that 1gig for the gfx adapter).
However, I get 4gig of fresh new ram on wednesday, so I'll wait until then before investigating any more.

---

### Post by scoobscoob on 2009-07-27
I can't wait to hear your report on how usable this platform is!!!
It holds such good promises of a small form factor and low power
drain media system PC.

Would you be willing to run a few HD flash videos + youtube 
and report on the results (once you have more RAM installed).

Here are some good sites for testing:

 [http://www.adobe.com/products/hdvideo/hdgallery/](http://www.adobe.com/products/hdvideo/hdgallery/)
 [http://www.hulu.com](http://www.hulu.com)
 [http://www.youtube.com](http://www.youtube.com)

Thanks in advance for sharing your findings!
PS: Are you running a DIY system or a commercial 330 based box?
Thanks!
-Christian

---

### Post by lemana on 2009-08-27
TG1, I'm very interested in finding out how things are working for you as I am considering buying that model. 

BTW, how is it noise-wise? Quiet enough to be left next to the screen?

---

### Post by tg1 on 2009-08-27
scoobscoop: sorry about the late reply. Flash actually runs quite poorly on my box. I get ~1fps on youtube movies in "hd". Surely that can't be right. :(
No, not diy, this one: [http://www.aleutia.com/products/ion-htpc](http://www.aleutia.com/products/ion-htpc)

lemana: it actually works very well with xbmc. 1080p playback is 99% smooth. 720p playback is perfect, of course. The fan is actually a bit louder than I was expecting. I almost regret not buying the cheaper, fanless model, without bluray drive. The bluray drive isn't useable for wathcing movies in linux anyway. :-?

---

### Post by lemana on 2009-08-27
> I almost regret not buying the cheaper, fanless model, without bluray drive. 

Do you mean the H1? [http://www.aleutia.com/products/h1](http://www.aleutia.com/products/h1)

The fanless version is single core, if you get the deluxe dual core however they add a fan, so back to the same problem... And in addition it only accepts 2.5'' drives.

I know that Tranquil PC's T7 is dual core and fanless however it is not geared towards HTPC. 

Do you know of any dual core Atom D330 + Nvidia Ion HTPC, fanless, with a slot for a 3.5'' DD? I would use this dream machine for HT, as NAS and to run Squeezecenter.

---

### Post by bgiannes on 2009-09-04
i installed the cuda ION driver

on this page "190" beta
[http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html)

[http://www.nvidia.com/object/thankyou.html?url=/compute/cuda/2_3/drivers/cudadriver_2.3_linux_32_190.18.run](http://www.nvidia.com/object/thankyou.html?url=/compute/cuda/2_3/drivers/cudadriver_2.3_linux_32_190.18.run)

works great.

from desktop
alt-ctrl-f1
sudo /etc/init.d/gdm stop
sudo ./cudadriver_2.3_linux_32_190.18.run
sudo reboot

worked for me. as the older version did not

---

### Post by denis6902 on 2009-10-19
Hello,

I got a Zotac Mini Itx N330 ION too and i just cant install nvidia drivers on it. 

I installed a fresh jaunty 32bit 2 times already, and nothing.

After running updates, i go to harware drivers, and doesnt seem that i have a graphic card as i shows nothing in there. 

I tried following the tutorial over XBMC forums on setting up this, and when it gets to login screen is asks for usrname and password as usual then i get the following message:

```

XBMC needs hardware accelerated OpenGL rendering
install an appropriate graphics driver.

Please consult xbmc wiki for supported hardware
[http://xbmc.org/wiki/?title+Supported_hardware](http://xbmc.org/wiki/?title+Supported_hardware)

```I tried entering the commands on the post above me and it didnt install the beta 190 driver either.

How can i download this driver from (CRT+ALT+F1) because i cant get to graphical mode as it fails to log in. 

And i dont want to have to re-reintall it all again.

Best Regards

Denis



edit:
here is my error:
[B]
(~/.xsession-errors file)

[/B]```

/etc/gdm/Xsession: Beginnin session setup...
Setting IM through im-switch for locale=en=US
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput/xinput.d/default.
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
Error: cound't find RGB GLX visual or fbconfig
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
xlib:extention "GLX" missing on display ":1.0".
Segmentation fault
```


What did i do wrong? I tried installing the ([http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run)) and i still get the same error then the one above.


NOTE: Running 4GB or DDR2 / ubuntu32bit jaunty main

---

### Post by tahina on 2009-10-20
Hi!

I have the Zotac ionitx-a with the atom 330 and I followed the advice of bgiannes in post #18 with great succes (so far).

I'd like to add a few things... 

[[COLOR="Red"]Warning:[/COLOR] **I'm not saying I know what I'm doing! This might burn your house down, for all I know. Just because I'm recless like this, doesn't mean you should be!**]

The N330 is 64 bit, so I chose the 64 bit linux drivers from the [cuda page]("http://www.nvidia.com/object/cuda_get.html") (bgiannes first link) instead. [Edit: And I had previously installed a 64 bit version of ubuntu.]

I needed to do ```
sudo chmod +x cudadriver_2.3_linux_64_190.18.run
``` to be able to run the command ```
sudo ./cudadriver_2.3_linux_64_190.18.run
``` succesfully.

Then I needed to run **nvidia-xconfig**(in a terminal), which complained that my device section didn't have a "Driver" part, so it overwrote my beautiful minimalistic xorg.conf with a new one with lots of possibly unnecessary sections...

I didn't like that, so I copied the device section which had the "Driver" part in it, from the newly generated xorg.conf and pasted that into the backup of the minimalistic original xorg.conf.

...so, now compiz is turned on (which it wouldn't be without the proprietary nvidia driver, right?). [Edit: And also, there is something called "nvidia" now in the list generated by the command **lsmod**.]

---

