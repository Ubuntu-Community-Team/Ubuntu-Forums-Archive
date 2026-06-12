---
title: "Sony Vaio TZ Series: Quest for 100% Compatibility"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by AlbinoButt on 2007-07-31
[COLOR=Blue]**List Updated April 7, 2008**[/COLOR]

Thanks to everyone who's kept this thread going with valuable information! This  list should be updated when Hardy Heron Final is released.

[COLOR="Gray"]Hi everyone, I just purchased a Sony Vaio TZ90 (VGN-TZ90HS). It's a Japanese model, but similar to the upcoming TZ series in the US. Hopefully this can be a starting point for everyone with a TZ so we can get most of the hardware up and running.[/COLOR]

**---------------------------------------------**

Here's a tentative list of the supported/unsupported features in Hardy (8.04 standard *beta 5* CD, clean install with all updates):

**_Works (out-of-the-box or with some tweaks)_**
Sound
Motion Eye
HSDPA modem [COLOR=Red](Needs verification! Someone please veryify/PM if this works/doesn't work for you.)[/COLOR]
Headphone Jack Sensing
Shutdown/Restart
Intel 950 Graphics
Wired Ethernet
Bluetooth
USB
Touchpad
DVD/CD Drive (burning and reading)
Intel 4965 (A,G,N Wireless)
Integrated Media Buttons [COLOR=Red](Needs verification! Someone please veryify/PM if this works/doesn't work for you.)[/COLOR]
FN Keys



**_Doesn't work_**
Suspend/Resume [COLOR=Red](Needs verification! Someone please verify/PM if this works/doesn't work for you.)[/COLOR]
Fingerprint Sensor
Memory Card Reader (Ricoh)

**---------------------------------------------**


Here's a current list of the supported/unsupported features in Gutsy (7.10 standard CD, clean install with all updates):

**_Works (out-of-the-box or with some tweaks)_**
Sound
Motion Eye (integrated webcam) [Latest Instructions/Experiences here]("http://ubuntuforums.org/showpost.php?p=4508643&postcount=102") (Thanks, [COLOR=SeaGreen]_teo_ and mikerussellnz[/COLOR]!)
HSDPA modem [Latest Instructions/Experiences here]("http://ubuntuforums.org/showthread.php?t=721257") (Thanks, [COLOR=SeaGreen]Astalavista, nothingspecial, and mikerussellnz[/COLOR]!)
Headphone Jack Sensing [Latest Instructions/Experiences here]("http://ubuntuforums.org/showpost.php?p=4131815&postcount=89") (Thanks, [COLOR=SeaGreen]Kache[/COLOR]!)
Shutdown/Restart
Intel 950 Graphics
Wired Ethernet
Bluetooth
USB
Touchpad
DVD/CD Drive (burning and reading)
Suspend/Resume
Intel 4965 (A,G,N Wireless)
Integrated Media Buttons
FN Keys



**_Doesn't work_**
Fingerprint Sensor
Memory Card Reader (Ricoh)

**---------------------------------------------**

Here's an [COLOR=Red]obsolete[/COLOR] list of the supported/unsupported features in Feisty (7.04 with all updates):

**_Works (out-of-the-box)_**
Intel 950 Graphics
Sound 
Wired Ethernet
USB
Touchpad
Suspend/Resume
DVD/CD Drive (burning and reading)
Microphone (integrated) (*Thanks, [COLOR=SeaGreen]KEYofR[/COLOR]*)
Integrated Media Buttons (Eject button only; *This seemed to work for me, but stopped working sfter certain software updates*)

**_Needs Manual Installation_**
Intel 4965 (A,G,N Wireless) [Click here for instructions]("http://ubuntuforums.org/showthread.php?t=493095")
FN Keys (Brightness) [Instructions Here]("http://ubuntuforums.org/showthread.php?p=3213947#post3213947") (Requires Gutsy Kernel)

**_Doesn't work_**
Motion Eye (integrated webcam)
Fingerprint Sensor
Memory Card Reader
Headphone Jack Sensing
EVDO (*Thanks, [COLOR=SeaGreen]KEYofR[/COLOR]*)

**---------------------------------------------**

I'll add to this list as I test out more of the hardware. Please help me add to (and fix) this list if you have a TZ! Thanks for your help and support.

---

### Post by misuto27 on 2007-08-02
Nice, I have just bought the exact same VGN-TZ90HS.

So far, I am seeing the same problem as you do.  I will share my experiences as my quest for 100% functionality with TZ.

:KS

---

### Post by AlbinoButt on 2007-08-02
Thanks, misuto!

I've made some progress with the wireless drivers following the instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=493095").  Once  wireless is up and running, you'll have upgraded to a Gutsy kernel (2.6.22-9-generic is the latest as of this post). This causes sound to be disabled, but this can be fixed by typing the following in a terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```

Add the following line to that config file:

```
options snd-hda-intel model=auto
```

Currently, using the Gutsy kernel causes suspend to be broken on my machine. It suspends okay, but once you try to wake it up, text scrolls on the screen and the caps lock/scroll lock light stays blinking. You can then switch to X by pressing ALT+F7, but things just seem to be buggy and crashy.

And I can't adjust the display brightness at all. (FN keys don't work, and gnome power management doesn't have brightness settings.)

The current problem with the wireless driver I'm having is that you can't use the Network Manager to connect to a WPA network with a static IP. You have to enable DHCP at the router. (Maybe there's a workaround, but I haven't found it.)

---

### Post by fabienpenso on 2007-08-02
For the brightness you have to use the sony-laptop drivers (not sonypi), it works fine here with my tz90. I installed a 2.6.22.1+suspend2 kernel, I'll post a post on my blog soon with config files. **UPDATE** : see this link : [http://blog.penso.info/articles/2007/08/03/ubuntu-linux-vaio-tz90-configuration]("http://blog.penso.info/articles/2007/08/03/ubuntu-linux-vaio-tz90-configuration")

I tried for hours for the webcam with no success. The r5u870 driver doesn't work at all, even changing the source to accept the new webcam (it is slightly different than the models supported by the driver from [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/) )

The SD card reader does'nt work neither, even with the drivers from [http://sdricohcs.sourceforge.net/](http://sdricohcs.sourceforge.net/)

Also I can't have the microphone to work, that means no Skype or SIP :( Does anyone had success with that ?

And did someone configure the framebuffer ? I can't find what to use in grub, or fbset. I'd like to have a panoramic framebuffer...

---

### Post by AlbinoButt on 2007-08-04
Thanks Fabien. Would I also need to download the kernel headers (aside from the suspend2 kernel image from your blog) to add the 4965 wireless patch?

I've been trying with no success to get the webcam, mic, and card reader to work. :( Haven't tried configuring the framebuffer, though.

---

### Post by fabienpenso on 2007-08-04
Albino, the headers have been added.

---

### Post by AlbinoButt on 2007-08-10
Thanks, fabien.

I installed Gutsy Tribe 4 and it works great on the tz! the 4965 driver is built in so wireless is running out-of-the-box.

To get sound working in tribe 4, all you have to do is type in the following in a terminal window:

```
modprobe snd-hda-intel
```

(suspend and brightness keys don't work by default; card reader, webcam, and mic don't work at all.)

---

### Post by fabienpenso on 2007-08-10
Sadly I would really need the mic to work to use Skype ;( I think the microphone is probably included within the webcam, the reason it doesn't work...

I could do without the SD reader, but the webcam man, it's 2007, not 1997 :(

---

### Post by AlbinoButt on 2007-08-10
Hopefully things will get ironed out soon enough :(

I blame this on hardware vendors/manufacturers like Sony for keeping their hardware info closed. They don't even have to provide drivers/support. all they have to do is give us the information that the community needs instead of keeping us in the dark.

We have great community efforts like the sony-laptop module devs that put so much hard work into just reverse-engineering the hardware. All this time and effort could be used to improve the linux experience instead of just getting things to **work**.

---

### Post by AlbinoButt on 2007-08-16
After doing the updates today for the Gutsy alpha,suspend seems to be working again with the default kernel. The only thing is, when you wake up the computer the caps lock and scroll lock lights stay blinking.

**Update August 25, 2007:** The caps lock and scroll lock lights now function properly on resume.

---

### Post by AlbinoButt on 2007-08-18
To enable the FN brightness keys in the Gutsy kernel, you'll need to enable the sony-laptop module. To do this, first install modconf by typing the following in a terminal window:

```
sudo apt-get install modconf
```

Then start modconf by typing:

```
sudo modconf
```

scroll down to **/kernel/drivers/misc**, and enable **sony-laptop**.

---

### Post by AlbinoButt on 2007-08-20
I noticed that the fan turns on for 1-2 seconds and then turns off. This happens pretty regularly.  It seems like this shouldn't be happening. :confused:

---

### Post by KEYofR on 2007-08-27
I just got a TZ150N off the shelf at best buy.

The built-in mic works fine in feisty, or rather kernel-2.6.20

after upping to gutsy as of today (20070826) the sound card is recognized very differently. xfce mixer shows different, abnd fewer sliders.

* no mic controls
* headphone and speaker sliders are backwards and the headphone one is really an on/off though it's given a slider. the speaker slider conreols the volume coming out the headphoine jack, and the headphone slider turns the built-in speakers on/off.
The headphone jack also does not automatically disable the built-in speakers, so it's good that at least there is a way to turn them off and still have the headphoine jack on, even if it's bass ackwards.
* mute hot-key worked correctly, toggled mute on/off, before gutsy, now it only mutes, never un-mutes.'
* volume up/down work in feisty and gutsy
* hardware media buttons for cd drive seem to do nothing.
* other Fn-* buttons do nothing


* after upping to gutsy, firefox crashes in at least one predictable, reproduceable way. When I went to write this very reply, ff crashed on typing by second character. restarted ff, told it to "restore session" , type a chacaracter, boom.
repeated several times. Had no other issues with ff for a few hours before this.
I narrowed the symptom down a little more, it's bizzare:
* reload the session, and type lots of characters, that don't happen to include a space. no-boom.
* reload the session, type only spaces, many, no-boom.
* reload the session, type one, or more, non-space characters, no boom, type a single space, boom.

Work-around:
I installed the pentium-m swiftweasel.deb and came right back here and am having no problems writing this post.

Anyways.. Hi from another TZ via the built-in wifi on a wpa network.
Using the built-in driver in gutsy not ndiswrapper (unless it's using ndiswrapper without needing me to suopply the windows drivers)
Luuuv how xubuntu feisty and gutsy recognized the screen geometry and resolution out of the box

Other than these little things my experience for what works/doesn't-work is the same as you already said.

Just in case it hasn't been mentioned here yet, you don't have to wipe the factory Vista to install either. Vista has a util to shrink it's own partition and it's effortless to create a new peartition in the now-unused space. Grub creates working boot entries for not only the vista install but also the vaio factory recovery partition. You do want to manually edit the labels though since they both just say vista/longhorn. trivial.

As for the evdo... well, even in vista where it would work fine, I may never use it. The plan is minimum $40/month on top of whatever you already pay, even if you have power vision already. However, I have a Treo700p and have powervision on that, unlimited for $15/mo. And it turns out to be possible to set up dialup networking via bluetooth to the phone. It requires a small hack to the phone but seems to be harmless ever since the firmware update last year. Since it works via bluetooth, that's just about as convenient as the built-in evdo. 
You don't have to do anything on the phone to enable it except once. after that you just fire up/shut down the connection from the notebook whenever you want and as long as the phone is nearby it just works.
It works via usb too, and there is an easier, no hack way by using pdanet, which is only $34, but just pointing out some people may not be out in the cold regardless if the evdo ever gets working.
I'm hoping that since the phone just looks like a modem and you don't have to feed it very special commands (it works in mac and windows by just following generic dialup instructions, you just need to know that the number is #777
and you username is [email]something@sprintpcs.com[/email], and the password can be replaced and set by you on the sprint web site.
Given all that, hoefully linux bluetooth has reached a point where it can do this much, if so, yeha!

Oh, has anyone been able to burn a cd or dvd?
I successfully burned a dual-layer single disk recorvery disk from vista, so I know the drive and the media are ok. xfburn seems to see the device, but I cant' get it to burn an iso.

other notes...
* lmsensors and the xfce sensors applet can read the cpu frequency as it fluctuates, can read the cpu temps, both cores individually for both speed & temp.
* Battery monitor works
* no hd temp
* smartctl -a -d ata /dev/sda works


This is one badasss little subnote. Everyone is talking about the Dellm1330 these days, it's cheaper and has a larger screen and is almost twice as fast, And the apples are finally both faster and cheaper, and they have that awesome unbreakable power connector and other design wins,  and I generally dislike Sony because of their various consumer-unfriendly tactics, but.. I have to say I do not regret this purchase at all. 

The biggest problem with this device is it's poky speed, but, since xubuntu existrs, and since everything important work in it, speed is not a problem. dual pentium-m cpus at 1ghz with a gig of ddr2-533 is more than enough for a nice optimized linux to run quite well in.

---

### Post by AlbinoButt on 2007-08-27
I updated the list with your info. Thanks, KEYofR!

CD/DVD Burning works fine here. I used both the GNOME CD/DVD Creator and GnomeBaker.

You're the first person with a model that has a Pentium M, 4200 RPM drive, and EVDO :)

---

### Post by KEYofR on 2007-08-28
It's an ultra low voltage dual core centrino core 2 duo, not a simple pentium-m, but the cores are basically pentium-m from a software/compatibility standpoint.

They also massively underclock them to 1.06 ghz for heat and battery life.
And the on-demand cpu scaling model that xubuntu uses by default actually clocks it down to 800 mhz most of the time.

The dell m1330 has basically the same dual core cpu but running at just over 2ghz... and has ram that runs at 667 where this TZ is at 533. I sure would love it if this unit could run at those speeds, but I think the only way that could happen is for the untit to be physically larger & heavier because it would need more cooling hardware (bigger sinks, & fan) and more battery to power both the hotter & faster cpu and the larger cooling hardware.

I'll take the smaller size, 2x 1G is fast enough as I mentioned thanks to the ability to optimize linux.

xubuntu boots up to a fully ready and idle desktop way faster than vista, but that's nothing compared to shutdown times. Waiting for Vista to shut down is positively ridiculous on this thing. Hello it's a super ultra portable, that means almost every user, almost every time they use it, is on the go. It's uh, the very definition of the product. I need to snap the lid and dash. every time. idiots...

This, even though I have tried to optimize Vista as much as possible to give it a fair shake. I turned off every enhanced vista feature I can find (I did leave the fs indexing enabled which I normally disable on xp, because there are tons of places now in vista where using the search is almost the _only_ way to get to some places. You can't for example "up directory" even though you know there is a higher containing level for the directory or other type of dialog you are in. There is only the back button, and a row of pseudo-path elements that borth only go back as far as wherever you entered the dialog, so for example: if you clicked on something that popped up a dialog to modify a network card properties, you can't use that dialog to get to some other network card. If you open a window into your workgroup, you can't up-arrow to see other workgroups.
Lots of things have no button anywhere, you simply must know how to ask for it, and ask for it, and maybe it finds it. It's a good idea taken too far. How often do we goole for something thats right there, but it's just faster and easier to google that to poke around and find that thing thats in one of these menues in here somewhere just a coupld levels deep... but to go and make it so that "googling" is now the only way to get to things is kind of retarded I think.
It's like saying, "drinking water is good for you" "wow really? Awesome! from now on we will ingest nothing but water!"

..gggr*^%$#%#@soft

Although I am here (on ubuntu forums and other unix forums) because I am a complete unix-head, I think now I need to also find a forum more geared to the device than a particular OS on the device, since I would love to see a large thread with lots of tips on how to tweak Vista to optimize it to make life more sensible on this thing.

I would love to see the same thing for linux here , but here only linux talk is topical, whereas I think I am going to be using both OS's on this device for most of it's life. FreeBSD or other os's would be interesting too. x86 solaris anyone? :) and I hate to say it out loud these days, but I am actually a huge SCO fan from all the years before they broke up and were re-animated with a brain from the bad brain institute (see FrankenThumb). So for me, getting OSR 5.0.7 would actually be pretty cool.

I've made a dd image of the 8 gig vaio factory restore partition, I think I'll try installing XP to that and see just how much faster XP runs on the same hardware vs Vista.

It really suck that there is no way to buy the thing without buying Vista Buisiness. no refund either.. I thought MS LOST those monopoly lawsuits!!?? You wouldn't know it by looking around at the market..

Eh enough ranting, sorry. I originally just wanted to comment on the cpu's. :)

---

### Post by KEYofR on 2007-08-28
good news (minor)

the hardware media buttons on the front edge are useable.
They all generate keycodes in xev, which means you can easily map whatever keysyms you want to them and then tie whatever app or windowmanager action you want to them right now.

Generic instructions on xev, keycodes, keysyms,  and internet/multimedia keys here:
[http://ubuntuforums.org/showthread.php?t=109377](http://ubuntuforums.org/showthread.php?t=109377)

---

### Post by AlbinoButt on 2007-08-28
KEYofR, did you have to install the sony-laptop modules to get the front panel buttons working? Or did they just work out-of-the-box?

If you'd like to go to a discussion that's dedicated to the TZ and other Sony hardware, I would suggest the [NotebookReview Forum]("http://forum.notebookreview.com/forumdisplay.php?f=8"). They go in-depth about tweaking Vista and XP to work better on the TZ, too.

I also really wanted to buy hardware like the TZ without windows :(

---

### Post by KEYofR on 2007-09-05
If anyone else considers blowing away the 8 gig recovery partition to use it for something more useful, use the util in vista to create the recovery disks first, ad make sure they acttually boot up.

I created the single 8gig dvd on a dual-layer dvd, but surprise surprise, it doesn't work for booting. The burn was fine, the disk is perfectly readable and uncorrupt. It's some limitation in the tz's bios I guess, or maybe in the boot files on the disk.

And surprise surprise, erasing the recovery partition breaks booting vista even though your grub or other boot loader may be fine.

What happens is when grub/other hands off control to vista's new boot loader, BCD, BCD's config file is no longer correct because it had knowledge of that recovery partition. This, for some idiotic typical MS reason, breaks booting vista at all.

It can be fixed but you need a BCD editor. EasyBCD is a supposedly nice easy gui editor that can fix most problems easily, but it's a windows util, that doesn't work in wine because it needs .NET... But EasyBCD includes a command line bcdeditor that does work from bartpe/ubcd4win, by booting up the cd and accessing a copy of the editor from a thumb drive.

Easier than than that though is BootIt NG. A $35 shareware app that has a functional free demo. (at least, functional enough for this)
Thats a windows app you have to install on some other win box, then it genertes a bootable iso image or writes to a cd directly. You boot that and it includes a gui bcd editor. It's completely bizarre and unclear what you are supposed to DO in the editor in order to fix vista, but I did managed to resurrect mine after quite a bit of random guessing. Vista's boot process is not simple like Xp/2k was.

Moral of the story? don't expect to be able to destroy the recovery partition, or move vista to a different partition etc... without breaking booting vista. 

and the breakage isn't in grub/lilo/other or in the mbr, and so can't be fixed in grub/lilo/other no matter how much you know about those or what claims things like SuperGrubDisk makes. The breakage is 100% in vista, specifically in the BCD config, and, it's some proprietary format similar to the registry and so you need  a special bcd editor not a text file editor, and no linux apps for that exist, only a few different windows apps, and since your windows is not bootable, and the TZ does not ship with recovery cd's so you can't do the one thing all googled directions say (boot your vista install cd and select repair...) ... Grrr! you see the train wreck that awaits you if you manage to break your ability to boot vista.

But the good news is it is actually salvageable, it just doesn't appear so when it happens to you. At least now you know how to avoid the land mine, and know that if you hit it, it IS recoverable with some effort.

Later I'll post some more detail about just what to do in bootitng. I'm still poking myself, I can boot, but it's not optimal, I now get an extra windows boot menu where I have to select windows (vs memory diag vs recovery, which doesn't work anyways when selected, memory diag does work though). If I can find the time I'll try to work out the shortest recipe that works by running the less user friendly bcdedit.exe in wine or qemu, so that the solution will use only gnu stuff and maybe not require burning a cd or access to some other working windows box. If nothing else, maybe it can all be done in wine or by using reactos inside qemu. And if it really requires booting the bootit ng cd, maybe some grub smoke & mirrors can be worked out where you don't actually have to burn a cd and boot from it, just select it from a grub boot menu item.

---

### Post by psuter on 2007-09-20
hi guys

i just bought myself a sony vaio tz150n at the sony store yesterday. i immediately blew away the windows partition (not the recovery partiton though) and installed ubuntu gusty 5. after i ran an update which took quite some time almost everything including fn-keys, brightness and wlan works. bluetooth is working too and the audio card works after loading the intel sound module as described in this thread. 

motion eye and sd card reader aren't working and more importantly, suspend doesn't seem to work either. 

is there anything i can do in order to get suspend to work? i saw in the early posts i should install suspend2 but these suggestions are already a bit dated and i have no idea on how to install that. i guess suspend2 is a kernel module? 

other than that, it really works like a charm. so any tips on how to get that suspend problem fixed are welcome, since i am really using that often ;) 

cheers
pascal

---

### Post by psuter on 2007-09-20
it seems that this is a known problem with the new kernel, so maybe we just have to be a bit patient. the tz series is based on intels santa rosa platform and thus i guess that this probelm probably exists with many notebooks. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134476](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134476)

---

### Post by akbardotinfo on 2007-09-21
3G ExpressCard works well on TZ :) I put the story on my blog.

[http://nustaffsite.gunadarma.ac.id/blog/akbar/]("http://nustaffsite.gunadarma.ac.id/blog/akbar/")


Thanks!

---

### Post by mikerussellnz on 2007-10-07
Hi fellow TZ users!

I have the TZ webcam working.  I have added support for the Sony VCC7 camera found in the TZ series to the r5u870 camera driver and it is working with my VGN-TZ17!

Attached is the modified r5u870 source with the extra firmware file for the VCC7 that I extracted from the Windows driver.

Just compile it and it should work,  I used xawtv for testing.

 
Let me know if it works for you.   If it does, I  will submit it back to the author of the r5u870 driver.

Regards

Michael

---

### Post by indraveni on 2007-10-10
Dear mikerussellnz,

 Many thanks to you for uploading the r5u870 driver for the VG17 Series VAIO laptops. It worked on my laptop, with webcamde having device id: 05ca:183a.

After a week struggle with this model we got your drivers. Thanks a lot.

Regards
Indraveni

---

### Post by agentblueuk on 2007-10-11
works perfectly for me on my VGN-SZ61WN laptop on fedora 7 running 2.6.22.9-91.fc7

---

### Post by AlbinoButt on 2007-10-18
I updated the list for Gutsy. Almost everything works perfectly :)

Thanks mikerussellnz for the webcam driver!

---

### Post by peter.braam on 2007-10-21
Hi -

Is the compatibility achieved with the 64bit or 32bit version of Gutsy?

Thanks.

- Peter -

---

### Post by AlbinoButt on 2007-10-23
> **peter.braam said:**
> Hi -

Is the compatibility achieved with the 64bit or 32bit version of Gutsy?

Thanks.

- Peter -

The compatibility listing is from the 32bit version :KS

I'm noticing that suspend/hibernate seems to be moody and now it only works about a third of the time :mad:

---

### Post by zakeen on 2007-10-25
Just letting you guys know. I got an Transcend 32GB ExpressCard with SSD working perfect in my TZ at the moment.

@akbardotinfo I went to your blog and saw your "file manager" program. Where can I get it from?

---

### Post by roberto gurovich on 2007-10-29
thanks everybody for the support. 

I have an vgn-tz15fn brand new, and all the ideas and procedures you people published where excellent and usefull.

a couple of few questions additional:

1:  the suspend / hypbernate function is malfunctioning, with erratic behavior.
 any tip?

2:  still cannot make the microphone to function, inclusive after applied successfully the package for the camera driver.  any idea?

3: as been impossible to setup a vpn configuration to contact my oficce while travelling.  
ani idea?

Roberto
[email]rgurovich@gya.cl[/email]

---

### Post by zakeen on 2007-10-30
For the mic, open the volume controller and go to options I think and make sure the mic is ticked and then make sure the volume is loud enough.

---

### Post by paultjeb on 2007-10-31
I got the VPN to work as well, using network-manager and installing all kinds of cisco-stuff and vpn-stuff in synaptic.

---

### Post by mikerussellnz on 2007-11-05
Hi

Here is an updated webcam driver that also supports the Sony VCC-6 camera.

VGP-VCC6
details:
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd

Has been tested to work on a:
VGN-CR12GH

Regards

---

### Post by pari on 2007-11-07
mikerussellnz,
Thanks for the updated driver, I got a VGN-CR120E and 
the webcam is working great with this new driver.

-Pari

---

### Post by a.r. jomar on 2007-11-07
**Novatel Sprint EVDO Modem is Working in Gutsy**

Basically, all you need to do is follow the instructions on the Sprint website (login with account number, and choose "device" and choose "download software", or see attached), using the 0x2120 as the product ID (found using the ubuntu "Hardware Information" applet.

The short of it goes as follows:
Add 
```
 sudo modprobe -r usbserial
 sudo modprobe usbserial vendor=0x1410 product=0x2120
```
to /etc/rc.local (before it "exit")

Install kppp
Configure /dev/ttyUSB0 as the modem device in kppp
Choose #777 as the dialup number
Use "user" as the username, and "user" as the password

Caveat:
  I don't know of a way to toggle the EVDO modem on/off in Ubuntu. Thus, you have to turn the modem on in Windows (SmartWi) and then restart the computer. The modem should remain on for subsequent boots after that. 

GPS
I have been able to identify the GPS device on /dev/ttyUSB1. However, I don't know how to toggle the hardware switch to turn it on...

---

### Post by ltorgo on 2007-11-09
I'm the proud owner of a TZ21XN/B (european model basically a U7600,2Gb, 100Gb 4200rpm).

One of my first steps was to install gutsy on it. As i prefer KDE I've installed KUBUNT 7.10 (386).

Everything went very smoothly :) I must say. I've got most of the things I need running out of the box. That means LAN, suspend+hibernate, compiz-fusion, dual boot with the vista that came with the machine, etc. 

The only thing that is currently bugging my mind, and for which I would like to ask your kind help, is sound. It simply is not working :-( I've already tried the suggestion of editing the /etc/modprobe.d/alsa-base file, but nothing changed.... Any suggestion is very welcome!

I would also like to try the webcam driver posted by mikerussellnz  ... Any step by step instruction for dummies on how to proceed ;-) ?

Thanks for any help on improving this wonderful toy I have in front of me!
lt

---

### Post by zakeen on 2007-11-09
Your sounds works, well mine did out of the box, however it is muted. All you have to do is unclear the box and your set!

---

### Post by ltorgo on 2007-11-10
zakeen, you are actually right! It works...

I couldn't believe that I missed that one and thus tried to understand what happened (I was sure that had explored the kmixer several times to check exactly if something was switched off). 

What happened (and I'm posting this because others may come into the some problem):
1. I changed the alsa-base file according to the instruction given before in this forum.
2. I did sudo /etc/init.d/alsa-base restart thinking that this would give me sound... no sound thus I posted my question....
3. I only got sound (after turning the volume up on kmixer) after a reboot. So step 2 must have missed something that the reboot sorted out ;-)

Now my current major issue with this is that those tricks on alsa-base gave me the sound but broke my suspend+hibernate that were working well :-( ... so now I've to decide which one I want more: sound or suspend+hibernate.... unless someone comes up with a suggestion ;-)  Otherwise I'll stop sound because suspend+hibernate are actually very big pluses to me....

Thanks for any help on getting both to work.
lt

---

### Post by zakeen on 2007-11-10
Glad to be of a help.

Ive got the ssd TZ so I only full shut down and never suspend. It take about 26seconds to full boot. Is shutting down that long for you with a normal drive?

---

### Post by kennethsoona on 2007-11-10
> **zakeen said:**
> Your sounds works, well mine did out of the box, however it is muted. All you have to do is unclear the box and your set!

i have a sony vaio tz21 wn... for sound we have to edit the alsa-base file

```

# sudo vim /etc/modprobe.d/alsa-base

```

at the end of the file:

```

options snd-hda-intel model=sony-assamd

```


sony - be like no other

---

### Post by ltorgo on 2007-11-11
> **zakeen said:**
> Glad to be of a help.

Ive got the ssd TZ so I only full shut down and never suspend. It take about 26seconds to full boot. Is shutting down that long for you with a normal drive?

Well as I've the 100Gb 4200 rpm it's a bit slower ;-) It takes me 45s to get into kdm login window, and roughly another 40s (though depending on my workspace saved state) to get to the point where I can start working after logging in. Not that it is something too annoying (at least compared to Vista!), it is just that there are times were I interrupt my work for some reason and it is very handy to be able to suspend the machine very quickly and then recover (again very quickly) my previous state to continue working and at the same time being able to save battery... Hibernate is not so useful, both because as the battery life time is so large I can use most of the times suspend, and also because it is a bit slow to hibernate and to recover...

---

### Post by ltorgo on 2007-11-11
> **kennethsoona said:**
> i have a sony vaio tz21 wn... for sound we have to edit the alsa-base file

```

# sudo vim /etc/modprobe.d/alsa-base

```

at the end of the file:

```

options snd-hda-intel model=sony-assamd

```


sony - be like no other

Thanks for your help. Unfortunately the result was the same as with 
options snd-hda-intel model=auto
i.e. suspend and hibernate stop working :-(

It is a strange behavior it  is like suspend is unable to stop some processes because the screen blanks but the machine doesn't sleep: the fan continuous to be on and the power button continuous to be with the green light instead of the blinking orange...

Any other suggestions are most welcome ;-)

---

### Post by KEYofR on 2007-11-12
I made up a few grub splash images specifically for use with the TZ (or any other 16:9 display where the BIOS will stretch text & plain vga graphics to fill the screen)

[http://www.aljex.com/bkw/vaio_tz/grub_splash/]("http://www.aljex.com/bkw/vaio_tz/grub_splash/")

They are pre-shrunk from 1366x768 or 854x480 down to 640x480, so that if you enable the expand text option in the bios, then at run-time the bios will stretch the 640x480 image to fill the 1366x768 screen, and the result will fill the screen and still have the correct aspect ratio.

I'll add a few more images occasionally, and I will add a freebsd directory shortly too, where I'll have pre-shrunk 256 color 1024x768 .pcx files suitable for use as freebsd boot splash images.
I already have a couple, just that they're on the freebsd partition so I'll have to upload them next time I boot into freebsd.

20071113 - added a couple more images, I'll be adding more a couple at a time for a while. I want to do a couple more silver surfer, at least one marvin the martian, and a few more sci-fi book/seires like Vorkisigan, and a few more bands, at least one more Talena Atfield (former bass player for Kittie) etc... I should probably switch to some other boot loader that allows you to use more that 14 colors!

---

### Post by wbg on 2007-11-14
Hey everyone

I've just installed Ubuntu (well, Xubuntu) 7.10 on my VGN-TZ27GN (11.1", 1GB, 100GB, 1.20ghz core 2 duo), here is my experience so far:

Partially works:
* function keys - volume/mute keys work, nothing else works (including brightness - annonying because this model has a very bright screen)
* sound - unable to control volume of sound! always max volume, mute/changing volume has no effect

Does not work:
* SD reader
* fingerprint reader
* multimedia buttons
* suspend / hibernate seems to hang
* plugging in headphones does not mute the speakers

Haven't tried:
* bluetooth (but appears to detect it fine)
* microphone
* memorystick slot
* built in "motion eye" camera

Works:
* expresscard slot (works fine with my Merlin XU870 HSDPA card)
* wireless (802.11)
* everything else you'd expect

---

### Post by zakeen on 2007-11-14
> **KEYofR said:**
> I made up a few grub splash images specifically for use with the TZ (or any other 16:9 display where the BIOS will stretch text & plain vga graphics to fill the screen)

[http://www.aljex.com/bkw/vaio_tz/grub_splash/]("http://www.aljex.com/bkw/vaio_tz/grub_splash/")


very very cool!

---

### Post by wbg on 2007-11-15
> **KEYofR said:**
> I made up a few grub splash images specifically for use with the TZ (or any other 16:9 display where the BIOS will stretch text & plain vga graphics to fill the screen)


This is cool, but although the GRUB screen is now correct aspect ratio and pretty (when full screen), the ubuntu logo while the system is booting is stretched out of shape! Is there a way to fix this?

---

### Post by peter.braam on 2007-11-16
Hi 

I am happy to report that everything that works on 32bit gutsy also works on 64bit gutsy - and it feels a bit faster and cooler (less fan noise).

- Peter -

---

### Post by peter.braam on 2007-11-16
Fixes to sound problems:

a. sound and suspend are working after adding a probe_mask option for the sound module (it prevents the conexant modem from confusing the driver)

b. speaker muting when the headset is plugged in is working with

options snd-hda-intel model=acer probe_mask=1

in /etc/modprobe.d/alsa-base

Hope that helps others too.  Peter

---

### Post by wbg on 2007-11-17
> **peter.braam said:**
> Fixes to sound problems:

a. sound and suspend are working after adding a probe_mask option for the sound module (it prevents the conexant modem from confusing the driver)

b. speaker muting when the headset is plugged in is working with

options snd-hda-intel model=acer probe_mask=1

in /etc/modprobe.d/alsa-base

Hope that helps others too.  Peter

Thanks Peter, that fixed the speaker muting problem for me, but suspend and hibernate still causes my TZ27GN to hang. What model are you using?

---

### Post by johnhedge on 2007-11-17
Hi list,

I have a TZ18GN.

uname -r gives 2.6.22-14-generic on Gutsy

lsusb gives 

Bus 005 Device 006: ID 05ca:183a Ricoh Co., Ltd

which I think is normal for this device but Camorama shows a split screen output in black and white (grey) and Ekiga reports that it cannot find colour support in the driver.

I've tried r5u870-0.10.0-tz17 and r5u870-VCC6

Ekiga also shows the device as VGP-VCC7

Any help is gratefully received.

TIA

John

---

### Post by wbg on 2007-11-17
> **peter.braam said:**
> Hi 

I am happy to report that everything that works on 32bit gutsy also works on 64bit gutsy - and it feels a bit faster and cooler (less fan noise).

- Peter -

One thing that doesn't work in 64-bit is sonypi, and hence spicctrl

---

### Post by Sfacs on 2007-11-17
Hi !

I tried to install the driver for the motion eye webcam, but when i launch xawtv to test it, the window with the webcam is black, but the little green light is on.

```
sfacs@sfacs-laptop:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1366x768+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb7d77450b7f78e73 [PAL_B,PAL_B1,PAL_I,PAL_D,PAL_D1,PAL_N,PAL_Nc,PAL_60,?,SECAM_B,SECAM_D,SECAM_G,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Argument invalide
ioctl: VIDIOC_S_STD(std=0x0 []): Argument invalide
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Argument invalide

```


Anyone has an idea?

Thanks.

Sfacs

---

### Post by ltorgo on 2007-11-19
> **peter.braam said:**
> Fixes to sound problems:

a. sound and suspend are working after adding a probe_mask option for the sound module (it prevents the conexant modem from confusing the driver)

b. speaker muting when the headset is plugged in is working with

options snd-hda-intel model=acer probe_mask=1

in /etc/modprobe.d/alsa-base

Hope that helps others too.  Peter

Is the line of code you include for solving both a. and b. ? I've tried adding it to my alsa-base file and unfortunately I continue without sound and suspend/hibernate. However, I'm using 32 bit kubuntu gutsy.... What is bugging my mind is that I remember being able to have sound with 

```
options snd-hda-intel model=sony-assamd
```

though it spoiled my suspend, which used to work also! I'm really frustrated because things to be getting worse. Currently, I'm unable to put both suspend and sound to work, while in the past I was able to have both, though never simultaneously... I guess I tried too many of the helpful hints I saw on this forum ;-) and I guess is time for a new installation (I think I'm going to try the 64 bit Kubuntu this time...)

As a side note I would like to mention to others NOT TO TRY  the disk management "software" that comes with Vista. I did it :-( I tried to use it to split my Vista partition into two, one for Vista, and another for my user files, so that I could see/use this second partition from both Vista and my Kubuntu installation. The result of this "nice" tool was to completely "destroy" both my Vista partition and also the recovery partition. As, unfortunately I did not burn the DVDs with the recovery partition before (yes I know!!) this operation the result was : no vista; grub destroyed; no recover partition.

Moreover, when I manage to got some  Vista legal DVD copy and tried a clean install it did not recognize the hard disk (!!??). With a XP CD the result was basically the same! So now I'm waiting for the DVDs Sony is going to send me by mail.... 

If only I could put suspend and output to LCD projector without restarting X (i.e. FN+F7) to work on this machine, I could finally get rid of this stupid Micro$ pseudo-software!

Any ideas are welcome,
ltorgo

---

### Post by KEYofR on 2007-11-19
> **wbg said:**
> This is cool, but although the GRUB screen is now correct aspect ratio and pretty (when full screen), the ubuntu logo while the system is booting is stretched out of shape! Is there a way to fix this?

Doh! good question.
I have that disabled since I'm still trying to arrive at the best kernel compile options and boot time modules.conf options and so I always want to see the boot messages.

I'll check it out some time. I hope it can be adjusted with maybe a video mode setting [...]

update:
I can't even make my usplash work at all any more. It might just be a side effect of me not using any initrd/initramfs any more ether.
There is a how-to for customizing usplash right here on this forum but it looks like kind of a pain in the neck to do.
However it also looks like the default setup already includes support for 1366x768 if you just knew how to work it, which might be as little as editing the resolution setting in /etc/usplash.conf

---

### Post by peter.braam on 2007-11-21
Hmm, Fn keys (brightness etc) and camera etc all work for me.  What part of sonypi / spicctrl isn't working you think?

---

### Post by peter.braam on 2007-11-21
Try probe_mask=3 then.  That might fix both.

---

### Post by nichtja on 2007-11-21
Hi,

 I just bought a vaio TZ21 MN yesterday and as I had read this thread I expected to install kubuntu 7.10 without problems but the install CD just gives me a corrupt video screen after switching to Xorg.

I have also tried to boot using the safe video mode without success. I tried to run X directly and the X server starts. I also tried startx, the X server started, got a blue background and then X exists saying that this screen is no DRI capable (an AIGLX error)

Any suggestions ? From what I have read here I should not be having this problems, should I ?

Thanks in advace.

---

### Post by nichtja on 2007-11-21
I managed to solve the problem. Disabling the splash screen I noticed a kernel message about a problem with the bios telling me to use "pnpbios=off"

Adding this option to the kernel parameter list allowed me to complete the whole boot process of the live CD

---

### Post by lkcl on 2007-11-21
mike, hi,
i have a (PINK!!!) VGN-CR21E.
this is what i get:
Nov 21 14:49:37 panther kernel: usbcam: registering driver r5u870 0.10.0
Nov 21 14:49:38 panther kernel: r5u870-0: Detected Sony VGP-VCC6
Nov 21 14:49:38 panther kernel: r5u870: probe of 1-3:1.0 failed with error -2
Nov 21 14:49:38 panther kernel: usbcore: registered new interface driver r5u870

am trying to compile with CONFIG_USBCAM_DEBUG to get some more info:
let me know if there's something i can do, ok?
l.

> **mikerussellnz said:**
> Hi

Here is an updated webcam driver that also supports the Sony VCC-6 camera.

VGP-VCC6
details:
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd

Has been tested to work on a:
VGN-CR12GH

Regards

---

### Post by nichtja on 2007-11-26
I have noticed that when running on batteries sometimes the LCD dims after entering KDE and sometimes it does not. As the Fn keys are not working I can not adjust the brigtness of the screen

Any suggestions ? I own a tz21 

Thanks in advance

---

### Post by ltorgo on 2007-11-29
I just wanted to share with you my recent experiences with Kubuntu on my TZ21 (C2DU7600, 2Gb, q00Gb 4200 rpm, IP3945abg).

I had previously installed the 32 bits version of Kubuntu 7.10. It mostly went alright, but several issues where not working properly, namely: suspend; hibernate; sound; Fn keys; and maybe others that I didn't try. I've managed to solve the Fn keys but the others not really. 

After seeing a post by someone on the 64bits version I've decided to give it a try as suspend (at least) is a most to me. I should say I'm very happy with the move and that is the main thing I wanted to share with you. Suspend worked out of the box. Hibernate not really (it blocks the machine), but I do not really care if I have suspend because it is much faster and the TZ has wonderful battery life so suspend is more then enough for me. Fn keys did also worked out of the box. Sound not really, but after trying a few of the suggestion on this forum the "options snd-hda-intel model=sony-assamd" did the trick for my model without spoiling suspend (which happened with the 32bits version). The sound is a bit low even at 100% volume and with the PCM on the mixer at the maximum also, but I don't really care...

So I'm happy to report that I reached at a status where I've everything I need on my TZ with Kubuntu 7.10 64bits. I still need to try a few other things like the camera for instance but those are not priorities for me.

lt

---

### Post by _teo_ on 2007-11-29
> **mikerussellnz said:**
> 
Let me know if it works for you.   If it does, I  will submit it back to the author of the r5u870 driver.


Hi Michael, the driver works on my device (TZ21VN). I tested it with XawTV as well. However I wasn't able to test it with Ekiga (Your video driver doesn't support the requested video format.) Do you have any ideas?
Teo

---

### Post by eartal on 2007-11-29
I have just bought a sony vaio vgn-tz21mn/n; I am not an ubuntu user (I use fedora). Essentially everything I tried works; I had problems with the webcam but this thread gave me the way to solve it; thanks! I would like to know if around 60 degrees C is a normal temperature (normal use) for the processors. Sometimes I increase the fan speed (using spicctrl) but very soon it decreases. I did not see any option in the bios to get more fan speed at a given temperature. Do you have an idea?

Best, E.

---

### Post by enigma32 on 2007-11-30
Wow. This is very cool.

I've got a TZ17TN (Taiwanese model) and lots of stuff worked out of the box just like most people seem to be experiencing. (Gutsy 32bit)

I've got sound (playback and mic) working with:
options snd-hda-intel model=auto probe_mask=1

Internal speakers don't mute when using the headphone jack... 

Suspend/resume seems to be working with that probe_mask flag in there. My wireless internet seems to die upon resuming though.. just have to figure out what exactly needs to be reset to make that happy...

MotionEye webcam works with the first driver provided in this thread. (thank you!)

My todo list:
- Internal speaker mute on headphone insert (can't be too hard if some people got it working with different snd drivers?)
- Brightness function keys. Can't be too hard either right?
- AT&T ExpressCard GE0202 wireless
- edit: If I change the setting in the control panel I suppose it'll try to suspend when I close the lid :-)

-matt

---

### Post by enigma32 on 2007-12-02
Edit:
I thought I was super cool and fixed the brightness function keys on my machine...
But when I undid my fix it still worked.

Was I imagining the problem in the first place?
Anyone out there without brightness keys that still don't work?

Also, I'm happy to report some success with my Cingular/AT&T Option 3.6 GT card... I don't have all the bugs worked out yet but I think it will be happy.

---

### Post by chongl on 2007-12-03
Did anyone get the built in mic working? I was testing with the Skype automated call testing and it didn't pick up anything.

Opened up alsamixer and see a few items relating to microphones.

Also, after doing the probe=3 and/or probe=1 thing, the headphone jack still doesn't work/and it doesn't mute the speakers when plugged in.

Anyone have an idea?  Thanks!

---

### Post by gimatta on 2007-12-04
hello everyone, i've proudly installed the latest version of ubuntu 64 bit on my sony tz11mn (italian model). Now i'm trying to fix certain things.
So I've got the file of mike about the built-in vcc7 eye motion camera, but i don't know how to "compile" this stuff to have my webcam working..if anyone could tell me what to do it will be appreciated (i guess i should use the terminal, right?).
I was able to fix the sound problem thank to itorgo using his string, but the speakers don't mute when i plug the earphones.
Also the sd card reader doesn't work...any suggestion?
I'll try to be self sufficient as much as i can so i can understand if anyone cannot give me a step by step help, but at least pointing me in the right directions...thank you to everyone!

---

### Post by fhobs on 2007-12-04
Hi everybody!

Thank you all for the useful information in this thread!

My webcam is working thanks to the driver posted here. I also had this message from Ekiga, but ignored it and played a bit with the configuration dialog. My current setting is "Sony VGP-VCC7 #1", AUTO, Channel 0. I can't remember the initial settings, but now Ekiga is working with the webcam and does not complain at a restart. (However, I haven't phoned yet.)

What I really need is the TV/VGA out because I am giving a presentation from time to time when travelling. 

> **ltorgo said:**
> 
If only I could put suspend and output to LCD projector without restarting X (i.e. FN+F7) to work on this machine, I could finally get rid of this stupid Micro$ pseudo-software!


Hi LTorgo, you mean that you can make the TV OUT working by restarting  X? How do you do that? Any help is much appreciated!

Cheers!

---

### Post by noelbush on 2007-12-06
> **mikerussellnz said:**
> Hi

Here is an updated webcam driver that also supports the Sony VCC-6 camera.

VGP-VCC6
details:
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd

Has been tested to work on a:
VGN-CR12GH

Regards

Thanks for this! I'm trying to get a VGP-VCC8 to work, on a Vaio VGN-FZ260E. Near as I can tell, the main thing I'm missing (other than a small patch to the r5u870_md.c) is a .fw file for this camera. I'm trying to figure out how to extract that -- can I get it from the driver from the Sony site somehow? Any pointers? Thanks!

---

### Post by _teo_ on 2007-12-06
> **fhobs said:**
> 
My webcam is working thanks to the driver posted here. I also had this message from Ekiga, but ignored it and played a bit with the configuration dialog. My current setting is "Sony VGP-VCC7 #1", AUTO, Channel 0. I can't remember the initial settings, but now Ekiga is working with the webcam and does not complain at a restart. (However, I haven't phoned yet.)


I haven't played with settings before, but after I saw you succeeded, I tried that as well. Now I noticed why it wasn't working before.

I setup a user who cannot do sudo, i.e. without administrative privileges. So this user cannot use the camera. Ekiga simply cannot detect it. However the other user (with administrative privileges) can use it. Ekiga recognizes it and video is shown.

Can someone prove that on his/her machine as well?
Thanks,
Teo

---

### Post by _teo_ on 2007-12-08
I did further investigated the audio. I'm able to record. The only issue left here is muting. While the headset is plugged in it doesn't mute the speakers.

My /etc/modprobe.d/alsa-base is appended with following option:
```

options snd-hda-intel model=sony-assamd

```

---

### Post by chongl on 2007-12-08
Does appending that make the microphone work? My speakers work but Skype/Sound Recorder don't pick anything up at all.

Thanks!

---

### Post by chongl on 2007-12-08
nm...I got it working after messing with alsamixer

---

### Post by _teo_ on 2007-12-08
> **_teo_ said:**
> 
I setup a user who cannot do sudo, i.e. without administrative privileges. So this user cannot use the camera. Ekiga simply cannot detect it. However the other user (with administrative privileges) can use it. Ekiga recognizes it and video is shown.


sorted out: the problem was that the user wasn't member of video group
Ekiga works now :)

---

### Post by ltorgo on 2007-12-09
> **fhobs said:**
> Hi everybody!

Hi LTorgo, you mean that you can make the TV OUT working by restarting  X? How do you do that? Any help is much appreciated!

Cheers!

Well what I meant was that if I booted the computer with the projector already plugged in, it works... I do not recall if I had to hit FN+F7, but nevertheless it works. What is not working (for me at least) is to be already logged in, plug in the projector, and then hit FN+F7 to have dual output to both the projector and the laptop...

Anyway I've only used projection in two different projectors till now, but I guess it should not depend too much on the projector .... Nevertheless, tomorrow I'll use a third one and I post something if it does not work ;-)

ltorgo

---

### Post by ponx on 2007-12-09
Hi,

Anyone managed to get the headphones switch to work yet..?  This is quite an important issue for me as I intend to use my soon-to-be-acquired-tz as a personal media centre on plane journeys, etc...

Also, no-one seems to mention Bluetooth, can I assume that it just works..?

ponx.

---

### Post by offthefront on 2007-12-09
> **ponx said:**
> Hi,

Anyone managed to get the headphones switch to work yet..?  This is quite an important issue for me as I intend to use my soon-to-be-acquired-tz as a personal media centre on plane journeys, etc...

Also, no-one seems to mention Bluetooth, can I assume that it just works..?

ponx.

Early days for me. Only installed a few hours ago.
Plugging in headphones doesn't mute speakers automatically, but headphones and speakers are independent alsa channels, so start up alsamixer and mute the "Front" channel manually. (use the M key). Bit of a pain for now, but suggests it should be possible, pehaps I'll look at why ...

Bluetooth is working so far without any problems

Sue

---

### Post by mdoube on 2007-12-10
> **mikerussellnz said:**
> Hi fellow TZ users!

I have the TZ webcam working.  I have added support for the Sony VCC7 camera found in the TZ series to the r5u870 camera driver and it is working with my VGN-TZ17!

Attached is the modified r5u870 source with the extra firmware file for the VCC7 that I extracted from the Windows driver.

Just compile it and it should work,  I used xawtv for testing.

 
Let me know if it works for you.   If it does, I  will submit it back to the author of the r5u870 driver.

Regards

Michael

Works for me on my Vaio SZ650N, 64-bit Ubuntu Gutsy.

lsusb:
Bus 006 Device 003: ID 05ca:183a Ricoh Co., Ltd 

Mike

---

### Post by fhobs on 2007-12-10
Hi!

> **ltorgo said:**
> Well what I meant was that if I booted the computer with the projector already plugged in, it works... 

Anyway I've only used projection in two different projectors till now, but I guess it should not depend too much on the projector .... 

I have tried the same but were not successful. My projector cannot handle the  1366x768 resolution, does yours? Or did you switch to another resolution before booting? 

Cheers!

---

### Post by ltorgo on 2007-12-15
> **fhobs said:**
> Hi!



I have tried the same but were not successful. My projector cannot handle the  1366x768 resolution, does yours? Or did you switch to another resolution before booting? 

Cheers!

Yes, I've the same "problem". It is working (i.e. I've output to both the projector and the LCD), but not at the 1366x768 resolution. Still, it allows me to do presentations with the TZ which was my goal. The resolution depends on the projector (I got different resolutions with different projectors), but still it is OK. If only I could do this without reboot.... I would be happy ;-)

---

### Post by punklinux on 2007-12-20
> **mikerussellnz said:**
> Hi

Here is an updated webcam driver that also supports the Sony VCC-6 camera.

VGP-VCC6
details:
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd

Has been tested to work on a:
VGN-CR12GH

Regards


Can someone please write a step by step process on how to install the drivers for the webcam.
thank you very much.

---

### Post by VladArod on 2007-12-20
To solve the VGA port on/off problem I used xrandr.

To turn on the VGA port (without restarting X):
      xrandr --output VGA --auto --same-as LVDS

To turn off the VGA port (without restarting X):
      xrandr --output VGA --off

auto option should work, but see [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) for more details and options.

To enable Fn-F7 functionality we must define a config file (e.g. sony-lcd-mode) in /etc/acpi/events directory. For Sony Vaio TZ21MN I have used:
#--------------------
 # /etc/acpi/events/sony-lcd-mode

event=sony/hotkey HKEY 00000001 00000012
action=/etc/acpi/sony-lcd-mode.sh toggle
#-------------------

The xrandr control commands must be placed in script sony-lcd-mode.sh. Here is mine
#---------------------
#!/bin/bash

# External output may be "VGA" or "VGA-0" or "DVI-0"
EXTERNAL_OUTPUT="VGA"
INTERNAL_OUTPUT="LVDS"

X_USER=$(w -h -s | grep " :[0-9]" | head -1 | awk '{print $1}')
DISPLAY=$(w -h -s | grep " :[0-9]" | head -1 | awk '{print $3}')

SU="su - $X_USER -c"

# Figure out current state
EXTERNAL_STATE=$($SU "export DISPLAY=$DISPLAY; xrandr" | grep ^$EXTERNAL_OUTPUT | grep con | sed "s/.*connected //" | sed "s/(.*//")

if [ -z "$EXTERNAL_STATE" ]; then
       STATE="VGA_port_OFF"
else
       STATE="VGA_port_ON"
fi

echo $STATE

function screen_VGAoff(){
     $SU "export DISPLAY=$DISPLAY; xrandr --output $EXTERNAL_OUTPUT --off"
}

function screen_VGAon(){
     $SU "export DISPLAY=$DISPLAY; xrandr --output $EXTERNAL_OUTPUT --auto"
}

function screen_toggle(){
       case "$STATE" in
               VGA_port_ON)
                       screen_VGAoff
                       ;;
               VGA_port_OFF)
                       screen_VGAon
                       ;;
       esac
}

# What should we do?
DO="$1"
if [ -z "$DO" ]; then
       if [ $(basename $0) = "sony-lcd-mode" ]; then
               DO="toggle"
       fi
fi

case "$DO" in
       toggle)
               screen_toggle
               ;;
       status)
               echo "Current Fn-F7 state is: $STATE"
               echo
               echo "Attached monitors:"
               xrandr | grep "\Wconnected" | sed "s/^/ /"
               ;;
       *)
               echo "usage: $0 <command>" >&2
               echo >&2
               echo "  commands:" >&2
               echo "          status" >&2
               echo "          toggle" >&2
               echo >&2
               ;;
esac
#-----------------------

See [http://www.thinkwiki.org/wiki/Sample_Fn-F7_script](http://www.thinkwiki.org/wiki/Sample_Fn-F7_script) for more information.

Restart ACPI daemon: sudo /etc/init.d/acpid restart

---

### Post by zengxg on 2007-12-28
I have verified the driver on my Sony SZ66. Thank you very mush!

> **mikerussellnz said:**
> Hi fellow TZ users!

I have the TZ webcam working.  I have added support for the Sony VCC7 camera found in the TZ series to the r5u870 camera driver and it is working with my VGN-TZ17!

Attached is the modified r5u870 source with the extra firmware file for the VCC7 that I extracted from the Windows driver.

Just compile it and it should work,  I used xawtv for testing.

 
Let me know if it works for you.   If it does, I  will submit it back to the author of the r5u870 driver.

Regards

Michael

---

### Post by queno on 2008-01-08
**Two Questions:**

1. I noticed that the Sony Vaio TZ21 still eats up quite an amount of energy while in suspend-mode (S3). Did anyone experience this, too? If so, what causes it and is it a fixable problem?

2. The packages for the MotionEye WebCam and other Sony-related stuff exist in the 32Bit-version of Ubuntu, but not in the 64Bit version. Why is that & will those packages be ported to 64Bit anytime soon (e.g. for Hardy)?

**A hint:**

Installing the 64Bit-Flash plugin via Automatix crashed my Firefox in irregular patterns. Firefox took the whole system with it. I even had to remove the battery in order to restart as indefinite power-button pushing had no effect. I gave GNASH (the open-source flashplayer) another shot after uninstalling the Adobe flashplayer. It doesn't yet render all interactive elements of flash perfectly, but it works and doesn't crash Firefox.

---

### Post by fhobs on 2008-01-08
Your hint is very much appreciated, VladArod. I made an update to Ubuntu 7.10 to get the right version of xrandr; this update caused some undesired effects (sound was dead, language/keyboard setting got lost, etc), but improved some other things (the brightness keys now work). But most important: I am happy to have my beamer working! You can even run the 1366x768 resolution on the LCD and show a 1024x768 portion of it on the VGA out, really nice!

Thank you!

---

### Post by steeef on 2008-01-08
> **punklinux said:**
> Can someone please write a step by step process on how to install the drivers for the webcam.
thank you very much.
Yeah, I'd appreciate this as well. I ran "sudo make install" and restarted just to be sure, but xawtv gives me "X Error of failed request:  XF86DGANoDirectVideoMode", which I assume is due to the driver not being installed correctly.

---

### Post by chokeonnails on 2008-01-10
> **enigma32 said:**
> 
- Brightness function keys. Can't be too hard either right?
-matt

I got these working by disabling the sonypi module, it was installed by the hotkeys script in /etc/init.d

---

### Post by Kache on 2008-01-10
I got the computer speakers to mute automatically upon plugging in headphones. Works exactly like I expect it to, with one minor problem. I'm not exactly sure on what I did yet, so I'm going to keep experimenting and post again when I've got it down.

In any case, does anyone know how to map the Fn-F2 mute function to mute the PCM channel ? (muting/not muting the Front channel wouldn't matter. It'd be redundant.) That'd be a way to fix that minor problem of mine.

---

### Post by _teo_ on 2008-01-12
I just got my Globetrotter HSDPA Modem working... \\:D/

---

### Post by Kache on 2008-01-13
Ah ha, yes!

Got it working exactly the way it should. Access to all the channels like
#options snd-hda-intel model=sony-assamd
while still having the headphone jack sensing of
#options snd-hda-intel model=vaio, sony, and sony-ar

it's hippo!
```
#options snd-hda-intel model=hippo
```
in your /etc/modprobe.d/alsa-base file

You can have all the correct muting/microphone boosting, you're supposed to have.
Some of the channels still appear to be useless though.

::added::
I'm not sure if it's my "hippo" settings though, but for me, (tz130n) I'm currently unable to properly suspend/restore or hibernate. Also, I lost Fn brightness along the way somewhere while tweaking. Can you guys test it out and let me know how those are working on your systems?

::edit::
Suspend and hibernate working after a reinstall, I believe it was laptop-mode that screws up suspend/hibernate (and it doesn't seem to be reversible w/o reinstall, so unless you're testing, don't turn it on)
Still don't have Fn brightness after reinstall though.

---

### Post by chokeonnails on 2008-01-15
> **Kache said:**
> You can have all the correct muting/microphone boosting, you're supposed to have.
Some of the channels still appear to be useless though.

VGN-TZ21WN here and that did the trick, thanks!

---

### Post by liquidsg on 2008-01-18
NVM.....Ninth times a charm. Not only did Ubuntu finally install after the 9th try, but it totally fixed my bootloader on its own. I'm already impressed haha.

---

### Post by enigma32 on 2008-01-18
... Tried the suggested fix to toggle the external VGA jack without rebooting.
The script works if I remove the su commands from what it performs...

I've had no luck getting it to work from the function keys....

Anyone else verified the fix?

---

### Post by -pt- on 2008-01-20
> **Kache said:**
> Ah ha, yes!

Got it working exactly the way it should. Access too all the channels like
#options snd-hda-intel model=sony-assamd
while still having the headphone jack sensing of
#options snd-hda-intel model=vaio, sony, and sony-ar

it's hippo!
```
#options snd-hda-intel model=hippo
```
in your /etc/modprobe.d/alsa-base file

You can have all the correct muting/microphone boosting, you're supposed to have.
Some of the channels still appear to be useless though.

Thanks a lot. This one works for me (7.04 on VAIO TZ21XN).

---

### Post by Kache on 2008-01-21
I'm not sure if it's my "hippo" settings though, but for me, (tz130n) I'm currently unable to properly suspend/restore or hibernate. Also, I lost Fn brightness along the way somewhere while tweaking. Can you guys test it out and let me know how those are working on your systems?

---

### Post by iamRoko on 2008-01-28
Hey everyone, first thanks for this awesome resource/thread!

I've gotten Linux up and running on my laptop nicely. I'm impressed how far it has come since I dabbled in it a few years ago.
[B]
Now my Problem![/B]

I was fiddling around with things, and I seem to have borked my video card settings. It's detecting as a plug and play 800x600 monitor, with a generic vesa video card.. I can set it to a LCD Panel 1360x768 in the screen and graphic preferences menu, then get the resolution to go to 1024x768, but I can't get it to fill the entire screen properly..

So, what are the proper settings? (I figure I might have to manually go into some X config files to redo this properly, but I'm not sure what files, and what to add, so if anyone could help me out it would be vastly appreciated)

I'm running a VGN-TZ17GN, for reference

**EDIT** Nevermind. I discovered the existence of a quaint version of the x config file with the suffix ".backup". It's back to normal. Not to figure out why Avant window manager doesn't work anymore....

**Edit Again**Nuts. Something is still not right.. I can't activate advanced window effects for some reason, I think something is still borked. I might just reinstall as soon as I can get to install CD. (In the middle of a move, waiting for a van so I'm fiddling with linux.. The CD is packed away at my other place.

---

### Post by Kache on 2008-02-03
Something like that happened to me while I was trying to multi-monitor. That's why you always back up your config files!

---

### Post by edzu on 2008-03-07
> **_teo_ said:**
> I just got my Globetrotter HSDPA Modem working... \\:D/

I have problems with HSDPA modem. Not detected by Ubuntu. Is there a howto about this ? Or is not yet supported ?

---

### Post by JohnHughes on 2008-03-10
Did you turn it on?

echo 1 > /sys/devices/platform/sony-laptop/wwanpower

---

### Post by edzu on 2008-03-10
echo 1 > /sys/devices/platform/sony-laptop/wwanpower as root, 

permision denied

---

### Post by JohnHughes on 2008-03-11
Does wwanpower exist (maybe I got the name wrong - don't have my laptop here).  You have got sony-laptop loaded, right?

---

### Post by nothingspecial on 2008-03-11
Here are the step by step instructions on installing the webcam which Astalavista kindly gave me.
[http://ubuntuforums.org/showthread.php?t=721257](http://ubuntuforums.org/showthread.php?t=721257)
If they work for you thank him please.

---

### Post by metabrew on 2008-03-13
Just got a Sony Vaio **VGN-TZ32VN** - amazing bit of hardware (new model w/ 64GB SSD). Now for the fun part.. I decided to start by trying Hardy, so i've installed from the Kubuntu Hardy Alpha 6 alt install CD. Nuked the entire disk and used encrypted LVM.

First boot: sound, network, wifi work. Suspend doesnt work (fails to resume, blank screen flashing cursor). Hibernate works. Function keys for volume and screen brightness work. (did anyone running gutsy give the hardy kernel a try?)

No sign of the camera on first boot, dmesg has this to say about it:
```
[   33.140913] Linux video capture interface: v2.00
[   33.195969] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[   33.196507] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   33.197007] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   33.197011] uvcvideo: Failed to initialize the device (-5).
[   33.197048] usbcore: registered new interface driver uvcvideo
[   33.197052] USB Video Class driver (v0.1.0)

```

I'm especially interested in getting the HSPA modem working, but I'm not sure which device it is, or if it's even listed. Any pointers appreciated:

```
rj@rjlaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
09:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
09:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
09:04.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
09:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
rj@rjlaptop:~$ lsusb
Bus 004 Device 003: ID 147e:2016
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 014: ID 044e:3012 Alps Electric Co., Ltd
Bus 005 Device 013: ID 044e:3013 Alps Electric Co., Ltd
Bus 005 Device 012: ID 044e:3010 Alps Electric Co., Ltd
Bus 005 Device 011: ID 05ca:183a Ricoh Co., Ltd
Bus 005 Device 010: ID 054c:02d5 Sony Corp.
Bus 005 Device 006: ID 044e:3011 Alps Electric Co., Ltd
Bus 005 Device 003: ID 0409:005a NEC Corp.
Bus 005 Device 001: ID 0000:0000
rj@rjlaptop:~$    
```

first post, been lurking on these forums for ages :)


**EDIT**
Built webcam driver from svn:
[http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT](http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT)
Works nicely :)

---

### Post by _teo_ on 2008-03-16
> **edzu said:**
> I have problems with HSDPA modem. Not detected by Ubuntu. Is there a howto about this ? Or is not yet supported ?

Hi, first of all sorry for my late response. I read forums really irregularly.

I am not aware of any howto. My HSDPA Modem isn't detected as well. However I do use it - pure mobility ;-)

Now on getting you connected. There are four basic steps:

1) you need root user (just sudo will not do it)
  ```

  sudo -s
  <enter your password>
  
```
2) power on the modem
  ```
echo 1 > /sys/devices/platform/sony-laptop/wwanpower
```
3) you are done with root user
  ```
exit
```
4) dial
  ```
sudo wvdial
```

Of course, you need to setup the wvdial. Below is my /etc/wvdial.conf

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATM0
Init4 = AT+CSQ
; Init5 = AT+CPIN?
; Init6 = AT_OPSYS=3,2
Init7 = AT+CGDCONT=1,"IP","surfo2"
Modem Type = Analog Modem
Baud = 460800
FlowControl = NOFLOW
SetVolume = 0
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Stupid Mode = 1
Phone = *99#
Password = no
Username = o2

```

wvdial will automatically start the ppp daemon. Hope this helps.
teo

---

### Post by metabrew on 2008-03-17
Awesome, it works nicely. Thanks _teo_ :)


FWIW, once i turned on the modem as indicated above, dmesg says:
```
[ 4171.653360] usb 5-6.1: new full speed USB device using ehci_hcd and address 11
[ 4171.763255] usb 5-6.1: configuration #1 chosen from 1 choice
[ 4171.764317] option 5-6.1:1.0: GSM modem (1-port) converter detected
[ 4171.765233] usb 5-6.1: GSM modem (1-port) converter now attached to ttyUSB0
[ 4171.765812] option 5-6.1:1.1: GSM modem (1-port) converter detected
[ 4171.765951] usb 5-6.1: GSM modem (1-port) converter now attached to ttyUSB1
[ 4171.766445] option 5-6.1:1.2: GSM modem (1-port) converter detected
[ 4171.766721] usb 5-6.1: GSM modem (1-port) converter now attached to ttyUSB2
[ 4171.767259] option 5-6.1:1.3: GSM modem (1-port) converter detected
[ 4171.767402] usb 5-6.1: GSM modem (1-port) converter now attached to ttyUSB3
```

No idea why it shows 4 modems - it works regardless.
The following wvdial.conf worked for t-mobile web n' walk (uk).

```
[Dialer Defaults]
Phone = *99***1#
Username = web
Password = web
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","general.t-mobile.uk";

```

i'm seeing around 350 K/s which is quite reasonable.

One very minor nitpick, I run wvdial to initiate this, I've not yet figured out how to integrate this into knetworkmanager. It has a "dial up connections" section, i think i need a pppd conf file for that, rather than let wvdial do it.


So all in all, i'm happily running Hardy on my VGN-TZ32VN. 
Hibernate + suspend are currently broken, and i suspect the sound driver is to blame. Will continue to investigate that, altho i'm hoping when i dist-upgrade one morning it will magically be fixed :)

---

### Post by _teo_ on 2008-03-17
> **metabrew said:**
> Awesome, it works nicely. Thanks _teo_ :)

