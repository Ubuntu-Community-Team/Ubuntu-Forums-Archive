---
title: "WoW with open source drivers"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by ffxigotenks on 2009-11-03
I have a radeon X1300 which is supported by the open source drivers, in 9.04 I was able to run WoW perfectly in d3d mode and get 27fps using the open source drivers. I am now running 9.10 and have the open source drivers configured and am using the exact same xorg.conf that was in 9.04 but when I run WoW the login screen is near frozen with the animation running a frame roughly every 5 seconds... I've got the DisabledExtenions registry change in effect as well as ffxglow, ffxdeath, and M2useshaders all disabled, I've even tried running in openGL with no more success.. is there any way for me to find out what's the problem with either my xorg.conf or my WoW setup?

my Config.wtf
```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "450.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET accountName "sporcic"
SET movie "0"
SET expansionMovie "0"
SET realmList "skrserver.no-ip.info:3725"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET timingTestError "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET showToolsUI "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "0.10000000149012"
SET Sound_SFXVolume "0.30000001192093"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0.30000001192093"
SET spellEffectLevel "6"
SET realmName "Shattered Kalimdor"
SET mouseInvertPitch "1"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET uiScale "1"
SET autoSelfCast "1"
SET questFadingDisable "1"
SET profanityFilter "0"
SET patchlist "us.version.worldofwarcraft.com"
SET guildMemberNotify "1"
SET checkAddonVersion "0"
SET ChatBubblesParty "1"
SET displayFreeBagSlots "1"
SET cameraView "2"
SET pixelShaders "1"
SET specular "1"
SET groundEffectDensity "24"
SET ffxGlow "0"
```

and my Xorg.conf
```
# /.../
Section "Files"
	FontPath     "/usr/share/fonts/misc:unscaled"
	FontPath     "/usr/share/fonts/local"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/Type1"
	FontPath     "/usr/share/fonts/URW"
	FontPath     "/usr/share/fonts/Speedo"
	FontPath     "/usr/share/fonts/PEX"
	FontPath     "/usr/share/fonts/cyrillic"
	FontPath     "/usr/share/fonts/latin2/misc:unscaled"
	FontPath     "/usr/share/fonts/latin2/75dpi:unscaled"
	FontPath     "/usr/share/fonts/latin2/100dpi:unscaled"
	FontPath     "/usr/share/fonts/latin2/Type1"
	FontPath     "/usr/share/fonts/latin7/75dpi:unscaled"
	FontPath     "/usr/share/fonts/baekmuk:unscaled"
	FontPath     "/usr/share/fonts/japanese:unscaled"
	FontPath     "/usr/share/fonts/kwintv"
	FontPath     "/usr/share/fonts/truetype"
	FontPath     "/usr/share/fonts/uni:unscaled"
	FontPath     "/usr/share/fonts/CID"
	FontPath     "/usr/share/fonts/ucs/misc:unscaled"
	FontPath     "/usr/share/fonts/ucs/75dpi:unscaled"
	FontPath     "/usr/share/fonts/ucs/100dpi:unscaled"
	FontPath     "/usr/share/fonts/hellas/misc:unscaled"
	FontPath     "/usr/share/fonts/hellas/75dpi:unscaled"
	FontPath     "/usr/share/fonts/hellas/100dpi:unscaled"
	FontPath     "/usr/share/fonts/hellas/Type1"
	FontPath     "/usr/share/fonts/misc/sgi:unscaled"
	FontPath     "/usr/share/fonts/xtest"
	FontPath     "/opt/kde3/share/fonts"
	# commented out by update-manager, HAL is now used
	#	InputDevices   "/dev/gpmdata"
	# commented out by update-manager, HAL is now used
	#	InputDevices   "/dev/input/mice"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Viewport  0 0
		Depth     24
		Modes    "1600x1200@60" "1024x768" "800x600" "640x480"
		Virtual	2304 1024
	EndSubSection
EndSection

Section "Module"
	Load  "dbe"
	Load  "type1"
	Load  "freetype"
	Load  "extmod"
	Load  "glx"
	Load  "dri"
	SubSection "extmod"
		Option	"omit xfree86-dga"
	EndSubSection
EndSection

Section "DRI"
	Group        "video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier     "Layout[all]"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Option	    "Clone" "on"
	Option	    "Xinerama" "off"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Option	    "DesktopSetup" "horizontal"
	Option	    "MonitorLyaout" "AUTO,AUTO"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "UseInternalAGPGART" "no"
	Option	    "UseFastTLS" "2"
	Option	    "Mode2" "1024x768"
	BusID       "PCI:2:0:0"
	Option	    "XAANoOffscreenPixmaps" "true"
	Driver	"ati"
EndSection

Section "Modes"
	Identifier     "Modes[0]"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
	Option	    "AllowMouseOpenFail" "on"
	Option	    "IgnoreABI" "on"
	Option	    "ZapWarning" "on"
EndSection

```

