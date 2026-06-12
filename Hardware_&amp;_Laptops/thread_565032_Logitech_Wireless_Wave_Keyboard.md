---
title: "Logitech Wireless Wave Keyboard"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by GhostZrydA on 2007-10-01
Anyone using a logitech "wave' wireless keyboard in ubuntu linux?.

Im thinking of getting one, but i can't seem to find out if the wireless side of things is going to work or not.

GhostZrydA

---

### Post by ohmyiv on 2007-10-17
I'm not sure if this helps, but I'm using the wave corded usb keyboard and a mx laser wireless usb mouse and both of them work fine for basic stuff in Gutsy...so far. :)   Now if I can figure out key mapping....

---

### Post by Fundi on 2007-10-19
Yeah I would love to buy one of these but its alot of money to spend and then find out it doesn't work.

---

### Post by dyrer on 2007-10-21
I have tested logitech wave keyboard and mouse wireless with 6.06 LTS and works perfect

---

### Post by Fundi on 2007-10-22
Awesome, I'm really tempted to get one now.

---

### Post by forteller on 2007-10-31
dyrer: What do you mean that it works perfectly? Just that all the basic stuff works like it should, or that all or most of the extra keys also works? I'm having a hard time finding any info on Wave and Linux, so I apreciate the info a lot!

---

### Post by prodigalson666 on 2007-11-01
You want a wireless keyboard and mouse that works with any linux? Find one that is R/F, these devices use the infrared frequency as most of you typical remote controls which means no drivers necassary, just plug and play! I'm using a logitech LX3000, no problems.

---

### Post by cwrann on 2007-11-03
I have a logitech ex110 wireless keyboard and mouse. It has always worked great out of the box with no tweaking. One suggestion: invest in some rechargeable batteries.

---

### Post by gtd123 on 2007-11-07
How did you get the logitech wireless wave to work?  I plugged in the USB receiver but the keyboard is not detected as far as I can tell.  Are there installation steps I have to perform?  Thanks.  G

---

### Post by Phloston on 2007-12-01
I only had to plug in the USB received and press the connect buttons to get my Wave keyboard and LX8 mouse to work. Basic functions work perfectly. I have not tried to get the extras to work, but a few of the extras work by default, such as volume and calculator.

---

### Post by mooglinux on 2007-12-26
on mine, calculator, power (its set to sleep by default) and the media keys to launch the mediaplayer, mute, volume up, down, next track, previous track, and stop, all work. but the fn key and all of its associated shortcuts do now, and neither does the appswitch button, the zoom button, the gadget button, and the photos button. otherwise, it feels great, and everything else works flawlesly, aside from a handful of keys. any solutions to this problem are definatly appreciated!

---

### Post by evan.rotert on 2008-01-03
I've had the same experience- the basic media functions work, but I want to use the buttons on the left side for some compiz functions and they aren't detected!  Any solution to this problem is much appreciated :-)

---

