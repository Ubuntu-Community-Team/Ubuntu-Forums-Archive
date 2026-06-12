---
title: "Summary on Sony Vaio E-series hardware support"
date: 2010-04-07
forum: Hardware
---

### Post by ultiva on 2010-04-07
Hello everyone.
I'd like to start this thread to exchange experience about running Ubuntu on Sony Vaio E series (mine is VPC-EB1S1E). I've managed to configure Ubuntu 9.10 for about 85% usability (and that is not enough), here is my summary:

1. ATI mobility radeon 5650 - works with fglrx driver, watermark can be removed, 3D accel and Compiz works, sadly looks like card does not display proper number of colours (gradiens look really messed up) - as far as I understand its up to AMD to correct this.

2. WiFi Atheros 9285 chip - "works" with ath9k driver. Link stability is very poor, often stop and wait during downloads. I'm out of ideas to make it function better. Tried Ubuntu 10.04 and it seems that there will be no much improvement. Same situation with windows 7.7.0 driver under ndiswrapper so I don't know if it is ath9k fault but it's Linux fault for sure - under Win7 driver 8.0.0 WiFi works superb.

3. Gigabit Ethernet (Marvell Yukon) - works perfect - if one manages to do some linking tricks in kernel sources and compile driver manually. Really hope it will be made working OOB, it is just one step ahead. Unfortunately Ubuntu 10.04 does not seem to correct this situation, on livecd this NIC still does not work.

4. Sound card Realtek 269 - also does not work OOB, it requires some hacks to the amplifer to work properly. Instructions are present on the Internet but I don't understand - if one line entered from terminal starts this sound card, maybe it can be made do work OOB ?

6. ALPS Touchpad - almost works - touchpad is functioning, but is detected as mouse. Also noticed that sometimes it does not react correctly for tapping under Ubuntu.

7. Camera - works OOB

8. Bluetooth - works OOB, additional I can say that Logitech V470 BT mouse works perfect, setup is very simple.

9. SD card reader - looks like it works, reader is detected, modules are loaded, hovever I haven't tested it.

10. MMC card reader - NOT TESTED

11. Screen brightness regulation - works OOB

If someone have additional experience please share it here, maybe we can make Ubuntu run flawless on this nice laptops before they became too old to use it :)

Regards
Piotr Sikorski

---

### Post by cub on 2010-04-13
Great stuff! I have been aiming to buy just this model (VPC-EB1S1E) and the Sony sales reps were all but helpful.

> 1. ATI mobility radeon 5650 - works with fglrx driver, watermark can be removed, 3D accel and Compiz works, sadly looks like card does not display proper number of colours (gradiens look really messed up) - as far as I understand its up to AMD to correct this.

Could you explain this a bit more in detail? I'm planning to use my laptop for sound recording and graphic design. Will the graphics be messed up so work in GIMP will not be correctly displayed?

---

### Post by cub on 2010-04-14
Did you run 32 or 64bit Ubuntu?

---

### Post by istoff on 2010-04-14
Hi,

Have a Vaio VPCEB17FG and running 10.04beta and updating daily.

Regarding wired ethernet, kernel 2.6.32 does not give me an eth0 device, but installing 2.6.33 from the kernel ppa makes it work.

Sound not working. Have the same problem as everybody else with no sound from speakers, very soft sound on headphones.  

Graphics.  Cannot install fglrx using stable ATI driver 10.3 or the built in gnome appearance wizard to download and enable ATI.

Would appreciate *any* info regarding sound / graphics on this machine.  

Currently planning to move to Fedora13 when released as I believe they are using 2.6.33 instead of 2.6.32

Thanks,
Ian

---

### Post by ultiva on 2010-04-14
Hi :)

- Im' using currently Ubuntu 32bit 9.10, planning to move to 10.04 as soon as it's available

- ATI driver - I've managed to correct that gradient problem by 1. installing fglrx driver from ubuntu repo 2. installing catalyst 10.3 from amd web page on top on it 3. removing watermark. Now card seems to work 100% OK.

- Wired ethernet can be run on ubuntu 9.10 (2.6.31) - have to compile sk98lin driver. Little tricky but can be done and wired ethernet works good (one issue - driver does not report amount of transferred data). Kernel 2.6.33 have sky2 driver with integrated support for this NIS. I can post compilation instructions on sk98lin driver if you want it. You'll have to create some symlinks in kernel sources directory.

- Sound works but needs alsa from backports and some trick with program called hda_verb (not in repo have to download and compile) to correct some amplifier settings in the driver. This command has to be done every boot up and also sound preferences have to be open all the time (if not this setting resets itself). Patch is on it's way to alsa.

- Wifi ar9285 in my case works good with madwifi driver + patches for this chip. In addition on kernel 2.6.31 it throws some errors in dmesg but card works with no problems. On Lucid b2 64bit (2.6.32) driver also compiles smoothly and works without errors.

It looks that this laptop is capable of running at about 99% of it's capabilities under Ubuntu, but requires some work. This missing 1% is acpi driver not reading correctly AC power supply state - always display battery and message "discharging" on connected AC adapter. Can't wait for stable release of Ubuntu 10.04, I really like it's  interface. It will be nice piece of OS.

In the mean time I've managed to make some tuning in Windoze7 to make it somewhat useful. That includes disabling or uninstalling anything that is not necessary including most of Sony's bloatware. Instaling Catalyst 10.3, and some useful GNU software. Now it at least more or less works and deserved to stay on my hdd :)

Tommorow I'll try to post some info about compiling sk98lin, hda_verb and madwifi.

Regards,
Piotr Sikorski

---

### Post by istoff on 2010-04-16
Hi

Just a quick update.

Yesterday, i upgraded to 2.6.32.21 and the wired network interface worked for the first time on a 2.6.32 kernel.  I removed the experimental 2.6.34 and stable 2.6.33 kernels I had installed and it worked fine using the newest 2.6.32 kernel.  This is awesome because this is a "supported out of the box" kernel.

Would appreciate a link to the sound fix.

Thanks,
Ian

UPDATE:
Sound working using hdaverb fixes posted elsewhere.  Just the ATI5650 to go and then I'm sorted!

---

### Post by cub on 2010-04-16
I installed Ubuntu 10.04 Beta 2 64-bit on my VPCEB1S1E yesterday and here are my (short) results:

1. ATI mobility radeon 5650 - worked OOB with automatically suggested ATI driver right away. No issues with gradients or watermark whatsoever.

2. WiFi - worked OOB. I didn't notice any cut-outs like I did when I later in the evening installed Ubuntu 9.10

3. Gigabit Ethernet - not tested

4. Sound card Realtek 269 - I ran a short test and I think I remember it working, but I wouldn't bet my left arm on it.

6. ALPS Touchpad - worked good in my experience, though I could not change the scrolling from "at the edge" to "two fingered scrolling". I don't know why.

7. Camera - not tested

8. Bluetooth - not tested, but it started up automatically

9. SD card reader - not tested

10. MMC card reader - not tested

11. Screen brightness regulation - did not work with Fn keys, I didn't look into it more closely.

I then proceeded to change it into a Ubuntu Studio 10.04 Beta 2 through following the "old" instructions at [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) . There were some complaints from the installation about Audacious and older versions but I didn't make too much note of it. On the whole it seemed to work well. However, for some reason I couldn't get my Edirol UA25-EX USB sound card to work with JACK. I could play mp3 in Audacious through the USB-card though.

Since my old Toshiba laptop (Ubuntu Studio 9.10) worked well with the Edirol card and JACK I then proceeded to install Ubuntu 9.10 32-bit and do the "upgrade" to Ubuntu Studio 9.10.

Strangely enough, with the same settings as the Toshiba the Edirol card still wouldn't work with JACK on the Sony Vaio. I don't understand that since it's the same Ubuntu version, same ALSA and same USB sound card. Still, JACK crash every time I try to start it even though I had the exact same settings as on the Toshiba laptop.

After that I hadn't much more time to fiddle around and had not installed the ATI drivers. I did notice the Wifi cut-outs though while downloading.

I also tried an Ubuntu Studio 9.10 64-bit DVD but the installation crashed 7 times in a row so I gave up.

---

### Post by ultiva on 2010-04-16
That's very good news. Thank you cub for posting this information. Can you describe your wifi cut-outs on 9.10 so I can compare it with my own issues ?

---

### Post by cub on 2010-04-16
> **ultiva said:**
> That's very good news. Thank you cub for posting this information. Can you describe your wifi cut-outs on 9.10 so I can compare it with my own issues ?
It was while running the first "sudo apt-get update" and when doing the update to the Studio version. While downloading the files it sometimes stopped and the time to download counted up from [1 min] to like [183 min], then it suddenly got going again and downloaded in a minute or so. Sometimes it also timed out and retried that specific package, which then downloaded very quickly. So I assumed it was similar to what you experienced.

---

### Post by ultiva on 2010-04-16
Thank you. It's exactly the same. Does your wifi started to work OK right after installation of 10.04 or after performing update ?

---

### Post by cub on 2010-04-16
With the 10.04 I did not notice any hang-ups. I was keeping an eye on it since I read it might occur. But it seems it worked directly from the DVD because I didn't see any interruptions when doing the updates. Or I was just lucky..;)

---

### Post by ultiva on 2010-04-16
OK, I've installed 10.04 beta 2 64 bit. Here's sumary:

ATI driver - works without problem, no gradient issues no watermarks
Wired ethernet - works with kernel 2.6.32-21
WiFi - STILL problems, have to install madwifi to make it usable, however there are no errors in dmesg (ath_fatal_tasklet)
Sound - still same problem, have to use hda-verb, but seems that now this setting does not reset itself and hdaverb can be inserted in /etc/rc.local = improvement :)

ADDITIONAL PROBLEMS that didn't existed in 9.10 :
Touchpad - scrolling does not work at all in 10.04 - found other reports about this bug, seems that it's known.
Screen brightness regulation - does not work at all

in dmesg there is message:
```
[   30.496053] sony-laptop: brightness ignored, must be controlled by ACPI video driver

```Brightness controll does not react to FN-keys not to brightness applet. It worked OK on 9.10.

I've found  that /proc/acpi/video/VGA/LCD/brightness reads correct brightness value and levels but when try to write to this file I get - permission denied (with sudo).

EDIT: have to do chmod 666 /proc/acpi/video/VGA/LCD/brightness then brightness controll works by manually writing value to this file. Unfortunatelly FN keys and applet stll does not work. At least I can now dim the screen not to hurt my eyes...

---

### Post by cub on 2010-04-20
> **ultiva said:**
> - Sound works but needs alsa from backports and some trick with program called hda_verb (not in repo have to download and compile) to correct some amplifier settings in the driver. This command has to be done every boot up and also sound preferences have to be open all the time (if not this setting resets itself). Patch is on it's way to alsa.
I set up the Backports on my laptop yesterday but I couldn't figure out which alsa I was supposed to install. Could you provide some hints?

---

### Post by ultiva on 2010-04-20
linux-backports-modules-alsa-lucid-generic - under 10.04

after that:
cat /proc/asound/version
says:
```

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 14 2010 for kernel 2.6.32-21-generic (SMP).

```

but still hda_verb is needed to make sound work.

