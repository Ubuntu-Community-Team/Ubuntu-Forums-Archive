---
title: "Enabling an on-screen Touch Keyboard? Erks!"
date: 2016-12-31
forum: Hardware
---

### Post by davethebass1 on 2016-12-31
Good Morning,

Over Christmas by way of a project I've managed to install Yaketey Yak 16.10 on an older PC that was running XP (Windows Embedded).

In the PC's previous life it was used as a control system for a piece of equipment that is now defunct, the PC was going to be dumped but I wanted to use it as a learning project mainly to enable me to have Internet access in a remote shed (that is covered by WiFi) where its not practicable to use a Mouse and Keyboard. This little project PC ticks many boxes as its fairly compact and has on-board touch screen keyboard capability that works fine when using the original MS XP OS but I can't find a way to enable this option in Yakety Yak 16.10.

Can anyone advise me please? 

I'm a newbie to Ubuntu and have got this far on my own (insert proud smiley!) but I'm falling at the final furlong as it were.

Any advice greatly received,

Thank You,

Dave the Bass.

---

### Post by hanspeteriv on 2016-12-31
Ubuntu comes with the on screen keyboard "Onboard". I use that on my tablet. If you go to System Settings > Universal Access, select the "Typing" tab and enable "On Screen Keyboard" it should pop up.

A new icon (4 squares) should appear in the system tray. If you click on it and select Preferences you can customize the look and behavior of the keyboard.

---

### Post by davethebass1 on 2016-12-31
OK, I'll try that tomorrow morning, thanks Hanspeteriv.

---

### Post by hanspeteriv on 2017-01-02
Did you get it to work?

---

### Post by davethebass1 on 2017-01-02
Hello Hanspeteriv, no unfortunately, I'm not given the 'typing' tab in Universal Access.

---

### Post by davethebass1 on 2017-01-02
Hi again, I now have the keyboard on-screen, whahey! But.... I can only use the OSK using a mouse pointer, it seems the keyboard doesn't 'know' the actual screen is a 'touch screen'. A partial success, sort of!

---

### Post by hanspeteriv on 2017-01-02
Hm, okay, that seems strange... But you are still able to use the touchscreen for other windows? How did you end up enabling the OSK?

---

### Post by hanspeteriv on 2017-01-02
Please also verify that in the Onboard Preferences under Keyboard > touch input you have selected either single or multi-touch, not "none". Here's a screenshot: [https://owncloud.tillvonelling.de/index.php/s/7H21s1b62zTETjg](https://owncloud.tillvonelling.de/index.php/s/7H21s1b62zTETjg)

---

### Post by davethebass1 on 2017-01-03
Hello again, sorry for the long delay between post's. OK, to answer how did I eventually get the OSK to function. I found it in 'Accessories', 'Outboard' 'Keyboard' and sure enough the 4 new Icon of 4 squares popped up in the system bar at the top of the screen just as you said it would. To confirm, it does function AOK using an external mouse to control the pointer to 'press' the keys of the OSK (though it is a long winded way of entering text into (say) a search engine), it still wont work using the Touch Screen capability, its almost as though the OS doesn't know its installed on a Touch Screen enabled computer (possibly? I'm a newbie I confess).

2nd answer regarding "are still able to use the touchscreen for other windows?", the answer is No, I've lost* ALL* Touch Screen capability when booting in Ubuntu. However, if I boot using Windows XP the Touch screen function still works! I'm scratching my head a lot :)

To answer your 3rd question, yes under 'Touch i/p' I've tried both 'single touch and 'multi', neither 'enable' the the Touch screen.

---

### Post by hanspeteriv on 2017-01-07
Ahh, I misunderstood your problem. I thought you had a working touchscreen but no keyboard but actually your touchscreen does not work in Ubuntu at all. Sorry.

In that case, please post the output of ```
lsusb
``` and ```
ls /dev | grep "ttyS"
```

These will list all your USB and serial devices, hopefully including your touchscreen.

Also, can you find out what touchscreen model you have in the Windows device manager?

You may also want to refer to [https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen)

---

### Post by davethebass1 on 2017-01-09
No need to be sorry, its no problem Hanspeteriv, thank you for continuing to help me. I really appreciate it as I'm stuck.

OK, I went into the Terminal Emulator and entered the 1st script and the result is...

david@david-H570:~$ lsusb
Bus 001 Device 004: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And the 2nd command resulted in this...

david@david-H570:~$ ls /dev | grep "ttyS"
ttyS0
ttyS1
ttyS10
ttyS11
ttyS12
ttyS13
ttyS14
ttyS15
ttyS16
ttyS17
ttyS18
ttyS19
ttyS2
ttyS20
ttyS21
ttyS22
ttyS23
ttyS24
ttyS25
ttyS26
ttyS27
ttyS28
ttyS29
ttyS3
ttyS30
ttyS31
ttyS4
ttyS5
ttyS6
ttyS7
ttyS8
ttyS9


I shall see if I can find any info on the Touch Screen model by booting up in Windows later tonight, I've not been in from work for long. I'll report back when I find some more information for you.

---

### Post by hanspeteriv on 2017-01-09
You're welcome! :)

Thanks, it does not look like your touchscreen is connected using USB.
From [https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen): "[COLOR=#333333][FONT=&amp]If there is no reference to a touchscreen device in your lsusb output, the connection is most likely through one of your serial ports." So I guess the next step would be to check those.[/FONT][/COLOR]

---

