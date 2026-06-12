---
title: "MSI GX720 laptop"
date: 2008-11-04
forum: Hardware
---

### Post by al3omdah on 2008-11-04
Hi guys ....

Honestly I'm going to purchase new laptop MSI GX720 but I'm little bit concerned about hardware support in ubuntu so any suggestion or recommendation ?

You can review its specifications [here]("http://global.msi.com.tw/index.php?func=prodtmpspec&maincat_no=135&cat2_no=&cat3_no=&prod_no=1521")

Your reply will be highly appreciated

Thanks :)

---

### Post by ounas on 2008-11-13
How did you get on , I am also thinking of purchasing this.
:)

---

### Post by al3omdah on 2008-11-18
I'm really concerned about drivers compatibly with Ubuntu

---

### Post by przemo28765 on 2008-11-24
I have the same problem with msi gt735. It's the same laptop, only it uses amd platform. Lan/Sound/GPU should be supported by kernel, there might be a problem with Wifi/Camera/Modem.

---

### Post by ounas on 2008-12-01
Thanks

:popcorn:

---

### Post by pYrO1v1aniac on 2009-02-07
I've just installed 8.10 on this laptop, and so far, the verdict is, it's a 9/10 Ubuntu machine.

The graphics ran at native resolution immediately, the wifi worked right out of the box, as does bluetooth and so far, everything's running brilliantly smoothly.

One point is lost because of its unusual 4 speakers and 1 subwoofer sound setup, that I haven't figured out how to properly utilise yet, but then, Vista is totally incapable of using that properly too, and I at least know with the right googling and asking around, I can get a solution.

Even the touch buttons for bluetooth and wifi work right off, and i haven't checked but I'm sure with a little playing around, the audio play buttons will too. It's a great laptop and i'm sure you'll be very happy with it.

---

### Post by YMS_1975 on 2009-04-02
Hey y'all,

I know it's a little late for this post, but I didn't see the need to start a new thread on an old subject.  ;)

I just purchased this unit, the MSI GX-720 & was wondering if anybody's who's used this laptop can shed some insight as to how this puppy works with Ubuntu. I appreciate that's the very nature of the previous posts, but seeing as how it's now April '09 I'm sure that's plenty of time for any hiccups to have presented itself to the user. Were there any hiccups by the way?

Also (and lastly) did you install the 64 bit version of Ubuntu or the 32 bit?

---

### Post by em3raldxiii on 2009-04-07
Hi YMS_1975.  I just purchased the GT735 which is in the same family of laptops.   I had to use the 8.04 disc to install because the 8.10 one was hanging on the battery discovery steps during livedisc boot.  Alternate install might work okay, but I have read a few other posts about it being a problem, so I just went with 8.04.

The other problem I am having (and this problem might go away with subsequent updates), is that I had some trouble configuring sound ... I had to enable an obscure checkbox in my volume control settings, and then I had to make sure it was checked.

Other than that, as far as I can tell, Bluetooth works out of the box, video resolution and stuff was enabled right out of the box (with correct resolution at 1680x1050), and I had to download the wireless network card driver (a native linux package that appears to perhaps be just a wrapper for the original drivers) from the network card's vendor website (ralink.com I believe it was).

