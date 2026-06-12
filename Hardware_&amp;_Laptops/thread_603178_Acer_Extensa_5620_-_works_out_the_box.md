---
title: "Acer Extensa 5620 - works out the box"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by reality1011 on 2007-11-04
I have been a member here for quite some time but I have not posted much.  I thought I would give back by mentioning my most recent purchase and install of Ubuntu on my newly purchased laptop.

This is going to be the most useful to someone looking for a good laptop at a good price.
I picked this up from bestbuy for $599.  

I was a little weary about getting an Acer Laptop but the specs lined up and they make a pretty good LCD...  

This laptop has the Intel 3945 series wireless card... 
Intel duo 2 processor
200gb hard-drive
1gb ddr2 667hz (upgradeable to 4gb)
Giga-bit Ethernet
G wireless

All in all this was a great purchase... The laptop worked right out the box, wireless an all.

---

### Post by CandyLadyNJ on 2007-11-05
I also got the Acer Extensa 5620 this past sunday for $599 and it's effin awesome! Gorgeous LCD screen and the laptop is just beautifully made. Fast Dual Core 2. I upped the memory from 1 gig to over 2 gigs with my Sandisk 1 gig flash drive that was ReadyBoost enabled. I didn't have the extra cash to spend on a 1 gig memory card so I just paid $19.99 for the flashdrive so I would have  over 1 gig of virtual  memory. Awesome! It even has a built in webcam that is pretty good. Love the massive 200 gig hard drive but I plan to get dvds so I can burn a restore disk since the laptop don't come with them. It's so fecking cool!

---

### Post by reality1011 on 2007-11-07
See I just completely wipped off vista... I dont even care to own a copy of it...

---

### Post by v01d on 2007-11-08
What about the hidden partition? Does the notebook function normally if you wipe the entire disk? (I don't want or need a recovery to vista, which I don't even want to touch) I imagine the BIOS has its own memory as it should... I wouldn't want this notebook to be like the old ones which stored the BIOS setup on that partition =S

---

### Post by reality1011 on 2007-11-08
I think this speaks for itself

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99e0b8e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23949   192370311   83  Linux
/dev/sda2           23950       24321     2988090    5  Extended
/dev/sda5           23950       24321     2988058+  82  Linux swap / Solaris
cappetta@cappetta-laptop:~$

---

### Post by v01d on 2007-11-09
Glad to read that. I think I'm not even going to boot Vista =]

---

### Post by Carl Hamlin on 2007-11-10
I'm currently trying to install 6.10 on my recently purchased Acer Extensa 5620 and the Live CD won't even boot - tells me it can't find the video hardware.

I tried adding vga=771 to the boot parameters, but still no go. Has this been resolved in 7.10?

---

### Post by Bartender on 2007-11-10
Thanks for posting with a timely success story.  I appreciate it when someone writes in to say "This laptop worked".

It's still on sale.  Been wanting to get a lappy for months.  I oughta just buy it and start having fun.

---

### Post by croxis on 2007-11-10
I just got the notebook too.  My only complaint is that the onboard microphone isn't being reconized.  It isn't even showing up in alamixer.  Does it work for any of you?

---

### Post by v01d on 2007-11-13
I haven't tried the mic but it shows up on kmix (maybe you need to add yourself to the audio group).
I'm having trouble getting the wireless card to work (at least, it seems it has its antenna turned off, because scanning returns immediately). I'm not using ubuntu (I use archlinux), but your experience with configuring this card on ubuntu is just as good.
Also, the soundcard has that common issue regarding the headphone (you plug the headphone in but the speakers are still on). The volume on the headphones is a little low, but maybe this card lacks a decent amplifier. 

Thanks

---

### Post by Carl Hamlin on 2007-11-13
Got it to work with 7.10 - no problems with the install.

Compiz doesn't run at all - video hardware just isn't snazzy enough.
Onboard microphone doesn't work either.

Also, the system locks up hard when there's heavy traffic over wireless. Reboot required. Symptom does not occur over wired network.

All in all, however, I have fewer problems running Ubuntu on this hardware than I did running it on my older desktop machine, and it's pretty quick. Thumbs up from me.

---

### Post by deresik on 2007-11-17
Hi, how did you manage to get sound from headphones? and how about geting wifi to work?

---

### Post by Carl Hamlin on 2007-11-17
Deresik:

For me, it just worked. No configuration necessary - I just installed off of a freshly burned 7.10 CD and away I went. Wireless and everything.

What's happening when you try to connect using the wireless?

---

