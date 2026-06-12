---
title: "Touch Screen wont work on my tablet pc"
date: 2011-02-24
forum: Hardware
---

### Post by Dj_Whitelion on 2011-02-24
Hi.

I have a prob. I ame thinking about installing ubuntu notebook ed 
on a tablet pc i have.
Its windows 7 on it right now.
Its this tablet: [http://blog.wholesaleonepiece.com/new-ipad-style-windows-7-tablet-pc-p07-winpad-1011-review/](http://blog.wholesaleonepiece.com/new-ipad-style-windows-7-tablet-pc-p07-winpad-1011-review/)

after serching abit i can se that one can buy the tablet with ubuntu notebook ed alreddy installed.
But when i try ubuntu over live usb i cant get the touch screen to work.
I dont want to try to fully install ubuntu until i know how to fiks the touch screen.
Do eney one here know how?:confused:

The name for the tablet is WinPad P07 or TENQ P07 also.

---

### Post by Dj_Whitelion on 2011-02-24
i have to also say that im almost a totaly newb on linux.
I understand alitle. But im far from a superuser.

im from norway. So im also sorry for my bad english.

---

### Post by Favux on 2011-02-24
Hi Dj_Whitelion,

Welcome to Ubuntu forums!

Let's see if we can identify who makes the touch screen.  Enter in a terminal:
```
lsusb
```
and see if the output contains the touch screen.  Post the output with your next post.

---

### Post by Dj_Whitelion on 2011-02-24
thanks ALOT for your help....

ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2101:1011 ActionStar 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$

---

### Post by Favux on 2011-02-24
There is no tablet listed in the lsusb output.

Looking at the reviews it is described as two finger touch (2FGT).

Given it doesn't appear to be a usb device it could be a serial device.

Based on the above I'm going to make a wild guess.  I think it is a new Wacom serial touch screen device.

They have been developing a new driver called the "Wacom W8001 serial touchscreen driver".  That driver isn't installed in Ubuntu by default like the standard Wacom drivers.  Which explains why it doesn't work with the live CD.

Right now the source code called wacom_w8001.c is in input-wacom-0.10.10-2.  Which is in turn in the xf86-input-wacom folder:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)

If so you have the first touch screen that needs that driver I am aware of.  We'll have to figure out how to compile it and install it, but I don't think that would be too hard.

Remember it is always best to keep your Windows partition if possible for BIOS and firmware updates.

---

### Post by Dj_Whitelion on 2011-02-24
Hi again..

Thanks for the respons.
The tablet onley have 16gig hard drive. And windows is using it all almost.
So if i ame going to put linux on it i have to use the whole hard drive. 
i have seen pictures of this tablet with ubuntu on. So maby the driver you are talking about is for this tablet? I mean. Sens they offer to sell this tablet with ubuntu on it. It has to be a driver somewhere? :)

---

### Post by Favux on 2011-02-24
Sure.  If it isn't the Wacom you would have to figure out which it is.  And you would hope if it comes with just Ubuntu installed they have some way to update it without needing Windows.

If it allows you to make an emergency Windows restore disk or whatever though, be sure to do that first.

---

### Post by Dj_Whitelion on 2011-02-24
hehe yea...
im going to bed now.
So wil try after work tomorow.
Did read the text with the driver that i did fined on the link you sendt. did not understand all.
But im also to tierd i reley understand that much right now :)
So going at it again tomorow :)
I wil report if i get it to work :) if i do its just the wireless and bluetooth left to figure out :)

---

### Post by Dj_Whitelion on 2011-02-25
Hi.

After using houers with uppdate the touch screen stil dont work. I used this way to install the driver:

[https://help.ubuntu.com/community/Wacom/LatestDriver#Compiling](https://help.ubuntu.com/community/Wacom/LatestDriver#Compiling)

> The simplest way is to add the wacom-plus package archive: 

sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get dist-upgrade

Then, In order to install the updated kernel module for Bamboo Fun: 

sudo apt-get install wacom-dkms

Restart the computer for changes to take effect. 

---

### Post by Favux on 2011-02-27
Hi Dj_Whitelion,

Sorry for the delayed response.

If I understand you correctly you are installing the wrong X driver.  You want the new Wacom W8001 serial touchscreen driver which is in the input-wacom-0.10.10-2 package:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/).  It's in the 2.6.30 folder in the input-wacom folder.  There's also a README that applies to it in the inputattach folder.

