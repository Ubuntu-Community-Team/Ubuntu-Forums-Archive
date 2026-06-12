---
title: "Dell: New Studio 14z Compatibility"
date: 2009-06-23
forum: Hardware
---

### Post by kestal on 2009-06-23
**[COLOR="DarkRed"]_Ubuntu 9.04 Jaunty_[/COLOR]**
**Potential Problems**
- Wireless
- Some Tearing on Startup and overall performance
- Locked Alps -> No Touchpad/Keyboard Support after a certain amount of time.
*[COLOR="SlateGray"]- Random blinking cursor display before xsplash (this delays boot by about 5-8 seconds BEFORE xsplash)[/COLOR]*
**Potential Solutions:**
- Wireless -> WICD
- Tearing -> Nvidia 190.36
- Locked Touchpad/Keyboard -> None yet.
**General Comments:**
- For the most part, this was a pretty easy install. After a while my touchpad stopped working just for Jaunty. Some form of a driver problem, I guess.
- Some minor tearing when loading up from grub->usplash->desktop.

**[COLOR="DarkRed"]_Ubuntu 9.10 Karmic Beta_[/COLOR]**
**Potential Problems**
- Some Tearing on start up
- Text garbage displayed before xsplash and when shutting down (instead of graphical shut down)
- Lonnnnng boot. (I am hoping this gets fixed soon - as soon as its in, its great)

**Potential Solutions:**
- The tearing/tect on start up -> No idea. Havent found a way around it.
- Fsck -> I turned this off as it was checking *every* time while loading up. This seems overkill.

**General Comments:**
- I am pretty impressed with Karmic, even though its only Beta.
- There is some tearing that occurs, in most cases during boot, and while switching from dual screen/single screen/presentation mode via Super+F1 when connected to an external monitor (or in my case, a TV via HDMI)
- HDMI Audio works perfectly out of the box.
- I still see some random text before xsplash starts up. Kind of annoying. Hopefully this gets fixed.
- xsplash flashes a few times (visible tearing) which is a bit unappealing.
- When Nvidia 190.36 is installed (works perfectly), my ####x720 display option disappears (though, I opted for the 900p monitor upgrade, I still use 720 at times when cloning screens). I had to manually add the resolution.

**Overall:**
- Not too bad. The tearing is annoying on startup/display switching and text garbage on startup/shutdown. Though, this is only Beta. Its a lot better than my previous Laptop.


**EDIT:**
For anyone having problems connecting with the dell 1515 wireless-N mini-card on 9.04...  download WICD. wireless worked near-perfectly for me. Sometimes it drops connection. Unknown reason.

---

### Post by codedash on 2009-06-24
I believe there are drivers for both. The graphics are the same as in the macbook and have seen reports that work. Please report what works (and doesnt) when you try cause i wait this model to come in europe and buy it.

---

### Post by kestal on 2009-06-24
I recently ordered it though its a custom (upgraded) model so currently its 'In Production' according to tell :) (I decided to go for the better CPU and add a few things), so this might take a while.

I will keep everyone here posted. I intend to test with Jaunty once it comes in.

---

### Post by Fluorescent Monkey on 2009-07-13
Just installed Ubuntu 9.04. The nVidia 9400M-G seems to work fine with the supplied driver.

