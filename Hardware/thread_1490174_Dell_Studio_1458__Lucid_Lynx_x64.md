---
title: "Dell Studio 1458 / Lucid Lynx x64"
date: 2010-05-21
forum: Hardware
---

### Post by gianttoddler on 2010-05-21
My fellow ubuntunians!

New here but already love it. I traveled  from a land of windows, leisured on the coasts of mac and now I'm finally  here in lucidstan of lynx!

Not wanting to afford my next  installment of macbook, i've decided to go ubuntu, my machine of choice  is Intel core i7 Dell Studio 1458. It took me 3 installs (1 video yes,  bluetooth no, wifi no, sound no || 2 video yes, bluetooth kinda, wifi  maybe, sound no || 3 video yes, bluetooth yes, wifi yes, sound yes).  Being new to all kinds of sudo action I'm taking it step by step.

Literally  3rd reinstall got my radios working right, I don't know why. I have  intel advanced n 6200 and now it works great. Network applet still acts funny  sometimes , with buggy sleep/suspend/eth auto/wifi disconnect  issues, overall stable though. Sound did take a bit of time. I used 
[http://ubuntuforums.org/showpost.php?p=9223069&postcount=18](http://ubuntuforums.org/showpost.php?p=9223069&postcount=18)
to  help myself

Installed VirtualBox and Windows 7 Ultimate x64  (boots fully in 30 sec), which had weird resolution issues and no sound.  I have installed the guest additions which fixed video and made it as  good as parelells in mac for free! Sound wise afterwards I used realtek  drivers and have full sound.
[http://forums.virtualbox.org/viewtopic.php?f=4&t=14155#p132517](http://forums.virtualbox.org/viewtopic.php?f=4&t=14155#p132517)

I  am using external screen as primary with lid closed (Asus VW246H) with  hdmi to dvi adapter (ps3 is taking up hdmi) and it does beautifully.  Interesting note that resolution on laptop's screen was 1366 x 768 but dell's site said maximum was 720p  (1280 x 720). Just realized virtualbox can run full 1080p  in fullscreen mode, so with virtualbox in separate workspace this is  amazing.

Still working on camera part, didn't figure out how to  use/set it up. Working on setting up external backup (have wd passport  750), contemplating whether to use it with usb  or though network  (have airport extreme but might change it now). Fan seems to be always  on, thankfully it's gentle but can get annoying for some people or on  some days.

Hopefully owners (or potential ones) of this machine  can get some reference from this. It ain't perfect like anything, but  for the price/size/power combination this is a pretty good deal and  Ubuntu is a way to go even if you are not much of a nerd :). 

Go  ahead guys, let's make this thread as helpful as we can. Thanx  everybody!

---

### Post by obrie on 2010-05-23
gianttoddler,

Thanks for the feedback from your experience... it was really helpful.  I just received a Dell Studio 1458 and finally get everything working myself.

These are the steps I followed (after 3 fresh installs trying to get it correct):

1. Make sure you've upgraded all pre-installed packages
2. Install proprietary ATI drivers via Hardware Drivers
3. Fix random boot freeze: sudo mv /etc/init/ureadahead.conf /etc/init/ureadahead.conf.disable
4. Fix sound not working: [http://ubuntuforums.org/showpost.php?p=6589810&postcount=1](http://ubuntuforums.org/showpost.php?p=6589810&postcount=1)

I found that camera and wireless both worked out of the box.  Suspend / Hibernate seem to be working properly as well.  I didn't have anything to test Bluetooth with.

I plan on testing dual external monitors, but haven't gotten around to it yet.

The fan does seem to run more often than it should, but after going through the steps above, it does at least shut off sometimes.  It was running constantly at first.  Hopefully this improves in the next release.

Hope this helps others.

---

### Post by tylerisfat on 2010-05-27
what kind of battery life are you guys getting?


i too have no sound, trying to get that sorted out ATM


> **obrie said:**
> gianttoddler,

Thanks for the feedback from your experience... it was really helpful.  I just received a Dell Studio 1458 and finally get everything working myself.

These are the steps I followed (after 3 fresh installs trying to get it correct):

1. Make sure you've upgraded all pre-installed packages
2. Install proprietary ATI drivers via Hardware Drivers
3. Fix random boot freeze: sudo mv /etc/init/ureadahead.conf /etc/init/ureadahead.conf.disable
4. Fix sound not working: [http://ubuntuforums.org/showpost.php?p=6589810&postcount=1](http://ubuntuforums.org/showpost.php?p=6589810&postcount=1)

I found that camera and wireless both worked out of the box.  Suspend / Hibernate seem to be working properly as well.  I didn't have anything to test Bluetooth with.

I plan on testing dual external monitors, but haven't gotten around to it yet.

The fan does seem to run more often than it should, but after going through the steps above, it does at least shut off sometimes.  It was running constantly at first.  Hopefully this improves in the next release.

Hope this helps others.

---

### Post by obrie on 2010-06-01
Has anyone gotten dual external monitor to work via the VGA & HDMI outputs?  I can get it running on one or the other but not both simultaneously (even though the ATI Catalyst software seems to think that I can).  This is a Radeon HD 5450 with the 10.4 proprietary drivers installed.

---

