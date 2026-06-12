---
title: "Lenovo Thinkpad Yoga 2nd Gen with Ubuntu 14.04"
date: 2015-03-25
forum: Hardware
---

### Post by cheflo on 2015-03-25
[FONT=arial][B]UPDATES 

[/B]-Added how to enable upper mouse buttons
- Unfortunately, the two issues below are present in 14.10 as well, both without and with the intel graphics installer(1.08). *However, they are significantly rarer and I am using 14.10 happily.*
- Upon opening the lid, the screen is sometimes frozen after the laptop has been closed (suspended) for a while. This usually fixes itself after a few seconds and I get redirected to the log in prompt, but once I had to kill X.
- The screen is definitely iffy after suspend. Not necessarily the touch input, but there are graphical glitches and scrolling becomes laggy. I will test with 14.10 and the latest intel drivers when I have more time.

**Original Post**
Hi everyone,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I thought I would start a thread where we can share tips and tricks on what makes Linux run smoothly on the 12.5" TP Yoga 2nd gen. I installed Ubuntu 14.04 Unity desktop on mine yesterday and it has been running great so far. Below you can take part of what is working (almost everything) and what is not (almost nothing) =). Many of the tips and scripts I include here are from [this guy]("http://en.pztrn.name/blog/2014/01/07-thinkpad-yoga-tricks-making-it-work-linux") and the [previous discussion]("http://ubuntuforums.org/showthread.php?t=2193327") on running Linux on the first generation TP Yoga and only include minor modifications of my own so credit goes to the original authors. I got the TP Yoga with 8gb of ram, i5, 256GB SSD (samsung evo, upgraded myself, [it's easy]("https://www.youtube.com/watch?v=nj7azo6syQQ")), 1080p multitouch screen with active digitizer.[/FONT]
[FONT=arial]
[B]Pen
[/B]
[LIST]
[*]I like the feel, it is a little small, but miles ahead of the one that came with the Asus Vivotab note8.
[*]Button = right click (configurable in settings as top button)
[*]Pressure Sensitivity
[LIST]
[*]Works out of the box in Krita, which also seems to have some sort of in build palm rejection. [Guide to calibration if needed]("http://www.davidrevoy.com/article182/calibrating-wacom-stylus-pressure-on-krita")
[*]In Gimp, Edit > Input Devices > Change the wacom device from 'Disabled' to 'Screen'.
[*]I got the best results by setting the tip feel as a little bit firmer in the wacom systems settings
[/LIST]
[/LIST]

**Fn Keys**

[LIST]
[*]Works:
[LIST]
[*]FnLock
[*]VolMute/Mute/VolUp/VolDown/MicMute
[*]BrightUp/BrightDown
[*]Wifi
[*]Home/End/Insert
[*]Fn+Space for keyboard backlight
[/LIST]

[*]Doesn't work (xev output in parenthesis):
[LIST]
[*]Projector key (expose event?)
[*]Settings (keycode 179)
[*]Search (lots of zeros)
[*]Task switcher (keycode 128)
[*]App menu (keycode 165)
[/LIST]
[/LIST]


**Webcam and mic**

[LIST]
[*]Works out of the box in Skype and cheese.
[/LIST]

**Touchscreen**

[LIST]
[*][Some gestures]("https://wiki.ubuntu.com/Multitouch") work out of the box. I read that unity does not play nicely with touchegg, so didn't investigate this further.
[LIST]
[*]Even though the default ubuntu gestures are somewhat lacking, Google Chrome has great support for gestures which pretty much save the day. In chrome://flags - Enable Touch events > automatic, Enable Pinch Scale > Enabled, Enable touch based editing > Default
[/LIST]

[*]Once it [died after suspend]("https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/1275416"), have tried some solution online to get it back but no luck.
[LIST]
[*]Originally 'SYNAPTICS Synaptics Touch Digitizer V04' in xinput list. Entry disappears after suspend.
[*]However, this only happened once and now it works perfectly after waking up.
[/LIST]

