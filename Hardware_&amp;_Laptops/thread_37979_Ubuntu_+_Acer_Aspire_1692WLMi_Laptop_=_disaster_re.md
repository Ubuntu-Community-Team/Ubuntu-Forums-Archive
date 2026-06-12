---
title: "Ubuntu + Acer Aspire 1692WLMi Laptop = disaster recipe?"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by toxicfume on 2005-05-29
I recently got an Acer Aspire 1692WLMi laptop, which is a 1.7Ghz Inte Pentium M Centrino, with a Mobility Radeon X700 (and a Intel PRO Wireless 2200 B/G wireless network card).
 
 I decided to install Ubuntu on it, just to meet with a LOT of problems, and I have been spending a lot of time in the past few days trying to fix them with no available (thanks to all the nice people in #ubuntu, irc.freenode.net).
 
 The first problem is whenever Ubuntu boots up, I get a message before the initialization process which goes something like: PnPBIOS caused a fatal IO error..and it says to look for the latest BIOS from your manufacturer (which i already have).
 
 Secondly, The wireless card never seems to work, sometimes it detects the WAP, but most of the times it doesn't, and even when it does detect (which has actually happened only once so far), it would just not transfer or receive anything.
 
 The other problem I have is that, and this is the most irritating one --  X just never seems to work, it always go into a black screen. I tried the fglrx drivers, and they too don't run, always gives an error saynig it couldn't start up(in the blue screen). I've been cracking my head over this the most. :(
 
 And not to mention, i cannot even start ubuntu without the acpi=off argument, which means I don't get all the nice acpi featuers such as speedstep, etc.
 
 Does anyone else have any experience with Ubuntu on this laptop? Anyone ever gotten the screen to work? I'd be very, very interested, thanks :)

---

### Post by ::DoGG:: on 2005-05-29
Well... it`s always a lot of problems with notebooks cause the BIOS is mostly mnade for windows, so it`s not showing everything that linux want to see.
Second thing - setting up X is sometimes a pain, try to edit manually /etc/X11/xorg.conf file end under section "Device" change driver, try to use "vesa"
P.S. Don`t worry, i spend 1,5 week first time installed linux on my new laptop to setup everything working. :D

---

### Post by Djax on 2005-06-01
My laptop (Acer Aspire 1694WLMi) make me crazy too.

For the black screen, I fixed it by adding **an option **

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
        Driver          "ati"
        **Option          "MonitorLayout" "LVDS, TMDS"**
        BusID           "PCI:1:0:0"
EndSection
```

I think we have to wait for xorg-driver-fglrx 6.x.y-8.12.10-ubuntuZ to have the 3D acceleration. The mobility x700 chip is not yet recognized. 

The come back from X to the console mode is very ugly and scary. The screen become like a white magma. Sometimes I can see some text, sometime not. ](*,) 

I disable /etc/init.d/pcmcia because it makes my pc freezing.

```
**$** sudo chmod -x /etc/init.d/pcmcia
```

