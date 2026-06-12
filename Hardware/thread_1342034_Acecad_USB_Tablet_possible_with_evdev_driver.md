---
title: "Acecad USB Tablet possible with evdev driver?"
date: 2009-11-30
forum: Hardware
---

### Post by RavanH on 2009-11-30
Hi,

My old tablet with stylus is recognized by X as an Acecad USB Tablet when I plug it in. However, out of the box Ubuntu seems to load the evdev driver for it. This results in no clicks or button events are accepted (let alone pressure). Just mouse pointer movement.

I have tried to get the tablet working by installing xserver-xorg-input-acecad. With that, the stylus works but it has flaky mouse pointer control. Unlike the evdev driver, which gives me very accurate control over the pointer. I have tried to get the acecad driver to behave but somehow it does not respond to any parameter I try to set in either xorg.conf or /etc/hal/fdi/policy/10-acecad.fdi

Subsequently, since I like the mouse pointer control the evdev driver gives me, I tried to get the evdev driver to recognize the stylus tipand buttons by testing with some parameters from [http://www.x.org/releases/X11R7.5/doc/man/man4/evdev.4.html](http://www.x.org/releases/X11R7.5/doc/man/man4/evdev.4.html) without much result (except being able to switch axes and such)...

Can anyone tell me if there are parameters (or better documentation) for the evdev driver that can be used to get a simple tablet/stylus working like it should?

Thanks for any ideas.

---

### Post by RavanH on 2009-12-03
Nobody? (bump)

---

### Post by Magnes on 2009-12-15
Run:

gksudo gedit /etc/hal/fdi/policy/10-acecad.fdi

Paste:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
 <device>
 <match key="input.originating_device" contains="if0">
 <match key="info.product" contains="ACECAD">
 <merge key="input.x11_driver" type="string">acecad</merge>
 <merge key="input.x11_options.Type" type="string">stylus</merge>
 <merge key="info.product" type="string">stylus</merge>
 </match>
 </match>
 </device>
</deviceinfo>

Restart.
If it doesn't work (or X won't start) login and run:

sudo rm /etc/hal/fdi/policy/10-acecad.fdi

---

### Post by RavanH on 2009-12-16
> **Magnes said:**
> Run:

gksudo gedit /etc/hal/fdi/policy/10-acecad.fdi

Paste:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
 <device>
 <match key="input.originating_device" contains="if0">
 <match key="info.product" contains="ACECAD">
 <merge key="input.x11_driver" type="string">acecad</merge>
 <merge key="input.x11_options.Type" type="string">stylus</merge>
 <merge key="info.product" type="string">stylus</merge>
 </match>
 </match>
 </device>
</deviceinfo>

Restart.
If it doesn't work (or X won't start) login and run:

sudo rm /etc/hal/fdi/policy/10-acecad.fdi

Thanks for responding! :)

