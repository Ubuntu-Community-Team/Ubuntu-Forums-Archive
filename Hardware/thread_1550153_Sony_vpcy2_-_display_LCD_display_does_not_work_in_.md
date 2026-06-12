---
title: "Sony vpcy2 - display LCD display does not work in X"
date: 2010-08-10
forum: Hardware
---

### Post by hamfletta on 2010-08-10
My LCD on my laptop will not display anything under X at all!

The live CD and full installation does not seem to set up X properly. I get a blank screen. I can use external display AND the LCD display is recognised (did xrandr and it listed the 2 displays). 

The only time i can get anything to run on the display is in recovery mode ONLY if i add "nomodeset" to the boot options.

I have tried adding a xorg.conf and manually setting a resolution but that made matters worse. Doing that it hangs and 2 led's blink at me (which i assume is something to do with refresh rates).

Anyone else have this laptop and got it working under ubuntu?

Interestingly enough fedora 13 live cd does the EXACT same thing so I am assuming this is a problem with X.

Any ideas? 

Adam

---

### Post by unixbestie on 2010-08-11
I have  the same problems. There  is still no solution. Vesa as  a solution?

Ronny

---

### Post by plb22 on 2010-08-15
I have the same problems with my Sony vpcy2

Philipp

---

### Post by nicewedda on 2010-08-24
Hi, 

I have also the same problem. 

Is there any solution on the net? Any ideas?

cheers

nicewedda

---

### Post by harrydrip on 2010-08-24
Probably not much help but I have this laptop with the ATI video chip and it does work fine under FC13 32bit. So if you have this variant you should be able to get it to go...

---

### Post by rioatca on 2010-08-24
I have exact same problem on DELL Latitude E6510.
LCD is Seiko Epson 15'
works on external monitor//

---

### Post by hamfletta on 2010-09-17
Still no joy. It has

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)


output from lspci rather than the ATI in the earlier post. Seems that linux does not like this graphics controller. 

Any suggestions?

---

### Post by tino.truppel on 2010-09-30
Same issue here. Any ideas are welcome!

I managed to start X using VESA, but only with 1024x786. Does somebody know how to switch to the native resolution?

Thanks

---

### Post by dpezely on 2010-10-23
Installing Ubuntu 10.10 on Sony Y-Series (VPCY2; Core i5; RADEON graphics option; mid-2010)

Quick notes on Ubuntu 10.10:
 - Ubuntu 10.10 installs cleanly but fails after reboot.
 - Prior to 23 October 2010: Upon reboot, system would hang without proprietary RADEON video drivers
 - Boot parameters must be added manually for Touchpad to be recognized.


Work-around:
 
From Grub menu, select "Recovery Mode" which bypasses X11.
From Recovery Menu, select "dpkg - Repair broken packages".

When that completes and you are returned to the "Recovery Mode" menu, select
"root shell".

Edit the Grub menu, so as to enable the Touchpad.

Run:
# vi /etc/default/grub
change the line:
 GRUB_CMDLINE_LINUX=""
to:
 GRUB_CMDLINE_LINUX="i8042.nopnp"

