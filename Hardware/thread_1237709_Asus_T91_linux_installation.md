---
title: "Asus T91 linux installation"
date: 2009-08-11
forum: Hardware
---

### Post by proverbs308 on 2009-08-11
I have been considering buying the T91 but was wondering if anyone has successfully installed linux on it.  If I bought it would the touchscreen work or would I be stuck with Windows?

---

### Post by rscasas on 2009-08-14
You can check eeeuser forums.
Also I have found this blog [http://linux-t91.blogspot.com/](http://linux-t91.blogspot.com/)

---

### Post by Mizukusai on 2009-08-20
Installed Moblin successfully but failed to boot it.
Installed Ubuntu Jaunty successfully. Needed to install a few additional packages. There is still a few issue. The bigger one is a annoying habit  : it freezes near every 20 minutes.

---

### Post by moocow1452 on 2009-08-21
From what I heard, there has been some success with it, but unless you really want to muck in the drivers, it's not recommended for end users.  But that's Linux for you...

@Mizukusai: What works and what doesn't with the T91? I heard that wireless was possible, but a hassle. I've also heard rumors of multitouch, but squat about the "rotate" feature.

---

### Post by Leed on 2009-08-27
Got it up and running on my new T91, it's all a bit slow at first, doesn't find the correct display and wireless drivers by default, but now I have it running real good and fast thanks to a friendly website. 

[http://www.hilbig.id.au/t91/index.html]("http://www.hilbig.id.au/t91/index.html")

--edit, to keep things were we can find them
**Wireless**
-Activate Backport repositories either in Synaptic or by removing the # in /etc/apt/sources.list
-sudo apt-get update
-sudo apt-get install linux-backports-modules-jaunty
-reboot

**Graphics Driver**
-add to /etc/apt/sources.list
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
-sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
-sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware

..and this (on ever kernel update)
-sudo apt-get install psb-kernel-source
-sudo apt-get install psb-kernel-source

--end edit

I'm still looking for a way to get the webcam working

---

### Post by Mizukusai on 2009-08-28
What does not work : 


[LIST]
[*]Compiz (Never mind. I'm using netbook remix)
[*]The "rotate" button below the screen. Actually, maybe it works but i don't know how to catch it.
[*]stability. The OS freezes often, randomly.
[*]Moblin does not boot as all. But Ubuntu does.
[*]the graphic driver perfs are bad
[*]webcom is cheese. But ok in Skype (i heard)
[/LIST]
What does work : everything else 

[LIST]
[*]touchscreen
[*]easystroke (great soft !!!)
[*]rotate screen from command-line (and so from easystroke actions as well)
[*]sound
[*]network
[/LIST]

Here are some touchscreen softwares, I have tested so far :

[LIST]
[*]gournal
[*]cellwriter
[*]easystroke (but adding exceptions fails: :()
[*]The gimp (I know it is not dedicated to touchscreens but it is funny to draw !)
[/LIST]
I'm looking for a media player with mouse gesture. VLC does not work fine in UNR.

---

### Post by Leed on 2009-08-28
Yes I had some random crashes too, not that many, it's annoying but hey it reboots fast. Hope that goes away after a few updates. I generally have the impression the crashes have something to do with the touchscreen. 

Compiz-fusion does work, I wouldn't recommend it on the standard UNR Interface/menu, when using scale to change windows the windows flickers while zooming into place. However if you change the settings to classic Ubuntu it works great. 
It's easy to get it working, System->Appearance>Visual Effects .. and set it to extra. I also recommend using compizconfig-settings-manager. 

of course it will only work if you got the display drivers working correctly, check the link I posted before.


Could you please give me some details on the screen rotation feature? Maybe we can get that button working somehow. 

Also anything on how to get that webcam working.

---

### Post by Mizukusai on 2009-08-28
I'm currently using the driven mentionned in your link. However, the perfs are not really good.
I tried to leave the netbook "alone" with a batch running. It froze as well.
I'll try the classic desktop with compiz. I'm looking forward to rotate the cube with my finger :D

To rotate the screen, either use the gui, or the command 
xrandr -o [left|right|inverted|normal]

I read from french forum that webcam is ok with skype. I don't know anything more for now. I'll check if I can get more information.

It would be great if you manage to capture the signal sent by the button below the screen. xev does not  see anything. 

I'll also try to disable the touch screen, just to be sure if it is the source of the "freeze".

---

### Post by Leed on 2009-08-28
How do you realize the display performance is not good? Seems ok to me, but I'd always enjoy better (it's definitely better than without that driver and better than the performance windows achieves)

I'll get Skype installed once I'm back from work, see if it makes a difference. 

About the display rotation, I'll try using the xev command to track the signal of the button. Just found some howto here
[http://ubuntuforums.org/archive/index.php/t-1218221.html](http://ubuntuforums.org/archive/index.php/t-1218221.html)

We could make a rotating script that executes the xandr commands on launch, then assign the button to it in metacity or compiz. All still a little theory, but it should work.

---

### Post by Mizukusai on 2009-08-28
> **Leed said:**
> How do you realize the display performance is not good? Seems ok to me, but I'd always enjoy better (it's definitely better than without that driver and better than the performance windows achieves)

I'll get Skype installed once I'm back from work, see if it makes a difference. 

About the display rotation, I'll try using the xev command to track the signal of the button. Just found some howto here
[http://ubuntuforums.org/archive/index.php/t-1218221.html](http://ubuntuforums.org/archive/index.php/t-1218221.html)

We could make a rotating script that executes the xandr commands on launch, then assign the button to it in metacity or compiz. All still a little theory, but it should work.
* When I pick a window and move it, the movement is [SIZE=2]a bit jerky[/SIZE]. I'll try with compiz. Like you, I'm @work and my Owl (yes, it is the name of the T91) cannot connect to the internet from here.
* Sure, the script with xrandr would be easy, once the signal of the button is captured.

Another point, I'm thinking of hacking a bit the netbook, adding him a 3G card. What do you think ?


EDIT : a bit jerky instead of "not fluent". I still need to pratice my english.

---

### Post by Leed on 2009-08-28
I didn't have any jerky issue after adding the psb drivers to the kernel, I could make a youtube video if you want to something to compare.

3G INSIDE the netbook... sounds cool, I have no idea if it has an interface for that. 

I've been trying to get my Iphone to do internet tethering via bluetooth at lunch time, but it didn't work out of the box, not sure if I'll try again.

I know my boss once had an USB stick for mobile internet via GSM/UMTS, I once put it in an Ubuntu (normal Ubuntu, Intrepid) laptop and it got recognized and worked immediately. I think that would be the simplest solution if you want mobile internet.

---

### Post by Leed on 2009-08-28
You are correct, display is a bit jerky when moving windows. I didn't notice because UNR doesn't use windows that much.

However I tried switching to Ubuntu classic desktop mode and activating compiz, there the windows mooved very smooth

---

### Post by Mizukusai on 2009-08-28
Good news. I'll switch to classic.
I wasn't found of netbook-launcher, anyway.

---

### Post by Leed on 2009-08-28
I kind'o like, specially how it utilizes full screen, still have to decide if I'll abandon it.

I just tried Skype, can hardly believe it, the webcam works there... but not in cheese, even if skype is still open. 
But I noticed another flaw, the mic isn't working.


--bad news on xev, it doesn't react to the button

---

### Post by scottfranklin on 2009-08-29
I'm strongly considering a T91, but only if I can get linux on it, so I'm following this thread with great interest!  Purchase probably won't occur for at least another month, so I'm afraid I can't help much with getting things working (not sure I'd be able to help much, anyway), but THANK YOU for trailblazing in this.

Do you notice significant speed differences between linux & the Windows installation it originally came with?

---

### Post by Leed on 2009-08-29
> **scottfranklin said:**
> 
Do you notice significant speed differences between linux & the Windows installation it originally came with?

Absolutely, netbooks were never made for Windows... on the other hand, thanks to many people wanting it, we get better hardware on them.

Windows XP boots pretty fast, but is often jerky, sometimes even lags a few seconds. But in general runs very well. 

Linux boots much faster, and doesn't hang that much, it's just getting everything working at first that's annoying (that's what this thread is for). 

Open issues:
-So far only Skype can activate the Webcam
-Microphone not working
-Screen turn feature is there, but we haven't got the button working with it
-Graphics run good, but could still be better
-Occasional system freezes, reason not yet known
-Wireless fn key does not work (wireless itself does, but you'll need a LAN cable first to set it up)
--Update: Screen Brightness fn Keys don't work

---

### Post by Mizukusai on 2009-08-31
Small update : 
Switched to classic desktop. Compiz works like a charge. But scrolling in firefox is still a bit "jerky".
Add "stroke" to rotate the cube in easystroke. Now, I rotate it with my finger !!! This is childish, I know. But I like it, even if I'm 34.

Next step is to disable all features one by one, to isolate the faulty one. Let's start with the touchscreen.

---

### Post by Leed on 2009-08-31
I noticed while most things freeze (even ctrl+alt+backspace, with dontzap disabled) you can still reboot using the more secure REISUB method

For those who don't know REISUB
that's Alt_Gr + Printscreen + <following keys, give 2-3 seconds time in between>

R (Takes back keyboard control from X)
E (Sends close command to open processes)
I (Kills processes that haven't closed)
S (Syncs to disc)
U (Unmounts drives and remounts as read only)
B (Reboots)

---

### Post by Leed on 2009-09-01
How I love the Linux world, with a little help from someone called davidjany I got the screen rotate button working:

(Jaunty instructions)

edit the file:
/etc/acpi/rotatescreen.sh

change:
```
case "$ROTATION" in
        right)
        NEW_ROTATION="normal"
        ;;
        *)
        NEW_ROTATION="right"
        ;;
esac
```

to

```
case "$ROTATION" in
        right)
        NEW_ROTATION="inverted"
        ;;
        left)
        NEW_ROTATION="normal"
        ;;
        inverted)
        NEW_ROTATION="left"
        ;;
        *)
        NEW_ROTATION="right"
        ;;
esac
```



then create a event handler by creating the file (as root/sudo)
/etc/acpi/events/asus-rotate

and change the content to (replace 9b)
```
event=hotkey ATKD 0000007b
action=/etc/acpi/rotatescreen.sh
```

the following codes are valid
7b - short keypress
7c - long keypress
7d - keyrelease

---

### Post by Leed on 2009-09-01
We can use the same way to get the wireless button working

edit /etc/acpi/events/asus-wireless

change the event=hotkey to:
```
event=hotkey ATKD 00000010
```

note: The LED won't switch off, but wireless will (not sure about Bluetooth)

I've also noticed that something isn't yet good with the wireless, upon first connect it always loses connection after about 10 minutes. After disabling and enabling network settings it then stays connected.

---

### Post by Leed on 2009-09-01
I wanted to make a shell script, that rotates through the display orientations when you press the key longer (just like in windows). 

I got pretty far, then noticed that you can't change ubuntu's OSD-Notification to switch faster. There's no point if it takes 5 seconds to update the notification... does anybody know another type of OSD?

---

### Post by Mizukusai on 2009-09-01
My idea is two scripts : 
one launched on long press : make a rotation every second
one lauched on release : kills the previous one


Compiz is really really slow when the screen is rotated. Is it the same with yours ?
Maybe we can restart compiz after the rotation.

---

### Post by Leed on 2009-09-01
I'm not using compiz, I'm sticking to the UNR interface, it's just more comfortable for what I use the machine for. I have a bigger laptop for Desktop work.

But I read the xrandr program has some problems with compiz, for me it takes 2-3 seconds, I assume compiz restarts itself and takes longer. 

The idea I had is similar to yours, only 3 scripts

script 1: activates on 7b (short press) and writes the current display state to a global variable

script 2: activates on 7c (long press, fires approx. ever second over the button) and rotates through the different orientations. On each change the current selection is shown via OSD (left|inverted|right|normal) together with an arrow icon. The arrow icons are set up according to the active display orientation taken from the variable in script 1 (to make sure they still point in the correct direction)

script 3: activates on 7d (key release) and sets the display to the last orientation from script 2


I already had the OSD working with the icon, but then noticed that the notifications stick there 5 seconds blocking the newer ones from being shown. So in the end you wouldn't know what orientation you're changing to

---

### Post by Mizukusai on 2009-09-01
OSD ?
Can you give more info on this function ? Are you talking about gnome's notification ?

---

### Post by Leed on 2009-09-01
yes, that is gnome's notification system, I'm not sure but it seems to have taken over all other OSD systems. 

you'll need to install libnotify-bin to be able to make your own OSD notifications. you can then send them with 

notify-send "message"

You can even send them to other users on the system, but you can't reduce the time (not even with the -t parameter)... if there would only be some way to replace the message we could do it. Maybe there is some way, after all the volume adjustment allows immediate updates.

---

### Post by Mizukusai on 2009-09-01
It's that easy ?! 
This gives me a lot of ideas... (Notification on my XBMC-box, for example)

---

### Post by Leed on 2009-09-01
some inspiration for you

```
notify-send -i "/usr/share/icons/Human/48x48/actions/back.png", "Screen Orientation" "Left"
```


if it doesn't do it, you've forgotten
```
sudo apt-get install libnotify-bin
```

---

### Post by scottfranklin on 2009-09-01
Great to hear the buttons are working!  I read in an earlier post that the functionality of the VGA out had yet to be determined; have either of you plugged an external monitor in and found that it didn't work, or have you just not gotten to it yet (there's a lot more on your plate, I know).  Conferences are one of the major uses I'd have for the T91 (reading and annotating .pdf papers would be the other), so VGA out is kind of important.

As for the camera, I don't know if this helps, but I have a Panasonic CF-R4 that the usb camera works w/Skype but not w/Gizmo.  (Haven't tried it w/Cheese yet).  I wonder what Skype is doing differently?  

scott

---

### Post by Mizukusai on 2009-09-02
There was a kernel update yesterday from Ubuntu.
I can't boot with it and I had to rebuilld the psb module. (dpkg-recongure psb-kernel-source) on the old kernel.

And the wireless does not work at all any more, even when booting with the old kernel (2.6.58-14-generic)
I'm trying a ```
dpkg-reconfigure linux-backports-modules-jaunty
```

I hope the "uninstall the new kernel" solution will work, but it will prevent me from receiving later updates.


I'd prefer to make it work with the new kernel.

---

### Post by Leed on 2009-09-02
Just tried the VGA out on an external screen using 1920x1080 resolution (BenQ G2411HD). 

It worked in full resolution, but I had to restart the X server (ctrl+alt+backspace) to get it up. Then the big resolution also affected the small screen making it show only a small portion of the screen, rather useless. I'm sure with a little configuring you should be able to get it working in any way you want it (both screens small -> clone, laptop small external big etc. ->extend) etc.

---

### Post by Mizukusai on 2009-09-02
After a lot (really a lot) of tries, every thing is back to "normal".
Situation : 
* kernel 2.6.28-15 doesn't ha any display when psb drivers are installed
* kernel 2.6.28-15 has an "ugly" display when psb drivers are not installed
* kernel 2.6.28-14 works fine, when linux-backports-2.6.28-14 is installed, and psb-kernel-source "reconfigured". I guess there is still some random freezes.

---

### Post by scottfranklin on 2009-09-02
> **Leed said:**
> Just tried the VGA out on an external screen using 1920x1080 resolution (BenQ G2411HD). It worked in full resolution, but I had to restart the X server (ctrl+alt+backspace) to get it up. Then the big resolution also affected the small screen making it show only a small portion of the screen, rather useless. I'm sure with a little configuring you should be able to get it working in any way you want it (both screens small -> clone, laptop small external big etc. ->extend) etc.

Thanks!  I couldn't think of any reason why it wouldn't work, but did figure it would take some configuring work.

---

### Post by ah_mad on 2009-09-02
Did any one manage to resume from suspend while using the "psb" graphic driver. I can resume successfully when I use the generic "ugly" driver but with the psb driver it always ends into a black screen after few "blue flashes"!

Also could you please tell me how can I calibrate my touch screen. It is bit off.

---

### Post by Mizukusai on 2009-09-03
Resume/suspend is fine here.
Calibration must done from command-line, without any X server started. (see previous posts)

---

### Post by Leed on 2009-09-03
@Mizukusai
That's scary, I started out with 2.6.28-15, I've been checking my updates ever since you posted that the new kernel is causing problems, but I've had it all the time. 

Makes me a bit worried when thinking about getting an update

---

### Post by Mizukusai on 2009-09-03
You started with kernel #15 ? 
I guess French repositories are updated after yours.

I'll try to uninstall all kernel #14 packages and see what happens...
For now, I can boot only on that one... I don't know exactly what is going on.

---

### Post by Leed on 2009-09-03
A little extra here, I don't think it'll solve your problem, but who knows

edit /etc/X11/xorg.conf and change the device section to
```

Section "Device"
	Identifier      "Configured Video Device"
	Option "AccelMethod" "EXA"
	Option "DRI" "off"
	Option "MigrationHeuristic" "greedy"
EndSection
```

---

### Post by ah_mad on 2009-09-03
Thanx for your reply. 

I used apt-get dist-upgrade and it upgraded me to 2.29-1-netbook, where psb-kernel-source can't be compiled (compiling error due to an "strut" which has lost some members in new kernel apparently). So, I had to down grade and probably the suspend/resume problem comes from that.

Apart from this, I used "calibrate_touchscreen", then started x successfully with "startx" and the calibration was very good. But when I restarted the machine, the X never start again, instead I get a lot of blue yellow lines.

However, if I go to recovery mode and start x from the command line I get x again. The problem is that I get an error about problem with "hal" and no input device (mouse/keyboard/touch screen) works. 

I think I need to install the whole thing again :(

---

### Post by ah_mad on 2009-09-03
OK, I re-install the whole OS. First I should say that I'm running eeebuntu 3.0 which is essentially the same as ubuntu 9.04.

I reconfirm that psb driver works with kernel 2.6.28-15-generic (actually apt-get required me to download this kernel when I wanted to download the psb driver). This is in spite of the fact that last time, it was not working with this kernel and I was getting the same result as Mizukusai mentioned and I had to down grade to 2.6.28-14-generic to make it works. This time however, I first installed the kernel, restarted and then installed the psb driver.

On suspend/resume: I check suspend/resume worked fine for me on kernel kernel 2.6.28-11/12/14 and 15-generic. However, as soon as I installed the psb driver and I restarted, it stopped working and I got the same result as I mentioned in my previous post.

My xorg.conf has the same entries as what Leed said (I'm not sure if Leed suggested them for me, but just for being on the safe side ;) ).

After resuming, I still can turn the Caps lock on and off. I am going to check if I can ssh into the machine or not.

Thanx again for all of your help.

---

### Post by Mizukusai on 2009-09-04
Weirder and weirder.
I let my laptop on during all the morning. No crash. 
During my lunch break, I've customized easystroke with the following actions ( next/previous tab fro firefox, next/previous page for firefox, next/previous desktop for compiz ). Now, I need to click less. No crash at all.
This may prove that the touchscreen could be in cause....

---

### Post by Leed on 2009-09-04
I didn't have a crash for quite a while either, that's mainly why I posted the changes for xorg.conf. I know it's nothing trivial, but I can't find anything else to blame the crashes on. I haven't changed that much. But on the other hand, I haven't been using the netbook that much in the last few days. 

What makes sense in this respect to is, it seems that it was only the X server that froze. All windows and menus stopped responding. The mouse pointer and the REISUB method still worked.

---

### Post by Mizukusai on 2009-09-06
Bad news. 
My T91 does boot any more. When I turn it on, the "ON" and "Wifi" Leds are on, but no activity at all : 
black screen, no hd activity.
And I need to press "off" for 4 sec to turn it off.
I tried to empty to battery. no success.
I reseted it using the inside button, no success.

I can still the "insurance" (tell me correct word, please) but I bought the laptop by internet. I don't want to send it back, and wait...

Do you have any idea ?

---

### Post by Leed on 2009-09-06
Thats not good, been enjoying your help in this thread.

Does the BIOS still work? By default it uses bootboost, a tiny partition on the HDD that skips the bios screen. Just hit esc continuously when switching on. You may only have a broken MBR.

Is it only a blank screen, or is there a cursor in the top left? Can you boot it from a USB stick?

I think the Reset button only sends out a shutdown signal (to switch the pc off)

-normally, if a hdd can't be found or read, you should get a error message
-If the screen wouldn't be working, you should still see hdd activity
-You could try opening the back module where the memory is, perhaps something has come loose in there...

Other than that you shouldn't open anything as long as you still have warrany/guarantee, else you can't send it back.

---

### Post by xyzo on 2009-09-07
Hi!
Very interesting thread :-)
Has anyone here been able to fix the problem of the microphone not working with Skype?
Thanks in advance.

---

### Post by Mizukusai on 2009-09-07
No, no bios. Actually, nothing at all.
The screen, the  HD led stay off. Except for the "power" and the "Wifi" leds, there is seem to be no life at all in this netbook.

This is definitely a hardware issue. (CPU meltdown, or motherboard ...)

---

### Post by Jonathanius on 2009-09-07
> **xyzo said:**
> Has anyone here been able to fix the problem of the microphone not working with Skype?

davidjany from the EeeUser forum may have a solution, haven't got a chance to try it out myself, but it apparently works for him:
[http://forum.eeeuser.com/viewtopic.php?id=73432](http://forum.eeeuser.com/viewtopic.php?id=73432)
(on your "Which distro for my T91 thread")

---

### Post by Leed on 2009-09-07
interesting, will have to have a little thinking if I should take that step. I hate moving away from the Repositories and Karmic will be released in a little more than a month.

Does anyone know what ALSA version karmic uses, and if it fits the T91?

---

### Post by Mizukusai on 2009-09-08
> **Mizukusai said:**
> No, no bios. Actually, nothing at all.
The screen, the  HD led stay off. Except for the "power" and the "Wifi" leds, there is seem to be no life at all in this netbook.

This is definitely a hardware issue. (CPU meltdown, or motherboard ...)

I'm sending it back to Asus for repair.:(
I'm "netbook-less". :-&

This will give me time to "play" with gnome notifications on my xbmc-box.

---

### Post by davidjany on 2009-09-10
Just to see what will happen, I've inserted a defective sd card in my netbook. Ubuntu hanged maybe 10 minutes later. After rebooting the bios didn't went on - it was just as Mizukusai has described, only WIFI and Power led were on. 

I'm guessing you have tried to run your netbook without the memory card, so maybe the same issue might happen if the ssd is broken?

---

### Post by Mizukusai on 2009-09-10
Oh. I'm sorry the same issue happened to someone else.
The only SD card I'm using was a 16 Go shipped with the laptop, and I've inserted it in the "permanent" slot (on the left side). The dummy sd card initially inserted in the front slot is still in there.
I did not insert or eject any of them since the installation. And, of course, I tried to boot without the SD card. Same problem.
So, I don't think the defective SD card may be a good clue.
But to sure of that, I'll try to read it from another SD card reader, tonight. (It's 9AM here)

I can't think the SSD is the source if the problem as well. If the SSD ( the hard drive) was broken, the PC would still boot, show me the bios, and fail to load the OS. But here, there is no activity at all. My guess is CPU or motherboard. 

I'm shipping the netbook tonight back to Asus, following their process.

---

### Post by Leed on 2009-09-10
You mean if you stick the SD card back in (on the side slot - Harddrive extension) it boots again normally? Or did you use the front slot?

I'm waiting for the prices of SD cards to drop, so that I can replace the one delivered with the eeepc, 15MB/s is simply too slow.

---

### Post by Mizukusai on 2009-09-10
For me, no matter where the card is inserted, no matter if the card is even inserted or not, the netbook don't work.

---

### Post by Leed on 2009-09-10
I wonder if that thing simply overheats... it does get pretty hot, when I leave it on for a longer time I put it upside down while not using it. That way the heat doesn't get stuck underneath.

---

### Post by Mizukusai on 2009-09-10
I think the same. 
I wonder if there is some warning in the documentation about that.

---

### Post by davidjany on 2009-09-10
I've just checked sensors:

acpitz-virtual-0
Adapter: virtual device
temp1:         +67.0°C (crit = +88.0°C)

eeepc-virtual-0
Adapter: virtual device
fan1:            0 RPM

The "virtual devices" are confusing me. How virtual are they? If they are authentic then the temperature seems to be ok. It's not my first device that is almost at 70°C. I'm using it almost all day long and it is not getting so hot I could burn myself. The intel manual says below 85°C for the cpu is ok ([http://download.intel.com/design/processor/datashts/319535.pdf](http://download.intel.com/design/processor/datashts/319535.pdf)).

The device has no active cooling, right? I haven't read of, heard or seen one ([http://jkkmobile.blogspot.com/2009/05/asus-eee-t91-dissected.html](http://jkkmobile.blogspot.com/2009/05/asus-eee-t91-dissected.html)).

My bios firmware is 0403.

---

### Post by Leed on 2009-09-10
Is there any "smart" way to figure out, if the device has the GPS device integrated? I bought mine on auction, so I'm not sure. 

In Bios PCI devices there something mentioned 3G 

Is there some simple program in Ubuntu that could recognize and use it?

---

### Post by Mizukusai on 2009-09-10
There is no fan that can be heard in the netbook.

---

### Post by Mizukusai on 2009-09-10
I think lspci or lsusb should show you something.

---

### Post by davidjany on 2009-09-10
@Leed: If you bought the T91, then there is no GPS integrated. There might be some devices (T91GO) in the future with integrated GPS, but as far as I know only the T91 is on the market right now.

After your guaranty has expired, there seems to be a way to rearm your device. Take a look at already mentioned link [http://jkkmobile.blogspot.com/2009/05/asus-eee-t91-dissected.html](http://jkkmobile.blogspot.com/2009/05/asus-eee-t91-dissected.html) .

---

### Post by Leed on 2009-09-10
Looks fun, for now I wouldn't dare put a soldering iron on my t91, but for the future, who knows ;)

---

### Post by Mizukusai on 2009-09-10
Let's hope that the slot for gps+3g is there.
Do you know where I can buy such device, for T91 ?

---

### Post by billl on 2009-09-11
I've been able to control the brightness with the following command:

```
dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:x
```

where x is the brigthness you want to set.

In an acpi script, the command must be run as the current user.

Here is the full script (/etc/acpi/brightness.sh):

```

#!/bin/bash

getXdisplay() {
  console=`fgconsole 2> /dev/null`
  DISPLAY=`ps ax | grep -m1 -e "[X] .* vt${console}" | sed -re "s,.*/X .*:([0-9]+).*,:\1,"`
  export DISPLAY
}

getXuser() {
  getXdisplay
  USER=`finger | grep -m1 "${DISPLAY}" | awk '{print $1}'`
  export USER
}

getBrightness() {
  getXuser
  sudo -u ${USER} dbus-send --session --type=method_call --print-reply --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.GetBrightness | tail -n 1 | grep -ow "[[:digit:]]\+"
}

setBrightness() {
  brn=${1}
  [ ${brn} -ge   0 ] || brn=0
  [ ${brn} -le 100 ] || brn=100
  getXuser
  sudo -u ${USER} dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:${brn}
}

incBrightness() {
  level=`getBrightness`
  if [ ${level} -lt 100 ]; then
    setBrightness $((${level} + 5))
  fi
}

decBrightness() {
  level=`getBrightness`
  if [ ${level} -gt 0 ]; then
    setBrightness $((${level} - 5))
  fi
}

BRIGHTNESS_FILE="/var/lib/acpi-support/brightness"
if [ -f "${BRIGHTNESS_FILE}" ]; then
  BRIGHTNESS_OLD=`cat "${BRIGHTNESS_FILE}"`
fi

BRIGHTNESS_NEW=`echo "${3}" | tr "[a-f]" "[A-F]"`

if [ x"${BRIGHTNESS_OLD}" != x"" ]; then
  if [ x"${BRIGHTNESS_NEW}" = x"${BRIGHTNESS_OLD}" ]; then
    if [ x"${BRIGHTNESS_NEW}" = x"0000002F" ]; then
      incBrightness
    elif [ x"${BRIGHTNESS_NEW}" = x"00000020" ]; then
      decBrightness
    fi
  else
    res=`echo "ibase=16; ${BRIGHTNESS_NEW} > ${BRIGHTNESS_OLD}" | bc`
    [ ${res} -eq 1 ] && incBrightness || decBrightness
  fi
fi

echo "${BRIGHTNESS_NEW}" > "${BRIGHTNESS_FILE}"

```

And here is the event (/etc/acpi/events/brightness):
```

event=hotkey ATKD 0000002[0-9a-f]
action=/etc/acpi/brightness.sh

```

---

### Post by amtvaish on 2009-09-11
> **Leed said:**
> Yes I had some random crashes too, not that many, it's annoying but hey it reboots fast. Hope that goes away after a few updates. I generally have the impression the crashes have something to do with the touchscreen. 

Compiz-fusion does work, I wouldn't recommend it on the standard UNR Interface/menu, when using scale to change windows the windows flickers while zooming into place. However if you change the settings to classic Ubuntu it works great. 
It's easy to get it working, System->Appearance>Visual Effects .. and set it to extra. I also recommend using compizconfig-settings-manager. 

of course it will only work if you got the display drivers working correctly, check the link I posted before.


Could you please give me some details on the screen rotation feature? Maybe we can get that button working somehow. 

Also anything on how to get that webcam working.




solution: display totally depand upon h/w which is situated in your system .....if it is not supported then black screen such type of problem are created when u use extra feature in graphic.
so check firstly display h/w then allow extra feature......
u search webcam s/w of linux and use it.........

---

### Post by Leed on 2009-09-13
Thanks for the input billl. I'm afraid your script didn't work on my machine, but it gave me the input to solve the problem using a more simple (or primitive) code. I just changed the following:

/etc/acpi/events/brightness
```
# /etc/acpi/events/brightness
# called when used brightness keys

event=hotkey ATKD 0000002[0-9a-f]
action=/etc/acpi/brightness.sh %e
```

/etc/acpi/brightness.sh
```
#!/bin/bash
getXdisplay() {
  console=`fgconsole 2> /dev/null`
  DISPLAY=`ps ax | grep -m1 -e "[X] .* vt${console}" | sed -re "s,.*/X .*:([0-9]+).*,:\1,"`
  export DISPLAY
}

getXuser() {
  getXdisplay
  USER=`finger | grep -m1 "${DISPLAY}" | awk '{print $1}'`
  export USER
}

  case $3 in 
    00000020)
    brn=0
    ;;
    00000021)
    brn=30
    ;;
    00000022)
    brn=35
    ;;
    00000023)
    brn=40
    ;;
    00000024)
    brn=45
    ;;
    00000025)
    brn=50
    ;;
    00000026)
    brn=55
    ;;
    00000027)
    brn=60
    ;;
    00000028)
    brn=65
    ;;
    00000029)
    brn=70
    ;;
    0000002a)
    brn=75
    ;;
    0000002b)
    brn=80
    ;;
    0000002c)
    brn=85
    ;;
    0000002d)
    brn=90
    ;;
    0000002e)
    brn=95
    ;;
    *)
    brn=100
    ;;
  esac
  getXuser
  sudo -u ${USER} dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:$brn