I tried ACECAD as you suggested and indeed the stylus is now using the **evdev** driver. Just as it would if I there was no /etc/hal/fdi/policy/10-acecad.fdi at all... But I am sure that is not what you meant to happen. If I use "Acecad" instead of "ACECAD" for info.product, then the pen will be using the **acecad** driver. However, there is a problem with that driver: It behaves weird because I use two screens. And for the life of me, I cannot get it to listen to any parameters to make it work for two screens :( In fact it will not take any parameter!

So that is why I am hoping for someone who can explain how to get the evdev driver to work well with this tablet and accept button/tip/pressure input instead of only movement.

---

### Post by calisun on 2010-03-03
RavanH,
Actually Magnes is correct, it needs to be ACECAD not Acecad.
At first I followed your instructions and changed it to Acecad, but I could not get it to work.
But than I went back and changed it back to what Magnes had: ACECAD, and now everything works fine.

Thank you Magnes (Dziekuje)

---

### Post by calisun on 2010-03-03
OK, 
I have found in another post that both could be correct: ACECAD and Acecad, it all depends on what driver your computer uses:

[http://swiss.ubuntuforums.org/showpost.php?p=8510566&postcount=26](http://swiss.ubuntuforums.org/showpost.php?p=8510566&postcount=26)

SO I would suggest everyone try: ACECAD, if after reboot your pad does not work, than change it to: Acecad

If both don't work, than you are out of luck :) :)

---

### Post by RavanH on 2010-03-04
Thanks calisun, for sharing. Sadly, I seem to be one of those "out of luck" ... So the acecad driver is working well with your tablet? 

For me it's useless. Or I 'd need to give up using two monitors which is not at option. But before having to buy a Wacom tablet, I was hoping to find a fix so hence the question of this thread: can the **evdev** driver be configured to listen to stylus button input (like the acecad driver does) so that all that Acecad derivative tablet hardware out there ( including mine ;) ) would be at at least minimally supported out of the box.

Anyone?

---

### Post by calisun on 2010-03-05
Try downloading the latest acecad driver for ubuntu and see if that helps:

[http://packages.ubuntu.com/lt/karmic/x11/xserver-xorg-input-acecad](http://packages.ubuntu.com/lt/karmic/x11/xserver-xorg-input-acecad)

(Scroll down to the section that says: Download xserver-xorg-input-acecad)

Make sure to restart your computer to see if the new driver works.


As far as using two monitors, that might be an issue. I have the "task bar" on the bottom of the screen to auto hide, it only pups up when you mouse over it. But when I use acecad, the pen does not go all they way to the bottom to make the task bar pup up. So I have to use the mouse to make the task bar open. So in your case, you might also need to use acecad/ mouse combination to make the pointer  move over to the next screen.  
I hope that helps.








.

---

### Post by RavanH on 2010-03-05
> **calisun said:**
> Try downloading the latest acecad driver for ubuntu and see if that helps:

[http://packages.ubuntu.com/lt/karmic/x11/xserver-xorg-input-acecad](http://packages.ubuntu.com/lt/karmic/x11/xserver-xorg-input-acecad)

(Scroll down to the section that says: Download xserver-xorg-input-acecad)

Make sure to restart your computer to see if the new driver works.

I am already using xserver-xorg-input-acecad_1.3.0-2 ...

> **calisun said:**
> 
As far as using two monitors, that might be an issue. I have the "task bar" on the bottom of the screen to auto hide, it only pups up when you mouse over it. But when I use acecad, the pen does not go all they way to the bottom to make the task bar pup up. So I have to use the mouse to make the task bar open. So in your case, you might also need to use acecad/ mouse combination to make the pointer  move over to the next screen.  
I hope that helps.
Thanks for the tip. Only my mouse pointer can move over every monitor but the problem is that the active area on the pad (where the stylus is detected and controls mouse movement and button clicks) is about one quarter of its full pad area. This gives me a **very small** stylus area to handle the mouse. And considering on the other hand the mouse pointer which needs to be moved over a **much larger** area than normal, this results in nearly impossible mouse control. Clicking anywhere is extremely difficult with the pointer flying all over the place on the slightest movement of the stylus. Let alone use it for drawing!

I've tried every config option to get the acecad driver to behave more like normal, but it seems to refuse just about anything... And since the evdev driver seems unsuitable (although mouse control is just perfect: easy and smooth) I think I am "out of luck" with this pad :(

---

### Post by calisun on 2010-04-08
RavanH, I can feel your frustration.
I have just tried to make my tablet work on another computer, and no luck. Both computers use Ubuntu 9.10, both computers using latest Acecad driver, on both computers I have the same code as given here by Magnes, both computers trying to use the same Acecad tablet. Yet, one computer works and another does not.

I guess these are some of the things we have to put up with when using Linux. I guess one needs to be a super goober linux programmer in order to make linux run problem free like OsX does right out of the box.




.

---

### Post by RavanH on 2010-04-18
yeah, it's weird to say the least... i read somewhere someone made it work with the wacom driver but no mention of exactly how. so no light on that angle :(

well, too bad about the tablet i guess. i am not returning to the M$ misery for it so i am looking out for a bamboo occasion or somthing like that. maybe i can even trade the acecad back in for some small change ;)

---

### Post by WasteOfSpace on 2010-05-07
Hi
I installed the driver and it makes all the buttons work properly; the only problem that I am now having is that the pointer will not move far enough to the edges of the screen to allow me to click on the corners.

Does anyone have a remedy for this?

Thanks

---

### Post by RavanH on 2010-05-07
> **WasteOfSpace said:**
> Hi
I installed the driver and it makes all the buttons work properly; the only problem that I am now having is that the pointer will not move far enough to the edges of the screen to allow me to click on the corners.

Does anyone have a remedy for this?

Thanks
Hi, can you please specify which driver and which tablet you are using together here?

---

### Post by WasteOfSpace on 2010-05-08
I am using a very old AceCad Flair, Model number 8" * 4" USB Graphics tablet.
The drivers are the ones available for Ubuntu through the Synaptics installer. (KPackageKit)


Package Name:
xserver-xorg-input-acecad
License: free
Group: Other desktops
Details: This package provides the driver for AceCad Flair input devices.

More information about X.Org can be found at: 

This package is built from the X.org xf86-input-acecad driver module.
Size:
20.9 KiB

---

