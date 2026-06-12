---
title: "Lenovo Thinkpad t400"
date: 2008-09-17
forum: Hardware
---

### Post by robertpolson on 2008-09-17
If anyone has successfully installed Ubuntu on Lenovo Thinkpad t400 with all the drivers working please post how you did it. 

Specifically:

Video drivers

Webcam

Power Management

Wireless - [http://ubuntuforums.org/showpost.php?p=5754065&postcount=62](http://ubuntuforums.org/showpost.php?p=5754065&postcount=62)

---

### Post by hdavid on 2008-09-18
I am wondering how difficult it will be to install Ubuntu on my T400 which will arrive in a few weeks. Please post the difficulties and success you have.

David

---

### Post by robertpolson on 2008-09-18
I managed to install Ubuntu 8.10 Intrepid. You have to go into bios "F1" and configure so that the Descrete graphics is on only and disable OS auto detect of the video. That way ATI will work as Intel does not work.

The problem came right after I updated Ubuntu which broke my wireless. I can see all the networks but cannot connect to any of them.

I think I will come back to this when Ubuntu is closer to final release or even final as this is too much time being wasted.

---

### Post by AstralCobra on 2008-09-22
Howdy,

I just purchased a T400 and decided it was destined to be my first Linux Box. I was to use 8.04 Hardy Heron. The journey was long and shitty.  Now after about a month of accelerated learning, melted vista partitions, wifi from hell, intel drivers from hell, and much else besides (mostly from hell) i can say that wifi will work, i cant figure out compiz/video drivers, and lshw shows about three other unclaimed devices (mostly SmBus controllers).  So write back with more specific questions,
Will/AstralCobra/Uliseslima

---

### Post by mglukhovsky on 2008-09-22
I'm running 8.04 (Hardy Heron) and everything works out of the box except for the webcam, wireless (Intel WiFi Link 5300), the fingerprint reader and the video card (ATI Mobility Radeon 3470). 

The fglrx drivers work fine once you set the video card to Discrete Only in the BIOS and remove OS autodetection. The kernel sees the Intel integrated video card as being first before the ATI card, so it will remain using Mesa until the ATI card is first (done by setting the option to Discrete in the BIOS).

Trying to use the webcam with a program like Cheese hardlocks the system.

Another point: I have 3GB of RAM installed but Ubuntu sees only 2.5GB. I don't think this is a 32-bit vs 64-bit issue, but if anyone has any insight, let me know.

I will try 8.10 when the final release is issued, as new hardware + frequent updates on a development build = disaster.

I do have to say though, that with a SSD and 3GB of RAM the machine is amazingly fast. I mean, blindingly fast. I love this thing.

---

### Post by robertpolson on 2008-09-22
Please post how specifically did you install ATi drivers ?

What was the guide you used ?

---

### Post by mglukhovsky on 2008-09-23
Robert, I replied in the other thread you started. Pretty much I just used the Restricted Drivers Manager and it worked fine (with Switchable Graphics off).

[http://ubuntuforums.org/showthread.php?t=926860&highlight=t400](http://ubuntuforums.org/showthread.php?t=926860&highlight=t400)

---

### Post by robertpolson on 2008-09-23
This takes care of the flickering:

[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by BroNardo on 2008-09-24
Any development on this? I have a ThinkPad T400 with integrated graphics only. Intel x4500MHD. Works fine if I use "vesa" drivers on Ubuntu 8.04, but can't get intel drivers to work.

There's very little info about x4500MHD w/r to Ubuntu online.
Seems like Intrepid Alpha5+ fixes the problems, I'm trying to install Alpha 6 and could need some support. Might create a new thread for this.

-b

---

### Post by Charlie708 on 2008-09-25
Vesa is working pretty good with my T400 with 4500M only too.  I checked Intel's site for drivers, and they seem to have the files mixed up.  Trying to get the Linux driver source throws an *.exe at me, while the release notes for what the download contains is very different.

---

### Post by robertpolson on 2008-09-26
Please be specific on how you got vesa drivers working ?

---

### Post by BroNardo on 2008-09-26
With 8.04 all I had to do was to change xorg.conf to

Driver    "vesa"

in the device section. Intrepid Alpha 6 was a little more difficult, I managed to get it to run with vesa eventually and now got the new intel drivers working after some time. Several glitches, but works.

---

### Post by wubrgamer on 2008-09-26
How's the T400 work now?

Let's say I just got one today, with an 4965 N wireless card, would ubuntu intrepid install perfectly on it?

Let's say I try and do so in a few months? Will it work then?

---

### Post by robertpolson on 2008-09-30
Try and test it and let us know.

---

### Post by robertpolson on 2008-10-03
> **BroNardo said:**
> With 8.04 all I had to do was to change xorg.conf to

Driver    "vesa"

in the device section. Intrepid Alpha 6 was a little more difficult, I managed to get it to run with vesa eventually and now got the new intel drivers working after some time. Several glitches, but works.

How did you get the intel drivers to work

---

### Post by robertpolson on 2008-10-04
If someone successfully installed Intrepid beta on T400 please post what did you do with the video drivers ?

I have flickering on my screen all the time. It is not that bad, but still noticeable.

---

### Post by wubrgamer on 2008-10-04
+1

---

### Post by BroNardo on 2008-10-04
I'm trying to remember how I got Intel drivers running on Intrepid.
Generally speaking, this is what I did:

o Got the Alternative Install CD for Ubuntu Intrepid alpha 6
o Installed Ubuntu via text-based installer
o Booted to a shell, got my WiFi working from the shell (PM me or google if you need help with this), and ran  asystem upate (sudo apt-get upgrade)
o Started X 

I've formated my drive in the meantime so I'll have to go through this procedure again, which is good 'cause this time I'll write it down exactly and let you guys know.

-b

---

### Post by beartung on 2008-10-07
i make my t400 a98 worked with gentoo.
only webcam not work 

bios:
   Graphics Device: Discrete&#65292;
   OS Detection for Switchable Graphics: Disabled
kernel: 
   2.6.27-rc5, only pre patch rc5 can make 5100agn work :(
graphics:
   ati-driver-installer-8-9-x86.x86_64.run, make 3d work, but need a patch for 2.6.27

  
kernel setting:

wireless:
Device Drivers => Network device surppot => wireless LAN
check mac80211, intel wifi core, intel wifi next gen AGN

CONFIG_WLAN_80211=y

CONFIG_IWLWIFI=y

CONFIG_IWLCORE=y

CONFIG_IWLWIFI_LEDS=y

CONFIG_IWLWIFI_RFKILL=y

CONFIG_IWLWIFI_DEBUG=y

CONFIG_IWLAGN=y

CONFIG_IWLAGN_SPECTRUM_MEASUREMENT=y

CONFIG_IWLAGN_LEDS=y

CONFIG_IWL5000=y

audio:
Device Drivers => Sound Card surpport=>ALSA=>PCI sound devices=> Intel HD Audio

CONFIG_SND_HDA_INTEL=m
CONFIG_SND_HDA_HWDEP=y
CONFIG_SND_HDA_CODEC_REALTEK=y
CONFIG_SND_HDA_CODEC_ANALOG=y
CONFIG_SND_HDA_CODEC_SIGMATEL=y
CONFIG_SND_HDA_CODEC_VIA=y
CONFIG_SND_HDA_CODEC_ATIHDMI=y
CONFIG_SND_HDA_CODEC_CONEXANT=y
CONFIG_SND_HDA_CODEC_CMEDIA=y
CONFIG_SND_HDA_CODEC_SI3054=y
CONFIG_SND_HDA_GENERIC=y
CONFIG_SND_HDA_POWER_SAVE=y
CONFIG_SND_HDA_POWER_SAVE_DEFAULT=0

pc card:
MMC/SD card support
CONFIG_MMC_BLOCK=y
CONFIG_MMC_BLOCK_BOUNCE=y
CONFIG_SDIO_UART=y
# CONFIG_MMC_TEST is not set

#
# MMC/SD Host Controller Drivers
#
CONFIG_MMC_SDHCI=y
CONFIG_MMC_SDHCI_PCI=y
CONFIG_MMC_RICOH_MMC=y
# CONFIG_MMC_WBSD is not set
CONFIG_MMC_TIFM_SD=y
CONFIG_MMC_SDRICOH_CS=y
# CONFIG_MEMSTICK is not set
CONFIG_NEW_LEDS=y
CONFIG_LEDS_CLASS=y

---

### Post by legolas_w on 2008-10-17
Hi
Does any one could get T400 webcam to work in ubuntu?
Thanks.

---

### Post by legolas_w on 2008-10-18
> **legolas_w said:**
> Hi
Does any one could get T400 webcam to work in ubuntu?
Thanks.

Any comment or update?

Thanks

---

### Post by legolas_w on 2008-10-18
Hi,

Does anyone managed to use D400 integrated webcam in Ubuntu?

Thanks

---

### Post by jango4 on 2008-10-27
With Ubuntu 8.10 rc the integrated webcam works out-of-the-box!

---

### Post by lmp3 on 2008-10-27
what does *not* work out-of-the-box?

---

### Post by cmcginty on 2008-10-27
On Ubuntu 8.4.1 AMD64 Hardy Heron -> 10/30/08 Upgraded to AMD64 Intrepid Ibex

[COLOR=DarkGreen]**Audio:**[/COLOR]
[LIST]
[*]System initial starts up using ALSA output, however there was some error that was blocking the sound output. Switching to PulseAudio server (System->Prefs->Sound) for all output enabled audio.
[*]Using driver 'snd_hda_intel'
[/LIST]
[INDENT]**status:** Stock audio works fine using 'PulseAudio Server'.[/INDENT][COLOR=DarkGreen]**Ethernet:**[/COLOR][INDENT]**status:** Works great with stock driver 'e1000e_ich9m'[/INDENT][COLOR=DarkGreen]**Wireless:**[/COLOR]
[LIST]
[*]Installed the iwlwifi-5000-ucode-5.4.A.11 microcode file from Intel
[*]Built compat-wireless-2.6-old, and manually loaded the 'iwlagn' driver.
[*]Also tried 9/9/08 version of compat-wireless and Windows XP64 drivers using ndiswrapper. Both failed.
[*][COLOR=Green]FIXED[/COLOR]: after updated to adm64-8.10
[/LIST]
[INDENT]**status:** Works great on 8.10 only with 'iwlagn' driver.
[/INDENT][COLOR=DarkGreen]**Video (integrated only):**[/COLOR]
[LIST]
[*]Running Xorg with stock 'intel' video driver which allows full compiz features. ('glxgears' outputs ~1165 FPS)
[*]Successfully enabled VGA port and used RandR to create dual monitor desktop. However if you go over 2048x2048 resolution compiz is disabled. There are reports that a driver patch will bump the resolution up to 4096x4096.
[/LIST]
[INDENT]**Status:** Full acceleration when using laptop LCD.
[/INDENT][COLOR=DarkGreen]**Bluetooth:**[/COLOR]

[LIST]
[*]Had to use GUI to manually add detected input device. Was expecting a simple "allow to connect" popup box.
[/LIST]
[INDENT]**Status:** Works with my Lenovo laser mouse.
[/INDENT][COLOR=Orange]**Docking Station:**[/COLOR]
[LIST]
[*]System hangs/freezes if docking station looses power.
[*][COLOR=Silver][COLOR=Black][COLOR=Green]FIXED[/COLOR]: [/COLOR]USB ports on docking station do not work. [COLOR=Black](I think my hub was drawing too much power, but not an issue any more) [/COLOR]
[/COLOR]
[*][COLOR=Green]FIXED[/COLOR]: [COLOR=Silver]DVI not yet functional. [COLOR=Black](HDMI-1 and HDMI-2 detected with XRandR only after amd64-81.0 upgrade)[/COLOR]
[/COLOR]
[/LIST]
[INDENT]**Status:** See issues above.[/INDENT][COLOR=DarkGreen]**Suspend/Resume:**[/COLOR][INDENT]**Status:** Works fine after upgrade to amd64-8.10. (did not have any luck on 8.04)
[/INDENT]

---

### Post by lmp3 on 2008-10-28
thanks for the exhaustive reply!

it is reasonable to expect that these issues will be resolved with the next ubuntu release?

---

### Post by legolas_w on 2008-10-29
hi
How big the laptop compartment should be in order to fit a T400 with 9 cell battery? Does anyone here has a T400 with 9cell battery and a messenger bag?

thanks

---

### Post by cmcginty on 2008-10-29
[http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=13811](http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=13811)

---

### Post by cmcginty on 2008-10-29
.

---

### Post by hdavid on 2008-11-01
By know Ubuntu 8.10 is running since 2 days on my T400 and everything works really nice. I just take cmcginty's list and update it:

Audio:

    * Is only working if I am using a headset. Did not have any time yet to work on this. (was the same for me on 8.04)

Ethernet:
    * Works great out of the box

Wireless:

    * Works great out of the box

Video (integrated only):

    * Running without any problems. Not tested with dual monitor...

Bluetooth:

    * Runs out of the box.

Docking Station:

    * No testing, don't have yet one :(

Suspend/Resume:

    * Both work fine without any issues

---

### Post by MagiSu on 2008-11-01
Currently my hardware support information:

[SIZE="4"]**Video**[/SIZE]
It works well in most of cases. However, X freezes when using Google-Earth.
(integrated graph accelerator)

[SIZE="4"]**Wired Network**[/SIZE]
Works very well in e100e driver.

[SIZE="4"]**Wireless**[/SIZE]
The wireless network lamp never lit even downloading. Other parts work well.
Need to install backport drivers to support wireless, and have to blacklist ath_pci.
(Using PCI Express AR24xx)

[SIZE="4"]**Webcam**[/SIZE]
Works well. Color is a little dark.

[SIZE="4"]**Audio**[/SIZE]
Several problems. One is "mute" button do NOT mute the earphone. Another is the volume up/down button do NOT control the volume at all, have to use KMix.

[SIZE="4"]**Suspend/Hibernate**[/SIZE]
Recovery from hibernate costs more time than a normal boot, that is almost 2 minutes.
Suspend not tested.

Have not checked other parts.

---

### Post by legolas_w on 2008-11-02
Does anyone tried graphic switching and discrete graphic card of T400 in ubunut 8.10?
Does the ATI card works fine, i want to have some gamin too.

---

### Post by jango4 on 2008-11-04
There is an thinkwiki article existing with good information!

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400)

You are invited to post your experiences there to build an useful guide!
(So updating is also easier!)
Thanks jango

---

### Post by calcioguy9 on 2008-11-04
Has anyone had any luck getting 1280x800 resolution on the T400? Right now I'm stuck with 1024x768, which works but isn't as sharp as it could be. Also, I have had it randomly boot into 1280x800 a handful of times. I have no idea what is causing that.

However, other than that issue, everything has been working great!

---

### Post by cmcginty on 2008-11-05
I've had no problems getting native resolution of 1440x900. If your driver supports RandR (i.e. integrated Intel 4500MHD), then you can switch the resolution dynamically from the command line:

xrandr --output LVDS --mode 1280x800

---

### Post by legolas_w on 2008-11-05
Hi 
Has anyone been able to install 8.10 on T400 with discrete graphic card?
If yes, would you please post a how to?

Thanks

---

### Post by legolas_w on 2008-11-21
Hi

Does T400 has built-in microphone and does it works in Intrepid?

Thanks

---

### Post by Mikey-G on 2008-11-22
Does anyone have power management working on the T400?, I'm only getting about 1.5 hours battery life. That sucks rather hard, especially considering I get at least 4.25 hours with Vista.

---

### Post by Siúlóir on 2008-12-17
> **legolas_w said:**
> Hi 
Has anyone been able to install 8.10 on T400 with discrete graphic card?
If yes, would you please post a how to?

I got both cards running, however, not at the same time. I have to choose the card to use from the BIOS Config/Display menu and disable switchable graphics.

Using the hint at [this site]("http://ariel.vardi.free.fr/ariel//vaiosz.html") I created an additional rc-file **xinit_conf** and symlinked it into **/etc/rc2.d**. Its contents:

```
#!/bin/sh
VIDEO=`/usr/bin/lspci |/bin/grep -c ATI`

if [ "$VIDEO" = 1 ]; then
    cp -f /etc/X11/xorg.conf.ATI /etc/X11/xorg.conf
else
    cp -f /etc/X11/xorg.conf.INTEL /etc/X11/xorg.conf
fi

```

**xorg.conf.ATI**:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
    Load    "dri"
    Load    "extmod"
    Load    "record"
    Load    "dbe"
    Load    "GLcore"
    Load    "xtrap"
    Load    "freetype"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver      "intel"
EndSection

Section "DRI"
    Mode 0666
EndSection

```
**/etc/X11/xorg.conf.ATI**:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
    Option      "VideoOverlay"  "off"
    Option      "OpenGLOverlay"  "on"
    Option      "TexturedVideo"  "off"
        Driver  "fglrx"
EndSection

```

Cheers

Siúlóir

---

### Post by 10thmayfly on 2008-12-17
> **Mikey-G said:**
> Does anyone have power management working on the T400?, I'm only getting about 1.5 hours battery life. That sucks rather hard, especially considering I get at least 4.25 hours with Vista.
 

I'm getting this too. Switching between Discrete and Integrated graphics doesn't make much difference either. I have a 6 cell battery I thought it would last like 6 hours but I'm getting about the same numbers as this(that might be some other problem?). But the battery lives for Vista and Ubuntu still should be about the same shouldn't they?

---

### Post by dustynus on 2009-01-04
> **10thmayfly said:**
> I'm getting this too. Switching between Discrete and Integrated graphics doesn't make much difference either. I have a 6 cell battery I thought it would last like 6 hours but I'm getting about the same numbers as this(that might be some other problem?). But the battery lives for Vista and Ubuntu still should be about the same shouldn't they?


Ya I have a 9 cell battery which get's me around 8 hours on decent settings in XP with integrated on. From a fresh install on the amd64 8.10 with the stock kernel, using nothing but be on firefox typing this on half brightness, right now at about 50 % discharge the power history indicates averaging around 25 W... Telling me I have 1 hour left of battery..

In XP I average around 10 W, and vista used to get me at around 8 W doing the same thing..

Having a 9 cell and basically getting 2 hours of battery with a full charge is very dissapointing, my old macbook used to get about 2.5 hours in 8.04!

Hopefully someone can find a reason for this excessive power usage, as such a major lack in power is a turn off for using the t400 on battery.

I'll put on powertop ( sudo apt-get install powertop ) and see if I can tone it down a bit, although powertop usually changes smaller things, and doubt I will be able to get around the same the windows uses. I'll post if I figure anything out

:guitar:

---

### Post by bettlebrox on 2009-01-19
Disable bluetooth when your battery power,that extends battery power a lot.

---

### Post by Miguel on 2009-01-24
If you are getting 1.5h you have the "OS detection" option probably turned on for the BIOS. I mean, I'm somewhat disappointed with the battery I get on linux (4h with a 6 cell), but 1.5h means something is really wrong.

And I'm sorry being so late for Legolas' post, but the Webcam and the internal mic (the T400 does have one) work OK... at least on Ekiga. On skype, the webcam runs OK, but I haven't been able to make the mic work. It's probably because I'm running 64bit ubuntu, though.

Regarding the resolution, I've had 1440*900 since I installed Ubuntu with almost no issues, with either intel or radeon. Almost no issues means I've seen myself stuck into 1368*768 some times I've switched the computer to an external projector.

EDIT: My avatar is actually a picture I took with my T400 of myself doing childish stuff.

---

### Post by 10thmayfly on 2009-01-24
OS Detection is disabled.

What are things that could be wrong?

---

### Post by Miguel on 2009-01-24
> **10thmayfly said:**
> OS Detection is disabled.

What are things that could be wrong?

Then I suppose that you are choosing the Intel graphics card, right? Let's leave it that way, as for the moment gaining 2.5h of battery life may be more important than gaming.

EDIT: Could you install powertop and run it as root? What's the output it gives?

---

### Post by wirawan0 on 2009-02-09
This thread is quite crowded and information is dispersed everywhere. Could someone put a kind of "switchboard" at the beginning of this thread? E.g. there is a group for the wireless problem, then a group for suspend/hibernate. Each of these problems should be a separate thread (with a thread preferably specific to that problem alone).

I am proposing to use this thread as the general-purpose T400-related starting point, since its title is so generic.

Here's my first attempt: I had trouble with my wireless card (Intel 5100); I wonder if somebody else had this kind of problem:

[http://ubuntuforums.org/showthread.php?p=6704953#post6704953](http://ubuntuforums.org/showthread.php?p=6704953#post6704953)

Wirawan

---

### Post by hypn0toad on 2009-03-01
i setup 8.10 on my t400 that i got in the beginning of december.  here are my experiences for others that might be useful...

**Wireless**
i have had no issues with my wireless- they worked right out of the box. (using intel wifi link 5300)

**Graphics**
i had some issues with my videocard, as other people mentioned.  i have to disable switchable graphics, and disable os detectionn in my bios before i boot into ubuntu. (have the switchable amd/ati 3470)

with the default drivers
- i dont have any animations (not able to enable), but stuff works alright
- detected multiple monitors, had some issues extending desktop

with fglrx
- have window animation
[COLOR="Silver"]- videos flicker in media players (work okay at fullscreen)
- does not properly detect monitors- only sees one "unknown" monitor.  using the hardware keys on my laptop i can select between laptop, external, and mirrored but i can't extend.[/COLOR]
- os doesnt seem to have 3d abilities (or something?) e.g. google earth doesn't open.
[B](EDIT)
- fixed video flickering by following: [http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)
- fixed multiple monitors by running catalyst control center (Applications > Accessories)
[/B]

**Sound**
Very very annoying.  With the out of the box settings i had no sound on speakers, but headphones worked.

After messing around with stuff, and installing programs, it got screwed up.  I'm not sure what did it, but suddenly i had static instead of sound.  (i saw this has been mentioned before at places like [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275392](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275392) .. not sure if this is the main bug report but it shows i'm not crazy).

[COLOR="Silver"]It still does it if i leave it on the default settings.  However, it works when i put it on the OSS settings for playback (music without static).  Downside- seems to only allow one program to control it... so i can have video or music but not both.

Flash sound does not work.  I tried applying the flash sound patch (flashplugin-nonfree-extrasound) to no avail.  this is frustrating[/COLOR]

[B](EDIT)
With terminal command  alsamixer -Dhw found out that volume for PCM set at 00.  changed to 100, and hcanged all sound devices back to "Pulseaudio" or auto i forget.  viola! everything works again.  no static, mixing, and flash sound.[/B]

**Battery Life**
Horrible.  In vista i get 5 hours, ubuntu less than 2- even with cpu freq clocked down to 800MHz.  granted i have my videocard switched to discreet all the time, but in vista if i leave it in discreet graphics i still get 4 hrs life.

**Conclusion**
ubuntu works alright on the t400.  everything takes some tweaking but works eventually.

---

### Post by plim on 2009-04-28
Anyone else have a problem with the volume mute button on the keyboard?
My vol up/down works fine but volume mute doesn't do anything. It doesn't seem to register a keypress (e.g. in keyboard shortcuts).

Other than that mine is working fine out of the box. First installed 8.10 32-bit and now have 9.04 64-bit. In both the power usage is rather high. Haven't tried webcam yet.

---

### Post by vancouverite on 2009-04-28
> **plim said:**
> Anyone else have a problem with the volume mute button on the keyboard?
My vol up/down works fine but volume mute doesn't do anything. It doesn't seem to register a keypress (e.g. in keyboard shortcuts).

Other than that mine is working fine out of the box. First installed 8.10 32-bit and now have 9.04 64-bit. In both the power usage is rather high. Haven't tried webcam yet.

Mine works to turn sound off, but won't turn it back on.  Also it does not show the muting notification.  To get sound back I have to use the *up* volume button.

For power usage, I am using integrated graphics with a 9 cell and tend to get about 4.5 hr battery life.  I am certainly open to ways to improve this!

I wanted to use a 32 bit system as I found the 64 bit one still a little buggy and couldn't get all the software that I wanted for it. In the end I stuck with the 32 bit but had to install the server kernel and headers to use the full 4GB of ram that my system shipped with (desktop kernel only gave me 2.9 GB...).  This doesn't seem to be a problem as my video drivers work and the VirtualBox kernel module worked after I recompiled it using */etc/init.d/vboxdvr setup*.

Overall, Ubuntu 9.04 runs quite well on this laptop. Web cam works and so did audio and 3D graphics out of the box with the integrated card.  I think that I will wait until switching has been figured out before installing the discrete card drivers.  Also, I do wish the finger print reader worked - but I bet that will be figured out pretty soon!

Van

---

### Post by legolas_w on 2009-04-28
Hi
does anyone installed 9.04 on T400?
I am just wondering whether everything works out of the box or not. specially the fingerprint reader and the switchable graphic card.


thanks

---

### Post by vancouverite on 2009-04-28
Hi legolas_w,
I have 9.04 32bit and everything seems to work *except* the finger print reader and the switchable graphics.  There is a very good description and some tips on the thinkwiki site:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400)

Cheers,
Van

---

### Post by cmcginty on 2009-04-28
@legolas_w

I'm running 9.04 64-bit since Thursday. 

Everything is working fine here. 9.04 resolved hangups when suspending while docked and a kacpid bug when re-docking the laptop in suspend/active state.

The only other open issue is that I have no 3D accelerated graphics when running with dual-monitors (3840x1200) off of the docking station (probably also effects LCD+VGA). I belive this is a bug in the DRI drivers or maybe the hardware really can't handle more than a 2048x2048 desktop.

I don't have fingerprint reader or switchable graphics on my system.

---

### Post by tutwabee on 2009-05-02
**@hypn0toad:**
Thanks for the tip about the static.  This has been bothering me for a few days now.  Changing PCM fixed it.

> **plim said:**
> Anyone else have a problem with the volume mute button on the keyboard?
My vol up/down works fine but volume mute doesn't do anything. It doesn't seem to register a keypress (e.g. in keyboard shortcuts).

Other than that mine is working fine out of the box. First installed 8.10 32-bit and now have 9.04 64-bit. In both the power usage is rather high. Haven't tried webcam yet.

**@plim:**
The mute button is a hardware mute.  I believe it allows the hardware to mute all sounds output, including the system beep.  It does not send a signal and it only has the function of muting.  This is actually pretty convenient imo because I like to know that when I press the mute button the sound will always mute and never unmute.  The hardware should automatically unmute if you press the "up volume" button.

---

### Post by Miguel on 2009-05-04
Hi again guys,

I noticed this weekend that my Cycle count is extremely high, bringing back past memories of the laptop-killing bug. I did a quick estimation and it happens that the average Load Cycle count per boot is around 120 (after 6 months of use), while on my old Dell Inspiron 8600 it's around 39 (old disk died in Sept 2006, so this is after 2.5 years of similar use).

The Jaunty defaults for "hdparm -B" (power management) are 254 for AC and 128 for Battery. Well, it seems 254 is WAY too high, and so the HD never spools down. At least it hasn't in the last 5 hours. I don't know if that directly is the cause for the right palm rest to be slightly warmer than in WinXP (and yes, it bothers me even if it's a mere 2ºC). However, on Battery, 128 is too darned low. It's so low that yesterday I got like 100 load cycles in an hour.

Anyway, after 6 months, my load cycle is 55.5k. This means that in 4 years my HD will have like 440k cycles and be very close to death. With a more normal load (Dell-like), it should be 180k. That would be soo much better for my data.

In case you're interested, Hdparm says my HD is a 250 Gb [Seagate Momentus 5400.4](http://www.seagate.com/ww/v/index.jsp?vgnextoid=c7de03cf785c6110VgnVCM100000f5ee0a0aRCRD&locale=en-US).

And talking about power management, this takes me to my other pet peeve I have. It seems I'm losing my patience, because while others are reporting power consumption around 20W, I'm really really pissed to have around 11W. This is after "powertopping", of course. The thing is, even though the HD stops way too frequently in linux, I suspect it's one of the reasons why I average 1-2W more than in windows. I think that's the culprit, because if I fire up anything non-CPU demanding (i.e. WMP or MediaMonkey or even FireFox), wattage is very similar. Any ideas? I've attached a screenshot of WinXP with the PowerManager (in Spanish, not very aggressive settings, notice the Wattage).

By the way, this is a 2765 TDG (P8600, 4Gb DDR3, dual GPu running the Intel one, 250 Gb HD and normal CCFL 1440*900 screen).

*EDIT:* Should we fill a joint bug report regarding power consumption?

---

### Post by SteveONCSU on 2009-05-04
I just installed 9.04 on my T500, everything is working except the Intel 5300 wifi.  REALLY getting frustrating.  I've recompiled the kernel using old drivers.  Still hunting the forums for a solution.....

---

### Post by cmcginty on 2009-05-04
Make sure you have linux-firmware installed:

```
apt-get install linux-firmware
```

---

### Post by bebox on 2009-05-13
mute doesn't work...

---

### Post by Miguel on 2009-05-13
> **bebox said:**
> mute doesn't work...

Yes, it does.

---

### Post by harelguy on 2009-05-16
I recently got a t-400 and installed Jaunty on it.
I set it up to use the discrete graphics, and everything almost works perfectly (except the fingerprint reader).

What I can't get to work properly is the external monitor. I plug it in to the VGA port, I can switch to it using Shift-F7, but the Catalyst control center only lets me switch to the resolutions supported by the Laptop LCD, so I can't use 1280x1024 for example, which is the monitor's native resolution.

Has anyone encountered and solved this problem?

Thanks!

---

### Post by Miguel on 2009-05-16
Harleguy,

Have you tried using the integrated graphics card? I've succesfully used VGA-out with the Intel GPU using Intrepid. Once was actually a PhD Thesis defense of a colleague. So far I haven't tested with ether Jaunty or the ATi, though.

---

### Post by harelguy on 2009-05-16
Hi Miguel,

Thanks for the quick reply :)
I've actually tried switching, but since on boot Jaunty expects to see the ATI it kinda freaks out (LSD style - shifting colors, gradients) but no welcome screen. It won't even let me shift-F1 to a command prompt :(

Isn't there some way to tell the ATI control center to just add a resolution it hasn't recognized automatically?

---

### Post by Miguel on 2009-05-16
> **harelguy said:**
> Isn't there some way to tell the ATI control center to just add a resolution it hasn't recognized automatically?

To be honest with you, I run away from fglrx as fast as possible. It's much better than it was when I started using linux (2004) but it still is an unstable piece of code, especially for laptops. I suppose you could specify more stuff on Xorg.conf, but modesetting works quite reliably today. I really think your best bet is toggling Integrated Graphics on the BIOS and see how it goes. I just hope that the fglrx libGL.so won't interfere with the projector part.

<not rant> Features in Intel GPUs work more or less as expected. It would be cool to have video acceleration for non-MPEG-2 stuff, but stability wise I don't complain...

<rant> but I've realised that performance wise they suck much more than ATi, even more than ATi before 7-11 (the first new codebase OpenGL driver). I mean, the Intel 4500 MHD in all our T400 should be able to play OpenArena blazingly fast with all detail at native resolution... but I doesn't.

---

### Post by harelguy on 2009-05-17
I agree about the fglrx driver. I have an HTPC setup in my living room with an AMD 780G chipset (Radeon HD3200) and I really wanted to run Linux/XBMC on it for ideaological reasons :) But the damn thing could not play HD content if its life depended on it... Stuttering, sync issues, the lot. After a month of desperately fiddling with it I gave up and used XP. Sad to say it works like a charm.

But back to my t400 - Is there a way to switch graphics controller without reinstalling Ubuntu? When I switch in the BIOS and try to load ubuntu, it freaks out and hangs... Actually, I'm gonna try recovery mode and "Reconfigure X Server" option. I'll post back whether it worked.

---

### Post by Miguel on 2009-05-17
> **harelguy said:**
> 
But back to my t400 - Is there a way to switch graphics controller without reinstalling Ubuntu? When I switch in the BIOS and try to load ubuntu, it freaks out and hangs... Actually, I'm gonna try recovery mode and "Reconfigure X Server" option. I'll post back whether it worked.

It should be pretty much doable. I mean, I switch GPUs every so often to play games on my Windows partition (used to be XP, where switchable graphics didn't work, it's now 7 rc, where the switchable lenovo drivers don't work either). What I would do is:[LIST=1][*] Disable desktop effects (just in case, to avoid OpenGL crashes)
[*]Back up and then edit /etc/X11/xorg.conf and change "fglrx" for "intel" or just comment out that line and try your luck with X11 autodetection
[*]Enter the BIOS configuration and go to Config -> Display. Make sure "OS Detection" is disabled and then switch to "Integrated Graphics"
[*]Cross your fingers
[/LIST]

The worst that could happen is that X doesn't load. Really. I wouldn't try to enable desktop effects without unisntalling fglrx, though, because the proprietary libGL.so may crash. Personally, I keep my xorg.conf minimal, and have two options that apply to one GPU each. The other one just gives a warning when loading and doesn't apply. Note that I have ati 6.12.2 and intel 2.7.1 from the Ubuntu X-swat ppa.

```

Section "Monitor"
	Identifier	"Configured Monitor"
	DisplaySize	303 190
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2464 900
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option 		"FramebufferCompression" 	"true"
	Option		"DynamicClocks" 		"true"
	Option		"AccelMethod"			"UXA"
EndSection

```

---

### Post by harelguy on 2009-05-18
Thanks alot, youv'e been a real help!

I'll try out your suggestions when I can spare my laptop for 15 minutes :)

---

### Post by Gaahl on 2009-05-26
hi,

i got a T400 some days ago and just noticed that if the fan turns on it stays on. I have to disconnect and re-connect the ac adapter to stop the fan.
can someone confirm this behaviour ?

In Windows XP the fan slows down after a very short time, so it's not a hardware issue.

on my T61 this doesn't happen. Both running jaunty.

---

### Post by Gaahl on 2009-05-29
no one else here with this problem ? :eek:

---

### Post by Miguel on 2009-06-01
> **Gaahl said:**
> no one else here with this problem ? :eek:

I don't know if I have this problem, but I'd guess that it is related to HD power management. I've found out that the Ubuntu default of hdparm -B 254 is way too high for a decent HD power management under AC, while 128 is way too low for battery. I've done some tests and, for my seagate, 240 is much better for AC, while Battery is better served with 160 or so. Maybe your HD is getting hot and needs continuous ventilation in order to control the temperature.

BTW: Windows 7 RC is killing my hd. I've been playing some Baldur's Gate on it this weekend and smartctl records an impressive 850 load cycles in two bloody days.

---

### Post by harelguy on 2009-06-01
Just wanted to post an update on my graphics problem:
I had originally installed Ubuntu using the discrete graphics selected in the BIOS. This caused problems using an external monitor - Catalyst wouldn't recognize the proper screens and resolutions and so on. When I switched to Integrated Graphics in the BIOS, X would not even start up.

What solved it in the end was uninstalling the proprietary fglrx driver in Ubuntu (while still under Discrete), and then rebooting and switching to Integrated. 

I used miguel's suggestion and reverted the X configuration to just autodetect everything, and it did :)


Thanks for the help, and I hope this also helps someone!

Guy

---

### Post by Gaahl on 2009-06-02
> **Miguel said:**
> I don't know if I have this problem, but I'd guess that it is related to HD power management. I've found out that the Ubuntu default of hdparm -B 254 is way too high for a decent HD power management under AC, while 128 is way too low for battery. I've done some tests and, for my seagate, 240 is much better for AC, while Battery is better served with 160 or so. Maybe your HD is getting hot and needs continuous ventilation in order to control the temperature.

BTW: Windows 7 RC is killing my hd. I've been playing some Baldur's Gate on it this weekend and smartctl records an impressive 850 load cycles in two bloody days.

My HD gets warmer in Ubuntu than in Windows, thats right. But the fan problem is still there if i boot a live USB-stick. 

Could you check out if you have this fan behaviour too ? Watch some flash movies in fullscreen till the fan runs on level 2 (2800 rpm or so) than wait if it slows down after you have closed the flash application.

BTW: i opened a bug report...  [https://bugs.launchpad.net/bugs/381315](https://bugs.launchpad.net/bugs/381315)

---

### Post by sumod on 2009-06-09
Miguel,

What is your power usage graph for ubuntu like.... this is mine...

The first one is my typical usage pattern.. I guess, I went on to read a paper or something and so it went to ultralow power usage...

The second one, I was pretty much using it through out.. I would say, my usage on the avg is 19-20W.... with integrated graphics card.. or 25-28 with other one....

And what all did you try to get it to go low power..

T400+2GB+160+2*VGA's....

Thanks..
Sumod

---

### Post by Miguel on 2009-06-10
> **sumod said:**
> Miguel,

What is your power usage graph for ubuntu like.... this is mine...

The first one is my typical usage pattern.. I guess, I went on to read a paper or something and so it went to ultralow power usage...

The second one, I was pretty much using it through out.. I would say, my usage on the avg is 19-20W.... with integrated graphics card.. or 25-28 with other one....

And what all did you try to get it to go low power..

T400+2GB+160+2*VGA's....

Thanks..
Sumod

I'll try to put a power usage graph later, but it'll probably be very different. Keep in mind I don't really stress my laptop on normal usage, which encompasses firefox + claws-mail + terminal + vim. It's another thing when I watch my photos (10 MPixel, it can be quite intensive) or when I perform DFT calculations, but I never do that on battery. In any case, it seems that your power usage only soared once you put the AC adapter. When on Battery, it seemed a tad too high (around 16W), but I don't know what you were doing. Keep in mind that 16W means a battery life of around 3.5h on the 6cell battery.

In my laptop, in order to keep power usage down, I follow all the suggestions given by powertop. You may not want to disable CD-ROM polling if you plan to use it, since reenabling it requires some console magic. I have USB autosuspend activated in grub, and I have a slightly modified xorg.conf to lower power consumption from the intel card. The power consumption of the ATi card is ridiculously high without fglrx, although I haven't tried some very recent Xorg options. I also modified the options for laptop-mode (have a look at the files in /etc/laptop-mode/), and I tend not to use bluetooth or WiFi when not plugged in.

---

### Post by yankee83 on 2009-06-20
I got the following in my /etc/laptop-mode/conf.d/bluetooth.conf and laptop-mode enabled but still bluetooth is not turned off when disconnecting the ac adapter. I verified that the bluetooth adapter is connected as hci0 (with hcitool).

Any ideas?


```
CONTROL_BLUETOOTH=1

# Enable bluetooth on battery
BATT_ENABLE_BLUETOOTH=0

# Enable bluetooth on AC
AC_ENABLE_BLUETOOTH=1

# Bluetooth interfaces to enable/disable
BLUETOOTH_INTERFACES="hci0"
```

Thanks for the help.

---

### Post by legolas_w on 2009-06-22
Hi,

Is there any hope to get switchable graphic card work in Ubuntu 9.04 or 9.10?

Thanks.

---

### Post by Miguel on 2009-06-23
> **legolas_w said:**
> Hi,

Is there any hope to get switchable graphic card work in Ubuntu 9.04 or 9.10?

Thanks.

Let's put it this way: switchable graphics currently doesn't work on Windows 7 RC1. I wouldn't expect switchble graphics to work anytime soon. This is even truer with Kernel modesetting, I fear, because more GPU-related utilities are moving in-kernel.

EDIT: It seems the fan on my T400 is indeed running almost continuously at the lowest speed, even with all temperatures noticeably below 40 degrees.

---

### Post by SteveONCSU on 2009-08-19
I've got a T500 (same family).
 
My problems now are:
1) Wireless flaky as hell (intell 5300)
2) Power consumption is high (ive enabled laptop mode)
3) I have random AHCI problems, mainly when I shutdown, the laptop doesn't actually shutdown, it stays at the kernel.

---

### Post by drtrill on 2009-09-17
> **plim said:**
> Anyone else have a problem with the volume mute button on the keyboard?
My vol up/down works fine but volume mute doesn't do anything. It doesn't seem to register a keypress (e.g. in keyboard shortcuts).

Did someone have a fix for this? I am having the same problem, pressing mute doesn't actually do anything so I have to click the volume control on the top right in order to mute.

---

### Post by obiwankamote on 2009-09-28
With regards to #3, I usually just press ctrl+alt+del to force it to shutdown

---

### Post by obiwankamote on 2009-09-28
> **drtrill said:**
> Did someone have a fix for this? I am having the same problem, pressing mute doesn't actually do anything so I have to click the volume control on the top right in order to mute.
You have to set acpi_osi=Linux in the grub menu. In my case I modified /boot/grub/menu.lst and added the string making it look something like this:

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		8f9fc1ef-d83d-4663-8a7e-998b938bfb49
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=8f9fc1ef-d83d-4663-8a7e-998b938bfb49 ro quiet splash acpi_osi="Linux"
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

---

### Post by vancouverite on 2009-09-29
Hi all,
I have a new issue for you.  I have a t400 with Jaunty 64 bit and an integrated card reader.  The card reader works great for SD cards, but doesn't even register xD cards.  All the posts I've found have said that the 7-in-1 works out of the box, but I'm not sure if it has been properly tested.

I use mostly SD and would have said, "yes, it works" but xD seems not to.  Additionally, I'm not alone: [http://ubuntuforums.org/showthread.php?t=1103021](http://ubuntuforums.org/showthread.php?t=1103021).

lspci gives me this:

```
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```

But I don't know what that means.  The xD-Picture Card Controller shows up (15:00.5), but does that mean it should work?

Van

---

### Post by Miguel on 2009-09-30
> **vancouverite said:**
> 
But I don't know what that means.  The xD-Picture Card Controller shows up (15:00.5), but does that mean it should work?

Van

AFAIK, it doesn't. It just means that piece of hardware is correctly detected. BTW, I have the same lspci output and recently found out that xD cards don't work. What's more, inserting an xD card doesn't cause any message to appear in dmesg. I'll try that card later under Win7 to see if it works (sd cards work perfectly in all OS).

---

### Post by vancouverite on 2009-09-30
Hi all,
Just an update on the xD reader.  I found this link which has a long discussion of the problem:

[https://bugs.launchpad.net/debian/+source/linux/+bug/202490](https://bugs.launchpad.net/debian/+source/linux/+bug/202490)

It seems that the Ricoh driver is proprietary and that there is no intention of ever backing out a linux version.  So, for those wondering what does and doesn't work on the T400, the 7-in-1 card reader gets a "Partially Working".

Van

---

### Post by Miguel on 2009-10-01
> **sumod said:**
> Miguel,

What is your power usage graph for ubuntu like.... this is mine...

The first one is my typical usage pattern.. I guess, I went on to read a paper or something and so it went to ultralow power usage...

The second one, I was pretty much using it through out.. I would say, my usage on the avg is 19-20W.... with integrated graphics card.. or 25-28 with other one....

And what all did you try to get it to go low power..

T400+2GB+160+2*VGA's....

Thanks..
Sumod

OK, sorry for the delay. A few days ago I forgot my AC adapter at home and had to carry on battery. This is my power usage during work: legible screen, firefox with a few tabs, claws-mail, terminal, gvim, xdvi and running latex and ssh. Not too heavy, but not idle either.

---

### Post by sh4d0w808 on 2009-10-28
Hi,

I have a T400 also only with integrated intel video. Does anyone know, how can I set up extended desktop? I have a 22' Lenovo monitor, but I can only clone the display...

SOLVED - Compiz should be totally deactivated to get extended desktop.

---

### Post by mathyou on 2009-11-22
Hello fellow T400 owners,

Just wondering if you can help me with a small issue. I currently blacklisted the system beep which worked, but, if I close my laptop and then open it i.e. resume from sleep, then I get a different beep. Does anyone else get this? I realize it may be possible to disable system beep in bios but would rather not do that as it is sometime useful for diagnosing hardware failures.

Any help appreciated.
cheers
matt

---

### Post by legolas_w on 2009-11-22
Hi,

Has anyone been able to hibernate the T400?
I have upgraded from 9.04 to 9.10 and I can not hibernate it, it just goes to sleep mode (blinking moon led) and not to hibernate.

Unfortunately, sometimes when I try to wake it up from sleep, it does not come up and if it come, the wireless does not work at all.
I tried doing things like 

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

```

and it had no effect. It works just fine after a restart.


Thanks

---

### Post by mathyou on 2009-12-26
Just wondering how noisy your hard drives are? I have a constant fan noise from mine, anyone else? Is there some way to to make it run quieter as hddtemp says it is quite cool.

cheers
m

---

### Post by Miguel on 2010-01-01
> **mathyou said:**
> Just wondering how noisy your hard drives are? I have a constant fan noise from mine, anyone else? Is there some way to to make it run quieter as hddtemp says it is quite cool.

cheers
m

My fans are quiet in Ubuntu. Temps are also good, and as long as I set hdparm -B to anything reasonable (210 seems to be a great choice on AC), the computer is amazingly cool. Have I said that I love these centrino2 laptops?

BTW, I'm attaching a new power graph, done today. This is light browsing with chrome, with claws-mail and empathy open and working, as well as the power manager applet. All suggestions of powertop have been applied, and I'm using my wifi (BT is killed, though). This is a clean install of 64bit karmic, with some tweaks to laptop-mode.

As you see, an average of 12W is feasible. You can appreciate the time at which I was listening to Pink Floyd's DSotM, as well as browsing sites with flash. Not bad, but not stellar either. This consumption would give me about 4:30 on a fully charged 6 cell battery (56 W). Remember this laptop doesn't have a LED screen. 

My complaints are that my other partition (now running 32bit Vista Business) has a better consumption profile. I haven't run any serious measurements (windows is there for my zombie-killing addiction), but from what I see, I can average about 10.5W in the other OS. Mmm... I know that the HD power management is *much* more aggressive there but I fail to see where the additional gains come from. Maybe the intel graphics drivers are to blame.

Happy new year to everybody,

Miguel

---

### Post by legolas_w on 2010-01-04
I have problem with sleep functionality of my thinkpad t400.

sometimes when I awaken it from sleep by opening the lid, the moon LED start blinking and it hangs. keyboard does not work and I must shut it down and turn it on again to get it working. The drawback is that all open  works will be lost :(

Is there any solution for this? I have ubuntu 9.10 32 bit installed in it.


Thanks

---

### Post by Miguel on 2010-01-04
> **legolas_w said:**
> I have problem with sleep functionality of my thinkpad t400.

sometimes when I awaken it from sleep by opening the lid, the moon LED start blinking and it hangs. keyboard does not work and I must shut it down and turn it on again to get it working. The drawback is that all open  works will be lost :(

Is there any solution for this? I have ubuntu 9.10 32 bit installed in it.


Thanks

I also have random resume failures (64 bit Ubuntu 9.10). This has happened to me in both an upgrade since Intrepid and in a clean install. I'd say the failure rate is between 5 and 10%. Knowing this, I never ever let it go to sleep without saving the work I've done.

In my case, it looks like the machine is resuming... but then the moon lights up again.

I've got a very recent issue: I upgraded to the latest bios (3.09-1.05). Now, every time I reboot, the BIOS appears twice! Who knows what's happening. I've already resetted the bios to the default values, but no joy.

---

### Post by arangel on 2010-01-10
Anyone had any luck with hdaps and tp_smapi with a kernel other than 2.6.31-14-generic? (I could only make it work with this version)

Ubuntu 9.10 64bit.

---

### Post by rCXer on 2010-01-10
I have hdaps working on kernel 2.6.28-17 but on a t43p, a similar machine.  Which instructions are you using to install hdaps? Are you getting any errors?

---

### Post by emeraldgirl08 on 2010-02-02
I know this has probably been asked a thousand times over by now but... How in the world can I improve the graphics with the Intel X4500HD??? I checked FPS and came with 20 in full screen and 40 in small screen with this:

```
/usr/lib/xscreensaver/glblur -window -fp
```

I also used glxgears and came out with a disappointing scores:

upper 2000's with small screen
around 200 with full screen

I'm hoping someone can tell me how to tweak my settings. This is unacceptable. I can't believe that the 4500HD has been out for almost two years and this is the best it can get. I've tried other distros and I'm just flustered. My R51e gets better scores! Any help people???

---

