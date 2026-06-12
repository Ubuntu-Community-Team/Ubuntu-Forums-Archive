---
title: "Dell Inspiron 6000 install issues and solutions"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by jc3835 on 2005-06-28
Hi all!
I finally got my laptop up and running with 5.04 (HH) installed.
I ran into quite a few problems while installing, and many of them were resolved with help from these forums. What I wanted to do was create this thread to detail the problems I ran into and the solutions to those problems.

[COLOR=Red]On initial boot from CD I got a technicolor screen and was able to do nothing but reboot...[/COLOR]
[COLOR=Navy]Solution was to use the "linux vga=771" at the boot prompt.[/COLOR]

[COLOR=Red]Configuring the network with the installed wireless adapter would not work and I kept getting the error that "perhaps DHCP is not running" or something like that.[/COLOR] :-# 
[COLOR=Navy]Solution was to plug in  :|  and use the broadcom adapter instead of wireless. DHCP found that.[/COLOR]
[INDENT]I did everything to get the wireless working, even disabling security temporarily, but nothing worked for wireless. I read on here that the 2200 wireless setup has issues and requires an update outside of the 5.04 install, so I'm attributing the problem to that.[/INDENT]
[COLOR=Red]
Upon completion of the first stage of the install, halfway thru package installations I get sent into aptitude because of errors, even after updating what aptitude asks to be updated.[/COLOR]  ](*,) 
[COLOR=Navy]Solution (again found in the forums) was to remove "ubuntu-base" and "ubuntu-desktop" and I was then able to boot right into the gnome login gui![/COLOR]

Hopefully this will help others who are having these issues. It may be completely specific to the Dell model.
Again, I didn't come up with these solutions, but simply compiled them here into one thread.

Thanks goes out to everyone who did post the solutions initially.   :grin: 


JC

---

### Post by Vorian on 2005-06-28
I have a 6000 too, this link helped me out with my wifi. Thanks to luca_linux
Just follow this HowTo: [Just follow this HowTo: http://www.ubuntuforums.org/showthread.php?t=26623](Just follow this HowTo: http://www.ubuntuforums.org/showthread.php?t=26623) 

good luck :)

---