I fixed my DSDT ( I put the result on [acpi.sourceforge.net](http://acpi.sourceforge.net)  ) and append the result to initd. Because of the 1GB of RAM, I have to compile my own kernel, so I enable the option CONFIG_ACPI_INITRD

My boot option is:
```
title           Ubuntu, kernel 2.6.11.050529-ACPI
root            (hd0,2)
kernel          /vmlinuz-2.6.11.050529 root=/dev/hda7 ro pci=noacpi quiet splash
initrd          /initrd.img-2.6.11.050529-ACPI
savedefault
boot
```

Before the fixing, my boot option was:
```

title           Ubuntu, kernel 2.6.11.050529 (original)
root            (hd0,2)
kernel          /vmlinuz-2.6.11.050529 root=/dev/hda7 ro pci=noacpi acpi=off noapic nolapic vga=771 quiet splash
initrd          /initrd.img-2.6.11.050529
savedefault
boot

```

For the  Intel PRO Wireless 2200 B/G , I didn't find the right solution. 

Acer Aspire 1690 have a wifi switch, that control a  /sys/bus/pci/drivers/ipw2200/*/rf_kill switch. Some programs like [acerhk](http://www.informatik.hu-berlin.de/~tauber/acerhk/) or [omke](http://sourceforge.net/projects/omke/)  should be able to turn up its orange light and status. 

But I didn't found how to configure it proprely. I don't know if they are the proper solution.

---

### Post by dsolsona on 2005-06-02
I have an acer aspire 1691WLMi and I have some problems too with acpi.

To fix your acpi problems you will need to fix your dsdt tables, maybe at [http://acpi.sourceforge.net](http://acpi.sourceforge.net) you'll find one for your laptop.

You can boot with some acpi support booting with the option noapic in kernel (and in my laptop disablind pcmcia services too)

There's a lot of problems with acpi support on acer laptops as im starting to see.

---

### Post by toxicfume on 2005-06-05
[QUOTE=dsolsona]I have an acer aspire 1691WLMi and I have some problems too with acpi.

To fix your acpi problems you will need to fix your dsdt tables, maybe at [http://acpi.sourceforge.net](http://acpi.sourceforge.net) you'll find one for your laptop.

You can boot with some acpi support booting with the option noapic in kernel (and in my laptop disablind pcmcia services too)

There's a lot of problems with acpi support on acer laptops as im starting to see.[/QUOTE]
 Hi again everyone.
Thanks for all the answers :) 

Djax: Thanks a million for that!!!! I entered that option in xorg.conf and my display worked right away! Even at the antive 1280x800 resolution, so thank you so much for that :) It has made life a lot easier :P

Djax & dsolsona: Okay, i have somehow manged to get wireless working. I installed the latest IPW2200 drivers (ipw2200.sf.net). But apparently, the ubuntu gets confused with the killswitch on my laptop..I did a setkeycode command and it now seems to work fine. However...I tried to download acerhk, but the URL that you guys posted seems down :( So is it possible to get the file from elsewhere? Or if you guys have it can you please send it to me? Thank you in advance.

I guess I'll tackle ACPI after permanantly fixing the wireless connection...since doing the ACPI thing seems more difficult(unless you guys suggest otherwsie and couldgive me some help :))

Thanks once again!

---

### Post by Djax on 2005-06-05
Hi,

if you can get this ( bloody  :-x ) orange led-switch-button turning on, thank you to let us know how.

I don't know why [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)  is down, I put the last copy of acerhk I get [here](http://users.linuxbourg.ch/didier/informatique/acer1694/acerhk-0.5.23.tgz) 

Best regards

---

### Post by Djax on 2005-06-05
When I load the module acerhk (Acer Hotkey driver for Linux - acerhk-0.5.24.tgz):
```

**$** modprobe acerhk verbose=4
**$** dmesg | grep acerhk:
[I][COLOR=DarkRed]    acerhk: area from 0xf000 to 0xffff mapped to c00f0000
   acerhk: area from 0xe000 to 0xffff mapped to c00e0000
    acerhk: area from 0x400 to 0x13ff mapped to f8d64400
    acerhk: key mapping:
    acerhk: help 0x8a
    acerhk: setup 0xab
    acerhk: p1 0x94
    acerhk: p2 0x95
    acerhk: p3 0xca
    acerhk: www 0x96
    acerhk: mail 0x9b
    acerhk: wireless 0x93
    acerhk: power 0x74
    acerhk: mute 0x71
    acerhk: volup 0x73
    acerhk: voldn 0x72
    acerhk: res 0xab
    acerhk: close 0xce
    acerhk: open 0x86
    acerhk: wireless2 0x93
    acerhk: play 0xa4
    acerhk: stop 0xa6
    acerhk: prev 0xa5
    acerhk: next 0xa3
    acerhk: display 0xe2
    acerhk: registered input device
    acerhk: start search for model string at c00f0000
    acerhk: found model string 'TravelMate 4600' at c00f16af
    acerhk: offset from model string to function address: 0xc7b1
    acerhk: model string indicates unknown TM 4xx series
    acerhk: using call_bios_52x mode
    acerhk: supported keys: help setup
    acerhk: supported functions:
    acerhk: cmos index set to 0xf4
    acerhk: bios routine found at 0xc00fde60
    Acer Travelmate hotkey driver v0.5.24
    acerhk: starting key polling, every 200 ms[/COLOR][/I]

```

```

**$** cat /proc/driver/acerhk/info
  [I][COLOR=DarkRed]  Acer hotkeys version 0.5.24
    Model(Type) : TravelMate 4600(unknown)
    request handler : 0xc00fde60
    CMOS index : 0xf4
    events pending : 0
    kernel polling : active
    autoswitch wlan : disabled[/COLOR][/I]
```

I don't know if  an "TravelMate 4600" is like a  "Aspire 1690" (or “Acer Aspire 1694WLMi”).:?:  

No LEDs (wifi-orange or bluetooth-blue) are turning on for me when I do:

```
    **$** echo 1 > /proc/driver/acerhk/wirelessled

    **$** echo 1 > /proc/driver/acerhk/blueled
```

---

### Post by toxicfume on 2005-06-06
[QUOTE=Djax]When I load the module acerhk (Acer Hotkey driver for Linux - acerhk-0.5.24.tgz):
```

**$** modprobe acerhk verbose=4
**$** dmesg | grep acerhk:
[I][COLOR=DarkRed]    acerhk: area from 0xf000 to 0xffff mapped to c00f0000
   acerhk: area from 0xe000 to 0xffff mapped to c00e0000
    acerhk: area from 0x400 to 0x13ff mapped to f8d64400
    acerhk: key mapping:
    acerhk: help 0x8a
    acerhk: setup 0xab
    acerhk: p1 0x94
    acerhk: p2 0x95
    acerhk: p3 0xca
    acerhk: www 0x96
    acerhk: mail 0x9b
    acerhk: wireless 0x93
    acerhk: power 0x74
    acerhk: mute 0x71
    acerhk: volup 0x73
    acerhk: voldn 0x72
    acerhk: res 0xab
    acerhk: close 0xce
    acerhk: open 0x86
    acerhk: wireless2 0x93
    acerhk: play 0xa4
    acerhk: stop 0xa6
    acerhk: prev 0xa5
    acerhk: next 0xa3
    acerhk: display 0xe2
    acerhk: registered input device
    acerhk: start search for model string at c00f0000
    acerhk: found model string 'TravelMate 4600' at c00f16af
    acerhk: offset from model string to function address: 0xc7b1
    acerhk: model string indicates unknown TM 4xx series
    acerhk: using call_bios_52x mode
    acerhk: supported keys: help setup
    acerhk: supported functions:
    acerhk: cmos index set to 0xf4
    acerhk: bios routine found at 0xc00fde60
    Acer Travelmate hotkey driver v0.5.24
    acerhk: starting key polling, every 200 ms[/COLOR][/I]

```

```

**$** cat /proc/driver/acerhk/info
  [I][COLOR=DarkRed]  Acer hotkeys version 0.5.24
    Model(Type) : TravelMate 4600(unknown)
    request handler : 0xc00fde60
    CMOS index : 0xf4
    events pending : 0
    kernel polling : active
    autoswitch wlan : disabled[/COLOR][/I]
```

I don't know if  an "TravelMate 4600" is like a  "Aspire 1690" (or “Acer Aspire 1694WLMi”).:?:  

No LEDs (wifi-orange or bluetooth-blue) are turning on for me when I do:

```
    **$** echo 1 > /proc/driver/acerhk/wirelessled

    **$** echo 1 > /proc/driver/acerhk/blueled
```[/QUOTE]
 Same here, when i issuse those echo commands, nothing seems to happen. However, yesterday, for a while wireless stopped working for a while (for reasons unknown to me :|) but I was fortunate enough to talk to one of the guys that maintains [http://rfswitch.sf.net](http://rfswitch.sf.net) and he helped go through a few steps that made it work again. I've asked him and hopefully he will find more info on the Acer Aspire 1690 series of laptops shortly to list at [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

If anyone else has got this working on a similar model of laptop, please do post :)

---

### Post by Djax on 2005-06-07
I contact Olaf Tauber, Mr. acerhk and he add 1690 serie autodetection in the version 0.5.25.
So you can get at [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

With previous version, you have to load it with usedritek=0

So **cat /proc/driver/acerhk/info** says:
```
Acer hotkeys version 0.5.25
Model(Type)     : TravelMate 4600(Dritek)
request handler : 0xc00fde60
CMOS index      : not available
kernel polling  : active
autoswitch wlan : disabled
use of Dritek EC: disabled
```

what is said on rfswitch.sourceforge.net is  inexact. Aspire 1690 serie have a software and hardware switch and I don't think that the options are usefull.

**echo 1 > /proc/driver/acerhk/blueled** turns the blue led on and load the bluetooth USB device
dmesg: ```
usb 1-1: new full speed USB device using uhci_hcd and address 14
```
**echo 0 > /proc/driver/acerhk/blueled** turns the blue led off.
dmesg: ```
usb 1-1: USB disconnect, address 14
```

**echo 1 > /proc/driver/acerhk/led** makes the mail led blinking.
**echo 0 > /proc/driver/acerhk/led** turn the mail led off.

**echo 1 > /proc/driver/acerhk/wirelessled** makes "/sys/bus/pci/drivers/ipw2200/0000\:06\:03.0/rf_kill" = 0 or 1, but no orange light
**echo 0 > /proc/driver/averhk/wirelessled** makes "/sys/bus/pci/drivers/ipw2200/0000\:06\:03.0/rf_kill" = 2 or 3

As memo:
```
_rk_kill status:_
0 = RF kill not enabled (radio on)
1 = SW based RF kill active (radio off)
2 = HW based RF kill active (radio off)
3 = Both HW and SW RF kill active (radio off)
```

Well if someone can put the orange LED on, please leave a note.

---

### Post by Djax on 2005-06-07
> Well if someone can put the orange LED on, please leave a note. 

  \\:D/   Victory    \\:D/ 
 
The module **ipw2200** must have the option **led=1**

So I put the following line at at the end of my /etc/modules:

```
ipw2200 led=1
``` 

And the LED is blinking when a wifi network is not reached and stays on when it is reached.

---

### Post by toxicfume on 2005-06-08
[QUOTE=Djax]\\:D/   Victory    \\:D/ 
 
The module **ipw2200** must have the option **led=1**

So I put the following line at at the end of my /etc/modules:

```
ipw2200 led=1
``` 

And the LED is blinking when a wifi network is not reached and stays on when it is reached.[/QUOTE]
 Ah great! But I have previous version of acerhk installed...now how do i remove that previous version? So that I can install the new version now. Or no need to remove..can i just install over the previous version?

Thanks :)

---

### Post by Djax on 2005-06-08
> Ah great! But I have previous version of acerhk installed...now how do i remove that previous version? So that I can install the new version now. Or no need to remove..can i just install over the previous version? 

You can install the new over the previous.

 To use it, you have to unload the previous:
```
$ sudo modprobe -r acerhk
```
install the new one
```
$ sudo make install
``` 
 and load it:
 ```
$ sudo modprobe acerhk
```

```
$ cat /proc/driver/acerhk/info | grep version
```
should show
```
Acer hotkeys version 0.5.25
```

---

### Post by toxicfume on 2005-06-08
[QUOTE=Djax]You can install the new over the previous.

 To use it, you have to unload the previous:
```
$ sudo modprobe -r acerhk
```
install the new one
```
$ sudo make install
``` 
 and load it:
 ```
$ sudo modprobe acerhk
```

```
$ cat /proc/driver/acerhk/info | grep version
```
should show
```
Acer hotkeys version 0.5.25
```[/QUOTE]
Yay!! Looks like it all works now :D The Orange light blinks when scanning(but haven't been connected yet..but i'm sure that'll work as this has).

Even the mail light blinks now :D (didn't know that light even blinks lol :P)

However, I was wondering when you mentioned about the Bluetooth's blue led..cause that worked for me even after i just installed Ubuntu out of the box...i didn't have to do anything..howcome you didn't have it?  :???: 

One question though, whenever I press the Wireless lan key..even though it does work, light does blink..however, when i do **dmesg**, I get these two errors that appear alternatively:
```
atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0). 
atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known. 
atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known. 


atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.

```
Whats that about? I tried the following command ** setkeycodes e056 0xd6**, but nothing seemed to happen

---

### Post by Djax on 2005-06-08
> Even the mail light blinks now  (didn't know that light even blinks lol :P)

However, I was wondering when you mentioned about the Bluetooth's blue led..cause that worked for me even after i just installed Ubuntu out of the box...i didn't have to do anything..howcome you didn't have it? ??:  

Yes, the mail light was also a surprise for me when I "echo 1 >  led".  :grin: 

The blue light was working, but I had to press it (hardware), now it works also via software (echo 1 > bluetoothled). I'm happy that BT works even if I don't really need it.


> One question though, whenever I press the Wireless lan key..even though it does work, light does blink..however, when i do dmesg, I get these two errors that appear alternatively:
Code:

atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0). atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known. atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0). atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known. atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0). atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known. atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0). atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known. 

Yes some keys are not set, 

You have to set those missing keys.
I write a script **acer1694shk** in **/etc/init.d**. I have made some soft links to it from /etc/rc[2345].d

I remark that if I choose code higher than 255, the keycode are still unknown. It's why some of the choosen code are a bit wired.

```
#!/bin/sh
#-----------------------------------------------
#Acer Aspire 1694WLMi hotkeys
#-----------------------------------------------
SKC=/usr/bin/setkeycodes

#help (symb ?) (Fn+F1 )
#dmesg: setkeycodes e025 <keycode>
#define KEY_HELP                138
$SKC e025 138

#Acer eSetting (Fn+F2)
#dmesg: setkeycode e026 <keycode>
#define KEY_SETUP               141
$SKC e026 141


#Acer ePowerManagement (Fn+F3)
#dmesg: setkeycodes e027 <keycode>
#define KEY_MENU                139
$SKC e027 139

#Sleep (symb Zz) (Fn+F4) doesn't work
#no dmesg or xev
#define KEY_SLEEP               142

##Display Choice (symb [  ]|[#]) (Fn+F5)
#dmesg: setkeycode e029 <keycode>
#define KEY_CYCLEWINDOWS        154
$SKC e029 154

##Black screen (symb [*]>[ ]) (Fn+F6) works (turn off/on the LCD)
#no dmesg or xev

##Mousepad (Fn+F7) works (turn off/on the mousepad)
#dmesg: setkeycodes e072 <keycode> (off->on)
#define KEY_CHAT->->216
$SKC e072 216
#dmesg: setkeycodes e071 <keycode> (off->on)
#define KEY_SPORT  220
$SKC e071 220
##extra € (near direction keys,above left key)
#dmesg: setkeycodes e033 <keycode>
#define KEY_PROG3               202
$SKC e033 202

##extra $ (near direction keys,above right key)
#dmesg: setkeycodes e034 <keycode>
#define KEY_PROG4               203
$SKC e034 203

##Brightness Up (Fn+Right) make LCD brighter
#dmesg: setkeycodes e06e <keycode>
#define KEY_BRIGHTNESSUP        225
$SKC e06e 225

##acer P
#dmesg: setkeycodes e073 <keycode>
#define KEY_PROG1               148
$SKC e073 148

##acer e
#dmesg: setkeycodes e074 <keycode>
#define KEY_PROG2               149
$SKC e074 149

##Blue LED Switchbutton (bluetooth)
#dmesg: setkeycodes e057 <keycode> (off-> on, the blue light turns on)
#define KEY_SENDFILE 145$
$SKC e057 145
#dmesg: setkeycodes e058 <keycode> (on-> off, the blue light turns off)
#define KEY_DELETEFILE 146
$SKC e058 146

##Orange LED Switchbutton (wifi)
#dmesg: setkeycodes e055 <keycode> (/sys/bus/pci/drivers/ipw2200/0000\:06\:03.0/rf_kill goes from 2 to 0 or from 3 to 1)
#define KEY_CONNECT   218
$SKC e055 218
#dmesg: setkeycodes e056 <keycode> (/sys/bus/pci/drivers/ipw2200/0000\:06\:03.0/rf_kill goes from 0 to 2 or from 1 to 3)
#define KEY_FINANCE   219
$SKC e056 219

``` 

Then I used a program like **hotkeys**
```
$ sudo apt-get install hotkeys
``` 

Then I used my own keyboard definition:
**/usr/share/hotkeys/aceraspire1690.def**
```
<?xml version="1.0"?>

<definition>

  <config model="Acer Aspire 1690 Series Keyboard">

    <VolUp        keycode="176"/>
    <VolDown      keycode="174"/>
    <Mute         keycode="160"/>

     <userdef keycode="245" command="echo Acer Help">Acer help</userdef>
     <userdef keycode="151">Acer e</userdef>
     <userdef keycode="159">Acer P</userdef>

     <userdef keycode="194" >wifi on</userdef>
     <userdef keycode="195" >wifi off</userdef>
     <userdef keycode="199" >bluetooth on</userdef>
     <userdef keycode="200" >bluetooth off</userdef>


     <userdef keycode="193" >eSetting</userdef>
     <userdef keycode="158" >ePM</userdef>
     <userdef keycode="196" >MousePad On</userdef>
     <userdef keycode="121" >MousePad Off</userdef>
     <userdef keycode="166" >Windows Cycle</userdef>
     <userdef keycode="171" >Euro</userdef>
     <userdef keycode="172" >Dollars</userdef>

     <PrevTrack keycode="144"/>
     <Play      keycode="162"/>
     <Stop      keycode="164"/>
     <NextTrack keycode="153"/>

    <WebBrowser   keycode="178"/>
    <Email        keycode="236"/>

  </config>

  <contributor>
    <name>Didier CLERC</name>
    <email>didier-clercNOSPAM@linuxbourg.ch</email>
  </contributor>

</definition>
``` 

Then I config **/etc//etc/hotkeys.conf**
```
############################################################
# Global configuration for hotkeys                         #
############################################################

# These are the default values.
# A line starting with # is a comment.

### Specify the default keyboard  (without the .def extension) so you
### don't need to specify -t every time
 Kbd=aceraspire1690
# CDROM=/dev/cdrom

 PrevTrack=xmms --rew
 Play=xmms --play-pause
 Stop=xmms --stop
# Pause=xmms --pause
 NextTrack=xmms --fwd
# Rewind=

 WebBrowser=firefox
 Email=thunderbird
 Calculator=kcalc
# FileManager=gmc
# MyComputer=gmc
 MyDocuments=xmms
# Favorites=gnome-moz-remote --remote=openBookmarks
# Transfer=gtp
# Record=grecord
# Shell=xterm -rv
# ScreenSaver=xscreensaver-command -activate
# NewsReader=mozilla -news
# Communities=mozilla -remote 'openURL(http://slashdot.org)'
# Search=mozilla -remote 'openURL(http://google.com)'
# Idea=mozilla -remote 'openURL(http://sourceforge.net)'
# Shopping=mozilla -remote 'openURL(http://thinkgeek.com)'
# Go=mozilla -remote 'openURL(http://linux.com)'
# Print=lpr
# Rotate=

 osd_font=-arphic-ar pl kaitim big5-bold-i-normal--0-250-0-0-c-0-*-*
### For the color, you can either use the strings in /etc/X11/rgb.txt,
### or use the RGB syntax #RRGGBB, e.g. ##A086FF
 osd_color=LawnGreen
 osd_timeout=3
### osd_position is either 'top' or 'bottom'
 osd_position=bottom
 osd_offset=25

```

Then I load **hotkeys** et voilà.

the OSD doesn't seem to work for me yet

---

### Post by Djax on 2005-06-10
[QUOTE=Djax]\\:D/   Victory    \\:D/ 
 
The module **ipw2200** must have the option **led=1**

So I put the following line at at the end of my /etc/modules:

```
ipw2200 led=1
``` 

And the LED is blinking when a wifi network is not reached and stays on when it is reached.[/QUOTE]


There is a better place to put this options:
in  **/etc/modprobe.d/ipw2200** (you have to create it if missing)

```
options ipw2200 led=1
```

The **/etc/modules** is to load modules at every boot.

---

### Post by mcleodz on 2005-06-11
And how can we do to show battery's charge?

---

### Post by pistolas on 2005-06-15
Can someone please send me the .config of the kernel of 1690 series, and please tell me more detailed how to with the dsdt and ipw2200, please!!!  ](*,)

---

### Post by duffman25 on 2005-06-15
[QUOTE=pistolas]Can someone please send me the .config of the kernel of 1690 series, and please tell me more detailed how to with the dsdt and ipw2200, please!!!  ](*,)[/QUOTE]