Glad to hear that. You are welcome :-)

---

### Post by tilkiy on 2008-03-18
&#305; want to get va&#305;o v&#305;deo capture 2 thank you for your help

---

### Post by relmes on 2008-03-19
[QUOTE=_teo_;4528594]
Now on getting you connected. There are four basic steps:

1) you need root user (just sudo will not do it)
  ```

  sudo -s
  <enter your password>
  
```
2) power on the modem
  ```
echo 1 > /sys/devices/platform/sony-laptop/wwanpower
```


Initially I couldn't get this to work.  wwanpower did not exist under the given path. This results in "Permission Denied" when you try and execute the above command.

From a bit of googling I've found (in another forum post) that if you disable the sonypi module it all starts to work!
Quote
"
You can stop sonypi from being loaded by commenting out the "modprobe sonypi;" line in /etc/init.d/hotkey-setup (as mentioned by nyc_863 in earlier post). See example below:


Sony*)
#modprobe sonypi; # Needed to get hotkey events
modprobe sony-laptop
;;
"

As a bonus my Fn keys now also work for the screen brightness.   

Hope this helps those that are still stuck trying to get the HSDPA card working.

---

### Post by metabrew on 2008-03-20
Quick update on running kubuntu Hardy on the VGN-TZ32VN - the latest dist-upgrade fixed suspend and hibernate, so i'm happily using working sound, cam, fn keys, wifi network and 3G modem now.

