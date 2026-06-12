---
title: "Wacom Intuos4 Configuration. Please assist me"
date: 2011-02-09
forum: Hardware
---

### Post by FWW on 2011-02-09
Hi all,

The past few days have been spent scouring the internet for anyway to configure the express keys and wheel on my Wacom Intuos4 small (wired) tablet in Ubuntu 10.10. Without any success that is. 

So if any one could provide me with simple step by step instructions it would be greatly appreciated.

Also I am in the process of reinstalling Ubuntu 10.10 in case there were any settings that I completely mashed.

Again, thank you very much.
-Freedom

---

### Post by Favux on 2011-02-09
Hi FWW,

Welcome to Ubuntu forums!

There are a few ways to go.  One is to setup up an xsetwacom script and the other is to use the OLED userland app.  There is also a configuration gui that I haven't got around to trying.

Sample xsetwacom scripts, including one for the Intuos4, are attached to the bottom of post #2 on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  By the way to get your touch ring working you'll need to update xf86-input-wacom.  See part II. in the HOW TO.

Christoph Karg's and sanette's OLED userland app. is [here]("http://ubuntuforums.org/showpost.php?p=10173761&postcount=111").  Although recently there is a question about it crashing X.  I believe Peter Hutterer just figured out the problem and posted a patch.  It's not yet committed to the xf86-input-wacom git repository however.  But should be in a few days.

Hope this helps.

---

