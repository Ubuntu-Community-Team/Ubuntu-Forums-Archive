---
title: "ASUS N53 Laptops, a few issues and some fixes."
date: 2011-05-04
forum: Hardware
---

### Post by TheShadow124 on 2011-05-04
Hi all, 

I recently purchased a ASUS N53 laptop from newegg: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16834220996](http://www.newegg.ca/Product/Product.aspx?Item=N82E16834220996)

These are a few of the issues, and solutions ive found to some of the problems ive had.

**Sleep/Hibernate(Fixed): **
Both would hang as they try to shut down due to a driver issue with the USB3 Port, Solution here: [http://ubuntuforums.org/showpost.php?p=9180298&postcount=7](http://ubuntuforums.org/showpost.php?p=9180298&postcount=7)

Another solution posed below: 
Add the following to your grub boot parameters:
```
pci=nomsi,noaer
```

**Optimus/video card switching: (You can now use your Nvidia card :D )**
use this project:
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

to use, type the following into terminal:
```
rm -r bumblebee
git clone https://github.com/MrMEEE/bumblebee
cd bumblebee/install-files
sudo sh bumblebee-uninstall
cd ..
sudo sh install.sh
```

**Keyboard Shortcuts(some working):**
Most function("fn") keys work exept for the volume up/down/mute and the media keys, screen brightness and projector switching key work, as well as the LCD switch.
Most of the fn keys do not return keycodes, as well as the media keys.

**Intel Turbo(Works)**
When you use the gnome applet for setting your core speed you may think your not getting turbo frequencies, but you are. See :[http://ubuntu.shapado.com/questions/soporte-de-turbo-boost-de-intel-core-i7](http://ubuntu.shapado.com/questions/soporte-de-turbo-boost-de-intel-core-i7)
Know any gnome applets the properly display/edit this information?

**HDMI Support(Minor issue)**
Little problem with HDMI support, if you try to turn on the computer with the HDMI cable plugged into the computer, ubuntu will never boot, it hangs just after grub. But if you unplug it for grub, press enter, then plug back in it all works fine.


Thanks

---

### Post by beew on 2011-05-04
Someone claims he has a solution to the Optimnus problem on Nvidia's Linux forum.

[http://www.nvnews.net/vbulletin/showthread.php?t=162171](http://www.nvnews.net/vbulletin/showthread.php?t=162171)

Don't know if it works or how well it works.

---

### Post by TheShadow124 on 2011-05-04
wow, fast reply, im trying it now, if you dont hear from me soon, i probably broke X

Update: I tried what he suggested, no luck so far, things seem a little worse then before, I have to go now though, I will go through it again tomorrow morning trying to get it working. Thanks

---

### Post by TheShadow124 on 2011-05-05
After following all he said, including enabling it for nvidia accelerated gnome. All icons when i logged in didn't support transparency anymore, no 3d acceleration at all, all icons had black backgrounds, luckily Xserver didn't crash.

---

### Post by Club17 on 2011-05-05
I have ASUS N53SV, same problem when trying to fix nvidia driver, Xserver didn't work. I'm still waiting for anyone know the solution.

Not with my desktop computer, a Phenom X4 that uses ATI 4200 Graphics.

See you.

---

### Post by TheShadow124 on 2011-05-05
did you try the above suggestion? I could have done something wrong.

---

### Post by Club17 on 2011-05-05
> **TheShadow124 said:**
> did you try the above suggestion? I could have done something wrong.

It's a trouble of the driver, and appear old style menu. Running in live mode, unlock the new unity menu.

---

### Post by TheShadow124 on 2011-05-07
Ive got it to not have the graphical problems I had before, but it still kills xserver when I try to run anything useing the nvidia card.

---

### Post by Club17 on 2011-05-07
I'm waiting for a fix, here in the forums. Thanks for the answer.

---

### Post by stimpie on 2011-05-12
You could try [https://lists.launchpad.net/hybrid-graphics-linux/msg01160.html](https://lists.launchpad.net/hybrid-graphics-linux/msg01160.html) to use your nvidia card.

---

### Post by TheShadow124 on 2011-05-12
use the script posted here : [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee) it works like a charm, will require you to know how to use the terminal to run your games though.

make sure you run the uninstall script before installing if youve used a old version, that was my problem for a while, now works quite well.

---

### Post by Club17 on 2011-05-16
> **TheShadow124 said:**
> use the script posted here : [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee) it works like a charm, will require you to know how to use the terminal to run your games though.

make sure you run the uninstall script before installing if youve used a old version, that was my problem for a while, now works quite well.

Ok, thank you. I just uninstalled Ubuntu on my Netbook, but will try to next time.

Cya!

---

### Post by Oliviakrk on 2011-05-17
How about N53SN??

It has nVidia GeForce GT 550M...

Will X-start?

---

### Post by azior on 2011-05-18
I recently bought a Asus N73 (N73SV-V1G-TZ342V) which is basically the same as the N53 except for a bigger screen. If it's possible I would like to expand this topic to also discuss some issues with the Asus N73 series.

I have tried some of the same things as TheShadow124 in his post and some other things not mentioned by him.

**The dual graphic cards issue**
I don't know how to verify this but my guess is that the system only uses the Intel card but that the nVidia card is also powered (battery life is much shorter on Ubuntu than on Windows)

The nouveau driver is installed now (but I don't if it is used). When I install de nVidia driver gdm can't start. When I run nvidia-detect nothing is detected. This is my first nVidia card so I don't know what to expect.

Because the nVidia driver doesn't work properly both the asus-switcheroo and bumblebee are not working at the moment. The asus-switcheroo even blacklists the intel en nouveau modules so the screen has no input whatsoever.

**USB 3.0**
with lshw, lspci and lsusb I know that the Fresco FL1000G USB 3.0 controller is correctly identified. However, when inserting anything in the USB port there is an error with the Intel PCI Bridge which is the host of the Fresco controller. I haven't found a solution yet, only people with [similar]("http://ubuntuforums.org/showthread.php?t=1680278") problems.

I also didn't have much luck with the mediakeys, some fn keys and bluetooth.

---

### Post by blackmoon105 on 2011-05-18
I've fixed USB 3.0 (Fresco Logic FL1000G) adding this parameter to kernel in the grub menu:

```
pci=nomsi
```then from command line type:
```
sudo update-grub
```I've rebooted and usb 3.0 work.

---

### Post by Xero5000 on 2011-05-18
I have a problem the N53JN which is not mentioned here. My sound only works with headphones, not the speakers. Anybody else have the same problem? Any ideas?

*Found solution in an another post*

In terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf
 
Add to the end of the file this line:

options snd-hda-intel model=auto position_fix=0

save&reboot and hopefully the sound now works :)

P.S.
For sound on HDMI also add 
options snd-hda-intel probe_mask=0xffff,0xfff2
to the end. I can't test this so if somebody can please report here does this work.

---

### Post by TheShadow124 on 2011-05-19
sorry, been a few days since ive checked back in here, azior, the solution ive posted above for the USB3 ports should work for any motherboard, and still give you use of them. and the solution for the graphics should fix your issue aswell, in all the OPTIMIS laptops the intel card is hardwired to the LCD, and the nvidia card transfers each frame to the intel card to be displayed. Nice idea for allowing you to only run some programs using each card, but this also makes rendering and such more complicated.

Ill edit the main post to include other modules and such in a day or so here, sorry ive been quite busy the last week here.

---

### Post by TheShadow124 on 2011-05-19
im thinking about starting a wiki for linux laptop support useing mediawiki so we can have a place where we all can post our solutions and problems with each laptop. any thoughts? or if such website exists already?
I own a server I can host it on, just want to know if there is any interest or if anyone thinks it worth it, if nothing like it exists already.

---

### Post by blackmoon105 on 2011-05-19
> **TheShadow124 said:**
> im thinking about starting a wiki for linux laptop support useing mediawiki so we can have a place where we all can post our solutions and problems with each laptop. any thoughts? or if such website exists already?
I own a server I can host it on, just want to know if there is any interest or if anyone thinks it worth it, if nothing like it exists already.

Starting a wiki is a good idea, i was thinking the same thing just yesterday. I don't have found nothing of similar in the web.

---

### Post by Oliviakrk on 2011-05-19
So would you recommend that(N53/73) laptop for linux ? 

I need something fast and it is the cheapest.

---

### Post by Xero5000 on 2011-05-19
@Oliviakrk 
I would try to avoid any laptop with Nvidia Optimus technology for Linux (including the N53/N73), it's a pain to setup and it doesn&#8217;t work properly even when you do set it up.

---

### Post by Oliviakrk on 2011-05-19
Ok. Thanks for the warning. I'll wait for decent amd :).

---

### Post by TheShadow124 on 2011-05-19
I am happy with my N53SV laptop, if you want to game on your linux OS a different laptop would be a good idea.

OK, Ill hopefully get a wiki up this weekend, ill post the link here when I finish with that, ive got a few other projects on the go right now and time is a little strained.

---

### Post by Oliviakrk on 2011-05-20
I need windows so I would play on it. Linux is for everyday use...

---

### Post by dugh on 2011-05-21
Also, even with the fixes to the card (I got nvidia disabled before, now using the bumblebee script), none of the compiz stuff works in 11.04 natty, including unity.

There seems to be (yet) another bug with nvidia-current in 11.04 where you can't enable compiz.  There are so many regressions in 11.04 I can't keep track anymore.

---

### Post by Oliviakrk on 2011-05-21
How long battery lasts using intel with disabled nvidia??

---

### Post by galois1 on 2011-05-23
Hi. I am going to buy an ASUS N53SV and I need it to work with Ubuntu. I will use Ubuntu with OpenOffice, latex, e-mail, internet, etc. I don't mind using windows for multimedia and games. Do you think that I can use the laptop with Ubuntu for these pourposes?

---

### Post by blackmoon105 on 2011-05-23
Yes, N53 is a good choice.

---

### Post by galois1 on 2011-05-23
Thanks. I think that I will get an ASUS N53

---

### Post by philou24 on 2011-05-24
(Excuse me, my english isn't very good...)

I have an Asus N73SV.
I use ArchLinux and the internet connection (by RJ45) doesn't work (no driver loaded).
What is the driver's name in Ubuntu ?

Thank you.

---

### Post by Oliviakrk on 2011-05-24
> **oliviakrk said:**
> how long battery lasts using intel with disabled nvidia??


^bump:)

---

### Post by galois1 on 2011-05-24
blakmoon105, does the wifi works with n53? Is it hard to configure?

---

### Post by blackmoon105 on 2011-05-25
> **philou24 said:**
> (Excuse me, my english isn't very good...)
I have an Asus N73SV.
I use ArchLinux and the internet connection (by RJ45) doesn't work (no driver loaded).
What is the driver's name in Ubuntu ?
Thank you.

The driver loaded in Ubuntu for N53sv is "r8169" ( even if it should be r8168 )
Anyway you can find the latest driver for Linux here: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)


> **Oliviakrk said:**
> How long battery lasts using intel with disabled nvidia??
With Linux, more ore less a couple of hours... In Windows up to 4.5 hours


> **galois1 said:**
> blakmoon105, does the wifi works with n53? Is it hard to configure?
Yes the wifi work fine, no special configurations are required. The same things that you do in Windows.

---

### Post by Oliviakrk on 2011-05-25
Thanks. I am going to buy it now;).

---

### Post by adam.webb on 2011-06-01
Has anyone had any luck getting the hotkeys to work? As OP said, only the Brightness buttons work so far, and it would be great to get the volume/media buttons working too! I've tried various things, and had no luck so far...

Adam

---

### Post by yahooking on 2011-06-04
I have all volume keys and play button and mute key working as well at the key with the little dude on it which i have set to lock my screen on pressing it. 

I used the following kernel module.
[http://acpi4asus.sourceforge.net/](http://acpi4asus.sourceforge.net/)

I hope this saved you some time :)

One issue i still have is the on screen display when i change brightness i do not get the OSD but brightness still is adjusted any tips on fixing that ?

> **TheShadow124 said:**
> Hi all, 

I recently purchased a ASUS N53 laptop from newegg: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16834220996](http://www.newegg.ca/Product/Product.aspx?Item=N82E16834220996)

These are a few of the issues, and solutions ive found to some of the problems ive had.

**Sleep/Hibernate(Fixed): **
Both would hang as they try to shut down due to a driver issue with the USB3 Port, Solution here: [http://ubuntuforums.org/showpost.php?p=9180298&postcount=7](http://ubuntuforums.org/showpost.php?p=9180298&postcount=7)

Another solution posed below: 
Add the following to your grub boot parameters:
```
pci=nomsi,noaer
```

**Optimus/video card switching: (You can now use your Nvidia card :D )**
use this project:
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

to use, type the following into terminal:
```
rm -r bumblebee
git clone https://github.com/MrMEEE/bumblebee
cd bumblebee/install-files
sudo sh bumblebee-uninstall
cd ..
sudo sh install.sh
```

**Keyboard Shortcuts(some working):**
Most function("fn") keys work exept for the volume up/down/mute and the media keys, screen brightness and projector switching key work, as well as the LCD switch.
Most of the fn keys do not return keycodes, as well as the media keys.

**Intel Turbo(Works)**
When you use the gnome applet for setting your core speed you may think your not getting turbo frequencies, but you are. See :[http://ubuntu.shapado.com/questions/soporte-de-turbo-boost-de-intel-core-i7](http://ubuntu.shapado.com/questions/soporte-de-turbo-boost-de-intel-core-i7)
Know any gnome applets the properly display/edit this information?

**HDMI Support(Minor issue)**
Little problem with HDMI support, if you try to turn on the computer with the HDMI cable plugged into the computer, ubuntu will never boot, it hangs just after grub. But if you unplug it for grub, press enter, then plug back in it all works fine.


Thanks

---

### Post by adam.webb on 2011-06-05
> **yahooking said:**
> I have all volume keys and play button and mute key working as well at the key with the little dude on it which i have set to lock my screen on pressing it. 

I used the following kernel module.
[http://acpi4asus.sourceforge.net/](http://acpi4asus.sourceforge.net/)

I hope this saved you some time :)

One issue i still have is the on screen display when i change brightness i do not get the OSD but brightness still is adjusted any tips on fixing that ?

Can't see any files for the N53, also looks like quite and old project, does anyone have any idea if any of the files might work with these machines?

Adam

---

### Post by yahooking on 2011-06-05
> **adam.webb said:**
> Can't see any files for the N53, also looks like quite and old project, does anyone have any idea if any of the files might work with these machines?

Adam
I am using this on my ASUS n53sv-xv1 it works fine.

---

### Post by adam.webb on 2011-06-06
> **yahooking said:**
> I am using this on my ASUS n53sv-xv1 it works fine.

Any hints or tips on what files to download etc? There seems to be a lot of different options.

Ta

Adam

---

### Post by blackmoon105 on 2011-06-08
I've write a wiki page for Asus N53 here: [https://help.ubuntu.com/community/Asus_N53](https://help.ubuntu.com/community/Asus_N53) :-)

Any contribute is welcome.

---

### Post by adam.webb on 2011-06-08
That's awesome Blackmoon! 

I'm still having trouble downloading acpi4linux-dkms,  I've added the repo and updated, but it still seems not to exist... any suggestions?

Love your work!

Adam

---

### Post by blackmoon105 on 2011-06-09
Sorry it was a typo, the correct package name is **acpi4asus-dkms** and NOT acpi4linux-dkms. Thanks for reporting. Wiki page fixed.

---

### Post by rigg63 on 2011-07-06
I recently bought an ASUS N73S, as I understand the same machine as N53S except the 17' size.

I can't get the USB3 port work at all with ubuntu 11.04 32-bit. The system dos not mount the disk. Tried with 2 different external USB3 disks.

In the pre-installed Win7 x64 the disks are running fine.

---

### Post by Oliviakrk on 2011-07-07
Add  pci=nomsi

to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

(GRUB_CMDLINE_LINUX_DEFAULT="quiet  pci=nomsi")

In /etc/default/grub

---

### Post by rigg63 on 2011-07-07
> **Oliviakrk said:**
> Add  pci=nomsi

to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

(GRUB_CMDLINE_LINUX_DEFAULT="quiet  pci=nomsi")

In /etc/default/grub

Thanx. Done that, without seccess!

---

### Post by Oliviakrk on 2011-07-07
Now:
```

sudo update-grub

```

---

### Post by rigg63 on 2011-07-08
> **Oliviakrk said:**
> Now:
```

sudo update-grub

```

Oh, did that too when I did the other steps... It doesn't work anyway

---

### Post by rigg63 on 2011-07-10
> **Oliviakrk said:**
> Now:
```

sudo update-grub

```

Reinstalled ubuntu x64 (first attempts was on 32-bit)

Now it's working fine 

Thanks, case closed ;)

---

### Post by jeroentj386 on 2011-08-17
Sweet!
I just solved my N53JN energy problems by installing asus-switcheroo.
It disables the nVidia card just like it's supposed to.

---

### Post by Club17 on 2011-08-17
Trying installing experimental nvidia display driver will solve the trouble.

---

### Post by fuzzywolf on 2011-08-25
I followed the instruction for bluetooth but I wasn't able to make it work. The driver compiling part gave out some errors but it was compiled and installed (i guess). not sure how to verify though... i've even found the original post where it came from but no luck  with that too :( I googled the id string of the bt peripheral but found nothing conclusive :( Any help will be appreciated :)

edit: bt is now WORKING

i went back to windos and cycled the device of and on again and on the next login in ubunto it was there nice and working :))))

---

### Post by Oliviakrk on 2011-08-25
I had the same problem. After hibernating or suspending bt wouldn't start in Lunix. Only in windows. That's the reason why I changed my mouse :(.

---

### Post by Tazza101 on 2011-08-27
Hi, I'm a new Italian user, it's the first time I write on this forum, but I've been reading it for ages :)

However I have a N53SV and this  topic has been quite useful, I especially want to thank the guy who created this wiki [https://help.ubuntu.com/community/Asus_N53]("https://help.ubuntu.com/community/Asus_N53#repository")  but I wanted to ask a question.
The suspend to ram function now works thatnks to the**20_suspend-ehci-hcd** script, BUT everytime i resume my computer from the suspend, the USB ports are not working and the webcam is not working too (I understand this is connected, because the webcam uses a usb connection I think). I haven't found ubuntu users complaining about this issue, but it's really annoying to me, as it makes suspending the computer pretty useless. 

I found a solution on the arch forum [https://bbs.archlinux.org/viewtopic.php?pid=910195](https://bbs.archlinux.org/viewtopic.php?pid=910195)  but even trying to do that, does not solve my problem....

I don't really want a solution, but I just want to know if I'm the only one with this problem! 

Thanks :)

Francesco

---

### Post by rd1381 on 2011-08-30
> **Tazza101 said:**
> Hi, I'm a new Italian user, it's the first time I write on this forum, but I've been reading it for ages :)

However I have a N53SV and this  topic has been quite useful, I especially want to thank the guy who created this wiki [https://help.ubuntu.com/community/Asus_N53]("https://help.ubuntu.com/community/Asus_N53#repository")  but I wanted to ask a question.
The suspend to ram function now works thatnks to the**20_suspend-ehci-hcd** script, BUT everytime i resume my computer from the suspend, the USB ports are not working and the webcam is not working too (I understand this is connected, because the webcam uses a usb connection I think). I haven't found ubuntu users complaining about this issue, but it's really annoying to me, as it makes suspending the computer pretty useless. 

I found a solution on the arch forum [https://bbs.archlinux.org/viewtopic.php?pid=910195](https://bbs.archlinux.org/viewtopic.php?pid=910195)  but even trying to do that, does not solve my problem....

I don't really want a solution, but I just want to know if I'm the only one with this problem! 

Thanks :)

Francesco

i have the same problem too.
i use ppa vesion mentioned in help.ubuntu.com for n53
but still usb is disable or someting after coming up from hibernate or sleep mode witch sucks cause i use a usb mouse

any help would be great

---

### Post by Tazza101 on 2011-08-31
> **rd1381 said:**
> i have the same problem too.
i use ppa vesion mentioned in help.ubuntu.com for n53
but still usb is disable or someting after coming up from hibernate or sleep mode witch sucks cause i use a usb mouse

any help would be great

It's nice to see I'm not the only one... I use a usb mouse too, so this is pretty inconvenient....
I tried to follow the advice to unload before suspend and then reload after suspend the module ehci-hcd, modifying the file /etc/default/acpi-support in this way:

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="ehci-hcd"
```


But this thing I tried to do didn't work at all :(

---

### Post by lancest on 2011-09-07
> **jeroentj386 said:**
> Sweet!
I just solved my N53JN energy problems by installing asus-switcheroo.
It disables the nVidia card just like it's supposed to.

N53S Nvidia 550M
Unable to make this work yet. Point me to exactly what you did?

---

### Post by lancest on 2011-09-07
Ok got card switching working following this: 
[http://ubuntuforums.org/showthread.php?p=11227184#post11227184](http://ubuntuforums.org/showthread.php?p=11227184#post11227184)

For volume key setup it seems unclear about acpi4asus 
What file to use?  Lapsus?

---

### Post by Oliviakrk on 2011-09-07
Could you post how you disable nvidia?? Is the status led changing to blue when you do that?

---

### Post by lancest on 2011-09-07
Got asus file from PPA.

What I've noticed:
No blue lights. 
It seems like the Intel card is default.
Use Bumblebee commands.
[At Command line typing[COLOR="Indigo"] bumblebee tab[/COLOR]  shows them]
[COLOR="Navy"]bumblebee enable[/COLOR] (nothing else typed) will give you NVidia
bumblebee disable back to default Intel.

Running cool at 43
acpi -t 

Not much time here.
Will post more later today if useful.

---

### Post by Oliviakrk on 2011-09-08
Blue is intel -> nvidia (white) is the default one.

It still don't see any difference in battery life. 2h is most I can get in linux. I think nvidia is always on.

---

### Post by lancest on 2011-09-08
lance@ubuntu:~$ sudo bumblebee-enablecard 
_PS0 Enabling nVidia Card Succeded.

lance@ubuntu:~$ sudo !!
sudo bumblebee-disablecard
_PS0 Disabling nVidia Card Succeded.

There is no light change on the keyboard.
Seems like the Intel card is default.

Battery life seems improved but haven't had time to fully test. 
The reading just jumped between 3:45 to 4:00 battery after unplugging.

edit:  my battery is the 5200 MA

---

### Post by rain87 on 2011-09-23
i've got this laptop yesterday, and installed 11.10 beta. i've got almost everything working out-of-the-box :) all the fn-keys (with exception for fn+f9, which toggles touchpad on/off), wi-fi, nvidia card is switched on/off perfectly with ironhide. there were troubles with suspend, but workaround for usb3 module from first post made the deal, suspend works now

the only problem left is a touchpad. when i boot ubuntu and login screen appears, touchpad works. when i login - touchpad dies

i've tried this commands to enable touchpad:```
root@rain87-N53SV:~# xinput list|grep -i touch
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=14    [slave  pointer  (2)]
root@rain87-N53SV:~# xinput list-props "ETPS/2 Elantech Touchpad"|grep -i enabled
    Device Enabled (132):    0
root@rain87-N53SV:~# xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 1
root@rain87-N53SV:~# xinput list-props "ETPS/2 Elantech Touchpad"|grep -i enabled
    Device Enabled (132):    0

```so i wasn't able to get touchpad working, googling hasn't helped much. does anyone know how to turn touchpad on/off at n53sv?

---

### Post by rain87 on 2011-09-24
figured out - i've moved settings from my old laptop, and touchpad was disabled via dconf. so i have enabled it, now everything works fine

---

### Post by lancest on 2011-10-13
ASUS N53SN
Is anyone using Oneric 11.10 with this notebook?  

I got hung up installing 11.10 with Bumblebee. 

Like to know if there is any difference in setup procedure.

Also what about battery life?  With 11.04 I get about three hours and BB works fine.

Looking to update.

---

### Post by adam.webb on 2011-10-23
I updated to Ubuntu 11.10 last week. The only major problem I had was with the wireless being verrry slow. Trawling through varios threads on these forums and elsewhere I finally found a solution that worked for me:

Create a file: 
```
/etc/modprobe.d/ath9k.conf
```

and add the line:
```
options ath9k nohwcrypt=1
```

That fixed it for me, and will hopefully help some others out.

I should point out, however, that I haven't got a clue how it works/what it does, so use at your own risk. :)

Cheers

A

---

### Post by lancest on 2011-10-24
Is 11.10 stable with the ASUS N53 yet?  I tried it on release day and ran into some strange lockups. Operating temp ok?  I tried Gnome Shell and it went nuts. 

How to disable touchpad when typing? The simple GUI methods aren't working for me. (I've got 11.10 on another laptop and it doesn't work there either.)

---

### Post by adam.webb on 2011-10-24
> **lancest said:**
> Is 11.10 stable with the ASUS N53 yet?  I tried it on release day and ran into some strange lockups. Operating temp ok?  I tried Gnome Shell and it went nuts. 

How to disable touchpad when typing? The simple GUI methods aren't working for me. (I've got 11.10 on another laptop and it doesn't work there either.)

Works fine for me, I'm not running Gnome Shell, but Unity (2D) seems to go ok, with temps not getting much above 60degC.

Having the same problem with touchpad though.

---

### Post by adam.webb on 2011-10-24
TO FIX THE DISABLE TOUCHPAD BUG:

First go to System Settings -> Mouse and Touchpad and make sure the 'Disable Touchpad while Typing' is NOT set.

(we will use our own method, and don't want the default one interfering). 

Then go to 'Startup Applications', click 'Add', and in the 'Command:' box put ```
syndaemon -i 1.5 -t -k -d
```

Call it 'Touchpad Disable' or something similar, and put a comment in if you want. Click 'Save', restart, and all should be well. 

To 'personalise' the settings:
```
-i 1.5
``` Controls how many seconds after typing has stopped until it enables the touchpad again. I have found 1.5 seconds to be about right.
```
-t
``` Means you can still move the mouse around the screen if you want to, but tapping and scrolling is disabled.
```
-k
``` Allows you to use 'key combos' without disabling the mouse, making it easier if you're doing a lot of copy-pasting or similar.
```
-d
``` Makes it run as a daemon (in the background).


PS. For some reason, I was not able to change anything in the 'Startup Application' window, whenever I set anything and exited the window, it wouldn't be there when I returned. If anyone else is having this problem then:

```
sudo chown [username] /home/[username]/.config/autostart
sudo chmod 775 /home/[username]/.config/autostart 
```

Should sort it out

---

### Post by lancest on 2011-10-27
Adam thanks for the heads up on Unity 2D. Wow I like the way it moves! 
Glad I tried it- per your recommend. Going to stick with it. (Unit is still buggy too)

The syndamon didn't work, I had tried it before in past without success. 

The .tp_toggle script from Ubuntu Wiki however does!

---

### Post by anjexe on 2011-11-05
[http://ssnjara.wordpress.com/2011/06/11/touchpad-onoff-shortcut-key-on-xubuntu-11-04-eeepc1005ha/](http://ssnjara.wordpress.com/2011/06/11/touchpad-onoff-shortcut-key-on-xubuntu-11-04-eeepc1005ha/)

Touchpad On/Off shortcut key on Xubuntu 11.04 (eeePC1005HA)


Immediately after installation shortcut keys (buttons) work for all except for the touchpad on/off button. I solved this problem with a little script.

Touchpad notifikacija

    script:

#!/bin/bash
#######################################
# DESCRIPTION: Toggles Touchpad ON/OFF
# DATE: 15.4.2011
# AUTHOR: ssnjara
#######################################
# Check if Touchpad is ON and set "var" acording
var=`synclient | grep TouchpadOff | cut -d\= -f2`
# if ON turn OFF, else turn ON
if [ $var -eq 0 ]
then
synclient TouchpadOff=1
notify-send -i dialog-error "Touchpad disabled!"
else
synclient TouchpadOFF=0
notify-send -i dialog-information "Touchpad enabled!"
fi
#END

    Copy the script in a text editor and save as &#8220;touchpadToggle.sh. After that you need to make a script executable . Open the &#8220;Terminal&#8221; in the directory containing the script and type:

sudo chmod +x touchpadToggle.sh

Now we have to make a keyboard shortcut to activate the script:

Postavljanje tipkovni&#269;ke kratice

    Open the Settings Manager> Keyboard> Application Shortcuts, click on &#8220;Add&#8221; and in the field command: enter the path to the script or click on the &#8220;open&#8221; and navigate to the script. When you open the &#8220;Command Shortcut&#8221; window, press shortcut key to turn off the touchpad.

You just set the touchpad On/Off button to perform its function :) .

---

### Post by Edemoe on 2011-11-16
Does anybody also experiencing problem loading Ubuntu with the second monitor connected? If so please vote for this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/814895](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/814895)
Or if you have a solution reply please :)

---

### Post by Tazza101 on 2012-01-05
Does anybody have updates on the "no usb after waking from suspend" bug?

---

### Post by ralliartvr47 on 2012-03-01
hello all. im new to this forum. i bought my first asus N53SV-EH71 laptop from amazon and d only trouble im experiencing is major webcam lag. does anyone know how to fix this...everything else is perfect

---

### Post by anjexe on 2012-05-03
i install ubuntu 12.04 on my asus n43 
still usb 3 dosent work :(
just a mobile charger now :(
hope fore solution

---

### Post by Clancy_s on 2012-06-26
> **Tazza101 said:**
> Does anybody have updates on the "no usb after waking from suspend" bug?

I couldn't fix it using any version of the 20_whatever suspend script but using the 

pci=nomsi,noaer

option in grub, with no suspend script, works for me - suspends fine, usb works on wake up.

I suspect this is something that varies between installs, given that there's been relatively few posts on it.  If the grub parameters option doesn't work for you there's a thread on arch linux that suggests adding a couple of lines to the script, it didn't work for me but may for you.  They're in the last post in this thread:

[https://bbs.archlinux.org/viewtopic.php?pid=910195](https://bbs.archlinux.org/viewtopic.php?pid=910195)

---

