---
title: "Sentelic touchpads: horizontal two-finger scrolling fixed"
date: 2012-12-11
forum: Hardware
---

### Post by maze2 on 2012-12-11
I have created a patch of the kernel that makes horizontal two-finger scrolling become functional on Sentelic touchpads. After applying the patch, you need to activate it in synaptics xorg driver, and then it just works.

Vertical two-finger scrolling also becomes much smoother.

The kernel version on which I have worked is 3.7-rc8 (3.7-rc7 will work fine also if you apply the patch against it; other versions, I don't know)

I'm going to attempt a first submission of my patch to the relevant kernel maintainer in a few minutes. I guess at best what they'll do is ask me for changes.

Here's where you can help:
I own a Sentelic touchpad version STL3888_C0, so I'm sure my patch works with this version of the touchpad. But, I need to know if and how it works on earlier and later versions of the touchpad. If you do own a Sentelic touchpad of an earlier or later version, you can help me, and the community by trying the following:
1) Download, compile and install kernel version 3.7-r7 or 3.7-rc8.
2) Activate horizontal two-finger scrolling in xorg through by configuring the synaptics driver with the following directive: 
Option "HorizTwoFingerScroll"  "1"
3) Open your favorite X app, and make a status on how horizontal and vertical two-finger scrolling work for you.
4) Apply my patch, recompile and replace the psmouse.ko module by the patched version that you just compiled
5) rmmod psmouse && modprobe psmouse; ; after reloading the driver, retrieve the kernel log message you get, in contains the version of your touchpad
6) Retry horizontal and vertical two-finger scrolling
7) Give feedback by reply to this thread

You can obtain my patch through git:
```
git clone git://sentelic.pkbd.org/sentelic.git
```You can also apply it as a diff against the kernel source tree versions 2.7-rc7 or 3.7-rc8. The diff can be found in the git repository, or you can download it directly by following this link:
[http://sentelic.pkbd.org/20121212-diffoutput.txt](http://sentelic.pkbd.org/20121212-diffoutput.txt)

If there's any problem with either of these downloads, please let me know.

---

### Post by AbtZ on 2012-12-18
I will gladly try your patch. I have some questions first however.

1. How do I find my touchpad version?

2. Is it necessary to recompile the whole kernel to try it, or is there a faster way?

---

### Post by maze2 on 2012-12-19
1) yes sorry, lspci does not work, my bad. Simplest way to get your touchpad version is:

```
dmesg|grep sentelic
```You get a kernel log message every time the psmouse module is loaded. The version of your touchpad is given in there as a number. The correspondance to actual named versions is in sentelic.h. For example for me it's like that:

```
[376632.331405] psmouse serio4: sentelic: Finger Sensing Pad, hw: 14.3.1, sn: 58037, sw: 1.1.0-K
```My touchpad version is "14" corresponding to FSP_VER_STL3888_C0.

2) Basically you do have to recompile at least the kernel module. If you don't have already a compiled kernel, you have to compile one which takes a while. If you already have a compiled kernel, just apply the patch, then issue the make command. It will be short because it'll only recompile the psmouse module psmouse.ko. Then you can simply replace the module in the installed modules tree which is:
```
/lib/modules/your-kernel-version/kernel/drivers/input/mouse/psmouse.ko
```[U][B]