We need to figure out how to compile and install the W8001 serial touchscreen driver.

---

### Post by Dj_Whitelion on 2011-02-28
Hi..

I did try this to:> 
**Compiling it yourself**

 Usually  it is not necessary to compile the drivers, as they come pre-compiled.  It is strongly discouraged to compile your own drivers and instead  should seek a ppa with the updated driver from a trusted source. If one  doesn't exist, then please ask. 
To install, using the precompiled binaries: 

[LIST]
[*]Download the latest drivers from the [Linux Wacom Project]("http://linuxwacom.sourceforge.net/")
[*]Extract the .tar.bz2 file to your desktop (you can safely delete these files later)
[*]Open a terminal (Accessories > Terminal)
[*]type  the following, entering your password when prompted and replacing  "linuxwacom-0.8.1-6" with the name of the folder created when you  extracted the .tar.bz2 file: cd Desktop/linuxwacom-0.8.8-6/prebuilt
sudo ./uninstall
[*]sudo ./install
[/LIST]
[FONT=monospace]

If this helps?

But nohing helpt.
I did read the readme file. But i did not understand that much tho.
Im prity nuub at this.

But i have to say.

Linux do read the touch screen in some way.,
Becouse if i touch the screen it reads that touch as a doubble klick.
So if i use a mouse i can hold it over a point and then touch the screen and it wil "klick". But it wont "klick" where i point my finger on the touch screen. Onley where i but the curser with a mouse.
[/FONT]

---

### Post by Favux on 2011-02-28
OK, as near as I can tell we first need to compile input-wacom and it will automatically make the wacom_w8001.ko (a kernel driver).  Apparently one of the locations it will turn up in is /lib64/modules/2.6.35-xx-generic/kernel/drivers/input/touchscreen.

Instructions on how to compile input-wacom are in the alternate section 1 here:  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

So that gets us at least halfway.  If the tablet isn't working at that point we need to make sure it is autoloading.  If it is then we need to look at the input-attach stuff.

---

### Post by Dj_Whitelion on 2011-02-28
Thanks for your help this far.
I wil try this after work today.
And say if it works or not :)
(and i wil try to read and try to understand now :P )

---

### Post by ojdon on 2011-02-28
Your tablet is fairly similar to the Viewpad 10. Not too sure if the Touch Screen is the same though, but is you read my tutorial here, it might [help]("http://ollie-reardon.co.cc/?p=182") you. 

What problems are you getting? Does it not work at all? Or does it work with two fingers pressed at the same time, if it's the latter then it's a problem with detecting multi-touch.

---

### Post by Dj_Whitelion on 2011-02-28
Hi..

I se on the picures of the wiewpad that its not the same.

[IMG]http://tabletnorge.no/butikk/images/473/IMG_0017+%281024x683%29.jpg/[/IMG]

[IMG]http://tabletnorge.no/butikk/images/474/IMG_0018+%281024x683%29.jpg/[/IMG]

This is WinPad

I did ask the produsers of this tablet. And they say that the touch screen name is "Nas". But serching "nas" dont tell me eneything :P
The onley thing that happens if i touch the screen is a dobble "klick" action.
So in some way the screen is working. Just not as it shuld.

---

### Post by EvilRobot on 2011-03-10
If it's still not working, have you checked to see if utouch is installed? There is a PPA for utouch in Launchpad, maybe that would help.

I'm curious to see if you get this working as I was thinking of getting the same tablet.

---

### Post by Dj_Whitelion on 2011-03-16
Hi all.
Sorry for not answering.
I have had almost no time to test. But now i have had the time to test.
Now the produser told me to test ubuntu 10.04.02, that it shuld work.
i formated the windows hard drive so im on an clean install. No live cd eney more.
It just took to much time when i was doing somthing on live cd.

I have tryed what you Favux did say on the link.
And stil nothing. maby i have to try to install  ubuntu 10.10?
Onley prob with that is that even with a new download when i try to make a USB install pen i get an arror that wont let me use live or install.