I had a little trouble with the wireless though. See this post:
[http://ubuntuforums.org/showthread.php?p=7611937#post7611937](http://ubuntuforums.org/showthread.php?p=7611937#post7611937)

---

### Post by kestal on 2009-07-14
Just got my Studio 14z finally, so I will be testing 9.04 in the next day or so. I wonder if that would void the warranty -_-; as I did get extra warranty which would go to waste.

Regardless, the Vista (with extras) that came with it was bloated, so its gonna go.

Has anyone who has tested the 14z with 9.04 managed to fix the wireless issue? Flourescent Monkey, by you being online I assume you are finally on? What was the problem/fix? Did you have the Dell Wireless 1515 (there were a few options, I think I changed it from the default)

Edit: Just got off with Technical Support and Software Support. It does not look like installing Ubuntu voids any warranties with the 14z. I even talked to a supervisor (supposedly) who confirmed this. Ontop of that, the Dell HDD does come with the recovery disk incase if I need to restore Vista to its unholy glory.

---

### Post by CodeSamurai on 2009-07-14
I'm looking forward to hearing about the wireless as well.  I wish they would simply offer intel wireless...it'd make life so much easier.  Keep us updated!  This is most likely going to be my laptop in the next couple weeks.  Did you go with the 1600x900 or the 1366x768 display? Do you like everything else so far? One last question: Is the top glossy or rubbery?  Thanks and take care!

Trent out

---

### Post by benbuntu on 2009-07-14
Hey guys, for the wireless issue, have you tried installing the linux-backports-modules-jaunty package?  This gives you much more up-to-date wireless drivers.  You have to have the "unsupported updates" repository enabled in "Software Sources" in order to get this package.  I have a different laptop that also has an Atheros N wireless card, and installing this package really helped improve the wireless behavior.  Please let me know if this helps, as I'm thinking about getting a Dell Studio 14z myself.

Thanks,
Ben

---

### Post by Fluorescent Monkey on 2009-07-14
I do have the 1515 Wireless card. Unfortunately, it's an intermittent problem. It will connect eventually, but it takes 6 or seven time-outs before it does.

Earlier I had a problem with the system hanging when I clicked on the Power Management tool, but that seems to have fixed itself.

I have also encountered another really annoying problem; sometimes when the system boots up, the keyboard and track pad don't work at the login screen. The keyboard works fine at the boot select screen, but goes dead at the login screen.

I've spent a week researching these issues and I've found many other people having these problems on all kinds of machines, so I don't think the Dell 14z is really any less compatible than another model.

I don't know, maybe 9.04 Jaunty is just a lemon or something, but it's frustrating. Everything works fine under Vista (albeit slowly). I may try downgrading to Intrepid next to see if that solves any of my problems.

As for the 14z...
I kind of went a little crazy and decked it out with the 5GB and 1600 x 900 display. The extra RAM probably wasn't worth the high cost, but I have no regrets about the screen. It's gorgeous! Bright and very clear. In fact, some default fonts in Windows are pretty small at this resolution. Computer screens keep getting better while my eyes keep getting worse :( If you're over 40, maybe the lower res screen is the way to go.

I got the purple lid. It actually looks better than in the pictures on the Dell web site. It's not aluminum, but sort of a rubberized plastic. The computer feels pretty solid overall (and much lighter than my old behemoth 17" Sager).

My only real complaint is that the keyboard feels kind of cheap and mushy. But to be fair, so did all the other laptops I tried out. The trackpad is OK. Better than most HP's but not as good as a MacBook Pro's.

I didn't buy Dell's external DVD drive, instead I got a cheaper one made by LG. It works fine.

---

### Post by codedash on 2009-07-17
Thanks for the great info pals. So i guess with karmic everything will be out of the box. If you find fixes take some time to tell us. Have a good time with your laps :-)

---

### Post by Bateluer on 2009-07-20
I've been exploring at Studio 14z for a light weight laptop replacement, along with the Acer Timeline 3810T. The Studio 14z has the better CPU and IGP, but the Timeline is smaller, lighter, and has better battery life. The Timelines also seem to have problems with Jaunty and resuming from suspend. 

How are the wireless problems with the Studio 14z? Did they get resolved?

---

### Post by belcherman on 2009-07-21
I'm also having trouble with my 14z hanging at the login screen. It runs fine from the LiveCD, but once I install and reboot, the trackpad and keyboard stop responding. I'm guessing this is a driver issue but I haven't had time to investigate. This is with Jaunty 64bit. As for the display, I went with the 720p display and wish now that I had upgraded to the 1440x900 display. I think there's enough space to squeeze those extra pixels in without making the fonts too small, and I wouldn't have to scroll web pages as often. I also ordered it with 3gb of RAM and I think that's probably enough for most people. Good luck.

---

### Post by CodeSamurai on 2009-07-21
Couple more questions from me: How is the keyboard? Does it have reasonable give?  I mean, if you press hard in the middle, does the whole thing collapse in?  That always bothers me with laptops...

Also, how is the build overall of the laptop?  Does it stay still when you type?  Does the screen feel flimsy or will it hold up for awhile?  How is the battery life under ubuntu? (I know Dell says 6 hours plus, but that's under windows and I couldn't care less about that) Any other quirky things?  Are you satisfied with the 14z?  Let me know!

Trent out

---

### Post by Bateluer on 2009-07-21
Well, I bit the bullet and took advantage of some promotions last night and ordered a Studio 14z myself. Windows will come up once so I can verify the hardware, then I'll likely set up a dual boot with clean Vista install. 

Unfortunately, I haven't been able to get my Garmin forerunner 305 working in any Linux distro,  native or through virtual box. Major stumbling block on my goal to phase out windows from my main machines.

---

### Post by belcherman on 2009-07-22
> **CodeSamurai said:**
> Couple more questions from me: How is the keyboard? Does it have reasonable give?  I mean, if you press hard in the middle, does the whole thing collapse in?  That always bothers me with laptops...

Also, how is the build overall of the laptop?  Does it stay still when you type?  Does the screen feel flimsy or will it hold up for awhile?  How is the battery life under ubuntu? (I know Dell says 6 hours plus, but that's under windows and I couldn't care less about that) Any other quirky things?  Are you satisfied with the 14z?  Let me know!

Trent out

Overall, the 14z feels solidly built and if you put it down on a flat surface it stays in one place. There is no flex on the keyboard and I type hard. The battery life is probably closer to 3 to 3.5 hours for me under Windows, but I don't have any of the advanced battery-saving features turned on. I can't report on the battery life for Ubuntu, as I haven't got that working yet.

---

### Post by Isira on 2009-07-23
I too am looking into purchasing a 14z. I was wondering how well the other features of the laptop work, such as audio and media hotkeys (in particular Volume Up/Down, mute), webcam, and bluetooth. (Is there anything else I missed?)

---

### Post by Bateluer on 2009-07-23
> **Isira said:**
> I too am looking into purchasing a 14z. I was wondering how well the other features of the laptop work, such as audio and media hotkeys (in particular Volume Up/Down, mute), webcam, and bluetooth. (Is there anything else I missed?)

I'll let you know after 4 August when mine arrives but likely someone else can answer quicker.

---

### Post by belcherman on 2009-07-23
The webcam works well in bright to moderate light. The audio is one area where I was disappointed. The sound was clear, but not very loud even at maximum volume. I haven't played too much with the hot keys or bluetooth, yet.

---

### Post by Bateluer on 2009-07-24
> **belcherman said:**
>  The sound was clear, but not very loud even at maximum volume. .

Doesn't that pretty sum up all laptops though, regardless of OS?

---

### Post by mrfuzzemz on 2009-07-27
I've been running 64-bit Jaunty on my 14z for a couple of weeks now and I'm so far very pleased with it. I have the Dell 1397 for wireless rather than the 1515 and it works without any problems. I've also had the issue with the keyboard and mouse not responding sometimes at the login screen, although USB input devices work fine. The screen is fantastic. I just wish the touchpad was a Synaptic instead of ALPS.

---

### Post by kestal on 2009-08-02
So I have the 1515 wireless and I just installed Ubuntu from a USB drive (I didn't bother with buying an external DVD, as I hardly ever use CD's - seriously).

To my surprise, everything worked out of the box. (Ubuntu is just that good sometimes). Wireless = Flawless. 1.2mb/s download speeds from certain servers. Sound quality = excellent (and loud at max volume). All the predefined special keys work just the way they should (except when using the brightness keys, my brightness bar via the notifications does not show up at all - though it still works - However, I will miss that - though I should probably update my out-of-the-box ubuntu, as it will probably work afterwards, anyway).

Video drivers were easily installable and I managed to get everything working with minimal effort. :)