### Post by kiwilinux on 2008-01-06
[SIZE=3]I do not have one of these but plan to in the next week or so. You may be interested in trying 'Keytouch' from [http://keytouch.sourceforge.net/index.php](http://keytouch.sourceforge.net/index.php) . I have used this before and it is a very effective and simple program to use. I plan to use it to get all keys working and to submit a configuration file to the project so it will just work out of the box in future.:mrgreen:
[/SIZE]

---

### Post by sweetthdevil on 2008-01-22
Just bought a wired one (logitech wave) create by the way, Have you manage to get the all keys working?

---

### Post by warpflux on 2008-01-29
Same issues here with the WIRED Wave. Great overall keyboard, with some minor inconveniences preventing it from being Fantastic. Here's a run down on what I've experienced.

The keyboard's primary keys work fine, has a great feel, and a few special keys work (luckily the few most of us use, such as volume, media, mute, along with calculator, email, and web when configured with KeyTouch). KeyTouch can see a few of the special keys, the ones mentioned as already working, but little more. This DOES allow you to remap the working keys. 

The "SCROLL LOCK" Does NOT function. (it's technically Fn+Pause/Break but it does NOT actually work) KeyTouch can see it but doesn't identify the function or allow it to map to Scroll Lock. Even some users with setpoint claim they have to remap it to a different key. 

Unfortunately the rest of the special keys are dead. No signal at all, no key presses seen probing any of the USBs. Tried KeyTouch (which is pretty awesome software) but it can't connect something that doesn't have signal. Thus far have found no way possible to get any kind of output from the non-working keys.

Best guess is that the logitech software (setpoint) somehow enables these keys, or uses a unique way to  activate the remaining keys (an undetected inactive 3rd USB device signal?). 


Keys That DON'T Detect In KeyTouch: Word, Excel, Calendar, a, b, c, messenger, wwwsearch, pcsearch, eject, mediacenter, pictures, config, zoomin, zoomout, windowmanager

Detected Under 1st USB Device:all standard keys,  scroll-lock, commandmenu
Detected Under 2nd USB Device: All Media Keys, IE, Mail, Calculator, Power(default is sleep) 


Here's another thread following this same issue from a more technical perspective.

[http://www.mail-archive.com/linux-input@vger.kernel.org/msg00161.html](http://www.mail-archive.com/linux-input@vger.kernel.org/msg00161.html)


The zoom and "Vista" keys would be great for compiz, but no biggie.  My bigger wish is that Logitech realized Unix/Linux based systems are a standard in most scientific and professional work places and that a Linux user base exists and is growing. This is one situation where "Open Source" would save a commercial company tons of money, and increase their users.  Oh well, that's my vent for the evening. 

Hope this helps anyone thinking about getting this keyboard. Personally I like it, just wish the semi-useful dead keys could be activated. (who am I kidding, I'd probably never even touch the keys, but it does make me feel like I'm missing out on features I paid for).

---

### Post by mooglinux on 2008-01-30
Over at keytouch i found a great announcment: >  When your keyboard is connected via USB you may have noticed that some extra function keys don't work. Note that most keyboard files in keyTouch are for a PS/2 connection and if a keyboard file is for a USB connection the name of the keyboard file will contain "(USB)". But still even if you are using the right keyboard file, some keys may not work. This is because the current USB input driver in the Linux kernel does not allow us to get these keys working. Currently I am modifying this driver so that we can get all keys working. This modification will be applied to the Linux kernel.

So at the moment I recommend you to connect your keyboard via PS/2 and wait for a new version of the USB input driver. I will also write a new version of keyTouch that will work perfectly together with the new driver.  [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

so its only a matter of time! a future kernal update will contain the changes we need for all these to work. in the meantime, anyone know if putting a usb to ps/2 adapter on the keyboard does the trick? it seem sunlikely but it may be possible that would be one solution

---

### Post by SuperAndy on 2008-02-12
I'm trying to get the wave keyboard to work fully [well, as fully as can be expected at the moment] in ubuntu. I am having a few issues though with keytouch. I am running keytouch-editor, and it picks up the handlers and the media keys and all that business. and i can save that as a file. But when i come to open it in keytouch itself, I get no response whatsoever. Its really quite strange.

Can anyone upload their keyboard preset they have created to help me out, or tell me which inbuilt one you used to get it to work?

cheers

---

### Post by SuperAndy on 2008-02-13
Well, after reading around randomly, it seems the majority of the keyboard presets in there are for PS/2 keyboards. I chose "Cordless Desktop MX 5000 (USB)", another logitech, and I get media buttons, email, and internet. Just for anyone who was wondering.

---

### Post by Scunizi on 2008-03-20
In testing the wired Wave I came across an irritating problem of delayed or slow reaction to my hitting certain keys.  Space bar was one of the primaries and the letter "n".  Occationally it would be other letters.  I fiddled with the speed setting for "repeat" under System/Preferance/Keyboard but that made little change.

Even knowing the scan codes I couldn't get keytouch to allow me to enter individual scan codes.. I looked at another program called Lineak and it appear that you can build your on driver/text file, but I'm fairly nOObish and haven't quite figured it out yet.

Another suggestion I found was to use evded as a keyboard driver in xorg but that drew a dead end for me.

[SIZE="2"]Using EVTEST or evtest I did manage to get scancodes for the dead keys.[/SIZE]

Here they are.
Fn key code combinations are 273 (for Fn) plus the following for the represented keys.
F1  =  256
F2  =  257
F3  =  258
F4  =  259
F5  =  261
F6  =  262
F7  =  172
F8  =  264
F9  =  155
F10 = 269
F11 = 266
F12 = 272
________________
Media Center = 263
Music Symbol = 171
Camera like symbol = 260
Box w/ Flower = 268  (what does this symbol represent?)
Zoom In = 271
Zoom Out = 270

Vol up 115
Vol down 114
next song 163
Play/Pause 164
Prev. Song 165
Stop CD 166
mute 113
Calc 140

and what I think most refer to as the Vista Key (3 offset overlayed boxes) = 267
I could not get the Power button code because everytime I pressed it I had to hard reboot. Machine wouldn't come back from sleep.

---

### Post by sweetthdevil on 2008-03-21
Are you using Hardy? 

Because I am but using it (hardy) and testing with xev they are still dead.

And what do you do with the scancode??

---

### Post by Scunizi on 2008-03-21
Yea.. xev didn't work for me either.. I had to use evtest to get the scan codes.. the scan codes can be placed in the keytouch file in the appropriate locations.. I tried that last night but couldn't tell if I had keytouch actually working.. I can't verify it's doing ANYTHING.  so until then I think we have the information needed but just can't seem to get it working..

I'm on Gutsy until the official upgrade is out.

---

### Post by sweetthdevil on 2008-03-21
Great thanks, I will try that tomorow and let you know what the results on Hardy

---

### Post by sweetthdevil on 2008-03-27
Quick question, how do you use evtest?

---

### Post by rolnics on 2008-04-02
Hey guys have you had any lucky? I've got one of these keyboards and it would be great to use some of the other function keys.

---

### Post by Scunizi on 2008-04-02
I took mine back because it was having mechanical problems.. some keys didn't work.. I ended up getting a Microsoft Comfort Curve 2000 that doesn't have as many programmable keys but works fine with keytouch.. I did have to manually edit the driver file changing the entries for aumix to amixer to make the volume keys work..  It's also comfortable and quiet. It was also only $19 at Fries.

---

### Post by VipeR_11 on 2008-04-19
I have the same problems all multimedia key doesn't work,and my calc and PC buttons are making my PC going to sleep mode.
Also when i need to press 2 times the same key (fast) it beeps instead of doing it.
And finally instead of turn the volume up and down with the volume buttons it turns up and down the mic volume :(

i am using the wave corded keyboard and I have it over 7-8 months now.
It is very good keyboard I only have problems in Ubuntu.
I think that most of this problems are going to be solved with the new version 8.04!
5 more days :) hopefully.

I also think that the problems are just because it is new keyboard and it is not on the list (most of logitech keyboard are there just not the wave). I am sure that it will be on the list in the new version and if not I hope the developers will read as, cause logitech wave keyboard is one of the best available in terms of convenience,quality,price.

---

### Post by ReverendFreeze on 2008-04-19
Quick question...I have the PC Coincepts SK-6000 Keyboard with built-in touchpad.  The Keyboard is PS/2 and the touchpad is serial.  Installing Hardy, the keyboard was obviously detected, but the touchpad wasn't.  I've done a little research, but I can't figure out how to get this working...I've tried several ps/2 mice as well, but none of them work.  The touchpad worked just fine on Windows2000Pro, but I did a complete wipe and install of Hardy...any suggestions?

---

### Post by Mandor on 2008-04-26
Hi everyone,

I have a Logitech dektop wave keyboard and mouse combo and they seem to cause the X to hang after some time (like 30 min) on all kind of distros I have tried. The configurations in xorg.conf are generic :

```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

```

The whole screen changes its colors, some stripes appear, the keyboard does not function anymore and the mouse moves, but no clicks are accepted. When I use normal wired keyboard and mouse, there is not problem.

If anybody has an idea of more specific configurations to be added, I will be thankful to get them, though I doubt that is the case. Also I wonder if there are any kind of device drivers available for the keyboard (it seems there are not, however).

Any help will be appreciated.

---

### Post by linux4life88 on 2008-05-30
I just got the wireless wave keyboard and wireless LX8 mouse and I was wondering if the media keys work in Ubuntu 8.04? Or is their another way to get it to work? Currently I'm using Ubuntu 7.10 x86-64.

---

### Post by mooglinux on 2008-05-30
nope, no difference. same keys work and dont work as before. the most useful ones, like the media keys, email, webbrowser, and calculater all work tho, so personally i dont miss not being able to use the others too much.a fix would be nice tho, they would be useful. but all the most usefulones work so no real biggie

---

### Post by ferrouswheel on 2008-06-11
@Scunizi: I've tried using evtest, but it doesn't receive any of the keys you mentioned.

Can you remember if you installed the drivers in Windows first or something. Perhaps they are disabled by default to allow compatibility with older OSes?

I was a bit suspect about this keyboard when it moved around my insert key and others. But after using it for half a day, it's so incredibly nice to type on that I'm glad I got it. The mouse that comes with the desktop package is also a lot more responsive than the portable bluetooth one I got too.

---

### Post by Scunizi on 2008-06-11
@ferrouswheel .. I'm trying to remember what I did exactly.. it's been a while.  I dual boot on my machine and my wife's is strictly xp home.  The keyboard I had even had problems on her machine with the correct drivers installed.  I must have got a bad one.  I really don't remember how I used evtest. I'm sorry I can't help you there.  The microsoft comfort curve I use now is pretty much on par with the logitec wave.. however the keys are a little closer together and I have big hands.. It's functional though.. 

On a side note, in Ubuntu 8.04 Keytouch interacts with something hanging my system on "restart" or "shutdown" leaving me to do it manually at the terminal.  I've since uninstalled keytouch and just use what extra buttons function and forget the rest.. I guess it all comes back to the "kiss" principal.. "Keep it simple stupid".. At least my motto for now.. 

Good luck.

---