Eney ide?
Now with an 10.04 clean install i dont get the same response when i touch the screen as i did on the notebook live.

Best Regardes
Hans Benny

---

### Post by Dj_Whitelion on 2011-03-18
> **ojdon said:**
> Your tablet is fairly similar to the Viewpad 10. Not too sure if the Touch Screen is the same though, but is you read my tutorial here, it might [help]("http://ollie-reardon.co.cc/?p=182") you. 

What problems are you getting? Does it not work at all? Or does it work with two fingers pressed at the same time, if it's the latter then it's a problem with detecting multi-touch.
Hi ojdon.
I did to day format the tablet and instaled Ubundu 10.10 notebook.
Then i had the prob that the touch screen work onley with 2 fingers.
I did use the way you have on that link.
And what happend was that now the touch screen dont work at al. 
Do you know way?

Best Regardes
Hans Benny

---

### Post by pguedes on 2011-03-21
I have this same "tablet" and since I am a Ubuntu User for more than 4 Years, I really would like to use the tablet with Ubuntu.

Unfortunately from Live USB I'm having exactly the same problem with Ubuntu 10.10. :(

After searching some forums and Checking in Windows 7 device manager the Touch device is a: 

Unitec usb touch 227d-0a19

I tried to ask the guy from [www.gizchina.com]("http://www.gizchina.com") if he could get me in touch with the developer guys who gave him this tablet with Ubuntu (working amazingly well), but no answer...

Check here: [http://www.gizchina.com/?s=ubuntu+tablet]("http://www.gizchina.com/?s=ubuntu+tablet")

Ubuntu is still a long way to be as tablet friendly as Win7, but I really prefer Ubuntu because this way I can have more usable SSD space (Win7 takes 14GB!!!), and no issues with virus and Malware/Spyware.
Also,.....because Windows7 weird Limitations......: Programs Files can only be installed in SSD drive, and Service Pack 1 cannot be installed because it requires at least 2GB of free SSD space.....which is impossible to have.....so it is not possible to install SP1....


Also if someone has the disassembly instructions for this tablet it woud be wonderfull, I would like to try to swap the SSD by a HDD or a Larger SSD, without breaking it.

BR.

---

### Post by pguedes on 2011-04-04
OK I installed dthe ubuntu on a USB stick, but not as a live one, it is set has primary partition, so it runs like it was a real hard disk on the tablet.

Curioslly the touchscreen works only when I use two fingers.....

Another curious thing is that if instaed of ubuntu I use for example, clonezilla (yes clonezilla, the touchscreen seems to work very well....)

---

### Post by Dj_Whitelion on 2011-04-04
clonezilla?

What is clonezilla?

---

### Post by pguedes on 2011-04-04
clonezilla is a set of tools running in linux that allow anyone to clone a disk or partition. runs as a live cd/usb

i used it to backup my whole windows 7 original installation before messing with ubunto on mty tablet.

curiouslly i noticed that with the original linux distro running in clonezilla the touchscreen seems to work better then with ubuntu. (i did not tried multitouch)

google it! :)

---

### Post by let_there_be_linux on 2011-04-12
Hi,

I read that this Tablet would be getting Ubuntu, but now it seems development has stopped :S. I was already getting impatient and was considering to buy the Windows version and then install Ubuntu on it myself. I only want to use this tablet if i can run it with Linux and not with Windows.
I don't mind messing around before it works, but it does need to be able to work before i get stuck with a tablet i can't use.
Basically my question is if it is worth buying this tablet not.


many thanks!

---

### Post by Dj_Whitelion on 2011-04-12
Hi.
 
I think this tablet is a good tablet.
And its esey to install ubuntu on it. So the instal is no prob. 
If you have a beyboard and mouse that work over usb there is no prob with using that
while you try to get touch to work.
I did not get it to work as it shuld so i gave upp. But if you do. Please do tell how you did it. Onley bad thing i can say about the tablet in it self is that its abit hevy.
But thats okey :)
 
best Regardes
Hans Benny

---

### Post by IsraGunner on 2011-04-13
Hey guys, I have read this threat over a couple of times, and now have decided to make a forum account.