Overall I am very pleased with the laptop. It has a great battery life, the keyboard itself is better than other laptops I was looking at, the bootup is quick and so far I am very happy.

---

### Post by belcherman on 2009-08-03
I was able to get my 14z set up dual-boot with Vista and Ubuntu. I shrunk the Vista partition down to 80 gb and installed Ubuntu from an external DVD drive. I had problems with 9.04, so I installed 8.10, 64bit. Very nice. I'm liking it (the Dell) much more with Ubuntu as opposed to Vista. It seems more responsive and even the speakers sound better. I was able to get the updated drivers for the video off the net. My next goal is to install VMware server and install WindowsXP in a vm, for those rare occassions when I need to run a Windows app.

---

### Post by kestal on 2009-08-05
What problems did you have? upon starting up after a few times, i did run into a few problems after updating+activating my hardware drivers.

1st: The wireless connection DID take forever to actually connect, with this said, its not so much of a problem with incompatibility. I used WICD and it worked perfectly (connected very well, too).

2nd: After activating hardware drivers and customizing (nothing interfering with code) my Ubuntu 9.04, the shut down screen looked borked. 4-5 different bars (instead of 1) were smeered down half of the screen. For this, I have not yet found a cure for.

---

### Post by tsmithtree on 2009-08-07
I can confirm everything kestal says, the wireless takes a while to connect sometimes but once it does, it's quite fast (I use wicd as well). The shutdown screen is corrupted too. Other than that, everything works as expected. The nvidia graphics card is impressive, I played ut2004/nexuiz along with halo, half-life 2 and a few others under wine. If you're considering purchasing this machine, definitely get the 8cell battery and 1600x900 screen. It looks fantastic.

