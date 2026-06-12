---
title: "::810x86-32b::Vaio VGN-SR19XN issues. Global All"
date: 2008-11-12
forum: Hardware
---

### Post by xerman on 2008-11-12
Hello there,

I just installed new Ubuntu 810x86 32 bit on my laptop, Sony Vaio VGN-SR19XN. As everything inside the machine seemed to be linux savy, i decided to buy this one. (Still did not get rid of Windows, though).

I started this to notice all the issues i face with this machine, and to find out how to solve them and then help anyone who decides to buy the same machine.

Issues noted:
xorg detect key pressed app
2008.11.13:
[LIST=1]
[*]Most annoying is screen resolution. Is set to 800x600 and not available to change to higher one. Screen top is 1280x800.
At this resolution of 800x600 fonts are really clear to read even at distance, but as i noticed a long ago, linux windows are made for more than 1024x768 screens, so i find myself pressing ALT and dragging windows all the time.

I cannot find any place where to assign more memory to video if that could be the issue. Machine has 3GB ram and seems 256MB are assigned to video, but no way to check that. Card is an integrated intel X4500MHD.

[*]SCIM took some time to configure itself after installing all correspondant languages (spanish, russian, chinese). Then selecting the ones in SCIM table took some time and needed a restart.

[*]Some keys are not usable. Volume ones with "Fn+F234" work fine. Can put volume up and down. But can not change brightness with "Fn+F56".
The "Supr" key works fine though, so does the "Print Screen".Also the "Bloq Num".Zoom ones do not, the one to choose Vga out have not been tested yet.

The keys on top of laptop for Mode and Settings with 5 keys in between are usless by now. In Vista they are use to trigger 5 different groups of apps. This is driven by a specific SonyVaio app. Still have to check the X11 key press to see if get any response.

[*]No way to trigger compiz. Certainly, due to the issue related to screen resolution.

[*]Webcam works ok with Cheese.Seems to be recognized well with amsn. We will se about videoconferencing.

[*]Seems that repositories still do not have all the 804's stuff. At least font related.

[*]Overall speed is quite messy. A bit slow for what it should be, and a lot more slow than Vista Bussiness on the same machine.

[*]Wireless seems to work ok, once you get used to the new network configuration system.

[*]SD reader works fine too. About MStick i can not tell as i do not use.

[*]Noise. Though this is a quiet laptop, with ubuntu fan seems to be always on, always on, always on... Making "noise", at least some. A lot more than with Vista, that for sure. Modified the Energy Savings but nothing changed.

[*]Trackpad is good. Does horizontal and vertical scroll with no issues.

[*]Do not know what to do with the Fingerprint reader yet.

[*]Audio is quite low volume always even at top volume level. This is a issue with all ubuntu, as 804 and 704 machines i have also show same issue.

[/LIST]

2008.11.14:
[LIST=1]
[*]Checking [COLOR="DarkRed"]xorg.conf[/COLOR] shows driver selected is VESA, so change in there to INTEL as installed is xserver intel 2.4.1, and this produces black screen. No nothing.
Ubuntu sports driver 2.4.1 and intel already has 2.5.0 available for download. Also needed dependencies not available in the repositories. So we should wait to 2.5.0. availability, or try to install it ourselves.
[*]Pressing power button when computer running brings the shutdown-logout window as expected. Good.
[/LIST]

2008.11.15:
[LIST=1]
[*]Battery life gets reduced in a considerable amount. 30 to 60 minutes less of use on batteries compared to Vista. Always with wifi on.
[*]Battery life notification depends on what used to notify. Energy management shows different amount of battery remain than Battery Charge Monitor.
[*]If computer turned on with wifi off and then on ubuntu gnome desktop turn wifi switch on, then wifi will not be recognized until set off and set on again in the Network Connections Browser on Notification Applet in panel.
[*]Bluetooth file transfer seems to work fine, at least with SonyEricsson W910i. Browsing the phone contents is easy once paired laptop with phone via Bluetooth.
[*]Video out is useless. Completely locks the system. Plug the VGA cable to Video out produces complete lock of system, no mouse movement, no ctrl-alt-backspace, no ctrl-alt-supr. Just pres the power button makes the system shutdown.
Maybe this is also related to using VESA driver as INTEL driver makes system unusable yet. When 2.5.0 is available in repos we'll need to check again.
[*]Keyboard configuration is not possible. No key repetition nor delay chance to modify. Whatever the place in the bar, keyboard shows no effect. Keyboard is recognized as 105 keys intl. And there is no Sony keyboard available.
[/LIST]

2008.11.16:
[LIST=1]
[*]Today i tried to restart in Vista to check out something for work to find out that Vista drive is corrupted and there is no way to restart machine in Vista.
So, seems that the Disk Partition utility provided is not yet ready for sharing drive with Vista. When installing i just let the program to do the partition itself. So default options ruin Vista installation.
[/LIST]


2008.12.09:
[LIST=1]
[*]Actually I can restart in Vista now. Ubuntu set up 2 start Vista options, one with the right partition, the other with wrong partition (in the grub menu.lst). Selecting the appropriate makes Vista start after some quiet long time of rearranging whatever.
[*]Finally i got 1280x800 screen resolution, but still using VESA driver in xorg.conf. This was possible by means of modifying xorg.conf according to:[this link]("http://www.claudiocamacho.org/tech/sr11m_debian.php#s4s4").
[*]Other way to arrange the screen might be use the new drivers available at[this intel link]("http://intellinuxgraphics.org/download.html"). But i have not had time yet to test them, besides the process needs some compiling and now i am to lazy. As version 2.5.0 seems to be stable, maybe wait until it is available in the repositories. Hope will be soon.
[*]Extra keys below screen (Mode, Settings and the other 5) are not even detected by XEV. So i guess will be useless. So the set screen brightness as FN+Bright UP/DOWN are not even detected also by XEV.
[/LIST]

As soon as i discover more stuff or find workaround for the ones in here i will keep on posting.

Best regards
Xermán

---

