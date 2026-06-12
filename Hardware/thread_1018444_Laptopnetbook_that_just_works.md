---
title: "Laptop/netbook that just works?"
date: 2008-12-22
forum: Hardware
---

### Post by petermoffat on 2008-12-22
I'm looking to buy myself a netbook, or maybe a laptop for Christmas. Been using Ubuntu since 5.04, though only on and off, a lot more recently as driver support has been getting better. 

Having read about netbooks and Ubuntu, I'm a little bit worried that some key things might not work, ie. webcam, sound, mic, wireless, all of which are pretty important as I'll mainly be using it for web, email and skype. Dell mini9 looks nice, but has a crappy webcam and 8GB hd..

Specs I'm looking for are:

Atom
160Gb hd
2Bb+ RAM
1.3MP+ webcam
Good battery life, 6 cell if possible
9 or 10" screen
Wireless LAN, 3G not required.

I've looked at Asus EEE 904HD, Lenovo Ideapad, Advent 4211 (rebranded MSI Wind) and Acer Aspire One

Any comments on which of these would work best, or with the least fidling? 

I've seen some people having to recompile drivers every time they do a kernel update, and I just don't want those sorts of issues to deal with. 

Can anyone that uses a netbook comment on erformance under 8.10 and what works/doesn't work and how you fixed it?

Also, should I just get a 'proper' laptop? I like the idea of small form factor, but could be swayed to a 13 or 15" laptop.

---

### Post by jespdj on 2008-12-22
Dell sells the Inspiron Mini 9 with Ubuntu installed.

---

### Post by petermoffat on 2008-12-22
The Dell is only available with 8GB hd though, and webcam is 0.3MP

---

### Post by bradthewanderer on 2008-12-22
Asus 1000H or 1000HA.

---

### Post by iggykoopa on 2008-12-22
The dell mini has a 32gb hardrive and 1.3 mp webcam as options, they just aren't included by default.

---

### Post by RookieUbuntuUser58 on 2008-12-22
I have a MSI Wind (see sig). Ubuntu works perfectly on it besides bluetooth (havent figured out how to get my phone connected, works in XP) and also Ubuntu drains the battery faster. I have the 6 cell version and in XP I was getting 4hrs and 30min+ but with Ubuntu the max Im getting is 3hrs and 30mins.

---

### Post by petermoffat on 2008-12-23
Right, so I've just bought a Samsung NC10!

it ticket most of the right boxes, the only one it missed was RAM, comes with 1Gb, so I'll get an extra 1Gb as soon as I find out what it uses and where to get them.. 

Anyone got one of these? I've found some ubuntu doocumentation on it and it seems as if most things work straight off, with a few needing updates and some keyboard related isuues that can either be fixed with kernel patches or not. 

Would be nice to hear from someone that uses it regularly and get their opinion?

---

### Post by Kernel Sanders on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=993458&highlight=NC10](http://ubuntuforums.org/showthread.php?t=993458&highlight=NC10)

---

### Post by themorningflight on 2008-12-24
> **petermoffat said:**
> Right, so I've just bought a Samsung NC10!

it ticket most of the right boxes, the only one it missed was RAM, comes with 1Gb, so I'll get an extra 1Gb as soon as I find out what it uses and where to get them.. 

Anyone got one of these? I've found some ubuntu doocumentation on it and it seems as if most things work straight off, with a few needing updates and some keyboard related isuues that can either be fixed with kernel patches or not. 

Would be nice to hear from someone that uses it regularly and get their opinion?
I have an NC10 and it is great. I left a bit of space to XP (for my garmin etrex and a scanner that is awkward) but gave most of the HDD to Intrepid.

I did the stuff with the wireless and to get the volume and brightness to work from the arrow keys. Sleep and hibernate worked out of the box. Touchpad works great, even horizontal scrolling, thought I did add 'touchfreeze' as I sometimes touched it while typing and found I inserted text where it was not wanted.

I had read about people trying to extend battery life on Acers by installing Linux without swap so I did that. I also chose ext2 so it would not be journaling. I reasoned the the no swap or journaling would stop the HDD getting thrashed (it was not battery I was trying to save, though probably does). 

I tried the netbook remix but the screen is so good I do not think it helps so have disabled it. A better option I think is to have the Avant Window Navigator. I don't use it on my other Ubuntu machines but it is perfect for the screen size of the NC10.

Only niggle I have not yet sorted is that some windows that open to do settings are too big for the screen and the 'cancel' or 'okay' buttons are below the screen.

It all seems to work very well. I am so glad I opted for the NC10 as I came close to getting a different netbook. Screen is great, hard disk size is great and the battery life... what can I say!?

---

### Post by jaseanton on 2008-12-24
> Only niggle I have not yet sorted is that some windows that open to do settings are too big for the screen and the 'cancel' or 'okay' buttons are below the screen.

1) Set all fonts to 7

