---
title: "microsoft wireless entertainment desktop 8000"
date: 2008-09-13
forum: Hardware
---

### Post by nickolasemp on 2008-09-13
Hello everyone.

I've been using Vista for the longer period of time and I've decided this summer to switch (not fully) to ubuntu. Here is the thing though.

Whenever I try to boot from ubuntu, my keyboard doesn't work. I have to manually press the connect button which is located underneath it.

However the mouse works just fine(as long as I don;t press anything in the keyboard because then the mouse stops responding for a while).

So is there any solution to this?

I don;t know if it helps, but when I first get to Vista, reboot and then to ubuntu, none of this happens.

I'm guessing that windows connects it automatically when it enters in vista and then the 'preferences' stay in its log for a while so that ubuntu can 'see' it as a functioning keyboard.

In case it helps, lsusb (when my keyboard works) gives back this:
```
Bus 008 Device 006: ID 045e:0714 Microsoft Corp. 
Bus 008 Device 005: ID 045e:0715 Microsoft Corp. 
Bus 008 Device 004: ID 045e:0707 Microsoft Corp. 
Bus 008 Device 003: ID 045e:070c Microsoft Corp. 
```


Thank you a priori for any advice.

---

### Post by ljw777 on 2008-09-13
I'm having problems getting this keyboard to recognize in linux too.  Of course, same as you, the mouse works just fine.  I don't have Vista or any other windows installed on the machine, so I'm not able to try that option.

I just started tinkering with this in my spare time in the last week.  If I figure out something, I'll post to let you know.

---

### Post by nickolasemp on 2008-09-13
We'll might as well wait for 8.10 to come in one month (see [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/BluetoothInputDevices") for reference). 

I'll try that one later on.
[COLOR="DimGray"]Greetings to Kansas...[/COLOR]