### Post by deresik on 2007-11-18
Hmm, perhaps my issue is becouse i have 5620z model, but as far as i know there are the same components (besides processor speed and memory amount).

Headphones started to work after i have installed "linux-backports-modules-generic" package. Mic doesn't work, but maybe this link [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) will help eventually when i'll have some free time.

About wifi, it seams that gutsy recognizes my card, it installed restricted drivers for Atheros HAL, but network manager simply don't see wireless card. To be honest i didn't spend too much time with it (for example drivers from cd + ndiswrapper) and simply hoped that you could give me a quick tip how to get it working:P

---

### Post by reality1011 on 2007-11-19
I also had the wireless work right out the box...  As far as mic, I don't use it.  I didnt have any problems with the video and I didnt have any probles with the system locking up because of heavy wireless...

---

### Post by pappfer on 2007-11-26
I have this notebook, too since last week. I only have a 160GB HDD in it. I'm running Gutsy on it and I'm really satisfied.
Even Compiz Fusion work almost perfect after installing XGL. The only problem with Compiz is that Shift Switcher icons disappear when reflection is enabled.

Wireless network works great for me.

My only real problem so far is about the sound. I can't get my 5.1 speakers work. Even I plug it in I only hear sound from the internal speakers. I also downloaded the Realtek drivers but still the same. I also installed "linux-backports-modules-generic" but again, the same. At the moment I'm out of ideas. Could someone give me an advice what to try, please?

Although I have this problem right now, I have to say that I'm really satisfied with both my notebook and with Ubuntu, too.
This forum is awsome! And Ubuntu's just the best OS I've tried so far. Thank you! ;)

---

### Post by v01d on 2007-11-27
Well, I'm not using Ubuntu but this may help:
To get the headphones work correctly (both the problem with headphones having really low volume and speakers not being muted when headphones are plugged) pass the model=acer parameter to snd-hda-intel (you can use the modprobe.conf or modprobe.d dir to add this option automatically next time the module is loaded).

---

### Post by ScottNC on 2007-11-27
After messing around I now have my internal mic/headphone jack/speakers working as they should, thanks to everyone in this thread so far.

To get audio working....