[*]There seems to be some random graphics issues occurring, like having [some letters disappear]("http://ubuntuforums.org/showthread.php?t=2232410") in titlebars and filenames. It is not very severe and goes away when rescaling the text in Display Options
[*]There is a[ patch suggested in this discussion]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1342675"), but it did not download when I updated my system and the[ newest intel installation tool]("https://01.org/linuxgraphics/downloads/2015/intelr-graphics-installer-linux-1.0.8") seems not to be available for 14.04 ([at least not 14.04.2]("https://01.org/linuxgraphics/comment/1157#comment-1157")).
[/LIST]

**Touchpad**

[LIST]
[*]One finger = left click (button 1), two finger = right click (button 3), three or more fingers = nothing (not registered by xev)
[*]Clickpad click = left click, clickpad click close to bottom right corner = right click
[*]Upper Buttons
[LIST]
[*]Left = button 4 (unfortunately the same as two finger scroll up)
[*]Right = button 5 (unfortunately the same as two finger scroll down)
[*]Middle = not registered by xev and omdifying 50-synaptics.conf has no effect
[*]This lack of button features is related to [bugs]("https://bugs.freedesktop.org/show_bug.cgi?id=88609")/lack of [functionality]("http://who-t.blogspot.de/2015/01/lenovos-x1-carbon-3rd-touchpad-woes.html") in the kernel for the new hardware lenovo chose to implement. There is a patch to be committed to 4.0 (and maybe backported?)
[*]If you want the buttons to work as left, middle, right and are ready to lose two finger scrolling/clicking and some touchpad sensitivity, then you can do the below (from [here]("http://askubuntu.com/questions/127757/how-do-i-make-modprobe-changes-permanent"))
[/LIST]
[/LIST]
```
modprobe -r psmouse

modprobe psmouse proto=imps
```
To make this change permanent, create a file such as touchpad.conf under /etc/modprobe.d/, and put the following line in it:
```
options psmouse proto=imps
```


[LIST]
[*]If you want to disable areas of the trackpad, copy /usr/share/X11/xorg.conf.d/50-synaptics.conf and name it 60-synaptics.conf to have higher precedence. Then add the following two lines```
Option "AreaTopEdge" "30%"
Option "AreaBottomEdge" "80%"
```

so that the second last section of the file reads
```
# This option enables the bottom right corner to be a right button on clickpads
# and the right and middle top areas to be right / middle buttons on clickpads
# with a top button area.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
        Option "SecondarySoftButtonAreas" "58% 0 0 15% 42% 58% 0 15%"
    Option "AreaTopEdge" "30%"
    Option "AreaBottomEdge" "80%"
EndSection
```

That disables to top 30 % and bottom 20 % for me.
[/LIST]

**Spin**
[LIST]
[*]This is a cool python utility written by an owner of the first gen yoga and linked in the thread mentioned above. You can download it from [GitHub]("https://github.com/wdbm/spin"). You will need to make a small change.
[LIST]
[*]The touchscreen name is now 'SYNAPTICS Synaptics Touch Digitizer V04' instead of 'ELAN Touchscreen'. Search and replace accordingly.
[*]Most things seems to work great here, but I was having some problem with windows not filling up the screen when rotated vertically. I will need to test this more.
[/LIST]
[/LIST]


**Additional comments**


[LIST]
[*]If you opt to use any of the other rotation scripts from the 1st gen TPYoga thread, note that you need to change ```
[COLOR=#000000][FONT=Ubuntu Mono]current_orientation(){xrandr|grep " connected" |awk '{print $4}'[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]}[/FONT][/COLOR]
``` to ```
current_orientation(){xrandr --verbose|grep eDP1|awk '{print $6}'}
``` and remove a left parenthesis from the first 'normal' a few lines after that.
[/LIST]