```

The only snag is, the power management icon appears a second time in the top bar, I suppose this has something to do with me not getting the user, but the suggested sudo -u ${user} in combination with getXuser and getXdisplay doesn't work on my system.

---

### Post by billl on 2009-09-13
I've edited my post and fixed a few things. The script should now work (as root).

---

### Post by dfauvarq on 2009-09-13
I'm still having the issue of wireless dropping connection after 10 minutes after boot and even asking for the WPA-PSK password again.

I have a Asus T91 with Ubuntu 9.04 installed (kernel 2.6.28-15) and the linux-backports-modules-jaunty installed.

Any help will be greatly apreciated.

Thanks
Daniel

---

### Post by Leed on 2009-09-14
@dfauvarq

I still have the same issue, but also a temporary workaround. First of all, make sure you have the Wireless fn key working (you'll find info's on that in this thread).

Ubuntu only asks for the password, because the reconnect attempt fails. So you'll want to get it reconnected before that happens.

Once the connection breaks, simply switch wireless of using the fn key, wait 1-2 seconds and switch it on again (LED doesn't react). In some cases you'll have to tell the network manager to connect to your wlan again. 

Do that once and the connection should be stable. Maybe it'll disconnect again in a few hours, but then you can just do it again.

---

### Post by Jonathanius on 2009-09-14
Is everyone still experiencing random lockups? How long has it been since the last one?

---

### Post by Leed on 2009-09-14
@bill
Thanks for the update, I've allowed myself to take a part of your code and edit it into my example, hope that's ok. Your example is definitely a more intelligent code, but I prefer keeping it simple, 16 brightness possibilities is more than I'll ever need and I also have the impression, that brightness values between 0 and 25 are the same anyway. 

@jonathan
Unfortunately I had my last lockup yesterday, before that I had a really long run without any problems... hope it stays that way.

---

### Post by mspenguin on 2009-09-17
Hi,
 
I'm new to UNR and would like to get the touch screen (Asus T91) on UNR Karmic into Asus T91. What's the best way to get working?
 
Thank you.

---

### Post by Truenash on 2009-09-18
Got my T91 this week; will be looking to install Crunchbang Linux on it this weekend, hopefully tomorrow. Going to try CrunchEEE/Crunchbang Lite. The Live boot from usb worked fine, with only one odd problem (it froze as if it was paused or you had closed the lid, only to be resumed by pressing the power button, but this didnt seem to cause any ill effects).

As with everyone else, the wireless didn't work out of the box and the video drivers need sorting, as well as a decent touch calibration and right click simulator. Definitely need a good right click simulator as CrunchBang uses OpenBox.

Sounds like you've all done fantastic work fixing the issues so far, I'll let you know how my installation goes ;) 

Thanks
Nash

---

### Post by xyzo on 2009-09-20
> **billl said:**
> I've been able to control the brightness with the following command:

```
dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:x
```where x is the brigthness you want to set.

In an acpi script, the command must be run as the current user.

Here is the full script (/etc/acpi/brightness.sh):
...

Hi!
The 1st command you give is working well but unfortunately the scripts don't work on my T91: no effect at all.
How should I run brightness.sh on command line to test it? What are the arguments to pass to the script?
TIA.

---

### Post by Leed on 2009-09-21
> **Leed said:**
> some inspiration for you

```
notify-send -i "/usr/share/icons/Human/48x48/actions/back.png", "Screen Orientation" "Left"
```


if it doesn't do it, you've forgotten
```
sudo apt-get install libnotify-bin
```

@xyzo
If you just want to test if the script is triggered, install the libnotify-bin and just add a command to send a notification message to your screen (example above)

I assume there's something wrong in your /etc/acpi/**events** folder, check the event handler files there. I once had the problem that I named one of the handlers brightness.sh, while in that folder it should be only brightness (no ending). Also you should check if there is any other brightness handler in that folder that may be conflicting. 

Last but not least, in the /etc/acpi folder check if your script brightness.sh is executable (sudo chmod +x /etc/acpi/brightness.sh)

There are two versions of that script in this thread, if the one you have doesn't work, try the other (dont forget to adjust /etc/acpi/events/brightness, they are not the same).

---

### Post by billl on 2009-09-21
> **xyzo said:**
> How should I run brightness.sh on command line to test it? What are the arguments to pass to the script?

To increase the brightness:
```
sudo brightness.sh hotkey ATKD 0000002f
```

To decrease the brightness:
```
sudo brightness.sh hotkey ATKD 00000020
```

---

### Post by Mizukusai on 2009-09-22
My T91 is back, with a brand new Windows...:(

I just finished the install.
Only issue : I  can't get compiz to work.
> Software rasterizer detected. Falling back to metacityI tried everything in this topic, and a lot of others... No luck.
Any clue ?


Edit : My bad !! some packages were missing... Now, I have to reconfigure easystroke, and install the acpi tunning.

---

### Post by Mizukusai on 2009-09-23
Another problem...
I have a very very poor signal for my home wifi spot.
The same signal is "max", with a eeepc 701 using easy peasy (based upon intrepid)

I tried to boot with #14 and #15 kernels. Same issue.

Any ideas ?

---

### Post by Leed on 2009-09-23
@Mizukusai

Congratulations to getting your netbook back and working. I'm not sure about you wifi issue, at home I have my wifi right behind me and sometimes it has a reception of 4/5, sometimes only 1/5. Then I still have the occasional dropout, I just switch off and on again using the fn keys. You may have some other problem, but in general the wifi drivers are not yet optimal. 


@maryjohn
It does have some problems after installation, most of them you can solve by going trough this thread from start to finish. If that doesn't solve it, you'll have to explain what your problems are.

---

### Post by Mizukusai on 2009-09-23
I will try that last wifi drivers :  [http://ubuntuforums.org/showthread.php?p=7743762](http://ubuntuforums.org/showthread.php?p=7743762)
If it's worthy, I'll copy/paste the content of the post here

---

### Post by Mizukusai on 2009-09-24
Not ok.
I can't load this drivers. My card is not working.
I currently using #14 kernel.

I'll try to upgrade to Karmic.

---

### Post by Mizukusai on 2009-09-24
[Ubuntu Moblin Remix]("http://linux.dell.com/files/ubuntu/moblin-remix/dev-edition-2.0/")
Let's try this !



**ALERT !!**
* This is made for the Dell Mini 10
* This will erase all your SSD without any warnings !

But, it works for th T91 as far as I know.
Wifi seems ok (no AP seen for now)
We I'll be able to connect it, I'll add ubuntu-mobile repository and activate psb drivers.

Moblin seems to be a really nice interface. :D

This ubuntu is based upon Jaunty, but with a 2.6.31 kernel, and specific repositories.

---

### Post by Mizukusai on 2009-09-25
Karmic is really not ready for the T91. (or is it the T91 not ready for Karmic?)

I tried : 
* Jaunty Moblin (with Dell) - no correct display. The psb modules can't "compile" on this 2.8.31 kernel.
* Karmic Moblin (with Dell) - no correct display either. Coflict between jaunty and Kamric packages
* Karmic, without Mablin - same issue (what did I expect ?)

So, I'm back with Jaunty and my  "not so good" Wifi.
And, i have the flu...

---

### Post by Truenash on 2009-09-25
That sucks, I was really hoping Karmic would provide a good solution to some of the current problems.

Can anyone whos successfully done it explain the process of screen calibration to me please? The GUI software for it on UNR won't start, and just goes to black screen than says screen is calibrated.

---

### Post by xyzo on 2009-09-26
> **Leed said:**
> @xyzo
If you just want to test if the script is triggered, install the libnotify-bin and just add a command to send a notification message to your screen (example above)
[...]

Thank you for your help! Your code is working well and I'm now able to control brightness on my T91 :)

---

### Post by xyzo on 2009-09-26
[maybe out of topic]
I've noticed that Asus support website is listing a BIOS update (version 0404) for the T91MT model (MT for MultiTouch?). Has anyone here tried to install this BIOS on the regular T91 model? Could it give better performences?
The link:
[http://support.asus.com/download/download.aspx?model=EEE+PC+T91MT&f_name=t91mt-asus-0404.zip&SLanguage=en-us](http://support.asus.com/download/download.aspx?model=EEE+PC+T91MT&f_name=t91mt-asus-0404.zip&SLanguage=en-us)

---

### Post by Truenash on 2009-09-27
I'm not brave enough to try that...

---

### Post by Leed on 2009-09-28
From what I know Multi-Touch is set only to be available with Windows 7. As there is a version of the T91 planed with Win 7 I'm not sure if it is hardware related or if the bios would do the change. Then again I don't know if Ubuntu supports multi-touch.... all I know is that there wouldn't be much use for it. 

Despite all that was said so far, I'm still planing to upgrade my system to Karmic once it is officially released. I still have hope it will somehow work, or work because it is an upgrade from jaunty.

---

### Post by Mizukusai on 2009-10-02
Just be sure that the "mobile" repositories are available before you start upgrading...

---

### Post by Jonathanius on 2009-10-05
> **Mizukusai said:**
> Karmic is really not ready for the T91. (or is it the T91 not ready for Karmic?)


I'm running Xubuntu Karmic beta, I started today so I haven't sorted everything out but so far, but I'm running well at native resolution, touchscreen working properly, no crashes - I tried drawing in Gimp for a half hour, but I can't get it to, so far - webcam in skype, speakers, wifi (and wifi on/off key) both working out-of-the-box. I still need to get the microphone to work, alsa 10.0.21 is supposed to do the trick, but karmic comes with only 10.0.20, which has not worked so far. Also, brightness keys don't work once I have the poulsbo driver installed and I haven't had a chance to try the script for the rotate button yet.

I'm following: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
more info found at this thread: [http://ubuntuforums.org/showthread.php?t=1253406](http://ubuntuforums.org/showthread.php?t=1253406)

note that the guide in the thread and the wiki use different xorg.conf files, i followed the wiki as the one in the thread made X not start.

also, instead of, for instance:
```
echo 'deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list
```I simply added 
```
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
```to my /etc/apt/sources.list manually, since I don't know how to do all the fancy "echo" stuff.

also I'm not using using the most recent edition of the psb-kernel-* and psb-modules packages from lucazade (4.41.6) instead of the older one linked to.
they can all be found here (under psb-kernel-source): [https://launchpad.net/~lucazade/+archive/gma500/+packages]("https://launchpad.net/%7Elucazade/+archive/gma500/+packages")

---

### Post by Mizukusai on 2009-10-06
> **Jonathanius said:**
> I'm running Xubuntu Karmic beta, I started today so I haven't sorted everything out but so far, but I'm running well at native resolution, touchscreen working properly, no crashes - I tried drawing in Gimp for a half hour, but I can't get it to, so far - webcam in skype, speakers, wifi (and wifi on/off key) both working out-of-the-box. I still need to get the microphone to work, alsa 10.0.21 is supposed to do the trick, but karmic comes with only 10.0.20, which has not worked so far. Also, brightness keys don't work once I have the poulsbo driver installed and I haven't had a chance to try the script for the rotate button yet.

I'm following: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
more info found at this thread: [http://ubuntuforums.org/showthread.php?t=1253406](http://ubuntuforums.org/showthread.php?t=1253406)

note that the guide in the thread and the wiki use different xorg.conf files, i followed the wiki as the one in the thread made X not start.

also, instead of, for instance:
```
echo 'deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list
```I simply added 
```
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
```to my /etc/apt/sources.list manually, since I don't know how to do all the fancy "echo" stuff.

also I'm not using using the most recent edition of the psb-kernel-* and psb-modules packages from lucazade (4.41.6) instead of the older one linked to.
they can all be found here (under psb-kernel-source): [https://launchpad.net/~lucazade/+archive/gma500/+packages]("https://launchpad.net/%7Elucazade/+archive/gma500/+packages")

Can you please explain more clearly how you made the display to work properly ? :)
Instead of Xubuntu, you should try the moblin edition.

---

### Post by Jonathanius on 2009-10-06
> **Mizukusai said:**
> Instead of Xubuntu, you should try the moblin edition.
Why, isn't Moblin edition only for the Dell?

Unfortunately my computer crashed a few hours after the original post was written, so it may not be the best way to go. I'm still looking for a solution that won't crash. 
I thought this might be a good solution for 2 reasons:
1) It is very similar to the solution on the following thread (post #15): [http://swiss.ubuntuforums.org/showthread.php?p=7781689](http://swiss.ubuntuforums.org/showthread.php?p=7781689)
which cdufour told me in a PM has been working perfectly, without crashing. Unfortunately, I still haven't figured out how to get it to work, even after several attempts, if Karmic keeps crashing I will try it again. He told me to follow recompile my kernel following: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
But I must of been doing something wrong, cause never compiled...
2) I thought, since that solution uses the karmic kernel anyway:
> **cdufour said:**
> GMA500 (on Asus T91) works On Ubuntu 9.04/Jaunty with Ubuntu linux-image-2.6.31-5-generic (from 9.10/Karmic) and psb-kernel-source from Lucazade (THANX MAN!)it might be better just to use Karmic, also that would save us from having to upgrade, and will be supported longer...

> **Mizukusai said:**
> Can you please explain more clearly how you made the display to work properly ? :) 
Here's what I did:
Added the following to the end of my /etc/apt/sources.list file:
```
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main
deb-src http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main
deb http://ppa.launchpad.net/lucazade/gma500/ubuntu karmic main 
deb-src http://ppa.launchpad.net/lucazade/gma500/ubuntu karmic main 
```Authenticated keys:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6699F3D9
```Updated package list and installed needed packages:
```
sudo apt-get update
sudo apt-get install  dkms fakeroot
sudo apt-get install libdrm-poulsbo1
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware
sudo apt-get install psb-kernel-headers psb-kernel-source psb-modules
```Added the following to my /etc/modprobe.d/blacklist.conf file:
```
blacklist i915
```Updated initramfs:
```
sudo update-initramfs -u
```
If you have a /usr/bin/compiz file (I didn't when I was using Xfce, but I switched to Gnome and now I do), whitelist the psb driver by adding psb to the whitelist line, for example:
```
# Driver whitelist
WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx"
```
is what mine looked like before... and 
```
# Driver whitelist
WHITELIST="psb nvidia intel ati radeon radeonhd i810 fglrx"
```
is what it looked like afterward.
Created /etc/X11/xorg.conf and inpasted the following:
```
Section "Device"
        Identifier      "GMA500"
        Option "AccelMethod" "EXA"
        Option "DRI" "on"
        Option "MigrationHeuristic" "greedy"
        Option "IgnoreACPI" "yes"
        Driver "psb"
EndSection

Section "DRI"
    Mode    0666
EndSection
```

---

### Post by Mizukusai on 2009-10-06
Great how-to. Thx.
There is 2 Ubuntu Moblin editions (actually 3)
* by Dell, based on jaunty, with a different kernel
* By Ubuntu, based on karmic (no need to say warning : "beta")

I think, you'll be able to make the last one work properly, with this how-to. I'll try it myself.

---

### Post by Jonathanius on 2009-10-08
The brightness scripts aren't working for me in Karmic, here's what I did, maybe I'm making a mistake somewhere:
-created an  /etc/acpi/brightness.sh
-pasted in bill's script:
> **billl said:**
> 
```

#!/bin/bash

getXdisplay() {
  console=`fgconsole 2> /dev/null`
  DISPLAY=`ps ax | grep -m1 -e "[X] .* vt${console}" | sed -re "s,.*/X .*:([0-9]+).*,:\1,"`
  export DISPLAY
}

getXuser() {
  getXdisplay
  USER=`finger | grep -m1 "${DISPLAY}" | awk '{print $1}'`
  export USER
}

getBrightness() {
  getXuser
  sudo -u ${USER} dbus-send --session --type=method_call --print-reply --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.GetBrightness | tail -n 1 | grep -ow "[[:digit:]]\+"
}

setBrightness() {
  brn=${1}
  [ ${brn} -ge   0 ] || brn=0
  [ ${brn} -le 100 ] || brn=100
  getXuser
  sudo -u ${USER} dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:${brn}
}

incBrightness() {
  level=`getBrightness`
  if [ ${level} -lt 100 ]; then
    setBrightness $((${level} + 5))
  fi
}

decBrightness() {
  level=`getBrightness`
  if [ ${level} -gt 0 ]; then
    setBrightness $((${level} - 5))
  fi
}

BRIGHTNESS_FILE="/var/lib/acpi-support/brightness"
if [ -f "${BRIGHTNESS_FILE}" ]; then
  BRIGHTNESS_OLD=`cat "${BRIGHTNESS_FILE}"`
fi

BRIGHTNESS_NEW=`echo "${3}" | tr "[a-f]" "[A-F]"`

if [ x"${BRIGHTNESS_OLD}" != x"" ]; then
  if [ x"${BRIGHTNESS_NEW}" = x"${BRIGHTNESS_OLD}" ]; then
    if [ x"${BRIGHTNESS_NEW}" = x"0000002F" ]; then
      incBrightness
    elif [ x"${BRIGHTNESS_NEW}" = x"00000020" ]; then
      decBrightness
    fi
  else
    res=`echo "ibase=16; ${BRIGHTNESS_NEW} > ${BRIGHTNESS_OLD}" | bc`
    [ ${res} -eq 1 ] && incBrightness || decBrightness
  fi
fi

echo "${BRIGHTNESS_NEW}" > "${BRIGHTNESS_FILE}"

```
-saved and exited
-made executable:
```
sudo chmod +x /etc/acpi/brightness.sh
```-created a /etc/acpi/events/brightness
-paste in:
```
event=hotkey ATKD 0000002[0-9a-f]
action=/etc/acpi/brightness.sh
```-save and exit
-reboot

I did the exact same thing with Leed's, (after deleting /etc/acpi/brightness.sh and /ect/acpi/events/brightness)

I tried:
```
dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:x
```putting numbers between 0 and 100 in place of x,  I also tried putting in the hexidecimals 00000020 and 0000002F as they were mentioned in bill's script, when testing leed's both a number that showed in the script (0,30,35...) and the corresponding hexidecimal.

also, I tried executing the following commands:
> **billl said:**
> To increase the brightness:
```
sudo brightness.sh hotkey ATKD 0000002f
```To decrease the brightness:
```
sudo brightness.sh hotkey ATKD 00000020
```
but both always returned "command not found " even if i was in the same directory.

There were two other events (with there corresponding .sh files) which I thought might conflict, the events were:
asus-brightness-up:
```

event=hotkey (ATKD|HOTK) 0000001[0123456789abcdef]
action=/etc/acpi/asus-brn-up.sh
```and
asus-brightness-down:
```
event=hotkey (ATKD|HOTK) 0000002[0123456789abcdef]
action=/etc/acpi/asus-brn-down.sh
```the .sh files (asus-brn-down.sh and asus-brn-up.sh):
```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0 
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_BRIGHTNESSDOWN
```and

```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0 
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_BRIGHTNESSUP
```executing:
```
acpi_fakekey 224
```or
```
acpi_fakekey 225
```had no noticeable effect
So I deleted them, but it still didn't work...

Anyone got any ideas? Is this a Karmic thing, or am I doing it incorrectly?

---

### Post by davidjany on 2009-10-09
Guys, have a look at [http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/](http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/). It might worth it - but I can't try it:
- Installation Tips (Swap,...)
- Configure simulated right-click
- Configure laptop-mode with Asus's Super Hybrid Engine

I'm using WinXP again, because I wanted to have full-screen writing capabilities, a good virtual keyboard and some other things and could'nt get them quite as good as WinXP with Touch-It Virtual Keyboard and ritePen Pro (all commercial). 

I'll switch back to linux when it has the same features...

---

### Post by Jonathanius on 2009-10-09
Hey guys, the davidjany's link (to Cedric's aka cdufour's) blog contained a command which worked to change my brightness:
```
xrandr --output LVDS0 --set BACKLIGHT x
```
where x is a number between 100 and 0
...now to make a script that can use it... I tried before to see if the script was triggered by setting the action in the /etc/acpi/events/brightness to launch a script that displayed one of those cool notification things, and the script worked when I executed it directly, but i never got it to launch when a key was pressed, even when trying keys that I knew worked (the rotate button). I don't know any shell so I wasn't surprised. So, could someone who knows what there doing give me a way to test if the event is being triggered? From there concocting a script should be trivial.

---

### Post by Leed on 2009-10-09
Nice work guys, guess I'll check back on that once I switch to Karmic by the End of the month. I read something in the updates, that brightness will be using xrandr. It already works in Jaunty by the way.


Jonathanius
You can type "acpi_listen" in the console to see what the keys trigger

as for the launched script, make sure you have the full path in the command line. The script must also be set as executable... or why not just post your event file

as to see if the script is launched, just place a notify-send command inside the script you want to launch, you don't need to make a new script for it.

---

### Post by Mizukusai on 2009-10-10
Just finished the installation of karmic beta, moblin remix.
Using your instructions. (Thx again!!)

It seems ok but :
> Section "DRI"
    Mode    0666
EndSectionThis section makes Xorg crashes when mutter (moblin interace) starts 
I think the problem is that one :
> (EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.

Without if, Xorg is o, but really really slow.

Any ideas, guys ?

---

### Post by Jonathanius on 2009-10-10
Mizukusai
Personally, I've only ever had crashes when compiz/compositing is on. The Moblin interface is built on Gnome, I believe that in standard Ubuntu Gnome interface, the Extra setting (in the Visual Effects tab of Appearance) uses Compiz -  I installed Compiz Settings Manager and played with it a bit to see if I could get it to crash - it did. So, if the Moblin interface uses any fancy graphics it's probably using Compiz as well.
If you have a /usr/bin/compiz file, you need to whitelist psb by adding "psb" to the WHITELIST line.
When I was using Xfce I didn't even have a /usr/bin/compiz, but now that I've switched to Gnome I do. I had the Visual Effects set to "Normal" for a long time and I didn't ever have  crash, currently I'm using "None" because when I rotate the screen the refresh rate was horrible. 
One more thing, you can try to change the acceleration method from EXA to  UXA, it's supposed to be faster and I remember reading that Karmic uses UXA by default now, but I have not tried it yet.

Leed
Thanks for the tip, the acpi_listen thing worked giving me:
```
hotkey ATKD 00000021 00000005
```for brightness down, and
```
hotkey ATKD 00000022 00000005
```for brightness up, note that the number 00000005 corresponds to how many times I have pressed each key. I tried replacing the asus-brightness-up and asus-brightness-down events that posted in last post, with:
```
event=hotkey ATKD 00000021
action=/etc/acpi/asus-brn-down.sh
```in the /etc/acpi/asus-brn-down.sh I simple put:
```
#!/bin/sh

notify-send -i "/usr/share/icons/gnome/scalable/actions/down.svg", "Brightness" "down" 
```with identical files for brightness up, only with a different key(in the event) and icon and "up" instead of down(in the script). 
But, like last time, if I double click the file or execute it, it does what it supposed to, but doesn't work when the key is pressed.
Any ideas? Thanks so much for all your help so far.

---

### Post by Mizukusai on 2009-10-11
> So, if the Moblin interface uses any fancy graphics it's probably using Compiz as well.
I guess not.
I check in "system->pref->appearances".  It is written "compiz is not installed".
Maybe I should try this one, and modify the WHITELIST variable.
I's worth the try.

---

### Post by Mizukusai on 2009-10-12
No luck.
Thinking about it, compiz and Mutter may use the same functions (3D accel), but they are different softwares.

---

### Post by Jonathanius on 2009-10-12
@Mizukusai
 I started getting quite a few crashes, I'm testing a new config, not sure how stable it is, but will post when I have results. Basically, I disabled compositing in /etc/X11/x.org
```

Section "Extensions"
        Option "Composite" "off"
EndSection
```

Still, don't know if it will help...

---

### Post by Mizukusai on 2009-10-16
With this option off, the X does not crash anymore because the session does not completly start. It stops with a black screen, with the b&w mouse cursor (functionning).
I think compositing is mandatory.

---

### Post by davidjany on 2009-10-16
> **Jonathanius said:**
> 
in the /etc/acpi/asus-brn-down.sh I simple put:
```
#!/bin/sh

notify-send -i "/usr/share/icons/gnome/scalable/actions/down.svg", "Brightness" "down" 
```with identical files for brightness up, only with a different key(in the event) and icon and "up" instead of down(in the script). 
But, like last time, if I double click the file or execute it, it does what it supposed to, but doesn't work when the key is pressed.
Any ideas? Thanks so much for all your help so far.

It's because these keys are not handled by xorg. You can either use the acpi events without xorg binding, try to connect to xorg within your script (I tried it unsuccessfully) or get xorg to recognize the key and use gnome-keybinding-properties to run your job. 

After unsuccessfully trying to connect to xorg within a script, I've tried a mixture of using acpi events and gnome keybindings. I used keybindings to show the changing in display orientation while pressing the key. After releasing the key an acpi event was planned to read and change towards the aimed orientation. But my attempts were without success and I had no time to try it further.

This might help you:
- [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)
- [http://www.howtoforge.de/howto/wie-du-die-funktionstasten-deines-laptops-auf-fedora-aktivierst/](http://www.howtoforge.de/howto/wie-du-die-funktionstasten-deines-laptops-auf-fedora-aktivierst/) (german!)

---

### Post by Mizukusai on 2009-10-20
I found that Intel was not the designer of the GMA 500. It was bought, by Intel, but not designed. They use the "historical" drivers made by the designers. This is why the current driver is "not too good".
Intel designed the GMA950 and their drivers. Moblin is not supported on the GMA 500, but i think it is on GMA 950.

I'm quite pessimistic about moblin on my T91. :( (really really sad)

---

### Post by Mizukusai on 2009-10-21
I've upgraded the jaunty I had in dual boot to karmic. Good News, mutter starts quite well. But, the moblin applications (myZone, ...) are not available. I found a ppa from a "Moblin Hackers team". 
A lot of packages seem to broken.

---

### Post by Mizukusai on 2009-10-22
I've dropped the idea of getting Moblin working, for now.
Following the previous how-to, i've installed Karmic NR. It works great but : 

* Sometimes the sound stops working.
* H264 videos are "jerky". Sound/video are not synchronous, and there is a lot of framedrop. But the graphical chipset is supposed to be able to decode it at a hardware level, isn't it ? Re-encoding them with avidemux solve the pb, but it is a bit long.
* When resuming after hibernate, netbook-launcher crashes, each time.
* Graphical performances are bad when the screen is rotated. I won't be using it anyway.

I'm thinking of writing a script launched by the "bellow the screen EEPC button". It will detect the position of the mouse, and make a virtual keyboard (like cellwriter) appear at the place where it is not disturbing.

---

### Post by Jonathanius on 2009-10-22
> **Mizukusai said:**
> I've dropped the idea of getting Moblin working, for now.
Following the previous how-to, i've installed Karmic NR. It works great but : 

* Sometimes the sound stops working.
* H264 videos are "jerky". Sound/video are not synchronous, and there is a lot of framedrop. But the graphical chipset is supposed to be able to decode it at a hardware level, isn't it ? Re-encoding them with avidemux solve the pb, but it is a bit long.
* When resuming after hibernate, netbook-launcher crashes, each time.
* Graphical performances are bad when the screen is rotated. I won't be using it anyway.

I'm thinking of writing a script launched by the "bellow the screen EEPC button". It will detect the position of the mouse, and make a virtual keyboard (like cellwriter) appear at the place where it is not disturbing.

The main issues for me were the sound and performance when rotated. Another thing I had problems with was Wifi, at first it was great but then it completely stopped working: randomly stopped and refused to reconnect, also, if turned off an on several times says: "device not ready"
Thats why I uninstalled Karmic(using jaunty and F11), it's not ready yet... RC comes out today, wonder if it will be any better... otherwise maybe we could all move to Fedora =P(if it behaves any better), the main reason I'm using Ubuntu is because of this forum(and it's Debian based) - there are lots of other people to help out, etc. But I have never had a configuration in which I could not get Xorg to crash after using the touchscreen with Compiz...

---

### Post by Mizukusai on 2009-10-22
The problems encountered are either : 
* little ones (hibernate issue)
* not depending on ubuntu (psb driver issue)

I think the sound problem can be easily corrected.

---

### Post by Jonathanius on 2009-10-22
> **Mizukusai said:**
> The problems encountered are either : 
* little ones (hibernate issue)
* not depending on ubuntu (psb driver issue)

I think the sound problem can be easily corrected.

You think that it's the fault of the psb driver? It doesn't crash in Windows, so it would be a problem with the Linux one, which was taken originally from 8.04, and made to work with jaunty, karmic and fedora 11... if it is a problem in the closed-source part, then none of our configs will work, no matter what distro or version we use. I really hope that's not the case. 
One of the things it might be is the touchscreen driver, because I've never had a crash when I'm using the trackpad, only with the touchscreen.

---

### Post by Kapitän Rotbart on 2009-10-22
Anyone try the release candidate? What are the steps to take to make Karmic work on the t91?

---

### Post by Mizukusai on 2009-10-23
[http://ubuntuforums.org/showpost.php?p=8061498&postcount=91](http://ubuntuforums.org/showpost.php?p=8061498&postcount=91)
This one is good.

---

### Post by Kapitän Rotbart on 2009-10-23
Yeah, that was a good post. I tried the live session in Jaunty (desktop edition) and (as I anticipated) the WLAN didn't work, however the touch screen did work (though it wasn't calibrated). I just tried Karmic RC UNR and the WLAN works out of the box (w00t) but no touch screen. Will touch screen be enabled once the graphics are properly configured? Also will the native screen resolution be resolved once configured? Are there any issues with the UNR on this netbook? I'm going to wait for release to install Karmic, so I'll just be using the live session on the t91 until then.

Say, is there any reason I have to keep Windows XP on that machine? I checked and my t91 already has the latest BIOS version (I can't see them updating the BIOS for this machine anymore seeing as the BIOS works fine and the Multi Touch t91 will be coming soon, I've not once heard of BIOS issues with Ubuntu and guess I could install BIOS updates via FreeDOS or Windows PE if need be).

---

### Post by Mizukusai on 2009-10-23
Touchscreen works just fine, once the xserver-xorg-input-evtouch is installed.
The only reason to keep Windows, is that you "want" it :D

Last Update : I have no more crash at all since upgrading to Karmic.
EEEbuntu developper might have said that Ubuntu sucks, but it works. :D

---

### Post by Jonathanius on 2009-10-23
> **Mizukusai said:**
> Touchscreen works just fine, once the xserver-xorg-input-evtouch is installed.
The only reason to keep Windows, is that you "want" it :D

Last Update : I have no more crash at all since upgrading to Karmic.
EEEbuntu developer might have said that Ubuntu sucks, but it works. :D
No crashes, at all? Are you using the config from my post? Or a different one? Also, which Ubuntu version are you using - UNR, Desktop or something else? I've been really busy lately, but I'll try it first change I get. :)

---

### Post by Kapitän Rotbart on 2009-10-23
Not that I want windows, I mean after reading the eee pc user forum, seems like the XP OEM is heavily bloated, and that I'd be better off installing XP or se7en retail and then installing the drivers myself than using the XP Home OEM...not that I'd want to do this, as I do want a Linux-only t91.

Still some questions though...
- In the live session I get an 800x600 resolution (Karmic RC UNR) and no touch screen. Will the proper resolution be fixed automatically once the drivers are correctly installed? Is there a reason UNR doesn't ship with *xserver-xorg-input-evtouch*?
- Are you using/have you tried the UNR and if so, are there any issues with the netbook remix on the t91?

---

### Post by Leed on 2009-10-23
Just did the update to the 16 Kernel, it's not enough to just repatch the kernel via 
sudo apt-get install psb-kernel-source

you'll need to 
sudo apt-get remove psb-kernel-source 

first

---

### Post by Kapitän Rotbart on 2009-10-25
Say, what filesystems do you Karmic users use on the t91?

I am concerned, because AFAIK SSD's cannot handle filesystems with file journaling. I know ext2 works, but it's so much slower than ext4. Has anyone tried ext4 on the t91's SSD, and ran the updates via the update manager or synaptic (including kernel updates) flawlessly? Are there any ways of using ext4 without file journaling via parameters or anything like that? I'd really appreciate a heads up on which filesystem to use.

---

### Post by xyzo on 2009-10-26
> **Leed said:**
> Just did the update to the 16 Kernel, it's not enough to just repatch the kernel via 
sudo apt-get install psb-kernel-source

you'll need to 
sudo apt-get remove psb-kernel-source 

first
My own experience. This was enough to make -16 kernel working well on my T91:
sudo dpkg-reconfigure psb-kernel-source
HTH.

---

### Post by Mizukusai on 2009-10-26
> **Kapitän Rotbart said:**
> Say, what filesystems do you Karmic users use on the t91?

I am concerned, because AFAIK SSD's cannot handle filesystems with file journaling. I know ext2 works, but it's so much slower than ext4. Has anyone tried ext4 on the t91's SSD, and ran the updates via the update manager or synaptic (including kernel updates) flawlessly? Are there any ways of using ext4 without file journaling via parameters or anything like that? I'd really appreciate a heads up on which filesystem to use.

It's ok here with ext4.
Can you be more specific about the issue on SSD with ext4 ?

---

### Post by Kapitän Rotbart on 2009-10-26
Maybe I'm just paranoid, but here's the deal...

Back when I installed Ubuntu 8.04 Hardy (ubuntu-eee, actually...now known as EasyPeasy) on an Acer Aspire One (pretty cool netbook, btw...I didn't want it because I wanted to wait for a touchscreen netbook to come along, but it has two SD memory card readers and it's really affordable), I tried first installing it on a ReiserFS filesystem (it was recommended on some website for some reason). I know ReiserFS is by no means a new filesystem, but I gave it a try. The install itself would be fine, but once I'd run the updates and restart, the OS wouldn't load and it claimed that the SSD was corrupt. Took me a while to figure out that the filesystem was the issue. I'd have to reformat using the Limpus recovery disc each time (Limpus uses ext2). Eventually I just used ext2 and everything worked fine. I just installed Karmic RC on that AA1 using ext2 and it works flawlessly, though I'd love to use ext4 if it'll be just as reliable plus faster.

I don't have a recovery disc for the t91 (just that disc that came with it which I believe has the XP drivers), so I don't want to risk a repeat of the experience I had with a journaling filesystem on SSD. If you say you've installed Karmic on ext4, ran the updates, restarted the t91 and everything went flawless, then I'll do it :D

Also, do y'all set up a SWAP partition on the t91? I have upgraded mine to 2GB RAM so I think 4GB SWAP would be a little much for an SSD of 16GB. Any thoughts?

---

### Post by Jonathanius on 2009-10-28
Karmic comes out tomorrow,(w00t) for anyone who has used karmic, would you recommend, Ubuntu UNR or Desktop? Has anyone had any problems with Xorg crashing when using the touchscreen? And if so, what's in your xorg.conf?

---

### Post by Mizukusai on 2009-10-28
> **Jonathanius said:**
> Karmic comes out tomorrow,(w00t) for anyone who has used karmic, would you recommend, Ubuntu UNR or Desktop? Has anyone had any problems with Xorg crashing when using the touchscreen? And if so, what's in your xorg.conf?

Currently using NBR, with the the how-to from above. No X crash, or freeze so far.

---

### Post by Kapitän Rotbart on 2009-10-29
I hear you can install compiz with the netbook remix in Karmic now. Has anyone tested the release of UNR 9.10 Karmic with compiz on the t91? T'would be slick, I can't really stand the min/max windows animation without compiz (it's too XP style and I don't even know how to disable it in Gnome :o )

---

### Post by Mizukusai on 2009-10-30
I've heard sonething [different]("http://forum.eeebuntu.org/viewtopic.php?f=46&t=3263").
NB : eeebuntu is not based on Karmic.
[]("http://forum.eeebuntu.org/viewtopic.php?f=46&t=3263")

---

### Post by Kapitän Rotbart on 2009-10-31
> **Mizukusai said:**
> I've heard sonething [different]("http://forum.eeebuntu.org/viewtopic.php?f=46&t=3263").
NB : eeebuntu is not based on Karmic.
[]("http://forum.eeebuntu.org/viewtopic.php?f=46&t=3263")

Eeebuntu will be switching over to Debian Unstable-based instead of Ubuntu-based in their next version.

OMG! Ubuntu! claims that compiz is now compatible with the netbook remix: [http://www.omgubuntu.co.uk/2009/10/quick-visual-tour-of-ubuntu-karmic.html]("http://www.omgubuntu.co.uk/2009/10/quick-visual-tour-of-ubuntu-karmic.html")

---

### Post by Kapitän Rotbart on 2009-10-31
OMG! Kamoso works with the webcam on the t91! I haven't tried Skype yet (which also apparently works), but at least I know Kamoso works.

The webcam is at /dev/video0. I'm going to try some other things including EasyCam, hopefully it'll work.

---

### Post by Leed on 2009-11-01
After big disappointments with Karmic I'm postponing the update on my T91... after all that Netbook is delicate enough without taking chances

---

### Post by Kapitän Rotbart on 2009-11-02
How do I fix the screen resolution? I used the gma 500 PPA (and added other Karmic PPA's to get the dependencies) - [https://launchpad.net/~lucazade/+archive/gma500]("https://launchpad.net/~lucazade/+archive/gma500"). It pretty much contains the same poulsbo packages as that jaunty repository, plus a modified kernel, but I still haven't managed to fix the screen resolution. Is there a way to do it? Am I missing something?

Edit: I blacklisted i915 and I set xorg.conf as stated in the instructions posted earlier in this thread, and the screen resolution now works properly.

Also, my netbook-launcher doesn't work. It's not that big a deal, I just use Alt+F1 to access the menus anyway, but still...

How exactly do I calibrate the touch screen now that I have that working?
Edit: I found the "calibrate touchscreen" under Sys>Prefs

Has anyone got the screen rotate button to work in Karmic and if so, what's the trick?

Please help.

---

### Post by Kapitän Rotbart on 2009-11-07
Say, I was trying to use EasyStroke but I couldn't get it to recognize my strokes using the touch screen (or even the touch pad for that matter). How do I get EasyStroke to recognize my "strokes"?

---

### Post by DrPotoroo on 2009-11-07
> **Kapitän Rotbart said:**
> Say, I was trying to use EasyStroke but I couldn't get it to recognize my strokes using the touch screen (or even the touch pad for that matter). How do I get EasyStroke to recognize my "strokes"?

Have you set up a gesture button? You need some key combination in the settings to tell the program when it should treat strokes as shortcuts and not just moving the pointer around. Unfortunately I can't get it to use that little screen rotate button, so it isn't much use in tablet mode. Unless someone has a trick for that I haven't thought of.

Thanks to everyone who has contributed to this thread. It has meant I've gotten my new t91 all set up and working with UNR karmic without much hassle. This thing ran like a sloth with the xp install it came with, but UNR performance is quite passable (once the graphics driver is installed).

---

### Post by dfauvarq on 2009-11-08
FYI,

I've managed to have a stable wifi connection using the ndiswrapper and the drivers provided by Asus on Windows (netathw)

My feeling is that the default Ubuntu driver doesn't configure the wireless board to use enough power to get a stable connection. At the same location in the house in one case I have more than 50% but 25% with the other driver

Daniel

---

### Post by pinkflamingo8806 on 2009-11-08
This thread has been extremely helpful with my new t91.  I have been trying it out with Fedora and everything works except the touch screen.  I tried evtouch but every time I reboot psb overwrites my xorg.conf.  Any suggestions?  I tried doing ```
livna-config-display --active off
``` but then something else overwrites the xorg.conf and puts VESA stuff in it.

thanks

---

### Post by xyzo on 2009-11-08
Hi!
I'm upgrading to UNR 9.10 (Karmic Koala) but the touchscreen is not working at all while it was enabled out of the box by Jaunty: any clue?
TIA.

---

### Post by Mizukusai on 2009-11-09
> sudo apt-get install xorg-xserver-input-evtouch
Then reboot
To calibrate touchscreen, do it with no X launched.

---

### Post by DrPotoroo on 2009-11-12
I've been using Ubuntu netbook remix 9.10 (Karmic) for a little while now. Mostly everything is working perfectly. I do get the occasional crashes, though. The main one is when I resume from sleep - the system resumes okay most times and I can continue working and saving documents. However, the launcher is unresponsive so if I switch to it I then can't do anything much. At that point the power slider will successfully bring up the shutdown options, and shutdown appears to happen correctly after asking to kill the launcher. However, on next boot fdisk runs. If I try to crtl+alt+f1 to kill the launcher, everything crashes and only REISUB will let me shutdown. Interestingly, sometimes after REISUB it starts without needing a disk check, unlike shutting down through the menu.
 
Addit: I should have mentioned that the resume crash I described started after I installed the graphics driver.

---

### Post by Mizukusai on 2009-11-12
yes, i have the same suspend/hibernate issue.

---

### Post by Perig on 2009-11-12
idem!
:(

---

### Post by xyzo on 2009-11-22
> **Leed said:**
> Thanks for the input billl. I'm afraid your script didn't work on my machine, but it gave me the input to solve the problem using a more simple (or primitive) code. I just changed the following:

/etc/acpi/events/brightness
```
# /etc/acpi/events/brightness
# called when used brightness keys

event=hotkey ATKD 0000002[0-9a-f]
action=/etc/acpi/brightness.sh %e
```/etc/acpi/brightness.sh
```
#!/bin/bash
getXdisplay() {
  console=`fgconsole 2> /dev/null`
  DISPLAY=`ps ax | grep -m1 -e "[X] .* vt${console}" | sed -re "s,.*/X .*:([0-9]+).*,:\1,"`
  export DISPLAY
}

getXuser() {
  getXdisplay
  USER=`finger | grep -m1 "${DISPLAY}" | awk '{print $1}'`
  export USER
}

  case $3 in 
    00000020)
    brn=0
    ;;
    00000021)
    brn=30
    ;;
    00000022)
    brn=35
    ;;
    00000023)
    brn=40
    ;;
    00000024)
    brn=45
    ;;
    00000025)
    brn=50
    ;;
    00000026)
    brn=55
    ;;
    00000027)
    brn=60
    ;;
    00000028)
    brn=65
    ;;
    00000029)
    brn=70
    ;;
    0000002a)
    brn=75
    ;;
    0000002b)
    brn=80
    ;;
    0000002c)
    brn=85
    ;;
    0000002d)
    brn=90
    ;;
    0000002e)
    brn=95
    ;;
    *)
    brn=100
    ;;
  esac
  getXuser
  sudo -u ${USER} dbus-send --session --type=method_call --dest=org.freedesktop.PowerManagement /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:$brn
```The only snag is, the power management icon appears a second time in the top bar, I suppose this has something to do with me not getting the user, but the suggested sudo -u ${user} in combination with getXuser and getXdisplay doest n't work on my system.
Hi!
This was working flawless with Jaunty but it is not working anymore on my T91 running Karmic (UNR 9.10): any clue?
Thanks in advance!

---

### Post by protman on 2009-11-24
Has anyone clue whose display t91 uses? I think of "get-edid | parse-edid" output.

---

### Post by Kapitän Rotbart on 2009-11-24
> **DrPotoroo said:**
> Have you set up a gesture button? You need some key combination in the settings to tell the program when it should treat strokes as shortcuts and not just moving the pointer around. Unfortunately I can't get it to use that little screen rotate button, so it isn't much use in tablet mode. Unless someone has a trick for that I haven't thought of.
I just had to switch the gesture button to button 1 in the prefs.

Say, I can't seem to boot 2.6.31-15 kernel build from the updates...has anyone else been able to boot it? Should I get the PAE build from the PPA's?

---

### Post by yigal.weinstein on 2009-11-27
I need help getting the touchscreen working on the t91mt.  I've included out from lsusb -v, lspci -vv, and lshal in one bunzipped and tarred file.  I don't think the t91mt uses evtouch, as it isn't mentioned in any hardware detection.

However the touchscreen is detected and is found in device:

/dev/usb/hiddev0

so that if one does a ```
cat /dev/usb/hiddev0
``` and touch the screen there is a response, but I can't configure the device nor does Ubuntu configure it automatically.

OS: Ubuntu 9.10
kernel: 2.6.31-15-generic
video: psb driver

thank you

---

### Post by jamespcole on 2009-11-30
For anyone wanting to get the Asus T91 working i have made step by step guides on my blog.

Fix Wireless Dropouts:
[http://setupguides.blogspot.com/2009/11/fixing-wireless-network-card-for-asus.html]("http://setupguides.blogspot.com/2009/11/fixing-wireless-network-card-for-asus.html")

Fix Screen Resolution
[http://setupguides.blogspot.com/2009/11/fixing-screen-resolution-for-asus-eee.html]("http://setupguides.blogspot.com/2009/11/fixing-screen-resolution-for-asus-eee.html")

Touchscreen
[http://setupguides.blogspot.com/2009/11/touchscreen.html]("http://setupguides.blogspot.com/2009/11/touchscreen.html")

Enabling Compiz
[http://setupguides.blogspot.com/2009/11/desktop-effects-and-compiz-for-asus-eee.html]("http://setupguides.blogspot.com/2009/11/desktop-effects-and-compiz-for-asus-eee.html")

Note: after enabling compiz some hd video is jerky, if you turn off compiz it works very smoothly, if anyone finds a solution to this please let me know.  If i figure it out i'll make another blog post

Hope this helps, i'm really liking my new T91 and Karmic.

EDIT:upgrade to 2.6.31-16-generic before installing the psb modules

---

### Post by Mizukusai on 2009-11-30
Thanks, but you offer nothing new. We already had these.;)
And even more, actually.

Netbook-naucher freezes after hibernate/suspend. Do you have anything about that ?

---

### Post by jamespcole on 2009-11-30
> **Mizukusai said:**
> Thanks, but you offer nothing new. We already had these.;)
And even more, actually.

Netbook-naucher freezes after hibernate/suspend. Do you have anything about that ?

Yeah i know, but i couldn't find a concise step by step guide for these things(let me know if there is one and i'll put up a link) figured i'd save people having to read through 15 pages of posts to get the basics working(and also so i don't need to next time i do a re-install)

not sure about the hibernate and suspend, i'll have to suss it out.  Have you had any luck getting video to play smoothly under compiz?  I'm not really fussed about having suspend and hibernate but the poor video playback is really annoying.  So if you make any progress let me know.

---

### Post by pinkflamingo8806 on 2009-12-01
Anyone still having those random freezes?  I get them in the middle of class when I'm taking notes using Xournal.  I'm running UNR Karmic.

---

### Post by yigal.weinstein on 2009-12-01
@my t91mt issue, ASUS appears unwilling to share either hardware specs or driver specs with anyone.  I personally tried to get information from them and was called at 6am - though I had requested to receive an email - that the driver was proprietary, which was obvious before I had made the effort of contacting them.

In any event hopefully there's a solution.

@provs: t91 yes, t91mt NOOO

to be fare everything on the t91mt works except the touchscreen ( and hibernation issues like t91).

> **proverbs308 said:**
> I have been considering buying the T91 but was wondering if anyone has successfully installed linux on it.  If I bought it would the touchscreen work or would I be stuck with Windows?

---

### Post by bennett on 2009-12-04
Re: touchscreen configuration:
Hey, your directions for calibrating the touchscreen were fantastic. I have been trying to calibrate my t91 ever since I got it. I am running eeebuntu 3.0 (base) which is a form of Jaunty (not Karmic) so I wasn't sure it would work. I do have the jaunty-backports installed but I can't seem to get any screen resolution other than 800x600 but it worked fine anyway. 

Some other notes: Following the directions, I ran the stylus all around the edge of the screen but the little Xs never did turn red. Nevertheless, I tapped on the centre of each one, beginning in the top row, going L---> R, then the mid-row, then the bottom. I did this quite quickly. You really have to be careful that the side of your hand does not touch the screen while you're doing this. Once  I had tapped the last X, the utility closed & I ran the startx command. When I returned to the X environment, the screen calibration was RIGHT ON for the first time!!! Thanks a lot.
Now, if only  I could get the wireless running properly...

---

### Post by bennett on 2009-12-10
I got an error message when attempting to build the ndiswrapper module. Can you say more about how you got it to work?

TIA

---

### Post by Jonathanius on 2009-12-11
> **bennett said:**
> I got an error message when attempting to build the ndiswrapper module. Can you say more about how you got it to work?

TIA

You may want to use Wicd instead, I was having all kinds of problems with wireless when I was using NetworkManager with the normal driver, so I installed Wicd instead and it fixed everything.

---

### Post by Jonathanius on 2009-12-11
Anyone tried Jolicloud pre-beta? Its based on Jaunty UNR and the site lists the T91 as a supported model, the touchscreen works - without the evtouch drive - but I'm not sure how to calibrate it, any ideas?

---

### Post by bennett on 2009-12-20
I have been trying wicd, then back to network-manager, back & forth with lousy results. The ath9k driver works in a so-so way with network-manager but I have to be almost sitting on top of the router to get decent wireless speed. I have read that ndiswrapper is a better wireless driver but can't get it to load (modprobe ndiswrapper gives all sorts of error messages no matter which directions I follow). I have been scratching away at this for a month. Can you tell me which driver you are using? Whether the wifi works as well as it does in windows?
Thanks a lot for your help.

---

### Post by DrPotoroo on 2009-12-23
> **pinkflamingo8806 said:**
> Anyone still having those random freezes? I get them in the middle of class when I'm taking notes using Xournal. I'm running UNR Karmic.
 
I'm also running UNR Karmic. I don't get very many random freezes - mostly mine are predictable. The main issue seems to be after the machine is woken from sleep/hibernate it will crash as soon as you switch to the launcher (only if you've updated the graphics driver to give your 1024x600 resolution). I suspect the real problem is something to do with certain graphical functions because certain other actions will cause a crash after sleep. So far I've noticed that rotating the screen orientation, using opengl functions and switching something like mplayer to full screen seem to cause crashes if the t91 has previously been in sleep mode.

---

### Post by kgingeri on 2009-12-24
> **jamespcole said:**
> For anyone wanting to get the Asus T91 working i have made step by step guides on my blog.

Fix Wireless Dropouts:
[http://setupguides.blogspot.com/2009/11/fixing-wireless-network-card-for-asus.html]("http://setupguides.blogspot.com/2009/11/fixing-wireless-network-card-for-asus.html")

Fix Screen Resolution
[http://setupguides.blogspot.com/2009/11/fixing-screen-resolution-for-asus-eee.html]("http://setupguides.blogspot.com/2009/11/fixing-screen-resolution-for-asus-eee.html")

Touchscreen
[http://setupguides.blogspot.com/2009/11/touchscreen.html]("http://setupguides.blogspot.com/2009/11/touchscreen.html")

Enabling Compiz
[http://setupguides.blogspot.com/2009/11/desktop-effects-and-compiz-for-asus-eee.html]("http://setupguides.blogspot.com/2009/11/desktop-effects-and-compiz-for-asus-eee.html")

Note: after enabling compiz some hd video is jerky, if you turn off compiz it works very smoothly, if anyone finds a solution to this please let me know.  If i figure it out i'll make another blog post

Hope this helps, i'm really liking my new T91 and Karmic.

EDIT:The psb drivers will fail badly if you upgrade the kernel to 2.6.31-15-generic, stay with 2.6.31-14-generic.  There is an issue with the psb drivers and the 2.6.31-15-generic kernel, i haven't found any or come up with any fixes yet so if you do please post it

Thanks James, these are the first instructions that worked for me.  I have a T91MT running Karmic 17, and could not install any psb stuff without it wanting to remove half the system!

I have noticed that I always have to use the Fn+F2 keys to kick-in wireless - after any reboot.  The LED is always on solid, but the radio is off by default. I'm sure there's a line to put into rc.local to fix it but I really just need my screen and touch working first.

Off to test some more...

---

### Post by jamespcole on 2009-12-26
> **kgingeri said:**
> Thanks James, these are the first instructions that worked for me.  I have a T91MT running Karmic 17, and could not install any psb stuff without it wanting to remove half the system!

I have noticed that I always have to use the Fn+F2 keys to kick-in wireless - after any reboot.  The LED is always on solid, but the radio is off by default. I'm sure there's a line to put into rc.local to fix it but I really just need my screen and touch working first.

Off to test some more...

No problem, glad it helped.  BTW i have tried all my instructions against the 2.6.31-16-generic kernel and everything works.  Just did a fresh install followed by a kernel update before doing them.  Also with the wireless LED, i am not experiencing that problem however after turning the wireless off and then on again it will not connect to my network.  I don't have the MT version but i'd be interested to know how the Multi touch goes.

---

### Post by jamespcole on 2009-12-26
> **Mizukusai said:**
> Thanks, but you offer nothing new. We already had these.;)
And even more, actually.

Netbook-naucher freezes after hibernate/suspend. Do you have anything about that ?

after upgrading to 2.6.31-16-generic suspend and hibernate are both working for me.

---

### Post by kgingeri on 2009-12-27
Ok, I'm not sure if a new thread should be started for the T91MT but I'm starting to realize there are differences.  

The touch-screen is definitely different.  It is reported to be AsusTek - not another supplier (could Asus really have built their own?) anyway, it also behaves like a 'resistive' touch rather then 'capacitive' - if I understand the differences.  I can activate 'touch' with any object (doesn't have to be my finger) and it's pressure sensitive.  I'm having a hard time find a spec that says what it is. 

The T91MT also comes with Win7 Home which is a far cry from the Win7 Starter Edition!  However, I still can't stand being in Windows long.  I like to actually get things done with my computer not just click thru pretty menus and options  ;)

Multitouch support for the T91MT seems brand-new!  I have gotten as far as having un-calibrated single-touch, and I'll post steps below.

I am running Karmic 2.6.32-17 - the latest as of this post - and I have no idea if this will work for anything else.  Most of this comes from SamT91MT over in the Asus Support forum and I'm not sure you can get [there]("http://vip.asus.com/forum/view.aspx?id=20091214162901203&SLanguage=en-us&page=1&board_id=20&model=Eee%20PC%20T91MT") without an account. Also the source below is from SamT91MT.  I may attempt some mods to it to get calibration working, but I may get nowhere as well :D

*(remember, I'm running Karmic 2.6.31-17, so your "mileage" [results] may vary ;)*

Nough background, now the goods...  These are the steps. I will attach files needed.  This is all using mods to source for the evtouch driver:

   [INDENT]1. Install the video psb drivers via instructions [here]("http://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic") (Ubuntu Wiki) - although I had better luck with this [blog post]("http://setupguides.blogspot.com/2009/11/fixing-screen-resolution-for-asus-eee.html")
   2. do "sudo apt-get install xserver-xorg-input-evtouch"
   3. you may need kernel source? Not sure about this - I did install it via Synaptics Package Manager so I could do a "make clean; make" to rebuild from source
   4. download the source/binaries from the attachment below (there is no need to recompile, only if you want to 'play' with code)
   5. do "tar -xvzf xf86-input-evtouch-0.8.8.orig.eeeT91MT.tar.gz"
   6. do "cd xf86-input-evtouch-0.8.8.orig.eeeT91MT"
   7. NOTE: at this point you could do a "make clean; make" to rebuild binaries - I believe
   8. do "sudo cp /usr/lib/xorg/modules/input/evtouch_drv.so /usr/lib/xorg/modules/input/evtouch_drv.so.save"
   9. do "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.save"
  10. do "sudo cp ./.libs/evtouch_drv.so  /usr/lib/xorg/modules/input/evtouch_drv.so" - NOTE: the .libs directory is hidden from an "ls" cmd - use "ls -a" to see it, or just "cd .libs" to look around.
  11. do "sudo cp ./xorg.conf /etc/X11/" (you didn't even have an xorg.conf until after you installed the psb video stuff)
  12. Shutdown and restart and you should have good screen resolution and some single touch activity.[/INDENT]

EDIT: Yeah your reading right - 'xf86...' - not to fear, it's modified to work with Xorg.

EDIT/UPDATE:
Calibration may not work BUT I found that if I used the following xorg.conf values I don't need it:

    Option "MinX" "0"
    Option "MinY" "0"
    Option "MaxX" "3475"
    Option "MaxY" "3475"

I am getting freeze-ups tho - nothing but a held power button to power off works  :(

[COLOR="Green"]EDIT/UPDATE (Mar 8th):  
I have a very stable T91MT with almost everything working - even sleep.  I did get calibration to work but it seemed to mess up more then it fixed.  
[LIST]
[*]I now use an fdi file for touch instead of xorg.conf (see xorg.conf attached for other settings).  It's put in (note path!) /usr/share/hal/fdi/policy/20thirdparty - see the attached - the T91MT uses evtouch for Xorg GUI stuff
[*]Also synaptics updates for 2 finger scrolling etc.  
[*]I have no multi-touch on the screen yet, BUT I haven't tried that much as it's no big deal for me.
[*]I've icluded another copy of the xf86 tar file, it's the latest I've used.  If you update to a new kernel, you'll need to run the following to re-establish touch - or is it the display... (you'll need to install poulsbo psb-kernel-headers and psb-kernel-source for display updates - info elsewhere here)
```
sudo dpkg-reconfigure psb-kernel-source
[*]sudo update-grub
```
[*]Also a copy of /etc/udev/rules.d/69-touchscreen.rules - used to set up devices for X.
[*]Strip off the ".txt" - I added them to be able to upload here only
[*] start about post [#215]("http://ubuntuforums.org/showpost.php?p=8916737&postcount=215") for more info or try this [blog]("http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html") or this  [blog]("http://binken.org/wordpress/?p=476") - a work in progress at this point :)
[*] and one more - grub, the boot manager. My current mods to /etc/default/grub are in the GRUB_CMDLINE_LINUX_DEFAULT line: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash mem=786mb pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=noop acpi_backlight=vendor"
``` ...(do 'sudo update-grub' after edits). These are for display mem reserved, display speed mods or sleep (can't remember), SSD saver and enabling backlight keys Fn+F3/F4.
[/COLOR]
[/LIST]

---

### Post by DrPotoroo on 2009-12-29
After a bit of fiddling I was able to upgrade to kernel 2.6.31-16 without starting from a clean install. I updated with the update tool, then tried to repeat the steps described earlier in this thread for installing the poulsbo driver before rebooting. That failed, but after removing the package psb-kernel-source it worked.

I still get crashes after waking from sleep. Also, for future kernel updates to not cripple me so much before I can redo the graphics driver, does anyone know how to enable the grub menu? I kew how to do it in other linux distros but can't seem to with UNR.

---

### Post by jamespcole on 2009-12-29
For those of you having trouble using your microphone in skype I have written up a quick blog post about getting it working.

[http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html]("http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html")

I had tried some other solutions first(upgraded alsa to 1.0.21) so without doing a fresh install I can't guarantee this will work for you(although I am pretty sure it will).  If it doesn't work for you please let me know and i will revise my post.

---

### Post by kgingeri on 2009-12-29
> **DrPotoroo said:**
> After a bit of fiddling I was able to upgrade to kernel 2.6.31-16 without starting from a clean install. I updated with the update tool, then tried to repeat the steps described earlier in this thread for installing the poulsbo driver before rebooting. That failed, but after removing the package psb-kernel-source it worked.

I still get crashes after waking from sleep. Also, for future kernel updates to not cripple me so much before I can redo the graphics driver, does anyone know how to enable the grub menu? I kew how to do it in other linux distros but can't seem to with UNR.

Hi DrPotoroo,

To change Grub, edit /etc/default/grub, with your favorite text editor to be what you want, then run 'update-grub'.  It will find all kernels you have active and rewrite /boot/grub/grub.cfg which is now the grub param file used at boot time.

---

### Post by kgingeri on 2009-12-29
> **jamespcole said:**
> For those of you having trouble using your microphone in skype I have written up a quick blog post about getting it working.

[http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html]("http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html")

I had tried some other solutions first(upgraded alsa to 1.0.21) so without doing a fresh install I can't guarantee this will work for you(although I am pretty sure it will).  If it doesn't work for you please let me know and i will revise my post.

Hi James,  I had no luck with that (I posted on your blog also).  I found that pavucontrol was not installed (UNR 2.6.31-17) but it didn't offer me anthing different then right-clicking the volume applet icon and going to preferences.  It also seems my output volume is now very faint - no matter what the settings.  Not sure if I need another reboot or what.  :/

---

### Post by jamespcole on 2009-12-30
Hi kgingeri,
just out of interest what is the output of this command for you?

cat /proc/asound/version

i get 

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec  2 2009 for kernel 2.6.31-16-generic (SMP).

so it may be that you need to upgrade alsa, this will install the latest alsa

sudo add-apt-repository ppa:ricotz/unstable

sudo apt-get update && sudo apt-get upgrade

thanks to [http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html]("http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html")
for the alsa instructions.

Sorry it wasn't working for you, as i said earlier i had been messing with the sound settings etc for a while before i got it working, thanks for the feedback, i'm  considering doing another fresh install to figure out the exact steps i took.  Let me know if the alsa upgrade makes any difference.

---

### Post by kgingeri on 2009-12-30
> **jamespcole said:**
> Hi kgingeri,
just out of interest what is the output of this command for you?

cat /proc/asound/version

i get 

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec  2 2009 for kernel 2.6.31-16-generic (SMP).

so it may be that you need to upgrade alsa, this will install the latest alsa

sudo add-apt-repository ppa:ricotz/unstable

sudo apt-get update && sudo apt-get upgrade

thanks to [http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html]("http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html")
for the alsa instructions.

Sorry it wasn't working for you, as i said earlier i had been messing with the sound settings etc for a while before i got it working, thanks for the feedback, i'm  considering doing another fresh install to figure out the exact steps i took.  Let me know if the alsa upgrade makes any difference.

SWEET - it works fine after the ALSA upgrade!!!  :D

here's my output - but I didn't even run pavucontrol after the upgrade.
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec 11 2009 for kernel 2.6.31-17-generic (SMP).

```

Thanks James!!

---

### Post by kgingeri on 2009-12-30
I still have a few annoying things that don't work with my T91MT and UNR:
[LIST=1]
[*]hangs when using the touch screen - only Alt-PrtSc+R+E+I+S+U+B gets me rebooted
[*]I have to press the Fn+F2 to start wireless after every reboot - i've tried several things in rc.local to no avail.
[*] brightness keys don't work (Fn+F3/F4) - xev doesn't even see them
[*] can't assign the button under the screen (next to power) - no xev events here either
[/LIST]
Is anyone else seeing any of these, or more importantly, any suggested work-arounds/fixes?!

EDIT: re the brightness keys - scripts in /etc/acpi don't line up with my system config - stuff they check for is either not found or in different places under /proc etc

---

### Post by kgingeri on 2009-12-30
Hey I got multi-touch working by install this fdi file and restarting, then going to System Prefs -> Mouse and clicking scrolling settings (these had no effect previously)  :D

I don't have it working for the screen yet tho  :/

UPDATE:
Not sure what happened to my attachments so I've attached both modified fdi files.  Remove ".txt" and place in /usr/share/hal/fdi/policy/20thirdparty

EDIT:  [COLOR="Red"]PLEASE NOTE! this is for the touchpad **only**[/COLOR]

---

### Post by jamespcole on 2009-12-30
> **kgingeri said:**
> 

Thanks James!!

awesome glad it worked, still not sure if it was just the alsa upgrade or a combo of that and the backports though.  did you remove the backports stuff before the alsa upgrade?

Either way i'll update my blog entry, i think i might do a fresh install next week to isolate the exact steps anyway.

---

### Post by jamespcole on 2009-12-30
> **kgingeri said:**
> I still have a few annoying things that don't work with my T91MT and UNR:
[LIST=1]
[*]hangs when using the touch screen - only Alt-PrtSc+R+E+I+S+U+B gets me rebooted
[*]I have to press the Fn+F2 to start wireless after every reboot - i've tried several things in rc.local to no avail.
[*] brightness keys don't work (Fn+F3/F4) - xev doesn't even see them
[*] can't assign the button under the screen (next to power) - no xev events here either
[/LIST]
Is anyone else seeing any of these, or more importantly, any suggested work-arounds/fixes?!

EDIT: re the brightness keys - scripts in /etc/acpi don't line up with my system config - stuff they check for is either not found or in different places under /proc etc

In regards to number 4 i am using that to rotate the screen.  to find out how check out this guy's blog, it's for 9.04 but the screen rotation is working for me.

[http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/]("http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/")

From the blog
> 
In order for ACPI to recognize the screen rotation button of the T91, you will need to add a new button configuration file:

/etc/acpi/events/asus-rotate-t91

event=hotkey (ATKD|HOTK) 0000007b
action=/etc/acpi/rotatescreen.sh
You may also want to edit the /etc/acpi/rotatescreen.sh script to rotate the screen to the left rather than from the (default) right.
You must restart /etc/init.d/acpid for that change to become effective.


as for the other stuff, yep it's happening to me too.  The one that bothers me the most is the random crashes.  The most annoying thing about it is that it just stops and i can't get any info on the error.  If you find any solutions let me know because it's really annoying.

I am  not experiencing the problem you mentioned with the wireless, it is enabled and on when i boot up.

---

### Post by kgingeri on 2009-12-31
Wow, the rotate trick was easy!!  
Created the two line file and did a "# restart acpid" and it's live.
(Actually I think I prefer the right to left rotation, but the jury is still out on it ;))

As for my process to correct the mic in Skype; I didn't uninstall anything - just did the backports (it re-did grub and a bunch of stuff - if I remember right) and then the alsa upgrade as you outlined.

Thanks again James!!

---

### Post by kgingeri on 2009-12-31
James and others, 

I've been trying also to find some log events or something on the freezes.  It is evtouch, I'm very sure - I can run all day without using the touch screen.  It doesn't matter what program I'm in and I have found no pattern other than maybe when you are dragging - scroll-bars, selections etc?

I wonder if there are anymore alternatives to the evtouch mods.  I did find one called plpevtch, but no luck compiling yet.  I did take a quick look at the source, but I'd have to get my 'head into it' to be able to check for mem leaks etc.  I thought I might take debug stuff out as that may be a mem leak potential - certainly not necessary for functionality.

The freezes are one of the main ones I'm working on. I keep this thread up to date if I find a fix!   :)

EDIT: The plpevtch stuff complains that xorg-server xproto and kbproto are not installed - when I try the "./configure --prefix=/usr" cmd

---

### Post by jamespcole on 2009-12-31
yeah i had figured it was something evtouch related, i've had the same problem on other touch screens too(WiBrain BL1) without finding a solution.  

BTW another useful tip in the blog i mentioned earlier is the making a single click followed by a long click == to a right click.  It makes using the touchscreen heaps easier and it definitely works on 9.10.  

Thanks for the feedback, i'll look into the evtouch issue too, between us i'm sure we can figure something out.  

Just out of interest has anyone got a way to consistently reproduce the bug? I can't figure out a way to crash it, it just seems to  be random but it'll be a lot easier to test fixes if we can reproduce the bug at will.

---

### Post by kgingeri on 2009-12-31
> **jamespcole said:**
> ...
BTW another useful tip in the blog i mentioned earlier is the making a single click followed by a long click == to a right click.  It makes using the touchscreen heaps easier and it definitely works on 9.10.  
...

Yeah, saw this one James, but can't get it to work.  I have put everything in xorg.conf, and that may be why.  I still don't understand the relationship of fdi files to devices for xorg yet.  I need to play with it some more.  

I currently have a udev rule file to create a sym link *(I have seen the touchscreen on either event5 or event6 so hardcoding them isnt the best)* for the /dev/input/event<n> device and then my xorg.conf section is as follows:

```
$ tail /etc/udev/rules.d/69-touchscreen.rules 

# Elo Touchscreen
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="04e7", ATTRS{idProduct}=="0020", SYMLINK+="input/evtouch_event"
#
[B]# Asus multitouch & buttons 
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0486", ATTRS{idProduct}=="0185", SYMLINK+="input/asus_touchscreen_event"
# NOTE: the following never does register - proc/..devices report Vendor:Prod of 0000:0000!?[/B]
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0B05", ATTRS{idProduct}=="B703", SYMLINK+="input/asus_buttons_event"
#
```

```
CSection "InputDevice"
    Identifier  "touchscreen"
    Driver      "evtouch"
    [B]Option      "Device"                "/dev/input/asus_touchscreen_event"
                # ...set mod'd /etc/udev/rules.d/69-touchscreen.rules[/B]
    Option      "DeviceName"            "touchscreen"
    Option      "MinX"                  "0"
    Option      "MinY"                  "0"
    Option      "MaxX"                  "3475"
    Option      "MaxY"                  "3475"
    Option      "ReportingMode"         "Raw"
    Option      "SendCoreEvents"        "On"
    Option      "taptimer"              "200" 
    Option      "movelimit"             "15" 
    Option      "Emulate3Buttons"       "true"
    Option      "Emulate3Timeout"       "50"
    Option      "longtouchtimer"         "400" 
#    Option     "touched_button"        "1" 
#    Option     "touched_action"        "down"
    Option      "longtouched_button"    "3" 
    Option      "longtouched_action"    "down"
    Option      "oneandahalftap_button" "2" 
    Option      "oneandahalftap_action" "down"
    Option      "Calibrate"             "0"
EndSection
```

so how does an fdi associate to my /dev/input/asus_touchscreen_event device - through the evtouch driver?  Anyway, none of the long or oneandahalf (short-then-held) clicks work.  :(

My custom fdi is:
```
cat 10-asustouchscreen.fdi 

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.name" contains="Asus">
      <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_options.taptimer" type="string">200</merge>
        <merge key="input.x11_options.movelimit" type="string">15</merge>
        <merge key="input.x11_options.emulate3buttons" type="string">true</merge>
        <merge key="input.x11_options.emulate3timeout" type="string">50</merge>
        <merge key="input.x11_options.longtouchtimer" type="string">400</merge>
        <merge key="input.x11_options.longtouched_action" type="string">down</merge>
        <merge key="input.x11_options.longtouched_button" type="string">1</merge>
        <merge key="input.x11_options.oneandahalftap_action" type="string">click</merge>
        <merge key="input.x11_options.oneandahalftap_button" type="string">3</merge>
        <merge key="input.x11_options.minx" type="string">0</merge>
        <merge key="input.x11_options.miny" type="string">0</merge>
        <merge key="input.x11_options.maxx" type="string">3475</merge>
        <merge key="input.x11_options.maxy" type="string">3475</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
*This ISN'T in place at the moment.  I believe it is BEST to have only a fdi or xorg.conf define params - not both.*

and finally *(did I do this all backwards?!;))*... /proc/bus/input/device Asus info is:
```
I: Bus=0003 Vendor=0486 Product=0185 Version=0100
N: Name="AsusTek, Inc. MultiTouch"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=1b
B: KEY=403 0 30003 0 0 0 0 0 0 0 0
B: ABS=ffffff00 100003f
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus EeePC extra buttons"
P: Phys=eeepc/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=rfkill kbd event7 
B: EV=3
B: KEY=100000 0 0 0 400b 400 0 1300000 e0000 0 0 0
```

EDIT:  I forgot my xinput info, so doing a "$ xinput list --short" I get
```
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"touchscreen"	id=2	[XExtensionPointer]
"touchscreen"	id=3	[XExtensionPointer]
"Asus EeePC extra buttons"	id=4	[XExtensionKeyboard]
"USB 2.0 Camera"	id=5	[XExtensionKeyboard]
"Sleep Button"	id=6	[XExtensionKeyboard]
"Power Button"	id=7	[XExtensionKeyboard]
"AT Translated Set 2 keyboard"	id=8	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=9	[XExtensionPointer]
"SynPS/2 Synaptics TouchPad"	id=10	[XExtensionPointer]
"Microsoft Compact Optical Mouse 500"	id=11	[XExtensionPointer]
```

I only get the cursor jumping to the bottom right if I try using the touchscreen.  I'm gonna fiddle some more...

---

### Post by kgingeri on 2009-12-31
Tried the fdi file again with none of the params in xorg.conf but no luck  :v(  

At least xorg.conf is working for me - just the long clicks do seem to register.

Interesting tho - it seems (see below) it is defaulting to Synaptics instead of evtouch - hmmmm - may have to play a little more with it...(from /var/log/Xorg.0.log)

```
...
(II) config/hal: Adding input device AsusTek, Inc. MultiTouch
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event6"
(**) Option "SHMConfig" "On" 
(**) Option "EmulateTwoFingerMinZ" "40" 
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(--) AsusTek, Inc. MultiTouch: no supported touchpad found
(EE) AsusTek, Inc. MultiTouch Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "AsusTek, Inc. MultiTouch"
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed (8)
...
```

---

### Post by kgingeri on 2009-12-31
Hi All,

I've been working in Xournal for almost 2hrs without a crash/freeze! :P  That's unheard of for me!

Things seem pretty stable - but time will tell. I'm even penning this all in using Cell  Writer :)

I'm also using EasyStroke a lot - for click actions + special key (tab, esc ...).

I'v attached a tar of soure & the 'support' files I'm currently using. The source is credited to SamT91MT over at the ASUS forum.  All binaries are there from my last compile - I didn't do a "make clean" on purpose, but you may need to recompile yourself.  See the README.T91MT file in the source folder.

EDIT: Use "tar xvzf ..." to extract - had to rename it to be able to upload it

EDIT2: You'll find a fdi file in the archive - I have it in /usr/share/hal/fdi/policy/20thirdparty at the moment, but I'm not convinced it's needed. I still need definitions in xorg.conf to get things to work.

EDIT3: Ok, just noticed that I have all the touchscreen stuff commented in my xorg.conf file, so I guess the fdi file is working now!  Sweet - but still no longtouch stuff.

EDIT4: Hey all, Psiegel reports that > ...two different versions of the xorg.conf file. One lives in the root of the tar, the other is in the xf86-input-evtouch-0.8.8-T91MT directory. It's the one in the xf86-input-evtouch-0.8.8-T91MT directory that was necessary to make it work, and I had copied the other.

---

### Post by kgingeri on 2010-01-01
No crashes or freezes yet - I do have DRI disable in xorg.conf.
Video and all still seems fine too! :D

EDIT: I have commented DRI lines in my xorg.conf and am testing more - all very stable so far, and I am using the touchscreen constantly :D

---

### Post by harbus on 2010-01-02
Great! kudos kgingeri

I haven't had any problems with the newest version either. It seems to be rock solid now.

:guitar:

---

### Post by Jonathanius on 2010-01-02
> **harbus said:**
> Great! kudos kgingeri

I haven't had any problems with the newest version either. It seems to be rock solid now.

:guitar:
Is this just for the T91MT or has anyone tried it with the regular T91?

---

### Post by kgingeri on 2010-01-02
> **Jonathanius said:**
> Is this just for the T91MT or has anyone tried it with the regular T91?

Hi Jonathanius,

If I understand right, the MT is fairly new and most of this thread is for the T91.  There is a difference in the touchscreens used in either models so I have no idea if it is solid in the T91 vs T91MT.

---

### Post by bennett on 2010-01-02
I *finally* got ndiswrapper working properly on my T91. To do this, I followed the comprehensive ndiswrapper troubleshooter available [here]("http://ubuntuforums.org/showthread.php?t=885847") (it's from the ubuntu forums because I am running eeebuntu on my t91). Somewhere along the way I discovered that the ndiswrapper packages created for various debian-based distros have been buggy for a while (see [this thread ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")for the note). So I had to 
[LIST=1]
[*]remove the driver that ndiswrapper had made for me with ndiswrapper -r <my driver name>
[*]completely remove ndiswrapper (using the --purge attribute)
[*]download the ndiswrapper source & compile it
[*]build a new ndiswrapper driver & use modprobe to load it again etc. etc.
[*]reboot, pray, fingers crossed (maybe not all essential but didn't hurt either)
[/LIST]
And then voila! All of a sudden my wireless is working like never before. The ndiswrapper driver is GREAT; nice strong & fast connection. Just like it should be.

THanks all.

---

### Post by virati on 2010-01-07
Hi All,

Just installed CrunchBang but I can't seem to get the internet (wired) to work. Very confused. Not used to the Ubuntu way (Arch-ie here myself) but I thought it was supposed to work out of the box. I didn't have my LAN on WHILE I was installing (is that the problem?) To clarify: Within BIOS, the option for the onboard LAN was set to disabled when I installed CrunchBang.

Time to reinstall or is there a way around? Thanks!

---

### Post by yigal.weinstein on 2010-01-07
@kgingeri: just awesome, the touchscreen would freeze after a couple of minutes using the original configs of SAMT91MT.  It hasn't frozen for 10 hours.  Thank you

touchpad:
I cannot get the touchpad to work.  No two finger scrolling, no two finger or three finger emulation of 2nd and 3rd mouse buttons.  

"synclient -h" returns "Can't access shared memory area. SHMConfig disabled?" but I've enabled SHMConfig.

---

### Post by virati on 2010-01-07
*Deleted*

---

### Post by virati on 2010-01-07
> **kgingeri said:**
> Hi All,

I've been working in Xournal for almost 2hrs without a crash/freeze! :P  That's unheard of for me!

Things seem pretty stable - but time will tell. I'm even penning this all in using Cell  Writer :)

I'm also using EasyStroke a lot - for click actions + special key (tab, esc ...).

I'v attached a tar of soure & the 'support' files I'm currently using. The source is credited to SamT91MT over at the ASUS forum.  All binaries are there from my last compile - I didn't do a "make clean" on purpose, but you may need to recompile yourself.  See the README.T91MT file in the source folder.

EDIT: Use "tar xvzf ..." to extract - had to rename it to be able to upload it

EDIT2: You'll find a fdi file in the archive - I have it in /usr/share/hal/fdi/policy/20thirdparty at the moment, but I'm not convinced it's needed. I still need definitions in xorg.conf to get things to work.

EDIT3: Ok, just noticed that I have all the touchscreen stuff commented in my xorg.conf file, so I guess the fdi file is working now!  Sweet - but still no longtouch stuff.

Bah, I'm REALLY sucking at reading today apparently.
--
Thanks for the hard work guys, just got my t91MT yesterday and now it's set up almost perfect. Got the touch screen working, video driver working, wireless working, etc. The only thing I'm working on at the moment is the rotate button and fixing suspend up right, we'll see how that goes.

---

### Post by DrPotoroo on 2010-01-10
I love being able to set a long-short tap combo to emulate a right click. However, a word of warning: Doing this causes crashes in at least gimp: Holding and dragging won't paint when right-click emulation is set up and after a short while it crashes everything (only alt+prt-scr+REISUB works, and even that doesn't after a while).

---

### Post by virati on 2010-01-12
> **DrPotoroo said:**
> I love being able to set a long-short tap combo to emulate a right click. However, a word of warning: Doing this causes crashes in at least gimp: Holding and dragging won't paint when right-click emulation is set up and after a short while it crashes everything (only alt+prt-scr+REISUB works, and even that doesn't after a while).

How did you get that set up?

---

### Post by DrPotoroo on 2010-01-16
> **virati said:**
> How did you get that set up?
I followed the instructions at [http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/](http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/) under the section "Configuring the touchscreen events".

I think that something about the "longtouch" settings messes with programs where you click and drag to do something. I have turned it off again now because I do like being able to use gimp to draw up diagrams on the touchscreen.

---

### Post by DrPotoroo on 2010-01-19
After installing blueman I was able to pair with my next G phone using bluetooth and get internet access. However, it then mysteriously stopped working: the connection would say it was successful but I couldn't actually connect to anything. The solutions seems to have been setting my netbook back to "untrusted" in my phone settings so that I had to acknowledge each initial connection request on the phone. After that it works again.
 
**Edit:** Actually, forget all that. It later stopped working again, and then I got it to work with the netbook "trusted" again. Must be another problem.

---

### Post by XeoNiCaLiTy on 2010-01-21
> **kgingeri said:**
> Hey I got multi-touch working by install this fdi file and restarting, then going to System Prefs -> Mouse and clicking scrolling settings (these had no effect previously)  :D

I don't have it working for the screen yet tho  :/
Could you clarify the way you made this work? The .fdi file included does not seem to be the one where you made your two finger scrolling work.

Does anyone know how to enable the mult touchpad on the T91MT?

---

### Post by kgingeri on 2010-01-22
> **XeoNiCaLiTy said:**
> Could you clarify the way you made this work? The .fdi file included does not seem to be the one where you made your two finger scrolling work.

Does anyone know how to enable the mult touchpad on the T91MT?

Seems my attachments got lost in post [#163]("http://ubuntuforums.org/showpost.php?p=8583858&postcount=163") - I've put them there again.  

Here are the two files I have mod'd and am currently running with (see attached and rename without ".txt" - ie 'mv <filename>.txt <filename>'.
Copy into place by using 'sudo cp <filename>.fdi /usr/share/hal/fdi/policy/20thirdparty' - both files in that folder) and reboot

EDIT: BTW two finger works for me vertically and horizontally  :)

EDIT: **[COLOR="Red"]NOTE! This is for the trackpad only![/COLOR]**

EDIT2: Thought I should include my /etc/X11/xorg.conf file also, as there can be conflicts between fdi defs and xorg.conf (at least that what I have found)...
```
Section "Device"
        Identifier      "GMA500"
        Option 		"AccelMethod" "EXA"
        Option 		"MigrationHeuristic" "greedy"
        Option 		"IgnoreACPI" "yes"
        Driver 		"psb"
EndSection

Section "DRI"
    Mode    0666
EndSection
```That's it - no more and no less!
And also my /etc/default/grub file (be sure to run 'update-grub' after edits)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

# items are zero based 1 per line as displayed in the grub menu
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="1"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**quiet nosplash mem=786mb**"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
``` (tho this has little to do with the touch pad, more with performance of the display)

---

### Post by XeoNiCaLiTy on 2010-01-24
> **kgingeri said:**
> Seems my attachments got lost in post [#163]("http://ubuntuforums.org/showpost.php?p=8583858&postcount=163") - I've put them there again.  

Here are the two files I have mod'd and am currently running with (see attached and rename without ".txt" - ie 'mv <filename>.txt <filename>'.
Copy into place by using 'sudo cp <filename>.fdi /usr/share/hal/fdi/policy/20thirdparty' - both files in that folder) and reboot

EDIT: BTW two finger works for me vertically and horizontally  :)

EDIT2: Thought I should include my /etc/X11/xorg.conf file also, as there can be conflicts between fdi defs and xorg.conf (at least that what I have found)...
```
Section "Device"
        Identifier      "GMA500"
        Option         "AccelMethod" "EXA"
        Option         "MigrationHeuristic" "greedy"
        Option         "IgnoreACPI" "yes"
        Driver         "psb"
EndSection

Section "DRI"
    Mode    0666
EndSection
```That's it - no more and no less!
And also my /etc/default/grub file (be sure to run 'update-grub' after edits)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

# items are zero based 1 per line as displayed in the grub menu
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="1"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**quiet nosplash mem=786mb**"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
``` (tho this has little to do with the touch pad, more with performance of the display)
Worked like a charm.

We have only a couple of issues left:

Sleep
Hibernate
Touch screen (flicks, rotate +90+90+90 instead of +90-90, multitouch)

Will post when I fix one of these!

---

### Post by rautarotta on 2010-01-25
> I am running Karmic 2.6.32-17 - the latest as of this post - and I have no idea if this will work for anything else.
I am running 2.6.31-18-generic and it worked for me too. Thanks!

I did the following steps from the provided instructions[INDENT]1. Install the video psb drivers via instructions in [blog post]("http://setupguides.blogspot.com/2009/11/fixing-screen-resolution-for-asus-eee.html")
[/INDENT][INDENT]2. do "sudo apt-get install xserver-xorg-input-evtouch"
[/INDENT][INDENT]    3. download the source/binaries from the attachment of post #171
4. do "tar -xvzf xf86-input-evtouch-0.8.8-T91MT.tar.gz"
6. do "sudo cp 50-asustek.fdi /usr/share/hal/fdi/policy/20thirdparty/50-asustek.fdi"

7. restart and hope best .. didn't helped. (Was it supposed to be enough ? I understood so from post #171)

   8. do "cd xf86-input-evtouch-0.8.8-T91MT"

   9. do "sudo cp /usr/lib/xorg/modules/input/evtouch_drv.so /usr/lib/xorg/modules/input/evtouch_drv.so.save"
   10. do "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.save"
  11. do "sudo cp ./.libs/evtouch_drv.so  /usr/lib/xorg/modules/input/evtouch_drv.so"
  12. do "sudo cp ./xorg.conf /etc/X11/"
  13. Shutdown and restart, and it was working.

Again thanks for SamT91MT and [kgingeri]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=703544")[/INDENT]

---

### Post by scottfranklin on 2010-01-26
> **XeoNiCaLiTy said:**
> We have only a couple of issues left: Sleep,  Hibernate, Touch screen (flicks, rotate +90+90+90 instead of +90-90, multitouch)

What is the current status of sleep/hibernate? Working never/sometimes/often?

Also, has anyone upgraded the SSD (likely voiding the warranty) to 64Gb or larger?

scott

---

### Post by mrkus on 2010-01-26
Hi,

I have been following this thread and is really thankful for all the great info.
Suspend has worked for me all the time time, the problem has been that the when resuming the wireless was completely dead.

I did spend som time and found some old issues and copied something that worked before.

[http://forum.eeebuntu.org/viewtopic.php?f=3&t=4136](http://forum.eeebuntu.org/viewtopic.php?f=3&t=4136)

The short story to get it working for me was adding 
"pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1" to the end of /etc/default/grub.conf default boot string. And running update-grub.

Now suspend works with psb and touch screen.

Do not know if this is required but I'm using the latest compat-wireless from linuxwireless.org
([http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.33/compat-wireless-2.6.33-rc5.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.33/compat-wireless-2.6.33-rc5.tar.bz2))
(The changelog from end of december describes suspend issues with ath9k, and therefore was this updated one of the first ones i did).

Someone might try the added boot string with backport version of linux wireless from ubuntu.

Unfortunate I have had one freeze, do not know if it is from wireless or the touch screen.

/markus

---

### Post by jamespcole on 2010-01-29
Hey Guys,
i think i have managed to find a solution to the freezing problem when using the touchscreen. I don't want to speak too soon but it has been a few hours since and i have not had a crash, normally it would have crashed a bunch of times by now.  I will post more detailed instructions on my blog but for the time being this is what i did.

I first un-installed the evtouch drivers via synaptic(obviously you only need to do this if you already installed them)

The simple t91, not the MT version, uses the IDEACOM IDC 6680 touchscreen.  You can get the manufacturer drivers from [http://www.ideacom.com.tw/en_home.htm]("http://www.ideacom.com.tw/en_home.htm")

I then extracted the files from the archive and run(as per the installation procedure in the pdf):

sudo ./IDC_setup.sh

then reboot

after this the drivers will be in /usr/local/IDC at the terminal type:

cd /usr/local/IDC

then:

sudo calibration

then reboot

after this you will still experience the random freezes, to fix this do the following:

open a terminal and type:

sudo gedit /etc/X11/xorg.conf

find the line that has "SendCoreEvents" and change the value from "On" to "Off"

Save and then reboot

I imagine that you can do this with the evtouch drivers too but i don't have them installed now and this solution seems to be working for me, so if someone wants to try this solution with the evtouch drivers and let me know how it goes it would be greatly appreciated.

EDIT:  These instructions are for the simple t91 not the t91MT

EDIT: Just had another freeze, damn this is an annoying problem.  The freezes seem less frequent now though.

---

### Post by milbournosphere on 2010-02-03
I'm not quite sure if this is the right place to post this.  I recently got a t91mt and have been closely following this thread to get Ubuntu up and running on it.  I have been largely successful for the most part and thank you all for your help.  I do have one question, though.  Has anyone here managed to get a palm rejection solution working for the touch screen? I have been trying to use Xournal and find it to be very difficult to use when my palm is resting on the screen.  Thanks again for everyone participating in this thread, it has been a great help!

---

### Post by PrincessNybor on 2010-02-06
Is there an official write-up of how to set up that custom touch-screen driver for the T91MT? I can dig through the thread and get a pretty good idea of what to do, but if there's a wiki or something for this info, I'd rather try that first! My Linux skills are a bit rusty. ;)

Also: how are my odds of getting this working on Jolicloud? If there's no chance, I may give Ubuntu NBR a try instead, but my understanding is that fewer things work out-of-the-box on the T91MT under Ubuntu NBR than do on Jolicloud. The touch screen, rotate button, and multi-touch trackpad are the only things NOT currently working on my machine. FN keys, wifi, bluetooth, SD card readers, etc. are all working GREAT.

---

### Post by scottfranklin on 2010-02-11
Is 2Gb the maximum memory the T91MT can access, or has anyone had success with some of the newer, 4Gb, memory cards?  Is this a hardward or software limitation?

---

### Post by RenataWas on 2010-02-13
Thanks to this thread I have managed to install most of what I needed!

I am having problems with Xournal, though - it works perfectly well with the
screen in landscape mode, but not in portrait mode. I thought it was a general problem of
the touchscreen not rotating properly, but now I realized that I can click the menus
with no problem, it is inside the Xournal editing area that things get mixed up. 


[kgingeri]("http://ubuntuforums.org/member.php?u=703544"), have you managed to use Xournal with the screen rotated?

I am running Karmic on the T91 (not MT) with the evtouch driver.

---

### Post by psiegel on 2010-02-16
Hey guys, thanks so much for posting all this stuff.  Between this thread and setupguides.blogspot.com, I've pretty much got everything working.  I'm still having trouble though getting two-finger scrolling up and running, and everyone else here seems to have had no trouble getting that up and running.  I was hoping maybe someone could give me some hints on how to debug this.

I'm running UNR Karmic on a T91MT.  I applied the fixes for wifi, screen resolution, and the rotate button  listed on setupguides.blogspot.com.  Then I followed kgingeri's post #155, but with the tar from #171.  I then downloaded and put the files from post #163 in place and changed my mouse settings.  When I put two fingers on the screen, it looks like one is just ignored.  It certainly doesn't scroll.  When I put two fingers on the track pad to try scrolling, the mouse jumps around the screen at random.

I tried also using the fdi files from post #186 in case they were any different from those on post #163, and no luck.  I even tried applying the grub changes from post #186 just in case.  Still no multi-touch scrolling.

Any thoughts?

---

### Post by kgingeri on 2010-02-16
> **RenataWas said:**
> Thanks to this thread I have managed to install most of what I needed!

I am having problems with Xournal, though - it works perfectly well with the screen in landscape mode, but not in portrait mode. I thought it was a general problem of the touchscreen not rotating properly, but now I realized that I can click the menus
with no problem, it is inside the Xournal editing area that things get mixed up. 

[kgingeri]("http://ubuntuforums.org/member.php?u=703544"), have you managed to use Xournal with the screen rotated?

I am running Karmic on the T91 (not MT) with the evtouch driver.

Yupper!  Use it all the time and for hours on end!  Not sure what your issues are.  (I am running the T91MT tho?)

BTW I keep upgrading my kernel (is it .18 now - at work so not sure) and did have trouble last time, but **_forgot_** about the 
```
$ sudo dpkg-reconfigure psb-kernel-source
$ sudo update-grub
```
(at work and I forget it, it's mentioned in this thread a ways back) so I had trouble and ended up getting files from a dropbox repository someone had set up.  But I am currently at work.  If ppl are having issues, let me know and I'll look it up again and do a new post.

**[COLOR="Red"]**** Definitely remember the "[B]dpkg-reconfigure**" command above when upgrading or you may be in for trouble! *** [/COLOR][/B]

Gotta try hibernate again - seems some have had luck with newer kernels and I haven't tried it lately.

EDIT:  Updated proper command - hope I didn't lead too many astray with that! ;)
Also being at home now, I chaecked and am at ...-20 kernel...
```
$ uname -a
Linux kgltnb 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
```

UPDATE: No ACPI/suspend yet - don't get wireless back - have to reboot.  :(

---

### Post by kgingeri on 2010-02-16
> **psiegel said:**
> Hey guys, thanks so much for posting all this stuff.  Between this thread and setupguides.blogspot.com, I've pretty much got everything working.  I'm still having trouble though getting two-finger scrolling up and running, and everyone else here seems to have had no trouble getting that up and running.  I was hoping maybe someone could give me some hints on how to debug this.

I'm running UNR Karmic on a T91MT.  I applied the fixes for wifi, screen resolution, and the rotate button  listed on setupguides.blogspot.com.  Then I followed kgingeri's post #155, but with the tar from #171.  I then downloaded and put the files from post #163 in place and changed my mouse settings.  When I put two fingers on the screen, it looks like one is just ignored.  It certainly doesn't scroll.  When I put two fingers on the track pad to try scrolling, the mouse jumps around the screen at random.

I tried also using the fdi files from post #186 in case they were any different from those on post #163, and no luck.  I even tried applying the grub changes from post #186 just in case.  Still no multi-touch scrolling.

Any thoughts?

Sorry, my mods are only for the touch-pad - not the screen.

---

### Post by kgingeri on 2010-02-16
About using EXT4 - I am running it fine.
I've read that there is no problem running it on an SSD - google is your friend :)

I do get system busy lockups when running some FLASH based sites - to the point where response is so slow I have to do a hard power off!  Stupid Flash!!  ;)  I've now got Flash blockers loaded in my browsers (Firefox and Chrome)

EDIT: Flash will run ok - it's sites that have multiple embedded flash tags

---

### Post by psiegel on 2010-02-16
> **kgingeri said:**
> Sorry, my mods are only for the touch-pad - not the screen.

Touch-pad would be great, but even that isn't working for me with your mods.  Whenever I touch the touch-pad with both fingers, the mouse jumps around at random.

---

### Post by kgingeri on 2010-02-17
> **psiegel said:**
> Touch-pad would be great, but even that isn't working for me with your mods.  Whenever I touch the touch-pad with both fingers, the mouse jumps around at random.

Hmmm... It's been a bit since I did this all so I am not remembering real clearly but a few of things to check....

[LIST=1]
[*]Be sure you don't have both defs for mouse in your /etc/X11/xorg.conf file and an fdi file in place.
[*] make sure there is no other fdi in /usr/share/hal/fdi/... that defines stuff for the Synaptics pad
```
$ cd /usr/share/hal/fdi/policy/20thirdparty/
$ grep -il synaptics *
11-x11-synaptics.fdi
``` should only produce "11-x11-synaptics.fdi" as show above - move any other file out of the folder if there is any
[*] ...it's seems to me one other definition too, but I can't remember it now - will post if I recall it.
[/LIST]

EDIT: possibly my third point may be to be sure you have both fdi files I posted in the /usr/share/hal/... folder

---

### Post by kgingeri on 2010-02-17
Ok got some resolve on suspend!

Thanks to Mrkus and post [#190]("http://ubuntuforums.org/showpost.php?p=8727591&postcount=190") I can now turn wireless back on after opening the display from a suspend event! :p

BTW Mrkus, I am not using compat-wireless from linuxwireless.org
([http://www.orbit-lab.org/kernel/comp...33-rc5.tar.bz2](http://www.orbit-lab.org/kernel/comp...33-rc5.tar.bz2))

Thanks!

EDIT:  Wireless still won't start for me on power on - I always have to kick it into gear with Fn+F2.  Is this everyone's experience?

---

### Post by psiegel on 2010-02-17
Thank you kgingeri!  Looking into the xorg.conf was exactly the clue I needed.  It turns out that your tar attached to post [#171]("http://ubuntuforums.org/showpost.php?p=8590363&postcount=171") includes two different versions of the xorg.conf file.  One lives in the root of the tar, the other is in the xf86-input-evtouch-0.8.8-T91MT directory.  It's the one in the xf86-input-evtouch-0.8.8-T91MT directory that was necessary to make it work, and I had copied the other.

Also, yes, I too must press Fn-F2 every boot to turn on the wifi.  Very annoying!

I wonder if anyone has played at all with the multi-touch screen drivers at this site:

[http://lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://lii-enac.fr/en/projects/shareit/multitouch-devices.html)

They have a driver specifically for the T91MT, but I can't quite tell from the site if the driver actually integrates into Xorg, or if it simply runs the demos they created.  What I'd really love is to be able to do stuff like zoom in firefox or acroread by using a pinch on the screen.  I'm not 100% convinced the driver above would get me that.

I suppose there's one sure way to find out...

---

### Post by kgingeri on 2010-02-17
> **psiegel said:**
> Thank you kgingeri!  Looking into the xorg.conf was exactly the clue I needed.  It turns out that your tar attached to post [#171]("http://ubuntuforums.org/showpost.php?p=8590363&postcount=171") includes two different versions of the xorg.conf file.  One lives in the root of the tar, the other is in the xf86-input-evtouch-0.8.8-T91MT directory.  It's the one in the xf86-input-evtouch-0.8.8-T91MT directory that was necessary to make it work, and I had copied the other.

Also, yes, I too must press Fn-F2 every boot to turn on the wifi.  Very annoying!

I wonder if anyone has played at all with the multi-touch screen drivers at this site:

[http://lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://lii-enac.fr/en/projects/shareit/multitouch-devices.html)

They have a driver specifically for the T91MT, but I can't quite tell from the site if the driver actually integrates into Xorg, or if it simply runs the demos they created.  What I'd really love is to be able to do stuff like zoom in firefox or acroread by using a pinch on the screen.  I'm not 100% convinced the driver above would get me that.

I suppose there's one sure way to find out...

Thanks - I updated the 171 post  :)

I have not tried the driver, but it looks like a good idea!  I'll try it when I get a chance.

The features you describe would be nice.  I do use EasyStroke for writing and gesture recognition so I'm not sure how well multi touch would live with that.  I have defined a Graffiti-like character and symbols set for EasyStroke that works very nicely.  My gesture list is long in EasyStroke  ;)  I do know about and have used CellWriter (excellent software as well) but EasyStroke allows me to just write anywher on the screen.

---

### Post by RenataWas on 2010-02-18
Kgingeri, I also keep the system updated and psb-kernel reconfigured. My problem seems to be inside Xournal. I will try other editing programs to see what happens. I can rotate the screen and the touchscreen seems to work fine in portrait mode, but inside the editing area of xournal it is as if the touchscreen was not calibrated. Thanks anyway, it is good to know that for someone it works :-)



EDIT: Ooops - my fault: I started Xournal before rotating the screen, and shouldn't do that according to the manual... If it is started after the
screen is rotated, it works perfectly well...

---

### Post by mrkus on 2010-02-19
> **kgingeri said:**
> Ok got some resolve on suspend!

Thanks to Mrkus and post [#190]("http://ubuntuforums.org/showpost.php?p=8727591&postcount=190") I can now turn wireless back on after opening the display from a suspend event! :p

BTW Mrkus, I am not using compat-wireless from linuxwireless.org
([http://www.orbit-lab.org/kernel/comp...33-rc5.tar.bz2](http://www.orbit-lab.org/kernel/comp...33-rc5.tar.bz2))

Thanks!

EDIT:  Wireless still won't start for me on power on - I always have to kick it into gear with Fn+F2.  Is this everyone's experience?

I have huge problems with the X hanging after using the touch screen for a short while. 
kgingeri is your touch screen stable?

I need to read back through the thread to see where I might have gone astray on the setup.

In regard to the wifi not starting without FN+F2 combo, I have something in the back of my head that this is a "feature" for ensuring that wifi doesnt start in an airplane, I do have some memory of that there is something rather easy to change to get it working, unfortunate I havent been able to find that page which I read this.

/markus

---

### Post by dargaud on 2010-02-23
[Updated after I got things to work on UMR, some entries are confusing between T91 and T91MT]

What is the best distro to install in order to get most stuff running out of the box ? UNR, eebuntu, moblin...?

---

### Post by kgingeri on 2010-02-23
Sorry for the late response ppl, life is busy!  ;)

@mrkus:  Yes my X is very stable - and my whole systems EXCEPT if I get runaway Flash stuff happening in a browser (Firefox or Chrome).
One thing to watch is that you don't have duped defines in an fdi file (if you have never installed one - then likely you don't) and /etc/X11/xorg.conf - I have been using xorg.conf and NOT fdi defs for X.  I would attach it, but I'm at work.  I will try to remember tonight.  I also attacch and use a nice big 21" monitor and can just use the Conf Display icon (which i have put permanently in my panel) to activate it or deactivate it as needed.  I did need to add a define for virtual size in my xorg.conf.

@dargaud:  I like to point ppl to James' blog, as most of what he has has been very useful to me and he has answered my questions when asked (Thanks again James!)  :)  See him at ---> [http://setupguides.blogspot.com/2009_11_01_archive.html](http://setupguides.blogspot.com/2009_11_01_archive.html) or his post [#141]("http://ubuntuforums.org/showpost.php?p=8411814&postcount=141") -- his username is jamespcole
EDIT:  BTW I love UNR (Ubuntu Netbook Remix) - it works very nicely for me :D  - however it WILL NOT run out-of-the-box on a T91, nothing does that I know of  :(

---

### Post by kgingeri on 2010-02-23
> **mrkus said:**
> ... 
kgingeri is your touch screen stable?
...
/markus

Markus, I said I'd post my xorg.conf, and here it is...
```
#	xorg.conf --- kgingeri's current asettings - Feb 2010

Section "Device"
    Identifier  "GMA500"
    Driver 	"psb"
#    Option 	"AccelMethod" 		"EXA"
#    Option 	"MigrationHeuristic" 	"greedy"
#    Option 	"IgnoreACPI" 		"yes"   # ...originally "yes"
#    Option      "DRI"                   "off"   # ...will it stop freezing?
#    Option      "NoDRI"

    Option      "DownScale"          "false"
    Option      "ExaNoComposite"     "false"
#    Option      "ExaMem"             "131072"
#    Option      "ExaScratch"         "4"
#    Option      "ExaCached"          "false"
    Option      "IgnoreACPI"         "true"
    Option      "LidTimer"           "false"
    Option      "NoAccel"            "false"
    Option      "NoFitting"          "false"
    Option      "NoPanel"            "false"
    Option      "MigrationHeuristic" "greedy"
    Option      "ShadowFB"           "false"
    Option      "SWcursor"           "false"
    Option      "Vsync"              "false"
EndSection

Section "DRI"
    Mode        0666
EndSection

Section "Screen"
    Identifier    "default screen"
    Device        "GMA500"
    Monitor       "Monitor"
    DefaultDepth  24
    SubSection "Display"
        Depth     24
        Modes     "1024x600" "800x600" "640x480"
        Virtual   2704 2704
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier      "Default Layout"
	Screen          "default screen"
EndSection
```

BTW, I thought I might also post my /etc/default/grub file as well - it has my dimming key Fn+F3 working but not Fn+F4 - interesting and a bit more progress...
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

# items are zero based 1 per line as displayed in the grub menu
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="2"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash mem=786mb pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=noop acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

...to change grub you need to use sudo and edit /etc/default/grub then do a 'sudo update-grub'

EDIT:  I do have some X stuff defined for my touchscreen in an fdi file and **_NOT_** in my xorg.  I'll post it later here (@ work currently)

---

### Post by apothecarius on 2010-03-02
I think the whole system freezes if you touch the screen with two fingers at the exact same time (on T91mt). Noticed that while playing minesweeper.
Unfortunately that's difficult to reproduce

You experience that too?

---

### Post by scottfranklin on 2010-03-02
> **kgingeri said:**
> EDIT:  BTW I love UNR (Ubuntu Netbook Remix) - it works very nicely for me :D  - however it WILL NOT run out-of-the-box on a T91, nothing does that I know of  :(
Is there a reason to prefer UNR over regular Ubuntu?  My T91MT arrives Thursday so I'll be installing before the week is out!!!

---

### Post by kgingeri on 2010-03-03
> **scottfranklin said:**
> Is there a reason to prefer UNR over regular Ubuntu?  My T91MT arrives Thursday so I'll be installing before the week is out!!!

It really 'boils down' to a personal preference, but being a user of linux since we had to piece X together on Slackware years ago, I have to say I like the way they utilize a small display and make it relatively easy to find stuff (your whole desktop becomes a launcher/menu - "netbook-launcher").  I do like the "maximus" addition as well (it puts apps as full screen as possible).  And then the other main thing is the "go-home" applet that takes you back to your desktop/launcher.  

One thing about Ubuntu that isn't great (and boy, is this another whole discussion!) is that they seem to roll-out updates for the sake of having an update and then things get broken.  However, that's not too bad when you learn how to install backports etc  ;)

That's my 2 cents worth  :)

---

### Post by scottfranklin on 2010-03-04
> **kgingeri said:**
> being a user of linux since we had to piece X together on Slackware years ago
I like to impress my students by telling them of my first Linux installation in 1993.  From floppies.  (Somewhere between 25-35 disks!)

> **kgingeri said:**
> I like the way they utilize a small display and make it relatively easy to find stuff (your whole desktop becomes a launcher/menu - "netbook-launcher").  I do like the "maximus" addition as well (it puts apps as full screen as possible).  And then the other main thing is the "go-home" applet that takes you back to your desktop/launcher.  

Thanks.  I'll give i a go tonight.  My goal is to get a stable system by a conference starting in a week.  Should be enough time, although I still have to prepare/teach classes, finish my talk, advise students.  I.e., lots of things to put off while I tinker w/Ubuntu & my new toy.

scott

---

### Post by kgingeri on 2010-03-04
> **scottfranklin said:**
> I like to impress my students by telling them of my first Linux installation in 1993.  From floppies.  (Somewhere between 25-35 disks!)



Thanks.  I'll give i a go tonight.  My goal is to get a stable system by a conference starting in a week.  Should be enough time, although I still have to prepare/teach classes, finish my talk, advise students.  I.e., lots of things to put off while I tinker w/Ubuntu & my new toy.

scott

Ha ha - yeah, weren't CD's a life-saver!! I remember when it was only about 4 or 5 floppies - I think - it too long ago! :p

The only other one I'd consider is PCLinuxOS, BUT I have NO idea how well it plays with this machine.  Also it not as user friendly and is KDE rather then Gnome based.

---

### Post by scottfranklin on 2010-03-04
And the fun begins.  UNR installed, followed the various threads to get the appropriate screen resolution, but can't seem to get the touchscreen working.  I installed the evtouch drivers but when I run calibrate_touchscreen from a terminal (Xwindows already killed) it can't open a display.  When run from a terminal in X it reports that no evtouch devices are found.

Any tips?

---

### Post by Mizukusai on 2010-03-04
I though evtouch did not work for the MT...

EDIT : forgot the "not" part.

---

### Post by kgingeri on 2010-03-04
> **scottfranklin said:**
> And the fun begins.  UNR installed, followed the various threads to get the appropriate screen resolution, but can't seem to get the touchscreen working.  I installed the evtouch drivers but when I run calibrate_touchscreen from a terminal (Xwindows already killed) it can't open a display.  When run from a terminal in X it reports that no evtouch devices are found.

Any tips?

Scott, I won't be around much in the next several hours (not sure where you are - I am EST Canada).  I started by following most of James' blog posts for November:

[http://setupguides.blogspot.com/2009_11_01_archive.html](http://setupguides.blogspot.com/2009_11_01_archive.html)

He has quite a few items that worked good for me.

I didn't actually use the calibrate utility (I had similar issues, in that X needed to be available but not running or something - can't remember), but my touch screen was good without it.

Check out the stuff on James' blog and see if it helps - I think most was posted in November but there may have been a post in December also (he does talk about using the utility)

I'll try to watch and give you help as I can.  :)

EDIT: Here's a quick C program to test ev...save it as evtest.c...
```
// evtest.c --- test T91MT touchscreen

#include <sys/types.h>
#include <fcntl.h>
#include <linux/input.h>
#include <stdio.h>
#include <errno.h>

main(int argc, char **argv)
{
    struct input_event ev;
    int fd;

    if(!argv[1])
    {
	printf("Using default device /dev/input/event6\ntouch screen for results...");
	fd=open("/dev/input/event6",O_RDONLY);
    }
    else
	fd=open(argv[1],O_RDONLY);
   
    for (;;) {
        int r=read(fd,&ev,sizeof(struct input_event));
       
        if (r==-1 && errno==EINTR) continue;
        if (r==-1) break;
        printf("Event: time %ld.%06ld, type %d, code %d, value %d\n",
                ev.time.tv_sec, ev.time.tv_usec, ev.type, ev.code, ev.value);
    }
    perror("read");
    close(fd);
}
```

Compile it in Terminal with "cc evtest.c -o evtest" and then run "./evtest" @ cmd prompt.  If I remember right, your event<n> may be different (edit in the source).  I think mine was different from the authors (isn't my work and I can't remember where I got it) - use...
```
cat /proc/bus/input/
```
to verify your touch screen device. (also "lsusb")

EDIT2: you may need to be root (use sudo) to run the evtest program.

---

### Post by kgingeri on 2010-03-04
Scott, it's been I while so hopefully I'm not leading you down the wrong paths here, but I also had to install or verify that the /etc/udev/rules.d/69-touchscreen.rules file looked like the following...(see my bolded area)...
```
# Evtouch udev.rules
#
# Because Evtouch can't autoprobe devices we assume that we only
# Have one device so we can make it like this :P
#
# List here your touchscreen, check if it works  and send it to lifebook_AT_conan_DOT_de
# Name can be found in /proc/bus/input/devices ('cat /proc/bus/input/devices')
#

# Generic ts-adc touchscreen modules
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{name}=="ts-adc", SYMLINK+="input/evtouch_event"

# These are the touchscreens supported by kernel's "usbtouchscreen" module

# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="3823", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="3823", ATTRS{idProduct}=="0002", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0123", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0123", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0eef", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0eef", ATTRS{idProduct}=="0002", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="1234", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# eGalax Inc. USB TouchController)
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="1234", ATTRS{idProduct}=="0002", SYMLINK+="input/evtouch_event"
# eTurboTouch
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="1234", ATTRS{idProduct}=="5678", SYMLINK+="input/evtouch_event"
# PanJit Touchset
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="134C", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# PanJit Touchset
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="134C", ATTRS{idProduct}=="0002", SYMLINK+="input/evtouch_event"
# PanJit Touchset
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="134C", ATTRS{idProduct}=="0003", SYMLINK+="input/evtouch_event"
# PanJit Touchset
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="134C", ATTRS{idProduct}=="0004", SYMLINK+="input/evtouch_event"
# 3M Microtouch EX II
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0596", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# ITM Touchscreens
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="F9E9", SYMLINK+="input/evtouch_event"
# Gunze AHL61
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0637", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
# DMC TSC-10/25
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0AFA", ATTRS{idProduct}=="03E8", SYMLINK+="input/evtouch_event"
# Elo Touchscreen
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="04e7", ATTRS{idProduct}=="0020", SYMLINK+="input/evtouch_event"
#
[B]# Asus multitouch & buttons 
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0486", ATTRS{idProduct}=="0185", SYMLINK+="input/asus_touchscreen_event"
# NOTE: the following never does register - proc/..devices report Vendor:Prod of 0000:0000!?
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0B05", ATTRS{idProduct}=="B703", SYMLINK+="input/asus_buttons_event"
#[/B]
# Lifebook B-Series
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{name}=="LBPS/2 Fujitsu Lifebook TouchScreen", SYMLINK+="input/evtouch_event"
```

---

### Post by scottfranklin on 2010-03-04
I just got home and will try these post-haste.  I followed James' blog, which is how I got the resolution issue resolved.

That said, I expect these installs to take several days.  Thanks again for all the suggestions.

scott

---

### Post by scottfranklin on 2010-03-04
Hmm, evtest fails with read: bad file descriptor, regardless of which event # I use.

cat /proc/bus/input/handlers seems to indicate # 3 is the touchscreen
N: Number=3 Name=evdev Minor=64

does that mean my /etc/udev file should be 64-touchscreen?  (Aside: I had to copy your 69-touchscreen... since there wasn't one in /etc/udev/rules.d

cat /proc/bus/input/devices seems to point to input 5:

N: Name="AsusTek, Inc. MultiTouch"
H: Handlers=mouse1 event 5

whereas event 3 is "Macintosh mouse button emulation"

Off to shower a kid.  Back for more later.  Wireless is also disabled, but since I have a LAN connection I haven't tried too hard w/that yet.

EDIT #1: just re-read post #171.  downloaded xorg.conf, 69-touchscreen.rules and edited it as per post #21 above.  Installed xorg-server.dev and re-compiled binaries from #171 & installed.

EDIT #2:  SUCCESS!  Thanks kgingeri!  Buried somewhere around p. 16 were he detailed instructions of how to use the tgz file from #171, and a few posts later you were thoughtful enough to post the output of your /proc/bus/input/devices file, which matched mine.  A few tweaks to xorg.conf (probably putting them back where you originally had them) and I now have touchscreen capabilities!  

Next step is wireless, buttons, & other stuff, but I'm way ahead of where I thought I'd be.

---

### Post by kgingeri on 2010-03-04
That's great Scott! I also remembered another ASUS forum that helped me a lot...
[http://vip.asus.com/forum/view.aspx?id=20091214162901203&board_id=20&model=Eee+PC+T91MT&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20091214162901203&board_id=20&model=Eee+PC+T91MT&page=1&SLanguage=en-us)
(I also posted some findings there).
 
I retried evtest and I now get the same file descriptor error - so forget that for now. I think maybe it came from the forum above. There is a French programmer there who is working on multi-touch for the screen.  

I do have multi touch for my mouse pad (not screen).  I also now have most buttons working except Brightness Fn+F4 (only Dimming - Fn+F3) but have not dug into why as yet.  I'll see what else I can dig up for you, to help you along...  Off to have a look.

EDIT: one quick update - If you haven't already been there try [http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/](http://www.ced-network.net/blog/2009/08/14/asus-eeepc-t91-and-ubuntu-904jaunty/) it was for Jaunty but a lot is still good I think

---

### Post by kgingeri on 2010-03-04
Not a lot other than from forums I've listed, Scott.

The rotate button is listed in the Ce.D Blog:
Set /etc/acpi/events/asus-rotate-t91 to read...
```
event=hotkey (ATKD|HOTK) 0000007b
action=/etc/acpi/rotatescreen.sh
```

Here is a line from my latest Grub conf file - you edit the file in /etc/default/grub and then run 'update-grub' - all as root (or sudo) of course. I think this got me the Fn+F3 dimming key working, increased video speed, SSD HD setting etc:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash mem=786mb pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=noop acpi_backlight=vendor"
```

I'm sure there are others but that's all I'm finding right now.

EDIT: Oh, and I had looked into the Brightness key - it is not returning any event info (run 'xev' in a terminal, un-maximize it and you'll get X event info for everything!) - so until someone figures that out, it won't work.

EDIT2: Almost forgot about the mouse/touch pad multi touch...  I have the two attached files in /usr/share/hal/fdi/policy/20thirdparty/ - strip off the ".txt" of course.  HOWEVER if you use them then do not use any mouse deinitions in your xorg.conf - I know it can be done that way also but it should be either or NOT BOTH or X can get very confusing!

---

### Post by DrPotoroo on 2010-03-05
I'm back on the bandwagon after being out of action for a month. Dropped my t91 and it would light the power LED and do nothing else. Eventually after pulling everything apart and putting it back together it works again. Some cable must have worked loose in the drop.
 
Anyway, kgingeri could you possible explain to me the reasons for "mem=786mb" and "elevator=noop" in your grub config? I am interested to learn what these do.
 
EDIT: Just tried my brightness keys after following your grub conf. BOTH my brightness keys work, although it only lets me increase brightness to 50%. Thanks for the tip!
 
EDIT2: Actually, it only lets me increase the brightness back to where it was. If it gets set (somehow) lower than 50% then I can't increase it beyond that. Any ideas?
 
EDIT3: Okay, both brightness up and brightness down are effective for a limited range of changes around the current setting. So if I type xrandr --output LVDS0 --set BACKLIGHT 100 I can only bring the brightness down a little. From 50 I can go down a little and up a little. The exact amounts seem a little bit random. (By the way, it's "output LVDS[zero]" not the letter "o")

---

### Post by scottfranklin on 2010-03-05
Rotation is working, thank you very much.  Nothing yet on multitouch touchpad, but I just started.

EDIT:  ISSUE 1 RESOLVED.  #2 is less important.
1.  Wireless isn't working at all.  ifconfig wlan0 up results in SIOCSIFFLAGS:  Unknown error 132.  Fn-F2 seems to have no effect.  I've installed the backports-modules-karmic package.  Any thoughts on what to try next?  FIXED

2.  When I boot w/a USB mouse attached, my touchscreen comes up as event 6.  W/o the mouse, event 5.  Is there a way to handle this in xorg.conf (multiple display entries?) or just make sure the usb mouse is disconnected when booting?

Scott

---

### Post by kgingeri on 2010-03-05
> **DrPotoroo said:**
> I'm back on the bandwagon after being out of action for a month. Dropped my t91 and it would light the power LED and do nothing else. Eventually after pulling everything apart and putting it back together it works again. Some cable must have worked loose in the drop.
 
Anyway, kgingeri could you possible explain to me the reasons for "mem=786mb" and "elevator=noop" in your grub config? I am interested to learn what these do.
 
EDIT2: Actually, it only lets me increase the brightness back to where it was. If it gets set (somehow) lower than 50% then I can't increase it beyond that. Any ideas?
 
EDIT3: Okay, both brightness up and brightness down are effective for a limited range of changes around the current setting. So if I type xrandr --output LVDS0 --set BACKLIGHT 100 I can only bring the brightness down a little. From 50 I can go down a little and up a little. The exact amounts seem a little bit random. (By the way, it's "output LVDS[zero]" not the letter "o")

Yes, the mem=786mb is to reserve video ram (I only have 2 gig) - the elevator=noop may not be necesarry if you are running ext4 (which is SSD friendly) but if you are not running a hardrive but a SSD solid-state drive, then it is suppose to help save the drive.

You have better response with brightness key then I did.  I would suggest keeping the randr command handy (I would have suggested it as I use it if I unplug A/C and can't get brightness up or down when running on battery)

---

### Post by kgingeri on 2010-03-05
> **scottfranklin said:**
> Rotation is working, thank you very much.  Nothing yet on multitouch touchpad, but I just started.

EDIT:  ISSUE 1 RESOLVED.  #2 is less important.
1.  Wireless isn't working at all.  ifconfig wlan0 up results in SIOCSIFFLAGS:  Unknown error 132.  Fn-F2 seems to have no effect.  I've installed the backports-modules-karmic package.  Any thoughts on what to try next?  FIXED

2.  When I boot w/a USB mouse attached, my touchscreen comes up as event 6.  W/o the mouse, event 5.  Is there a way to handle this in xorg.conf (multiple display entries?) or just make sure the usb mouse is disconnected when booting?

Scott

No Scott I don't worry about have my USB mouse plugged or not.  The udev file should takes care of it, as it sets up a devices based on /proc/bus/input/devices.  You are correct tho, in that the event device will change numbers.  I attached my udev file in a previous post.

Glad stuff is starting to work for you.  There has been some reports of correcting the wireless always off on reboot by installing back-ports, but it has worked for me yet  :(  I always need to tap the Fn-F2 to bring up wireless after a reboot.
Links for such are [here]("http://ubuntuforums.org/showpost.php?p=69509&postcount=2") (for a BCM wireless card - no ASUS T91) and [here]("http://setupguides.blogspot.com/2009/11/fixing-wireless-network-card-for-asus.html") - can't find the other backports/blacklist one right now.

---

### Post by scottfranklin on 2010-03-05
Yeah, progress comes slowly.  I must have missed the udev file; thanks for the pointer.

I can live w/Fn-F2 after booting.  It's not ideal, but manageable.

Do you have any issues resuming from suspend?  Sometimes it works; sometimes not.  It may be related to wireless; still trying to track that down.

When you connect to an external monitor, do you just use the detect displays from System setting? 

scott

---

### Post by kgingeri on 2010-03-05
> **scottfranklin said:**
> Yeah, progress comes slowly.  I must have missed the udev file; thanks for the pointer.

I can live w/Fn-F2 after booting.  It's not ideal, but manageable.

Do you have any issues resuming from suspend?  Sometimes it works; sometimes not.  It may be related to wireless; still trying to track that down.

When you connect to an external monitor, do you just use the detect displays from System setting? 

scott

Yeah, suspend is not working for me yet either.  :(

I do use the detect displays and it works fine.  DO NOTE that you'll need the virtual desktop settings in xorg.conf - it's at home and I'm at work right now - I think it is "virtual 2048 2048" in the server section - not sure.

---

### Post by scottfranklin on 2010-03-05
Thanks for the quick replies.  I wonder if the wireless is interfering w/suspend.  I'll try disabling wireless before suspending and see if that helps.  Are you able to hibernate w/o a problem?

Just noticed another "bug".  I was using xournal to annotate a .pdf (one of the main uses for me).  Works great in landscape mode, but when I rotate the screen to portrait all of a sudden the annotations are offset by 1-2 inches from the pen.  Weird, since it's only in the annotation; selecting menus, etc... seems unaffected.

Scott

---

### Post by kgingeri on 2010-03-05
> **scottfranklin said:**
> Thanks for the quick replies.  I wonder if the wireless is interfering w/suspend.  I'll try disabling wireless before suspending and see if that helps.  Are you able to hibernate w/o a problem?

Just noticed another "bug".  I was using xournal to annotate a .pdf (one of the main uses for me).  Works great in landscape mode, but when I rotate the screen to portrait all of a sudden the annotations are offset by 1-2 inches from the pen.  Weird, since it's only in the annotation; selecting menus, etc... seems unaffected.

Scott

Ha - not something I've tried in xournal yet ;)  I love xournal also - it's the main reason I wanted and have this machine  :D  I do use it to sketch/diagram in both landscape and portrait as well tho, without problems.

Good thought on suspend - it could be wireless related!  I'm not sure I've tried hibernate, I usually only use suspend.

---

### Post by scottfranklin on 2010-03-05
> **kgingeri said:**
> DO NOTE that you'll need the virtual desktop settings in xorg.conf - it's at home and I'm at work right now - I think it is "virtual 2048 2048" in the server section - not sure.
Do you have both settings in a single xorg.conf file or do you have a xorg.conf.external that you swap when needed?

---

### Post by tHe-BiNk on 2010-03-05
3 questions. I just finished switching my desktops from Windows to Ubuntu. Now I want to switch to Ubuntu on my tabletPC (T91MT).

1. Which version should I install 10.04 Alpha 3, or 9.10?
2. Is Ubuntu stable on the T91MT?
3. Will I be able to use my SonyEricsson Mobilephone as a modem (like I now do in windows), using tethering over bluetooth?

TIA!

---

### Post by DrPotoroo on 2010-03-06
> **tHe-BiNk said:**
> 
3. Will I be able to use my SonyEricsson Mobilephone as a modem (like I now do in windows), using tethering over bluetooth?

TIA!

I tether my ultra-cheap Samsung to work as a modem via bluetooth. You need to install blueman to do it.

---

### Post by scottfranklin on 2010-03-06
> **tHe-BiNk said:**
> 
1. Which version should I install 10.04 Alpha 3, or 9.10?
2. Is Ubuntu stable on the T91MT?
I went w/9.10 and seem to be able to follow in the path of others on this forum w/o too much difficulty.

Moderately.  There are issues w/suspend, which I think are due to wireless.  Suspend works most of the time when I remember to manually shut down the wireless first w/Fn-F2.

It's still hanging a bit too often for my tastes, but I'm only 2 days into tweaking the config files.  It's mostly X that's hanging, though, not the OS itself.  REISUB reboot does always get it to reboot nicely.

scott

---

### Post by kgingeri on 2010-03-06
> **scottfranklin said:**
> Do you have both settings in a single xorg.conf file or do you have a xorg.conf.external that you swap when needed?

Sorry Scott - forgot to post it!  Here it is.  All one file - no swapping needed, just apply when you use the Config Display Settings applet (I have it in the panel).

---

### Post by kgingeri on 2010-03-06
> **scottfranklin said:**
> ...

It's still hanging a bit too often for my tastes, but I'm only 2 days into tweaking the config files.  It's mostly X that's hanging, though, not the OS itself.  REISUB reboot does always get it to reboot nicely.

scott

Scott, pay special attention to the DRI and - try it either on or off.  Also the IgnoreACPI settings.  Both in xorg.conf.  That should help with freezing.

The other thing I have seen is my disk busy like nuts and usually do to a Flash heavy web site.

Other than the Flash thing, I never hang any more  :D

EDIT: one other thing is the /etc/default/grub setting for "pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1" - I seem to recall this was for wireless but not sure it didn't stop my hanging as well. Oh, that's a param added to the "GRUB_CMDLINE_LINUX_DEFAULT=" line.

---

### Post by kgingeri on 2010-03-06
BTW Scott, turning off wireless for sleeps seems to work for me too.  I'm quite sure there is an ACPI file for sleep and we could likely disable (and maybe re-enable on wake)!?  Thanks for that tip! :)  I'll look into the ACPI file stuff and post if I find a solution.

---

### Post by kgingeri on 2010-03-06
Ok, there is a bunch of scripts in /etc/acpi for various things.  However disabling wireless (or at least toggling state) did seem to make any difference.  It seems this is a fairly complex area.  You can use "acpi_listen" to see key ID's and values but Gnome handles some stuff, X handles some and ACPI handles some - if I understand right.

I did find an excellent page on this stuff tho in the Ubuntu Wiki (gotta remember this more often, and maybe contribute! ;)) - see

[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

Gotta get back to other work right now, but I think we'll get this stuff soon  :)


EDIT: in my quick playing around, I discovered that my dim key seq does return values (via acpi_listen) and that coming out of sleep mode, "wireless networking" is 'disabled' (see via right-click on the wireless applet) - so it's not that wireless needs to be turned on, just re-enabled.

---

### Post by tHe-BiNk on 2010-03-06
Okay, thanks everybody for the information. I will go ahead with installing Ubuntu 9.10.

---

### Post by scottfranklin on 2010-03-06
> **kgingeri said:**
> BTW Scott, turning off wireless for sleeps seems to work for me too.  I'm quite sure there is an ACPI file for sleep and we could likely disable (and maybe re-enable on wake)!?  Thanks for that tip! :)  I'll look into the ACPI file stuff and post if I find a solution.
That was along the lines of what I was thinking.  Put "disable wireless" in the suspend script.

I've noticed, though, that when I wake from suspend I can't get back to the launcher.  I can use any applications that I had open before suspend, but either netbook-launcher or gdm itself is hung.  Worse, if I try to log out or restart gdm the screen goes blank & hangs and I have to REISUB.

I'm not sure if this is an xorg issue (I'll try the suggestions you made) or a netbook-launcher problem.  I wonder if there's an easy way to go classic gnome just once to see if it works.  I'll investigate and let you know.

scott

p.s. the xorg.conf you posted for external monitor didn't have anything related to the touch screen.  How do you simultaneously run touchscreen & external monitor (or don't you)?

---

### Post by kgingeri on 2010-03-06
> **scottfranklin said:**
> That was along the lines of what I was thinking.  Put "disable wireless" in the suspend script.

I've noticed, though, that when I wake from suspend I can't get back to the launcher.  I can use any applications that I had open before suspend, but either netbook-launcher or gdm itself is hung.  Worse, if I try to log out or restart gdm the screen goes blank & hangs and I have to REISUB.

I'm not sure if this is an xorg issue (I'll try the suggestions you made) or a netbook-launcher problem.  I wonder if there's an easy way to go classic gnome just once to see if it works.  I'll investigate and let you know.

scott

p.s. the xorg.conf you posted for external monitor didn't have anything related to the touch screen.  How do you simultaneously run touchscreen & external monitor (or don't you)?

Scott, I don't have those issues with suspend at all - very weird.  Mine seems to be working fine now = even without turning off wireless!?  

All my touch stuff is in fdi files.  X can use either xorg.conf or fdi (see bolded below):```
$ ls -l /usr/share/hal/fdi/policy/20thirdparty/
total 68
-rw-r--r-- 1 root root 2723 2009-10-14 19:05 10-linuxwacom.fdi
-rw-r--r-- 1 root root  242 2009-05-11 18:06 10-x11-input-tslib.fdi
[B]-rw-r--r-- 1 root root 2823 2009-12-30 16:47 11-x11-synaptics.fdi
[/B]-rw-r--r-- 1 root root  348 2009-10-26 06:29 11-x11-vmmouse.fdi
-rw-r--r-- 1 root root  440 2009-07-13 02:54 20-libgpod-sysinfo-extended.fdi
-rw-r--r-- 1 root root 3066 2009-10-09 07:15 25-ntfs-3g-policy.fdi
[B]-rw-r--r-- 1 root root 1956 2009-12-31 22:36 50-asustek.fdi
[/B]-rw-r--r-- 1 root root 1330 2009-11-23 06:06 50-eGalax.fdi
-rw-r--r-- 1 root root  840 2009-11-23 06:06 50-elo-2700.fdi
-rw-r--r-- 1 root root  963 2009-11-23 06:06 50-Fujitsu.fdi
-rw-r--r-- 1 root root  757 2009-11-23 06:06 50-gunze.fdi
-rw-r--r-- 1 root root 1157 2009-11-23 06:06 50-ideaco.fdi
-rw-r--r-- 1 root root 1183 2009-11-23 06:06 50-ideaco-idc6681.fdi
-rw-r--r-- 1 root root 1138 2009-11-23 06:06 50-itm.fdi
-rw-r--r-- 1 root root  964 2009-11-23 06:06 50-Panasonic.fdi
-rw-r--r-- 1 root root 1338 2009-11-23 06:06 50-touchkit.fdi
-rw-r--r-- 1 root root 1888 2009-11-23 06:06 50-touchpack.fdi
``` ...I did a long listing so you have a hint at which ones I've changed - and I've attached the two main ones - have a look.  I do touch screen and touch pad (mouse) with fdi's and everything else xorg.conf.  I have found that having definitions in both for the same thing ends up confusing X tho, so beware.

There used to be a disable netbook icon script/program in previous UNR versions, but it's gone now.  You can go into Startup Applications (icon in System) and disable netbook-launcher and Maximus, but it doesn't work as expected, I don't think.  I have no problem with launcher, so I don't think that's your issue.

EDIT: Also, not sure that I've tried touch screen with extern monitor connected - I know I've had to add settings in xorg.conf in previous machines, to configure what touch screen effects - ie local display vs both or only external.  I haven't done that tho with this one.  I use the extern monitor for Xmind mostly, and usually use my USB mouse.  I'll have to try it.

---

### Post by scottfranklin on 2010-03-07
EDIT 1:  yes, I'm dense, but am I correct in thinking I should have both an xorg.conf file (for resolution issues) and .fdi files (for touchscreen stuff)?

First of all, thanks to everyone for being so patient.  I'm sorry I'm taking the forum on a (yet again) step-by-step journey through getting the T91MT up and running.  Let me know if I should take this off-line to e-mails instead.

I'm taking 1 step back to enable several steps forward:

kgingeri, I'm going to try reproduce EXACTLY what you have on your machine.  So, I've removed my xorg.conf file and added the .fdi files to /etc/hal/fdi/policy (I don't have a third-party folder).  X starts but doesn't recognize the monitor so defaults to 800x600.  I've added the two lines to /etc/udev/rules.d/69-touchscreen.rules, and confirmed that the idVendor & idProduct are correct.    

Are there any other config files I'm missing?  (i.e. are input/asus_touchscreen_event & input/asus_buttons_event automatically generated?)

dmesg confirms an AsusTek MultiTouch device.  Now I need to figure out why hal doesn't seem to apply the correct .fdi file.

---

### Post by kgingeri on 2010-03-07
> **scottfranklin said:**
> EDIT 1:  yes, I'm dense, but am I correct in thinking I should have both an xorg.conf file (for resolution issues) and .fdi files (for touchscreen stuff)?

First of all, thanks to everyone for being so patient.  I'm sorry I'm taking the forum on a (yet again) step-by-step journey through getting the T91MT up and running.  Let me know if I should take this off-line to e-mails instead.

I'm taking 1 step back to enable several steps forward:

kgingeri, I'm going to try reproduce EXACTLY what you have on your machine.  So, I've removed my xorg.conf file and added the .fdi files to /etc/hal/fdi/policy (I don't have a third-party folder).  X starts but doesn't recognize the monitor so defaults to 800x600.  I've added the two lines to /etc/udev/rules.d/69-touchscreen.rules, and confirmed that the idVendor & idProduct are correct.    

Are there any other config files I'm missing?  (i.e. are input/asus_touchscreen_event & input/asus_buttons_event automatically generated?)

dmesg confirms an AsusTek MultiTouch device.  Now I need to figure out why hal doesn't seem to apply the correct .fdi file.

Ok Scott, yes I do use both xorg.conf and fdi files.
I can see one problem tho - you don't see the thirdparty folder cuz your in the wrong folder tree. ;)
Leave /etc/hal untouched and use /usr/share/hal....
If you have duped fdi stuff going on one will get ignored - and I think it's the /etc one!   Try that and see what you get.  My instructions didn't say /etc did they?!  I'm mobile right now or I'd check.

---

### Post by tHe-BiNk on 2010-03-08
Okay I have started installing UNR 9.10. I will be writing a HOWTO install UNR on the T91MT, along the way, see:

[http://binken.org/wordpress/?p=476](http://binken.org/wordpress/?p=476)

To give new users 1 place to find all the information from around the Internet. It's still a work in progress. Any suggestions are welcome.

I have installed Ubuntu itself and the Intel Poulsbo drivers.

Question: The best way to install the drivers for the multi-touch display? Is this still to follow the [kgingeri #155 ]("http://ubuntuforums.org/showpost.php?p=8566880&postcount=155")post? Or are there now better ways/newer drivers? TIA!

---

### Post by kgingeri on 2010-03-08
> **tHe-BiNk said:**
> Okay I have started installing UNR 9.10. I will be writing a HOWTO install UNR on the T91MT, along the way, see:

[http://binken.org/wordpress/?p=476](http://binken.org/wordpress/?p=476)

To give new users 1 place to find all the information from around the Internet. It's still a work in progress. Any suggestions are welcome.

I have installed Ubuntu itself and the Intel Poulsbo drivers.

Question: The best way to install the drivers for the multi-touch display? Is this still to follow the [kgingeri #155 ]("http://ubuntuforums.org/showpost.php?p=8566880&postcount=155")post? Or are there now better ways/newer drivers? TIA!

Sounds good! My #155 post is a bit dated now, but just ask, and I'll try to update you as you go.  It is a good starting place at least.  The problem is that I do tweaking every week it seems that gets things ,ore complete.  
If you start with #155 and then read post between me and ScottFranklin (previous 2 or 3 pages) that'll give you most of what I know.

I've attached the xf86 file again, in case it's more recent (named different so not sure).

EDIT: Your blog looks good so far BTW

EDIT2: I've updated #155 a bit, as it seems a lot of ppl end up there.

---

### Post by DrPotoroo on 2010-03-09
I have the same problems with the launcher and sleep/resume as described by scottfranklin. If I put the t91 to sleep with a program running in the foreground I can usually use it again on wake as long as I don't try to bring up the launcher, switch to a console or (maybe) run anything that uses openGL. HOWEVER, if I shut down after resuming from sleep it appears to shut down properly, but runs fdisk on resume suggesting something didn't go right. Using REISUB gets a cleaner restart.
 
Given the behaviour I'm suspecting the problem lies in how the graphics driver talks to the hardware for certain things - maybe a memory access issue? I was able to resume from sleep without any problems in the days back before I worked out how to install the poulsbo driver.

---

### Post by scottfranklin on 2010-03-09
> **DrPotoroo said:**
> I have the same problems with the launcher and sleep/resume as described by scottfranklin. If I put the t91 to sleep with a program running in the foreground I can usually use it again on wake as long as I don't try to bring up the launcher, switch to a console or (maybe) run anything that uses openGL. HOWEVER, if I shut down after resuming from sleep it appears to shut down properly, but runs fdisk on resume suggesting something didn't go right. Using REISUB gets a cleaner restart.
 
Given the behaviour I'm suspecting the problem lies in how the graphics driver talks to the hardware for certain things - maybe a memory access issue? I was able to resume from sleep without any problems in the days back before I worked out how to install the poulsbo driver.

Thanks, I was beginning to think it was just me.  A few interesting tidbits from yesterday's playing:

1.  If you kill gdm (sudo /etc/init.d/gdm stop) and suspend from the console it resumes just fine.  

2.  If you suspend/resume from w/in X and *then* try to kill gdm, the machine hangs.  But, if you ssh in to the hanging machine, you'll find it absolutely impossible to kill the X process.  It's hanging or waiting for something, but it just won't die.  

scott

---

### Post by dargaud on 2010-03-09
Globally I find UNR on the T91MT to be very useful: it's fast, looks good, has good utilities, etc... Just two things: 
1 - are there people working on solving those random freezes ? I've had several kinds: loss of the trackpad but the touch-screen keeps working; lost of alt-tab but the top app keeps working properly... This is an important issue because I'm configuring a buch of those for work to be shared between several people. If it hangs, they'll hang me...

2 - are there softwares that can enhance the touch-screen experience ? Currently it only works as a single-button mouse, without double click. Can it perform full mouse functions (left-right, double click, wheel) ? Multitouch ? Zoom ? I've heard that Opera has some embedded multitouch but I haven't tried it. I tried one of the 'gesture' software recommended in this thread but I felt like a chicken playing with a knife: I had no clue how to configure and use it.

---

### Post by Roman Shuvalov on 2010-03-09
Hi,
I want to use "rotate button" to make right-click of mouse. I read how you catch ACPI events of pressing/releasing this button, but **how to write the script that turns on left-handed mouse orientation? **can you help me?

By the way, there are 2 events on transformation netbook to tablet mode and backwards transformation (this events are used on M$ Windows for decreasing processor's frequency to 800 MHz - maybe because of problems with cooling). 
```

> acpi_listen
hotkey ATKD 0000007e 00000002 /* transform to tablet */
hotkey ATKD 0000007f 00000002 /* transform to normal notebook */ 
```I recommend attach whis events to 180-degree screen rotation - when you transform netbook to tablet you ALWAYS need to rotate the screen and this rotation can be easily automated by this events.

---

### Post by kgingeri on 2010-03-09
> **scottfranklin said:**
> Thanks, I was beginning to think it was just me.  A few interesting tidbits from yesterday's playing:

1.  If you kill gdm (sudo /etc/init.d/gdm stop) and suspend from the console it resumes just fine.  

2.  If you suspend/resume from w/in X and *then* try to kill gdm, the machine hangs.  But, if you ssh in to the hanging machine, you'll find it absolutely impossible to kill the X process.  It's hanging or waiting for something, but it just won't die.  

scott

Dargaud and Scott, You guys have strange behavior!  Are you running the latest kernel?
I am currently at 2.6.31-20-generic.  I have very good SLEEP action lately - my wireless even comes back on (most times) automatically!!!  I have my power prefs set for sleep when I close the display and also for the Zz button (Fn+F1).  Either of these methods have worked wonderful for me for the last several days!  I've been putting it to sleep very regularly too.

I wish I would have documented my fixes better - so sorry for my bad memory and disorganization! :( I'm temped to reinstall completely and docu my steps, but almost afraid to, as I may not do something the same!  ;)  I have other projects right now that need attention as well, but I may consider this soon.

EDIT: @dargaud - I am running the poulsbo driver also, and have not had any random freezes for months!?

EDIT2: Just tried again now - had Chrome open on this page, the Package installer for gnome-gmail ;), and a terminal open.  Pressed my Fn-F1 sleep button, waited for a blinking blue power LED and the pressed a Shift key to bring it all back up again. All is fine, other than I did have to right-click the network-manager-applet and enable wireless this time (this is rare, but does happen occasionally). I am typing this on a resumed session!

EDIT3: You could also try to add "acpi_skip_timer_override" to your /etc/default/grub file, append it inside the quotes on the GRUB_CMDLINE_LINUX_DEFAULT line (space seperate all values, of course), then do a "sudo update-grub" and reboot.  See if that helps

---

### Post by kgingeri on 2010-03-09
> **Roman Shuvalov said:**
> Hi,
I want to use "rotate button" to make right-click of mouse. I read how you catch ACPI events of pressing/releasing this button, but **how to write the script that turns on left-handed mouse orientation? **can you help me?

By the way, there are 2 events on transformation netbook to tablet mode and backwards transformation (this events are used on M$ Windows for decreasing processor's frequency to 800 MHz - maybe because of problems with cooling). 
```

> acpi_listen
hotkey ATKD 0000007e 00000002 /* transform to tablet */
hotkey ATKD 0000007f 00000002 /* transform to normal notebook */ 
```I recommend attach whis events to 180-degree screen rotation - when you transform netbook to tablet you ALWAYS need to rotate the screen and this rotation can be easily automated by this events.

Roman, this is what I use to rotate the screen...
```
$ more /etc/acpi/events/asus-rotate-t91 

event=hotkey (ATKD|HOTK) 0000007b
action=/etc/acpi/rotatescreen.sh

$ more /etc/acpi/rotatescreen.sh

#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
	right)
	NEW_ROTATION="normal"
	;;
	*)
	NEW_ROTATION="right"
	;;
esac

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
	fi
done
```

You could hack the /etc/scpi/rotatescreen.sh line to another script and then use the acpi_fakekey command to possibly do the right-click.  I'd check other scripts in /etc/acpi for examples, man pages etc.
Hope that helps!

EDIT: a great tool to find acpi key values is 'acpi_listen'

---

### Post by Mizukusai on 2010-03-10
> **dargaud said:**
> . I tried one of the 'gesture' software recommended in this thread but I felt like a chicken playing with a knife: I had no clue how to configure and use it.

You may talk about easystroke.
The basic function is to trigger an action (keystroke, launch command, ...) when you draw a given pattern on the screen.
Let me give you an example.
I'm not using UNR. I have several desktops (gnome-shell or compiz).
I have configured easystroke to strike (CTRL+ALT+LEFT) when i draw a small line from right  to left.  This way, the cube rotates to the left when i move my finger from right to left.

You have to set the way easystrike is triggered. In the second tab, choose button1 as the gesture button. Keep the default time-out profile for now. Change it later if you feel like.
In  the "action" tab, clic "Add action'. Name it. Chosse the type (Command, key, text, ...). set the Details (according to the type). Then "record gesture" => Draw the gesture.


You can also add exclusion. Apps you don't want to trigger easystroke (Like gimp, for example)

---

### Post by kgingeri on 2010-03-10
I personally LOVE EasyStroke - _it is WORTH the learing and VERY USEFUL_ - IMHO. :D  
I actually have definition files that allow me to write characters anywhere on the screen and they are excepted into the focused window (unless there is an exception app defined).  

If anyone wants the definition files, I've included them below.  
[LIST=1]
[*] download and extract files from the attached tar file easystrokefiles.tar
[*] install and run EasyStroke to initialize things 
[*] quit EasyStroke and put the un-tar'd files into your *<home folder>*/.easystroke *(.easystroke is not visible unless you unhide hidden files in the Nautilus file browser [Ctrl]+[H])*
[*] re-run EasyStroke and click the applet icon *(small blue/green pretzel-like icon on the panel)* and you will get the list of strokes defined
[/LIST]
To read how a strokes work, look at the stroke and follow it form dark-blue to light-green - that's how you draw it.  The stylus works best.  Enjoy!

*Hope I'm not repeating myself, I may have already posted this stuff elsewhere ;)*

---

### Post by Roman Shuvalov on 2010-03-11
> **kgingeri said:**
> You could hack the /etc/scpi/rotatescreen.sh line to another script and then use the acpi_fakekey command to possibly do the right-click.  I'd check other scripts in /etc/acpi for examples, man pages etc.
Hope that helps!

EDIT: a great tool to find acpi key values is 'acpi_listen'
Thank you, of course I use acpi_listen to search key values. 

about right-click: I don't want to make "fake key" (right-click), i want to temporary replace left-click and right-click to make right-click when I'm holding rotate button:
- press rotate button // script must turn on "left-handed mouse mode"
- touch the screen (it must be worked as right-click)
- release rotate button // script must turn off "left-handed mouse mode"

Any ideas how to manage left/right-handed mouse mode inside the script?

P.S. About random freezes: In BIOS I disabled on-board camera and disabled "CPU freq is controlled by operating system" option. No freezes since this change, but I didn't worked on T91 too much.

---

### Post by kgingeri on 2010-03-11
> **Roman Shuvalov said:**
> Thank you, ...

Any ideas how to manage left/right-handed mouse mode inside the script?
...

No, sorry Roman - I don't know of a way to monitor the state of a button.  :(

---

### Post by Roman Shuvalov on 2010-03-11
I've just found bug with graphics...

When system starts, all is ok. But after sleeping to suspend and waking up - I see that screen color depth is 16-bit!! Look at the display carefully. Have you got this problem? How to fix?

P.S. and one more serious thing: sometimes (probably after stopping X server by logging out) I see that strings in Ctrl+Alt+F[1..6] terminal (they appear directly in cursor randomly): 
```

[<timestamp>] hda-intel: spurious response 0x0:0x0, last cmd=0x270600
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x870600
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x870600
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x170503
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x170503
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x170503

```I have no idea that is this... big count of this strings appear on <tab> and one on <arrow down>.

---

### Post by scottfranklin on 2010-03-11
> **Roman Shuvalov said:**
> I've just found bug with graphics...

When system starts, all is ok. But after sleeping to suspend and waking up - I see that screen color depth is 16-bit!! Look at the display carefully. Have you got this problem? How to fix?
I don't have my machine in front of me, but I bet I do have this problem.  I"ve noticed that the color of the icons in the status bar are not quite right.  I'm not sure how to fix it, but it's a good direction to search in.

EDIT:  xwinfo returns a color depth of 24bit, although I do see some weird color issues in icons.  Not sure what the issue is.

scott

---

### Post by Roman Shuvalov on 2010-03-12
Random freezes continue happen... who have NO random freezes? what's your kernel version, poulsbo driver version?

I found here (at ubuntuforums.org) instructions about installing poulsbo driver for getting good 3D acceleration on GMA 500. I think I should install here, maybe it will help to deal with some problems... :(

---

### Post by scottfranklin on 2010-03-13
Roman, I'm also having random freezes.  Please keep me posted on whether your re-installing poulsbo helps.

---

### Post by jtjs on 2010-03-13
Hi Everyone, I've been following this thread for about a week.. I did have a severe issue with random freezes when I used the touch screen, though it has subsided since I followed kgingeri's suggestion for grub in post #222... 

[EDIT] I spoke too soon, just locked up.. it's been a while 

I have a different issue though, after clicking on a text input box(like the Quick search box in synaptic.. all of my click events are stuck on that control. I am unable to select anything else with the touchpad or the touchscreen. Even if I tab away focus to another control, as soon as I click anywhere, it selects the input box again. If I exit the program, the touchpad and touchscreen return to normal. If I run a program like "onboard" for typing into one of these input boxes, I lose the ability to change focus to any programs and I can't even exit a program with "ALT F4", becuase no program is in focus.. Though I can trigger the shutdown screen.

Anyone have any ideas on what is causing this?

Thanks
-J

---

### Post by Roman Shuvalov on 2010-03-13
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
I recommend it to all. I used "New Method" (polusbo.sh script). All graphics seems to be OK, Compiz is working, no problems with color depth after waking up from suspend. Random freezes are not tested yet (I need more time). Some problems with performance when playing video with compiz, but I think GMA500 can't give more performance... Linux kernel version is 2.6.31-20-generic. 

I've just locked version psb driver packages in Synaptic, and I want to lock kernel version - how to do it? I don't want ubuntu upgrading kernel version because there is a risk that poulsbo drivers will not work with other kernel version.

---

### Post by markalosey on 2010-03-15
dude, you rock. Thanks for the easystroke definitions....

---

### Post by DrPotoroo on 2010-03-15
> **Roman Shuvalov said:**
> 
P.S. and one more serious thing: sometimes (probably after stopping X server by logging out) I see that strings in Ctrl+Alt+F[1..6] terminal (they appear directly in cursor randomly): 
```

[<timestamp>] hda-intel: spurious response 0x0:0x0, last cmd=0x270600
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x870600
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x870600
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x170503
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x170503
[<timestamp>] hda-intel: spurious response 0x0:0x0, last  cmd=0x170503

```I have no idea that is this... big count of this strings appear on <tab> and one on <arrow down>.
 
This is to do with sound module. I find the sound has some bugs and this seems to be one of them. The keys you are pressing are trying to generate a system beep (because you are at the end of a line, for example) - the sound module is then generating these errors. I get the same thing sometimes. It doesn't seem to be anything too serious.

---

### Post by DrPotoroo on 2010-03-16
Sleep/resume is now working perfectly for me - including wifi coming back up. I'm running UNR on kernel 2.6.31-20 with poulsbo drivers installed using the automatic script method someone has mentioned on here. I think, though, that it was one of the grub options kgingeri uses that made the difference, because the first time I tried this kernel sleep/resume was still behaving the same way, with netbook-launcher crashing after resume.

---

### Post by scottfranklin on 2010-03-16
> **DrPotoroo said:**
> Sleep/resume is now working perfectly for me - including wifi coming back up. I'm running UNR on kernel 2.6.31-20 with poulsbo drivers installed using the automatic script method someone has mentioned on here. I think, though, that it was one of the grub options kgingeri uses that made the difference, because the first time I tried this kernel sleep/resume was still behaving the same way, with netbook-launcher crashing after resume.
Properly installing poulsbo drivers fixed the netbook-launcher problem for me as well, although I'm still having hangs if I don't turn off wireless before suspending.  I'll look for the script you mention; does it turn off wireless as part of the suspend process?

Thanks again for figuring this out, and also to kgingeri for the easytouch config files.  Things are working much more smoothly now!

---

### Post by H3g3m0n on 2010-03-20
After having to reinstall several times in a few days, I have made a fairly big entry on the EEEUser wiki for getting 9.10 working on the T91 / T91MT's with all the tweaks mentioned here, setup guides and so on combined into one place.

[Linkage]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt")

---

### Post by DrPotoroo on 2010-03-22
> **scottfranklin said:**
> I'll look for the script you mention; does it turn off wireless as part of the suspend process?
 
The script I was referring to was the one for installing the poulsbo drivers, mentioned in Roman's post ([http://ubuntuforums.org/showpost.php?p=8961771&postcount=261](http://ubuntuforums.org/showpost.php?p=8961771&postcount=261)).
 
I might have imagined it, but I'm pretty sure my kernel got updated at my last update a few days ago, but I didn't have to go do the poulsbo installation afterwards.
 
I haven't been able to find an answer on how to turn wifi off when sleep is invoked.
 
As an aside, when I turn my t91 on the wifi comes up in whatever state it was shutdown in. I wonder why others find it is always off on startup?

---

### Post by scottfranklin on 2010-03-23
I see.  I did use that to install the poulsbo drivers and that's working fine.  But if I forget to turn off wireless before sleeping (not shutting down) then it hangs on awakening.  I don't have the exact error message, but it looks like it's waiting for wlan0 to be released.

Output to external monitor is now working (even used it during my talk!), but it won't mirror screens, only treat the external monitor as an adjacent display.  Odd, but workable.

---

### Post by spl on 2010-03-24
Hi everyone. Thanks a lot for all the work done so far. I started a **[new thread](http://ubuntuforums.org/showthread.php?p=9022438)** for the T91MT where I summed up the whole procedure to get things running (i.e. poulsbo with working acceleration, stable wireless and of course the touch screen).

---

### Post by Roman Shuvalov on 2010-04-08
2 weeks ago I've disabled On-board Audio (in BIOS). No Random freezes since that time. And no sounds :) So problems in audio drivers. But I have absolutely no ideas how to change audio drivers and/or bring them working without crashing system. And you?

**spl**: have you catch random freezes? If No, what are you audio drivers? (ALSA packages versions etc...)

---

### Post by DrPotoroo on 2010-04-11
Has anyone else had problems with the clock on the T91 suddenly losing hours of time? I'm running Ubuntu UNR 9.10. I installed ntpd so the time is correct whenever I have a network connection but when I don't the time is completely unreliable. I'm not entirely sure if it's becoming incorrect while on, while off or both, though I'm beginning to suspect it's only when it's on.

---

### Post by Roman Shuvalov on 2010-04-13
> **DrPotoroo said:**
> Has anyone else had problems with the clock on the T91 suddenly losing hours of time? I had on 9.10... but now look like all is ok with clock.

---

### Post by Mizukusai on 2010-04-14
I need to open the T91. I can't find any how-to in the net.
Does anyone have any idea how I should procede ? (not need to say very very carefully):P

---

### Post by DrPotoroo on 2010-04-14
> **Mizukusai said:**
> I need to open the T91. I can't find any how-to in the net.
Does anyone have any idea how I should procede ? (not need to say very very carefully):P

Have a look at [http://myt91.info/?tag=disassembly](http://myt91.info/?tag=disassembly) I did it myself, with a little damage to the chassis because I was rushing a little (and had a 9 month-old trying to eat the screws while I did it). Probably not that much care needed as long as you follow the instructions and don't force anything. I had to do it because I dropped mine and it stopped working.

---

### Post by DrPotoroo on 2010-04-14
> **Roman Shuvalov said:**
> I had on 9.10... but now look like all is ok with clock.

So what are you running now if not 9.10?

---

### Post by Mizukusai on 2010-04-15
thank you ! 
it's a bit harder than i though.
I'll follow the instructions.
I think my antenna is unplugged.

---

### Post by Roman Shuvalov on 2010-04-18
> **DrPotoroo said:**
> So what are you running now if not 9.10?
I'm still running 9.10 but this bug don't appear anymore. 

Guys! What about random freezes? I didn't have it for a long time (with disabled sound in BIOS) but now freezes appear again :(

---

### Post by DrPotoroo on 2010-04-19
> **Roman Shuvalov said:**
> I'm still running 9.10 but this bug don't appear anymore. 
 
Guys! What about random freezes? I didn't have it for a long time (with disabled sound in BIOS) but now freezes appear again :(
 
I wonder if disabling sound fixed your clock? (Crazy, but who knows. Mine still loses time constantly, and I have sound enabled.)
 
The only freezes I get with any regularity are:
[LIST]
[*]netbook launcher sometimes (pretty rarely) crashes (other applications still run fine). I've set up a keyboard shortcut to bring up the "panel" menu, so I can still do everything if this happens. I have to shutdown with alt+REISO though to have it come up cleanly the next boot.
[*]The trackpad or keyboard sometimes become unresponsive (sometimes this includes a key "sticking" so I might get an endless string of 'jjjjjjjjjjjjjjjjjjjjjj' in oowriter, for example). This can usually be fixed by tapping the touchscreen, which seem to "unstick" everything.
[/LIST]

---

### Post by Leed on 2010-04-20
Just wrecked my whole installation thanks to a freeze during upgrade. 

Have now replaced the whole Ubuntu with Lucid 10.04. 

Looks pretty neat so far, most things are working out of the box. However there seems to be no possibility to get the Poulsbo to run, any suggestions?

For now at least it's better than the running 9.04 I had, the freezes just took away all the fun. At least in 10.04 the menu isn't as slow when no psb driver is running, you can actually work pretty well with it, it's just not quite as smooth as it should be.

---

### Post by Mizukusai on 2010-04-20
No PSB support with the Xorg shipped with Lucid...

---

### Post by Leed on 2010-04-20
I'm afraid so Mizukusai

having low resolution puts me off a little, but still my T91 never worked as well, for my needs that is. 

The poulsbo drivers in jaunty keept freezing up the pc, no good.
Without the driver Jaunty UNR was simply too slow to use.


In the out of the box state lucid runs pretty well. Of course I'm hoping that some miracle will happen that gets the gma500 working in lucid, that better resolution and animations that are a little smoother would be nice. 
But the as is situation is not that bad, boots up in a few seconds, no freezes and the new unr menu is totally fun and touchscreen friendly. For me it is worth the price of missing that driver. Performance is really not perfect but still pretty good, not at all comparable with Jaunty's crappy state without driver.

---

### Post by Mizukusai on 2010-04-21
Did try to get the iegd drivers ? So far, I can't get my hands on it.
I heard someone manage to make moblin work on a GMA500. 
There's still hope.

---

### Post by Leed on 2010-04-22
I've so far found no resource claiming it to work on xorg 1.7, only warnings that it will not work and rumors that the IEGD still contains the old drivers.

Makes me hate myself for not knowing how to write my own driver

---

### Post by pinkflamingo8806 on 2010-05-02
Anyone find psb drivers for lynx yet?

---

### Post by H3g3m0n on 2010-05-03
> **pinkflamingo8806 said:**
> Anyone find psb drivers for lynx yet?

Theres another [thread]("http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma500&page=50") trying to get psb/gma500 working on Ubuntu. It's not there yet but seems closeish.

The [Mandrivia people got it working on Xserver 1.7]("http://blino.org/blog/mandriva/poulsbo-xserver1.7.html")

So far there seems to be a [hack to fix the resolution]("http://ubuntuforums.org/showpost.php?p=9191574&postcount=461") using non-psb drivers, but performance will of course be crap (or crappier). Add it to /etc/grub.d/40-custom:
```
insmod 915resolution
915resolution 5c 1024 600
set gfxmode=1024x600
```
I haven't tried it on the T91 yet.

There is also still some hope that we will see working drivers, reportedly [Intel are working on them]("http://www.phoronix.com/scan.php?page=news_item&px=NzY2Mg"), they are pushing their own Linux platform after all (unless the current drives we have are those). [Another post with quake video]("http://www.phoronix.com/scan.php?page=news_item&px=NzY2MA").

The main issue right now might be the 2.6.33 backported DRI code that ended up in the 2.6.32 kernel shipped with Ubuntu.

---

### Post by Leed on 2010-05-03
I've just tried your code on my T91 today and it works great. 

You'll also need to edit /etc/default/grub and add a line with "GRUB_GFXMODE=1024x600" and then run "update-grub". Reboot and resolution is good. Thanks to Alfrenovsky [http://ubuntuforums.org/showthread.php?t=1229345&page=50]("http://ubuntuforums.org/showthread.php?t=1229345&page=50")


So far the T91 in lucid seems more performant on web 2.0 pages like facebook etc than it was in jaunty with the psb drivers. Also the new Netbook release menu is really cool. Last but not least, all is stable. 

I can't wait to see how well lucid runs once someone gets a driver working or intel provides one.


Two other issues still bother me
1. Can't find a way to calibrate the touchscreen
2. Can't rotate the screen (don't know if vesa supports this)

---

### Post by H3g3m0n on 2010-05-04
> **Leed said:**
> 
Two other issues still bother me
1. Can't find a way to calibrate the touchscreen
2. Can't rotate the screen (don't know if vesa supports this)

There is a 'calibrate_touchscreen' command, as far as I know it works fine on the T91, although on the T91MT there are issues but you can edit the .fdi file and but in some basic offsets by hand. Also I noticed that was a calibrate touchscreen option on the  netbook eddition, but I can't find it anymore (might have been when I was trying 10.04 on a system with a touchscreen, right now I only have 9.10 and a vitualized 10.04).

Try 'xrandr -o left' and see if that works.

Also hows basic non video playback under the nonpsb drivers? YouTube?

I might update if the rotate and basic video works since the PSB acceleration was so crap that it was hardly worth it (still wondering if I didn't set it up right).

---

### Post by H3g3m0n on 2010-05-04
Just noticed that the guys over at the [other thread]("http://ubuntuforums.org/showthread.php?t=1229345&page=57") seem to have just gotten the drivers working. No install packages yet as they are still building from source but it should be soon now &#9786;

---

### Post by Leed on 2010-05-05
All I can find is a 'calibrate_ppa' which is surely not the same thing... do you know what package your command comes with?

the 'xrandr -o left' command doesn't work in Vesa, worked pretty well in the previous ubuntu with psb.


Video Playback is, well sometimes ok, depending on the size you get lags, forget HD Videos. Youtube standard videos can be watched, you won't miss anything but it is not as smooth as on a desktop or notebook. But that wasn't really different with the psb driver.

As already stated, web 2.0 pages like facebook are clearly better than with the psb. The Netbook remix Interface feels a bit like a cross between iphone and compiz-fusion (nice smooth animations, without compiz actually running), menu animation performance could still be a little bit better, but is all in all pretty nice. 

forget 3D accelerated apps, they are slow.

...all in all, for what I care Vesa in Lucid clearly is better than psb in Jaunty.

I've also been following the other thread over the last few days, looks really exciting. If those guys get that thing working, that graphics boost would turn my t91 into a real cool speedy devil.

---

### Post by Leed on 2010-05-10
Minor disappointment on the train this morning, wanted to watch a video but the headphones jack doesn't work. Kinda strange, because the internal speakers have no problem at all and even the microphone works.

---

### Post by kgingeri on 2010-05-10
> **Leed said:**
> Minor disappointment on the train this morning, wanted to watch a video but the headphones jack doesn't work. Kinda strange, because the internal speakers have no problem at all and even the microphone works.

They will work if you go into sound properties (right-click the panel applet) and switch the Output tab param to headphones - but it's a manual process each time  :(

---

### Post by Leed on 2010-05-11
Btw. if you haven't been actively following 
[http://ubuntuforums.org/newreply.php?do=newreply&p=9274285]("http://ubuntuforums.org/newreply.php?do=newreply&p=9274285")

We have some heroes who have already gotten the psb drivers working, still working on 3D tho. The Netbook menu won't work with this, but the normal gnome desktop will.

> **lucazade said:**
> ```
wget http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh && sh ./poulsbo_lucid.sh
```

this is the correct one, there was a typo in my previous message.

---

### Post by kgingeri on 2010-05-11
> **Leed said:**
> Btw. if you haven't been actively following 
[http://ubuntuforums.org/newreply.php?do=newreply&p=9274285]("http://ubuntuforums.org/newreply.php?do=newreply&p=9274285")

We have some heroes who have already gotten the psb drivers working, still working on 3D tho. The Netbook menu won't work with this, but the normal gnome desktop will.

Actually the UNR menu works fine if you set UNR sessions to be 2D. In System menu fine the Login Screen (I think - i'm at work, cant check) and choose Netbook Launcher 2D. Maximus doesn't start but can be started manually, however you'll get a white screen for some time if you use the Go Home applet.  :)

---

### Post by kgingeri on 2010-05-12
Does anyone have a touchscreen working yet on Lucid?  I have a T91MT (vs T91) and eGalax is not the driver.  Evtouch used to work but I can't get stuff to compile.  Looks like bad incompatibilities with new kernel source  :(

@Leed:  Thanks for the link.  Display is working not too bad.  Stuff does hang my machine - like trying to rotate with xrandr etc but it is usable.  I had to set UNE 2D as my session type as well.  The thread is pretty active and lucazade is doing some great work!

---

### Post by Leed on 2010-05-12
They sure are doing great work, especially lucazade and jbernado...

The touchscreen is working on my T91 out of the box, but I haven't gotten round to calibrating it properly. I've had some tips on 3rd party applications that should give data you can insert into xorg.conf... but nothing really simple and useful so far.

---

### Post by kgingeri on 2010-05-12
> **Leed said:**
> They sure are doing great work, especially lucazade and jbernado...

The touchscreen is working on my T91 out of the box, but I haven't gotten round to calibrating it properly. I've had some tips on 3rd party applications that should give data you can insert into xorg.conf... but nothing really simple and useful so far.

Hmmm, my touch screen is not responsive and I see nothing in /proc/bus/input/devices at all for it!  :(  I've been chatting on the [other T101MT thread and Plippo]("http://ubuntuforums.org/showpost.php?p=9285126&postcount=47") suggested the evdev driver.  I seem to recall messing with that too originally.  Think I'll try it again when I get a chance.  Thanks for your response!

---

### Post by kwabou on 2010-05-12
If you'd like to calibrate the touchscreen in 10.04, just do the following:

First, install the Linux driver from the manufacturer of the touchscreen. When it asks what type it is, enter '0' for USB:
```
wget http://www.ideacom.com.tw/download/DRIVE/IDC_Linux_3_1_0.tar.gz
tar xvzf IDC_Linux_3_1_0.tar.gz
cd IDC_Linux_3_1_0
sudo ./IDC_setup.sh
```
Your xorg.conf will now have the appropriate device section for the touch screen.

Reboot.

To calibrate, use the following command:
```
sudo /usr/local/IDC/calibration
``` 

Enjoy!

Edit: For t91 only (as far as I know)

---

### Post by kgingeri on 2010-05-13
> **kwabou said:**
> If you'd like to calibrate the touchscreen in 10.04, just do the following:

First, install the Linux driver from the manufacturer of the touchscreen. When it asks what type it is, enter '0' for USB:
```
wget http://www.ideacom.com.tw/download/DRIVE/IDC_Linux_3_1_0.tar.gz
tar xvzf IDC_Linux_3_1_0.tar.gz
cd IDC_Linux_3_1_0
sudo ./IDC_setup.sh
```
Your xorg.conf will now have the appropriate device section for the touch screen.

Reboot.

To calibrate, use the following command:
```
sudo /usr/local/IDC/calibration
``` 

Enjoy!

Edit: For t91 only (as far as I know)

Whoa!  That just about 'bricked' my system!!  Luckily there is an "uninstall" param for the IDC_setup.sh script (available in safe mode) or I would have been in for a complete reinstall  :o

**[COLOR="Red"]IDC is definitely for the [B]T91** only!
[/COLOR][/B]

---

### Post by HarrisonNapper on 2010-05-13
The IDC calibration worked for me except on the screen edges for some reason.

Anyone else having this problem?

Cheers to all of the work that has been done on this in the last month or so. Things have come a looooong way for the usability of my T91SA in Lubuntu. Thank you all. :)

---

### Post by kwabou on 2010-05-13
My touch screen worked before calibration, except for on the edges (and it was inaccurate the further towards the edges you went). After IDC, before I found the calibration, I tried xinput_calibrate. It never worked, sometimes forcing the cursor to the bottom right corner no matter where I touched the screen. The reason I mention this then, is that the output of xinput_calibrate showed me the proper IDC version number. For my T91, my screen is IDC 6680, and that is the driver I linked above. There is also a 6681 driver. Not sure how much of a difference this could make (as that's not the version mine is)...

---

### Post by HarrisonNapper on 2010-05-14
After calibration, did you immediately restart X?

---

### Post by Leed on 2010-05-17
> **kwabou said:**
> If you'd like to calibrate the touchscreen in 10.04, just do the following:

First, install the Linux driver from the manufacturer of the touchscreen. When it asks what type it is, enter '0' for USB:
```
wget http://www.ideacom.com.tw/download/DRIVE/IDC_Linux_3_1_0.tar.gz
tar xvzf IDC_Linux_3_1_0.tar.gz
cd IDC_Linux_3_1_0
sudo ./IDC_setup.sh
```
Your xorg.conf will now have the appropriate device section for the touch screen.

Reboot.

To calibrate, use the following command:
```
sudo /usr/local/IDC/calibration
``` 

Enjoy!

Edit: For t91 only (as far as I know)

Finally got round to testing this... Absolutely cool calibration tool!!! Works a charm on my T91, thanks a lot.

---

### Post by kwabou on 2010-05-17
Haven't figured out right click yet, but finally having a calibrated touch screen is nice.

EDIT: Right click works with the stylus but not my finger for some reason. Just tap and hold for 1.5 seconds. Found in /usr/local/IDC/setting.txt

---

### Post by HarrisonNapper on 2010-05-17
> **kwabou said:**
> Haven't figured out right click yet, but finally having a calibrated touch screen is nice.

EDIT: Right click works with the stylus but not my finger for some reason. Just tap and hold for 1.5 seconds. Found in /usr/local/IDC/setting.txt

Do you have the problem of the cursor position messing up at the edges of the screen?

---

### Post by kwabou on 2010-05-18
> **HarrisonNapper said:**
> Do you have the problem of the cursor position messing up at the edges of the screen?

No I do not. Make sure you run the calibration tool as the superuser, and restart X/your computer afterwards.

Also, in the setting.txt file, I changed the timeout to 1000 (ms) and the movement to 100 (Originally 30 or something low) and I can now get right click menus using my finger.

---

### Post by Roman Shuvalov on 2010-05-19
I can't calibrate touchscreen. I'm running:

sudo /usr/local/IDC/calibration 

then calibration tool appears and immediately closes. No output at console. video driver - poulsbo by lucazade (1024x600)

---

### Post by HarrisonNapper on 2010-05-19
> **kwabou said:**
> No I do not. Make sure you run the calibration tool as the superuser, and restart X/your computer afterwards.

Also, in the setting.txt file, I changed the timeout to 1000 (ms) and the movement to 100 (Originally 30 or something low) and I can now get right click menus using my finger.

Tried again and it worked. Not sure why it didn't the first few times, but thank you :)

Now to tackle a new problem: hard lock ups while using gimp or mtPaint. Strangest thing is nothing in syslogs, so I'm guessing hardware/bios/etc problems. Will keep you all posted.

EDIT: turns out, this hard lock up also happens when I switch to dvorak and back to us using xkbsel <layout>, which is consistent since my arrow keys are disabled in dvorak for some reason (no big loss there)

EDIT 2: lock up no longer happens on switching keyboard layouts (still happens with graphics), but now when I switch to dvorak and back to us, I cannot use the keyboard (letter keys are dead); improvement nonetheless

---

### Post by HarrisonNapper on 2010-05-19
> **Roman Shuvalov said:**
> I can't calibrate touchscreen. I'm running:

sudo /usr/local/IDC/calibration 

then calibration tool appears and immediately closes. No output at console. video driver - poulsbo by lucazade (1024x600)

To verify no output, do this:

```


cd /usr/local/IDC/
sudo ./calibration > ~/A_FILE_NAME.txt
cat ~/A_FILE_NAME.txt


```

For "A_FILE_NAME" use anything that is not already a file in your home directory.

---

### Post by DrPotoroo on 2010-05-19
> **HarrisonNapper said:**
> 
 
EDIT: turns out, this hard lock up also happens when I switch to dvorak and back to us using xkbsel <layout>, which is consistent since my arrow keys are disabled in dvorak for some reason (no big loss there)
 
Wow! Another dvorak user running Ubuntu on a T91. There can't be many of us. I don't have your arrow key problem (although I'm still running 9.10). I switch keyboards by adding additional layouts in the gnome keyboard setup utility and setting the windows-style "alt-shift" as a switching shortcut.

---

### Post by HarrisonNapper on 2010-05-20
> **DrPotoroo said:**
> Wow! Another dvorak user running Ubuntu on a T91. There can't be many of us. I don't have your arrow key problem (although I'm still running 9.10). I switch keyboards by adding additional layouts in the gnome keyboard setup utility and setting the windows-style "alt-shift" as a switching shortcut.

I think I just got that utility when I got baobab, so I shall give that a try. Lubuntu doesn't make it as easy as Gnome and KDE did, but it should work. If anything, I can modify xorg.

---

### Post by dfauvarq on 2010-05-20
I have a problem with the rotate screen on a regular Asus T91 (no MT) with Ubuntu 10.04 Lucid.

I installed the gma500 drivers from [https://launchpad.net/~gma500](https://launchpad.net/~gma500) and the touchscreen driver from the vendor indicated on the previous threads.

Resolution is good, touchscreen is working and calibrating OK.

But when I rotate the screen with "xrandr -o left" (or right) the screens gets black and I can only force poweroff.

xrandr -o inverted or normal work correctly.

any hints ? is this a known bug of this version of the driver. It used to work without any problem on Ubuntu 9.1. I'm using this feature to use the T91 as a Portrait tablet.

Thanks for the help
Daniel

---

### Post by dfauvarq on 2010-05-20
Found a crash of the X server in the gdm log. If a developer of the GMA 500 is monitoring this thread here is the back trace:

                        (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xd53410]
3: /usr/bin/X (xf86DisableUnusedFunctions+0x8c) [0x80cc49c]
4: /usr/bin/X (0x8048000+0x8dc97) [0x80d5c97]
5: /usr/bin/X (RRCrtcSet+0x95) [0x8108e55]
6: /usr/bin/X (ProcRRSetScreenConfig+0x40c) [0x810ea2c]
7: /usr/bin/X (0x8048000+0xbe945) [0x8106945]
8: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
9: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
10: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x168bd6]
11: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address 0x20

Caught signal 11 (Segmentation fault). Server aborting

---

### Post by HarrisonNapper on 2010-05-20
> **dfauvarq said:**
> I have a problem with the rotate screen on a regular Asus T91 (no MT) with Ubuntu 10.04 Lucid.

I installed the gma500 drivers from [https://launchpad.net/~gma500]("https://launchpad.net/%7Egma500") and the touchscreen driver from the vendor indicated on the previous threads.

Resolution is good, touchscreen is working and calibrating OK.

But when I rotate the screen with "xrandr -o left" (or right) the screens gets black and I can only force poweroff.

xrandr -o inverted or normal work correctly.

any hints ? is this a known bug of this version of the driver. It used to work without any problem on Ubuntu 9.1. I'm using this feature to use the T91 as a Portrait tablet.

Thanks for the help
Daniel

Does the following or some variant thereof work?

[http://setupguides.blogspot.com/2010/01/eanbling-screen-rotate-button-for-asus.html](http://setupguides.blogspot.com/2010/01/eanbling-screen-rotate-button-for-asus.html)

Probably goes without saying, but remember to back files up before modifying them.

---

### Post by dfauvarq on 2010-05-20
Yes I did this setup and the button is working correctly, it is unfortunately when the actual command is executed (xrandr) that X crashes.

I can reproduce the crash also if I manually setup the rotation to left in the Display options.

---

### Post by HarrisonNapper on 2010-05-21
> **HarrisonNapper said:**
> Tried again and it worked. Not sure why it didn't the first few times, but thank you :)

Now to tackle a new problem: hard lock ups while using gimp or mtPaint. Strangest thing is nothing in syslogs, so I'm guessing hardware/bios/etc problems. Will keep you all posted.

EDIT: turns out, this hard lock up also happens when I switch to dvorak and back to us using xkbsel <layout>, which is consistent since my arrow keys are disabled in dvorak for some reason (no big loss there)

EDIT 2: lock up no longer happens on switching keyboard layouts (still happens with graphics), but now when I switch to dvorak and back to us, I cannot use the keyboard (letter keys are dead); improvement nonetheless

EDIT 3: I caved and used this for dvorak:  ```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,dvorak
``` I added it to /etc/xdg/lxsession/Lubuntu/autostart  EDIT 4: It appears I hit the quote button instead.  Oh well. Lockups still happening; will post more info as I find it.

---

### Post by Leed on 2010-05-23
> **dfauvarq said:**
> I have a problem with the rotate screen on a regular Asus T91 (no MT) with Ubuntu 10.04 Lucid.

I installed the gma500 drivers from [https://launchpad.net/~gma500](https://launchpad.net/~gma500) and the touchscreen driver from the vendor indicated on the previous threads.

Resolution is good, touchscreen is working and calibrating OK.

But when I rotate the screen with "xrandr -o left" (or right) the screens gets black and I can only force poweroff.

xrandr -o inverted or normal work correctly.

any hints ? is this a known bug of this version of the driver. It used to work without any problem on Ubuntu 9.1. I'm using this feature to use the T91 as a Portrait tablet.

Thanks for the help
Daniel

The xrandr Problem is a bug I reported a while ago in Lucazade & Co's Group, I think we just have to wait for the experts to find a solution.

I didn't know that inverted works. But just for Info, you shouldn't force power off when things don't work, instead try the REISUB method.

hold alt+printScr and then press R, E, I, S, U and B after each other, give each letter one or two seconds time inbetween. Your pc will then reboot safely.

---

### Post by Roman Shuvalov on 2010-05-24
[]("http://ubuntuforums.org/member.php?u=911544")**dfauvarq**
so, you've installed pouulsbo driver from GMA500 PPA repository and ideacom (IDC) touchscreen driver and you don't have any random freezes and system crashes except xrandr? 

can you share your xorg.conf?

---

### Post by HarrisonNapper on 2010-05-24
> **Roman Shuvalov said:**
> []("http://ubuntuforums.org/member.php?u=911544")**dfauvarq**
so, you've installed pouulsbo driver from GMA500 PPA repository and ideacom (IDC) touchscreen driver and you don't have any random freezes and system crashes except xrandr? 

can you share your xorg.conf?

Ditto. Would love to be able to use my touchscreen without crashing computer :)

---

### Post by kwabou on 2010-05-25
poulsbo driver from other thread and IDC touchscreen driver.

Limited to no touchscreen use = no crash
Constant touchscreen use = crash(freeze) after an hour or so

Here is my xorg.conf:

```
Section "Device"
	Identifier "GMA500"
	Driver "psb"
	Option "ShadowFB" "true"
	#Option "DownScale" "false"
	#Option "ExaNoComposite" "false"
	#Option "ExaMem" "131072"
	#Option "ExaScratch" "4"
	#Option "ExaCached" "false"
	#Option "IgnoreACPI" "true"
	#Option "LidTimer" "false"
	#Option "MigrationHeuristic" "greedy"
	#Option "NoAccel" "false"
	#Option "NoFitting" "false"
	#Option "NoPanel" "false"
	#Option "SWcursor" "false"
	#Option "Vsync" "false"
EndSection

Section "DRI"
	Mode    0666
EndSection

Section "Extensions"
	Option	"Composite" "Disable"
	#Option	"RENDER" "Disable"
EndSection

Section "ServerFlags"
	#Option "AIGLX" "off"
	#Option "IgnoreABI" "off"
EndSection
### Touch Configuration Beginning ###
Section "ServerLayout"
        Identifier "Default Layout"
        InputDevice "IDCTouchScreen" "SendCoreEvents"
EndSection

Section "InputDevice"
      Identifier  "IDCTouchScreen"
      Driver      "idctouch"
      Option      "Device" "/dev/idcts"
      Option      "Interface" "0"
      Option      "DeviceName" "IDCTouchScreen"
      Option      "MinX" "0"
      Option      "MinY" "0"
      Option      "MaxX" "8191"
      Option      "MaxY" "8191"
      Option      "ScreenNumber"  "0"
      Option      "ButtonNumber"  "2"
      Option      "ReportingMode" "Raw"
      Option      "Emulate3Buttons"   "0"
      Option      "DebugLevel"    "0"
      Option      "SendCoreEvents" "On"
      Option      "RealLeftBtn" "1"
      Option      "ReverseBtnRelease" "0"
      Option      "ProcPolltime" "2000"
      Option      "IsPnp" "0"
      Option      "SelfOnPoll" "2000"
      Option      "LoginRes" "1"
EndSection
      ## IdeaCom Touch Screen script end ##"
```

---

### Post by dfauvarq on 2010-05-26
Here is my xorg.conf generated automatically by the driver installation + touchscreen driver installation and calibration as explained in this thread.

I haven't experienced any freezes yet but I must admit that I didn't use it on this configuration long enough and using the touchscreen long enough to experience it.

Note that I'm not using any 3D fancy stuff nor compiz.

Daniel


Section "DRI"
    Mode    0666
EndSection

Section "Device"
    Identifier    "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "DRI" "on"
        Option "MigrationHeuristic" "greedy"
        Option "NoDDC"
        Option "IgnoreACPI" "yes"
    Driver    "psb"
    Option    "ShadowFB"    "True"
EndSection

### Touch Configuration Beginning ###
Section "ServerLayout"
        Identifier "Default Layout"
        InputDevice "IDCTouchScreen" "SendCoreEvents"
EndSection

Section "InputDevice"
      Identifier  "IDCTouchScreen"
      Driver      "idctouch"
    Option      "Device" "/dev/idcts"
Option      "Interface" "0"
      Option      "DeviceName" "IDCTouchScreen"
      Option      "MinX" "0"
      Option      "MinY" "0"
      Option      "MaxX" "8191"
      Option      "MaxY" "8191"
      Option      "ScreenNumber"  "0"
      Option      "ButtonNumber"  "2"
      Option      "ReportingMode" "Raw"
      Option      "Emulate3Buttons"   "0"
      Option      "DebugLevel"    "0"
      Option      "SendCoreEvents" "On"
      Option      "RealLeftBtn" "1"
      Option      "ReverseBtnRelease" "0"
      Option      "ProcPolltime" "2000"
      Option      "IsPnp" "0"
      Option      "SelfOnPoll" "2000"
      Option      "LoginRes" "1"
EndSection
      ## IdeaCom Touch Screen script end ##"

---

### Post by pinkflamingo8806 on 2010-05-27
I have been dealing with those hard freezes for a long time.  Again, attributed to using the touchscreen for a while.  It's very annoying when I'm taking notes in class because I have to reboot 2 or 3 times per class.

Thanks

---

### Post by mechashiva119 on 2010-05-27
I don't know if I'm a special case or what, but using Xournal my T91 will hard freeze within a minute or two. Poulsbo 500 installed, running in 2D mode, perfect calibration though!

---

### Post by HarrisonNapper on 2010-05-28
Mine's the same, mecha. It's a shame because the whole reason I got it was to use gIMP. It's like being stuck between Windows XP where I can use the touchscreen and gIMP, but not scriptfu and Ubuntu where I can't use the touchscreen, but can use touchpad with gIMP and have scriptfu.

It's like that, but not really since I would never consider using Windows regardless. :)

Good thing I'm a terrible artist, so it's not a big loss.

---

### Post by DrPotoroo on 2010-05-29
> **HarrisonNapper said:**
> Mine's the same, mecha. It's a shame because the whole reason I got it was to use gIMP. It's like being stuck between Windows XP where I can use the touchscreen and gIMP, but not scriptfu and Ubuntu where I can't use the touchscreen, but can use touchpad with gIMP and have scriptfu.

It's like that, but not really since I would never consider using Windows regardless. :)

Good thing I'm a terrible artist, so it's not a big loss.

I don't have crashes in xournal or gimp. But I did find I got crashes all the time when I had fdi settings that simulated a right click if the pointer was held down. Do you have any settings like that to simulate right clicks?

---

### Post by ah_mad on 2010-05-29
> **DrPotoroo said:**
> I don't have crashes in xournal or gimp. But I did find I got crashes all the time when I had fdi settings that simulated a right click if the pointer was held down. Do you have any settings like that to simulate right clicks?

I always get crash on right click simulation. What I do, is that i press Alt+Ctrl+F1, log in, type top. Mousetweak is always at the top. I can't kill it with killall but I kill it by

kill -n 5 [mousetweak PID]

and then Alt+Ctrl+F7, and everything back to normal (without simulator of course).

---

### Post by pinkflamingo8806 on 2010-06-10
yes, I think my problems are related to right-click simulation. How do you adjust those settings?

---

### Post by H3g3m0n on 2010-06-10
I turned on the right click simulation option in the System>Mouse area on my T91MT running 9.10 and got a freeze today (I ctrl+alt+f1'd to a console, saw mousetweak was using all the cpu and killed it then when back into xorg without issues).

Previously I have had no problems what so ever with the system locking up.

The right click option in the mouse settings is close to useless on this system too, it's very hard to keep the cursor steady enough for it to be picked up. I'll just disable it.

Those of you with problems, might wan't to have a go at the way I normally use right click on the system.

Install the easystroke package, set it to autorun, set it to work with the first mouse button and bind a simple gesture to right click (I use down then up since it is easy enough to right click the notification icons up the top of the screen and you don't need to do down the bottom, also as you go down first your finger isn't over the area you are going to have to move back up to in order to right click there).

The only problems with easystroke is it can interfere with painting programs, you can exclude them and loose the right click option but with most of them right clicking isn't needed as things like gimp have menus (and I don't use them much on the netbook anyway).

The other problem is to do something like select text or drag you have to hold for a little bit before you move your finger (the delay cancels the gesture input mode) but it becomes fairly natural after a little while and you don't think about it (it only needs a very short delay, not enough to be annoying and you can customize the length).

You also get the added benefit of gestures to launch programs and even enter text (if you can be bothered to invent strokes for every letter, there doesn't appear to be a way to do shift either) which is damn handy. Also bind strokes for left, right, up, down, enter and space which will allow navigation of things like comix and ebook readers. I also bound left with a tick up and right with a tick up for alt+left/right for changing tabs, and up/down with a tick for pageup/down.

---

### Post by pinkflamingo8806 on 2010-06-10
i have that mouse setting disabled already and I have never seen mousetweak running.  when i get the freezes I can't do anything but reboot via power button or R-E-I-S-U-B.  Is there something in xorg.conf or any driver config files that contain right click info?  I am using the ldc driver in lucid but i had this problem in karmic and jaunty using evtouch too.

---

### Post by dfauvarq on 2010-06-17
Some update on my T91.

The rotation issue posted earlier has been fixed, thanks to the developper. GMA500 driver seems to work with no problem. 

I have the touch screen driver installed from the vendor and it is calibrated correctly when the screen is in the normal position.

My problem is when I rotate the screen, the pointer is not under the place I touch anymore. It sounds like the change of coordinates that is taken into account for the mouse is not taken into account for the touchscreen.

Anyone help would be apreciated.

my xorg.conf looks like this:


Section "DRI"
    Mode    0666
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "psb"
    Option    "ShadowFB"    "True"
EndSection

### Touch Configuration Beginning ###
Section "ServerLayout"
        Identifier "Default Layout"
        InputDevice "IDCTouchScreen" "SendCoreEvents"
EndSection

Section "InputDevice"
      Identifier  "IDCTouchScreen"
      Driver      "idctouch"
    Option      "Device" "/dev/idcts"
Option      "Interface" "0"
      Option      "DeviceName" "IDCTouchScreen"
      Option      "MinX" "0"
      Option      "MinY" "0"
      Option      "MaxX" "8191"
      Option      "MaxY" "8191"
      Option      "ScreenNumber"  "0"
      Option      "ButtonNumber"  "2"
      Option      "ReportingMode" "Raw"
      Option      "Emulate3Buttons"   "0"
      Option      "DebugLevel"    "0"
      Option      "SendCoreEvents" "On"
      Option      "RealLeftBtn" "1"
      Option      "ReverseBtnRelease" "0"
      Option      "ProcPolltime" "2000"
      Option      "IsPnp" "0"
      Option      "SelfOnPoll" "2000"
      Option      "LoginRes" "1"
EndSection
      ## IdeaCom Touch Screen script end ##"

---

### Post by dfauvarq on 2010-06-20
Found the solution for the touchscreen and rotation with the help of some other forums.

First on my T91 no MT, desinstall the IDC touch driver under /usr/local/IDC, the default one works better.

Then calibrate the touchscreen, personally I had to calibrate it manually using the xinput command, the xinput_calibrator_x11 didn't provide good results for me.
Here is the command that works for my screen:
xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axis Calibration" 32 300 7900 400 7800

to have this command executed at each start of an X session I created a script under 
/etc/X11/Xsession.d/98x11-common_touchscreen 
with only that command

Then I changed the /etc/acpi/rotatescreen.sh to add xinput commands to swap axes, here is the script (note that I changed right to left for the rotation):

#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
  left)
  NEW_ROTATION="normal"
  ;;
  *)
  NEW_ROTATION="left"
  ;;
esac

for x in /tmp/.X11-unix/*; do
  displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
  getXconsole;
  case $NEW_ROTATION in
  left)
    xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axis Inversion" 8 1 0
    xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axes Swap" 8 1
    ;;
  normal)
    xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axis Inversion" 8 0 0
    xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axes Swap" 8 0
    ;;
  esac
  if [ x"$XAUTHORITY" != x"" ]; then
      export DISPLAY=":$displaynum"
      /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
  fi
done

---

### Post by nothing42 on 2010-06-27
This worked liked a charm for me today on my t91 in 10.04 with default touchscreen drivers... with only one slight thing to look out for in your instructions.

My "IDEACOM  IDC 6680" was actually "IDEACOM   IDC 6680" with two spaces between IDEACOM and IDC.  A quick check of the /var/log/Xorg.0.log in gedit and a search for IDEACOM verified that.  Thanks!

---

### Post by Mizukusai on 2010-06-28
Are you saying that Lucid Lynx is working on your T91 ?
I though the gma drivers didn't exist for Xorg 1.7, shipped with 10.04 ?

---

### Post by H3g3m0n on 2010-06-29
> **Mizukusai said:**
> Are you saying that Lucid Lynx is working on your T91 ?
I though the gma drivers didn't exist for Xorg 1.7, shipped with 10.04 ?

They exist now, although there still a bit experimental.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

Just wish I could get my T91MT touchscreen working :(
[http://ubuntuforums.org/showthread.php?t=1507489](http://ubuntuforums.org/showthread.php?t=1507489)

The normal T91 apparently works fine though.

---

### Post by Mizukusai on 2010-06-29
Good news. I'll try as soon as I have a moment.

---

### Post by pinkflamingo8806 on 2010-07-19
I tried using the default driver and manually calibrating the screen and came across an interesting problem.  When I tap the screen in one location and pick up the pen and tap another spot on the screen, it doesn't 'lift' the pen tip.  In other words, it draws a line between the two points.  Is there something in xinput that I need to set?

Thanks

---

### Post by pinkflamingo8806 on 2010-07-20
Not to mention, should I have 2 copies of IDEACOM  IDC 6680 in xinput list?

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; IDEACOM  IDC 6680                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; IDEACOM  IDC 6680                       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=10	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```

---

### Post by mechashiva119 on 2010-08-06
hey, i had a question. It seems that simply disabling the right click option has ended the hard-freezes.

I'm having a new unrelated problem, and was wondering if it was universal. I just installed skype, and fixed the audio. I am, however, totally unable to see the people i'm chatting with. Is this solvable? thanks alot.

---

### Post by bkruggel on 2010-08-07
Mousetweaks can't be the reason for me, since I didn't even have it installed. I tried with it installed (just to be sure) and right click disabled and didn't change either.
Some ideas about the freezes.
Does somebody else get "report_id 10 received" in dmesg when using the touch screen? When i use it, I get a good hundreds of them within only 1 second.

When it freezes, I can still ssh into the machine and stop X, but the display will stay the way it was when the computer froze. Does that mean that the poulsbo driver is to blame?

---

### Post by HarrisonNapper on 2010-08-23
Anyone have any update on the freezing/crashing issues? I'm going to upgrade Jolicloud 1.0 today and see if the touchscreen support for the T91 has improved. Supposed to work out of the box. If not, before I go through a 4th OS install (XP then Lubuntu then Jolicloud then theoretically Ubuntu or Kubuntu), I want to be fairly certain it will not crash every few minutes.

---

### Post by mechashiva119 on 2010-08-25
Best of luck Harrison! Please post what you find about jolicloud 1.0!
I even went back to 9.10 as there were less extraneous minor glitches in it, so yeah, its still freezing like crazy.

---

### Post by buee on 2010-09-16
I have the T91SA and touchscreen worked out of the box on 10.04.  The only problem I'm having with it is getting the screen rotation to work with the button.  I've tried multiple solutions I've found by googling and the ones listed here to no avail.  My button still does nothing.  Any ideas?

---

### Post by H3g3m0n on 2010-09-19
> **buee said:**
> I have the T91SA and touchscreen worked out of the box on 10.04.  The only problem I'm having with it is getting the screen rotation to work with the button.  I've tried multiple solutions I've found by googling and the ones listed here to no avail.  My button still does nothing.  Any ideas?

Try seeing if 'xrandr -o left' works. 

Also have a look at editing the /etc/acpi/rotatescreen.sh script
[http://ubuntuforums.org/showthread.php?t=1507489](http://ubuntuforums.org/showthread.php?t=1507489)

---

### Post by buee on 2010-10-01
> **H3g3m0n said:**
> Try seeing if 'xrandr -o left' works. 

Also have a look at editing the /etc/acpi/rotatescreen.sh script
[http://ubuntuforums.org/showthread.php?t=1507489](http://ubuntuforums.org/showthread.php?t=1507489)

xrandr -o left doesn't do anything.  I get the following error:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

I went to that forum post you suggested and the screen still won't rotate.  Either by command or the button.  Any other ideas?

---

### Post by H3g3m0n on 2010-10-01
> **buee said:**
> xrandr -o left doesn't do anything.  I get the following error:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

I went to that forum post you suggested and the screen still won't rotate.  Either by command or the button.  Any other ideas?

If it's not working from the command, nothing will get the button to work.

Sounds like the GMA500 drivers haven't been installed correctly, or maybe installed out-of-date drivers via an old method?
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by buee on 2010-10-02
> **H3g3m0n said:**
> If it's not working from the command, nothing will get the button to work.

Sounds like the GMA500 drivers haven't been installed correctly, or maybe installed out-of-date drivers via an old method?
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

I was actually reloading Ubuntu when you sent this message.  But I had been to that link and installing the drivers apparently didn't work.  For some reason it did work this time, I could definitely tell the difference in video quality before screwing with the rotation of the screen.  Any way to get it to do 90, 180, 270 degrees?

---

### Post by H3g3m0n on 2010-10-02
> **buee said:**
> I was actually reloading Ubuntu when you sent this message.  But I had been to that link and installing the drivers apparently didn't work.  For some reason it did work this time, I could definitely tell the difference in video quality before screwing with the rotation of the screen.  Any way to get it to do 90, 180, 270 degrees?

If the drivers are now working, screen rotation should work fine with:
```
xrandr -o left
xrandr -o right
xrandr -o inverted
xrandr -o normal

```

At least it does on mt T91MT.

If you want quick access to the rotations, there is a gnome applet you could try that allow you to select the rotation from a drop down menu.
System->Preferences->Monitor, "Show monitors in panel"

If your wanting it to work with the extra rotations via the rotate screen button, your going to have to modify the script to add the extra rotations. I don't think it would be worth bothering as it takes a few seconds for each rotation so the complete cycle could be 10+seconds, it's much easier to just toggle between normal and either left or right (I chose left since it puts the stylus up the top right). There is no on screen app like the official ASUS one that I know of (although it wouldn't be to hard to code one up).

There's not really any point to rotating it in other directions though, its easier to just turn the system upsidedown...

---

### Post by RockyM93 on 2010-10-05
> **dfauvarq said:**
> Found the solution for the touchscreen and rotation with the help of some other forums.

First on my T91 no MT, desinstall the IDC touch driver under /usr/local/IDC, the default one works better.

Then calibrate the touchscreen, personally I had to calibrate it manually using the xinput command, the xinput_calibrator_x11 didn't provide good results for me.
Here is the command that works for my screen:
xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axis Calibration" 32 300 7900 400 7800

to have this command executed at each start of an X session I created a script under 
/etc/X11/Xsession.d/98x11-common_touchscreen 
with only that command



Literally just registered to say: dfauvarq, you're an absolute legend. I figured out ages ago that the Ideacom drivers were causing random freezes, and since then I've spent goodness knows how many hours trying to find a way to calibrate the default ones.

As I said. Absolute. Legend.

:P

---

### Post by jamespcole on 2010-10-13
> **pinkflamingo8806 said:**
> I tried using the default driver and manually calibrating the screen and came across an interesting problem.  When I tap the screen in one location and pick up the pen and tap another spot on the screen, it doesn't 'lift' the pen tip.  In other words, it draws a line between the two points.  Is there something in xinput that I need to set?

Thanks
I have exactly the same issue in 10.10, has anyone found a solution to this yet?  

BTW: if anyone is using Docky on 10.10 with the gma500 drivers I have posted a solution to the compositing error.

[http://setupguides.blogspot.com/2010/10/installing-elegant-gnome-on-ubuntu-1010.html](http://setupguides.blogspot.com/2010/10/installing-elegant-gnome-on-ubuntu-1010.html)

---

### Post by rentabuddha on 2010-11-03
For 10.10 with a T91MT, try here: [http://ubuntuforums.org/showthread.php?t=1595220](http://ubuntuforums.org/showthread.php?t=1595220)

It includes instructions for the rotation button but there have been unsolved problems across the board. For me, its not that my wireless gets disabled but it simply doesn't work haha

---

### Post by nh2 on 2010-12-15
> **pinkflamingo8806 said:**
> I tried using the default driver and manually calibrating the screen and came across an interesting problem.  When I tap the screen in one location and pick up the pen and tap another spot on the screen, it doesn't 'lift' the pen tip.  In other words, it draws a line between the two points.  Is there something in xinput that I need to set?

This is this bug: [https://bugs.launchpad.net/ubuntu/+bug/573006](https://bugs.launchpad.net/ubuntu/+bug/573006)

Please confirm it and add your hardware details.

Seems to be a driver bug, the driver is reporting wrong positions. I might be able to fix it if somebody could tell me which driver/package/source code is actually used.

---

### Post by pinkflamingo8806 on 2011-01-26
> **nh2 said:**
> This is this bug: [https://bugs.launchpad.net/ubuntu/+bug/573006](https://bugs.launchpad.net/ubuntu/+bug/573006)

Please confirm it and add your hardware details.

Seems to be a driver bug, the driver is reporting wrong positions. I might be able to fix it if somebody could tell me which driver/package/source code is actually used.

Could you elaborate on what you are looking for?  I am using 10.04 still.

---

### Post by mikeypizano on 2011-03-31
Has anyone found a fix for the problem with touchscreen not lifting the pointer yet for 10.10???

---

### Post by jtjs on 2011-04-01
> **mikeypizano said:**
> Has anyone found a fix for the problem with touchscreen not lifting the pointer yet for 10.10???

The pointer doesn't lift? I can't say I've had that issue in 10.10.

Can you elaborate?

---

### Post by mikeypizano on 2011-04-01
> **jtjs said:**
> The pointer doesn't lift? I can't say I've had that issue in 10.10.

Can you elaborate?

When you tap, and tap somewhere else, the cursor stays clicked down and will draw a line between the two points.

---

### Post by pinkflamingo8806 on 2011-04-06
Adding a ppa for xorg-edgers works for me.
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
Run the Ubuntu update utility and make sure you deselect all of the video packages or it will blow up your hard work getting the psb drivers to work.

My only problem now is that I don't know how to calibrate the touchscreen.  I downloaded a utility called xinput_calibrator, but it doesn't seem to work.  Any thoughts?

[https://github.com/tias/xinput_calibrator/downloads]("https://github.com/tias/xinput_calibrator/downloads")

---

### Post by jtjs on 2011-04-07
> **mikeypizano said:**
> When you tap, and tap somewhere else, the cursor stays clicked down and will draw a line between the two points.

Sounds like something is wrong with your t91mt.

Do you have any issues when using the track pad by any chance? How about the track pad's right and left click buttons?

---

### Post by Lencho66 on 2011-05-01
I am new to this world of Linux.  I would be lying if I said that I knew how to do any of this.  Where doI go exactly to make these changes to get my rotation button working?  Also, is there a way to get wifi working without having to open a terminal and type *sudo rfkill unblock all* each time I turn on the machine?

---

### Post by thopiekar on 2011-05-17
> **mikeypizano said:**
> Has anyone found a fix for the problem with touchscreen not lifting the pointer yet for 10.10???
try my packages for the GMA500 team at: ppa:gma500/emgd
do a upgrade and it should work fine

---

### Post by musheno on 2011-06-15
After following this thread, everything seems to work ok, except for the external video seems to no longer work... is there something I am missing or was disabled by one of the other settings?

Todd

---

### Post by onebir on 2011-07-09
> **pinkflamingo8806 said:**
> My only problem now is that I don't know how to calibrate the touchscreen.  I downloaded a utility called xinput_calibrator, but it doesn't seem to work.  Any thoughts?

[https://github.com/tias/xinput_calibrator/downloads](https://github.com/tias/xinput_calibrator/downloads) It didn't work for me either. But adding the file below as* /etc/X11/Xsession.d/98x11-common_touchscreen* did:
```
#!/bin/sh
# calibrates touchscreen for each X session

xinput set-int-prop 9 "Evdev Axis Calibration" 32 300 7900 400 7800
```

(From here: [http://setupguides.blogspot.com/2010/10/calibrating-touchscreen-in-ubuntu-1010.html](http://setupguides.blogspot.com/2010/10/calibrating-touchscreen-in-ubuntu-1010.html))

Note that the 9 might be different; use the ID from the first "IDEACOM  IDC 6680" device displayed after doing:
```
xinput list
```

---

### Post by onebir on 2011-07-09
I'm trying to get gestures working without having to press a mouse button, by getting bezel button (usually used for screen rotation but often broken) to stand in, via a script called xdotool ([http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/)). (It's available from the software centre.) This would make Easystroke gestures usable in tablet configuration - making that configuration a lot more useful.

It should be really simple, but unfortunately I haven't been successful so far. This is what I've tried.

Based on tips earlier in this thread, I put two event handlers in /etc/acpi/events/
1) asus-fake-mousedown:
```
event=hotkey (ATKD|HOTK) 0000007b
action=/etc/acpi/fakemousedown.sh
```2) asus-fake-mouseup:
```
event=hotkey (ATKD|HOTK) 0000007d
action=/etc/acpi/fakemousedup.sh
```In /etc/acpi I put 1) fakemousedown.sh
```
#!/bin/sh
#
# simulates mouse down action when bevel 
xdotool mousedown 1
```

and 2) fakemouseup.sh
```
#!/bin/sh
#
# simulates mouse down action when bevel 
xdotool mouseup 1

```The xdotool commands work ok from the command line, as does invoking the shell scripts. Any ideas what the problem might be?

---

### Post by HarrisonNapper on 2011-08-23
Is anyone using 10.10 on the T91? The HardwareComponent... GMA500 driver wiki indicates that 10.10 works well, but for me when I install it to sdb and do an upgrade, it won't even boot. I get an error "invalid arch independent ELF magic. Aborted. Press any key to exit."

Furthermore, below are various operating systems and their results (yes, this has consumed a notable chunk of my life):

1. Ubuntu 0.0-9.10: If it supports poulsbo, there is a great deal of crashing; especially when using the touchscreen.
2. Jolicloud (any version): See above.
3. Ubuntu 10.04+ (EMGD enabled):
     a. Ubuntu 10.04: I'm trying it next
     b. Ubuntu 10.10: Install, upgrade, no boot
     c. Lubuntu 10.10: Install, upgrade, no boot (but in a less expressive way), also has a tendency to install grub to first partition (very windowsy thing to do) even if use whole disk is selected for sdb (why the behavior differs in ubiquity, not sure)
     d. Ubuntu 11.04: Once EMGD is installed, you CANNOT (read as "I wasn't able to") upgrade or downgrade the kernel. Also, it doesn't work. Which is really the more relevant part there. I tried this two ways: install, update, upgrade kernel, install emgd (emgd wouldn't install); and install, install emgd, upgrade kernel, <fails>
     e. Lucid Puppy 5.2.8: Actually works pretty well except the wireless drivers are pretty bad, so it's impossible to download or install just about anything.

If anyone has ANY distro running on the T91 wherein:
1. The resolution is LCD-1024x600-24
2. The touchscreen works without crashing and is calibrated
3. It can run on an SD card (not the SSD) (in the case of the T91 this is generally /dev/sdb)

Please post a full installation guide from start to finish. I know that I would be very grateful and I'm sure there are others who will as well. Even if it's a high-level overview, that would work, too. I assume that all of these problems stem from trying to install to sdb since things seem to work for everyone installing to the SSD and the main problem so far has been boot problems.


EDIT: I'm still working on 10.10, so if that ends up being successful, I will post the full guide. At the moment, since it wouldn't boot, I wanted to use boot-repair (because it's easier), but apt hung on installing a ubiquity package, so trying to fix that to fix the repair install to fix grub to fix boot to install emgd and hopefully fix upgrading problems I've seen with emgd and other kernels/packages. In any case, it might be awhile, but will let everyone know.

UPDATE: 10.10 didn't work. I tried boot-repair livecd, both options, as well as one pass with the advanced mode. I think bottom line is that grub needs to be on /dev/sda. Because I am apparently a masochist, I'm now installing 10.04 to see if it behaves differently. So far pre-update everything works on 10.10 buntu installs, but once you update packages (200 or 300 depending on install), it gets nerfed. I assume it's a grub update, but that's one place to start in 300 packages.

---

### Post by onebir on 2011-08-23
> **HarrisonNapper said:**
> 
1. The resolution is LCD-1024x600-24
2. The touchscreen works without crashing and is calibrated
3. It can run on an SD card (not the SSD) (in the case of the T91 this is generally /dev/sdb)
2 ish - the commands I found & posted above got the touchscreen calibrated in 11.04, but it seems to fall asleep or something. Very irritating when reading an ebook. Which is basically what I bought the bloody thing for. (But probably you meant 1 & 2 & 3...)

> **HarrisonNapper said:**
> EDIT: I'm still working on 10.10, so if that ends up being successful, I will post the full guide. At the moment, since it wouldn't boot, I wanted to use grub-repair (because it's easier), but apt hung on installing a ubiquity package, so trying to fix that to fix the repair install to fix grub to fix boot to install emgd and hopefully fix upgrading problems I've seen with emgd and other kernels/packages. In any case, it might be awhile, but will let everyone know.
If you have any success, this fellow T91 victim would much appreciate any guidance you can offer!

(BTW, I have a vague impression the EMGD repos are dead. Or I can't access them for upgrades or something...)

---

### Post by HarrisonNapper on 2011-08-23
> **onebir said:**
> 2 ish - the commands I found & posted above got the touchscreen calibrated in 11.04, but it seems to fall asleep or something. Very irritating when reading an ebook. Which is basically what I bought the bloody thing for. (But probably you meant 1 & 2 & 3...)


Yeah because unfortunately Windows couldn't install to the SD card (I haven't tried, but I've had bad experiences with this in the past), so it's on the SSD which is only the 16 GB one atm. The resolution is not as important, that's just a workflow thing, though I do highly prefer a legible resolution. All of this worked practically out of the box on puppy so if I can figure out how to fix the networking, I will post that as well, as that would be the best option for any eee.


Note to Googlers: if the length of this thread has not already convinced you, allow me to clarify: If you are considering purchasing an Asus EeePC T91SA (aka T91) or T91MT for the purpose of running Linux, look elsewhere, it will not work.

---

### Post by bkruggel on 2011-08-23
I wrote a pretty complete tutorial for Bodhi Linux, an Ubuntu spinoff, which should be perfectly applicable to Ubuntu Maverick.
It's here: [http://www.bodhilinux.com/forums/index.php?/topic/51-t91-bodhi-and-emgd/page__p__168__fromsearch__1#entry168](http://www.bodhilinux.com/forums/index.php?/topic/51-t91-bodhi-and-emgd/page__p__168__fromsearch__1#entry168)
Note to googlers: first hit with "T91 emgd"

If the problem is really booting from SD, then that won't help though.

Lucid had bad touchscreen support with this machine last time I tried. Bodhi is running pretty good, and loads very quickly (even from SD) - you might want to give it a try. All Ubuntu repos are still there, although they backport a lot by themselves. The base system is 2gb, so you might consider putting it alongside your 'other' system on the SSD.

The problem with the touchscreen going to sleep has to do with USB autosuspend. Turn it off and you're good.

Onebir: that's a neat idea! Maybe a DISPLAY variable problem? (xdotool wouldn't know 'where' to click?) Try and let me know!

---

### Post by HarrisonNapper on 2011-08-23
> I wrote a pretty complete tutorial for Bodhi Linux, an Ubuntu spinoff, which should be perfectly applicable to Ubuntu Maverick.
It's here: [http://www.bodhilinux.com/forums/ind...ch__1#entry168](http://www.bodhilinux.com/forums/ind...ch__1#entry168)
Note to googlers: first hit with "T91 emgd"

I actually used that and cross-referenced [https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd) as well as the [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) page on the Ubuntu wiki.

For the new user, use the guide above, as it should work fine for 10.10 (all derivatives of Ubuntu 10.10). When I installed 11.04 that didn't work and that was a default install to the SSD on /dev/sda

> Lucid had bad touchscreen support with this machine last time I tried. Bodhi is running pretty good, and loads very quickly (even from SD) - you might want to give it a try. All Ubuntu repos are still there, although they backport a lot by themselves. The base system is 2gb, so you might consider putting it alongside your 'other' system on the SSD.

Quick load time is a big plus. And the battery life after power tweaks is similar to what I had running Lubuntu before I gave up on nix on the T91 the second time (this might be the third). I think it's just that grub for whatever reason will not work except running from /dev/sda.

---

### Post by bkruggel on 2011-08-23
> **HarrisonNapper said:**
> When I installed 11.04 that didn't work and that was a default install to the SSD on /dev/sda

Nothing happened at all?

> **HarrisonNapper said:**
> I think it's just that grub for whatever reason will not work except running from /dev/sda.

Actually just remembered that I did that. I put an Android live-distro in the front SD slot (sdc), installed it to the side SD slot (sdb) and then booted through the BIOS from the SD (sdb) into a grub menu and then into Android. Although that wasn't grub2 (what Ubuntu uses now). Did you try lilo or plain grub?
I don't exactly understand what you try to do (I assume keeping Windows?), but could you just install grub to sda and then boot from there to your SSD or to your SD? As in: have two choices, 1) boot Windows from sda, 2) boot Ubuntu from sdb.

I did: installed the distro, went into the terminal (Ctrl+Alt+F1 if even X fails to start, i.e. black screen after boot), downgraded the kernel to 2.6.35-24, installed the headers (!forgot that twice!), rebooted into the new kernel (!), installed the EMGD drivers for natty, run emgd-xorg-conf (forgot that once, nearly went crazy), and reboot. (removed old kernel)
Just remember, whenever you install a new kernel, install the corresponding headers as well and if it worked, run emgd-xorg-conf.
I'm sure with a few logs we could get through :P Maybe install ssh at some point in order to get into the PC if the screen is black.

---

### Post by HarrisonNapper on 2011-08-23
> **bkruggel said:**
> Nothing happened at all?

Booting after doing all upgrades and getting installation failure of either the kernel or emgd update resulted in a kernel panic.

> 
Actually just remembered that I did that. I put an Android live-distro in the front SD slot (sdc), installed it to the side SD slot (sdb) and then booted through the BIOS from the SD (sdb) into a grub menu and then into Android. Although that wasn't grub2 (what Ubuntu uses now). Did you try lilo or plain grub?
I don't exactly understand what you try to do (I assume keeping Windows?), but could you just install grub to sda and then boot from there to your SSD or to your SD? As in: have two choices, 1) boot Windows from sda, 2) boot Ubuntu from sdb.

I did: installed the distro, went into the terminal (Ctrl+Alt+F1 if even X fails to start, i.e. black screen after boot), downgraded the kernel to 2.6.35-24, installed the headers (!forgot that twice!), rebooted into the new kernel (!), installed the EMGD drivers for natty, run emgd-xorg-conf (forgot that once, nearly went crazy), and reboot. (removed old kernel)
Just remember, whenever you install a new kernel, install the corresponding headers as well and if it worked, run emgd-xorg-conf.
I'm sure with a few logs we could get through :P Maybe install ssh at some point in order to get into the PC if the screen is black.

I have no doubt that I could have gotten things to work even with grub2, the kernel panics, the lack of independent arch for ELF magic (I deleted my EFI partition a long time ago, though side-note this does not give a grub console), but I was trying to find out what would install the easiest since I assume that something that supports the GMA500 chipset well out of the box will generally continue to do so.

As for the reason I didn't put grub on /dev/sda, I nearly had a computer bricked for having that configuration before. If you install Windows Vista SP1, install something alongside it (more accurately, if you move the MBR from the start of the HDD OR have another bootloader besides the windows loader), and do a SP upgrade, all sorts of wonky things happen. 

Luckily, I was able to save most of my Debian partition and some of my Windows data, but ever since that relatively long process, I avoid it just in case when I can. 

Also, I rather like the idea that the SSD isn't being accessed during the whole process and I'm routing to the SSD (/dev/sda) using grub. Long and short of it is this became more an effort of ideology (opposing forced install of grub to any particular location) for posterity, as I've been able to get things working on the T91 to my liking several times in the past.

In any case, 10.04 working just fine and will post the full report tomorrow for the benefit of the 3 people of the world who want to use this configuration.

---

### Post by onebir on 2011-08-24
> **HarrisonNapper said:**
>  In any case, 10.04 working just fine and will post the full report tomorrow for the benefit of the 3 **special** people of the world who want to use this configuration. ;-)

---

### Post by bkruggel on 2011-08-24
> **HarrisonNapper said:**
> In any case, 10.04 working just fine and will post the full report tomorrow for the benefit of the 3 people of the world who want to use this configuration.

That some good news at last! :P I don't know if they fixed the touchscreen by now - I remember back then, typing "test" on an onscreen keyboard would give "tttessst". Replacing xserver-xorg-input-evdev with any version above 2.5.99 fixes it. (They have 2.5.99 [at Xorg Edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa"))

> **HarrisonNapper said:**
> I assume that something that supports the GMA500 chipset well out of the box will generally continue to do so.

Wouldn't count on it. :P Better just lock the kernel version when you got it working. EMGD is made for MeeGo (thus your kernel panics with versions other than they tested), closed source (no out of the box) and generally unstable (2D works good, but 3D freezes after some time). No Intel never for me again.

> **onebir said:**
> I'm trying to get gestures working without having to press a mouse button, by getting bezel button (usually used for screen rotation but often broken) to stand in, via a script called xdotool.

Onebir, I played around with it and found the problem. Indeed it was DISPLAY. I am simulating a right click (an old topic in this thread) like this:

the event handler is /etc/acpi/events/asus-rotate
```
event=hotkey (ATKD|HOTK) 0000007b
action=/etc/acpi/mouse3.sh
```
(like yours)

and mouse3.sh is:
```

**DISPLAY=:0** xdotool click 3

```

Funny - this idea came up two years ago.. now there's a solution :P

EDIT: re-read your first post, Onebir and suddenly doubt if I understood well... Did you try in Easystroke to go into Preferences and change the Gesture Button to 1? Gestures work then in tablet mode.

---

### Post by HarrisonNapper on 2011-08-24
EDIT:Since this didn't work too well until I installed to SSD and now it works great, I'll leave it at this for now: I've got everything working in 10.04. If anyone's interested in the full walkthrough, let me know.

---

### Post by HarrisonNapper on 2011-08-24
For those not going through the tutorial above:

> **HarrisonNapper said:**
> 6g. **FREEZE THE KERNEL AND GRUB**. I assume this entails marking the packages to be held back and not upgraded. I'll quote myself here while simultaneously laughing at the fourth wall in another post so I'm not making people read this whole tutorial for feedback. Will include that info in an edit. In the meantime, I just disabled any prompts to update anything on mine.

Other todo if anyone knows the answer:
1. How to replace lxdm with xdm successfully in Lubuntu (this will be easy for me to figure out, just figured others might know)

---

### Post by HarrisonNapper on 2011-08-28
Same elf magic error as before; can't get to recovery mode. Grub console says out of memory no matter what I type. It was working fine. I booted it up, rebooted (making literally 0 changes), and got the error. If I type boot it says no kernel loaded. No memory for everything else. I think this has to do with a few things:

1. I mixed up Maverick and Lucid and went around installing the wrong EMGD drivers a few times. Frustration doesn't do nice things to my brain.

2. I don't think running an OS on an SD formatted ext4 is wise. This probably also contributed.

When I had to choose between having either Windows or Linux on the SSD, the choice was fairly obvious. The T91 doesn't have enough power to run Windows well even with the upgrade to 2GB RAM. I have Lubuntu 10.04 installed to the SSD and the speed is head and shoulders above Windows, even if I have to sacrifice some precision on the touchscreen.

EDIT: Touchscreen works fine now as does everything else :)

---

### Post by ahmadjnedy on 2011-09-25
Hi, I am still new to Linux world (UBUNTU)
I have Asus T91 notebook and I've managed to install Karmic Koala on it and everything is working perfectly (VGA, Sound, TouchScreen, ...), but then I was wondering if there is another version of ubuntu that can give me the same result of Karmic.
in other words, my question is :
- I am looking for Ubuntu 10.04.3 or Ubuntu 10.10, and I am wondering if GMA 500 will work the same as on Karmic (even though that on Karmic it is still slow when I try to play some 3D games,but Youtube is watchable in windowed size but not full screen size) and what about TouchScreen calibration, any tweaks I have to learn for installation ?

---

### Post by HarrisonNapper on 2012-06-23
> **ahmadjnedy said:**
> Hi, I am still new to Linux world (UBUNTU)
I have Asus T91 notebook and I've managed to install Karmic Koala on it and everything is working perfectly (VGA, Sound, TouchScreen, ...), but then I was wondering if there is another version of ubuntu that can give me the same result of Karmic.
in other words, my question is :
- I am looking for Ubuntu 10.04.3 or Ubuntu 10.10, and I am wondering if GMA 500 will work the same as on Karmic (even though that on Karmic it is still slow when I try to play some 3D games,but Youtube is watchable in windowed size but not full screen size) and what about TouchScreen calibration, any tweaks I have to learn for installation ?

On the off-chance you are still looking for this, the GMA500 chipset is one where different versions of Ubu can work very differently. I have had everything set up in 10.04 for awhile, but it took about two weeks to get it all set up. If everything's working for you (for the most part), I would leave it be.

On the video, can you zoom in on the page using Ctrl + or does that make it choppy, too? Note that phones are starting to have more in the way of hardware than the T91, so there's a lot of stuff that will never work quite as well as other computers.

---

### Post by HarrisonNapper on 2012-06-23
I've upgrade the RAM on mine to 2GB, so that may be helping, but I also have youtube set to run videos on 240p and I do notice when I up the quality; even if I have the cpu frequency set to the full 1.33GHz, it starts to lag/skip. Probably just the hardware not being able to keep up; not much to do there.

---

### Post by onebir on 2012-06-26
Seems like this (Russian) guy's had some luck with 12.04:
[http://snowdimon.blogspot.com/2012/03/ubuntu-1204-intel-gma-500.html](http://snowdimon.blogspot.com/2012/03/ubuntu-1204-intel-gma-500.html)

Perhaps the GMA 500 support's better in the newer kernels? This list of Poulsbo (spit) drivers available for Linux (Arch) suggests there's now at least a bit more choice:
[https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)

EDIT: "Welcome to the new support thread for the GMA500 (Poulsbo) graphics card. This card should now be working out of the box with the gma500_gfx driver and minimal user intervention:"
According to [this thread](http://ubuntuforums.org/showthread.php?t=1984236)...

EDIT #2: Display is messed up on boot into Xubuntu 12.04, but dropping into terminal and "sudo service lightdm restart" gets it working, as documented [here](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). 

Still some problems (suspend, brightness keys, haven't tested video) but wifi works fine, so I think I'll give the other steps in the wiki (& on our comrade's blog) a go.

Perhaps a usable Linux T91 is within my grasp. Or perhaps not. But worth a try before flinging it out of the window screaming "A curse on all your Poulsbos!". (Not that I'm traumatised. :p)

---

### Post by onebir on 2012-06-27
38 pages is enough - starting new thread [here](http://ubuntuforums.org/showthread.php?p=12057516#post12057516).

---