Fingerprint scanner is apparently just a usb scanner, and doesn't have a coprocessor, so the work has do be done in software. No useful drivers i could find yet.

Not tried the sd card slot. Media keys "work" as in they have keycodes when i tested with xev, but i didn't map them to anything useful yet.

---

### Post by Poromenos on 2008-03-23
What kind of battery life does Ubuntu get on this? What's the longest you guys have run it continuously?

---

### Post by orclev on 2008-03-23
Just got a new VAIO TZ and I'm running the latest beta of Hardy. Just about everything has worked out of the box, with a couple exceptions. I haven't tested the webcam, so that's a maybe, but I'm hopeful it will work fine. Right now, my biggest headache is that I've got a bluetooth mouse, and the scroll wheel isn't working properly. Reading up on this, it seems the problem is that the mouse hasn't been paired with the computer properly, but most of the instructions I've found don't seem to work. Tried doing hciconfig hd0 inqmode 0 which I found in another thread, but I get a "Input/output error (5)" when I do that. Is the bluetooth driver just flaky, or am I missing something?

UPDATE: Suspend isn't working. Experiencing the same problem someone else was where when it comes back up all I get is a non-responsive blank screen with a blinking underline cursor. Interestingly enough when I tried suspending from the live disk it worked fine, but suspend from the fully installed system is broken.

