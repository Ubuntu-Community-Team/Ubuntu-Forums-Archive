---
title: "Bluetooth keyboard and mouse recommendation"
date: 2008-10-04
forum: Hardware
---

### Post by ravalox on 2008-10-04
I'm looking to get a bluetooth keyboard and mouse combo for my ubuntu home entertainment system.  I'm looking for recommendations; one that has good out of the box support.

---

### Post by DaisyDeuce on 2009-03-09
I have the same question.  Does anyone have a bluetooth keyboard/mouse combo that they are totally satisfied with?  Ideally the mouse wheel and special keyboard buttons would work and the range would be at least 12 feet.   

Please give brand and model number.

---

### Post by DaisyDeuce on 2009-03-10
Bump.  

I just want to buy a ubuntu-friendly wireless keyboard and mouse.

---

### Post by DaisyDeuce on 2009-03-11
It doesn't have to be bluetooth.  I just need a range of 15 to 20 feet.  Does anyone have a wireless keyboard+mouse combo that works on Ubuntu?

---

### Post by bbear1 on 2009-03-12
I am also looking to get a wireless keyboard & mouse/touchpad/joystick.

I have done a fair bit of research and are most interested in the Logitech Mediaboard Pro which is Bluetooth and is a keyboard with integral touch pad. I read that it works great with earlier versions of ubunto but that Bluetooth is screwed in 8.10 (which I am using).

I am not sure whether to take the plunge and just buy the keyboard and try it. I have read about a 'blueman' Bluetooth manager which can be installed and replaces the default Bluetooth manages which comes with the 8.10 install. It can be used to configure your regular wireless connection, not just Bluetooth.

A lot of people still seem to be complaining about Bluetooth problems in 8.10, but it is not clear if they gave the blueman manager a try or not.

I sure would like to hear from someone who has got the Mediaboard Pro to work in 8.10. (or any other Bluetooth keyboard, such as the Logitech Dinovo)

---

### Post by DaisyDeuce on 2009-03-13
Me too.  Bump.

---

### Post by jlibster on 2009-03-15
the best overall keyboards as keyboards are the Logitech diNovo Edge and the Logitech diNovo Mini. If you don't have the edge I'd go with the mini as its small. The diNovo Edge is still a good alternative as the mouse is also built in (as it is with the mini). The main advantage of the mini is the size but unless you have thin fingers like I do, you may find touch typing with it to be more difficult if writing longs essays (as I do in my replies). For people who like to write novels, stick with the Edge. The one reservation I have about the Logitech diNovo is that although it works wonderfully out of the box and pairing it was easy as pie, every 45 minutes or so the diNovo bluetooth keyboard/mouse ( have the edge) stop responding for about a minute and then operates normally. Its not a deal breaker for a media center but it is sometimes a minor annoyance. I've posted a thread to ask people about ideas why this is happening. My first guess is something to do with the way the bluetooth stack is procesisng keyboard/mouse messages that periodically need to be clear, or it could be the keyboard/mouse occasionally lose sync. Again, the device carries on happily after about a minute of this "black out" of responsiveness. My non-wireless devices (I have a logitech non-bluetooth mouse in case an app is easier to operate with a mouse in your hand rather than a touchpad mouse device), has no such issues and when this occurs in the diNovo Edge bluetooth device I use the non-bluetooth mouse to do stuff and it works without interruption or issues. the diNovo Edge is an awesome keyboard so I use. I just hope someone has a way to reduce or remove the issues I've mentioned. there is my two cents. Hope it helps.

---

### Post by bbear1 on 2009-03-24
jlibster,
thanks for sharing your experiences of the DiNovo. I would have liked to have gone with the DiNovo but could not afford it at the time. Instead I decided to take the plunge and buy the Logitech Mediaboard Pro + IoGear Bluetooth dongle.

This is the dongle which I bought:

IOGear GBU421W6 Bluetooth USB MicroAdapter - Network adapter - USB - Bluetooth 2.0 EDR - Class 2

Intitially I had problems with loosing the connection when using the default bluetooth manager in Ubuntu 8.10. I stuck with it for a while but eventually gave up and installed blueman.

I could not find documention on blueman and had some difficulties figuring out how to do the pairing, enabling the input device, etc but I appear to have it working now.

I have not done much testing yet but so far it seems to be working ok. The touchpad took a little bit of adjustment but it now works as well as the one on my Thinkpad, which is all I can expect really.

---

### Post by Xander {MP} on 2009-04-03
I am using Ubuntu I bought the microsoft 7000 bluetooth keyboard and it came with the microsoft 8000 bluetooth mouse, 90 bucks oem. Since it is oem and did not come with a dongle I bought a trendnet dongle for 13 bucks at newegg. Everything worked out of the box, in fact I am using to type this up. The only trouble I have is this. I am using it on my desktop and it will not work when grub loads. When I need to use the other operating system I can't pick it using the bluetooth keyboard. I have to keep the ps/2 keyboard connected to pick the other operating system. Anybody know how to get a bluetooth keyboard to work when grub loads? My desktop is a dinosaur it is a little over ten years old is that what is keeping the keyboard from working at the grub menu?

Thx,

Xander {MP}

---

### Post by ndmaque on 2009-12-21
i got a logitech dinovo for notebooks and have issues in ubuntu 9 on my Lenovo T61