check [this](http://ubuntuforums.org/showthread.php?t=37395&page=1) thread.

---

### Post by toxicfume on 2005-06-16
[QUOTE=pistolas]Can someone please send me the .config of the kernel of 1690 series, and please tell me more detailed how to with the dsdt and ipw2200, please!!!  ](*,)[/QUOTE]
 I'd like to see a DSDT for Acer Aspire 1692 :)

---

### Post by Djax on 2005-06-17
[QUOTE=toxicfume]I'd like to see a DSDT for Acer Aspire 1692 :)[/QUOTE]

The DSDT of 1691 and 1694 have been fixed, the 1692 may not differ too much.

if you can get your DSDT, we can try to fix it:
```
$**cat /proc/acpi/dsdt > ~/dsdt.dat** 
```

---

### Post by toxicfume on 2005-06-17
[QUOTE=Djax]The DSDT of 1691 and 1694 have been fixed, the 1692 may not differ too much.

if you can get your DSDT, we can try to fix it:
```
$**cat /proc/acpi/dsdt > ~/dsdt.dat** 
```[/QUOTE]
 So should I go ahead and get the 1691 or 1694 dsdt?

---

### Post by Djax on 2005-06-17
[QUOTE=pistolas]Can someone please send me the .config of the kernel of 1690 series, and please tell me more detailed how to with the dsdt and ipw2200, please!!!  ](*,)[/QUOTE]