[LIST]
[*]It's annoying that insert is the default behaviour of the End key under FnLock. Add ```
sleep 2 && setxkbmap us -option  caps:ctrl_modifier && xmodmap -e "keycode 118 = End" && xmodmap -e "keycode 115 = Insert"
``` to the start up scripts and without the sleep command to a custom keyboard shortcut for when waking from suspend etc.
[/LIST]


[LIST]
[*][Double mouse icons after rotating the screen]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1376760") (only for a while)
[*]Arrow keys feel a bit small
[*]Wifi works after suspend!! =D (unfortunately not that great in 14.10, need to turn it on and off some times)
[*]Keyboard feels great!
[*]Battery life was a bit disappointing during the first day (around 4 hours), but today it seems to be at least 5. I need to experiment more with brightness settings as this computer gets pretty bright which draws a lot of juice.
[/LIST]

Overall I am very happy with my new laptop! It is so much more portable than my last (17", hehe) and the screen folding with pen input helps a lot when reading articles and taking notes. I still have to test note taking with onenote under virtualbox/vmware, but I have a lot of work to do this week so future updates might take a while. Looking forward to input from other TP Yoga owners with their experience in running Linux on this machine.

[/FONT]

---

### Post by cheflo on 2015-03-26
So the only major issues so far are with the screen after suspend. There are graphic glitches, laggy scrolling and missing characters (the latter actually not only after suspend and not yet with 14.10+intel updater). These issues are present in Ubuntu 14.04 and 14.10 even with the intel graphics updater. I have only tried the Unity desktop so far, is it time to venture into alternative desktop environments/linux flavors or does anyone have any suggestion to what I can do to remedy these problems?

---

### Post by ZICODIAN on 2015-03-27
Hey

I've updated spin by adding a little procedure to get the appropriate input device names, so it should work with both the ThinkPad S1 and S120 Yogas without modification now.

[https://github.com/wdbm/spin](https://github.com/wdbm/spin)

---

### Post by cheflo on 2015-03-27
sweet thanks!

btw, can I ask you what desktop environment you are using. are you having similar issues as I am?

---

### Post by cheflo on 2015-04-11
After a couple of weeks with the yoga, I am extremely happy with my purchase!

Especially since a reddit user made me look into how to extend the battery life of this laptop:

Without any tweaks, I used to have an estimated battery life of 5-6 h and a wattage usage of about 7-8 W... . This is with brightness level 3 ([using brightness indicator]("http://ubuntuhandbook.org/index.php/2014/11/install-brightness-indicator-ubuntu-1410/")) and reading articles in chrome while having my gmail open.

After tweaking, I now have and whopping 7+ h of estimated battery and use only 5-6 W in the same scenario as above! Of course, this method of measuring is not directly rigorous, but I tried to keep usage scenario as similar as possible and my laptop definitely has longer battery life estimates now.

So what did I do? Well, barely nothing. Initially, battery tweaks were slightly confusing as there is multiple utilities for this, including jupiter, laptop-mode-tools, pm-utils and tlk. After reading [all]("https://help.ubuntu.com/community/PowerManagement/ReducedPower") [over]("http://askubuntu.com/questions/172391/is-laptop-mode-tools-still-relevant-for-12-04-and-the-3-x-kernels") [the]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks") [place]("http://askubuntu.com/questions/265880/why-does-powertop-still-detect-tunable-settings-on-12-04"), what I took away from it was this (please correct me if I am wrong): The kernel what updated a few years ago with powersaving settings for laptops but these are not enabled automatically. Therefore, laptop-mode-tools was initially needed to enable these settings. Then there is also jupiter, which enabled additional power saving features. Later, pm-utils was added and most of jupiter's settings were now enabled by default (and jupiter has since been discontinued), but configuration is spread out in a few scripts and the defaults are not as aggressive as they could be. Now there is tlp, which has more efficient default settings and any additional configuration can be done from a single script instead of several different. You can see the difference in powertop, both in the lower wattage and the amount of tunables that have been changed from 'bad' to 'good' (there are a few extra that can be toggled, i didn't try them). The only default setting that I read was somewhat questionable is low power sata mode, which [could cause data corruption]("https://wiki.ubuntu.com/Kernel/PowerManagementALPM") in the odd case, I'm still using it for now. **TL;DR install [tlp]("http://www.linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html") and enjoy **(tlp tlp-rdw, and thinkpad specific: tp-smapi-dkms acpi-call-dkms [tp-smapi will show as inactive, which seems to be the case of all new thinkpad as per the tlp faq])

The same user on reddit also pointed me towards [a set of scripts]("https://github.com/admiralakber/thinkpad-yoga-scripts") for automatic rotation of the screen using the accelerometer, but I haven't tried them out yet. Lastly, I do not have as severe screen issues as before, just garbled text that can be fixed on zooming in/out, no stuttering.

---

### Post by ZICODIAN on 2015-04-14
Hey there! Thanks for all of the details on the power efficiency. I'll take a look at the details on it, but what you've got looks good.

I've updated [spin]([https://github.com/wdbm/spin](https://github.com/wdbm/spin)), fixing the touchpad switch and adding nipple/touchpad orientation control.

Thanks also for mentioning the experiments concerning the accelerometer. I'll take a look.

---

### Post by xt-gr79 on 2015-04-21
@cheflo Thanks for sharing all these. I own a yoga S1 and I've noticed that the power consumption is much bigger in ubuntu and manjaro KDE than in windows. In addition the fan is working more time. Do all these apply to S1 as well? Could you please briefly write down the steps you followed to reduce power cosumption (it was not clear to me from your post)?

---

### Post by ZICODIAN on 2015-04-29
[COLOR=#3E3E3E]Hi *

I have added acceleration control to spin. [https://github.com/wdbm/spin](https://github.com/wdbm/spin)[/COLOR]

---

### Post by xt-gr79 on 2015-05-12
Has anybody tried [this]("http://linrunner.de/en/tlp/docs/tlp-configuration.html") on thinkpad yoga S1? Is it worth trying?

---

### Post by ragtag on 2015-08-20
I got the ThinkPad Yoga a few days ago, and have installed Ubuntu 14.04 on it, but am having some issues with it.

Firstly, changing rotation or resolution, logs me out almost every time. This is the same if I use the options in the System Settings, or the spin.py script. It will rotate/change resolution, and then almost instantly revert back to what it had before, but messed up, and then log me out. The log output looks like this.

```