---

### Post by ffxigotenks on 2009-11-05
bump

---

### Post by ffxigotenks on 2009-11-05
if it helps, I'm getting these errors in xorg.0.log

```

(WW) RADEON(0): Option "DesktopSetup" is not used
(WW) RADEON(0): Option "MonitorLyaout" is not used
(WW) RADEON(0): Option "EnablePrivateBackZ" is not used
(WW) RADEON(0): Option "UseInternalAGPGART" is not used
(WW) RADEON(0): Option "UseFastTLS" is not used
(WW) RADEON(0): Option "Mode2" is not used
(WW) RADEON(0): Option "XAANoOffscreenPixmaps" is not used
(WW) RADEON(0): Option "VendorName" is not used
(WW) RADEON(0): Option "ModelName" is not used

```

---

### Post by ffxigotenks on 2009-11-09
anyone?

---

### Post by EJeanmaire on 2009-11-09
> **ffxigotenks said:**
> anyone?

Just a shot in the dark, change driver from "ati" to "radeon"

---

### Post by ffxigotenks on 2009-11-13
unfortunately that didn't work, it's still doing it.. has anyone gotten WoW to work on 9.10 using ATI open source drivers?

---

### Post by dazer26 on 2009-11-13
What version of wine are you using?  I use the latest develpment version, Wine 1.1.33, with no problems.  I know when I used to use the stable 1.01 version I couldn't run wow in d3d mode, only opengl.  My desktop uses the closed source nvidia driver, but my laptop uses an open source ati driver (mobility radeon, very old lol) and it runs wow alright in Ubuntu.

---

### Post by ffxigotenks on 2009-11-13
I'm trying to install 1.1.33, but all I seem to get is 1.1.32, which is what I was trying to use before

---

### Post by ffxigotenks on 2009-11-14
dazer, could I get a look at your config.wtf and your xorg.conf? maybe then I'll figure out where I went wrong

---

### Post by ffxigotenks on 2009-11-20
could anyone using ATI open source drivers playing WoW on 9.10 show me their xorg.conf and config.wtf?

---

### Post by ffxigotenks on 2009-11-21
please?

---

### Post by jessiebrownjr on 2009-11-21
> **ffxigotenks said:**
> please?


Ahhhh.... I'm so glad I finally quit playing WoW after 4 years... I remember on tuesdays fiending for the server to come back up so I could get my nerd on :-p

I couldn't get it to work on my laptop or desktop either btw, So the best of luck to ya!

---

### Post by ffxigotenks on 2009-11-21
> **jessiebrownjr said:**
> Ahhhh.... I'm so glad I finally quit playing WoW after 4 years... I remember on tuesdays fiending for the server to come back up so I could get my nerd on :-p

I couldn't get it to work on my laptop or desktop either btw, So the best of luck to ya!

thakfully, I'm just on a private server, I was able to get it to work in intrepid and Jaunty, but I have no idea why the same solutions that worked then, won't work now in karmic

---

