---
title: "Acer Aspire V5-573G and Ubuntu"
date: 2014-01-22
forum: Hardware
---

### Post by go3d on 2014-01-22
Hello to all Ubuntu users!

I recently bought a Notebook Acer Aspire V5-573G-54208G50AII and installed Ubuntu 12.04 LTS / KDE-Desktop on it. I want to share here my experiences with other users. It has been quite an adventure. First, to find the optimal device for my purposes. And then, to find solutions to several problems that arose.

**What I was looking for:**
a) a modern notebook with Intel i5 CPU - ok
b) Full HD display - ok
c) keyboard with numeric pad - ok
d) yet no more than 2kg (4.4 lb) of weight - ok
e) NVidia graphics card - ok
f) no more than 700 EUR (950 USD) - ok (got it for 650 EUR at Amazon Germany)
g) Nice to have: touchscreen - could not find this with Full HD

There were not many devices out there that could fulfill my requirements. At the end, I had no more than 2 candidates: the Acer V5-573G and a Lenovo one, the IdeaPad U530touch. The problem with the Lenovo device was, that some users reported having ordered Full HD and gotten only HD. After some phone calls with Lenovo, it turned out that the Full HD resolution is (was) not really available...

So, I decided to get the Acer one.

[B]Main characteristics of the device I got:
[/B]
- silver color (looks cool!)
- i5 4200U
- 8GB RAM
- 500GB HDD
- Full HD display (1920x1080)
- NVidia 750M
- German QWERTZ-Keyboard (Got it in Germany, but I actually prefer the US-Layout... see below)


In general, I am quite happy with the device so far. Here some main aspects that I like/dislike:

[B] Good:
[/B]- Overall nice design, good build quality
- Low weight (2.0 kg)
- Display resolution and quality
- Backlight keyboard (though not equally bright through all the keyboard... see below)
- Decently quiet
- Doesn't get too warm, feels cool most of the time
- Keyboard - I like the feeling of the quite flat keys (this is personal taste, though) plus numerical keypad

[B] Not so good:
[/B]- Touchpad with no dedicated buttons (and only left button functionality - at least under Ubuntu 12.04, see below)
- No indicators for Caps-Lock, Num-Lock and Scroll-Lock


[B]How it works with Ubuntu
[/B]
I installed Ubuntu 12.04 LTS and KDE Desktop. Almost everything worked straight away: LAN, WLAN, Bluethooth, USB, Sound, Touchpad, Display (only the Intel-Graphics though, not NVidia), and suspend.