Aug 21 00:46:14 yoga mtp-probe: bus: 2, device: 9 was not an MTP device
Aug 21 00:46:21 yoga gnome-session[3755]: WARNING: Application 'compiz.desktop' killed by signal 11
Aug 21 00:46:21 yoga gnome-session[3755]: WARNING: App 'compiz.desktop' respawning too quickly
Aug 21 00:46:21 yoga gnome-session[3755]: CRITICAL: We failed, but the fail whale is dead. Sorry....

```

The same thing happens with a fresh user, and when booted from the Lived CD.

The second problem I'm having is that pressure is not very accurate. In both Gimp and MyPaint, it leaves blotches. This is most noticeable with an ink pen. I tried with my old tablet pen too, and got the same result. Plus, you have to apply quite a bit of pressure before it registers at all, which is kind of annoying (more than on my old tablet, and way more than on a Cintiq).

I'm almost tempted to 'dd' back the image I took of the Windows install it came with for comparison, just to rule out hardware problems. I didn't really test it much in Windows, before replacing it with Linux. :)

p.s. And does anyone have two finger scrolling working on the touch screen. Would be nice to have when in tablet mode.

---

### Post by darklordjohn on 2015-08-21
Hi ragtag, I had  the same problem - logout whenever the screen resolution and orientation changed. Seems like it's a newer screen than the other models and the drivers don't work in ubuntu 1404. What worked for me was to 

a) Install ubuntu 1504
b) manually update the kernel to 4.0
c) use these scripts: [https://github.com/admiralakber/thinkpad-yoga-scripts](https://github.com/admiralakber/thinkpad-yoga-scripts) (run systemctl enable instead of systemctl start if you want to always run these scripts on startup). The spin script did not work for me, it would always turn the screen the wrong way round in 'stand' mode.
d) I kept getting errors along the lines of: `maximum number of clients reached, cannot connect to X server', I fixed this by editing the file /opt/thinkpad-yoga-scripts/tablet/tablet-mode.sh to change the xbindkeys -f ... command to `xbindkeys -n -f ...', i.e. I added the -n option to xbindkeys. UPDATE: scrap the -n option, it didn't actually work, I needed to update /opt/thinkpad-yoga-scripts/yoga-tablet.service to set the variable Restart to `no'. Sorry for the confusion!
 