Looks like sound fix for out VAIOs is added to 1.0.23
[http://alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23]("http://alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23")

---

### Post by cub on 2010-04-20
> **ultiva said:**
> linux-backports-modules-alsa-lucid-generic - under 10.04

after that:
cat /proc/asound/version
says:
```

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 14 2010 for kernel 2.6.32-21-generic (SMP).

```

but still hda_verb is needed to make sound work.

Looks like sound fix for out VAIOs is added to 1.0.23
[http://alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23]("http://alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23")
I installed the latest alsa I could get for 9.10. And then followed a explanation from a forum on hda-verb. No joy. Could you link to the guide you followed?

[edit] I tried another guide and actually got sound. However it is so incredibly low volume I can barely make out there's sound when all the volume knobs I find are 100% and I'm using headphones. Somethings's fishy...

---

### Post by ultiva on 2010-04-20
Hmmm I don't remember where I found that, but it is quite simple.
Newest alsa You can get, output set to Analog Stereo Duplex +
```

sudo hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22     

```

Unfortunately on 9.10 there is some annoying issue (there was in my case) - You have to open sound preferences (that applet where you can set up outputs, volume etc.) and after that do hda_verb. If You close it anytime (or not open) changes made by hda_verb will reset itself after few seconds. There is no such issue in 10.04 - so I could insert hda_verb in rc.local.

Ps. Can You post your alsa version ? Maybe You should try to compile alsa 1.0.23 ? - according to changelog the fix is there.

---

### Post by cub on 2010-04-20
Thanks, that workaround fixed the volume.

```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).
```
I'll wait for the 1.0.23 to appear in the lucid repository. I don't have good experience from compiling things myself. :)

Now, if I only could get my USB soundcard to work as well I'm a happy camper.

---

### Post by ultiva on 2010-04-20
What is this card ? lsusb, dmesg, lsmod ?

---

### Post by cub on 2010-04-20
> **ultiva said:**
> What is this card ? lsusb, dmesg, lsmod ?
It's ongoing in a JACK thread: [http://ubuntuforums.org/showthread.php?t=806730&page=4](http://ubuntuforums.org/showthread.php?t=806730&page=4)

It's an Edirol UA-25EX external USB sound card. Worked fine on my old Toshiba laptop, but with the same OS and same settings JACK just won't run on the VAIO.

---

### Post by cub on 2010-04-22
> **ultiva said:**
> OK, I've installed 10.04 beta 2 64 bit. Here's sumary:

ADDITIONAL PROBLEMS that didn't existed in 9.10 :
Touchpad - scrolling does not work at all in 10.04 - found other reports about this bug, seems that it's known.
Screen brightness regulation - does not work at all
I reinstalled 10.04 beta 2 64 bit today for fun and the scrolling comes and goes. It's quite sporadic but from time to time the edge scrolling works.

Another issue I experienced was that directly after startup the laptop complained of drained battery (which was 100% though) and wanted to hibernate. I pressed cancel, plugged in the cable for a short time and then went back to battery without any problem. Though after I left the pc for a while the battery low window reappeared and I pressed OK out of confusion. Bad idea. The system tried to hibernate and after strange blips on the screen it finally went down. Then I tried to re-start it and there were a lot of messed up graphics power up/down before it finally came back to life. No more hibernation! :D

---

### Post by ultiva on 2010-04-22
I haven't tried hibernation because I suspected sth like that or even worse :) I've just tried suspend mode and it worked OK except that my beloved madwifi driver went freak after resume generating some scary messages in dmesg "FIFO overrun..... blah blah" and have to reload it to make it work again. Thank You for testing hibernation, at least now I know that there are good chances my laptop will survive when I eventually try that :)

According to touchpad - I've just enabled scrolling emulation and forget about it because I prefer my BT mouse which works perfect under Ubuntu (even better than with windoze). I'll try to solve that problem when I find some time. There is something interesting with this touchpad problem. In 9.10 Vaio's touchpad was detected as PS/2 mouse and scrolling worked. Now in 10.04 it's detected as ALPS Touchpad - improvement hehe, but unfortunately scrolling problem showed up.

And this issue with low battery - my Ubuntu sometimes display scarry message, sth like - battery 80% 3 minutes to discharge (when laptop is connected to AC power). Another thing is that under ubuntu laptop can sustain about 1h 15m on battery power while on windoze >2h. Maybe it's due to fact that I have compiz with many modules loaded and display at about 80% brightness all the time, while windoze limits brightness and aero glass degrades to aero without glass. Quite strange due to fact that under Ubuntu my laptop is MUCH colder than under Windoze (CPU 40-45C vs 55-60C).

---

### Post by DrRush on 2010-04-25
Hi,

I managed to get sound working from headphones and pc-speaker on my Vaio E-series running Ubuntu 10.4 beta 2.
Installing Alsa 1.0.23 did the trick.
Heres steps that should replicate what I did:

