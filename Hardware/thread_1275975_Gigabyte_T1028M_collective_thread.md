---
title: "Gigabyte T1028M collective thread"
date: 2009-09-26
forum: Hardware
---

### Post by beke on 2009-09-26
There are currently three different threads about the Gigabyte T1028M in the forum. I thought it might be useful to have a unifying thread.

[CENTER]**Please help with any and all comments!!!**
and
**WARNING: I am not an expert -- you follow any advice at your own risk!!! -- make backups!!!**
[/CENTER]
Nuff said.

**Tested Ubuntu Version:**
Ubuntu Netbook Remix 9.10

**Problems:**
[LIST]
[*] **Problem: Touchpad not working.**
  **Solution:**
**9.04 / grub**: modify  /boot/grub/menu.lst by adding 'i8042.noloop=1' at the end of the line(s) starting with "linux" (containing the uuid of the root partition)
**9.10 / grub2**: modify /etc/defaults/grub and modify the "splash quiet" line by including 'i8042.noloop=1'. Afterwards run update-grub2.
You can **test this** by adding 'i8042.noloop=1' in the grub menu at boot.
(Thanks to [http://0x42.org/blog/archives/62-Ubuntu-auf-dem-Gigabyte-M912-Der-Touchscreen.html](http://0x42.org/blog/archives/62-Ubuntu-auf-dem-Gigabyte-M912-Der-Touchscreen.html) and [http://ubuntuforums.org/showthread.php?t=1230484](http://ubuntuforums.org/showthread.php?t=1230484) )

[*] **Problem: Touchscreen not working.**
**Solution:** Install xserver-xorg-input-evtouch. 
Some people (see comments) experience problems and/or severe stability issues especially with 9.04.
**Workarounds** include: 
(Doktor.Wahnsinn)  If your touchscreen still does not work, try activating the 'activate second mouse button on holding first' feature.
(beke) If an application (like Xournal) uses Xinput, deactivate the use of Xinput.
(ratiafak) Install the drivers from [eGalax]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm").

[*] **Problem: Touchscreen calibration unstable.**
**Solution:** Following [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/368135/comments/14](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/368135/comments/14) I use an fdi instead -- save it as a text file in /etc/hal/fdi/policy/SOMENAME.fdi

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
  <match key="info.product" contains="eGalax Inc. USB TouchController">
 <merge key="input.x11_driver" type="string">evtouch</merge>
 <merge key="input.x11_options.ReportingMode" type="string">Raw</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
 <merge key="input.x11_options.Emulate3Timeout" type="string">1</merge>
 <merge key="input.x11_options.SendCoreEvents" type="string">On</merge>
 <merge key="input.x11_options.MinX" type="string">0</merge>
 <merge key="input.x11_options.MinY" type="string">2</merge>
 <merge key="input.x11_options.MaxX" type="string">4096</merge>
 <merge key="input.x11_options.MaxY" type="string">4096</merge>
  </match>
</device>
</deviceinfo>

```

[*] **Problem: Webcam not working.**
**Solution:** Webcam works after reactivating the webcam using SmartManager in winXP.

[*] ** Problem: Connecting the power plug triggers suspend mode.**
**Solution:** None. Could be a regular bug, but I haven't found anything similar. Does anybody else experience this?

[*] ** Problem: Calibration is suddenly bad in the center (happens at random).** Sometimes triggered by rotation (but not always), sometimes by simply using the touchpad (or so it seems...)
**Solution:** None. Workaround: log off, restart X, reboot. Does anybody else experience this?


[*] **Problem: Wireless -- nm-applet crashes while connecting.**
**Solution:** Updating ubuntu using ethernet solved it for me.
[/LIST]



**Installation/Karmic/software related**

[LIST]
[*] **Netbook Launcher:** The touchscreen click is unable to start programs that are not in the "favorite" section. The problem seems to be that instead of a click a drag is registered. Dragging everything important to favourites is a workaround. Any hint would be great.

[*] **Rotating:** Works fine, but Netbook Launcher has problems in portrait orientation: In the section "system" the two subsections "preferences" and "administration" overlap.

[*] ** SmartManager:** A replacement for Gigabyte's "Smart Manager" for winXP would be nice. [WattOSpm]("http://ubuntuforums.org/showthread.php?t=1275975") could be a replacement, but I couldn't try it so far.

[*] **Installation** ran smoothly (except that (W)LAN connection did not work)

[*] **Post-Installation:** the first boot ended at root console claiming that the last time of mounting was in the future. One run of fschk per partition solved the problem; could be realted to encryption.
[/LIST]

Well, that's all for now. I hope this helps anyone thinking about installing ubuntu! So much works out of the box :P

---

### Post by Fecos on 2009-10-13
Hi beke!

Did you find something instead of "Smart Manager"?

---

### Post by beke on 2009-10-15
Hi Fecos, I haven't found anything -- so far I concentrated on checking progress of Karmic on it, which is coming along fine, but I'll update the post when I have some more time. 
Maybe we should open a new thread for this? It would be nice to have a GUI in general, and especially nice to be able to switch off the camera, which I don't seem to be able to under Ubuntu at all.

---

### Post by Doktor.Wahnsinn on 2009-10-15
Hello,

how do you deactivated the XInput support ?

greetings,

Doktor.Wahnsinn

---

### Post by beke on 2009-10-15
Hi Doc,
in my case, the only problematic application was Xournal -- which is where I deactivated Options->'Use Xinput' after which I haven't had a single crash.

I don't know if there is a general way. So checking each 'destabilizing' application for Xinput might be the way to go.

I might add however that I also installed the xorg-wacom-package at some point (which offers Xinput capabilities for wacom tablets), so uninstalling it might help, but that's for you to test...

---

### Post by Doktor.Wahnsinn on 2009-10-16
Hi beke,

i havent installed any kind of xournal or anything like this.

But some curious effect, thats let my touchscreen permanet ´life´ is activating the mouse-feature ´activate second button on holding first´ . 

After reboot this special feature doesn´t work anymore, but since this, my touchscreen not freezed anymore.. 

curios...so next step for me, is to activate the second button..

greetings

Doktor.Wahnsinn

---

### Post by beke on 2009-10-18
Doc,
that's weird. I use the "activate second button on holding first", too, but I never had that kind of issue. Are you using Karmic, too? Otherwise upgrading might be an option.
B.

---

### Post by ratiafak on 2009-10-23
Hi, I have T1028X and 9.04.
I have tried xserver-xorg-input-evtouch but if freezed even on desktop (with no application running). I have uninstalled it and tried _[eGalax]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")_ driver from [www.eeti.com.tw]("http://www.eeti.com.tw"). Beta installed without any problem. It has settings utility, which is the same as in W.XP, so calibration was easy. I just switched off right-click emulation and use the Mouse->Accessibility->Simulated Secondary Click.
I can also recommend gnome-randr-applet for rotating and onboard as working keyboard.

---

### Post by Petr Mach on 2009-10-30
> **beke said:**
> 
[LIST]
[*]**Warning!!!** for 9.10/grub2 this is a bad hack: running grub-update/grub2-update (i.e. each kernel update) will generate grub.cfg without this addition. For this reason grub.cfg is read only and you shouldn't alter it. I don't know how to convince grub2 to add this in a safe way. You can however test this hack by adding 'i8042.noloop=1' in the grub menu at boot.
[/LIST]
 
Safe way is edit /etc/defaults/grub and modify "splash quiet" line by including 'i8042.noloop=1'. After it run update-grub2.

---

### Post by beke on 2009-10-31
@ratiafak: Have you tried upgrading to 9.10?

@Petr: thanks! I will finally have time to update the post this weekend, so this really comes in handy!

---

### Post by beke on 2009-11-01
I finally had the time to update the thread. New features include: touchscreen workarounds, power-plug issues, possible SmartManager substitute, slight 'redesign'. Hope this helps.

---

### Post by Sparkarof on 2009-11-01
I installed UNR 9.10 yesterday - I must say I wasn't very happy at all at first. It seemed as if everything weren't just working as intended. For example, the new Software Centre seems intended for complete idiots and it actually takes longer to install software (more clicks) - and the first time I ran it I couldn't install anything because I had no "install button" at first, second time that button showed up.

I can confirm petr's advice for the touchpad works a charm!

I have also followed the advice with getting the touchscreen callibration to act more stabel with making the .fdi file - and I can confirm it works well.

I have some problems I would really appreciate help with:

1) I cannot get an on screen keyboard to pop up with the pressing of the hard button on the left hand side of the T1028 (the battery indicator button) - It might be a problem with onBoard. I selected onboard as the default onscreen keyboard in the assistive technologies window. And I set that hard button on the left to initiate onboard in the shortcuts application - but to no avail. Would love this to work.

2) I do not know how to emulate a right-click with the touch-screen, that would be really handy (it would be nice if a right click is initiated on a click-and-hold on the touchscreen). How to I do that?

3) It is extremely irritating that all applications in the Launcher interface (except for the favourites menu) is recognised as a click-and-drag when tapped on with the touchscreen. I know this has been mentioned earlier.

4) On more of a side-note, easystroke (gesturing app) does not want to record (or recognise) any 'strokes' - I tried this method also to initiate onBoard - didn't work.

We should keep this thread active and going and share our knowledge.

Thanks guys.

---

### Post by Sparkarof on 2009-11-01
I figured out how to use onscreen keyboard and the left-hand side hard button - I managed this with Cell-Writer and a custom command in the keyboard shortcuts application. 

Still  want to know how to right click with my stylus.

Just typed all this with the onscreen keyboard.

---

### Post by beke on 2009-11-02
@Sparkarof: nice "typing" ;)

The "right click on hold" should be in the system -> mouse -> accessibility -> "trigger secondary click..."

Thanks for the tip about getting the keyboard shortcut working for cellwriter.

---

### Post by Sparkarof on 2009-11-02
> **beke said:**
> @Spararof: nice "typing" ;)

The "right click on hold" should be in the system -> mouse -> accessibility -> "trigger secondary click..."

Thanks for the tip about getting the keyboard shortcut working for cellwriter.
@ beke: Thanks for the Right-click tip - it works a charm!

---

### Post by doonit on 2009-11-10
I must apologise for my ignorance, but what does this mean? I'm very new to Ubuntu.

"I figured out how to use onscreen keyboard and the left-hand side hard button - I managed this with Cell-Writer"

I installed Karmic on my T1028m a few days ago and I'm having a few problems:

I've calibrated my touchscreen a few times but find that it is only accurate in the middle of the screen. The closer I get to the edges the more inaccurate it gets.

If I go into System>Preferences>Mouse there are no options for the touchpad. I'd like to configure the multi-touch capabilities.

If I use any application that requires me to save (eg if I want to save a text doc) the "Save As" dialogue box takes about a minute to appear and then about another 5 minutes to become populated with options. I've found the same thing when trying to import music into Rhythmbox where the "Import From Folder" dialogue box really takes its time.

I don't know if this is a problem with my Netbook or with Koala. Any ideas?

---

### Post by beke on 2009-11-11
Hey doonit! To help you out, please give us some more info.

0) For key bindings check out the keyboard shortcuts in the system section of the UNR launcher. You can add new applications and bind them to the button.

1) Calibration. Have you tried either solution suggested in the main post, i.e., the fdi or the eGalax driver?

2) Touchpad configuration. I must admit I haven't tried anything fancy yet, so hopefully somebody else can help. Two finger scrolling works automatically on mine. What else are you missing? Are you sure that this is a touchpad, not an application issue? 

3) The "hanging" I haven't encountered, but I remember seeing this on another netbook. Back then it was an issue with the virtual resolution. Have you increased the virtual resolution (e.g. by setting up an external monitor)? Reversing this in /etc/X11/xorg.conf might be worth a try.

---

### Post by doonit on 2009-11-12
Hi beke. Sorry but I've been kinda busy. Played around last night again. Did the fdi thing from the beginning of this thread and that sorted out my screen calibration issue. Sweet!

For your point 2) above you are right, two finger scrolling works out the box but I was kinda hoping to get three finger gestures working as they did with XP. Really got used to 3 finger taps for right mouse clicks, three fingers left for back, right for forward, up for My Computer and down for move to different (minimised) running app. Mostly its the back gesture I want. Not very important but nice to have.

Your point 3). No. I havent changed the resolution since installing 9.10. Cant find a fix for the hanging on the forums anywhere. Its a real pain. Given time it usually un-hangs itself but patience is definitely needed.

I have another problem in that my netbook hibernates evrytime I plug in or unplug the battery charger. Seems someone else also has this problem but so far there doesnt seem to be a fix. After hibernating I need to do a restart to get wifi working.

---

### Post by beke on 2009-11-12
Hi doonit. Great to hear that the fdi helps.

@2) I guess I never used Windows on it :D, but we should investigate this.

@3) Just to check: I was speaking of the virtual(!) resolution of the X server, not the actual resolution used for the screen.

4) I was the one with the plug/unplug problem. I haven't found a fix yet, but I haven't had much time with my Gigabyte, so not enough incentive ;) 

5) I have another problem and was wondering if anybody else has this. I cannot access the external mic (below the screen). 
Has anybody else got this to work? Or is it a dummy? Windows doesn't seem to "see" it either.

---

### Post by Sparkarof on 2009-12-03
Hi, All is well with me and my T1028 if anyone was wondering. Can anyone tell my how to let the wireless to be enabled automatically on boot? I do not wish to press "Fn" and "F2" each time to get my wifi on - this is a netbook, and I want to use it for the "net" with my "wifi" at every boot.

---

### Post by beke on 2009-12-04
I second that -- does anybody know how to keep wireless on?

---

### Post by Fecos on 2009-12-04
Sparkarof, beke!

To keep the wireless on, you need to update the [BIOS]("http://www.gigabyte.com.tw/Support/Notebook/BIOS_Model.aspx?ProductID=3190#anchor_os").

The last update (2009/12/04) is solve it :)

Br.
Fecos

---

### Post by beke on 2009-12-04
Thanks Fecos! I'll try the BIOS upgrade asap.

---

### Post by NCLI on 2009-12-06
Maybe we should report all of this as one big bug?

---

### Post by Fecos on 2009-12-06
> **NCLI said:**
> My unit randomly crashes when using the touchscreen(evtouch). Anyone else?

Hi, use the eGalaxy's driver!

---

### Post by NCLI on 2009-12-06
> **Fecos said:**
> Hi, use the eGalaxy's driver!

I found that fix myself by actually reading the thread xD

Anyway, these bugs should all be reported. I've reported some of them already myself, but not all.

---

### Post by beke on 2009-12-07
NCLI: thanks for reporting the bugs! 
I guess I did expect to have more time to work on the thread (i.e. do proper bug reporting). (Un)fortunately, new job, less time. 
It'd be great if you could post links to your bugreports in this thread for completeness -- then other people can fill in the blanks without reporting everything twice.

---

### Post by elianto on 2009-12-08
Hello all,
with the intent to sum up and keep up with the latest updates, I want to report my personal experience with these problems to this helpfull thread:
> **beke said:**
> 
**Problems:**
[LIST]
[*] **Problem: Touchpad not working.**
  **Solution:**
**9.10 / grub2**: modify /etc/defaults/grub and modify the "splash quiet" line by including 'i8042.noloop=1'. Afterwards run update-grub2.
You can **test this** by adding 'i8042.noloop=1' in the grub menu at boot.
(Thanks to [http://0x42.org/blog/archives/62-Ubuntu-auf-dem-Gigabyte-M912-Der-Touchscreen.html](http://0x42.org/blog/archives/62-Ubuntu-auf-dem-Gigabyte-M912-Der-Touchscreen.html) and [http://ubuntuforums.org/showthread.php?t=1230484](http://ubuntuforums.org/showthread.php?t=1230484) )
[/LIST]


Thanks, this works for me, vote for this bug @ [https://bugs.launchpad.net/ubuntu/+bug/432984](https://bugs.launchpad.net/ubuntu/+bug/432984)

> **beke said:**
> 

[LIST]
[*] **Problem: Touchscreen not working.**
**Solution:** Install xserver-xorg-input-evtouch. 
Some people (see comments) experience problems and/or severe stability issues especially with 9.04
[/LIST]
[SIZE=2]AND[/SIZE]

[LIST]
[*]**Problem: Touchscreen calibration unstable.**
**Solution:** Following [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/368135/comments/14](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/368135/comments/14) I use an fdi instead -- save it as a text file in /etc/hal/fdi/policy/SOMENAME.fdi
[*]** Problem: Calibration is suddenly bad in the center (happens at random).** Sometimes triggered by rotation (but not always), sometimes by simply using the touchpad (or so it seems...)
[/LIST]


With this fdi and xserver-xorg-input-evtouch 0.8.8-0ubuntu6.1 it works without crashing any second but, as I wrote in launchpad, it's still slow in reacting to input and the calibration ALWAYS goes away when rotating.

> **beke said:**
> 
[LIST]
[*] **Problem: Webcam not working.**
[*]**Problem: Connecting the power plug triggers suspend mode.**
[*]**Problem: Wireless -- nm-applet crashes while connecting.**
[*]**[B]Netbook Launcher:** The touchscreen click is unable to start programs[/B]
[/LIST]
[INDENT][https://bugs.launchpad.net/netbook-remix-launcher/+bug/434502](https://bugs.launchpad.net/netbook-remix-launcher/+bug/434502) 
[/INDENT]
[LIST]
[*]**[B]Rotating in netbook menus problems...**[/B]
[*]**[B][B][B]Installation/**Post-Installation...[/B][/B][/B]
[*]**[B][B][B] SmartManager..**[/B][/B][/B]
[/LIST]


I didn't had these problems or I avoided using kde

**ADDITIONALY:**
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/432939](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/432939)
the Mic on the screen doesn't work and/or there is no way to command it on mixer
Anyone experience this/found a solution?

---

### Post by doonit on 2009-12-24
Since my last posts here I installed 9.10 Netbook Remix over the desktop version that I had running because that was just TOO full of bugs to manage. UNR has proven to be a lot more stable in a lot of ways except that now I absolutely can't get the touchpad to work. I've been on every forum and I've tried every bit of advice but still nothing. It's been a month now of exhaustive search and I'm reaching the end if my tether. What's the good of a netbook if I need to be carrying periferals like a usb mouse around. One of the big attractions of my T1028 was the MULTI touch touchpad when I bought it.

So, if I go into Preferences>Mouse Preferences there is no tab for Touchpad, or any other indication or option for Touchpad. There is no way to activate Touchpad. I have all the latest Synaptic software installed.

Please note: I am NO linux pro!!!

---

### Post by beke on 2009-12-27
Doonit, two questions.
1) Is your touchpad working at all? Does it do two-finger scrolling and three-finger-right-click? (it should)
2) Would the application you use actually support multitouch? This seems to be the bigger issue from what I read elsewhere.

Speaking of which, unfortunately (or fortunately imho) the answer seems to be the typical open source answer: it's possible, but not yet implemented automagically. If you feel bold look up [http://www.ibm.com/developerworks/opensource/library/os-touchpad/?ca=dgr-lnxw07FingerLinux](http://www.ibm.com/developerworks/opensource/library/os-touchpad/?ca=dgr-lnxw07FingerLinux) . Be sure to let us know if this worked for you.

What can be done with the synaptics driver at the moment is documented at [http://w1.894.telia.com/~u89404340/touchpad/](http://w1.894.telia.com/~u89404340/touchpad/) and in the man page (or e.g. [http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics) ).

In general, you might want to start by reading [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) . Maybe installing one of the GUIs will help you, maybe running one of the daemons will. Hope this helps a little.

---

### Post by ein.selbst on 2010-02-06
**"Problem: Connecting the power plug triggers suspend mode.**
**Solution:** None. Could be a regular bug, but I haven't found anything similar. Does anybody else experience this?"

For some reason, the pluging seems to trigger the closing of the lid (screen). If one changes the energy settings to just switch of screenlight, it only does that when pluging.
To bad there is no "Do nothing" option.

Best,
Sly.

---

### Post by beke on 2010-02-07
@Sly Thanks! That's a decent workaround. Personally, I switched to Kubuntu Netbook Remix -- much better interface for my tast and it's KDE4...

In particular, this problem with the power plug does not occur with KDE -- so it's probably a gnome problem.

Has anybody got the mic in the display to work? I can't  :( -- I hope it's not a defect of my t1028...

---

### Post by ein.selbst on 2010-02-19
I wasn't able to get the mic working under ubuntu 9.10.

I tried a lot of things, but not all and not in all combinations, from these sites:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

[http://jadmadi.net/blog/2007/12/27/ubuntu-gutsy-skype-microphone/](http://jadmadi.net/blog/2007/12/27/ubuntu-gutsy-skype-microphone/)

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)


It is working fine under windows.

I added myself to the bug-affected:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/432939](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/432939)

best, sly.

---

### Post by ein.selbst on 2010-02-19
I would like to know, if someone tried to use the ExpressCard Slot for a SSD with os on it.
There is e.g. this available:

[http://www.amazon.de/Verbatim-SSD-Express-Speicherkarte-32/dp/B0029SAMUO/ref=sr_1_1?ie=UTF8&s=ce-de&qid=1266573240&sr=8-1](http://www.amazon.de/Verbatim-SSD-Express-Speicherkarte-32/dp/B0029SAMUO/ref=sr_1_1?ie=UTF8&s=ce-de&qid=1266573240&sr=8-1)


I tried latetly installing a crunchbang on a 2GB MicroSD and it is working from within the cardreader slot, however it is a bit slow (it's not a SDHC card) and I don't like that it is not completly inside the chassis,
so I would prefer an ExpressCard.

*Update*: Tried the Verbatim ExpressCard SSD. 
My T1028 does not start, when the card is included. I have the newest firmware (which fixed wlan always off). Changing Bios settings doesn't bring success. 
Also the slot is to short to eat the whole card. :(
Gave it back.
However, there is another one which may work better and maybe I'll try it. If someone is interested let me know, so I update here.

---

### Post by beke on 2010-04-22
I just upgraded to 10.04. Upgrade went smoothly (and KNR is much sleeker), but the touchscreen is not working at all (always jumps to top right corner). 

Has anybody else upgraded yet?

I'll post any progress.

---

### Post by nsk7even on 2010-05-02
Same for me after upgrade to Lucid (but it's jumping to the left for me :D ) ... did you made any progress?

I encountered the error "XLoadQueryFont: failed loading font '*freemono*'" when trying to start "/usr/lib/xf86-input-evtouch/ev_calibrate" manually.

And the following when trying to start "/usr/lib/xf86-input-evtouch/calibrate.sh" manually:
Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready.

Wasn't HAL replaced in Lucid?

---

### Post by beke on 2010-05-02
nsk7even: No progress on my part. I think this is it [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/546487](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/546487) 

Yes, I believe HAL has been replaced. I don't know how to try something manually, i.e., using these new xorg.conf.d files -- could be related to [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/242590](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/242590) but I don't get it. Trying around got me in trouble (had to go into recovery mode to remove my conf.d )

So we should add to the bug comment since it's only considered low...


///////
Update: Reading up on the above bug I reported this as new -- [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/573822](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/573822)

Update2: nsk7even: On second thoughts I don't get anything about HAL though (see my bug report). Can you check if we have the same bug?

---

### Post by w1tw0lf on 2010-05-05
> **beke said:**
> I just upgraded to 10.04. Upgrade went smoothly (and KNR is much sleeker), but the touchscreen is not working at all (always jumps to top right corner). 
 
Has anybody else upgraded yet?
 
I'll post any progress.
 
 
Is your wireless working on knr ? worked on unr but cant seem to pick up a wireless network on knr.

---

### Post by beke on 2010-05-05
w1tw0lf: Networkig works fine for me -- well, as fine as knetworkmanager does. Sometimes it does not connect in which case it often helps me to switch to nm-applet to connect and switch back.

---

### Post by nsk7even on 2010-05-07
beke, to the first bug you mentioned I am already registered. I also added me to your new bug. (I am "Nicolas" in launchpad)

Meanwhile I tried generic eGalax drivers ... but they did not worked as well! Maybe I did something wrong (e. g. I disabled the modules "touchscreen" and "usb_hid" as adviced by the installer).

Additionally I deactivated the touchscreen part in /usr/lib/X11/xorg.conf.d/05-evdev.conf ... but nothing helped.

Many combinations remained untestet, so I will proceed at this weekend if I find the time; more updates soon. ;)

---

### Post by nsk7even on 2010-05-10
OK, first update:
Module "usbtouchscreen" seems to work best, but until now I did not managed to calibrate.

My steps:
- Uninstall of xserver-xorg-input-evtouch
- Install of libts-bin (because of ts_calibrate)
- Blacklisted module usbhid from loading (sudo echo usbhid >> /etc/modprobe.d/blacklist.conf)

- Then I tried ts_calibrate:
```
nsk@mini-n:~$ sudo su
[sudo] password for nsk: 
root@mini-n:/home/nsk# ll /dev/input/by-id/
insgesamt 0
lrwxrwxrwx 1 root root 9 2010-05-11 01:31 usb-eGalax_Inc._USB_TouchController-event-if00 -> ../event7
root@mini-n:/home/nsk# export TSLIB_TSDEVICE=/dev/input/event7
root@mini-n:/home/nsk# ts_calibrate 
xres = 1366, yres = 768
selected device is not a touchscreen I understand
Took 4 samples...
Top left : X = -538375268 Y = 16069774
Took 4 samples...
Top right : X = -538375268 Y = 16069774
Took 4 samples...
Bot right : X = -538375268 Y = 16069774
Took 4 samples...
Bot left : X = -538375268 Y = 16069774
Took 4 samples...
Center : X = -538375268 Y = 16069774
-0.215772 0.003475 0.116473
1.312756 -0.002532 -0.084810
Calibration constants: -14140 227 7633 86032 -165 -5558 65536 
root@mini-n:/home/nsk#

```
It blames my touchscreen of not being a touchscreen!

...now I have to go to bed


//Edit: Ah, one thing I forgot: I discovered /etc/ts.conf ... interesting file, maybe it is possible to manually adjust the touchscreen there.

Question to the others:
I have problems with the mousepointer, after most logons it constantly shows the waiting cursor - sometimes not. It has something to do with the touchscreen stuff I am sure about that. S. o. else such behaviour?

---

### Post by beke on 2010-05-11
nsk7even: I tried your method without success. Could you give more details? 

Btw, I do not have the 'waiting cursor' phenomenon (using KDE or Gnome).

---

### Post by nsk7even on 2010-05-12
Yes of course - it was late last time when I wrote the last posting.. ;)


I will describe as much as I remember what I have done:

1.) In syslog and/or eGalax driver installation instructions I found out that the kernel modules usbtouchscreen and usbhid are responsible for registering the touchscreen as input device

2.) I wondered if they would interfere with each other

3.) eGalax driver installation instructions gives the description on how to exclude kernel modules from loading at bootup (/etc/modprobe.d/blacklist.conf)
And this works ... compare syslog at/after bootup to see different initialization of the touchscreen to verify

4.) With including usbhid and usbtouchscreen into blacklist.conf I tried every possible combination of those modules and xserver-xorg-input-evtouch
The only combinations I did not test were those with eGalax drivers because they explicitly tell to deactivate the modules

Just to be as clear as possible, I tried:
a) usbtouchscreen alone
b) usbhid alone
c) usbtouchscreen & usbhid
and additionally all of the above together with xserver-xorg-input-evtouch

Those were the results:
a) touching the screen places mouse pointer "somewhere" else => different positions on different touches, but at least the mouse pointer did not jump to the corners or edges
b) touching the screen places mouse pointer exactly in the left upper corner => no differences, everytime the corner
*) I can't remember the exact differences of c) to the combinations with xserver-xorg-input-evtouch - but every other combinations resulted in worse behaviour than a)
E. g. placing the mouse pointer at the bottom of the screen, but on different x-positions when touching different places on the screen

5.) So method a) worked best, to sum up xserver-xorg-input-evtouch was deinstalled (I don't know if it made a difference), but more important usbhid was blacklisted from loading

6.) Then I searched for a calibration tool and found ts_calibrate which sits in package libts-bin => installed

7.) ts_calibrate command was available then (together with some other ts_-tools) but none of them worked and quitted with an error message

8.) www and man came up with the environment variable TSLIB_TSDEVICE to set if the device is not recognised by ts_-tools automatically

9.) Either in syslog at initializing the touchscreen or in /dev/input/by-id one can find on which /dev/input/eventX the touchscreen is registered

10.) Store this path to TSLIB_TSDEVICE but do this as root because we need root priviledges for executing ts_calibrate and sudo does not see environment variables stored for the normal user

11.) Then ts_calibrate throws those coordinates and tries to convince our touchscreen of not being a touchscreen

At this stept I went to sleep last time and here I will try to proceed next time (maybe tomorrow)...


As not being a Linux crack, everyone feel free to point me to mistakes or someting like that .... it feels of being nanometers away from the solution!

---

### Post by beke on 2010-05-17
nsk7even: thanks for the detailed info. Unfortunately, I am travelling without my netbook, so my own tests will have to wait.

---

### Post by nsk7even on 2010-05-17
Yeah .. the time went by and I did not managed to proceed with that as well. But I will update any progress here.

---

### Post by leunvcy on 2010-05-26
Have a read over here for the touchscreen, somebody has done it.

[http://ubuntuforums.org/showthread.php?t=1478877](http://ubuntuforums.org/showthread.php?t=1478877)

edit: By the way I have tried and it worked for me, somehow, on a T1028X.

---

### Post by 11zac11 on 2010-06-02
> **leunvcy said:**
> Have a read over here for the touchscreen, somebody has done it.

[http://ubuntuforums.org/showthread.php?t=1478877](http://ubuntuforums.org/showthread.php?t=1478877)

edit: By the way I have tried and it worked for me, somehow, on a T1028X.

How did you get this to work as i cant seem to do it?

---

### Post by nsk7even on 2010-06-02
Ah I forgot to reply since I tried this as well and it did not work for me as well!

I have noticed that even pressing on the exact same position on the touchscreen places the pointer to different locations ... understandable that the calibration tool is unable to gather correct values then.

Anyone an idea what could cause this behaviour?
There is a good possibility that I caused this by installing/configuring around in the system, therefore I reverted everything I can remember. But until now this "jumping" stays the same.

---

### Post by leunvcy on 2010-06-03
> **11zac11 said:**
> How did you get this to work as i cant seem to do it?

Actually after a few days of using it I can conclude that I experience the same effect as this person below, from the thread I have referred to.   I am still looking into it.   Not sure why I can set up the touchscreen on my DIY EEE701 with ease but not this one.

> **cywhale said:**
> Hmmm...
after some days I must correct my last post - the touchscreen seems to  work randomly - sometimes from first login after boot, sometimes not,  sometimes it stops working after some time again... :(

With the kernel option mentioned above this also occurs using evdev only  (no usbtouchscreen module needed)... :(

---

### Post by nsk7even on 2010-06-03
haaaach ... I am thinking about downgrading to Karmic

---

### Post by 11zac11 on 2010-06-04
> **nsk7even said:**
> haaaach ... I am thinking about downgrading to Karmic

hehe yeah i have started to think the same way.....but i dont want to really wipe and do a clean install :/

---

### Post by leunvcy on 2010-06-04
Give this one a try before giving up all hopes.  it worked on my used* and clean** Lucid install for the past few hours and a few reboots for each used and clean Lucid install.

I have done 2 things straight from installation, before halt the live CD, to get the touchpad and touchscreen both working.

added "i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40" to "/boot/grub/grub.cfg" at the end of the linux line

and black listed "usbtouchscreen" in "/etc/modprobe.d/blacklist.conf"

I don't see why it wouldn't work for used install.  I would recommend to change "/etc/default/grub" and do "sudo update-grub" instead of changing "/boot/grub/grub.cfg" directly.

* It worked on my previous used Lucid install but I did a clean install to make sure it works not because something else I did.

**Clean as in formatted partitions, I still left OEM Win7, Win7 recover and Win7 bootloader, only asked Win7 bootloader to point to grub2 in the formatted partition.

---

### Post by Emperor Jake on 2010-06-24
OK, I just got a t1028c, the touchpad works perfectly, thanks...
But I can't get the touchscreen to work. It just jumps around erratically as described in previous posts. I have tried everything, but nothing works. Can somebody give me a straightforward instruction on how to make it work? (it's UNE 10.04)
Thanks, 
Jake

(edit) Woohoo! I got it working by following the above instructions again, and REMOVING the eGalx driver!
Thanks!

---

### Post by aurilliance on 2010-06-26
Hi all,

I have been following this thread for a while, but this is my first post. @leunvcy your tips worked a charm getting my touchscreen working again! I have a t1028x with Ubuntu Netbook Edition 9.10 upgraded to 10.04, and then hacked back to a desktop-looking system.

Thanks for the fix - really appreciate it!

---

### Post by nsk7even on 2010-06-26
Oh yess!!!

Before trying I was sure to have tested this combination as well, but obviously not! Now it works for me as well!

THank you leunvcy for summarising those steps!

Remark:
Even blacklisting usbtouchscreen in /etc/modprobe.d/blacklist.conf will load this module, if it is listed in /etc/modules

//Edit: My permanent waiting cursor stays the same. So this has to be another issue, not related to the touchscreen.

---

### Post by Emperor Jake on 2010-06-27
How can nobody be having trouble with the wifi?
Please tell me what you did to make it work. 
My wifi works only sporadically... and even then I have to activate it first (as described in previous posts) But I've tried madwifi (which didn't work) and ndiswrapper (which only works 20% of the time.

THanks,
Jake

---

### Post by akhe on 2010-06-27
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX


HEY MEN UPDATE YOUR THREAD 

YOU HAVE BUG IN LINE **9.10 / grub2**: modify /etc/defaults/grub and modify the "splash  quiet" line by including 'i8042.noloop=1'. Afterwards run update-grub2.

THERE NEED TO BE  /etc/default/grub - not that "DEFAULTS" !!!!!!!):P!!!!!!!!

on T1028 WORK NOW !!!!!!!!!!!!!

thanks :guitar:


here is your original:
**Problem: Touchpad not working.**
  **Solution:**
**9.04 / grub**: modify  /boot/grub/menu.lst by adding  'i8042.noloop=1' at the end of the line(s) starting with "linux"  (containing the uuid of the root partition)
**9.10 / grub2**: modify /etc/defaults/grub and modify the "splash  quiet" line by including 'i8042.noloop=1'. Afterwards run update-grub2.
You can **test this** by adding 'i8042.noloop=1' in the grub menu at  boot.
(Thanks to [http://0x42.org/blog/archives/62-Ubu...uchscreen.html]("http://0x42.org/blog/archives/62-Ubuntu-auf-dem-Gigabyte-M912-Der-Touchscreen.html")  and [http://ubuntuforums.org/showthread.php?t=1230484](http://ubuntuforums.org/showthread.php?t=1230484) )

---

### Post by Greya on 2010-08-30
My pc is hot while in linux even without anything started. How to fix it? In default windows 7 it is quiet and cold.

---

### Post by nsk7even on 2010-08-30
Do you have this "mouse  pointer always shows the waiting icon"-problem also?

I still have not solved this (and sometimes are encountering this on my main pc as well!).
And I can imagine that there is some background process doing silly things which turn the mouse pointer into waiting state and maybe increase cpu load.
Sometimes when shutting down I have an unknown process not responding and maybe this has something to do with this... but because it is an "unknown process" I don't know how to debug this further.

---

### Post by sam.crowther on 2010-12-06
@leunvcy, Thanks, works on T1028X

got everything running, told my Dad (the other *unix geek in the family) that I finally got it going rebooted; it didn't work.

missed the blackilst usbtouchscreen. << did that works now.

(anyone find the touch pad actually seems better in 10.04 than Win7?)

---

### Post by new_acp on 2011-01-29
sorry if this is the wrong place to ask this, but I just bought a Gigabyte T1028 TouchNote off of Amazon, was brand new, and I got it today. and well I let it fully charge ect and when it had charge all the way I turned it on and set it up ect, and then when I got to the home screen after it turned on all the way.


When I hit a key like a letter or whatever it shuts down, why does it do that. Another thing is that some times when I hit the power button it doesnt want to turn on, the LED lights come on but the computer doesnt turn on as it should.


Any ideas to what is going on and how to fix this please?

---

### Post by ivzave on 2011-11-30
Anyone still using this notebook and wishing SmartManager button (hardware button on the left side) to work please contact me. I've got it to work on my device (T1005) and there's great chance it will be working on T1028.

---

