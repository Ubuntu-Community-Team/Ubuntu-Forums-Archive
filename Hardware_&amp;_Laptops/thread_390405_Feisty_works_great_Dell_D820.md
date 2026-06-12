---
title: "Feisty works great Dell D820"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by mattyj on 2007-03-21
Hello,

Given there is not that much out there on which laptops work well with linux I thought I would post my experience.  I am a relative newbie, and have only used Ubuntu on desktops to date.

I got a Dell D820 refurbished with:

2.33 ghz Core2duo
WUXGA
160GB HD
Intel 3945 wireless
4GB RAM (chipset only supports 3.2gb unfortunately)
nvidia nvs 120 512mb (really 256 dedicated)

For 2K on Dell Refurbished!

I got the latest feisty fawn daily build (March 21) AMD 64  build off ubuntu and dual booted it with windows by repartitioning the drive.  Basically everything works that matters to me:

Screen resolution/video:  Works out of the box at 1920x1200, if you enable the nvidia restricted driver nvidia-glx you need to make sure your resolution is in the xorg.conf file, and reset the x server, but that is it.  glx gears gives ~ 2800 fps, not great, but if you wnat more get a precision with a better graphics card I guess...

Wireless works out of the box with Network Manager (get the Intel 3945 so you don't have to mess with the broadcom issues).

Suspend works out of the box and wakes up no problem when using the standard video driver and when the nvidia driver is enabled.  However, when you enable compiz it no longer does.  So I don't use compiz.  It would be nice to have this though.

Heat seems to be OK, the fans come on during compiling etc, then go off during nl work.

Touchpad works out of the box, and settings seem OK, not slow, not weird like with Edgy.

Both cores recognized and SMP works well during compiling or heavy load.  Processors scale down when not being used.

I haven't tried the card reader or firewire 1394 port etc, but USB seems to work fine.  I will make a more formal post when I have worked for a while, but basically wanted to let people know that Feisty fixes most of the issues I had with using Ubuntu on Dell laptops.

Basically this removes any need for me to dual boot as long as I run parallels or VM ware.  Not sure on battery life yet, but will let you know.

Great work Ubuntu team.  The folks in my lab are stoked!  The folks running OSX for the simplicity are jealous of my 64 bit badness!

Only remaining issue is a simple solution for connecting to projectors.

---

### Post by bimmerd00d on 2007-05-08
Any chance you could post some more info on how you got Parallels to work in Ubuntu?  I've got a D820 here, and the only thing that doesn't work (yet) is the fingerprint reader!  I love this laptop, couldn't ask for more.

---

### Post by Jester_ag on 2007-05-25
I have a D820 with 2GB Ram and the 512 video, Intel 3945 wireless. My only problem is getting the wireless to work with a WEP 128bit. I can connect to unsecure just fine but not the WEP. On my wife's Dell 1505 I created the Bcom and used NDISwrapper & WIFI Radar to get the wep working. Is there anyway to get Wifi Radar or another app to allow me the 26 characters for my 128bit WEP? I have even re-installed 3 times (trying different scenarios and none have worked yet). 

Please help.

---