I then also needed to install the chrome-beta because text selection in chrome was broken. The only thing that does not seem to work right now is the projector button and automatic suspend when I close the lid. Hope that helped!

PS: Scrolling on the touch screen works in chrome once enabled as described in the first post of this thread. I can confirm that I need quite a bit pressure to make lines appear in Xournal or Krita - I find it still usable though and pressure sensitivity still works. Would be nice to fix this.

---

### Post by ragtag on 2015-08-25
Thanks for the information. Since 15.10, which comes with kernel 4 so should work out of the box, is just a couple of months away, I decided to restore Windows 10 on it for now. It also gives me a chance to figure out how it's meant to work, before I get everything up in Linux again. For instance, the issue with the pen pressure registering a bit late, is also present in Windows, so it's probably a hardware thing. I just tested it on my old HP TC4400, and it takes about the same pressure there too for a stroke to register. I think I've become spoiled by using Cintiq's and Intuos tablets, that register a stroke with just 1 gram of pressure. :)

I'll definitely be going back to Linux though. :)

---

### Post by mueller.pascal on 2015-09-03
It's really a pain in the ass to set it up. I wouldn't recommend buying it if you want to run Linux.

I have the pro Dock, which nearly works okay but: If I unplug it while running and plug it back in -> doesn't work, I have to log out and log in again. but then, maybe the screen is turned off. Then, all my settings of the panels might get lost. It's all very weird. How can I set it up properly? I want to plug and unplug as often as I want and in any situation and it all should work perfectly. It's annoying if it doesn't.

Also, I'm using Kubuntu 15.04 because most of the other desktop GUI's aren't useable at all. I can't stand Unity and most of the others. Here, touchscreen doesn't work. What do I have to install? I just want to scroll with one finger, resize with too. I don't rly care about the rest.

Also, the sensor-hub probably is still not working thus needing some scripts, which also is just a cheap hack and not very nice.

I think I'm going to sell the Yoga and buy me another machine, since I stopped writing via Hand on it anyway. Noticed, that paper is still the best. I even stopped editing PDF's with the pen, since it's just as good via mouse.

Sry, I'm a bit pissed since I'm trying to get everything set up properly... but I can't, too nooby probably.

---

### Post by ragtag on 2015-12-16
I thought I would add some additional info to this thread, even though I've yet to get everything working smoothly on the Yoga. I'm running Ubuntu 15.10, and on it most things are working, but not all.

**Installation**
I needed to disable Secure boot, in BIOS to get it to install correctly, but otherwise it worked fine. I installed it along side Win10, without any major problems.

**Special Keys**
Most of the special keys are working, including keyboard light, volume (both on the keyboard, and on the side of the machine), mute, brightness, wifi. F12 opens the Home folder.

The following keys are not working: F7 (presentation mode), F9 (settings), F10 (search) and F11 (switch desktop).

**Touch Screen**
The touch screen just works. I installed Google Chrome, as it has better touch support. Touch works nicely in Evince too. Though, there is no two finger scrolling.