UPDATE: I've got suspend working, and hibernate partially working using the "options snd-hda-intel model=acer probe_mask=1" trick from earlier. When you activate hibernate, it starts to shutdown, but stops with a message that says something like drm_sys_initfs, or something along those lines. If you power it off and back on at this point it behaves as if it went into hibernate, so it's like it finishes going into hibernate mode, but fails just before sending the power down signal. I've also got the webcam working (at least some of the time) using the latest version of the r5u870 driver from another post, although I haven't quite figured out what makes it work or not. Sometimes when I try to use the webcam it works fine, other times it doesn't. Still no luck on the bluetooth which is really my biggest complaint at this point, as I really really want to get my scroll wheel working. Would be nice to get the eject button on the front working as well.

UPDATE: Got the scroll wheel on the mouse working. I had to do a hcicontrol hci0 reset at which point it saw the mouse and the scroll wheel started working. Seems the bluetooth adapter still "remembered" the mouse from when the laptop was running Windows and until I reset the adapter it wouldn't reacquire it.

UPDATE: Spoke too soon. The scroll wheel stops working after every reboot. If I want to get it working again I need to drop to the command line, run 'hciconfig hci0 reset' and then re-add the mouse with the task tray applet. This is needless to say a major pain in the butt. Looking for a solution, but I'm afraid I may need to add 'hciconfig hci0 reset' to a boot script somewhere.

