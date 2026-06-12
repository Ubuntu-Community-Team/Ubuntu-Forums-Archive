---
title: "WACOM Bamboo Pen Tablet"
date: 2010-09-18
forum: Hardware
---

### Post by teward on 2010-09-18
Got one of the above listed tablets.  Wondering how I go about getting and installing the drivers for it so that it operates on 10.04.

System is a Dell Latitude E6500 (probably the same specs as in my sig), fully Ubuntu 10.04.

---

### Post by Favux on 2010-09-18
Hi TrekCaptainUSA,

See the [Bamboo Pen & Touch HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by teward on 2010-09-18
**I.  Install LinuxWacom's 0.8.8-8 wacom.ko** (the USB kernel driver)

That 404's when i try and wget it.

---

### Post by Favux on 2010-09-18
Should work.  It's still up on the site:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)  unless the site is temporarily down.  You could try downloading it directly onto your Desktop.

---

### Post by teward on 2010-09-18
lol I can officially blame internet lag for that.  x]

I'll let it finish downloading the stuff i need then i'll get back to this and see if it worked :)

---

### Post by teward on 2010-09-18
**IV.  For Lucid & Maverick you use a xsetwacom script file instead of wacomcpl and  wacomcpl's .xinitrc** (attached below).

Which attached file to that thread is the correct file to use/download?

---

### Post by Favux on 2010-09-18
Sample_Bamboo-P&T_xsetwacom-scripts.tar.gz

Since you're not using xorg.conf use the wacom.conf script and use the "Device Names" that:
```
xinput --list
```
returns for you.

---

### Post by teward on 2010-09-18
Got to this part, got lots of errors in it, with properties not existing, or faild requests.

But up to the point of the custom script needing to be run...

**IT WORKS!**

Thanks for the help.

---

### Post by teward on 2010-09-18
er, whoops.

I ran the .xsetwacom.sh... and now i cant click.

A restart seemed to rectify the issue, but I believe that you do not need to run the .xsetwacom.sh script if you have just the pen version... or did I miss somethign?

---

### Post by Favux on 2010-09-18
With the Pen version you just need the stylus section in the script.  Not the other 3 sections because you don't have the eraser, touch, or pad.  So just remove those sections.

---

### Post by teward on 2010-09-19
the device id from xlist --input and the script do not match up.  What should i do in that case?

---

### Post by Favux on 2010-09-19
Always use the "Device name" your system returns from:
```
xinput --list
```
This is because the "Device name" changes with different versions of the linuxwacom wacom.ko (the usb kernel driver).

---

### Post by teward on 2010-09-19
The device name I have and the script(s) you provided don't have the device name in the scripts.

So thus I assume the script is a moot point, and cannot be used?

---

### Post by Favux on 2010-09-19
The "Device name" and the ID number are interchangeable.
```
## stylus = ID 9 = "Wacom BambooFun 2FG 4x5 Pen"
```
Change the number to your stylus' "Device name".  The ID number can change with hotplugging.

---

### Post by teward on 2010-09-20
My device name shows up as "Wacom Bamboo 4x5 Pen stylus".  Will your script still be able to make it work?

Also, is it possible to interchange the rocker-button functions that exist on the stylus so that when i click up on the stylus' button, it middle clicks rather than right clicks?

---

### Post by Favux on 2010-09-20
Hi TrekCaptainUSA,

Yes to both questions.

For the stylus buttons just switch the assigned button number:
```
xsetwacom set "Wacom Bamboo 4x5 Pen stylus" Button2 "2"  # middle mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen stylus" Button3 "3"  # right mouse click

```

---

### Post by teward on 2010-09-21
Got it.  The thing is not taking the changes into effect, however.  As such, the rocker buttons remain doing what they were originally designed to do.

---

### Post by Favux on 2010-09-21
Did you remember to make the script executable like the HOW TO shows you how?  And you can test out a command by entering it in a terminal.  It will take effect immediately.

---

### Post by teward on 2010-09-21
Lets put it this way:  I admin a linux server, and I know how to run scripts

sudo chmod +x <target file>

Done.  Even ran the commands in terminal standalone.


Same outcome:  the click commands did not change.

---

### Post by Favux on 2010-09-21
Hmmm.  Let's look at your Xorg.0.log then (in /var/log, as you know) and see if that tells us anything.

---

### Post by teward on 2010-09-23
There is no logfile like that.  Not sure why.

Maybe its just being stupid like a billion other things have been for me lately...

---

### Post by Favux on 2010-09-23
I have no idea why you don't have a Xorg.0.log in a Lucid gnome desktop install.

---

### Post by teward on 2010-09-24
Perhaps the NVIDIA drivers are taking over and writing in a weird fashion to logs?

In any case, I might just get used to the way the clicking is now.  It won't be insanely hard, just something I don't really want to do.

Thanks for your help though.

---

