---
title: "Helpful Hints for a tx1000 (mark II)"
date: 2009-01-16
forum: Hardware
---

### Post by Alejandro Nova on 2009-01-16
If you are like [Diatribex]("http://ubuntuforums.org/showthread.php?t=442483") or me, after you installed the latest Ubuntu, some things just didn't work&#8482;.

However, the list of non working things with the Intrepid Ibex has shrunk...

Here it goes: how I got this lappy to an almost fully working state with Ubuntu Intrepid Ibex. This is my experience with Ubuntu 8.10, and it may be useful to you.

**Sound:** Working out of the box with the Ibex.

**Video:** Works well with nVidia 180 drivers. Please, note that **the bug with Suspend to RAM/Suspend to Disk and nVidia 180 drivers only affects GeForce 8xxx, 9xxx and GTx-xxx users**. Your nForce 430/GeForce 6150 will suspend and hibernate, and resume, properly. Use the Ubuntu Restricted Drivers manager.

**Wireless:** Your best bet is with the b43 free drivers, and fw-cutter. It works for me a lot better than Broadcom STA proprietary drivers. You can install it through Ubuntu Restricted Drivers manager, with ease.

**Multimedia keys, remote control:** They do not work reliably until you configure them properly. But wait, **in the Ibex, don't touch /etc/X11/xorg.conf and do not use esoteric solutions**. You can do it easily.

1. In your GNOME menu, go to the Preferences menu, Keyboard. Then choose the model of your keyboard. There's no Pavilion tx1000 there, but don't worry: select another HP Pavilion or Omnibook keyboard model. Under KDE, go to the System Settings app, then click under "Country and Language" (the UN flag), You will see three icons in your left-side panel. Click on the keyboard, and select "HP Pavilion zt1100". That worked for me.

2. Configure your keys. At least GNOME and KDE 4.2 will configure several multimedia keys for you.

Don't worry about the remote: it's a low level remote that only "press keys". You won't need drivers for it, it will work.

**Fingerprint scanner:** It should be as easy as:

$ sudo apt-get install fprint_demo libpam-fprint
$ sudo adduser <user> plugdev (to give that user access to the fingerprint scanner)

Later, if you want to, you may follow a howto about logging in with your finger. I advise against it. There is no good support, neither in kdm nor gdm.

**Card reader:** It works out of the box.

**TV Out:** Working. Press Fn+F4. You can configure it through nvidia-settings. Don't forget to install it!

**Touchscreen:** It's an eGalax. Please, do yourself a favor and **if you are using Ubuntu Intrepid Ibex, do not follow those eGalax howtos, do not install proprietary drivers, do not configure your xorg.conf, let the Ibex do all the work**. Simply issue this:

$ sudo apt-get install xserver-xorg-input-evtouch

and restart X. If you don't have luck, you'll have an uncalibrated touchscreen; if you have luck, you'll have an autocalibrated touchscreen, if you don't have luck, run ev_calibrate and FOLLOW CAREFULLY THE INSTRUCTIONS.

Pay attention: the touchscreen behaviour when the screen is rotated is BUGGY. The upcoming evtouch 0.8.8 will make, at last, an usable rotated screen. 

**Side buttons:** This is more complicated. You may have read some howtos about making work two of the four buttons. Those howtos are useless with the Ibex: the kernel does not recognize accurately those key presses. The real support comes through a kernel module, QuickStart, available at [http://quickstart.sourceforge.net](http://quickstart.sourceforge.net) . This will give you real support through ACPI, and allows launching apps through that interface. It won't work, because you need special scripts, and neither the app nor Ubuntu provides them.

If you want to use that, you must know how to compile software. Get build-essential.

$ sudo apt-get install build-essential

Follow the instructions. Read the README! ;)

**Modem:** This won't work under Linux, but is near useless with Windows Vista, so, at least we are on par with them! ;)

---

### Post by stuckwi on 2009-02-06
Thanks for your informative post Alejandro,
I have the same series of laptop (tx1000z), currently running 32bit hardy.  
I was wondering if you installed the 32bit or the 64bit version?
Does the mic and headphone jacks work?
Does the webcam work?

---

### Post by Alejandro Nova on 2009-02-08
> Thanks for your informative post Alejandro,
You're welcome ;)