---

### Post by kennethsoona on 2008-03-24
I installed Ubuntu 8.04 beta yesterday on my Sony tz21wn bought from official Sony Online Store.
sony-laptop module was aktivated by the installer so there was nothing to do.

the most important features for me are:
- supsend and hybernate mode
- hsdpa module (i have an o2 umts flatrate)
- sound
- hotkeys for mute and brightness
- hotkey for cd-opener because the button on the dvd-drive is very stupid small...

the hsdap module works after i installed comgt. the only things i have to now is:
```

echo 1 > /sys/devices/platform/sony-platform/wwanpower
comgt -d /dev/ttyUSB0
wvdial

```

and it works with the wvdial.conf postet here in this thread.

the hotkeys on the number keys working for me. the cd opener not.

the suspend mode and hybernate mode doesn't work. with this line in /etc/modprobe.d/alsa-base
```
/etc/modprobe.d/alsa-base
```
it doesn't work as well. 

with this line:
```
/etc/modprobe.d/alsa-base probe-mask=3
```
it works but only for one time. after a second reboot it doesn't work anymore...

are there any more conifgs i need?

---

### Post by orclev on 2008-03-26
I finally got around to adding the temperature sensor applet to the gnome panel and now I'm a bit worried. I've noticed the fan never seems to crank up really high like it did with Windows, and when I look at the temperature sensors I see values around ~65C (~145F) which seems awfully high. Is there a problem with the fan control on the Vaio TZs? Even without the proper fan control drivers shouldn't the firmware be keeping it cool?

---

### Post by hu5h on 2008-03-29
> **relmes said:**
> 
You can stop sonypi from being loaded by commenting out the "modprobe sonypi;" line in /etc/init.d/hotkey-setup (as mentioned by nyc_863 in earlier post). See example below:


Sony*)
#modprobe sonypi; # Needed to get hotkey events
modprobe sony-laptop
;;
"

As a bonus my Fn keys now also work for the screen brightness.   

Hope this helps those that are still stuck trying to get the HSDPA card working.

Thank you! Commenting out that line made my brightness buttons work!

---

### Post by starlily on 2008-03-30
> **hu5h said:**
> Thank you! Commenting out that line made my brightness buttons work!

I have a brand new FZ-340E. I used gparted and shrunk the windows partiton to 50GB, I havent tried to boot it yet. 

Installed a Hardy beta (Ubuntu Studio), ran update manager (276 updates).

The Good- 
SD slot works.
Wireless works!
Havent tried the video stuff yet, sry. 
Media buttons work to raise/lower volume, and fkey works for mute. 

The Bad- 
I cannot get the brightness to change, and I am going blind! Its very bright, and I cannot turn it down at all. I have commented out sonypi, and dmesg says sonly-laptop has loaded, but I still cant figure out how to control it. Fkeys have no effect, panel applet has a slash through it. 

The Ugly-
Or, not :) Once network is up, I had to enable the NVidia driver (restricted hardware dialog), then reboot, then I could just enable desktop effects from the dialog and it did the rest. Very nice! :) 

Please help me fix my brightness! Its the only flaw in an otherwise perfect install. 

Thanks, 
Lily

---

### Post by _teo_ on 2008-03-31
> **orclev said:**
> I finally got around to adding the temperature sensor applet to the gnome panel and now I'm a bit worried. I've noticed the fan never seems to crank up really high like it did with Windows, and when I look at the temperature sensors I see values around ~65C (~145F) which seems awfully high. Is there a problem with the fan control on the Vaio TZs? Even without the proper fan control drivers shouldn't the firmware be keeping it cool?

I don't t know whether this value is high. However I tried to find specifications and according to:
[HTML]http://processorfinder.intel.com/details.aspx?sSpec=SLA2U[/HTML]
the max temperature value is 100°C. My processor is U7600.

I measure here ~60°C and I don't hear the fan at lower temperatures. Just in case you can force the fan to spin if you echo 255 into /sys/devices/platform/sony-laptop/fanspeed.

Any further findings are welcomed.

---

### Post by orclev on 2008-04-01
> the max temperature value is 100°C. My processor is U7600.

I measure here ~60°C and I don't hear the fan at lower temperatures. Just in case you can force the fan to spin if you echo 255 into /sys/devices/platform/sony-laptop/fanspeed.

Any further findings are welcomed.

When I check the settings it lists the "critical" temperature as 100°C which according to the docs is the temperature at which it does a forced shutdown of the computer to prevent damage to the CPU. I have noticed the fan throttling up and down, although having temperatures in the 60-70 range still makes me a bit nervous, particularly when they spike up to around 75. Looking around at various sites it seems that the high/low point is totally dependent on the processor and where the sensor is mounted at relative to it, so I don't really have any way of knowing if this is a high value or not, it just subjectively seems high to me. On a related note, does anyone know what DTS1, DTS2, and ATF0 actually correspond to? From reading, I think ATF0 is the actual CPU censor, but I've got no clue about the other two. HD and GPU maybe?

---

### Post by orclev on 2008-04-02
Maybe someone who knows a bit more about bluetooth can help me. When I boot my computer and turn on my bluetooth mouse, it works, except for the scroll wheel. From reading other posts, this seems to be because it isn't "bonded" or whatever the appropriate term is. The mouse itself doesn't support any sort of authentication. When I check the bluetooth applet, it shows the mouse, and shows it as trusted, but not connected. If I remove the mouse and re-add it, it still doesn't show up properly, but if I do a `hciconfig hci0 reset` before I re-add it, it shows up as both trusted and connected and the scroll wheel works. Anyone have any suggestions for how to get this thing working properly without needing to do the `hciconfig hci0 reset`, and preferably without needing to do anything after each boot?

---

### Post by orclev on 2008-04-03
I've got a semi-fix to get the front eject button working. If you already have all the other media buttons working using the instructions from previous you're ready for this step, if not, go back to the earlier posts in this thread about getting the media buttons working and follow that.