Firstly, the tablet is excellent. I CANT WAIT to put either Ubuntu, Android x86, or even Mac/iOS on it.

The only problem, is so far, Android x86 and Ubuntu are not compatible out of the box.

Is this a driver issue?

If so, would looking around in system32 in windows for a driver help? Or is it something different?

---

### Post by Israeleet on 2011-04-16
Guys, I will soon have the drivers for the screen, wifi, and bluetooth. When I do, can we make this work?

---

### Post by EvilRobot on 2011-04-18
> **Israeleet said:**
> Guys, I will soon have the drivers for the screen, wifi, and bluetooth. When I do, can we make this work?

That's great news, I may just have to buy one of these tablets now. :D

I wonder if it would be possible to put those drivers into a PPA or something to make it easier for others to install.

---

### Post by Israeleet on 2011-04-22
It's great that the drivers will help.

One suggestion though.

Please don't buy this product now. There is better stuff coming out soon, actually, there is better stuff out now, just a bit expensive. 


Wait a little bit :) I bought this on an impulse, and although it beats all your iPads, android tablets, HP slates, etc, this still has much flaws.

---

### Post by Israeleet on 2011-04-22
LADIES AND GENTLEMEN 

THE WINPAD DRIVERS!

[http://www.mediafire.com/?67qzg1q7jyefgw1](http://www.mediafire.com/?67qzg1q7jyefgw1)

Both touchscreen, bluetooth, and wifi drivers!



Anyone have any idea how we can start this?

---

### Post by let_there_be_linux on 2011-05-01
> **Israeleet said:**
> It's great that the drivers will help.

One suggestion though.

Please don't buy this product now. There is better stuff coming out soon, actually, there is better stuff out now, just a bit expensive. 


Wait a little bit :) I bought this on an impulse, and although it beats all your iPads, android tablets, HP slates, etc, this still has much flaws.

I was seriously thinking of getting this tablet because i couldnt find anything better, especially since they now have it with 32GB SSD and 2BG RAM as far as I know there arent any better tablets around. Also what are the flaws you are talking about? If you have any sugestion of another tablet that might be better that is out now or is comming out soon please let me know.

If there arent any other good alternatives that you can run ubuntu on I will propably get this one and then I would be glad to help trying things with the drivers.

By the way, has anyone tried putting ubuntu 11.04 on it yet? I know that there are a lot of new (multi)touch drivers incorperated in it standard.

---

### Post by Israeleet on 2011-05-04
Dear let_there_be_linux,

I am glad you show so much interest in this tablet. And you know, although I really wish someone would help the world winpad community get support for this, I wouldn't really recommend this tablet.

Firstly and most importantly, the battery life is terrible. It is about 3 hours, and sometimes even drops to 2 hours and 45 minutes. 

Secondly, windows 7 is FAR too heavy for the tablet. It SOMETIMES, not that often, but SOMETIMES has trouble keeping up with it.

720p HD videos are played with SUITABLE quality, but 1080p ones hardly play. Just pure terrible.


In terms of speed, the tablet is very fast (I.e. navigation through windows.)

Lastly, there is a lie with this tablet, the HDMI port isn't really HDMI. It is a vga/LAN, but definitely not an HDMI port.

---

### Post by Israeleet on 2011-05-04
Overall, this is the best thing for its price, and third best in the ENTIRE market (The Acer EP121 beats it with its Core i5 which costs $1300 and so do the motion ink tablets which cost 1000-3000 dollars).

Another problem by the way- the tablet is not "multi-touch." It is dual-touch.

---

### Post by Tripper_11 on 2011-05-08
Thanks for the linux drivers!  I've been looking for this one!!!!!
:)

---

### Post by Israeleet on 2011-05-08
You're very welcome! Acquiring them took me a ton of time and effort, glad it paid off.

Now if only someone from the Ubuntu community would notice us and help us.... the opportunities for this are great for us.

We would be able to run any Linux environment.... Ubuntu, Android, Lucid Linux....

---