System > Preferences > Appearance > Fonts

(You can also try Subpixel smoothing)

2) Remove Menu Bar from the panel and Replace it with Main Menu
[LIST]
[*]Right-click on the top panel bar
[*]Choose Add to Panel
[*]Select Main Menu and drag it to the panel
[*]Right click on Menu Bar and remove it
[/LIST]

3) Reduce the size of the Top Panel
[LIST]
[*]Right click on panel
[*]Properties
[*]General tab
[*]Size: 18
[/LIST]

4) Unlock features you want on the bottom panel and drag them to the top panel, arranging things as you'd like them (play around with things).

5) Delete the bottom panel.

6) When space is especially needed, temporarily set the top panel to Autohide (you should know how to get to the panel properties by now.

HTH

---

### Post by Jon Bradbury on 2008-12-24
> **themorningflight said:**
> I have an NC10 and it is great. I left a bit of space to XP (for my garmin etrex and a scanner that is awkward) but gave most of the HDD to Intrepid.

I did the stuff with the wireless and to get the volume and brightness to work from the arrow keys. Sleep and hibernate worked out of the box. Touchpad works great, even horizontal scrolling, thought I did add 'touchfreeze' as I sometimes touched it while typing and found I inserted text where it was not wanted.

I had read about people trying to extend battery life on Acers by installing Linux without swap so I did that. I also chose ext2 so it would not be journaling. I reasoned the the no swap or journaling would stop the HDD getting thrashed (it was not battery I was trying to save, though probably does). 

I tried the netbook remix but the screen is so good I do not think it helps so have disabled it. A better option I think is to have the Avant Window Navigator. I don't use it on my other Ubuntu machines but it is perfect for the screen size of the NC10.

Only niggle I have not yet sorted is that some windows that open to do settings are too big for the screen and the 'cancel' or 'okay' buttons are below the screen.

It all seems to work very well. I am so glad I opted for the NC10 as I came close to getting a different netbook. Screen is great, hard disk size is great and the battery life... what can I say!?

Well, you could tell us how you fixed the hotkeys... :D

I presume you're using the CTRL-key workarounds.

---

### Post by vegetarianshrimp on 2008-12-24
> **petermoffat said:**
> Dell mini9 looks nice, but has a crappy webcam and 8GB hd

I have the mini 9, and you can now actually get 32GB Solid State Drive (SSD). If that is not enough space, you can get a portable hard drive or insert a 16GB SD card. You can upgrade to a 1.3MP webcam, which you said in the specs you wanted was ok, for $25. 

Also, if that is still not good enough, you can get the mini 12, which is more expensive and closer to laptop than netbook. I heard it will be available with Ubuntu early 2009, so maybe a late Xmas present for yourself?

Hope that helps!

---

### Post by themorningflight on 2008-12-26
Good advice. However I already have the panel/taskbar to auto-hide and I still have not been able to see to the bottom of some of the preferences windows. I will try changing the font sizes to see if that does it.

---

### Post by themorningflight on 2008-12-26
> **Jon Bradbury said:**
> Well, you could tell us how you fixed the hotkeys... :D

I presume you're using the CTRL-key workarounds.
For the hotkeys I just did what I was told at [https://help.ubuntu.com/community/NC10#Hotkeys](https://help.ubuntu.com/community/NC10#Hotkeys). 

It only fixed a few of the keys. Those working are sleep, brightness, volume, home & end. I have not got around to trying the rest of the keys.

---

### Post by the3dman on 2008-12-26
The Sylvania g meso is a great netbook with ubuntu pre-installed.

---

### Post by jaseanton on 2008-12-28
> **themorningflight said:**
> Good advice. However I already have the panel/taskbar to auto-hide and I still have not been able to see to the bottom of some of the preferences windows. I will try changing the font sizes to see if that does it.

Thanks.  With the preferences problem, it's usually just a case of experimenting with Tab & Enter, unfortunately.

---

### Post by impact on 2008-12-31
> **jaseanton said:**
> Thanks.  With the preferences problem, it's usually just a case of experimenting with Tab & Enter, unfortunately.

Assuming you use Compiz, you can install the compizconfig-settings-manager (it's a package in Synaptic, search for compizconfig), then launch it and go to the Move Window plugin settings and uncheck the "Constrain Y". 

Then, when you encounter a window that is too tall, you can hold down the ALT key, click the window and drag it up. The edge of the screen will no longer stop you from dragging the top of the window offscreen thus revealing the bottom of the window.

---

### Post by tandemcrash on 2009-01-04
get the eeepc1000 40Gb SSD linux from newegg for 399. or windows 160Gb for slightly more

---

### Post by laptop-power-battery on 2009-01-04
I want to know the anwer.


[ADVENT 7016 Laptop battery]("http://www.laptop-power-battery.com/laptop-power-supply/advent-7016-laptop-batteries.html"):confused:

---