---

### Post by stelford on 2009-08-08
Hello everyone,
   long time unix user, first time poster. I recently got the dell studio 14z, and installed 9.04 on the new machine. I noticed that unless I went into the bios screen, after installing the nvidia 173 glx drivers, then keyboard/mouse wouldn't work. 

   Installing the nvidia 180 glx plain out didn't work at all for me. I upgraded to Alpha3 of 9.10 and installed (from the nvidia site) nvidia 190 and .. joy. no problems whatsoever.

   Wireless, I have the ath9k driver .. whichever that one is (dell 1515 perhaps ?) and I have noticed -much- better stability using wicd than network-manager. Even when using 9.10. I have also noticed that when putting the machine into standby mode, that the wireless has a hard time recovering from it. I have to shutdown completely, and then ; iwconfig wlan0 txpower on and power on.. then I also have to set the txpower 20 and commit (it complains that the commit doesn't take but without it, I notice that the wifi doesn't come back on).

   So far, I -love- this machine. I get 6 hours on battery without wifi (8 cell) and about 4 hours with wifi and using around 50% cpu. Cpufreqd is very nice .. mostly down at the 1.2ghz range and occasionally jumping upto 1.6.. very -very- rarely does it get upto the 2.1ghz. very rare (opening firefox can do it).

   On bootup, I do get a loud 'pop' from the internal speakers usually when setting videomode. I never got this on 9.04, it only started when I upgraded to 9.10. Pulseaudio also went mad and tried to network stream, so, I am fine with chalking this upto '9.10 madness'.

   But.. everything else works. The only thing I lament is the lack of 'wifi on' led (I like them) and the lack of docking port on the base (I have an e6400 which has that) but.. overall.. 95% happy :)

   Regards
   Stef

---

### Post by kestal on 2009-08-09
> **stelford said:**
> 
   Installing the nvidia 180 glx plain out didn't work at all for me. I upgraded to Alpha3 of 9.10 and installed (from the nvidia site) nvidia 190 and .. joy. no problems whatsoever.

