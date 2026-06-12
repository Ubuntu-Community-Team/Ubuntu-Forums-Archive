---
title: "Viewpad 10 on Ubunutu 10.10 (Maverick) touchscreen, gestures and rotation"
date: 2011-03-01
forum: Hardware
---

### Post by jonnyara on 2011-03-01
Hello everyone

After lots of searching and playing I now have the following working on my viewpad 10:

1. Touchscreen
2. Gesture support
3. Screen Rotation
4. Large scroll bars, window controls and onscreen keyboard

and this is how I did it:
**1. Touchscreen**
The touchscreen in the Viewpad 10 is reported as a Hanvon 10.1. Drivers for this are provided by ENAC (who work on all multi-touch support in Linux) and are included in the 2.6.38 kernel and above. Maverick uses kernel versions 2.6.35.

Fortunately, ENAC provide a patch for Ubuntu 10.10

My new twitter friend @ojdon has written excellent instructions on how to install this patch, here:
[http://ollie-reardon.co.cc/?p=182](http://ollie-reardon.co.cc/?p=182)

**2. Gesture Support**
This requires installing ginn and creating a wishes.xml file. Full instructions for this are here:
[http://ubuntuforums.org/showthread.php?t=1252492&page=128](http://ubuntuforums.org/showthread.php?t=1252492&page=128)
However:
1. the wishes.xml file needs to be in /usr/share/ginn, other locations don't seem to be recognised
2. It feels slow to me and can cause lock ups. Ginn and uTouch should be considered alpha software, although kudos to the devs behind it, it is going to be great.
3. I seem to be having some problems with geiss/utouch and the long press right click in mouse accessibility.

**3. Screen Rotation**
The command xrandr will rotate the screen, but it doesn't rotate the touchscreen orientation. To do this you have to use xinput to tweak the X.org evdev driver. In particular just swaping and inverting axes wasn't enough, it also required calibration. This took a lot of messing around, and in particular a shout goes out to xinput_calibrator - although I had to use it many times to get an accurate result.

To cut a long story short, I've attached a zip file to this post which contains 4 scripts entitled rotateleft, rotateright, rotatenormal and rotateinverted.

Download the zip and copy the scripts to /usr/local/bin:
```
$ unzip rotation.zip
$ chmod a+x rotate*
$ sudo cp rotate* /usr/local/bin
```

You can then run the commands from the command line to rotate the screen. If the calibration is wrong, please let me know - it may be that the calibration line works for just my viewpad!

In order to associate these commands to rotating the screen as the viewpad sends keystrokes when you rotate the screen. Therefore you can do the following:
1. load keyboard shortcuts from system -> preferences
2. click add
3. enter name "rotateleft" and command "rotateleft" (This will only work if you have copied my scripts above)
4. In the list, click "new shortcut" and then tilt the screen left. This seems to be mapped to ctrl+alt+left
5. repeat 3 more times!

**Large scroll bars, window controls and onscreen keyboard**
You can modify the file .gtkrc-2.0 in your home directory to control things such as the scrollbars. I include my gtkrc file here for reference, it just increases the scroll bars to make them more finger friendly.

I have also modified the clearlooks theme to have larger window control buttons. The included file metacity-theme-1.xml is a modification of the one in /usr/share/themes/Clearlooks/metacity-1/

Finally, for an onscreen keyboard I use onboard (it's in the respositories) but I didn't like any of the themes. It's very easy to make a new theme using inkscape, and my blue one is also included. To use it copy the *.svg files to /usr/share/onboard/layouts

Have a nice day and let me know if you find any useful hacks for linux tableting, especially if you can get ginn to play nice!

---

### Post by Kirboosy on 2011-03-01
> **jonnyara said:**
> Hello everyone

After lots of searching and playing I now have the following working on my viewpad 10:

**1. Touchscreen**
The touchscreen in the Viewpad 10 is reported as a Hanvon 10.1. Drivers for this are provided by ENAC (who work on all multi-touch support in Linux) and are included in the 2.6.38 kernel and above. Maverick uses kernel versions 2.6.35.

Fortunately, ENAC provide a patch for Ubuntu 10.10


Does this mean that it might work on my Dell Duo? (Egalax touchscreen) My screen tracks it just doesn't have multi touch (even though it should)

---

### Post by ojdon on 2011-03-01
Thanks for linking to my tutorial! A very helpful tutorial indeed! Can't wait to get stuck in and apply these fixes. Thanks for all your wisdom!

---

### Post by jonnyara on 2011-03-02
> **Caboose885 said:**
> Does this mean that it might work on my Dell Duo? (Egalax touchscreen) My screen tracks it just doesn't have multi touch (even though it should)

maybe. Do you know what the usb id is for the screen?
[http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)
this page gives detials of the current state of multi touch support available by applying the patch, although you may not need to do this as it tracks already.

Note that you need to install ginn and utouch to get multitouch to do anything useful - see my second point above.

---

### Post by Kirboosy on 2011-03-02
Hmm I had uTouch installed but not ginn. I will install the package and see if that fixes it. 

[This thread]("http://ubuntuforums.org/showthread.php?t=1658635") shows everything I have done to my computer to get it to work.

I had to edit my grub for my touchscreen to work..


```

I: Bus=0003 Vendor=0eef Product=725e Version=0210
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=1b
B: KEY=421 0 30001 0 0 0 0 0 0 0 0
B: ABS=100 3f
B: MSC=10
```

Guess it won't work with my screen. Oh well, it was worth a shot.

---

### Post by Kirboosy on 2011-03-08
Try using my script to rotate your screen. Its a bit easier. :) Just set it on your desktop if you wish and double click it to change orientation. 

It only does left and normal but really thats all you need. Also it cuts down on your script amount since it automatically switches between the two.

Enjoy,

~Caboose

---

### Post by jonnyara on 2011-04-19
dleite has posted to me to point out that the touch rotation doesn't work on 11.04

I haven't installed it yet, but I have one idea, the scripts contain two lines, one to rotate the screen and another to calibrate the touch interface. It's possible that the touch interface either a) doesn't need calibrating or b) the calibration is not valid.

Technically, I think the fact that it needs to be callibrated in 10.10 is in fact a bug, from what I can understand X should take care of this within itself, just as it does if you are using a USB mouse. Therefore the first thing I would try is removing the calibration line in the rotation scripts.

I'm personally not upgrading to 11.04 just yet, as all my machines are business critical and as rule I don't install beta software unless absolutely necessary.

Hope this helps. Please post what you find. 
Thanks

---

### Post by dleite on 2011-04-23
well, I gave up and could not get the touch to rotate with the screen in 11.04 (yes, before the official release). 

I tried all sorts of xinput commands, formats and values. Although terminal did not display any errors, swapping axis, inverting etc had absolutely no affect. I see others have filed a bug report on similar issues.

I downgraded (re-installed) 10.10. Better luck next time.

---

### Post by ambhe on 2011-05-03
Prompt, and you had problems with a sound on ViewSonic VPAD 10? At installation 10.04 and 11.04 sound works For me normally, and at 10.10 sounds isn't present, though the sound card is defined and the loudness toddler works, but the sound isn't present. :(

For touchscreen many thanks!:D

---

### Post by jonnyara on 2011-05-05
Yes, sound didn't work, but I didn't really notice until it was pointed out to me!

I've installed 11.04 now, and I have all the same issues as everyone else on this forum, but I haven't looked at any of them yet and I am not sure if I will have the time for a while, as I have huge work deadlines for the next couple of months.

In other news, viewpad have released Android 2.2 for the x86 viewpad, available here:
[http://www.viewsonic.com/products/vpad10.htm](http://www.viewsonic.com/products/vpad10.htm) - click the “Downloads” tab and look under “White Papers”.  Full instructions and download links are provided to complete the process. Note though, you have be very careful about the partitioning if you have ubuntu installed, don't install grub via the android installer, boot into ubuntu and modify grub2 (hint: install android, mount the android partition and copy the grub entries in it to /etc/grub2/40_custom and then run sudo update-grub2)

Have fun hacking everyone! Let me know if you make any headway with 11.04, Unity actually seems like a reasonable plan for a tablet (although my autohiding keeps messing up, can you make it fixed?)

When I've had a chance to play, I'll repost something, but it might be some time.

---

### Post by ojdon on 2011-05-06
It's weird... Unity looks like a Tablet interface but it really isn't optimized for the tablet at all. I mean there is no mouse gesture such as finger scrolling and those funny scrollbars are really annoying trying to find them under the finger. It's a shame really, in the alpha it was pretty usable on the Viewpad 10.

Edit: Also jonnyara, I'm using a .co.uk domain now instead of .co.cc. :)

---

### Post by ambhe on 2011-05-07
Prompt, and how it is possible to organize click by the right button of the mouse?](*,)
At 11.04 the sound and &#1090;&#1072;&#1095;&#1089;&#1082;&#1088;&#1080;&#1085; worked, but at turns of the device the data &#1090;&#1072;&#1095;&#1089;&#1082;&#1088;&#1080;&#1085;&#1072; didn't change and on the turned screen of coordinate of the mouse was not correct. 
Following instructions on site ENAC on assemblage of a kernel with the driver hid-multitouchh, has led to that the system has ceased to be started. (2.6.38-4). Support in a kernel I am primary haven't found. 
At 10.10 the sound device is visible, level toddlers work, the microphone works, through &#1076;&#1080;&#1085;&#1072;&#1084;&#1080;&#1082; the sound isn't present, and through bluetooth to set is. Tried to establish driver ALSA in manual, the sound device in general was gone.

I will wait when on [http://lii-enac.fr/](http://lii-enac.fr/) will make a patch on 11.04. To music I will listen through bluetooth...:(

---

### Post by ojdon on 2011-05-09
Regarding sound not working... Someone from [my Blog]("http://www.ollie-reardon.co.uk") suggested to me a while back that you should edit alsa-base.conf by using this command:

> sudo gedit /etc/modprobe.d/alsa-base.conf

Then adding this line at the bottom of the file:
> options snd-hda-intel model=asus

Then restart Alsa using:
> alsa force-reload.conf

Never tried it myself, though so would love to hear if it did work or not.

---

### Post by ambhe on 2011-05-11
Has tried. Doesn't work.:(

---

### Post by jonnyara on 2011-05-27
Meh. Having played around 11.04 doesn't seem like the linux for this tablet. Unity is far from finger friendly and right-clicking doesn't seem to work. I can't seem to work out screen rotation either.

So, ideas anyone on a full fat quick booting linux distro? Meemo? Something based around Gnome 3? Back to 10?

Such a shame. At the moment, I'm actually thinking of ebaying the viewpad as android 2.2 isn't good enough either.

---

### Post by ojdon on 2011-05-27
Unity isn't a tablet friendly interface at all. Although Gnome-Shell is excellent, probably my favourite interface to use on a tablet device. If you want Meego installed on the Viewpad 10 then I've made a tutorial [here]("http://www.ollie-reardon.co.uk/meego-on-the-viewpad-10/"). You can get the official Viewsonic update for 2.2 [here]("http://www.viewsonic.com/ISOs/p10t-V2.2-1.4_viewsonic_dual.iso"). Although I prefer using [this image]("http://www.cartft.com/support_db/support_files/CTFPAD_Android_V2_2.zip") since it comes with a few more useful apps like Gapps. 

There are a few more interesting things coming up for Tablets in the next coming months, Maliit (The excellent Virtual Keyboard for Meego) is [currently being packaged up for Fedora 15]("http://www.jonnor.com/2011/04/introducing-maliit-on-screen-keyboard-in-gnome-3/"). As well as Chrome OS getting touch enhancements too! It's just a matter of being patient, I'm afraid.

---