### Post by FWW on 2011-02-09
Thank you very much :) Its mainly your posts on different threads that have been helpful at all in the process, so I thank you for all of the posts you have submitted everywhere. I will let you know if either of the two processes work for me. (Which I'm sure they will) Its interesting that in 10 minutes of posting a thread someone can give you the answer you have been looking for, for days.

---

### Post by mikael138 on 2012-03-14
Hello!
I'm a totally novice to ubuntu, after years with Windows I've decided to use ubuntu for my music and painting needs. So I have installed ubuntu studio but I can't get my wacom tablet running. I Saw the scripts you put up on the board earlier, but I don't know what to do with them.
the Favux_Intuous4_wacom.conf-.xsetwacom script

What should I do with it?

Would help a lot if anyone could help me, I'm very new to ubuntu

Thanks!

---

### Post by Favux on 2012-03-14
Hi mikael138,

Welcome to Ubuntu forums!

Which release of Ubuntu are you using?  Is your Intuos4 working, i.e. the stylus draws?

---

### Post by mikael138 on 2012-03-15
Thanks! And thank you for the quick respons!
I'm using ubuntu 11.04 and then installed ubuntu studio.
Yeah the stylus is working, but only like an relative mouse, it doesn't use the tablet as an absolute source, know what I mean?
and the LED display doesn't light and the stylus pressure-sensitivity and stuff doesn't work and such

know what I need to do?

Regards Mike

---

### Post by Favux on 2012-03-15
OK, a few issues to look into.

Open a terminal and post the output after entering the following commands in it:
```
lsusb
```
and
```
xinput list
```

We'll wait on the LEDs for now.

---

### Post by mikael138 on 2012-03-15
lsusb:

Bus 002 Device 004: ID 056a:00bc Wacom Co., Ltd 
Bus 002 Device 003: ID 1210:000a DigiTech 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 
Bus 001 Device 003: ID 13d3:3304 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and xinput list

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL eraser                     id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL cursor                     id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL pad                        id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL stylus                     id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 WebCam                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

---

### Post by Favux on 2012-03-15
OK, the Intuos4 wireless.  You're using the "charging" usb cable currently?

You appear to be on the Wacom X driver because xinput list shows that stylus, eraser, etc. are being appended to the "device name".

Let's see what mode the stylus is set to:
```
xinput list-props "Wacom Intuos4 WL stylus"
```

---

### Post by mikael138 on 2012-03-15
Yes, exactly the wireless and I'm using the USB cable

here's the output for the  xinput list-props "Wacom Intuos4 WL stylus"[FONT=monospace] code:

[/FONT]Device 'Wacom Intuos4 WL stylus':
    Device Enabled (127):    1
    Coordinate Transformation Matrix (129):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Wacom Tablet Area (481):    0, 0, 40840, 25400
    Wacom Rotation (482):    0
    Wacom Pressurecurve (483):    0, 0, 100, 100
    Wacom Serial IDs (484):    188, 0, 2, 0
    Wacom Capacity (485):    -1
    Wacom Pressure Threshold (486):    27
    Wacom Sample and Suppress (487):    2, 4
    Wacom Enable Touch (488):    0
    Wacom Hover Click (502):    0
    Wacom Enable Touch Gesture (489):    0
    Wacom Touch Gesture Parameters (490):    50, 20, 250
    Wacom Tool Type (491):    "STYLUS" (501)
    Wacom Button Actions (492):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (493):    0, 0

---

### Post by Favux on 2012-03-15
Sorry, I thought Mode would appear in there.  Instead use:
```
xsetwacom get "Wacom Intuos4 WL stylus" Mode
```
If it says Relative then change it to Absolute:
```
xsetwacom set "Wacom Intuos4 WL stylus" Mode Absolute
```
I thought Absolute was the driver default now for a graphics tablet stylus.  Unless I'm mistaken that might indicate a bug.

There are two manuals for Wacom that are available.  To see them enter either *man wacom* or *man xsetwacom* in a terminal and they will pop up in the terminal.

---

### Post by mikael138 on 2012-03-15
oh, embarrassing, first time I tried it, the stylus really was relative, but now it says it is absolute and this seems to work now, wierd, sorry. I had some problems when I used the tablet for Windows Vista aswell, sometimes when I started it it got the buttons all mixed up wrong and it couldn't make difference between the eraser and the pen. but when I restarted it, it got better most of the times. maybe something wrong with the drivers, got new computer this time though, so I should be starting from fresh now.

So this works now, thanks! But still got the proble m that the stylus can't get the pressure sensitivity right, and the buttons on the tablet doesn't work right either

---

### Post by Favux on 2012-03-15
Alright, let's do pressure next.  What do you see with?
```
xsetwacom get "Wacom Intuos4 WL stylus" PressureCurve
```
then to set it softer say:
```
xsetwacom set "Wacom Intuos4 WL stylus" PressureCurve 0 10 90 100
```

Or are you not seeing pressure in some applications?  Some like Gimp requiring setting the extended input device.  In Gimp you have to go to Edit > Preferences > Input Devices > Configure Extended Input Devices and set the stylus to Screen.

---

### Post by mikael138 on 2012-03-15
I've tried it, tried some other variations of the pressure aswell, but it doesn't changes anything, weird
Yeah I'm using Gimp, and I've tried all possible choices of the brush dynamics, the velocity dynamics works, but not the pressure. And it seems to be using my secondary color as primary color!?

---

### Post by Favux on 2012-03-15
After you change the pressure with the set command does the get command return the new values?

---

### Post by mikael138 on 2012-03-15
Yes it does. But do I need to reboot the computer or something aswell? I've only changed the values

---

### Post by Favux on 2012-03-15
No, don't reboot.  xsetwacom commands are runtime commands and they only apply to the current session.  You can set them up in a start up script or change to static Options.  See the Linux Wacom Project mediawiki HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)  See [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration").

You need to close Gimp then do the xsetwacom command and then open Gimp.  Maybe that's the problem?

Otherwise you could try reinstalling the driver package. xserver-xorg-input-wacom in case it got garbled.  That contains xf86-input-wacom which is the X driver.  Or you could update it.  The [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") has instructions for that.  Plus it has a sample Intuos4 script on post #2 and instructions on how to set it up.

---

### Post by mikael138 on 2012-03-17
I'm sorry but I'm not sure I understand, and I'm pretty sure I didn't install it correct from the start.
But I got the file [Favux_Sample_Intuos3&Intuos4_.xsetwacom.sh.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=180515&d=1294523780") from #2 on **HOW TO Set Up the Bamboo Pen & Touch in Lucid  on ** my desktop, should I just copy this into terminal?

should I just copy all the codes mentioned on the page into the terminal and reboot?

---

### Post by Favux on 2012-03-17
No.  It is a script because the commands are placed in at text file but with the extension .sh.  The .sh file is then made executable.  That way all the commands are run when the .sh file is run.  Part IV. of the HOW TO explains how to do that.

The xsetwacom.sh file you downloaded is a sample or template.  It shows you what you can do.  For one thing you have to make sure it uses your <device names> which you get by entering *xinput list* in a terminal.  You may need to change them if they are different.  For another thing the only xsetwacom commands that should be active are ones you have changed from the default.  There is no reason to re-state driver defaults with xsetwacom commands if you are not changing them.  However I leave all the xsetwacom commands in even if I have disabled them by commenting them out, i.e. prefacing the line with a #.  That way I can look at each input tool section and know what I have available to modify if I want to.

Also the xsetwacom command Parameter names can change depending on the version.  For example xsetwacom went from using Button3 to Button 3.  In other words the Button parameter added a space before the button number.  If you enter the command in a terminal and inadvertently use the old parameter name xsetwacom will return output telling you that's what you did and provide the new parameter name.

Once you get a little bit up the learning curve you'll realize that it really is pretty simple.

---

### Post by mikael138 on 2012-03-17
Aren't there any premade scripts for intuos 4 wl that I just can copy and paste into my script?
I mean afterall I don't want to edit any of the functions at all, just use it as it works to my windows computer

Or aren't there any way I can just press a button "install wacom drivers" and it's done?

I've tried so far changing everything in the script from the standard into i.e. this:

xsetwacom set "Wacom Intuos4 WL pad" Button2 "key ctrl"

is this correct?

And I've tried to do this chmod  stuff (renamed the scripts name into what mine's called, adn putting it in homedirectory)
But it can't be found

---

### Post by Favux on 2012-03-17
> But it can't be found
That most likely indicates you are in the wrong directory when executing the command.  You can also right click on the file and choose Properties then go to the Permissions tab.  Check the box in front of "Allow executing file as program".  That does the same thing.

There is a configuration gui already in Oneiric called Wacom tablet in System Settings.  It doesn't have the pad buttons and doesn't do much.  But the next version in Precise will be better.  Don't know if it will allow you to configure buttons yet.  But they are building libwacom (for tablet metadata) is it is coming and there will finally be a configuration gui like in Windows or the Mac.  KDE already has a pretty good configuration gui and GNOME is catching up.

Probably with your version of xsetwacom it is:
```
xsetwacom set "Wacom Intuos4 WL pad" Button 2 "key ctrl"
```
not
```
xsetwacom set "Wacom Intuos4 WL pad" Button2 "key ctrl"
```
You can determine the version by running:
```
xsetwacom -V
```
in a terminal.
> Aren't there any premade scripts for intuos 4 wl that I just can copy and paste into my script?
Sorry, no.  I gave up making them because there were so many changes as they worked on the Wacom X driver it was too much work to update.  Plus making them for each tablet model would be a large task, much less updating all of them.

It sounds like you're fairly new to the command line so the learning curve there might be causing some frustrations.  In a short bit you'll wonder what you were worried about.

---