### Post by jc3835 on 2005-06-28
[QUOTE=Vorian]I have a 6000 too, this link helped me out with my wifi. Thanks to luca_linux
Just follow this HowTo: [Just follow this HowTo: http://www.ubuntuforums.org/showthread.php?t=26623](Just follow this HowTo: http://www.ubuntuforums.org/showthread.php?t=26623) 
[/QUOTE]

did you follow his instructions explicitly? meaning did you install everything he recommended?
What else have you done to your 6000? Did you have any issues with the touchpad?
How about the front panel buttons? I found a link that is supposed to get those working... I'll post it once I find it again and verify it works, if you need it.

Thanks.

---

### Post by ewinslow on 2005-06-28
I've also just installed Hoary on an Inspiron 6000, and didn't have an issue besides the vga=771. The wireless didn't get connected during the install, but had no problems once I booted into system.

One issue that I have had, and will be interested to see if you run into it, is the wireless connection would not come up again after coming out of hibernation or leaving the system idling for a bit. At some points the eth1 interface would disappear. An 'iwconfig' would not list eth1 at all.

Now I have upgraded the ipw2200 drivers to 1.0.4 and upgraded the firmware, but have not had time to evaluate the recurrence of the issue.

Other than that, Ubuntu has been great on this machine. Hibernation was working well for a while and then the wireless issue cropped up (perhaps a kernel upgrade messed it up?). Haven't it sleep on a lid close is not working out of the box, and I haven't put the time in to solve it.

Cheers.
Eric

---

### Post by ewinslow on 2005-06-28
[QUOTE=jc3835]did you follow his instructions explicitly? meaning did you install everything he recommended?
What else have you done to your 6000? Did you have any issues with the touchpad?
How about the front panel buttons? I found a link that is supposed to get those working... I'll post it once I find it again and verify it works, if you need it.
[/QUOTE]
I did follow those instructions closely, but did not go the WPA route. I stopped before installing wpa_supplicant.

As for the touchpad and the front panel buttons I have done nothing to get those working. The touchpad works fine, but no vertical or horizontal scrolling is enabled.

---

### Post by Vorian on 2005-06-28
[QUOTE=ewinslow](perhaps a kernel upgrade messed it up?)

Which kernal (2.6.11-1-686?)

---

### Post by Vorian on 2005-06-28
[QUOTE=jc3835]did you follow his instructions explicitly? meaning did you install everything he recommended?
What else have you done to your 6000? Did you have any issues with the touchpad?
How about the front panel buttons? I found a link that is supposed to get those working... I'll post it once I find it again and verify it works, if you need it.

Thanks.[/QUOTE]

No problems with the touchpad or keyboard. There is a problem with the 686 kernal, i have to boot with the 386.  Trying to work on that one......

---

### Post by ewinslow on 2005-06-28
[QUOTE=Vorian]

Which kernal (2.6.11-1-686?)[/QUOTE]
I'm on 2.6.10-5-386

---

### Post by ewinslow on 2005-06-29
Okay, now I'm totally hosed on the wireless (this post is being done from a Mac). I'm getting all the nice error messages laid out in this post:
[http://ubuntuforums.org/showthread.php?t=29950](http://ubuntuforums.org/showthread.php?t=29950) 
Not even a reboot gets the card loaded properly.

When I have the time to hook the machine up via wire to my router I'll try what that person did and rollback the driver to ipw2200 1.0.0

Wish me luck.

---

### Post by Vorian on 2005-06-29
[QUOTE=jc3835]
 Did you have any issues with the touchpad?
[/QUOTE]

I am having some issues with the scroll functions on the touchpad, any ideas? :smile:

---

### Post by banditti on 2005-06-29
Vorian, your issue is not with the 386, it is with the 2.6.11-686 kernel.

---

### Post by jc3835 on 2005-06-29
I found these links for the touchpad config, although I haven't tried anything yet... will do that tonight.

[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)
[http://www.simons.fi/touchpad.html](http://www.simons.fi/touchpad.html)

and there is a forum thread here outlining it as well:
[http://ubuntuforums.org/showthread.php?t=28132](http://ubuntuforums.org/showthread.php?t=28132)


Following the first link should be sufficient in getting all features working, including the vertical and horizontal scrolling from the touchpad.

Please post if anyone gets that working.
My touchpad works fine from the initial install, I'd just like to be able to disable tap-click and enable the scrollling.

JC

---

### Post by Vorian on 2005-06-29
[QUOTE=banditti]Vorian, your issue is not with the 386, it is with the 2.6.11-686 kernel.[/QUOTE]
 
Banditti, you seem wise and have much to share.  

I boot with the 386 kernal, and yet the scroll functions have yet to work.

---

### Post by jc3835 on 2005-06-29
As far as the front panel buttons, I think I found a solution... once again, I'll post my results later once I give the script a try.

This guy seems to have a solution from his install on a 9300:
[http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)
Halfway down the page he has a script to download and describes his setup.

Good luck and let the rest of us know if you succeed.

JC

---

### Post by jc3835 on 2005-06-30
Thought I'd post a little update to my progress:

I was unable to get much working last night. Took me forever to even run a "make" for the ipw2200 stuff. I figured out, after reading a lot of threads, that I had to upgrade to the 686 kernel headers and whatnot. Then I was able to at least get the ipw2200 installed... not working, but installed. I also was trying to use the WPA supplicant, however I think I may just go back to WEP if it works without all this hassle. [COLOR=Red]**No wireless yet!**[/COLOR]  :-# 

The front panel buttons... Haven't gotten the volume buttons, to work, but I think the play, pause, track, etc. buttons do work with the XMMS plugin I installed. The link I posted was for a guy running (K)Ubuntu, hence KDE, and he was using KDE packages, which I don't think should be a problem to install, but hey, what do I know.  ](*,) 

Installed the synaptics drivers, but still no vertical scrolling. I'll keep messing with that tonight and see if I can't get the vertical scrolling... I've gotten used to it within WinXP.

JC

---

### Post by ewinslow on 2005-06-30
[QUOTE=jc3835]
I was unable to get much working last night. Took me forever to even run a "make" for the ipw2200 stuff. I figured out, after reading a lot of threads, that I had to upgrade to the 686 kernel headers and whatnot. Then I was able to at least get the ipw2200 installed... not working, but installed. I also was trying to use the WPA supplicant, however I think I may just go back to WEP if it works without all this hassle. [COLOR=Red]**No wireless yet!**[/COLOR]  :-# 

JC[/QUOTE]
I rolled back my ipw2200 drivers to version 1.0.0, the stable version, and I'm up and running again with the wireless. Stable and working is good.  O:) Perhaps the issue was that the remove-old script in the 1.0.4 package did not remove all the old files. 1.0.0 does NOT ship with a remove-old script and I manually deleted the files, not directories, as directed in the INSTALL directions. I'm still running the 2.3 firmware (which needs to be used with the 1.0.4 drivers) and we'll see if that hurts me in some way. Also yet to be seen is if my wireless comes back from hibernation.

Was your wireless working with the 0.19 drivers that Hoary came with? My machine was working with those drivers.

---

### Post by ewinslow on 2005-07-01
[QUOTE=ewinslow] I'm still running the 2.3 firmware and we'll see if that hurts me in some way. Also yet to be seen is if my wireless comes back from hibernation.
[/QUOTE]
All is working, even coming back from hibernation. If I really wanted to complete my knowledge I'd try the 1.0.4 drivers being sure to clean out every bit of the old ones. Perhaps when I have some time on my hands. But for now it'll be the 1.0.0 drivers with the 2.3 firmware.

---

### Post by jc3835 on 2005-07-01
My wireless hasn't worked PERIOD  :-x 
I did a complete fresh install again last night, no wireless connection.
Then I tried using the NDISwrapper method that many people have tried, but no luck there either. 
 ](*,) 
I think tonight I'll do a fresh install once again, do apt-get install linux-686 first thing, reboot into the 686 kernel, then install the ipw2200 on the stable version. If I remember correctly, the first time I tried doing the ipw2200 I used 1.0.0 because someone else mentioned the stable drivers worked for them, but not the 1.0.4... I've tried both with no luck, but will keep at it! 

On the note of working with the Hoary install... what steps are you taking to configure wireless then to get it working?? Are you just using the network config tool and activating the wireless device (eth1) and it works? 

Thanks for all of the help.

---

### Post by jc3835 on 2005-07-01
OK... still trying to get the touchpad FULLY functional, ie. vertical scrolling.
I posted a question in the HOWTO regarding this crap, but realised I shouldn't post there... OOPs...
here's the link to that:
[http://www.ubuntuforums.org/showthread.php?t=28132&page=3](http://www.ubuntuforums.org/showthread.php?t=28132&page=3)

Hope someone can answer that question...

All the issues aside, I'm having a blast with Ubuntu so far.
Thanks for all of your help!

JC

---

### Post by ewinslow on 2005-07-02
[QUOTE=jc3835]

On the note of working with the Hoary install... what steps are you taking to configure wireless then to get it working?? Are you just using the network config tool and activating the wireless device (eth1) and it works? 
.[/QUOTE]
I believe I just used the System->Administration->Networking interface. For your key are you using a string as the password? If so, be sure to enter it as ```
s:passphrase
```
I've also configured in the past using 
```
iwconfig eth1 essid "NAME OF NETWORK"
iwconfig eth1 key s:passphrase

```
and that should do it.

Mine did work with whatever firmware was loaded and the 0.19 drivers. We should be able to get this working without issues. What do you see if you do the 
```
dmesg | grep 'ipw'
```?

---

### Post by bullpa on 2005-07-02
Look at here for the front panel keys set up using lineakd [http://www.antoniocheca.com/wp/content-text/ubuntu-inspiron6000.html](http://www.antoniocheca.com/wp/content-text/ubuntu-inspiron6000.html)
I added lineakd into the startup list of gnome, and all the front panel keys are working.

---

### Post by jc3835 on 2005-07-03
[QUOTE=ewinslow]I believe I just used the System->Administration->Networking interface. For your key are you using a string as the password? If so, be sure to enter it as ```
s:passphrase
```
I've also configured in the past using 
```
iwconfig eth1 essid "NAME OF NETWORK"
iwconfig eth1 key s:passphrase

```
and that should do it.

Mine did work with whatever firmware was loaded and the 0.19 drivers. We should be able to get this working without issues. What do you see if you do the 
```
dmesg | grep 'ipw'
```?[/QUOTE]

Thanks for offering more help...
```
root@ubuntu:~ # dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.0
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```
As you can see I've upgraded the drivers to the latest stable release.
I've tried using the passphrase and the numeric key for my WEP key.
I don't believe the WEP is my issue though, as I completely disabled it the other day, and I couldn't connect still. For some reason my router just isn't seeing the laptop, or doesn't like it for some reason. 

dhclient gives me this result:
```
root@ubuntu:~ # dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:36:5a:23
Sending on   LPF/eth1/00:12:f0:36:5a:23
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by jc3835 on 2005-07-03
[QUOTE=bullpa]Look at here for the front panel keys set up using lineakd [http://www.antoniocheca.com/wp/content-text/ubuntu-inspiron6000.html](http://www.antoniocheca.com/wp/content-text/ubuntu-inspiron6000.html)
I added lineakd into the startup list of gnome, and all the front panel keys are working.[/QUOTE]

Great link... one last favor though... can you tell me where the "startup list" is in gnome? 
Thanks for your help!

I hope this doesn't interfere with the plugin I installed in XMMS to use the front panel  buttons.  :???:  I posted a link to that earlier in this thread.

---

### Post by ewinslow on 2005-07-03
[QUOTE=jc3835]
```
root@ubuntu:~ # dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:36:5a:23
Sending on   LPF/eth1/00:12:f0:36:5a:23
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```[/QUOTE]
Hmmm. Looks like your Ubuntu is doing fine. Is the router setup correctly? Have you connected to it using another operating system?

On a related issue, my network interface woes with hibernation still exist. I just came back to my laptop and brought it up from hibernation and eth1 was not to be found by ifconfig or iwconfig. It just seems to disappear. Too bad. I need to reboot to get things going again.

---

### Post by jc3835 on 2005-07-03
Alright... we have WIRELESS!! Woohoo!  \\:D/ 
I disabled all security and MAC filtering in the router.
I restarted the computer... on restart eth0 (wired) was default and started. I went into network config (for the 14th time) and switched eth1 (wireless) to default.
Then I  hit Fn-F2 to enable the wireless transmitter... DUH!  ](*,) 
I mean I knew it was there... but I've never had to enable it manually within WinXP.
So I read on one of the sites to do this, and also that the WiFi light doesn't light up yet because of a bug, and did a "dhclient eth1" and voila!...
It finally connected...
Then I went into the router and re-enabled WEP (not even going to try WPA yet), added the key (numeric, not passphrase) and it connected again. So I'm a bit more secure now.
I guess it really came down to the Fn-F2 key, and the fact that it was never mentioned, so it never crossed my mind. Always the simplest things it is.
So thanks to everyone who has helped... I'll take wireless off of my ToDo list.  :smile: 

JC.

---

### Post by AsburyPark on 2005-07-04
[QUOTE=jc3835]Alright... we have WIRELESS!! Woohoo!  \\:D/ 
I disabled all security and MAC filtering in the router.
I restarted the computer... on restart eth0 (wired) was default and started. I went into network config (for the 14th time) and switched eth1 (wireless) to default.
Then I  hit Fn-F2 to enable the wireless transmitter... DUH!  ](*,) 
I mean I knew it was there... but I've never had to enable it manually within WinXP.
So I read on one of the sites to do this, and also that the WiFi light doesn't light up yet because of a bug, and did a "dhclient eth1" and voila!...
It finally connected...
Then I went into the router and re-enabled WEP (not even going to try WPA yet), added the key (numeric, not passphrase) and it connected again. So I'm a bit more secure now.
I guess it really came down to the Fn-F2 key, and the fact that it was never mentioned, so it never crossed my mind. Always the simplest things it is.
So thanks to everyone who has helped... I'll take wireless off of my ToDo list.  :smile: 

JC.[/QUOTE]
 Who would have thought.  With XP you don't even think of the FN~F2.  

I tied the F2 and it didn;t work.  Do you have the 2200 or the 2915?

Did you do anything else to your 6000?

---

### Post by jc3835 on 2005-07-04
[QUOTE=AsburyPark]Who would have thought.  With XP you don't even think of the FN~F2.  

I tied the F2 and it didn;t work.  Do you have the 2200 or the 2915?

Did you do anything else to your 6000?[/QUOTE]

That's what I was saying... it's so obvious to hit Fn-F2, but I've just never thought to do it.
I have the 2200BG in my laptop.
I installed scripts and tweaked to get the front panel buttons working. Soon I'll be rebuilding the kernel to include the new synaptics modules so that I can get the vertical scrolling portion working.
Other than that, I've just been tweaking the whole system and programs to my likings... nothing too major.
Really, I'm completely satisfied with Ubuntu HH. I haven't had any issues other than wireless, which after a lot of hassles, really wasn't an issue in the first place. Haven't tweaked the ATI drivers, sound, etc... worked right off the bat!

JC

---

### Post by AsburyPark on 2005-07-04
Everything worked on mine too except the wifi, front pannel buttons, and the scroll functions on the touchpad.  

I haven't been able to figure out the wifi, I tried the F2, didn't work for me.  I set configured my network preferences to eht1, still no wifi.

---

### Post by jc3835 on 2005-07-04
[QUOTE=AsburyPark]Everything worked on mine too except the wifi, front pannel buttons, and the scroll functions on the touchpad.  

I haven't been able to figure out the wifi, I tried the F2, didn't work for me.  I set configured my network preferences to eht1, still no wifi.[/QUOTE]

Best thing I found to do is to restart, go into network config, activate eth1, enter your ESSID, enter your WEP if you have one, hit OK, OK, and then hit Fn-F2. After that, type the following in a shell window:

```
sudo dhclient eth1
``` 

Hopefully, if your router likes your settings, it'll connect.

The other guys were saying that should work with the default drivers, however, I had updated to 1.0.0, and I think I'm going to try 1.0.4 soon to see if I can get WPA working.

Good luck.

---

### Post by Vorian on 2005-07-04
Has anyone been able to get the scroll functions working yet? (touchpad)

---

### Post by jc3835 on 2005-07-05
[QUOTE=Vorian]Has anyone been able to get the scroll functions working yet? (touchpad)[/QUOTE]

Haven't gotten to it quite yet... long 4th of July weekend and whatnot recently have really infringed on my Linux time  :smile: 
Best solution seems to be to upgrade the kernel to 2.6.12.2 as there are some fixes in that kernel related to the touchpad and whatnot... see here:
[http://www.ubuntuforums.org/showthread.php?t=46106](http://www.ubuntuforums.org/showthread.php?t=46106)

I'll post my results if I get to it soon, but this week is looking to be busy.

Good luck!

JC

---

### Post by bullpa on 2005-07-05
[QUOTE=jc3835]Great link... one last favor though... can you tell me where the "startup list" is in gnome? 
Thanks for your help!
[/QUOTE]

Goto system->preferences->sessions->startup programs

---

### Post by bullpa on 2005-07-05
After upgraded ipw2200 to 1.0.4, I was unable to get router list in the gnome networking and 'iwlist scan' returned 'no result'. Used to be able to scan with what comes from ubuntu.
Just now tried pressing 'fn+f2', and I am able to scan networks, but still cannot get connected ;(

---

### Post by jc3835 on 2005-07-05
[QUOTE=bullpa]Goto system->preferences->sessions->startup programs[/QUOTE]

That's what I was trying to use, so I guess I was on the right track.
For some reason though, I was unable to add the script... I thought maybe it was only able to use programs there, and that maybe there was another location for startup scripts.
Thanks!

---

### Post by Vorian on 2005-07-05
I got the scroll to work!!!!

```
% sudo aptitude install linux-source-2.6.10 kernel-package xorg-driver-synaptics
% cd /usr/src
% sudo tar -x -j -f linux-source-2.6.10.tar.bz2
% cd linux-source-2.6.10
% gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | sudo patch -p1
% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config
% sudo make-kpkg --us --uc --initrd --append_to_version "-5-386-alps" kernel_image kernel_headers kernel_source
% cd ..
% sudo dpkg -i kernel*alps*deb
```

```
Then just use the template in /usr/share/doc/xorg-driver-synaptics/README.alps for your xorg.conf. To disable tap-to-click while preserving the scrolling behavior on the right edge of the pad, try setting MaxTapTime to 0.
``` 

here's the link to the how to

[http://ubuntuforums.org/showthread.php?t=28132&highlight=alps](http://ubuntuforums.org/showthread.php?t=28132&highlight=alps)

---

### Post by jc3835 on 2005-07-07
Having the same "black screen" issue with this method of building a new kernel. Doesn't matter which set of instructions I find and use to compile a new kernel, I can't ever login to them. GRUB comes up, I make a selection, and just blackness.
I've tried this method, I've tried the method in the HOWTO, I've tried other methods out on the web.
Frustrating.

Good thing everything else works with the Ubuntu kernels :)

---

### Post by Zerileous on 2005-07-07
[QUOTE=Vorian]I got the scroll to work!!!!
[/quote]

I followed those directions and the *-alps kernel will fail to start x, any chance you could share your xorg.conf file?

---

### Post by bullpa on 2005-07-09
Ok, back home today I tried again the wireless network. This time I am able to connect to the router, with WEP 64bit, or WAP (using wap_supplicant). The ipw2200 driver is the new one 1.0.4.
Happy? Sort of.
I cannot use the network! Pinging the router returns:
```

$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```
So although wireless is working, it cannot reach nowhere!

eth1 looks like this
```

eth1      Link encap:Ethernet  HWaddr 00:12:F0:7F:69:4B
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe7f:694b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1004 errors:1 dropped:1 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10507 (10.2 KiB)  TX bytes:22644 (22.1 KiB)
          Interrupt:17 Base address:0x6000 Memory:dfcfd000-dfcfdfff

```

Any clue? I hate to sit beside the router to have a cable pluged in just because my wireless is not working as expected!

---

### Post by bullpa on 2005-07-11
[QUOTE=bullpa]
```

$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```
[/QUOTE]

Wireless is running :-P 
The 'sendmsg' error is caused by the firewall. Why I didn't observe anything about eth1 in firestarter, there are lots of messages recorded in /var/log/message, after I stopped the firewall, eth1 is able to connect.
I am happy with my laptop now.
I found the KWifiManager could detect whether the wireless radio was disabled or not. I am using gnome and wish the network-admin could have the same function.

---

### Post by jc3835 on 2005-07-11
Still no new kernel, but everything else is working great.
One item of note though, for others' info... When setting the WEP key, I couldn't use:

```
s:passphrase
``` 

I had to manually type the 128-bit encryption key. With the ipwconfig I could see that the key was incorrect when using the "s:passphrase" and it didn't connect to the router.
Not sure if this is true for everybody, but just a note for others that it may cause problems.

JC

Edit: Stupid smiley faces showing up when you don't want them to!  :-x

---

### Post by jc3835 on 2005-07-13
I thought I'd give a little update on my status...

Once I finished setting up the wireless with WEP and saved the session, everything works from all subsequent boots and restarts. It hangs a bit on the network configuration portion of bootup, I suppose while it's talking to the router and obtaining a connection, but that's only a minor issue... at least it's working.
I don't have to turn on the antenna or do anything, it works fine on startup, which I am extremely happy about.   :grin: 
Still struggling to get a working kernel built that isn't from synaptic... but that won't stop me from trying.  ](*,) 

JC

---

### Post by adrawer on 2005-07-13
I've got a 6000, but has anyone gotten their ati x300 mobile graphics to work with 3d acceleration in ubuntu?

---

### Post by jc3835 on 2005-07-13
[QUOTE=adrawer]I've got a 6000, but has anyone gotten their ati x300 mobile graphics to work with 3d acceleration in ubuntu?[/QUOTE]

Haven't seen the need to yet, so I haven't really tried.
Why do you need to, other than gaming?

---

### Post by Andilek on 2005-07-19
I did and x300 works.

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X300 (M22)"
        Driver          "fglrx"
        Option          "MonitorLayout"         "LVDS,NONE"
#       Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseInternalAGPGART"    "no"
EndSection

---

### Post by caporaso on 2005-07-19
Hello all:
Has anyone had any luck getting the display to work at 1920x1200 resolution? I've had luck with the front panel buttons, my Treo 600 phone, and for the most part all of the hardware (including the internal wireless card), and the screen resolution is my last hardware hurdle.

Thanks for any advice!

Greg

---

### Post by jc3835 on 2005-07-19
[QUOTE=caporaso]Hello all:
Has anyone had any luck getting the display to work at 1920x1200 resolution? I've had luck with the front panel buttons, my Treo 600 phone, and for the most part all of the hardware (including the internal wireless card), and the screen resolution is my last hardware hurdle.

Thanks for any advice!

Greg[/QUOTE]

how did you get the front panel buttons working? using lineakd?
Volume buttons work without having XMMS or mplayer running?

---

### Post by caporaso on 2005-07-19
To get the front panel buttons working I used the 'Keyboard Shortcuts' tool that came with Ubuntu.

I found this at 'System > Preferences > Keyboard Shortcuts'. It seems to work good, but I haven't tried it with too many applications.

---

### Post by jc3835 on 2005-07-19
Andilek, thanks for the input. What are the benefits of upgrading the ATI drivers other than gaming improvements?

On an unrelated note... I FINALLY got a new kernel to install properly and boot!  \\:D/ 
I detailed my steps in this thread:
[http://ubuntuforums.org/showthread.php?t=46729](http://ubuntuforums.org/showthread.php?t=46729)

I basically followed Luca's HowTo, other than a couple of things I outlined in that thread.

JC

---

### Post by Andilek on 2005-07-19
Well, 3D graphics is working much better and faster  ;-) 
Even 2D seems a bit better, but I would have to run tests.
Starting Xserver is faster.

Contrary there is some issue with colors. When I started to work, it was OK, than I closed laptop for a while, and when opened, I got color information broken, fonts unreadable and everything was sick.
After restarting xserver it was OK.

Second issue are fonts. I used LCD aliasing, but now I see weird colors in fonts so I had to switch it to gray (the best shapes regime)

I am unsure, may be during the time I will get sick of these drivers and switch back to ATI driver. But I red somewhere the new drivers are prepared, so the hope dies last.

---

### Post by Andilek on 2005-07-19
I just found that last config changes eliminatd color problems when closing display:


Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "GLcore"
#this will fix on fly resolution changes issue
        SubSection "extmod"
           Option "omit xfree86-dga"
        EndSubSection
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X300 (M22)"
        Driver          "fglrx"
        Option          "MonitorLayout"         "LVDS,NONE"
        BusID           "PCI:1:0:0"
        Option          "UseInternalAGPGART"    "no"
    # If X refuses to use the screen resolution you asked for,
    # uncomment this; see "Bugs and Workarounds" for details.
#       Option          "NoDDC"

    # === Video Overlay for the Xv extension ===
#       Option          "VideoOverlay"   "on"

    # === OpenGL Overlay ===
    # Note: When OpenGL Overlay is enabled, Video Overlay
    #       will be disabled automatically
        Option          "OpenGLOverlay"  "on"

     # === Use internal AGP GART support? ===
     # If OpenGL acceleration doesn't work, try using "yes" here
     # and disable the kernel agpgart driver.
       Option   "UseInternalAGPGART"  "no"

EndSection

---

### Post by mbmonk on 2005-07-22
Ok i have a Dell Inspiron laptop 6000

When I boot up normally on my laptop I get a black screen. I plugged in my CRT Monitor to the laptop and instead of a black screen I get the ubuntu GUI login screen. So how can I config ubuntu to display on my laptop?

I did not use the vga=771 flag on the install. What does that do and could that be my problem?

Any clues? Any way I can give you more information? Should I post this to another forum? Should I take my shoes of and do an African tribal dance to the laptop gods?

Thanks,
mike

---

### Post by mbmonk on 2005-07-23
Would someone with a working display for the Inspiron 6000 post the XConfig here? 

Thanks,
Mike

---

### Post by zho40 on 2005-07-23
Here is mine w/ ati video driver:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"GLcore"
	Load	"glx"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"UserInternalAGPGART" "no"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"MonitorLayout" "LVDS, NONE"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by jc3835 on 2005-07-28
[QUOTE=caporaso]To get the front panel buttons working I used the 'Keyboard Shortcuts' tool that came with Ubuntu.

I found this at 'System > Preferences > Keyboard Shortcuts'. It seems to work good, but I haven't tried it with too many applications.[/QUOTE]

That's just too easy, ain't it!!
That keyboard shortcut mapping is SWEET!!
Thanks for that advice... here I'm installing libraries and following HowTo's and nothing's working...  ](*,)

---

### Post by c0rderr0y on 2005-07-29
weird i didnt have any wireless problems mine worked right out of the box....

---

### Post by jc3835 on 2005-07-29
[QUOTE=c0rderr0y]weird i didnt have any wireless problems mine worked right out of the box....[/QUOTE]

yeah, some others had said that too... mine might've worked out of the box too, who knows... but i messed with it and had to get it working.

---

### Post by RBJ1128 on 2005-08-03
[QUOTE=zho40]Here is mine w/ ati video driver:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

...

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"GLcore"
	Load	"glx"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

...

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"UserInternalAGPGART" "no"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"MonitorLayout" "LVDS, NONE"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

...

EndSection[/QUOTE]

Is there anything that you did other than add this stuff to your **/etc/X11/xorg.conf** file; i.e. install any additional packages and/or run any configurations?

---

### Post by jc3835 on 2005-08-03
RBJ1128:
who is your question directed to?
install any other packages period? or just to get something specific to work?

---

### Post by RBJ1128 on 2005-08-03
[QUOTE=jc3835]RBJ1128:
who is your question directed to?
install any other packages period? or just to get something specific to work?[/QUOTE]
 Sorry, my question is directed to getting the ATI drivers working correctly.

---

### Post by jc3835 on 2005-08-03
[QUOTE=RBJ1128]Sorry, my question is directed to getting the ATI drivers working correctly.[/QUOTE]

no prob... i personally haven't tried the ATI drivers yet on my 6000.
i've been satisfied with the default drivers and haven't needed 3D accel.

---

### Post by RBJ1128 on 2005-08-03
[QUOTE=jc3835]no prob... i personally haven't tried the ATI drivers yet on my 6000.
i've been satisfied with the default drivers and haven't needed 3D accel.[/QUOTE]
 My main reason for asking is that whenever I reboot I have color distortion on the GDM login screen.  If I kill X with "Ctrl" + "Alt" + "Backspace" I then get the correct login screen coloring.  I am hoping that using the ATI drivers would correct this.

---

### Post by MoreBikesFewerCars on 2005-08-12
Edit: started new thread after no responses.

---

### Post by robtotheb on 2006-01-17
Any one worked out how to get the WiFi light working?

---

### Post by AsburyPark on 2006-01-18
[QUOTE=robtotheb]Any one worked out how to get the WiFi light working?[/QUOTE]

nope, gave up.

---

### Post by jc3835 on 2006-02-12
Been a while since I've re-visited this post.
No, I never did get the WiFi light working, but I haven't tried much since.
I did upgrade to Breezy with no issues though, other than my touchpad vertical scroll disappeared on me again.

---

### Post by Vorian on 2006-06-02
Dapper is working perfectly on the old 6000!

---

### Post by jc3835 on 2006-06-02
[QUOTE=Vorian]Dapper is working perfectly on the old 6000![/QUOTE]

thanks for the info... i'll have to upgrade and give it a try.

---

### Post by Vorian on 2006-07-13
I've gone back to 5.04.....

I just like it so...

---

### Post by basketcase on 2006-07-14
Dapper works great on my 6000...though no light, and I haven't tried WPA yet.

---

### Post by dans on 2007-02-12
I'm running 6.10 on an Inspiron 6000 with no wifi problems.  I'm using NetworkManager to manage.

---

### Post by scoggy on 2007-02-14
I'm dual booting Edgy on my Inspiron 6000. I thas an intel wireless card, and I can't get it connected to my router with WPA. I've seen various posts about this, but can anyone link to a topic which goes through it in detail?

Cheers

---