Other than those fairly minor issues, everything else works wonderfully.  Runs super smooth, the track-mouse thingie works perfect (the right side is also a scroller, though it's not marked), and it even enters sleep mode without any troubles (that I have noticed yet).  Volume controls (function + F-keys) work fine, turbo (one-press overclocking) works, and the touch-button wireless + bluetooth thingies work great.

The subwoofer on the bottom provides good bass, however I am having some difficulty figuring out how to configure the sound so that it "sounds right".

Windows Vista Home Premium (came pre-installed) had no troubles with the sound, and actually works quite well, despite my hatred of Vista.  It works good for gaming and runs much smoother that pretty much anyone elses laptop that I have come across.

I know this thread wasn't intended to be a review of the product, but i figured since there are so few posts about this brand of laptop that I should at least contribute a bit.

So for the original poster:  If you don't mind spending a little bit of time to get the latest driver from the vendor for the wireless, and perhaps a bit of time configuring the sound (perhaps installing the latest ALSA driver), then I highly recommend this laptop.  I am using it as dual-boot with Vista/Ubuntu so i can do a little gaming now and again.  Unfortunately, this flavor of Vista installs on 3 primary partitions on the HD, so it's a bit of a waste.  Ubuntu is happy enough if you just shrink one of the partitions, and make the 4th a logical with your favorite partition arrangement as logicals.  And until 9.04 comes out, use Ubuntu 8.04.

Cheers!

---

### Post by trevelyon on 2009-05-02
Just got a GX720 (the barebones version w/ 4 buttons on the side of the keyboard and none on top) and loaded Jaunty on it yesterday.  Here are my results:

Video:
Works out of box using xorg-nvidia drivers.  I used aptitude to load the nvidia proprietary drivers and they work but give terrible performance.  Here is a rough comparison using glxgears:
with open drivers: 128
with compiz on: 3000
with compiz off: 4200
my old inspiron 9400 w/ geforce 7800 go and no compiz: 7500

So you can see the performance is no where near the 3x improvement I was expecting over the 7800 go in fact it is worse.  I should say that performance in NWN is much smoother than on the 9400 and all subjective tests show better so maybe glxgears is not a good guage. 

Audio:
Works out of the box but all sound is played over the subwoofer.  Need to play with configuration to get this working properly.

Wireless:
I have the intel 5300 chipset and it works out of the box.  You need to activate it by pressing the wireless button on the laptop to enable it.  The button also works out of the box.

Bluetooth:
Works out of the box.  On mine I had to press the wireless button 3 times to get both the wireless and bluetooth active (took a bit to figure this out).  Once done it just works.

Ethernet:
Works out of the box.

Webcam:
Is working right out of the box.  The button does not light up and sometimes you need to press it several times to get it to activate again but it does work.  Tested the camera in Ekiga and was working right out of the box once enabled.

HDMI:
Haven't tried it yet.

Softkeys:
The volume up/down, mute, suspend, touchpad disable and brightness up/down keys all work out of the box.

Suspend/Hibernate: Both working very well out of the box.

Other notes:
Was getting an error updating sensor temp1.  Adding the following option lines to /etc/X11/xorg.conf seems to have fixed it:
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
        Option  "AccelMethod"   "exa"
        Option  "EXAOptimizeMigration"  "true"
        Option  "MigrationHeuristic"    "greedy"
EndSection


Getting periodic freezing but that may be Skype or a general issue in Jaunty.  Have not tracked it down yet but seems to occur less often now.

I updated the button controller firmware (can't recall the name they use but it is in the System Information section of the BIOS right under BIOS version) to 1.29.   That may have helped with the webcam button.

Loving the laptop.   It runs cool and quiet and the screen is very nice (1920x1200 non-glare).  Also is lighter than my inspiron.  Will be fantastic once the last bits are working properly.

Hope this helps,

---

### Post by Burmudar on 2009-06-17
Has anyone got the sound working correctly ?

Through countless hours of googling I have gotten the "top" left and right speakers working, but then the subwoofer stops working. Also the headphone jack doesn't work as well.

If anyone can shed some light on how to get the sound working properly it will be greatly appreciated.

---

### Post by enginerd0x07b8 on 2009-06-17
This has also been a great laptop for me, however, I have also had audio issues.  I've messed around with the drivers from realtek, and pulse audio, etc...  but to no avail.  Any help would be greatly appreciated.

---

### Post by Cone on 2009-08-07
Anyone get the sound working right yet?  I'd even love to know how to get just the top left/right speakers working...anything other than all the sound coming through the subwoofer would be great -- the rattling is quite horrid.

---

### Post by bchurchill on 2009-08-18
With an MSI gx720 and an ALC1200 sound card I have a partial solution.

My partial solution seems to get everything right except for the extra line-out jack.  The headphone jack works properly.  I also have suggestions on how to get a better solution, but I don't know yet if they'll do better.


The first thing I did was upgrade the ALSA drivers to 1.0.20.  I don't think this is really necessary... but it may help.  The easiest way is to run the script provided here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)


Now for the fun part... there's a file /etc/modprobe.d/alsa-base.config.  Changing this file and restarting ALSA can improve things however it seems that nobody *really* knows what settings work quite best, and it depends on your hardware configuration.

So far, the best for me has been:
```

options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
# u1Nb.u_BNWJ+LvyF:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel

```**You will most likely need to tweek this... read on.**

I believe you could leave out the third line for the same effect.  After editing this file as root (use sudo), you need to do

```
sudo /etc/init.d/alsasound stop
```For me, I get errors the first time and have to run this command twice (the second time works).  Then you run

```
sudo /etc/init.d/alsasound start
```If you don't get errors from the stop command, you could do this command instead of running the other two:

```
sudo /etc/init.d/alsasound restart
```Now a lot of stuff should be working.  In gnome-volume-control click all the boxes in preferences.  You should also change options/channel mode to 4 or 6 channels.  You can use 'Front' to change the l/r volumes of front speakers.  Center and LFE adjusts the subs.  Ticking the 'headphones' check under 'switches' will use the levels for 'Front' in the headphone jack.   At first plugging in headphones will turn of the front speakers (but not the others).  Interestingly, I found if you mute the 'Front' it will still play through the headphone jack, and if you unmute it again then it plays through both the headphone jack and your front speakers... at least on my setup.  I have not been able to get the second output jack to do anything though.  I haven't tested the inputs.  


**HOWEVER: this configuration may not work for your computer.**  The key things to try and adjust is the setting for 'model' on the first line of the alsa-base.conf file.  There is a list of recommended things to try here: [http://forums.opensuse.org/hardware/laptop/412857-no-sound-msi-laptop-2.html](http://forums.opensuse.org/hardware/laptop/412857-no-sound-msi-laptop-2.html) (post 15).  I'm guessing the targa-related options are a good place to start.

The second, third and forth lines may or may not be needed as well.  Other things to try include appending 'probe_mask=1' to the end of the first line, but I have not had any success with this.  Also, it looks like someone got 7.1 surround sound working here: [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg24635.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg24635.html).

Good luck!  Let me know if you come up with a setup that gets everything (or almost everything) working for you!

---

### Post by RazTaz on 2010-12-11
I also have an MSI GX720 laptop. I've been using this laptop with Ubuntu Jaunty, Karmic and Lucid. Everthing works fine: camera, bluetooth, lan, front microphone, headphones, external microphone, dvd-rom, card-reader, nvdia graphic card. etc. 

The only things I couldn't set up to work properly are:

a) line-in.  I connected an mp3 player to the line-in connector but I cannot hear the sound of music in the laptop speakers although I specifically checked that line-in is enabled with "alasamixer"

b) the modem. I'm still trying to find out a way to configure it.


Everything else worked just fine and right out of the box.


I highly recommend this laptop/notebook together with Ubuntu. I'm a heavy user, running video, audio, office applications, a web server, mysql server, various GIS applications, games. I've never had a problem with it, it has never frozen.

I hope this helps.

Later edit:
I managed to make the modem work. Here is how:

1. I found this wonderful support page: [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/) (many thanks to the maintainers).
2. I downloaded, installed and ran the ScanModem utility + followed the instructions 
3. It turned out I needed the the following packages:
agrsm-11c11040_20091225_i386.deb,
agrsm-tools_0.0.1_all.deb 
agrsm_howto.txt
   All available at:
[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)
4. I installed the deb files.
5. I ran "sudo agrsm-test"
6. I installed the latest efax-gtk utility by
a) adding the repository:  "sudo add-apt-repository ppa:eugenesan/ppa"
b) updating: "sudo apt-get update"
c) installing: "sudo apt-get install efax-gtk

---

### Post by RazTaz on 2011-02-26
> **bchurchill said:**
> With an MSI gx720 and an ALC1200 sound card I have a partial solution.

My partial solution seems to get everything right except for the extra line-out jack.  The headphone jack works properly.  I also have suggestions on how to get a better solution, but I don't know yet if they'll do better.
[...]
Now for the fun part... there's a file /etc/modprobe.d/alsa-base.config.  Changing this file and restarting ALSA can improve things however it seems that nobody *really* knows what settings work quite best, and it depends on your hardware configuration.

So far, the best for me has been:
```

options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
# u1Nb.u_BNWJ+LvyF:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel

```

[...]


This worked for me like a charm and really gave me a wonderful surround sound (Now I'm using Ubuntu 10.10 Maverick)

Thanks for the great tip! Awesome.

---