> I have the same series of laptop (tx1000z), currently running 32bit hardy. 
> I was wondering if you installed the 32bit or the 64bit version?
I installed the 32 bit version. 

> Does the mic and headphone jacks work?
With the Intrepid Ibex, yes, they work.

1. When you insert a headphone jack in your notebook, speakers should mute themselves and sound must start coming out from your headphones. That is called 'jack autosensing', and, if it behaves erratically, you must insert this line into your /etc/modprobe.d/options as root.

```
options snd-hda-intel model=hp
```

2. Your mic should be working out of the box... but you may not know it, because it is muted. Here is how to make it scream.

* Go to your GNOME volume applet, and double click it. You'll get the GNOME Volume Control. Press "Preferences".
* Ensure the following boxes are checked.

PCM (Playback)
ATAPI Mic (Playback)
Capture (Recording)
Input Source (Options)

* Close that box. You'll have new options to try!
* Unmute (clicking the small speaker below) "ATAPI Mic" in the "Playback" view. Turn output volume to max.
* Go to the "Recording" tab, rise the "Capture" volume to max, and enable the "Capture" button, clicking in the small button below the slider.
* Go to the third tab, "Options". Select as your "Input Source" "ATAPI Mic". What is that? The ATAPI Mic is the microphone built into your tx1000's screen. Now, you'll be able to speak freely, as you did in Vista.

> Does the webcam work?
Yes, out of the box. It is an USB Video Class webcam, fully supported under Linux.

---

### Post by stuckwi on 2009-02-09
alright,
Here I go, I'm a gonna install intrepid ibex 32bit now...
Thanks again.

---

### Post by stuckwi on 2009-02-09
Alright, I'm rolling along with tx1000z on 32bit intrepid ibex, everything is working fine, as far as I can tell.  Tethering to my cell using USB worked out of the box, unlike prior versions.
But one comment to your step-by-step:

"$ sudo apt-get install fprint_demo libpam_fprint"

for me it was fprint-demo libpam-fprint

Ciao

---

### Post by gborzi on 2009-03-02
Hello to everyone,
I have recently installed Intrepid on my TX1350el, and as with Hardy I made a package for evtouch with a patch to fix the rotation issue. The package (for amd64) and the diff file are attached to this post.

---

### Post by crazyness003 on 2009-03-09
Life saver! I was trying to get the eGalax to work the old way....and I failed...till I ran across this thread.

Some one should edit the old thread and link it to this one (whoever can, o great mods)

> **gborzi said:**
> Hello to everyone,
I have recently installed Intrepid on my TX1350el, and as with Hardy I made a package for evtouch with a patch to fix the rotation issue. The package (for amd64) and the diff file are attached to this post.

Im gonna have to sleep on that one, I dont even think i have rotation enabled.
Thanks tho.

---

### Post by onerodetoasabay on 2009-03-10
Thanks for making a new thread, Alejandro! I followed the old one since I got my laptop about a year ago and have read it pretty much front to back and it helped me resolve a lot of issues. However, Hardy ended up committing suicide over the summer (I *think* this is because I installed a program on Vista that would let me get into Ubuntu... it looks like Windows just ate the Linux partition) and I didn't get around trying to get Ubuntu to work again until about three months ago. Things have gone fairly swimmingly until Hardy decided to go kaput once more, this time I think I played with the xorg.conf file one too many times. Restoring backed up xorg files doesn't seen to do much although I need to do some more testing. Anyway, for some reason, I'm stuck in 600x800 resolution and can't seem to find a solution no matter what I do (any suggestions are hugely appreciated). I'm thinking about backing up my data and just starting over with Jaunty when it releases. Looks like a lot of things I struggled with in the past are being resolved with each new version of Ubuntu (TV out!!!!).

---

### Post by MBishton on 2009-03-18
Alejandro (or anyone else who can help);

I currently run VM workstation under Vista Home Premium on a tx1000 (tx1320US) to learn linux, but want to turn that around 180 degrees to run vista under UBUNTU. I want to learn enough to convert all five of my windows machines at home to ubuntu. 

I started to play by installing 8.10 64bit server on a 16GB thumb drive. It installed and booted immediately. Under the 80/20 rule, 20% effort gave me 80% of the desired functionality. Now I am at a point where the 80% effort kicks in for the last (but important) 20% functionality...