IMPORTANT[/B][/U]: please download [http://sentelic.pkbd.org/diff/3.7/diffoutput.txt](http://sentelic.pkbd.org/diff/3.7/diffoutput.txt) to get the latest version of the patch. 

This new patch is much simpler for the same effect.

---

### Post by AbtZ on 2012-12-23
Awesome. Two finger scroll AND horizontal two finger scroll went from unusable to being quite pleasant to use. With this fix I'd actually say the touchpad is more responsive than in Windows. I cloned the diff from git instead of using the http-link, but I assume they are the same?

However, it seems I have the exact same version as you do, so unfortunately I cannot help you there.

---

### Post by AbtZ on 2012-12-24
OK, this is bad. When I started the computer now the touchpad started behaving very irratically -- sometimes not responding, overshooting, random clicks.

I tried using the original psmouse module, as well as one that came with an older kernel, but I still get the same problem. Is there anything in the new firmware I tried that might have caused this?

---

### Post by maze2 on 2012-12-26
Well I'd say no, there is nothing in the modified driver which could cause this, since I changed only the way information is reported to userspace.

I haven't changed, removed or added any values written into the hardware registers, for instance.

Did the issue persist after rebooting again, or better, after shutting down the computer, waiting for maybe 20 seconds, and starting it again?

---

### Post by maze2 on 2012-12-27
Just in case, you could try to add this kernel boot parameter:
```
i8042.reset=1
```(this can be done from /etc/default/grub, then I think you have to use update-grub2 to regenerate your grub.cfg file)

I found this here:
[http://en.gentoo-wiki.com/wiki/Sentelic_touchpad](http://en.gentoo-wiki.com/wiki/Sentelic_touchpad)

And it's also mentioned here:
[http://en.gentoo-wiki.com/wiki/MSI_Wind](http://en.gentoo-wiki.com/wiki/MSI_Wind)

In case the touchpad "sporadically doesn't work after booting" which seems to fit your issue.

---

### Post by maze2 on 2012-12-27
> **AbtZ said:**
> I cloned the diff from git instead of using the http-link, but I assume they are the same?

The diff from the link below is the same as what you can clone through git:
 [http://sentelic.pkbd.org/diff/3.7/diffoutput.txt](http://sentelic.pkbd.org/diff/3.7/diffoutput.txt)
(you can also access the above link from the site's home page)

I have an old link which is an outdated version which I leave in there for maybe a few weeks since I linked it in a couple of places where I can't edit:
[http://sentelic.pkbd.org/20121212-diffoutput.txt](http://sentelic.pkbd.org/20121212-diffoutput.txt)
So you shouldn't use this version of the diff, it's outdated.

---

### Post by pezed on 2012-12-28
I'm currently using the saaros patch on my zenbook for vertical scrolling.  Is yours a variation of this one?

Also it seems I'm unable to connect to your git repository.

---

### Post by maze2 on 2012-12-28
> **pezed said:**
> I'm currently using the saaros patch on my zenbook for vertical scrolling.  Is yours a variation of this one?

My patch in its last incarnation is a very simple (one line!) modification of the stock Sentelic driver from the official mainline kernel 3.7 and 3.8.

I don't know if Saaros patch was included into the mainline kernel at some point in the past. If it was, there have been other changes since.

> **pezed said:**
> Also it seems I'm unable to connect to your git repository.

It seems that my repo is up right now as I write this. 

It also seems that Abtz succesfully did download from the git repo a few days ago.

Could be that you tried immediately after my ISP changed my IP address (I'm stuck with a dynamic IP with my current ISP). Every 24 hours my IP changes and it can take a few minutes before DNS servers are updated all around the world.

I did some trials yesterday, and it seems that my patch also resurrects two-finger tapping. For all useful purposes, I'll post my **/etc/X11/xorg.conf.d/50-synaptics.conf** below. With this it seems that I get the following:


[LIST]
[*]Left click with a one-finger click or one-finger tap
[*]Right click with a two-finger click
[*]Middle click with a two-finger tap (does not work without the patch)
[*]Vertical two-finger scrolling (kind of works without the patch bu the patch makes it much smoother)
[*]Horizontal two-finger scrolling (does not work without the patch)
[/LIST]
```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "Synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "HorizTwoFingerScroll"  "1"
        Option "TapButton1"  "1"
        Option "TapButton2"  "2"
EndSection

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection

Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection
```

---

### Post by AbtZ on 2012-12-29
> **maze2 said:**
> Well I'd say no, there is nothing in the modified driver which could cause this, since I changed only the way information is reported to userspace.

I haven't changed, removed or added any values written into the hardware registers, for instance.

Did the issue persist after rebooting again, or better, after shutting down the computer, waiting for maybe 20 seconds, and starting it again?
I don't want to say anything yet, but the problem I had might be because of a badly configured kernel. I'm on my second try now with a freshly compiled kernel, let's hope it works out better :)

I do still have the problem that the touchpad doesn't immediately work after boot/suspend, though. I already have the "i8042.reset=1"-parameter enabled. Ofttimes it will take several seconds before the driver is loaded:
```

<snip>
[    7.587054] wlan0: authenticate with 00:ff:ff:00:00:01
[    7.595318] wlan0: send auth to 00:ff:ff:00:00:01 (try 1/3)
[    7.597346] wlan0: authenticated
[    7.597433] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[    7.600092] wlan0: associate with 00:ff:ff:00:00:01 (try 1/3)
[    7.602654] wlan0: RX AssocResp from 00:ff:ff:00:00:01 (capab=0x411 status=0 aid=3)
[    7.602702] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    7.602731] wlan0: associated
[   18.541844] fuse init (API version 7.20)
[   35.293741] psmouse serio4: sentelic: Finger Sensing Pad, hw: 14.3.1, sn: 58037, sw: 1.1.0-K
[   35.337472] input: FSPPS/2 Sentelic FingerSensingPad as /devices/platform/i8042/serio4/input/input11
```

Is this something you know anything about? Or where I can get more info about fixing it? It's quite annoying.

---