**Wacom Pen**
The Wacom pen works out of the box in Gimp (after enabling it in Gimp), Krita and MyPaint, though calibration is a bit wonky. It seems to get more offset, each time you calibrate. Running "xsetwacom --set 10 ResetArea", rests the calibration, but I need to look into this further, to figure out what is going on.

I'm also not fully happy with the pen. The one that comes with the Yoga, is too skinny, so I got the Bamboo Feel pen. It seems to register with less pressure, which is great, but I'm not happy with the pressure curve (both under Windows and Linux). It seems to lack the mid range. It's seems to go very quickly from 10% pressure to 90% pressure, so it's hard to work in the mid range. I've tried adjusting it, but not found a result I'm happy with. For comparison, I find the pressure curve on my Cintiq 13HD to be much nicer, it detects with almost no pressure, and has an even pressure range from no-pressure to 100% pressure.

**Power Management**
I ran the following, and it did wonders for the battery life. Now it's the same as under Windows 10, around 7 or more hours if not under too heavy use.

  sudo apt-get install powertop tlp tlp-rdw tp-smapi-* acpi-call-dkms
  sudo tlp start

**Tablet Mode**
This is where things get painful. I made a fork of wdbm's spin tool, to try and get everything working as smoothly as under Windows. You can find it here [https://github.com/ragtag/spin/tree/yoga12-2nd-gen](https://github.com/ragtag/spin/tree/yoga12-2nd-gen)  (note, it's very much work in progress, and not complete yet). I updated the code that detects the orientation of the tablet, to make it more stable. But there are other issues.

The Rotate Lock key on the side of the screen is detectable through ACPI, but registers two presses each time you press it, and presses Super-o, so the Unity Launcher pops up when you press it....wich is kind of annoying if you just want to use it to toggle rotation locking.

Secondly, I've yet to figure out how to correctly detect when it goes from tablet/tent mode to laptop mode. When I'm reading from the accelorometer, the screen position detector triggers twice, once when entering/leaving tent mode and once when entering/leaving tablet mode, but with the same signal. This means I have no way of knowing if the laptop went from tent mode to tablet mode, or tent mode to laptop mode.  When I'm not reading from the accelorometer, it only registers, when leaving/entering tablet mode, but I want to get full functionality...so really want to get this working.

I've found that the screen position detectors outputs unknown keycodes e058 and e059. The e059 is only triggered when going from tent to laptop mode, which is what I need. The only problem is, I've yet to figure out a way to get these keycodes to trigger a script, so I can do something usefull with them. See [http://ubuntuforums.org/showthread.php?t=2304980&highlight=thinkpad+yoga+12](http://ubuntuforums.org/showthread.php?t=2304980&highlight=thinkpad+yoga+12) 

Thirdly, I've found some issues with switching the screen rotation too quickly. When the screen is rotated, the touch interface gets disabled for a second or two. I've added support for this in my version of spin.py, to wait for the touch interface to respond, before attempting to rotate it. What is worse, is that sometimes...seemingly at random...I get gconf/dconf error when I rotate the screen. I'm not exactly sure what causes this.

I did a hacky GUI workaround for the screen rotation, so you could do it manually, but I don't really like it, and would like to get everything working smoothly as it does under Win10....though I've found a couple of small bugs there too.

Anyways....I'll still try to figure out the tablet/laptop mode issues, and the calibration stuff, and will post any solutions I find here...and probably make a long post on my blog about how to set everything up. But first I need to get to a point where I've got everything working, so any help or suggestions are appreciated. :D

p.s. If you use Spotify under Ubuntu 15.10, you need libcrypto.11.so, which you can get from earlier versions of Ubuntu.

---

### Post by ragtag on 2015-12-23
A big update here. ):P

I've got my ThinkPad Yoga 12 more or less working the way it should. I forked spin.py, and did a lot of changes, to get it working almost as smoothly as under Windows. You can find my fork of spin.py here [https://github.com/ragtag/spin](https://github.com/ragtag/spin)

