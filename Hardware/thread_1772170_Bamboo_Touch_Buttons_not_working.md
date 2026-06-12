---
title: "Bamboo Touch Buttons not working"
date: 2011-05-31
forum: Hardware
---

### Post by pythagoreanmetronome on 2011-05-31
I have a wacom bamboo touchpad.  This is NOT the pen version.  Its just the simple touchpad.  When I first installed ubuntu 11.04 it worked fine then I updated my computer and installed the nvidia drivers and now upon reboot the "right" and "left" click buttons are not working properly.  Now whenever I click on either of the buttons the mouse-pointer on my screen just goes directly up to the top left hand side of the screen and a "double-click" starts the Unity search.

I am using 2.6.38-8-generic-pae

and according to lsusb

Bus 006 Device 002: ID 056a:00d0 Wacom Co., Ltd 


IS THERE SOME SORT OF CONFIGURATION FILE OR GUI where I can assign the buttons to a use rather than just have them default to this one useless behavior?

---

### Post by Favux on 2011-05-31
Hi pythagoreanmetronome,

Sure, but first we want to find out if the Bamboo touch is still on the Wacom X driver.  Because it sounds like it may be on the evdev X driver.  What is the output of *xinput list* and *xsetwacom list* in a terminal?

---

### Post by pythagoreanmetronome on 2011-05-31
Thank you for the reply.  I will post the results in a few hours when I finish at work.

---

### Post by pythagoreanmetronome on 2011-05-31
First the output of my xsetwacom list:

~$ xsetwacom list
Wacom Bamboo 2FG Pen eraser         id: 10    type: ERASER    
Wacom Bamboo 2FG Pen stylus         id: 11    type: STYLUS    
Wacom Bamboo 2FG Finger pad         id: 12    type: PAD       
Wacom Bamboo 2FG Finger touch       id: 13    type: TOUCH  


AND second the output of my xinput list

~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Pen eraser                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Pen stylus                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Finger pad                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Finger touch               id=13    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Device 2Port KVMSwitcher                    id=8    [slave  keyboard (3)]
    &#8627; IR-receiver inside an USB DVB receiver      id=9    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver

---

### Post by Favux on 2011-05-31
That looks good.  You appear to be on the Wacom drivers so all that should be needed is to configure the buttons.  The kernel defaults for the pad buttons changed with Natty.  See  the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part V.  Also see the Linux Wacom Project's mediawiki [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") page and the [general HOW TO]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO") page.

---

### Post by pythagoreanmetronome on 2011-05-31
Yes, I looked at the part 4 you mentioned in your reply.  The problem for me is I have no idea where I am supposed to assign these button mappings you refer to in that guide.  When you say:

                     _Natty_ physical Button 1    BTN_RIGHT/Right click    X Button 3 physical Button 2    BTN_BACK                 X Button 8 physical Button 3    BTN_FORWARD              X Button 9 physical Button 4    BTN_LEFT/Left click      X Button 1

I understand what you are getting at but I have no idea whatsoever where these button mappings should be entered.  

Here is a copy of my   /usr/share/X11/xorg.conf.d/50-wacom.conf

I played around with trying to assign button mappings and restarting but the behaviour of the buttons on my bamboo touch remains the same.  I am sorry to be so dense but it just not make sense to me where I am supposed to assign these mappings if not here:

Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

---

### Post by Favux on 2011-05-31
Not a problem.

You can assign integer values to the buttons in the wacom.conf.  You'd want the usb snippet, so:
```
Section "InputClass"
Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
# MatchProduct "Wacom|WALTOP|WACOM"
MatchProduct "Wacom|WACOM|Hanwang"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
Option "Button1" "1"
Option "Button2" "3"
Option "Button3" "2"
Option "Button4" "4"
EndSection
```
Using whatever integer you want mapped to the button.

Otherwise if you want to set a key to a button you need a xsetwacom command.  So:
```

xsetwacom set "Wacom Bamboo 2FG Finger pad" Button 1 3
xsetwacom set "Wacom Bamboo 2FG Finger pad" Button 2 1

```
and so on.  Except since Button 1 is now Button 3 in Natty you'd use that, etc.  Then part IV. tells you how to make an xsetwacom script executable and place it in start up.

---

### Post by pythagoreanmetronome on 2011-05-31
First off let me say...  Thanks for your assistance.  I am just a guy who wants to double click on an icon to make it open like you can do with almost any other computer on the planet earth.  I guess its my fault for trying to plug an exotic usb device into a linux machine but good lord this is agony.  I have now rebooted my computer about 30 times this evening and changed my 

/usr/share/X11/xorg.conf.d/50-wacom.conf

in every way imaginable to get these buttons to work.  Here are my current settings, and these settings have in no way changed the behavior of the buttons from what I reported originally.  In short, when you press any button it sends the mouse pointer to to the top left hand corner of the screen.  This is where I left it.  No change at all in the behavior even after reboot.

Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
    MatchDevicePath "/dev/input/event*"
        Driver "wacom"
    Option "Button1" "4"
    Option "Button2" "3"
    Option "Button3" "2"
    Option "Button4" "1"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

---

### Post by Favux on 2011-05-31
You have the button options in a serial snippet, not the usb snippet.  That won't apply to your tablet because it is a usb tablet.  I know you're frustrated but try to slow down and look at things a little more.

It's also possible you have a bug of some sort, but we haven't established that yet.

---

### Post by pythagoreanmetronome on 2011-05-31
I read your last post and thought "ok now I will just put buttons part of the code into the different snippets and see if any of those get a response!"  Well, upon unplugging the Bamboo Touch and plugging it back in ALL of my input devices froze.  So, I could not type on the keyboard or click with a mouse.  I tried rebooting but ALL of the input devices were frozen still.  So I unplugged every usb device and rebooted this time with a PS/2 keyboard plugged in and STILL nothing will input into the computer.  I cannot type anything AT ALL into the machine or click in any way.

Obviously my xorg config is absolutely dead.

So, I do very much appreciate the help but this is a seriously diminishing returns type of situation.

I am typing this from my Debian Squeeze computer, by the way... and NO the Bamboo Touch doesn't work with this box either but at the same time I would never even bother trying to get it to work with my debian box so there you go.  I guess I just bought into this "Ubuntu is easy" mystique from the recent marketing.  Ubuntu is linux.  If you want to spend 5 hours of your life troubleshooting a double click then Ubuntu, like any other linux distro, is for you.  Anyway, even if I got it working right now, it would no doubt break at the next update, so I am now going to try to sell my bamboo touch to a windows user at work.  :P

I do appreciate your help.   I am going to reinstall and just stick to the old trusty PS2KeyboardMouse configuration.

---

### Post by Favux on 2011-05-31
Fine.

But it is beyond me why you are experimenting with random snippets.  I posted the usb snippet with the button options demonstrated in it.  Can't make it much clearer.

Any time you mess with an X configuration file you should back up the last working version of it in case you break X.  That way you can restore it from the command line.  Although I don't see how what I showed you could have broken X.

---

