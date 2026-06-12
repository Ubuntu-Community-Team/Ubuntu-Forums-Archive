---
title: "need help customizing logitech MX5000"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Apertotes on 2008-01-17
hiya!!!! a brand new linux user here!!! please, be patient.

i do not want to bore you, so short story is i bought a new dell XPS M1330 which came with vista. i tried it 2 days, and i decided to make the big jump to linux, ubuntu more specifically.

after a few weeks wrestling with ubuntu i have finally set up the laptop quite good, i think. only thing that is not working as it should is my logitech MX5000, both keyboard and mouse.

tonight i've spent more than 5 hours reading these forums and i have managed to make them work, at least basically. the xps internal bluetooth recognises both periferals and i have gone as far as to install xbindkeys. not only that, now both the mouse and keyboard work even on the login screen. take into account that until 3 hours ago i didnt even know how to edit a text file with root (my word of today) permissions, so i am quite extremely happy with myself.

the situation right now is as follows.

**1. Keyboard**: regular keys work perfectly, even spanish accents, "ç", and secondary key actions like *!"·$%&/()=?¿*. windows key doesnt do anything as far as i can tell, although that may be a thing of ubuntu, and not a problem with the keyboard. also volume control works allright. but that is all. all the rest of the multimedia and internet keys are not working, neither does the zoom bar and the secondary actions for the "F" keys.

**2. Mouse**: primary and secondary buttons work fine. also vertical scrolling works fine (both turning the middle wheel and with the buttons upside and downside of the middle wheel). back and forward with lateral buttons also work very good. but i cant make horizontal scroll with the wheel. it just doesnt do anything. also, pressing the wheel doesnt do anything, and the third lateral button doesnt do anything either.

the lack of horizontal scroll is quite strange cause i can do it on the touchpad, but with the MX1000 it just doesnt work.

now, what i would love to achieve is this:

- be able to open "My Music", "My Videos", turn on the webcam, vlc/winamp, firefox, etc. with the extra keys on the keyboard

and for the mouse

- pressing the wheel down would turn cruise control on

- pressing the wheel towards the sides would scroll horizontally

- pressing the third lateral button should be "Alt+Tab"

- pressing the two main lateral buttons should be "Crtl+W" for the first one and "F5" for the further one.

so, is this possible? and even more important, is it easy enough for a complete noob?

thanks a lot for your help

ps: sorry if this is a known issue and there are other threads. i have been looking the whole night and in fact, i managed to make my laptop recognise the devices thanks to all the threads i found. but i didnt find how to map keys or mouse buttons to custom actions. or at least, i didnt find it in a way i could understand and actually reproduce. anyhow, if someone can point me to another thread where this is explained, i'll be most grateful

---

### Post by Yellow Pasque on 2008-01-17
Here's something from the Gentoo forum. Ignore the first step when it talks about kernel config as you already have a properly built/config'd kernel
[http://gentoo-wiki.com/HOWTO_Logitech_MX5000_Keyboard](http://gentoo-wiki.com/HOWTO_Logitech_MX5000_Keyboard)

---

### Post by Apertotes on 2008-01-18
> **Temüjin said:**
> Here's something from the Gentoo forum. Ignore the first step when it talks about kernel config as you already have a properly built/config'd kernel
[http://gentoo-wiki.com/HOWTO_Logitech_MX5000_Keyboard](http://gentoo-wiki.com/HOWTO_Logitech_MX5000_Keyboard)

mmm... that looks great, but following the links it says that for the keyboard to work correctly you need to use the dongle and emulate a usb hub. if i understood correctly (cause english is not my language), this means that i can not make full use of the keyboard with the internal XPS bluetooth. if i am correct, then this solution is not the one i am looking for, cause i would prefer to not use the MX5000 dongle.

also, it seems this solution is only for the keyboard. does anybody know an easy way to map the MX1000 mouse buttons?

---

### Post by Apertotes on 2008-01-19
well, i am making some progress. i am using keytouch for the keyboard and btnx for the mouse.

btnx is really what i wanted. i can map any mouse button to any key combination i need. although i am not able to map one of my buttons to "alt+tab" or any other combination that lets me switch between current applications.

keytouch is also a nice program, but it doesnt recognizes most of the "special" keys of the MX5000 keyboard, so i didnt improve a lot. i am still missing functionality of all the "My ..." keys (my videos, my pictures, etc) and the messenger, state and webcam buttons.

can somebody help me any further?

---