It worked for me for a bit, then I had the same problem. So I temporarily installed Windows 7 off of a USB. (I know, shame, but W7 isn't horrible, I do like the GUI/standards for UI - I wish Ubuntu was a bit more like this rather than segregated).

> **stelford said:**
> 
I have noticed -much- better stability using wicd than network-manager. Even when using 9.10. 

I havent tried 9.10 yet, but supposedly there are less problems in the alpha than there are on the released 9.04 for this laptop, so I will give it a go.

> **stelford said:**
> 
   On bootup, I do get a loud 'pop' from the internal speakers usually when setting videomode. I never got this on 9.04, it only started when I upgraded to 9.10. Pulseaudio also went mad and tried to network stream, so, I am fine with chalking this upto '9.10 madness'.

I have had these popping noises no matter what OS was on. Windows 7 seemed to minimize these which were comforting. I seemed to notice them disappear after I updated my W7 audio drivers (there isnt even a popping noise when restarting/shutting down anymore - its now a soft noise which is hardly noticible) - However, that could just be my imagination. If you google 'Dell laptop Popping', some people mention it could be to do with Wireless.

> **tsmithtree said:**
> I can confirm everything kestal says, the wireless takes a while to connect sometimes but once it does, it's quite fast (I use wicd as well). The shutdown screen is corrupted too. Other than that, everything works as expected.

Im pretty glad that I am not the only one experiencing the really weird shutdown screen. I also get a very quick corruption upon start up (for a split second, but annoying nonetheless as other linux distros dont have this problem, nor does anything above XP).

with that said, i wonder if (because karmic alpha 3 might be using beta drivers), that if the shutdown/startup error is fixed. I might try that sometime, or wait until alpha 4 (only a few more days away, anyway)

---

### Post by citbruce on 2009-08-18
Except for battery life everything works fine.

- 900p Display
- 1515 Wireless Card + bluetooth
- 2.66 / 9550 Processor
- Ubuntu 9.04

To get the wireless working I needed the backport (linux-backports-modules-jaunty).

To get the display working for some applications I needed to use the NVIDIA 173 (180 causes the screen to freeze in some apps, such as texmaker).

However, the 6 cell battery only lasts about 2 hours even in seriously low display brightness. While the fan is very quiet, it blows very hot. The CPUs are running at 47 C and the GPU at 56 C, which doesn't sound bad but the case is pretty warm. Could be the processor or the bluetooth that is draining the battery.

---

### Post by aacidd on 2009-08-21
I'm using the laptop n havin no problem wif the wifi nor vga card. for the vga card, I downloaded the latest driver from nvidia url....sound works fine on mine....though under vista n debian....it cracked...

---

### Post by crisosma on 2009-08-22
Well, I've been testing kubuntu 9.04 fir this week, i faced the problems with the instability in the wireless, and the internal mic not working, and until now, just once the problem with the keyboard and touch-pad at booting. I resolved these problems like this:

For the wireless, first I checked the pre-released and unsupported updates, and make an overall updated, the wireless began to work better, then I installed the Linux-backports-modules, but the wireless conected fast and 3 minutes later it disconnected, so I just keep without the backport modules.

For the internal mic, I've already known that I have to put a  model in the /etc/modprobe.d/alsa-base.conf to make everything work perfect. Now, alsa in 9.04 offers complete compatibility  with the sound card choosing the model "dell-s14" which it's pretty obvious.

I also installed the nvidia 185 for the video card and it's working really good. I tested the hdmi output, perfect. On the other hand, the audio output via hdmi is more problematic, using kubuntu sound preference, i selected to use hdmi audio and it worked, most sounds came out by the hdmi, but vlc didn't, I'm trying to fix that. For now, i'm using dragon, however, it's very simple and doesn't allow me to change the size of the font in subtitles.

I don't know how to fix the problem with the keyboard and touchpad at booting.

Overall, this laptop is working very well, the keyboard is good and the screen is amazing.

UPDATE:

Now, i can put the audio through the hdmi, just put on the iec958 option in alsa, then, in vlc advanced options choose the hdmi audio output. The problem with the keyboard is supposedly fix adding "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" in menu.list in the part for the kernel options, or fixed for the 2.6.30 kernel.

---

### Post by kestal on 2009-08-26
I used WICD for the wireless, I did the same thing to fix the audio problem, and I installed the 190 nv driver and things seemed to run pretty smoothly. Karmic doesn't work yet, though hopefully in the betas, it'll be fixed.

---

### Post by Gnobody on 2009-09-02
I have setup 2 of these notebooks with Ubuntu 9.04, if you buy the latest version that comes with the Atheros Wireless N Mini card you have to: ***sudo apt-get install linux-backports-modules-generic*** meta package to get the Ahteros Wireless N working and to increase the range because the Ath2k9 driver is outdated in Jaunty.  The Broadcom and Belkin Wireless G chipsets work fine out the box if you have an earlier revision of this hardware.  All the other hardware works GREAT out of the box with restricted drivers, including HDMI out, Bluetooth, ACPI, poweer management, and the webcam.  I was blown away by how well everything just worked when I first set it up.  IMNSHO this is the perfect notebook for Ubuntu.

---

### Post by ramesh_v on 2009-09-02
Hi, I purchased a Dell Studio 14z last week and trying to install 9.04 64bit on it. I am newbie to Ubuntu 64 bit. I have installed older versions on older laptops with no issue. The issue with 14z I have is that I am unable to get the sound to work. Webcam, wireless seems to work fine out of the box. I see that many of you are enjoying 9.04 on 14z. I would greatly appreciate if someone can walk me through to get the sound to work.

Here are some of the outputs...

"lspci -v" finds the audio card
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: Dell Device 02ba
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f0980000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


"aplay -l"
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ramesh_v on 2009-09-02
Looks like the sound was working. But the volume was too low to hear. Now when I set to 100% I hear it as if it was at 30%. Is there a way to get good quality sound?

Another issue I have is that I am unable to change the brightness of the LCD. It defaults to 100% and the keys (F4 and F5) don't work. I can add the "Brightness Applet" to the panel and change to my desired level. The problem is that everytime I reboot the brightness defaults to 100%. Is there a way to make the keys work or remember the setting from the applet?

---

### Post by Bateluer on 2009-09-12
> **ramesh_v said:**
> Looks like the sound was working. But the volume was too low to hear. Now when I set to 100% I hear it as if it was at 30%. Is there a way to get good quality sound?

Another issue I have is that I am unable to change the brightness of the LCD. It defaults to 100% and the keys (F4 and F5) don't work. I can add the "Brightness Applet" to the panel and change to my desired level. The problem is that everytime I reboot the brightness defaults to 100%. Is there a way to make the keys work or remember the setting from the applet?

Does anyone know how to resolve this? I want to install Jaunty on this Studio 14z but the LCD at 100% brightness is eye burning.

---

### Post by Bateluer on 2009-09-12
Not sure if anyone else has run into this problem. I haven't installed Jaunty yet, just booted into the LiveCD. Once in, neither the Studio's track pad or keyboard function. External USB mice and keyboards work fine. Obviously, this is unacceptable on a laptop. 

Anyone know how to resolve this?

---

### Post by Bateluer on 2009-09-30
> **Bateluer said:**
> Not sure if anyone else has run into this problem. I haven't installed Jaunty yet, just booted into the LiveCD. Once in, neither the Studio's track pad or keyboard function. External USB mice and keyboards work fine. Obviously, this is unacceptable on a laptop. 

Anyone know how to resolve this?

Anyone encounter this or know of a resolution?

---

### Post by mrfuzzemz on 2009-10-01
I think many of us have experienced this issue. It happens on about 20% of boots. I just restart the system (turn off then on) and usually it's okay.  A bit frustrating, but not too terrible.

---

### Post by kestal on 2009-10-04
> **Bateluer said:**
> Anyone encounter this or know of a resolution?

I experienced this in Jaunty (only after a certain amount of time - then happened all the time). However, I have not yet experienced this in Karmic. (Pretty much everything worked out of the box, so thats very reassuring, especially as Karmic is being released in the next 3 weeks).

I am currently using Karmic Beta. The brightness/sound issue is fixed as well on my end.

The Wireless even worked out of the box (though it was a bit chaotic - from 60-90% in a second back down to 60%, etc.. Though my download speeds were constant. I havent tried WICD with Karmic yet.

---

### Post by mrfuzzemz on 2009-10-04
> **kestal said:**
> I experienced this in Jaunty (only after a certain amount of time - then happened all the time). However, I have not yet experienced this in Karmic. (Pretty much everything worked out of the box, so thats very reassuring, especially as Karmic is being released in the next 3 weeks).

I am currently using Karmic Beta. The brightness/sound issue is fixed as well on my end.

The Wireless even worked out of the box (though it was a bit chaotic - from 60-90% in a second back down to 60%, etc.. Though my download speeds were constant. I havent tried WICD with Karmic yet.

Have you tested HDMI audio output with Karmic yet?

---

### Post by kestal on 2009-10-05
> **mrfuzzemz said:**
> Have you tested HDMI audio output with Karmic yet?

I have a fully updated system (with the latest nvidia 190 beta drivers) and just tested on my 14z.

HDMI audio output works. As soon as you plug the HDMI cable in, you right click the volume button -> Sound Preferences -> Hardware. Then under Profile at the bottom switch to Digital Stereo (HDMI) Output. Done.

Its not too bad. I will miss switching between presentation mode and laptop seemlessly (I get a few jitters/tearing) but nothing major. I had to manually set the volume output on Windows either way, so its not much different.

---

### Post by Bateluer on 2009-10-05
> **mrfuzzemz said:**
> I think many of us have experienced this issue. It happens on about 20% of boots. I just restart the system (turn off then on) and usually it's okay.  A bit frustrating, but not too terrible.

Odd problem. When I posted about the issue first, I tried several revisions of Ubuntu and hit the same problem, including reboots. Sunday, I tried 9.04 and Mint 7 and had the mouse and keyboard work fine. 

Ran into trouble with the Wireless through. It would connect easily enough the first time, and then drop randomly and never reconnect. Mint 7 and WICD didn't even detect the wireless at all.

---

### Post by kestal on 2009-10-05
> **Bateluer said:**
> Odd problem. When I posted about the issue first, I tried several revisions of Ubuntu and hit the same problem, including reboots. Sunday, I tried 9.04 and Mint 7 and had the mouse and keyboard work fine. 

Ran into trouble with the Wireless through. It would connect easily enough the first time, and then drop randomly and never reconnect. Mint 7 and WICD didn't even detect the wireless at all.

Since I started with Karmic alpha 6, I havent had a problem with the wireless drivers at all. Then again, Karmic isn't released yet and not meant to be put on Production machines, but I am pretty pleased with the out of box support for touchpad (though sometimes not sensitive enough even on max), keyboard, and wireless.

---

### Post by Bateluer on 2009-10-06
> **kestal said:**
> Since I started with Karmic alpha 6, I havent had a problem with the wireless drivers at all. Then again, Karmic isn't released yet and not meant to be put on Production machines, but I am pretty pleased with the out of box support for touchpad (though sometimes not sensitive enough even on max), keyboard, and wireless.

No wireless in Karmic Beta either, even after I installed the Hardware drivers through Ubuntu Software Center. Afterwards, it detects the free wireless broadcom driver and the proprietary sta driver, but Karmic detects no wireless networks even with WICD. I'll play with this some more. 

Keyboard works fine. Touchpad works, though it seems to have sensitivity drop off randomly, making it hard to navigate around. I've seen this happen under Dell laptops running windows a lot too, usually on Vostros or Latitudes.

---

### Post by kestal on 2009-10-06
> **Bateluer said:**
> No wireless in Karmic Beta either, even after I installed the Hardware drivers through Ubuntu Software Center. Afterwards, it detects the free wireless broadcom driver and the proprietary sta driver, but Karmic detects no wireless networks even with WICD. I'll play with this some more. 

Keyboard works fine. Touchpad works, though it seems to have sensitivity drop off randomly, making it hard to navigate around. I've seen this happen under Dell laptops running windows a lot too, usually on Vostros or Latitudes.

Which Wireless option did you select? The intel or the dell? when choosing/customising (if you did so).

---

### Post by Bateluer on 2009-10-07
> **kestal said:**
> Which Wireless option did you select? The intel or the dell? when choosing/customising (if you did so).

The Dell 1397 card is what I selected during the build when I customized the laptop on Dell's site. Karmic prompted me to install either the Broadcom STA proprietary driver or the open E43<?> driver. I chose the STA driver. The open driver isn't showing up in the Hardware Drivers tool now though. 

Sometimes, it will detect that there are wireless networks in range, other times it will report that no wireless networks are detected. This occurs in both the Gnome Network tool and the WICD tool.

Edit - This is on Karmic Beta as well, not the official Jaunty.

---

### Post by caspian154 on 2009-10-08
I've been experiencing the same issues with the dell 1397 card on a studio 15. I was able to see wireless networks in gnome network manager, but when I tried to connect the portlet would freeze, and no longer respond to mouse clicks.

---

### Post by Bateluer on 2009-10-08
> **caspian154 said:**
> I've been experiencing the same issues with the dell 1397 card on a studio 15. I was able to see wireless networks in gnome network manager, but when I tried to connect the portlet would freeze, and no longer respond to mouse clicks.

That's what happens when attempting to connect to my home wireless network. When connecting to the work wireless, it seems to function.

Edit - Overall though, I really like the Karmic Beta. If these wireless issues get sorted out, I'll be running in on the Studio for a lot longer.

---

### Post by caspian154 on 2009-10-08
I just installed all the latest from the repositories, including upgrading to the 2.6.31-11 kernel and everything is working. I am using the proprietary "Broadcom STA wireless driver". 

I totally agree this release seems like it's going to be a good one!

---

### Post by kestal on 2009-10-09
I couldn't be much help as I chose the other wireless-n mini-card option available which was Atheros-based. Im glad that they included something that will work.

Curious, Does anyone have a bit of lag/delay before hitting xsplash? or see text on the screen? (On Karmic)

If you do not, which Nvidia Driver did you use? Kernel?

---

### Post by Bateluer on 2009-10-11
> **caspian154 said:**
> I just installed all the latest from the repositories, including upgrading to the 2.6.31-11 kernel and everything is working.

I totally agree this release seems like it's going to be a good one!

I did similar, tho upgrading from 2.6.31-11 to -12 to -13 did cause a noboot problem that needed to be addressed. Price of using a Beta release though.

Karmic is shaping up to be pretty decent.

---

### Post by jason_g on 2009-10-12
Hi,

I have a dell 14z and I am very new to ubuntu.  I have been trying to get ubuntu 9.04 32-bit running smoothly so I can run this open source software for some research.  I am still having issues with the wireless and the audio. When in Vista the audio is noticeably louder, even at minimal settings, but when I boot to ubuntu I have to be at about 100% to perceive any audio.

My wireless card is the "Dell Wireless 1397 802.11g Half Mini-Card".  As suggested I used the Broadcom STA drivers that show up under hardware, and I use the WICD manager.  I am able to connect to regular wifi signals fairly well, but I am unable to create or connect to an AD-HOC.  I get my internet by means of an AD-HOC through my mobile phone, so it would be very nice if I could figure this out.

I have also had the issue of weird colors followed by full brightness on my lcd during shutdown, and loose mouse and keyboard use during boot up (although it hasn't happened in awhile).

Thanks for any help,

Jason

---

### Post by Bateluer on 2009-10-14
> **jason_g said:**
> Hi,

I have a dell 14z and I am very new to ubuntu.  I have been trying to get ubuntu 9.04 32-bit running smoothly so I can run this open source software for some research.  I am still having issues with the wireless and the audio. When in Vista the audio is noticeably louder, even at minimal settings, but when I boot to ubuntu I have to be at about 100% to perceive any audio.

My wireless card is the "Dell Wireless 1397 802.11g Half Mini-Card".  As suggested I used the Broadcom STA drivers that show up under hardware, and I use the WICD manager.  I am able to connect to regular wifi signals fairly well, but I am unable to create or connect to an AD-HOC.  I get my internet by means of an AD-HOC through my mobile phone, so it would be very nice if I could figure this out.

I have also had the issue of weird colors followed by full brightness on my lcd during shutdown, and loose mouse and keyboard use during boot up (although it hasn't happened in awhile).

Thanks for any help,

Jason

The weird colors, or tearing, at shutdown are a known issue right now. Its not super critical, but it may be resolved in the 9.10 RC or by using the most current drivers form nvidia's site. 

Not sure how to configure Ad-Hox wireless through a cell phone though, never had to do that. Have you tried creating a new wireless Adhoc connection through either the Gnome Network Manager or WICD with the applicable information?

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

### Post by bcleveng on 2009-11-10
> **jason_g said:**
> ... and loose mouse and keyboard use during boot up (although it hasn't happened in awhile).


This problem is driving me absolutely insane right now. I have to reboot on average 3-4 times every time I try and turn my laptop on just to get activity. I found a thread stating it may be do to the d-bus not starting, in turn causing HAL not to start ([http://ubuntuforums.org/showthread.php?t=1292477](http://ubuntuforums.org/showthread.php?t=1292477)).

Unfortunately, the solution proposed is to put the system into raw keyboard mode via usage of the SysRq key, which doesn't seem to exist on the 14z keyboard.

Has anyone run into and solved this problem? Currently I'm still on 9.04, though I've tried 9.1 and had the same issue.

---

### Post by mrfuzzemz on 2009-11-10
> **bcleveng said:**
> This problem is driving me absolutely insane right now. I have to reboot on average 3-4 times every time I try and turn my laptop on just to get activity. I found a thread stating it may be do to the d-bus not starting, in turn causing HAL not to start ([http://ubuntuforums.org/showthread.php?t=1292477](http://ubuntuforums.org/showthread.php?t=1292477)).

Unfortunately, the solution proposed is to put the system into raw keyboard mode via usage of the SysRq key, which doesn't seem to exist on the 14z keyboard.

Has anyone run into and solved this problem? Currently I'm still on 9.04, though I've tried 9.1 and had the same issue.

I used to see this every other time on 9.04, but I haven't seen it once since I've upgraded to 9.10.

---

### Post by mrfuzzemz on 2010-05-13
Has anyone had any success with outputting a video signal from a 14z via a displayport to VGA(standard DB-15) connection? I have a StarTech DP2VGA adapter and, while it connects, the picture flashes black for a few seconds every once and a while.

I'm using Lucid 10.04 64-bit and had the same issues with previous editions of Ubuntu. I've only tested briefly in Windows 7, but it seemed to be okay there.

---

