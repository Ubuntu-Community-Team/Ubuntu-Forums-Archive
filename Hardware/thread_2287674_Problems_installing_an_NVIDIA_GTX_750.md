---
title: "Problems installing an NVIDIA GTX 750"
date: 2015-07-21
forum: Hardware
---

### Post by SeijiSensei on 2015-07-21
I just bought[ this card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127870") and had a few problems getting Ubuntu (Kubuntu in my case) to recognize it and work properly.  I thought I'd pass along what steps I needed to take in case others have these problems.

First, after installation, the nouveau drivers are used.  The display looked terrible with nearly unreadable text.  I proceeded to try to install the appropriate proprietary driver in a variety of unsuccessful ways.  Running the "Driver Manager" from Kubuntu's System Settings did not detect the card at all, though it was clearly recognized by Linux when I ran lspci.  So I did what I had done in the past with NVIDIA hardware and ran 
```
sudo apt-get install nvidia-current
```
This installed the 304 driver which apparently is incompatible with the 750.  I saw little improvement in the display.  After hunting around on the Internet, I decided to use the 331 driver with
```
sudo apt-get install nvidia-331
```
This worked properly but had the same persistent problem every NVIDIA adapter I've used has where the text fonts are incredibly tiny if the adapter is connected to an HDTV.  I fixed this with the normal workaround.  First I ran
```
sudo nvidia-xconfig
```
to generate /etc/X11/xorg.conf.  Then I edited that file (as root with sudo) and changed the "Monitor" section to read:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Option         "DPI" "96x96"  <== added this line
EndSection

```
Then after rebooting everything looked fine...

...until I tried to play a video and send the audio out the HDMI cable.  No sound at all.  When I was using the onboard Intel adapter HDMI audio "just worked."  On a machine with an ATI adapter HDMI sound also worked as soon as I installed the fglrx proprietary adapter.  In this case, the problem was really obscure.

I could see the adapter using the normal tools like pavucontrol or the Multimedia component of Kubuntu's System Settings.  But in every case I could not change the settings.  On Kubuntu the adapter was greyed-out.  I have never encountered this problem before, so it was off to the Internet once again.  I found the answer [here](http://askubuntu.com/questions/512621/unable-to-get-audio-through-hdmi-connection-to-tv-with-ubuntu-14-04).  It's a problem with permissions.

Following the suggestion in that posting I added myself to the audio, pulse, pulse-access, video and voice groups, then rebooted. Now I could access the device and make it the default for audio output.  I've never had to do this before with either Intel or ATI cards.  I don't know why it is needed with NVIDIA hardware, but adding myself to those groups solved the problem.

By the way, this is the best price I've seen for a GTX 750 adapter with 2 GB of video RAM.

---

### Post by PaulW2U on 2015-07-21
*Thread moved to **Hardware**.*

---

### Post by Vladlenin5000 on 2015-07-21
It would be recognized and the proper driver offered - 346 - in 15.04.
I was under the impression 331 (the higher official version for 14.04) isn't enough*. Most 14.04 users just add the PPA and install 346 or higher straight away.

*EDIT: [for GTX750 and mobile variants]

---

### Post by dino99 on 2015-07-21
yeah start purging your installed one, and dont use xconfig (reserved for troubles); and install nvidia -352 (xorg-edgers ppa)

---

### Post by SeijiSensei on 2015-07-21
I prefer to stick with the repositories; 331 works fine.  I don't game on Linux so performance doesn't matter.

Rather than a discussion about which driver to use, I was hoping to prompt a discussion about the need to change permissions in order to get HDMI audio to work.  As I said, I've never had this problem with other hardware.  Apparently it's a pretty obscure problem, too, considering how many places I had to look to find the solution.  I didn't need to do anything to get the Intel adapter to send audio over HDMI.

I was also surprised the card wasn't recognized at all by the Driver Manager.  It's hardly that new.

---

### Post by SeijiSensei on 2015-07-24
Update:

I went ahead and installed the PPA, then installed nvidia-346.  After rebooting, I got a notification from the driver manager that a more recent version was available, so I upgraded to 352.  I'm still using the xorg.conf I created earlier.

However I now have a new problem.  If the computer is left idle for an extended period, say overnight, the screen is blank and does not reappear if I use the keyboard or mouse.  I have to disconnect and reconnect the HDMI cable to reactivate the display.  This didn't happen with the Intel adapter, and I haven't made any changes to the power saving or screensaver options after installing the NVIDIA card.  This is really annoying, too, since I keep the computer behind the TV where access to its back panel is limited.

I upgraded to 352 in hopes it would solve this problem, but it did not.

I didn't see anything relevant I could change in the NVIDIA X Server Settings tool either.

I do route the HDMI signal through my Yamaha A/V receiver rather than directly into the TV, though that didn't matter when I was using the Intel adapter.

---

### Post by SeijiSensei on 2015-07-25
^
Any ideas about why I have to unplug and replug the HDMI cable?  I had to do so again this morning, and it's quite annoying.

---

### Post by dino99 on 2015-07-25
> **SeijiSensei said:**
> ^
Any ideas about why I have to unplug and replug the HDMI cable?  I had to do so again this morning, and it's quite annoying.

well you are not alone with that awaking blank screen; i've seen lot of posts recently complaining about that (maybe a quick search may help) and might not be related to the driver itself, but something dealing with events: is that an faulty/missing apparmor rule ? or a gvfs, or udev,  or xorg ? Could be a kernel trouble too (test the 4.1 for example to narrow down that problem, or install wily).

---

### Post by efflandt on 2015-07-26
I was initially surprised that my GTX 750 Ti did "not" work with the nvidia 304 version in nvidia-current of 14.04 when it "did" work with whatever updated 304 version was nvidia-current in 12.04. But I have never had any font size issues with nvidia drivers, other than a larger font would help on my 15.6" 1080p laptop. My desktop used to use a 19" 1280x1024 monitor years ago (GT 220 then GT 430 that failed after a year) and in recent years have been using a 32" 1080p HDTV with GTX 550 Ti and now GTX 750 Ti. Font size has never been a problem on those. I am currently running xorg-edgers nvidia-352 on my desktop PC (and nvidia-331-updates from normal repos on laptop).

I don't think I have had a problem with HDMI audio since before 12.04 (I forget if it was 11.10 or 10.04). In fact I was quite surprised one time when I was using digital audio for wireless headset, headset battery died, disconnected its dongle, and audio came out of my TV through DVI to HDMI cable. Apparently Nvidia cards since somewhere in the GT/GTX 200 series have been able to do audio through DVI. But I normally use 2.1 analog stereo speakers with subwoofer.

As far as the screen going off, HDTVs do not do dpms like monitors do to put them into, and wake them up from, power saving standby mode. So when your computer tries to put the screen to sleep (even if the computer itself does not go into standby) and the TV no longer gets a video signal, it turns off (mine turns off 10 minutes after no signal). But mine does not automatically turn on when it gets a video signal, so I use the remote to turn my HDTV on before hitting a key (usually Shift) on my keyboard to wake up my video card.

There is something called CEC that might also play a part. That can do remote control through HDMI including turning things on/off, although, I don't think Ubuntu versions have that implemented by default. I just knew that from running XBMC on a Raspberry Pi ($35 computer on credit card size circuit board) and being able to control menus in Linux with the TV remote. It is the same process used if you have a matching TV and Blu-Ray player and can use either remote to control both devices.

---

### Post by SeijiSensei on 2015-07-27
> **dino99 said:**
> well you are not alone with that awaking blank screen; i've seen lot of posts recently complaining about that (maybe a quick search may help) and might not be related to the driver itself, but something dealing with events: is that an faulty/missing apparmor rule ? or a gvfs, or udev,  or xorg ? Could be a kernel trouble too (test the 4.1 for example to narrow down that problem, or install wily).
As I say, it only occurs with this NVIDIA device.  The built-in Intel adapter didn't have the problem, nor did an HP laptop with an ATI adapter when it was connected to this TV.

I guess I'm glad that I'm not alone, but the array of possible solutions is a bit daunting. I don't have the patience to solve stuff like this any more.  I just want things to work as expected.

> **efflandt said:**
> in recent years have been using a 32" 1080p HDTV with GTX 550 Ti and now GTX 750 Ti. Font size has never been a problem on those.
I also had miniscule fonts when it was using a 40" Sony Bravia as the display device. I wondered if it had to do with something missing from the EDID information, but this TV is an LG and had the same problem.  I might run a test with the DPI option turned off to see if it persists.

> I don't think I have had a problem with HDMI audio since before 12.04 (I forget if it was 11.10 or 10.04).
As I said, the solution in my case was to add myself to some of the audio-related groups. Maybe if I had installed Kubuntu with the card in place the installer might have added me to those groups.  Still this is a really obscure problem, and one neither the Intel adapter on this machine, nor the ATI adapter on another machine, requires.

> But mine does not automatically turn on when it gets a video signal, so I use the remote to turn my HDTV on before hitting a key (usually Shift) on my keyboard to wake up my video card.
I turn on the TV first as well, but hitting a key doesn't bring the screen back.

---

### Post by SeijiSensei on 2015-07-27
The screen-blanking problem has been reported since 2006!

I'm trying the solution of adding
```
Option "NvAGP" "1"
```
to xorg.conf and adding 
```

SAVE_VBE_STATE=false
POST_VIDEO=false

```
to /etc/default/acpi-support.  We'll see if that helps.  If that's not sufficient, I'll try blacklisting the intel_agpgart module.

---