From  [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

installed** linux-backports-modules-generic **   <<Search for this in the Synaptic Package Manager (System > Administration > Synaptic Package Manager)

added options line below to first line of /etc/modprobe.d/alsa-base   <<use sudo gedit in terminal to edit
**options snd-hda-intel model=acer**


After this I restarted, don't know if this is needed but I"m a noob and am use to restarting between changes system changes. After restarting double click speaker icon to launch volume control. Make sure under File > Change Device > HDA Intel is selected. After that select "Edit" "Preferences" Then check every device listed.  When you close that you should now have Playback, Recording and Options listed in the Volume Control. In Options select "Front Mic". At this point I could record audio from the Sound Recorder with the built in mic but it was way too loud and distorted so play with the recording levels until it sounds good. 


For Video...

To get compiz working check out the 4th and 5th paragraph at [http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2](http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2)

Following his instructions I was able to get compiz working. But that broke video playback. After selecting "X Windows System (No Xv)" in video properties my videos played but looked really bad (real player 1998 bad) and Miro still would not work. I ended up disabling compiz after all. If anyone is able to get compiz working and have good video playback please update in this thread.

---

### Post by TheMouse on 2007-11-28
I also just picked up an Extensa 5620. I'm running from the Live CD right now, but I'm definitely installing Ubuntu later in the week (when I'm done with exams). I've had no issues so far which don't stem from my own unfamiliarity with the system.

---

### Post by pappfer on 2007-11-28
> **v01d said:**
> ...pass the model=acer parameter to snd-hda-intel ...
I've already did this, but it didn't help.

> **ScottNC said:**
> ...To get audio working...
I've did everything like you and all I got is that now my speakers working, but I'm still not able to get my 5.1 working. Only front left and front right are working none of the other speakers.
Is it possible to get 5.1 sound from this notebook? My friend have an older MSI notebook and he was able to get 5.1 sound from that with some Realtek software (under Windows XP). It has the same 3 connectors.

---

### Post by ScottNC on 2007-11-29
> **pappfer said:**
> I've did everything like you and all I got is that now my speakers working, but I'm still not able to get my 5.1 working. Only front left and front right are working none of the other speakers.
Is it possible to get 5.1 sound from this notebook? My friend have an older MSI notebook and he was able to get 5.1 sound from that with some Realtek software (under Windows XP). It has the same 3 connectors.

I don't know if it is possible to get 5.1 audio from this notebook, that is a good question. I found this thread [http://ubuntuforums.org/showthread.php?t=515003](http://ubuntuforums.org/showthread.php?t=515003) about getting surround sound from an HDA Intel card. However I don't know if the Acer's mic/line in ports can be reconfigured to output rear/center/sub. I just use the normal stereo laptop speakers and wanted to have the internal mic work for skype and the headphone jack work for traveling.

---

### Post by Sunaj on 2007-11-29
I have a couple questions.. :confused:

Can you boot from a thumbdrive to have a 'live cd' effect on the Acer 5620?

Since the Acer 5620 has a 64bit processor is it recommended that you install 64 bit Ubuntu? 

Can the Intel 3945 be put into monitor mode and/or do packet injection?

I'm bound to have more questions I'll post them when I think of them :)

---

### Post by reality1011 on 2007-12-01
I am sure you can boot from a thumbdrive to have a live cd effect... I did that with one of my thumbdrives but it was for Windows 98 not a linux flavor...

I would say install the 64 bit version but you can use the 32 bit as well... One of the differences is that you can use more Ram with the 64 bit then the 32 bit.  The 64 bit also processes 64 0/1's versus 32 0/1's.  Although the 64 bit application are still being developed and it is a newer technology.  



I dont know about monitor mode or packet injection...

---

### Post by pappfer on 2007-12-14
> **ScottNC said:**
> I don't know if it is possible to get 5.1 audio from this notebook, that is a good question. I found this thread [http://ubuntuforums.org/showthread.php?t=515003](http://ubuntuforums.org/showthread.php?t=515003) about getting surround sound from an HDA Intel card.
Thank you! It's a nice thread but things written there didn't work for me. [As I wrote there, too]("http://ubuntuforums.org/showpost.php?p=3934536&postcount=11") I just don't have Surround in the sound preferences at all. Do you have it there?

---

### Post by skizzay on 2007-12-14
You should be able to boot from a usb thumb drive by changing the order of boot devices in your BIOS.  I know I had to do this initially just to get the live CD to boot (luckily, I did this out of curiosity before Vista could get a chance to boot).

Has anyone had any luck getting the SD card reader to work?  I haven't had much time to test it, but I haven't had any success.  The only thing that hasn't worked out of the box for me so far.

---

### Post by pappfer on 2007-12-14
> **skizzay said:**
> Has anyone had any luck getting the SD card reader to work?  I haven't had much time to test it, but I haven't had any success.  The only thing that hasn't worked out of the box for me so far.
For me it worked out of the box. I used it with Memory Stick Duo.

---

### Post by ScottNC on 2007-12-14
> **Sunaj said:**
> Since the Acer 5620 has a 64bit processor is it recommended that you install 64 bit Ubuntu? 

I have installed both just messing around and decided to go with 32 bit version, mainly for battery life. Currently only the 32bit version supports a tickless idle out of the box, which means longer battery life. **[http://ubuntuforums.org/showpost.php?p=3715877&postcount=24](http://ubuntuforums.org/showpost.php?p=3715877&postcount=24)** 

> **skizzay said:**
> Has anyone had any luck getting the SD card reader to work? 

My SD card reader worked out of the box, I have used SD cards and Ubuntu auto mounts and places an icon on my desktop.

> **pappfer said:**
>  I just don't have Surround in the sound preferences at all. Do you have it there?

I do not have any surround settings in sound preferences :( If you do get it working can you post in this thread as well?

---

### Post by pappfer on 2007-12-15
> **ScottNC said:**
> I do not have any surround settings in sound preferences :( If you do get it working can you post in this thread as well?
Sure! But to be honest as time goes I see less and less chance to get sorrund sound working in this notebook. :(
But I won't give up! ;)

---

### Post by QrK0 on 2007-12-16
Hi mates, I just purchased the Aceer Extensa 5620z mainly due to the good price.
Trying to run Gutsy from the livecd, the hardware info shows me a Broadcom 802.11g wireless card at this time I'm unable to make it run. The wireless monitor doesn't show any wifi available network, so I enter the essid mannually, but it doesn't find any network to connect to.
The rest of hardware seems to work fine (display, sound...all seems right).

Does anyone have the same network card and made it run?

---

### Post by pappfer on 2007-12-25
When I turn on the notebook WIFI always turns on by itself. Is there something to do about it? Or I have to turn it off manually each time I turn on my notebook?

---

### Post by landonray83 on 2007-12-26
This seemed to work for me in getting the headphone jack to work and disable the external speakers when something is plugged in...
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")
> Method E: Patch to add support for Realtek ALC268 Codec to Alsa 1.0.14

    *

      Does work: [WWW] Acer TravelMate 6292, Compal IFL90, MSI PR200
    *

      Does not work:

Support provided :

    *

      Internal speaker works
    *

      Headphones works (and internal speakers are automuted correctly)
    *

      External speaker works (and internal speakers are automuted correctly)
    *

      Internal mic doesn't seem to work...
    *

      External mic untested.

Procedure (See [WWW] #116326) :

    *

      Rebuild the linux-ubuntu-modules-2.6.22 packages after applying this [WWW] patch
      Or use this already pacthed,ready to install, [WWW] linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb.
      Note: It only works with an up-to-date Gutsy.
    *

      Add the following line in /etc/modprobe.d/alsa-base:

      options snd-hda-intel model=acer

      Note: You can specify one of the following model : acer, toshiba, 3stack or auto Note 2: For MSI PR200, use model=targa-dig
    *

      Reboot


---

### Post by eranical on 2008-01-07
I am an absolute noob.... So please excuse if my question is silly..
I bought an acer extensa 5620 with no OS installed. I downloaded & made a live cd for 7.10 & had no problem to install it on the laptop. Now my difficulty is I can't seem to use my wifi. The network option is not to be seen itself. I can only use wired network. Am I making sense? 
Oh by the way my card reader is working at least with SD cards...
Thanks in advance

---

### Post by ScottNC on 2008-01-08
> **eranical said:**
>  Now my difficulty is I can't seem to use my wifi. The network option is not to be seen itself.

Go to Applications - Accessories - Terminal

Type **ifconfig** and press enter

You should get a few paragraphs of text back with a title to the left of each clump of data. The first will most likely be "eth0" with 7/8 lines of text to the right. Do any of those headers say "wlan0"? If not can you post the results here? When you say you bought it with no OS, did you buy used from someone?

---

### Post by eranical on 2008-01-19
> **ScottNC said:**
> Go to Applications - Accessories - Terminal

Type **ifconfig** and press enter

You should get a few paragraphs of text back with a title to the left of each clump of data. The first will most likely be "eth0" with 7/8 lines of text to the right. Do any of those headers say "wlan0"? If not can you post the results here? When you say you bought it with no OS, did you buy used from someone?

Thanks & I am sorry didn't reply earlier. I was out of town for a week. I in the meantime managed to install Vista on the laptop & then installed Ubuntu again so that I can dual boot. I doubt I will do much of it since the blue screens on windows are making me loose whatever hair I have left. :confused:

However once I got the wireless installed on Vista it was really pretty easy getting the card going on Ubuntu.

The only item of slight concern now seems to be a driver for the Intel PRO/Wireless 3945 Network connection is a proprietary driver. Should I be concerned about this? Sorry if it's a dumb question.....

---

### Post by Empecinado on 2008-01-22
Hi, i got the 5620z at work and i am struggling to get wifi up for home use. Can you specify what you did to get it working? Sure as hell i ain't going to install vista :p

This is the result of my ifconfig 


```
pnavascues@empecinado:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1D:72:04:70:03  
          inet addr:10.10.19.32  Bcast:10.10.19.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe04:7003/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:361782 (353.3 KB)  TX bytes:34725 (33.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

ty to everyone.

---

### Post by eranical on 2008-01-24
I am really not sure how or why my wifi started working. As I mentioned the only thing I know is I did is I installed Vista. I have to have Windows for some work related requirements.
I also just realized my sound stops working once it recovers from sleep or hibernation. The noob that I am I can´t understand the earlier posts about how to solve the issue.
when you say search for the synaptic program... what do you mean? Do I have to use some command in terminal....

---

### Post by ScottNC on 2008-01-24
> **eranical said:**
> when you say search for the synaptic program... what do you mean?  

Yeah, it should say search for in the synaptic package manager.

Goto **System** > **Administration** > **Synaptic Package Manager**

---

### Post by opaofu on 2008-01-24
my keyboard is different than the one in my manual. mine has some blue numbers and symbols on the keys just like the manual but it also has green. mine also has "AltCar " on one of the alt keys. the green on the keys are symbols like this É,»,",/,?,`,>,^,',¨. thats when I press the shift key, now the most important is are the ? which is on the six key . when I push the ? key it is this é. and my apostrophe to the right of my right pinky. and also the "at" symbol which is on the 2 key is quotation marks.

this problem might be easier
how do I or what do I need to get the web cam to work in ubuntu?

---

### Post by opaofu on 2008-01-24
sorry

---

### Post by eranical on 2008-01-25
> **ScottNC said:**
> Yeah, it should say search for in the synaptic package manager.

Goto **System** > **Administration** > **Synaptic Package Manager**

Thank you.. I feel like a real noob once I saw how easy that was!:lolflag:

---

### Post by zombiepig on 2008-01-27
I'm also the happy owner of an Extensa 5620 - seems to be a great little laptop and very linux friendly. :)

A word of warning - the 5620z ships with a Broadcom wireless card, rather than the Intel card that's included in the 5620. So while the wireless works out of the box with the 5620, you'll have to go through a few hoops to get it working with the 5620z.

---

### Post by breaking on 2008-02-03
Would just like to chime in here... also have Extensa 5620-6830, and for the most part, it works great!  I did have to add the "model=acer" parameter to modprobe.conf to get the mic, etc, to work, but it's been pretty much smooth sailing.  Please note that with many models, you will be using the proprietary driver for the IntelPRO wireless card, but it's been working fine for me (actually get better wireless reception in (k)Ubuntu than when using my Windows install on a separate partition!

Another thing I didn't see mentioned are the function keys (the keys with the blue symbols) - they work out of the box, too!  Which is great, because on my previous lappy, a Vaio, I never could get them working right, and when there is no volume dial on the computer (which is the case with both the Vaio and this Acer, having to use the GUI is cumbersome).  So that's another bonus.

Two issues I've had, though, are this:

1. Webcam - I got it working with many programs (including Cheese and Kopete - (like I said, I'm running Kubuntu), but it does *not* work with other programs - ekiga, and no joy with Stickam.com (although it does work in Windows).  I have used the Linux-UVC driver ([http://ubuntuforums.org/showthread.php?t=593231](http://ubuntuforums.org/showthread.php?t=593231)) to get most functions working, though.  If anyone has had total compatibility with their webcam, please let me know.  It's the Suyin, not the Buffalo.  

2. Sound - Sound *does* work.  Don't get me wrong.  However, I have found it only is loud enough when PCM is up all the way.  As most of you know, turning up PCM more than like 75% will cause distortion.  So either I have acceptable volume with bad quality, or very low volume at good quality.  I'm sure this is due to the HD Intel drivers, but it's kind of annoying.  However, the headphones put out sound quite loudly!  So if anyone has any answers with this, please let me know (I hate having to boot into Windows to listen to my tunes).

Other than those two, no complaints, and everything's been swell.  See, this is why I use Ubuntu as opposed to other Linux distros- the hardware support is comparable across the major distros, but we have *by far* the best community out there!  Keep it up guys.:guitar:

---

### Post by reality1011 on 2008-02-03
I have also noticed the external speakers are very weak.... I was wondering if this was normal or if there was something that needed tweeking.... I can't compare the speaker output with vista because I deleted it before I used the laptop.

If you are dual booting are the volumes the same ?

---

### Post by breaking on 2008-02-05
reality1011:

The weird thing about the volume in Ubuntu is that if the volume slider is at about halfway or below, there is really no sound at all, and only at the top quarter of the slider does it really make a noticeable difference (I'm using Kmix in Kubuntu, but I'm sure there's an Ubuntu equivalent).

On the other hand, the speakers sound good in Windows (I "upgraded" to XP - but getting the SATA drive recognized was a nightmare).  Volume is louder, clearer, and the volume gets louder or quieter in an intuitive fashion in relation to the volume slider.  I'm thinking it is just due to the drivers, but if anyone has found a way to get good, clear louder sound out of their 5620, I'd be interested in the methodology.

---

### Post by eranical on 2008-02-07
> **ScottNC said:**
> Go to Applications - Accessories - Terminal

Type **ifconfig** and press enter

..... When you say you bought it with no OS, did you buy used from someone?

@Scott I am sorry I missed that part of the post earlier.. I bought it from this auction site for Bestbuy employees. I never was an employee but someone once gave me an invite. They keep coming with this laptop configuration on the site & I bought 2 of them for approximately $400/- The only thing is that it comes with a blank hard disk, In our case I guess that is ok since even if it had Vista I intended to wipe it clean before installing Ubuntu.
Though eventually I ended up installing Vista for some work related stuff....

@ breaking & reality1011:
Oh so I am not alone in the boat:) I also find the speakers pretty low....

---

### Post by breaking on 2008-02-17
UPDATE:

I have got a little better performance, both out of the sound system, and getting the webcam to work with other programs (still not 100% compatibility, but oh well)...

**Sound:** I temporarily installed Ubuntu Studio, just to see what the fuss was, and I definitely noticed better sound out of the box.  Upon examining the difference in configs, it seems the difference was with gstreamer plugins.  So when I re-installed Kubuntu Gutsy, I went into Adept (Synaptic, same thing) and downloaded all available gstreamer plugins, (the good, the bad, the ugly - really!).  I may be imagining, but it seems that the sound is definitely better now, although it still sounds better when I boot into Windows... :/

**Webcam:**
Upon adding all those gstreamer plugins, I found that I got better compatibility with the webcam as well!  Cheese now works *beautifully* with the cam.  In addition to the linux-uvc drivers that I listed above, I made sure to get _both_ the V4L and V4L2 drivers, which are both in the repositories.  I could never get Ekiga to work with the webcam, but once I installed V4L2, and picked that driver in Ekiga settings, it worked fine!

So, while not entirely perfect, I am happy with the usability of this great lappy using a great OS.

Thanks everyone for their help, and if anyone has questions regarding any of the above, I'll be happy to elaborate in detail if necessary.

---

### Post by Amateur on 2008-02-23
Hi,
I also have seen the extensa 5620 and want buy it.

Can somebody tell me about the fan and temperature?
How often the the fan is runnig? Is it noisy?

Speedsteep and powersave are working? (my 5620 com's with a T5450 CPU)

Is suspend ram/ disk working and waking up?

I hope anybody understand my.
I'm sorry my englich is not verry well!

Michel

---

### Post by janinab on 2008-02-27
dude,i m new here. i wanna know , if i buy ACER EXTENSA 5620 from UK, then how will it cost? 
actually i wanna know the price of thiz laptop in UK? can u plz gimme that information???
thanks

---

### Post by Amateur on 2008-03-01
So decided for a Acer Extensa 5620-3A2G16 (with T5450-cpu and intel-graphic)
There are a littele speedstep (only 3 steps:1--1.3--1.6GHz)
And the fan works also only in one or two steeps - it could be better.
But it's OK. I think I can do my daily work softly.
The fan don't running for little tasks. On bigger jobs the fan is runnging pwerfull.

Hallo janinab,
I've got my laptop for 649&#8364; in germany.

Have anybody informations about suspend?
It was verry helpfully.

Michel

---

### Post by mrphoenix on 2008-03-01
Hi everyone,

I would like to know what version of Ubuntu(7.04 vs 7.10 and x86 vs x64 etc.) you use on 5620 Extensa!

What is the most recommended, powerful, compatible?

I was try 7.04 x64 but at first I got Busybox when install... I try at install boot menu after pressing F6 and write after "--" all_generic_ide" and it worked and didn't stopped with Busybox. But after loading, I got Failed to load X-Server message on a blue screen. I got the same at Safe graphics mode too.

Please help me!

Thanks.

mrphoenix

---

### Post by J$oney on 2008-03-02
I have the acer 5620, i'm running 7.10 X64.
Upgraded ram to 2 gig
For some reason when i wiped the drive i only see 177 gig, Yes, i did delete all the hidden partitions, i used f disk which i weird. The other thing is when i walk away and come back say after getting a drink, when i move the mouse the screen brightness jumps, not finding any drivers anywhere, so it's running generic. Overall this is a good machine, i just wish so many things on it where proprietary.

---

### Post by mrphoenix on 2008-03-03
Thanks for the reply. Don't you have problem with wireless(wi-fi) connecting with 7.10 x64?

Because I had it, unfortunately. On the panel the icon for the wireless connection were disappear very often(or almost always) when I tried to connect different networks.

Now I use the newest Ubuntu Ultimate 1.7 x86 without the same problems.

---

### Post by J$oney on 2008-03-08
never had a problem, try running ndrs wrapper though

---

### Post by jgerd on 2008-03-10
Hello All,

My Acer Extensa 5620-6830 runs Ubuntu 7.10 very well, but sometimes when I will boot up it freeze. I just can see a black display, so I turn off my laptop and remove the battery, then the laptop boot up very well. I have dual boot with Vista, but I just use Ubuntu. I have noted that this occurs when I use my wireless.

thanks

---

### Post by breaking on 2008-03-11
To those having problems running Ubuntu 64-bit: I hate to say it, but the 64-bit versions of Ubuntu are still quite buggy, and many common apps/plugins (like Flash) don't work ideally yet.  Even if your computer has 64-bit capabilities, I would suggest using the 32-bit versions available, at least for now.  That, in my estimation, would solve 90% of your problems.  It's not specific to this model, the problems are specific to 64-bit computing on Linux.  Make some backups, and try it.  Anyone who decides to do so, please post your findings here. 

Thanks!

---

### Post by jgerd on 2008-03-12
I'm using the 32bit ubuntu, I will upgrade my BIOS to see if this bugg is solved.
thanks

---

### Post by pappfer on 2008-03-15
> **jgerd said:**
> Hello All,

My Acer Extensa 5620-6830 runs Ubuntu 7.10 very well, but sometimes when I will boot up it freeze. I just can see a black display, so I turn off my laptop and remove the battery, then the laptop boot up very well. I have dual boot with Vista, but I just use Ubuntu. I have noted that this occurs when I use my wireless.

thanks
I have the same configuration (32 bit Ubuntu Gutsy + Vista) and I experienced the same problem a couple of times.
Since I've updated my BIOS the problem didn't show up.

About BIOS update:
- Is it only possible under Windows?
- I was hoping that it'll solve the annoying thing (at least for me) about WIFI turning on everytime I restart my notebook but it didn't.

---

### Post by breaking on 2008-03-16
> **pappfer said:**
> I have the same configuration (32 bit Ubuntu Gutsy + Vista) and I experienced the same problem a couple of times.
Since I've updated my BIOS the problem didn't show up.

About BIOS update:
- Is it only possible under Windows?
- I was hoping that it'll solve the annoying thing (at least for me) about WIFI turning on everytime I restart my notebook but it didn't.

BIOS updates are technically doable on Ubuntu (or any Linux distro), but if you have Vista, by all means, USE THE BIOS TOOLS THAT ACER PROVIDES!  It's a *lot* easier (just make sure you've booted into Windows), and if you ever need it serviced, Acer shouldn't have a problem with you using their tools (but don't quote me on that ;))  Plus, if you download the AHCI/SATA driver, you can install XP over the Vista partition.  If you have to use Windows (I do for some things), you may as well be using their best version, ya know?

[ftp://ftp.work.acer-euro.com/notebook/extensa_5620](ftp://ftp.work.acer-euro.com/notebook/extensa_5620)

---

### Post by Nano on 2008-04-01
Probably someone of you can help me on this.
I have a brand new Extensa 5620 which has an Intel GM965 graphic chipset. 
In theory the right driver should be the Intel i810 but it fails when I select it.

I'm currently using Hoary Beta, just intalled.

Did any of you have the same problem?
Thanks in advance

---

### Post by bugmenaut on 2008-04-05
you're running Hoary? do you mean Hardy?

---

### Post by Nano on 2008-04-07
haha, yes, sorry! It was just a lapsus, probably remembering good ol' times :)

It's Hardy and I still have the this problem unsolved

---

### Post by janinab on 2008-04-22
can u plz tell me the price of this Acer extensa 5620-6635 model?
does the price vary in EBAY OR BUY.COM. i neeed the information.. plz provide it..
Thanks.

---

### Post by Nano on 2008-04-22
I wish I can tell you. The company bought it for me in Spain, where prices usually are bigger than in UK or US for tech products.

---

### Post by Godneyeh on 2008-04-24
Hi mates,
I have a 5620Z machine and it works very well after a few hours of tinkering.
But one annoying problem still remains, namely the 5in1 card reader just won't work. And I found no stuff around about that. Has anyone solved this?
THX in advance.
Cheers.

---

### Post by Nano on 2008-04-25
Jeez, am I the only one who can't load the i810 drivers on the 5620? :(

---

### Post by pappfer on 2008-04-27
5.1 card reader doesn't work for me either on Hardy.
It worked very well in Gutsy.

---

### Post by Jeff Dean on 2008-04-29
> **CandyLadyNJ said:**
> I also got the Acer Extensa 5620 this past sunday for $599 and it's effin awesome! Gorgeous LCD screen and the laptop is just beautifully made. Fast Dual Core 2. I upped the memory from 1 gig to over 2 gigs with my Sandisk 1 gig flash drive that was ReadyBoost enabled. I didn't have the extra cash to spend on a 1 gig memory card so I just paid $19.99 for the flashdrive so I would have  over 1 gig of virtual  memory. Awesome! It even has a built in webcam that is pretty good. Love the massive 200 gig hard drive but I plan to get dvds so I can burn a restore disk since the laptop don't come with them. It's so fecking cool!

[COLOR="Blue"]I've just purchased 5620 and am trying to upgrade the memory but I'm having problems removing the back panel. I don't want force it but it won't come loose. I've loosen all the screws but it's stuck hard.
I noticed you upgraded so did you have problems removing the back panels and is there a method/secret to removal?
Thanks
Jeff Dean[/COLOR]

---

### Post by SneakyBooBoo on 2008-06-05
I think my 5620Z must be a later model then. I dont have an Intel wlan. I got a broadcom card but i cant get it to work in 7.10. I used my Alternative CD to upgrade to 8.04 thinking that will give me new drivers but still nothing. I enabled the restricted drivers and rebooted but when i go to network tools im still seeing my LAN and the loop, no WLAN.

when i do ifconfig in terminal i get this
```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:27:d1:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:72:27:d1:c0  
          inet addr:169.254.8.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101342 (98.9 KB)  TX bytes:101342 (98.9 KB)

```

and then when i do iwconfig i get this

```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

so it seems the card IS there and getting picked up BUT why cant i scan for wireless networks with the network manager?

---

### Post by SneakyBooBoo on 2008-06-05
actually nevermind. i just booted up a live version of gOS Space and the card is there and the wireless networks are shown. and seeing as its based on 7.10 already, ive formatted and installed that instead just to get me started with some sort of linux on there. im not enjoying windows.

---

### Post by reality1011 on 2008-06-16
> **Jeff Dean said:**
> [COLOR="Blue"]I've just purchased 5620 and am trying to upgrade the memory but I'm having problems removing the back panel. I don't want force it but it won't come loose. I've loosen all the screws but it's stuck hard.
I noticed you upgraded so did you have problems removing the back panels and is there a method/secret to removal?
Thanks
Jeff Dean[/COLOR]



You need to apply some pressure... it has some clip like things holding it in.  I actually bent mine a little get get it off.  then I did the same getting it back on.  The back panel is somewhat flexible.

---

### Post by cpriyantha on 2008-07-13
Hi Guys,

I have installed Solaris Express edition on my Extensa 5620. I wonder whether any of you have configured the sound card for this model using Solaris. It would be great if any of you can help me out.

Cheers!

Chanaka

---

### Post by zggame on 2008-07-16
Hi, I just got a 5620-4025 (Pentium Dual 2370 1.7G/1G RAM/120G).  It shows 5620Z on the right corner below the lcd. I have put in the Ubuntu 8.0.4.  And it works well msot of the part.  I am surprised the compiz works just fine although there is only 8M is set to the video in the BIOS.  I need to do a few tweak, such as to disable the synaptics touchpad during typing.  Here are things less ideal. 

1. It has a broadcom BCM94311MCG wireless, which works out of box with this proprietary driver but very slowly.  It only works in 1Mb/s mode most of the time even within a very close to the router.  The wireless works fine within Vista (dual-boot), so it is likely the problem with the software.  In iwlist scan, the noise level is very high, 50dBm, while other laptop shows 90dBm.  

2. Another problem is the "suspend".  The laptop seems not in a full off status, the light in the left of the battery light in the fornt blinks, as well as the power light.  When I open the lid, or push the power key, it will restart instead of go back.  

3.  Functioanl keys. Lots of them works.  But some are not and I cannot set.  There are seven keys on the left of the main keyboard.  Only the 5th(browser), and 6th(email) work, I can set others in the system->preference->shortcut key, it shows something like 0x97. But it does nothing when I push the button.

---

### Post by Mithryn on 2008-07-19
I have the same laptop, and have noticed that the hibernate and suspend states crash when I try to bring back up.  For the functional keys, the same 2 work, and all the others seem to not be recognized.  I haven't checked, but in the System > Preferences > Keyboard, I saw quite a few different choices for keyboard layouts, and I"m sure one of them works.  

As for the wireless, my Acer Extensa 5620z shows an Atheros 242x chip, which I have found to be the problematic Atheros 5007 chipset.  Thankfully, [this post]("http://ubuntuforums.org/showthread.php?t=816780&highlight=atheros+5007+madwifi")following the directions of this post has allowed me to get 54mbp/s on my wireless, with absolutely no trouble at all ( of course, if you have the Broadcom card, that won't help you at all) 
May wanna check out this post [here]("http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM94311MCG")

---

### Post by cetheriel on 2008-07-24
same here. 5th (browser), 6th (email client), 7th (custom, i set to Rhythmbox and it works). others do nothing, and keyboard shortcuts doesn't even recognize them. btw, what is the keyboard layout for it?

---

