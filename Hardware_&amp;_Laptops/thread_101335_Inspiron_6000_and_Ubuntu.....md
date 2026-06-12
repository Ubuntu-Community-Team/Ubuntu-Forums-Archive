---
title: "Inspiron 6000 and Ubuntu...."
date: 2005-12-09
forum: Hardware &amp; Laptops
---

### Post by Confuse on 2005-12-09
Hi guys,

I was wondering if anyone was running this laptop with ubuntu and what they thought of it. Does everything work well?

Also, does anyone have any opinions on the quality of the LCD on this machine? I bought the 1280x768 version, I couldn't afford the fancier one. ;[ Anyways, what can you guys tell me about the screen?

---

### Post by emperor on 2005-12-09
[quote=Confuse]Hi guys,

I was wondering if anyone was running this laptop with ubuntu and what they thought of it. Does everything work well?

Also, does anyone have any opinions on the quality of the LCD on this machine? I bought the 1280x768 version, I couldn't afford the fancier one. ;[ Anyways, what can you guys tell me about the screen?[/quote]

I have a Inspiron 9300 with ati adapter and a higher resolution screen. Ubuntu Breezy installs and runs quite well on this hardware. The only exception is the sleep/hibernation feature does not work yet; expecially with the ATI display drivers. DMA is enabled on the DVD drive in Breezy, so no kernel re-compile is required.

Ubuntu Breezy is an excellant choice!

---

### Post by Confuse on 2005-12-09
Why doesn't sleep/hibernate work? Because of the ATI driver issue? Thanks for the input. I knew I could count on ubuntu for my laptop needs. =]

---

### Post by Delvien on 2005-12-09
Im running Kubuntu, and it runs very well. With some work i was able to get 3d working, Wifi working, (the wifi light does not work even though the wireless card works ) 

ATI cards are wierd with every OS, i had the same kind of problems in windows that i do in linux (hibernate, lid closing etc.) so hey..

---

### Post by ewinslow on 2005-12-10
I have an Inspriron 6000 widescreen 15 incher. It's not the fanciest screen though. I saved some bucks there. If I were richer I would have upgraded the screen, but for my programming needs it is not a necessity.

Everything works quite well including the wireless (no wireless light here either, but it is not missed). I've never bothered with the 3d acceleration. I'm not doing games or video.

