---
title: "Official Hp Dv9000 Laptop Thread!!"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by EXCiD3 on 2007-05-03
**MAKE SURE YOU READ [Howto: Ubuntu on HP dv9000 series laptop]("http://ubuntuforums.org/showthread.php?t=512059") thread before posting questions here!**


Post here if you have any questions on installing Ubuntu on an HP DV9000 laptop. I currently have Ubuntu 7.04 running pretty well. The only things I haven't tried are: Microphone, card reader, express card, and I HEARD that the webcam CAN be used. Post any questions, problems, comments, ideas or whatever about your DV9000 here! :)

---

### Post by Paulo79 on 2007-05-04
Hello,

I also have a DV9000t. Does suspend (to RAM) and hibernate (to disk) work for you? Did you have to patch your kernel or change any configuration?

And what about the (FN + vga output) key combination, needed when you have a projector attached to your laptop? This key combo will either crash X or the whole system (kernel) in my Kubuntu 6.10. Hope it has been fixed in 7.04.

The camera works with the drivers found at [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

Also, have you tried the s-video TV output? I does not work for me in Windows either. HP's support is horrible!

Thanks,

Paulo

---

### Post by Grungydan on 2007-05-04
I'm running Feisty on a dv9000t as well.  I don't have anything to add at the moment, other than that the nvidial drivers and Beryl both installed absolutely perfectly and I haven't had any major issues yet.

I have also not used the mic, camera, card reader, or video outs yet.

edit:  Actually, I did just think of one issue I seem to be having.  The battery monitor doesn't seem to "keep up" with actual battery power/time as well as the one in XP.  Admittedly, I haven't done any searching on the issue, yet.  Anyone else noticing this?

---

### Post by Paulo79 on 2007-05-04
HP's website says you should calibrate your battery every three months by (1) disabeling WinXP's power management; (2) letting your computer on until your battery is out of charge; (3) doing a full recharge; and (4) re-enabling power management.

I never did that though and don't know if it makes a significant difference. Please let me know if you have tried id. Also, there are a couple of BIOS patches that may help, although I don't remember what they are supposed to fix (Win Vista issues?). I do remember one of them added an option for enabling the virtualization features of the Intel processor.

Cheers,

Paulo

---

### Post by Grungydan on 2007-05-05
I probably should calibrate my battery again soon, but I don't think it has quite been 3 months since the last one.  I will try it and see if it changes anything.  (Though not right now.  Busy trying to get the webcam going. :))

---

### Post by EXCiD3 on 2007-05-07
I just recalibrated my battery, but have not had a chance to see whether it helped my batter life or not. I have had my HP since December.

---

### Post by teaker1s on 2007-05-07
hi guys I started a dv6000 wiki page that may help
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e")

---

### Post by EXCiD3 on 2007-05-07
Nice thanks for the help. I would like it if we could get the entire HP dv*000 series running extremely well. I would encourage people to buy an HP DV9000t if they want a good linux/windows compatible laptop. PC World's latest issue gave this laptop #1 place for their Windows Vista compatible laptops. That means the laptop will be plenty powerful for anything you could need AND most importantly it is extremely compatible w/Linux! ;)

---

### Post by JHSaunders on 2007-05-07
To get the webcam working follow the instructions [here]("http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/"). They are for the DV200 but work for the DV9000.  You will need to install subversion, but its very easy. I have tested it with ekiga, but I know that some Apps will not work with it, like camorama.

Has anyone found out how to get the Mic working, its the last thing that isn't working on my system.

---

### Post by EXCiD3 on 2007-05-08
Ok, so i was trying to play CounterStrike 1.6 the other day. I was going through the settings and wondered what it would do if i tested the mic. IT WORKED! It was pretty slow in responding and came out kind of noisy. It didn't work perfectly, but at least I got feedback from it. NOTE: I have done nothing to try to configure it so far. It seemed to work right out of the box. I am going to install Audacity and see what kind of recordings it can take.

Wish me luck! ;)

---

### Post by Grungydan on 2007-05-08
> **JHSaunders said:**
> To get the webcam working follow the instructions [here]("http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/"). They are for the DV200 but work for the DV9000.  <snip>

Thank you for the link.  I'll give that a shot when I get a chance. :)

---

### Post by Grungydan on 2007-05-08
A quick update, the headphone jack auto-mutes the laptop speakers, and the output works perfectly.  Still having a weird issue with volume not being "right".  With alsa mixer open, turning down to about 1/3 is nearly inaudible.  Down to 1/4 and it's as though the system were muted.

As an aside, Ubuntu automatically detected my HP 6122 Desk Jet, and prints just fine.  Awesome.

---

### Post by EXCiD3 on 2007-05-09
> **Grungydan said:**
> With alsa mixer open, turning down to about 1/3 is nearly inaudible.  Down to 1/4 and it's as though the system were muted.

I have noticed the same problems with my audio being ridiculously quiet. I think I may have fixed it...I don't remember. I'll post back if I can remeber what I did...

---

### Post by EXCiD3 on 2007-05-10
OK, I think I may have figured out the sound problem. See, on the GNOME sound icon in the tray (next to the time) I have the sound set at about 2/3 up. I noticed taht when I change the sound with the touchpad volume thingy, it does not change the volume in GNOME. I thought it did, but that meter stays the same. Also Rythymbox (or any other media player for that matter) has its own volume settings. Unfortunately one of them might be set low and that is why the volume is not as loud as it should be. My headphone jacks and built in speakers seem to be playing fine now.

---

### Post by blackdevil on 2007-05-10
I attached laptop to hardline and it says its connected, but no IP is listed and no internet functions operate properly... help

---

### Post by Brightbelt on 2007-05-10
Thanks for this thread. I have an HP dv9030us laptop and I would have never tried putting Ubuntu on it without seeng that others had succeeded. I just recently put Ubuntu onto an old Gateway M675x laptop merely for experimentation - I set it to dual boot with Vista. And I could not get the wireless to work on the Gateway, but with the HP dv9030us, the wireless works like a charm, and my email works as well. 

Btw, I set the HP laptop to dual-boot Ubuntu & XP and I let Ubuntu do the partitioning during the install and things went just fine. A couple of things: Ubuntu did say that it's having to use a non-supported driver for the video card and I have not tried my Dvd-rw as yet nor the web cam. 

Thanks again for the thread,...Frank

---

### Post by EXCiD3 on 2007-05-11
> **Brightbelt said:**
> A couple of things: Ubuntu did say that it's having to use a non-supported driver for the video card and I have not tried my Dvd-rw as yet nor the web cam. 

Thanks again for the thread,...Frank

The non-supported driver just means that the driver is proprietary and conflicts with Ubuntu's idea of having only "free" software. They realize that the nv driver is not really good at 3D yet so they have integrated the Restricted Drivers Manager to remove many of the troubles of installing Nvidia's proprietary driver (trust me, its very nice to not have to do anywork yourself). 

Your DVD burner should work just fine and there is a post earlier in this thread about installing the webcam drivers. I personally ahve not had time to try this, but *hopefully* this weekend i will find some time... hopefully...

I thought it would be productive to have 1 thread to talk about all the HP dv9000 laptop problems, ideas, comments, etc.

Come and see us again!:)

---

### Post by 3rods on 2007-05-13
Have either of you been able to get the hibernate and/or suspend functions to work? My dv9000t won't hibernate or suspend properly. 

I'm running 7.04 with the restricted nvidia driver (and intel wifi lan driver).

2.0Ghz C2D 
2GB RAM
100GB x 2 SATA 7200rpm
Go 7600 512mb

The rest is your standard fare.

---

### Post by Grungydan on 2007-05-13
I wasn't able to suspend properly.  It went into suspension, and responded to the touchpad as a wakeup call, but when it woke up, my desktop was the size of a postage stamp.  :)  I had mouse control, etc, but I couldn't see anything so I restarted.  

I haven't tried to hibernate yet.  

Personally, I rarely used either function anyway, so I'm missing much.  I do hope everyone is able to get it worked out though! 

I haven't tried the steps for the webcam listed in the other post yet.

---

### Post by 3rods on 2007-05-14
I use hibernate all the time so I'm hurtin'. 

Are you using the restricted driver or the ubuntu one? I find I get a little further with the ubuntu driver, but I don't get the fancy beryl effects either so... Either way though, it won't resume. 

This is the only thing that makes me keep the other HD for Vista 64. 

P.S. Vista is garbage. If it wasn't for games, I'd dump it altogether.

---

### Post by EXCiD3 on 2007-05-15
The only reason i still dual boot is because i play games sometimes. I'm using the restricted driver because of the opengl support that the nv driver does not have. I enjoy having Beryl, but i keep reinstalling ubuntu because i usually mess it up pretty horribly (im still fairly new).

---

### Post by boggyUMI on 2007-05-19
for some reason when I tryed to install ubuntu 7.04 and debian 4.0 etch neither of them could load gui the screen just goes all silverish. i'm not going to try suse or redhat even tho they might work i need debian. I tryed solaris 10/11 they booted gui fine but nothin really worked so that was a lost cause.. i'm not sure what the problem is i guess neither distro can probe the video? any sugguestions would be great thanks

---

### Post by 3rods on 2007-05-19
Are you using a dv9000t or a dv9000z? My 9000t worked out of the box; including video. I did have to download a post release iso because the beta version wouldn't load the gui.

---

### Post by old_salt on 2007-05-19
**This post could be related to an Ubuntu bug filed at**: satisfied. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				DV 9000z

Pretty much everything works. Took me 1 day but most all is well. Wireless was an absolute pain. Not sure why Linux in general is so far behind in getting this to working like anything else. I guess everyone wants all the eyecandy instead of ease of install and configuration.

NOTES

To install or even bootup
- Use the noapic noirqdebug uptions to the boot parameters. My system hung without it during boot.

Wireless
- I used this link to get my wireless working. It shows it's for a Dell however it worked when everything else wouldn't. NDIS wouldnt work. I guess because the firmware wasn't or wouldn't load ? Anyway I'm using the " sudo modprobe bcm43xx" to activate this after each boot.

[http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946)

Lightscribe .
- unable to get the software for this however I just boot to Winblows to use this when needed temporarily.

Webcam
I know the microphone works as is however I plan to follow some links posted in this forum to give it a try.

LMSENSORS
I followed the Ubuntuguide steps and everything works. Gkrellm works perfectly.

Videos / DVD's
BEAUTIFULL

Keyboard 
-hot keys like the sound and dvd menu things. Volume works however DVD functions do not. Oh well not that big of a deal.

Media Reader
- Works out of the box. No problems whatsoever.

Printers
- I have an HP Photosmart 8450. Works but the print area is off. It starts printing twice the distance down from the top edge thereby cutting off the bottom of the printout. Side to side centering is fine. If anyone knows of a fix for this I would appreciate it.

Overall I'm very satisfied.

AMD 2.2Ghz Dual Core, 2Gb RAM, 160Gb HD, Lightscribe D/L DVDRW

---

### Post by boggyUMI on 2007-05-20
I'm not sure if it's the t or z but NOTHING works on this junk. I'm not happy at all i've tryed alot of different solutions and overall I get the same result no gui.

---

### Post by scunc_dvl on 2007-05-21
I am using Ubuntu Edgy. I have three (four?) issues with my late dv9000 


Has anyone noticed this error in dmesg: *[   40.572671] **vbetool**[3702]: segfault at 0000000000003632 rip 00000000004246a4 rsp 00007ffff740c950 error 4*
I'm also noticing inconsistencies - my lid does seldomly lock my sessions, but I really want Linux to do it all the time - that may be related to vbetool crashing but I haven't looked much into it yet.

------

The **modem** (DSL / analogue) I can confirm isn't supported, yet. In WinXP I can confirm (with some rough help from scanModem) the Intel thingy really had a conexant chipset (Using Device Manager to actually look at the modem and its driver).

Linuxant.com will probably have to support this driver... Or else..perhaps kinternet (a SuSE package) would do the trick.

I think there's a file that tells you if you have the conexant chipset
$ cat /proc/asound/card0/codec#0
[INDENT]
Codec: Generic 14f1 ID 5045
Address: 0
Vendor Id: 0x14f15045 (...is an "HDAUDIO with SmartCP")
Subsystem Id: 0x103c30bb
Revision Id: 0x100100[/INDENT]

------

Lastly, I hear Alsa 1.0.13 is needed for the headset port to work, and Edgy has Alsa 1.0.12, so I'd need to compile a whole new Alsa to get the port working.

Oh and I haven't tried the wireless yet :P dmesg seems to detect the hardware, I have a feeling it may need some tweaking.

I guess I'm satisfied with this laptop except for my ACPI/vbetool flakiness..Heh

---

### Post by EXCiD3 on 2007-05-21
You ought to just upgrade to Fiesty. The functionality it adds beats out all the previous versions and you dont have to update any software as almost everything works out of the box.

---

### Post by sambahat on 2007-05-21
Does anyone have any ideas on how to get the HP ExpressCard to work?  It's made by Hauppauge but i've had no luck with drivers (videodev, ivtv, etc) so far.

---

### Post by scunc_dvl on 2007-05-22
> **EXCiD3 said:**
> You ought to just upgrade to Fiesty. The functionality it adds beats out all the previous versions and you dont have to update any software as almost everything works out of the box.
I'll look into upgrading now. :)

---

### Post by EXCiD3 on 2007-05-22
> **scunc_dvl said:**
> I'll look into upgrading now. :)

Let us know how it goes. If you have any problems, message me, post back here, or contact me on AIM or something.

---

### Post by DShepherd on 2007-05-22
This got my sound working.. well the voluming adjusting is still weird but i guess i can work with that for now
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

I got my video camera to work by using the uvcvideo driver.  My camera only seems to work with ekiga and nothing else. I am aware that the uvcvideo only supports v4L2 and I think uvccapture and lucview should support it too but they dont work. Has anyone else had this problem??

---

### Post by blackdevil on 2007-05-22
Old Salt. Thank you so much, that link you posted up for the wireless finally got it working. I have tried a ton of others using ndiswrapper and nothing worked. Thanks alot for that. Now only to get the video drivers updated, web cam, mic....

---

### Post by stchman on 2007-05-22
My dad got a dv9233CL and I installed Feisty on the 2nd hdd (about 14G)

Everything I tested worked just fine

Video (with restricted driver install for Go 7600)
Intel Wireless
Chipset (I believe it is a 945 chipset)
Sound (even the sound slider worked)
Remote
Ethernet
I can burn CDs and DVDs but have not tried the lightscribe feature
USB ports
Plays DVDs and audio CDs perfectly
Plays MP3s

I have not tested these:
Webcam
Microphone on laptop lid
Microphone jack
HDMI output (I believe Fcn - F4 switches display)
S-Video out
Firewire (they should work)
Suspend or Hibernate (dad never uses these anyway)
Digital sound input next to headphone jack
Headphone jack (should work)
Media slot (from what I have read it works out of the box)

All in all it seems the necessary stuff works just fine.  Let me know if anyone else has tested the other stuff.

---

### Post by m1e1w1 on 2007-05-25
i will be referanceing this thread alot.... seems to have almost everything i might have a problem with with a fix accept i couldent find this:

ubuntu 7.04/vista premium dual boot

installed ubuntu, but wont boot from hard drive. vista boots fine.
i posted this with more detail at:
[http://ubuntuforums.org/showthread.php?t=454012](http://ubuntuforums.org/showthread.php?t=454012)

i posted here with this to see if i can get some help fixing it.

---

### Post by EXCiD3 on 2007-05-25
Dual booting Vista and Ubuntu 
A couple of weeks ago I set up my laptop to dual boot between Vista RC2 and Ubuntu. There are a few tricks to getting both operating systems to work together that I thought I would share.


Install Vista first. Set up your Vista partition and leave the space you are going to allocate to Ubuntu free.
Once you are happy with your Vista installation, put in the Ubuntu bootable distribution. Install Ubuntu (remember to allocate a partition for SWAP!). 
As of Ubuntu Dapper Drake, Vista won&#8217;t be detected. When you reboot, you&#8217;ll go straight back into Ubuntu and Vista won&#8217;t be a boot option. Don&#8217;t panic, Vista is still there, you just have to do a bit of mucking about.
In Ubuntu, you&#8217;ll need to edit the file /boot/grub/menu.lst. To do this you&#8217;ll need to use sudo to grant your account admin privileges. 
You&#8217;ll need to make the following changes:
Set timeout to 30 (this will give you time to review the menu)
Under examples, edit the Windows example so that it appears as follows

title      Windows Vista
root      (hd0,0)
makeactive
chainloader +1
Once you&#8217;ve done that, the next time you reboot you&#8217;ll get the GRUB bootloader allowing you to choose between booting Ubuntu or Vista (Vista will be the default)

Taken from: [http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx](http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx)


Let us know if this works ;)

---

### Post by m1e1w1 on 2007-05-25
yes, that worked out great. made a few modifications to the setup, but the code worked as intened

---

### Post by lexarrow on 2007-05-26
For sound related problems maybe [this]("http://ubuntuforums.org/showthread.php?t=455147") could help

---

### Post by EXCiD3 on 2007-05-26
Thanks for the help lexarrow, however I am fairly certain that Feisty fixes most audio problems as it has one of the most recent ALSA's.

---

### Post by Rascal555 on 2007-05-26
I installed 7.04 Fiesty on my dv9260us

Working

Video with the restricted driver installed
Intel Wireless worked from the install
Sound  worked from the install
Remote  worked from the install
Ethernet  worked from the install
USB ports  worked from the install

- Suspend resumes properly with restricted driver, or to a postage stamp size desktop without.
-  Hibernate resumes properly with restricted driver, but sound and controls for sound cease to function until reboot.
- I have not tried my tv tuner yet, but I suspect it will need a new linux driver as well. 
- I installed the R5u870 driver for the HP Webcam.  The new aMSN works, but my webcam blue light flashes!  Help would be appreciated!

So far I'm pretty impressed with Ubuntu!  I will continue to check the posts and will add what I find.  This is a very helpful forum, thanks everyone.  I can't see Microsoft lasting too much longer..do you?

---

