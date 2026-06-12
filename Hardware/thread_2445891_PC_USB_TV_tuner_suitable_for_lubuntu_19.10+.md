---
title: "PC USB TV tuner suitable for lubuntu 19.10+"
date: 2020-06-21
forum: Hardware
---

### Post by nginmu on 2020-06-21
I would like to find a TV tuner gizmo that has an over-the-air digital terrestrial TV coax antenna socket on one side, and a USB2 / USBA plug on the other, that'll let me watch UK freeview DTV on my lubuntu machine.

I have lubuntu 19.10 at the moment but am expecting a new HDD tomorrow, I'll quite likely upgrade to 20 when I install afresh.

I'm worried that most of the low cost USB tuners available on ebay / in pound shops etc will expect one to install a companion program only supported in Windows

I wondered if any UK-based forum members knew of such an item of hardware that definitely works fine with lubuntu, whether by coming supplied with a suitable linux app, or being happy to integrate with an existing program already in the repos? Or even maybe something that is primarily sold with Windows in mind, but works happily in linux all the same with fairly simple tweaks.

Thanks for any suggestions.

---

### Post by tea for one on 2020-06-21
This one works with Ubuntu 20.04 so I suspect that it will be OK with Lubuntu.

[https://idaffodil.co.uk/collections/usb-digitial-tv-tuners/products/august-usb-freeview-hd-tv-tuner-dvb-t210-watch-digital-television-in-full-hd-on-laptop-and-desktop-computers-external-televison-card-for-windows-10-8-7-vista-xp](https://idaffodil.co.uk/collections/usb-digitial-tv-tuners/products/august-usb-freeview-hd-tv-tuner-dvb-t210-watch-digital-television-in-full-hd-on-laptop-and-desktop-computers-external-televison-card-for-windows-10-8-7-vista-xp)

You have to download and install the correct firmware into /lib/firmware. I'm pretty sure it is these:-

dvb-demod-si2168-b40-01.fw
dvb-tuner-si2158-a20-01.fw

I use tvheadend to watch and record UK Freeview DVB TV.

[https://tvheadend.org/](https://tvheadend.org/)

Once you have scanned the TV channels, you can export a channel list and use VLC to watch and record TV.

Also, have a look at this website for more info about TV tuners.

[https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices](https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices)

---

### Post by nginmu on 2020-06-22
Thanks for the suggestion. I've ordered one :-)

Also thanks for the additional info.

A reviewer mentioned it should also work with nextpvr.

Look forward to playing with it

---

### Post by tea for one on 2020-06-22
Well, you made up your mind quickly and I hope that you find it a useful device.

Thank you for mentioning **nextpvr**, I'm unfamiliar with this app and I'll have a look at it in the next few days.

---

### Post by nginmu on 2020-06-24
Do I need to add a repository (bintray?) to get tvheadend? Have now upgraded to lubuntu 20.04

[edit] I think I'm in the right place here; [https://tvheadend.org/projects/tvheadend/wiki/AptRepositories](https://tvheadend.org/projects/tvheadend/wiki/AptRepositories) - ?

---

### Post by tea for one on 2020-06-24
Yes, you need to add a repository. Just to complicate things, there are various choices.

I've been using this one for 18 months or so because, sometime ago, the doozer repo was not available.

[https://launchpad.net/~mamarley/+archive/ubuntu/tvheadend-git-stable](https://launchpad.net/~mamarley/+archive/ubuntu/tvheadend-git-stable)

Of course, the doozer repo is now available and the instructions are on the page you linked.

```
sudo apt-get -y install coreutils wget apt-transport-https lsb-release ca-certificates
```

```
sudo wget -qO- [https://doozer.io/keys/tvheadend/tvheadend/pgp](https://doozer.io/keys/tvheadend/tvheadend/pgp) | sudo apt-key add -
```

```
sudo apt update
```

```
sudo apt install tvheadend
```

Have you located the firmware and popped it into /lib/firmware?

Lastly, if you prefer, there is also a snap package [https://snapcraft.io/install/tvheadend/ubuntu](https://snapcraft.io/install/tvheadend/ubuntu)

---

### Post by nginmu on 2020-06-24
I seem to have gotten tvheadend 'partially' installed, and I'm trying to talk to it via kodi right now, but nothing's working and I'm snowed under with errors.

Steepest part of the learning curve, I'll persevere & hopefully get there!

Good thing is right now, I've got everything setup so that a complete reinstall is no problem (all my important stuff's on external storage) so I can play to my heart's content without worrying about breaking the system.

---

### Post by tea for one on 2020-06-24
*_Partially installed_* sounds like a problem waiting to happen.

You do not need Kodi to use tvheadend.

Tvheadend can be treated as a stand alone application.

if you are using Kodi, then you probably need to add tvheadend as an **addon** rather than a separate application.

I've never used Kodi within Ubuntu so I'm not sure what the exact procedure is to watch TV.

For example, there is a Linux distro, purely for media, where the main application is Kodi and the tvheadend part is an **addon**.

[https://libreelec.tv/](https://libreelec.tv/)

---

### Post by nginmu on 2020-06-24
I've gone wrong somewhere adding the repo and installing tvheadend I think. As soon as I'd done that via the command line I looked in muon and it did show up, but then I happened to try updating & it errored out "couldn't download packages" as soon as it started hitting the tvheadend stuff.

I'm going to wipe the system & do a full reinstall of 20.04 before going any further, gives me a clear head to step on forwards ;-)

---

### Post by CelticWarrior on 2020-06-24
No need for a full reinstallation. Just remove the PPA you added because it likely has no contents for your release, something that should be checked before adding any PPA.

---

### Post by tea for one on 2020-06-24
Yes, sometimes it's less arduous to reinstall and start from scratch. It's good practice and helps build confidence.

If you are looking for a media application which also includes TV viewing (in order to avoid tvheadend, other repositories, Kodi & addons), then have a look at **Kaffeine**.

It may pull in a myriad of dependencies but the TV part is reasonably simple to configure - assuming your DVB device is recognised.

---

### Post by nginmu on 2020-06-24
hey - cookin' on gas now, as they say.. Kaffeine didn't work at first but somewhere in it, I clicked on something and it offered to 'show dmesg', so I clicked on that, and read through a massive load of lines, and noticed there were a few lines complaining it couldn't find some firmware files...

It was saying it wanted dvb-demod-si2168-d60-01.fw and dvb-tuner-si2141-a10-01.fw so I found them online & stuck them in /lib/firmware, everything seems to have sprung to life now

I have purchased a slightly newer version of the stick than you maybe?

---

### Post by tea for one on 2020-06-24
I've had my device for approx 3 years so I'm sure your tuner is a newer model with different firmware.

Anyway, it looks like you've made good progress and now you can afford to experiment a bit.

It can be fun exploring other dvb scanning tools and pvr applications.

Please mark the thread as solved because it is helpful to other forum members.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by TheFu on 2020-06-25
**me-tv** is a simple TV watching program without all the overhead that tvheadend demands. i've used it only with a USB tuner in the US, but think it was created in Australia.  

i barely use that since hdhr network tuners with DLNA allow much more flexibility for watching and recording using any devices on the network.  Of course, they cost more than a single-tuner USB dongle.  Don't know whether HDHR works in the UK. They are great when we need better antenna than a mono-pole 16 inch antenna and need it mounted in the attic or outside.  [https://www.amazon.co.uk/Silicondust-HDHomeRun-CONNECT-Network-software/dp/B07BFPWBNS](https://www.amazon.co.uk/Silicondust-HDHomeRun-CONNECT-Network-software/dp/B07BFPWBNS) i have the US version of that. Wow, it looks to be 3x more expensive in the UK.  Recording TV shows is just a wget download.

---

### Post by tea for one on 2020-06-26
I also used **me-tv** in the past.

It **was** a nice simple application for viewing/recording but it hasn't been in the Ubuntu repositories for a long time.

Tvheadend is not the most intuitive program to use but it scans DVB-T and DVB-T2 channels without errors.

Also, tvheadend has a nice feature to allow you to export a channel list for use in VLC.

It's a pity that me-tv is no longer in development because that would have been my first suggestion for the OP.

There is a fork of me-tv [https://github.com/Me-TV/Me-TV](https://github.com/Me-TV/Me-TV), but I've not had much luck with it yet.

---

### Post by TheFu on 2020-06-26
> **tea for one said:**
>  It **was** a nice simple application for viewing/recording but it hasn't been in the Ubuntu repositories for a long time.

I suppose "long time" is relative. ;)

```
$ apt search me-tv
Sorting... Done
Full Text Search... Done
me-tv/xenial 1.3.7-1build2 amd64
  Me TV, it's TV for me computer

w-scan/xenial 20141122-1 amd64
  Channel scanning tool for DVB and ATSC channels

```

On a 20.04 system, it doesn't look as good:
```
$ apt search me-tv
Sorting... Done
Full Text Search... Done
w-scan/focal 20170107-2 amd64
  Channel scanning tool for DVB and ATSC channels
```

I'm not exactly worried about security for a TV-tuner software package that runs as a normal userid. OTOH, it doesn't work with HDHR network tuners, so me-tv seldom gets used.

---

### Post by nginmu on 2020-06-26
Kaffeine & the daffodil stick are working faultlessly here now, I'm really pleased with the setup.

Can't schedule to record 2 programmes on different channels simultaneously but I figure that's simply a limitation of the hardware. Could Kaffeine handle that scenario with the use of multiple daffodil sticks?

---

### Post by TheFu on 2020-06-26
Typical USB tuners only have 1 tuner.  That means 1 channel can be recorded though in the US on ATSC that 1 channel has 20 Mbps bandwidth and often has 4 sub-channels so all the programs on those subchannels CAN be recorded too using only 1 "tuner" if the software is smart enough.  Don't know what the UK does.   

if you want 2 or 4 tuners, the HDHR link provided above will lead to models with that capability.  These things are extremely well supported and there are probably 50-100 software methods to watch and/or record with them.  Get any of the models with DLNA support.  A raspberry-pi v2 or better can be used to watch and record on the low end.  Apps for Android and all the other OSes exist. Plex, kodi, tvheadend, mythtv, and all the commercial methods are supported too.  ZERO drivers needed, just a wired ethernet and connection to the antenna(s).  if you find one on-sale or used (DLNA capable models), buy if the price fits your budget.  They make 2, 4, and 6 tuner US models (QAM and ATSC). Think you want DVB models.

---

### Post by nginmu on 2020-06-29
Thanks for the info re HDHR that's something I'm certainly going to follow up. It does look like it should work in the UK according to what I've read so far.

Still using Kaffeine at the moment & it's working well, I just ran into one thing. I found a button marked "Update scan data over internet" so gave it a try to see what it did. I received a message "Failed".

Looking into it a little deeper it seems I'm suffering from the same issue reported here: [https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/1879923](https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/1879923)

Not experienced or knowledgeable enough to go any further with it though.. is it something that one would just have to wait for devs to fix?

---

### Post by tea for one on 2020-06-29
Scan Data is a list of TV transmitters.

Here is the latest table for Kaffeine [https://linuxtv.org/downloads/dtv-scan-tables/kaffeine/](https://linuxtv.org/downloads/dtv-scan-tables/kaffeine/)

You can compare the date issued of the scantable.dvb if you navigate:-

Kaffeine > Digital TV > Television >Configure Television > Edit Scanfile

Do you think that you are missing some channels?

---

### Post by nginmu on 2020-06-29
Kaffeine > Digital TV > Television >Configure Television > Edit Scanfile shows me a text file named 'scanfile.dvb' as follows:

```

# this file is automatically generated from https://linuxtv.org/downloads/dtv-scan-tables
[date]
2019-03-14
.
.
.    + many data lines . . .
.

```

The date, 2019-03-14, does seem older than the latest version online that is labelled 2019-09-29.

I would unfortunately, not have a clue if I were missing any channels - It's only very recently (since I've switched fully over from Windows to Linux, and since I've been less busy day to day with non TV life) that I've been bothered at all about watching TV, so unlike many regular watchers I'm not really too aware of what should and shouldn't be present these days. Last time I regularly watched TV avidly, there were only 5 channels. I certainly am able to tune in a huge number of channels though, 135 all told including radio services.

Looking inside the files I can see what I think is the section relevant to me - it's labelled with the name of my local transmitter:

```

my own 'scanfile.dvb':

[dvb-t/uk-WinterHill]
T 602000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 626000000 8MHz 3/4 NONE QPSK 8k 1/32 NONE
T 698000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 706000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 770000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 778000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T2 554000000 8MHz 2/3 NONE QAM256 32k 1/128 NONE 0
T2 737833000 8MHz 2/3 NONE QAM256 32k 1/128 NONE 0
T2 746000000 8MHz 2/3 NONE QAM256 32k 1/128 NONE 0

```

```

latest 'scantable.dvb' from https://linuxtv.org/downloads/dtv-scan-tables/kaffeine/

[dvb-t/uk-WinterHill]
T 602000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 626000000 8MHz 3/4 NONE QPSK 8k 1/32 NONE
T 698000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 706000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 770000000 8MHz 3/4 NONE QAM64 8k 1/32 NONE
T 778000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T2 554000000 8MHz 2/3 NONE QAM256 32k 1/128 NONE 0
T2 737833000 8MHz 2/3 NONE QAM256 32k 1/128 NONE 0
T2 746000000 8MHz 2/3 NONE QAM256 32k 1/128 NONE 0

```

If I'm right these are identical, so I guess I'm probably not actually missing anything?

The updater button in Kaffeine just isn't working at the moment because of the filename difference, I guess..

---

### Post by tea for one on 2020-06-29
Yes, it seems that you already have the latest scanfile table

I double checked my scanfile table [dvb-t/uk-Hannington] and I also have the latest info.

Anyway, I'm not too bothered about additional TV channels, I would prefer better content from existing services.

One other piece of info (if you are concerned) is that not all DVB scanning tools produce identical results.

Scanning via Kaffeine produced 133 channels (TV & Radio)

Scanning via Tvheadend produced 173 channels (TV & Radio)

However, I've never tried to view all the channels so, it's certainly possible that some may be inaccessible.

Best wishes

---

