---
title: "external monitor on Acer Extensa 5220"
date: 2008-09-07
forum: Hardware
---

### Post by chicoperico on 2008-09-07
hello all,

after at least 10 hours during this weekend trying to get my Acer Extensa 5220 
to output to an external monitor i am getting quite desperate, and i really 
did not plan to pass my weekend this way!!!! 4 weeks from now i have to make 
an international presentation, and i really do need my laptop to be able to 
output to a beamer! (and i do not want to be forced to export to powerpoint and use somebody else's machine - i have a lot of movie bits in the presentation and the openoffice export would not work well enough, and i should really hate to use microsoft!)

i have been researching the net, of course, and studying the man pages for 
setkeycodes, showkey, lineakd etc. especially informative is a page on 
nerdstock by some Rob ( <http://nerdstock.org/acer_vista_mandriva_keys> *- 
this page is not always accessible, but as it offered a pdf-version-download, 
i do have that text on my machine). Rob's page is written for an Aspire 
machine, but most of the scancodes, linux keycodes and X11 keycodes are 
identical. a few of the key functions Rob had to define for the Aspire 
machine actually work out of the box on the Extensa - like the button for the 
wlan module.

i attach below the relevant part of my /etc/lineakb.def and my lineakd.conf.

BUT - there is no way to get the machine to talk to an external monitor. 
according to /usr/include/linux/input.h the kernel on this machine (ubuntu 
8.04) uses linux keycode 227 for KEY_SWITCHVIDEOMODE, while Rob used a linux 
keycode that was undefined for his kernel - *238. this one, though on the 
ubuntu 8.04 kernel is reserved for KEY_WLAN. so i assigned another undefined 
one to the Fn+F5 key-combination, namely 199. i also tried 227. this was all 
duely documented in /etc/lineakb.def, then creating a new lineakd.conf by 
lineakd -c, then defining the key associations by hand (klineakconfig was of 
no use at all). i was able to define the user programmable keys, got a nice 
display when using the sound up and down functions etc. *- *but not what i 
really cared for, the external monitor function!

what in all the world can i do???

and why has this to be this complicated? i have been using linux for 10 years 
now - *what is a newbie to think? this must put off a lot of people!

best regards, and thanks for any input!
Rainer

attachments:
/etc/lineakb.def


[ACER-5220]
  brandname = "Acer"
  modelname = "Extensa 5220"
  RAWCOMMAND[SETKEYCODES] = "e027 227 e029 199 e073 148 e074 149 e075 227 e033 219 e034 239"
  [KEYS]
    Help		= 245 # Fn + F1	Help		KEY_HELP (138/e025)
    Setup		= 158 # Fn + F2	Acer eSetting	KEY_MENU (139/e026)
    AudioMute 	= 160 # Fn + F8	Mute
    Video		= 214 # 3d key on the left side	KEY_SWITCHVIDEOMODE (227/e075)
    Display         = 167   # scancode e029 - Linux keycode 199 (238 on the extensa is occupied!)
    AudioPlay|Pause 	= 162 # Fn + Home	Play
    AudioStop	 	= 164 # Fn + PgUp	Stop
    AudioPrev		= 144 # Fn + PgDn	Next Song
    AudioNext		= 153 # Fn + End	Previous Song
    AudioRaiseVolume	= 176 # Fn + ArrUp	Volume Up
    AudioLowerVolume	= 174 # Fn + ArrDn	Volume Down
    UserDefined1	= 159 # Top 'P'	Custom App.	KEY_PROG1 (148/e073)
    BrightnessLower	= 239 # Fn + ArrLe	Brightness Up	KEY_BRIGHTNESSDOWN (224)
    BrightnessHigher	= 123 # Fn + ArrRi	Brightness Down	KEY_BRIGHTNESSUP (225/e06e)
    UserDefined2	= 151 # Top 'e'	Acer eMgr/Cust.	KEY_PROG2 (149/e074)
    WWW			= 178 # Top Web	Web Browser	KEY_WWW (150)
    Mail		= 236 # Top Mail	Email Client	KEY_EMAIL (215)
    EuroSign        = 195   # scancode e033 - Linux keycode 219
    DollarSign      = 244   # scancode e034 - Linux keycode 239
  [END KEYS]
[END ACER-5220]


lineakd.conf

# LinEAK - Linux support for Easy Access and Internet Keyboards
#  Copyright (c) 2001,2002, 2003  Sheldon Lee Wen <leewsb@hotmail.com> (Current Maintainer)
#  	and Mark Smulders <Mark@PIRnet.nl>
#  [http://lineak.sourceforge.net](http://lineak.sourceforge.net)
#
# lineakd configuration file
#
# example key configuration:
# 	play	= "xmms --play-pause"
# 	eject	= EAK_EJECT
#
# Lineakd supports the following modifier keys:
#    control alt shift mod2 mod3 mod4 mod5

CdromDevice = /dev/cdrom
Display_align = center
Display_color = 0aff00
Display_font = -adobe-helvetica-bold-r-normal-*-*-240-*-*-p-*-*-*
Display_hoffset = 0
Display_plugin = xosd
Display_pos = bottom
Display_soffset = 1
Display_timeout = 3
Display_voffset = 50
KeyboardType = ACER-5220
MixerDevice = /dev/mixer
RAWCommands = 
Screensaver = 
conffilename = /home/chico/.lineak/lineakd.conf
keystate_capslock = 
keystate_numlock = 
keystate_scrolllock = 

Display = 
Help = 
Setup = 
Video = 
AudioLowerVolume = EAK_VOLDOWN
AudioMute = EAK_MUTE
AudioNext = EAK_MEDIADETECT(NEXT)
AudioPlay|Pause = EAK_MEDIADETECT(PLAYPAUSE)
AudioPrev = EAK_MEDIADETECT(PREVIOUS)
AudioRaiseVolume = EAK_VOLUP
AudioStop = EAK_MEDIADETECT(STOP)
BrightnessHigher = 
BrightnessLower = 
DollarSign = EAK_SENDKEYS(shift+4)
EuroSign = EAK_SENDKEYS(mod5+5)
Mail = /usr/bin/kmail
UserDefined1 = /usr/bin/konqueror
UserDefined2 = /usr/bin/firefox
WWW = /usr/bin/konqueror

---

### Post by chicoperico on 2008-09-08
the aforementioned Rob has already answered, i copy the relevant bits, so others can profit from this thread:

Rob:
To me it looks like you're looking in the wrong direction...
Have you ever looked at you X.org configuration (/etc/X11/xorg.conf)? If 
your external monitor isn't defined there, you can try what you want, 
but you'll never be able to use it.

Try this:
- back up your /etc/X11/xorg.conf
- plug in your external monitor or beamer
- switch to runlevel 3 (`telinit 3')
- run `Xorg -configure'

This last command will probe your hardware and create an initial 
xorg.conf. I think it does this in your cwd, so afterwards you may need 
to move it to /etc/X11/xorg.conf. After that, switch back to runlevel 5 
(`telinit 5').

Hope this helps,
* Rob

Rainer:
hello again, and thank you for answering so quickly!

your approach seems fine - *as long as the beamer is mine.

but would that work on any beamer? i mean, i am going to be at a conference, 
plugging in my machine, having 15 minutes for my talk. i am not supposed to 
configure my xserver there ......

on my old machine it was just Fn+F3, and the display was toggled to the beamer 
and back, worked just out of the box. it is too slow for the video parts, 
though.

best regards,
Rainer


Rob again:
Then I think it would be a good idea to start with comparing 
the /etc/X11/xorg.conf on the old box and on the new one.

I don't have any experience with beamers, but as far as I know they all 
compare to the same monitor (just VGA, I think). But you're probably 
better of asking someone else's advise on that...


Rainer again:
i tried Rob's approach with a second screen here at home, it works, but it would be a hassle at a conference, even if i do not have to reconfigure the xserver, i still would have to restart it ....

so i am waiting for tips!!!!

---

### Post by chicoperico on 2008-09-11
hello again,
so i keep running this thread alone .....

well, for the benefit of anybody having similar problems, i found a good and fast workaround:
Rob's suggestions set me on the right track, btw.

i noted that when i started the x-server with a second monitor attached to the laptop - not necessarily a beamer -  and hibernated the machine, the x-server still sent its output to a second monitor at the vga -connection after restarting the machine, and this could then be the beamer.

so i created a new user "presenter" with read-only rights, logged in as such with a second monitor connected and could then log in and out as my usual self at will, with or without a second monitor -  as long as i did not log out "presenter" and when stopping the machine did so with the hibernating option, i could always switch to "presenter" login and successfully connect to a second monitor.

good luck to all ....
Rainer

---

