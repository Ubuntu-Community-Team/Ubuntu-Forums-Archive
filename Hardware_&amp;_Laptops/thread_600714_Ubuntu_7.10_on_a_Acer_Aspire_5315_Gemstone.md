---
title: "Ubuntu 7.10 on a Acer Aspire 5315 Gemstone"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by Arnitak on 2007-11-02
I bought this laptop for programming. Installed Vista and Ubuntu 7.10 as a dual boot. The problem is that the WiFi Card is always locked in roaming mode (whatever that is) and when I try to override manually to connect, it just connects ... and nothing. The other major problem is ... I get no sound at all although the card is seen and I can access alsamixer, although I get only two volume panels, Master and PCM. Another problem is, I run in 1280x800 and I cant change the sensitivity on my touch-pad. The touchpad works, but if I up the sensitivity from the Mouse Panel, nothing happends. Can anyone help me? Here are my specs (not all of them, those that I found out only).

The wifi is seen as a Broadcom BCM94311MCG.

The sound I think, from windows vista that it is a realtek.

---

### Post by kameleon25 on 2007-11-02
You bought the laptop from walmart for $498 this morning huh? I have the same laptop and am going to try the triple boot deal but am unsure how well that will work. How did you get your dual boot working? I am interested as most sites and threads have conflicting ideas.

---

### Post by Arnitak on 2007-11-02
Well, I bought it from what it would be a Eastern Europe equivalent of Walmart. Yeah, around that sum. But honestly, it's woth all the money. Excellent laptop, the LCD is fantastic and vibrant. Very enthusiastic as you see ... however im straying from the point :)

I got the dual boot simply, I told Ubuntu to install the GRUB on MBR along side Win Vista Home Premium. It had no trouble at all.

---

### Post by mikeserv on 2007-11-02
I bought an Acer Aspire 5315-2153 from Walmart this morning for $348.  The wireless card is an Atheros AR5007EG.  I found this thread about it:  [http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg)

Does this help?  I'm in the process of wiping Vista and installing Ubuntu on it right now.  I left the 10gb Windows recovery partition, though.

-Mike

---

### Post by soleblaze on 2007-11-02
The Acers that walmart sold are different than the european versions (well, mostly..they have the same look).. the Euro versions have a webcam and can burn dvds..they also use a different wireless chipset (a Broadcom).  Other than that, they're the same.

---

### Post by bytor4232 on 2007-11-03
I picked up the $348.00 deal Friday morning at 8am.  Our Wal-mart had 20 of them, I got the 15th one.  I've been working on it ever since, trying to get everything working.  Here are some helpful, if not somewhat cryptic, ramblings from my travels.

First order of business, Vista had to GO.  Ubuntu installed quick, and impressed me with as much as it got working.  This is all pretty new hardware, and I expected nothing to work properly.  And in true Linux Zealot fashion, I wiped everything, burning all bridges to Microsoft forever.  Bye Bye Windows Recovery partition.:guitar:

After you get through the install, which is painless, first things first, edit /etc/X11/xorg.conf and disable the synaptics driver.  It doesn't work right.  Once you comment out the line, looks like InputDevice     "Synaptics Touchpad" under serverlayout twords the end of the file, the touch pad started working properly.  The middle button even acts as a scroll mouse.  Obviously, you need to restart X.

Wireless was a pain.  I tried all the madwifi drivers, and no luck.  I even tried ndiswrapper, and the version shipped with Gutsy is too old.  You need to download the most recent version, mine is using 1.49.  Next you have to download the Windows XP drivers for the wireless device.  The vista drivers don't work.  You'll need to apt-get install build-essential to compile ndiswrapper.  Oh, every kernel update will need this rebuilt and installed, so make sure you save it somewhere sane.  i put mine in /drv.