I currently use the WIFI and bluetooth a lot. I have ATT with a data plan, so I also use my cell in tethered mode via a USB cable or bluetooth. Being new to linux, I unfortunatly don't understand much of your linux shorthand when you explain things. 

Do you know where can I find step-by-step newbee instructions to: 
[LIST]
[*]Get WiFi to work (with WEP, etc).
[*]Get bluetooth to work in general.
[*]Tether my cell using USB or bluetooth.
[/LIST]
I haven't had any luck finding them yet.

Many thanks!

---

### Post by Textureglitch on 2009-03-19
I helped a friend setup Intrepid Ibex on a tx1410us laptop and had trouble getting the sound working. Using the "3stack" model name in alsa got the speakers working, but not the headphone jacks and there was no autosensing.

We got the front headphone jacks working properly (and muting the speakers when in use) by adding the following line at the bottom of /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=3stack-dig position_fix=0 single_cmd=0


The wireless, webcam, etc. worked out of the box. The touchscreen required the TouchKit package from the eGalax manufacturer.

---

### Post by crazyness003 on 2009-03-19
is anyone else having hardware issues with their tx lappies? (specifically wireless and video).
First my wi-fi went out, now my monitor wont start up (kinda pointless to hook up an external monitor, since its a tablet)
This angers me.

---

### Post by redenex on 2009-03-25
> **gborzi said:**
> Hello to everyone,
I have recently installed Intrepid on my TX1350el, and as with Hardy I made a package for evtouch with a patch to fix the rotation issue. The package (for amd64) and the diff file are attached to this post.

When I run the deb file it says some helper files are missing, what did I do wrong?

---

### Post by gborzi on 2009-03-26
> **redenex said:**
> When I run the deb file it says some helper files are missing, what did I do wrong?

Can you please post the command used to run the deb file (I suppose you mean install) and the error messages?

---

### Post by mkarnicki on 2009-05-26
Do you guys also have problem with the touchscreen 'mouse drag' ? It totally disappeared for me, I can't drag icons or draw with my tx1320us. And I'm looking for help, with no luck yet.

---

### Post by Favux on 2009-05-26
Hi mkarnicki,

On this launchpad bugreport Tom Jaeger has some fixes followed by Ramaddan towards the bottom, including a deb.  See:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

---

### Post by qhimq on 2009-05-26
thanks!

```

cd /tmp
sudo apt-get build-dep xserver-xorg-input-evtouch
apt-get source xserver-xorg-input-evtouch
cd xf86-input-evtouch-0.8.7/
rm debian/patches/02-buttonless-device.patch
wget -O debian/patches/02-buttonless-device.patch http://launchpadlibrarian.net/26529094/02-buttonless-device.patch
echo 02-buttonless-device.patch >> debian/patches/series
dpkg-buildpackage
sudo dpkg -i ../xserver-xorg-input-evtouch_0.8.8-0ubuntu3_i386.deb

```

worked for me!

---

### Post by tapsevarg on 2009-06-19
Hello,
I was told this thread would help me activate the touchscreen on my TX1000. But it isn't doing the trick. Forgive me, I am a noob. But could somebody tell me what's wrong?

I think I figured out part of the problem:

```
cd xf86-input-evtouch-0.8.7/
```

I think this line should be 0.8.8... not 0.8.7 as listed.

Second:

```
sudo dpkg -i ../xserver-xorg-input-evtouch_0.8.8-0ubuntu3_i386.deb 
```

The "i386" suffix seems like a mistake, I think it's supposed to be "_amd64".

Even with these things fixed the touchscreen isn't working. I open the Evtouch calibration thing and it still says that no touchscreen is recognized.

---

### Post by Favux on 2009-06-19
Hi tapsevarg,

Sorry it isn't working for you.  You might want to check the tmp directory and see what the two apt-get's got you.  It looks like someone else had a problem with it to, see post #5 this thread:  [http://ubuntuforums.org/showthread.php?t=1166052](http://ubuntuforums.org/showthread.php?t=1166052)

I'm assuming you already tried the evtouch in Synaptic Package Manager in System > Administration.  Maybe the deb by Ramadd (5-22-09) an near the bottom of the bug report will work for you:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)  It's called "xserver-xorg-input-evtouch_0.8.8-0ubuntu3_i386.deb".  You download it onto your Desktop and then double click it and it should install itself if you have the right CPU architecture etc.