a) it only seems to work in the back rh usb port which isn't a problem
b) if i rest for say 5 minutes the next key i hit will produce a hash key (regardless of what i press), this is annoying as it busrts open a new window and the linux help system, sometimes dozens of them.

eg i am in gedit, office or or terminal press any key and bang, in goes a # which causes the problem 

if i am in Firefox and type anywhere after the 5 min pause then it opens up an infinite number of tabs until the system grinds to a halt

its a lovely £60 kbd but useless too

$ hcitool scan

shows nothing

---

### Post by Cirbre on 2010-01-10
I have the same problem as ndmaque, but with Microsoft 6000 Bluetooth Keyboard. If the keyboard has been idle for a moment, when resuming use, it can cause exactly the same problem, ie. some given command gets repeated endlessly. New tabs opening endlessly in Firefox is a common case.

---

### Post by Cirbre on 2010-02-06
Seriously, nobody else knows what's up with this behaviour?!?!

Have tried to track it down myself, but simply don't know enough about the system. About the only thing that looks like a clue I've managed to track down comes from xorg.0.log -file:

```
(II) config/hal: Adding input device Microsoft Bluetooth Mobile Keyboard 6000
(**) Microsoft Bluetooth Mobile Keyboard 6000: always reports core events
(**) Microsoft Bluetooth Mobile Keyboard 6000: Device: "/dev/input/event9"
(II) Microsoft Bluetooth Mobile Keyboard 6000: Found 1 mouse buttons
(II) Microsoft Bluetooth Mobile Keyboard 6000: Found scroll wheel(s)
(II) Microsoft Bluetooth Mobile Keyboard 6000: Found keys
(II) Microsoft Bluetooth Mobile Keyboard 6000: Configuring as keyboard
(II) Microsoft Bluetooth Mobile Keyboard 6000: Adding scrollwheel support
(**) Microsoft Bluetooth Mobile Keyboard 6000: YAxisMapping: buttons 4 and 5
(**) Microsoft Bluetooth Mobile Keyboard 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Bluetooth Mobile Keyboard 6000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(EE) Microsoft Bluetooth Mobile Keyboard 6000: failed to initialize for relative axes.
```

Might this have something to do with the problem? It appears that when the keyboard is detected, it is configured as having a scrollwheel?!?!? Might this be a bug in the detection function? Should I set up a pre-defined key layout or something? 

Help wanted!!! ;)

---

### Post by Cirbre on 2010-06-11
Bump!!!

This still happens with Lucid Lynx.. The keyboard goes to sleep after a while of inactivity and when it wakes up it goes berserk (repeats the latest key pressed until something else breaks it off and then just "sulks")..

Come on, is there no-one else using this keyboard or anyone with any idea what could be going on?!? I'm getting desperate... I really want to get this keyboard working, since I cannot afford a new one!.. :cry:

---

### Post by efflandt on 2010-06-12
I have a diNovo Edge keyboard/mousepad that works great with its included dongle.  It worked fine in 9.10, but due to some bug report by someone, they changed something in 10.04 that broke it.  But that was easy enough to fix with minor editing once I determined the issue.  I have no issues with any delays, dropped keys, or wrong keys, even if I leave the keyboard turned on in suspend overnight, or if I turn the keyboard off and later back on.  I think it only communicates when necessary, because its li-ion battery is supposed to last a month between charges.

The change I had to make in 10.04 was in this section of [B]/lib/udev/rules.d/70-hid2hci.rules
[/B]
```
# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Either change "hiddev*" to "hidraw*" like it was in 9.10, or simply comment out those 2 lines like this:

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```It works in CMOS set up and for BIOS password, so it should not even need any special driver.  The "hiddev*" thing makes it not even work for 10.04 live/install CD until you change that or comment it out.

---

### Post by ingeva on 2010-06-13
This is interesting reading.
I have a Dell Vostro 400 computer, about 3 years old now. The first system I was able to use it with, was Hardy 8.04. (Wireless/Bluetooth) Mouse and keyboard worked just fine with it, after I found out that I had to disable and remove all the Blutooth drivers/managers.
```
# Remove bluetooth controls that mess up mouse & keyboard.
apt-get -y purge bluez-audio bluez-cups bluez-gnome bluez-utils
```
(A couple of the above were not installed anyway).

The system worked much better without those, but from time to time there's still some erratic stops and auto-repeats. However, I can live with those because a wireless keyboard is so much more convenient.

Mouse and keyboard are from Dell. No further description except a bunch of numbers that probably won't tell anyone anything.

When I had installed Lucid 10.04, there was no contact between the mouse/keyboard and the computer. I installed the server version which always worked "out of the box", but not here. I could borrow a keyboard and install the desktop, but there's still no contact with the wireless sets, whether the managers are loaded or not.

So I'm back to 9.10, and I'd be grateful if anyone had a similar experience and a solution. Or do we have to wait for 10.10?

---

### Post by rykel on 2013-04-04
Hi, I am using a Prolink Bluetooth Keyboard PKM-3810B and Prolink Bluetooth Mouse PMO624B on Ubuntu 13.04 dual-booting with Windows 7. While both devices (devices) can connect and work out-of-the-box, it is not without problems. One, the devices cannot be used in GRUB. Two, if the Keyboard had been paired with Windows 7, I need to re-pair it with Linux and vice versa. Three, the Mouse is unresponsive/laggy and this is a known problem between Ubuntu and Bluetooth mice.

---

