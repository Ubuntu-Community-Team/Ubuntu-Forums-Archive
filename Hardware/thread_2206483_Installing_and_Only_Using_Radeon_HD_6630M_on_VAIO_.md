---
title: "Installing and Only Using Radeon HD 6630M on VAIO VPC-CB15F"
date: 2014-02-19
forum: Hardware
---

### Post by CybaCowboy on 2014-02-19
At the moment my Sony VAIO VPC-CB15F is using *only* my integrated Intel HD Graphics 3000 graphics card with the "X.org X server - AMD/ATI display driver wrapper from xserver-xorg-video-ati" driver, however I would like to:
a) Get my AMD Radeon HD 6630M graphics card working and;
b) Use the Radeon HD 6630M *exclusively* (i.e. _not_ use the integrated Intel HD Graphics 3000 graphics card _at all_).

I'm not worried about whether it's propriety or Open Source drivers, just as long as I am either using my Radeon HD 6630M exclusively *or* I am able to switch between the two effortlessly (though as I said, I'd *prefer* the former)...

At the time of writing, I am using Ubuntu 13.10 ("Saucy Salamander"), however as per usual, I will be upgrading to Ubuntu 14.04 LTS ("Trusty Tahr") the moment it is available (I typically upgrade to each new version, .04 LTS and .10).

Being someone that is semi-competent with Terminal, I have "toyed" with this in the past, but the last time I did, Ubuntu would boot-in to a plain black screen after login (i.e. I could see the login screen, I could login and then the screen would go completely black) and I had to run a whole heap of commands from the recovery Terminal (at boot) in order to get things running again.. Most likely however, it was because I "broke" something when trying to setup my Radeon HD 6630M - I did it using a whole page of commands I found via Google, none of which was specific to my laptop.

Any help in sorting things out would be greatly appreciated...

---

### Post by squakie on 2014-02-19
I *think* you'd find that series needs the fglrx-updates driver package.  You would need to first be sure that your BIOS is set to allow PCI video and not forcing the onboard GPU.  Then I personally would install synaptic package manager if you haven't already:

sudo apt-get install synaptic

When that finishes, start up synaptic via the menus.

In the search area, type:

fglrx-updates

and it should take you right to the package.  Click it and mark for installation, then click Apply and wait for it to finish.

---

### Post by soum_axetuirk on 2014-02-20
Ubuntu recently declared support for Hybrid graphics card (integrated Intel HD with ati) as [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
Make sure you are using the default Ubuntu Display manager, that is  LightDM.
 For **AMD/Intel Hybrid systems**, run this command in the terminal :
```
sudo apt-get install fglrx fglrx-pxpress
```

i promise you will get a working graphics card with swithable option.you can use flowlessly as in windows.both intel HD and ATI.
[ATTACH=CONFIG]250529[/ATTACH]

---

### Post by squakie on 2014-02-21
You stated you wanted to use the AMD/ati card exclusively and not use on the onboard GPU at all.  With those ideas in mind, stick with flgrx-updates.  It has the correct driver for your AMD/ATI card.

If you want to be able to switch between them, then follow [ 						 					]("http://ubuntuforums.org/member.php?u=1906179") 				 				 					 						 	[**[COLOR=#000000]soum_axetuirk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1906179")'s post.  If you just want to use the AMD/ATI, follow mine for fglrx-updates.

---

### Post by CybaCowboy on 2014-02-21
> **soum_axetuirk said:**
> Ubuntu recently declared support for Hybrid graphics card (integrated Intel HD with ati) as [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
Make sure you are using the default Ubuntu Display manager, that is  LightDM.
 For **AMD/Intel Hybrid systems**, run this command in the terminal :
```
sudo apt-get install fglrx fglrx-pxpress
```

i promise you will get a working graphics card with swithable option.you can use flowlessly as in windows.both intel HD and ATI.
[ATTACH=CONFIG]250529[/ATTACH]

Yeah, I got that far... But it (the AMD management/switching program) tells me there's no drivers installed!

In Ubuntu's settings, it says I have propriety drivers in use (specifically "Video driver for the AMD graphics accelerators from fglrx (proprietary)")... So I'm not too sure why it's saying there's no drivers installed.

I went to installed the drivers manually using [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD"), but it warns that the latest drivers are probably incompatible with Ubuntu 3.10 and when I get to Step 2 of "Installing via the Command Line", it only lists my integrated (Intel) graphics... There's no mention of my AMD graphics at all!
[I]display: :0.0  screen: 0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 9.2.1)[/I]


> **squakie said:**
> If you want to be able to switch between them, then follow                                                                                      [**[COLOR=#000000]soum_axetuirk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1906179")'s post.  If you just want to use the AMD/ATI, follow mine for fglrx-updates.

Well that is still the intention... But I can't seem to access my BIOS!

According to the Sony support site, machines with Windows 8 (including those that have been upgraded) need to hold the "Assist" button to power-on and they will be taken to the "recovery" menu... This works fine on our computers that had Windows 8 pre-installed, but on my laptop (which originally ran Windows 7), it simply takes me to the same menu one would get when inserting the "recovery" DVDs (wipe the computer, make changes to the partitions, yada yada yada).

I've tried all the usual keys (various function keys, Delete, etc) on the "VAIO" logo (which the Sony support site says shouldn't work once a computer has been upgraded to Windows 8), but all I get is an "Operating system not found" message!

Sooo, unless you've got an answer to this dilemma, I'll have to go with sodum's answer... It's not what I was aiming for, but it's halfway there.

---

### Post by squakie on 2014-02-21
If it installed fglrx, not fglrx-updates, I don't believe it is the correct driver - that may be why it's giving you the error.  When I tried fglrx, it gave me a message about "card not supported" or some such thing whenever I logged in so that X started.  Removing fglrx and changing to fglrx-updates fixed that for me.  If  you check things out for fglrx-updates, it mentions the HD cards it supports whereas fglrx itself doesn't support those.

---

### Post by CybaCowboy on 2014-02-21
As I was expecting (I've had it happen before), fglrs-updates caused Unity to crash (all I get is a black screen after login)... So I booted-up Terminal (which still worked) and un-installed fglrx.

After a reboot, I thought I'd give it one more shot... And it worked!

I'm using the fglrx drivers and according to the AMD program, everything is working fine...

It's not what I originally intended (as per my BIOS issue above), but it'll do for now I guess.

---

### Post by squakie on 2014-02-22
Hummmmmm........flgrx-updates is supposed to be the driver for those cards.  I've had to use it on both a HD 5450 and a HD 6450.  

Hey, as long as things are working for you, who am I to say??  ;) ;)

Glad you found your solution and be sure to thank [**[COLOR=#000000]soum_axetuirk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1906179") for their help.  Sorry I couldn't have been of more help.

---

### Post by squakie on 2014-02-22
BTW - wasn't this the same issue from your post [http://ubuntuforums.org/showthread.php?t=1999501&page=2](http://ubuntuforums.org/showthread.php?t=1999501&page=2) from 2012?  I thought it looked like you had it solved there.

---

### Post by CybaCowboy on 2014-02-22
> **squakie said:**
> and be sure to thank [**[COLOR=#000000]soum_axetuirk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1906179") for their help.

Yeah about that... Maybe it's just me, but I can't find the damn link! I know that I've used it before, but for the life of me, I simply cannot find it!

Maybe I'm just getting old...

*Rolls eyes*


> **squakie said:**
> BTW - wasn't this the same issue from your post [http://ubuntuforums.org/showthread.php?t=1999501&page=2](http://ubuntuforums.org/showthread.php?t=1999501&page=2) from 2012?  I thought it looked like you had it solved there.

Ha, so it is... I forgot about that!

Because I'm using Ubuntu almost exclusively now and because I am seriously considering making the switch full-time, I've started keeping a log locally (i.e. on my computer) of "common problems and resolutions" from the past, in addition to actively educating myself on the more advanced aspects of Ubuntu and Linux-based operating systems... Terminal commands in particular.

I'm no wizard yet, but computers come naturally to me and if I am to make the full-time jump, I'd rather know my stuff.

---