---

### Post by tapsevarg on 2009-06-19
Thanks Favux for the help! Still no luck. I tried both of your new suggestions, I also edited my last post. I tried downloading ramadd's file, but I get stopped with the package installer saying "error wrong archtitecture i386".

Two lines of qhimq's code code get no response from terminal:

```
rm debian/patches/02-buttonless-device.patch
```

After pressing enter nothing happens and brings the prompt back up as if you simply pressed enter

Same goes for this line:

```
echo 02-buttonless-device.patch >> debian/patches/series
```

Even when I tried your suggestion and changed the order.... nothing, no response.


So I am just guessing those two lines might be an issue, as they do nothing.





Could my whole problem be that I am using the 64bit Jaunty?

---

### Post by tapsevarg on 2009-06-19
This is the error I get even when I make the two corrections in my edited post a few ago.

```
Applying patches...Patch debian/patches/02-buttonless-device.patch does not exist
Applying patch 20_fix_calibrate_submission_directions.patch
patching file calibrate.sh

Applying patch 21_more_calibration_fixups.patch
patching file evtouch.c
patching file ev_calibrate.c

Applying patch debian/patches/02-buttonless-device.patch
failed! (check stampdir/log/patch for details)
make: *** [stampdir/patch] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
```

---

### Post by Favux on 2009-06-19
Hi tapsevarg,

Wow, you are learning rapidly!  Hopefully someone who knows more about patching than me will come along and bail us out.  In a terminal if you type "man patch" you'll get the manual.  From that:

"patch’s exit status is 0 if all hunks are applied successfully, 1 if some hunks  cannot  be applied, and 2 if there is more serious trouble."

So "02-buttonless-device.patch" is in serious trouble.  I don't what Error 1 means.

---

### Post by tapsevarg on 2009-06-20
Fauvux,

To satisfy my curiosity, I reinstalled Jaunty with the 32 bit desktop version.

It made no difference. And the two lines of code I pointed that did nothin in terminal, well they still do nothing.

I don't think the 64bit version was the problem.

---

### Post by Favux on 2009-06-20
Hi tapsevarg,

I agree, it looks like it's not a 64 bit vs 32 bit problem.

Don't know what else to add.  Have you verified that there is a 02-buttonless-device in debian/patches/series?  Also actually check in (open in a text editor) 02-buttonless-device.patch and see where it expects to be applied.  It's usually near the beginning.

If that appears to be fruitless try PMing qhimq.  Hopefully he's still around and will bail us out.

---

### Post by hojthojt on 2009-06-25
Hi,
have not been very active on the Ubuntu forums lately, but I have been using Ubuntu on my tx1151ea since 7.10 (always the 64 bit version). I'm glad to see all the improvements made during this time. In the beginning I had to tweak and patch a lot to make everything work, but now (9.04 with all updates taken) almost everything works out of the box.

I only had three problems:
a) the touchscreen click-and-hold not working
b) screen rotation together with a working touchscreen calibration
c) the laptop overheats

Thanks to qhimq and his post earlier in this thread:
[http://ubuntuforums.org/showpost.php?p=7352571&postcount=16](http://ubuntuforums.org/showpost.php?p=7352571&postcount=16)
I have solved a). Thank you qhimq. 

Any tips for b) and c) would be appreciated. I have seen other posts on this forum talking about these issues but I could not really understand what the current status is or if there are any good workarounds.