Edit#1:This doesn't help but it's a good thing to add. In terminal type ```
sudo gedit /etc/X11/xorg.conf
```, then edit the part where mouse is located, so as to say ```
Option "Buttons" "7"
```. Now you can use front and back as the side buttons on your mouse... Still looking for another solution.

Edit #2: Found [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/InstallUSBKeyboard"). Since it is not a bluetooth device (it is actually a usb), I figured out that [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/InstallUSBKeyboard") might help. I cannot get it to work in BIOS, so probably my problem lies there...

---

### Post by nickolasemp on 2008-09-13
Problem solved for me..! Well sort of... actually not so much... I just figured where I should actually look for.

The problem is in my BIOS not in ubuntu.

As pointed out [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/InstallUSBKeyboard") I can't get the Grub to work so this is not a fault of Ubuntu... Still... It should check for PnP devices at startup...

[SIZE="1"]Kudos to Andreas Troschka![/SIZE]

---

### Post by ljw777 on 2008-10-10
Thanks for the info.  I'm glad you got yours working!  Still no go for me.  I already had USB keyboard support enabled in my BIOS and PNP OS--disabled.  I've even tried enabling PNP OS.

What's really interesting about this problem is that within dmesg, it's detecting the keyboard and mouse, but neither work.

Since changing BIOS solved it for you, I will probably see if there is a BIOS update for the MSI mainboard that I'm using.

I'm sure I'll eventually get it working, but will have to do some more troubleshooting.

---

### Post by nickolasemp on 2008-11-02
> **ljw777 said:**
> Thanks for the info.  I'm glad you got yours working!

I didn't... I just know that it is BIOS's fault.

Then again, using Windows Vista still doesn't recognize my keyboard from BIOS, but I have to wait till the login screen for Vista to find it and make it usable... So MS intended to have the OS to "enable" the keyboard...

So, I don't know, should I upgrade my BIOS too? That probably won;t change a thing.

The guy from the previously pointed blog, said that if you can't enable it from BIOS then nothing can be done... then again, you say that dmesg says it is there... **_And since Vista enables it after BIOS, I'm sure that ubuntu can do it as well_**...

I am no expert in linux, so I can't really help much...

P.S.: Did 8.10 change any of this??? My brother has 8.10 in his laptop with 8000 and he can use the mouse but not the keyboard... He once did something with that bluetooth icon next to the clock and something with the keyboard preferences, and got it working... Then he rebooted and no luck since then...

---

### Post by z2177199 on 2008-11-18
Check with different USB ports. On my motherboard, ga ep35 ds3p, the 8000 Keyboard only work (in both Ubuntu 8.04 and last night 8.10) when the dock is connected to the bottom/lowest usb port (when you have a stand up case). According to the motherboard manual, all usb ports are from the same southbridge but somehow reacted differently to the 8000 kb. Also, when lsusb, the bottom usb port gave lower device id compare to the other usb ports.

---

### Post by dgooding on 2009-05-25
FYI, I just bought a Microsoft Wireless Entertainment Desktop 8000 combo, unpackaged it, put batteries in, plugged everything in to my machine running 9.04, and it all started working.  Didn't even need to reboot.  Some of the special keys don't work (as it usual), but both keyboard and mouse worked literally out of the box.  So far, it's more than I could have hoped for. (Even the little trackpad and mouse buttons on the keyboard work!)

---

### Post by nickolasemp on 2009-05-26
> **dgooding said:**
> FYI, I just bought a Microsoft Wireless Entertainment Desktop 8000 combo, unpackaged it, put batteries in, plugged everything in to my machine running 9.04, and it all started working.  Didn't even need to reboot.  Some of the special keys don't work (as it usual), but both keyboard and mouse worked literally out of the box.  So far, it's more than I could have hoped for. (Even the little trackpad and mouse buttons on the keyboard work!)

Do you plug it into a laptop or a desktop computer? See, in a laptop computer, ubuntu usually doesn't recognize it. Actually not even BIOS recongnizes it in a BIOS (there lies the problem)!

---

### Post by dlast on 2009-06-29
I bought WED 8000 one month ago with my new computer. Everything worked perfectly out of the box (Ubuntu 9.04). I was even able to make it work in bios and grub (it was just necessary to enable the USB keyboard support in bios configuration). My bluetooth dongle was connected directly to the computer. Only later I realized that it can be inserted into the "MS Charging Hub", ok, today I bought some usb extension cords I needed and tried to put it into use with this hub. It did not work.
What was worse: it did not work even when I tried to connect everything back as before. I started to have exactly the same problems described by nickolasemp and ljw777.

I was quite terrified, however the good news is that I managed to make it work again: my procedure is described bellow. 

I didn't try to repeat this procedure, sorry, I am too coward to break it again and try the procedure once more to find out whether it really works or whether it was just by chance. I was playing with the stuff 5 hours already, I managed to make it work once (without remembering the exact procedure), break it again, and now make work 2nd time while noting down the procedure as described bellow...  

Anyway, even if it does not work for you, my experience shows that:
- in spite of that you were lucky at the beginning and your keyboard worked out of the box, it may get broken
- it is possible to make it work if you are patient enough and try again and again the process of reconnecting of the tranceiver and keyboard/mouse...

As I was googling on the topic of reconnecting MS transceiver with keyboard/mouse, it seems that they had problems like this also in Windows in previous MS wireless keyboard/mouse versions. WED 8000 worked for me however perfectly in Windows 7 RC with drivers provided on drivers CD that came with the keyboard. With Ubuntu you need to have Good luck!!!

My procedure:

Short version (press means actually "press and hold few secs"):
- press bluetooth button on the dongle
- press bluetooth button on the keyboard
- press bluetooth button on the dongle
- press bluetooth button on the mouse
- press bluetooth button on the keyboard

Long version: 
- keyboard/mouse off, usb dongle disconnected from the pc, be sure that batteries in the mouse as well as keyboard are charged, MS Charger Hub plugged into the PC
- turn on keyboard
- turn on mouse
- insert dongle into usb charger hub
- press and hold "bluetooth" button on the dongle: hold few secs until the led on it starts blinking quickly
- wait a while... (let's say 5s, I was just trying not to hurry during the process I don't know whether it does matter)
- press and hold "bluetooth" button on the keyboard: hold few secs until the keyboard "battery status indicator" light starts blinking - switching green and red
- after few secs this blinking stops, wait a while and try the keyboard and the touchpad on the keyboard: it was working for me!!!

- now: mouse still not working, I continued like this:
- press and hold "bluetooth" button on the dongle: hold few secs until the led on it starts blinking quickly
- press and hold "bluetooth" button on the mouse: hold few secs  until the mouse "battery status indicator" light starts blinking - switching green and red
- (wait a while, try move mouse, it should be working, keyboard is death however)
press and hold "bluetooth" button on the keyboard: hold few secs  until the keyboard "battery status indicator" light starts blinking - switching green and red
- wait a while, try mouse, try keyboard, everything was working!!!

---