[B][SIZE=4]Problems I had so far (and some solutions)[/SIZE]
[/B]
[B]1. Touchpad - no dedicated buttons ([COLOR=#008000]solved[/COLOR])
[/B]First, I saw this as something minor. I thought it was only a visual thing, and knowing where to click it would behave exactly the same as a regular touchpad with two buttons (left, right, and middle button via pressing both at the same time = middle button emulation). But when I first used it, I was shocked! It turned out that there is only one button - the whole pad is a single button (pressing it is easiest on the lower area, while impossible on the top). This is something you need to get used to - specially when you want to drag objects...

So no right button at all, and thus no middle button emulation. For me, this was a no-go and I was sure that I would return the device within a few days. Having to carry an extra mouse all the time just was not an option for me.

My solution:
Fortunately, after some research, I found out that the native Linux drivers are better than I thought. The right and middle buttons were there all the time, and I didn't notice this for months with my other notebook: the middle button is accessible through the upper right corner, and the right button through the lower right corner. It takes some practice though, and I still need sometimes 2 or 3 tries before I get the expected reaction. But it is an acceptable compromise.

[COLOR=#008000]New solution (2013.01.28):[/COLOR]
For both the middle and right button, an area of the touchpad can be defined.
In order to get virtual areas for both buttons (dividing the lower area in 3 equal areas) I use the following command:

```
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Soft Button Areas" 2170 0 1870 0 1080 2169 1870 0
```

More information below in my post of Jan.01 and here:  [https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Buttonless_TouchPads_.28aka_ClickPads.29](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Buttonless_TouchPads_.28aka_ClickPads.29)

[B]2. No indicators for Caps-Lock and Num-Lock (kind of solved)
[/B]Why would the manufacturer want to safe three LED indicators? Can't understand. It is really annoying.

My solution:
  CAPS-Lock: Since I don't really use the CAPS-Lock key, and since it rather annoys me to trigger it inadvertently, I completely deactivated it. That is, I redefined it with KDE as an extra Hyper-Key. This is nice beause now I have a whole new set of possible key shortcuts.
  Num-Lock: I set it which KDE such that it is always on. Furthermore, I installed "indicator-keylock", which shows me the status when I change it.   

[B]3. NVidia 750M can not be properly installed ([COLOR=#ff0000]unsolved[/COLOR])
[/B]  First thing I tried to install was the NVidia driver. After several tries I got them somehow installed. But the driver was never successfully activated. I got an error in Xorg.0.log, and running nvidia-settings would give me an error saying something like "no nvidia card detected". And worse, resuming from **suspend** did not work any more. So I removed the NVidia drivers and am still waiting for an update of Ubuntu or NVidia, that enables me to use my NVidia gfx. Anybody with a better result here?

[B]4, HDMI output not working ([COLOR=#ff0000]unsolved[/COLOR])
[/B]  Don't know if the HDMI output needs the NVidia card running. I simply cannot switch to an external monitor now with the Intel graphics. Any ideas?

[B]5. Sound makes hiss noises ([COLOR=#ff0000]unsolved[/COLOR])
[/B]  When my system comes up, the short welcome-tune I hear is not played clearly. There is some hissing sound. This is something I also had with my old notebook (also Ubuntu 12.04 LTS), so probably not Acer specific. Does anybody know a solution?

[B]6. Brightness control with FN-left/right keys not working ([COLOR=#ff0000]unsolved[/COLOR])
[/B]  I read many threads about this. The solution about editing the file /etc/default/grub did not work for me. Also, others speak about changing the brightness through the folder "/sys/class/backlight/". But my folder is empty. Any ideas?

[B]7. After suspend, the touchpad is not available until after a while (20-30 seconds) ([COLOR=#ff0000]unsolved[/COLOR])
[/B]  This puzzles me. I've never seen this before. It is not too bad, but if someone has an idea, please let me know.

[B]8. Keyboard - US Layout (still looking...)
[/B]  I searched the Internet for a replacement keyboard, but was not lucky so far. There are some cheap keyboard covers, that are simply put on top of the normal keyboard (and protect it from dirt and liquid). Does anybody have good experience with this type of keyboards covers with the Acer V5? What about the keyboard backlight?

[B]9. Battery
[/B]  Many people speak about up to 8 hours battery tine. But my battery indicator shows me about 3 hours remaining time at 100%. I wonder myself how the indicator calculates that figure. And why don't I get more time? Is my system configuration somehow wrong? I would be interested to learn what other users get, and if it matches to the estimate of the battery indicator (KDE or Unity).


Hope this helps some people out there to decide what device to buy or to improve their Ubuntu experience with their current Acer Notebook. Would also appreciate, any comments or hints on how to solve to the unsolved issues.

Thanks!

---

### Post by aeroflotsam on 2014-01-23
Hello go3d,

My operating system is Ubuntu 12.04 LTS and I can easily identfy with your concerns as I have recently purchased an Acer v5-131-2887 notebook and share some of your problems as well.  My touchpad also doesn't recognize the right button no matter what I do and it makes life difficult at times.  I share your problem with the lack of indicator LEDs for caps and number lock.  This model of Acer also ignores the "Fn" key brightness control.  It appears that Acer is not a good choice when using Ubuntu.  I am going to try booting up the machine from a USB stick using another distro and see if perhaps Mint might solve some of this stuff.  So at least you're not alone with Acer's problem and I'll be keeping an eye on your post hoping for solutions.  Here's hoping that someone will come to the rescue as I'm not a tecchie by any means.  

Good Luck!

---

### Post by aeroflotsam on 2014-01-23
Hello again go3d.......

I just booted the Acer from Linux Mint 14 on an external hard drive.  The touchpad/mouse controls all work as they should.  The problem with the pad seems to be the driver used with 12.04!  I have no idea how to copy this driver from Mint 14 to Ubuntu 12.04 or if it is even possible to do so.  I'd hate to change operating systems for something like that but perhaps someone will come up with a patch.  Something to tink about I guess.......

The Function key still cannot control brightness though....

---

### Post by mörgæs on 2014-01-24
Thanks for the advice.

> **aeroflotsam said:**
> The problem with the pad seems to be the driver used with 12.04

Yes, and the same might be true for other problems. When dealing with new hardware the best option is using the newest of software from the start, that is 13.10 for the time being.

---

### Post by go3d on 2014-01-28
[I]
Regarding **Problem 1.** (Touchpad - no dedicated buttons):[/I]

> **aeroflotsam said:**
> Hello again go3d.......

I just booted the Acer from Linux Mint 14 on an external hard drive.  The touchpad/mouse controls all work as they should.  The problem with the pad seems to be the driver used with 12.04!  I have no idea how to copy this driver from Mint 14 to Ubuntu 12.04 or if it is even possible to do so.  I'd hate to change operating systems for something like that but perhaps someone will come up with a patch.  Something to tink about I guess.......


Thanks aeroflotsam for that test with Mint-14. That is interesting... you say that you can't trigger the right mouse button under ubuntu at all with your Acer? I mean, not even with the driver trick of tapping (not pressing) the lower right corner? (It is a rather small area at the corner though, so it needs a bit of practice to get it right) This works for me with at least 3 different Linux Notebooks. (The upper right corner works the same way for the middle button).

Anyways, what you said about the correct function of the buttons under Linux Mint made me further investigate, and I luckily found a **better solution** than the virtual buttons on the corners:

It is actually possible to define an area of the synaptics touchpad for the middle and right buttons (see more under [https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Buttonless_TouchPads_.28aka_ClickPads.29](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Buttonless_TouchPads_.28aka_ClickPads.29)). That means, that when you click on one of these areas, the button actually being triggered will be the middle or right button correspondingly.

The definition of these areas can be done somehow through the configuration file /etc/X11/xorg.conf.d/50-synaptics.conf. Since I don't have this file for now, I just did it manually through xinput:

First, I found the name of the Touchpad with:
```
xinput -list
```

Mine is "ETPS/2 Elantech Touchpad" (probably the same for all Acer V5-573G devices).

Knowing the name, the button area can be set:

```
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Soft Button Areas" 1630 0 1870 0 0 0 0 0
```

The example above sets the lower right half (and about 18% of the touchpad's height) for the right mouse button. The numbers refer to the x and y resolution of the touchpad, whose values can be found in /var/log/Xorg.0.log (for me: x=3260 and y=2282).

The following line also defines a middle button (which I use a lot):

```
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Soft Button Areas" 2170 0 1870 0 1080 2169 1870 0
```

The result is 3 "virtual buttons" (left, middle and right) which can be  used almost as a touchpad with 3 physical buttons (only problem  is, that resting your fingers in that area will still interfere with the use  of the main area):

Try it! I am still figuring out how to make it permanent. Either through the config file mentioned above, or through a script in my Autostart folder.

---

### Post by go3d on 2014-01-28
> Yes, and the same might be true for other problems. When dealing with  new hardware the best option is using the newest of software from the  start, that is 13.10 for the time being.

Thanks mörgæs,

If somebody with the same device and Ubuntu 13.10 reads this, it would be nice to hear which problems do not show under 13.10.

---

### Post by aeroflotsam on 2014-01-30
Hi go3d...

Many thank yous for your post on the touchpad.....  I was totally wrong in my own evaluation of the pad and based on what you said I revisited the device.  You're right! It does have a "sweet spot corresponding to a right button after all.  It is very difficult to discover at first but I've gotten used to it.  There is just a tiny spot where the light tap works at the extreme lower right part of the pad and I'll bet that there are many users out there having the same problem with the V5 series Acers.  I'm using Ubuntu 12.04 LTS and would hate to lose that long term supported O/S.... At my age (72) I may be lucky to outlive the support period..... I'll do my best though!

Thanks again and here's hoping that a future update provides a better hardware control over the touchpad.  In the meantime I will keep an eye on your work with these problems.

Aeroflotsam

---

### Post by pankrat2 on 2014-02-12
**4. HDMI**

As you suspect, the HDMI port is probably wired to the Geforce card: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup#wiring](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup#wiring)

**8. Keyboard**

Have you found a US keyboard yet? IMHO, replacing the keyboard is better than using a cover considering the layout differences (especially around the left shift key and the return key for German keyboards).

Google brings up these offers (I have never purchased anything in either shop):

[http://www.uskeyboard.com/laptop-us-keyboard-for-acer-aspire-v5573g-v5573g9491-p-1210.html](http://www.uskeyboard.com/laptop-us-keyboard-for-acer-aspire-v5573g-v5573g9491-p-1210.html)
[http://www.us-keyboard.com/us-keyboard-for-acer-aspire-v5573-v5573g-p-2394.html](http://www.us-keyboard.com/us-keyboard-for-acer-aspire-v5573-v5573g-p-2394.html)

Apart from the German layout: Are you happy with the keyboard? I've read that some people returned this laptop because they never became comfortable typing on the Acer.

**9. Battery**

Have you disabled the unused Geforce card in the BIOS? 

Are the 3 hours with the screen on maximum screen brightness?

Windows drivers are often optimized for saving power in battery mode. Some Haswell Laptops completely deactivate the CPU turbo mode when running on battery (though I'm not sure if the OS or the hardware does that). If the OS is responsible, you might be able to get more out of your battery by trying similar tweaks:

[http://linrunner.de/en/tlp/docs/tlp-faq.html](http://linrunner.de/en/tlp/docs/tlp-faq.html)

---

### Post by go3d on 2014-03-05
Thanks pankrat2! After a longer thinking process, I decided to switch to  Debian Jessie (testing), and kernel 3.12-1-686-pae. I was planning to  wait for Ubuntu 14.04 LTS, but I finally didn't want to wait till April,  plus I learned more things about Debian that makes it a better choice  for me. I suppose though, that the results would have been comparable  with Ubuntu 13.10.


Now, several problems disappeared out of the box:
**3. NVidia 750M** **([COLOR=#008000]solved[/COLOR])**
Works now together with the Intel graphics (through  the nouveau  driver). Leads to more Battery time. I haven't tested the  proprietary  Nvidia driver though. 

**4. HDMI output not working (****[COLOR=#008000]solved[/COLOR]****)**
Because of 3. also solved.

**5. Sound makes hiss noises ([B][COLOR=#008000]solved[/COLOR]**)[/B]
Not anymore.

**6. Brightness control with FN-left/right keys not working ([B][B][COLOR=#008000]solved[/COLOR]**[/B])
[/B]Works now, although not with the on-screen-indicator. However,  through KDE I was able to assign alternative key-shortcuts, which do  show the indicator (and operate at 10% steps, whereas the FN-keys do  only 1% steps. Interesting...)

**9. Battery **** ([B][COLOR=#008000]solved[/COLOR]**)
[/B]I am not quite sure why (maybe the graphics, or the newer kernel). My indicated times at 100% are now around 6 hours... nice!


@pankrat2:
> **pankrat2 said:**
> **4. HDMI**

As you suspect, the HDMI port is probably wired to the Geforce card: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup#wiring](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup#wiring)

Solved now with Debian. It seems to be the case, that the HDMI port is  wired to the Intel chip, since I can expand my screen over the Notebook  monitor and my LCD-TV (hdmi).


> 
**8. Keyboard**

Have you found a US keyboard yet? IMHO, replacing the keyboard is better  than using a cover considering the layout differences (especially  around the left shift key and the return key for German keyboards).

Google brings up these offers (I have never purchased anything in either shop):

[http://www.uskeyboard.com/laptop-us-keyboard-for-acer-aspire-v5573g-v5573g9491-p-1210.html](http://www.uskeyboard.com/laptop-us-keyboard-for-acer-aspire-v5573g-v5573g9491-p-1210.html)
[http://www.us-keyboard.com/us-keyboard-for-acer-aspire-v5573-v5573g-p-2394.html](http://www.us-keyboard.com/us-keyboard-for-acer-aspire-v5573-v5573g-p-2394.html)

Apart from the German layout: Are you happy with the keyboard? I've read  that some people returned this laptop because they never became  comfortable typing on the Acer.

Thanks for this. I already ordered the keyboard via the first link (both  links seem to belong to one company anyhow). After they made me  disassemble my device to send them a picture of the back of the keyboard  (because there are 2 models for my device), now I am waiting for news  from them, because the correct keyboard was not on stock...
**Update:** I got a refund, because the vendor could not get the correct keyboard. Can you imagine this?

Yes, I am quite happy with the keyboard actually, and I got used to it  in no time. But the keys are very flat, and some people indeed don't  like them. What bothers me more are the missing lock-indicators (caps,  num, scroll).

> 
**9. Battery**

Have you disabled the unused Geforce card in the BIOS? 

Are the 3 hours with the screen on maximum screen brightness?

Windows drivers are often optimized for saving power in battery mode.  Some Haswell Laptops completely deactivate the CPU turbo mode when  running on battery (though I'm not sure if the OS or the hardware does  that). If the OS is responsible, you might be able to get more out of  your battery by trying similar tweaks:

[http://linrunner.de/en/tlp/docs/tlp-faq.html](http://linrunner.de/en/tlp/docs/tlp-faq.html)


Now I get much more (as mentioned above). I can't tell at what  brightness the screen was before, since I could not change it at all.  I'm planning to install the proprietary Nvidia driver over the nouveau  one some day, and I wonder if my battery time is going to change. I'll  update on this.

---

### Post by joaomfsantos on 2014-03-29
Hi go3d,
To get the backlight working with fn keys AND the on screen display indicator just do this:
sudo nano /etc/default/grub
change line: 
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

Then do:
sudo update-grub

There's another solution with grub but doesn't show the OSD.

---

### Post by go3d on 2014-04-01
> **joaomfsantos said:**
> Hi go3d,
To get the backlight working with fn keys AND the on screen display indicator just do this:
sudo nano /etc/default/grub
change line: 
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

Then do:
sudo update-grub

There's another solution with grub but doesn't show the OSD.

I tried that, but it didn't change anything. I guess my notebook is too new or exotic for Ubuntu 12.04. Thanks anyway.

---

### Post by pankrat2 on 2014-04-07
Small update regarding Ubuntu compatibility: My wife now got the same laptop. Ubuntu 12.04.4 worked almost completely out of the box (kernel 3.12) only power off after shutdown did not work which is extremely annoying. 

This is fixed in kernel 3.13 which is shipped with Ubuntu 14.04. The nvidia driver can be activated with a few mouseclicks. I haven't used the laptop long enough to be able to tell whether the video driver has an effect on battery times.

IMHO the clickpad is the worst I have ever used. I can't seem to hit the intended location with left-click - right-click is even harder. Drag and drop is near impossible. Even moving the cursor sometimes has problems (some people suggested it's because of the texture). Maybe it can be improved by playing with the configuration but I haven't found settings that worked well enough for me. 

@go3d: I'm sorry to hear replacing the keyboard doesn't seem to be possible (weird story).

---

### Post by go3d on 2014-04-16
Hi pankrat2,

Yes, I think the problems should be solved with Ubuntu 14.04, just as with the latest Debian (I now also have kernel 3.13).

My clickpad is not that bad really. I got used now and can work quite well with it. You mean you can not hit the intended location for left- and right click, or rather middle- and right? Left click should not be a problem, since everywhere is left-click (when you hear the click) with default configuration. I reconfigured mine to have virtual areas for the middle and right buttons, and it works good for, say, 80 percent of the time. Also, I redefined the tapping so that a tap with 2 fingers gives me a right-click, and a tap with 3 fingers a middle click. This also works most of the time, once you got the hang of it. Here are my synclient parameters:


>  > synclient
Parameter settings:
    LeftEdge                = 130
    RightEdge               = 3130
    TopEdge                 = 123
    BottomEdge              = 2159
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 175
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 79
    HorizScrollDelta        = 79
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0502639
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 2
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 19
    VertHysteresis          = 19
    ClickPad                = 1
    RightButtonAreaLeft     = 2170
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1870
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 1080
    MiddleButtonAreaRight   = 2169
    MiddleButtonAreaTop     = 1870
    MiddleButtonAreaBottom  = 0



What is sometimes annoying is when I am writting a lot, the pad suddenly gives a mouse click signal (when my hand palm moves too close to it), thus moving my cursor and making me write on the wrong spot. It is so sensitive, that this can happen even with no physical touch, but just some hovering of the hand over the pad surface. So I defined a keyboard shortcut to quickly disable and enable the tapping for left-click. This can be done with the command "synclient TapButton1=x", with x either 0 or 1 to disable or enable respectively.

Hope that helps.

Regarding the replacement of the keyboard, I am now in contact with Acer. It seems to be that they only offer the keyboard together with the front cover (which includes the touch pad) for a price of around 130 USD. That's a lot, so I am thinking about it. Another problem is that replacing the keyboard seems to be quite difficult. Everything has to be unscrewed and removed from the back before you have access to the keyboard. Not sure yet if I would go for the extra risk.

Regards!

---

### Post by go3d on 2014-09-10
News on my keyboard:

I finally got my German keyboard replaced by a new one, UK-layout. I sent my notebook to Acer Germany. It cost 100 Euros. Note that the whole keyboard cover including the touch-pad must be replaced.

Unfortunately, several things went wrong:

- They said it would take 1 week total, but I got my notebook back 4 weeks later!!!

- The deal was to get my original keyboard back (otherwise it would cost about 15 Euros less), but they didn't send it back!!

- When I got the notebook back, the lower cover was damaged (2 small cracks at the edges).

After many e-mails and phone calls, I finally got a new German keyboard (the original was lost) and a replacement for the lower cover.

I would have done the keyboard replacement on my own, but it turns out that it is quite difficult to do with the Aspire V5-573G.

Side note:
The touch-pad controller of the UK-keyboard I got seems to be different from the original German keyboard. It used to be "ETPS/2 Elantech", now it is "SynPS/2 Synaptics". So I had to do the settings for middle and left button again, since it needs different values. But worst of all, the new touch-pad does not work as precisely as the Elantech one. Sometimes the mouse pointer jumps to the lower left corner. And holding the finger on the lower edge steady leads sometimes to an erratic moving mouse cursor (about +/-5 pixels vertically).

---

### Post by littlegrn on 2015-02-10
Hello, guys!

I recently purchased the same unit and have only ran Ubuntu 14.10 on it. Truth be told I am quite impressed with it so far. Here are my personal thoughts and impressions so far:

1. I got the unit with i7-4500U CPU, US keyboard layout (bought it from Bulgaria though), 8GBs of RAM and NVidia 750M. It runs nice, most of the time quiet and cool. One of the fans seems to be noisier than the other - a little irritating but I can live with it.

2. My keyboard seems evenly lit across the whole thing - the only button that seems shadier is the "5" on the numpad. 
3. Everything worked out of the box for me - suspend, shutdown, etc. ... 
4. Proprietary NVidia drivers installed prior to any testing, but -> HDMI works.
5. Wifi, bluetooth, ethernet - everything just works. 
6. I have no trouble with my touchpad whatsoever. Buttons work quite as they should, so does pointer navigation. I hate touchpads though, so I don't use it. It's ETPS/2 Elantech.

All in all I am pleased with the computer. The only thing I didn't like is that it shipped with a Hard Drive, so I took that one out and installed an SSD - even before I turned it on... but I am experiencing a rather irritating issue - every time I power the unit off and start it again I get an error message, stating that I don't have a boot device installed. I hit Ctrl+Alt+Del, the computer restarts and boots properly. Reboot doesn't produce the issue, only when I completely shut it down (or hibernate). I tried updating and rolling back BIOS versions to no avail - if someone has an idea of how to resolve this I'll be really grateful if they shared.

---

