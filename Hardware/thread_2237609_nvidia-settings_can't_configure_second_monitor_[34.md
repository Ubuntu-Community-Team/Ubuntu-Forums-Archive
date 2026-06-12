---
title: "nvidia-settings can't configure second monitor [340.24 / 850m GTX]"
date: 2014-08-02
forum: Hardware
---

### Post by --epic on 2014-08-02
Hi,

After having no luck solving the problem described below I decided to try Ubuntu, with a fresh install of 14.04 the steps I followed are;
```

[B]apt-get update 
apt-get upgrade 
apt-add-repository [B]ppa:xorg-edgers/ppa
[/B]apt-get update && apt-get install nvidia-340 nvidia-prime nvidia-settings
[/B]
```
I am experiencing the same issue described below in ubuntu/unity, namely I am unable to configure monitors in nvidia-settings and touchpad freezing.
So my choices are either not use nvidia drivers or not use my second display, neither work for me.

I would appreciate any advice, otherwise I'll probably have to resort back to windows.

-----------------------------------------------------------------------------

I'm trying to get my new laptop up and running with the nvidia drivers, nouvea works fine but I'd like to do some gaming and purge my windows partition entirely.


My laptop has a 850m GTX and I am running Mint 17 with Cinnamon 2.2.13, the steps i followed are:
Install packages  from the xorg-edgers ppa: **nvidia-340 nvidia-prime nvidia-settings** and reboot.

After rebooting my laptop & external monitor connected via HDMI are mirrored, however everything else appears to be working fine & games are running okay.


So I can only see one display in nvidia-settings, if I untick mirrored displays in the cinnamon settings cinnamon will crash to fallback mode.
I was able to restore cinnamon by deleting my **~/.config/monitors.xml** file.


I have also noticed that using the touch pad results in random display freezes, the system runs on fine in the background but the display is locked until I switch tty, which appears to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1220426](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1220426)


**screenshot **- [http://i.imgur.com/D2XHhkw.png](http://i.imgur.com/D2XHhkw.png)


**$ lspci | egrep 'VGA|3D'**


    00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 850M] (rev a2)


**~/.config/monitors.xml** - [http://pastebin.com/raw.php?i=ZPZ8c9ud](http://pastebin.com/raw.php?i=ZPZ8c9ud)


**/etc/X11/xorg.conf** - [http://pastebin.com/raw.php?i=BHzcsNHK](http://pastebin.com/raw.php?i=BHzcsNHK)


**/var/log/Xorg.0.log** - [http://pastebin.com/raw.php?i=78UKCM25](http://pastebin.com/raw.php?i=78UKCM25)


**nvidia-bug-report.log** - [https://drive.google.com/file/d/0B0y6-Hhc3-u8VlV4R25wcTBseUU/edit?usp=sharing](https://drive.google.com/file/d/0B0y6-Hhc3-u8VlV4R25wcTBseUU/edit?usp=sharing)


I'm still trying to get my head around linux and this has been my biggest hurdle so far, haven't had much luck with Google but these optimus setups seem fiddly... 

-----------------------------------------------------------------------------

---