### Post by koua29 on 2011-05-09
I have this tablet ( FEPAD or WINPAD ) !
you can see it at [http://www.tablette-pc.net/tablette-tactile-pc/test-fepad-tablette-windows-7/]("http://www.tablette-pc.net/tablette-tactile-pc/test-fepad-tablette-windows-7/")

I have the same problem to find the touch screen driver for ubuntu:(

WIFI = ok ( 3DSP driver )
Webcam = ok ( ubuntu 10.10)
Touchscreen = 2101:1011 ActionStar

---

### Post by Nixot on 2011-05-15
> **Israeleet said:**
> LADIES AND GENTLEMEN 
THE WINPAD DRIVERS!
[http://www.mediafire.com/?67qzg1q7jyefgw1](http://www.mediafire.com/?67qzg1q7jyefgw1)
Both touchscreen, bluetooth, and wifi drivers!
Anyone have any idea how we can start this?

Tried putting the touch screen drivers on 11.04 following the instructions in the included "SOP.doc". I then restarted, and touch sreen operation is exactly the same as it has been. The arrow can be moved but can only click some things, for some reason.
I suppose I could try installing 10.04 on the tablet and re-installing those drivers, but I doubt it would make any difference.

I'm now going to try the Wi-fi and bluetooth drivers. I'll feed back to you what happens.

---

### Post by koua29 on 2011-05-15
Hi,

I have found a solution with ENAC driver.
Look on my french blog : [http://www.tablette-pc.net/logiciel-et-systeme-dexploitation/tablette-tactile-fepad-sous-linux-ubuntu/]("http://www.tablette-pc.net/logiciel-et-systeme-dexploitation/tablette-tactile-fepad-sous-linux-ubuntu/")

touch work fine (single touch) on Ubuntu 10.10 with FEPAD or WINPAD (it's the same tablet )

---

### Post by Nixot on 2011-05-17
> **koua29 said:**
> Hi,

I have found a solution with ENAC driver.
Look on my french blog : [http://www.tablette-pc.net/logiciel-et-systeme-dexploitation/tablette-tactile-fepad-sous-linux-ubuntu/]("http://www.tablette-pc.net/logiciel-et-systeme-dexploitation/tablette-tactile-fepad-sous-linux-ubuntu/")

touch work fine (single touch) on Ubuntu 10.10 with FEPAD or WINPAD (it's the same tablet )

There is one fatal flaw with this: you have to first use apt-get install to get the drivers, but wi-fi doesn't work as there are no drivers for it. I can't build the wi-fi drivers because build-essentials isn't installed, and I can't install that because wi-fi does not work! Do you have any suggestions on how to work my way out of this vicious circle?

---

### Post by koua29 on 2011-05-17
With my tablet (FEPAD), i have an adaptor for the ethernet connexion and the driver is already in UBUNTU.
I use this ethernet connexion to have internet and to install the ENAC driver.

you can see the ethernet adaptator in this vidéo : [http://youtu.be/XcS-1OggHnI](http://youtu.be/XcS-1OggHnI)

---

### Post by Nixot on 2011-05-18
I have one of those. I'm going to acquire an Ethernet cable and get the drivers that way. I'm so dependent on wireless I forgot about wireful!
I'll report on how it works once I try it out.

---

### Post by koua29 on 2011-05-18
nice,

after the touch and the wifi , i recommend you to install florence.
It's a good virtual keyboard.

---

### Post by Nixot on 2011-05-19
Well I tried cloning that got thingy, and it responded with "remote HEAD refers to nonexistent ref".
I'm going to try it with Ubuntu 10.10. I'll try and report back.

---

### Post by koua29 on 2011-05-21
look here, a vidéo of the FEPAD's tablet with Ubuntu 10.10

[http://www.tablette-pc.net/tablette-tactile-pc/tablette-tactile-fepad-winpad-sous-linux-ubuntu-10-10/]("http://www.tablette-pc.net/tablette-tactile-pc/tablette-tactile-fepad-winpad-sous-linux-ubuntu-10-10/")

---

### Post by Nixot on 2011-05-22
500 internal server error.

- EDIT - OK, well it is working now - will re-edit after watching.

---

### Post by Nixot on 2011-05-22
I've got the touch screen working now, it's great!
Any idea, however, on how to get a right click? Holding my finger down doesn't work, whereas it does in Windows 7.

---

### Post by Nixot on 2011-05-23
Apologies for the triple post, but everything is now working.

Got hold-down press right click to work. I also managed to install Florence and get an on-screen keyboard for login and lock screen. You have to disable focus grab and dimming to use the on-screen keyboard in gksudo.

All that is needed now is to add Florence and the 3dsp radar thingy to startup applications, and disable requiring the root password for the wifi radar.

 I feel it would be good to create a guide on how to get the tablet fully set up. Do you mind if I use the instructions on your French website, but translated to English? (I will, of course, link to the source).

---

### Post by Tripper_11 on 2011-05-23
Forgive me for my ignorance, but I only speak English and Spanish (now nothing about French except for a few expressions).  Mind if anyone make a tutorial in English how to install Ubuntu with a working touch screen?

Google translate doesn't do justice.

---

### Post by koua29 on 2011-05-23
Nixot, yes you can publish a translation of my french tablette-pc.net' s topic if you link the source.
You can also use my vidéo.

thanks for your work, if you have the time post a comment (en english) in my blog to give the link. :)

---

### Post by Nixot on 2011-05-23
> **Tripper_11 said:**
> Forgive me for my ignorance, but I only speak English and Spanish (now nothing about French except for a few expressions).  Mind if anyone make a tutorial in English how to install Ubuntu with a working touch screen?

Google translate doesn't do justice.

Yeah, I'm working on one right now in fact. I'll link you to it once I'm done.

---

### Post by Nixot on 2011-05-24
**I HAVE MADE THE ENGLISH GUIDE**
it's not done yet.

[http://www.nixot.x10.mx/index.php?name=p07]("http://www.nixot.x10.mx/index.php?name=p07")

 - koua29: I've also added a link to your blog, in a comment. Thanks for all your findings! :)

---

### Post by Israeleet on 2011-05-24
Sir, with all honesty, I'd like to thank you on behalf of the entire P07 tablet community.

Thank you very much.

I will definitely give this a shot!



Could this same process work with perhaps..... Android? ;)

---

### Post by Nixot on 2011-05-25
Hmm, maybe - there are drivers for android it appears in the git thingymabob, but there'd be all sorts of things like improper standby and inability to rotate the screen and no menu/back/home buttons, etc. To be honest I don't think it would be worth it - especially when you can now run Ubuntu on it. I'm going to focus now on optimizing Ubuntu for this tablet.

---

### Post by Tripper_11 on 2011-05-27
@nixot and kuoa29

nothing else to say but thanks!  that's sweet!

Ubuntu Netbook Release now works on my p07 as if factory installed!   :guitar:   ROCKS!

---

### Post by koua29 on 2011-05-28
cool !
do you know good tactile software for ubuntu ?

---

### Post by let_there_be_linux on 2011-05-29
@ Israeleet:
Even though Android runs on the Linux kernel, most comparisons end there. I am not very familiar with Android, but I dont believe it is debian based, hence any ubuntu techniques wouldnt work. Also I believe Android lacks a terminal in which one could actually enter the comands to install the drivers, but for that I am not familliar enough with Android.
Also I dont quite understand why one would want to put Android on this tablet, there are many tablets around that are much cheaper and run Android fine. This tablet has netbook hardware and thus its alsmost a waste not to run a computer OS on it.
If you do want to get Android to work on this tablet I sugest you try another forum, im sure there are a lot of android forums out there.

@ Nixot:
Your guide is awsome, very comprehensive for the most part. However i have a few tips. 
In step 3.5 you are giving options where to install the grub, you are talking about a microSD card here that you havent mentioned before, also it is unlear where you install ubuntu afterwards, on the SSD or on the MicroSD?
In step 5 you rename the bluetooth driver for ease later, this is indeed easier if you dont know that you can autocomplete a filename of directory with TAB.
In step 6 when you install florence, there is an easier way to do that. I wanted to see what it looked like on my laptop, and i just installed it from synaptic package manager. (And indeed its quite awsome)

Please dont think I'm criticizing, just trying to help!

p.s. I hope your stat exam goes/went well (not sure which thursday you were refering too.)

I cant wait to get started on mine, but thats gonna have to wait two months, no time until then.

---

### Post by Nixot on 2011-05-30
> **let_there_be_linux said:**
> 

In step 3.5 you are giving options where to install the grub, you are talking about a microSD card here that you havent mentioned before, also it is unlear where you install ubuntu afterwards, on the SSD or on the MicroSD?

Right, OK. Whenever I say microSD card or USB drive there I mean external drive of any sort. I suppose I should make that more clear. In the test run that I used to make the guide I installed Ubuntu on a USB stick but installed Grub on the SSD. I'll use in my serious run a better way (installing Ubuntu and Grub on the USB stick and getting the Windows boot loader to show a choice between booting the SSD or the USB stick), and update the guide accordingly.


> 
In step 5 you rename the bluetooth driver for ease later, this is indeed easier if you dont know that you can autocomplete a filename of directory with TAB.

Yes but - halfway through when you need to sudo the installation sh if you just write "sudo ./Install_3DSP.sh" it says "command not found", so I had to write the absolute path name "/home/nixot/bluew/Install_3DSP.sh" in order to get it to work. Could I tab-complete the bluew folder name if it is complete by typing in "/home/nixot/bluew" and pressing Tab?

> 

In step 6 when you install florence, there is an easier way to do that. I wanted to see what it looked like on my laptop, and i just installed it from synaptic package manager. (And indeed its quite awsome)

That is what I tried first. sudo apt-get install florence -> "E: unable to locate package florence"

> 
p.s. I hope your stat exam goes/went well (not sure which thursday you were refering too.)


I did the exam last thursday. It went very well, thanks :D

---

### Post by Nixot on 2011-06-03
I've been trying to get the enac drivers for a new install, and every time I do "git clone git://git.lii-enac.fr/linux-input/enac-drivers" it responds with "fatal: the remote end hung up unexpectedly". Without this I won't be able to get the touch screen working. Any help please?

Actually, I fixed my problem by using the enac folder I prepared eariler (lol blue peter) from the other USB drive I installed it to during the test run I did to make the guide. If anyone else is having the same problem I'll upload the folder to here.

The guide has been updated! Now the finishing touches part had been made and some other bits have been updated.

---

### Post by koua29 on 2011-06-08
i think that you can use :
git clone git://git.lii-enac.fr/linux-input/hid-multitouch

---

### Post by let_there_be_linux on 2011-08-05
Hi Nixot (I hope your still subscribed to this thread)

I have finally gotten time to order and install my tablet. Unfortunately I'm having some trouble and I was wondering if you could help.

Firstly your website isn't working anymore :( it was really good!

Secondly I'm also having the problem with: every time I do "git clone git://git.lii-enac.fr/linux-input/enac-drivers" it responds with "fatal: the remote end hung up unexpectedly" just like you were having. koua29's tip unfortunately didn't work either.

And finally i installed the wireless drivers successfully, but when i connect to my network it says it's connected, and I can ping to google but i cant visit anything on the internet (like google)

You said that you might be able to upload your folder for the touch driver, that would be great! (I think I can sort the rest out with a bit more time)

thanks!

---

### Post by Nixot on 2011-08-09
Hey there...

...I got your message let_there_be_linux, and I'll respond to it here: yes, my website is indeed down because I went on holiday for two weeks and the inactivity limit kicked in. I'm trying to sort that out.
Sorry for my inactivity by the way, I've been focusing on other things like PSP modding and open source handhelds. I do have a habit of community hopping, but I sometimes leave a few people behind in the process.

And as for the touch screen drivers, I discovered I could use the already compiled ones that I tried on a previous installation so I'll find my previous installation USB stick and upload them to my website (or perhaps a better file host!) and change the instructions a bit.
They will be up by tomorrow. Speak to you soon. :)

---

### Post by Nixot on 2011-08-10
OK, I have updated my website and it now contains an extra bit under section 4 with a link to a zip file containing all the files you should need. Let me know how it works out. :)

---

### Post by mightybuddha on 2011-08-10
> **Nixot said:**
> OK, I have updated my website and it now contains an extra bit under section 4 with a link to a zip file containing all the files you should need. Let me know how it works out. :)

OMG!!! Thank you!  i'm not using this particular touchscreen but i've been trying to get my touchscreen working for weeks and the enac drivers you uploaded did the trick! THANK YOU!

---