### Post by rfrey74 on 2007-05-26
I chronicled my install experience with an HP dv9000z.  I have had great success in getting it working using Feisty.  You may view it here: [http://ubuntuforums.org/showthread.php?t=433881](http://ubuntuforums.org/showthread.php?t=433881)

---

### Post by old_salt on 2007-05-27
I posted earlier but an update.

Most everything I see posted relates to Ubuntu and not Kubuntu however I've managed to work some things out. 

After my initial post, I played around (Tweak it till it breaks) last weekend.

ITEMS OF INTEREST

DV9000z
- AMD 64 Core Duo 2,2Ghz
- 2Gb RAM
- 160Gb Hard Drive
- nVidia 6150
- Lighscripe D/L DVD/RW

Kubuntu 7.04 32-bit (I know, why 32bit on 64bit HW? Because I have a 64bit Desktop and I didn't want the constant hassle of ongoing issues surrounding the 32bit Browsers and plugins, printing etc. Stinking Adobe and Sun - Gnash doesn't work either).

I have most everything running just fine after a few days of work. Yes the media reader does work and very well I might add. The HPLIP also works great and much appreciated considering this is the #1 printer manufacturer in the world. Function keys work, Keyboard options like the DVD, Volume etc all work fine. My remote control even works as well. I do not have a Bluetooth device to test with so I cannot comment on this. 

ITEMS NOT WORKING

- WebCam

Tried some things and it sorta worked however there really isn't a good application to test this. Sorta means it worked and then it stopped working after a few test runs. I've been hesitant on such a nice final build to play around and risk forcing a reload.  

- Power Save Features (Hibernate, Suspend, Shutdown)

Nothing works. System locks up claiming PCI errors. screen locks up and a power reset is required. To be honest, I have yet to find ANY Linux distro with working power features. I would think this would be something the entire community (all distro's) would be feverishly working on given it's importance especially on laptop units..

- Lirc

Lirc reminds me of something from the dark ages. I've reviewed all I can find about it and I can't believe a technology as mature as IR isn't just supported "Out-of-Box" like Windows or MAC. I didn't have the heart to attempt the days of manual editing and configuration just to get this working. Ubuntu could win a lot by making this seamless.

- Lightscribe
I tried the apps directly from the Lightscribe site and I saw where they are having some issues getting their software to work on non-rpm based systems. Unfortunately they don't post source code for a manual install. I have Automatix and tried that as well and it doesn't work. View the files and you will see it was converted from the posted rpm's using Alien which I had already tried earlier before the Automatix route. Maybe in about 2 years it will be available ? 

SUMMARY
 Wireless took a while to get going with Ndiswrapper. Still unsure why wireless requires manual startup to connect. Once again; Windows and MAC are seamless with this and will auto-connect at bootup. I see Sony and IBM listed in the KDE Options for special setups for mapping keys etc yet these models are not the most popular. 

My recommendations to Cannonical
- work on the Power features for everyone. Get this to working and you will be the first Linux Distro to achieve this feat. This alone would garner a tidal wave of new users including corporate and businesses.Oh and it has to work in all flavors not just the Gnome UI.
- InfraRed for laptop users is my next area. It's an important feature on a laptop however I know desktop users will appreciate this equally as well and once again this would drive more users to this platform.
- Wireless on laptops for the most part has come built-in for several years. There can't be too many different chipsets to warrant a seamless integration to the standard install. 

Is there a way we could split this Forum to listing "How-To's" specific to this platform? I believe the fact finding has been successful here and after reading through, everyone has a good idea of what does and doesn't work and can determine which ones are "Hot Items". I see where some including myself have successfully resolved some issues but the instructions need to be posted and organized properly. I don't believe this forum is the correct place for that.

Tony

---

### Post by lexarrow on 2007-05-27
> **EXCiD3 said:**
> Thanks for the help lexarrow, however I am fairly certain that Feisty fixes most audio problems as it has one of the most recent ALSA's.

In general, that's true but I've been waiting for 2 months for alsa to release something that would fix my sound problems and the patch in the [howto]("http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000") is not in the last version of the driver (it's true that is still a rc release).

If you have a specific sound problem (mic, jack, etc. not working) search for a patch that fixes it and apply it to your drivers. You are most likely to find a patch for a bug [here]("https://launchpad.net/ubuntu/+bugs")

---

### Post by Bladez0r on 2007-05-28
Hi there, I have just purchased a dv9000 series notebook and after I saw a video of Ubuntu with XgL, Beryl & Kiba-Dock I fell in love with it and wish to ditch Vista ;) . I am completely new to Ubuntu and cannot find any installation guides or whatnot to do this lol. Any help would be greatly appreciated :D.

System Specs:
AMD Turion™ 64 X2 1.8ghz
2GB DDR2
NVIDIA GeForce Go 6150
120G Sata HD
LightScribe DVD±RW
802.11b/g WLAN
Altec Lansing Sound
Webcam and Mic

---

### Post by m1e1w1 on 2007-05-28
can you give us your dv9000 specs?
AMD ? is it a 64 bit processor? start with that, so you know what version if ubuntu to get. id suggest 7.04 for AMD 64
youll need a CD-R. you have the same as mine, so i can help you with it if you need, youll need to be absolutly sure you want to remove vista. i dident. i dual booted, its safer incase you have a major problem

---

### Post by 3rods on 2007-05-28
> **Bladez0r said:**
> Hi there, I have just purchased a dv9000 series notebook and after I saw a video of Ubuntu with XgL, Beryl & Kiba-Dock I fell in love with it and wish to ditch Vista ;) . I am completely new to Ubuntu and cannot find any installation guides or whatnot to do this lol. Any help would be greatly appreciated :D.

System Specs:
AMD Turion™ 64 X2 1.8ghz
2GB DDR2
NVIDIA GeForce Go 6150
120G Sata HD
LightScribe DVD±RW
802.11b/g WLAN
Altec Lansing Sound
Webcam and Mic

I would recommend running a virtual machine first or dual booting before you dive right in to ubuntu. I have a dv9000t and the latest 7.04 x86 seems to work the best. 

There are a couple glitches/bugs with ubuntu and  the 9000; like, hibernation does not work very well (at least not for me, but I'm dual booting.)

---

### Post by scunc_dvl on 2007-05-29
> **EXCiD3 said:**
> Let us know how it goes. If you have any problems, message me, post back here, or contact me on AIM or something.

Okay, updating fixed ALSA's issues, I even got volume and mute working in KDE by using a combination of keytouch and KMix. [SIZE="1"](Using Keytouch wasn't *that* good an idea though, because it mapped my Left CTRL key to "My Computer"... Keytouch should have more keyboards in their database anyway, it wouldn't be too hard to support given everything is a scancode...)[/SIZE]

I also noted when I fired up gnome in Fiesty, it listed some alsa/oss devices related to the modem. I'd be interested in knowing if anyone has had any luck with it (it's analog+DSL apparantly, and conexant based :( )

OH and lid closure only seems to be detected by the system ONCE for every bootup, which is no good if I want my session locked automatically like so... I'd REALLY like to see that fixed.

---

### Post by Bladez0r on 2007-05-29
> **3rods said:**
> I would recommend running a virtual machine first or dual booting before you dive right in to ubuntu. I have a dv9000t and the latest 7.04 x86 seems to work the best. 

There are a couple glitches/bugs with ubuntu and  the 9000; like, hibernation does not work very well (at least not for me, but I'm dual booting.)

Thanks for that,  I have 2 hard drives both 120g so I was thinking keep vista on one and dual boot with ubuntu, as for xgl and beryl I will let you know how my first attempt goes with installing them; if anyone knows of a good guide or is there a one-off installation package? any info would be great thanks :D

---

### Post by m1e1w1 on 2007-05-29
keep in mind that vertual machine only works with vista ultimate, or xp pro. if you dont have that you still have to dual boot anyway. best option

---

### Post by EXCiD3 on 2007-05-29
dual booting is probably the easiest option. It is faster but uses a bunch of extra room. I just installed Windows Vista (just to see what its like) and i have yet to reinstall Ubuntu (probably tonight). Vista isnt too shabby, but i hate Micro$haft so it will probably only be used for gaming (?) and if i NEED hibernation/sleep mode. :(

---

### Post by 3rods on 2007-05-30
Didn't know you got the dual drives. I dual boot vista ubuntu and it's pretty easy. Vista came preloaded so I just put ubuntu on the second drive; grub handles the recovery partition, the vista boot and both ubuntus (reg & safe/recovery). 

Beryl works pretty well. I get some annoying screen flicker sometimes but it's pretty good for the most part.

I think all I had to do was a apt-get install beryl beryl-manager and I was all set, but don't quote me on that.

If you get a chance, try out mikeytag's solution for hibernation and see if it works for you, since you will have a fresh install to try it on. I couldn't get it to work, but my install is no longer "fresh". I didn't want to wipe my install just to have it not work right for me.

[http://ubuntuforums.org/showthread.php?t=394131&highlight=dv9000&page=4]("http://ubuntuforums.org/showthread.php?t=394131&highlight=dv9000&page=4")

Good luck.

---

### Post by Continental on 2007-05-31
I've got a six-month old dv9000 (dv9008nr, to be specific). It's got Windows XP Media Center 2005 installed, and I've been trying to install Ubuntu. I tried live booting several times, but that never worked. I finally got Ubuntu installed via the alt-install text-based installer, but I can't boot. I get the GRUB screen, select Ubuntu, boot, it seems to load but after the loading's done I get a black screen, or sometimes a blinking underscore-type thing in the upper left-hand corner. I've tried adding noapic and noirqdebug as suggested in some posts, but to no avail. Any help would be very appreciated... the less I have to use Windows, the better. Thanks.

edit: Totally new to this. I know very little about Linux shells, kernels, and most everything else.

---

### Post by Caste#02 on 2007-05-31
> **Continental said:**
> I've got a six-month old dv9000 (dv9008nr, to be specific). It's got Windows XP Media Center 2005 installed, and I've been trying to install Ubuntu. I tried live booting several times, but that never worked. I finally got Ubuntu installed via the alt-install text-based installer, but I can't boot. I get the GRUB screen, select Ubuntu, boot, it seems to load but after the loading's done I get a black screen, or sometimes a blinking underscore-type thing in the upper left-hand corner. I've tried adding noapic and noirqdebug as suggested in some posts, but to no avail. Any help would be very appreciated... the less I have to use Windows, the better. Thanks.

edit: Totally new to this. I know very little about Linux shells, kernels, and most everything else.

When appear to you the blinking underscore, try to press **Ctrl+Alt+F1**, log in and then give **startx** ;)

---

### Post by Continental on 2007-05-31
Ok, I gave it a try. I saw some text for just a second (I thought I saw the word "starting" too) but then I got the black screen again. I'm wondering if it could be a display problem. Never did get to any log in screen either, though.

---

### Post by crazy25000 on 2007-06-02
Hello, 

I have a DV9207US and im trying to find a driver for the HP Analog Express TV Tuner. Can anyone point to a link please. I cant seem to find it anywhere. I have Ubuntu 7.04. 

Thanks

---

### Post by old_salt on 2007-06-03
Okay, here's something I've not seen a post about. Under the 64bit Kubuntu 7.04 flavor on an HP9000z;

Has anyone tested to see if they can add a printer? I've had no issues on my 64bit desktop but I loaded up the laptop and under

System - Settings - Printers

When trying to add a printer, it just hangs there forever. I've even let it run overnight. Nothing still the spinning clock.
Any ideas anyone?

Thanks
Tony

---

### Post by EXCiD3 on 2007-06-03
I have a HP 3180 printer that i bought with my DV9000t and it was detected just fine.

---

### Post by tacklebox28 on 2007-06-03
Alright, So I bought the HP DV9000 about a month ago, and I have had nothing but problems with the webcam that is built in, I just got off the phone with Hp, and they made me reinstall the software for the webcam, that didnt work, so they tried getting to me download the new driver for it, pretty much was replacing it....So we did that over the phone and still no luck


Now they are telling me I have to reformat my computer, when there is no way in hell i should have to, The computer is brand new, Any suggestions, or anyone else had the same problems. if so would love to know if there is a better way to fix it..

I paid alot for this computer, and I expect it to work properly..

my friend also bought the same laptop a few weeks before me, and seems to be having the same trouble, so  maybe a problem with the Hp Software?

---

### Post by EXCiD3 on 2007-06-04
tacklebox28,

Are you running Windows Vista? I'm currently running Vista at the moment and i dont really know if the webcam works. I had trouble installing Vista with the HP DVD's that they mailed me (i bought my laptop just before Vista was released so I qualified for a free upgrade to Home Premium and I hate it).

I would probably recommend reinstalling Windows so that your copy is not screwed up. Unfortunately they use a special SATA controller that cannot be detected by a regular copy of XP so that option probably would not work. I would recommend using XP over Vista as it is much more reliable...however you would need to incorporate the drivers in a "special copy" of XP. I was fortunate enough to get it before Vista was released ;)

Paulo79 post a link to this Webcam Driver for Linux: [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)
I dont know if this will help you or not.

---

### Post by diablo75 on 2007-06-07
I'm trying to install Ubuntu on a DV9000 and I'm running into a problem with the partitioning tool.  I am wanting to do a dual boot setup.  Currently (according to Computer Management>Storage in windows control panel) there are three hard drive partitions shown:

1. A 1.00 gig partition that has no name, but says that it's NTFS.  It has no drive letter.
2. The system partition, C:
3. An 11.49 gig partition, HP_Recovery, drive letter is D:

When I run the live CD,  gparted doesn't know what partition to select to resize.  And I don't know how to make my way around the Manual gparted controls, but I am wanting to resize the 2. (System) partition, and install Linux on it's own partition.

Can this be done without deleting any of these other partitions?  I just want to resize the C:.

---

### Post by EXCiD3 on 2007-06-07
If you have burned off the Recovery disc's (or purchased them) you can go ahead and delete the HP_Recovery partition and/or the 1GB NTFS partition (this partition contains the embedded copy of windows that is used to play DVD's or CD's only). I would recommend removing these paritions, mainly because you can restore your OS if you have the recovery discs and i found the embedded copy of Windows pretty much useless (after all you could just boot into Windows and watch movies/listen to music AND do other stuff.).

If you would like to just resize the C: partition, click the partition in GParted and choose "Resize/Move" from the menu as follows:
[IMG]http://gparted.sourceforge.net/larry/resize/big/operations-b.gif[/IMG]

Proceed by moving the slider to create as much free space as you need for your linux partition as follows:
[IMG]http://knowledge76.com/images/Gparted_resize_partition.png[/IMG]

You will then need to create a linux partition out of this unallocated space that you created as follows:
[IMG]http://www.hezardastan.org/breezy_xp_dualboot/en/images/12.png[/IMG]

That should take care of your question. Post back if you have any other problems/questions/comments! Hopefully this thread will become the only place you need to go if you have troubles installing Ubuntu on a dv9000!

BTW, has any brave soul attempted installation of Gutsy Gibbon Alpha 1 yet? I may download it if i get some free time...;)

---

### Post by diablo75 on 2007-06-08
I used automatix to install the nvidia drivers, and this guide:

[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html)

The drivers appear to load correctly, but when I run the Beryl Manager, I get some screwy results...

The cube works...but that's about it.  If I click on a menu, it's represented by a blank black box where the menu would normally be.  The same occurs with many other windows.  The mouse will pass over the windows as though there is clickable items on the black box, and clicking works....but you can't REALLY see what you are clicking on.

Please help!

Also, How do I get wireless networking to work on the DV9000?

---

### Post by Atomic Dog on 2007-06-08
> **diablo75 said:**
> I'm trying to install Ubuntu on a DV9000 and I'm running into a problem with the partitioning tool.  I am wanting to do a dual boot setup.  Currently (according to Computer Management>Storage in windows control panel) there are three hard drive partitions shown:

1. A 1.00 gig partition that has no name, but says that it's NTFS.  It has no drive letter.
2. The system partition, C:
3. An 11.49 gig partition, HP_Recovery, drive letter is D:

When I run the live CD,  gparted doesn't know what partition to select to resize.  And I don't know how to make my way around the Manual gparted controls, but I am wanting to resize the 2. (System) partition, and install Linux on it's own partition.

Can this be done without deleting any of these other partitions?  I just want to resize the C:.

I would not delete the embedded XP quickplay partition as you can still use it -will show up in Grub boot as Embedded XP.  If I just want to watch a DVD I will occasionally fire up Quickplay instead of booting into Windows.

I also would not delete the HP recovery partition without forst creating a backup of it.  The boot discs and recovery partition are different *slightly*  Better to use Acronis TrueImage and make a backup so the recovery partition can be restored.  getting Acronis TrueImage is well worth the money IMHO.

---

### Post by diablo75 on 2007-06-08
But what about wireless networking?  And beryl?

---

### Post by EXCiD3 on 2007-06-08
Ok, so if you have the Intel Wireless card the wireless should be support right out of the box.

If you have a broadcom card visit this link: [dv6000 wiki]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e")

---

### Post by Atomic Dog on 2007-06-09
The one annoying thing about the HP DV6xxx or DV9xxx laptops is the wide array of hardware installed.  I find the Intel Centrino DV series laptops are good out of the box for the most part (Intel processor, intel wireless, intel video).  The AMD based DV laptops seem to cause people a lot more trouble.  

If you are looking for a DV6000 or DV9000 HP laptop I suggest going with the Centrino versions if you want a smooth Ubuntu install.

---

### Post by doldett on 2007-06-12
Hi, I just finished ubuntu installation (dual boot with vista) on DV 9207us. However, when I chose to start ubuntu on Grub menu, i got message (failed to allocate memory resources) before entering to boot skin, but i can enter to ubuntu properly. Any idea what is wrong and how can i fix it? Does anyone have the same error message?

---

### Post by mmykle on 2007-06-13
Ubuntu 7.04 (64bit processors version) will not install on my dv9000. when i try to run the live CD it wont load anything past the part were it tries ti load my network card. Before it freezes there it gives me a bunch of errors saying that it failed to install (or maybe load, im not sure) some drivers. I have also tried the normal version of Ubuntu 7.04 and it does get a bit farther on trying to load the live cd but it still freezes at some point. My specs are:

Turion64 X2 2.01 GHz
2GB Ram DDR
Nvidia 7600 Go series
74 GB HDD X2

If u want me to be more detailed about something, please ask.

---

### Post by EXCiD3 on 2007-06-13
> **Atomic Dog said:**
> The one annoying thing about the HP DV6xxx or DV9xxx laptops is the wide array of hardware installed.  I find the Intel Centrino DV series laptops are good out of the box for the most part (Intel processor, intel wireless, intel video).  The AMD based DV laptops seem to cause people a lot more trouble.  

If you are looking for a DV6000 or DV9000 HP laptop I suggest going with the Centrino versions if you want a smooth Ubuntu install.

Yes, I totally agree. The AMD versions seem to be the ones having problems. My Core 2 Duo has worked almost flawlessly.

---

### Post by EXCiD3 on 2007-06-13
Here is a list of the topics covered in this thread so far:

1) Does the FN + VGA key work in Feisty? Do the other fn + ?? keys work by default?

2) Webcam
     Paulo79 gave us this link [http://lsb.blogdns.net/ry5u870/]("http://lsb.blogdns.net/ry5u870/")
     JHSaunders gave us this link [Webcam for the dv2000]("http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/")
     I personally have not tried either because i don't really need the webcam at the moment.
 
3) Battery recalibration, found by Paulo79 on HP's website:
   > HP's website says you should calibrate your battery every three months by (1) disabeling WinXP's power management; (2) letting your computer on until your battery is out of charge; (3) doing a full recharge; and (4) re-enabling power management.

I never did that though and don't know if it makes a significant difference. Please let me know if you have tried id. Also, there are a couple of BIOS patches that may help, although I don't remember what they are supposed to fix (Win Vista issues?). I do remember one of them added an option for enabling the virtualization features of the Intel processor.
  
   I personally have recalibrated my battery twice, but usually use my laptop plugged into AC power.

4) Does S-Video, SPDIF outputs work?     

5) teaker1s has created a dv6000 series wiki that has a lot of information that spans the entire dv series of laptops. Go check it out, its very informative.
   [dv6000 wiki]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e")

6) Does the microphone jack/built-in mic work? My built-in mic worked somewhat while playing Counter-Strike 1.6 in Wine. It was extremely choppy sound but it WAS audible.

7) Sound volume? I think that the volume is controlled in several different places, such as in the Gnome tray, the volume touch buttons, and the individual application volumes and if one of these is set to low, your overall volume may sound lower than you would expect. DShepherd gave us this link to help with the volume: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29") lexarrow posted [this.]("http://ubuntuforums.org/showthread.php?t=455147")

8) Differences between the dv9000t and the dv9000z? My dv9000t had no problems whatsoever installing but apparently the dv9000z is quite different.
   As old_salt said earlier:
  > To install or even bootup
- Use the noapic noirqdebug uptions to the boot parameters. My system hung without it during boot.

Wireless
- I used this link to get my wireless working. It shows it's for a Dell however it worked when everything else wouldn't. NDIS wouldnt work. I guess because the firmware wasn't or wouldn't load ? Anyway I'm using the " sudo modprobe bcm43xx" to activate this after each boot.

[http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946)

  the dv9000z seems to have a different wireless driver than then dv9000t which works right out of the box.

9) Media card reader? old_salt mentioned that his worked out of the box but we have not gotten much feedback on this yet.