Hibernate does work on this one, but not Suspend when closing the lid. I have not put much time into getting that to work either. The ACPI stuff has been getting better every release (I've run all 3 major releases of Ubuntu) so I'm hoping Suspend works without extra effort with Dapper Drake.

I did have to do a bit of digging to get the Alps touchpad working in all ways. It was extremely sensitive after installing Breezy Badger. A post in these forums had the fix spelled out nicely.

---

### Post by nevin on 2005-12-10
ive got the 6000 with the 1280x800 or whatever screen.  when installing, i had to do a special line like "linux vga-711" or something like that for it to work.  but after that everything worked automatically.  i still havent set up the alps scrolling features or anything.  if someone has a link for the alps, please post it, cause i'd really like to get this working too.

/nevin/

---

### Post by emperor on 2005-12-10
[quote=nevin]if someone has a link for the alps, please post it, cause i'd really like to get this working too.
/nevin/[/quote]

Here's the the procedure I used to get the Alps touchpad problem fixed on my i9300:
[http://www.ubuntuforums.org/showthread.php?t=76585&page=2](http://www.ubuntuforums.org/showthread.php?t=76585&page=2)

---

### Post by Confuse on 2005-12-10
Hmmmmmm, so opt out for a higher resolution screen is what you're hinting at huh?

---

### Post by Delvien on 2005-12-11
WSXGA+ is pretty much the best screen imho, not to large of a resolution, and text pics, and video are SO sharp.. a very noticable difference from the WXGA screen

---

### Post by jhnphm on 2005-12-11
[QUOTE=Delvien]Im running Kubuntu, and it runs very well. With some work i was able to get 3d working, Wifi working, (the wifi light does not work even though the wireless card works ) 

ATI cards are wierd with every OS, i had the same kind of problems in windows that i do in linux (hibernate, lid closing etc.) so hey..[/QUOTE]
Put "ipw2200 led=1" in your /etc/modules

Anyway, yes, it works very well on the I6K - my main gripe is mostly hibernate/suspend support.

---

### Post by GoodPanos on 2005-12-11
Ubuntu runs great on this notebook.  I have the "fancier" model; WSXGA and ATI 300X.

The same here, can't get suspend to work with 3D accelaration.  The only way I found to enable suspension is by disabling 3D accelaration and removing the *vga-711* line from /boot/grub/menu.lst.  The only thing with that is that when you boot or shutdown the screen flashes.

I also have not gotten the modem to work nor the SD slot.

---

### Post by Confuse on 2005-12-11
Guys! Thanks for all your input. I've decided to get the inspiron with the upgraded screen, although I held out on the X300 video card due to my non-gamer status. Hope thats not a problem when it comes to the quality of the screen. This should be a great laptop for my basic needs. Thanks! Hopefully hibernate and suspend aren't too much of a hassle to get to work, but a challenge is always a fun thing (sometimes). =]

---

### Post by Leebobs on 2005-12-12
[QUOTE=ewinslow]I did have to do a bit of digging to get the Alps touchpad working in all ways. It was extremely sensitive after installing Breezy Badger. A post in these forums had the fix spelled out nicely.[/QUOTE]

My tocuhpad is uber sensitive, you don't happen to have the link for that post do you?

Thanks

Leebobs

---

### Post by ewinslow on 2005-12-12
[QUOTE=Leebobs]My tocuhpad is uber sensitive, you don't happen to have the link for that post do you?
[/QUOTE]

Here is the link:
[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)

One thing to note is that you could have a different 'event' number than what Scubajeff is showing. From his run of  *cat /proc/bus/input/devices* he shows 'event5' in the Handlers line. My system was showing 'event2'. That's what I used in the 
Options "Device" "/dev/input/event5" 
line of the xorg.conf file

May it help.

---

### Post by Confuse on 2005-12-12
Guys, whats the battery life like of this laptop in ubuntu? I do moderate web surfing/ircing and whatnot.

---

### Post by emperor on 2005-12-12
[quote=GoodPanos] I also have not gotten the modem to work nor the SD slot.[/quote]

I've had the modem working using the drivers from here:
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

Only tried the free version at 14k limit.

---

### Post by Vorian on 2005-12-18
[QUOTE=Confuse]Guys, whats the battery life like of this laptop in ubuntu? I do moderate web surfing/ircing and whatnot.[/QUOTE]

You'll get 3-4 hours dep on screen setting.

I do love ubuntu on the 6000!

---

### Post by Confuse on 2005-12-18
[QUOTE=Vorian]You'll get 3-4 hours dep on screen setting.

I do love ubuntu on the 6000![/QUOTE]

With the 6 cell really? Wow. I don't play games so I didn't opt for the Radeon X300.

---

### Post by Vorian on 2005-12-18
[QUOTE=Confuse]With the 6 cell really? Wow. I don't play games so I didn't opt for the Radeon X300.[/QUOTE]

I have the screen at 1 clik above bottom, and I also will run one app at a time when I am away from power.

I don't play games either, I just had to get the system over $2000 to get one of those $800 off coupons....

---

### Post by Confuse on 2005-12-18
[QUOTE=Vorian]I have the screen at 1 clik above bottom, and I also will run one app at a time when I am away from power.

I don't play games either, I just had to get the system over $2000 to get one of those $800 off coupons....[/QUOTE]


What do you think about the screen? Good quality? I opted for the WSXGA+ which gives me a ridiculously high resolution and better viewing angles, but I've heard in the past of the infamous dell light leakage screens, so I'm a little frightened. Thanks for the feedback, I appreciate it. Still anxiously awating my machine. hehe

---

### Post by Vorian on 2005-12-18
I love the screen when I don't have to run between computers, I hate going from the 1680x1200 to a 10"crt with 800x600@#$@!!!!!

---

### Post by Confuse on 2005-12-20
Whoo hoo! Got my Inspiron! Its installing Ubuntu as we speak! Thanks for all the replies guys!

---

### Post by Confuse on 2005-12-21
Quick question, what is the best way to setup my wireless network with this computer? Do I use the drivers supplied by default or use some of the instructions on the board about downloading the ipw2200 drivers? I'm having random trouble connecting with network manager.

---

### Post by Vorian on 2005-12-23
[QUOTE=Confuse]Quick question, what is the best way to setup my wireless network with this computer? Do I use the drivers supplied by default or use some of the instructions on the board about downloading the ipw2200 drivers? I'm having random trouble connecting with network manager.[/QUOTE]

You get the drivers you need when you install.  What kind of random trouble are you having?

---

### Post by Confuse on 2005-12-23
I was having problems connecting with network manager. It kept trying to login to my wireless network with key but never did. Now that issue is over for now. Thats why I thought there was something wrong with the driver.

On another note, I can't get suspend to work. It goes into suspend mode, but then it doesn't come out of it. The screen remains black and I don't think theres any response from the system. Any ideas?

---

### Post by GoodPanos on 2005-12-23
[QUOTE=Confuse]The screen remains black and I don't think theres any response from the system. Any ideas?[/QUOTE]
Do you have the ATI drivers installed?

---

### Post by Confuse on 2005-12-23
No, its just the integrated drivers by intel.

---

### Post by steve313 on 2005-12-23
[QUOTE=nevin]ive got the 6000 with the 1280x800 or whatever screen.  when installing, i had to do a special line like "linux vga-711" or something like that for it to work.  but after that everything worked automatically.  i still havent set up the alps scrolling features or anything.  if someone has a link for the alps, please post it, cause i'd really like to get this working too.

/nevin/[/QUOTE]

I believe the exact line is "**linux vga=771**" -- I tried 711, which failed, but then found the following thread:
[http://www.ubuntuforums.org/showthread.php?t=45142&highlight=inspiron+6000](http://www.ubuntuforums.org/showthread.php?t=45142&highlight=inspiron+6000)

---

### Post by oveh on 2005-12-24
hi! installed ubuntu for the first time yesterday and everything seems to be working, except 3d ;P my i6000 is the wuxga version with 1920x1200 resolution and the ati x300, i just love the screen :D

about getting the 3d to work i tried to follow the steps in method 2 over at [ATIwiki]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide"),    but the fglrxinfo still shows the mesa info :( 
```

ove@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
going to keep trying to get it to work, help me anyone? ;)

---

### Post by emperor on 2005-12-25
> **oveh]hi! installed ubuntu for the first time yesterday and everything seems to be working, except 3d  said:**
> ATIwiki[/URL],    but the fglrxinfo still shows the mesa info :( 
```

ove@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

``` going to keep trying to get it to work, help me anyone? ;)


Did you edit your xorg.conf file and change "ati" to "fglrx"?

See this section in "offical" wiki for details:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by oveh on 2005-12-25
> or use sudo dpkg-reconfigure xserver-xorg and select "fglrx" instead of "ati"

i did that yesterday, now i edited xorg.conf and manually replacing ati with fglrx, still no 3d support :(

---

### Post by emperor on 2005-12-25
Does  "sudo lsmod" show the fglrx module loaded?

if not, then 
sudo modprobe fglrx

Then kill x and restart it.
1. Exit to gdm
2. Then restart x using "Ctrl-Alt-Backspace"
3. login 
4. recheck using "fglrxinfo"

---

### Post by oveh on 2005-12-25
thanx for helping me emperor ;) i ended up by following [this]("http://www.ubuntuforums.org/showthread.php?t=24557&pp=10") thread in the forum, and now it works :D

---

### Post by oveh on 2005-12-26
Hmm, Anyone given tv-out with x300 a try? in winxp its just to plug in the cable and press Fn+F8, but that doesn't work in ubuntu. So I don't know how to activate it. 

Read some about tv-out in the forums and some people are saying that you need to reboot with the cable in, and then ubuntu will discover the tv. Didn't work for me, the only thing that happens is som flicker at the tv and then black again. 

I would love to get ubuntu to work on my new tv, so please say what you did to get it to work :)

---

### Post by emperor on 2005-12-26
[quote=oveh]Hmm, Anyone given tv-out with x300 a try? in winxp its just to plug in the cable and press Fn+F8, but that doesn't work in ubuntu. So I don't know how to activate it. 

Read some about tv-out in the forums and some people are saying that you need to reboot with the cable in, and then ubuntu will discover the tv. Didn't work for me, the only thing that happens is som flicker at the tv and then black again. 

I would love to get ubuntu to work on my new tv, so please say what you did to get it to work :)[/quote][[IMG]http://ubuntuforums.org/images/element/buttons_blue/quote.gif[/IMG]]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=604515")

ATI's fglrx driver for linux does not support TV out.

The Gatos project has TV out working for some ATI Video adapters but I do not think that the X300 is one of them.

---

### Post by oveh on 2005-12-27
[QUOTE=emperor][[IMG]http://ubuntuforums.org/images/element/buttons_blue/quote.gif[/IMG]]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=604515")

ATI's fglrx driver for linux does not support TV out.

The Gatos project has TV out working for some ATI Video adapters but I do not think that the X300 is one of them.[/QUOTE]
Ok, thanks for the info ;)

---

### Post by Confuse on 2005-12-28
I have a theory on my suspend problem. My inspiron contains the new sonoma chipset, perhaps this has something to do with it. I think the older inspirons have a different chipset (can't remember code name) and they do work with suspend, but thats just my theory. Would anyone like to set me straight? If anyone has the new Sonoma chipset and has suspend working, reply to this post with your experience please. I reinstalled ubuntu and still suspend is broken.

---

### Post by emperor on 2005-12-28
[quote=Confuse]I have a theory on my suspend problem. My inspiron contains the new sonoma chipset, perhaps this has something to do with it. I think the older inspirons have a different chipset (can't remember code name) and they do work with suspend, but thats just my theory. Would anyone like to set me straight? If anyone has the new Sonoma chipset and has suspend working, reply to this post with your experience please. I reinstalled ubuntu and still suspend is broken.[/quote] 
All Dell Inspiron 6000 and 9300 laptops with 533Mhz frontside bus and DDR2 memory have the Sonoma chipset. This appears to coencide with the introduction of the 1.6 Mobile Pentuim chipsets in Dell's laptops; the 7xx series Mobile Pentuim's. The suspend problem is generally a X11display driver problem. ATI's fglrx driver does not support the advanced sleep functions. The more generic "ati" driver is better in this respect, but has no 3d support.

---

### Post by seekyrr on 2006-01-03
Am looking into getting one of these Dell 6000.

Are you guys running it with 512 or 1024mb or ram?

Seek

---

### Post by oveh on 2006-01-03
1024mb, special offer from dell so the upgrade from 512mb was free :)

---

### Post by daviddoregan on 2006-02-10
> Did you edit your xorg.conf file and change "ati" to "fglrx"?

Im running Breezy on an Inspiron 6000, I installed all fglrx and followed this step. I've got ATI Radeon 300 64Mb and 1280x800 screen
fglrxinfo shows that this step worked, and glxinfo goes noticably faster!

How do I know if 3D support is enabled?
My 1280x800 option is now gone and I'm stuck with 1280x768 and 60Hz, It's faster but a little bit blurry. Is there a solution to this?

I've done nothing about installing special 915 drivers or anything else, what needs to be done, if anything? I saw a post giving top 10 things to do right away after installing Ubuntu, but I've lost it!

I'm hoping to do something about my touchpad sensitivity soon. 

I'm really happy with my new Ubuntu install, this is my first time with Linux. 
I'd appreciate any tips for the inspiron 6000!

---