(See /var/log/messages or /var/log/Xorg.0.log: "PNP: PS/2 appears to have
AUX port disabled, if this is incorrect please boot with i8042.nopnp")


Further notes have been checked-in here:
[https://code.launchpad.net/~sony-vaio-y-series]("https://code.launchpad.net/%7Esony-vaio-y-series")
(Look for file called INSTALL.txt)

---

### Post by xalbert76 on 2010-10-29
Hey folks.

The same problem here. I bought VPCY2 a few days ago and tried to install Ubuntu 10.04 first and then also 10.10.

With 10.04, I had to connect an external screen to see the installation, otherwise the laptop LCD was totally blank. Ubuntu installs without problems, even webcam and all controls with the Fn key work fine (brightness up & down, etc.) However, I could only use it if the external screen was connected.

I then upgraded to 10.10 using the Update Manager within 10.04 but after the reboot, both the LCD display and the external monitor remained blank. The only way to use it was to boot to the recovery mode, create xorg.conf for vesa and reboot. If X is started after normal boot, it loads up but the screen goes blank after a few minutes. One has to boot into the recovery console again and do startx from the command line. This allows me to use X, although only in 1024x768.

Somebody mentioned the blinking of the LEDs. This happened to me when I had nomodeset or i915.modeset=0 or 1 in my grub menu. Also, xforcevesa has no effect - I had to manually edit xorg.conf to use the vesa driver.

Any further ideas about what could be the cause of the blank screen ?

Roman

---

### Post by jmaroto on 2010-11-09
Same problem here. 

vaio vpcy2 with intel graphics.

As workaround, using "nomodeset" and xforcevesa during boot works for me (with low resolution, of course).

Regarding to the problem with the intel driver, it is listed in the known bugs in fedora 14:

[http://fedoraproject.org/wiki/Common_F14_bugs#Blank_screen_displayed_on_many_laptops_using_eDP_displays_.28Dell_E4310.2C_E6410.2C_E6500.2C_E6510.2C_Sony_Vaio_VPCZ1.29](http://fedoraproject.org/wiki/Common_F14_bugs#Blank_screen_displayed_on_many_laptops_using_eDP_displays_.28Dell_E4310.2C_E6410.2C_E6500.2C_E6510.2C_Sony_Vaio_VPCZ1.29)

But the bug already resolved listed in the wiki looks promising:

[https://bugzilla.redhat.com/show_bug.cgi?id=596557](https://bugzilla.redhat.com/show_bug.cgi?id=596557)

The problem was reported with a vaio z, but looks the same thing, and I have no time to check it but probably both Y and Z series share the same chipset.

Should be great if someone could test the new kernel.

---

### Post by xalbert76 on 2011-01-22
I just noticed a release of the new Intel video driver v. 2.14.0 for linux. From what I read, it is promised that this be included in kernels 2.6.37 and higher. Has anobody compiled any of these kernels on Sony Vaio Y ? Is the problem with KMS now working (i.e. blank screen) for these cards fixed ? I really hate to run my laptop on the VESA resolution.

Thanks,

Roman

---

### Post by bkye on 2011-01-25
I have Sony VAIO vpcy216 laptop with intel i3-330um proccessor nad Intel HD Graphics. I fixed the blank screen and touchpad using the new kernel and alternative drivers as told here:

[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e](http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e) 

It is working for me. I can use 1366*768 resolution and touchpad now. But brightness is in the maximum level and cannot be changed using fn keys. Still looking for solution about this problem and waiting for your respond. 

Regards

---

### Post by xalbert76 on 2011-01-25
bkye, thanks a lot for bringing this to my attention. This works like a charm. I had to install only the kernel and the headers and I am now at 1366x768. After all those months my desktop fonts seem to me quite compressed now. You are great ! Thanks so much.

---

### Post by bkye on 2011-01-25
> **xalbert76 said:**
> bkye, thanks a lot for bringing this to my attention. This works like a charm. I had to install only the kernel and the headers and I am now at 1366x768. After all those months my desktop fonts seem to me quite compressed now. You are great ! Thanks so much.

I am very glad that I could help you! How about brightness control ? Does it work?

Edit : What is your full model number?

---

### Post by xalbert76 on 2011-01-27
Yes, brightness control works and the sound control works as well. I have Ubuntu 10.04 into which I installed the kernel you wrote about. The laptop is SONY VAIO VPCY21S1E.

---

### Post by ceminino on 2011-03-21
> **bkye said:**
> I have Sony VAIO vpcy216 laptop with intel i3-330um proccessor nad Intel HD Graphics. I fixed the blank screen and touchpad using the new kernel and alternative drivers as told here:

[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e](http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e) 

It is working for me. I can use 1366*768 resolution and touchpad now. But brightness is in the maximum level and cannot be changed using fn keys. Still looking for solution about this problem and waiting for your respond. 

Regards

I tried this on my vpcy21s1e but it didn't work. It seems the intel driver loads but it can't find any screen :/ 
I tried several of the new kernels 2.6.37 or 2.6.38 but it doesn't work... Could you post your xorg.conf file?

---

### Post by ceminino on 2011-03-23
> **xalbert76 said:**
> Yes, brightness control works and the sound control works as well. I have Ubuntu 10.04 into which I installed the kernel you wrote about. The laptop is SONY VAIO VPCY21S1E.

which kernel did you install? the one he suggested is not available anymore...

---

### Post by mkdotam on 2011-03-23
> **ceminino said:**
> I tried this on my vpcy21s1e but it didn't work. It seems the intel driver loads but it can't find any screen :/ 
I tried several of the new kernels 2.6.37 or 2.6.38 but it doesn't work... Could you post your xorg.conf file?

Same for me, I'm on vpcy216gx and I've tried kernels from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/) and here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-03-08-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-03-08-natty/) , both these kernels didn't work. On the last one even wifi didn't work. I've tried both 'vesa' and 'intel' drivers in my xorg.conf and both fails when I'm running without "nomodeset"

---

### Post by dinoc on 2011-04-28
Hi guys,

I have installed the latest Ubuntu 11.04 on my Vayo VPCY2 , and everything seems to work fine "out of the box" (install) , X, mouse, sound, bluetooth ... except the wifi adapter which is grayed out (I can't enable it) , it says :

"Wireless is disabled by hardware switch" - but I don't know about the existence of any hardware switch for wireless for this computer, do you ?

Anyone know how to enable the wireless on this ?

The adapter seems to be detected fine :
```

[B]
iwconfig wlan0[/B]
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

How did you enable your wireless on your laptops ?

---

### Post by ceminino on 2011-04-28
> **dinoc said:**
> Hi guys,

I have installed the latest Ubuntu 11.04 on my Vayo VPCY2 , and everything seems to work out of the box (install) , X, mouse, sound, bluetooth ... except the wifi adapter which is grayed out (I can't enable it) , it says :

"Wireless is disabled by hardware switch" - but I don't know about the existence of any hardware switch for wireless for this computer, do you ?

Anyone know how to enable the wireless on this ?

The adapter seems to be detected fine :
```

[B]
iwconfig wlan0[/B]
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

How did you enable your wireless on your laptops ?

you have to blacklist the module acer-wmi which somehow loads...

---

### Post by mkdotam on 2011-04-28
> **dinoc said:**
> Hi guys,

I have installed the latest Ubuntu 11.04 on my Vayo VPCY2 , and everything seems to work out of the box (install) , X, mouse, sound, bluetooth ... except the wifi adapter which is grayed out (I can't enable it) , it says :

"Wireless is disabled by hardware switch" - but I don't know about the existence of any hardware switch for wireless for this computer, do you ?

Anyone know how to enable the wireless on this ?

The adapter seems to be detected fine :
```

[B]
iwconfig wlan0[/B]
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

How did you enable your wireless on your laptops ?

Try to do following:
rfkill list
rfkill unblock 0
rfkill unblock 0
rfkill unblock 4
rfkill unblock 4
rfkill list
You will see the following: 
```
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
Both soft and hard blocked for phy0 and sony-wifi should be "no".

Then install wicd:
```

sudo apt-get install wicd

```
And then run Menu -> Internet -> Wicd Network Manager

It will work fine with wifi (o;

---

### Post by mkdotam on 2011-04-28
Btw, does anyone knows how to deal with closing lid stuff? 

When I'm closing the lid (both "do nothing" and "blank screen" modes) it show white screen and never turn back on again.

---

### Post by dinoc on 2011-04-28
WOW you guys are FAST !  :)

I'm replying  from a wifi enabled Vaio now  :)

Many thanks!
Dinu

---

### Post by mkdotam on 2011-04-28
> **ceminino said:**
> you have to blacklist the module acer-wmi which somehow loads...
And how could I disable that? It's sucks to do this rfkill stuff after every boot :D 

[QUOTE=dinoc]WOW you guys are FAST !  
I'm replying from a wifi enabled Vaio now  
Many thanks!
Dinu
[/QUOTE]
Glad to hear! 
You're welcome (o;

---

### Post by dinoc on 2011-04-28
Yep you have to issue all rfkill commands again after each reboot, I just did that after closing the lid :) which takes me to the next issue 

where I can confirm after closing the lid, the laptop enters in a power save mode and when trying to recover the screen remains blanc

---

### Post by ceminino on 2011-04-28
> **mkdotam said:**
> Btw, does anyone knows how to deal with closing lid stuff? 

When I'm closing the lid (both "do nothing" and "blank screen" modes) it show white screen and never turn back on again.

it's because standby doesn't work, it's really annoying because it worked with the previous kernel.

---

### Post by ceminino on 2011-04-28
> **mkdotam said:**
> And how could I disable that? It's sucks to do this rfkill stuff after every boot :D 


Glad to hear! 
You're welcome (o;

just add the line

blacklist acer-wmi

in /etc/modprobe.d/blacklist.conf

it'll then work automatically on boot.

---

### Post by dinoc on 2011-05-04
Yes, works great, thank you @ceminino !

---

### Post by dinoc on 2011-08-13
Guys I've updated the kernel (following Ubuntu update) to 2.6.38-11 and the X is not working anymore.
Is working with 2.6.38-9 but not with 2.6.38-11 , wtf is going on ?
Do you have the same issue ?

---

### Post by mkdotam on 2011-08-13
I'm on 2.6.38-10 and it works fine. Didn't updated yet.

---

### Post by ceminino on 2011-08-13
> **dinoc said:**
> Guys I've updated the kernel (following Ubuntu update) to 2.6.38-11 and the X is not working anymore.
Is working with 2.6.38-9 but not with 2.6.38-11 , wtf is going on ?
Do you have the same issue ?

I'm glad I didn't do the update yet...

---

### Post by Ruisou on 2011-09-02
Any thoughts on the Fn keys, or any other way for that matter, not able to adjust screen brightness?

---

### Post by dinoc on 2011-09-21
Guys,

If you have the suspend/hibernation issue on your Vaio laptops please post here , too - the more we report this the better, maybe they will fix this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357)

---

### Post by dinoc on 2011-09-26
guys does your suspend/hibernate work on your Vaio laptops ?
If yes, what did you do to make it work ?

---

### Post by mkdotam on 2011-09-27
No, even worse. If I will close the lid, and then open again, it will show blank screen, despite of I've change settings to do nothing.

---

### Post by ceminino on 2011-09-27
> **mkdotam said:**
> No, even worse. If I will close the lid, and then open again, it will show blank screen, despite of I've change settings to do nothing.

+1

Add to that that X doesnt work with the new kernel... No more sony for me...

---

### Post by dinoc on 2011-09-27
Can you guys please report this issue on the bug I"ve opened :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357)

They will not fix this, if I'm the only one who complain about this we should be a little bit united here .

Another bug where X is not working on 11.10:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/860791](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/860791)

Also I've opened a bug not being able to upgrade to 11.10 Beta 2.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/860100](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/860100)

If you guys have other bugs, please report them, also.

---

### Post by dinoc on 2011-10-08
**"Thanks"** for sharing your problems with X server 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/860791](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/860791)

PS> it looks the X, suspend and hibernation are working fine with 3.1 (tried the OpenSuse 12.1 Beta)

---

### Post by dinoc on 2011-10-11
Tried Natty 11.04 and kernel 3.1.rc7 ( oneirc ) and X is working again.
It lookes like Suspend and Hibernate are working (tough there are some errors, but both seems to work).

---

### Post by mkdotam on 2011-10-12
Thanks for good news (o:

---

### Post by dinoc on 2011-12-10
Has anyone tried if X server and others are working in 11.10 ?

---

### Post by dinoc on 2013-02-24
This was the solution that fixed my brightness issue in Ubuntu 12.10
[http://ubuntuforums.org/showthread.php?t=2086359](http://ubuntuforums.org/showthread.php?t=2086359)

---