Here are the two files you need for the wireless:
[http://arthur.jfmi.net/ndiswrapper-1.49.tar.gz](http://arthur.jfmi.net/ndiswrapper-1.49.tar.gz)
[http://arthur.jfmi.net/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip](http://arthur.jfmi.net/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip)

After uncompressing the Atheros driver, its located in Wireless_Atheros_V5.3.0.67_XP_XB63_XB62\(WHQL\)/Drivers/XP-x32/

To install the driver, run ndiswrapper -i net5211.inf

Before you reboot, you need to blacklist the non-working driver (madwifi):

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

And put ndiswrapper at the end of /etc/modules

As for the sound, no luck.  I tried updated alsa to the latest rc, tried installing from mercurial, and even upgraded the kernel to 2.6.23.1.  No luck so far.  However, it doesn't really bother me.  I have two portable DVD players, one plays divx, and I have an iPod Nano.  I have all the portable entertainment I need, what I have to have is a portable wireless workstation, and I'm to that point with this baby.  Besides, this isn't a bug specific to Acer Aspire's.  Pretty much all the most recent laptops all use the intel HDA drivers, and none of them are working right.  There is bugs out to Alsa, Kernel, Ubuntu, and most major distributions.  It will sort itself out in time.

All in all, I'm extreamly happy with this laptop.  The display is beautiful, the wireless strong even with winXP drivers.  This pretty much is the laptop I've always dreamed of.  Besides my 7 year old Compaq is really starting to show its age.

You can email me at arthur(at)jfmi.net if you need any help. I'll post when sound starts working.

---

### Post by krowv on 2007-11-03
> **bytor4232 said:**
> I picked up the $348.00 deal Friday morning at 8am.  Our Wal-mart had 20 of them, I got the 15th one.  I've been working on it ever since, trying to get everything working.  Here are some helpful, if not somewhat cryptic, ramblings from my travels.

First order of business, Vista had to GO.  Ubuntu installed quick, and impressed me with as much as it got working.  This is all pretty new hardware, and I expected nothing to work properly.  And in true Linux Zealot fashion, I wiped everything, burning all bridges to Microsoft forever.  Bye Bye Windows Recovery partition.:guitar:

After you get through the install, which is painless, first things first, edit /etc/X11/xorg.conf and disable the synaptics driver.  It doesn't work right.  Once you comment out the line, looks like InputDevice     "Synaptics Touchpad" under serverlayout twords the end of the file, the touch pad started working properly.  The middle button even acts as a scroll mouse.  Obviously, you need to restart X.

Wireless was a pain.  I tried all the madwifi drivers, and no luck.  I even tried ndiswrapper, and the version shipped with Gutsy is too old.  You need to download the most recent version, mine is using 1.49.  Next you have to download the Windows XP drivers for the wireless device.  The vista drivers don't work.  You'll need to apt-get install build-essential to compile ndiswrapper.  Oh, every kernel update will need this rebuilt and installed, so make sure you save it somewhere sane.  i put mine in /drv.

Here are the two files you need for the wireless:
[http://arthur.jfmi.net/ndiswrapper-1.49.tar.gz](http://arthur.jfmi.net/ndiswrapper-1.49.tar.gz)
[http://arthur.jfmi.net/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip](http://arthur.jfmi.net/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip)

After uncompressing the Atheros driver, its located in Wireless_Atheros_V5.3.0.67_XP_XB63_XB62\(WHQL\)/Drivers/XP-x32/

To install the driver, run ndiswrapper -i net5211.inf

Before you reboot, you need to blacklist the non-working driver (madwifi):

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

And put ndiswrapper at the end of /etc/modules

As for the sound, no luck.  I tried updated alsa to the latest rc, tried installing from mercurial, and even upgraded the kernel to 2.6.23.1.  No luck so far.  However, it doesn't really bother me.  I have two portable DVD players, one plays divx, and I have an iPod Nano.  I have all the portable entertainment I need, what I have to have is a portable wireless workstation, and I'm to that point with this baby.  Besides, this isn't a bug specific to Acer Aspire's.  Pretty much all the most recent laptops all use the intel HDA drivers, and none of them are working right.  There is bugs out to Alsa, Kernel, Ubuntu, and most major distributions.  It will sort itself out in time.

All in all, I'm extreamly happy with this laptop.  The display is beautiful, the wireless strong even with winXP drivers.  This pretty much is the laptop I've always dreamed of.  Besides my 7 year old Compaq is really starting to show its age.

You can email me at arthur(at)jfmi.net if you need any help. I'll post when sound starts working.

Thanks for the post.  I did pretty much exactly the same thing.  Purchased it at 8;30am from Walmart, brought it home, and have been playing with it ever since.  I nuked Vista as well including the recovery partition, and I am running Ubuntu 7.10 on it.

As for wireless and ndiswrapper, I've gotten things working with what ships with Gutsy and XP drivers, however it has been a little bit flaky.  Is that what you noticed before you upgraded?  Or were you not able to get things to work at all with Gutsy without upgrading ndiswrapper.

As for sound, I'm noticing problems as well.  No sound will play.  Oddly, it looks like everything is working, the open volume control interface works, and then Vol + and Vol - keys on the laptop will move the sound volume, and yet no sound comes out.

Overall, I'm quite happy with the laptop as well.  Given a little time I'm sure the sound and wireless issues will get worked out.

---

### Post by Arnitak on 2007-11-03
The one I bought dosent have any webcam, no Vista licence, no card-reader. Ah well, dosent really matter. I could not use ndiswrapper at all with my broadcom chip. As for the sound, dosent work at all. I am going to use my XP drivers for the broadcom with you ndiswrapper tar. I bought this laptop especially for nix programming, imagine the Broadcom surprise on my head ...:(

---

### Post by mikeserv on 2007-11-03
Ok, I've got the wireless networking and sound working for the Acer Aspire 5315-2153.  I followed the wireless installation instructions in the forum I posted above ([http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg)) and got it setup.  But I was unhappy with the way that Ubuntu's default Network Manager was handling my network card (I had to redefine my "manual configuration" for my home network every time I rebooted, which is a lot right now because I'm trying to get all of these things to work), so I followed the author of that thread's advice and installed wicd.  So far it's working great and only required an initial setup - no mucking around with it since.  You can get installation instructions for wicd here: [http://blakecmartin.googlepages.com/wicd.html](http://blakecmartin.googlepages.com/wicd.html)

The sound was pretty hard.  I followed a combination of the instructions found here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and [http://ubuntuforums.org/showthread.php?t=584890&highlight=ar5007eg](http://ubuntuforums.org/showthread.php?t=584890&highlight=ar5007eg).  For the ALSA upgrade I followed the instructions given by the first link, but only after stopping alsa as outlined by the second link.  Then, after compiling and installing alsa-utils, I went on to follow the instructions given in the second link starting with running alsaconf and followed that to the end.  After rebooting, I went back to the first link, tried cat /proc/asound/card0/codec#* | grep Codec
and found that I had a Codec: Realtek ALC268

After all of this I continued with the first link in adding the "options snd-hda-intel model=acer" line to my /etc/modprobe.d/alsa-base file.

I should point out that I also added the lines: 
# default boot parameters, set pci=routeirq for sound to work (as per dmesg output)
kopt=pci=routeirq  
 to my /boot/grub/menu.lst file.  It comes immediately after "### END DEBIAN AUTOMAGIC KERNELS LIST" in the file.

While I'm not sure how much of that was actually necessary, I know that the sound works now.  So, good luck.

I think next I'll check out compiz - when I try to enable desktop effects right now it's a nogo.

-Mike

---

### Post by samtr on 2007-11-03
Hi I have the exact same computer and I was able to get the wireless working with the same link that you posted, but I've spent the last couple of days trying to get the sound to work and I've had no luck. I tried following the two links you listed for the sound but being new to Linux all the coding really confused me, especially with installing the alsa drivers. I hope there's an easier way sooner.

---

### Post by KriKit on 2007-11-03
Here's what I did to get the following missing features for my cheap Walmart Asus 5315-2153 to work on Ubuntu.

**Enabling Wireless** these directions worked for me:
[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

**Enabling Sound** follow the directions in this link
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

1. When the above directions ask you to edit /etc/modprobe.d/alsa-base to add the model add the following to the last line of the file:
options snd-hda-intel model=acer
2. Save then restart.

**Enabling Visual Effects** use the following link:
[http://ubuntuforums.org/showpost.php?p=3654273&postcount=20]("http://ubuntuforums.org/showpost.php?p=3654273&postcount=20"). 

1. run sudo gedit /usr/bin/compiz
2. find and comment string T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965 by adding # in front of the line
3. Goto 'System' > 'Preferences' > 'Appearance', Choose 'Visual Effects' and select 'Extra'

**Please note it appears that enabling Visual Effects will cause video playback issues, Totem, VLC, and other media players kept crashing immediately until I disabled Visual Effects**

I love this little laptop! It doesn't run hot on my lap, the design doesn't say "steal me", it runs quite, the monitors bright, and it feels like it could take a spill from a drop.

---

### Post by samtr on 2007-11-04
I'm having a bit of trouble following the directions to get the sound working with the link above. I go and type in 

sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

and I get 

cp: cannot stat `/home/sam/downloads/alsa*': No such file or directory

can somebody help me? Again I'm not computer literate. Thanks.

---

### Post by Lumbergh on 2007-11-04
I managed to install Gutsy just fine but same issues with the wireless and sound, I'll fix this stuff
if I get past my current problem. The hard drive is really squeaky and I wonder if this is a specific
problem with mine or you guys that bought them also noticed this? If not I can send it into them 
for replacement but I was just curious..

---

### Post by KriKit on 2007-11-04
> **samtr said:**
> I'm having a bit of trouble following the directions to get the sound working with the link above. I go and type in 

sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

and I get 

cp: cannot stat `/home/sam/downloads/alsa*': No such file or directory

can somebody help me? Again I'm not computer literate. Thanks.
**Samtr **I had this problem too until I realized that the directions are assuming you have downloaded the alsa drivers in your user directory under a directory called downloads. If you download the alsa files to your desktop then the command would be:

sudo cp ~/Desktop/alsa*

Try moving those files to your desktop then following those steps again, with the above command.

---

### Post by KriKit on 2007-11-04
> **Lumbergh said:**
> I managed to install Gutsy just fine but same issues with the wireless and sound, I'll fix this stuff
if I get past my current problem. The hard drive is really squeaky and I wonder if this is a specific
problem with mine or you guys that bought them also noticed this? If not I can send it into them 
for replacement but I was just curious..

I noticed the LCD screen rings a bit when it is running from a power outlet. I'm not sure if it only happens when it is charging.

---

### Post by samtr on 2007-11-04
KriKit thank you so much I finally got the sound working.

---

### Post by awang44 on 2007-11-04
I still could not get the sound card to work.

when I do "cat /proc/asound/cards" 
it tells me " no sound card"

seems like I have to activate the card somehow.

---

### Post by mikeserv on 2007-11-04
Awang:

When you press the "Vol +" and "Vol -" buttons on the keyboard do you see anything on the screen?

-Mike

---

### Post by mikeserv on 2007-11-04
Compiz - 

I got it working - but not the same way that other guy did.  I did this:

1.  ```
sudo mkdir ~/.config/compiz
sudo touch ~/.config/compiz/compiz-manager
echo "SKIP_CHECKS=yes" | sudo tee -a ~/.config/compiz/compiz-manager
```

2.  And then, in order to make sure video still worked I ran (with *ALT+F2*) the program *gstreamer-properties*.  I clicked on the *Video* tab and, I chose *X Windows System (No Xv)* for my *Default Output* plugin.

I will note that I had to use this for both users on the laptop.

-Mike

---

### Post by Arnitak on 2007-11-04
> **awang44 said:**
> I still could not get the sound card to work.

when I do "cat /proc/asound/cards" 
it tells me " no sound card"

seems like I have to activate the card somehow.

Have the same problem, yeah I see the volume on the screen.
For acer 5315 what codec do I need?

---

### Post by samtr on 2007-11-04
It should say something along the lines of Realtek 268

BTW does anybody else find that the Touchpad is a little bit touchy (no pun intended)?

---

### Post by mikeserv on 2007-11-04
Well, you have to get ALSA completely reinstalled.  The only reason I can think that you wouldn't show a card is that there is no driver for it.  Try the ALSA directions as outlined in this thread.

Also, try adding 
# default boot parameters, set pci=routeirq for sound to work (as per dmesg output)
kopt=pci=routeirq
to your /boot/grub/menu.lst file. It comes immediately after "### END DEBIAN AUTOMAGIC KERNELS LIST" in the file.

-Mike

---

### Post by awang44 on 2007-11-04
> **mikeserv said:**
> Awang:

When you press the "Vol +" and "Vol -" buttons on the keyboard do you see anything on the screen?

-Mike

Mike:
thank you for replying.
I am able to see the volume thing but no level showing. the volume icon on top right of the screen shows in mute. I was able to see the adjusting volume before I followed the step of [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I have what you suggested in the menu file.


thanks

---

### Post by mikeserv on 2007-11-04
Ok, I think I understand.  I think that you need to go through that whole thing again.  Only, this time, make sure that you run this command first:  ```
sudo apt-get install libncurses5-dev
```.

Actually, make sure you stop the current ALSA processes first.  ```
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsasound stop
```

-Mike

Edit:  Also, I guess I should say that I was in that spot for a little while.  While I never actually tried the codec display command, I definitely had the other thing: you know, where you press the Vol + or - button and it pops up but won't adjust and it shows the volume all the way down.  Also, I had the volume control icon at the top right of the screen perpetually set to "mute" and it wouldn't change.  It wasn't until I went through all of the steps that I said that I took (post #9 in this thread) for a SECOND time that I finally got it to work.

Edit:  Oh, and another problem I had when I was in-between trying to get it to work and it ACTUALLY working (at the same time that the VOL+ and - buttons behaved as described above) was this: I tried *System > Preferences > Sound* and whenever I would try to change any of the drivers on the drop-down lists in there (and then press test) I would get this error message, something about something not being found maybe?  Anyway, I think that if you try that right now, you'll find that you have the same problem (at least I hope so), because, if you do, then we'll know that you're roughly in the same place that I was and that it can be fixed.

If you go through all of that stuff and it STILL doesn't work, then I would recommend a clean install.  (I installed Gutsy on this thing three times when I was trying to get wireless to work)

-Mike

---

### Post by awang44 on 2007-11-04
Hi, Mike

I did "sudo apt-get install libncurses5-dev"
It responded
" Reading state information ... done
E: can not find libncurses5-dev"

I did try "sudo apt-get install libncurses5"
it tells me that i have the latest package

Al

---

### Post by mikeserv on 2007-11-04
Ok, I'm gonna write my own little sound how-to here, since, as I've said, I really used two threads put together to get my sound working.  These can be found [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and [here]("http://ubuntuforums.org/showthread.php?t=584890&highlight=ar5007eg").  (Actually, it was three, if you count the first step, but I don't remember where I got that info - it just seemed to make sense when I read, though I have no idea what it actually does)

**Enabling Sound**

1.  Press *ALT+F2* and run the command *gksudo gedit /boot/grub/menu.lst*  Warning: be careful what you do with this file, as this is the file that tells your computer where on the harddrive to find Linux (and Windows, if you dual-boot).

Ok, now find the line that says: *### END DEBIAN AUTOMAGIC KERNELS LIST* and, immediately under it, add these two lines: ```
# default boot parameters, set pci=routeirq for sound to work (as per dmesg output)
kopt=pci=routeirq 
```

Save and exit.

2.  We're about to start downloading, compiling, and installing a new version of ALSA, but, before we do, we need to stop any ALSA processes that might be currently running.

Open a terminal window and enter these commands: ```
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsasound stop
```

3.  Now, again before we download and install, let's make sure that we have all of the packages required for compilation and install. ```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install libncurses5-dev
```

4.  Next we need to get the ALSA packages.  Download the latest versions of [alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/"), [alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/") and [alsa-utils]("ftp://ftp.alsa-project.org/pub/utils/") at their respective links.  (Note, those three file names in the previous sentence are actually links to the download sites.)

Be sure you remember what your save location was (the directory that those three files were downloaded to) because that path will be in a command in the next step.  The command will say *sudo cp ~/downloads/alsa* .* but what it really means is *sudo cp (directory that you saved those three files to)/alsa* .*  For instance, if you saved those three files to your desktop, the code would be ```
sudo cp ~/Desktop/alsa* .
```

5.  Now that we have the driver packages, we're almost ready to install them.  But first, let's create a separate directory to install them from and then unpack them.  ```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```

6.  With the files unpacked and setup, we're ready to compile and install.  First, we'll do the alsa-driver package: ```
cd alsa-d*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```  And next the alsa-lib packages: ```
cd ../alsa-l*
sudo ./configure
sudo make
sudo make install
```  And finally the alsa-utils package, (pay special attention to this one, I ran into errors because I didn't have the proper curses libraries installed): ```
cd ../alsa-u*
sudo ./configure
sudo make
sudo make install
```

7.  Now run the initial ALSA setup program: ```
sudo alsaconf
```

Edit: I added *sudo* in there because apparently that script requires root access.  Thanks to [minhdinh]("http://ubuntuforums.org/member.php?u=424140") for pointing that out.

8.  Ok, here's where some stuff really starts to get interesting.  I did a lot of copying at this point, and, again, while I'm not sure how necessary it is, I know it's what I did and how I got things to work.  

Press *ALT+F2* and run *gksudo nautilus*.  Warning:  what you've just done is open a root-enabled browser window for your harddrive.  It is entirely possible to delete or move very important files with this access.  Be careful.

Ok, now we're going to do some file copying.  Navigate to */lib/modules/(kernel version)/kernel/sound/pci/hda/* and copy the file *snd-hda-intel.ko* to the directory */lib/modules/(kernel version)/ubuntu/media/snd-hda-intel/*.  Next navigate to */usr/src/alsa/alsa-driver*/modules* and find these 13 files: ```
snd-hda-intel.ko
snd-hwdep.ko
snd-mixer-oss.ko
snd-page-alloc.ko
snd-pcm-oss.ko
snd-rtctimer.ko
snd-seq-device.ko
snd-seq-midi-event.ko
snd-seq-midi.ko
snd-seq-oss.ko
snd-seq.ko
snd-timer.ko
snd.ko
```  Copy them all to */lib/modules/(kernel version)/kernel/sound/*.

Run: ```
sudo depmod -a
```

9.  Ok, now we'll start ALSA back up: ```
sudo /etc/init.d/alsa-utils start
sudo /etc/init.d/alsasound start
```

10:  Run: ```
sudo alsamixer
```  Unmute all of the channels and set your volume.

11.  We're just about done, but first we're going to manually input our model.  Press *ALT+F2* and enter the command *gksudo gedit /etc/modprobe.d/alsa-base*.  Warning: we've just given ourselves root access to an important sound configuration file.  We must be careful here.

Scroll to the bottom of the file and enter this line: ```
options snd-hda-intel model=acer
```  Save and exit.

12.  Reboot.  It was at this point that my sound started working.  I knew it when I heard the Ubuntu drums at startup.  Hopefully it works for you, too.

-Mike

---

### Post by mikeserv on 2007-11-04
Did you run a search for it in Synaptic?  It could be that you do not have the development repositories enabled.  Try *System > Administration > Software Sources* and make sure that all 5 of the checkboxes under *Downloadable from the Internet* are checked in the first tab.  Then navigate to the bottom and hit "Close."  If you've made any changes it should update your sources for you.

Next, open *System > Administration > Synaptic Package Manager* and run a search for *libncurses5-dev*.  It should find it.  When it does, just check the checkbox next to it and hit "Apply."  That should do all of the installing that you need. 

Afterwards, try to take the ALSA installation from the top again.

-Mike

---

### Post by Moey on 2007-11-04
I know this seems really stupid, but I can't get my laptop to boot from CD so I cant even install Ubuntu.  Did you guys do anything special?

****Nevermind F2 worked for me this time.

---

### Post by mikeserv on 2007-11-04
Yeah, when it first boots up you'll see that big whit acer screen.  At the bottom left, for just a split second, it will say something like "Press F2 for setup."  (At least I think it's F2).  Anyway, press whatever button it says and you'll be at the BIOS setup screen.  TAKE CARE!  There is some really sensitive stuff in there. 

Ok, once in the BIOS find the boot menu and tell the computer to check for a bootable CD *before* a bootable harddrive.  It's pretty simple, just move the CD drive to the top of the list.  Then, Save and Exit.

The next time the computer boots up, if there's a bootable CD in the drive, it'll boot from it.  If there's not, it'll move on to the hard drive.

-Mike

---

### Post by Moey on 2007-11-04
Thanks for your response.

I am also having one more problem.  When it trys to install Ubuntu off the cd, it spits out the error "cannot access tty".  After doing some google work, I think my CD may have an error, so im re-downloading the iso.  Does anyone have any more insight on this?

---

### Post by monte48lowes on 2007-11-04
Thanks for the help with the sound Mike. Now I have everything working on my cheap Wal-mart special. I am using kubuntu gutsy, so some of the items were different, but I have found this thread very helpful.

Someone asked about the touch pad... it sucks in vista as well. I think it's just the way it's built.

Mike

---

### Post by monte48lowes on 2007-11-04
Almost forgot something. During my first boot into Vista I ran windows update. The system blue screened during the update installation. I could no longer log into the machine unless I was in safe mode (it would blue screen as soon as I logged in,,, during several subsequent tries). It ended up being the Intel video driver. I downloaded the version from the ACER website and was able to get it running again. I was really upset. I could not believe windows would leave me stranded... and without a support forum as good as this one.... and to think it costs money.. sheesh.

Mike

---

### Post by bytor4232 on 2007-11-05
> **mikeserv said:**
> Ok, I've got the wireless networking and sound working for the Acer Aspire 5315-2153.  I followed the wireless installation instructions in the forum I posted above ([http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg)) and got it setup.  But I was unhappy with the way that Ubuntu's default Network Manager was handling my network card (I had to redefine my "manual configuration" for my home network every time I rebooted, which is a lot right now because I'm trying to get all of these things to work), so I followed the author of that thread's advice and installed wicd.  So far it's working great and only required an initial setup - no mucking around with it since.  You can get installation instructions for wicd here: [http://blakecmartin.googlepages.com/wicd.html](http://blakecmartin.googlepages.com/wicd.html)

The sound was pretty hard.  I followed a combination of the instructions found here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and [http://ubuntuforums.org/showthread.php?t=584890&highlight=ar5007eg](http://ubuntuforums.org/showthread.php?t=584890&highlight=ar5007eg).  For the ALSA upgrade I followed the instructions given by the first link, but only after stopping alsa as outlined by the second link.  Then, after compiling and installing alsa-utils, I went on to follow the instructions given in the second link starting with running alsaconf and followed that to the end.  After rebooting, I went back to the first link, tried cat /proc/asound/card0/codec#* | grep Codec
and found that I had a Codec: Realtek ALC268

After all of this I continued with the first link in adding the "options snd-hda-intel model=acer" line to my /etc/modprobe.d/alsa-base file.

I should point out that I also added the lines: 
# default boot parameters, set pci=routeirq for sound to work (as per dmesg output)
kopt=pci=routeirq  
 to my /boot/grub/menu.lst file.  It comes immediately after "### END DEBIAN AUTOMAGIC KERNELS LIST" in the file.

While I'm not sure how much of that was actually necessary, I know that the sound works now.  So, good luck.

I think next I'll check out compiz - when I try to enable desktop effects right now it's a nogo.

-Mike

Oh snap!  I came to this thread to post the same thing.  I added the following line to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=acer

Rebooted, and BAM!  I got the "dump dunt!" at the longin window!  I am super happy.  I can also note that kernel 2.6.23.1 and the model=acer does NOT work, so don't upgrade your kernel.

EVERYTHING IS WORKING!  I am dancing for joy.  I couldn't be happier.  This is the laptop I've always wanted.

---

### Post by iffydonatello on 2007-11-05
Alright, I'm a Ubuntu dilettante so bear with me. When I tried to install alsa-utils it gave me an error:

checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.
iffydonatello@Awesome:/usr/src/alsa/alsa-utils-1.0.15$ sudo make
make: *** No targets specified and no makefile found.  Stop.
iffydonatello@Awesome:/usr/src/alsa/alsa-utils-1.0.15$ sudo make install
make: *** No rule to make target `install'.  Stop.

and I can't continue with the setup. Has anyone had this problem, or figured out a way to workaround it?

Many thanks!

---

### Post by awang44 on 2007-11-05
Mike:
thank you for the help.
at step 7, I enter "alsaconf" it returns command not found. I can see alsaconf in the directory. just not able to use it.

Al

---

### Post by mikeserv on 2007-11-05
Al,

If you're seeing that error (which is one I remember well and encountered myself), it's mostly likely because your installation of alsa-utils did not complete.  I had the same problem.

Now, when alsa-utils would not install for me it was because I didn't have libncurses5-dev installed.  Have you successfully installed that from the repositories?  Refer to post #27 in this thread (that post was for you, by the way, I just forgot to put your name in it) and try the steps outlined there, first.

If you can get libncurses5-dev installed, try the process again from the top.  Good luck!

-Mike

P.S.  Have faith, it can work!  I have the exact same computer and it works fine.

---

### Post by awang44 on 2007-11-05
Mike:
Yes, libncurses5-dev was a problem. I did by your instruction in #27 posting, it worked. 
Then I encounter the problem in #35. I'm thinking of reload Ubuntu and start all over from begining. Maybe soemthing I did before broke whatever it is so it wouldn't work.

thanks.

Al

---

### Post by colbypaperboy on 2007-11-05
> **mikeserv said:**
> Navigate to */lib/modules/(kernel version)/kernel/sound/pci/hda/* and copy the file *snd-hda-intel.ko* to the directory */lib/modules/(kernel version)/ubuntu/media/snd-hda-intel/*.

Thanks for doing a how-to for Ubuntu morons like me. :)

Now...I'm with you till this part. I can navigate all the way to the "pci" folder, but there is no "hda" folder. Obviously I've dorked something here...any ideas?

TIA

---

### Post by mikeserv on 2007-11-05
Al - 
  If you try the reinstall, please document your progress.  I know it's a lot of work, but it helps everyone out.

TIA - 
  I'm as lost as you are on that one, buddy.  As I said in the how-to, I'm not really certain what all of that file-copying does - I just know that was one of the steps that I took to get my sound to work.  Do you also have the Acer Aspire 5315-2513?  Did you see any error messages while you were compiling and installing the three alsa packages?

-Mike

---

### Post by colbypaperboy on 2007-11-06
> **mikeserv said:**
>  Did you see any error messages while you were compiling and installing the three alsa packages?

I want to say yes, but I'm not sure. I've gone through the how-to a couple of times and am pretty sure I saw some errors generated, but the Alsa setup program still ran when I was through, so I assumed all was OK.

I don't have the computer with me now...I will reply with the exact output from each step when I have time later on to fool with it again.

The computer is the same one you've got. I'm really stunned with how *nice* this thing is for just $348 plus tax. I didn't really need a computer, but at that price I would have been foolish to pass it up. Ubuntu runs great on it. Wireless wound up being pretty easy thanks to the how-to I found on it in another thread and the information regarding your trials and tribulations.

I elected to keep Vista on it since there was plenty of hard drive space after I reduced the size of the "DATA" drive.

I'll get back with you later with more details on my install. I appreciate (and I'm sure others do as well) your help and hard work on this. =D>

---

### Post by bytor4232 on 2007-11-06
I thought about keeping Vista, but I would never use it.  I'd rather have the hard drive space.

Yeah, it blows me away how good this lappy is.  400 laptops are usually slow Via processors and 40 gig hard drives with 1/2 gig of ram.  This definitely has power, and the price was unbeatable.

---

### Post by minhdinh on 2007-11-06
hi i have an acer aspire 5570-2094 and i am having problems with my sound card. i have absolutely no sound at all and i tried to follow this thread and all the comments people posted but i cant get it to work. when i first booted into ubuntu with the live cd the sound works perfectly but when i installed ubuntu onto this laptop with duel boot vista the sound doesnt work but when i load into vista it workes perfectly.

the part that i am stuck at is this

minh@minh-laptop:~$ sudo apt-get install build-essential ncurses-dev gettext
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

everysingle time i try to do something i usually get the exact same message saying "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " and i am absolutely new to linux and ubuntu so i dont even know wat it means or wat its telling me to do. ive tried to follow other threads to get my sound working but whenever i have to download something or edit something or practically do anything in the terminal i get this stupid message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

im not sure if this is important but these are the specs on the sticker for my laptop
intel pentium duel-core processor T2060 (1.60 GHz, 533 MHz FSB, 1MB L2 cache)
14.1 WXGA ACer CrysalBrite LCD
Intel Graphics Media Accelerator 950
160GB HDD
1GB DDR2
802.11b/g wireless LAN

BTW i am using ubuntu 7.10

please someone post a reply to help me with this problem becuz its frustrating me to the point where i think that i might as well stick to vista cuz without sound theres no point using ubuntu

---

### Post by mikeserv on 2007-11-06
Minh - 

If I were in your situation the first thing I would do is follow the error messages's advice, meaning I would open a terminal window, and type "dpkg --configure -a" and press enter. I'm not sure what will happen, but it looks like some kind of configuration setup, so be prepared to answer questions about your system.

Now, if that didn't work, my next step would be uninstalling and reinstalling dpkg.  The way I would do it is this:   First I would open Software Sources (click *System > Administration > Software Sources*) and check to make sure that I was using only Official Ubuntu Repositories.  You can do this in that program by clicking on the second tab from the left (*Third Party Sources*) and unchecking everything.  

Next, I would open Synaptic (click *System > Administration > Synaptic Package Manager*) and run a search for *dpkg*.  After this I would check all of the GREEN boxes and select *Mark for Reinstallation*.  Then I would click apply and let Synaptic do its job.

After all of that I would start over with whatever I was trying to do in the first place.

And, if it still didn't work, I would try searching the forums with my error message.  Last, if all else failed, I would open up my own thread and title it with the error message I was getting.

-Mike

---

### Post by nvance on 2007-11-06
Minh, 

Mike has gone down the correct path...I ran into this the other night when my laptop was acting up and I had to manually run the Synaptic Package Manager via the terminal window.  Open the terminal window and type 'Sudo dpkg --configure -a' (I believe that this is correct).  It will manually run the updates that were interrupted when you were doie-ng them via the GUI interface (Synaptic Package Manager).  After that has ran, you can run every update with the Package Manager again and you should not see the error anymore.

Hopefully this helps.

-Nate-

---

### Post by ralpho1228 on 2007-11-06
> **mikeserv said:**
> I bought an Acer Aspire 5315-2153 from Walmart this morning for $348.  The wireless card is an Atheros AR5007EG.  I found this thread about it:  [http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg)

Does this help?  I'm in the process of wiping Vista and installing Ubuntu on it right now.  I left the 10gb Windows recovery partition, though.

-Mike
I bought the $348 Acer 5315 from Walmart last Friday also, and am still trying to get PCMCIA card reader working.  Found support # for Acer: 800-816-2237. Tech said card reader is bad.
Here's how to reinstall system or drivers:
ALT F10    setup password: 666666  hint: acer 
once you have this setup look for restore and click vista on left side.
Next time you press ALT F10 -- the menu will come up.
Hope this helps !!

---

### Post by mikeserv on 2007-11-06
Ralph -
So, if I did want to restore to manufacturer's settings, when would I press ALT+F10?  At boot?  It doesn't seem to do anything in Linux.

-Mike

---

### Post by mikeserv on 2007-11-06
Nate - 

Yeah, that looks right, but Minh, don't capitalize "Sudo" rather use "sudo".  Linux is case sensitive all the time.

-Mike

---

### Post by iffydonatello on 2007-11-06
Thanks everyone for all your help. After trying and trying and...well you get it, I wasn't able to get the sound to work. I did everything you told me to Mike. After doing all that, I got the Gstreamer message when trying to use the volume controller. I decided to see if there were anything else out there about the sound card in this laptop and I found this post:

[yep this one]("http://ubuntuforums.org/showthread.php?t=543793&highlight=gstreamer&page=2")

And it it worked right away! Anyway thanks for all the help the last few days of struggle. I learned a ton about ubuntu, because of this problem. And to think I was about to reinstall Vista! Thanks again all

---

### Post by gcastell on 2007-11-06
Mike,

I've the instruction on that thread and it didn't work for me, can you please tell me which of all drivers did you use?  and did you use the version 1.49 for ndiswrapper?

The first time I install it I was able to see the wireless networks but I was unable to connect, then I decided to start over and I reinstall gutsy follow the instruction and it seems that the problem is that the hardware is not being initialized because I can't see it using lspci, any idea?

Thanks for all your help, I am new to Ubuntu and since I installed it successfully in an old laptop I thought it will be just as easy on this new laptop.. not so far :(

> **KriKit said:**
> Here's what I did to get the following missing features for my cheap Walmart Asus 5315-2153 to work on Ubuntu.

**Enabling Wireless** these directions worked for me:
[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

**Enabling Sound** follow the directions in this link
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

1. When the above directions ask you to edit /etc/modprobe.d/alsa-base to add the model add the following to the last line of the file:
options snd-hda-intel model=acer
2. Save then restart.

**Enabling Visual Effects** use the following link:
[http://ubuntuforums.org/showpost.php?p=3654273&postcount=20]("http://ubuntuforums.org/showpost.php?p=3654273&postcount=20"). 

1. run sudo gedit /usr/bin/compiz
2. find and comment string T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965 by adding # in front of the line
3. Goto 'System' > 'Preferences' > 'Appearance', Choose 'Visual Effects' and select 'Extra'

**Please note it appears that enabling Visual Effects will cause video playback issues, Totem, VLC, and other media players kept crashing immediately until I disabled Visual Effects**

I love this little laptop! It doesn't run hot on my lap, the design doesn't say "steal me", it runs quite, the monitors bright, and it feels like it could take a spill from a drop.

---

### Post by minhdinh on 2007-11-06
i fixed my problem with the dpkg error that i posted earlier thanks to nvance, wat happened was i was installing flash plugin and it was so slow that i just exited it but it made an error so when i did wat nvance said it fully installed the plugin and then i was able to download other things now. the problem i am having now is about step 5 or 6 on page 3 of this thread; mikeserv's guide to fixing the sound problem.

i dont know how to copy wat i see in the terminal so im just gonna copy n paste wats going on. btw i downloaded those 3 files no problems now i just dont know wat to do cuz im getting this error

minh@minh-laptop:~$ sudo mkdir -p /usr/src/alsa
minh@minh-laptop:~$ cd /usr/src/alsa
minh@minh-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
minh@minh-laptop:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
minh@minh-laptop:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tar: alsa-utils*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
minh@minh-laptop:/usr/src/alsa$ 

mike i hope u can reply to me soon to help solve this cuz its been almost a week since i installed ubuntu and i really want to fix sound

---

### Post by mikeserv on 2007-11-06
Iffy - 

Sweet!  That set of instructions worked?  That looks much easier than all the **** I went through...  Man, I wish I had tried that instead...

G -

I had the same problem.  The first time I installed I was on the verge of getting wireless to work when, in my ignorance, I screwed something up royally (though I can't remember off hand what it was).  So I installed again, and, unlike the first time I installed, I didn't receive any Atheros HAL (the drivers that Ubuntu erroneously tries to use to control our WIFI) messages.  As it turned out, the card wasn't showing up in lspci, either - not even the wrong Atheros AR5006 it tried to install the first time.  After installing ndiswrapper and trying to get it to work, the system still wouldn't recognize my card.

But, as they say, the third time is the charm.  I say this because the third time I installed Ubuntu it did try the HAL drivers and I was able to install ndiswrapper (yes, version 1.49, along with the latest version of net5211.inf), and, this having been my third try, I was experienced enough to keep it running right.

So, while I know my saying "reinstall" sounds like a cop-out, I'm only telling you to do what I did.  The truth is it did seem awfully weird to me that Ubuntu would see my wireless card only some of the time, but that seems to be what happened.

-Mike

---

### Post by mikeserv on 2007-11-07
Minh - 

It looks like tar isn't finding the driver packages in there.  Can you see them if you type the command *ls*?  Another thing to try is pressing *ALT+F2* and using the command *gksudo nautilus*.  That will open a root-access level harddrive window.  CAREFUL!  YOU CAN MOVE OR DELETE IMPORTANT FILES WITH THIS.  Navigate to the directory you were just in (*/usr/src/alsa*) and look for the three files that you downloaded.  If they're there, simply double-clicing on them each one at a time will open up a window that you can use for extracting them - just untar them right there in that directory.  But if they're not there, it means that you haven't copied the files there successfully.  Try running a file search for them.

Another option is to try running the set of instructions that iffydonatello pointed us to, but maybe find out more from him about the gstreamer thing he's talking about.  What I know about gstreamer is that it is a compilation of plugins and codecs for audio and video, but that's it.

I've got my fingers crossed for you.

-Mike

---

### Post by mikeserv on 2007-11-07
Minh -

In step 5, are you using this command?
```
sudo cp ~/downloads/alsa* .
```

If so, are the three files you downloaded actually in *~/downloads/*?  (You can check by opening your home folder, and then opening a directory called "*downloads*".  If there is no directory of the sort, or if there is and the files aren't in there, then obviously that command won't work for you.  Well, maybe not obviously.  The command *cp* means copy.  The line *~/downloads/alsa** means "all (that's what the star means - it's a wildcard) files that start with 'alsa' in the directory 'downloads' in user's home directory (the ~ is shorthand for 'home')".  And the "." means current directory, or */usr/src/alsa/*.  So basically that command says: "copy all files that start with alsa from downloads directory in user's home to here."

But, if you read step 4, I warn you to remember the directory that you download those files to (I think the default is the desktop) so that you can modify that command to reflect their real location.

A good rule of thumb is to remember to use the *man* command.  While at a terminal screen, if you're unsure of how a command works try *man (command)* and 9 times out of 10 it will give you a pretty detailed help page, usually including a little tutorial and instructions of how to use a command's modifiers.  For instance, try: *man cp* or *man dpkg*.

-Mike

P.S.  I just bought a Linux book two weeks ago and look at me now!

---

### Post by minhdinh on 2007-11-07
mikeserv thanks to u im past that step and now i am on step 7 of ur guide. after installing everything im trying to do "alsaconf" and i get this 

minh@minh-laptop:/usr/src/alsa/alsa-utils-1.0.9rc4a$ alsaconf
You must be root to use this script.
minh@minh-laptop:/usr/src/alsa/alsa-utils-1.0.9rc4a$ su
Password: 
su: Authentication failure
Sorry.


my password for my account when i log in is ****** and when i type that in it says authentication failure and i dont know wat else to do because thats the only password ive used since i installed ubuntu.

i hope i can get a quick response from u again ur helping me alot and i hope that i dont just give up b4 finishing all ur steps cuz it gets annoying when things go smoothly then something else goes wrong

---

### Post by mikeserv on 2007-11-07
Minh -

Try *sudo alsaconf*.  Ubuntu doesn't really use the *su* command, but substitutes *sudo*.  Basically the difference is this:

*su* assumes the root login, which is a password you don't have because you've never assigned one, because, again, Ubuntu doesn't really use that.  But *sudo* just assigns root, or administrative, powers to authorized users (like the first account you setup, which is probably the account you're using right now) and then takes them away after a specified amount of time (I think the default is 5 minutes, but I'm not sure).

Anyway, that explains why *su* won't accept your password, but I think you'll find that *sudo (command)* will work just fine instead.

-Mike

P.S.  Again, try using the *man* command for those, like *man su* and *man sudo*.

---

### Post by minhdinh on 2007-11-07
ok so now im on step 8 and where it says

/lib/modules/(kernel version)/kernel/sound/pci/hda/

i dont have the folder hda so im not sure wat i should do next

sry to keep bothering u mikeserv but i really want this to work

---

### Post by minhdinh on 2007-11-07
i finally fixed my sound problem!!!! i couldnt continue using ur guide mikeserv because i got stuck and i didnt get a reply back from u but thats ok cuz u got a life n i cant expect u to answer me imediately. so wat i did was i searched around for other acers with sound problems and i found this [http://ubuntuforums.org/showthread.php?t=583920&highlight=acer+sound+problems](http://ubuntuforums.org/showthread.php?t=583920&highlight=acer+sound+problems)

i followed this instruction

grenier! you are genius! =)
about the sound problem. i'll give the exact package names to be installed:
open Synaptic Package Manager, then search packages by the name "backport"
you'll see the list in which just check the "linux-backports-modules".. in the description it's written, that "This package will always depend on the latest generic Linux backported
drivers available." so i think it will automatically upgrade the package when the linux kernel is upgraded.
after installing the package i got the sound working! once again thank you grenier!!!


and now i can use sound:) thanks for trying to help me out best u can, i learned alot from u while trying to fix my sound problem like how to use sudo and make move files n stuff well thanks man

---

### Post by mikeserv on 2007-11-07
Minh -

Ok!  Try and write that down in a step by step so other people can use that - it seems much simpler than that grueling **** that I had to go through.

-Mike

---

### Post by awang44 on 2007-11-07
Mike
 I reloaded the whole thing and just follow your step on #26 posting. it works after step 12 (final reboot). 
The sound works. volume control on keyboard works as well. but the alsamixer volume thing is not starting up. when i run "sudo alsamixer" it just do nothing.
thank you very much!!!

Al

---

### Post by area51 on 2007-11-07
I bought the same exact laptop from Walmart for $348 to. The sound instructions mikeserv wrote were great, the sound was working upon reboot of his instructions. I then found another post in this thread about the wireless and that worked flawlessly the first time after a reboot too. Great thread guys, makes my life much simpler to get another cheap linux box up and running :thumbsup

---

### Post by area51 on 2007-11-07
Just a quick question while on the subject of this notebook (bear in mind I haven't checked into this yet) are we able to get Intel linux GFX drivers that are accelerated for our build in video or do they not offer any accelerated drivers like NVIDIA does?

---

### Post by soleblaze on 2007-11-07
I though the open source intel driver did have acceleration.  If you're wanting to use accelerated desktop effects, it is possible, but when you get them turned on watching a video using the xv driver will freeze your machine.  

In other ACER 5315 problems, does anyone else have the problem with the middle touchpad button making the mouse jump around?  Very hard to paste text when it does that..  anyone know a solution?

---

### Post by monte48lowes on 2007-11-07
soleblaze,

I haven't yet figured out how to get the middle button to work the same as it does in Vista. In Vista it works much like a scroll-wheel for up and down. That doesn't work in xorg. I have solved the problem of the touchy pad though, for both Vista and Kubuntu. Download and install the new BIOS firmware from Acer's website.

[ftp://ftp.support.acer-euro.com/notebook/aspire_5315]("ftp://ftp.support.acer-euro.com/notebook/aspire_5315")

There is a DOS bat file or a windows executable. I ran the firmware update from Vista. I don't have a proper solution to follow if Vista has already been removed from the PC. I will continue to investigate that middle button. Just thought this information would be helpful.

Mike

---

### Post by gcastell on 2007-11-07
> **mikeserv said:**
> Iffy - 

Sweet!  That set of instructions worked?  That looks much easier than all the **** I went through...  Man, I wish I had tried that instead...

G -

I had the same problem.  The first time I installed I was on the verge of getting wireless to work when, in my ignorance, I screwed something up royally (though I can't remember off hand what it was).  So I installed again, and, unlike the first time I installed, I didn't receive any Atheros HAL (the drivers that Ubuntu erroneously tries to use to control our WIFI) messages.  As it turned out, the card wasn't showing up in lspci, either - not even the wrong Atheros AR5006 it tried to install the first time.  After installing ndiswrapper and trying to get it to work, the system still wouldn't recognize my card.

But, as they say, the third time is the charm.  I say this because the third time I installed Ubuntu it did try the HAL drivers and I was able to install ndiswrapper (yes, version 1.49, along with the latest version of net5211.inf), and, this having been my third try, I was experienced enough to keep it running right.

So, while I know my saying "reinstall" sounds like a cop-out, I'm only telling you to do what I did.  The truth is it did seem awfully weird to me that Ubuntu would see my wireless card only some of the time, but that seems to be what happened.

-Mike

Mike,

Thanks for all your help, I was able to make it work, just like you I made a mistake the first time, I thought it didn't work when it did, after some reading I learned that wicd has a problem connecting using WEP, well long story short it seems that after the 3rd reinstall/reboot the card finally kick in and now I am up an running,  I had to configure my network using System -> Administration -> Networking though.

---

### Post by gcastell on 2007-11-07
> **mikeserv said:**
> 
4.  Next we need to get the ALSA packages.  Download the latest versions of [alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/"), [alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/") and [alsa-utils]("ftp://ftp.alsa-project.org/pub/utils/") at their respective links.  (Note, those three file names in the previous sentence are actually links to the download sites.)

-Mike

Mike made an excellent guide I just want to point out a stupid error I made while following his instructions, I went all the way down on the file list and I thought the latest version was 1.0.9 and it is not, the latest version is alsa-driver-1.0.15.tar.bz2 which is in the middle of the list, I'd recommend you get it from the [alsa website]("http://www.alsa-project.org/"), once I got the latest version it worked perfectly.

---

### Post by mikeserv on 2007-11-07
Area51 -

I second soleblaze on that comment about the video driver.  I outlined how I got desktop effects working in post #19 of this thread.  It also talks about how to disable the xv driver for video watching.  Of course, I think it only disables them for *gstreamer* set of codecs (which is what Ubuntu will install by default when you try to watch a video) so I'm not totally sure what would happen if you were using a different setup.

I can say that I've watched DVDs, DIVX files, and flash videos (to mention a few) with active desktop effects and I have not experienced any problems.

Krikit also discusses how he got desktop effects enabled in this thread (using a different method), and, though I can't speak as to his video watching, I assume he would have mentioned it if there were a problem.

-Mike

---

### Post by The_Great_Beast on 2007-11-08
> **iffydonatello said:**
> Thanks everyone for all your help. After trying and trying and...well you get it, I wasn't able to get the sound to work. I did everything you told me to Mike. After doing all that, I got the Gstreamer message when trying to use the volume controller. I decided to see if there were anything else out there about the sound card in this laptop and I found this post:

[yep this one]("http://ubuntuforums.org/showthread.php?t=543793&highlight=gstreamer&page=2")

And it it worked right away! Anyway thanks for all the help the last few days of struggle. I learned a ton about ubuntu, because of this problem. And to think I was about to reinstall Vista! Thanks again all

Nothing else worked, I tried this and it worked great thanks :)

---

### Post by area51 on 2007-11-08
Has anyone tried a BIOS update via USB thumb drive? Technically this should work fine if you download the driver posted above and install DOS on it I would think. I guess I'll give it a shot since I don't have anything to do with Vista on this machine anymore - I'm talking of booting from the USB drive into DOS mode.

---

### Post by MarttiTheFinn on 2007-11-08
Hi Ubuntu Aspire folks,

I also got the Aspire 5315 and Gutsy is now working (typical ndiswrapper and alsa tweaking made them to work, thanks for people in this thread, very helpful info).

Now, the remaining problem is a bad showstopper..noth suspend and hibernate do not work..in both cases ubuntu never wakes up..the display remains black. Aspire tries to wake up (led on, bit of hd activity..then nothing). After reboot, works again.

I've set the extra eye candy on with compiz and not tested w/o it.

Anyone knows a solution?

Secondly, with Vista the machine stayed quite cool, with Ubuntu even idling..warmer air flows out..

Thanks in advance

Martti

---

### Post by area51 on 2007-11-08
Is the internal Intel GFX card capable of playing some open gl games? I realize not the newest stuff but quake 3 arena etc in open gl mode?

---

### Post by samtr on 2007-11-08
Has anybody experienced any overheating issues, especially while running on the battery? I tired running it on the battery three times and for all of those times after about ~35 minutes the computer just shuts off and I feel the bottom where the fan is and it is hot. I'm a little concerned that Ubuntu isn't managing the fan speeds right. People who have Vista said they haven't experienced this problem.

---

### Post by area51 on 2007-11-08
I've been running ubuntu on it for 48-72 hours straight and while it is a little warm at times I havent noticed any significant difference in temp over when Vista was on it.

---

### Post by monte48lowes on 2007-11-08
I have had it shutdown a couple of times on high temperature. However, after noting the fan suction being on the bottom, I have kept it on a hard surface to allow air to circulate. I have not had a problem since. I also invested $20 on a laptop pad that comes with internal fans to help keep things cool.

Still no luck on getting the center button for the glidepoint touch pad. Any help?

Mike

---

### Post by mcauley on 2007-11-08
I have been having problems with mine shutting down after about 40 min. The fan is not running during this time. Takes several min to cool off and reboot. Other times the fan runs continuously and I don't get the shutdown problem. Any of you dual boot users having this issue in Windows?
Scott.

---

### Post by monte48lowes on 2007-11-08
I don't have the over heat issues while running Vista. But I haven't had them running Gutsy for several days either. I did install lm-sensors and am running SuperKaramba with a monitor applet to keep an eye on the CPU temperature. It has stayed 45 - 50 C.

Mike

---

### Post by mikeserv on 2007-11-08
I don't have overheating issues either, and I only run Gutsy.  Mike - what is lm-sensors and how do I go about setting it up?

-Mike

---

### Post by monte48lowes on 2007-11-08
lm-sensors:

"Lm-sensors is a hardware health monitoring package for Linux. It allows you to access information from temperature, voltage, and fan speed sensors. It works with most newer systems.
This package contains programs to help you set up and read data from lm-sensors.
Homepage: [http://www.lm-sensors.org]("http://www.lm-sensors.org")

It is available from the repositories. 

Try this command before you install lm-sensors. If this works you don't need to install the lm-sensors:

cat /proc/acpi/thermal_zone/TZ01/temperature

If you get "temperature: 45 C" or something like that you are good. If not, install lm-sensors. I am running superkaramba with kornermonitor available from kde-look.org. I have made some changes to work for me.

[IMG]http://www.geocities.com/monte48lowes/mydesk1.jpg[/IMG] 

If you want the basic one as I have shown there let me know. I can send it to you.

I have the center button for the mouse working. However, now the vertical scrolling has stopped responding. I added "i8042.nomux" to the end of the kernel line in /boot/grub/menu.lst. Now the buttons work, however vertical scrolling does not.

Mike

---

### Post by monte48lowes on 2007-11-08
Results from some more testing regarding the kernel parameter i8042.nomux. 

I rebooted with i8042.nomux added. Once the desktop was up an running I tried using the 4-way button. This time it did the same thing it is doing for everybody: Up - scroll down (mouse button 5), Left - middle click (mouse button 2), right - ??, down - ??. I started up konsole and ran 'xev' to see what the inputs were. After a few tries clicking around in the xev box everything started working correctly. Up - scroll up (mouse button 4), Down - scroll down (mouse button 5), Left or Right - middle click (mouse button 2). And again the vertical scroll is not working for me any longer.

I next commented out the i8042.numux from menu.lst and restarted. This time no matter how much I played with xev I could not get the buttons be recognized correctly. Any ideas? I am thinking it might be better to just not use the 4-way button at this point. 

Mike

---

### Post by mikeserv on 2007-11-09
This is what I get in response to your suggested command: ```
m******@ubuntu:~$ cat /proc/acpi/thermal_zone/TZ01/temperature
cat: /proc/acpi/thermal_zone/TZ01/temperature: No such file or directory
```

-Mike

---

### Post by samtr on 2007-11-09
> **mikeserv said:**
> This is what I get in response to your suggested command: ```
m******@ubuntu:~$ cat /proc/acpi/thermal_zone/TZ01/temperature
cat: /proc/acpi/thermal_zone/TZ01/temperature: No such file or directory
```

-Mike

Strange, it works for me.

---

### Post by monte48lowes on 2007-11-09
Mike,

That's the same result I get from my desktop. Let me retrace my steps exactly to determine what I did to get that working. I believe it centered around installing lm-sensors. If I find enough free time I will reinstall and work it from the beginning. I use adept for installing packages and can do a search for all packages containing "sensors". I will post a list of which packages I have installed in addtion to lm-sensors, when I get home later today.

Mike

---

### Post by area51 on 2007-11-09
Has anyone had any luck updating the BIOS firmware if theres no Windows installed?

---

### Post by monte48lowes on 2007-11-09
Here are the 'sensor' packages I have installed:

lm-sensors
libsensors3

That should be what you need to monitor the CPU temp.

As for getting a DOS bootable CD-Rom to update the BIOS... there are many bootable cds available, or possibly use a usb drive.

Mike

---

### Post by area51 on 2007-11-11
I got the BIOS fully updated with no Windows on the machine.

I happened to have a Windows 98 cd, I booted it up to command prompt with cd access.

I burned on a seperate the 1.19 bios update (unzipped) from:

[ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/](ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/)

There's a seperate file in it called CLxXxX.zip that I unzipped and used. Put the cd in the drive, did a D: to access it

then ran the IF50.bat which uses flashit (included) to update the bios, worked great. I'm now using 1.19 and things seem smoother.

---

### Post by khowe on 2007-11-11
Can someone help get the touchpad working correctly?  I have been looking at a similar solution for a different model acer @ [http://ubuntuforums.org/showthread.php?t=517156]("http://ubuntuforums.org/showthread.php?t=517156")

The cat /proc/bus/input/devices is not the same as the 5315-2153 that this thread is about.

Does anyone know how to decipher this fix and apply it?

My double-tap does not work correctly to move windows.

Thanks for the info.

---

### Post by area51 on 2007-11-12
I'm running 7.10 with a relatively clean configuration, I installed the system just a few days after I bought it when Vista was driving me nuts. I didn't have to do anything special to get the touchpad working correctly, the Ubuntu installer pretty much took care of things in that regard. The double tap works fine, I did install the BIOS update which makes the touchpad movement more smooth.

---

### Post by monte48lowes on 2007-11-14
Unfortunately, I do not like the tapping thing. As such I have tapping disabled. Since this touchpad is not a true synaptics touch pad there are some things about it that don't play well. Do you have qsynaptics or ksynaptics installed? I am running kubuntu with ksynaptics to disable tapping. One of these might work for you.

Mike

---

### Post by gcastell on 2007-11-15
> **area51 said:**
> I got the BIOS fully updated with no Windows on the machine.

I happened to have a Windows 98 cd, I booted it up to command prompt with cd access.

I burned on a seperate the 1.19 bios update (unzipped) from:

[ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/](ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/)

There's a seperate file in it called CLxXxX.zip that I unzipped and used. Put the cd in the drive, did a D: to access it

then ran the IF50.bat which uses flashit (included) to update the bios, worked great. I'm now using 1.19 and things seem smoother.

Has anyone tried this ROM update on the aspire 5315-2153? I am a little bit hesitant to update it since this is for the European version.

---

### Post by Malekish on 2007-11-15
Sadly for work reasons I need to keep Windoze on my laptop so I have it dual-booting between Feisty and Vista Basic Home.  I downloaded the BIOS patch listed above and ran it inside Vista sucessfully.

The touchpad (and everything else) is working perfectly, it is much less jumpy now, before it was nearly unusable in Ubuntu due to the sensativity of the touchpad (my thumb even brushing the pad would register as a click)

---

### Post by Arnitak on 2007-11-16
What actually is the brand of the touchpad? I have those Aspire 5315, european version. The problem is, it is moving SLOW and I really need to hurt my fingers in order to reach the end of the screen with the cursor. I increased sensitivity from the mouseoptions but it does not react at all. Also, how can I use my scroll button, and my dead keys, like the window key should bring the startmenu and the options the equivalent of a right click.

Also ... what is my version of the audio? It does not work at all under Ubuntu 7.10!

---

### Post by soleblaze on 2007-11-16
> **Arnitak said:**
> What actually is the brand of the touchpad? I have those Aspire 5315, european version. The problem is, it is moving SLOW and I really need to hurt my fingers in order to reach the end of the screen with the cursor. I increased sensitivity from the mouseoptions but it does not react at all. Also, how can I use my scroll button, and my dead keys, like the window key should bring the startmenu and the options the equivalent of a right click.

Also ... what is my version of the audio? It does not work at all under Ubuntu 7.10!

How to fix the sound is listed in the first few pages of this thread.  It requires compiling a newer version of alsa yourself and installing a few modules.  Also adding an option to your modules conf file.

Also the scroll button doesn't currently work, and the windows key isn't dead, it's just not programed to open the applications window.  I'm not sure how to do this, as I've never needed to use it that way.

With regards to trackpad speed, I added these three lines to my /etc/X11/xorg.conf file under the Section "Input Device" with the identifier "synaptics touchpad":

```

Option           "MinSpeed"                "0.80"
Option           "MaxSpeed"                "1.00"
Option           "AccelFactor"             "0.0010"

```

This speed may or may not be too fast for you (It will go the entire length of the screen with one swipe) if so, you can tweak the Min and Max speed numbers to get it more to your liking.  Note:  You will have to restart X (ctrl-alt-backspace) everytime you save your changes for them to have an effect.

---

### Post by monte48lowes on 2007-11-21
I did get the scroll button to work. Although when it works the vertical scrolling stops responding. I am ingnoring the scroll button for now. The windows key is often listed as the <Super> key for some actions. For example: <Super>+e will perform expose in compiz. It can be mapped to other actions, however this would result in many current actions losing their normal shortcuts.

Mike

---

### Post by JonathanSteenbrugge on 2007-11-27
To enable the windows key, there is a simple solution. go to system, than to preferences and then there should be a link to a program dealing with shortcut keys. there program the "super" key the way you like. For me it brings up a terminal window.

---

### Post by gcastell on 2007-11-29
Anyone has a problem of low volume on the laptop?, sometimes is hard for me to listen to youtube videos or other applications because the volume is so low.

> **mikeserv said:**
> Ok, I'm gonna write my own little sound how-to here, since, as I've said, I really used two threads put together to get my sound working.  These can be found [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and [here]("http://ubuntuforums.org/showthread.php?t=584890&highlight=ar5007eg").  (Actually, it was three, if you count the first step, but I don't remember where I got that info - it just seemed to make sense when I read, though I have no idea what it actually does)

**Enabling Sound**

1.  Press *ALT+F2* and run the command *gksudo gedit /boot/grub/menu.lst*  Warning: be careful what you do with this file, as this is the file that tells your computer where on the harddrive to find Linux (and Windows, if you dual-boot).

Ok, now find the line that says: *### END DEBIAN AUTOMAGIC KERNELS LIST* and, immediately under it, add these two lines: ```
# default boot parameters, set pci=routeirq for sound to work (as per dmesg output)
kopt=pci=routeirq 
```

Save and exit.

2.  We're about to start downloading, compiling, and installing a new version of ALSA, but, before we do, we need to stop any ALSA processes that might be currently running.

Open a terminal window and enter these commands: ```
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsasound stop
```

3.  Now, again before we download and install, let's make sure that we have all of the packages required for compilation and install. ```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install libncurses5-dev
```

4.  Next we need to get the ALSA packages.  Download the latest versions of [alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/"), [alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/") and [alsa-utils]("ftp://ftp.alsa-project.org/pub/utils/") at their respective links.  (Note, those three file names in the previous sentence are actually links to the download sites.)

Be sure you remember what your save location was (the directory that those three files were downloaded to) because that path will be in a command in the next step.  The command will say *sudo cp ~/downloads/alsa* .* but what it really means is *sudo cp (directory that you saved those three files to)/alsa* .*  For instance, if you saved those three files to your desktop, the code would be ```
sudo cp ~/Desktop/alsa* .
```

5.  Now that we have the driver packages, we're almost ready to install them.  But first, let's create a separate directory to install them from and then unpack them.  ```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```

6.  With the files unpacked and setup, we're ready to compile and install.  First, we'll do the alsa-driver package: ```
cd alsa-d*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```  And next the alsa-lib packages: ```
cd ../alsa-l*
sudo ./configure
sudo make
sudo make install
```  And finally the alsa-utils package, (pay special attention to this one, I ran into errors because I didn't have the proper curses libraries installed): ```
cd ../alsa-u*
sudo ./configure
sudo make
sudo make install
```

7.  Now run the initial ALSA setup program: ```
sudo alsaconf
```

Edit: I added *sudo* in there because apparently that script requires root access.  Thanks to [minhdinh]("http://ubuntuforums.org/member.php?u=424140") for pointing that out.

8.  Ok, here's where some stuff really starts to get interesting.  I did a lot of copying at this point, and, again, while I'm not sure how necessary it is, I know it's what I did and how I got things to work.  

Press *ALT+F2* and run *gksudo nautilus*.  Warning:  what you've just done is open a root-enabled browser window for your harddrive.  It is entirely possible to delete or move very important files with this access.  Be careful.

Ok, now we're going to do some file copying.  Navigate to */lib/modules/(kernel version)/kernel/sound/pci/hda/* and copy the file *snd-hda-intel.ko* to the directory */lib/modules/(kernel version)/ubuntu/media/snd-hda-intel/*.  Next navigate to */usr/src/alsa/alsa-driver*/modules* and find these 13 files: ```
snd-hda-intel.ko
snd-hwdep.ko
snd-mixer-oss.ko
snd-page-alloc.ko
snd-pcm-oss.ko
snd-rtctimer.ko
snd-seq-device.ko
snd-seq-midi-event.ko
snd-seq-midi.ko
snd-seq-oss.ko
snd-seq.ko
snd-timer.ko
snd.ko
```  Copy them all to */lib/modules/(kernel version)/kernel/sound/*.

Run: ```
sudo depmod -a
```

9.  Ok, now we'll start ALSA back up: ```
sudo /etc/init.d/alsa-utils start
sudo /etc/init.d/alsasound start
```

10:  Run: ```
sudo alsamixer
```  Unmute all of the channels and set your volume.

11.  We're just about done, but first we're going to manually input our model.  Press *ALT+F2* and enter the command *gksudo gedit /etc/modprobe.d/alsa-base*.  Warning: we've just given ourselves root access to an important sound configuration file.  We must be careful here.

Scroll to the bottom of the file and enter this line: ```
options snd-hda-intel model=acer
```  Save and exit.

12.  Reboot.  It was at this point that my sound started working.  I knew it when I heard the Ubuntu drums at startup.  Hopefully it works for you, too.

-Mike

---

### Post by mikeserv on 2007-11-29
Yeah, the volume sucks because the speakers suck.  That's as much as they can do.

-Mike

---

### Post by gcastell on 2007-11-30
Oh well, can we ask for 348 dollars right? by the way, Mike did you upgrade your BIOS? I am hesitant to upgrade since the upgrade is for the European model.

---

### Post by monte48lowes on 2007-11-30
I upgraded the BIOS to 1.19. It definately helped the touchpad sensitivity.

Mike

---

### Post by mikeserv on 2007-11-30
I haven't upgraded - but then again, I haven't noticed any touchpad issues.  I can scroll with the right side of the pad and the cursor moves to where I point it.  I have noticed that pressing the middle button makes the cursor jump, though I never use the middle button anyway.  Does the BIOS upgrade fix the middle button thing?  What does the middle button do, anyway?

-Mike

---

### Post by monte48lowes on 2007-11-30
The middle button is used as a scroll-type pointer. Viewing a webpage it scrolls the page up and down. It can also scroll the page sideways to the left and right (or go forward and back in the history). I found it useful in windows, since the touchpad scrolling can be touchy there as well. I was able to get the touchpad to perform the same operations, however I lost the vertical scrolling. I decided I liked vertical scrolling better....

Without any system changes it should work as a middle click (push button left) and downward scroll (push button up). Pushing the button in the other two directions is currenlty undefined as noted by the cursor jumping all over the place.

Mike

---

### Post by monte48lowes on 2007-11-30
OK,

I just completed a reinstall. I did a dumb thing yesterday. I installed the acer-acpi package from the repos. It broke my ndiswrapper installation somehow... I was unable to get ndiswrapper working properly... so... I have reinstalled. I have everything written down. I will get it written nicely so I can post it here, along with some proofreading for errors.

First things first:

I backed up my /home directory to my desktop using rsync over ssh. When I reinstalled I restored my /home directory back to the laptop so I did not have to configure anything extra to get compiz to work. Also, I didn't lose any of my configuration files. :D

I will try to get this posted by the end of the weekend.

Mike

---

### Post by monte48lowes on 2007-11-30
Here is the step by step instructions for how I installed kubuntu gutsy 7.10 on my Acer Aspire 5315-2135.

Notes:

Since this is a reinstall I had previously backed up my /home directory to my desktop. For that reason I did not have to reconfigure some options in my /home directory, such as the compiz fix listed earlier in another post. [There are many websites with directions on using rsync and ssh to get this done. I do not have it set up to perform automatic backups (yet).] 

I have already installed the bios update 1.19 running Windows Vista, this fixes the erratic operation of the touchpad:

[ftp://ftp.support.acer-euro.com/notebook/aspire_5315]("ftp://ftp.support.acer-euro.com/notebook/aspire_5315")

You can skip to Section A - D if you have already installed Gutsy.

[SIZE="3"][B]Contents:

A. Setup partitions to prepare for install*
B. Start install*
C. Complete install and reboot*
D. Update system
E. Setup Wireless
F. Setup Sound
G. Touchpad Setup
H. Setup Compiz[/B][/SIZE]

*** CAUTION:** These steps will REMOVE VISTA. Please do not follow them if you wish to keep Vista installed on your computer. I have left the restore partition intact, just in case I need to restore vista later.  

References:

[http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg]("http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg")
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
[http://ubuntuforums.org/showthread.php?t=600714]("http://ubuntuforums.org/showthread.php?t=600714")



Boot into a live session of kubuntu 32-bit.

[SIZE="3"]**A. Setup partitions to prepare for install**[/SIZE]

**1**     Open konsole (terminal) and install gparted

```
sudo apt-get install gparted
```

**2**     Run gparted and remove the second partition 'sda2'

**3**     Add new partition at the beginning of the available space
**3.1**    Set size to 2000MB (installed RAM x2) 
**3.2**   Format as 'swap'

**4**     Add new partition to fill remaining space
**4.1**   Format as 'ext3'

**5**      Format last partition 'sda4' as 'ext3'

**6**      Commit changes and close gparted

[SIZE="3"]**B. Start install**[/SIZE] 

**1**      Select 'Manual' partitioning
**2**      Edit sda3
**2.1**    Format as 'ext3'
**2.2**    Mount as '/'
**3**      Edit sda4
**3.1**    Format as 'ext3'
**3.2**    Mount as '/home'

[SIZE="3"]**C. Complete install and reboot** [/SIZE]

[SIZE="3"]**D. Update system**[/SIZE]

**1**      Open Adept Manager 
**2**      Fetch Updates
**3**      Full Upgrade
**4**      Apply Changes

#Here I installed 'ssh' and logged out. I then restored my /home directory from my desktop using rsync

[SIZE="3"]**E. Setup Wireless**[/SIZE]

**1**      Install ndiswrapper

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

**2**      Remove restricted driver for Atheros card
**2.1**    Open kcontrol>System Administration>Restricted Drivers
**2.2**    Select 'Administrator Mode' and deselect the ath driver
**2.3**    Select 'OK'

**3**      Install wireless driver

**3.1**   Download driver

```
wget http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz
```

**3.2**    Extract driver

```
tar xzf ar5007eg-32-0.2.tar-gz
```

**3.3**    Moved



**3.4**    Blacklist the ath_pci driver

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

**3.5**    Restart system

**3.6**    Install driver

```
cd ar5007eg-32-0.2/ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```

**3.7**    Load module

```
sudo modprobe ndiswrapper
```

At this point I was able to use wireless!

**3.8**    Add ndiswrapper to load on start

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

[SIZE="3"]**F. Setup Sound**[/SIZE]

**1**      Download alsa-drvers, alsa-lib & alsa-utils

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2
```

**2**      Install required tools

```
sudo apt-get install libncurses5-dev gettext
```
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

**3**      Make source directory and copy alsa files to it

```
sudo mkdir /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```

**4**      Stop alsa

```
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsasound stop
```

**5**      Compile alsa-driver

```
cd alsa-dr*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

**6**      Compile alsa-libs

```
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
```

**7**      Compile alsa-utils

```
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```

**8**      Restart system

**9**      Add acer to module version

```
sudo nano /etc/modprobe.d/alsa-base
```

Add this to the end and save:

```
options snd-hda-intel model=acer
```

**10**     Run alsaconf

```
sudo alsaconf
```

**11**     Copy drivers to correct folder

```
sudo cp /lib/modules/2.6*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6*/ubuntu/media/snd-hda-intel/
```

and

```
sudo cp -r /usr/src/alsa/alsa-driver-1.0.15/modules/* /lib/modules/2.6*/kernel/sound/
```

**12**     Load alsa-driver

```
sudo depmod -a
```

**13**     Restart alsa

```
sudo /etc/init.d/alsa-utils start
sudo /etc/init.d/alsasound start
```

**14**     Restart system

[SIZE="3"]**G. Touchpad Setup**[/SIZE]

**1**      Edit xorg.conf

**1.1**    Backup xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

**1.2**    Edit xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

**1.3**    Add the three lines at the end:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
        Option          "HorizScrollDelta"      "0"
EndSection

```

**2**     Save and exit
**3**     Logout and restart X with 'CTRL-ALT-Backspace'

[SIZE="3"]**H. Setup Compiz**[/SIZE]

**1**     Install compiz and emerald

```
sudo apt-get install compiz emerald
```

**2**     Configure compiz to work with blacklisted Intel driver

```
sudo mkdir ~/.config/compiz
sudo touch ~/.config/compiz/compiz-manager
echo "SKIP_CHECKS=yes" | sudo tee -a ~/.config/compiz/compiz-manager
```

**3**     Whichever video player you use must be set to use the 'X11' driver instead of the 'xv' driver. Compiz does not play well with the xv driver, which is one of the reasons the Intel driver was blacklisted. X11 works well here.

Thanks to the following for providing what is here, or at least providing directions to it:

ubuntuforums
    [INDENT]mikeserv
    KriKit[/INDENT]

---

### Post by DemonBob on 2007-12-03
Madwifi Patch  for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work. 

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315. 

lsmod | grep ath output

```

ath_rate_sample        15232  1 
ath_pci               114600  0 
wlan                  211376  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280544  3 ath_rate_sample,ath_pci

```

dmesg output

```

[   15.652000] ath_hal: module license 'Proprietary' taints kernel.
[   15.652000] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[   15.728000] wlan: 0.8.4.2 (svn r2756)
[   15.760000] ath_pci: 0.9.4.5 (svn r2756)
[   15.760000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   15.760000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   16.248000] ath_pci: switching rfkill capability off
[   16.324000] ath_rate_sample: 1.2 (svn r2756)
[   16.324000] ath_pci: switching per-packet transmit power control off
[   16.324000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   16.324000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   16.324000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   16.324000] wifi0: mac 14.2 phy 7.0 radio 10.2
[   16.324000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   16.324000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   16.324000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   16.324000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   16.324000] wifi0: Use hw queue 8 for CAB traffic
[   16.324000] wifi0: Use hw queue 9 for beacons
[   16.344000] wifi0: Atheros 5424/2424: mem=0x54100000, irq=19

```

---

### Post by kameleon25 on 2007-12-03
> **DemonBob said:**
> Madwifi Patch  for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work. 

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315. 

lsmod | grep ath output

```

ath_rate_sample        15232  1 
ath_pci               114600  0 
wlan                  211376  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280544  3 ath_rate_sample,ath_pci

```

dmesg output

```

[   15.652000] ath_hal: module license 'Proprietary' taints kernel.
[   15.652000] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[   15.728000] wlan: 0.8.4.2 (svn r2756)
[   15.760000] ath_pci: 0.9.4.5 (svn r2756)
[   15.760000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   15.760000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   16.248000] ath_pci: switching rfkill capability off
[   16.324000] ath_rate_sample: 1.2 (svn r2756)
[   16.324000] ath_pci: switching per-packet transmit power control off
[   16.324000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   16.324000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   16.324000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   16.324000] wifi0: mac 14.2 phy 7.0 radio 10.2
[   16.324000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   16.324000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   16.324000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   16.324000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   16.324000] wifi0: Use hw queue 8 for CAB traffic
[   16.324000] wifi0: Use hw queue 9 for beacons
[   16.344000] wifi0: Atheros 5424/2424: mem=0x54100000, irq=19

```

Now this is what I was waiting for. Since this is a madwifi driver that means it should be compatible with the security software that is compatible with madwifi, correct?

---

### Post by DemonBob on 2007-12-04
As far as the security i have no way to test at the moment since my router is not saving my settings for WPA or WEP, but it does connect. 

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1B:38:63:67:7C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2721 (2.6 KB)  TX bytes:8914 (8.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-1D-D9-4B-2E-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26346 errors:0 dropped:0 overruns:0 frame:104
          TX packets:10885 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8586087 (8.1 MB)  TX bytes:1710239 (1.6 MB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr 00:1D:D9:4B:2E:DB  
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe4b:2edb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7056631 (6.7 MB)  TX bytes:1462337 (1.3 MB)

```

iwlist scan output

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:3F:93:B1
                    ESSID:"DLinkVWR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=72/70  Signal level=-23 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100



```

I am posting from the connection at the moment.

---

### Post by bboypoprocks on 2007-12-25
i followed the directions from the link above to solve my sound problem and got cut short

poprocks@poprocks-laptop:~$ sudo apt-get install build-essential ncurses-dev gettext 
[sudo] password for poprocks:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ncurses-dev

i've tried multiple other sound "remedies" and always recieve the same feedback, packages missing. whats up with that? where could i find them?

also tryed
E: Couldn't find package libncurses5-dev

---

### Post by mikeserv on 2007-12-27
bobby:

I think you need to make sure that you have all of your sources checked.  If you're using Gutsy (which you should be) go to *System > Administration > Software Sources* and check all boxes, especially "Source Code."

Everyone:

I lost my sound today.  I received an update that included "linux-headers-yadayadayada" after which I had to restart.  Upon restart, I realized that my volume icon was back to the "Mute" position and when I tried to unmute it I received the old "No sound card" message.  So I went through monte's instructions above (post #101) in Section F and only had to make it to the first restart before I heard the Ubuntu drums.

-Mike

---

### Post by bboypoprocks on 2007-12-28
thanks mike. i reinstalled ubuntu and checked everything for my sources. the instructions worked great. thanks everyone.

---

### Post by monte48lowes on 2008-01-01
I am glad that I am not the only one who finds this post useful. I have used it several times since I posted it weeks ago. Mostly just for fun and the occasional update breaking the self-compiled packages. I have made some changes and am looking at a couple others. I might post this on my blog as well, that will give me something to put there ;) 

Mike

---

### Post by JimTDI on 2008-01-01
This thread is awesome!  Thanks to the instructions from monte48lowes (worked perfectly!!) I got my wireless working, my sound, Compiz, and am enjoying my cheap ($350) Wal*Mart Acer 5315 so much now!  Very happy to ditch Vista!!

I even found a 2GB ram upgrade (online) at Crucial, went to Best Buy last night and asked them if they'd match the price, and they did.  So now my Acer 5315 Gemstone has 2GB of RAM (for $52 total) and works so well thanks to everyones help in this thread!

I can't say I see what the touchpad instructions did - my touchpad seems to work about the same (never thought it had a problem) but I had done the bios upgrade a few weeks ago.

So far - no problems with overheating on mine (knock on wood) and had it 2 months.  This laptop was worth standing in line for 2 hours to grab.

---

### Post by mikeserv on 2008-01-02
The touchpad instructions - for me - enabled the use of the middle scroll button.  Before reading through this thread I had no idea what that button was even for, and was less than interested in investigating.  But, after reading some of these other guys talk about it, I decided to give the xorg edit a try, and, to my surprise, I can use the middle button to scroll up and down!  Of course, before the edit, I was able to do it with the right side of the touchpad, but I think I like the button better.

-Mike

---

### Post by OldAlgis on 2008-01-04
I bought an Acer Aspire 5315 in Australia in the after Christmas sales in Canberra where I live. It has Vista Home Basic edition.  Enough said...  I have been a SUSE user for a few years now, but consider myself a newbie in Linux.  As I hardly have any need of any variety of M$Win, I want to install Linux on the laptop, at first in a dual boot fashion.  With another newish PC (AMD 64 duo processor--when neither the latest SUSE nor anything else worked, I found great fun in using kubuntu 7.04, which buzzed along just fine. 

 I have a live CD version of kubuntu 7.10.  I hear sad tales about its installation stopping in the middle at about 70% done point.  The live CD of the "Gutsy" works fine on the new laptop (I have no ide if it is "Gemstone" as the label just says "Acer Aspire 5315".  When you guys installed the "Gutsy", did you have to create a space for it, or were you able to leave all that to the Gutsy installation routine, particularly when installing from a live CD?

It is a very basic question, but I want to be careful.  Perhaps it is my age - I am 2 months of 83 - yes, 83 year old newbie!  :-).

Thanks in anticipation,

OldAl,

Downunder.

---

### Post by mikeserv on 2008-01-04
OldAl:

I'm pretty sure you have the same laptop as me; I haven't any reference to "Gemstone" on mine either.

For your installation I would suggest using a different guide (I found [this one]("http://www.psychocats.net/ubuntu/installing") with just a few clicks through google), one tailor-made to the dual boot situation.  From there, come back to this thread and go through all of the setup prcoedures (see monte48lowes rather long - and extremely detailed and informative set of instructions, post #101 I believe) and see where that gets you.  

I think you'll find that if you're able to get everything working properly, Ubuntu is an extremely intuitive computer interface.  I hope you like it.

-Mike

---

### Post by OldAlgis on 2008-01-04
> **mikeserv said:**
> OldAl:

I'm pretty sure you have the same laptop as me; I haven't any reference to "Gemstone" on mine either.

For your installation I would suggest using a different guide (I found [this one]("http://www.psychocats.net/ubuntu/installing") with just a few clicks through google), one tailor-made to the dual boot situation. 
[...]
I think you'll find that if you're able to get everything working properly, Ubuntu is an extremely intuitive computer interface.  I hope you like it.

-Mike

Mike,

Thanks a lot for that info - I will follow it up for sure.  I did download "Acronis" (with 15 day free trial), which is a Win compatible cloning tool, so I should be able to clone the disk.Also I made the dvd backups of the factory default disks, so I should be reasonably covered against any foolishness on my part.  

I really do like kubuntu/ubuntu and have stuck to SUSE only because the Linux SIG I frequent is mainly for SUSE users.  I am sure that your advice will serve me well!

Kind regards,

---

### Post by JimTDI on 2008-01-05
> **mikeserv said:**
> The touchpad instructions - for me - enabled the use of the middle scroll button.  Before reading through this thread I had no idea what that button was even for, and was less than interested in investigating.  But, after reading some of these other guys talk about it, I decided to give the xorg edit a try, and, to my surprise, I can use the middle button to scroll up and down!  Of course, before the edit, I was able to do it with the right side of the touchpad, but I think I like the button better.

-Mike

Mike - OK I understand now what the touchpad fix is supposed to do.  It appears my center button does something now, but it does not allow me to scroll up/down a page.  It seems like it scrolls up 1 time, then does nothing.  But from reading your post I learned about using the right side of the touchpad to scroll, and that works well.  Thanks for your response, and tip!

---

### Post by monte48lowes on 2008-01-08
OldAlgis,

I initially installed kubuntu with vista dual-boot. I used the 'D: drive' partition to install kubuntu. I was then able to dual boot with vista. PM me if you need help with getting that accomplished. After the basic install you should be able to complete the remaining instructions for getting everything setup.

Mike


JimTDI,

I got the scroll button working by playing around with 'xev'. I was not able to get it to work from a fresh boot without going through the 'xev' dance. Personally I prefer the vertical scrolling on the side rather than the button. Again, just personal preference.

Mike

---

### Post by RossPaul on 2008-01-14
Hi Old Al,

I also bought a Acer 5315 after Christmas I live in Sydney. I haven't had a chance to use it much yet, but I was wondering how you found vista was working with only 512mg. I'm thinking ahead that it maybe be necessary to find a windows OS that is a little less thirsty on the RAM. What do you think.

Regards

Ross

---

### Post by hervflo on 2008-01-17
Hi Everyone,

I tried to configure the alsa driver on my Laptop. But i receive this reply:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Can someone give me a help on how i should proceed now?

Thanks.

---

### Post by hervflo on 2008-01-17
Hi yeah!!!

It's working.:guitar:
What is with the issue of desktop effects?:confused:
I am excited to get something new from u guys.

bye.

---

### Post by mikeserv on 2008-01-17
What issue are you having with desktop effects?  Check monte48lowes's post #101 in this thread.  I believe he addresses desktop effects there.

-Mike

---

### Post by csim on 2008-02-10
hi,

regarding shutdown / overheating, please have a look here:
[http://ubuntuforums.org/showthread.php?p=4305576](http://ubuntuforums.org/showthread.php?p=4305576)

---

### Post by kikke on 2008-02-23
Doesn't work. 
Maybe after 1-2 years this problem is changing in Launchpad to confirmed. 
It's my experience. I'll use Windows XP instead.

---

### Post by mikeserv on 2008-02-23
What doesn't work?  If you're saying that Ubuntu doesn't work on the Acer 5315 then I can assure you that you are mistaken.  I'm also fairly certain that, with effort, you can get it up and running on just about anything.  But, if you like, Windows XP is good, too: just kind of a memory hog.

-Mike

---

### Post by imclumzy on 2008-02-26
I just wanted to pipe up and say thanks to Mike and all who contributed to this thread.  I bought an Aspire 5315-2442 on the weekend and turfed Vista without even booting up to it.  Here's my experience.

I do need WinXP for some legacy device compatibility stuff so I installed TinyXP in a small partition.  Following the instructions in this thread I have successfully installed Gutsy and have sound and wifi working well.  The touchpad is a bit sensitive and the middle button doesn't click but I haven't tweaked xorg.conf yet so I'll have to do that today and see what happens.  The laptop came with firmware 1.21 on it and I updated to 1.25 using my XP partition.  And it still seems very sensitive with the "tap-click".  I'll update to 1.29 tonight and see if that fixes anything.

Anyway, I just wanted to say thanks!  I based my decision of buying on this thread and the WinXP install thread here [http://soulpass.com/2007/11/10/installing-windows-xp-professional-sp2-on-acer-aspire-5315-2153-laptop/#comment-20200](http://soulpass.com/2007/11/10/installing-windows-xp-professional-sp2-on-acer-aspire-5315-2153-laptop/#comment-20200)

---

### Post by Delicatessen on 2008-03-03
Hello,

As everyone else, I also had problems with the sound when installed Ubuntu on my pc. Then, thanks to the instructions above, I could install the sound. However, a couple of days ago, I did un update and the sound was not working again. then I went through the instructions, and after the first restart, the sound was working. then I went on and when I restarted my pc again, it didn't work.....

So since then I went through the instruction a number of times without any positive results....

when I click on the sound icon in the top right corner, it says that either my soundcard is not installed or it can not find a perifery or "greffon de GStreamer" (sorry....I installed everything in French....hope you know what this means...)

So....what do you think, what is the problem?

when I tipe this in:sudo nano /etc/modprobe.d/alsa-base

and I add this to the end:options snd-hda-intel model=acer

I can not save it.....how do I do it? If I click on the close button it closes the window without saving it.....

However, I have to add, that the last lines of the file are:
options snd-hda-intel model=acer
sudo reboot
sudo reboot

Thanks for any help in advance! 

Delicatessen

---

### Post by kikke on 2008-03-04
> **mikeserv said:**
> What doesn't work?  If you're saying that Ubuntu doesn't work on the Acer 5315 then I can assure you that you are mistaken.  I'm also fairly certain that, with effort, you can get it up and running on just about anything.  But, if you like, Windows XP is good, too: just kind of a memory hog.

-Mike

You have an USER ID10T problem.
It doesn't work. With any effort. Go the hell with your RTFM attitude.

This model doesn't supported by Ubuntu or Acer or anything else than Windows. It has a buggy/undocumented ACPI, the Acer's support SAYS I have NO entitlement for ANY support with Linux. I only want to contact a developer for getting any info about this modell's ACPI, but the Acer's support is totally neglective so i given up. STFU.

---

### Post by rpalyvoda on 2008-03-08
Hi,

Has anyone here been able to connect this laptop to TV using the  svideo connexion?

---

### Post by mikeserv on 2008-03-09
kikke -

Wow, you're a real *******.  If I'm the idiot, why is it that Linux runs fine for me, and you can't get it to work at all?

-Mike

---

### Post by linux1time on 2008-03-10
hi i bought an acer aspire 5315 can i install ubuntu?
thanks you guys

---

### Post by mikeserv on 2008-03-10
Yes, if you follow the directions in post #101 of this thread you should be able to install Ubuntu.

-Mike

---

### Post by cabez0n on 2008-03-10
> **kikke said:**
> You have an USER ID10T problem.
It doesn't work. With any effort. Go the hell with your RTFM attitude.

This model doesn't supported by Ubuntu or Acer or anything else than Windows. It has a buggy/undocumented ACPI, the Acer's support SAYS I have NO entitlement for ANY support with Linux. I only want to contact a developer for getting any info about this modell's ACPI, but the Acer's support is totally neglective so i given up. STFU.

Seems to me your are not trying hard enough. It is truth that ACER doesnt treat Linux user very nicely, but in fact you can get most (if not all) of the hardware working for your Acer laptop in Linux...

check out> acer2linux.blogspot.com

---

### Post by kikke on 2008-03-11
> **mikeserv said:**
> kikke -

Wow, you're a real *******.  If I'm the idiot, why is it that Linux runs fine for me, and you can't get it to work at all?

-Mike


No, you are a big *******.
After hibernate or suspend, the ACPI doesn't work. It's absolutely unacceptable for me. Don't lie for newcomers.

---

### Post by kikke on 2008-03-11
> **linux1time said:**
> hi i bought an acer aspire 5315 can i install ubuntu?
thanks you guys

You can, but it will overheating because ACPI problems.
See more about this issue here: [http://ubuntuforums.org/showpost.php?p=4305576&postcount=69](http://ubuntuforums.org/showpost.php?p=4305576&postcount=69)
The ACPI team doesn't do anything.
The Acer Support said they don't support this model with Linux.
But you can use it with XP very well: [http://soulpass.com/2007/11/10/installing-windows-xp-professional-sp2-on-acer-aspire-5315-2153-laptop/](http://soulpass.com/2007/11/10/installing-windows-xp-professional-sp2-on-acer-aspire-5315-2153-laptop/)
Or hack a thermal regulator into it.
That's all. Don't trust the "Ah-everything's-works-for-me-and-it-makes-good-cafee" guys.


edit: Look! [http://ubuntuforums.org/showthread.php?t=604158&page=8](http://ubuntuforums.org/showthread.php?t=604158&page=8)
A new hope for using this model with Linux! Anybody tried it? It's a 7h old post :)

---

### Post by mikeserv on 2008-03-11
Kikke:

I will try it tonight, but I doubt if I will notice any difference.  I leave my laptop on for weeks at a time and it has never once overheated - or shut down on its own, for that matter.  But, I'll let you know how to make the BIOS update later.

-Mike

---

### Post by kikke on 2008-03-11
> **mikeserv said:**
> Kikke:

I will try it tonight, but I doubt if I will notice any difference.  I leave my laptop on for weeks at a time and it has never once overheated - or shut down on its own, for that matter.  But, I'll let you know how to make the BIOS update later.

-Mike

You tried the suspend/hibernate functions?

I'll try the suspend with XP, because it was wrong, the ventilator turned on only with resuming from hibernated status.

---

### Post by mikeserv on 2008-03-11
Well, after reading your post this morning I tried hibernate, and then turned the computer back on.  I then shut the cover and left for work, with the computer still on.  I've now come home (11 hours later) and opened the cover.  Everything is as I left it.  I don't recall ever trying "Suspend", but in my experience that doesn't play well with Compiz, anyway, so I doubt I'll use it.  

It is true that some native hardware functions work better in Windows, that is if you don't mind paying for the "Suspend" feature with double the resource usage and 1/4 of the customization.  But, to be honest, even with my old laptop which always ran XP, I never used hibernate or suspend.  If I wanted to turn the computer off, I turned it off, otherwise, it was on.

If you're that worried about boot time, maybe you should look into speeding that process up.  I'm sure I've seen some posts around the forums about 30 sec boot times.  There's all kinds of optimization techniques that can be deployed in the Linux OS.

But, to answer your ACPI question: 12 hours straight running AFTER a hibernate -> resume cycle.  No shutdown.  The laptop is sitting in my lap: it's not even hot.

-Mike

---

### Post by kikke on 2008-03-12
> **mikeserv said:**
> Well, after reading your post this morning I tried hibernate, and then turned the computer back on.  I then shut the cover and left for work, with the computer still on.  I've now come home (11 hours later) and opened the cover.  Everything is as I left it.  I don't recall ever trying "Suspend", but in my experience that doesn't play well with Compiz, anyway, so I doubt I'll use it.  

It is true that some native hardware functions work better in Windows, that is if you don't mind paying for the "Suspend" feature with double the resource usage and 1/4 of the customization.  But, to be honest, even with my old laptop which always ran XP, I never used hibernate or suspend.  If I wanted to turn the computer off, I turned it off, otherwise, it was on.

If you're that worried about boot time, maybe you should look into speeding that process up.  I'm sure I've seen some posts around the forums about 30 sec boot times.  There's all kinds of optimization techniques that can be deployed in the Linux OS.


"Hibernate is a feature seen in many operating systems where the contents of RAM is written to non-volatile storage, such as the hard disk (as either a file or on a separate partition) before powering off the system. Later the system can be restored to the state it was in when hibernation was invoked, so that programs can continue executing as if nothing happened."

> **mikeserv said:**
> 
But, to answer your ACPI question: 12 hours straight running AFTER a hibernate -> resume cycle.  No shutdown.  The laptop is sitting in my lap: it's not even hot.

Good news! Which version of BIOS you use? Which distro, which alsa, which ndiswrapper?

You have a new kernel with patched ACPI?
[http://ubuntuforums.org/showthread.php?p=4305576#post4305576](http://ubuntuforums.org/showthread.php?p=4305576#post4305576)



UPDATE:

I tried the latest Hardy alpha, with 1.31 BIOS.
It's wrong.
After resuming suspend, the processor's temperature seems 50 C degree, after resuming hibernate, the detected temperature is 40 C. The real temperature was ~55 C.

---

### Post by pp77 on 2008-03-20
New bios 1.32 released (without a readme). Don't know if it will fry our laptops.

[ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios]("ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios")

---

### Post by kikke on 2008-03-27
Lazy developer at Acer release the 1.33 BIOS without any changelog or readme, only an exe.

---

### Post by kikke on 2008-04-12
New release: 1.34 

BIOS: 
   1). Enable Execute Disable Bit. 
   2). Add ATI M86 VGA board. 
   3). Fix BSOD 0x101.(update DTS function) 
   4). Enable SATA port 2. 
EC: 
  1). None. 
   

1.33 changes was:

BIOS: 
  1). Fixed BOBO sound when play music. 
  2). Fixed can't via int15 function to get serial number 
  3). Fixed Asset Tag issue. 
 
EC: 
  1). None.

---

### Post by kikke on 2008-04-18
Overheating problem seems to solved by David Edward's hack.
See [http://ubuntuforums.org/showpost.php?p=4702613&postcount=108](http://ubuntuforums.org/showpost.php?p=4702613&postcount=108) for more infos.

---

### Post by gcastell on 2008-04-21
Hi everybody,

First let me thank Mike, his instructions worked like a charm on my acer 5315-2153 that I got at Walmart for 375 tax included :), I've enjoyed Ubuntu since November almost without a problem (hibernate works but suspend doesn't, I don't care anyway boot time is a lot faster that my dual core vista machine ).

Anyway, the reason for this post is to ask if somebody has upgraded to 8.04 with success, I am pretty much new to linux and even though I was able to install 7.10 I am afraid to mess my machine with 8.04.

Hope someone has been braver than me and try to upgrade.

Thanks again,
Gabe

---

### Post by fartymcsimmons on 2008-04-22
Hi all,

I have this laptop as well and have been dualbooting Vista and XP on it for some time now. 

I decided to go the linux way recently... I tried wubi and everything worked fine aside from wireless and the fan :-(

After ditching the Wubi install I installed a 32 bit copy of 8.04 and the fan works well on bootup (not after suspend, haven't tried hibernate.)

The wireless was simple enough for me (linux noob) to get going after reading this thread. 

Sound worked automatically, touchpad works okay except the scroll buttons are reversed. Graphic effects work out of the box as well.

I was very impressed with how smooth everything went. I'm loving ubuntu more and more each day.

Thanks to all.

---

### Post by gcastell on 2008-04-22
I am glad to hear that a clean installation of 8.04 works, just one question fartymcsimmons, what do you mean that the scroll buttons are reversed?

---

### Post by fartymcsimmons on 2008-04-22
The scroll button thing inbetween the left and right mouse button on the touchpad are reverse (up scrolls down, down scrolls up).

It's not that big of a deal for me as i usually use a wireless mouse.

---

### Post by gcastell on 2008-04-22
Thanks for the information!

Now the question is, anybody has upgraded from 7.10 to 8.04?

---

### Post by gcastell on 2008-04-24
OK, so I decided to be the brave in the group... I am currently upgrading my laptop.. wish me luck!

---

### Post by alucardromero on 2008-04-25
Hey gcastell,

What's the verdict?

---

### Post by gcastell on 2008-04-25
So far mixed, while upgrading I prevented the upgrade process from overwriting the alsabase file, this kept my sound working.. but I lost wifi, currently I am working on this with the instructions from this thread.. I will let you know!

---

### Post by alucardromero on 2008-04-25
Awesome stuff.

I did a fresh install and sound worked just fine.  Wifi didn't work though, so I did sanone's methods of bringing it up.

So far, I'm only able to connect to my router WITHOUT security.  But I'm going to try WEP as I didn't get to thoroughly test it earlier.

I'm on it right now.

---

### Post by gcastell on 2008-04-25
OK, so I follow the steps in this thread and it worked!. After checking the end result I think that by doing the following you can bring back wifi:

```

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
echo "ndiswrapper" | sudo tee -a /etc/modules

```

I suspect too that even if the upgrade had overwritten my alsabase file, sound would have been ok.

Hope this helps!

---

### Post by gcastell on 2008-04-25
it seems that suspend is now working perfectly! I am checking if the fan works, I hope it does.

---

### Post by idrinkalot on 2008-04-26
ok, after months of fussing with the xp tricks on this laptop, i decided to go with ubuntu today. first time linux user (well, i tried about 8 years ago when i was doing the skins section at deviantart and wanted to utilize some programs, but completely didn't understand it so i ditched it quickly). i've got wireless working. that was the first thing i did since the only network cable i have is 3 feet long..
i ended up using the newer build at [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) 

now i'm going to go try to tackle monitor brightness...

---

### Post by fartymcsimmons on 2008-05-05
I used Ubuntu 8.04 for about a week straight but the following issues are preventing me from switching full time. I've reverted back to Vista (which I don't hate like most people do.)

1. Wireless won't auto connect when coming out of suspend. (which fan seems to work somewhat)

2. Fan doesn't seem to speed up/slow down at right times. Seems like it's going constant speed all the time... the laptop seems to run hotter (might be my imagination.)

3. I'm relatively inexperienced in the art of Linux. 

I can hopefully fix the first and third problem, but the second one bugs me. Can somebody explain to me what could be causing this (buggy ACPI?)

---

### Post by kikke on 2008-05-11
> **fartymcsimmons said:**
> 
2. Fan doesn't seem to speed up/slow down at right times. Seems like it's going constant speed all the time... the laptop seems to run hotter (might be my imagination.)



I found the solution for the problem.

1. Restore the /etc/rc.local into original state (delete the acer fancontrol specific lines)

2. Edit the setting in /usr/bin/acer_fancontrol for your needs.
I set the FAN_ON value to 50, and FAN_OFF to 55.
Don't forget to uncomment the correct PATCH_ADDRESS line! (Maybe somebody wrote autodetection routin for this.)

3. Create a new service in /etc/init.d:

"sudo gedit /etc/init.d/acer_fan"

and paste this:

```

#! /bin/sh -e
#### BEGIN INIT INFO
# Provides:          acer_fan
# Required-Start:    $syslog $time $local_fs
# Required-Stop:     $syslog $time $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Acer fan control
# Description:       Acer fan control
### END INIT INFO
# Author: kikke <info@kikke.hu>

set -e

PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=acer_fancontrol

test -x /usr/bin/acer_fancontrol || exit 0

. /lib/lsb/init-functions

case "$1" in
    start)
    log_daemon_msg "Starting Acer fancontrol" "acer_fan"
    exec $DAEMON &
    log_end_msg $?
    ;;
  stop)
    log_daemon_msg "Stopping Acer fancontrol" "acer_fan"
    killall -q $DAEMON
    log_end_msg $?
    ;;
  force-reload|restart)
    $0 stop
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/acer_fan {start|stop|restart|force-reload}"
    exit 1
    ;;
esac

exit 0

```and save.

4. Add the acer_fan service to default runlevels:
"sudo update-rc.d acer_fan defaults"

5. Edit the /etc/default/acpi-support, add the acer_fan to STOP_SERVICES.

"gedit /etc/default/acpi-support"

find
STOP_SERVICES=""

and change to 
STOP_SERVICES="acer_fan"

and save.

6. Try out the service with "sudo /etc/init.d/acer_fan start"

Reboot or hibernate!
It works for me perfectly :)


---

UPDATE: [http://ubuntuforums.org/showthread.php?p=4948195#post4948195](http://ubuntuforums.org/showthread.php?p=4948195#post4948195)
New version.

---

### Post by Darksword on 2008-05-19
I'm sorry to drag this topic back up, but I'm having trouble with post 101's setup instructions for the sound card.  Everything seems to go along perfectly, but the sound doesn't work.  When I shut down and restart Alsa ( sudo /etc/init.d/alsasound stop >  sudo /etc/init.d/alsasound start) , I get the following message:

/usr/sbin/alsactl: load_state:1327: No soundcards found...

 
Seems the ALSA driver, Alsa config, and alsa utils all work fine.  When I run 

sudo alsaconf

It can see the hda-intel card, but for some reason the system loses it.

Any ideas?  

My exact model is an Acer Aspire 5315-2153

My card info, according to aplay -l  is 

card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any suggestions?

---

### Post by mikeserv on 2008-05-19
Darksword:

Hmm...  That's a shame that the directions aren't working for you.  I have to ask, though, what version of Ubuntu are you using?  

After installing 7.10 on my laptop and following all of the above instructions everything worked perfectly - until I received any kernel updates.  Every 7.10 kernel update I installed resulted in my having to reinstall the ALSA drivers.  

I was afraid that the same would happen with the upgrade to 8.04 as well, but, to my pleasant surprise, the new 8.04 kernel modules seem to support our sound card out of the box.  

So, if you are using 7.10, please consider an upgrade to 8.04, and, if you're using 8.04 already, then the directions in post #101 are not for you.  If it is 8.04 you are using it may have something to with a blacklist... 

In any case, fill me in on your situation and I will make an attempt at assisting you.

-Mike

---

### Post by Darksword on 2008-05-19
I'm still running 7.10.

I'll try running the upgrade, but I was wary it would bust my WiFi card, which DOES work perfectly.

---

### Post by Darksword on 2008-05-19
Oh crap!  Nevermind, I figured it out!

I ran alsaconf again and then ran preferences-Sound and manually changed all the sound configurations from "Auto detect" to ALSA.  I've got sound! :guitar:

---

### Post by mikeserv on 2008-05-19
That's good - though I would still consider upgrading to 8.04.  It works perfectly and it definitely DIDN'T break my wifi - in fact I ran the upgrade completely over wifi.

-Mike

---

### Post by alucardromero on 2008-05-19
Darksword... awesome.

For Kubuntu 8.10 I can confirm that sound works out-of-the-box.  I have this laptop too.  You can use the guide to set things up, but there's a few differences...

WiFi is not broken, it can be brought up the same way as the guide posted here BUT if you use a network manager like WICD it won't connect automatically on boot.  You have to connect manually all the time.  I don't know if there is a fix for this yet.  It's not much of a bother for me, although I obviously would prefer it connected automatically.  I don't know if there's issues for any other network manager interface.

I posted a thread for the brightness issue of this particular laptop.  I don't know if it's a general or a model specific issue, but upon boot the screen is dim.  You can raise the brightness back (Fn+LEFT or Fn+RIGHT) but when the screen saver kicks in, it's dimmed again and it won't brighten back up when you move the mouse.  YOU CAN use the Power Manager to adjust some settings but not always does it work.

---

### Post by zdude on 2008-06-18
> **mikeserv said:**
> That's good - though I would still consider upgrading to 8.04.  It works perfectly and it definitely DIDN'T break my wifi - in fact I ran the upgrade completely over wifi.

-Mike
I did the 8.04 upgrade and the sound and everything else worked except wireless. I've tried every trick in the book to get this working but to no avail. I tried recompiling the ndiswrapp, the restricted installed atheros drivers and even recompiled various 5700eg madwifi drivers and nothing works.:confused: 
I had to restore from an image I made to get back to 7.10 (which use the ndiswrapper) and all is working well again. 
One note, while updating my bios to 1.40 the firmware bricked my laptop completely. I sent it to acer, who replaced cpu fans, motherboard and a few other things and returned it back very quickly.
So, what wireless drivers are you guys using and how did you set them up?

---

### Post by OldAlgis on 2008-06-18
> **zdude said:**
> [...]One note, while updating my bios to 1.40 the firmware bricked my laptop completely. I sent it to acer, who replaced cpu fans, motherboard and a few other things and returned it back very quickly.[...]

I would like to know more about your BIOS upgrade as I have not taken the non-reversible step of trying to upgrade BIOS - my Acer BIOS is still 1.31.  I am concerned about the possible "sea anchor" creation as our ozzie "Acer service" are likely to be less helpful if they sniff upgrades that they did not authorise.

In particular, where did you get the flashing data for the upgrade?

Thanks in advance for the information.

---

### Post by zdude on 2008-06-19
> **OldAlgis said:**
> I would like to know more about your BIOS upgrade as I have not taken the non-reversible step of trying to upgrade BIOS - my Acer BIOS is still 1.31.  I am concerned about the possible "sea anchor" creation as our ozzie "Acer service" are likely to be less helpful if they sniff upgrades that they did not authorise.

In particular, where did you get the flashing data for the upgrade?

Thanks in advance for the information.

I was doing a regular upgrade and when it was at 10% or so it said there was a verify error. The computer then locked up and was frozen and eventually it turned off. After that it was totally dead - even the charging light quit working. Acer repaired the unit and also had to reload the org. OS (Vista, ugh) - I guess the meltdown wiped the HD too! I read the serial number to the tech guy and I did not have to dig out my receipt for the unit or any proof of purchase (although I have it somewhere :rolleyes:).
Good luck if you decide to try upgrading you bios. The good news is the cpu fan they put in plus the newer bios - my laptop seems very cool to the touch and the battery seems to last a lot longer. YMMV
I got the firmware upgrade from Acer's website.

---

### Post by OldAlgis on 2008-06-19
> **zdude said:**
> I was doing a regular upgrade and when it was at 10% or so it said there was a verify error. The computer then locked up and was frozen and eventually it turned off. After that it was totally dead. [...] I got the firmware upgrade from Acer's website.

Thank you for that. Could you give the URL of the Acer website? Down under, we are used to use of various websites that are overseas, so the URL would help.

Actually, it would also help to have the flash patch data (one file only), so that others (particularly I :-) ) could check their patch data against it (viz comparing the two files, or at least comparing their MD5 SUMS. Would it be possible to download your patch from some site?

 Having once created a "sea anchor", I am very careful about flashing the BIOS...  

There has to be a reason for the flashing failure and what springs to my mind, in addition to the obvious power failures, are two things:

1. Corrupted download
2. Choice of a patch for a different model.

Thanks for your reply, which helped to highten my concerns about flashing the BIOS...

---

### Post by zdude on 2008-06-19
I think I got the bios update from here:
[ftp://ftp.support.acer-euro.com/notebook/](ftp://ftp.support.acer-euro.com/notebook/)
but I am not sure due to losing all data on the computer after servicing including the firmware I download. I remember testing the download zip file and it test ok. I won't update if everything else is ok - also see the site, lots of acer notebook users here with lots of info.
[http://forum.notebookreview.com/forumdisplay.php?f=22](http://forum.notebookreview.com/forumdisplay.php?f=22)

---

### Post by OldAlgis on 2008-06-20
> **zdude said:**
> I think I got the bios update from here:
[ftp://ftp.support.acer-euro.com/notebook/](ftp://ftp.support.acer-euro.com/notebook/)
but I am not sure due to losing all data on the computer after servicing including the firmware I download.[...]
[http://forum.notebookreview.com/forumdisplay.php?f=22](http://forum.notebookreview.com/forumdisplay.php?f=22)

zdude,

Thank you for the information. Pity, though not unexpected, that the original flash data is lost.

---

### Post by andrewbmartin on 2008-07-08
I did the BIOS upgrade to V1.40 using my Vista partition ( I'm hanging on to it because apparantly you need it to configure NextG Cards before they can be used in Ubuntu) and found you need to right click on the exe file and select run as Administrator before it will work.  The upgrade too a ( tense) few minutes but seems to have done the trick.

---

### Post by NMbottlecap on 2008-07-08
I've got the 5315 with the Intel 965 graphics chip and I am so close to getting my company to switch over to linux, but I need to have dual displays... when I connect my Dell 17" it doesn't detect it.  any ideas?

---

### Post by OldAlgis on 2008-07-08
> **NMbottlecap said:**
> I've got the 5315 with the Intel 965 graphics chip and I am so close to getting my company to switch over to linux, but I need to have dual displays... when I connect my Dell 17" it doesn't detect it.  any ideas?

Is that a Dell 17" LCD display that you connect to the laptop? If so, perhaps you would get better response in other threads that are still active.  This one is already an archive!

Just a 2c thought.

---

### Post by BBT on 2008-07-14
Using all of the wonderful advice in this thread I have had my 5315 running perfectly since last year. Thank you all!

A couple of months ago I tired of the touchpad and decided to buy a wireless mouse. I bought a Logitech V220 Mouse. I configured it using the the evdev driver, and it works great!

The problem is  that now the touchpad no longer works correctly. The touchpad now operates absolutely. Whereever you touch the pad, the cursor moves to that position on the screen. There is no relative movement, no acceleration, nothing. In fact none of the org.conf parameters for the touchpad have any effect whatsoever.

The relevant conf.org sections are as follows:

```

Section "InputDevice"
        Identifier      "Logitech V220"
        Driver          "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:1d.0-1/input0"
        Option          "SendCoreEvents"        "true"
        Option          "evBits"                "+1-2"
        Option          "keyBits"               "~272-287"
        Option          "relBits"               "~0-2 ~6 ~8"
        Option          "Pass"                  "3"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
        Option          "HorizScrollDelta"      "0"
        Option          "FingerHigh"            "40"
        Option          "FingerLow"             "20"
        Option          "MinSpeed"              "0.10"
        Option          "MaxSpeed"              "1.00"
        Option          "AccelFactor"           "0.0500"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Logitech V220"
        InputDevice     "Synaptics Touchpad"
EndSection

```

Unplugging the mouse does not improve the touchpad operation. If I remove the line:

```
     InputDevice     "Logitech V220"
```

and restart the Xserver, the touchpad works again.

I've tried various combinations of the options "AlwaysCore", "SendCoreEvents", and "CoreEvent" with no improvement.

There are a couple of forum postings that I thought had good ideas, but none have helped so far:

[http://topperh.blogspot.com/2008/06/howto-synaptics-touchpad-and-usb-mouse.html]("http://topperh.blogspot.com/2008/06/howto-synaptics-touchpad-and-usb-mouse.html")
[http://www.nabble.com/Touchpad-in-%22absolute%22-mode-td14890025.html]("http://www.nabble.com/Touchpad-in-%22absolute%22-mode-td14890025.html")

Any help would be greatly appreciated.

---