Go into the /etc/acpi/events/ directory, and make sure you have the sony-eject config script. It's contents should look like so:
```

# Eject button on Sony Vaio TX3

event=sony/hotkey SPIC 00000001 0000001b
action=/etc/acpi/ejectbtn.sh
```

I've verified that on a TZ the code provided (1b) is correct. The problem is with the default /etc/acpi/ejectbtn.sh script, which attempts to fake a ACPI eject action:

```
#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_EJECTCD
```

For whatever reason, this isn't working on the TZ, the ACPI driver is probably the problem. Until that can be fixed however, you can still get the eject button working. Just use the userspace eject utility like so:
```

#!/bin/bash
#. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_EJECTCD
eject
```

---

### Post by maxtoor on 2008-04-05
Hi,
here's a  list of the supported/unsupported features in Hardy (8.04 standard beta CD, clean install with all updates) on my VGN-TZ31WN (italian model)

Works out-of-the-box:

Sound 
Motion Eye ( with r5u870-0.11.2 )
HSDPA modem ( with [https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/) )
Headphone Jack Sensing
Shutdown/Restart
Intel 950 Graphics
Wired Ethernet
Bluetooth
USB
Touchpad
DVD/CD Drive (burning -> yes reading -> yes)
Intel 4965 (A,G,N Wireless)
Integrated Media Buttons ( Front Eject Button -> added line eject to /etc/acpi/ejectbtn.sh)
FN Keys (f10 -> No f12 -> no)
Suspend/Resume :)

Not tested
Fingerprint Sensor
Memory Card Reader (Ricoh)

---

### Post by bossdak on 2008-04-05
Hi I'm new here. Does anybody tried the UPEK drivers for the fingerprint sensor?

They can be found here:
[http://www.upek.com/support/dl_linux_bsp.asp](http://www.upek.com/support/dl_linux_bsp.asp)

[http://www.upek.com/solutions/pc_and_networking/sdks/linux/](http://www.upek.com/solutions/pc_and_networking/sdks/linux/)

I tried it but I think it was too complicated for me :(

---

### Post by soulsurfa on 2008-04-06
HI All, 

just installed HARDY 8.04 beta 5 on my TZ27GN

Most things work that i have tried.

I've been through the whole thread above and found that most issues people have had are resolved with the newest release.

issues I'm having though are:
bluetooth - bt mouse works straight away but click wheel doesn't, haven't tried to resolve this yet.

bonding the phone only works after a 'hciconfig hci0 reset' but then the bt mouse won't work.

does anyone have any suggestions on how this could be fixed?

also haven't tried sd card but suspend works perfectly so far.

also not sure how to dial out through my nokia phone to use the 3G connection. help?

---

### Post by benoelmalo on 2008-04-06
> **mikerussellnz said:**
> Hi fellow TZ users!

I have the TZ webcam working.  I have added support for the Sony VCC7 camera found in the TZ series to the r5u870 camera driver and it is working with my VGN-TZ17!

Attached is the modified r5u870 source with the extra firmware file for the VCC7 that I extracted from the Windows driver.

Just compile it and it should work,  I used xawtv for testing.

 
Let me know if it works for you.   If it does, I  will submit it back to the author of the r5u870 driver.

Regards

Michael


It works great for me. I have a Sony VAIO VGN SZ 700. Thanks a lot.

---

### Post by soulsurfa on 2008-04-06
Webcam with skype on Hardy 8.04 beta 5 works out of the box..

just to let you know..

---

### Post by Aleph42 on 2008-04-07
Hi! Very useful post, thanks to everyone here.

I just got my VGN-TZ92HS ;  problems I still have right now:

1) integrated graphics are not working (no hardware accelaration) (945 chipset), and I don't have the option to use propriatary drivers with the "hardware driver" gui.

2) fan is running to quick for my taste; lm-sensors only detect processor emp (might be fixed when i get the 945 properly installed), and if I echo to /sys/device/platfeorm/sony-laptop/fanspeed, it resets automaticaly. I can do it every tenth of seconds, but I'd rather check if some other script is not using it first.

WARNING: I'm not running the latest beta of hardy (I think I have beta 4... how can I check?), so some stuff might be gone in later versions. But my version is up to date.

---

### Post by orclev on 2008-04-07
> **soulsurfa said:**
> HI All, 

bluetooth - bt mouse works straight away but click wheel doesn't, haven't tried to resolve this yet.

bonding the phone only works after a 'hciconfig hci0 reset' but then the bt mouse won't work.

Sounds very similar to the problem I'm having. I don't have a BT phone, just the BT mouse, but I have to do some work to get the scroll wheel working as well. Essentially the problem seems to be (near as I can tell, don't know much about BT) with the firmware for the bluetooth circuit restoring connections to previously bonded devices, but the OS not picking up on it. If I turn my mouse on, it works, the scroll wheel doesn't work, and it shows up as a trusted device in the bluetooth applet, but not connected. That is, the OS seems to know about the mouse, but doesn't think it's actually running. 

Running 'hciconfig hci0 reset' resets the bluetooth controller and forces it to forget what it was bonded to previously, so the next time I click the connect button on my BT mouse, it shows up as a new device (**important**: you need to remove the entry for the BT item from the bluetooth applet before running hciconfig hci0 reset, and before pressing the connect button on the device). Once the device has been "re-discovered" and re-added using the bluetooth applet, it shows up as both connected and trusted and works just fine.

Try the following and let me know if it works for you. Go to the applet and remove all your bluetooth devices (you can leave them as trusted, just go to each service section [input service, audio service, etc.] and remove any listed devices). Next run 'hciconfig hci0 reset', you should see a message popup on the applet telling you that the device has been made discoverable or whatever the last state it was in is. Now open up the preferences, go back to the device list, and push connect on your devices and start adding them all back in. I've discovered on my mouse that after I push the connect button and try to add it, if I move it around too much before the applet says it's been added, it will show up as added, but not connected and I have to go through the whole process again.

What I don't know how to do at this point, is find a way to make the mouse connect properly the first time without having to reset the bluetooth controller every single time I boot the computer, which is a complete and utter pain in the butt.

---

### Post by orclev on 2008-04-08
> **Aleph42 said:**
> Hi! Very useful post, thanks to everyone here.

I just got my VGN-TZ92HS ;  problems I still have right now:

1) integrated graphics are not working (no hardware accelaration) (945 chipset), and I don't have the option to use propriatary drivers with the "hardware driver" gui.


As far as I know their are no proprietary drivers for the 945 chipset, although the stock xorg driver should provide acceleration. What output are you getting from glxinfo? As an example here's mine:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x71 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

As for the fan, I seem to be having the opposite problem, with it running so slow it makes me nervous at times. When I check the value in the fanspeed file it's usually fairly low. Right now for example it's 35 (with the temperature probes registering about 60°C), and I can't even hear the fan over the buildings AC, or the sound of the desktop on the other side of my desks partition.

I'm not sure exactly which version of hardy I have installed either. I downloaded the latest beta about a month ago, and I've been applying all the updates since then (gone through 2 new kernels), so I'm assuming it should be on par with whatever the latest release is.

---

### Post by orclev on 2008-04-08
> **bossdak said:**
> Hi I'm new here. Does anybody tried the UPEK drivers for the fingerprint sensor?

They can be found here:
[http://www.upek.com/support/dl_linux_bsp.asp](http://www.upek.com/support/dl_linux_bsp.asp)

[http://www.upek.com/solutions/pc_and_networking/sdks/linux/](http://www.upek.com/solutions/pc_and_networking/sdks/linux/)

I tried it but I think it was too complicated for me :(

I got the BioAPI SDK installed, but the UPEK TFMESS BSP won't install for me because I'm running the 64 bit version of hoary and the binary being distributed on that website is compiled against a 32 bit kernel. Going to need someone with a 32 bit copy to test this.

FYI, the steps for installing this are as follows:

Download bioapi-1.2.2.tar.bz2
Make sure you have gcc-c++ installed (by default only gcc is usually installed)
extract bioapi-1.2.2.tar.bz2 to a directory (bioapi-1.2.2 is what I used, but the directory doesn't matter)
```
tar -xvjf bioapi-1.2.2.tar.bz2
```
When I'm doing work that's going to require root permissions rather than use sudo all over the place, I just switch to a root shell (don't forget to exit that shell when your done, and BE CAREFUL, you can seriously screw up the system running as root):
```
sudo -s
```
Compile the code
```

cd bioapi-1.2.2
./configure --with-Qt-dir=no
make LDFLAGS='-R /usr/local/lib'

```
At this point I got an error and had to go edit a file.
Edit line 458 of addins/dl/mds/dal_classes.h and delete the part that says DAL_DATABASE_INFO_LIST::
It should look like so afterwards:
```

        CSSM_RETURN GetDBNamesAndParameters(
                                CSSM_DL_DB_HANDLE DLDBHandle,
                                DAL_DB_OPEN_PARAM_PTR pParam);

```

Run make again, followed by make install
```

make LDFLAGS='-R /usr/local/lib'
make install

```

Download TFMESS BSP and extract it somewhere. Then CD into that directory and run the install.sh script file (may need to make it executable first).
```

cd tfmessbsp
chmod u+x install.sh
./install.sh

```

At this point I get the following error because I'm running 64 bit:
```

Installing TouchChip TFM/ESS Fingerprint BSP ...
/usr/local/lib/libtfmessbsp.so: wrong ELF class: ELFCLASS32Could not load addin module "/usr/local/lib/libtfmessbsp.so"!

```

If anyone gets farther than this let me know. If this works ok in 32 bit, maybe we can convince the manufacturer to release a 64 bit build. Also, if you have this working and want to configure it to allow logins, there's a pdf in the bioapi zip with instructions for configuring PAM to use the fingerprint sensor.

---

### Post by bossdak on 2008-04-08
i got this error when i try "make LDFLAGS='-R /usr/local/lib'"


make[1]: Entering directory `/tmp/bioapi-1.2.2/addins/dl/mds_install'
/bin/bash ../../../libtool --tag=CC --mode=link gcc  -g -O2  -R /usr/local/lib -o mds_install  dl_portreg.o ins_mds.o mds_install.o ../../../framework/port/libport.la ../mds/libbioapi_mds300.la ../../../framework/bioapi_util/libbioapi_util.la -lpthread -ldl 
gcc -g -O2 -o .libs/mds_install dl_portreg.o ins_mds.o mds_install.o  ../../../framework/port/.libs/libport.a ../mds/.libs/libbioapi_mds300.so ../../../framework/bioapi_util/.libs/libbioapi_util.a /tmp/bioapi-1.2.2/framework/mds_util/.libs/libmds_util.so -lpthread -ldl -Wl,--rpath -Wl,/usr/local/lib
gcc: ../mds/.libs/libbioapi_mds300.so: No such file or directory
make[1]: *** [mds_install] Error 1
make[1]: Leaving directory `/tmp/bioapi-1.2.2/addins/dl/mds_install'
make: *** [all-recursive] Error 1

I cd to the mds/.libs directory and found these links are broken

lrwxrwxrwx 1 root root     25 2008-04-09 03:31 libbioapi_mds300.so -> libbioapi_mds300.so.0.0.0
lrwxrwxrwx 1 root root     25 2008-04-09 03:31 libbioapi_mds300.so.0 -> libbioapi_mds300.so.0.0.0

I try to find this file libbioapi_mds300.so.0.0.0 but cannot locate it.

---

### Post by Aleph42 on 2008-04-08
Ji orclev, thanks for answer.

the output of glxinfo is:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

The problem being the "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)". Hum, actually this seems to mean that some option must be setting direct rendering off.

I'm surprised that there is no propriatary driver for 945; is there at least a way to get temperature readings from the chipset (that was my initial problem)

> **orclev said:**
> 
As for the fan, I seem to be having the opposite problem, with it running so slow it makes me nervous at times. When I check the value in the fanspeed file it's usually fairly low. Right now for example it's 35 (with the temperature probes registering about 60°C), and I can't even hear the fan over the buildings AC, or the sound of the desktop on the other side of my desks partition.


My fan defaults at 35 too, and that's what I find to loud. Sure if you are in a loud environment it doesn't change anything, but personally I bought my vaio with SSD SPECIFICALY for the silence. Indeed I thought it had no fan at all, and I'm pretty disappointed that it has to run that fast.

Setting it to a lower value manually (with /sys/device/plateform/sony-laptop/fanspeed ) works, but you have to do it continuously since it resets itself in permanance. I hope this is not a bios thing.

---

### Post by orclev on 2008-04-09
> **bossdak said:**
> 
I cd to the mds/.libs directory and found these links are broken

lrwxrwxrwx 1 root root     25 2008-04-09 03:31 libbioapi_mds300.so -> libbioapi_mds300.so.0.0.0
lrwxrwxrwx 1 root root     25 2008-04-09 03:31 libbioapi_mds300.so.0 -> libbioapi_mds300.so.0.0.0

I try to find this file libbioapi_mds300.so.0.0.0 but cannot locate it.
Hmm, when I look at those files I find both of them and the symlinks. I think maybe they're built earlier in the build process. Maybe try a make clean and then try to build it again? Baring that extract the archive again. Not sure what else to say, other than I downloaded 1.2.2 and it seems to build fine. It's only the binary distribution of the fingerprint reader driver that's causing me problems.

---

### Post by orclev on 2008-04-09
> **Aleph42 said:**
> 
I'm surprised that there is no propriatary driver for 945; is there at least a way to get temperature readings from the chipset (that was my initial problem)
Intel has released the drivers for the 945 as open source and they've been rolled into the xorg distribution, so the xorg ones are effectively the proprietary ones. As for temperature readings, I've got three readings on my system, all with names I can't understand (don't know much about temperature probes). What I have is DTS1, DTS0, and ATF0. From what I've read, I think ATF0 is the CPU temperature, which leads me to believe that DTS1 and DTS0 are probably some combination of GPU and HD.

> **Aleph42 said:**
> 
My fan defaults at 35 too, and that's what I find to loud. Sure if you are in a loud environment it doesn't change anything, but personally I bought my vaio with SSD SPECIFICALY for the silence. Indeed I thought it had no fan at all, and I'm pretty disappointed that it has to run that fast.

The selling point for the SSD drive was the low power drain and fast access times, running quietly is just a nice perk. I'm afraid if you want a fanless system you're going to have to go with something a lot lower powered and/or much larger than the vaio. Passive cooling of even a moderately powerful CPU such as the one in the vaio is going to require a very large heatsink, and it's simply not possible to keep things compact with a big heatsink slapped in there. Now, if you were running a single core CPU, say around 500 Mhz, you might be able to get away with something close to the size of a vaio. See for instance a ultra-low power desktop system like this: [http://www.aleutia.com/products/]("http://www.aleutia.com/products/"). As an aside the CPU in the vaio TZ is actually underclocked, and if running at full power would require a much beefier cooling system.

> **Aleph42 said:**
> 
Setting it to a lower value manually (with /sys/device/plateform/sony-laptop/fanspeed ) works, but you have to do it continuously since it resets itself in permanance. I hope this is not a bios thing.
Actually I think it's in the ACPI firmware. The firmware defines a set of temperature ranges that dictate various responses. By default it runs at 35 (RPM?) it seems, and only cranks up the fan speed at certain temperature thresholds. I don't know about you, but running at even 65 Celsius makes me a bit nervous, but then again I've had fans fail and CPUs cook on me before. It is possible to replace the firmware and change the defaults, but it's definitely not recommended because you risk frying your shiny new laptop.

---

### Post by Aleph42 on 2008-04-10
> **orclev said:**
> I don't know about you, but running at even 65 Celsius makes me a bit nervous, but then again I've had fans fail and CPUs cook on me before. It is possible to replace the firmware and change the defaults, but it's definitely not recommended because you risk frying your shiny new laptop.

I have some experience with overclocking, water cooling and overheating CPUs; from what I've seen, 65 degrees is actually a pretty standard running temperature, and, when your CPUs really does overheat, you generally have warnings like errors (I had random color pixels on extures with an overheating gpu once), and also the system generally shuts down itself (harware initiated) when reaching critical values.

So, give me those risky ways of meddling with the ACPI !

Still, things that could go wrong:
1) the temp you read are not actually from sensors inside the cpu, but a little outside, giving you a temperature that is too optimistic (unlikly with chipset issued sensored)

2) Even with the automatic shutdown/ warnings, you still could make irreversible damages (I don't think it could happen, but again that's just my non expert opinion)

For information, setting the fanspeed at 18 (and that's not RPM, btw; it goes from 0 to 255) is way quieter, and if I'm just typing in consoles/browsing the web (without flash), my CPU temperatures stay under 63 degrees.
Those temps are located at cat /sys/devices/platform/coretemp.0/temp1_input (and the same with coretemp.1), and are rea by the "sensors" command.

To set the fanspeed, I used that command:
```

while true ; do sleep 0.005 ; echo "18" > /sys/devices/platform/sony-laptop/fanspeed ; done
```
run as root.

So my questions are:
1) Where did you get those DTS0, DTS1 and ATF0 temperatures? (exact location, and packages installed to get them)
2) How to access that ACPI and tell him to let me manage the fans ?
3) What model eactly is your vaio? Bcause, since the diferrence between the temp we get is so big, it might be that I have better cooling/power efficiency, or the wrong readings!

And again, thank you for answering!
Btw, webcam is recognized zith the latests update, but works poorly (distorted image)

---

### Post by orclev on 2008-04-10
> **Aleph42 said:**
> 
So my questions are:
1) Where did you get those DTS0, DTS1 and ATF0 temperatures? (exact location, and packages installed to get them)
2) How to access that ACPI and tell him to let me manage the fans ?
3) What model eactly is your vaio? Bcause, since the diferrence between the temp we get is so big, it might be that I have better cooling/power efficiency, or the wrong readings!