10)Suspend/Hibernate? Does the proprietary Nvidia driver break this? Has anyone successfully gotten either of these to work? Has anyone tried the [solution]("http://ubuntuforums.org/showthread.php?t=394131&highlight=dv9000&page=4") that 3rods posted?

11)TV Tuner?

12)Remote control? I don't remember any talk about this, but i purchased the cheap little remote that fits in the ExpressCard slot for use when watching movies, however, I have never tried to use it in Ubuntu yet. Anyone have one of these?

13)Lightscribe? Sounds like Lightscribe has only released rpm's of their software and they cannot be converted to deb's successfully.
      *edit* I just noticed a Lightscribe labeler in Automatix. Has anyone tried this yet? I didn't get the Lightscribe burner so I can't try it.

14)Printers?

If anyone has any comments/ideas on these topics please let us know. I would love it if I could completely replace Windows on my laptop.

For those of you hardcore Ubuntu fans, check out Full Circle (The Ubuntu Community Magazine) and the My Story - Researching Ubuntu article. It talks about Magnus Wahlberg's experiences finding a reliable distro of Linux that would run well out-of-the-box on his HP nx8220 laptop.

---

### Post by EXCiD3 on 2007-06-13
> **doldett said:**
> Hi, I just finished ubuntu installation (dual boot with vista) on DV 9207us. However, when I chose to start ubuntu on Grub menu, i got message (failed to allocate memory resources) before entering to boot skin, but i can enter to ubuntu properly. Any idea what is wrong and how can i fix it? Does anyone have the same error message?

I'm not exactly sure what you talking about. Is it a message that is show during boot-up? Because I get a couple of errors like this when I am booting into Ubuntu. One thing, it cannot find an interrupt for eth0.

> **mmykle said:**
> Ubuntu 7.04 (64bit processors version) will not install on my dv9000. when i try to run the live CD it wont load anything past the part were it tries ti load my network card. Before it freezes there it gives me a bunch of errors saying that it failed to install (or maybe load, im not sure) some drivers. I have also tried the normal version of Ubuntu 7.04 and it does get a bit farther on trying to load the live cd but it still freezes at some point. My specs are:

Turion64 X2 2.01 GHz
2GB Ram DDR
Nvidia 7600 Go series
74 GB HDD X2

If u want me to be more detailed about something, please ask.

Looks like you have the dv9000z. We have had lots of problems with the dv9000z. You may want to go back through this thread and find the posts about installing Ubuntu on dv9000z's. I personally have a 9000t and it works perfect. Sorry I cant be much of a help on this topic. :(

---

### Post by doldett on 2007-06-13
> **EXCiD3 said:**
> I'm not exactly sure what you talking about. Is it a message that is show during boot-up? Because I get a couple of errors like this when I am booting into Ubuntu. One thing, it cannot find an interrupt for eth0.


Ummm, It is a message showing before we can see Ubuntu logo and loading bar (PCI Bus : failed to allocate memory resources). However, it actually does not matter as long as i can get into ubuntu. I just want to know if there is somebody getting this message. :D

---

### Post by explemonk on 2007-06-14
> **doldett said:**
> Hi, I just finished ubuntu installation (dual boot with vista) on DV 9207us. However, when I chose to start ubuntu on Grub menu, i got message (failed to allocate memory resources) before entering to boot skin, but i can enter to ubuntu properly. Any idea what is wrong and how can i fix it? Does anyone have the same error message?

I get the exact same error message on my dv9207us,  There is a bug filed somewhere about it.

> **EXCiD3 said:**
> 1) Does the FN + VGA key work in Feisty? Do the other fn + ?? keys work by default?

The following fn + keys work on my laptop:
F1 (Help), F2 (Print), F3 (launch web browser), F6 (lock computer) F7-F8 (brightness).  I have not tested the F4 (VGA) or F5 (suspend), and F9-F12 (play/stop/previous/next) do not work, and I suspect that is because they are not mapped anywhere.  One day I'll take the time to mess with them.

> **EXCiD3 said:**
> 7) Sound volume? I think that the volume is controlled in several different places, such as in the Gnome tray, the volume touch buttons, and the individual application volumes and if one of these is set to low, your overall volume may sound lower than you would expect. DShepherd gave us this link to help with the volume: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29") lexarrow posted [this.]("http://ubuntuforums.org/showthread.php?t=455147")

My volume is noticeably lower in Ubuntu than in Vista.  I haven't tried to compile the new version of Alsa yet.

> **EXCiD3 said:**
> 9) Media card reader? old_salt mentioned that his worked out of the box but we have not gotten much feedback on this yet.

My card reader works out of the box for SD cards.

> **EXCiD3 said:**
> 10)Suspend/Hibernate? Does the proprietary Nvidia driver break this? Has anyone successfully gotten either of these to work? Has anyone tried the [solution]("http://ubuntuforums.org/showthread.php?t=394131&highlight=dv9000&page=4") that 3rods posted?

After reading and trying the solution at the link you gave, both suspend and hibernate work for me (and my wireless networking comes back up), but only if I turn Beryl off first.  With Beryl on it resumes to a black screen where I can move the mouse cursor around but nothing else works--I have to hard reset.  This is using the 2.6.20-16 kernel--I also have 2.6.22-6 installed but I have not tested that one yet.

> **EXCiD3 said:**
> 11)TV Tuner?

Not as far as I know.  dmesg shows that it is recognizing the card being inserted and removed, but I haven't gone anywhere from there.  There is a brief thread on it [here]("http://ubuntuforums.org/showthread.php?t=430121").

> **EXCiD3 said:**
> 12)Remote control? I don't remember any talk about this, but i purchased the cheap little remote that fits in the ExpressCard slot for use when watching movies, however, I have never tried to use it in Ubuntu yet. Anyone have one of these?

I played with it briefly; the volume buttons work on mine.  I suspect that it has to do with a keymapping issue like the fn + keys.

> **EXCiD3 said:**
> 14)Printers?

The only printer I've tried is a Brother 5250-DN (over the network) that I have at work.  It works out of the box.

---

### Post by sdm_cacto on 2007-06-14
Im having a problem after the installation of Ubuntu Feisty in a friends Pavilion dv9000.
It has an AMD processor and a NVIDIA Geforce 7600 Go graphics card.
The problem is that after I install the Nvidia driver I cant set a higher Refresh Rate than 53 hz, is there any solution for this?

Sorry for the bad english

---

### Post by explemonk on 2007-06-14
> **sdm_cacto said:**
> Im having a problem after the installation of Ubuntu Feisty in a friends Pavilion dv9000.
It has an AMD processor and a NVIDIA Geforce 7600 Go graphics card.
The problem is that after I install the Nvidia driver I cant set a higher Refresh Rate than 53 hz, is there any solution for this?

Sorry for the bad english

I think this is a reporting problem when using the restricted driver.  On both my laptop with a Geforce Go 7600 and my two desktops with a Geforce 6600GT and a Geforce 4 MX 440 the refresh rate is listed at 50hz, though my monitors say it is actually 60hz.

---

### Post by EXCiD3 on 2007-06-14
> **doldett said:**
> Ummm, It is a message showing before we can see Ubuntu logo and loading bar (PCI Bus : failed to allocate memory resources). However, it actually does not matter as long as i can get into ubuntu. I just want to know if there is somebody getting this message. :D

Ok, i think i know what you are talking about. I get that same exact message about pci, to tell you the truth, i havent had too much time to spend on my computer, I have 3 jobs... I wouldn't worry about it as it has never caused me any problems...

---

### Post by EXCiD3 on 2007-06-14
> **explemonk said:**
> I think this is a reporting problem when using the restricted driver.  On both my laptop with a Geforce Go 7600 and my two desktops with a Geforce 6600GT and a Geforce 4 MX 440 the refresh rate is listed at 50hz, though my monitors say it is actually 60hz.

You are probably right that it is a reporting problem because my computer has detected incorrect refresh rates several times and I know that the only supported refresh rate is 60hz but have gotten 59 and several other numbers.

---

### Post by louix on 2007-06-14
Hey
My laptop is a HP Pav dv9271 and I use Ubuntu 7.04 on it.
All things works great except the built-in webcam.

lsusb says:
Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

UPDATE:

If tryed the R5U870 and UVCVIDEO driver and the both works but only in black/write :/ Is there anybody who knows how I get colors on my webcam?

---

### Post by louix on 2007-06-14
> **louix said:**
> Hey
My laptop is a HP Pav dv9271 and I use Ubuntu 7.04 on it.
All things works great except the built-in webcam.

lsusb says:
Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

UPDATE:

If tryed the R5U870 and UVCVIDEO driver and the both works but only in black/write :/ Is there anybody who knows how I get colors on my webcam?

Update: I  should just adjust the colors.

---

### Post by mmykle on 2007-06-14
I get the following error when I try to run ubuntu 7.04:

error: microcode "bcm43xx_microcode5.fw" not available o
load failed.

I get several errors like this. after ubuntu is done loading everything else it goes to a black screen and then does not do anything. i have to hold the power button on my computer to shut it off. i am a linux NOOB so if you are nice enough to help me, please go into detail.

---

### Post by #Reistlehr- on 2007-06-15
Ok, so i've had Fedora 7 and Ubuntu 7.04 on this laptop, DV9000z, AMD Turion64 X2 TL-60, 2gb ram, nvidia 7600, braodcom bcm4310.. 

Now, for those of you who have got it working, did you use the i386, or the i686. uname -m returns i686, but when i install it, i get a sound loop bug on the gnome login screen, and absolutley NO wireless with the 4310. I can get the nvidia card working NP.

Also, i cannot boot the machine without the use of noapic and acpi=off

any suggestions?

---

### Post by old_salt on 2007-06-15
Okay #Reistlehr-: Here's my suggestion after many attempts to get that "Perfect Load" -  I use Kubuntu as I can't stand the inadequate Gnome interface however this will work for you.

This procedure takes me only 2 hours using a 3mb DSL conmnection. 

1. Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and from your location download the "64bit Alternate Install" flavor. The 32bit does not do this machine justice. Take your pick of Ubuntu or Kubuntu - your choice. If you use the 32bit version you will have a PCI BIOS error and the system may work however for me I don't like getting boot errors nor did I intend to waste a good 64bit chipset either.

2. You must add the noapic option to the boot parameters. It doesn't hurt anything except allow the machine to work. Put this in at bootup before you install and that's it.

3. Once installed, immediately go to section 1.4.10 and follow the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories). 

Be carefull to use the text pertinent to your system either Gnome or KDE. I used nano to edit all my stuff. 

4. Now update your machine completely. sudo apt-get update

reboot

