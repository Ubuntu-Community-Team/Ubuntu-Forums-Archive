---
title: "LIRC remote questions"
date: 2008-10-17
forum: Hardware
---

### Post by Kain000 on 2008-10-17
Hey everyone, 
I'm wondering if anyone out there can help me or at lest point me in the right direction when it comes to LIRC (linux infrared remote control) I bought a antec drive bay insert that holds an IR receiver and connects 
1)into the motherboard constant 5 volt rail and into the power switch pins so it can be used to power on the computer

2) into a USB header, for the serial connection

my question is though I've looked arround both on the general internet and on the LIRC homepage, i've found nothing so far as config files to feed into LIRC for that particular remote or anything close to it.   

I'm more then willing to wright my own config file to say 
the button i just pressed (right) that the computer just read as this hex number...... blah.......    will be treated as if I pressed the right key on the keyboard.    

However I do not know where to start.    First I would think I need to find out how the kernel is handling the IR receiver into the usb... if at all!  and from there where it's outputs are going.  

From there I could just go threw all the buttons and give LIRC a config file to translate those hex numbers to keyboard commands.  

The ultimate goal here was to use the antec remote to both turn on the computer...CHECK    and to be used as a remote to navigate threw Elisa media center.

any guidance would be greatly appreciated.
-sean

---