1.  sudo apt-get build-essential
2.  wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
3.  tar -xjf alsa-driver-1.0.23.tar.bz2
4.  cd alsa-driver-1.0.23/
5.  ./configure
6.  make
7.  sudo make install
8. alsamixer (don't know if this step was necessary since my volume was already enabled)
9. reboot

Sound should now work.

By the way, does anyone know if one continues to receive updates of alsa after installing it manually like this?

---

### Post by cub on 2010-04-26
> **DrRush said:**
> Hi,

I managed to get sound working from headphones and pc-speaker on my Vaio E-series running Ubuntu 10.4 beta 2.
Installing Alsa 1.0.23 did the trick.
Heres steps that should replicate what I did:

1.  sudo apt-get **install** build-essential
2.  wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
3.  tar -xjf alsa-driver-1.0.23.tar.bz2
4.  cd alsa-driver-1.0.23/
5.  ./configure
6.  make
7.  sudo make install
8. alsamixer (don't know if this step was necessary since my volume was already enabled)
9. reboot

Sound should now work.

Thanks for that guide! With the addition of **install** this also works with Ubuntu 9.10. My alsamixer was muted so step 8 should be there just in case.

---

### Post by Qselma on 2010-04-29
i got the brightness-control working! well, not the keys, but the settings:P:

```
$cat /sys/class/backlight/acpi_video0/max_brightness 
8
$ sudo chmod 666 /sys/class/backlight/acpi_video0/brightness
$sudo echo '5' > /sys/class/backlight/acpi_video0/brightness

```

---

### Post by linuxrulez on 2010-05-02
when i tried the above step i got this error :
 echo: write error: Input/output error

I am using sony vaio VPCEB14EN from E series.

This brightness issue is very annoy. My eyes are getting strained due to this :(

---

### Post by asarefin on 2010-05-02
> **linuxrulez said:**
> when i tried the above step i got this error :
 echo: write error: Input/output error

I am using sony vaio VPCEB14EN from E series.

This brightness issue is very annoy. My eyes are getting strained due to this :(


Well, it worked for me with VPCEB16FG (AUS model), but is there is any way?

- to activate the function keys? (for brightness control)
- any solution for scroll bar on touchpad?

P.S : every thing works fine on ubuntu 9.10 karmic 
(just fix sound with new alsa mixer install and  graphics ATI ccc 10.4)  but I want to be lucid lynx.

FYI, sony vaio F series real game looser in ubuntu, so atleast be happy with E series.

---

### Post by cub on 2010-05-02
> **linuxrulez said:**
> when i tried the above step i got this error :
 echo: write error: Input/output error

I am using sony vaio VPCEB14EN from E series.

This brightness issue is very annoy. My eyes are getting strained due to this :(
Same here with a VPCEB1S1E.

---

### Post by ultiva on 2010-05-02
> **cub said:**
> Same here with a VPCEB1S1E.

Very strange. My VPCEB1S1E accept this method.
Please post output of:
cat /proc/acpi/video/VGA/LCD/brightness

In my case it is 
```

levels:  21 24 29 36 44 53 63 76 100
current: 76

```

I can do chmod 666 to this file and then write to it as regular user. Ex
echo "76" > /proc/acpi/video/VGA/LCD/brightness

also /sys/class/backlight/acpi_video0/brightness method works with my laptop.

---

### Post by cub on 2010-05-03
> **ultiva said:**
> 
I can do chmod 666 to this file and then write to it as regular user. Ex
echo "76" > /proc/acpi/video/VGA/LCD/brightness
This works, but the other method didn't.

---

### Post by asarefin on 2010-05-04
> **cub said:**
> This works, but the other method didn't.
why the brightness function keys are not working? it worked on 9.10...!!!

---

### Post by cub on 2010-05-04
> **asarefin said:**
> why the brightness function keys are not working? it worked on 9.10...!!!
Yes, strange. It responds to the pressing of Fn and the brightkeys with showing the panel, but nothing happens. The volume changes work so why not this.

---

### Post by ultiva on 2010-05-04
Hehe, in my case Fn backlight keys does not show anything. No light bar at all. I've tested them with xev and they are working OK, but no bar and no backlight regulation.

---

### Post by sixpounder on 2010-05-05
Just a sec: am I the only one who gets terrible FPS on my e series with 5650 hd when using compiz??

Also the brightness problem is odd as stated before...

---

### Post by cub on 2010-05-08
After running updates yesterday I had to reapply the alsa 1.0.23 to get my sound back again. I didn't see that alsa was part of the updates. Though it was an updated kernel so perhaps it needs to be reapplied along with every kernel update?

---

### Post by danyzoca on 2010-05-09
Hi everyone,
My Vaio EB1S1E is going to arrive tomorrow or so, and I pretend to install just Ubuntu on it.
So, what do I really need to do to get it running?
Activate restricted driver in "Hardware Drivers"; 
Remove ATI's Watermkark;
Download and compile ALSA 1.0.23;

Is this it? Or should I install ATI's official driver?

Two questions, though:
What about screen brightness regulation? Do function keys work properly? From what I've read It seems me that you need to manually right the values to a file, wouldn't it be more easier to create a script to adjust that and add it to the panel/dock as launcher? Doesn't the gnome-panel brightness applet work?

And about wifi, does it now work OOB or do you have to compile some drivers?

Thanks in advance,

---

### Post by cub on 2010-05-09
I didn't install ATI official drivers, just activate the one in Hardware Drivers. I didn't get any watermark to remove with 10.04.

As for Brightness neither the functions keys or the panel works. Manually set is the way to go so far.

Wifi works OOB, but I know Ultiva was not happy about the performance and did some things to work it out. I have not suffered with my wifi and never looked in to it.

---

### Post by birdmanuk on 2010-05-09
I have just compiled the alsa driver for my Sony VPCEB1ZOE, rebooted and I have sound at start up, but as soon as I log in, the sound is gone again. I have run alsamixer and nothing is muted.

Any ideas?

Running 10.04

---

### Post by sazawal on 2010-05-09
Hello forum,

I just installed ubuntu 10.04 on my vaio e series (VPCEB16FG) but there are few hardware issues.

1. My touchpad scroll is not working, though i enabled it from System>Preferences>Mouse
2. The same Fn key brightness control issue
3. I accidentally used Storage Device Manager to mount System Reserved Space(105 MB). Now everytime it boots it shows 

[I]unable to mount media/system

Press S to skip mounting and M to try mounting manually.
[/I]
Furthermore my Places>Computer shows an extra System Reserved space which shows following error when i try to open it

[I]Unable to mount System Reserved

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 15 in /etc/fstab is bad
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab[/I]


Somebody please help

---

### Post by Cuppa-Chino on 2010-05-11
Hi, has anyone managed to either disable the touchpad or even better disable it while typing?

its the one last annoying thing about my e

thanks

---

### Post by cub on 2010-05-11
> **Cuppa-Chino said:**
> Hi, has anyone managed to either disable the touchpad or even better disable it while typing?
My touchpad is ticked to be disabled while typing, but it don't seems so to me. But I have not had that feature before so I'm not sure how it is supposed to be working..? All I know is that it's annoying when I type and my hand accidently touch the touchpad.

---

### Post by onandcorei on 2010-05-13
> **ultiva said:**
> 
4. Sound card Realtek 269 - also does not work OOB, it requires some hacks to the amplifer to work properly. Instructions are present on the Internet but I don't understand - if one line entered from terminal starts this sound card, maybe it can be made do work OOB ?



To overcome sound problem on VPCEB1S1E,I've upgraded files related to alsa(driver,firmware,lib and utils) to 1.0.23 then problem is over.To download updated Alsa files:
[http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")

---

### Post by Cuppa-Chino on 2010-05-14
> **cub said:**
> My touchpad is ticked to be disabled while typing, but it don't seems so to me. But I have not had that feature before so I'm not sure how it is supposed to be working..? All I know is that it's annoying when I type and my hand accidently touch the touchpad.

tell me its a complete nuisance

---

### Post by Graysphere on 2010-05-15
On my VPC-EA1S1E, 10.04 installed well. I had to use the Alsa upgrade to get sound (linux-alsa-driver-modules-2.6.32-22-generic from ppa:ubuntu-audio-dev). Both fglrx and the open source driver work. I'll see what powertop tells me about that.

The brightness keys are not working, but the /proc/acpi does work:

# cat /proc/acpi/video/VGA/LCD/brightness 
levels:  5 8 11 16 23 34 48 70 100
current: 23

I also had some problems with the screen brightness when switching to battery power and the brightness would go way down, but that does not happen any more right now.

This laptop has an interesting 'battery saver' feature: the Vaio tools can set a maximum charge percentage. This is also respecten when Linux is running. I set the battery to charge not more than 50%; according to Sony this will stop the battery from aging much (so I have half the capacity now instead of a broken battery in 2 years). They suggest 80% asa compromise setting to prolong life with litle impact. I wonder is we could set this threshold from Linux so it is easy to do a full charge before traveling.

The highest C-state I see is C3. This is a core i3-330. Is that normal?

---

### Post by rax_m on 2010-05-17
Hi all, 

On my sony vaio f-series, I added the following to the DEVICE section of the xorg.conf file. After restarting, it allowed me to adjust the brightness of the screen using the gnome-applet - but only with your mouse scroll wheel. 

Hope this helps. Note that this is with an Nvidia 330m graphics card. 

```

Option "RegistryDwords" "EnableBrightnessControl=1"

```

Got from this forum: [http://ubuntuforums.org/showthread.php?t=1408321](http://ubuntuforums.org/showthread.php?t=1408321)

---

### Post by birdmanuk on 2010-05-24
Anyone having poor battery performance on their Vaios with 10.04? I get at least an extra 40 mins running Win 7.

VPCEB1ZOE

Thread here [http://ubuntuforums.org/showthread.php?t=1466241&highlight=battery&page=5](http://ubuntuforums.org/showthread.php?t=1466241&highlight=battery&page=5) other seem to be having same issue.

---

### Post by cub on 2010-05-24
I haven't compared with Win but the Battery Power is a bit screwed up. Sometimes I get a notice that my battery is broken and only 1,9% left, but the battery icon in task bar say 40% or something. (My eee pc says this all the time)

The most annoying is that if I run on battery, plug in the cord, but after a short while unplugs to run on battery again it gets really confused. Example: Yesterday I was running on battery and the icon said 40 minutes left. I plugged in the cord for like 15 minutes, then I had to pull it again to go into another room. I should have at least 40 minutes left then, right? Oh no, immediately I get a window warning saying "Your battery is critical low, will hibernate." then Ok/Cancel buttons. I click Cancel every time but it still hibernates EVERY TIME. So after the shutdown and me pushing the button to get it to go back fron hibernation I can then run it on battery no problem. But connect the cord and unplug it = hibernation every time.

---

### Post by sazawal on 2010-06-07
> **Qselma said:**
> i got the brightness-control working! well, not the keys, but the settings:P:

```
$cat /sys/class/backlight/acpi_video0/max_brightness 
8
$ sudo chmod 666 /sys/class/backlight/acpi_video0/brightness
$sudo echo '5' > /sys/class/backlight/acpi_video0/brightness

```

Hi Qselma,

Your brightness control was working really fine. But I made some changes to some files in order to get Fn keys work. Now I get this error

```
$ cat /sys/class/backlight/acpi_video0/max_brightness 
cat: /sys/class/backlight/acpi_video0/max_brightness: No such file or directory

```I dont know how the file got missing. So I checked it manually  /sys/class/backlight/ in nautilus, there is just one shortcut named "sony". Can you tell me how to fix it, or instead let me know the contents of your /sys/class/backlight/ folder.

---

### Post by Qselma on 2010-06-08
> **sazawal said:**
> Hi Qselma,

Your brightness control was working really fine. But I made some changes to some files in order to get Fn keys work. Now I get this error

```
$ cat /sys/class/backlight/acpi_video0/max_brightness 
cat: /sys/class/backlight/acpi_video0/max_brightness: No such file or directory

```I dont know how the file got missing. So I checked it manually  /sys/class/backlight/ in nautilus, there is just one shortcut named "sony". Can you tell me how to fix it, or instead let me know the contents of your /sys/class/backlight/ folder.

what changes did you made? maybe these switches are rovided by the graphic driver? i installed the fglrx as suggested by the hardware manager. everything else is pretty much the default.

In the meantime i wrote a little script that reads the current brightness level and adds or substract it by one. afetrwards i assigned it to the fn-keycombination using the gnome hotkey manager and edited the sudoers file so that the script can perform the action without the need to enter the password every time. i found this method very convenient, however it does not fix the automatic brightness correction eg. when switching to battery etc. if anyone gets stuck with this i will post the short script file and the sudoers howto.

regards

---

### Post by Gillus on 2010-06-10
Hi, quick question... Has ubuntu already an official update for the alsa driver, in other words, if I install ubuntu right now on my e-series and update, will I have sound? I think I've worked to long now with Windows, so I really hope ubuntu will work properly on the e-series.
Thanks!

---

### Post by fugu72 on 2010-06-17
Hi there,

I had the same problems with the fn keys and brightness control which did not work on the VAIO EB1S1E, so I did the following quick and dirty fix:

Run 
```
acpi_listen
```when pressing the Fn+F5 and Fn+F6 keys respectively, I got the following:
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

This is all the information you need to add the relevant scripts in /etc/acpi/
create the file /etc/acpi/events/sony-brightness-up with the following contents:

```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```In a similar manner create /etc/acpi/event/sony-brightness-down as:

```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```Now create the corresponding scripts:
/etc/acpi/brightdown.sh

```
#!/bin/bash

curr=`cat /sys/class/backlight/acpi_video0/actual_brightness`
if [ $curr -gt 0 ]; then
curr=$((curr-1));
echo $curr  > /sys/class/backlight/acpi_video0/brightness;
fi
```and /etc/acpi/brightup.sh

```
#!/bin/bash

curr=`cat /sys/class/backlight/acpi_video0/actual_brightness`
if [ $curr -lt 8 ]; then
curr=$((curr+1));
echo $curr  > /sys/class/backlight/acpi_video0/brightness;
fi
```then all you need to do is restart acpid for the changes to take effect:

```
sudo service acpid restart

```Unfortunately you will not see the nice brightness bar going up and down, but at least you will protect your eyes from the super bright backlight :p

---

### Post by Cuppa-Chino on 2010-06-19
> **Cuppa-Chino said:**
> tell me its a complete nuisance

I now decided to just make to launchers to start and stop the touchpad, easier than constant aggrevation:


create launcher (where you want)

to turn on the touchpad : 

```
gksudo modprobe psmouse
```

to turn the touchpad off:

```
gksudo rmmod psmouse
```

you could also write scripts and allow them de facto sudo, but I was to lazy for it

---

### Post by Cuppa-Chino on 2010-06-21
Hi,

I have a sony vaio e-series with bcm 2070 foxconn t77h114 bluetooth chip. I want to stream music via bluetooth to my stereo using a belkin bluetooth audio receiver.

this works okayish under windows, occaisonal gaps in playback but all in all ok.
under linux there are times when it seems to go okay but most of the time it just cuts in and out at an amazing rate.

log files report that pulseaudio skips this and that amount of micro seconds, anybody been able to fix this kind of problem?

I am using blueman and have updated to the latest bluez packages from ppa but no real change.

using ubuntu 10.04 alsa 1.0.23 blueman or gnome bluetooth

thanks
```
Jun 17 08:14:49  pulseaudio[1834]: module-bluetooth-device.c: Skipping 130464 us (= 23012 bytes) in audio stream
Jun 17 08:14:50  pulseaudio[1834]: module-bluetooth-device.c: Skipping 1354756 us (= 238976 bytes) in audio stream
Jun 17 08:14:51  pulseaudio[1834]: module-bluetooth-device.c: Skipping 179786 us (= 31712 bytes) in audio stream
```
etc etc

---

### Post by ff670099 on 2010-06-27
> **fugu72 said:**
> Hi there,

I had the same problems with the fn keys and brightness control which did not work on the VAIO EB1S1E, so I did the following quick and dirty fix:

Run 
```
acpi_listen
```when pressing the Fn+F5 and Fn+F6 keys respectively, I got the following:
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

This is all the information you need to add the relevant scripts in /etc/acpi/
create the file /etc/acpi/events/sony-brightness-up with the following contents:

```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```In a similar manner create /etc/acpi/event/sony-brightness-down as:

```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```Now create the corresponding scripts:
/etc/acpi/brightdown.sh

```
#!/bin/bash

curr=`cat /sys/class/backlight/acpi_video0/actual_brightness`
if [ $curr -gt 0 ]; then
curr=$((curr-1));
echo $curr  > /sys/class/backlight/acpi_video0/brightness;
fi
```and /etc/acpi/brightup.sh

```
#!/bin/bash

curr=`cat /sys/class/backlight/acpi_video0/actual_brightness`
if [ $curr -lt 8 ]; then
curr=$((curr+1));
echo $curr  > /sys/class/backlight/acpi_video0/brightness;
fi
```then all you need to do is restart acpid for the changes to take effect:

```
sudo service acpid restart

```Unfortunately you will not see the nice brightness bar going up and down, but at least you will protect your eyes from the super bright backlight :p

Hello, unfortunately it doesn't work for me. I'm missing something?

Thank you!

---

### Post by danyzoca on 2010-06-30
Installing latest Catalyst 10.6 driver (Official ATI Proprietary driver) from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") solved all my brigthness control problems. All works without any hacks -> brightness control notifications and even automatic brightness adjustement when plugging the battery out :-) 

All this in a VPC-EB1S1E/BJ.

[COLOR="Red"]**First **[/COLOR]remove all fglrx related packages, just do a search by fglrx in Synpatic or Software Center and remove all installed packages.

Then download the file, move to your Home Folder, open up a shell and do:

[HTML]
# chmod +x ati-driver-installer-10-6-x86.x86_64.run 
#./ati-driver-installer-10-6-x86.x86_64.run 
[Follow on-screen instruction, and when finished run...]
# aticonfig --initial [/HTML]

Reboot. There you have, on screen brightness controls :-)
(and with this update I've finally been able to watch Blu-Ray 1080p awesomely well, a thing that with the previous driver was impossible).

---

### Post by bigbrovar on 2010-07-13
Hi guys I have been following this thread because I have my eyes on this [Sony Vaio]("http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644712007") and would like to ask if its worth the trouble. I am not afraid to get my hands dirty (no dirty no learn) but all i want to know is if there are work around to any of the issues faced with the Sony Vaio E series. How well and stable does ubuntu run on it forexample would really appreciate it if someone here can share there experience with the laptop

---

### Post by birdmanuk on 2010-07-13
Hi Bigbrovar,

I have this Vaio - [http://www.sony.co.uk/product/vn-e-series/vpceb1z0e-b](http://www.sony.co.uk/product/vn-e-series/vpceb1z0e-b) It's a similar spec. Initialy I had a few problems with graphics etc, but that has now been resolved in 10.04. My only couple of niggles are:-

I had to compile alsa to get the sound working.
Battery life is only an hour with ubuntu, 2 with Windows 7.

The sound issue is easy, just compile alsa ( I have details if you need it) This has to be done each time a new kernel update appears - or maybe there is a soloution?

Battery is a pain, but I think it's ubuntu being power hungry, rather than a problem with the laptop.

Other than that, I love it!

---

### Post by cub on 2010-07-13
As said the ALSA needs compiling after each kernel update. The brightness has to be changed manually through commands, I have not seen a solution there yet.

The battery might be low but the biggest issue there is that I can't go from plugged in to battery. It tells me the battery is empty every time and hibernates. No problem if I boot it up on battery or when I finally get back up after the hibernation. But disconnecting the power cord will hibernate the laptop, every time.

Other than that it works pretty good. I'm not happy about the issue I have with the USB ports and Edirol UA25EX sound card for my studio work but that's pretty specific.

---

### Post by birdmanuk on 2010-07-13
I see a similar problem when I unplug the power cable, however, it doesn't go into hibernate. It just keeps running but says 2 mins of battery left :-(

---

### Post by Jcbpnl on 2010-07-19
> **danyzoca said:**
> Installing latest Catalyst 10.6 driver (Official ATI Proprietary driver) from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") solved all my brigthness control problems. All works without any hacks -> brightness control notifications and even automatic brightness adjustement when plugging the battery out :-) 

All this in a VPC-EB1S1E/BJ.

[COLOR=Red]**First **[/COLOR]remove all fglrx related packages, just do a search by fglrx in Synpatic or Software Center and remove all installed packages.

Then download the file, move to your Home Folder, open up a shell and do:

[HTML]
# chmod +x ati-driver-installer-10-6-x86.x86_64.run 
#./ati-driver-installer-10-6-x86.x86_64.run 
[Follow on-screen instruction, and when finished run...]
# aticonfig --initial [/HTML]Reboot. There you have, on screen brightness controls :-)
(and with this update I've finally been able to watch Blu-Ray 1080p awesomely well, a thing that with the previous driver was impossible).

Thanks a ton for this fix! Worked perfect on my VPCEB290x!

---

### Post by cub on 2010-07-19
> **danyzoca said:**
> Installing latest Catalyst 10.6 driver (Official ATI Proprietary driver) from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") solved all my brigthness control problems. All works without any hacks -> brightness control notifications and even automatic brightness adjustement when plugging the battery out :-) 

All this in a VPC-EB1S1E/BJ.

[COLOR="Red"]**First **[/COLOR]remove all fglrx related packages, just do a search by fglrx in Synpatic or Software Center and remove all installed packages.

Then download the file, move to your Home Folder, open up a shell and do:

[HTML]
# chmod +x ati-driver-installer-10-6-x86.x86_64.run 
#./ati-driver-installer-10-6-x86.x86_64.run 
[Follow on-screen instruction, and when finished run...]
# aticonfig --initial [/HTML]

Reboot. There you have, on screen brightness controls :-)
(and with this update I've finally been able to watch Blu-Ray 1080p awesomely well, a thing that with the previous driver was impossible).
Hmm I have the VPCEB1S1E and it did not work that well for me. Installation seemed fine but when rebooting X did not start and I got some troubleshooting windows to click through, I'm not sure what they all did but eventually I got X up again. The screen is darker than before, but I can't control the brightness with the Fn-buttons.

How can I check which driver I'm actually using now?

---

### Post by birdmanuk on 2010-07-19
Worked a treat for me on my VPCEB1ZOE. It has actually improved the battery life too. And that was the biggest pain point! 

Just watched a DVD and I still get the flicker lines when the screen moves in car chases for example. I can live with that.

---

### Post by blimbo on 2010-07-19
I've got problems coming back to life after suspending - it has worked before, but it seems to hang/stay black about 4 times out of 5 now. I installed the most recent ATI driver recently, but that does seem to change anything.

Cheers,

Tim

---

### Post by cub on 2010-07-20
Anyone notice when the touchpad started to work with the scrolling at the right edge of the pad? I noticed it today so I checked my Mouse settings and the touchpad tab had disappeared.

Any ideas how to get this back and perhaps if the two-finger-scroll is working now?

As a note, my graphic drivers seems to be loading alright after the first struggling reboot. It changes the brightness between on power and battery as well as when idle. I can also change the brightness from the settings window. The Fn+F5/F6 does not work though.

---

### Post by johanbove on 2010-07-20
Thanks so much for posting how to compile the Alsa driver. This works on VPC-EB2Z1E.

---

### Post by sergioaa on 2010-07-27
Hello, friends,

I have a lot of problems with Wifi card (Atheros AR-9285) on my VPCEA1S1E. I'm using 10.04 with backport modules, but problem persists... (I have tried from 2.6.32 - 2.6.35RC1 kernels....)

Anyone is going ok with this wifi card? 

Thank you very much in advance and regards.

---

### Post by wecacuee on 2010-07-29
On my  VPCEA23EN
-Broadcom wifi work OOB !!! (one of my biggest fears)
-ATI Radeon 4500 do not support compiz :(
-No sound (Intel 5 series/3400 chipset)
   +- I believe, i have to install alsa 1.023 

Thanks for sharing all the info,
vikas

---

### Post by wecacuee on 2010-07-29
Copied from DrRush and sound works.
```
sudo apt-get build-essential
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2 -O- | tar -xjf alsa-driver-1.0.23.tar.bz2
cd alsa-driver-1.0.23/
./configure
make
sudo make install
alsamixer # (don't know if this step was necessary since my volume was already enabled)
#reboot
```

---

### Post by wecacuee on 2010-07-29
ati driver support worked.

Downloaded from:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

then did as suggested.

---

### Post by Lazaro21 on 2010-07-31
Hi,

I have a VCEB1EOE and I want to run LinuxMint9 (based on Ubuntu 10.04 so practically the same problems arose). I'm a bit of a newbie so I haven't given upgrading the ALSA driver a proper shot yet but hopefully that will get the sound working. 

However I'm wondering if anyone has a fix for the touchpad, which is not as responsive as in Windows (often difficult to tap click), lacks horizontal and vertical scrolling and any multitouch capabilities. I find this very irritating as it is a good touchpad. Also I get the message that its going to hibernate if i don't plug it in, it doesn't actually hibernate thankfully but it's a little annoying, and the battery life seems much worse than in Windows (although I haven't tested it thoroughly) . 

On the plus side the brightness buttons and function button worked out of the box, and I don't have ATI graphics so no problems there.

If there is nothing that can be done about these problems then I shall have to live with Windoze (although its a close call as to which situation is more irritating)

Alex

---

### Post by cub on 2010-08-02
> **Lazaro21 said:**
> However I'm wondering if anyone has a fix for the touchpad, which is not as responsive as in Windows (often difficult to tap click), lacks horizontal and vertical scrolling and any multitouch capabilities. I find this very irritating as it is a good touchpad.
With one of the latest updates my touchpad started to work with horizontal scrolling. As for the other functions, still no go.

---

### Post by latitudehopper on 2010-08-04
> **danyzoca said:**
> Installing latest Catalyst 10.6 driver (Official ATI Proprietary driver) from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") solved all my brigthness control problems. All works without any hacks -> brightness control notifications and even automatic brightness adjustement when plugging the battery out :-) 

All this in a VPC-EB1S1E/BJ.

[COLOR=Red]**First **[/COLOR]remove all fglrx related packages, just do a search by fglrx in Synpatic or Software Center and remove all installed packages.

Then download the file, move to your Home Folder, open up a shell and do:

[HTML]
# chmod +x ati-driver-installer-10-6-x86.x86_64.run 
#./ati-driver-installer-10-6-x86.x86_64.run 
[Follow on-screen instruction, and when finished run...]
# aticonfig --initial [/HTML]Reboot. There you have, on screen brightness controls :-)
(and with this update I've finally been able to watch Blu-Ray 1080p awesomely well, a thing that with the previous driver was impossible).

Does anyone else do this and get really shoddy performance compared to the OOB option? when i log in the fade is so chunky.  Am I missing something?

---

### Post by cub on 2010-08-05
I have not seen any chunkiness with the fade. I just installed the 10.7 ATI driver and now everything works on my VPC EB1S1E including the Fn-keys.

---

### Post by claudios on 2010-08-05
> **sergioaa said:**
> Hello, friends,

I have a lot of problems with Wifi card (Atheros AR-9285) on my VPCEA1S1E. I'm using 10.04 with backport modules, but problem persists... (I have tried from 2.6.32 - 2.6.35RC1 kernels....)

Anyone is going ok with this wifi card? 

Thank you very much in advance and regards.

Hi sergioaa,
I have a Vaio VPCEB1J8E and I've been dealing with the same problem for some time and experiment in the same way you did but the wireless was unreliable dropping always to 1 M/s. Googling I found this page 
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
I tried all drivers and just one worked, the second one, compat-wireless-2.6.33.6.tar.bz2
Performance are not excellent like in windows7, vista and xp but are good.
Now I can use my laptop with ubuntu.
Sometime I watch a movie on my network share but it freezes too many times so I have to copy it locally first... better than nothing...
I'd really like to know what the problem is... 
I was thinking to change the internal wifi with an intel but I fear to experiment opening a new laptpop...
Regards

---

### Post by danyzoca on 2010-08-06
> **cub said:**
> I have not seen any chunkiness with the fade. I just installed the 10.7 ATI driver and now everything works on my VPC EB1S1E including the Fn-keys.

I installed the 10.7 driver as well, but I got some strange problems, specially with colors. Blues turned into green, white in pink and all strange color behaviours. They're occasional, but rather annoying so I got back to 10.6. It wait and see for the next Catalyst 10.*x* driver ;)

---

### Post by wecacuee on 2010-08-09
> **cub said:**
> 

The battery might be low but the biggest issue there is that I can't go from plugged in to battery. It tells me the battery is empty every time and hibernates. No problem if I boot it up on battery or when I finally get back up after the hibernation. But disconnecting the power cord will hibernate the laptop, every time.


I was affected by the following bug on VPCEA23EN:
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190)

Workaround:
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false

---

### Post by cub on 2010-08-09
> **wecacuee said:**
> I was affected by the following bug on VPCEA23EN:
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190)

Workaround:
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
Great! Do I need to run that every time I boot up or is this one time enough?

---

### Post by claudios on 2010-08-10
> **wecacuee said:**
> I was affected by the following bug on VPCEA23EN:
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190)

Workaround:
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false

WOW!
that solved my last problem with my vaio VPCEB1J8E and makes this laptop usable with Ubuntu 10.04.
Now the icon battery with the message 'Laptop battery discharging...' is always present when power is connected, funny :-)
but better than before.
Hope that some new kernel release will make everything to work properly (ar9285,audio,power management).
Thanks.

---

### Post by lyovushka on 2010-08-10
Thanks guys, you are awesome. Managed to make my brothers laptop usable with Ubuntu 10.04 thanks to your posts. Keep up the great job!

---

### Post by ichramm on 2010-08-11
> **ff670099 said:**
> Hello, unfortunately it doesn't work for me. I'm missing something?

Thank you!


Make sure the files

```

/etc/acpi/brightup.sh
/etc/acpi/brightdown.sh

```
are executable
```

sudo chmod +x /etc/acpi/brightup.sh
sudo chmod +x /etc/acpi/brightdown.sh

```
It should work like a charm :P

---

### Post by Charbs on 2010-08-16
Hey guys. 

Im planning on purchasing the  VPC-EA24FM or VPC-EA22FX. 

Im assuming that I will have all the same problems with either of those 2 models, that everyone else has had in this thread so far.

I guess all the VPC-E models will react the exact same to Ubuntu. Does anyone have one of those exact models, and can speak to their experience with them?

Also, does anyone know exactly how the VAIO model numbers are determined?

---

### Post by asarefin on 2010-09-20
[FONT=Courier New]I had the same problem and was going nuts. Found it to be an issue with  linux kernel 2.6.32-24 (which made it's way to the Ubuntu repositories a  few days ago - you probably just got it while running updates). I  rolled back to 2.6.32-23 and now I can install any version of Catalyst  again, including the new 10.9 (fglrx 8.771).

Just install the following from Synaptic:[/FONT] [FONT=Courier New]
linux-headers-2.6.32-23
linux-headers-2.6.32-23-generic
linux-image-2.6.32-23-generic

It should update grub for you automatically. Next time you reboot, you  should presented an option for which kernel you'd like to use. Select  the -23 version and install Catalyst again. It shoudld work now. [/FONT] [FONT=Courier New]

You can either leave -24 there for now or remove it. I would also  install StartupManager from synaptic to help you manage grub if you are  going to keep several images to boot to.[/FONT] [FONT=Courier New]

Hope that helps! Frustrated the hell outta me for a bit.[/FONT] 

source here: [http://www.phoronix.com/forums/showthread.php?p=148453](http://www.phoronix.com/forums/showthread.php?p=148453).

Now running ubutnu 10.04 with no problem, just fixed alsa by updating

---

### Post by johanbove on 2010-10-03
:-k Maybe it would be nice if all Sony Vaio users would unite in the "Sony users" group of this forum:
[http://ubuntuforums.org/group.php?groupid=560](http://ubuntuforums.org/group.php?groupid=560)

---

### Post by cub on 2010-10-17
Yesterday I did an upgrade through Update Manager to 10.10. It didn't work. It would never start X and the screen was sometimes going crazy.

Instead I downloaded the 10.10 CD (amd64) and re-installed this morning. That worked as supposed to I believe. Some comments:

Audio worked out-of-the-box. No need for alsa upgrade as in 10.04.

ATI driver was suggested and I installed them, seems to work fine just as before. [edit] 
The Brightness control does not work with the Fn-keys.

The mouse-pad is still no recognized and therefore I can't turn it off when writing (as with other pc's). Very annoying.

I look forward to test out my system with my Edirol UA-25EX sound card, but that's for another day.

---

### Post by doopy on 2010-11-09
Some information about 64-bit Ubuntu versions 10.04 and 10.10 on Sony Vaio VPC-EA2S1E (or VPCEA2S1E).

For version 10.04, the following worked out-of-the-box:
[LIST]
[*]Network (via cable)
[*]Wireless networking (also WPA2)
[*]Bluetooth
[*]eSATA
[*]Touchpad was recognized and worked ok
[*]HDMI up to resolution 1920x1080
[*]DVI using HDMI to DVI converter up to resolution 1920x1200 (the highest I tested
[/LIST]

What doesn't work out-of-the-box on 10.04
[LIST]
[*]Sound
[*]Screen brightness control (Fn-keys or Gnome applet)
[/LIST]


Ubuntu 10.10 version corrected all the problems I had with version 10.04. I cannot control screen brightness with Fn-keys, but this time Gnome applet works (although when clicking the applet, the only way to change brightness is to use arrow keys up and down).

I'm quite happy with it now! :guitar:

---

### Post by trouty187 on 2010-12-17
Hi everyone,
             Looking at custom ordering a VPCEB3X5E from sony.com with the following hardware:

Core i3
4GB RAM
320GB 7200rpm HDD
ATI Radeon HD5650 HD
1366x768 screen

Would just like some confirmation on what will work on an up to date version of Ubuntu 10.10 64bit (especially regarding the ATI 5650), as once ordered, it will be near impossible to send back. I don't mind editing a few config files etc. as long as I can get things working in the end...

I've noticed this thread has gone quiet for the last couple of months, does this mean everyone has been able to obtain a decent level of usability with recent updates?
Many Thanks
Rich

---

### Post by cub on 2010-12-17
> **trouty187 said:**
> I've noticed this thread has gone quiet for the last couple of months, does this mean everyone has been able to obtain a decent level of usability with recent updates?
Many Thanks
Rich
No, it means nothing has changed...for good or worse.

---

### Post by johanbove on 2010-12-20
The 56+ graphic card should work out-of-the-box without desktop effects. I personally installed the AMD linux driver and am quite happy with it.

---

### Post by trouty187 on 2010-12-20
OK, cheers for the info guys... Are there any differences in functionality in 10.10 64bit between the AMD driver and the one from the Ubuntu repositories?

---

### Post by johanbove on 2010-12-21
Didn't do much comparison on performance since I don't play any games, but mainly I install the AMD catalyst drivers because I like the Catalyst Control Center ;)

---

### Post by Niels_D on 2011-01-30
I have a 3rd generation Sony VAIO E-series (VPC-EC3C5E, purchased januari 2011) with the following specs:

Intel® CoreTM i5-460M, 2,53GHz
ATI MobilityRadeon HD5650 1GB
4 GB 1066MHz DDR3-SDRAM

I had to do the following to make **Kubuntu 10.10** **x64** work:
=========================================================================

                       [SIZE=2]**Fix touchpad**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Edit     /etc/default/grub from:[/SIZE]
     [SIZE=2]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash"
```[/SIZE]     [SIZE=2]to:[/SIZE]
     [SIZE=2]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```[/SIZE]
[/LIST]
 
[SIZE=2]**ATI Mobility Radeon HD 9550 drivers**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Install     the fglrx drivers     with KpackageKit.[/SIZE]
[*][SIZE=2]Activate     with &#8221;Additional Drivers&#8221;.[/SIZE]
[*][SIZE=2]Reboot.[/SIZE]
[*][SIZE=2]After     installation of the     Catalyst driver, execute    the following commands:

[/SIZE]```
$ sudo aticonfig --initial -f
$ sudo aticonfig --input=/etc/X11/xorg.conf &#8211;tls=1
```
[/LIST]
  
   [SIZE=2]    Rebooting now displays a &#8220;simple&#8221; bootscreen in low resolution, but it turns into hi-res mode when asking for     login credentials. 
Driver seems stable (CCC also works fine) and performance is much better.[/SIZE]


[SIZE=2]**Solve low-res bootscreen**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Add to     /etc/default/grub (_uncomment_):

[/SIZE]```
GRUB_GFXMODE= [desired resolution (eg. 1920x1080)]
GRUB_GFXPAYLOAD_LINUX=keep
```
[*][SIZE=2]Execute:
 [/SIZE]```
$ echo FRAMEBUFFER=y     | sudo tee /etc/initramfs-tools/conf.d/splash
```
[*][SIZE=2]Execute:
[/SIZE]```
$ sudo update-grub &&     sudo update-initramfs -u
```
[*][SIZE=2]Personalization of     the splash screens can be done in the System settings menu, but     don't forget the sudo update-grub afterwards![/SIZE]
[/LIST]
  
 [SIZE=2]**Brightness adjustment with Fn keys (Fn+F5/Fn+F6)**[/SIZE]
 
[LIST=1]
[*][SIZE=2]First of all you need     to define code of keys. For it write in console:[/SIZE][B][SIZE=2]
[/SIZE][/B]```
acpi_listen
```
[/LIST]
  
[LIST=1]
[*][SIZE=2]Then push keys what     you need. Usually it shows two code. First - when press in, and     second - press out.

So now you should know your code. For me it was[/SIZE][B][SIZE=2]

[/SIZE][/B][SIZE=2]SNC 00000001 0000001[/SIZE][SIZE=2]1[/SIZE]
[/LIST]
   
[LIST=1]
[*][SIZE=2]Then go to directory     "/etc/acpi". [/SIZE]
[*][SIZE=2]In     "[/SIZE][SIZE=2]events[/SIZE][SIZE=2]"     create file "[/SIZE]*[SIZE=2]sonybright-up[/SIZE]*[SIZE=2]"     [/SIZE][SIZE=2]with     the following code:

[/SIZE]```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/actions/sonybright.sh up
```[SIZE=2]

(event - means code of key, and action - script, which will be executed after you press this key)

[/SIZE]
[*][SIZE=2]A[/SIZE][SIZE=2]nalogically     create "[/SIZE]*[SIZE=2]sonybright-down[/SIZE]*[SIZE=2]":

[/SIZE]                      p { margin-bottom: 0.21cm; }```
event=sony/hotkey     SNC 00000001 00000010
action=/etc/acpi/actions/sonybright.sh     down
```
[*][SIZE=2]The     last part - you need to create script "[/SIZE]*[SIZE=2]sonybright.sh[/SIZE]*[SIZE=2]",     which will change brightness of your display. 
So I wrote it in bash,     but you can write your own in another language(perl or maybe     python):[/SIZE]

```
#!/bin/bash

if [ "x$1" = "xdown" ]; then
expr `cat /sys/class/backlight/acpi_video0/brightness` \- 1 > /sys/class/backlight/acpi_video0/brightness

elif [ "x$1" = "xup" ]; then
expr `cat /sys/class/backlight/acpi_video0/brightness` \+ 1 > /sys/class/backlight/acpi_video0/brightness

else
echo "Error">/home/<user>/bright_script.log
fi
```
[/LIST]
  
[SIZE=2]**Fix RAM-suspend**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Create files:     
/etc/pm/config.d/00sleep_module 
/etc/pm/config.d/unload_module[/SIZE]
[*][SIZE=2]Add     line to files : 

[/SIZE]```
SUSPEND_MODULES="xhci-hcd"
```
[/LIST]
 

 [SIZE=2]**Get rid of ****&#8220;****MCP power or thermal limit&#8221; ****messages**** in kernel log**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Edit file     /etc/modprobe.d/blacklist.conf [/SIZE]
[*][SIZE=2]Add     at the end of the file:[/SIZE]

```
&#8220;blacklist     intel_ips&#8221;
```
[*][SIZE=2]Save file and     restart. [/SIZE]
[/LIST]
  
=========================================================================

The only things that are not fully functional at the moment are:


[LIST=1]
[*]Brightness control doesn't show applet
I tried using the "fake key" that is used by other brightness controls to get this to work, but it isn't as simple as it looks... :p
[*]Fan control isn't optimal (also power state C6 of the i5 processor isn't supported):

Powertop shows:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 8,3%)       Turbo Mode     0,1%
polling           0,0ms ( 0,0%)         2,54 Ghz     0,0%
C1 mwait          0,4ms ( 1,5%)         2,40 Ghz     0,0%
C2 mwait          1,4ms (25,1%)         1,74 Ghz     0,0%
C3 mwait          2,0ms (65,0%)         1199 Mhz    99,9%
```The i5 460M datasheet says that it should support:

C0
C1
C1E
C3
C6

I did't pay much attention to this yet, but I can imagine it is not easy to solve this.
Maybe the overall intel Core ix series is better supported in 11.04?
[/LIST]
If someone has something to add to this list, please let me know!
Thanks!

---

### Post by fasoulas on 2011-01-31
I have a sony vaio EB3M1E
Specs:
i3 370M 2.4Ghz
4 gb ram
ati radeaon 5650 
500 gb HD

I would like to ask how did you partitioned your Hard Disk in order to install ubuntu on it?

My HD already has 3 partitions as it comes from the factory
- win7 
- system reserved
- restore

On an ubuntu installation you normally need to make 2 new parttions on the hard disk, one for ubuntu and one for swap.
But as i know you can have at max 4 partitions on an HD.
So how am i gonna install ubuntu on this laptop??

---

### Post by Niels_D on 2011-01-31
I simply deleted all the Sony rubbish and created a full size (k)ubuntu partition and a 11Gb swap partition (which is in fact a bit too big, I still have to find out how to that afterwards).

If you still want to use Windows 7 on a multiboot system it needs a different configuration (but you can also use VMware or VirtualBox).

---

### Post by trouty187 on 2011-02-01
> **fasoulas said:**
> I have a sony vaio EB3M1E
Specs:
i3 370M 2.4Ghz
4 gb ram
ati radeaon 5650 
500 gb HD

I would like to ask how did you partitioned your Hard Disk in order to install ubuntu on it?

My HD already has 3 partitions as it comes from the factory
- win7 
- system reserved
- restore

On an ubuntu installation you normally need to make 2 new parttions on the hard disk, one for ubuntu and one for swap.
But as i know you can have at max 4 partitions on an HD.
So how am i gonna install ubuntu on this laptop??

I kept the 3 primary partitions but resized the Windows 7 partition to roughly 70GB and created an extended partition in the newly created free space. An extended partition acts like a container allowing several "logical" partitions to be created inside of it. I then created the required partitions within the extended partition and told the Ubuntu installer to use these when I installed.

My set up is as follows:

Recovery 10GB NTFS (primary)
System Reserved 100MB NTFS (primary)
Windows 7 70GB NTFS (primary)
Extended Partition containing...
[INDENT]Ubuntu 10GB EXT4 (logical)[/INDENT]
[INDENT]/home 200GB EXT4 (logical)[/INDENT]
[INDENT]swap 4GB (logical)[/INDENT]

You can adjust the partition sizes depending upon your requirements and hard drive capacity (I'd leave the recovery partition well alone though!) Just remember your swap partition must be at least the size of the amount of RAM your system has or hibernate will not work correctly.

Creating a separate /home partition is optional (although it does have its advantages) you could just create a larger Ubuntu partition and have your home folder mounted in there with the OS instead. There's plenty more info about this in the Ubuntu forums or on Google...
Hope this helps...

---

### Post by fasoulas on 2011-02-01
> **trouty187 said:**
> I kept the 3 primary partitions but resized the Windows 7 partition to roughly 70GB and created an extended partition in the newly created free space. An extended partition acts like a container allowing several "logical" partitions to be created inside of it. I then created the required partitions within the extended partition and told the Ubuntu installer to use these when I installed.

My set up is as follows:

Recovery 10GB NTFS (primary)
System Reserved 100MB NTFS (primary)
Windows 7 70GB NTFS (primary)
Extended Partition containing...
[INDENT]Ubuntu 10GB EXT4 (logical)[/INDENT]
[INDENT]/home 200GB EXT4 (logical)[/INDENT]
[INDENT]swap 4GB (logical)[/INDENT]

You can adjust the partition sizes depending upon your requirements and hard drive capacity (I'd leave the recovery partition well alone though!) Just remember your swap partition must be at least the size of the amount of RAM your system has or hibernate will not work correctly.

Creating a separate /home partition is optional (although it does have its advantages) you could just create a larger Ubuntu partition and have your home folder mounted in there with the OS instead. There's plenty more info about this in the Ubuntu forums or on Google...
Hope this helps...

Very helpfull info thanks a lot ,i didn't know that about swap partition.

SO i was thinking of making an extented partition and make another 3 partitions inside it ubuntu(ext4),swap and one for data(fat32).

Does the logical partitions have any difference in performance?

Thanks a lot again

---

### Post by trouty187 on 2011-02-01
> **fasoulas said:**
> Very helpfull info thanks a lot ,i didn't know that about swap partition.

SO i was thinking of making an extented partition and make another 3 partitions inside it ubuntu,swap and one for data.

Does the logical partitions have any difference in performance?

Thanks a lot again

Performance should be the same, I've had installs on primary and logical partitions in the past and have never noticed a difference.

There are numerous articles dotted around the Internet about setting up a home partition for your data. I would advise reading several of these before you proceed, its always best to know all the pitfalls before you start moving around your personal data, I don't mean to state the obvious here but ALWAYS make sure you've got everything backed up too... :)

---

### Post by fasoulas on 2011-02-01
> **trouty187 said:**
> Performance should be the same, I've had installs on primary and logical partitions in the past and have never noticed a difference.

There are numerous articles dotted around the Internet about setting up a home partition for your data. I would advise reading several of these before you proceed, its always best to know all the pitfalls before you start moving around your personal data, I don't mean to state the obvious here but ALWAYS make sure you've got everything backed up too... :)

Ok thanks a lot
I will do some research on the net and try to partition the disk.

Sorry for getting a little out of the subject of the topic put i posted here because i though is better getting an advice from someone who has a sony e series rather than posting to a more general thread.

As soon as i install ubuntu 10.10 i will post back about any issues with hardware support.

---

### Post by fasoulas on 2011-02-01
> **Niels_D said:**
> I have a 3rd generation Sony VAIO E-series (VPC-EC3C5E, purchased januari 2011) with the following specs:

Intel® CoreTM i5-460M, 2,53GHz
ATI MobilityRadeon HD5650 1GB
4 GB 1066MHz DDR3-SDRAM

I had to do the following to make **Kubuntu 10.10** **x64** work:
=========================================================================

                       [SIZE=2]**Fix touchpad**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Edit     /etc/default/grub from:[/SIZE]
     [SIZE=2]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash"
```[/SIZE]     [SIZE=2]to:[/SIZE]
     [SIZE=2]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```[/SIZE]
[/LIST]
 
[SIZE=2]**ATI Mobility Radeon HD 9550 drivers**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Install     the fglrx drivers     with KpackageKit.[/SIZE]
[*][SIZE=2]Activate     with ”Additional Drivers”.[/SIZE]
[*][SIZE=2]Reboot.[/SIZE]
[*][SIZE=2]After     installation of the     Catalyst driver, execute    the following commands:

[/SIZE]```
$ sudo aticonfig --initial -f
$ sudo aticonfig --input=/etc/X11/xorg.conf –tls=1
```
[/LIST]
  
   [SIZE=2]    Rebooting now displays a “simple” bootscreen in low resolution, but it turns into hi-res mode when asking for     login credentials. 
Driver seems stable (CCC also works fine) and performance is much better.[/SIZE]


[SIZE=2]**Solve low-res bootscreen**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Add to     /etc/default/grub (_uncomment_):

[/SIZE]```
GRUB_GFXMODE= [desired resolution (eg. 1920x1080)]
GRUB_GFXPAYLOAD_LINUX=keep
```
[*][SIZE=2]Execute:
 [/SIZE]```
$ echo FRAMEBUFFER=y     | sudo tee /etc/initramfs-tools/conf.d/splash
```
[*][SIZE=2]Execute:
[/SIZE]```
$ sudo update-grub &&     sudo update-initramfs -u
```
[*][SIZE=2]Personalization of     the splash screens can be done in the System settings menu, but     don't forget the sudo update-grub afterwards![/SIZE]
[/LIST]
  
 [SIZE=2]**Brightness adjustment with Fn keys (Fn+F5/Fn+F6)**[/SIZE]
 
[LIST=1]
[*][SIZE=2]First of all you need     to define code of keys. For it write in console:[/SIZE][B][SIZE=2]
[/SIZE][/B]```
acpi_listen
```
[/LIST]
  
[LIST=1]
[*][SIZE=2]Then push keys what     you need. Usually it shows two code. First - when press in, and     second - press out.

So now you should know your code. For me it was[/SIZE][B][SIZE=2]

[/SIZE][/B][SIZE=2]SNC 00000001 0000001[/SIZE][SIZE=2]1[/SIZE]
[/LIST]
   
[LIST=1]
[*][SIZE=2]Then go to directory     "/etc/acpi". [/SIZE]
[*][SIZE=2]In     "[/SIZE][SIZE=2]events[/SIZE][SIZE=2]"     create file "[/SIZE]*[SIZE=2]sonybright-up[/SIZE]*[SIZE=2]"     [/SIZE][SIZE=2]with     the following code:

[/SIZE]```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/actions/sonybright.sh up
```[SIZE=2]

(event - means code of key, and action - script, which will be executed after you press this key)

[/SIZE]
[*][SIZE=2]A[/SIZE][SIZE=2]nalogically     create "[/SIZE]*[SIZE=2]sonybright-down[/SIZE]*[SIZE=2]":

[/SIZE]                      p { margin-bottom: 0.21cm; }```
event=sony/hotkey     SNC 00000001 00000010
action=/etc/acpi/actions/sonybright.sh     down
```
[*][SIZE=2]The     last part - you need to create script "[/SIZE]*[SIZE=2]sonybright.sh[/SIZE]*[SIZE=2]",     which will change brightness of your display. 
So I wrote it in bash,     but you can write your own in another language(perl or maybe     python):[/SIZE]

```
#!/bin/bash

if [ "x$1" = "xdown" ]; then
expr `cat /sys/class/backlight/acpi_video0/brightness` \- 1 > /sys/class/backlight/acpi_video0/brightness

elif [ "x$1" = "xup" ]; then
expr `cat /sys/class/backlight/acpi_video0/brightness` \+ 1 > /sys/class/backlight/acpi_video0/brightness

else
echo "Error">/home/<user>/bright_script.log
fi
```
[/LIST]
  
[SIZE=2]**Fix RAM-suspend**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Create files:     
/etc/pm/config.d/00sleep_module 
/etc/pm/config.d/unload_module[/SIZE]
[*][SIZE=2]Add     line to files : 

[/SIZE]```
SUSPEND_MODULES="xhci-hcd"
```
[/LIST]
 

 [SIZE=2]**Get rid of ****“****MCP power or thermal limit” ****messages**** in kernel log**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Edit file     /etc/modprobe.d/blacklist.conf [/SIZE]
[*][SIZE=2]Add     at the end of the file:[/SIZE]

```
“blacklist     intel_ips”
```
[*][SIZE=2]Save file and     restart. [/SIZE]
[/LIST]
  
=========================================================================

The only things that are not fully functional at the moment are:


[LIST=1]
[*]Brightness control doesn't show applet
I tried using the "fake key" that is used by other brightness controls to get this to work, but it isn't as simple as it looks... :p
[*]Fan control isn't optimal (also power state C6 of the i5 processor isn't supported):

Powertop shows:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 8,3%)       Turbo Mode     0,1%
polling           0,0ms ( 0,0%)         2,54 Ghz     0,0%
C1 mwait          0,4ms ( 1,5%)         2,40 Ghz     0,0%
C2 mwait          1,4ms (25,1%)         1,74 Ghz     0,0%
C3 mwait          2,0ms (65,0%)         1199 Mhz    99,9%
```The i5 460M datasheet says that it should support:

C0
C1
C1E
C3
C6

I did't pay much attention to this yet, but I can imagine it is not easy to solve this.
Maybe the overall intel Core ix series is better supported in 11.04?
[/LIST]
If someone has something to add to this list, please let me know!
Thanks!

Very very helpful tutorial thanks for posting it here,
No problems after following it, except the brightness ,it works with the fn keys on the ubuntu 10.10 32bit installation.

---

### Post by Niels_D on 2011-02-02
Thanks!
I hope someone is able to help improve the fan control and power state.
As you might have experienced the fan is pretty loud and the laptop generates quite some heat.

I searched on the net but didn't find any usable info yet.

---

### Post by cub on 2011-02-02
> **fasoulas said:**
> Very helpfull info thanks a lot ,i didn't know that about swap partition.

SO i was thinking of making an extented partition and make another 3 partitions inside it ubuntu(ext4),swap and one for data(fat32).

Does the logical partitions have any difference in performance?

Thanks a lot again
Just as others above I resized my windows partition inside of Windows. Then I made one root and swap partition in the new space. I could have made a /home but I don't remember now why I didn't.

Why will you make a FAT32 data partition? Will you access it from Windows?

---

### Post by fasoulas on 2011-02-02
> **cub said:**
> Just as others above I resized my windows partition inside of Windows. Then I made one root and swap partition in the new space. I could have made a /home but I don't remember now why I didn't.

Why will you make a FAT32 data partition? Will you access it from Windows?

Yes i wanted to have access from windows.
I finally made  just 2 logical partitons ubuntu and swap only ,i wanted to se if that will work and later i might make a partition for my data only.

**Niels_D** as for the fan ,i haven't noticed any difference from when running in windwos ,and some times i can't even hear it, if i notice a difference in fan speed i wil report it here

i found something about regulatig the fan speed although a havent't used it myself you might want to check it out
[http://www.ubuntugeek.com/how-to-silence-sony-vaio-laptop-fan-using-vaiofand.html#more-3054](http://www.ubuntugeek.com/how-to-silence-sony-vaio-laptop-fan-using-vaiofand.html#more-3054)
and here
[http://vaio-utils.org/fan/](http://vaio-utils.org/fan/)

---

### Post by M!SF!TS on 2011-02-02
I am thinking about Purchasing a Sony EB490X
Here are the Specifications:

Intel® Core™ i5-580M processor (2.66GHz) with Turbo Boost up to 3.33GHz
Genuine Windows® 7 Home Premium 64-bit
Gunmetal Black
320GB Hard Disk Drive (7200rpm) (Reg. $50.00)
6GB (4GBx1 + 2GBx1) DDR3-SDRAM-1066 (Reg. $100.00)
15.5" Full HD VAIO Premium Display (1920x1080)
ATI Mobility Radeon™ HD 5650 GPU (1GB VRAM)
CD/DVD Player / Burner
Standard capacity battery
*Copied from Sony.com



I was wondering if anyone could tell me what compatibility issues I may run into when running ubuntu on this machine so I can make a more informed purchase prior to buying this computer.

-Thanks

---

### Post by fasoulas on 2011-02-02
> **M!SF!TS said:**
> I am thinking about Purchasing a Sony EB490X
Here are the Specifications:

Intel® Core&#8482; i5-580M processor (2.66GHz) with Turbo Boost up to 3.33GHz
Genuine Windows® 7 Home Premium 64-bit
Gunmetal Black
320GB Hard Disk Drive (7200rpm) (Reg. $50.00)
6GB (4GBx1 + 2GBx1) DDR3-SDRAM-1066 (Reg. $100.00)
15.5" Full HD VAIO Premium Display (1920x1080)
ATI Mobility Radeon&#8482; HD 5650 GPU (1GB VRAM)
CD/DVD Player / Burner
Standard capacity battery
*Copied from Sony.com



I was wondering if anyone could tell me what compatibility issues I may run into when running ubuntu on this machine so I can make a more informed purchase prior to buying this computer.

-Thanks

You will most likely face the same problems as those posted on this thread ,so read the posts of the thread and you will get an idea.

As you will see most of the problems can be solved very easy just follow the instructions provided.

---

### Post by M!SF!TS on 2011-02-02
> **fasoulas said:**
> You will most likely face the same problems as those posted on this thread ,so read the posts of the thread and you will get an idea.

As you will see most of the problems can be solved very easy just follow the instructions provided.

Yeah I kind of felt stupid for posting that... sorry


But how about Hyper-Threading and turbo boost technology? does ubuntu or the linux kernal support these? or are they a hardware thing? Im not that computer savy...

---

### Post by Niels_D on 2011-02-04
> **fasoulas said:**
> Yes i wanted to have access from windows.
I finally made  just 2 logical partitons ubuntu and swap only ,i wanted to se if that will work and later i might make a partition for my data only.

**Niels_D** as for the fan ,i haven't noticed any difference from when running in windwos ,and some times i can't even hear it, if i notice a difference in fan speed i wil report it here

i found something about regulatig the fan speed although a havent't used it myself you might want to check it out
[http://www.ubuntugeek.com/how-to-silence-sony-vaio-laptop-fan-using-vaiofand.html#more-3054](http://www.ubuntugeek.com/how-to-silence-sony-vaio-laptop-fan-using-vaiofand.html#more-3054)
and here
[http://vaio-utils.org/fan/](http://vaio-utils.org/fan/)

Ok, I don't actually know how it was with Windows, as this was the first thing I removed when I opened the laptop for the first time, but if it is mostly the same I don't bother it :)
The vaiofand unfortunately doesn't work on the latest VAIO models, I already tried that.

---

### Post by Niels_D on 2011-02-07
I discovered that in KDE 4.6.0 the display brightness applet is working when the display brightness is adjusted via the power manager.
While I am using a manual script (as described in my tutorial) I cannot get this to work with my Fn keys.
 
Does someone have an idea of how to implement this?
Or does the reaction of the applet mean that I can discard my manual script? :eek:
 
Thanks!!!

---

### Post by Doubleaadogg on 2011-02-14
I was wondering if current owners could give me an idea of battery life for the new EB series. I am most interested in the ATI 5650 equipped boxes with big batteries. If you can compare the big and standard battery that would be most helpful. The big battery doesn't look that much bigger in the pictures, how much extra life do you get? Have the newer catalyst drivers helped consumption? How much of a difference does changing the brightness make on battery life? Those sorts of things. If you have both Windows and Ubuntu times, that would be awesome. 

Also, does deleting the windows partition break the splashtop browser? I'm guessing it does, but maybe splashtop has all its own drivers.

Judging by the posts in this forum, it looks like the big issues eg. screen brightness control, sound, and graphics are annoying but to a degree, fixable.

---

### Post by M!SF!TS on 2011-02-14
I just got my new Sony! I like this computer very nice...


I dont think the Graphics card works... When I boot my computer up, you know the 


                                        Ubuntu
                                     o  o  o  o  o

Screen? when you first turn it on...
That is all in text it looks like this


                                     Ubuntu 10.10
                                         ....


Than it says some stuff like i915? or something and graphics... I was wondering if this means my graphics card is not really working good and if anyone can help...

Sorry I am a newbie when it comes to getting my computer to work

Any help is appreciated... I am wondering if someone already fixed this issue and could point me to it I have a hard time reading whats what here and I dont like throwing random code into my terminal... I see on page 9 or so someone fixed there graphics driver but that was for kubuntu i just got regular old ubuntu...

Thanks alot for who ever steers me in the right direction
and sorry for making this thread look like crap... newbies tend to do that.... I know...

---

### Post by cub on 2011-02-15
> **M!SF!TS said:**
> I just got my new Sony! I like this computer very nice...


I dont think the Graphics card works... When I boot my computer up, you know the 


                                        Ubuntu
                                     o  o  o  o  o

Screen? when you first turn it on...
That is all in text it looks like this


                                     Ubuntu 10.10
                                         ....


Than it says some stuff like i915? or something and graphics... I was wondering if this means my graphics card is not really working good and if anyone can help...

Sorry I am a newbie when it comes to getting my computer to work

Any help is appreciated... I am wondering if someone already fixed this issue and could point me to it I have a hard time reading whats what here and I dont like throwing random code into my terminal... I see on page 9 or so someone fixed there graphics driver but that was for kubuntu i just got regular old ubuntu...

Thanks alot for who ever steers me in the right direction
and sorry for making this thread look like crap... newbies tend to do that.... I know...

As for the graphics and booting, I get i915 as well. I did some searches though I don't remember all the details I then decided it was not anything major and I'd ignore the message (and the extra boot time). There was some suggestions to fix it, but to me it was more hassle than to leave it be.
Does the graphic work fine when you get to the login page? Sometimes my laptop show more textbased stuff while booting and sometimes the more "fancy" with graphics. But as long as the login page show up at the end I have not bothered about it.
Fixing the graphic driver I think was some time ago. With 10.10 I did not have to replace any drivers myself but are using the ATI drivers Ubuntu suggests.

---

### Post by M!SF!TS on 2011-02-15
Yeah the login screen for me looks and works fine. I was just wondering if there is a fix to the i915 graphic turbo disabled text boot thing we are talking about where the boot splash looks like

Ubuntu 10.10
....

so just leave it be... Damn it lol, I find it annoying but your saying it is more annoying to have to fix it... I will take your word on it then.

Thanks

Misfits

---

### Post by fasoulas on 2011-02-16
> **M!SF!TS said:**
> I just got my new Sony! I like this computer very nice...


I dont think the Graphics card works... When I boot my computer up, you know the 


                                        Ubuntu
                                     o  o  o  o  o

Screen? when you first turn it on...
That is all in text it looks like this


                                     Ubuntu 10.10
                                         ....


Than it says some stuff like i915? or something and graphics... I was wondering if this means my graphics card is not really working good and if anyone can help...

Sorry I am a newbie when it comes to getting my computer to work

Any help is appreciated... I am wondering if someone already fixed this issue and could point me to it I have a hard time reading whats what here and I dont like throwing random code into my terminal... I see on page 9 or so someone fixed there graphics driver but that was for kubuntu i just got regular old ubuntu...

Thanks alot for who ever steers me in the right direction
and sorry for making this thread look like crap... newbies tend to do that.... I know...

Go to the 9th page of this thread ,then go the last post of the page ,it's by **Niels_D**.

Then go to the point tha says fix low resolution screen and try that is think a had the same problem with you when i first installed ubuntu ,remember to back up the files that you will change in case something goes wrong

---

### Post by Niels_D on 2011-03-02
Yesterday I received the following update:

[IMG]http://pic80.picturetrail.com/VOL1953/13150501/23400396/395484103.jpg[/IMG]

I think it comes from the backport repository, as I am using KDE 4.6.0 on Kubuntu 10.10.
However, this update solved the Fn brightness problem only for 50%:

When I want to lower display brightness, this works fine (also with the indication applet):

[IMG]http://pic80.picturetrail.com/VOL1953/13150501/23400396/395484616.jpg[/IMG]

But when I want to increase display britghtness, the sceen flickers and eventually doesn't do anything.

Is there somebody else with a VAIO who has KDE 4.6.0 and got this update?
If yes, what are your experiences?

EDIT: 
I also noticed that there is a Sony Notebook control driver available, is this new?

[IMG]http://pic80.picturetrail.com/VOL1953/13150501/23400396/395484406.jpg[/IMG]

---

### Post by trouty187 on 2011-03-02
I am running Ubuntu 10.10 64bit, with the latest update brightness control using 'fn' keys is now working perfectly (for both increasing and decreasing the brightness) in Gnome.

---

### Post by Niels_D on 2011-03-03
And what model VAIO do you use?

---

### Post by trouty187 on 2011-03-03
> **Niels_D said:**
> And what model VAIO do you use?

Niels,
See post #85 on page 9 of this thread for full spec & model number...
:)

---

### Post by Niels_D on 2011-03-03
Ah ok, seems like a model from the same generation as mine.
What version of Ubuntu are you using? 

And did you have to apply the workarounds as described in this topic to make it work before your current installation/release?

---

### Post by trouty187 on 2011-03-03
> **Niels_D said:**
> Ah ok, seems like a model from the same generation as mine.
What version of Ubuntu are you using? 

And did you have to apply the workarounds as described in this topic to make it work before your current installation/release?

I am running Ubuntu 10.10 64bit with the proprietary AMD graphics driver installed from the Ubuntu repositories... Didn't try to implement any workarounds in the past, just used to adjust the brightness using the Gnome brightness applet...

---

### Post by cub on 2011-03-03
> **trouty187 said:**
> I am running Ubuntu 10.10 64bit with the proprietary AMD graphics driver installed from the Ubuntu repositories... Didn't try to implement any workarounds in the past, just used to adjust the brightness using the Gnome brightness applet...
Same thing here. Ubuntu 10.10 64bit, Gnome, with the latest kernel update -27 the Fn keys for Brightness work as intended. I have a VPCEB1S1E.

---

### Post by Niels_D on 2011-03-03
Hmm, might be that the KDE thing works different with the backport from 4.6.0.
I am installing Kubuntu again on my new SSD in my VAIO next week so I'll try the not backported one first.

---

### Post by Niels_D on 2011-03-04
**Update:**
The KDE March update "Helga" solved my problem.

As described in the changelog:

**Powerdevil**

              *Bugfixes:*       
[LIST]
[*]Fix problem with increase brightness key not working sometimes. Fixes bug [264534]("http://bugs.kde.org/show_bug.cgi?id=264534").  See Git commit [57a927f]("http://commits.kde.org/kde-workspace/57a927ff69f5b1673e441c87ac59550f23ac3594").
[/LIST]
       

So I am happy :)

Next step is the full touchpad support!
Or did somebody try it already without the "nopnp" option?

---

### Post by trouty187 on 2011-03-11
For anyone who's interested I've done a bit of googling and figured out how to disable the inbuilt webcam on my VPCEB3C5E...

Just add "**blacklist uvcvideo**" (without the quotation marks) to **/etc/modprobe.d/blacklist**

---

### Post by danjjl on 2011-03-22
Hello,
I'm experiencing problems with the horizontal functions and multitouch functions of my touchpad - it all works fine in windows 7 -. I did change my /etc/default/grub file to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```but it didn't seem to change a thing.

I am running a ubuntu 10.10 VPCEB1M1E

Thanks to all of you who will kindly answer my post 
danjjl

---

### Post by cub on 2011-03-23
> **danjjl said:**
> Hello,
I'm experiencing problems with the horizontal functions and multitouch functions of my touchpad - it all works fine in windows 7 -. I did change my /etc/default/grub file to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```but it didn't seem to change a thing.

I am running a ubuntu 10.10 VPCEB1M1E

Thanks to all of you who will kindly answer my post 
danjjl
As far as I know, noone has got the touchpad to work with all features.

---

### Post by trouty187 on 2011-03-23
As far as I can tell when using **i8042.nopnp** the touchpad is actually recognised as an ordinary PS/2 mouse, hence the lack of touchpad features such as horizonal edge scroll and multi-touch...

Had a play around with one of the daily development builds of Ubuntu 11.04 a couple of weeks ago and the basic touchpad pointing functions worked out of the box without needing to use i8042.nopnp...

The touchpad tab was present in the **Mouse Preferences** window too, so it seems the touchpad was recognised by the O/S. None of the advanced touchpad functions worked though (muti-touch, two finger scroll etc.) and changing the touchpad specific settings had no effect. 

This might mean a fix is on the way with a bit of luck...

---

### Post by cub on 2011-03-24
> **trouty187 said:**
> As far as I can tell when using **i8042.nopnp** the touchpad is actually recognised as an ordinary PS/2 mouse, hence the lack of touchpad features such as horizonal edge scroll and multi-touch...

Had a play around with one of the daily development builds of Ubuntu 11.04 a couple of weeks ago and the basic touchpad pointing functions worked out of the box without needing to use i8042.nopnp...

The touchpad tab was present in the **Mouse Preferences** window too, so it seems the touchpad was recognised by the O/S. None of the advanced touchpad functions worked though (muti-touch, two finger scroll etc.) and changing the touchpad specific settings had no effect. 

This might mean a fix is on the way with a bit of luck...
That&#836;'s good news! I so wish the "Disable touchpad while typing"-setting will work. It's driving me crazy...

---

### Post by trouty187 on 2011-03-31
With a bit of help from the documentation at [http://linuxwireless.org]("http://linuxwireless.org") I've figured out how to turn off Bluetooth by default when logging into Ubuntu 10.10.  

add the command **sbin/rfkill block bluetooth** to **System > Preferences > Startup Applications**

Bluetooth can then be turned back on as and when required by clicking the **Bluetooth Applet** or running the command **rfkill unblock bluetooth** in **Terminal**. This should help to increase battery life for anyone like me who doesn't use Bluetooth very often but often forgets to turn it off. :)

---

### Post by Niels_D on 2011-05-01
I just updated to Natty 11.04 this week.
All fine (slow download however!!), but now I am having problems with Compiz.
Every time I switch from KWin to Compiz as window manager, there is a crash.

Also the low-res bootscreen is back again :(

Yaaay for updates which only make it worse! ):P

---

### Post by .Jonathan. on 2011-05-12
Hi,

Since I  installed 11.04 on my EB4Z1E i'm not able to scroll anymore, it used to work on 10.10 though...

I also get the touchpad settings, which i didn't have on 10.10, but none of them work.

---

### Post by Niels_D on 2011-05-14
The same here.
Do you also have Compiz problems? Or don't you use it?

---

### Post by Niels_D on 2011-05-15
If you want to enable touchpad scrolling again under (k)ubuntu 11.04, run the following command:

```
echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse
```

It will disable the touchpad settings and let the touchpad be reckognized as a PS/2 mouse, but as Jonathan already mentioned, the settings are worthless after all.

Has anybody got a working solution for the 20.000 RPM fan running the entire time? :O

---

### Post by .Jonathan. on 2011-05-16
Thanks a lot! Scrolling works now :D

I use compiz, but i haven't noticed any troubles yet..

And I can't control my fan neither. It's not going very fast, but it won't ever stop...

---

### Post by Niels_D on 2011-05-16
Weird that you don't have any Compiz problems!
What video card do you have and what drivers do you use? :shock:

---

### Post by .Jonathan. on 2011-05-16
I have an ATI HD 5650 and i'm using a driver i found under 'additional drivers' but it doesn't specify it's version...

---

### Post by Niels_D on 2011-05-17
Weird, I also have the same videocard.
Do you use the fglrx driver? :shock:

---

### Post by .Jonathan. on 2011-05-18
Yes. What kind of problems do you have?

---

### Post by cub on 2011-06-14
So, no news about the touchpad?

---

### Post by MarjaE on 2011-06-14
ALPS Glidepoint - an ergonomic nightmare!

The computer detects the touchpad as an ordinary PS/2 mouse and detects tapping, hand motions an inch or two away, hair, attempts to type on the nearby keyboard, etc. as button1 clicks.

For click and drag, I now use a portable mouse, though it hurts my wrist and outer fingers. For typing, I have yet to find any solution. In 10.10 I used a hotkey to disable the touchpad before typing, but in 11.04, it has been broken.

---

### Post by trouty187 on 2011-06-14
I agree with regards to the ALPS touchpad being a nightmare. I've found that messing with the acceleration and sensitivity sliders in 'Mouse Preferences' can help to make the touchpad more bearable with regards to 'tap clicks' being missed and accidental taps whilst typing. The sliders don't behave as you'd expect them to though so it's very much trial and error. Here's the settings which work best for me...

[IMG]http://mr7xoa.bay.livefilestore.com/y1pDlRDPG9SDMz6DGgw7PdOkuyAGrW50jHL9yIUC6SO2_VmIvJjKrPPQaqIu434UgDRj0T3ILSSSIEzK5ilH8ecMdvRiB-Nv9Y6/Screenshot-Mouse%20Preferences.png?psid=1[/IMG]

Since installing 11.04 I've been having trouble with the suspend function... If the battery is below approx 30% when suspending or if it drops below that level whilst suspended it fails to resume correctly... The power button turns to green but the system doesn't respond, after roughly 20secs of inactivity the fan briefly spins at full speed before the system abruptly powers off... Has anyone else encountered this problem?

I have also been experiencing CPU temps of 70c whilst encoding video (90-100 % CPU usage for 15 mins +) even with the laptop elevated on a flat surface, seems a little high to me... opinions..?

---

### Post by cub on 2011-06-18
> **Niels_D said:**
> If you want to enable touchpad scrolling again under (k)ubuntu 11.04, run the following command:

```
echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse
```

It will disable the touchpad settings and let the touchpad be reckognized as a PS/2 mouse, but as Jonathan already mentioned, the settings are worthless after all.
I noticed there was an update today for touchpad, but since I have run the code above I wonder how I can undo that to check out if it has been fixed?

---

### Post by .Jonathan. on 2011-06-20
> **trouty187 said:**
> 
Since installing 11.04 I've been having trouble with the suspend function... If the battery is below approx 30% when suspending or if it drops below that level whilst suspended it fails to resume correctly... The power button turns to green but the system doesn't respond, after roughly 20secs of inactivity the fan briefly spins at full speed before the system abruptly powers off... Has anyone else encountered this problem?



I have the same problem with 10.10 (used to have in with 11.04 as well) even when battery is charging or +30%...

---

### Post by johanbove on 2011-06-27
> **trouty187 said:**
> 
Since installing 11.04 I've been having trouble with the suspend function... If the battery is below approx 30% when suspending or if it drops below that level whilst suspended it fails to resume correctly... The power button turns to green but the system doesn't respond, after roughly 20secs of inactivity the fan briefly spins at full speed before the system abruptly powers off... Has anyone else encountered this problem?

I have also been experiencing CPU temps of 70c whilst encoding video (90-100 % CPU usage for 15 mins +) even with the laptop elevated on a flat surface, seems a little high to me... opinions..?

Same here, I had this problem on 10.10 (LinuxMint 10) as well. But I don't think it has to do with the battery running low, since for me it happened even with the battery fully charged. I don't see the temperature rise thát high however.

What kernel version do you have?

I've updated to LinuxMint 11 (has kernel 2.6.38-8-generic #42-Ubuntu) now and haven't had the issue, but will try to keep an eye on it.

---

### Post by trouty187 on 2011-06-27
> **johanbove said:**
> Same here, I had this problem on 10.10 (LinuxMint 10) as well. But I don't think it has to do with the battery running low, since for me it happened even with the battery fully charged. I don't see the temperature rise thát high however.

What kernel version do you have?

I've updated to LinuxMint 11 (has kernel 2.6.38-8-generic #42-Ubuntu) now and haven't had the issue, but will try to keep an eye on it.

I never really noticed the suspend problem when I was using 10.10 and I did use the suspend function quite often. 
It seems to be an intermittent problem under 11.04, I've tried various methods of suspending and waking the system but have never been able to get it to reliably repeat the error. The only thing I have noticed is that for me, it mainly occurs when running on battery and when the battery is low... Kernel version is "2.6.38-8-generic #42-Ubuntu"

With regards to the CPU temp I usually get ~36-46c normal usage (light browsing, instant messaging etc.) I only usually see temps of 70c when both cores are running at 90-100% load constantly for 15mins or more, such as when encoding MP4s using Handbrake, this occurs in Ubuntu and Windows 7. Has anyone else experienced temperatures this high when running at full tilt?

---

### Post by shaf_96 on 2011-06-28
hi I have a sony vaio laptop, model VPCEB3C5E, 

ati hd 5650m 1gb working, the unity is a bit slowww, everything is ok

keyboard fine

wifi working fully

bluetooth working fully, using bluetooth internet now!

function keys mostly working except fn + F7 (change display out) and fn + F9/F10 for zooming in/out

anyone tell me how to fix this?

sd card i think is working by adding the line     tifm_sd

in etc/modules

memory stick is not working, cant find anyway of fixing this

alps touchpad  - normal mosue functions are working, MULTI-TOUCH WAS WORKING OOB ON UBUNTU 11.04 X64 BUT! after running updates, vertical scrolling would not work at all 

i tried following this guide
[http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/)

but its still not working, can someone please help, thank you

---

### Post by shaf_96 on 2011-06-28
also the camera, sound and gigatit port working  fully

---

### Post by fasoulas on 2011-07-12
> **shaf_96 said:**
> hi I have a sony vaio laptop, model VPCEB3C5E, 

ati hd 5650m 1gb working, the unity is a bit slowww, everything is ok

keyboard fine

wifi working fully

bluetooth working fully, using bluetooth internet now!

function keys mostly working except fn + F7 (change display out) and fn + F9/F10 for zooming in/out

anyone tell me how to fix this?

sd card i think is working by adding the line     tifm_sd

in etc/modules

memory stick is not working, cant find anyway of fixing this

alps touchpad  - normal mosue functions are working, MULTI-TOUCH WAS WORKING OOB ON UBUNTU 11.04 X64 BUT! after running updates, vertical scrolling would not work at all 

i tried following this guide
[http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/)

but its still not working, can someone please help, thank you

Are you talking about the 32bit or the 64bit version of 11.04 ??

Because i would like to upgrade from 10.10 32bit which is working well, but i prefer to update to the 64bit version if there are not many problems, or at least problems that can be fixxed.

---

### Post by wgarciamachmar on 2011-09-12
> **cub said:**
> Thanks for that guide! With the addition of **install** this also works with Ubuntu 9.10. My alsamixer was muted so step 8 should be there just in case.

> **DrRush said:**
> Hi,

I managed to get sound working from headphones and pc-speaker on my Vaio E-series running Ubuntu 10.4 beta 2.
Installing Alsa 1.0.23 did the trick.
Heres steps that should replicate what I did:

1.  sudo apt-get build-essential
2.  wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
3.  tar -xjf alsa-driver-1.0.23.tar.bz2
4.  cd alsa-driver-1.0.23/
5.  ./configure
6.  make
7.  sudo make install
8. alsamixer (don't know if this step was necessary since my volume was already enabled)
9. reboot

Sound should now work.

By the way, does anyone know if one continues to receive updates of alsa after installing it manually like this?

I did this. But now i lost all sound. I tried to run alsamixer after reboot but it doesn't work. Looks like the file is missing. HELP!

---

### Post by cub on 2011-09-12
> **wgarciamachmar said:**
> I did this. But now i lost all sound. I tried to run alsamixer after reboot but it doesn't work. Looks like the file is missing. HELP!
Hmm I haven't needed to do that extra update for several updates. What version of Ubuntu do you run?

---

### Post by wgarciamachmar on 2011-09-12
> **cub said:**
> Hmm I haven't needed to do that extra update for several updates. What version of Ubuntu do you run?

I am running natty. Actually, Mint 11.

---

### Post by wgarciamachmar on 2011-09-12
I have a new Vaio VPCEG15FX.

I was trying to get my heaphone jack to work and i lost all sound.

When I do a ```
sudo modprobe snd-hda-intel
```I get

```

FATAL: Error inserting snd (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```


My alsa info is here

[http://www.alsa-project.org/db/?f=c867c8e120a8a1726227cb22cb54ade875770af2](http://www.alsa-project.org/db/?f=c867c8e120a8a1726227cb22cb54ade875770af2)

---