5. Now return back to [http://ubuntuguide.org](http://ubuntuguide.org) and either follow the guide as you need being careful to read through each step prior to taking actions as some require extra or different steps using the 64bit version or use Automatix2.

6. After updating and adding in the Automatix repo to my apt.sources, I install Automatix2 and add in my nvidia driver and reboot. 

7. Once the video is installed then I use Automatix2 to add in all my multimedia, codecs etc, Google Earth (requires 3D acceleration  - it's why you install video driver first) and Acrobat reader.  

Now, my personal tweaks.... I install these from the command line using apt.

A - I install Firefox, Mozilla-Thunderbird, Build-essential, Synaptic, Yakuake, cabextract

To get your wireless working - 
Go to 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and follow the instructions here. This only takes a couple minutes and you will have a working wireless in minutes. I used the Broadcom 4311 driver even though the system says it's the 4310 Rev01. Go and get the Wireless driver download from the HP Website and download  [**_sp34152.exe_**]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=3224049&os=228&lang=en")  for Windows XP 32 bit. I can't remember if during the install if this driver showed the info while installing or not but it installs. 

Flash - 

Go to [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) and follow the instruction here to get Flash working in your 64bit Firefox if you use that as your browser. It will also work for Opera too. I added the files in all Firefox locations and ran the nspluginwrapper -v -a -i from the Flash directory and it works. I also had to create a launcher for firefox. I've attached my 
launch file used to replace the firefox launcher. Be sure & place this in your /usr/bin directory and don't forget to set permissions and make this executable. 

After this you should be good to go.

For me the Bluetooth, volume buttons above the keyboard, the USB ports, Firewire and Media Card Reader all worked "Out of Box". I did not have an express card to try that. 

Webcam - This does not work and in fact, even the Winblows folks are having issues with this as well. The system will recognize it as a UVC device and there is a driver available however I've not put any effort towards this as it isn't a priority and if the windows folks are having issues, then I don't want to inherit that. 

My system screams and in fact I have Mythtv Frontend installed and stream my TV from another sytem via wireless with no issues. 

I hope this helps as I've tried several other distro's and everything including winblows requires tweaking and extra steps to get working. I've found Kubuntu 7.04 the quickest easiest, most stable, and best performing OS on the Dv9000z. 

Take Care
Tony

---

### Post by old_salt on 2007-06-15
> **mmykle said:**
> I get the following error when I try to run ubuntu 7.04:

error: microcode "bcm43xx_microcode5.fw" not available o
load failed.

I get several errors like this. after ubuntu is done loading everything else it goes to a black screen and then does not do anything. i have to hold the power button on my computer to shut it off. i am a linux NOOB so if you are nice enough to help me, please go into detail.

Go to [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and follow the instructions completely. I tried just installing the firmware for the bcm43xx and it was garbage. Use the ndiswrapper method for best results and throughput.

---

### Post by #Reistlehr- on 2007-06-16
> **old_salt said:**
> Go to [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and follow the instructions completely. I tried just installing the firmware for the bcm43xx and it was garbage. Use the ndiswrapper method for best results and throughput.

thank you, i will give it a try when i get to work. Why waste my own time, when i can get paid to do it :D

---

### Post by mmykle on 2007-06-16
> **old_salt said:**
> Go to [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and follow the instructions completely. I tried just installing the firmware for the bcm43xx and it was garbage. Use the ndiswrapper method for best results and throughput.

Thank you, i will give it a shot and report back to post if it worked ir not.

---

### Post by #Reistlehr- on 2007-06-17
Hey, just wanted to tell you i was successful. You are a life saver. I'm gonna type up a tut on my site, and you got yourself credit.

---

### Post by copeland on 2007-06-18
n/m

---

### Post by old_salt on 2007-06-18
> **copeland said:**
> n/m

My email said you were asking about disk allocation space yet your forum posting is nothing.

As for disk Allocation..... Use the guided use entire disk option unless you dual boot. If that's the case then select manual and go from there. I can't begin to assist without details.

I normally prefer dedicated partitions for / , swap and Home however I've learned that by using simplebackup on a schedule provides adequate backup capabilities provided you burn these to DVD/RW media accordingly. You will have to chown the backup folder ( a small nuisance) and manually burn off but aside from that it's great. This way you maximize your disk utilization to your needs I think.

Tony

---

### Post by copeland on 2007-06-18
> **old_salt said:**
> My email said you were asking about disk allocation space yet your forum posting is nothing.

As for disk Allocation..... Use the guided use entire disk option unless you dual boot. If that's the case then select manual and go from there. I can't begin to assist without details.

I normally prefer dedicated partitions for / , swap and Home however I've learned that by using simplebackup on a schedule provides adequate backup capabilities provided you burn these to DVD/RW media accordingly. You will have to chown the backup folder ( a small nuisance) and manually burn off but aside from that it's great. This way you maximize your disk utilization to your needs I think.

Tony

wow thanks alot, I had actually deleted my post cause I went the route you suggested...but I do have a question....

I'm trying to update my go6150 drivers, I'm having a hard time reading at 1280x800 when it should be 1440x900 for a quick fix I figured out how to increase font to 101 pixels...some things the bottome line of pixels were being cut off the text

used envy to correct

---

### Post by old_salt on 2007-06-18
Folks - Do your research BEFORE posting here. 

I see many new postings daily asking the same questions posted pages before with responses of resolution, links for detailed info and assistance by others to assist in answering the same questions. Please  - patience and due diligence and research BEFORE posting an identical question here. While I'll do my best to assist where I can to help contribute to the community, my patience as well as many others wear thin with those who are lazy and makes me and many others reluctant to even offer advice or assistance. 

There are many postings and responses regarding the web cam issue here and elsewhere. Please search this forum or topic BEFORE repeating this question here. The built-in web cam on the DV9000z for about 99% of us is not working. There are several postings that assist in getting this to work however lack of follow up responses of success or failure BY YOU with augmenting details are not available. This forum is a 2-way street and depends on everyone's feedback of success or failure with supporting documentation, details and error logs for a proper dialog of resolution to occur. PLEASE provide feedback - good or bad - to the appropriate topics as this is crucial to arriving to a resolution for all.


WEB CAM on DV9000z

It isn't working for the masses. The biggest obstacle is lack of an application that you can test with aside from Ekiga which not many people use and the failure of everyone to properly get aMSN working. As I see it, unless you can open an app to test or view your cam, how else can you verify your results? 

On another note, even though the web cam came included, and knowing everyone wants to utilize all assets purchased; for many, this is not a priority in comparison to say blue tooth, wireless or the nVidia hardware acceleration. In fact, many more would prefer the Lightscripe burning option resolved above the web cam. One thing at a time here. 

I suggest holding your horses until the next release of whatever before proceeding with the web cam issue. While it came with my system, I preferred the other options above this regarding my purchase. If you search the HP website; you will find that even the Winblows users are experiencing issues in getting the web cam properly working. Now think about this; If a windows design has issues with getting hardware to work properly with winblows, then what do you think is going to happen with an unsupported OS?

Folks, please remember - it's a 2-way dialog here and without your feedback, how else are we to know if our diagnosis and recommendations work or not? 

PLEASE PLEASE don't repeat the same questions. Research - remember that troubleshooting is not a quick resolution to a problem, it's an effort that requires patience and perseverance. It may take you a week or a month however, the lack of YOUR feedback of your efforts is what helps reduce this time frame for other's. Let's remember this is not a solutions database; but instead an open dialog for all.

Sincerely

---

### Post by old_salt on 2007-06-18
> **copeland said:**
> wow thanks alot, I had actually deleted my post cause I went the route you suggested...but I do have a question....

I'm trying to update my go6150 drivers, I'm having a hard time reading at 1280x800 when it should be 1440x900 for a quick fix I figured out how to increase font to 101 pixels...some things the bottome line of pixels were being cut off the text

*edit* trying envy now to correct

If you followed my post, you should have used Autonatix2 to install your nvidia driver. I have the 6150 card and it displays correctly at 1680x1050 resolution at 50Hz refesh rate. NOTE: according to other postings - the refresh rate is inaccurate. Do Not go by this as your display can onlly accomodate a 60 Hz rate which is standard for the display. Other posts have reported using tools which indicate the true refresh rate as being 60Hz vice the reported 50Hz. 

I'm puzzled as to why you have a screen size different from the norm? Even Vista uses this size as it's default. I know from experience that FC7 and Suse DO NOT accept this size so I'm a little concerned as to why you opt for the non-standard screen size.

Tony

---

### Post by copeland on 2007-06-18
ok, trying to get the wireless to work

using the walktrhough for

Broadcom Wireless 1390 WLAN MiniCard and thsi tut but I'm too much of a noob I got hung up at step 4  I think

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by old_salt on 2007-06-18
> **copeland said:**
> ok, trying to get the wireless to work

using the walktrhough for

Broadcom Wireless 1390 WLAN MiniCard and thsi tut but I'm too much of a noob I got hung up at step 4  I think

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

------------------

Dude, unless I missed something, are you not using an HP900 series laptop? If so then why are you messing with a 1390 WLAN Minicard? 

You have a Boradcom Wireless 4300 series card built-in.

---

### Post by copeland on 2007-06-18
> **old_salt said:**
> ------------------

Dude, unless I missed something, are you not using an HP900 series laptop? If so then why are you messing with a 1390 WLAN Minicard? 

You have a Boradcom Wireless 4300 series card built-in.

my device manager is reading it as 

Vendor : Broadcom 
Device : Dell wireless 1390 wlan mini pci

---

### Post by elj4176 on 2007-06-19
I've got a dv9074cl here and 7.04 32bit. Video works fine, I got the wireless working ok, DVD multi drive works fine, remote works fine, touchpad works ok, hibernate/suspend seems to work ok.

However, the USB ports do not seem to work. I plugged in a set of usb headphones and they do not work. Plugged in a usb mouse and it does not work. Plugged in my iAudio X5 mp3 player and it doesn't work. 

The usb ports are getting power because my mp3 player started charging when I plugged it into the usb port.

Media reader doesnt read my xd card. Don't have a different card to try sd. 
Webcam doesnt work but I have not tried the fixes to get  that working yet.

Any help on the usb and media reader?

lspci reports this:

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)

thx!

---

### Post by old_salt on 2007-06-20
> **elj4176 said:**
> I've got a dv9074cl here and 7.04 32bit. Video works fine, I got the wireless working ok, DVD multi drive works fine, remote works fine, touchpad works ok, hibernate/suspend seems to work ok.
-----------------------------------
**My first question is why aren't you running the 64bit OS? I've found there's a night/day difference between the two on my 9000z. **
-----------------------------------

However, the USB ports do not seem to work. I plugged in a set of usb headphones and they do not work. Plugged in a usb mouse and it does not work. Plugged in my iAudio X5 mp3 player and it doesn't work. 

---------------
[B] If your adamant at running the 32bit OS, then you will need to play around with your kernel boot parameters using a trial and error method to see what all gets you the best or most of anything. You also should check to see if you have everything installed or not. 

Boot parameters to try are; noisapnp, noapic, nolapic, pnpacpi=off, pnpbios=off

As I said you will have to play around and mix different combinations to see what works best or try my guide on pag 9 of this posting.[/B]

--------------

The usb ports are getting power because my mp3 player started charging when I plugged it into the usb port.

Media reader doesnt read my xd card. Don't have a different card to try sd. 
Webcam doesnt work but I have not tried the fixes to get  that working yet.

Any help on the usb and media reader?

lspci reports this:

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)

----------------------------------

**My lspci is a lot more than what you show here even considering you edited out the fluff. Looks to me like your host bridges aren't showing up for starters. I don't really know what else to recommend except the above or else go download the 64bit Alternate Install CD and try that. With the exception of Wireless and Webcam, everything for me worked "Out of Box". Wireless was a 15min install, webcam I can care less about.**
---------------------------------

thx!


Let me know what you decide and how it turns out.

---

### Post by copeland on 2007-06-20
> **old_salt said:**
> Let me know what you decide and how it turns out.

could you please link how you got wireless working? I just had to do a reinstall cause I fubared everything trying to get it up and running...by fubar I mean it would boot through the user screen and password screen...

but the desktop came up blank (just the light tanish color of the background from the login screen) with a white square in the upper left corner, I could move the mouse all over and it would turn to a cursor over some parts of the white screen, but I could do nothing else...

---

### Post by old_salt on 2007-06-20
> **copeland said:**
> could you please link how you got wireless working? I just had to do a reinstall cause I fubared everything trying to get it up and running...by fubar I mean it would boot through the user screen and password screen...

but the desktop came up blank (just the light tanish color of the background from the login screen) with a white square in the upper left corner, I could move the mouse all over and it would turn to a cursor over some parts of the white screen, but I could do nothing else...
------------
Copeland - _without sounding rude_; you are seeking help for a Dell Laptop and **this is a forum specific to the 64bit HP 9000 series laptops**. There are no guarantees the solutions posted here will work for your particular model. Please go here [http://ubuntuforums.org/search.php?searchid=22383574](http://ubuntuforums.org/search.php?searchid=22383574) for information and assistance specific to your hardware. 

My guide can be found on page 9 of this forum regarding initial installation and follow on tweaks however - my posting is specific to the HP9000z Pavilion Laptop. Your mileage will vary and there is no guarantee of success in following this on your model. 

Tony

---

### Post by elj4176 on 2007-06-20
I'm not using the 64-bit because I couldn't get it to install when I first tried it a few months ago. I was attempting a dual-boot setup with MCE on the 1st drive and ubuntu 64 bit on the second drive. At the time I didn't know about the boot parameters. I recently had a problem with the MCE and decided to try again but with the 32 bit this time and I added noapic boot parameter and it worked.

I will take your advice old_salt and download a fresh iso of the 64-bit and see what I get. Why the alternate CD?

Thanks!

---

### Post by old_salt on 2007-06-20
> **elj4176 said:**
> I'm not using the 64-bit because I couldn't get it to install when I first tried it a few months ago. I was attempting a dual-boot setup with MCE on the 1st drive and ubuntu 64 bit on the second drive. At the time I didn't know about the boot parameters. I recently had a problem with the MCE and decided to try again but with the 32 bit this time and I added noapic boot parameter and it worked.

I will take your advice old_salt and download a fresh iso of the 64-bit and see what I get. Why the alternate CD?

Thanks!

The alternate CD does not include the Live CD and uses the text installer which is a quicker and smoother install (It's still a guided install with dos style graphics).  You also have more control during the install process of the available options. I've never had any issues dual booting in past so I'm unsure why some people have problems unless they opt not to install grub due to misunderstanding during the process. Alllow grub to control the boot process which is required. The Alternate install also is geared more towards this type of installation including vendor specific installations which may include hardware specific drivers and configurations. I've also found that this is also kept up to date and once loaded you have less to update.

---

### Post by copeland on 2007-06-20
> **old_salt said:**
> ------------
Copeland - _without sounding rude_; you are seeking help for a Dell Laptop and **this is a forum specific to the 64bit HP 9000 series laptops**. There are no guarantees the solutions posted here will work for your particular model. Please go here [http://ubuntuforums.org/search.php?searchid=22383574](http://ubuntuforums.org/search.php?searchid=22383574) for information and assistance specific to your hardware. 

My guide can be found on page 9 of this forum regarding initial installation and follow on tweaks however - my posting is specific to the HP9000z Pavilion Laptop. Your mileage will vary and there is no guarantee of success in following this on your model. 

Tony

Again, this is a HP 9000 laptop I have, 

my device manager is reading it as

Vendor : Broadcom
Device : Dell wireless 1390 wlan mini pci

but this laptop is a HEWLETT PACKARD DV9000

---

### Post by old_salt on 2007-06-21
> **copeland said:**
> Again, this is a HP 9000 laptop I have, 

my device manager is reading it as

Vendor : Broadcom
Device : Dell wireless 1390 wlan mini pci

but this laptop is a HEWLETT PACKARD DV9000

Try lspci-v and see if it looks anything like mine. I've attached a text output from my system.

Which model of the 9000 are you running? I'm running the z with the AMD chip. Even though mine says Broadcom 4310, I truly believe it slightly different as I pulled the driver from the HP site. I once forgot to add the ndsiwrapper to the modules file which prevented the radio from activating. Also make sure you choose only one network manager to run. I use KDE so I left the default knetwork Manager. Under Gnome it's different and you may have try something like wi-fi radar even though mine worked out of box under Gnome when I tested. I didn't have as much control though under Gnome as I do with KDE.

---

### Post by lightningstormz on 2007-06-21
I have a hp dv9500t w/ the Nvidia 8400m gs graphics card. I tried to install the 64 bit edition of ubuntu 7.04 an nothing happened. The screen went blank every time after i selected the install option. The kernel would load and then nothing would happen afterwards. Any help would be greatly appreciated!

---

### Post by EXCiD3 on 2007-06-21
Friend of mine is having the exact same problem at the moment. I'm trying to help him out. He has 2 8800GTS's in his desktop. I'll post back if we get this figured out.

---

### Post by lightningstormz on 2007-06-21
I have received this error when I tried acpi=off ,"/bin/sh:can't access tty; job control turned off" I then arrive at something called BusyBox v1.1.3. It looks like some type of command prompt but I don't know what to do from here. I also noticed that for a split second I get a message saying something about not being able to access memory.

---

### Post by old_salt on 2007-06-21
> **lightningstormz said:**
> I have a hp dv9500t w/ the Nvidia 8400m gs graphics card. I tried to install the 64 bit edition of ubuntu 7.04 an nothing happened. The screen went blank every time after i selected the install option. The kernel would load and then nothing would happen afterwards. Any help would be greatly appreciated!

This has been documented in detail throughout this forum. You must use the noapic option in your kernel boot parameters. Page 9 on this forum is my install guide. If you use any other option then weird things happen. It was a toss up between the pnpbios=off and noapic. What worked best for me was the noapic. 

Seems all the hardware manufacturers are getting lazy and cheap and cowing down to Microcrap's wishes to make everything plug-n-pray. Compaq among many has been using a plug-n-pray BIOS for some time (which has both good and bad points) to keep resistance against the borg to a minimum. As you can see, Microcrap wants full control. Bad side is coding of the OS increases for PnP BIOS Support which sacrifices performance yet a wider variety of hardware can be accomodated. A regular BIOS I think is better but it increases hardware manufacturing costs so.....

I recommend taking a few minutes and review everything in this forum and bookmarking it for quick reference. About the only real outstanding issue is the webcam and as I've already stated, not many care about this and even the Winblows folks have issues too. 

Let me know how everything went.
 
Oh and also----- get the alternate install CD version. The one you have is not the best for this model of laptop.

---

### Post by EXCiD3 on 2007-06-21
> **old_salt said:**
> 
Seems all the hardware manufacturers are getting lazy and cheap and cowing down to Microcrap's wishes to make everything plug-n-pray.

:KS That is my favorite quote on this ENTIRE forum! =D>

---

### Post by EXCiD3 on 2007-06-21
About the 8800 graphics card: Change the kernel boot parameters by deleting "quiet" and "splash" and add "vga=0x31B". This will allow you to boot into the normal kernel option in grub. Hope it works!

---

### Post by old_salt on 2007-06-22
> **EXCiD3 said:**
> :KS That is my favorite quote on this ENTIRE forum! =D>

Thanks EXCiD3, your comment prompted me to finally finish up my profile, upload my avatar and setup my signature.

---

### Post by elj4176 on 2007-06-22
I've reinstalled using the 64 bit this time and it does seem a bit snappier. Anyone having trouble with beryl? When I run beryl every window I open has no decorations (min, max close bar). Terminal comes up completely white and I have to use alt-f4 to close it. I tried loading emerald and emerald-themes but that did not help.
I have the dv9074cl amd64x2 w/nvidia geforce go 7600. I used automatix2 to install my nvidia drivers.

Any ideas? Other than not using beryl ;)

---

### Post by old_salt on 2007-06-22
elj4176

As for using any of that "Eye Candy" stuff, I don't know what to say. I know there are several posts outside this forum regarding this and more capable in helping you on this. Most posting here are more concerned about getting the OS installed on the laptop because the hardware is so new and getting accessories to work. Try the search box on the main page for Beryl and start there. Like I said, I know there's been a lot of activity with this and some even have very detailed info. 

Have you tried [http://ubujntuguide.org](http://ubujntuguide.org) yet? There's a complete step by step for Beryl section on that site. I have it bookmarked and refer to it often.

Personally I think any of the eye candy stuff is a waste of good resources, overloads your system and is experimental at best. I had it working briefly but man what a load it was. I idled at 15% CPU utilization. 

The biggest mistake most laptop users make is they attempt to treat/use the system like a desktop. Laptops aren't designed to be a desktop replacement and are still primarily for the traveling businessman to communicate with the office and clients and the lightweight home user. (Word Processing, Web Browsing, email etc). Even with today's technology, they still lack the "Torque" (for lack of better terms here) that a good desktop has. This should be considered before purchase and a primary focus when deciding if a laptop is a suitable choice or not.

I urge caution in using Beryl and wish you the best. I wished I could help you more however I'm not a fan of it. Try the suggestions above and let me know if that helps.

Tony

---

### Post by old_salt on 2007-06-22
Does anyone know of a link to post some suggestions for KDE4?

---

### Post by lightningstormz on 2007-06-22
ok I dowloaded the 64bit alternate install and was able to install on my second hard drive. I typed in the vga=0x31B and was able to get to the linux kernel. Then, I got the generic Xorg failure. I am now runing "sudo apt-get update" to get the latest nvidia driver. Thanks for your help!

---

### Post by elj4176 on 2007-06-22
> **old_salt said:**
> elj4176

Personally I think any of the eye candy stuff is a waste of good resources, overloads your system and is experimental at best. I had it working briefly but man what a load it was. I idled at 15% CPU utilization. 

I urge caution in using Beryl and wish you the best. I wished I could help you more however I'm not a fan of it. Try the suggestions above and let me know if that helps.

Tony

I hear ya. I actually bought this laptop with running beryl in mind. One of the reasons for this laptop is so that I can show windows users what linux has to offer. The eye candy helps get their attention.

If I can get it to run then great - but if not then no big deal. I'll do a search and see what I can find.
Thanks!

---

### Post by old_salt on 2007-06-22
> **elj4176 said:**
> I hear ya. I actually bought this laptop with running beryl in mind. One of the reasons for this laptop is so that I can show windows users what linux has to offer. The eye candy helps get their attention.!

I hear you however I do a lot of video editing and I need all the resources I can muster. I really don't have intentions showing winblows users anything other than - 

Your what? reloading again after 3, 4 months? It's crashed? Your infected with what?  I guess you won't be playing golf & having a beer with us this Saturday - you have an all day chore reloading your system huh!

LOL

I like it when windows just pop open and things run fast. Beryl was okay but the delay in apps opening, windows lagging and the CPU churning at 15% at idle is taxing on the system. However that's what this is all about, choices right? Let me know how it goes.

---

### Post by lightningstormz on 2007-06-22
I thought everything was going alright but now I have an issue with the Nvidia driver. I installed the latest driver from the Nvidia website and I still get X errors. It says that kernel and the driver doesn't match.

---

### Post by mkoyle on 2007-06-22
lightningstormz:

I have always liked envy; it downloads the nVidia driver and recompiles the kernel and everything.  Elsewhere in this thread, others recommend Automatix2.  Either one will attempt to automatically fix the problem you are describing.  It just sounds like your kernel drivers aren't installed.  Use synaptic or some other package manager to get automatix2 or envy and install the kernel drivers with the nvidia driver.

--Matthew

---

### Post by old_salt on 2007-06-23
> **lightningstormz said:**
> I thought everything was going alright but now I have an issue with the Nvidia driver. I installed the latest driver from the Nvidia website and I still get X errors. It says that kernel and the driver doesn't match.

Lightning - Let Automatix install the vid driver. This way if it fails, you can recover at boot by using the automatic-restore-nvidia  command that automatix so nicely setup. 

1. load system
2. go to  ubuntuguide to add your repos, update system and install automatix2 (IN THIS ORDER! )

DO NOT go hogwild and install everything else at this point. Let's just get the base install loaded, updated and the important drivers loaded BEFORE doing everything else. 

So after you update and get automatix2 installed...

3. using  automatix2 - install ONLY the nvidia driver (you can install the rest later)


Finish the install as you see fit.

---

### Post by lightningstormz on 2007-06-23
The problem is that I can't get into the X server so automatix2 didn't work. I tried using envy, but still got the same error messages from X. The driver didn't not match the kernel even though it said it had compiled a kernel for me.

---

### Post by lightningstormz on 2007-06-23
Yes! envy did work! I don't know how it worked but when I tried booting ubuntu i saw the nvidia splash screen and then i saw the ubuntu login. I never thought I would see the day. Thanks again!

---

### Post by old_salt on 2007-06-24
I've had the same thing happen to me. I thought it it was just something on my end until I just remembered after reading your last post that I decided to try something different. I updated everything except my kernel and when Automatix2 installed the nVidia driver, my kernel went from 2.6.20-12 to 2.6.20-15. Everything worked great then I updated to the 2.6.20-16 version and doing just fine.

Sorry for the slight omission but like I said, I thought it was something I did or was doing forcing me to go that route. I now have no doubt that there must be something amiss in the 2.6.20-16 headers etc. The kernel works fine however when trying to compile against this version, it just won't work for some reason. WEIRD !!!!!

---

### Post by natacho on 2007-06-24
is it possible to make the tv tuner work?

---

### Post by EXCiD3 on 2007-06-24
> **natacho said:**
> is it possible to make the tv tuner work?

No one has been able to get it working so far.

HOWEVER, i wonder if someone could install WinXP or Vista on VirtualBox and install the drivers on there... Anyone game for trying this out? I personally don't have a tv tuner so i cant help...

---

### Post by old_salt on 2007-06-25
natacho - 

I didn't get the Tuner Card with my unit but I don't see why it can't work if you obtained the ivtv software and firmware and loaded this up. You would need something like mythtv to view with however. I am subscribed to the ivtv mail list and it's very active. Give it a try is all I can suggest. Guaranteed it's not going to work if you don't try.

Excid3

Not to rain on your parade but that won't work. You would need something that supports paravirtualization which is ZEN at the moment. VMware is close to marketing a product with this soon. Virtualbox only half worked on my test run. I didn't like how awkward it was changing your mouse and keyboard back and forth. In fact, I could never get that working correctly and then it couldn't even load up a VM so... I'll stick with VMware Server for now.

---

### Post by mnederlanden on 2007-06-25
I finally got my wireless card to be recognized.

I followed the directions at 
[http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946)

Thank you whoever posted that this worked with our laptop models.

But I have two problems.

A. I have to type sudo modprobe bcm43xx every time I log on. Is there a way to automate that?

B. I cannot see any wireless networks. I installed Wifiradar, KWifiManager, and Wireless Assistant to see if it was incompatibility with a program, but I cannot see anything with any program.

I have a HP Pavilion dv9009nr and am running 7.04

---

### Post by EXCiD3 on 2007-06-25
> **mnederlanden said:**
> I finally got my wireless card to be recognized.

I followed the directions at 
[http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946)

Thank you whoever posted that this worked with our laptop models.

But I have two problems.

A. I have to type sudo modprobe bcm43xx every time I log on. Is there a way to automate that?

B. I cannot see any wireless networks. I installed Wifiradar, KWifiManager, and Wireless Assistant to see if it was incompatibility with a program, but I cannot see anything with any program.

I have a HP Pavilion dv9009nr and am running 7.04

Hmmm. So you know that it is working for sure? Because usually if the drivers are installed correctly you should be able to see wireless networks.

---

### Post by mnederlanden on 2007-06-25
When I type

sudo lspci -vnn

I get the right hardware. (The Dell from [http://ubuntuforums.org/showthread.php?t=434946;](http://ubuntuforums.org/showthread.php?t=434946;) even though I have of course a hp)

Should I check another way to see if it is working?

---

### Post by EXCiD3 on 2007-06-25
Sounds like all you need are the drivers:

Compliments of Old_Salt:
> To get your wireless working -
Go to
[https://help.ubuntu.com/community/Wi...ndiswrapper%29](https://help.ubuntu.com/community/Wi...ndiswrapper%29)

and follow the instructions here. This only takes a couple minutes and you will have a working wireless in minutes. I used the Broadcom 4311 driver even though the system says it's the 4310 Rev01. Go and get the Wireless driver download from the HP Website and download sp34152.exe for Windows XP 32 bit. I can't remember if during the install if this driver showed the info while installing or not but it installs.

Flash -

Go to [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) and follow the instruction here to get Flash working in your 64bit Firefox if you use that as your browser. It will also work for Opera too. I added the files in all Firefox locations and ran the nspluginwrapper -v -a -i from the Flash directory and it works. I also had to create a launcher for firefox. I've attached my
launch file used to replace the firefox launcher. Be sure & place this in your /usr/bin directory and don't forget to set permissions and make this executable.

After this you should be good to go.

I cant really help you as i have the Intel wireless because i have a dv9000t, yours is based off of the dv9000z which has a broadcom wireless card. The intel works out of the box, the broadcom takes a little work to get going.

---

### Post by old_salt on 2007-06-25
> **mnederlanden said:**
> I finally got my wireless card to be recognized.

I followed the directions at 
[http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946)

Thank you whoever posted that this worked with our laptop models.

But I have two problems.

A. I have to type sudo modprobe bcm43xx every time I log on. Is there a way to automate that?

B. I cannot see any wireless networks. I installed Wifiradar, KWifiManager, and Wireless Assistant to see if it was incompatibility with a program, but I cannot see anything with any program.

I have a HP Pavilion dv9009nr and am running 7.04

You did not follow the instructions I posted on page 9 of this forum that has worked flawlessly for many. You will need to check the documentation from the link you used to install the BCM43xx firmware. The link I used an posted is here;
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)


On another note, your problem too rests with having 3 network managers installed and trying to operate. Use only one. I've found that the default manager for whatever interface you use is best. Either networkmanager (gnome) or knetworkmanager for kde.

---

### Post by DocME on 2007-06-25
For those of you running Kubuntu 7.04, have you had any issues with usb powered external hard drives? Edgy mounted it right out of the box, but Feisty doesn't automatically mount it...I've tried a couple of approaches, but I was hoping that somebody already had some luck.

---

### Post by EXCiD3 on 2007-06-25
> **DocME said:**
> For those of you running Kubuntu 7.04, have you had any issues with usb powered external hard drives? Edgy mounted it right out of the box, but Feisty doesn't automatically mount it...I've tried a couple of approaches, but I was hoping that somebody already had some luck.

Are your drives NTFS or FAT? My thumb drives have worked fine and they are FAT. My external 3.5" powered hdd seems to work fine, except it is in NTFS so i used the Automatix thingy to install automatic NTFS mounting. I havent had any problems myself. A little more info would be helpful.

---

### Post by old_salt on 2007-06-25
> **EXCiD3 said:**
> Are your drives NTFS or FAT? My thumb drives have worked fine and they are FAT. My external 3.5" powered hdd seems to work fine, except it is in NTFS so i used the Automatix thingy to install automatic NTFS mounting. I havent had any problems myself. A little more info would be helpful.

This is weird. My long time friend came down last weekend to replace Suse with Ubuntu. He purchased a 250Gb Seagate External USB HDD to backup his laptop. It used it's own power source however. Long story short....

1- Thumb drives are not the same as External HDD's even if they both connect via usb.
2- According to the box, it's default format is NTFS - therefore some work is involved initially if you aren't using Winblows. Even Macs are forced to reformatting the drive.

As it turned out, our issues were due to a botched partition/format from the factory. Once this was cleaned up (Chkdsk -f from a windows system) everything appeared to work except he has to use the following command 

sudo mount -t ntfs-3g /dev/sda1 /media/usbdrive1

to access the drive. Weird as we installed the automatix ntfs tools. Don't understand why it must be manually mounted however it's not that big of a deal. It works so..... 

I'm curious about more info as well.

---

### Post by DocME on 2007-06-25
The external hard drive is a Western Digital 120gb USB Travel drive. With Edgy the drive was automatically recognized and brought up a window with options and an icon on the Desktop.  With the new install of Feisty there is no reaction when I plug in the External HD (although it does power up.) There is nothing under Media Devices in Konquer and the computer seems to recognize other usb devices such as my trackball mouse.

I haven't tried Automatix yet...but I will right now, THANKS!

---

### Post by old_salt on 2007-06-25
> **DocME said:**
> The external hard drive is a Western Digital 120gb USB Travel drive. With Edgy the drive was automatically recognized and brought up a window with options and an icon on the Desktop.  With the new install of Feisty there is no reaction when I plug in the External HD (although it does power up.) There is nothing under Media Devices in Konquer and the computer seems to recognize other usb devices such as my trackball mouse.

I haven't tried Automatix yet...but I will right now, THANKS!

Once you install Automatix2, under utilities I believe you select the NTFS utilities to automatically read/write and mount those systems. Before that did you try the mount command I listed in my previous message?

---

### Post by DocME on 2007-06-25
Yes, I have tried the command and i get the response that it is an invalid mount point

$ sudo mount -t ntfs-3g /dev/sdb1 /media/usbdrive1
mount: mount point /media/usbdrive1 does not exist

PS Thanks for the quick replies

---

### Post by old_salt on 2007-06-25
> **DocME said:**
> Yes, I have tried the command and i get the response that it is an invalid mount point

$ sudo mount -t ntfs-3g /dev/sdb1 /media/usbdrive1
mount: mount point /media/usbdrive1 does not exist

PS Thanks for the quick replies

Hey no need to install something if you don't need it so yes, try the ntfs-3g from automatix and see if that helps. Also of note, I had some minor issues when booting with my drive connected during bootup. I plugged in after I logged in and it worked. Your mileage may vary.

Thanks I'm online now so.... I try and help when I can. I know what it's like when your trying to troubleshoot and you have to way another day to get the next step or obtain more info.

---

### Post by DocME on 2007-06-25
I have now installed Automatix2 and the Automatix read/write NTFS and FAT32 Mounter.  I rebooted and I still can't access my external hard drive. Using fdisk -l shows...

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)

do you have any more suggestions?

---

### Post by old_salt on 2007-06-26
> **DocME said:**
> I have now installed Automatix2 and the Automatix read/write NTFS and FAT32 Mounter.  I rebooted and I still can't access my external hard drive. Using fdisk -l shows...

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)

do you have any more suggestions?

Now try the command

sudo mount -t FAT32-3g /dev/sdb1 /media/usbdrive1
or
sudo mount -t VFAT-3g /dev/sdb1 /media/usbdrive1

remember, this isn't going to be recognized like a USB thumb drive. It's a real hard drive. It's like you added a disk to your system. It must be mounted. When you work out the command that works, add that to your fstab file making sure to use EXACTLY the same format as used there but with the info that was successful in mounting it. Then it should mount when booting up or plugging in.

---

### Post by EXCiD3 on 2007-06-26
> **DocME said:**
> Yes, I have tried the command and i get the response that it is an invalid mount point

$ sudo mount -t ntfs-3g /dev/sdb1 /media/usbdrive1
mount: mount point /media/usbdrive1 does not exist

PS Thanks for the quick replies

This error just means you need to create the folder yourself, /media/usubdrive1. You should then be able to mount it and then check that folder to see if there are files there afterwards.

Problem:
Every time i plug in my 19" acer monitor ubuntu clones the screens (laptop and acer) then when it gets to the login screen it shuts off my laptop monitor and only uses the acer monitor. I would like to use both, but i dont really know how to set this up and it ALWAYS detects the screen as a refresh rate of 50Hz but the monitor only supports 60Hz. When i go to change the screen resolution options in GNOME, it gives me the options of 50 Hz and 51Hz. 51 Hz seems to be the correct setting as the screen is quite clear on this one and not on 50 Hz. How would I configure ubuntu to always use 51Hz setting (or 60Hz)? Would it cause problems because that monitor is only half the time plugged in? Can i set it up to use 51hz on that monitor whenever it is detected? I really dont know too much about setting this stuff up and since every time i get online i am away from home, i cant mess with my monitor and be online at the same time :( I wish my parents would give in and buy high speed internet... but i live in the country so i could probably only get satelite...

---

### Post by EXCiD3 on 2007-06-27
Ok, so i just had the worst night evar... I got KDE installed, chose kdm as the desktop manager. Once it got to the login screen, everything was black. Checked the console, apparently something with the kernel was wrong. I didn't have internet to look it up so i just removed kdesktop and hoped it would work...well, it didn't. I didn't have anything important on that install so i reinstalled Feisty...and realized i couldn't do anything important with it (like watch family guy) so i installed Ubuntu Ultimate...and when i was playing with the themes one of the icon packs screwed up and i got a black screen again...i said screw it, im going to bed. Called a friend to download Kubuntu so...now thats what i'm using...one hell of a night...

---

### Post by mnederlanden on 2007-06-27
> **old_salt said:**
> You did not follow the instructions I posted on page 9 of this forum that has worked flawlessly for many. You will need to check the documentation from the link you used to install the BCM43xx firmware. The link I used an posted is here;
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)


On another note, your problem too rests with having 3 network managers installed and trying to operate. Use only one. I've found that the default manager for whatever interface you use is best. Either networkmanager (gnome) or knetworkmanager for kde.

Old_Salt, Your instructions do not work.

After I input sudo apt-get install cabextract unzip, I get this error:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cabextract is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cabextract has no installation candidate[/INDENT]

Then when I put in cabextract sp33008.exe, I get this error:

[INDENT]The program 'cabextract' is currently not installed.  You can install it by typing:
sudo apt-get install cabextract
Make sure you have the 'universe' component enabled
bash: cabextract: command not found[/INDENT]

Lastly when I input unzip sp33008.exe, I get this error.
[INDENT]
Archive:  sp33008.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.r
unzip:  cannot find zipfile directory in one of sp33008.exe or
        sp33008.exe.zip, and cannot find sp33008.exe.ZIP, period.[/INDENT]

Also I was not using three network manages at once.  I was merely trying to illustrate that I had tried multiple options.

I have a 9009nr and lspci returns:
[INDENT]
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)[/INDENT]

Any help would be appreciated.

---

### Post by EXCiD3 on 2007-06-27
Am i wrong in thinking that your wireless card is a Broadcom 43xx card? If found a HOWTO located here: [http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+broadcom+43]("http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+broadcom+43")

---

### Post by old_salt on 2007-06-27
> **mnederlanden said:**
> Old_Salt, Your instructions do not work.

After I input sudo apt-get install cabextract unzip, I get this error:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cabextract is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cabextract has no installation candidate[/INDENT]

Then when I put in cabextract sp33008.exe, I get this error:

[INDENT]The program 'cabextract' is currently not installed.  You can install it by typing:
sudo apt-get install cabextract
Make sure you have the 'universe' component enabled
bash: cabextract: command not found[/INDENT]

Lastly when I input unzip sp33008.exe, I get this error.
[INDENT]
Archive:  sp33008.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.r
unzip:  cannot find zipfile directory in one of sp33008.exe or
        sp33008.exe.zip, and cannot find sp33008.exe.ZIP, period.[/INDENT]

Also I was not using three network manages at once.  I was merely trying to illustrate that I had tried multiple options.

Any help would be appreciated.



Sounds like you omitted step #3 to properly add all the necessary repos to your apt sources list following the ubuntuguide. If you performed the copy-paste then you forgot to apt-get update or didn't follow the steps to obtain the keys for those repos to allow access and update your database. 

If you follow the guide on ubuntuguide.org and the rest of my instructions it will work. I've personally installed close to a dozen systems not counting my testing personally and not to mention those who have reported success from this forum. You have to be missing something. It happens and it's no different than a syntax or typo error.

---

### Post by EXCiD3 on 2007-06-27
People need to start being more careful about what they do. If you don't know what you are doing, follow the instructions. If you DO know what you are doing, well...you wouldnt have had any problems.

When we post instructions, do what we tell you. Dont complain about it not working if you didnt do what we said.

---

### Post by mnederlanden on 2007-06-28
I don't think the problem is with not "doing what you said", but rather not understanding what you mean. You should really consider making the guide more user friendly. For example: the guide stays, without a descriptor of  where you find these items and what "uncomment" means. (There were several more incomplete instructions like this)


[INDENT]
"Find and uncomment these lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

and

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe"[/INDENT]

as I stated earlier, find where and what is uncomment?

Secondly, you should attempt to break through your current strategy of demeaning the person who asks a question. If you are going to answer a question on the forums, you must realize you are an evangelist for the product and that to some extent the way in which you answer the question determines whether someone will adopt it. Repeating  a mantra -- "you're not following directions" -- is hardly effective at correcting the problem and has made me less likely to want to use the forums to find help.
If you don't want to help or can't do so nicely,* you don't have to post.*

---

### Post by old_salt on 2007-06-28
> **mnederlanden said:**
> I don't think the problem is with not "doing what you said", but rather not understanding what you mean. .[/I]

Okay... let's all stop right here before tempers flare okay? I apologize for this.

First off - Linux isn't Windows or MAC. It's a totally different environment. While it's not as "Point-n-Click" as it's comrades, it has it's advantages. Before Windows, DOS required users to be fluent at the Command Line. Windows improved on that however many will say it made people more computer illiterate and lazy. With recent Windows versions (2003 and Vista), Microcrap has returned to the Command Line. GUI development takes time and costs money. 

Now while you may be new to Linux, there is a certain measure of knowledge assumed every user has. If not it's expected that you learn while researching and perform due diligence in attempting to work through a problem or whatever as much as possible before & during the assistance process. Remember - Google is your friend and more importantly - use [www.google.com/linux](www.google.com/linux)  

The UbuntuGuide is without a doubt the best single point of reference I've seen (and I've been in I.T. for almost 20 years) of any operating system and this includes Windows and Mac's.  The UbuntuGuide literally walks you through a complete system setup step by step while attempting to teach. IT IS NOT a guide to get you a complete system in a few minutes.There's too many options available and just that much to a Linux System that will prevent this. As with any set of instructions, procedure or guide, you're advised to read through first and understand the steps BEFORE attempting those actions. 

Your reference to "Commenting" tells me you aren't reading. 
Pasted from Ubuntuguide.org - Adding Repositories - Actual text from the Sources file text
--------------------------------------
## Add comments (##) in front of any line to remove it from being checked.   

As it states, you ad a # or ## at the beginning of the line to comment that line out. The provided text is meant for you to copy & paste it into your sources.list file as is. They provided everything for you. The commenting was informational as not everyone uses all the same repositories available. In fact some are incompatible however the ones listed in the guide are safe to use "as-is". 

The guide provides all the commands for you so you only need to copy - paste into a Konsole/Terminal Window. Amplifying text is provided in narrative form to assist. However, the entire Linux Bible is already on your system. In fact it's on EVERY Linux OS. It's called the Manual. Open a Konsole or Terminal window and type 

man (topic, question, command etc)
Example:  man sources.list --- or---- man make

will provide the documented info for that topic or command, all variables, it's options etc including examples. 

I strongly encourage you to visit your local bookstore and pick up the  "Linux for Dummies" Teach yourself Linux in 24 hours book. Not trying to insult you here, I'm sure your familiar with and have seen the series before. The book won't necessarily cover X/K/E/Ubuntu flavors however, aside from the package management, it's enough to get you started. It's actually a pretty neat book with all sorts of projects as well. 

While I apologize for letting things get to this point, I can't stress enough how important it is to **READ** thoroughly **BEFORE** executing. Oh and patience! Computing is technical and VERY detail oriented. It's a safe bet you take everything you read literally and exactly as stated. 

While you embark on this I assure you that YOU WILL kill or toast something. It's part of the learning process.  I've used Red Hat, Fedora (all), Suse, Novell Suse, Mandrake, Mandriva, Ubuntu, Saboyan, Debian, Knoppix and a few others to experiment with on both 32bit and 64bit versions. As an I.T. Professional, the Ubuntu flavor is by far the best I've found for any end user desktop system. It's completeness, attention to detail, performance, ease of use, documentation, support  and forums are without a doubt far superior to those mentioned above.  Why do you think Dell chose this platform?

I assure you that we will be here to assist you to the best of our ability however I request that you please read and pay attention to detail. The Ubuntuguide.org site.as I've referenced and provided excerpts from has all your answers for now. 

:popcorn:

---

### Post by natacho on 2007-06-29
When i try to record sound whit my kubuntu + dv9207us i have a horrible back noise. There is any solution?

---

### Post by old_salt on 2007-06-29
> **natacho said:**
> When i try to record sound whit my kubuntu + dv9207us i have a horrible back noise. There is any solution?

Can you be a little more specific and explain what it is your doing and the apps your using?

---

### Post by old_salt on 2007-06-29
Tribe 2 release has been announced. I've been playing around with it a little under VMware and I like what I'm seeing. 
[B][SIZE="3"]
PLEASE NOTE: The Tribe 2 release of Kubuntu 7.10 is FOR TESTING PURPOSES ONLY !!!!! It is NOT a valid release and therefore should be treated as experimental ONLY!!! Please read the Ubuntu 7.10 release notes.[/SIZE][/B]

The minor changes to the KDE 3.5.7 interface are a nice and long overdue change. The kernel is 2.6.22-7 and appears to be working very well even though I've installed the 32bit flavor under VMware on my 64bit base install of Kubuntu 7.04. Still haven't been able to get the 64bit install to work under VMware. I'll research that. There's a lot of work and effort involved with this release and I believe that some of the workarounds required of 7.04 for the DV9000 series laptop will be history once this version is completed and released. More support and included apps / libraries for multimedia capabilities is promised. One issue on this note however is I have no sound. Unsure if this was due to VMware or what. I also noticed on bootup that the USB Filesystem is not yet supported so be advised. I'm sure it will later on.

I like the inclusion of the gdebi installer. Makes things smoother I think and bridges the core of the various flavors of X/K/E/Ubuntu better. 

I'l post another update later today after spending more time on this.

UPDATE --------- Sound now works. I forgot to add the Sound system to the VM config....

Update 2 -------- Used Ubuntuguide for Fesity and successfully added all multimedia add-ons without a hitch and I didn't have to add, change or modify the default repos list either.

---

### Post by EXCiD3 on 2007-06-30
Sorry about my little rant...i was so pissed off at the moment...but i have my computer running almost exactly how i want it right now so...bring on the problems!

CAPS LOCK - cruise control for awesomeness

---

### Post by FOBS1 on 2007-07-01
> **lightningstormz said:**
> I have received this error when I tried acpi=off ,"/bin/sh:can't access tty; job control turned off" I then arrive at something called BusyBox v1.1.3. It looks like some type of command prompt but I don't know what to do from here. I also noticed that for a split second I get a message saying something about not being able to access memory.

I have the same problem - always.  Brand new v9500t Core 2 Duo t7300, 2 gigs, 511mb Nvidia GeForce 8600M GS Intel 4965AGNw/Bluetooth.
Sort of expected the nvidia to be a problem, but can't even get the LiveCD to boot.  Hangs at "Running; script/casper - premount"

CD checks and works in other computers.

Knoppix 5.1.1 loads, Gentoo gets to gdm, can't start X, PCLinuxOS boots in safe graphics mode.  

Tried all the noapic, nolapic, noscsi, noirqpol, nosmp combinations in standard and safe graphics modes.  It just "can't access tty"

Any help appreciated - I don't want to validate Vista until I can load Ubuntu.

---

### Post by EXCiD3 on 2007-07-02
Here's a link to [ SOLUTION TO /bin/sh: can't access tty; job control turned off]("http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control"). Lemme know if this works.

---

### Post by EXCiD3 on 2007-07-02
> Here's a link to  SOLUTION TO /bin/sh: can't access tty; job control turned off. Lemme know if this works.

This is probably caused by having an 8600 video card in your laptop.

---

### Post by FOBS1 on 2007-07-03
> **EXCiD3 said:**
> This is probably caused by having an 8600 video card in your laptop.

Thanks for the link.  I got a lot further with the tip - but not all the way.  I agree that the 8600 is probably the problem.  From other discussions, I am hoping that drivers become available soon.  I'm learning a lot and appreciate the time and effort people are putting helping those with problems

---

### Post by EXCiD3 on 2007-07-03
> **FOBS1 said:**
> Thanks for the link.  I got a lot further with the tip - but not all the way.  I agree that the 8600 is probably the problem.  From other discussions, I am hoping that drivers become available soon.  I'm learning a lot and appreciate the time and effort people are putting helping those with problems

Without you guys on the forums i sure wouldn't be using linux...There is no way i could have figured all this stuff out without this place. So what are your other problems that stopped you? My friend just bought an ASUS and he was having the same problem because he has the same video card. If i can get his working, i'll post a how-to or something.

*EDIT* Those of you with the 8000 series nvidia cards might want to check this link out: [http://ubuntuforums.org/showthread.php?t=479158&highlight=asus+g1s]("http://ubuntuforums.org/showthread.php?t=479158&highlight=asus+g1s"). It talks about install ubuntu on the Asus G1S, Its the gaming laptop that my friend has. Some of the stuff, especially the video card section, will probably relate heavily with getting ubuntu on the dv9500 or others.

---

### Post by disque71 on 2007-07-04
installed linux today and just wanted to post my results

i have a dv9207us
intel core duo 32bit with intel wireless chipset

tried to install Kubuntu 7.04 

followed this guide to repartition and dual boot with vista already installed first
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

install went fine
added noapic option
got to desktop
unfortunately did not recognize wireless chip set

so...
popped in Ubuntu 7.04
repartitioned
added noapic option within grub boot menu
got to desktop
wireless works perfect

haven't tried out all that much so i am unsure of complete functionality but flash and audio seem to be working just fine

following guide on [page 9]("http://ubuntuforums.org/showthread.php?t=431815&highlight=dv9000&page=9") of this post, as it is most excellent, and [ubtuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

will check back after a week or so and add some updates

---

### Post by EXCiD3 on 2007-07-04
Glad to see someone can read the previous pages of this thread for once... ;) Glad we could help!

---

### Post by disque71 on 2007-07-04
Compiz Fusion Update - dv9207us

if you have an nvidia card and 
intend to install compiz fusion
be sure to read

[http://compiz.org/NVidia]("http://compiz.org/NVidia")

i wasted a good bit of time searching the forums for a solution

---

### Post by MarsdaleSA on 2007-07-04
elj4176

Hope you have resolved your beryl issues by now... if not...

I recall having this same issue and it is actually documented on the beryl site (can't find a link right now) as well as a few postings in these ubuntu forums and many other locations I'm sure.

Strangely I haven't had the issue again with my last 2 fresh installs (on both my HPdv9309ea and my Desktop AMD X2 both running 7.04 64-bit). I also found that running beryl manager and not turning on desktop effects helped too. My first post so let's hope i have the procedures right. I assume you are fairly new to linux so I'm using as much detail as I can think of.

Anyway, onto helping you. (you might want to print this or write it down)

First off you'll need to make sure you have all the packages - I don't know if you use automatix2 or not but I don't believe in it and see it as a terrible habit. Start a terminal (**Applications -> Accessories -> Terminal**) and type: 

[I]sudo apt-get install beryl-manager beryl-settings emerald emerald-themes beryl-plugins beryl-plugins-data beryl-settings-bindings beryl-settings-simple libberyldecoration0 libberylsettings0 libemeraldengine0 beryl-core
[/I]

these are all the items installed on my machine. You'll notice when this operation is complete you have new items located in Applications -> System Tools. Those being beryl manager and beryl settings manager.

Next, make sure desktop effects is off - System -> Preferences -> Desktop Effects.

if memory serves me correctly you'll now need to edit your xorg.conf file, so - fire up your terminal again.

Safety first!

type:

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backupberyltest*

this backs up your xorg.conf in case you accidentally make a hash of it and need to restore your original configuration.

now type:

 *sudo gedit /etc/X11/xorg.conf*

this takes you to the gedit text editor.

You now need to scroll down until you find the section 'Section "Screen"' - you will find, in this section, the line DefaultDepth - make it 24 as opposed 16 (leave if already 24). Press enter to create a new line and enter the following: 

Option "AddARGBGLXVisuals" "True"

Here is what my xorg.conf screen section looks like:

[B]Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection     *.... and so on*[/B]

Save the file and close it.

now you can either restart the machine or just terminate x by pressing Ctrl+Alt+Backspace (save any work that needs saving before doing so). 

Assuming all went well you are back at your login window. log in as usual. (if not - refer to the last section)

Once logged in, start Applications -> System Tools -> Beryl Manager. 

You should now see a red 'diamond' in your taskbar. right-clicking on it gives you options. I'll leave you to play with most of them yourself but the 3 we want to work with now are Select Window Decorator (select 'standard beryl decorator(emerald)'), Select Window Manager (select beryl) and lastly Emerald Theme manager, this allows you to select a theme.

If all is well then you should now be seeing changes when you click on a theme and all the other wonderful beryl goodiness. I leave further tinkering to you (including setting up beryl to run at boot). While I, like other posters, see beryl as a bit of a show off tool - I do not have it on permanently.

If this did not work for you - try the desktop effects again. and as i said, many sites document this issue. I believe the keywords i used were beryl nvidia no window decorations. 



**If it did not take you to the login window** and you are staring at a black screen with large white text, press Ctrl+Alt+F1 and you'll be taken to a login prompt. use your account as you would to normally login and type the following:

*sudo mv /etc/X11/xorg.conf.backupberyltest /etc/X11/xorg.conf*

then type:

*sudo reboot*

this reboots the machine and all should be back to the way it was.

As a last measure re-install - and please stay away from automatix as much as you can.

Really long post so my apologies.


Dale

---

### Post by rksii on 2007-07-05
I read through all the posts and I never saw a resolution to the problem of USB drives not mounting under 7.04.

I have this problem. I am running on a dv9000. I tried all the stuff discussed previously -- installed pmount, ran lsusb and fdisk -l (and the drive is not listed by either).

/dev/sda is my primary internal HD
/dev/sdb is the second internal HD
There is no /dev/sdc or above
/dev/hda is my cdrom
/dev/mmcblk0 is the built-in card reader (and it works fine)

Maybe this issue is being caused by the internal SATA HDs being named sda and sdb. I'm not sure how to do it but I wonder if it would help to create /dev/sdc.

A couple of other possible clue to the mystery: 

[LIST]
When I don't have any USB drives plugged in (only USB keyboard and mouse) lsusb returns its results very quickly. When I plug in any USB drive (memory stick, ipod or a self-powered HD) lsusb seems to hang for a while before returning results. In every case, however, the USB drive is not listed.
[/LIST][LIST]
If I try to boot with a self-powered USB HD plugged in, GRUB locks up the computer without ever displaying its menu. The last thing it says is "Error 17".
[/LIST]
I'm tempted to go back and try version 6 since someone mentioned that these devices worked in that version. I just don't know what other features I would be loosing if I did that.

---

### Post by mercurymouth on 2007-07-06
Hey guys, new to Ubuntu, and just trying to figure out partitioning for my HP dv9000.  I have dual 100 Gb hard drives.  On HD1 is XP and the HP recovery partition.  HD2 is blank.  I will be using Ubuntu and XP equally.  What is the best way of setting up the partitions?  I would like to store all my multimedia fiiles (about 35 Gb) to be used in both OS's.  I have read that there are stable programs that will allow Ubuntu to read and write to NTFS and Windows to read and write to .ext3.  Is this true?  And if so, what is my best option for partitioning?  I know there are a lot of forums concerning partitioning, but I haven't seen any that deal with dual booting on a laptop with dual HDs... So I'd appreciate any suggestions...  Also, what are the general sizes I should use for swap and /home ?  I have 2 Gb RAM, should my swap be any bigger than that?

---

### Post by EXCiD3 on 2007-07-06
> **disque71 said:**
> Compiz Fusion Update - dv9207us

if you have an nvidia card and 
intend to install compiz fusion
be sure to read

[http://compiz.org/NVidia]("http://compiz.org/NVidia")

i wasted a good bit of time searching the forums for a solution

If anyone has installed beryl, but messed it up, make sure you completely remove or purge all of the packages for it. The same goes for compiz and compiz fusion. This will remove all of the packages including their settings and allow for a fresh install. This is what i had to do with beryl and fixed my problem. before any compositing manager i had installed would not work.

> **rksii said:**
> 
[LIST]
When I don't have any USB drives plugged in (only USB keyboard and mouse) lsusb returns its results very quickly. When I plug in any USB drive (memory stick, ipod or a self-powered HD) lsusb seems to hang for a while before returning results. In every case, however, the USB drive is not listed.
[/LIST][LIST]
If I try to boot with a self-powered USB HD plugged in, GRUB locks up the computer without ever displaying its menu. The last thing it says is "Error 17".
[/LIST]
I'm tempted to go back and try version 6 since someone mentioned that these devices worked in that version. I just don't know what other features I would be loosing if I did that.

I recently plugged in my external ntfs hdd and it would not mount even though i had the automount ntfs automatix script installed. I soon found out that it would not mount because the hdd had not been safely removed upon last removal. I plugged it into my parent's computer and safely removed it, plugged it back into my laptop and it worked just fine. This and my 2 usb thumb drives work perfectly fine, 1 is a corsair flash voyager and the other is a pny U3 2gb. Everything usb works perfectly fine for me. I did notice that if you have a usb hdd attatched and turned on during boot up Grub will crash because it detects another hdd that wasnt there before. To fix that just turn your drive on after your computer passes through grub. External hdd's and thumb drives are completely different.

> **mercurymouth said:**
> Hey guys, new to Ubuntu, and just trying to figure out partitioning for my HP dv9000.  I have dual 100 Gb hard drives.  On HD1 is XP and the HP recovery partition.  HD2 is blank.  I will be using Ubuntu and XP equally.  What is the best way of setting up the partitions?  I would like to store all my multimedia fiiles (about 35 Gb) to be used in both OS's.  I have read that there are stable programs that will allow Ubuntu to read and write to NTFS and Windows to read and write to .ext3.  Is this true?  And if so, what is my best option for partitioning?  I know there are a lot of forums concerning partitioning, but I haven't seen any that deal with dual booting on a laptop with dual HDs... So I'd appreciate any suggestions...  Also, what are the general sizes I should use for swap and /home ?  I have 2 Gb RAM, should my swap be any bigger than that?

Ok here is what i have done to dual boot my computer on my laptop containing 2x 80GB hdd's:

hdd1 contains WinXP, the embedded xp (used only for playing movies and music from CDs/DVDs) and the HP recovery partition. Since i burned off the recovery DVDs there is really no need to have the recovery partition, so i removed that and i did not ever use the HP Quickplay partition so i wiped that also.

Since you wanted a partition between both OS's i would recommend a FAT32 parition. While it will be unable to contain files larger than 4GB (limitation of the filesystem) it will be great for holding multimedia. I would recommend having XP on drive 1 and Ubuntu on drive 2. If you are going to use one more than the other, choose that lesser operating system and partition off about 40GB or so for a FAT32 shared partition. FAT32 is readable by both XP and Ubuntu out of the box and is completely stable where as writing to NTFS on linux or writing to ext3 or winxp may cause problems. 

Because we both have 2GB of ram, you will probably not need a large swap partition. In general the swap partition is equal to the amount of ram you have. This is required for hibernation because anything stored in ram needs to be stored to your harddrive so that it can resume later. I personally chose to have 1GB of swap because i have tweak Feisty to run faster. This improved my boot up and shutdown times and eliminated my need for suspend/hibernate, which are apparently quite unusable as of now. Very little success has been made using suspend or hibernate with the hp laptops so far.

If you have any other questions let us know. We would be glad to help.

---

### Post by old_salt on 2007-07-06
> **mercurymouth said:**
> Hey guys, new to Ubuntu, and just trying to figure out partitioning for my HP dv9000.  I have dual 100 Gb hard drives.  On HD1 is XP and the HP recovery partition.  HD2 is blank.  I will be using Ubuntu and XP equally.  What is the best way of setting up the partitions?  I would like to store all my multimedia fiiles (about 35 Gb) to be used in both OS's.  I have read that there are stable programs that will allow Ubuntu to read and write to NTFS and Windows to read and write to .ext3.  Is this true?  And if so, what is my best option for partitioning?  I know there are a lot of forums concerning partitioning, but I haven't seen any that deal with dual booting on a laptop with dual HDs... So I'd appreciate any suggestions...  Also, what are the general sizes I should use for swap and /home ?  I have 2 Gb RAM, should my swap be any bigger than that?

Quick answer----------
Use Automatix and the NTFS utils from that. It works and you can access those files in read/write capability.

DETAILED----------

- Get your XP setup the way you want it on 1 Disk. 
- Install Ubuntu on Drive 2 and then add in the NTFS Utils from Automatix2 so Linux can access your media files

OR---------------

Install Ubuntu and setup LVM to span both drives and install Vmware-Server and put XP under that

or-----------
carve out a portion from 1 drive or the other or both using FAT file format and mount those equally whenever you boot up from either system. 

To be honest, it depends on how you use or plan on using either OS. On my 160Gb HD I use VMware on Kubuntu 7.04 and let it ride from there. I have no need for Windows except web development and all my video editing, recording, TV viewing and MP3 playing etc are all done on Linux with better results and beeter performance and without hte hassles of the DRM.

---

### Post by mercurymouth on 2007-07-06
OK, thanks guys...  One question... Is Automatix a Linux app?  If I could get ubuntu to read my mp3 files from the NTFS drive that'd probably be best...  Also, do you guys use a /home partition?  If so, how large should that partition be compared with the one w/ the main OS?  Oh, and one more thing, when manually setting up partitions with the GUI install, does it matter what order the partitions are done in?  Thanks again for the help...

---

### Post by EXCiD3 on 2007-07-06
> **mercurymouth said:**
> OK, thanks guys...  One question... Is Automatix a Linux app?  If I could get ubuntu to read my mp3 files from the NTFS drive that'd probably be best...  Also, do you guys use a /home partition?  If so, how large should that partition be compared with the one w/ the main OS?  Oh, and one more thing, when manually setting up partitions with the GUI install, does it matter what order the partitions are done in?  Thanks again for the help...

Automatix IS a linux application that is used for easy installation of commonly used linux applications. I'm actually using it at the moment :D. I don't use a separate /home partition. And no it wont matter what order the partitions are made in as all of the settings will be applied and it wont matter.

Just google Automatix to learn about it, installation is as simple as these 6 steps:
```

Installing Automatix2 on (K,X)Ubuntu 7.04 i386,AMD64 (Feisty) 
From terminal do the following (ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP): 
First Step: 
 echo "deb http://www.getautomatix.com/apt feisty main" | sudo tee -a /etc/apt/sources.list

Second Step: 
 wget http://www.getautomatix.com/keys/automatix2.key

Third Step: 
 gpg --import automatix2.key

Fourth Step: 
gpg --export --armor E23C5FC3 | sudo apt-key add -

Fifth Step: 
 sudo apt-get update

Sixth Step: 
 sudo apt-get install automatix2


```
*taken directly from the Automatix webiste*

---

### Post by EXCiD3 on 2007-07-09
So i just reinstalled WinXP :( I used the recovery DVD's because using a regular XP disc doesn't have SATA support and therefore cant detect the hdd's. Does anyeone know how i can recover my Kubuntu install, the install is safe because i installed it on the second hdd and the Recovery discs only mess with the first hdd...

Basically i think im just looking to reinstall grub to the mbr...i guess. I just need to be able to dual boot using grub.

Any help would be great... i just had a couple things i wanted to save off of that install annd i havent had time to search the forums...

**EDIT**

Fixed the problem by installing grub manually from the live CD. Took me a while before i found a standard Kubuntu WinXP menu.lst entry... Damn Micro$oft...

---

### Post by jmfrey on 2007-07-11
Alright, I have read the entire thread.  If I missed something, please feel free to slap me around.

Just got my new dv9500t, made my Vista recovery disks and proceeded to install Ubuntu (amd64 alternate cd).

Installation went off without a hitch.  However, upon boot-up, the laptop screen blanks out (no power to the lcd) and the system freezes.  It does this after the console login prompt is displayed and the remaining services begin to start running.  I'm assuming it's gdm that's causing the hangup.

Here's what I've tried.

1) Ensured "noapic" in boot command.

2) Removed "quiet" and "splash" from boot command.  This sometimes gets be past the blank lcd, but presents me with a scary looking whitewashed screen and hangs.

3) Added "vga=0x31B" and received a prompt that the resolution entered was wrong.  It asked me for the correct COLUMN x ROW (80 x ##).  Regardless of what I entered, same result.

4) I can boot into recovery mode and can work around the command prompt.  Of course, running "startx" from this command - no display device configured.

It looks like I may need to tweak it from the recovery console and try to set up the display device manually.  Ethernet works so I can work on it from the console.

I tried to install the NVIDIA drivers from their site for x86-64, but it couldn't setup the kernel drivers.  I then followed a long list of dependencies that needed to be installed.

Automatix2 doesn't help since I have not been able to get a graphical display.

Any quick thoughts?

Much appreciate the help and information on this thread.

Jason

HP dv9500t, Intel T7500-2.2GHz, 4GB RAM, Nvidia 8600M GS, 2@SATA-100GB, 4965AGN Network w/Bluetooth

---

### Post by EXCiD3 on 2007-07-11
> **jmfrey said:**
> scary looking whitewashed screen

I have gotten this screen when ever i try to hibernate or sleep. It looks pretty scary so i never tried it since because i didn't want to ruin my screen.

As for getting the display to work, use the text based mode of Envy from the console. Its pretty helpful to either have another computer nearby or print off some of the instructions. This will *hopefully* fix your problem.

---

### Post by cmdln on 2007-07-11
Has anyone been monitoring their hard drive temps?
I have a dv9000t with a t7200. 
My hard drive seems to get pretty steamy.

from smartctl -H /dev/sda
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
190 Temperature_Celsius     0x0022   044   039   045    Old_age   Always   FAILING_NOW 5996715966520

---

### Post by rfrey74 on 2007-07-11
I've noticed that my dv9000z runs pretty hot.  I got a chill pad for it, and it does keep it cool.  I dual boot, and I can tell ya that it stays cooler running Linux that when running XP.  I had an older model HP laptop before this one, and I have to say that they seem to naturally run hot.  It doesn't run hot enough to make me worry about it though.

---

### Post by jmfrey on 2007-07-11
> **EXCiD3 said:**
> I have gotten this screen when ever i try to hibernate or sleep. It looks pretty scary so i never tried it since because i didn't want to ruin my screen.

As for getting the display to work, use the text based mode of Envy from the console. Its pretty helpful to either have another computer nearby or print off some of the instructions. This will *hopefully* fix your problem.

Consider myself officially slapped.  Worked like a charm...  :redface:

Thanks!

Jason

---

### Post by alej on 2007-07-12
Hello everybody, and thank you for all your tips and tricks, they are making the unexpectadly complicated task of installing ubuntu 7.04 in a dv9343eu (Specs: Turion X2 6 64-bit with 2x120 GB disks) more feasable.

 I was wondering if any of you with a dv9000 with two drives can give me some advice on the following:

By factory defaults the laptop comes with the following configuration:
Drive1: sda:  c: Vista OS e: HP recovery
Drive2: sdb:  d: NTFS Partition totally empty

when you boot the laptop and press Esc the BIOS allows you to choose where to boot from (sda, sdb, dvd/cd) This I don-t fully understand since sdb is empty... 

My ideal configuration is the following:
sda: keep as it came
sdb: ubuntu partitions (swap, /, /home at least) and a NTFS Document Backup partition

I was wondering if there is a way to install ubuntu so that instead of using GRUB to choose which OS to load, I could just do that from the BIOS by pressing Esc.

Of course I`ve tried it out already but have only achieved miserable results. When I installed GRUB to /dev/sdb I lost the possibility to boot up from sdb through the BIOS. In other words even though my BIOS sees both drives, it only allows me to boot from the  first one or the CD/DVD. I've attempted reformatting sdb to NTFS but now there is no way I can make it bootable as it was initially. I see that sdb is not described as bootable by the Vista Disk Manager, but I can-t seem to be able to change that using bootrec /fixmbr or anything else since bootrec only recognizes the drive where the OS is installed (c:)

I imagine most of you will recomend to just install grub onto the sda MBR and dual boot from there, but I was wondering if it is possible to do otherwise. 

On the other hand I was wondering if anyone could tell me how I can reconfigure the sdb drive so it is bootable again. 

Thankyou guys in advance for your time and interest

---

### Post by cmdln on 2007-07-12
The only way you would be able to select what os to boot from bios is if you installed linux bios. I dont think anyone has sucessfully done that yet. However you could possibly select which drive to boot from by pressing escape. Windows will have its boot loader setup for it already, Then you still need to install a boot loader on the second drive. .... Seems like extra work for no added benefit to me but up to you.

---

### Post by cmdln on 2007-07-12
> **rfrey74 said:**
> I've noticed that my dv9000z runs pretty hot.  I got a chill pad for it, and it does keep it cool.  I dual boot, and I can tell ya that it stays cooler running Linux that when running XP.  I had an older model HP laptop before this one, and I have to say that they seem to naturally run hot.  It doesn't run hot enough to make me worry about it though.
Which chillpad?
I have been looking around a bit but I cannot seem to find one large enough for a 17inch notebook. The largest I have found is the one from antec i believe it measures 13 inches in width, still several inches short of my laptop width and i think it was about an inch short on depth.

---

### Post by jmfrey on 2007-07-12
Has anyone with an Intel 4965 wireless card gotten it to work?

I've seen references to other Intel cards working out of the box, but not the 4965.

I've been playing around with some native drivers, but so far no luck.



Jason


HP dv9500t, Intel T7500-2.2GHz, 4GB RAM, Nvidia 8600M GS, 2@SATA-100GB, 4965AGN Network w/Bluetooth

---

### Post by EXCiD3 on 2007-07-12
> **alej said:**
> Hello everybody, and thank you for all your tips and tricks, they are making the unexpectadly complicated task of installing ubuntu 7.04 in a dv9343eu (Specs: Turion X2 6 64-bit with 2x120 GB disks) more feasable.

 I was wondering if any of you with a dv9000 with two drives can give me some advice on the following:

By factory defaults the laptop comes with the following configuration:
Drive1: sda:  c: Vista OS e: HP recovery
Drive2: sdb:  d: NTFS Partition totally empty

when you boot the laptop and press Esc the BIOS allows you to choose where to boot from (sda, sdb, dvd/cd) This I don-t fully understand since sdb is empty... 

My ideal configuration is the following:
sda: keep as it came
sdb: ubuntu partitions (swap, /, /home at least) and a NTFS Document Backup partition

I was wondering if there is a way to install ubuntu so that instead of using GRUB to choose which OS to load, I could just do that from the BIOS by pressing Esc.

Of course I`ve tried it out already but have only achieved miserable results. When I installed GRUB to /dev/sdb I lost the possibility to boot up from sdb through the BIOS. In other words even though my BIOS sees both drives, it only allows me to boot from the  first one or the CD/DVD. I've attempted reformatting sdb to NTFS but now there is no way I can make it bootable as it was initially. I see that sdb is not described as bootable by the Vista Disk Manager, but I can-t seem to be able to change that using bootrec /fixmbr or anything else since bootrec only recognizes the drive where the OS is installed (c:)

I imagine most of you will recomend to just install grub onto the sda MBR and dual boot from there, but I was wondering if it is possible to do otherwise. 

On the other hand I was wondering if anyone could tell me how I can reconfigure the sdb drive so it is bootable again. 

Thankyou guys in advance for your time and interest

Here's what you can do: Install GRUB to the MBR of the second drive. During installation of Ubuntu on the last page, choose the advanced button and tell it to install to the second drive's MBR. This will also detect Vista on your other drive but will give you those options on GRUB. If everything goes well, you can choose to boot to the first hdd and will only get Vista and you can choose the other drive where you will get GRUB. My BIOS does not support this because there is always the possibility of someone buying this laptop with only 1 hdd therefore they couldn't add an option to choose WHICH hdd to boot to.

> **cmdln said:**
> Which chillpad?
I have been looking around a bit but I cannot seem to find one large enough for a 17inch notebook. The largest I have found is the one from antec i believe it measures 13 inches in width, still several inches short of my laptop width and i think it was about an inch short on depth.

If you are looking for a chillpad check out the BYTECC one on Newegg.com. Here's the link to it: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834999336]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834999336")
I really like it, but i have to have it hang over the front so i can still use my headphone jacks, and so it wont tip over backwards. ;) It has a nice ergonomic tilt to it also.

> **jmfrey said:**
> Has anyone with an Intel 4965 wireless card gotten it to work?

I've seen references to other Intel cards working out of the box, but not the 4965.

I've been playing around with some native drivers, but so far no luck.

To get your wireless card working check out this post: [http://ubuntuforums.org/showthread.php?t=493095&highlight=4965]("http://ubuntuforums.org/showthread.php?t=493095&highlight=4965")
Looks like there is somewhat of a tutorial there... I also found this: [http://ubuntuforums.org/showthread.php?t=396204&highlight=Intel+4965]("http://ubuntuforums.org/showthread.php?t=396204&highlight=Intel+4965") but i dont know how much help there is on that thread.


Anyone who would like to help me compile the scattered information on this thread would be greatly appreciated. I would like to collect everything i can so that i can edit the first post and have a nicely organized almost "tutorial" like post so it is easy for everyone to find. Contact me if you want to help. ;)

---

### Post by jmfrey on 2007-07-13
> **EXCiD3 said:**
> 
To get your wireless card working check out this post: [http://ubuntuforums.org/showthread.php?t=493095&highlight=4965]("http://ubuntuforums.org/showthread.php?t=493095&highlight=4965")




The directions in this thread work to get the card recognized and installed.  I'm having problems with activating to a network though.  When attempting to activate the system hangs completely.


Everything was straight forward with regards to the installation, however.

One key note:

Use the iwlwifi-0.0.38 driver, not the iwlwifi-0.1.1 version.

The iwlwifi-0.1.1 did not work for me.

Jason

---

### Post by alej on 2007-07-13
*[quote=EXCiD3;3009415]Here's what you can do: Install GRUB to the MBR of the second drive. During installation of Ubuntu on the last page, choose the advanced button and tell it to install to the second drive's MBR. This will also detect Vista on your other drive but will give you those options on GRUB. If everything goes well, you can choose to boot to the first hdd and will only get Vista and you can choose the other drive where you will get GRUB. My BIOS does not support this because there is always the possibility of someone buying this laptop with only 1 hdd therefore they couldn't add an option to choose WHICH hdd to boot to*.
 
 
[COLOR=black]Thanks for the advice, ... What you described was what I initially tried to do, i.e. only installing GRUB in the second drive's MBR. I must say that after wasting considerable time taking out drives and trying everything else I could imagine I must accept I should have accepted your last phrase. [/COLOR]
 
[COLOR=black]:( My dv9343eu laptop is designed to only boot from the BIOS to whatever disk is in bay 1  MBR.  I prooved it to myslef by taking out Drive from bay 1 and installing Ubuntu to drive 2. After installation and bootup, I would get a message saying it couldn't find any OS. [/COLOR]
 
[COLOR=#000000]I feel defeated, evermore since I can clearly remember that with the initial factory settings, when I pressed Esc I would get to select from either drive or the CD/DVD... I'm actually starting to believe that the available options "Notebook Disk" or "Disco duro del portátil"[=Notebook disk in spanish] actually both pointed to the same MBR.... [/COLOR]
 
[COLOR=#000000]Therefore I give up with my ideal config... i still think it would be neat though to have the possibility of chosing from which drive to boot with this notebook.... guess its just that I like the idea of keeping both OSs with the minimum impact on each other and fully recoverable without having to continually tweak GRUB o bootrec loader...[/COLOR]
 
[COLOR=#000000]So I call it a night... [/COLOR]
 
[COLOR=#000000]while felling grateful for the noapic option.....[/COLOR]
[SIZE=2][/SIZE]

---

### Post by jmfrey on 2007-07-14
Sound on the dv9500t uses the Realtek 268 codec.  ALSA does not have support for this in their current branch.  They did mention it is in their HG branch.  Sound is something I can wait for a more stable codebase for.   see - [http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001368.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001368.html)

Intel 4965AGN wireless card is identified using the native linux drivers, but am still receiving segmentation faults when attempting to connect to WPA-enabled networks.

I'm actually re-installing my system with debian to test some rumors on performance increases, so I will not be working directly with ubuntu distros (at least for the time being).

---

### Post by Spelley on 2007-07-15
Got the webcam working on my DV9000z laptop. Apparently, there are two different webcams (at least) for the HP Pavilions: Ricoh or Sonix/Microdia. This should work for the Sonix / Microdia variant.

Open a console and enter:

lsusb

If it looks similar to the following

Bus 002 Device 002: ID 0c45:62c0 Microdia

Then give this a shot.

1) Install subversion from the repos. ("apt-get install subversion")

2) open a console and enter:

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd /linux-uvc/linux-uvc/trunk
gedit Makefile

3) This was the tricky part. Ubuntu does things differently here. Change the following in the Makefile:

INSTALL_MOD_DIR := usb/media
to 
INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo

4) Save it and close. In the console enter:

make
sudo make install
sudo modprobe uvcvideo
gstreamer-properties

5) Under VIDEO, select v4l2 and choose USB 2.0 for device.

DONE. This worked for me in Ekiga and Cheese. Haven't tried anything else.

---

### Post by jmfrey on 2007-07-15
Intel 4965 - got it working on Debian Lenny,  but it should work on Ubuntu as well.

I used the latest kernel from kernel.org which has built-in support for mac80211.  I compiled that kernel with mac80211 enabled and then added the drivers and firmware per the instructions at [http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)

I'm using Gnome and the network manager worked perfectly to setup the WPA.

---

### Post by scunc_dvl on 2007-07-16
I guess I'm one for finding obsucre bugs, but I would surely like to have the **lid closure** thing fixed. Lid closure seems to be detected only once, and the ACPI software seems to flake out judging by the log messages given, and Linux doesn't seem to detect any subsequent lid closures.

If anything, the software that handles that could be completely restarted as a quick kludge. I sure would like to have this thing "lock" every time I close the lid! Thanks for your help.

---

### Post by cessna_89702 on 2007-07-16
My live disk doesnt work. I try to boot it and when the screen for login should pop up it just has all these lines going through the screen and doesnt start.any ideas?

---

### Post by EXCiD3 on 2007-07-16
> **cessna_89702 said:**
> My live disk doesnt work. I try to boot it and when the screen for login should pop up it just has all these lines going through the screen and doesnt start.any ideas?

If you have any AMD based laptop or a newer dv9500 series Hp laptop you need custom boot options and/or use the alternate cd to install. Please read through previous posts, as this problem has already been covered. I am trying to collect a bunch of information and create a "tutorial" page for everything we have fixed so far. If someone wants to help me collect the info let me know.

---

### Post by BluChaoz on 2007-07-17
Ok I was searching throught the topics and I may have missed it but I never really saw what I was looking for. I am getting ready to pull off windows and install Ubuntu Studio on my dv9208nr. I was wondering if anyone knew of any problems I may have when I go about this. It's an AMD Turion 64x2 Mobile Technology TL-50 1.60 GHZ. With 64megs of shared video memory. Not to worried about using the MIC or using the Wireless Card, main concern is video, headphones and being able to code my MUD. So if you think it should be a clean install sweet, if not please feel free to reply to this or send me a PM with something that may be able to assist in the install.

---

### Post by cessna_89702 on 2007-07-17
> **EXCiD3 said:**
> If you have any AMD based laptop or a newer dv9500 series Hp laptop you need custom boot options and/or use the alternate cd to install. Please read through previous posts, as this problem has already been covered. I am trying to collect a bunch of information and create a "tutorial" page for everything we have fixed so far. If someone wants to help me collect the info let me know.

Noapic worked when I added it. I have a dv9000z

---

### Post by yiannism on 2007-07-19
Hello there....Am new to this forum as well as to Ubuntu.
i got my laptop which is a Dv9000 and tried to install Ubuntu feisty 7.04..
1st problem after booting from cd, notebook halt, could not see the desktop....
After that i pressed F4 in the installation screen on the cd and tried to change resolution to 1024x... this fixed my problem. while trying to install ubuntu, and to tell you what ..i removed the 2nd hdd from the notebook and i cleared everything on the 1st so i will start with anew clean and fresh hard drive / partitioning in ubuntu. it installed everything ok and amazingly fast too.
at the end where it needs to reboot the computer, ubuntu is shutting down...then it ejects the cd tray so u get the cd out..close the tray and press ENTER to reboot...this never worked.....i dont know why but i tried installation 4 times...same problem...

So i figure out i will switch off manuall the notebook and reboot...

this is the strange part...first i get ubuntu loading orange thing going left-right, after that i get to prompt asking to fsck the disk..and over there is halts, stops and notebook does not respond...

This is so annoying trying to install such a great OS like Ubuntu but not be able to work it out..

I would be please if anyone could help me on that, cuz am really up to head with Windows and microsoft..

ah to tell u specs, notebook is an AMD turion X2 2Ghz , 2GB ram, 1 HDD (removed 2nd) nvidia 256MB go express.

Cheers !!!

---

### Post by MikeDK on 2007-07-19
Hi yiannism! i totally agree with you, i had that same problem, untill i got some help.

the fschk, is the system, doing a selfcheck of sytem-files every 20th mount of filesystem or so, wich you actually do every time you reboot.

The install: Have you tryed using the 1024x768x32 instead of 1024x768x16 or else try just booting on safe graphics mode,
if you managed to get ubuntu installed and can't bootup, dont worry.
as soon you'll see the grub loading on bootscreen, press esc. and select recovery-mode and hit enter
if it hangs on bootin into recovery just try a few times.
now when in recovery-mode be careful we're in as root here, so dont mess up, just go along.
IF and only if you machine's complaining about firmware not being loaded, you should first of do```
apt-get install bcm43xx-fwcutter
```
it will now ask you if you want to fetch and extract the firmware, Yes to that.
and your done
Now the fschk, is probably not far away, so im gonna guide you through how to stop the fschk from starting.
as i know the fschk makes the laptop hang and freeze, mine did a dv9000eu series.
first of im gonna give you a link to my screenshot of fstab, so you'll know what im talkin about [HTML]http://www.4shared.com/file/20320671/d3407e25/terminal-fstab-screenie.html[/HTML]
Here it is, open a terminal and write this command ```
sudo nano -w /etc/fstab
``` and hit enter
first maximize the window of fstab so you can see all the text, then as you see in my screenshot, the 1 needs to be changed to a 0.
To safe the work you've done press and hold Ctrl and hit othen hit enter, to exit the shell-terminal press and hold Ctrl and hit x.
and your done.

**THIS is only if you have an Nvidia card in your laptop**

Next thing is your resolution as i know the vesa-driver does not go higher than 1280x1024
if your screen has a resolution of 1440x900 you should install the nvidia-glx-new package```
apt-get install nvidia-glx-new
```
then do a reconfigure of xorg```
dpkg-reconfigure xserver-xorg
```
and go through it by using arrows,tab and space
select with space
then add Option         "RenderAccel"    "True" to your xorg.conf
```
nano /etc/X11/xorg.conf
```
go to section Device: go down so you have the cursor placed under Driver and hit tab once, then write Option with a big O, hit tab twice and write "RenderAccel" then hit tab once and write "On"
And you should be done.
```
reboot
```
if it doesnt work and get to login screen, then go back to recovery-mode and check your xorg.conf, you should check for resolution-settings go down to Section "Screen" and see if your screenresolution is 1440x900, if it isnt correct it and safe the file as you did before and reboot again.
Kind regards MikeDK

Hope it works for you, or else just keep asking

---

### Post by nelliott71 on 2007-07-20
I have a DV9207US, I can't get gparted to recognize the drive.

I'm using the most recent version from the gparted site.  I tried several different boot configurations from the grub menu, including the ones that say 'HP'

Google isn't helping me much either.  =(

Several configs result in unusable X configuration (scrambled video)

A few boot X, but then say "No devices detected"

This is making me feel like a noob.:confused:

--------------------

Update - I'm stupid.  I didn't realize there was a partitioning tool included on the install CD.... which works fine!

So now I have Kubuntu 7.04 installed (1280x800 yuk!)   Now I just need to get the NVIDIA driver loaded, do my updates,etc.

Hopefully I can keep my head out of my rear end for the rest of the install. =D

---

### Post by #Reistlehr- on 2007-07-21
nelliott71: best bet, go to getautomatix.com (i think), and install the nvidia drivers with that. Works perfect every time. But! if you want to use beryl, you will have to use the command: nvidia-xconfig --add-argb-glx-visuals, then go into the xorg.con (/etc/X11) and change the DefaultDepth (i thunk under screen?) to 24.

Anyone get suspend or hibernate to work?

---

### Post by jonathanmotes on 2007-07-21
Has anyone had trouble with the force fsck hanging infinitely? I just installed Ubuntu on my two week old HP dv9428nr laptop and I haven't been able to boot since it started trying to do a disk check. I have posted a thread [here]("http://ubuntuforums.org/showthread.php?t=505787"), but it is not getting many reads. I was able to mount the disk using the GParted live disc terminal and have been looking for a forcefsck file but haven't been able to find it. Please help!

---

### Post by MikeDK on 2007-07-21
look in the post's abovejonathanmotes, yes some of us have had that same problem yes

---

### Post by danimall on 2007-07-21
I have an HP dv6408nr notebook and I was able to get Ubuntu 6.10 to install correctly onto my computer using the live CD, but now when I try to start it up it will get to the Ubuntu loading splash screen and then just go completely blank. Is this an issue with the Nvidia drivers for my graphics card? If so then how would I work around it? I am still kind of new to linux so if you have any basic solutions then that would be great. My specs are listed below.

Microprocessor 1.8 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-56
Microprocessor Cache 512KB+512KB L2 Cache
Memory 1024 MB DDR2 System Memory (2 Dimm)
Memory Max Max supported 2048 MB
Video Graphics NVIDIA GeForce Go 6150 (UMA)
Video Memory Up to 287 MB

It probably doesn't make a difference but I am dual booting Ubuntu 6.10 and Vista.

---

### Post by bselk on 2007-07-21
I have an HP Pavillion dv8400  with all the features (TV card, bluetooth, nvidea graphics, duel core 2 processor). Just installed kubuntu and it looks great. has anybody got the vmware software to work?
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by jmfrey on 2007-07-22
SOUND!!!  GLORIOUS SOUND!!!

Realtek 268 chipset working.

First let me make a disclaimer that I'm running my dv9500t on Debian Lenny with a custom 2.6.22.1 kernel, but the instructions I followed were from the Ubuntu forum.  Pretty simple patch and re-compile of the alsa-drivers.

[http://ubuntuforums.org/showthread.php?p=3000405#post3000405](http://ubuntuforums.org/showthread.php?p=3000405#post3000405)

Enjoy...

---

### Post by EXCiD3 on 2007-07-22
> **bselk said:**
> I have an HP Pavillion dv8400  with all the features (TV card, bluetooth, nvidea graphics, duel core 2 processor). Just installed kubuntu and it looks great. has anybody got the vmware software to work?
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

i have had VMWare working, but i personally like VirtualBox much better. I used automatix2 to install it.

---

### Post by Snipersnest on 2007-07-22
Hi.. I'm new to the Laptop area. I struggled a bit tonight to get my DV9010us to install Ubuntu but got it going finally.
 
Now I'd like to get my wireless going... Do you guys have any links that would help me get my "Dell Wireless 1390 WLAN Mini-PCI Card" working good?
 
By default device manager says "info.linux.drver string bcm43xx"  so I'm guess I need the bcm43xx stuff.
 
If anybody has ideas please let me know! Thanks

---

### Post by jediborger on 2007-07-23
Does anyone know what the port is on the front left corner that is in between the card reader and the usb ports?
No where does HP even tell you what all is on the computer or even a diagram of the ports. This one little port has a picture of a 3 knobs around a circle. Any ideas?

---

### Post by jmfrey on 2007-07-23
> **jediborger said:**
> Does anyone know what the port is on the front left corner that is in between the card reader and the usb ports?
No where does HP even tell you what all is on the computer or even a diagram of the ports. This one little port has a picture of a 3 knobs around a circle. Any ideas?

Firewire 400.

---

### Post by jmfrey on 2007-07-23
> **Snipersnest said:**
> Hi.. I'm new to the Laptop area. I struggled a bit tonight to get my DV9010us to install Ubuntu but got it going finally.
 
Now I'd like to get my wireless going... Do you guys have any links that would help me get my "Dell Wireless 1390 WLAN Mini-PCI Card" working good?
 
By default device manager says "info.linux.drver string bcm43xx"  so I'm guess I need the bcm43xx stuff.
 
If anybody has ideas please let me know! Thanks

The information in this thread on the broadcom wireless card should work for you.

---

### Post by Snipersnest on 2007-07-23
> **jmfrey said:**
> The information in this thread on the broadcom wireless card should work for you.
 
So what did I miss or am I missing?
 
I followed EVERYTHING in this guide [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-ea76065f30b99d3b8472289cd049e2b141856b55](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-ea76065f30b99d3b8472289cd049e2b141856b55)
 
But after restarting to test result iwconfig doesn't see wlan0 at all..Do I have to start over if so how? 
 
2 things I hate about Linux... wireless and video drivers...biggest set back on Linux to make its come back for an everyday OS.

---

### Post by EXCiD3 on 2007-07-23
Video drivers arent too much of a problem when you have slick installers like envy, but wireless drivers have a long ways to come except the intel ones! ;) You guys should have just bought a dv9000t...Sorry about that little rant ;)

Try using this Howto to install the wireless drivers: [http://ubuntuforums.org/showthread.php?t=434946]("http://ubuntuforums.org/showthread.php?t=434946")

---

### Post by sakul07 on 2007-07-24
I just bought my HP dv9000 and installed Feisty Fawn! and most of the things worked awesome! nvidia, microphones, webcam, usb, speakers, lirc, cd burner worked all fine.

Things that are not working:
-My "sd-ms-mmc-xd"  reader is not working (i only  tried with a memory stick)
-I can't mute the beep sound of quickplay (and it's already muted from the bios)

any ideas?

---

### Post by Druke on 2007-07-25
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

this guide for wifi has worked for me many times without fail. However you have to read the guide to the letter, there are parts where you have to sudo -s (or simply sudo su) to do some echo'n.

read it well!


I just reformatted my laptop trying to pimp it out for defcon (and RoR development) and have gotten compiz fusion, dvd playback and wifi working great. Now i just need to get my webcam working and going to toil through the 20+ pages of this thread

---

### Post by EXCiD3 on 2007-07-26
> **sakul07 said:**
> I just bought my HP dv9000 and installed Feisty Fawn! and most of the things worked awesome! nvidia, microphones, webcam, usb, speakers, lirc, cd burner worked all fine.

Things that are not working:
-My "sd-ms-mmc-xd"  reader is not working (i only  tried with a memory stick)
-I can't mute the beep sound of quickplay (and it's already muted from the bios)

any ideas?

Are you sure, I muted mine in the BIOS and have never heard it since. Sure you applied those settings?

> **Druke said:**
> [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)Now i just need to get my webcam working and going to toil through the 20+ pages of this thread

lol, I'm really glad i started this thread. We have helped out a crapload of ppl. Want to help me organize the stuff so I can edit the first post with all the links/code we have covered before it gets too messy? I'm trying to find some time to do this but i could use some help. If someone wants to layout all the steps for installing it on a dv9000z, plz pm me or IM me!

---

### Post by MikeDK on 2007-07-26
just wanna know if some of you have the dv9000eu, and if, then do you have the BIOS bug under bootup along with the "failed to allocate mem resources"

Kind Regards MikeDK

BTW. tryed the gutsy-upgrade from feisty, and saw the Bios bug was gone but stil the "failed to allocate mem resources" was still there, hope it gets better in the full release

---

### Post by Caste#02 on 2007-07-27
Hi everybody!

I've a little problem with *vanilla* kernel: **every time** that I try to recompile it - even if I don't touch or remove nothing, I've tried it -, when I boot **PC** with the new one I heard like a **hiss** from left side of the keyboard. Anyone has the same problem?

It's annoying, especially 'cause every time that I wanna stop it I have to **reboot with the official Ubuntu kernel**...
I've called **HP** directly, but the '*HP guy*' - I don't know which is the english word for the italian 'centralinista' - said to me that he can't do anything if I don't reinstall **Windows** (*and I really don't want to*).
Can anyone help me, please?

Thanks in advance, and excuse me for my english.

:)

**P.S.** The most important thing: I have an **HP DV9059EA**.

---

### Post by jmfrey on 2007-07-27
The one frustration I have with the dv9500t is the damn right shift key being a single width key and the up arrow being just next to it.  I'm constantly hitting the up arrow and screwing up things, especially if I catch them both.

Maybe I'll look into remapping the arrow keys, since I have them on the numlock anyway.  Anyone tried this?

---

### Post by richk14 on 2007-07-27
Hey, i dunno if these forums are still active, but i have a HP DV9000, and i was wondering if there is a way to tighten up the hinge for the monitor, its a 17"er.. any help would be great, thanks alot!!

-Richk14

---

### Post by sakul07 on 2007-07-27
About the beep sound in Quickplay buttons... yes, its disable in the bios, but still sounding....

About re maping the keyboard, i did it, and works perfecly.... see this post: [http://ubuntuforums.org/showthread.php?t=90040](http://ubuntuforums.org/showthread.php?t=90040)

---

### Post by netsplit on 2007-07-28
I've read the whole entire thread, and I still can't get the livecd to boot.

From postings and a link or two I can gather:

- If you have a dv9000z you're going to have problems
- all AMD based systems are dv9000z`s
- since my dv9208nr is AMD based it's a dv9000z

I really want to try ubuntu on my laptop. I used pclinuxos and it was nice but I'd like to find something that gives me less trouble getting things to compile (it was always missing things!, and what I needed was seldom in synaptic)

I've tried the kubuntu 7.04 for x86, gives bios bug error (I can reboot and get the error number if it'll help), then  normal boot, then some errors about bmc3xx.firmware.fw or something missing (that should be easy to fix when it actually boots), then normal booting then it shows this weird white and grayish screen that looks kind of like a lavalamp. That screen freaks me out because is it dangrous to my lcd screen? It freezes there.


the AMD64 version doesn't give me the bios bug error, but right before the boot screen it shows the weird white screen again for a few seconds then boots. Gives the bcm3xx errors then freezes on starting network connections.


Any help would be most appriciated.

---

### Post by MikeDK on 2007-07-28
> **netsplit said:**
> I've read the whole entire thread, and I still can't get the livecd to boot.

From postings and a link or two I can gather:

- If you have a dv9000z you're going to have problems
- all AMD based systems are dv9000z`s
- since my dv9208nr is AMD based it's a dv9000z

I really want to try ubuntu on my laptop. I used pclinuxos and it was nice but I'd like to find something that gives me less trouble getting things to compile (it was always missing things!, and what I needed was seldom in synaptic)

I've tried the kubuntu 7.04 for x86, gives bios bug error (I can reboot and get the error number if it'll help), then  normal boot, then some errors about bmc3xx.firmware.fw or something missing (that should be easy to fix when it actually boots), then normal booting then it shows this weird white and grayish screen that looks kind of like a lavalamp. That screen freaks me out because is it dangrous to my lcd screen? It freezes there.


the AMD64 version doesn't give me the bios bug error, but right before the boot screen it shows the weird white screen again for a few seconds then boots. Gives the bcm3xx errors then freezes on starting network connections.


Any help would be most appriciated.

hi there!
bout the bcm43xx firmware you have to install the bcm43xx-fwcutter package to get that error fixed, its the the driver for the wireless card Broadcom 43xx series. thats probably the reason the screen freezes on starting the network, but try do ```
sudo apt-get install bcm43xx-fwcutter
```
This should work

Kind Regads MikeDK.
P.S. maybe i should go fetch the AMD64 edition to get rid of the BIOS bug i get that to also DV9000z but bought as an dv9232eu amd64 TL-52 1.6ghz

---

### Post by Snipersnest on 2007-07-28
> **netsplit said:**
> I've read the whole entire thread, and I still can't get the livecd to boot.
 
From postings and a link or two I can gather:
 
- If you have a dv9000z you're going to have problems
- all AMD based systems are dv9000z`s
- since my dv9208nr is AMD based it's a dv9000z
 
I really want to try ubuntu on my laptop. I used pclinuxos and it was nice but I'd like to find something that gives me less trouble getting things to compile (it was always missing things!, and what I needed was seldom in synaptic)
 
I've tried the kubuntu 7.04 for x86, gives bios bug error (I can reboot and get the error number if it'll help), then normal boot, then some errors about bmc3xx.firmware.fw or something missing (that should be easy to fix when it actually boots), then normal booting then it shows this weird white and grayish screen that looks kind of like a lavalamp. That screen freaks me out because is it dangrous to my lcd screen? It freezes there.
 
 
the AMD64 version doesn't give me the bios bug error, but right before the boot screen it shows the weird white screen again for a few seconds then boots. Gives the bcm3xx errors then freezes on starting network connections.
 
 
Any help would be most appriciated.
Here check out my thread...I'm sure your having the same problems I did. If your getting BIOS BUG #81 its going to just be there and it won't bother anything. As for your wireless you can get around it with my post. Getting it to work is tricky and I still haven't gotten mine working. Hope this post helps you.
[http://ubuntuforums.org/showthread.php?t=507197](http://ubuntuforums.org/showthread.php?t=507197)

---

### Post by Walkboss on 2007-07-28
Hi, I've read this entire thread and I am, quite frankly, thrilled there is such a dedicated topic to my exact model of laptop. I've since finally resolved my WiFi issues, which was a huge hurdle in my mind. I still have yet to tackle my audio issues, however. I've compiled alsa 1.0.14 from source multiple times as per instructions listed in this thread and others, but my "jack sense" refuses to enable (sound still comes from onboard speakers when I have headphones plugged in)

I am not too optimistic of this problem being resolved so I actually have a purpose to this thread...

I have the AMD Turion X2 TL-51 (maybe 50 or 52, I'm ashamed I don't remember, but I don't think it's relevant). My question(s) is this: Should I be using the 64bit version of Ubuntu? Is it any more difficult to get up and running than the 32bit version? Do all 32bit applications work in a 64bit environment?

Sorry for the ramble, and thank you for your time. 

PS: Kudos to everyone involved in this thread! Thanks a ton! :)

---

### Post by netsplit on 2007-07-28
> **MikeDK said:**
> hi there!
bout the bcm43xx firmware you have to install the bcm43xx-fwcutter package to get that error fixed, its the the driver for the wireless card Broadcom 43xx series. thats probably the reason the screen freezes on starting the network, but try do ```
sudo apt-get install bcm43xx-fwcutter
```
This should work

Kind Regads MikeDK.
P.S. maybe i should go fetch the AMD64 edition to get rid of the BIOS bug i get that to also DV9000z but bought as an dv9232eu amd64 TL-52 1.6ghz

Awesome :)

How do I get to the live cd's bash to do that?

---

### Post by netsplit on 2007-07-28
> **Snipersnest said:**
> Here check out my thread...I'm sure your having the same problems I did. If your getting BIOS BUG #81 its going to just be there and it won't bother anything. As for your wireless you can get around it with my post. Getting it to work is tricky and I still haven't gotten mine working. Hope this post helps you.
[http://ubuntuforums.org/showthread.php?t=507197](http://ubuntuforums.org/showthread.php?t=507197)

I'll give that a try:)

---

### Post by Spelley on 2007-07-28
> **netsplit said:**
> I've read the whole entire thread, and I still can't get the livecd to boot.

From postings and a link or two I can gather:

- If you have a dv9000z you're going to have problems
- all AMD based systems are dv9000z`s
- since my dv9208nr is AMD based it's a dv9000z

I really want to try ubuntu on my laptop. I used pclinuxos and it was nice but I'd like to find something that gives me less trouble getting things to compile (it was always missing things!, and what I needed was seldom in synaptic)

I've tried the kubuntu 7.04 for x86, gives bios bug error (I can reboot and get the error number if it'll help), then  normal boot, then some errors about bmc3xx.firmware.fw or something missing (that should be easy to fix when it actually boots), then normal booting then it shows this weird white and grayish screen that looks kind of like a lavalamp. That screen freaks me out because is it dangrous to my lcd screen? It freezes there.


the AMD64 version doesn't give me the bios bug error, but right before the boot screen it shows the weird white screen again for a few seconds then boots. Gives the bcm3xx errors then freezes on starting network connections.


Any help would be most appriciated.

1) edit your boot parameters and add "NOAPIC" at the end of the kernel line. That should boot you into UBUNTU.
2) The BIOS error only shows up with the 386 version, not AMD64. Either way, seems to have no effect.
3) AMD64 performance vastly superior (IMO) to 386. Worth the extra hassles with programs like Firefox.
4) bcm error is your wireless card. It will go away when you install the drivers.
5) the weird white and grayish screen freaks me out, too. The freakout horizontal lines went away by adding "vga=792" to the end of the kernel line. The "lavalamp" effect disappeared after installing the NVIDIA drivers. However, it still shows up when resuming from suspend.
6) Overall pleased except for a random hard lock-up once a day. The "NOAPIC" parameter screws up your USB controllers (among other things), and I hope this issue and stability get fixed soon.

---

### Post by Spelley on 2007-07-28
WEBCAM UPDATE.

For those of you trying to get your MICRODIA/SONIX webcam working --

The "NOAPIC" parameter in your kernel line screws up your USB controllers. In my case, after installing the V4L2 drivers, Ekiga & Cheese show a garbled green screen. You can fix this and get your webcam working (and USB in general?) by adding "IRQPOLL" or "IRQFIXUP" to your boot-up kernel line (after "NOAPIC"). But this causes other problems, like messes with CPU frequency and correct battery profiling :(

Still -- if you are bent on seeing your webcam working properly, even if only to make sure it even works, give this a try.

---

### Post by EXCiD3 on 2007-07-28
I have compiled all the information talked about in this thread so far and created a Howto out of it. 

Here is a link to it: [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

Please read through it and make sure everything is correct. Thanks for all your help guys!

---

### Post by netsplit on 2007-07-28
Okay so the noacpi acpi=off boot options worked great!

Thanks heaps for that!



Now the bad news.I can't get internet off the livecd, and that's really important I need to be sure it's going to work okay before the commit (I have no windows install cd and I'll have trash the boot partition to install ubuntu. so I'll be screwed if I can't get on the net with ubuntu).  I was thinking I could edit the livecd and put the firmware files in myself. However it appears it boots off something called SquashFS.

I've looked all over, is there anyway to edit it from windows?

---

### Post by EXCiD3 on 2007-07-28
Thats a little bit out of my leage. Why is it that you cannot get internet? Does ethernet work for you?

---

### Post by Snipersnest on 2007-07-28
> **netsplit said:**
> Okay so the noacpi acpi=off boot options worked great!
 
Thanks heaps for that!
 
 
 
Now the bad news.I can't get internet off the livecd, and that's really important I need to be sure it's going to work okay before the commit (I have no windows install cd and I'll have trash the boot partition to install ubuntu. so I'll be screwed if I can't get on the net with ubuntu). I was thinking I could edit the livecd and put the firmware files in myself. However it appears it boots off something called SquashFS.
 
I've looked all over, is there anyway to edit it from windows?
 
Hi again...your wireless internet is going to take a lot of tweaking. But ethernet should work on the livecd.. It would be strange if it doesn't.. (mine did) My wireless still doesn't work even after following guide after guide...its depressing.
 
I don't know much about the Ubuntu partition setup I think it allows you to resize as part of the Ubuntu installation wizard. I'm still using an old-school Windows program thats no longer made called Partition Magic 8. Its like GParted for Ubuntu but for Windows.

---

### Post by netsplit on 2007-07-28
Eithernet works great, except I have nothing to plug it in to. 

I'm thinking of just saying screw it and making a boot repair cd, for windows, burning another pclinuxos (with the wireless driver files) disk then going ahead and install ubunutu on the hard drive and mess with it like that.

edit: Sniperfest: resize sounds like a great idea, but partition resizers sometimes eat partitions. So good to have a plan b if it crashes I think.

---

### Post by Snipersnest on 2007-07-28
> **netsplit said:**
> 
edit: Sniperfest: resize sounds like a great idea, but partition resizers sometimes eat partitions. So good to have a plan b if it crashes I think.
 
Never had a problem with Partition Magic doing it...but its for Windows. My backup plan is always make sure nothing is on there worth losing lol.
 
** My laptop dv9010us has a Broadcom Dell 1390 mini pci rev01 for wireless. If anyone could give me a working tutorial on how to get this working I'd be greatful. **The others in this thread lead you to 1000 other links and then they don't work. I've reformatted my laptop 3 times already with Feisty because no one has been able to help me figure out whats going on with the wireless.

---

### Post by EXCiD3 on 2007-07-28
You might check this out: [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")  Its a tutorial I just made using some of the stuff we have talked about here, and some research on my own.

---

### Post by bspeakmon on 2007-08-01
never mind - known 2.6.22 issue.

---

### Post by old_salt on 2007-08-01
When Excid3 started this thread and my arrival shortly after; we made an agreement to make this thread as complete and concise as possible for the DV9000 series laptop to help everyone get up and running with E,K,Ubuntu on the DV9000 series model. There are some issues that remain like the Webcam & Lightscribe and some that are hit and miss but I believe overall we have attained our goal.

Excid3 and I have spent many hours of our free time documenting our trials and errors, research and responding to post replies. 

**In short.....**
Excid3 and I continue to see repeat postings with questions that have already been asked, responded to and resolved with step-by-step procedures or reference links on previous pages. This just creates chaos and makes it harder to search. The design & intent of any topic thread is to provide a searchable index for everyone to review to obtain their answers._ In other words_, search the thread first to see if your question(s) haven't already been asked and resolved BEFORE posting. Unfortunately that isn't happening. 

Time is running out and in order to allow Excid3 and myself to move on and help others, I believe it's time for us to consider locking this topic for posterity and take a break before taking the next step. 

As I stated before, not all issues were resolved unfortunately and I'm not sure they all will for a while. It's so great to see so many new K,U,Edu,buntu users and converts. I enjoy helping people as best I can to help wherever I can however I believe a certain measure of self-help and patience is also required from all. Forums are not a one-stop quick response resource for troubleshooting. There is no such thing in Linux unless you subscribe and pay for support from the various distro's. The more that repeat questions are asked, the less useable a thread becomes and after a while it becomes just wasted space in cyberspace and benefits nobody.  

**[CENTER][SIZE="2"]In summary;[/SIZE][/CENTER]**

 I believe it's time that we lock this thread down for now while we move on to testing the Gutsy release. I know Excid3 has college starting up soon and needs to prepare accordingly and I plan on experimenting with Xen. 

Excid3 do you concur? You can submit the request to Freeze the thread since you initiated it and I already have a new thread topic for us to start on release of Gutsy. I also believe we should proceed with obtaining moderator rights for the next thread so we may keep it lean & mean.

Sincerely,
Old_Salt
Tony

:guitar:

---

### Post by EXCiD3 on 2007-08-05
Yes I agree. I plan on locking this thread in the near future (tomorrow?) In the mean time, I have compiled all the topics we have talked about here into this post: **[http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059").** 

I agree that we should get Moderator rights for a "HP Laptop" thread that could possibly cover all the HP laptops as many have the same hardware, or slight variations.

**If you need help on setting up hardware please see the link in my first paragraph.**

---

### Post by bapoumba on 2007-08-07
Thread closed as per OP's request.
See post above mine for a summary. Thanks.

---

