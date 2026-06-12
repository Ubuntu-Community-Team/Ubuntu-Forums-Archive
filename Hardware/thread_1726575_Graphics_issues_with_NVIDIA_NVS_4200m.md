---
title: "Graphics issues with NVIDIA NVS 4200m"
date: 2011-04-11
forum: Hardware
---

### Post by ethomp on 2011-04-11
Forgive me if this is the wrong place, but I'm having some issues getting Ubuntu Desktop 10.10 64-bit working on my new Dell Latitude E6520. It has the NVIDIA NVS 4200m graphics card. I am able to get it booted and working, but it must be using a default driver, since all the graphics are very slow even with all settings on minimum. 

There is nothing listed in the "Install Proprietary Drivers" list. From what I can find on the [NVIDIA Website]("http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html"), it's not supported yet. Does anyone know if there are plans to support it or if there is a way I can get them working at a decent level without the proprietary drivers?

---

### Post by johnalewis on 2011-04-13
Looks like support for that GPU was added in 270.41.03. You can get the latest version of the nVidia drivers from this PPA:
[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=maverick](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=maverick)

---

### Post by beew on 2011-04-13
From the specs here the Dell Latitude E6520 is Optimus enabled. 
[http://www.dell.com/us/business/p/latitude-e6520/pd](http://www.dell.com/us/business/p/latitude-e6520/pd)

In that case unless you have a BIOS option to disable Optimus.--I don't think the Dell offers that,-- you won't be able to use the Nvidia card in Linux even if the card is "supported". We are seeing more and more these days as most new laptops with Nvidia are Optimus enabled. This means Nvidia has effectively stopped supporting Linux laptops even though the cards may be "supported" by Nvidia drivers. But worse, even though you cannot use the Nvidia card that you paid for (stuck with the crappy Intel card) , the nvidia card would still eat your battery and generate heat.

[http://www.nvnews.net/vbulletin/showthread.php?t=144750](http://www.nvnews.net/vbulletin/showthread.php?t=144750)

Better return your computer if you still can. Otherwise the least undesirable outcome out of all horrible alternatives would probably be to turn off the Nvidia card (so that it becomes a paperweight instead of sucking system resources)
 [http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus)

Please add your voice here.

[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

I don't expect Nvidia to support gpu switching for Linux, but it is ridiculous that Linux users wouldn't be able to use the Nvidia cards at all,-- the cards that they pay for**, **and Nvidia supports with Linux drivers**.**

Maybe you would also want to write to Dell asking it to provide the BIOS switch to disable Optimus.

---

### Post by ethomp on 2011-04-13
Good news! Looks like dell is putting the option to disable Optimus in the bios of their new laptops. The option said something like "Note, Optimus is only applicable for Windows, it should be disabled for all other OSes". Hopefully this means that they are going to be more supportive towards *nix in the future.

I'm really glad to see that the new NVIDIA drivers support the NVS 4200m. I'll give them a go when I get home from work tonight and post back with how it went.

---

### Post by beew on 2011-04-13
> **ethomp said:**
> Good news! Looks like dell is putting the option to disable Optimus in the bios of their new laptops. The option said something like "Note, Optimus is only applicable for Windows, it should be disabled for all other OSes". Hopefully this means that they are going to be more supportive towards *nix in the future.



If this is true that would be a great news. Do you have any source you can link me to?

---

### Post by nodroglinux on 2011-04-14
Hi

Same problem as you Guys, Dell Latitude E6520, Nvidia and Intel, Ubuntu 10.10

before I disabled Optimus in the BIOS
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: nVidia Corporation Device 1056 (rev a1) (prog-if 00 [VGA controller])

after I disabled optimus in the BIOS
01:00.0 VGA compatible controller: nVidia Corporation Device 1056 (rev a1)

Then I thought lets configure NVidia drivers, so installed the latest from 

> **johnalewis said:**
> Looks like support for that GPU was added in  270.41.03. You can get the latest version of the nVidia drivers from  this PPA:
[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=maverick](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=maverick)

Configured the nvidia and it all works.

Thanks for the help chaps, all sorted now and working with nvidia-settings and dual screen with Dell 23" both running HD/1080P.

---

### Post by ethomp on 2011-04-14
It worked! All I had to do after disabling Optimus was install nvidia-current. Thanks for all the help guys!


> **beew said:**
> If this is true that would be a great news. Do you have any source you can link me to?

I can't find a source, but here's a picture of my bios setup screen:
[IMG]http://i.imgur.com/Qd8PD.jpg[/IMG]

---

### Post by nodroglinux on 2011-04-15
Hi again,

Well having got the graphics working great with the Nvidia card, sound was now an issue.
Spent ages looking around and then followed instructions on [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

After much messing about.....to no avail I got sound at reboot and nothing else.

Disabled Nvidia sound card in "System > Preferences > Sound" Hardware tab and enabled built in internal sound and all burst into life, so graphics and sound just my "reboot" to sort out now and then I will have a working version of a Dell Latitude E6520 with 10.10.

cheers

---

### Post by ethomp on 2011-04-15
Haha thanks man, I spent last night struggling with the sound and then I woke up to this. I'll try what you did. 

When you say sort out your "reboot", what do you mean? When I reboot all I get is the shutdown messages and then it halts there and I need to shut it down by using the power button. Is yours doing that?

---

### Post by nodroglinux on 2011-04-15
When I reboot it goes down but then just displays the "splash" screen and does not attempt to come back up, working on this now.

I got SD card and camera working OK, skype OK but now no mic....another to sort out.

Messages says
[ 8158.434656] Restarting system....

and then nothing happens....

Mic working now......can use skype and others.....

reboot left.....

---

### Post by jastewvanc on 2011-04-21
Thanks all in this thread helping me configure my Dell Latitude E6520.  I thought I'd contribute back by providing a concise description of my system and setup and how I arrived at a working system for this notebook.

I have my Dell E6520 (i7-2720qm Sandy Bridge) working with Ubuntu 10.10 64 bit amd64 kernel version 2.6.36-28, NVidia NVS 4200m.  Optimus is turned off in bios.  Video @ 1920x1080.  Sound and Mic is working as well as the webcam.

I installed the NVIDIA driver: 
```
   sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
   sudo apt-get update
   sudo apt-get install nvidia-graphics-drivers
```

I had to get system updates after this install before it worked. 

I installed the ppa sound driver (which apparently enabled the mic as well):

```
   sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
   sudo apt-get update
   sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```   

Restart is still an issue, but it is tolerable.

---

### Post by Deronius on 2011-04-22
After many hours of frustration I now have drivers enabled and working.  Here's what I did.

```

sudo apt-get purge nvidia-*
sudo apt-get purge xserver-xorg-video-nouveau
sudo add-apt-repository ppa:ubuntu-x-swat/x-update
sudo apt-get update
sudo apt-get nvidia-current

```
NOTE: The last command is different from other posts. This grabbed the 270.x.x drivers for me. The other suggested methods resulted in 'no package found'.
I continued with...
```

sudo nvidia-xconfig

```
***IMPORTANT***
I restarted and entered the BIOS and disabled 'Optimus' under display settings.  Hopefully your bios allows you to do that.

I restarted again and finally had drivers enabled and working.  

Hope this helps someone.

***EDIT*** 
Just realized that my BIOS also had a setting to detect 'Optimus' so it was resetting it every boot.  I disabled it and haven't run into anymore trouble. 

I'm not a big fan of software trying to guess what I want.

---

### Post by Wlo on 2011-05-01
Really helpful, thanks!  I didn't spot the "autodetect optimus" thing!

One small note for anyone else finding this thread - it should be

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

and

sudo apt-get install nvidia-current

Thanks loads!

Wlo.

---

### Post by jth on 2011-05-09
We have a few new E6520s at work and I noticed that there is a Dell-modified image of 10.10 for this model: ubuntu-10.10-i386-dell_A00.iso - [http://ftp.dell.com/OS/](http://ftp.dell.com/OS/)

Before we boot and nuke, has anyone tried this image? We have already installed and tweaked regular 10.10 on the E6520 with mixed results but we are still getting fairly regular hard hangs with the X server.

---

### Post by lochutus on 2011-05-30
I have  a Dell E6420 (i7 with 1600x900 display
[http://www.dell.com/downloads/global/products/latit/en/latitude-e6420-spec-sheet.pdf](http://www.dell.com/downloads/global/products/latit/en/latitude-e6420-spec-sheet.pdf)
)

I originally set it up with ubuntu 10.10 and the video would only give me 800x600 or similar. Although the US site lists 10.10 as an available option for an OS on this laptop, Dell Aus do not support linux. They did, however, very helpfully hunt down the video driver option for me and I got it working. Using the monitor preferences app I was unable to get my external monitor to work but using the Nvidia settings app, it detected and I had both working.

Now to the problems. along comes 11.04, I do a fresh install and everything seems to work just fine. Then I try my external monitor and it doesn't work with monitor preferences, nothing fixed there then. I try nvidia settings and it detects, I set it up, save to xorg.conf, restart X. problems, I find this thread, follow the advice and the best I can get is when I get to the login screen both monitors fire up and the external one has the background image and the laptop screen has the background image and login window. 

Login and the external monitor goes black and the laptop monitor has no unity sidebar (the one with the icons in it on the left hand side of the screen) and the top bar has no unity icon in the top left corner and nothing on the right handside except the weather appindicator I installed, the dropbox appindicator I installed and the bluetooth indicator. 

clicking with the mouse shows no menus. ctrl-alt right/left arrow, moves to another workspace where the external monitor now shows the background image (as does monitor) and some icons flash temporarily on the desktop then disappear. pressing  the power  button briefly flashes the logout options window and if you click in the spot where shutdown or logout should be then that will happen. 

ctrl-alt-F1 takes me to a login screen where I can swap back to the old xorg.conf and get some functionality back.  But I need to external monitor to work. I may have to revert to 10.10 if this isn't fixed soon.

A new anomaly I have discovered since attempting to fix the system. If I right-click on the title bar or an app, say firefox, and select "move to another workspace" the app just shuts down altogether rather than being relocated. If I logout and back in and reopen firefox all the old windows come back. 

any ideas? I have attached screenshots of nvidia settings and monitor prefs and the failed xorg.conf

I hope someone can help and that this helps someone else.

cheers

---

### Post by chandanadesilva on 2011-06-08
I have installed 11.04 on a Dell Latitude 6520 with the NVDIA NVS4200M. This works perfectly out of the box with the nouveau driver. Dual screen suspend and start up all work correctly, provided the Optimus box is ticked in the BIOS setup screen.

If the Optimus box is not clicked, the driver does not recognise the video card.

---

### Post by skrobul on 2011-06-14
> **chandanadesilva said:**
> I have installed 11.04 on a Dell Latitude 6520 with the NVDIA NVS4200M. This works perfectly out of the box with the nouveau driver. Dual screen suspend and start up all work correctly, provided the Optimus box is ticked in the BIOS setup screen.

If the Optimus box is not clicked, the driver does not recognise the video card.

which version of nouveau are you using ? I am having difficulties starting nouvaeu on E6520, dmesg says:

```
[drm] nouveau 0000:01:00.0: Unsupported chipset 0x0d9160a1
```

---

### Post by frogotronic on 2011-06-15
Does this machine suspend/resume & hibernate/thaw with the nVIDIA driver running (i.e. Optimus not checked).

- CH

---

### Post by bjordan1979 on 2011-06-17
Bah! I'm banging my head against the wall. I have a new Thinkpad T420 and can't for the life of me get the Nvidia drivers to work with 10.10. 

If I set the graphics to discrete in the BIOS (use Nvidia) I get the blinking cursor hang on boot.

If I set it to integrated in the BIOS it boots up just fine. I've tried purging all nvidia settings and installing using the x-swat PPA. However every time I install the drivers, shutdown, enable discrete graphics and reboot I get the blinking cursor. 

I'll continue looking into it tonight.

For the people who got it working what order are you doing things as far as BIOS settings? Do you boot up in Integrated install drivers, then reboot in Discrete? Boot with Optimus install drivers, reboot in Discrete, etc?

---

### Post by sillyxone on 2011-07-25
Sorry for reviving a solved thread, but many people are still asking questions. Please feel free to move this to a new thread. 

Here is what I found after suffering the last two weeks with a new E6420:

- sound and wireless don't work out of the box in 10.10, so I use 11.04 instead

- Disabling Optimus will cause the 4200M to run fulltime (5hr battery, dmesg shows only nVidia VGA). This requires either nvidia-current or the driver downloaded directly from Nvidia. These two basically the same, just different versions.

- Enabling Optimus will use the Intel graphic, which is weak (7hr battery, dmesg shows both Intel and nVidia VGA), but the Intel driver is supported out of the box (used primarily). You can selectively run apps with 4200M by using the experimental bumblebee project. However, bumblebee is too experimental for me. 

- When I dual-boot into Windows XP, the Windows' nVidia driver will automatically disable Optimus in the BIOS. On the next reboot back to Ubuntu, I got a black screen (perhaps because Ubuntu doesn't know that it needs to switch from Intel driver to nVidia driver). I had to boot into recovery mode and re-install nvidia-current, also purge xorg.conf.

- the nvidia driver is fine, Compiz works great, suspend/resume works fine. However, it would segfault (error 4, nvidia_drv.so) and crashes xorg every few days (I don't shutdown my laptop, leaving it running/suspend). 

- External monitor work fine with both Intel and nvidia graphics, I can connect to my HDTV just fine. The shortcut (Fn-F8 ) doesn't work with nVidia driver, had to use disper instead.

---

### Post by kelhajjam on 2012-03-29
> **cement_head said:**
> Does this machine suspend/resume & hibernate/thaw with the nVIDIA driver running (i.e. Optimus not checked).

- CH

I have a DELL E640 LATITUDE with Nvidia NVS 4200M, ubuntu 10.10 came installed and Optimus unchecked. At the beginning I had no problem with display. Lately I messed up with the nvidia settings. I got my computer logging off every time I run apps like virtualBox or VLC or Skype... Other apps works just fine.

I ve been trough everything, I know it is the x server which crashes. I tried reinstalling the drivers, reconfiguring the xorg.conf. But nothing works.

Can anyone help me with this problem?

Thank you in advance.

I attach my xorg.conf

---

### Post by frogotronic on 2012-03-30
> **jth said:**
> We have a few new E6520s at work and I noticed that there is a Dell-modified image of 10.10 for this model: ubuntu-10.10-i386-dell_A00.iso - [http://ftp.dell.com/OS/](http://ftp.dell.com/OS/)

Before we boot and nuke, has anyone tried this image? We have already installed and tweaked regular 10.10 on the E6520 with mixed results but we are still getting fairly regular hard hangs with the X server.

I've used this image and it works well - never any hangs

- CH

---

### Post by frogotronic on 2012-03-30
> **chandanadesilva said:**
> I have installed 11.04 on a Dell Latitude 6520 with the NVDIA NVS4200M. This works perfectly out of the box with the nouveau driver. Dual screen suspend and start up all work correctly, provided the Optimus box is ticked in the BIOS setup screen.

If the Optimus box is not clicked, the driver does not recognise the video card.

Then you are not using the nouveau driver, you are using the intel driver.

- CH

---

### Post by frogotronic on 2012-03-30
> **kelhajjam said:**
> I have a DELL E640 LATITUDE with Nvidia NVS 4200M, ubuntu 10.10 came installed and Optimus unchecked. At the beginning I had no problem with display. Lately I messed up with the nvidia settings. I got my computer logging off every time I run apps like virtualBox or VLC or Skype... Other apps works just fine.

I ve been trough everything, I know it is the x server which crashes. I tried reinstalling the drivers, reconfiguring the xorg.conf. But nothing works.

Can anyone help me with this problem?

Thank you in advance.

I attach my xorg.conf

Hello,

I would make sure that all nVIDIA drivers, including the remaining bits (use Synaptic to remove including configuration files) are completely removed.

Then, download the DELL support (URL in attachment) nVIDIA driver and install it.  The remaining instructions are also in the attached xorg file.  Note, this xorg file is set-up for the laptop and an external (VGA) connected with a 1280x1024 resolution.

Post back if you need more help.

- CH

---

### Post by Wopple on 2012-04-12
Just wanted to say thanks for this. I have been scouring the net for weeks trying to figure out why the nvidia drivers weren't working. This was the answer to my problems.

---

### Post by frogotronic on 2012-04-16
> **Wopple said:**
> Just wanted to say thanks for this. I have been scouring the net for weeks trying to figure out why the nvidia drivers weren't working. This was the answer to my problems.

Did the XORG.CONF file work for you?

- CH

---

### Post by VitasLoWang on 2012-07-20
Any news? I have Lenovo T420 with Nvidia Optimus and also have a black screen problem. If I press escape during boot (in the LUKS dialog) I can see soem messages and then I am able to switch to text console and login. Deleting xorg.conf which was generated by nvidia-xconfig and switching to integrated graphics in BIOS made it work and GUI started, but the graphics acceleration seems to be corrupted and cannot be disabled or enabled in compiz settings manager (app crashes with segfault when I try to do it)
Now I don't know how to revert it. Removing nvidia-current does not seem to help, so I guess I am going to reinstall :-]

So I just deleted xorg.conf and it seems to be working! Just compiz settings manager still crashes but I guess I can just leave it on...

---

### Post by frogotronic on 2012-07-20
> **VitasLoWang said:**
> Any news? I have Lenovo T420 with Nvidia Optimus and also have a black screen problem. If I press escape during boot (in the LUKS dialog) I can see soem messages and then I am able to switch to text console and login. Deleting xorg.conf which was generated by nvidia-xconfig and switching to integrated graphics in BIOS made it work and GUI started, but the graphics acceleration seems to be corrupted and cannot be disabled or enabled in compiz settings manager (app crashes with segfault when I try to do it)
Now I don't know how to revert it. Removing nvidia-current does not seem to help, so I guess I am going to reinstall :-]

So I just deleted xorg.conf and it seems to be working! Just compiz settings manager still crashes but I guess I can just leave it on...

my Dell e6420 works very well with a fresh install of 12.04 LTS AMD 64

And I did not have to install anything from DELL, just worked straight out of the box.

Attached is my Xorg.conf

I'm using nVIDIA, and usually a dual head setup (external monitor).

- CH    :guitar:

---

### Post by VitasLoWang on 2012-07-20
I forgot to say it is Ubuntu 11.10 Oneiric Ocelot.

---