[My .config](http://users.linuxbourg.ch/didier/blog/files/config-2.6.11.050607.gz) for a kernel 2.6.11 (Ubuntu src) with support of 1GB of RAM,  I didn't remove ALL useless modules, so I suppose that we can light it up.

---

### Post by Djax on 2005-06-17
[QUOTE=toxicfume]So should I go ahead and get the 1691 or 1694 dsdt?[/QUOTE]

You can get your buggy DSDT, disassemble it and compare it with the original 1691 DSDT.asm or 1694 DSDT.asm  to see which is the closest (or the same) and try to fix it by doing the same corrections. The correction of the Acer TM 8100 helps me fixing my Aspire 1694. 

IMHO Acer techies don't create a DSDT from scratch for each model, they adapt an old one. 

Here you can see [how I debbug mine](http://users.linuxbourg.ch/didier/blog/?p=30&lp_lang_view=en)

---

### Post by pistolas on 2005-06-17
After debuging it, how to insert it into the kernel??

---

### Post by toxicfume on 2005-06-17
[QUOTE=Djax]You can get your buggy DSDT, disassemble it and compare it with the original 1691 DSDT.asm or 1694 DSDT.asm  to see which is the closest (or the same) and try to fix it by doing the same corrections. The correction of the Acer TM 8100 helps me fixing my Aspire 1694. 

IMHO Acer techies don't create a DSDT from scratch for each model, they adapt an old one. 

Here you can see [how I debbug mine](http://users.linuxbourg.ch/didier/blog/?p=30&lp_lang_view=en)[/QUOTE]
 Wow, all that seems too hard for me to follow it seems, I'd need live help for that one, if anyone wants to help via msn or something, they are welcome :P

---

### Post by pistolas on 2005-06-17
when i do iwconfig with the rf_kill=0
apeeares unassociated instead of IEEE... iw that normal? and about the dsdt, how can i put it to work?

---

### Post by Djax on 2005-06-17
[QUOTE=pistolas]when i do iwconfig with the rf_kill=0
apeeares unassociated instead of IEEE... iw that normal? and about the dsdt, how can i put it to work?[/QUOTE]

Yes it is normal, you have to associated to the right network.

To see which network is available,do:
```
iwlist eth1 scan
```

Then you can associated manualy: It's depend a bit of your wifi-network (DHCP or not, WEP or not, WPA or not...)
In my case, I have no DHCP, no WPA but WEP network and I do:
```

/sbin/iwconfig eth1 essid <YourEssid>
/sbin/iwconfig eth1 channel <ChannelNumber>
/sbin/iwconfig eth1 mode Managed
/sbin/iwconfig eth1 key restricted <hexadecimalstring>
...

```

or it can be set via **/etc/network/interfaces**


For the DSDT, see this [http://ubuntuforums.org/showthread.php?t=37395&page=2](http://ubuntuforums.org/showthread.php?t=37395&page=2)

---

### Post by Djax on 2005-06-17
[QUOTE=toxicfume]Wow, all that seems too hard for me to follow it seems, I'd need live help for that one, if anyone wants to help via msn or something, they are welcome :P[/QUOTE]

if you attach the DSDT here, I can drop an eye.

---

### Post by jmr on 2005-06-20
I've just uploaded the original DSDT on my Acer Aspire 1692WLMi (LX.A6505.043) to [http://acpi.sourceforge.net/dsdt/view.php?id=392](http://acpi.sourceforge.net/dsdt/view.php?id=392) .  I had to use pmtools acpidmp to obtain this since the kernel wouldn't boot with acpi=on, and so there was no /proc/acpi/dsdt file to start with.  A different way to get the DSDT is to run "iasl -d" in Windows.  This is actually simpler because the iasl Windows binary is readily available from the intel site.  This method produced exactly the same file, so I feel confident there was no error in the process.

I've also uploaded a custom version, [http://acpi.sourceforge.net/dsdt/view.php?id=393](http://acpi.sourceforge.net/dsdt/view.php?id=393), with modifications inspired by the custom 1691 and 1694 DSDTs on that site.  I managed to boot my kernel --- standard ubuntu 2.6.10-5-686 --- with no recompilation (it seems to have CONFIG_ACPI_INITRD=y), by simply appending my DSDT.aml (and signatures) to the initrd-image.  Still, I had to avoid starting pcmcia (I simply removed the pcmcia-cs package), and boot with pci=noacpi.   I'll try other boot params later to see if I can isolate the remaining problems.

Please inspect the code and If you find something wrong with it, inform me.

NOTE: Acer seems to sell different machines under the same model number, depending on the region and even varying with time.  I bought my Aspire 1692WLMi in Portugal with 1024 MB DDR2 memory and an ATI X700, but reports I've come across in the Net have diferent specs for this model.  Likewise, there seems to be two different 1694WLMi models on sale here (LX.A4405.007 and LX.A6605.034, see [http://www.acer.pt/acereuro/page4.do?dau22.oid=7944&UserCtxParam=0&GroupCtxParam=0&dctx1=18&ctx1=PT&crc=3791544490](http://www.acer.pt/acereuro/page4.do?dau22.oid=7944&UserCtxParam=0&GroupCtxParam=0&dctx1=18&ctx1=PT&crc=3791544490) ).  The first few chars of the serial number possibly identify the exact model.  Mine is a LX.A6505.043.

I hope this helps.

João

---

### Post by toxicfume on 2005-06-20
[QUOTE=jmr]I've just uploaded the original DSDT on my Acer Aspire 1692WLMi (LX.A6505.043) to [http://acpi.sourceforge.net/dsdt/view.php?id=392](http://acpi.sourceforge.net/dsdt/view.php?id=392) .  I had to use pmtools acpidmp to obtain this since the kernel wouldn't boot with acpi=on, and so there was no /proc/acpi/dsdt file to start with.  A different way to get the DSDT is to run "iasl -d" in Windows.  This is actually simpler because the iasl Windows binary is readily available from the intel site.  This method produced exactly the same file, so I feel confident there was no error in the process.

I've also uploaded a custom version, [http://acpi.sourceforge.net/dsdt/view.php?id=393](http://acpi.sourceforge.net/dsdt/view.php?id=393), with modifications inspired by the custom 1691 and 1694 DSDTs on that site.  I managed to boot my kernel --- standard ubuntu 2.6.10-5-686 --- with no recompilation (it seems to have CONFIG_ACPI_INITRD=y), by simply appending my DSDT.aml (and signatures) to the initrd-image.  Still, I had to avoid starting pcmcia (I simply removed the pcmcia-cs package), and boot with pci=noacpi.   I'll try other boot params later to see if I can isolate the remaining problems.


Please inspect the code and If you find something wrong with it, inform me.

NOTE: Acer seems to sell different machines under the same model number, depending on the region and even varying with time.  I bought my Aspire 1692WLMi in Portugal with 1024 MB DDR2 memory and an ATI X700, but reports I've come across in the Net have diferent specs for this model.  Likewise, there seems to be two different 1694WLMi models on sale here (LX.A4405.007 and LX.A6605.034, see [http://www.acer.pt/acereuro/page4.do?dau22.oid=7944&UserCtxParam=0&GroupCtxParam=0&dctx1=18&ctx1=PT&crc=3791544490](http://www.acer.pt/acereuro/page4.do?dau22.oid=7944&UserCtxParam=0&GroupCtxParam=0&dctx1=18&ctx1=PT&crc=3791544490) ).  The first few chars of the serial number possibly identify the exact model.  Mine is a LX.A6505.043.

I hope this helps.

João[/QUOTE]
 Hmm..My Acer Aspire came with x700 and 256mb DDR ram(not sure if it's DDR2 or not)..but i upgraded the ram to 512mb. Anyways, I don't know why you have to boot with those parameters, for me..I just boot into ubuntu with 2 parameters: irqpoll=off and pnpbios=off...is this different from any body elses? And would that DSDT you made work on my machine too?

Edit: I just checked my laptops serial, it's LXA5305064(and more numbers)
And if you need me to do anything to to identify my version of hardware, please let me know what to do and I can help.

---

### Post by jmr on 2005-06-20
[QUOTE=toxicfume]Hmm..My Acer Aspire came with x700 and 256mb DDR ram(not sure if it's DDR2 or not)..but i upgraded the ram to 512mb. Anyways, I don't know why you have to boot with those parameters, for me..I just boot into ubuntu with 2 parameters: irqpoll=off and pnpbios=off...is this different from any body elses? And would that DSDT you made work on my machine too?

Edit: I just checked my laptops serial, it's LXA5305064(and more numbers)
And if you need me to do anything to to identify my version of hardware, please let me know what to do and I can help.[/QUOTE]


Well, I don't see why "my" DSDT would work any better or any worse on your machine than any other, since I'm not sure it's the same machine, nor am I confident that it solves the problems with the original (EDIT: it merely compiles cleanly, although I tried not to do anything radical).  My intention was mainly to post the original DSDT for others to see.  My custom modifications were based on examples and a bit of trial-and-error.  I browsed the ACPI spec superficially, to understand the basic ASL syntax but I do not understand the full implications of my actions.  I would certainly  like that someone else try this and criticise.  I strongly suggest that you compare the Original and Custom DSDTs first, though.  EDIT: You should also compare your original DSDT with my original DSDT.  If these are closer than to other DSDTs, there is good chance that the custom modifications will work too, I guess.

I'm going try other boot params later.  I'll report here, if I can conclude anything.

Something you could do is to check the System BIOS version in your computer (mine is S3A18).  Someone in this forum might be able to start making some sense out of this.

( EDIT: the BIOS version is S3A18.  The smiley above was automatically generated, and I didn't notice it before.  Sorry! )

João

---

### Post by toxicfume on 2005-06-20
[QUOTE=jmr]Well, I don't see why "my" DSDT would work any better or any worse on your machine than any other, since I'm not sure it's the same machine, nor am I confident that it solves the problems with the original (EDIT: it merely compiles cleanly, although I tried not to do anything radical).  My intention was mainly to post the original DSDT for others to see.  My custom modifications were based on examples and a bit of trial-and-error.  I browsed the ACPI spec superficially, to understand the basic ASL syntax but I do not understand the full implications of my actions.  I would certainly  like that someone else try this and criticise.  I strongly suggest that you compare the Original and Custom DSDTs first, though.  EDIT: You should also compare your original DSDT with my original DSDT.  If these are closer than to other DSDTs, there is good chance that the custom modifications will work too, I guess.

I'm going try other boot params later.  I'll report here, if I can conclude anything.

Something you could do is to check the System BIOS version in your computer (mine is S3A18).  Someone in this forum might be able to start making some sense out of this.

João[/QUOTE]
 Yup, that pretty much went right over my head. 

Anyways, I'll check the BIOS version of my laptop and post here in a little while.

---

### Post by Djax on 2005-06-21
[QUOTE=jmr]
NOTE: Acer seems to sell different machines under the same model number, depending on the region and even varying with time.  I bought my Aspire 1692WLMi in Portugal with 1024 MB DDR2 memory and an ATI X700, but reports I've come across in the Net have diferent specs for this model.  Likewise, there seems to be two different 1694WLMi models on sale here (LX.A4405.007 and LX.A6605.034, see [http://www.acer.pt/acereuro/page4.do?dau22.oid=7944&UserCtxParam=0&GroupCtxParam=0&dctx1=18&ctx1=PT&crc=3791544490](http://www.acer.pt/acereuro/page4.do?dau22.oid=7944&UserCtxParam=0&GroupCtxParam=0&dctx1=18&ctx1=PT&crc=3791544490) ).  The first few chars of the serial number possibly identify the exact model.  Mine is a LX.A6505.043.

I hope this helps.

João[/QUOTE]

The Aspire 1694 WLMi concern also many kind of machine, but the content doesn't vary a lot. When I command my laptop, the graphic chipset was a X600, and when I received it, it was a X700. The X700 is more powerful, but not yet  3D supported by Ubuntu, as far as I know. The other  difference are the amount of RAM (1GB in my case), the size of the disk (100GB in my case), the speed of CPU (Centrino 760: 2GHz in my case).  
This differences are not important for Linux point of view (some flags change in linux kernel for the RAM). The biggest differences for the Aspire 1690 model are IMHO the Bios version, I get the 3C25 version.

---

### Post by jmr on 2005-06-21
Just to let you know: my Aspire 1692 with the custom BIOS also boots with the single option "noapic", but still with pcmcia-cs disabled.  ACPI reports temperature, battery and ac-power status.  CPU-throtling and the laptop-mode service are activated automatically.

Some errors were reported by dmesg in a specific ACPI method.  I made a second version of my custom DSDT, which eliminates these errors but there are still a few failures reported.  I'll try to understand these later, and I'll then post my new DSDT.  
Anyway, please be advised that the custom 1692 DSDT in acpi.sourceforge.net is experimental and certainly incorrect, although it makes ACPI work on my computer.  I hope the next version wil be more trustworthy.

Maybe Djax and others would care to inspect my DSDTs.  I'd very much apreciate any comments or suggestions.

(A side note, since Djax mentioned graphics driver support: the Mobility X700 chip should be supported by the latest ATI proprietary driver, while the Mobility X600 still is not.  (See [ATI Proprietary Linux Release Notes](http://www2.ati.com/drivers/linux/linux_8.14.13.html).)  The fglrx package in Ubuntu seems to be a bit dated, though, and still has no support for the X700.  One of these days I'm going to try the new version.)

João

---

### Post by Djax on 2005-06-23
> (A side note, since Djax mentioned graphics driver support: the Mobility X700 chip should be supported by the latest ATI proprietary driver, while the Mobility X600 still is not. (See ATI Proprietary Linux Release Notes.) The fglrx package in Ubuntu seems to be a bit dated, though, and still has no support for the X700. One of these days I'm going to try the new version.) 

The X600 mobility seems to be supported and sould be working with actual Ubuntu.

In some logs, like ```
[here](http://www.gentooforum.de/thread.php?threadid=4721&threadview=0&hilight=&hilightuser=0&page=2) 
I can see that the X600 Mobility chip is known: 
**line 384**
[COLOR=Blue]MOBILITY RADEON X600 (M24 3150[/COLOR]), MOBILITY RADEON - (M24 3151),
**line 336:**
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version =[COLOR=DarkGreen] 8.8.25[/COLOR]
**line 1:**
X Window System Version[COLOR=Red] 6.8.0[/COLOR]
```

Hoary xorg-driver-fglrx is [COLOR=Red]6.8.0[/COLOR]-[COLOR=DarkGreen]8.8.25[/COLOR], so it has to work.

X700 is supported by ATI 8.12.10, so I have to wait. Even Ubuntu Breezy doesn't have it yet, as far as I know.

See this [HowTo](http://www.ubuntuforums.org/showthread.php?t=3567) to install it

---

### Post by vbcn on 2005-06-29
Hi there!
Nice thread, very interesting for acer owners :-)

There is something missing that I need to know: what if my laptop (aspire 1692WLMi /Mobility Radeon x700 / 1GB RAM) doesn't let me start ubuntu with ACPI?

This happens to me so, I'm unable to do all that stuff with the /proc/acpi/dsdt file, because ubuntu doesn't load the ACPI ("acpi" is missing in /proc/).

PD: I managed to run at full resolution with the option described by Djax, thank you! ;). Correctly working with vesa at the moment (I hope to improve the results soon with the right mobile radeon x700 driver).

Greetings from Barcelona

---

### Post by toxicfume on 2005-06-29
[QUOTE=Djax]The X600 mobility seems to be supported and sould be working with actual Ubuntu.

In some logs, like ```
[here](http://www.gentooforum.de/thread.php?threadid=4721&threadview=0&hilight=&hilightuser=0&page=2) 
I can see that the X600 Mobility chip is known: 
**line 384**
[COLOR=Blue]MOBILITY RADEON X600 (M24 3150[/COLOR]), MOBILITY RADEON - (M24 3151),
**line 336:**
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version =[COLOR=DarkGreen] 8.8.25[/COLOR]
**line 1:**
X Window System Version[COLOR=Red] 6.8.0[/COLOR]
```

Hoary xorg-driver-fglrx is [COLOR=Red]6.8.0[/COLOR]-[COLOR=DarkGreen]8.8.25[/COLOR], so it has to work.

X700 is supported by ATI 8.12.10, so I have to wait. Even Ubuntu Breezy doesn't have it yet, as far as I know.

See this [HowTo](http://www.ubuntuforums.org/showthread.php?t=3567) to install it[/QUOTE]
 I almost forgot to report back my Acer 1692's BIOS..but how do I find out what is my laptop's BIOS version?

---

### Post by Djax on 2005-06-30
[QUOTE=toxicfume]I almost forgot to report back my Acer 1692's BIOS..but how do I find out what is my laptop's BIOS version?[/QUOTE]


You can achieve that with the command "**dmidecode**". Probably the information is also available in the bios setup at boot time.

---

### Post by toxicfume on 2005-06-30
[QUOTE=Djax]You can achieve that with the command "**dmidecode**". Probably the information is also available in the bios setup at boot time.[/QUOTE]
 Thanks :) The BIOS version is: S3C25, which I guess is the same as yours Djax? (Hope this makes things easier for me :P)

---

### Post by Djax on 2005-06-30
[QUOTE=jmr]Just to let you know: my Aspire 1692 with the custom BIOS also boots with the single option "noapic", but still with pcmcia-cs disabled.  ACPI reports temperature, battery and ac-power status.  CPU-throtling and the laptop-mode service are activated automatically.

Some errors were reported by dmesg in a specific ACPI method.  I made a second version of my custom DSDT, which eliminates these errors but there are still a few failures reported.  I'll try to understand these later, and I'll then post my new DSDT.  
Anyway, please be advised that the custom 1692 DSDT in acpi.sourceforge.net is experimental and certainly incorrect, although it makes ACPI work on my computer.  I hope the next version wil be more trustworthy.

Maybe Djax and others would care to inspect my DSDTs.  I'd very much apreciate any comments or suggestions.

João[/QUOTE]

I check your DSDT, I can't do better. It even works with the **iasl**  (version 20050513).

---

### Post by Djax on 2005-06-30
[QUOTE=toxicfume]Thanks :) The BIOS version is: S3C25, which I guess is the same as yours Djax? (Hope this makes things easier for me :P)[/QUOTE]

Yes, do even though a "diff" between my original 1694WLMi DSDT and ours, to see if there is any differences.

---

### Post by toxicfume on 2005-06-30
[QUOTE=Djax]Yes, do even though a "diff" between my original 1694WLMi DSDT and ours, to see if there is any differences.[/QUOTE]
 You mean you want me to compare my DSDT with yours? Not sure I understood.

---

### Post by Djax on 2005-07-01
[QUOTE=toxicfume]You mean you want me to compare my DSDT with yours? Not sure I understood.[/QUOTE]

Yes, we have the same bios version. Our DSDT shouldn't differ that much even at all , but you have to check..

---

### Post by jmr on 2005-07-06
[QUOTE=vbcn]Hi there!
Nice thread, very interesting for acer owners :-)

There is something missing that I need to know: what if my laptop (aspire 1692WLMi /Mobility Radeon x700 / 1GB RAM) doesn't let me start ubuntu with ACPI?

This happens to me so, I'm unable to do all that stuff with the /proc/acpi/dsdt file, because ubuntu doesn't load the ACPI ("acpi" is missing in /proc/).

PD: I managed to run at full resolution with the option described by Djax, thank you! ;). Correctly working with vesa at the moment (I hope to improve the results soon with the right mobile radeon x700 driver).

Greetings from Barcelona[/QUOTE]

Hi,

Sorry I couldn't reply sooner, I was on vacation.  (Ironically I was in Barcelona last saturday...  What a small world).

Anyway, it seems we have the same model 1692 WLMi.  I could not see /proc/acpi/dsdt either since ACPI was disabled, but I used a pmtools program to extract the DSDT directly, as I explained in a previous message (#29).  You can also boot in Windows (if that isn't against your principles), download the iasl compiler from Intel (windows version) and run it in a DOS window: "iasl -d".  It will read the DSDT and write it to a file.

If you do this, please compare it with the original DSDT I uploaded to acpi.sourceforge.net.

If you need any more help, please ask.

João Rodrigues

---

### Post by jmr on 2005-07-06
I uploaded a second custom version of the DSDT for the ACER Aspire 1692WLMi (LX.A6505.043), BIOS revision S3A18, to [http://acpi.sourceforge.net/dsdt/view.php?id=402](http://acpi.sourceforge.net/dsdt/view.php?id=402).

This version eliminates some errors reported by dmesg on a particular ACPI method with the previous custom DSDT.  With the new version some failures are still reported by that method, but maybe that is normal.  Anyway I would recommend this version instead of the previous.

I kept the previous version in [http://acpi.sourceforge.net/dsdt/view.php?id=393](http://acpi.sourceforge.net/dsdt/view.php?id=393), under a different BIOS revision (S3A18-1), if you care to compare.  I hope the modified BIOS revision numbering does not confuse people.  I just wanted to keep the previous version available, but the acpi.sourceforge.net interface does not allow a custom1, custom2, ... naming scheme, for instance.

João

---

### Post by jmr on 2005-07-07
About the different models of the ACER Aspire 1690 series: see the [ACER-europe Drivers page for this series](http://support.acer-euro.com/drivers/notebook/as_1690.html).

Basically there are two versions, distinguished by the type of memory they use, DDR or DDR2, with different drivers and BIOSes.  The first digits of the serial number identify the model type:
LXA43, LXA44, LXA53, LXA54 is an Aspire 1690 DDR series
LXA65, LXA 66, LXA72, LXA84 is an Aspire 1690 DDR2 series

(This is from the ACER Europe page.  Other regions may have different information, I haven't checked.)

João

---

### Post by kpisacic on 2005-07-09
just a note to all 1692 users that have problem with synaptics touchpad not beeing recognized by kernel with ACPI=on, but working when ACPI=off

i have tried tons of suggestions, recompiled kernel with fixed DSDT, but really all it took was to put:

    echo -n "psmouse" > /sys/devices/platform/i8042/serio0/drvctl

into rc.local

when issueing this command, kernel recognizes touchpad.



br,

k.

---

### Post by buse on 2005-08-05
Hello Djax,

I have a Acer Aspire 1694WLMI too (the 512 Mb version), and i can't make my wifi working (excuse my english, I'm french ...)

I read, and read again this post and others, but i always have a problem. Sometimes, when i turn the switch on and modprobe ipw2200. It tells me that it disable IRQ10, i don't know why ...

So, can you tell me exactly the version of ipw2200, and acerhk did you use, and tell me how you do to make it work well please ?

buse.

---

### Post by kpisacic on 2005-08-07
[QUOTE=buse]

modprobe ipw2200. It tells me that it disable IRQ10, i don't know why ...

buse.[/QUOTE]

for ipw2200 to work you should have turned ON acpi. if you have acpi=off or noacpi it will not work.



br,

k.

---

### Post by buse on 2005-08-07
Thank you kpisacic,

I'm going to try this soon. Thank you for answering =)

Buse.

---

### Post by buse on 2005-08-07
Yeahhhh ! It's working =)

I'm writting this post from Ubuntu under wifi =) I'm so happy :grin: 
Thank you very much kpisacicn, Djax and the others.
I didn't understand that the acpi had to be turned on, and now, it is working well. Thank you =)

Buse.

---

### Post by Djax on 2005-08-31
Hi there,

Some guys on this [forum](http://forum.kanotix.net/viewtopic.php?t=5377&start=15&postdays=0&postorder=asc&highlight=) 
make the PCMCIA running again. We have comment  the line:

```
include port 0×800-0×8ff
```

with a ‘#’ in the file **/etc/pcmcia/config.opts**

> [COLOR=Red][SIZE=7]**WARNING**[/SIZE][/COLOR]
If you have purge pcmcia-cs (**dkpg --purge pcmcia-cs**), an **apt-get install pcmcia-cs** will freeze your laptop.

So you can do:
[QUOTE]    sudo apt-get install pcmcia-cs –download-only
> 
    sudo dpkg –unpack $(locate pcmcia-cs | grep \.deb)

>     sudo vi $( locate postinst | grep pcmcia-cs ) 

comment the line “/etc/init.d/pcmcia start”

>     sudo dpkg –configure pcmcia-cs

>     sudo vi /etc/pcmcia/config.opts

comment the line “include port 0×800-0×8ff”

>     sudo vi $( locate postinst | grep pcmcia-cs ) 

uncomment the line “#/etc/init.d/pcmcia start”
> 
    sudo /etc/init.d/pcmcia start

“sudo dpck-reconfigure pcmcia” said it clearly in a semi-graphic interactive menu that we can choose to start the deamon or not after the configuration.

[IMG]http://users.linuxbourg.ch/didier/blog/files/pcmcia-cs1.png[/IMG] 
then
[IMG]http://users.linuxbourg.ch/didier/blog/files/pcmcia-cs2.png[/IMG] 

But I can’t start apt-reconfigure before that pcmcia-cs is installed.
It must be a way to have this semi-graphic menu before or during the installation, but I don’t know how.[/QUOTE]

---

### Post by Djax on 2005-09-02
> It must be a way to have this semi-graphic menu before or during the installation, but I don’t know how.

I found it, so you have to do:
```
[FONT=Courier New][COLOR=Navy]DEBIAN_FRONTEND=dialog DEBIAN_PRIORITY=low  sudo apt-get  install pcmcia-cs[/COLOR][/FONT]
```
You have to choose **No** for this screen:
[IMG]http://users.linuxbourg.ch/didier/blog/files/pcmcia-cs1.png[/IMG] 
then
[IMG]http://users.linuxbourg.ch/didier/blog/files/pcmcia-cs2.png[/IMG]
```
[FONT=Courier New][COLOR=Navy]sudo vi /etc/pcmcia/config.opts[/COLOR][/FONT]
```
comment the line “include port 0×800-0×8ff” 
```
[FONT=Courier New][COLOR=Navy]sudo /etc/init.d/pcmcia start[/COLOR][/FONT]
```

---

### Post by voltaire on 2005-09-21
Hi ppl,

i'm just a newbi in this kind of stuff.. so sory anything... (my english also :p )

here's the problem.. (i just don't know more what to do)

i have a 1692 with a S3A22 Bios.

I get the DSDT for my bios, the "costum" version, compilet and follow the "tuturial" from [https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery) 

The problem is: when i boot my computer, it freeze's on "uncompressing Linux... Ok, booting the kernel" 

but if I put the "pci=noacpi" it passes the "uncompressing Linux" fase, but a little after, aparently when X starts, it just freezes, and i get nothing but a black screen :(


please help.. :(

Thx
Voltaire

---

### Post by voltaire on 2005-09-21
Aparently i solved the boot problem, i disable pcmcia, and now the system don't freeze anymore on the black screen..

```
sudo chmod -x /etc/init.d/pcmcia
``` 

now the system boot's, but  i don't have network :( and i still don't have battery status. 

if i do ```
acpi -V
``` 

 i get

```

No support for device type: battery
     Thermal 1: ok, 50.0 degrees C
No support for device type: ac_adapter

```

 
and my network no longer work...

at the moment, my menu is:

```

title		Ubuntu, kernel 2.6.10-5-386 ACPI OFF
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=off quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 WITH ACPI
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386.acpi root=/dev/hda2 ro pci=noacpi quiet splash
initrd		/boot/initrd.img-2.6.10-5-386.acpi
savedefault
boot


```

please help..


Voltaire

---

### Post by aran384 on 2005-09-22
this is kinda werid my dad has the athlon 64 of that laptop i think its 1592 .... 

and when i booted with the amd64 livecd it worked like a charm!!!....

everything was working ..... pcmia slots, network , wireless 

straight away with out me install any packages.... it was great...but because my dad is big on windows and dont wanna try something different and compatibilty crap and the if its not broke dont change it stuff and all sorts i had to reboot back in windows.... :(

kinda shame cause it was working ever well...

---

### Post by chatuser on 2005-11-23
- edit /boot/grub/menu.lst
- change acpi=off to noapic
- reboot your computer

Your network cards work now, damn ACPI !!

---

### Post by technofreak on 2005-12-05
I've got an acer aspire 1692 with 1024 mb ram, pentium m 750 and x700.
I have tried ubuntu on a desktop pc and I would really like to have it on my laptop. Is there any kind of tutorial available on how to install it? I could really use a step by step guide.

---

### Post by zi99y on 2005-12-12
[QUOTE=technofreak]I've got an acer aspire 1692 with 1024 mb ram, pentium m 750 and x700.
I have tried ubuntu on a desktop pc and I would really like to have it on my laptop. Is there any kind of tutorial available on how to install it? I could really use a step by step guide.[/QUOTE]
there's no step by step guide but you'll be able to do it by collecting peices of information from here as you need them (& learning at the same time). I did it, and I'm a complete linux noob. In fact it's half of the fun! Don't be afraid :)

---

### Post by technofreak on 2006-01-30
see that's why linux is still only used by a small group of people. there's people crazy enough to program the whole OS for free but there's no simple step by step way to install it onto a laptop. I just don't have the time to search in the forums for every problem I encounter. I loved ubuntu on the desktop but on my laptop I can't even get my screen to work with the special boot parameters. I don't have the spare time to fool around in the config files with the command line so I'll just wait and see if the next version of ubuntu will support my laptop or maybe there'll be a noob guide in a while.

---

### Post by Zim_ on 2006-03-26
Well, technofreak, that's true. But that is because Linux can't just be installed like Windows (on laptops). Most of the laptops have been 'optimized' for Windows (XP), therefor they might not use standarts.


Anyway, I had the same problem. I've got an Acer 1692 WLMi too. Mine got 512mb ddr. The 1692-models are not always the same. There are some with 1gb, some with just 256mb and, like mine, some with 512mb of RAM.


I have made a little Step-By-Step Tutorial how to install Ubuntu 5.10 on an Acer 1692 WLMi. I'm sure this will work for other Acer laptops too, but I can't guarantee.

**usage:**
[I][COLOR=DarkRed]what_is_on_the_screen:[/COLOR] [COLOR=RoyalBlue]the_commands_you_have_to_enter[/COLOR]
[COLOR=Green]I_am_something_in_the_nano-text-editor[/COLOR][/I]

start the computer with the CD inserted
You will see:
*[COLOR=DarkRed]boot[/COLOR]:[COLOR=RoyalBlue] linux acpi=off[/COLOR]*
install ubuntu
after the installation is complete and you boot ubuntu for the first time, you will see a black screen.
reboot, hit ESC and select the second entry ( „Ubuntu, kernel 2.6.12-9-386 (recovery mode)“).
wait[INDENT]*This is what I did in chronological order, I do not know if that helped ubuntu to work. This is why I post it in here too. Please correct me if that step is just nonsense :)*
You will see
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]sudo apt-get update[/COLOR]
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]sudo apt-get remove xorg-driver-fglrx[/COLOR]
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]sudo apt-get remove linux-restricted-modules-$(uname -r)[/COLOR]
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]nano /etc/X11/xorg.conf[/COLOR]
 go to Section „Device“
 edit „Driver“ to „[COLOR=Green]ati[/COLOR]“ (if not set yet)
 reboot
 again, hit ESC and select „recovery mode“
 insert the installation-CD
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]sudo apt-get install linux-restricted-modules-$(uname -r)[/COLOR]
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]sudo apt-get install xorg-driver-fglrx[/COLOR]
  [COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]nano /etc/X11/xorg.conf[/COLOR]
 go to Section „Device“
 edit „Driver“ to „[COLOR=Green]fglrx[/COLOR]“
 reboot
if it already works, gr8 (it didn't for me, so I restarted again)
hit ESC and select „recovery mode“
[/INDENT][COLOR=DarkRed]root@computername:~# [/COLOR][COLOR=RoyalBlue]nano /etc/X11/xorg.conf[/COLOR]
  go to Section „Device“
  edit „Driver“ to „[COLOR=Green]ati[/COLOR]“
  add another line under „Driver“[INDENT][COLOR=Green]Option        "MonitorLayout" "LVDS, TMDS"[/COLOR]
   [/INDENT]save and restart



Please note:
This is the first time I succesfully installed ubuntu. I am a windows whore and trying to switch to linux. That way up there worked for me, but I don't realy know what I did. I made all those things by asking in IRC Chats and searching the internet. I hope this might have helped someone.

Zim

---

### Post by ktogias on 2006-04-12
I am testing Ubuntu Dapper on my Acer Aspire 1692WLMi laptop.

I have not managed to make the LCD display work properly with the ATI driver.

I have created this bug report in launchpad 

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/39232](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/39232) 

about LCD display going black after booting the installed system.
Also after adding monitorLayout option at xorg.conf the LCD display shows a scrabbled image.

I have reproduced the bug with Flight 6 CD and Daily Build 11-Apr-2006 Installation CD. The bug also happens when booting from Daily Build 11-Apr-2006 Live CD, making live cd unusable in graphical mode.

If any of you have this laptop, you are able to download the installation disks and have some time, it would be really helpfull to try to reproduce the bug and confirm it in launchpad, in order to take priority and be fixed.

You can download the daily build installation cd from here:
[http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/)
and daily build live cd from here:
[http://cdimage.ubuntulinux.org/daily-live/current/](http://cdimage.ubuntulinux.org/daily-live/current/)

---

### Post by ktogias on 2006-04-12
I have also created a page in wiki about installing and running Ubuntu Breezy on Acer Aspire 1692WLMi. It is located here:
[https://wiki.ubuntu.com/Ubuntu5.10OnAcerAspire1692WLMi](https://wiki.ubuntu.com/Ubuntu5.10OnAcerAspire1692WLMi)

---

### Post by jamper on 2006-04-22
hi ktogias
to solve the screen problem, first u must enter console mode and edit xorg.conf. replace ati or fglrx with vesa, then startx. then follow this link [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) . i followed method 2 and it worked

---

### Post by ktogias on 2006-04-24
[QUOTE=jamper]hi ktogias
to solve the screen problem, first u must enter console mode and edit xorg.conf. replace ati or fglrx with vesa, then startx. then follow this link [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) . i followed method 2 and it worked[/QUOTE]

Thanks for your suggestions jamper. 

I have already managed to make the display to work with fglrx and vesa drivers.

The problem here is that the default 'ati' driver that is used just after the installation and when booting the live cd does not work.

If you have the machine and can confirm the fact that the display does not work out of the box it would be very usefull to add a confirmation comment for bug #39232 in launchpad ([https://launchpad.net/distros/ubuntu...ati/+bug/39232](https://launchpad.net/distros/ubuntu...ati/+bug/39232)) in order to help developers to fix it.

---

### Post by [MEGA] on 2006-05-18
Same problem!

I used Breezy with Option "MonitorLayout" "LVDS, TMDS" at Devide section (in xorg.conf). Driver "ati"

I updated to Dapper Fligth 5 using ati driver, but I saw a 2 x 3 screen when X started. To solve the problem I installed xserver-xorg-fglrx. I worked well but when I updated to fligth 6 It crashed again , a ******* black screen....

After 2 /etc/init.d/gdm restart system needs to be rebooted because is blocked.

Is there any solution for this bug? ATI and Propietary ati driver are the problem ?

I happends me with anothers distributions (Suse, etc)

---

### Post by subcom on 2006-06-02
With the ati driver installed I fixed monitor problem with this line in the device section of the xorg.conf file:

Option          "MonitorLayout" "LVDS, AUTO"

with the TMDS option in place of the AUTO option I can't get it working

Now everything works fine

---