And again, thank you for answering!
Btw, webcam is recognized zith the latests update, but works poorly (distorted image)
Ok, I'm going to run through these in reverse order (because it's easier that way).

3) I've got a TZ250N/B, although I'm not certain the temperatures are all that different. On a cold boot it's usually around 35C to start with, and slowly works up to a running average of about 63C. If I'm doing something intensive it can spike all the way up to 75C but I've yet to see it get much beyond that (maybe a degree or two). It just makes me nervous having such small buffer between the current temp and the "OMG SHUTDOWN!!!" temp of 100C. It also just "feels" hot to me because I can put my hand on the bottom of the computer and it feels almost too hot to touch. Plus being a laptop if I even reduce the lifetime of the system due to thermal stress it's a major deal as I'll pretty much have to replace the whole thing, not just slap in a new CPU.

2) I read it in a forum somewhere (found it while trying to figure out if my computer was cooking itself or not). I've got to go back and look it up, but it had something to do with flashing a customized data table to some piece of firmware. I'll go look it up again and get back to you.

1) I'm getting those values from the GNOME sensors-applet. Looking through the list of loaded modules it seems that the thermal module is the one reporting the values. Specifically the following all seem to be interrelated: processor, acpi_cpufreq, thermal, cpufreq_ondemand, cpufreq_stats, freq_table. I didn't have to do anything to get all those modules loaded, they loaded by default when I installed Hoary.

UPDATE: Ok, so I went back and did some research. Turns out my system is supporting the temperature sensors, but doesn't support ACPI control of the fan for whatever reason (that is Linux doesn't know how, I'm sure it's possible though). The table I was thinking about earlier is something called a DSDT and is apparently part of ACPI supplied by the BIOS and hardware vendor, but for whatever reason tends to get screwed up by the vendor (see here for details [http://acpi.sourceforge.net/dsdt/index.php]("http://acpi.sourceforge.net/dsdt/index.php")). If your system is already working (that is ACPI seems to be functioning ok) it shouldn't be necessary to muck with the DSDT.  Assuming control of the fans is supported by ACPI, it should be possible to echo a new set of threshold values to /proc/acpi/thermal_zone/<SENSOR>/trip_points, and have the fan speed properly controlled by ACPI. As I said however, at least on my laptop only the critical stop temperature is being reported as available, so the contents of my trip_points file looks like so:
```

critical (S5):           100 C
passive:                 86 C: tc1=1 tc2=2 tsp=50 devices=CPU0 CPU1

```
But if it was properly supported should look something like this:
```

critical (S5): 93 C
passive: 90 C: tc1=2 tc2=3 tsp=100 devices=0x0357b280
active[0]: 70 C: devices=0x0357bc00
active[1]: 60 C: devices=0x0357bd20
active[2]: 50 C: devices=0x0357be4

```

For more info see the following:
[http://tldp.org/HOWTO/ACPI-HOWTO/resources.html]("http://tldp.org/HOWTO/ACPI-HOWTO/resources.html")
[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt")

---

### Post by orclev on 2008-04-10
I suspect my lack of fan controls may be caused by a buggy DSDT. The VAIO TX series is listed as having known problems, so it doesn't seem like much of a stretch for the TZ to also have problems. At any rate, I'm working on decompiling the stock DSDT and searching for problems, and if I find them I'll post what I found, and if possible a patched DSDT as well.

UPDATE: No dice, the DSDT seems to be fine. The tutorial I was following said that after I recompiled it if I got any warning the DSDT was the problem, but it compiled with no warnings or errors. It might still be the DSDT, but I'm going to have to go digging through the ACPI spec to figure out if it is or not. I did check the DSDT, and their are a couple places it fingerprints the OS to adjust some things, so I may try tricking it into thinking it's booting Windows and see if I get any functionality back (interestingly it actually looks to see if it's running under Linux in one spot as well).

---

### Post by mrmarvel on 2008-04-15
Gooh Job every one!!

---

### Post by bossdak on 2008-04-18
> **orclev said:**
> Hmm, when I look at those files I find both of them and the symlinks. I think maybe they're built earlier in the build process. Maybe try a make clean and then try to build it again? Baring that extract the archive again. Not sure what else to say, other than I downloaded 1.2.2 and it seems to build fine. It's only the binary distribution of the fingerprint reader driver that's causing me problems.

I downloaded again the bioapi-1.2.2.tar.bz2 and finally installed it. I tried to install pam_bioapi-0.2.1 but I got this error during package configuration.


```
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking security/_pam_macros.h usability... no
checking security/_pam_macros.h presence... no
checking for security/_pam_macros.h... no
configure: error: cannot find required header: security/_pam_macros.h
```

which package does _pam_macros.h belong to? I want to install that package.

---

### Post by iamRoko on 2008-04-20
Well, my TZ got stolen last week.. Meaning the wait until 8.04 is officially released is that much easier and I get to install linux all over again from scratch when insurance replaces it. 

But I still hate thieves. I had a couple things on there that weren't backed up. Ugh. :mad:

---

### Post by master_kernel on 2008-04-20
Have you tried fprint?
[http://ubuntuforums.org/showthread.php?t=760018]("http://ubuntuforums.org/showthread.php?t=760018")

---

### Post by orclev on 2008-04-21
> **bossdak said:**
> 
checking security/_pam_macros.h usability... no
checking security/_pam_macros.h presence... no
checking for security/_pam_macros.h... no
configure: error: cannot find required header: security/_pam_macros.h[/CODE]

which package does _pam_macros.h belong to? I want to install that package.

I would guess that would be in the pam dev packages. That being said, I don't seem to have any of the pam dev packages installed and I don't get that error. What I do have installed is libpam0g, libpam-modules, and libpam-runtime.

---

### Post by orclev on 2008-04-21
> **master_kernel said:**
> Have you tried fprint?
[http://ubuntuforums.org/showthread.php?t=760018]("http://ubuntuforums.org/showthread.php?t=760018")

From the links on that page it doesn't look like the fingerprint scanner on the vaio is supported. I installed fprint and tried to get it to work, but it says it can't find a fingerprint scanner, so it would appear it's a no go. From what was said on their it may be that the UPEK binary I was trying to get working probably won't work either, even if I could get a 64 bit binary, as they say on one page that Sony installed custom firmware so only Sony software can use the fingerprint scanner.

---

### Post by quinthar on 2008-04-27
I have a new Sony TZ270N/B and here's my report installing a stock 8.04 (alternate) CD (with full-disk encryption):

Worked out of the box:
- Sound
- Wired Ethernet
- Wireless Ethernet
- Touchpad
- Shutdown/Restart
- FN Keys
- Correct screen resolution
- Headphone jack sensing
- CD burning
- Integrated media buttons
- USB

Worked with tweaks:
- Sprint EVDO modem (thanks a.r.jomar!)
[INDENT]  1) Turn on (must be done once every reboot/resume):
        [INDENT]sudo su
        echo 0 > /sys/devices/platform/sony-laptop/wwanpower
        sleep 1
        echo 1 > /sys/devices/platform/sony-laptop/wwanpower[/INDENT]
  2) Edit /etc/rc.local (add the following before "exit")
        [INDENT]sudo modprobe -r usbserial
        sudo modprobe usbserial vendor=0x1410 product=0x2120[/INDENT]
  3) Install and configure KPPP
        [INDENT]sudo apt-get install kppp
        Configure /dev/ttyUSB0 as the modem device in kppp
        Choose #777 as the dialup number
        Use "user" as the username, and "user" as the password[/INDENT]
[/INDENT]
- Suspend / Hibernate
[INDENT]. Add "options snd-hda-intel probe_mask=1" to the end of /etc/modprobe.d/alsa-base (note the underscore, not a dash!)
. Create a file named /etc/pm/config.d/modules containing the following: (thanks abgesq!)
[INDENT]SUSPEND_MODULES="ehci_hcd uhci_hcd"[/INDENT]
. Hibernate spews a million "usb 5-6: clear tt 1 (9072) error -1" lines to the console, but they seem benign
[/INDENT]
- Motion Eye (thanks ltorgo!)
[INDENT]. Just follow the instructions here: [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation), specifically:
[INDENT]svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) r5u870
cd r5u79
make
sudo make install
sudo sudo modprobe r5u870
[/INDENT]
[/INDENT]

Not tried yet:
- Bluetooth
- DVD reading/burning
- Fingerprint Sensor
- Memory Card Reader (Ricoh)

I'll update this as I experiment, with workarounds.  (I expect most of these problems are already solved in the thread above, but I haven't read through the entire thing.)

---

### Post by abgesq on 2008-04-30
On the suspend issue, I've had luck (so far, knock on wood, etc.) adding the following line to /etc/pm/config.d/modules:

SUSPEND_MODULES="ehci_hcd uhci_hcd"

You may get some error messages when you select suspend, but so far it works to suspend the system.

---

### Post by lfernandosg on 2008-05-05
I wanted to know the duration of your battery because mine is lasting 1: 00hs the less. excuse English but it is that am of the brazil. In the windows the dvdr-w is also turned off to save energy and with that the hard bateiria 6: 00hs while in the ubuntu 4: 00hs. 

 as I do to turn off the dvdr-w for the battery to last more and to leave the duration same or better than the seen windows because I know that the linux better management the energy d that the windows. Reminding that the powernowd is activated and the shine of the monitor is low.

my model: TZ150NB

---

### Post by manato on 2008-05-06
Running Hardy with TZ250N
Out of the box not working are...
Webcam, 
Finger Print, 
SD/Memory card, 
Spring WWLan, 
Hibernation/Suspend, 
Modem
Media Function key

Some errors
Dim function is working, but however PM is causing the system not to save the DIM settings, there was a post on it somewhere but have yet to fix the problem on mine.


As for Battery,
Without the ability to shutdown CDROM or reduce CPU usage
or DIM the laptop
I am getting about 2.5hrs


Back on XP
Will full blown battery save with 30% brightness, i get about 5.5hrs
Stock Battery

---

### Post by orclev on 2008-05-06
> **lfernandosg said:**
> I wanted to know the duration of your battery because mine is lasting 1: 00hs the less. excuse English but it is that am of the brazil. In the windows the dvdr-w is also turned off to save energy and with that the hard bateiria 6: 00hs while in the ubuntu 4: 00hs. 


Are you reporting the actual lifespan for a fully charged battery, or what the battery applet is estimating? In my experience I get about 3 hours out of mine without turning anything off and with the monitor brightness turned down just a little. Of course the battery applet is usually a bit off, often reporting estimates of 4 or 6 hours, or sometimes dropping to 2.

---

### Post by lfernandosg on 2008-05-07
I carry  the baterria completely and I make the test. He/she/you only gave 4 hours with to I shine of the low monitor. I tested until him to hibernate. In the Seen windows she gives 6:00 hours.

 I placed  he with the command cpufreq-set for powersave but even so it lasts little. Do you know as incapacitating the dvdr-w as the seen windows he/she does to save battery for me the duration to be seen it increases?

manato,

 like you he/she did for intalar and to configure Finger Print,Hibernation/Suspend and mic??can happen?

---

### Post by _teo_ on 2008-05-07
> **manato said:**
> 
As for Battery,
Without the ability to shutdown CDROM or reduce CPU usage
or DIM the laptop
I am getting about 2.5hrs


Back on XP
Will full blown battery save with 30% brightness, i get about 5.5hrs
Stock Battery

You should be able to turn the CD drive off:
1) become root
```
sudo -s
<your password goes here>
```
2) turn the CD drive off
```
echo 0 > /sys/devices/platform/sony-laptop/cdpower
```

[-X ! and please be cautious when you act as root ! [-X

---

### Post by lfernandosg on 2008-05-08
and to activate of turn the cd it would be: 
echo 1 > /sys/devices/platform/sony-laptop/cdpower

another thing, I am with the ubuntu 8. 04 installed end and the camera normal fucniona but the times the image is a lot of grtande and I only get to see if opens Xawtv and to increase the screen for fulll screen.

is that happening with anybody? and the microphone as I place to work?

---

### Post by lfernandosg on 2008-05-09
I made the test. in it dresses him/it the battery it lasted 5: 55 until hibernating and the ubuntu only gave 4: 00 even with d turned off dvdrw, what can be since the linux management very well the energy?

---

### Post by zakeen on 2008-05-11
has anybody got there mic working under skype? how did u do it?

---

### Post by lfernandosg on 2008-05-12
I made a test with an ear phone + microphone and it works like this. . the mic embedded in(microfone doesn't only work). But did nobody get to solve the problem of the battery?

---

### Post by ltorgo on 2008-05-13
I've a TZ21XN/B (european model basically a U7600,2Gb, 100Gb 4200rpm).

I'm currently running Kubuntu 7.10 64bits and everything apart from Hibernate works fine... well with the exception of sound that is terribly low but it works.

One of these days I could not resist and tried the new Hardy. Still decided to maintain my 7.10 installation (and I'm glad I did!).

The things I cannot live without:
1) Suspend
2) Sound and mic
3) Camera (for Skype)
4) Good battery life

Here are my experiences (out of the box):