I did not experience any overheat problems with earlier Ubuntu versions on this laptop. Actually Vista overheating this laptop was one of the reasons for me to switch from the beginning since it ran much cooler with Ubuntu. But that advantage seems to have gone away :-(

regards
HojtHojt

---

### Post by tapsevarg on 2009-06-26
Hojthojt,

I wish I could say qhimq's code solved my problem. No matter what I try it seems that it never recognizes that I have a touchscreen. I bought it second hand and now wonder whether it even has a touchscreen.

Not sure if the TX1151EA has the same problems as the TX1000.

The TX1000 is notorius for massively overheating. Specifically the GPU overheats. Part of the problem is the GPU gets so hot it melts it's own solder taking it away from the connection. I had to take mine completely apart, build a heatshield, and use a heatgun to reflow the solder. New thermal paste was used on CPU/GPU as well as slipping a penny between the GPU and heatsink. I know it sounds crazy but it brought the laptop back from the dead.

Now after I did all of this I found the laptop still ran red hot, but no problems. _But recently I went into the bios and doubled the amount of shared ram for graphics card. This has made a huge difference. I guess this lightened the load on the GPU._


Can you offer any advice getting my touchscreen recognized?
Two lines of code did nothing in terminal. I suspect they might be the problems. Did you tweak these lines? If so, to what?

```
rm debian/patches/02-buttonless-device.patch
```
```
echo 02-buttonless-device.patch >> debian/patches/series
```

---

### Post by qhimq on 2009-06-26
my post was to get the hold and click working.  With my computer, ubuntu already had my touch screen working, but the hold and click wasn't.

I can't help you with getting that working, due to ubuntu just setting it up for me automatically straight from the install.  I agree it doesn't look like a 32 , 64bit problem.  Just for trivial details, I have it on a 32bit.

i havn't turned on my tx1000 in awhile, should it show your touchscreen thing in:
lspci
or
lsusb
?

I'm guessing it should be in your lsusb. idk, good luck though!  My wireless isn't in my lspci and I can't get wireless anymore, so who knows, maybe your touchscreen disappeared.

---

### Post by hojthojt on 2009-06-29
Hi tapsevarg,
as for qhimq, my touchscreen was working right from the start with the support from evtouch already built into Ubuntu 9.04. My problem, as qhimq correctly pointed out, was the click and hold problem (that I solved using qhimq:s post).

Here is my output from lsusb:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 004: ID 064e:a111 Suyin Corp. 
Bus 001 Device 003: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"

```

The second entry is the touchscreen. 

I have had my tx1151ea for almost 3 years now, and I have had it serviced twice. 

The first time it suddenly went completely dead -> The service center switched the motherboard. I suspect that the problem was heat related (something similar to what tapsevarg described).

The second time the touchscreen stopped working (then it wasn't listed when running lsusb) -> The service center switched the entire display.

So tapsevarg, if you are unlucky, your touchscreen might be broken as mine was. 

I also know that the tx1000 is famous for overheating, but my problem is that it ran much cooler with earlier versions of Ubuntu (i.e before Jaunty). In Jaunty both CPU cores is running at 20-40 % all the time (even when I'm just typing this in Firefox). Xorg, firefox and compiz.real seem to be the processes taking most CPU. The power save mode of the CPU is set to "ondemand" which means that it just runs at 800 MHz during low load.

-> the GPU is around 80 deg C and the core temp is around 55 deg C.

/HojtHojt

---

### Post by Thalarse on 2009-06-30
> **tapsevarg said:**
> Hojthojt,

I wish I could say qhimq's code solved my problem. No matter what I try it seems that it never recognizes that I have a touchscreen. I bought it second hand and now wonder whether it even has a touchscreen.



My tx1210ca doesn't have a touchscreen, remote, or (obviouly) a stylus. I was very disappointed when I got it, but it has since proved to be a good laptop - and because it's not really a standard hardware layout it has been a good machine to learn linux on :p 


I was having trouble getting flash and my bluetooth gps receiver to work under 9.04, so I went back to 8.04 and while I have gotten flash and the gps working, the other things that don't work under Hardy is worse. I think I'll take what I have learned with the bluetooth and try again in Jaunty - and let time take care of the flash issue. Youtube is a distraction anyway haha. 

Other than that I seem to be having an issue with the gpu being rather hot. Under Hardy the gpu is at 74c and the cpus are at 51c. That's with firefox and xgps running, and that's it. With Jaunty the cpus were the same but the gpu was usually at 80c. I have attempted to pull the laptop apart, but didn't have a small enough screwdriver to remove the tiny screws in the dvd drive bay. I'll try again, I think, at some point in the future. 

One last thing I've noticed. Under Hardy the gnome-power-manager program has an option in Power History to graph the amount of power in watts the machine is using (though currently it's stuck at zero), wheras later versions of unbuntu don't have that option. I would think it would be a handy thing for a laptop if it worked.

---

### Post by omegaphyr on 2009-08-30
Hey all, 
I haven't been to excited about the evtouch in the repositories. It seems to not quite know where the cursor should be(even after the ump-teenth time recalibrating) or start writing right away in various programs. So if anyone is interested in another solution I found one. 

Go to [http://home.eeti.com.tw/]("http://home.eeti.com.tw/") and click on "Touch Drivers" link. Navigate to linux and grab the BETA for which ever version you're running. The website seems to be about 4-6 months behind on Ubuntu releases so this may not work right away with releases newer than Jaunty. But be patient they seem pretty consistent with their updates. 

extract the file and cd to its location. open a terminal and type: 

sudo sh setup.sh

follow the commands, hit (3) because it's a USB touch screen. Blacklist anything it says to. then Restart X. 

Open a terminal and type: 

eGalaxTouch

Do the calibration and see if it works after applying the changes. If is not working properly you may have to edit your xorg a bit like i did. here's what i did for that. 

open a terminal and type 
sudo gedit /etc/X11/xorg.conf

look for this 
Section "InputDevice"
	Identifier "EETI"
	Driver "egalax"
	Option "Device" "usbauto"
	Option "Parameters" "/var/lib/eeti.param"
	Option "ScreenNo" "0"
	Option "SkipClick" "1"
EndSection

Change the option "SkipClip" from "1" to "0" and save

after restarting my touch screen worked like a charm and seemed to work better than the option from the repositories

good luck.

(sorry for the crappy format, this is my first post)

---

### Post by hvymtlsteve on 2009-09-08
Hey guys, I seem to be having new wireless issues. 
For most of this year I haven't had any use for the wireless, but I remember it was working last time I tried to use it (June).
I recently upgraded my kernel so I figure this would be the source of my problem, but anyway I tried to use the wireless this week and discovered that I can't turn the card on with the hardware switch, and the card no longer shows up on lspci (it used to). 
Nor does it show up on lshw -C network.
I went ahead and put on a fresh 9.04 thinking it might work out of the box like with 8.10, but no dice.

I can't get my tx on the internet at the moment using ethernet directly to the modem (and don't have an extra cat5 cable to try the router's wired outs) so I'll have to try again in a couple days I guess.
But will enabling the restricted hardware likely fix this?

Update -- No dice. Wireless doesn't show up on the "restricted hardware" menu. 
It seems people have commonly had issues with wireless cards going bad on these HP notebooks, so maybe that is what happened.

UPDATE-- Well, the day before yesterday, my wireless mysteriously reappeared when I turned the computer on for a few minutes. However, yesterday I tried to power up, only to find that the machine will not power up completely. 
The fan spins up a little bit, and all the LEDs light up, but the display is dead.
When I had searched around a little about the wireless issue last week, I also found reports of this happening.. Wi-fi, first, then the whole computer. According to the threads out there, it has to do with the NVIDIA chipset. 

This doesn't have anything to do with Ubuntu but I thought I'd leave my comment here to give everybody the heads up.
A lot of the complaints said they had the computer for about 2 years... exactly how long I've had mine. So that might be the magic number?

---

### Post by Alejandro Nova on 2009-11-24
I've definitely settled on Mandriva on this cycle (I can stand the click and hold issue, but I DO want KDE, and you know what I mean. I'll be waiting for that Timelord project, though ;)).

So, is there any official solution for the click and drag issue with Karmic? I would like to know. In the meantime, I can tell you that Mandriva indeed is heavier than Ubuntu or Kubuntu.

The overheating issue can be overcome installing nVidia series 190 driver (it can manage on its own PowerMizer)

Edit: The wireless issue is a classic. Ubuntu is a good way to partially avoid the overheating that kills this laptop under Vista/7 (Aero demands a lot of power from the chipset). I fixed it by going to a non-HP service center. They charged me $150, but they actually changed the southbridge (they had the machinery to remove a chip and install another one into my motherboard). Try to REPAIR it. At least, here in Chile HP charges me about $650 for changing my motherboard, and that doesn't include the months of waiting while my notebook goes to Mexico. If you have an extended warranty, use it, but consider the additional time. And do not buy HP again. That service center recommended me Toshiba.

---

### Post by jvalal on 2010-03-04
Hello,

I run the program and on line E i get No X configuration file found.  Is there a fix for this?
thanks

---

### Post by championswimmer on 2010-05-06
**[COLOR=red]Installing UBUNTU 9.04 on HP TX1000 laptop (touchscreen+fingerprint)[/COLOR]**
  [COLOR=red]1.       [/COLOR][COLOR=red]Install Ubuntu 9.04 Jaunty[/COLOR]
  [COLOR=red]2.       [/COLOR][COLOR=red]Connect to Internet and open SYSTEM>ADMINISTRATION>HARDWARE DRIVERS [/COLOR]
  [COLOR=red]3.       [/COLOR][COLOR=red]Install NVIDIA current version[/COLOR]
  [COLOR=red]4.       [/COLOR][COLOR=red]Install Broadcomm B43 driver[/COLOR]
  [COLOR=red]5.       [/COLOR][COLOR=red]Install software modem driver[/COLOR]
  [COLOR=red]6.       [/COLOR][COLOR=red]Download eGalaxDriver from website [/COLOR][COLOR=#76923C][[COLOR=#76923C]http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm[/COLOR]]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")[/COLOR][COLOR=red][/COLOR]
  [COLOR=red](download for kernel 2.6.xx)[/COLOR]
  [COLOR=red]7.       [/COLOR][COLOR=red]Extract tarball and run setup.sh from terminal with sudo[/COLOR]
  [COLOR=red]8.       [/COLOR][COLOR=red]Restart Computer and run (with Alt+F2) “eGalaxTouch” (without quotes and linux is case sensitive)[/COLOR]
  [COLOR=red]9.       [/COLOR][COLOR=red]Configure your touchscreen[/COLOR]
  [COLOR=red]10.   [/COLOR][COLOR=red]Open xorg.conf with following command[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]
  [COLOR=red]11.   [/COLOR][COLOR=red]Under Section “Device” add the following line[/COLOR]
  [COLOR=red][FONT=&quot]Option  “RandRRotation”        “True”[/FONT][/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]12.   [/COLOR][COLOR=red]Create two launchers on your gnome panel with following commands:-[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]xrandr –o 1                (for tablet mode) P.S. u can set it “3” as well if u want opposite rotation)[/COLOR]
  [COLOR=red]xrandr –o 0                        (for Laptop mode)[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]13.   [/COLOR][COLOR=red]Install Cellwriter from synaptic[/COLOR]
  [COLOR=red]14.   [/COLOR][COLOR=red]Install xournal from synaptic[/COLOR]
  [COLOR=red]15.   [/COLOR][COLOR=red]Install the following for finger print recognition[/COLOR]
  [COLOR=red]lib-fprint[/COLOR]
  [COLOR=red]libpam-fprint[/COLOR]
  [COLOR=red]fprint-demo[/COLOR]
  [COLOR=red]16.   [/COLOR][COLOR=red]Open file common-auth[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/pam.d/common-auth[/FONT][/COLOR]
  [COLOR=red](delete all lines in the file and paste these lines)[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    required           pam_unix.so   nullok_secure[/FONT][/COLOR]
  [COLOR=red][FONT=&quot] [/FONT][/COLOR]
  [COLOR=red](the first line can be copied 3-4 times if u want to allow more than 1 chance to register fingerprint)[/COLOR]
  [COLOR=red]17.   [/COLOR][COLOR=red]Create keyboard shortcuts for screen rotation (here is an example)[/COLOR]
  [COLOR=red]Key                                                                                        Command[/COLOR]
  [COLOR=red]Ctrl+Alt+UP                                                                       xrandr –o 0[/COLOR]
  [COLOR=red]Ctrl+Alt+LEFT                                                                    xrandr –o 1[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red](Notes: This Guide will work for any UBUNTU installation upto Karmic (9.10). Unfortunately in Lucid, the developers have tried to provide native support for Touchsdcreen and Nvidia but it has turned out to be sloppy. And there is no xorg file as well. So viable options are to uninstall nv and nouveau drivers and install Nvidia and the run sudo nvidia-xconfig from command line. After that follow steps 4 to 17)[/COLOR]

---

### Post by Potturi on 2010-06-24
Can anyone help me to figure out if the webcam in my Tx1000z is working or not please ?

I've just installed Lucid Lynx successfully with all the functions working (Thanks to Alex for putting up this thread without which I'd have completely rolled back to Windows ).

---