It includes:
- Palm rejection when using the stylus
- Automatic screen rotation, when in tablet mode, using the built in accelorometer
- Rotation lock, to disable the automatic screen rotation when needed
- On screen icons for toggling between laptop and tablet mode, which can be put in the Unity launcher for easy access

I've not tested it extensively yet, but it seems to work fine so far.

Please let me know if you find any bugs with it, or are having problems with using it.

---

### Post by ragtag on 2015-12-25
I've written a longish blogpost about how to configure the ThinkPad Yoga 12, under Ubuntu 15.10 here. [http://ragnarb.com/configuring-thinkpad-yoga-12-with-ubuntu-15-10/]("http://ragnarb.com/configuring-thinkpad-yoga-12-with-ubuntu-15-10/")

I hope you find it usefull.

---

### Post by e7ail on 2015-12-29
I've just joined the forums to say that you guys have inspired me to give Ubuntu a go on my TPY15". I've had win 10 running for a bit, and while it's "okay", I've been wanting to try something different. I am sure you'll see me in here with many questions. Thanks for the inspiration!

---

### Post by nikola8 on 2016-01-18
Hi there, just another person switched the windows to linux (ubuntu 15.10). I saw ragtag installed powertop and tp smapi and acpi call, I looked at the tlp stats and saw that the smapi was disabled, then looked at the smapi support devices page and saw that the thinkpad yoga is not one of them. So I've ignored them, has anyone seen any benefit of smapi and if so, how you managed to run it. Also I would like to share my experience with the bluetooth module. As I use the laptop connected to an external monitor sometimes I want to login with BT keyboard and mouse, but the Thinkpad bluetooth keyboard and the microsoft designer mouse were not able to connect at first. 
Altough in launchapd is said that bluez-5.35 solves the problem with bluetooth v4.0 devices it really didn't work out of the box for me. 
with help from askubuntu user's answer: 