i) Ubuntu 8.04 32bits 
Not working: camera, hibernate
As these were part of my must set I immediately gave up... maybe other things did not work out...

ii) Kubuntu 8.04 32bits
Not working: mic (after some tunning I managed to put it working), camera (some times works some times it does not!)
Working better than 7.10: sound is loud finally, hibernate worked a few times but now it is not working anymore...

In summary, with the camera like this I have to go back to 7.10 for now... I'll try to tune it in my spare time but for now it is a failure for me...

P.S.: The way I managed to put the mic to work was by using the same stuff  there was on the /etc/modprob.d/alsa-base file of my 7.10 installation...
namely:
options snd-hda-intel model=sony-assamd

---

### Post by ltorgo on 2008-05-14
Some updates on my Kubuntu 8.04 32bits installation: 

1) I've managed to put the camera to work with the R5u870 module following the instructions [here]("http://wiki.mediati.org/R5u870").

2) The media buttons work as well as the FN keys

3) Suspend works, but hibernate not. When I start the latter it prompts some complaint on not finding the swap (!)... strange, probably I need to work a bit more on this one...

In summary, with the exception of Hibernate I'm almost at the perfect setup within Kubuntu. Well I wished compiz worked a bit better (it is too erratic, lots of stuff (e.g. kwallet) do not end up on the sys tray and things like that)

---

### Post by ltorgo on 2008-05-14
Yet another update on my Kubuntu 8.04 32b install.

I googled a bit on hibernate and finally managed to get it to work. It was not that difficult (now I even remember doing something similar in a previous version...).

The solution:
Went to the /boot/grub/menu.lst file and on the entry of my installation 
added a resume option making it look like this:
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=fe14f446-7cc3-4f6a-bcde-e4c58ebab4c1 ro quiet splash resume=UUID=0b13b111-429e-4c4a-b93c-8c0f648c6ca2

Obviously you need to put the UUID of your own swap partition. You may get it at the /etc/fstab file

After a reboot hibernate started to work! (well just tried it once but I guess it works)

So finally after the MIC, camera and hibernate tweaks I have an installation that is working 100% for me on my TZ! I'm happy! 

There are a few things that I still didn't tried like the Memory Card reader but these are irrelevant for me so I really don't care if they work or not...

---

### Post by lfernandosg on 2008-05-17
ltorgo,
which the duration of your battery? does he/she know how to say because it lasts much less than in the windows windows?

---

### Post by astadolfo3 on 2008-05-17
ltorgo thank you very much for your posting on hibernate. I have a VGN SZ540 where hibernate and suspend stopped working after I upgraded to Gutsy, and Hardy did not solve the issue. I searched everywhere but nothing seemed to work until I tried your solution. After adding the entry on then menu.lst Hibernate worked for a couple of times, then stopped working again, weird!. Suspend was never fixed after it stopped working when I upgraded to Gutsy.

---

### Post by marcip3 on 2008-05-17
hi,

i have one question. i want to buy a sony vaio tz21. is it possible to use the webcam under ubuntu in skype? i need it very often...

thx
marcip3

---

### Post by ltorgo on 2008-05-18
lfernandosg: I really don't know... it seems to last time enough not to bother me, but I can't give concrete times but maybe one of theses days I do some testing. Regards the comparison to Windows, sorry I have no Windows anymore on my TZ.

astadolfo3: I'm sorry to learn that it stopped working for you... it is in effect weird... for me it has been work well, zero failures till now...

marcip3: As I've mentioned on one of my posts above I've managed to put it to work on Hardy following the instructions of the link in my post.

---

### Post by ltorgo on 2008-05-19
lfernandosg: 
I did the test today. After a 100% recharge I let it run down while I worked. The conditions where the following:
- wireless/bluetooth switched off; editing files, some compilations, one processor intensive experiment (basically 100% CPU usage during around 15mins), always listening to music (MP3s on Amarok), occasional browsing, a few downloads and screen set to around 70% brightness.

The battery lasted 5 hours (well after 5 hours it was time to go home and the applet was saying 10 mins left...).

Obviously this is with the standard battery that came with the laptop. Overall, this was what I was expecting and I'm happy with the result.

---

### Post by lfernandosg on 2008-05-19
1)were you with turned off wireless? if yes, with me with the wireless deligado lasts also 5 hours. . . and in the windows it goes close at 7 hours. 

2)oes my microphone work connecting an external microphone but in the case of using the built-in microphone doesn't work, like you he/she did do for yours usnado it works the own microphone of the notebook? 

3)did you get to place the finger print reader?

: I will reinstall the ubuntu through the cd. I installed of a dvd and now it began to present problems in the boot and when restarting. . . it is a black screen with lines closing programs and he/she doesn't close.

---

### Post by zerubbabel on 2008-05-21
Has anyone gotten the fingerprint reader to work? or the memory card reader?

---

### Post by ltorgo on 2008-05-26
Update to my previous personal 100% success story:

- Unfortunately, I've to report that putting the machine into suspend "spoils" the web cam... that is, everything is working but after restoring from a suspend the web cam does not work anymore (well actually it works but with the image completely spoiled up to a point that you only see some movements but you cannot see what is going on). Strangely enough hibernate does not have that effect... So if I want to stay with the web cam working I cannot suspend which is boring as hibernate takes ages to both hibernate and restoring... anyway that's my current setup I'm afraid... it's odd that on 7.10 suspend and the web cam worked fine together, though hibernate did not work at all...

---

### Post by benste on 2008-05-26
Someone told me that HSDPA modem works in hardy with vodafone mobile connect software for linux - the device was called hurican ...

MAybe you change these infos on your first post

---

### Post by scicode on 2008-05-27
Hi here I have a tz21mn and thanks to the help of you I got all the nice features to work, however i have a problem with the vga output.

When I fist installed Ubuntu I used Feisty to create the xorg.conf since Gutsy did not recognize the 1366x786 screen resolution. However I never got the vga out to work. On some page i found that you can add
```
Section "Monitor"
...
 Option          "MonitorLayout" "CRT,LFP"
 Option          "Clone" "true"
```
and now it works, but not very good. Yes I have no clue what I really did there. I also tryed xrandr as it was descibed in this thread before but I cannot get any of the xrandr commands to show any effect. My guess is that my xorg.conf is not correct. Can you please help me? Maybe if you have an tz21mn with working x you could send me your xorg.conf

Thanks already and here is something that I found but have not tryed out yet which definetly belongs in here: _[COLOR="Blue"][making the instant-on mode work without windows installed]("http://hacesol.net/installing-kubuntu-linux-on-a-sony-vaio-tz21mn")[/COLOR]_
Since I deleted my windows partition i will be hard to try it out but in case some of you still have their win partition it would be nice to share your instant-on data with me ... and the rest of the world :D

---

### Post by ltorgo on 2008-05-27
I have some more bad news concerning the web cam.

After upgrading to the new kernel (2.6.24-17) released yesterday, and after compiling the r5u870 module as I did before, the web cam does not work at all!

So in summary, I can only have the web cam working if:
1) use the 2.6.24-16 kernel
2) do not use suspend

Sad news for me... I guess 100% compatibility is still far...

---

### Post by ltorgo on 2008-05-27
What is even more strange, after posting my previous reply, and running now the 2.6.24-17 kernel (that I've reported not working with the web cam), guess what? the web cam is working! strange.... I can assure you that yesterday did not work (and yes I did several reboots after installing both the new kernel and the r5u870 module)... I'll give it a try in the next few days and then report again on this annoying issue! Sorry about the mess

---

### Post by acca74 on 2008-05-29
Ubuntu 8.04 32bit on TZ21MN:
For the webcam, I just found this repository
[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)

I chose my version of the kernel
2.6.24-17-generic

I clicked on the file
ricoh-webcam-r5u870-2.6.24-17-generic_0.11.0-1arakhne1_i386.deb

...and all went through automatically.

I then checked with Skype that the webcam works.
It was late so I didn't try to make a call and test the mic as well.

---

### Post by maxtoor on 2008-06-01
Sony TZ31WN
Good news
after updating today (hardy backports repo selected :confused:) my webcam works perfectly under skipe and ekiga -> Sony VGP-VCC7 # 1 (/ dev/video0)
without r5u870a
But does not seem to work with Cheese

---

### Post by maxtoor on 2008-06-01
[http://140.164.23.2/~mysony/](http://140.164.23.2/~mysony/)

---

### Post by maxtoor on 2008-06-01
> **scicode said:**
> 
Since I deleted my windows partition i will be hard to try it out but in case some of you still have their win partition it would be nice to share your instant-on data with me ... and the rest of the world :D

ooops

[http://140.164.23.2/~mysony/](http://140.164.23.2/~mysony/)

---

### Post by scicode on 2008-06-02
> **maxtoor said:**
> ooops

[http://140.164.23.2/~mysony/](http://140.164.23.2/~mysony/)

nice, thanks alot maxtoor

can you please also post your xorg.conf for me???

---

### Post by maxtoor on 2008-06-02
> **scicode said:**
> nice, thanks alot maxtoor

can you please also post your xorg.conf for me???

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
        Option          "SHMConfig"             "true"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```
	

does not seem to say nothing special :confused:
but works perfectly
attached the image of my desk

---

### Post by scicode on 2008-06-02
thanks again now my vga out is working :D

---

### Post by miSAKe on 2008-06-04
Thanks everyone very much who has contributed to this thread, it helped me decide what laptop to buy and then to get a few outstanding things working.

Running Ubuntu 8.04 x64 on Sony Vaio VGN-TZ11XN

Straight install completely removing all traces of windows and the recovery partition, everything worked straight away with 2 exceptions, 
1. finger print scanner
2. Card reader

after installing all updates suspend stopped working but the fix on the previous pages worked. Thanks abgesq.

Anyone managed to get the fingerprint scanner or card reader to do anything useful?


A few small issues I'm having that i cant work out, 

1. the mouse cursor appears in the centre of the screen during full screen games and hardware accelerated applications, enabling SWCursor in xorg.conf fixs this but causes direct rendering to be disabled for everything is there a work around for this... an intel driver specific issue rather than TZ? Films do not have this issue through VLC.

2. I cannot get scaling turned off on the LCD, the option in the BIOS is turned off yet once X loads all resolutions get scaled to full screen, I have tried these options to no avail;
	Option		"NoStretch" "true"
	Option		"LcdCenter" "true"
	Option 		"SuspendHack" "true"
my guess is that they aren´t supported by the intel driver so again not TZ specific issue, anyone found a way to maintain the AR in full screen games not in native res, again films are fine through VLC.

3. configure the CD drive to automatically be powered down post boot and after periods of inactivity, map the front media eject button to turn it on again on one click and eject on a second.This should be fairly straight forward, but if someone could save me the trial and error it would be much appreciated.  This may not actually have any benefit anyone know?

Anyone tried Xubuntu and Ubuntu and noticed any difference in battery life? or a significant performance gain?



Thanks.

---

### Post by nagaxen on 2008-06-10
I just setup 8.04 on my new TZ2000 about a week ago and can't seem to get Bluetooth working properly.  When I switch wireless to 'on' the Bluetooth icon shows up in the upper panel and I can run hcitool, etc.  The problem, however, is in the fact that the TZ can't find any bt devices; nor can any bt devices find it.  If I disable the wireless by sliding the switch to 'off' (Bluetooth icon on the panel goes away) and then plug in my Belkin USB Bluetooth module (model f8t001 v2) (Bluetooth icon comes back), I can scan and find all devices just fine.  I've also tried scanning from my 8.04 workstation with the same Belkin USB BT module and can find the cell phone but not the laptop (even though it is set to discoverable).

I'm at a bit of a loss here.  I know the TZ has Bluetooth 2.0 but that's supposedly backward compatible with 1.1 (my cell phone and Belkin BT module are both 1.2 iirc) so I don't think the difference in versions could be causing the issue though I could be wrong.  Wifi works without any problems.  Does anyone have any ideas as to what could be causing this issue?  Thanks for any help!

Bluetooth USB Module: Belkin F8T001 ver. 2
Cellphone: Nokia E60

dmesg output for all lines matching bluetooth:
[   46.064174] Bluetooth: Core ver 2.11
[   46.064574] Bluetooth: HCI device and connection manager initialized
[   46.064580] Bluetooth: HCI socket layer initialized
[   46.102341] Bluetooth: L2CAP ver 2.9
[   46.102349] Bluetooth: L2CAP socket layer initialized
[   46.218108] Bluetooth: RFCOMM socket layer initialized
[   46.218132] Bluetooth: RFCOMM TTY layer initialized
[   46.218135] Bluetooth: RFCOMM ver 1.8
[136356.872209] Bluetooth: HCI USB driver ver 2.9

---

### Post by KEYofR on 2008-06-13
> **maxtoor said:**
> ooops

[http://140.164.23.2/~mysony/](http://140.164.23.2/~mysony/)


Wow thank you so much. I've been living without that since day one (almost a year now).
I never got it to work even when I first got my tz and still had vista, and of course after wiping and repartitioning with 4 new partitions and 4 different OS's all bets were off.

I just unpacked this, took a wild guess that this should be written to  the root of a ntfs partition, I happen to have XP installed on partition #2, and sure enough it worked first time.

In case anyone else uses this, don't worry that the language is not english. It's settable from within the app.
Press the avmode hardware button to get to the main icon screen.
Press Enter on the music icon.
When the music app comes up, press the menu key on the keyboard.
Down-arrow to the bottom choice, Enter.
Right-arrow while sitting on the top choice.
Select language.

I did it the hard way at first by loopback mounting the reg file (it's a small ext2 filesystem) and editing a couple of small text files that are the equivalent of windows registry entries. But I couldn't read the word "settings" in the app to even know there were menus that could be pulled up like that!

I don't know if it matters, but, the original vista was on primary partition 2, and that's where my current xp is now, though all partitions are different sizes and have been overwritten since original. The InstantON dir and ntfs filesystem might need to be in the 2nd partition.

Shortly after finding this post I also found another article elsewhere on the net that describes in some detail how to get the app from your original  installation or from a temporarily restored original install from a recovery disk, but this saved a ton of time and grief since my original stuff is all in inconvenient forms like drive snapshot .sna images and dd images and a useless recovery disk made on a single dual-layer dvd which the machine can read but not boot from.

It might be interesting to loopback mount the initrd (/InstantON/ivi-id) and poke around for alsa, screen, ricoh card reader settings since, InstantON is linux, and all that stuff works perfectly in there, and people still don't always have things working well in regular linux. I don't think I ever even heard of the card reader working at all yet, so that should be worth digging up if nothing else.

Anyways, thanks a bunch.

---

### Post by jloxen on 2008-06-25
> **relmes said:**
> [QUOTE=_teo_;4528594]
Now on getting you connected. There are four basic steps:

1) you need root user (just sudo will not do it)
  ```

  sudo -s
  <enter your password>
  
```
2) power on the modem
  ```
echo 1 > /sys/devices/platform/sony-laptop/wwanpower
```


Thank you very much! This made my modem run on a TZ31.

BTW: 
sudo echo 1 > /sys/devices/platform/sony-laptop/wwanpower
does not work but instead of going root you may try
sudo "echo 1 > /sys/devices/platform/sony-laptop/wwanpower"
:-)
regards - Johannes

---

### Post by ilcontegis on 2008-07-18
how about the temperature? if I read well the tz model is fanless..the temperature is ok? or the laptop is always 100°?

Thank you
:guitar:

---

