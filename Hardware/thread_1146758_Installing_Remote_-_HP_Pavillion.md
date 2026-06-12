---
title: "Installing Remote - HP Pavillion"
date: 2009-05-02
forum: Hardware
---

### Post by CybaCowboy on 2009-05-02
I have a HP Pavilion dv4-1041TX Entertainment Notebook PC and I have most of the hardware working under Linux (some of which didn't need to be configured at all!), however one of the pieces of hardware that is not yet working is the included infrared remote-control...

The included infrared remote control is specifically for Windows Media Center, though works in most Microsoft Windows-based programs - it is identified by part number RC1762307/01, it connects to a built-in infrared port and that is all I know about it.

I installed a few LIRC packages (lirc and gnome-lirc-properties, both of which stated that they were for using and/or configuring infrared remote-controls under Linux), and I have enabled the infrared remote-control plugin in Totem Movie Player, but the remote does not appear to work at this stage... I also specified that the infrared remote-control was a "Philips" version as it was clearly indicated during setup that this is the "new version" (which considering my Microsoft Windows Vista: Home Premium notebook PC is new-ish, makes sense that the remote-control would be the "new version").

Anyone have any ideas on how to get it working?


I am using a HP Pavilion dv4-1041TX Entertainment Notebook PC (if all went to plan, there should be an official HP brochure attached) with the included infrared remote-control and the latest version of Ubuntu at the time of writing...

---

### Post by StaticIp on 2009-05-04
I have an HP DV4 and would also like to know how to get this up and working, so far only one button works.. The switch display button. The lirc config tool does nothing for me :/.. Any advice?

---

### Post by CybaCowboy on 2009-05-04
I just found a new "Remote Control Properties" menu, but it's been no help with setting-up my remote control...


When I try to manually choose an infrared receiver (I chose "Microsoft Windows Media Center Remote", because this is the closest match...), I am told:
*Warning: Cannot find such a receiver.*

If I try the "Auto-detect" option, I am told:
[i]No IR Receivers attached
Could not find any IR receiver. Is your device attached?

Note that some devices, such as homebrew serial port receivers must be selected manually since there is no way to detect them automatically.[/i]


Finally, I've also tried the "Use supplied remote control" and "Use a different remote control/HP TSGH-IR01" (this model number was already entered, and is the only option under "HP") options, but they do not appear to work...

There is an "Configuration Test/Press remote control buttons to test: <none>" option at the bottom, but pressing the buttons on my remote control does nothing (which I assume has everything to do with the infrared receiver issue above).

---

### Post by oktubrer on 2009-09-27
Bump!

¿Any luck with this issue?

---

### Post by thisguykev on 2009-10-10
same issue as above!.. can anyone help.. using Ubuntu Studio 9.04;  is there a problem with the driver for the IR receiver?  Does anyone know how to install this?

thanks

---

### Post by Sylslay on 2009-10-11
Your post was from may, 
in Juanty , Ir remote work out of the box, on laptop
HP dv9000 series

---

### Post by stefe on 2010-01-01
My dv6 - 1333 remote, part number rc1762308/01b is also not working, only the display button generates a call.

tried different configurations, but none worked.

Ubuntu 9.10

---

### Post by ebe0 on 2010-03-12
Same issue here. 
Laptop:dv6-1110ax
Remote control: RC1762308/01B
Ubuntu 9.10

---

### Post by corruptor1972 on 2010-05-15
Same here, only the display switch button works.

I have an [HP DV5-1000ea]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3753564") laptop.

R/C details attached.

---

### Post by dtach on 2010-05-26
would love it if someone found out how to get the remote working..

---

### Post by Misilo on 2010-06-19
Same issue here.
laptop: dv6t quad (i7)
remote control: RC1762308/01B
Ubuntu Lucid 64

Only the display button does something. This button is received as "0xf8" by the Ubuntu Keyboard Shortcuts, and as "KEY SWITCHVIDEOMODE" by the Infrared Remote Control Properties, When pressing the button it also produces a blink on my screen. The rest of the buttons on the RC does nothing.

Any ideas on how to make the other buttons to be received?

---

### Post by Misilo on 2010-06-20
Hi again!

I have just updated the BIOS from the HP page, and now it's working.

I have tested all buttons on the keyboard shortcuts, and this is what I've got:

The volume + and - control, mute, next song, prev song, stop, and sleep(power) buttons are working as I expect.
DVD button as Ctrl+V
Windows media smart (weird wave thing next to DVD) as ctrl+E
UP and DN (the ones on the left) are received as pageup and pagedown
the arrows as the keyboard arrows
OK as Intro
the i as ISO level3Shift
The little curved up arrow as backspace, I think.
fast forward(>>) as Shift+ctrl+F 
fast backward(<<) as shift+ctrl+B
display as 0xf8
Windows button as 0xc9

The only button witch is not giving any output is the Play/pause button. It does nothing.

My laptop is from the dv6-2000 series, (dv6t quad i7) I downloaded BIOS update from HP site, installed it from windows.
My previous version was F.1A, now is F.1B rev A

If you try this, tell me if it works.

good luck!

---

### Post by corruptor1972 on 2010-08-12
It's good that it works for you.  Sadly I am not so lucky, HP will probably need to update the BIOS for my machine too.

For waht it's worth, there's a Launchpad bug for this - [click here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461796") and add a comment to say so if it affects you.

---

### Post by Miguel Angel Da Vila on 2010-08-19
I found this solution in the Internet, but I don't have the original author page.

It works for RC model RC1762308701B.

Install lirc

In the /etc/lirc/hardware.conf file configure as in the sample:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="HP_RC172308-01B"
REMOTE="ENE KB3926 B/C/D (ENE0100) CIR port"
REMOTE_MODULES="lirc_dev lirc_ene0100"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lirc.conf"
REMOTE_LIRCD_ARGS="-d /dev/lirc0"

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

```

Then copy the following text in /etc/lircd/lircd.conf

```

#
# this config file was automatically generated
# using lirc-0.8.6(default) on Tue Jun 15 13:43:01 2010
#
# contributed by fogobogo 
#
# brand:                       	HP
# model no. of remote control:  RC1762308/01B
# devices being controlled by this remote: HP Pavillon Entertainment Laptop
#

begin remote

  name  HP_RC172308-01B
  bits            8
  flags RC6
  eps            30
  aeps          100

  header       2780   893
  one           467   412
  zero          467   412
  pre_data_bits   29
  pre_data       0x37FF07B
  gap          72382
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_POWER                0xF3
          KEY_DVD                  0xDB
          KEY_UNKNOWN              0x7F # thats the "check" or "squareroot" button on the top row of the remote
          KEY_SWITCHVIDEOMODE      0x7E
          KEY_MENU                 0xF2 # the "windows" button
          KEY_UP                   0xED
          KEY_DOWN                 0xEC
          KEY_STOP                 0xE6
# these dont work particularly well with most applications. you might want to alter them
          KEY_REWIND               0xEA
          KEY_PLAYPAUSE            0x91
          KEY_FASTFORWARD          0xEB

          KEY_PREVIOUS             0xE4 # the "up" button on the left of the remote
          KEY_NEXT                 0xE5 # the "dn" button on the left of the remote

          KEY_UP                   0xE1
          KEY_LEFT                 0xDF
          KEY_RIGHT                0xDE
          KEY_OK                   0xDD
          KEY_DOWN                 0xE0

          KEY_BACK                 0xDC
          KEY_INFO                 0xF0

          KEY_VOLUMEDOWN           0xEE
          KEY_VOLUMEUP             0xEF
          KEY_MUTE                 0xF1
      end codes

end remote

```

---

### Post by pepo.k on 2010-09-10
Hi,

**Strange 1st row on remote control!**
 I have an HP dv 6810 EG with remote control HSTNN-PRO7. I have found a configuration for HSTNN-PRO7 on the lirc website [http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7](http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7).
I have copied the configuration into the lircd.conf in \etc dir. But I still cannot configure any of the ¨remote control¨ buttons in the first row except the ¨display switch¨ and ¨power¨ buttons which are the only one working out of the box. The other rows on remote control were working out of the box.

**Laptop**
The 2nd button ¨DVD¨ on the laptop itself is the onlyone not working. The 1st one ¨quickplay¨ button is working.
Strange is if I start the lirc menu from gnome menu, there is not clear what should I choose as IR receiver.
Should I choose ¨generic¨ with UDP Port listener...? Or what. There is also an option: ¨linux input device¨ and as a model ¨HP Webcam / Power button / Sleep button¨. The other options are possibly wrong as it is writting ¨Warning: Cannot find such receiver¨.
Am I missing something?

I am using Linux mint 9. All kernel/software is up to date except the LIRC:
Lirc version is 0.8.6, the 0.8.7 is 4 days old.
The laptop has the newest BIOS from 2009...

Please help!

Pepo

---

### Post by benjamimgois on 2010-10-20
I have an HP dv4 and i follow all the procedures. When i press the keys on the terminal "irw" everyone of then are detected correctly but i can't control anything on my desktop. What am i missing ?

ps:i'm using maverick 64bit.

---

### Post by corruptor1972 on 2010-10-31
Fantastic news for HP Pavilion DV5-1000ea owners!!!!  I have a working remote control!!!

I simply _[COLOR="Blue"][followed these instructions given in the HP Forum]("http://h30434.www3.hp.com/t5/Hardware/ENE-CIR-under-Linux-HDX16/td-p/34808/page/2")[/COLOR]_ and the remote control now gives sensible output to the terminal.

The _[COLOR="Blue"][remote control configuration file]("http://lirc.sourceforge.net/remotes/hp/RC1762307-01")[/COLOR]_ is listed in the lirc project.

:guitar:

---

### Post by corruptor1972 on 2010-11-03
> **benjamimgois said:**
> I have an HP dv4 and i follow all the procedures. When i press the keys on the terminal "irw" everyone of then are detected correctly but i can't control anything on my desktop. What am i missing ?

ps:i'm using maverick 64bit.

It seems there are three configuration files for remotes:
1. Hardware configuration file for the IR receiver/transmitter (/etc/lirc/hardware.conf)
2. Remote Control keycodes definitions for lirc daemon (/etc/lirc/lircd.conf)
3. Remote control key mappings for the remote to applications (/etc/lirc/lircrc, with a user's ~/.lircrc overriding, if it exists).
 
So seeing as your remote works, the first two steps are good.  I think you now need to configure what the keys do, and have the 'irexec' program run to act on that config.  

I have irexec run on log-in by adding an entry for it in the Gnome Preferences/Startup Applications.  This works with a .lircrc file in my home directory.  Alternatively I could have set up the config file in /etc/lirc/lircrc.

[See the page on the configuration file at the lirc project.]("http://www.lirc.org/html/configure.html")  Googling lircrc may well yield more help.

Hope this helps.

---

### Post by benjamimgois on 2010-11-03
> **corruptor1972 said:**
> It seems there are three configuration files for remotes:
1. Hardware configuration file for the IR receiver/transmitter (/etc/lirc/hardware.conf)
2. Remote Control keycodes definitions for lirc daemon (/etc/lirc/lircd.conf)
3. Remote control key mappings for the remote to applications (/etc/lirc/lircrc, with a user's ~/.lircrc overriding, if it exists).
 
So seeing as your remote works, the first two steps are good.  I think you now need to configure what the keys do, and have the 'irexec' program run to act on that config.  

I have irexec run on log-in by adding an entry for it in the Gnome Preferences/Startup Applications.  This works with a .lircrc file in my home directory.  Alternatively I could have set up the config file in /etc/lirc/lircrc.

[See the page on the configuration file at the lirc project.]("http://www.lirc.org/html/configure.html")  Googling lircrc may well yield more help.

Hope this helps.

Thanks a lot ! Your information really help, could you post your .lircrc configue file ?

---

### Post by corruptor1972 on 2010-11-04
> **benjamimgois said:**
> Thanks a lot ! Your information really help, could you post your .lircrc configue file ?

Sure.  It is still a work in progress, athough the media buttons work (volume, mute, back, forward, play/pause and stop) and a lot of the buttons work with MythTV.

I have had to rename '.lircrc' to '.lircrc.txt' in order to attach it.  Good luck!  Let me know how you get on, and if you can improve on the config don't forget to share it here!

Perhaps we should have a thread for HP .lircrc files??!!

---

### Post by wkpalan on 2010-11-13
Thnks corruptor1972 I think I got it to work

---

### Post by pepo.k on 2010-11-28
Still no solution for me???

> **pepo.k said:**
> Hi,

**Strange 1st row on remote control!**
 I have an HP dv 6810 EG with remote control HSTNN-PRO7. I have found a configuration for HSTNN-PRO7 on the lirc website [http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7](http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7).
I have copied the configuration into the lircd.conf in \etc dir. But I still cannot configure any of the ¨remote control¨ buttons in the first row except the ¨display switch¨ and ¨power¨ buttons which are the only one working out of the box. The other rows on remote control were working out of the box.

**Laptop**
The 2nd button ¨DVD¨ on the laptop itself is the onlyone not working. The 1st one ¨quickplay¨ button is working.
Strange is if I start the lirc menu from gnome menu, there is not clear what should I choose as IR receiver.
Should I choose ¨generic¨ with UDP Port listener...? Or what. There is also an option: ¨linux input device¨ and as a model ¨HP Webcam / Power button / Sleep button¨. The other options are possibly wrong as it is writting ¨Warning: Cannot find such receiver¨.
Am I missing something?

I am using Linux mint 9. All kernel/software is up to date except the LIRC:
Lirc version is 0.8.6, the 0.8.7 is 4 days old.
The laptop has the newest BIOS from 2009...

Please help!

Pepo

---

### Post by benjamimgois on 2010-11-28
Guys, the latest kernel 2.6.36 makes the IR remote on my HP dv4 works out of box. Make a trie and load the module "ene_ir"

---