[LIST=1]
[*]Comment out the only non-commented line in file /lib/udev/rules.d/50-bluetooth-hci-auto-poweron.rules
[*]Uncomment lines [Policy] and AutoEnable=true (originaly there is =false, change it) in /etc/bluetooth/main.conf
[*]Reboot
[*]Search and pair your mouse. If cursor is not moving, try pairing again.
[/LIST]
commenting the line in the file [COLOR=#111111][FONT=Ubuntu]50-bluetooth-hci-auto-poweron.rules , disables the bluetooth at boot. So, if you need as me to log in via bluetooth keyboard you would want to uncomment it once you've connected the device. Then after reboot/shutdown the keyboard connects and I am able to log in. 

Also want to point out that I also got non working fans at some point. As it happened before on windows, just updated the bios, now running 1.2 with no problems (for now). I used a usb stick to do it.

For the note taking, I use xournal as it allows me to take handwritten notes, which is really important to me. 


Will post here another problems that I encounter. [/FONT][/COLOR]

---

### Post by cheflo on 2016-01-27
Ah why have I not gotten notifications of all the interesting updates here?? Thanks for all the improvements to spin @ragtag, it is easier to run palm rejection without a GUI now, which is my main use of it. I am on Arch with Gnome now and the experience is pretty much the same as on Ubuntu. For spin, I had to remove "stylus" from the end of line 393 as the name of the pen in xinput is "Wacom ISDv4 EC Pen" for me. I can also not get the autorotation to work, but I don't mind that (I think it was something with acpi display_position_change being an unknwon command, your github fork doesn't allow opening new issues so I couldn't comment there).

For the pressure curves, I agree that the default curve in gimp works better with an external pen (I have a bamboo with soft tip), but I find that it works ok with the included stylus also after adjusting the curve to a more sigmoid shape. Although, keep in mind that I only use it for note-taking and can barely draw stick figures, so you probably have much higher standards than I do. For what it is worth, I am including a couple of screenshots of my setup.

Included pen:
[ATTACH=CONFIG]266980[/ATTACH]

Bamboo:
[ATTACH=CONFIG]266979[/ATTACH]

---

### Post by cheflo on 2016-01-27
Another user reported the [same acpi problem running Ubuntu]("https://github.com/wdbm/spin/issues/8#issuecomment-175769277"). The error message is

```

[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode unknown[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode unknown[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Triggered acpi_listen with unknwon mode display_position_change[/FONT][/COLOR]
```

---

### Post by Rob_Johnson on 2016-02-10
Hi.  How did you go about installing this on Arch?  I've got Antergos Gnome and Manjaro Xfce installs to play with!  As well as Mint Xfce.  I found the same with the stylus naming in Antergos, but not in Manjaro, with another set of scripts.  For the record, autorotate worked with those:  [https://github.com/admiralakber/thinkpad-yoga-scripts](https://github.com/admiralakber/thinkpad-yoga-scripts)
(Actually, maybe it didn't for the tent/tablet change, will check)

> **cheflo said:**
>  I am on Arch with Gnome now and the experience is pretty much the same as on Ubuntu. For spin, I had to remove "stylus" from the end of line 393 as the name of the pen in xinput is "Wacom ISDv4 EC Pen" for me. I can also not get the autorotation to work, but I don't mind that (I think it was something with acpi display_position_change being an unknwon command, your github fork doesn't allow opening new issues so I couldn't comment there).


---

### Post by cheflo on 2016-02-10
Hey, I am using Antegros as well! I view it almost as an Arch installer, since all the repos are the normal Arch ones + one extra from the Antegros team, unlike Manjora where they have their own repos (which I actually think is advantageous due to the lower probability of breaking from updates, but I had some troubles with dual boot in Manjaro and I prefer Gnome to KDE). Antegros has been working smoothly since I changed lightdm for gdm and installed a few essentials packages for an improved desktop experience (Put Windows gnome extensions, jumpapp application launcher and fixed the font rendering as described in a post in the Manjaro forum).

Come to think about it, there is one problem with the touchscreen - If I use the pen or the mouse in combination with touching the screen at the same time, the OS will freeze for several seconds. I barely use touch, so I just turn it off and use either the pen or the mouse. Impeccable "palm rejection" is a nice side effect =) I never got spin to work perfectly, and I don't use it right now, but the palm rejection worked with the tweaks I listed earlier, although it outputs a few error messages.

---

### Post by gingepaton on 2016-04-16
> **ragtag said:**
> I've written a longish blogpost about how to configure the ThinkPad Yoga 12, under Ubuntu 15.10 here. [http://ragnarb.com/configuring-thinkpad-yoga-12-with-ubuntu-15-10/](http://ragnarb.com/configuring-thinkpad-yoga-12-with-ubuntu-15-10/)

I hope you find it usefull.

Thank you very much, I have found this to be very helpful indeed.
I love Lenovo's X series, I have had 6 of them. I thought it was time to change things up and I switched to the S2 Yoga 12 and without this post I would have lost my beloved Ubuntu.

---

### Post by cogito.ergo.lulz on 2016-06-27
Hi, I am considering buying a 2nd gen ThinkPad yoga (i5, 8GB RAM) to be used as a Linux-only machine. Before buying I'd like to know what are the issues (if any) related to the hardware support. Before this laptop, I tried with an [Asus X205TA]("http://ubuntuforums.org/showthread.php?t=2254322&highlight=asus+x205ta") which is still quite problematic (no sound/random freezes/bluetooth not working), so I feel I have to be pretty cautious before buying a new laptop.
By reading on the forums looks everything is OK with this one, am I right?
Both the basic stuff (Video/audio/wireless/sleep/hibernate/power management) and laptop-specific ones (touchscreen/digitizer/tablet mode) are working?

---

