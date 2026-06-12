---
title: "Ubuntu on Eee PC T101MT"
date: 2010-05-01
forum: Hardware
---

### Post by Plippo on 2010-05-01
This thread is here to discuss how to make Ubuntu work perfectly on the Eee PC T101MT touchscreen netbook.[COLOR=Gray]
[/COLOR] 
**The instructions on what has to be done after the installation of Ubuntu and more useful information can be fo[COLOR=Black]und here in the Ubuntu wiki: [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)[/COLOR]**[COLOR=DimGray][COLOR=Black]

[/COLOR][/COLOR][COLOR=DimGray][COLOR=Black]If you have any problems with the instructions, other questions or ideas, this thread is the place to share them.[/COLOR]

[/COLOR][COLOR=Gray] (This is a continuation of this old thread: [http://ubuntuforums.org/showthread.php?t=1442164](http://ubuntuforums.org/showthread.php?t=1442164))[/COLOR]

---

### Post by minhato on 2010-05-01
Hello, and thanks to all the people in both previous and this new thread for their work.
I need to make some questions about Ubuntu Lucid on Eee PC T101MT.

The first problem is about the last kernel driver supplied by Plippo in this post. After some problems and failures in its installation, it works as expected. I can configure the pressure sensitivity and probe it in Gimp. But now the USB mouse doesn't work, and I can't fix it. With the first eeepc-t101mt-touchscreen package I have no problem with the mouse.
I have some command outputs:
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController             id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                       id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

$ dmesg | grep mouse
[    0.399777] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.496470] mice: PS/2 mouse device common for all mice

```The second problem is about the precision with the calibration of the touchscreen. I have tried very carefully to get a perfect calibration, even with a very fine stylus, but the touchscreen always have a little error, about 5 or 10 pixels, depending on the zone. The error is bigger in the borders of the screen. In Windows the calibration works much better, but a little error persists too. And there is a small zone in which I can't trace a straight line with drawing software. I'm thinking that my T101MT has some hardware failure so I would appreciate some feedback from your experience about the performance of the touchscreen.

Besides, I'd like to tell you that I have achieved the double click using the mouse properties, in the accessibility menu. It doesn't works fine, but is better than nothing.

---

### Post by mrspacklecrisp on 2010-05-02
As an artist, this driver comes as a disappointment- pressure sensitivity is still broadly ignored by art applications, and when it does work (in gimp alone) it makes the program unusable with the touchscreen: Line width and opacity are almost impossible to control, half of these lines spontaneously become squiggles, at lighter pressures annoying dots are produced, and only **6** levels of a capacity for 256 levels of pressure sensitivity are used.

I have little other option than to revert back to windows or to learn how to build a driver myself.....

---

### Post by mrspacklecrisp on 2010-05-02
These may be of interest:


[LIST]
[*][http://lii-enac.fr/en/projects/shareit/xorg.html](http://lii-enac.fr/en/projects/shareit/xorg.html)
[/LIST]

[LIST]
[*][http://lii-enac.fr/en/projects/shareit/linux.html](http://lii-enac.fr/en/projects/shareit/linux.html)
[/LIST]

[LIST]
[*][http://lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://lii-enac.fr/en/projects/shareit/multitouch-devices.html)
[/LIST]

ENAC has definitely made pressure sensitivity and multitouch work on the t91mt. [http://www.youtube.com/user/CybercomLab#p/a/u/0/Ei58CkPxDr0](http://www.youtube.com/user/CybercomLab#p/a/u/0/Ei58CkPxDr0)

They use the mosart driver for the t91mt, though at the same time others have made egalax work on it. Since the t91mt and the t101mt are such similar computers, and since the egalax driver works on both, perhaps we could use the mosart driver as well. Either way, this looks like a good way of implementing real multitouch.

---

### Post by mrspacklecrisp on 2010-05-04
If you want to record video, use guvcview. It's the only one I've been able to get sound working in. And it's a serious video capture gui, not a silly little toy like cheese.

---

### Post by Plippo on 2010-05-04
@mrspacklecrisp
Does the Windows driver have any pressure sensitivity at all? If yes, I would be curious to know about it. The »6« has nothing to do with the levels of pressure, it is just the axis that reports the event. If you use an utility like evtest you see the driver reports much more different values. The driver reports the pressure value as it comes from the device, so if the sensitivity it gives you isn't enough for you, I'm sorry, but that's all the device reports.

Most art apps expect pressure sensitivity to be on axis 3, with this screen it's on 6, so they don't work correctly if they don't have an option to set the axis (like Gimp has). Maybe we can manage to change the order in which the axes are reported, I'll look into that.

The driver I packaged here **is** from ENAC, as Stéphane Chatty (StCh) from ENAC created it. He is also the person who created the Mosart driver for the T91MT. The driver I packaged **is** the Egalax driver, and it is different from the Mosart driver, because the screens **are** different and the Mosart driver doesn't work. The driver **does** support multitouch and pressure sensitivity, which you can also see by using evtest. If the T91MT has better pressure sensitivity (which I can't say from what I see in the video you posted) then it's because it's a different screen. The only reason you can't use Multitouch at the moment is because no standard Linux application supports it yet. The application used in the video seems to do, so if you find out which one it is, you will probably also be able to use it on the T101MT.

@minhato
That the USB mouse doesn't work is strange, I also tried it out and it also doesn't work for me. I'll look into this and maybe ask StCh if I can't figure it out.
 
The problem with the calibration seems to be a hardware problem, I also have such a problem at the left edge of my screen, but it's only 1cm wide or so so it doesn't disturb me much, seems to be worse in your case. The problem is that we can only do a 4-point calibration with the current evdev driver in Linux. I guess the Windows driver calibrates with more points, that's probably why it works a bit better there.

---

### Post by Plippo on 2010-05-04
Okay, I found and fixed the USB mouse issue, it was caused by a small mistake I made building the driver. The new version is online, so please first remove the old kernel module package (sudo apt-get remove egalax-multitouch-driver-*) and then download and install the new one: [http://www.philmerk.de/dwl/deb/egalax-multitouch-driver-2.6.32-21-generic.deb](http://www.philmerk.de/dwl/deb/egalax-multitouch-driver-2.6.32-21-generic.deb)

Sorry for the inconvenience!

---

### Post by Plippo on 2010-05-04
I've uploaded yet *another *new version of the driver that maps the pressure to axis 3 (was easier than I thought, and also seems to give better results. Thanks mrspacklecrisp for nagging :-) )

Now it should also work in other applications, I tested it with Xournal. In GIMP, you have to set the axis back from 6 to 3.

To install it, proceed as described in the previous post: Uninstall old driver, install new one, reboot, that's it.

---

### Post by mrspacklecrisp on 2010-05-04
Hey, nagging works for wives. It means I'll make a good wife someday.

I must admit, I've been kind of a jerk. But I'm very impressed with the newest update. I still have wiggly lines in gimp, sure, but I now have it working *flawlessly* in xournal and my very favorite painting program, mypaint, is now accepting pressure input (It's still not usable in mypaint, but that's because of a known bug in the program and NOT the driver)

Point is, if I want to use this computer to draw, I can, and that's super awesome. I'm _ecstatic_. Control is something I'll have to relearn, though- I checked evtest and learned that it's sensing 2047 levels, which I'm guessing is why lines come out heavy-handed. It's possible, yet difficult to keep a line from maximum opacity and/or width.

I have a portable art studio! A homemade cintiq! And all it took was hours and hours of fruitless googling and annoying the Hell out of some poor stranger!

---

### Post by dusjagr on 2010-05-05
Thanks for all the work. i got everything working using your tips in a single afternoon.

a small hint about the multitouch and right mouse click:

you can choose in the mouse accessibility settings the following option, "Simulated Secondary Click", just adjust it all the way to the left and you can press+hold on your touchscreen to get the right-click context menus.

---

### Post by Plippo on 2010-05-05
There has been a kernel update today, so there's a new version of the driver. It's linked in the first post, just install the new kernel driver for 2.6.32-22 after you have done the update (you don't have to uninstall the old driver, you also don't have to reinstall the calibrator, just download the new kernel driver and install it).

@mrspacklecrisp: I appreciate your excitement :-) And don't worry, you haven't been as annoying as you think. I also noticed the bug in MyPaint and tried to work around it in the driver without luck. Can you give me a link to the corresponding bug report? If there is already a patch, maybe I can create a package with the new version.

@dusjagr: Good to know! I'm working on a small daemon that will allow things like two-finger right click, two finger scrolling, two finger zooming and two finger rotation in many applications without having to change them, but it's far from finished, so in the meantime, your workaround is quite nice.

---

### Post by mrspacklecrisp on 2010-05-05
Plippo, I think I love you. Really, your devotion astounds me.

Anyway, yes, the bug I'm referring to has been reported.[https://gna.org/bugs/index.php?13622](https://gna.org/bugs/index.php?13622) It's the ghost line problem. Mypaint expects movement to come from a regular graphics tablet with which you move the cursor by hovering. It assumes the touchscreen is a mouse, and thus isn't happy.

> Several users with special  input devices (eg. capacitive touchscreens) have reported that MyPaint  adds extra lines between the strokes. 
 This happens when MyPaint does not see any motion events between the  strokes. It will interpolate position and pressure from the last motion  event. 

 The workaround is in to either disable pressure information (in  settings->pressure, set "mode for input devices" to "disabled") or to  require some minimal pressure before painting (in  settings->pressure, add a new control point to the "global pressure  mapping" curve and drag it to (0.2, 0.0). 

 There were several attempts to fix this, the most recent one,  reverted again in svn r330 since it caused problems on normal tablets.  To find a good fix that works for everyone, someone has to analyze what  GDK events you actually get on those devices and in what order.
On another note, I have Karmic on a usb stick, so I can take a look at the fn keys issue. Plippo, you may want to direct me to make sure I check in the right places. I can also save some helpful things (say, to replace the events in lucid) to an sd card.

---

### Post by Confuseling on 2010-05-06
Hi Plippo;

Thanks for your work on this. My t101mt arrived today, so I'm going to be dual booting it, though I tend to use Debian these days, and would prefer to run that if I can.

Any chance you could make the sources available so we can have a crack at building these ourselves?

---

### Post by Plippo on 2010-05-06
Of course you can get the sources, it's all free software, so it's your right to get them.

The kernel driver is provided by ENAC, you find sources and building instructions there:
- [http://www.lii-enac.fr/en/projects/shareit/linux-howto.html](http://www.lii-enac.fr/en/projects/shareit/linux-howto.html) contains general build instructions
- [http://www.lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://www.lii-enac.fr/en/projects/shareit/multitouch-devices.html) contains the specific driver - look for "eGalax"
For the package I've modified the driver a bit, one patch has already been sent to ENAC but not yet been accepted, the other one has not been sent there yet, I'll do that later and also post the patches then, I don't have them available right now.

The calibrator is basically this one: [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator) - I've just modified it a bit so it directly writes the calibration to the xorg.conf.d path, but depending on which version of Debian you use, I don't now if they already use this mechanism or still one of the older udev or hal or Xorg.conf mechanisms. In any case, I'll also post my modifications for this later.

---

### Post by Confuseling on 2010-05-06
> **Plippo said:**
> ...In any case, I'll also post my modifications for this later.

Don't let me rush you - all this is very much appreciated. I may well end up installing Ubuntu on it anyway until the useful stuff flows up to Debian or the kernel - I'll have a play, and decide what looks more feasible.

Cheers.

---

### Post by riccardo.depalo on 2010-05-06
Well, I must thank Plippo for his work: his driver is the only one which works without any problem. I tried also the driver from eeti (I found it here: [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm) ) but it doesn't support drawing with Gimp or Xournal, for instance. Anyway, the driver (I tried the beta one) comes with a calibration tools which supports 4, 9 and 25 points of calibration, and also a drawing test. Maybe it could be used to improve pen response of the t101mt.

---

### Post by Plippo on 2010-05-06
If I don't do it now, I have to do it later, so why not do it now? :-)

So, attached to this post is an archive with the patches for the kernel module and, for your convenience, also the already patched module file. So you can either download the original hid-egalax.c from the ENAC homepage and apply the two patches or simply use the hid-egalax.c from the archive.

The source code of the modified calibrator can be downloaded from [http://www.philmerk.de/dwl/deb/egalax-calibrator-0.0.2-src.tar.gz](http://www.philmerk.de/dwl/deb/egalax-calibrator-0.0.2-src.tar.gz)

---

### Post by Plippo on 2010-05-06
Hi riccardo,

yes it would really be nice if we had 9 or 25 point calibration, but unfortunately the EETI driver is closed source, so we can't improve it or use it to improve our multitouch driver. So this shows again why closed source software is a bad, bad thing.

---

### Post by Plippo on 2010-05-06
@mrspacklecrisp: Thanks for the love, you can never have enough of it.

And thanks for your offer to do some experiments in Karmic. The thing that would be of greatest interest is whether the eeepc-laptop module or any other acpi module is used in Karmic. To test this, you can go to a terminal and call
```
lsmod
```and post the output here.

Another thing you could post is the output of the command
```
cat /proc/acpi/video/VGA/LCDD/brightness
```About MyPaint: I'll try to compile that SVN Revision 330 or extract the patch from there, but then it will probably only work for resistive screens and no longer for Wacom tablets, so if you also want to use a Wacom tablet with the EeePC, that won't work. But I'll try it when I find the time.

---

### Post by mrspacklecrisp on 2010-05-06
Suspicions about lucid being darker are right. In Karmic the screen is lit up like the sun. If I'm told what commands/files can help, it'll only take a couple of minutes.
```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
arc4                    1660  2 
ecb                     2524  2 
snd_rawmidi            22208  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
dm_crypt               12928  0 
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               59080  0 
ath9k                 258744  0 
mac80211              181236  1 ath9k
led_class               4096  1 ath9k
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 10272  0 
ath                     8060  1 ath9k
psmouse                56180  0 
cfg80211               93052  3 ath9k,mac80211,ath
atl1c                  30880  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
eeepc_laptop           13936  0 
squashfs               22912  1 
aufs                  149420  1 
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
usb_storage            52544  2 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
ubuntu@ubuntu:~$ cat /proc/acpi/video/VGA/LCDD/brightness
levels:  0 3 5 7 9 11 13 16 19 23 26 30 33 37 41 46
current: 16

```
**Note:** Brightness was at the highest level I could put it at with the fn keys. It was much brighter than the maximum in Lucid.

---

### Post by lorenzoferrara on 2010-05-06
Hello, the screen brightness on Ubuntu is much lower then on Windows 7.

Also, I've installed Ubuntu on an SD card, so I can shut down the hard drive. I use 'hdparm -Y /dev/sda' to put the drive to idle. Anyone knows a way to do it automatically on boot?

---

### Post by Plippo on 2010-05-07
@lorenzoferrara: You can put this command into /etc/rc.local so it is executed on every boot.

@mrspacklecrisp: The output is very interesting. It shows that the eeepc_laptop module is loaded in karmic while in lucid, I can't even load it manually. I've also found a bug report about this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505452)

There seems to be a solution: Open a terminal, enter
```
sudo gedit /etc/default/grub
```and change the line that starts with GRUB_CMDLINE_LINUX_DEFAULT to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

```Then call
```

sudo update-grub

```and reboot. For me, this fixed the hotkeys and the screen is really brighter now.

When you've changed this and rebooted, you can also use the Sytem &#8250; Settings &#8250; Shortcuts utitity to assign the volume keys back to Fn+... if you have changed them before. You can also create a new entry using "add" and setting "gnome-system-monitor" as command. Then, you can assign this to Fn+F9. You can create also a new entry with command "sh home/*yourname*/touchrotate.sh LVDS1 10 toleft" and assign it to the rotation button (the first time you do this, the screensaver starts, but that's okay). With this, the only keys that don't work are Fn+F4, Fn+F7 and Fn+Space.

---

### Post by mrspacklecrisp on 2010-05-07
To get gnome-power-manager to properly recognize the backlight, to get desktop notifications for a change in brightness, and (atleast for me) to get maximum brightness, add the option acpi_backlight=vendor.

Make /etc/default/grub look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```
Then sudo update-grub again.

@Plippo: My wacom has been dead a week or two now. Years of use has frayed and loosened the cord, and I don't have the money for another, so it doesn't matter to me whether I can use a wacom with Mypaint. Still, there are others who want the option. Since they can't get support for both at the same time, maybe it could be an option to be turned off or on... I don't know. I don't pretend to know about such fancy things. But unless you're a Mypaint user too, I don't want you to worry about it. I can nag some other people, since it works so well ;)

---

### Post by Confuseling on 2010-05-08
Has anyone attempted to restore the T101MT to its original state?

I understand that if I use the restore disc I'll lose the restore partition, that doesn't bother me.

Just seeking some reassurance that if I wipe out the partitions on it, it'll still boot the disc if need be - and I have no understanding of EFI bootloaders. [ignore this question - see below]

Thanks.

[P.S. Thanks for the sources, Plippo!]

---

### Post by Hangman228 on 2010-05-08
@Plippo : Can't wait for your daemon ! When do you think it will be finished ? One week ? One month ?
Thanks a lot for your work !

---

### Post by minhato on 2010-05-08
In the last days I had no time to thanks Plippo for his work, patience and efficiency to make Ubuntu and our tablet T101MT work better.

Your last kernel fix solved the mouse problem, and it came when I was a bit desperate. I was about to reinstall Ubuntu, but it wasn't necessary.

---

### Post by Plippo on 2010-05-09
@mrspacklecrisp: Okay, I'll look what I can do, but don't expect it tomorrow. You can nag as many others as you like :-)

@Hangman228: It should take a few weeks. It already kind of works, but currently it can only send the same events to every application. It needs to recognize the running application and send specific events. And it currently breaks applications with pressure sensitivity like GIMP or MyPaint, so it'll have to automatically be deactivated when such an application is active. I also have to work on the gesture recognition code, currently it sometimes performs multiple gestures at once which can confuse applications. So don't expect it to work perfectly at the beginning.

---

### Post by Confuseling on 2010-05-09
Revised question -

Having searched eeeuser a bit harder, I'm assuming that the EFI partition is just for the boot booster. Is this correct? Does the system not, in fact, use EFI at all?

So presumably, if I format and start again from the disc, I'll lose the restore partition, but it'll recreate the boot booster. What about Express Gate?

Any clues helpful... Bit lost here. :)

---

### Post by dusjagr on 2010-05-09
thanks for the brightness fix. saved my day, especially now that the sun finally came out again... :)

four questions/remarks

1. touchscreen rotation 
is there a way to fix the device id of the eGalax. whenever i restart x and/or plug in new input devices, the id seems to change randomly. i used the touchrotate.sh script to flip the screen and input, but allways need to change the id and check. so its a bit difficult to put a launcher on a shortcut.

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController             id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]

2. speed after touchrotate
are you also experiencing massive speed issues after the rotations? pretty much everything gets slower, dragging around windows, and most of all the input itself when used in a graphic program, GIMP or something, the touch input react muuuuuch slower. anyway to fix that?

3. audio plug
when i plug in a headphone into the audio plug, the internal speakers are not turned off and no sound on the headphone. i need to manually change it in the Sound Preferences -> Output -> Connectors

is there a way to use the internal switch of the plug?

4. microphone
anyway to fix the internal microphone. i can record something, but input volume is almost minimal and lots of noise. Checking the Sound Preferences -> Input i get a tiny peak on the level meter when flicking the microphone with my fingers.

Notes: plugged in microphones/headsets work perfectly though the input plug. and no manual switching needed, as mentioned above.

---

### Post by mrspacklecrisp on 2010-05-09
@dusjagr: This fixes the microphones.    	 	 	 	 	 	  [http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html](http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html)

---

### Post by tlimsisnw on 2010-05-10
I tried Hangman228's recipe to invert the camera, but got this error:

make -C lib all
make[1]: Entering directory `/home/johnson/Downloads/v4l-utils-0.7.92-test/lib'
make -C libv4lconvert all
make[2]: Entering directory `/home/johnson/Downloads/v4l-utils-0.7.92-test/lib/libv4lconvert'
cc -Wp,-MMD,"libv4lconvert.d",-MQ,"libv4lconvert.o",-MP -c -I../include -fvisibility=hidden -fPIC -DLIBDIR=\"/usr/lib\" -DLIBSUBDIR=\"libv4l\" -I../../include -D_GNU_SOURCE -g -O1 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4lconvert.o libv4lconvert.c
/bin/sh: cc: not found
make[2]: *** [libv4lconvert.o] Error 127
make[2]: Leaving directory `/home/johnson/Downloads/v4l-utils-0.7.92-test/lib/libv4lconvert'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/johnson/Downloads/v4l-utils-0.7.92-test/lib'
make: *** [all] Error 2

Anyone else got this? Sorry, I'm new to ubuntu and linux. Grateful for some pointers.

---

### Post by Hangman228 on 2010-05-10
@tlimsisnw : I think you have ton install build-essential before run commands

@all : Have you tried the new unify ? It works quite good on my computer and it's good for tactile! But there is many bugs at the moment...

---

### Post by Plippo on 2010-05-10
Unfortunately, I wasn't able to find the SVN revision mentioned in the MyPaint bug (MyPaint has switched to GIT, so I haven't found any SVN at all) so I tried to create my own patch for this bug, with more or less success: It works for some simple brushes, but not for all. Anyway I've created a package with the modified version so my wife and anyone else who's interested can try it out, I guess a few working brushes are better than no working brushes. The package is available here: [http://www.philmerk.de/dwl/deb/mypaint-resistive.deb](http://www.philmerk.de/dwl/deb/mypaint-resistive.deb) - have fun!

@Hangman228: I've tried unity, interesting concept, but at the moment too many bugs for me, e.g. dragging a new link to the bar crashes it. Also I don't like that the maximized windows have title bars, I like it better how it's in UNE now with the title integrated into the panel.

@dusjagr: Strange that the device ids change for you, probably because you're using a mouse. I'll look if I can update the rotation script to automatically determine the ID. The speed problem is not a problem with the touchscreen but with the graphics driver, Intel have screwed up their Linux driver a lot in the last two years. Maybe there's some workaround to make it quicker, I don't know.

@Confuseling: I also guess the EFI is only for the boot booster, but I don't really know. I left all default partitions intact, only reduced the size of the Windows partition to 40 GB and created my Ubuntu partitions in the available space.

---

### Post by Plippo on 2010-05-10
Oh, and @dusjagr: Strangely for me automatic switching between speakers and headphones works. Have you installed any special ALSA package? Or maybe ASUS has built in different audio chipsets in different models. For me, lspci -v shows the following audio device:
```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ce
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

### Post by mrspacklecrisp on 2010-05-10
Plippo, I can't thank you enough. 

Mypaint is working very well, but this error interrupts me after a minute of drawing. After, I draw invisible lines that don't appear until I minimize the window, then maximize it again.
```
Traceback (most recent call last):
  File "/usr/share/mypaint/gui/tileddrawwidget.py", line 203, button_press_cb(self=<TiledDrawWidget object at 0xb82ee3c (GtkDrawingArea at 0x9c350a0)>, win=<TiledDrawWidget object at 0xb82ee3c (GtkDrawingArea at 0x9c350a0)>, event=<gtk.gdk.Event at 0x9ebe1a0: GDK_2BUTTON_PRESS x=403.60, y=236.01, button=1>)
                    self.last_painting_pos = x, y
                self.doc.stroke_to(dtime, x, y, pressure)
  variables: {'y': ('local', 236.01098901098902), 'x': ('local', 403.59926739926738), 'dtime': ('local', None), 'self.doc.stroke_to': ('local', <bound method Document.stroke_to of <lib.document.Document instance at 0xb82d08c>>), 'pressure': ('local', None)}
  File "/usr/share/mypaint/lib/document.py", line 109, stroke_to(self=<lib.document.Document instance>, dtime=0.0, x=403.59926739926738, y=236.01098901098902, pressure=None)
            l.surface.begin_atomic()
            split = self.brush.stroke_to (l.surface, x, y, pressure, dtime)
            l.surface.end_atomic()
  variables: {'self.brush.stroke_to': ('local', <bound method Brush.stroke_to of <lib.brush.Brush; proxy of <Swig Object of type 'Brush *' at 0x9ebe230> >>), 'pressure': ('local', None), 'split': (None, None), 'l.surface': ('local', <lib.tiledsurface.Surface; proxy of <Swig Object of type 'TiledSurface *' at 0x9ebe218> >), 'y': ('local', 236.01098901098902), 'x': ('local', 403.59926739926738), 'dtime': ('local', None)}
  File "/usr/share/mypaint/lib/mypaintlib.py", line 134, stroke_to(self=<lib.brush.Brush; proxy of <Swig Object of type 'Brush *' at 0x9ebe230> >, *args=(<lib.tiledsurface.Surface; proxy of <Swig Object of type 'TiledSurface *' at 0x9ebe218> >, 403.59926739926738, 236.01098901098902, None, 0.0))
        def set_mapping_point(self, *args): return _mypaintlib.Brush_set_mapping_point(self, *args)
        def stroke_to(self, *args): return _mypaintlib.Brush_stroke_to(self, *args)
        def get_state(self): return _mypaintlib.Brush_get_state(self)
  variables: {'_mypaintlib.Brush_stroke_to': ('global', <built-in function Brush_stroke_to>), 'stroke_to': (None, None), 'self': ('local', <lib.brush.Brush; proxy of <Swig Object of type 'Brush *' at 0x9ebe230> >), 'args': ('local', (<lib.tiledsurface.Surface; proxy of <Swig Object of type 'TiledSurface *' at 0x9ebe218> >, 403.59926739926738, 236.01098901098902, None, 0.0))}
TypeError: in method 'Brush_stroke_to', argument 5 of type 'float'
```

I'm having the same issue dusjagr is, and that output matches mine, but in 9.10 it would automatically switch for me (although unplugging the headphones wouldn't)

---

### Post by Confuseling on 2010-05-11
@Plippo - well, I went the slightly more reckless route (heck, when you have a restore disc little is truly reckless), and deleted partition 2, turning it into two 30 gig root partitions, a 4 gig swap, and the rest home.

Grub went on one of the roots initially, and I set the bootable flag, but it wouldn't work, so I used a rescue CD to put grub on the MBR and have had no notable problems since - can still use Express Gate (whether that counts as an advantage or not...), but did admittedly lose the F9 restore function.

The drivers work excellently as all have said, so thanks to you and StCh.

@anyone: What I'm more concerned about now though is that I think my unit may be defective. Once a system is up and running nothing seems to be able to find ethernet - ifconfig on Ubuntu and Debian reports only loopback and wireless, lspci can't see anything either, Express Gate has the 'LAN' option greyed out... Even Win7 device drivers just says 'wifi adapter' under networking.

The really bizarre thing is that the Debian Squeeze netinst ISO downloads and installs everything perfectly through ethernet. It's just that once you boot the installed system - or any installed system - it can't see it...

Is anyone else having problems? Thanks. :confused:

---

### Post by Plippo on 2010-05-11
@Confuseling: I have no problems with Ethernet, eth0 shows up in ifconfig. But once after I had installed Ubuntu, I had the problem that my Bluetooth device disappeared. It turned out that it has been automatically disabled in BIOS for some reason. U reactivated and everything worked again. Maybe that happened to your Ethernet, too? Maybe for network booting the BIOS ignores this setting...

---

### Post by hanoc on 2010-05-11
Hi,

first of all I want to thank everyone in this thread and specially Plippo for their help.

I bought the T101MT just some hours ago and in just 3 hours I got an ubuntu netbook edition running and the touchscreen working.

1. Screensaver 

EDIT: SOLVED

I followed the instructions to get the rotate button recognized and I got it as xf86screensaver. As Plippo said the first time i clicked the button it launched the screensaver. The problem is it's still doing it and the screen does not rotate (it does rotate correctly if I use the command directly).

EDIT: Sorry, the screen saver did not let me see the "reassing notice". I tried again, reasigned, and it works. 

2. Longpresses 
I guess it's not possible to perform different actions with long presses of a button, isn't it?
It would be wonderful to be able to launch matchbox keyboard and to rotate the screen while in tablet mode and we only have one button in the screen.

3. Virtual keyboard
Additionaly, are there any alternatives to matchbox-keyboard? does anyone if I can configure it to get displayed when I try to write in any field while on tablet mode? I know this should be explained elsewhere but my google skills are eluding me right now. I would appreciate even if anyone has any idea how to ask google for it.

Again, thanks to all of you, it's great to see the amount of work that there's been on lucid and the t101mt in so little time. 

Thanks!

Edit: Out out, you demons of stupidity!

---

### Post by Plippo on 2010-05-11
I've created a new version of the MyPaint package that should fix the bug mentioned by mrspacklecrisp. It's available at the old place, [http://www.philmerk.de/dwl/deb/mypaint-resistive.deb](http://www.philmerk.de/dwl/deb/mypaint-resistive.deb)

---

### Post by Plippo on 2010-05-11
@hanoc:
[COLOR=Silver]To 1.: Have you set the screensaver button for the rotation action you created by clicking at the »Shortcut« column in the respective row in the Keyboard Shortcuts application and then pressing the rotation button? This set the shortcut for me and disabled launching of the screensaver.
[/COLOR] EDIT: Great that it has been solved :-)

To 2.: As the button sends its press events repeatedly, that should be possible in theory.

To 3.: I'm using CellWriter as a virtual keyboard. It's mainly a handwriting recognition software, but it also has a keyboard. It comes with a notification area icon so you can start it by just pressing the icon.

---

### Post by Confuseling on 2010-05-11
@Hanoc; try System -> Preferences -> Mouse -> Accessibility -> Simulated secondary click, it's the closest so far. Credit someone earlier in the thread (or maybe even in the earlier thread) for spotting that.

@Plippo; good thinking, but I did try that. I think it might really be dead (err... except when it's not because some netinst ISO talks to it beyond the grave). I just have to decide whether that really matters enough for a device like this to make it worth returning, as everything else seems to be fine...

---

### Post by Plippo on 2010-05-11
@Confuseling: I guess hanoc means pressing the rotation button for a longer time...
Your Ethernet issue is strange, it can't be a hardware failure if it works for the ISO.

@dusjagr: I have created a new version of the touchrotate script where you don't need to set the output and input devices any more. The new script and the instructions are now in the [first post]("http://ubuntuforums.org/showpost.php?p=9210836&postcount=1") of this thread.

---

### Post by Confuseling on 2010-05-11
D'oh. :)

---

### Post by tlimsisnw on 2010-05-11
Has anyone been able to get more than 1 workspace in Lucid? I think I have only 1 as I can't seem to switch between workspaces. Is there something I need to set?

@Hangman228: Thanks for the camera tip. Installed build essentials and everything worked! Now I'm on the ground, cool!

---

### Post by mrspacklecrisp on 2010-05-11
I am very much indebted to both Plippo an StCh. The ubuntu community owes its wonderfully communal and supportive nature to people like them. (If only governments were like this)

My first test of the machine's potential for painting:
[IMG]http://i42.tinypic.com/18kraq.jpg[/IMG]

Already I've been taking notes on this machine, and used the webcam to practice for a play, and used it to read some books, write a paper.... This is a useful little machine, and I feel that linux has _greatly_ extended its capabilities and efficiency. My first go with linux, and I'm overwhelmed by the results.

Yay!

---

### Post by kgingeri on 2010-05-11
Hey, just for reference, the T91MT does not use eGalax driver - it needs evTouch (I think - gotta look back at my info).  Anyway, I did try this and the calibration util says something like "can't find device"  :(

---

### Post by Plippo on 2010-05-12
@mrspacklecrisp: Wow, really nice painting! That's what happens when you give your users the freedom to do what they want with a device and go beyond the usages intended by the manufacturer. Wouldn't it be a waste to use such a wonderful device only for watching videos of cats doing cute stuff?

@tlimsisnw: Are you using normal Ubuntu or the Netbook Edition? I think in a normal ubuntu, there should already be at least two workspaces, you can switch with Ctrl+Alt+Left/Right. But you can also change the number of workspaces. Just press Alt+F2 and enter gconf-editor. In the program that opens, you can change the number of workspaces, depending on whether you use desktop effects or not.
If you use desktop effects: Go to /apps/compiz/general/screen0/options and set hsize and vsize (NOT number_of_desktop) to the horizontal and vertical number of desktops you like.
If you don't: Go to /apps/metacity/general and set num_workspaces to the number you like.

@kgingeri: There are two levels of drivers: a kernel driver and an X driver. For the kernel driver the T101MT uses eGalax and the T91MT uses MosArt, which should already be preinstalled in Ubuntu 10.04. For the X driver, you can choose between evTouch and evdev. For the T101MT, only evdev seems to work, but I don't know which one is best for the T91MT. In any case, the calibrator provided here only works with evdev. If you have problems, maybe you can look at one of the T91MT threads or create a new one because the T101MT and the T91MT have pretty different hardware.

---

### Post by kgingeri on 2010-05-12
> **Plippo said:**
> ...

@kgingeri: There are two levels of drivers: a kernel driver and an X driver. For the kernel driver the T101MT uses eGalax and the T91MT uses MosArt, which should already be preinstalled in Ubuntu 10.04. For the X driver, you can choose between evTouch and evdev. For the T101MT, only evdev seems to work, but I don't know which one is best for the T91MT. In any case, the calibrator provided here only works with evdev. If you have problems, maybe you can look at one of the T91MT threads or create a new one because the T101MT and the T91MT have pretty different hardware.


@Plippo: Thanks for the heads up!  You are right, I do remember seeing evdev as well.  I'll likely go that route.

---

### Post by hanoc on 2010-05-12
Thanks 

@Plippo I am using cellwriter now. Being used to the android software keyboard I was expectinc that the screen available resized to get out of the way of the keyboard. Of course I was expecting a little too much! (for now)

@Confuseling, yes Plippo was right. Thanks anyway!

Now that everything is more or less working I think it's time to start over again. At the time of purchase I was almost convinced to replace the hard disk with a SSD one as described [here]("http://forum.eeeuser.com/viewtopic.php?id=84868"). But after reading @lorenzoferrara post I'm willing to give SD cards a try. For me reducing the use of the hard drive (and so battery usage) would be a top priority and I think I could have enough with a 16Gb card with only occasional access to the regular hard drive.

@lorenzoferrara, wich sd card did you use?
The 30Mb/s of the [SanDisk Extreme]("http://www.sandisk.com/products/imaging/sandisk-extreme-sdhc-cards-")* look promising, but I do not have any experience on fast SD cards and I don't know if the speed is real. They also don't state if the speed is in writing or reading nor any other details.
I guess that 30MB/s would be more than the actual 7200RPM hard drive quite less than a regular SSD. The ambiguous 30MB/s makes it a little difficult to compare anyway.

Does anyone have any experience on them? Should I ask this somewhere else?

* the prices are totally outdated in [this store in spain]("http://www.pcgreen.com/productos_busqueda.asp?PRODUCTO=sd+30mb%2Fs&ORIG=1&Submit3.x=0&Submit3.y=0&Submit3=Buscar"), for example, the prices are much more reasonable.

---

### Post by beastrace91 on 2010-05-12
Could anyone say exactly what all works and what doesn't work on their T101MT? I am thinking about picking one up but want to know Ubuntu will work with it before I do so.

~Jeff

---

### Post by mrspacklecrisp on 2010-05-12
@Jeff:

What we've figured out:

[LIST]
[*]The camera
[*]The touchscreen
[*]The microphone
[*]All but a few fn function keys
[*]The rotate button
[*]Simulated right-click when using the touchscreen alone
[*]Maximum brightness
[*]Support in gimp
[*]A special touchscreen edition of mypaint
[*]An accurate calibration tool
[/LIST]
Issues we still have:

[LIST]
[*]Camera is fussy. The only webcam programs that see it are cheese and guvcvideo. Cheese won't take anything but pictures, and video and sound become out of sync in guvcvideo unless captured at a very low resolution (and even then it sometimes goes out of sync) I'm unable to get it to work in any sort of video chat, though I don't know that anyone else has tried. (I'm the only person so far to note this, so I can't guarantee it isn't a singular incident)
[*]The touchscreen driver has to be restarted if you close the computer, but (atleast for me) not if you simply leave it open and let it go to screensaver.
[*]A couple people (including me) can't get the sound output to change automatically (i.e. when inserting headphones) You can work around this by doing it manually in sound preferences.
[*]One person couldn't get the camera to be right-side up with our fix. You can work around this in most video capture programs.
[*]One person (me) keeps getting wiggly lines in gimp when using the touchscreen.
[*]Some think the rotate button goes too fast. You can work around this by setting the command for the rotate script to a keystroke, key combination, or a desktop launcher.
[/LIST]
I probably forgot something, but you can basically assume that if it isn't on either of these lists, it worked all along.

~Miss Norton

---

### Post by beastrace91 on 2010-05-12
Sweet! Hopefully I'll be ordering one shortly then. How does the gfx card in it handle compiz?

~Jeff

---

### Post by riccardo.depalo on 2010-05-13
@mrspacklecrisp: Hi, maybe you get wiggly line in gimp because you tried but didn't uninstall EETI driver? Just guessing, it happened to me before I used Plippo's drivers (thanks again for them!).

@beastrace91: I used the regular gnome version of ubuntu, and I noticed compiz works fine. With 3d cube, effects and so on.

---

### Post by Plippo on 2010-05-13
@riccardo.depalo: Thanks for the hint with the EETI driver, but uninstalling it unfortunately didn't help, lines are still wiggly in GIMP. I guess it's really only a GIMP issue as no other program seems to have this issue. 

Oh, and don't thank me for the driver - it's great you like it, but I only compiled and packaged it. Thank StCh who created it!

---

### Post by hanoc on 2010-05-15
Hi,
i've been working and playing with the t101mt and ubuntu for more than a day now and I'm very happy with it.

Having had some time to get the context of the system I reread the thread and I have a couple of questions:

**1. patched hid-egalax.c**
What was @Plippo refering with [this post]("http://ubuntuforums.org/showpost.php?p=9249026&postcount=17")? I've searched all my system for the file and I haven't found it so I guess replacing an old one is not an option.
Maybe I do not need to. I installed the kernel module following the current link from the first post. I don't know if the first post was already edited to the last version when I downloaded it.


**2. brightness **
I think I'm also having some problems with the brightness.

I made the changes to the grub as indicated by @mrspacklecrisp [here]("http://ubuntuforums.org/showpost.php?p=9258509&postcount=23").

But it seems to me that I still get more brightness from windows that from linux. Is there any way to know if the change worked?

I don't know if it's usuarl but ```
cat /proc/acpi/video/VGA/LCDD/brightness
```
gives me ```
<not supported>
```

**3. hibernation **
Also I can not return my system from hibernation. It hangs at "resuming from /dev/disk/someverylongid"

Is there something I need to do before being able to use hibernation?



Finally to add to the answer @mrspacklecrisp gave @beastrace91 I must say I am having no problems with the headphones nor the orientation of the camera.

Thanks all of you for your time!

---

### Post by chavi on 2010-05-17
Hello, 
Thanks for the useful info & drivers. I'm very happy with my t101mt with Debian squeeze now!!!.

The system is running an 2.6.33-4 vanilla kernel, and runs fine, and i am trying my solutions. I wrote an helper to rotate screen what notifies the orientation and uses acpi in place the gnome keyboard shortcuts, the daemon needs one parameter extra because the rotate button emits two signals on push and release:

grotate twoclicks

I hope that works for you :) 

 [ATTACH]157320[/ATTACH]  (source)

[ATTACH]157321[/ATTACH] (binary deb package)


P.D. Sorry for my terrible english, i do not practice so much....

---

### Post by tlimsisnw on 2010-05-19
Has anyone gotten multitouch (2finger scroll, zoom in/out, rotate) to work on the T101MT trackpad?

I'm using the Netbook remix,  apart from only having one workspace, other things seems to work ok as per advice from this thread. Many thanks to all contributors. However, recently I had 2 problems appearing:

1. A message saying "cannot update .ICEAuthority" keeps popping up at boot up, although it goes away after I clicked OK. Has anyone a solution to this? I found some threads on this suggesting to delete the .ICEAuthority file, which I did. But the same problem remains.

2. Openoffice writer keeps popping up at startup although I did not add it to the startup list. How to stop this?

---

### Post by Plippo on 2010-05-20
@hanoc:
1.) The post you referring to describes manually compiling of the kernel module. If you have installed the package from the first post, you don't have to do this.

2.) The  seems to be normal, I also get it on another notebook.

3.) I'm also experiencing this problem. Don't know where it comes from, doesn't seem to have sth to do with the driver as it also happens when I unload it before. There are also no log entries, so I don't have any clue right now.

@chavi:
Thanks very much for the app, looks promising, I'll try it out later.

@tlimsisnw:
Two finger scrolling works for me, the rest not. I can post some instructions later how you can make it work, it's quite easy.  Multiple workspaces definitely also work for me, I'll have to look where's the correct setting. About the applications starting automatically:  Have you maybe set "remember running applications at logout" in the startup settings application?

---

### Post by riccardo.depalo on 2010-05-20
I noticed that webcam works fine with cheese or xawtv, with the workaround provided by this forum, but the picture is still upside down using skype. Did anyone get the same problem?

---

### Post by Plippo on 2010-05-20
The problem is that skype uses its own version of the video library, not the modified one. You should be able to fix this by calling skype using the following command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
You can change the entry in the menu to use this command so you don't have to type it every time.

---

### Post by riccardo.depalo on 2010-05-20
@Plippo: thanks, it worked, now cam in Skype is ok. But to launch it from the menu, with the code you suggested, I had to put LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype in a file I called skype.sh and write in the command line of the menu: sh skype.sh. No way to put the code as it is otherwise. But it's no problem!

---

### Post by Plippo on 2010-05-20
I've created a new version of the kernel driver package that fixes the problem that you have to re-load the module after the Eee PC has been in standby. Just download and install the package for Kernel 2.6.32-22 from the first post again (you don't have to uninstall the old one before).

---

### Post by Plippo on 2010-05-20
To make two-finger scrolling work on the touchpad, press Alt+F2 and enter
[B]gksudo gedit /usr/lib/X11/xorg.conf.d/96-synaptics-twofing.conf
[/B]An editor with an empty file will load. Paste there the following text:
```

Section "InputClass"
        Identifier "touchpad two finger scrolling"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "EmulateTwoFingerMinZ" "10"
        Option "EmulateTwoFingerMinW" "7"
        Option "VertTwoFingerScroll" "True"
        Option "HorizTwoFingerScroll" "True"
        Option "VertEdgeScroll" "False"
        Option "HorizEdgeScroll" "False"
        Driver "synaptics"
EndSection

```Now press Alt+F2 again and enter
[B]gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method --type=int 2
[/B]Nothing will happen then, that's okay. Log off and back in, now two-finger scrolling on the touchpad should work.

---

### Post by chavi on 2010-05-20
Plippo, thank you very much !!

Can you post the patch for the kernel driver.....? I'm debian user and i have an vanilla kernel....

Is not possible fix this thing in the suspension scripts (black lists for kernel drivers reloads..)?

---

### Post by Plippo on 2010-05-21
@chavi: It's not really a fix for the kernel driver, I've just added a script to /etc/pm/sleep.d which removes the module before standby and reloads it afterwards. You should be able to achieve the same thing by adding "hid_egalax" to the STOP_SERVICES list in /etc/default/acpi-support (at least that's where that file is on Ubuntu). I've just used the script variant because it was easier to add in the package.

Anyways, here is what the package does: it creates /etc/pm/sleep.d/80_egalax_touchscreen with the content:
```

#!/bin/bash
case "$1" in
    hibernate|suspend)
        rmmod hid_egalax
        ;;
    thaw|resume)
        modprobe hid_egalax
        ;;
    *)
        ;;
esac
exit $?

```That works well, but it'd be better if it was solved directly inside the driver. I've written to StCh about it but not received an answer so far, I'll of course tell you when there is a better solution.

---

### Post by dusjagr on 2010-05-21
i am also still troubled about the screen brightness. at some point i thought i got it working to be on maximum brightness, but meanwhile i start to have my doubts.

during boot, after the grub menu and before i see the logon-screen i see a sudden small dimming and i dont know if i really have it on max now. similar to the quote below, i get the same output of "cat /proc/acpi/video/VGA/LCDD/brightness" . 

is there a way to test it?

> **hanoc said:**
> [B]
2. brightness [/B]
I think I'm also having some problems with the brightness.

I made the changes to the grub as indicated by @mrspacklecrisp [here]("http://ubuntuforums.org/showpost.php?p=9258509&postcount=23").

But it seems to me that I still get more brightness from windows that from linux. Is there any way to know if the change worked?

I don't know if it's usuarl but ```
cat /proc/acpi/video/VGA/LCDD/brightness
```gives me ```
<not supported>
```

---

### Post by Plippo on 2010-05-21
I can now also confirm what dusjagr is experiencing. I added plymouth to the initramfs so the boot splash screen starts earlier and now can clearly see that at the beginning of the boot, the screen is really bright and then suddenly gets darker, with no possibility to reach the previous level of brightness again. I don't know yet what can be done about it.

---

### Post by riccardo.depalo on 2010-05-21
@Plippo: thanks for the two-finger scrolling workaround you provided. I used another script which worked, but I had to activate it at each boot and give again the password. For anyone interested, the script was:

#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
-------------------------------
I'm also experiencing low brightness in Ubuntu.

---

### Post by tlimsisnw on 2010-05-21
Plippo: Sweet! 2 finger scroll works very nicely, a lot smoother than in Windows 7! Thanks again! Looking forward to zoom in/out. Yes, I did "remember running applications at logout" once before, but I've unchecked that and it openoffice writer still pops up. How to reset this?

Also, would be nice if someone can help me get rid of the cannot update .ICEauthority error message at the start.

For some reason, in Cheese, Skype or guvcview, I get a blank screen even though the webcam LED is on. The image does show once I take a photo. Anybody experienced this?

---

### Post by tlimsisnw on 2010-05-21
Plippo: Solved the openoffice writer popping up issue. I just checked  the "remember running applications at logout" but this time I closed all windows before restarting. So it now remembers the clean state. Then I unchecked the "remember ..." again.

---

### Post by tlimsisnw on 2010-05-21
Plippo: Workspaces worked too following your previous set of instructions. :)

---

### Post by penguininja on 2010-05-21
@Plippo I have been using the Kernel 2.6.32-21 package with a lot of success the past couple of weeks.  Unfortunately, I just updated to the 2.6.32-22 kernel and updated the driver package as per your instructions in comment #1, and now I can't get the screen to calibrate correctly.  

Specifically, I run the touchscreen calibration tool as I have before.  Then the horizontal axis works fine, but on the vertical axis the cursor is always much lower then where the stylus is on the screen.  I have tried re-running the tool, rebooting again, reinstalling the driver, and reloading the module manually.

Any ideas?  Thanks for all your work on this!

(Oh and the two-fingered scrolling works great.  Thanks!)

---

### Post by Plippo on 2010-05-21
@penguininja: That's strange, the calibration tool hasn't changed since the first version of the kernel driver. It's normal that the cursor is at a wrong place while you are calibrating, but it should be okay afterwards. Does the calibration area cover the whole screen or is there maybe a bar above or below it? If yes, you can try to set this bar to auto-hide before you start the calibrator.

As a last resort, you can also try to change the calibration values manually in /home/dd/daten/Entwicklung/egalax-calibrator/deb/usr/lib/X11/xorg.conf.d/97-touchscreen-calibration.conf - then log off and log in again.

---

### Post by penguininja on 2010-05-21
I have no idea if this is related, but I unplugged my USB mouse, logged out/in, ran the calibration utility again and now everything is working great again.  Yeah!  Perhaps just user error...

---

### Post by Plippo on 2010-05-22
Yes, it could be that because your mouse was connected, it tried to calibrate the mouse, which of course didn't work out that well :-)

---

### Post by tlimsisnw on 2010-05-22
Found the problem with the image not appearing when webcam is on. I had been in extended desktop mode, so I think ubuntu became confused as to where to display the image. After I unplugged the external display, the image reappeared again. By the way, I noticed that the touchscreen calibration became completely off in extended desktop mode, presumably because the overall desktop is now much larger? Is there anyway to resolve this?

---

### Post by Plippo on 2010-05-24
Remember the daemon I promised which would listen to multitouch gestures on the touch screen and turn them into mouse and key events to control applications? Well, I haven't forgotten about that, and I think it is now in a state where I can provide you with a first rough version to test.

What it does: It recognizes the following two-fingered gestures: Two-fingered tap, two-fingered scroll, two-fingered zoom, two-fingered rotate. It blocks input so these gestures don't reach the underlying application as normal mouse events. It creates mouse and key events and sends them to the application instead.

To be able to do this, the daemon needs different profiles for different applications. Here is what should work at the moment:
**Eye of Gnome (Ubuntu's default picture viewer):** Zoom, scroll, rotate, right click
**Evince (Ubuntu's default document (PDF) viewer):** Zoom, scroll, rotate, right click
**Ubuntu Netbook Launcher:** Scroll, right click, and if you're using Compiz: switching between virtual desktops
**Desktop:** right click, and if you're using Compiz: switching between virtual desktops
**F-Spot:** Zoom, scroll, right click
**Google Earth **(REALLY fun!)**:** Zoom, rotate, change viewing angle 
**Almost every other application:** Scroll, right click, for many (like Firefox, Nautilus, Openoffice) also zoom

Of course, many more profiles need to be added. If there is an application which you would like to be supported better, please let me know.

Unfortunately, applications which use extended input capabilities like GIMP, Xournal or MyPaint don't work with the daemon. They are blacklisted, so the daemon automatically pauses when one of those applications is active. This means that you can't use two-finger gestures in those. This also means that if you find an application that doesn't work at all while the daemon is running, it probably needs to be blacklisted, too.

If you like to test the daemon, please feel free to do so, but beware that there might be (quite many) bugs in it. If you find one, please also let me know. To test it, this is what you must do:

[LIST]
[*]Download the archive attached to this post
[*]Extract it to a folder of your choice (e.g. your home dir)
[*]Open a terminal and navigate to the extracted folder (e.g. **cd ~/twofing-0.0.6b** if you extracted it to your home dir)
[*]Install the required packages: **sudo apt-get install build-essential libx11-dev libxtst-dev libxi-dev x11proto-randr-dev libxrandr-dev**
[*]Compile the daemon by calling **make**
[*]Install the daemon by calling **sudo make install**
[*]Reboot (doesn't have to be done on updates, only on first install as a new udev rule is created)
[*]Open a terminal again and call **twofing **(nothing will seem to happen)
[*]Open your favorite application
[*]Perform gestures on the screen with two fingers
[*]Enjoy :-)
[/LIST]
To stop the daemon, simply call **killall twofing**
If it doesn't work right after you have started the daemon, maybe you have to switch to a different window first.
If it still doesn't work, stop the daemon and try to start it in debug mode by calling **twofing --debug**
To make it start after every boot, add the command **twofing --wait** to the Gnome startup applications.

---

### Post by riccardo.depalo on 2010-05-24
@Plippo: your daemon is quite impressive, thanks a lot for it! Zoom works very well with chrome, but also with other browsing applications. I use a lot word-processing for work and it's amazing that pinch and zoom worked not only with openoffice, but also with Word 2007, that I installed with wine. For scrolling you have to put a lot of pressure, but it may be also resistive screen's fault. Also rotating pictures with eye of gnome is a little hard, but it works. I tried also calibre, that I use for reading documents and ebooks, and I noticed that zoom works with pdf but not with epub documents, that are now mainly used for books. Excellent work, bravo! :)

---

### Post by deephack on 2010-05-24
@Plippo

This looks excellent, unfortunately it isn't working for me.  I am running Kubuntu however with KDE 4.4 as my desktop so this might be the issue.  I ran the daemon in debug mode and got the messages saying that window blah blah was found and then that it was reading input from device.  Nothing else was displayed though even when I tried applying hard pressure.

First couple of lines I get are


Input device name: "eGalax Inc. USB TouchController"
XInput device id is 10.

Which looks like it is finding the device at least.  Any ideas?

---

### Post by Plippo on 2010-05-25
@riccardo.depalo: Good it works for you! It works better if you use your finger nails, that's the resistive screen's fault. If you perform the zooming gesture, it normally simply sends Ctrl+Mouse Wheel events, so it should works in all applications where you can zoom with Ctrl+Mouse Wheel (even ones where you wouldn't expect it, like Nautilus). If you can zoom in calibre with Ctrl+Mouse Wheel also in epub books, there is something wrong.

@deephack: I haven't tried it with KDE yet, but it should work there too. It could only be that KWin handles windows differently, I'll look into this. Currently there is no debug output if you perform a gesture, only when windows are detected, but I'll add this.

---

### Post by tlimsisnw on 2010-05-25
@Plippo: Nice work. Very impressive start for two finger nails multitouch. Can you make a control to allow user to specify the pressure level desired for multitouch detection? Or better still, autodetect the user's normal/preferred finger (nail) pressure for touch operations? That might help to alleviate the high pressure required to activate the multitouch scrolling/zooming/etc. When the screen is rotated to portrait, there seems to be more lag in the multitouch response during scrolling and zooming, possible bug somewhere or just because of going thru the mouse layer? Also, would be nice to include some acceleration to scroll in response to twofing "flicks"/quick sweeps. Still can't quite control the right click effectively for highlighting a portion of text and do a cut or copy operation by right click menu, is there a trick to this? Thanks for your efforts once again. They're definitely making my T101MT much more useful!

---

### Post by riccardo.depalo on 2010-05-25
@Plippo: I experienced ubuntu became a little more unstable with the daemon, but it may be also hardware's fault. It happened also before that some programs hang and I had to reboot. Could it be because I have double boot in grub and only one partition for ubuntu, without swap partition? I didn't want to erase hidden windows partitions. Should I exclude some program in the ubuntu boot? I have regular gnome ubuntu version, with compiz active (and this without problems).
Oh, and brightness is always a little less brigth than windows. There must be a way to solve that.
Thank you again for all.

---

### Post by atomp on 2010-05-25
Howdy folks.

Great work going on in this thread, really taking full advantage of the hardware's potential.

In terms of what is operating with the drivers and solutions provided here:

The camera
The solution to fix the rotation of the camera provided here did not work for me, I've bypassed it for now by just rotating the input with gucview.

The touchscreen
All working perfectly. Testing the multitouch daemon provided by Plippo now, but I want to get some more results before giving full feedback.

The microphone
Untested as of yet.

All but a few fn function keys
All the function keys that I need work and the for the ones that don't I've merely tied them to Super key shortcuts.

The rotate button
I'm having a bit of a problem with this, it refuses to lose its linking with gnome-screensaver. Reassigning the key with the Keyboard Shortcuts dialog didn't work and I've searched through the gnome configuration options for any sign of where it is still attached. Ideally I'd like to link it to an Esc function so that I can exit fullscreen browsing when in touchscreen mode. (Possible now with the multitouch right click however).

Simulated right-click when using the touchscreen alone
This worked fairly well, with the implementation of multitouch it becomes less of an issue.

Maximum brightness
The brightness might be max, I can't be sure as I haven't booted Windows in a looong time in order to test, however more brightness would be appreciated as sunlight has a habit of straining the eyes.

Support in gimp
Works well.

A special touchscreen edition of mypaint
Works well. (Also a wicked application, can't believe I haven't tried it before).

An accurate calibration tool
Besides initial teething issues with the calibration tool (last point would not configure) which have gone now, no problems.

I would also like to ask whether anyone knows anymore about the slowdowns when the screen is rotated because of the Intel graphics drivers?

Other than that, Ubuntu and the efforts of the individuals in this thread (special thanks to Plippo) have really unlocked the hardware's full potential.

[EDIT]: Additional - I tried putting twofing command on the startup program list and gnome appears to fail to load properly until killing the process from a console, this is only a minor issue as I can happily load the daemon manually upon startup, I just figured that this behaviour might be of interest.

Also, my desktop enjoys an odd bug/feature where X starts the screen rotated once anti-clockwise without the touchscreen input being rotated as well. This wasn't difficult to workaround (I put Plippo's screen rotation script in the startup programs with the variable set to normal) but once again I figured that this is somewhat strange behaviour.

---

### Post by Plippo on 2010-05-25
@tlimsisnw: The problem with the pressure is that this device doesn't deliver touch information when the screen is not pressed hard enough. From the few tests I have done under Windows I think I can say that there you also have the same problem. I haven't set any threshold for the pressure, it always recognizes gestures as long as the screen recognizes both fingers. But maybe I can modify the daemon so it ignores when one finger is released for a short time, which may happen when you don't press hard enough and currently breaks gesture recognition.

The reduced speed when the screen is rotated is probably again the Intel driver's fault and not specific to the multitouch daemon as the calculations required to adapt the touch coordinates to the rotated screen are not very heavy, the problem seems to be the re-drawing of the screen done by the Intel driver.

@riccardo.depalo: Do the hangs happen with specific programs? And can you still switch to a text console with Ctrl+Alt+F1? A known problem is that when you are performing a gesture like rotate or zoom and manually press a key at the same time that is also required by the gesture, that key can get stuck.

The click of the right-click action always appears at the center between the two touch points. So, if you have selected a piece of text, touch the screen with your two fingers so the selected text is in the middle between them, that should work. Please also notice that a short touch with the two fingers is enough, a longer touch could activate another gesture.

@atomp: Yes, for some reason the daemon blocks when it's started too early. If you want to add it to the startup applications, just use **twofing --wait** as the command, this causes it to wait for a few seconds before it's loaded and fixed the issue for me.

---

### Post by chavi on 2010-05-25
@atomb, i did have the same problem with the screenlock with the rotate button. My solution was to change the gconf key /desktop/gnome/lockdown/disable_lock_screen. It is not the better solution, but it works for me.

---

### Post by riccardo.depalo on 2010-05-25
@Plippo: simple applications like update-manager hanged, but I was not using the daemon in that case. I also tried to put the command "twofing" in the startup, before you explained the --wait issue. The result was that the eeepc didn't finish to boot, and hanged with the plymouth wallpaper and no gnome. At that point, I couldn't even open a terminal.

Oh, did anyone try the application provided by wcale in this thread to adjust brightness with gma 3150?
[http://newyork.ubuntuforums.org/showthread.php?t=1397371](http://newyork.ubuntuforums.org/showthread.php?t=1397371)

---

### Post by atomp on 2010-05-25
@riccardo

I have tried the setpci command and can confirm that it does indeed set full brightness, a significant improvement.

Just make sure to use ff rather than 00 as I did first time (lost all display, oops).

---

### Post by Plippo on 2010-05-25
I can confirm that using setpci, I can also increase the brightness of my Eee PC 1005HA. As its screen is generally brighter than the T101MT, I didn't notice that it didn't have full brightness before. So it seems this isn't a problem with the T101MT alone, but also other Eee PC models. This is a regression from Karmic.

[COLOR=DimGray]Manually setting the setting via setpci is a temporal solution, but the brightness changes back as soon as you use the brightness control keys or gnome-power-manager changes the brightness, so for a permanent solution this bug has to be fixed.[/COLOR]
Looks like I was wrong. While it like this on my Eee PC 1005, on the T101MT you can also use the brightness control keys to get to the old value after you have set it using setpci.

Thanks Riccardo for the hint!

---

### Post by Plippo on 2010-05-25
So, to sum it up: To make full brightness work after every boot, open the file /etc/rc.local with root rights:
```
gksudo gedit /etc/rc.local
```ABOVE the line that reads **exit 0**, add the following line:
```
setpci -s 00:02.0 f4.b=ff
```Now save the file.

This way, when you boot up, the screen will start with full brightness and you can control it normally using Fn+F5/F6 on your keyboard.

Before you do this, please make sure that for your model 00:02.0 is  the correct address by typing in a terminal:
```
lspci | grep "VGA compatible"
```The result should be a line that reads:
**00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller**

---

### Post by riccardo.depalo on 2010-05-25
I'm happy I gave you a good hint! I tried also and saw an improving of brightness.

@Plippo: system seems more stable, since I installed twofing with --wait on boot. I also tried multifinger zooming with a flash application to read a newspaper online and, though a little sluggish (no more than in windows), it worked. Then I tried to use the newer libdrm 2.4.20 - es explained in
[http://ubuntuforums.org/showthread.php?t=1484137](http://ubuntuforums.org/showthread.php?t=1484137)
because I had a similar error log during boot, and it seems it worked.

---

### Post by ebix on 2010-05-27
I'm relatively new to linux, but I just installed UNR 10.04 on my t91mt, and can't for the the life of me get the touchscreen to work. I have followed the advice of the OP and also tried installing the evTouch driver, and nothing seems to work (all the drivers and stuff install as they should, but my touchscreen refuses to even register touches).

Any helpful hints would be much appreciated:confused:

---

### Post by minhato on 2010-05-27
I have a big problem with the* twofing* Plippo software. When I run *twofing* from konsole (I use this program in Ubuntu NBR), it makes the system very unstable. I can't access to the desktop or another program, but I always can do Crtl+Alt+F1. With top command I have this output: 
```
Xorg -> 69% CPU
twofing -> 24% CPU
```If I kill the *twofing* process everything works well again.
Besides, if I run *twofing* from Alt+F2 option, I can run chromium, and it works well. But I can't run nautilus, evince, firefox, konsole, or gwenview: the system hangs and I need to kill the process to make the system to work well again.

---

### Post by Plippo on 2010-05-27
@ebix: This thread is about the T101MT, which has very, very, very different hardware than the T91MT, which again has different hardware than the T91. Please open another thread or post to one of the already existing threads about the T91MT. This one here is about the T101MT only.

@minhato: That doesn't sound good. Have you tried starting the daemon in the console with ```
twofing --debug
```
That should give some output and show you whether the daemon is hung. What window Manager do you use? As you're using konsole, are you using KDE?

---

### Post by tomtucker on 2010-05-27
Hello all....just picked up my T101MT last week!  Thanks to Plippo and everyone else who has done so much work figuring out this machine....this thread is a life-saver!

Mrspacklecrisp  - I viewed the link that you found containing a fix for the microphone issue (quiet, static) using a backports alsa module.  I installed this but it didn't resolve the issue...Do I need to still upgrade alsa using ricotz's PPA?  I noticed that thread was originally for Karmic (which used an older version of ALSA) so I'm not sure if that suggestion is applicable.

Otherwise, there is only one lingering issue I've run into, and I would appreciate any insight you fellow T101'ers can provide:  The software is gtk-recordmydesktop.  Micropohone issues aside, video lags behind the sound rather severely (behavior is same using an external mic).  At first I thought this might be due to the relatively slow atom proc, but the problem seems consistent for me even with very low framerate/sound quality settings.

Thanks in advance,
TT

---

### Post by tlimsisnw on 2010-05-27
Plippo: I did some further tests and found that twofing on screen scrolls are generally more laggy than the two finger trackpad scrolls. Also, I found the two finger scrolling (whether screen or trackpad) response is  acceptable for the Normal screen orientation, but not for for the other 3 orientations. So it does seem that the screen driver is at fault. Any ideas if that could be patched?

Also, thanks to Riccardo and Plippo, the setpci cure is finally giving me some good screen brightness.

Occassionally, when I switch screen orientation, the entire screen blacks out. Can't get it on with repeated presses of the button linked to Plippo's touchrotate.sh or any keyboard presses. Did anyone experience this? Only way to get the screen on again is to do Fn+F1 to put the system to sleep/suspend, then relogging again (without rebooting). Probably a bug somewhere?

---

### Post by kgingeri on 2010-05-28
> **ebix said:**
> I'm relatively new to linux, but I just installed UNR 10.04 on my t91mt, and can't for the the life of me get the touchscreen to work. I have followed the advice of the OP and also tried installing the evTouch driver, and nothing seems to work (all the drivers and stuff install as they should, but my touchscreen refuses to even register touches).

Any helpful hints would be much appreciated:confused:

@ebix: try this [thread]("http://ubuntuforums.org/showthread.php?t=1237709"): [http://ubuntuforums.org/showthread.php?t=1237709](http://ubuntuforums.org/showthread.php?t=1237709)
There is stuff there for you (I have a T91MT also) - the display driver here will work on the T91M fine, but I've reverted to Karmin 9.10 for other compatibilities. (Welcome to the forum tho ;) )

---

### Post by tomtucker on 2010-05-28
> **tomtucker said:**
> 
Otherwise, there is only one lingering issue I've run into, and I would appreciate any insight you fellow T101'ers can provide:  The software is gtk-recordmydesktop.  Micropohone issues aside, video lags behind the sound rather severely (behavior is same using an external mic).  At first I thought this might be due to the relatively slow atom proc, but the problem seems consistent for me even with very low framerate/sound quality settings.


For what its worth, this issue seems to be software related...I upgraded another laptop From Jaunty to Lucid today, and the issue appears on that machine as well.  Under Jaunty, gtk-recordmydesktop had been working just fine.

---

### Post by minhato on 2010-05-29
@Plippo
I don't know what's happened, but I'm executing **twofing --wait** from startup applications and everything is OK. I can run  firefox, evince, nautilus,etc, and top command is normal. And all the  gestures works well.  I can execute twofing from konsole or Alt+F2 too. I can't repeat that failure, because everything works fine.
> Have you tried starting the daemon in the console with twofing --debugYes, I have tried, but nothing strange occurred. Simply, when the sistem was hung, there was no new output.
> What window Manager do you use? As you're using konsole, are you using KDE?No, I'm using Gnome, with Ubuntu Netbook Launcher. I usually prefer KDE desktop and applications to Gnome ones, but for little screens like this the Ubuntu Netbook Launcher is more usable.

The only difference that maybe explains this magical resolution of the problem, is the installation of compiz. I think that after this, the daemon works well.

---

### Post by nebelwanderer on 2010-05-29
So, I can record sound, but the microphone still does not work in skype. Maybe there is some ways to fix this issue?

---

### Post by beastrace91 on 2010-05-30
So I finally went out and ordered myself a T101MT and I have Ubuntu all installed on it and everything appears to be working except I cannot get the screen calibration to work correctly... I installed the calibration program from the first post and ran it (which did something, the mouse now moves instead of staying in the upper left hand corner) but the mouse is nowhere near where I am touching, any suggestions?

Also just to be sure I have the right calibration program - it is just four points it asks me to press on right?

Regards,
~Jeff

---

### Post by jeromeontheweb on 2010-05-30
Thank Plippo very much for the work.

With this post, functional installation with touch screen is straight forward.

I am very fond of the design of Ubuntu Lucid and I discover with saisfaction the features of the Ubuntu Netbook Edition.

---

### Post by riccardo.depalo on 2010-05-30
Hi everybody. To get the microphone work with skype, I had to install padevchooser to regulate mono mic and not stereo. I launched the application, click on input, click on the middle button on the upper right to unblock the channels, and put one of channels to zero and the other one to 100%. It seems that skype doesn't find the mono internal mic otherwise and stops to work.
This way mic should work not only with ubuntu voice recorder, but also with skype. Or, at least, it works for my system, with alsa backports installed.

@Plippo: no way to get full brightness with setpci command in rc.local. I had to write a little script to make it work and load it at boot, called brightness.sh and launch it with gksudo sh brightness.sh
The only annoying thing is you have to give your password twice on boot

---

### Post by hanoc on 2010-05-30
Hi,

As I mentioned earlier I was trying to install everything on an SD card.

The overall results are quite good even with a slow sd card so I've decided to try to write the steps to install Ubuntu 10.4 on an sd card for T101MT.

As I did not wanted to kidnap this thread I started a new one [here]("http://ubuntuforums.org/showthread.php?p=9382954").

My idea is to keep updating the post once I solve the minor issues I got now and also to see if other people have other ideas about optimizing for sd card on the T101MT.

If any of you is interested in the topic I would be very glad to hear about it.

---

### Post by therightuser on 2010-05-30
I wanted to use the multi touch to read pdf books on Adobe Reader (zoom in, zoom out with two fingers), but with no good results, is there any tweak to allow this. Best regards

---

### Post by beastrace91 on 2010-05-30
I have my touch screen working now and I see we have multi-touch drivers! Are there any multi-touch applications people can recommend that I can utilize this feature in? It does not appear to work in Xournal or MyPaint...

~Jeff

---

### Post by beastrace91 on 2010-05-30
Also - about the camera... It was upside in Cheese so I applied the fix you provide and now it is correct under Cheese, but it is upside down in skype! Any suggestions on this one?

~Jeff

---

### Post by riccardo.depalo on 2010-05-30
@beastrace91: maybe you missed this

> **Plippo said:**
> The problem is that skype uses its own version of the video library, not the modified one. You should be able to fix this by calling skype using the following command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
You can change the entry in the menu to use this command so you don't have to type it every time.

@therightuser: the daemon Plippo provided worked for me with pdf documents using ubuntu's default gnome document viewer

---

### Post by therightuser on 2010-05-30
thank you [riccardo.depalo]("http://ubuntuforums.org/member.php?u=1058842") for your answer, i`ll try it later.
Best regards.

I`m loving Ubuntu 10.04 on a SD Card

---

### Post by beastrace91 on 2010-05-30
> **riccardo.depalo said:**
> @beastrace91: maybe you missed this

Ahh! I had missed this, thanks!

~Jeff

---

### Post by tlimsisnw on 2010-05-30
@Riccardo: I tried Plippo's fix on skype in terminal and it worked. However, when I put it in the menu, clicking on skype icon doesn't launch. How to resolve this?

---

### Post by riccardo.depalo on 2010-05-31
hallo tlimsisnw
I made a file called skype.sh in the home directory,
putting on the terminal: sudo gedit skype.sh
I wrote in it the following line:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

then I put in the menu, in the command line:

sh skype.sh

so when you click on the menu, the program starts
it worked for me very well

---

### Post by tlimsisnw on 2010-05-31
@Riccardo: Thanks for all your help to get the camera right-side-up and the microphone working in Skype. My Skype is finally working properly.

---

### Post by sleytr on 2010-06-01
Thank you all (specially to Plippo) for everything. With your work, my t101mt is now much better than when it comes from asus. 

I want to share a little finding; Opera Software released Opera Mobile's developer version for Linux, Mac and Windows. Though _currently_ it doesn't support flash, Its awesome onscreen keyboard and perfect UI makes it a wonderful web browser for tablet pcs. 


[http://www.opera.com/developer/tools/](http://www.opera.com/developer/tools/)
[http://get.opera.com/pub/.custom/campaign/labs/20100421/OperaMobileLinux_35.deb](http://get.opera.com/pub/.custom/campaign/labs/20100421/OperaMobileLinux_35.deb)

Note to Plippo: I've the same high cpu usage issues with twofing daemon. As a workaround I'm thinking about writting a little script that watches the cpu usage of X/twofing process and than sending a  HUP signal to twofing. What you think? Is this works or are you have any clues about solution of this bug?

Thanks again

---

### Post by hanoc on 2010-06-01
that's exactly the kind of keyboard I was looking for. It's such a shame that opera is not Free software.
I am also aware that one of the things that opera does great is resizing the available window space when the keyboard is out and that this is easy for an application to do with it's own space and quite difficult for the whole operating system to accomplish. Anyway that keyboard broke my heart.

BTW I'm having some trouble installing ubuntu on an sd card I know some of you in this thread did that if any of you[ know how to help]("ubuntuforums.org/showthread.php?t=1499015") I would be grateful.

---

### Post by therightuser on 2010-06-01
Hello everyone, i`m liking very much to work with Ubuntu 10.04. I`m having problem with the sleep/hibernate, after coming back from sleep/hibernate, touch screen dosen`t work, can anybody help me.
Somebody redirect-me to a single post, but i need detailed explanation. I´m new to this.

Best regards

Keep up the good work

---

### Post by tlimsisnw on 2010-06-01
@therightuser: I also found a similar problem with the touchscreen coming back from suspend: with the screen in portrait mode, when resuming from suspend, the touchscreen is out of calibration, need to rotate the screen back to landscape, then back to portrait for the calibration to be rectified. Also, onboard sometimes disappears after returning from suspend so I can't use it to enter the password from the screen. Seems like the screen is somewhat displaced vertically after return from suspend, but this corrects itself after rotating the screen one round.

@Plippo: In addition to the above, I also found that pressing the screen-rotate button (linked to touchrotate.sh) sometimes rotates the screen twice, even with very careful single press. Possible bug somewhere? 

@sleytr: Thanks for the Opera link. Love the fluid single touch scrolling and nice keyboard. Wish that onboard were as good.

---

### Post by Plippo on 2010-06-02
@sleytr: Well, it could be a fix, but of course not a true solution for the problem. Normally the daemon should be completely idle while you're not touching the screen - if it's not, it's a bug I have to fix in the daemon.

@therightuser: Are you using the T101MT or a different touch screen? If you have the T101MT, just follow the instructions in the [first post]("http://ubuntuforums.org/showpost.php?p=9210836&postcount=1") of this thread to install the current version of the driver (or re-install if you're already using it), than the touch screen should automatically work after suspend.

@tlimsisnw: Yes, the rotation problem also occurs for me sometimes. I'll try out a little workaround to prevent this and post it if it works. The better solution would be the one provided by chavi earlier in this thread, but currently that doesn't work correctly for me.

---

### Post by riccardo.depalo on 2010-06-02
@Plippo: I still have problems of crashes with ubuntu. Usually it happens when I have a browser opened, with twofing loaded and I click on the password for update-manager or synaptic. I still can open a shell with crtl-alt f2 and reboot this way. Maybe a bug with keyring and twofing together?

---

### Post by sleytr on 2010-06-02
> **Plippo said:**
> 
@therightuser: Are you using the T101MT or a different touch screen? If you have the T101MT, just follow the instructions in the [first post]("http://ubuntuforums.org/showpost.php?p=9210836&postcount=1") of this thread to install the current version of the driver (or re-install if you're already using it), than the touch screen should automatically work after suspend.


I'm having the same problem with the latest driver and script. Touch screen is working but goes out of calibration. I have to run same rotation command again to fix it. In other words, if I'm working in "touchrotate.sh left" mode, I have to run same command again after resuming from suspend.

---

### Post by Hangman228 on 2010-06-02
@Plippo : Do you know why the right clic is on the middle of the two finger ? It would be better is it's on the second finger

---

### Post by chavi on 2010-06-02
@plippo: ¿not works the little notify program? . It's working perfectly for me... may be little differences between Debian Squeeze and Ubuntu?. ¿What is not working exactly?.
The only thing is that the program must be launched with 'twoclicks' parameter because the rotate key sends two acpi events, one for push and one for release, or maybe the acpi message is different in Ubuntu....

I have a new version (is exactly the same thing) that eliminate the gtk builder GUI and the notification scripts. I would like to know the problems.

Thank you very much.

[ATTACH]159139[/ATTACH]

[ATTACH]159140[/ATTACH]

---

### Post by therightuser on 2010-06-03
@Plippo: i`m using a Eee PC T101MT, i reinstaled all the drivers, but no results, after suspending mode, my touchscreen dosen`t work, if everyone have a fix for this, it would be great. I think you have a single post, that speaks about this thread, but because of my poor experience, i didn`t have the skill to make it work. 

Best regards

---

### Post by Plippo on 2010-06-04
@therightuser: Is there a file /etc/pm/sleep.d/80_egalax_touchscreen on your system?

@chavi: I looked at the problems I had again and I could solve two:

The first problem was that the ACPI script didn't work in Ubuntu but I could make it work by changing your /etc/acpi/events/event-rotate and changing the "event" line to
event=hotkey ATKD 0000001a

The second problem is that when I now press the rotate button, the screen saver still comes up. This can be solved by adding a dummy action for the button with the Gnome shortcut manager, but of course this is not an ideal solution.

The third problem is that every time I rotate the screen with your utility, a new xrandr <defunct> Zombie process appears in the process list that can't be killed. I don't know if this has any further negative effects.

By the way, when I rotate the screen in Ubuntu (with your utility or manually using my script) graphics performance get really slow (e.g. scrolling in Firefox lags a lot). How is this in Debian?

---

### Post by Plippo on 2010-06-04
@Hangman228: The click point is between your two fingers because I thought it is best that way as I normally put both fingers on the screen at the same time, so there's no real »second« finger for me. But if you'd like it better the other way, I can maybe add an option for that.

@sleytr: Yes, currently the calibration information gets lost when you suspend while the screen is rotated. I'll look into that.

@sleytr, minhato: It seems that when you're not using compiz, the twofing daemon will lock up as soon as you open a new window. I'll look into this, too.

---

### Post by Plippo on 2010-06-04
I've created a new version (0.0.2) of twofing which should solve the problem of getting 100% CPU usage when not using compiz. You find it attached to [this post]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77"). Please report if it works for you.

---

### Post by riccardo.depalo on 2010-06-04
@Plippo: it seems the new version of your daemon works nicely like the previous one, though with some problems. I was using compiz, so didn't have any problem for that, but I noticed that system always hanged when I used an application that launched gksu (as I saw in the debug) and asked me for the password. Now I tried again to click on update-manager. Once it worked as it should, the second time the system crashed again and I had to reboot with ctrl-alt-F2. Maybe we should blacklist also the application "gksu" in "profile.h" file? I tried to do it and recompile but it didn't work.
Thank you for your work, I appreciated it a lot.

---

### Post by Plippo on 2010-06-04
I've created a package for the touchrotate script. You can download it here: [http://www.philmerk.de/dwl/deb/touchrotate-0.0.1-1.deb](http://www.philmerk.de/dwl/deb/touchrotate-0.0.1-1.deb)

It puts the script in /usr/bin, so when you have installed the package, you can call the script by simply calling
```
touchrotate toright
```(or your preferred direction). After you have install this package, the touch screen should now also stay calibrated when you suspend your device while the screen is rotated.

You can also achieve this manually: If you find at any time that the orientation of the touch screen doesn't match the orientation of the display, simply call
```
touchrotate current
```And it automatically makes the touch screen match the display.

---

### Post by therightuser on 2010-06-04
to plippo - i don`t have a a file /etc/pm/sleep.d/80_egalax_touchscreen . How do i get one?

Best regards

---

### Post by therightuser on 2010-06-04
sorry, i just found it, but the touchscreen is dead after hibernate or suspend

why?

---

### Post by therightuser on 2010-06-04
i already have installed twofing 0.1, to install the new version (twofing 0.2), do i have to erase the old one. sorry for so much questions.

best regards

---

### Post by riccardo.depalo on 2010-06-05
@Plippo: it seems that my gksu hanging problem is not related with twofing daemon. Crashes in fact occur also when daemon is not enabled. I have to find out why.

---

### Post by Plippo on 2010-06-05
@therightuser: That is strange. Does the screen work again when you manually call
```

sudo rmmod hid_egalax
sudo modprobe hid_egalax

```
after resume?

To install the new version of twofing, just unpack it and call
```

make
sudo make install

```
again. You don't need to uninstall the old version.

@riccardo.depalo:
You can try to go to System › Settings › Assistive Technologies and there enable the setting **Password dialogs as normal windows**.

---

### Post by riccardo.depalo on 2010-06-05
@Plippo, thanks for the hint, it worked but... in reverse. I had already enabled password dialog as normal windows. Instead, deselecting it, it seems that update-manager doesn't hang anymore.

---

### Post by chavi on 2010-06-06
@Plippo: 
* Yes, I was thinking that the acpi key code would be changed in Debian to Ubuntu. 

* The screen saver problem is worst in Debian. I can't change the screen saver lock behaviour of the rotate key. If I change the lock screen shortcut, the screen locks with the shortcut, but also whith rotate button!!!. The only fix is deactivate lock screen in the gconf key /desktop/gnome/lockdown/disable_lock_screen.  I think that it is a Gnome related problem.

* The xrandr <defunct> problem, it was not important, but it's fixed in this new version.

* Do screen rotation in my T101MT make slow performance, but not too much. The scrolling is functional, by example. The compiz's cube rotation is slowest. I think that it's a video driver problem, and I am running an vanilla kernel 2.6.33-4 compiled for atom architecture. I am getting random kernel failures, but continues working... 
I am waiting for an official Debian kernel actualization :(

Thank you very much for the feedback, and the new version goes here:
[ATTACH]159555[/ATTACH]

[ATTACH]159560[/ATTACH]

P.D. : Remember to change event_rotate file....

---

### Post by chavi on 2010-06-06
I'm working in a button tool bars that will be activated by the rotate key. This tool bars are designed with xml files, and can fire compiz effects. Here there are an video example:

[http://www.youtube.com/watch?v=bOLRDU32Vrg](http://www.youtube.com/watch?v=bOLRDU32Vrg)

When the package is installed, no xml menus are installed, and it works exactly as the previous grotate utility. If a menu.xml is present in $HOME/.gkeymanager or in /etc/gkeymanager/xml then the first chance is launch the menu bar. In /usr/share/doc/gkeyrotate there are a explain README. There are also, various xml menu files examples.

If you have the grotate utility installed it must be purged before the installation of gkeymanager.

I hope that it will be useful. (don't forget change the acpi event_rotate code to fit your system acpi code for rotate key).

[ATTACH]159781[/ATTACH]

[ATTACH]159782[/ATTACH]

P.D. Someone get touch screen working with xbmc full screen?

---

### Post by sleytr on 2010-06-07
@Plippo
Thanks for the fixes; twofing daemon working well and new rotate script remembering the calibration after resume.

@chavi
Button bar looks exciting, its exactly the tool that I'm looking for, will try asap. Thank you.

---

### Post by Plippo on 2010-06-07
@chavi
I really love your gkeymanager tool, it's amazing!

I had to install it from source as the deb package seems to be broken (only has 45 bytes for me) but I could install it from the source package after I had installed libxdo1 from Debian Squid (it's not included in Ubuntu). After I changed the ACPI event file, everything works great (except that I'll have to adapt some keys to my Compiz settings in the xml files).

Thanks very much for this great tool! One improvement though I'd love is if there was an option to turn off the icon in the notification area as I like to keep this area as clean as possible and everything is accessible with the rotation button.

---

### Post by chavi on 2010-06-07
Sorry for the erroneus .deb file submitted before. I attach a new version with a possible extra parameter ('showtray'). If this parameter is not specified, the program not shows the systray icon anymore, and, if you wish that systray icon shows, you must specify 'showtray' in the program launch.

I didn't know that libxdo1 are not packaged for Ubuntu, and i think that is not very much difficult change libxdo for direct XTestFakeKeyEvent calls...  (the related file is only sendkey.c). I think that libxdo is a great library, and ... well, if it's important may be i will make the change (some day).

[ATTACH]159674[/ATTACH]

[ATTACH]159780[/ATTACH]

---

### Post by mrspacklecrisp on 2010-06-07
@Plippo: I think you mentioned earlier the issue of the toolbar becoming crowded when the screen is sideways- I think this issue is actually solved with Chavi's utility. A person could make space on their toolbar by removing things they could write into the utility, such as shut downs.

Well, come to think of it.... Another option for the crowding thing is adding a side toolbar that has "autohide" turned on. It just sound like an annoying thing to accidentally run into with one's mouse.

@Chavi: Muchas gracias. Su utilidad parece ser tan chido. Seria muy util, al menos para mi. Buen trabajo!

@Everybody:
Small detail #1 Those brushes that don't work in the ALTERED version of Mypaint can be fixed by changing a couple minor settings, but it has to be done for each broken brush so I'm going to fix the set of preconfigured brushes and get back to y'all with the replacement directory.

Small detail #2 If anybody wants to use the awesome Nintendo64 emulator Mupen64Plus in Lucid on the T101MT, you have to get the graphics driver "Glide64". However, audio is skippy, though to be fair I haven't looked for a replacement.

---

### Post by riccardo.depalo on 2010-06-08
@Chavi: quite a nice and useful application, thank you for creating it! I still have to personalize it a little with my compiz effects, but I find it quite interesting. The full screen application is very useful, for example, to avoid using keyboard to press f11.

---

### Post by therightuser on 2010-06-08
Plippo: the lines you said to me to write doesn't work, the first one gives me an error, saying that it is already running, the second one, nothing happends.

---

### Post by ofisette on 2010-06-09
Does anyone have an x86_64 binary of the egalax-multitouch driver? I did a 64 bits install on my T101MT, and I find the ENAC's compilation instructions difficult to follow.

Thanks in advance to anyone who can help me!

Olivier

---

### Post by mrspacklecrisp on 2010-06-09
Obviously I'm much too dumb for this.... There is a way to just go to  /usr/share/mypaint/brushes and replace the lines "slow_tracking *" and  "slow_tracking_per_dab *" to be "slow_tracking 0.0" and  "slow_tracking_per_dab 0.0" with sed, but when I do it with the command  ```
sed -i 's/original line */new line 0.0/g' *.myb
``` it leaves  the old number value next to the new line. I don't know. Other than that, a person can simply edit those brush settings for each brush they come across that makes ghost lines. Don't think you can fix each by hand, though, there are something like 300 brushes.

There might be a device issue with pidgin/empathy, i.e. the camera. Not entirely sure.

I'm psyched about gkeymanager. I'm ready to write a tool for it that pops up random pictures of my boyfriend. :biggrin:

 Linux has become a wonderful alternative to Windows 7 on this machine. I'm very impressed with all that -if I could really be counted as a contributor at all- we've accomplished. I get a lot of attention for this computer: "Really, the software is free?", "You drew that on this screen? Wow!", "You're taking notes?", "You can use Skype and everything?", "That's awesome!" Good job, everybody.

---

### Post by riccardo.depalo on 2010-06-09
@Ofisette: did you already try the deb files provided by Plippo in the first page of this thread? I also have a i686 system and it worked. Don't do it, instead, if you read when you launch gdeb that not all dependencies are accomplished.

@mrspaklecrisp: did you try to change values as a superuser, using command sudo nautilus or sudo gedit? it should work.

did anyone find a way to launch setpci command for full brightness on boot? I used /etc/rc.local but it doesn't work and I have to apply it at each boot.

---

### Post by mrspacklecrisp on 2010-06-09
@riccardo:
I can edit them as root individually and it works, but who wants to fix over 300 files when a couple bash commands could do it? The problem is that wildcard values aren't catching the original, varied values for these settings. 
If I had these values in each of three files:

red 89
red 23
red 65

and I ran sed -i 's/red */red 00/g'
I'd get

red 0089
red 0023
red 0065

As for you:
So as I understand it, you sudo gedit rc.local, add setpci -s 00:02.0 f4.b=ff before exit 0, restart the computer, find that your screen is brighter, and then find that rc.local no longer has setpci and your screen dims upon next boot? Is that exactly what's happening?

---

### Post by riccardo.depalo on 2010-06-09
@mrspacklecrisp: no, the problem is that in /etc/rc.local I wrote exactly setpci -s 00:02.0 f4.b=f above the last line, and it remains written in that file, but i dont' get any more brightness that way. Only with terminal, with sudo and the same command, I get more brightness. I wrote a script as a boot application, but I have to give the password twice every time I turn on the pc. Strange, isn't it?

---

### Post by ofisette on 2010-06-09
[QUOTE=riccardo.depalo;9435344]@Ofisette: did you already try the deb files provided by Plippo in the first page of this thread? I also have a i686 system and it worked. Don't do it, instead, if you read when you launch gdeb that not all dependencies are accomplished.

Thanks, but I installed an x86-64 system (or amd64, if you prefer), not an i686 one. The drivers provided by Plippo are 32 bits and will not work with my system.

---

### Post by mrspacklecrisp on 2010-06-09
@riccardo:

Does anything happen when you do sudo /etc/rc.local?

Or this, an idea from the user lamego:
> To be sure rc.local is being called just append to it a line for  debugging:
```
echo $(date) - Running >> /var/test.run 
```Reboot and check /var/test.run

To check your scripts errors just use:
  ```
 /path/to/script > /var/myscript.log 2>&1 
```

That came from this thread. [http://ubuntuforums.org/showthread.php?t=371948](http://ubuntuforums.org/showthread.php?t=371948)

---

### Post by riccardo.depalo on 2010-06-10
@mrspacklecrisp: no, it only happens that system doesn't find touchkitusb driver, that I think is the firmware driver I uninstalled when Plippo provided enac's one, but was not erased from this file. I tried also to put the script you told me in it, but it doesn't create any log file. Thank you anyway.

---

### Post by mrspacklecrisp on 2010-06-10
I'm sorry I couldn't help. Perhaps you should start a thread for the subject.

---

### Post by Plippo on 2010-06-10
@riccardo:
If you have added the line to the end of /etc/rc.local, maybe there is a line before that reads **exit 0**? You have to add the pci line before the **exit 0** line. Otherwise, you could simply post your rc.local file so we can see if there's something wrong with it.

@ofisette:
Unfortunately, as I'm using 32 bit, I can only build the drivers for 32 bit. But I have written a semi-automated script that I'm using to automate building the packages, so if you like I can send it to you and give you instructions how to use it, then you should be able to build 64 bit module packages. If it works, it would be really nice if you could upload those packages (or send them to me so I can upload it) so I could link them in the first post for other 64 bit users.

@mrspacklecrisp: You could try the following command:
```
sed -i 's/original line .*/new line 0.0/g' *.myb
```sed uses extended regular expressions, so the * does not mean "everything". Instead, you have to use .* The . means "every character" and the * means "any number of times"

---

### Post by tlimsisnw on 2010-06-10
@Plippo: Ahh! Calibrator messed up again. With the screen in rotate to right mode, I tried to calibrate the touch screen to get more accuracy. However, each time after calibration, the pointer becomes more offset to the right. I kept trying to calibrate and it keeps moving to the right. May be a bug in calibrator? Now I can only use the touchpad. :(

---

### Post by ofisette on 2010-06-10
@Plippo That would be great! I will upload the packages to this thread as soon as I manage to compile the driver. If you prefer to use mail for sending the instructions, you can reach me at ofisette at gmail.com.

---

### Post by Th3Blaze on 2010-06-10
Sorry, I have just come to this last page straight away.
What does this guy want?

Can anyone help me?
[http://ubuntuforums.org/showthread.php?t=1506503](http://ubuntuforums.org/showthread.php?t=1506503)
It needs to be done and I'm sure you're all smart enoguh to help me, do someone a favour and make someone's day.

Wouldn't that make you smile?

---

### Post by riccardo.depalo on 2010-06-10
@Plippo: no, of course I put the setpci command before the last line exit 0. This is the content of /etc/rc.local:
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
## eGalax Touch kernel module section begin ##
   rmmod touchkitusb
   # This module may be renamed &#8220;usbtouchscreen&#8221;.
   insmod /lib/modules/tkusb.ko
   # for Kernel 2.6.x only.
## eGalax Touch kernel module section end ##
setpci -s 00:02.0 f4.b=ff
exit 0

---

### Post by Hangman228 on 2010-06-10
@Plippo : It's enough difficult for me to be precise with one finger, so with two... It would be very great for me to have this option to choose between the middle or the second finger. Maybe it's not to difficult to change this in your source file (I didn't know much about programming ^^) ?

You also said that the lag problem when you rotate the screen came from the driver. I tried the last one 2.11 but it's the same problem...

---

### Post by Hangman228 on 2010-06-10
I didn't manage to install chavi's program gkeymanager. What I have to do ?

---

### Post by chavi on 2010-06-10
@Hangman228: You must:

a) uncompress the deb package: tar -xvzf gkeymanager_0.1-1.1_i386.deb.tar.gz

b) install the package: dpkg -i gkeymanager_0.1-1.1_i386.deb

c) In /usr/share/doc/gkeymanager are a README file with the instructions, but resuming:

1.- add gkeymanager twoclicks to gnome startup session programs (System->Preferences->startup applications (or similar, i have an spanish system)).

2.- create your toolbars in $HOME/.gkeymanager (or copy the files in /usr/share/doc/gkeymanager/xml/)

3.- Adjust the compiz shortcuts to match the menus or viceversa.

I hope that this help.

---

### Post by mrspacklecrisp on 2010-06-10
@Th3blaze: Uh, not so sure how relevant that conversation is. Does this have to do with a T101MT?

@Hangman: For me, I had to edit /etc/gkeymanager. I don't have a .gkeymanager in my home directory. For whatever reason, gkeymanager has actually been failing me. I had it set as a startup program, but after the first time it won't start. I have tried running it in terminal, but lately it's been freezing up and making everything slow, then flat out quitting. It's a shame, I really like it....

I'm not sure if this has to do with the machine, but I've been experiencing problems with voice and video calls to google talk users. If anyone else is having or has had similar issues on this computer, this is the thread I started: [http://ubuntuforums.org/showthread.php?p=9439040#post9439040](http://ubuntuforums.org/showthread.php?p=9439040#post9439040)

---

### Post by riccardo.depalo on 2010-06-10
It seems I solved the /etc/rc.local. I had to to delete the line "rmmod touchkitusb" which gave an error message. Easier than I thought.

---

### Post by Airelle on 2010-06-10
> **Plippo said:**
> @riccardo:
@ofisette:
Unfortunately, as I'm using 32 bit, I can only build the drivers for 32 bit. But I have written a semi-automated script that I'm using to automate building the packages, so if you like I can send it to you and give you instructions how to use it, then you should be able to build 64 bit module packages. If it works, it would be really nice if you could upload those packages (or send them to me so I can upload it) so I could link them in the first post for other 64 bit users.


You should actually be able to cross compile from 32 to 64 bits using (and linking against) gcc-multilib/g++multilib and using the -m64 flag. See for example here: [http://ubuntuforums.org/showthread.php?t=1377396](http://ubuntuforums.org/showthread.php?t=1377396)

---

### Post by chavi on 2010-06-10
@mrspacklecrisp: extrange. The program it has not been much tested,  (i actually don't work with the T101MT) but i will see what happens. I didn't saw slow performance... 

Well, i will see and i will comment....

---

### Post by mrspacklecrisp on 2010-06-10
> **riccardo.depalo said:**
> It seems I solved the /etc/rc.local. I had to to delete the line "rmmod touchkitusb" which gave an error message. Easier than I thought.

When did it give you an error message? Maybe rc.local is run too early, and it might be possible to fix it by putting in a sleep command.

Anyway, I'm very happy for you. The screen brightness is one of the more annoying errors.

---

### Post by tlimsisnw on 2010-06-10
Hi, has anyone else encountered the problem of not being able to calibrate the touch screen I posted to Plippo yesterday? Would appreciate if anyone has a solution to this.

---

### Post by riccardo.depalo on 2010-06-11
@Tlimsisnw: you can try this hint by Plippo in the first thread [http://ubuntuforums.org/showthread.php?t=1442164&page=5:](http://ubuntuforums.org/showthread.php?t=1442164&page=5:)

> You can try to calibrate it manually by executing the command (without sudo)
Code:
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
The values here are for my screen, so maybe your calibration is a bit off after executing the command, but at least you should be able to use the screen. If that works, you can try to start the calibration again. You can also try to start the calibration from the terminal with
Code:
sudo egalax_calibrator_x11


@mrspacklecrisp: I had an error message when I tried on terminal: sudo sh /etc/rc.local
I think it is a script that remained written when I tried EETI firmware, but uninstalled it.

---

### Post by tlimsisnw on 2010-06-11
@Riccardo: Many thanks. Your calibration works very nicely for my screen. It is spot on in the middle of the screen (in landscape mode), offset by about 3mm to the left on the left-edge, and offset by about 3mm to the right on the right edge. Top and bottom edges seems ok. At least I can use the touch panel again.

@Plippo: May be there's a bit of mismatch in the horizontal length of the touch panel and the horizontal length of the screen? How can we check or change that?

---

### Post by Plippo on 2010-06-11
@tlimsisnw: Unfortunately it is generally not possible to calibrate when the screen is rotated. I guess the correct calibration is different on different machines, I don't think there is a general solution for that.

@Airelle: Thanks for the link, I'll look into that.

---

### Post by Hangman228 on 2010-06-11
@chavi : I did all the tings but it's not working.

First of all, there is no .gkeymanager in home folder. I created it and copy usr/share/doc/gkeymanager/xml/ in it.

Program don't launch, I added 'gkeymanager twoclicks' (without quotes) to startup program I reboot and nothing happen.

When I type gkeymanager or gkeymanager twoclicks in a console, nothing happen, it's seem to be lock...

Do you have a verbose or a debug mode to see what happen ?

---

### Post by riccardo.depalo on 2010-06-11
@hangman: I had it working installing the deb file, then creating a directory .gkeymanager in the home directory. I copied from the source package in this directory all xml files. Then I  created inside /home/yourname/.gkeymanager a directory called icons and put in them all icons that are in the source package. Then, to launch it, call from terminal (or put in the menu): gkeymanager showtray. You will see a small icon up on the panel. Click and enjoy.

@tlimsisnw: you better thank Plippo, who created the package and the workaround

---

### Post by tlimsisnw on 2010-06-11
@Plippo: Thanks for the calibrator work around and advice. Yes, I must remember not to calibrate when rotated.

---

### Post by chavi on 2010-06-11
@mrspacklecrisp: Thank you for the advice, the file findproc.c had a misplaced close statement, a silly bug :/ .  In other side, i don't find any slow performance....

The new files:
[ATTACH]160075[/ATTACH]

[ATTACH]160076[/ATTACH]


@Hangman228:  The program only listen for a acpi key code, the code must be in /etc/acpi/events/event-rotate, and the toolbars shows when the key is pressed. In the T101MT i think that the better key code is the screen rotate button, but in my Debian is a different code that in Ubuntu. There are a Plippo post that shows that code, or you can execute in console acpid -d and push the key.
Of course, if the tray icon is showed you can click on it too and remember twoclicks parameter for rotate screen button.

---

### Post by Plippo on 2010-06-12
@ofisette: I'm so sorry about the delay, but I was so busy the last days. But now here is everything you should need to build the Kernel driver. I've modified my script a bit so now it should be completely automatic. 

First download the archive [http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz](http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz) and uncompress it in any directory, e.g. your home directory.

Then you have to install the packages build-essential, fakeroot, linux-headers-generic and linux-source. 

To build the driver, open a terminal and go to the directory you uncompressed, which should have the name t101mt-kernel-driver.

Inside this directory, just call ```
./build.sh
```You should be asked to enter your password, then everything should work automatically. Afterwards, you should find a package called egalax-multitouch-driver-xx-generic-amd64.deb in this drive, which you can install by double clicking on it or with dpkg.

I hope it works for you, if not, please tell me.

---

### Post by riccardo.depalo on 2010-06-12
@Plippo: is it possible to use this driver also for next ubuntu kernel upgrade with an average i686 system? Would it work only with 2.6.32 kernel? (thank you again for your work)

everybody: did you know that Canonical is developing an ubuntu version for tablet pc like (I imagine) our t101mt? it would be an interesting development.
> Were Ubuntu Linux ported to any device you could name, it wouldn't be much of a surprise, but developer Canonical intends to release a tablet-specific branch of the OS this time.

[http://www.engadget.com/2010/06/11/canonical-making-full-fledged-ubuntu-tablet-push-in-early-2011/](http://www.engadget.com/2010/06/11/canonical-making-full-fledged-ubuntu-tablet-push-in-early-2011/)

---

### Post by chavi on 2010-06-12
@riccardo: I'm using this driver with a 2.6.34 vanilla kernel, therefore i suppose that it will work in any new kernel.

---

### Post by atomp on 2010-06-12
I've got some feedback for the twofing daemon.

I have found that it can have odd behaviour when used with onBoard in that it will not lock the "alt", "shift" or similar keys on as it should. I have also found that the odd behaviour can also occur in normal use, sometimes registering a right click, sometimes a double, but it is most notable with onBoard's "alt", "shift" or similar key behaviour.

I have found this in both versions of twofing and can confirm that it is twofing that is the cause as killing the daemon stops the problem (and unfortunately as well as the awesome goodness that twofing allows).

Once again cheers for all your hard work with this and the drivers, it's massively appreciated.

---

### Post by hanoc on 2010-06-13
Hi,

When I try to install gkeymanager (downloaded from above) I get the warning:
Dependency is not satisfiable: libxdo1 (>= 1:1.20100227.2679)

I tried to install libxdo1 from [here]("http://packages.debian.org/unstable/libs/libxdo1") but it asked for libxdo2.
I downloaded and installed libxdo2 from [here]("http://packages.debian.org/sid/i386/libxdo2/download").
Then tried to install libxdo1 again. I do not remember if, at that time, it installed or said that it was already installed but it says libxdo1 is installed now yet, when I try to install gkeymanager I get the dependency error still.

I don't know why i having more trouble than average with that.

I am using ubuntu 10.04 and I don't know what other information could be relevant.

Am I downloading the correct libxdos?


Additionally since I installed libxdo the two finger scroll on the trackpad makes the cursor jump like crazy but I'm not sure if the issue is related.

Any tips? 

Thanks!

---

### Post by Plippo on 2010-06-13
@hanoc:
Cursor jumping occurs when you have booted Windows and then reboot into Linux. Shutting down after using windows and turning the Eee PC on again instead solves this problem.

---

### Post by chavi on 2010-06-13
@hanoc: I'm sorry. I have a Debian squeeze system, and libxdo1 is in debian repository tree. I think that installing debian squeeze libxdo1 should be work....

I see that your actual installed package is an debian sid's package, perhaps squeeze it's different. You can uninstall actuall libxdo stuff and install squeeze's libxdo1. 

I hope that this work.

---

### Post by hanoc on 2010-06-13
@Plippo That was exactly the case. You discovered me *^^*

@chavi Sorry, I got a little confused with the different versions. I've added the squeeze repository and installed just libxdo1 from there using the familiar apt-get. Now it works.

Thanks!

---

### Post by ofisette on 2010-06-13
Here is an amd64 package of the egalax multitouch driver. Use it if you have installed a 64 bits system. All thanks go to Plippo for his build instructions and, of course, to the ENAC people who wrote the driver.

As an owner of the previous generation T91MT, I find the new touchscreen on the T101MT much more precise (once properly calibrated using the stylus).

@Plippo Thanks for your assistance. I am a new Ubuntu user (coming from Gentoo), and I am not familiar yet with patching kernel sources and building modules the Ubuntu way.

---

### Post by riccardo.depalo on 2010-06-14
@Plippo: I tried to build the egalax driver for the new 2.6.32-23 kernel, and I got a new deb file. But couldn't install if I didn't uninstall previous kernel driver. I uninstalled it, and installed the new one, but the driver didn't work, I didn't even have touchscreen working. Any idea?

---

### Post by Plippo on 2010-06-15
@riccardo.depalo:
This is strange. When you have installed the new package and then call
```

sudo rmmod hid_egalax
sudo modprobe hid_egalax

```
are there any errors? If not, are there any when you call
```
dmesg | tail
```
afterwards?

@ofisette:
Thanks for sharing the package!

---

### Post by riccardo.depalo on 2010-06-15
@Plippo: well, if I run the deb file without uninstalling the 2.6.32-22 one, I get this error message: (I'm translating from italian) tried overwrite "/etc/pm/sleep.d/80.egalax_touchscreen" which is also in egalax-multitouch-driver-2.6.32-22-generic
Then I try again to uninstall it and run it again without that previous deb file
I reboot, touchscreen doesn't work and I get the following error messages:

sudo rmmod hid_egalax
ERROR: Module hid_egalax does not exist in /proc/modules

sudo modprobe hid_egalax
WARNING: Error inserting usbhid (/lib/modules/2.6.32-23-generic/updates/hid-egalax/usbhid/usbhid.ko): Invalid module format
FATAL: Error inserting hid_egalax (/lib/modules/2.6.32-23-generic/updates/hid-egalax/hid-egalax.ko): Invalid module format


I tried also to force installing with the previous deb installed, but didn't solve the problem

this is what I got from ./build.sh in terminal:

BUILDING KERNEL MODULE...
hid.h is already fine.
hid-core.c is already fine.
hid-ids.h is already fine.
Makefile is already fine.
Building modules...
make: ingresso nella directory «/usr/src/linux-source-2.6.32»
  CC [M]  /usr/src/linux-source-2.6.32/drivers/hid/hid-egalax.o
  Building modules, stage 2.
  MODPOST 35 modules
  LD [M]  /usr/src/linux-source-2.6.32/drivers/hid/hid-egalax.ko
make: uscita dalla directory «/usr/src/linux-source-2.6.32»
Copying...
Should have built. Ready to build deb.
BUILDING DEB PACKAGE...
dpkg-deb: generazione del pacchetto "egalax-multitouch-driver-2.6.32-23-generic" in "deb.deb".
SHOULD BE FINISHED.

it seems it skipped building the driver, didn't it?
Anyway, the driver from the first page of this thread for 2.6.32-22 works very well

---

### Post by hanoc on 2010-06-15
@Chavi Hi, thanks for your script.
I am having some trouble getting it to work.
I think I have installed it corectly but I do not understand how do I have to launch it.

Could you explain further what acpi rotate means and what should that event do?

I followed the instructions here:
[http://ubuntuforums.org/showpost.php?p=9442044&postcount=158](http://ubuntuforums.org/showpost.php?p=9442044&postcount=158)
until point 3 wich lost me.
---- 

Si quieres puedes explicarmelo en castellano y lo traduzco para el thread. 
Puedes mandarme un privado o postearlas aqui. Estoy atento al hilo.
Mi inglés es bastante mejor que mis habilidades con linux :P

---

### Post by chavi on 2010-06-16
@riccardo: try as root:

depmod -a

and then 

modprobe hid_egalax

Perhaps after the module installation is needed an depmod -a ....

---

### Post by riccardo.depalo on 2010-06-16
@Chavi: thanks for the hint, but it seems that after sudo depmod -a I get the same error message as before. The strange thing is that, booting 2.6.32-22 kernel, touchscreen works very well. 
Muchas gracias. Creo que esta algo en el deb file que no funciona.

---

### Post by hanoc on 2010-06-16
Hi,

With some help from @Chavi I've been able to get the grotate menu to work so I'm going to write a step by step of what I did in case it can help somebody.

1. Install libxdo1 from debian squeeze for example downloading in deb form from here:
[http://packages.debian.org/squeeze/libxdo1](http://packages.debian.org/squeeze/libxdo1)

2. If not yet installed install acpi. For example by calling "sudo apt-get install acpi" (this was not installed by default in my UNR)

3. Install gkeymanager. Search from the last version in this same thread. The last right now is this:
[http://ubuntuforums.org/showpost.php?p=9446053&postcount=171](http://ubuntuforums.org/showpost.php?p=9446053&postcount=171)

4. At this moment you should have a file called /etc/acpi/grotatescreen.sh
Executing this should rotate the screen with a notification. This it's its default behavior.

5. To make that command it launch a menu by creating an xml file with it's instructions. There are examples of those xmls in /usr/share/doc/gkeymanager/xml/
gkeymanager will search for the xml's first in $HOME/.gekeymanager and then in /etc/gkeymanager/xml. In both cases the icons should be in ./icons/

6. To make the program start at boot put "gkeymanager twoclicks" in your startup program manager.
 
7. To make it run every time the rotate button is pressed the press of x86screenSaver has to be binded to the command /etc/acpi/grotatescreen.sh
7.1. In ubuntu with gnome you can use keyboard shorcuts under System  > Preferences > Keyboard Shortcuts.
7.2. With compiz bind the keypress to the action in /etc/acpi/events/event_rotate
I've never used compiz (and step 7.1 worked for me so I really did not proceed with 7.2) but I can say that executing acpi_listen and pressing the rotate button produces the following result for me:
```
hanoc@hanoc-t101mt:~$ acpi_listen
hotkey ATKD 0000001a 00000008
hotkey ATKD 0000001a 00000009
```
 
I got to this point with my system and it launches the example menu's. I have yet to test the following instructions, and see if I can use them without compiz or if I want to use compiz but I'll translate it verbatim from the instructions @chavi sent me.

The buttons are binded to compiz actions and the only thing they do is to simulate keypresses to activate this options. For this reason the actions in the buttons should be the same than compiz created actions.
Note: To be able to change the color of anything written with the compiz annotate plugin compiz should use gconf as a backend.
Note: At this moment the touchscreen  only detects one mouse button.

If you want I'll try to expand this post once I try the program and the menus further but it seems quite straightforward from here.

Thanks for your help @Chavi!

---

### Post by Plippo on 2010-06-16
@riccardo: The problem that happens when you install the deb comes from me being extremely stupid. I have put a file into the deb that should not be there. I'll upload a package later that fixes that, I'm so sorry.

The problem with the module itself seems to be that it indeed doesn't build the new version and instead puts the old one into the package which is installed then for the new Kernel. I will try to build it myself and post later if it worked for me and post the new package. One possibility I could think of is that your kernel source is of an older version. Sometimes the kernel source is uploaded to the repository at a different time than the pre-built kernel packages.

---

### Post by riccardo.depalo on 2010-06-16
@Plippo: danke für Ihre Hilfe, thank you for helping me and all of us in trying to use this hardware with linux and free software. It would be wonderful if we could build driver by ourselves, also the ones of us (like me) that are no software developer professionals. So I appreciated a lot your script, even if something didn't work. Of course Ubuntu developers should be aware that if they will include the driver in the kernel (I know StCh send a patch for it), it would be better not only for all of us, but also for Ubuntu.

---

### Post by Plippo on 2010-06-16
@riccardo: Prego! I think I have fixed the problem with the deb packages. You (and all others) find instructions below. For your problem building the new kernel, I think it should be enough to re-install the package linux-source-2.6.32 in synaptic.

[B]@all:
There has been a bug in the kernel driver package version 2.6.32-22 which would break updating to 2.6.32-23. If you have installed it before June 17 2010, please do the following:
[/B]
[LIST]
[*]**Uninstall the old package egalax-multitouch-driver-2.6.32-22-generic**
[*][B]Install the new package from here: [http://philmerk.de/dwl/deb/egalax-multitouch-driver-2.6.32-22-generic-i386.deb](http://philmerk.de/dwl/deb/egalax-multitouch-driver-2.6.32-22-generic-i386.deb)
[/B]
[*]**Install the new common package from here: [http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb](http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb)**
[/LIST]
[B]You don't have to reboot after doing this, it doesn't change anything in the driver, just fixes the package structure. I'm very sorry for your inconvenience!

If you are building the kernel package yourself using the script I provided, please download the new version from here: [http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz](http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz) and rebuild the driver package, then proceed as described above, just instead of downloading the i386 package install the one you've built yourself.[/B]

---

### Post by riccardo.depalo on 2010-06-16
@Plippo: Yes, it works! I followed your instructions and I could easily build the driver for 2.6.32-23 kernel, after reinstalling linux-source-2.6.32-23, and it worked very well. I didn't have to recalibrate, and twofing gestures work also like in the previous kernel. Thank you again.

---

### Post by beastrace91 on 2010-06-17
Just wanted to drop a comment that I installed your multi-touch package and it is working fantastically! Now all we need is a decent on-screen keyboard and this will be like a real tablet computer XD

~Jeff

---

### Post by tlimsisnw on 2010-06-17
@Plippo: Possible to implement a 3finger middle button click?

---

### Post by cH!cK3n on 2010-06-17
Hi,

I installed Ubuntu Remix and the driver-packages on my new T101MT and everything works fine.

For me, the most important application is Xournal, working fine as well. Unfortunately, every time I lay my hand on the screen while writing with the pen, Xournal draws lines from my hand to the pen. On Windows Asus PenWrite prevent this. I googled and searched threw the forum but didn't found anything referring to "Ubuntu" and "PenWrite". I suspect that there isn't any compareable software available for Ubuntu, isn't it?

Do you know if there is any software I can install allowing me to put my hand on the screen while writing? Or is there any workaround to fix this issue?

Thank you!

Best regards,
Nina

---

### Post by hanoc on 2010-06-17
Well, after trying for some days ubuntu on a sd card I formated everything and started from scratch.
Now I'm not being able to calibrate the screen. I don't know if I did anything different. I am using the *.22 kernel and the correct package for the egalax driver.

The output of the calibrator is the following:

```
DEBUG: XInputExtension version is 2.0
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Skipping device 'Virtual core XTEST pointer' id=4, does not report Absolute events.
DEBUG: Read axes swap value of 0.
Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=10
	current calibration values (from XInput): min_x=4110, max_x=4114 and min_y=4072, max_y=4072
DEBUG: Adding click 0 (X=1023, Y=0)
DEBUG: Not adding click 1 (X=1023, Y=0): within 7 pixels of previous click

```

Of course I am touching the second cross and it's not getting recognised.

Is there anything I could be missing that produces that error?

---

### Post by Plippo on 2010-06-17
@Jeff:
Your welcome, always good to know when it works. As an on-screen keyboard, have you tried CellWriter?

@tlimsisnw:
Unfortunately, the touchscreen hardware is only able to recognize two fingers at once.

@cH!cK3n:
Unfortunately, there is no such software at the moment. I once tried to extend the driver to provide this feature, but it didn't work out very well. I think the ASUS driver uses a quite sophisticated algorithm to distinguish between the hand and the pen.

@hanoc:
That's strange, the problem is that your "current calibration values" are false. The calibrator package actually should provide default calibration values, I don't know why they are not active on your machine. You can try to use the following command to set these default values and then run the calibrator again:
```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```

---

### Post by hanoc on 2010-06-17
@Plippo, thanks, it worked.

I don't know why this happened but I had a version of the driver and calibrator installed prior to the one I used. It was from before the 17th of this month but I uninstalled it and reinstalled as you instructed.

I'll paste the debug log in case it sheds some light to this, there is a strange segmentation fault at the end.

```
hanoc@hanoc-t101mt:~$ egalax_calibrator_x11 -v
DEBUG: XInputExtension version is 2.0
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Skipping device 'Virtual core XTEST pointer' id=4, does not report Absolute events.
DEBUG: Read axes swap value of 0.
Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=10
	current calibration values (from XInput): min_x=411, max_x=32557 and min_y=45, max_y=32517
DEBUG: Adding click 0 (X=119, Y=77)
DEBUG: Adding click 1 (X=893, Y=72)
DEBUG: Adding click 2 (X=117, Y=521)
DEBUG: Adding click 3 (X=902, Y=525)

Doing dynamic recalibration:
	Setting new calibration data: 37, 32663, 31, 32394
DEBUG: Succesfully applied axis calibration.
Segmentation fault

```

---

### Post by beastrace91 on 2010-06-17
> **Plippo said:**
> @Jeff:
Your welcome, always good to know when it works. As an on-screen keyboard, have you tried CellWriter?

I mean a touch screen keyboard designed for a *touch* screen - not for clicking with a mouse as cell writer is. Basically the type of on screen keyboard that touch screen smart phones have or the opera mobile emulator has. Ubuntu has nothing like that as of yet - hopefully this will change once we get the Ubuntu tablet edition into alpha/beta :D

~Jeff

---

### Post by waldwatz on 2010-06-18
> **Plippo said:**
> @Jeff:
Your welcome, always good to know when it works. As an on-screen keyboard, have you tried CellWriter?

@tlimsisnw:
Unfortunately, the touchscreen hardware is only able to recognize two fingers at once.

@cH!cK3n:
Unfortunately, there is no such software at the moment. I once tried to extend the driver to provide this feature, but it didn't work out very well. I think the ASUS driver uses a quite sophisticated algorithm to distinguish between the hand and the pen.

@hanoc:
That's strange, the problem is that your "current calibration values" are false. The calibrator package actually should provide default calibration values, I don't know why they are not active on your machine. You can try to use the following command to set these default values and then run the calibrator again:
```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```


Hi everybody - the last tip solved my problem; though not having everything tested yet no it seems to work. Thanks to all doing such a great work. btw: I'm using it on easyPeasy and had a little trouble to get it waork, which - I think - was mainly caused by myself having installed previously the eGalaxDriver 3.0 and not removing it correctly.
Thanks again - I will keep watching this forum and give any hint a newbie like me may be able to give

Kind regards from Frankfurt, Germany

---

### Post by riccardo.depalo on 2010-06-18
@Beastrace91 and all: did someone try this virtual keyboard called Florence?
[http://sourceforge.net/projects/florence/](http://sourceforge.net/projects/florence/)
It seems quite interesting: > Florence is an extensible scalable on-screen virtual keyboard for GNOME that stays out of your way when not needed. You need it if you can't use a real keyboard either because of a handicap, broken keyboard or tablet PC but you can use a pointing device

this is a screenshot

[IMG]http://sourceforge.net/dbimage.php?id=197265[/IMG]

Also this looks interesting:
[http://matchbox-project.org/](http://matchbox-project.org/)

---

### Post by beastrace91 on 2010-06-18
Florence is nice but it keeps seg faulting on me :-/ But it still is not quite what I am looking for. Matchbox is nifty but I really just want an on screen keyboard - not a whole Window manager. Still might give it a try though.

~Jeff

---

### Post by beastrace91 on 2010-06-18
Anyone know why multi-touch won't auto load at startup for me? Even when I add the command to my startup programs I still have to manually fire **twofing** in terminal for it to start working.

Any ideas?

~Jeff

---

### Post by riccardo.depalo on 2010-06-19
@Beastrace: I load at startup the command twofing --wait as suggested by Plippo and it works for me.

---

### Post by cH!cK3n on 2010-06-20
@riccardo.depalo: I tried florence. imho its the best onscreen-keyboard for ubuntu i tried yet. You can show/hide it with one click, can simply move it on the screen. Very nice. (I just changed the icon cause I don't like the original. ;))

---

### Post by SirAry on 2010-06-20
'a small hint about the multitouch and right mouse click:

you can choose in the mouse accessibility settings the following option, "Simulated Secondary Click", just adjust it all the way to the left and you can press+hold on your touchscreen to get the right-click context menus.'

Hello, after I did, it told me that Assistive Tech. are not enabled, and if I want to enable. I chosed enable and log-out, and after that, the touchscreen is working wrong. I sense move only on an axis (but i an not sure) and only on a little area of the screen. Of course, the cursor is in another area ...
I reverted to the initial state, tried to recalibrate but, nothing helped ... Ubuntu 10.04 updated (2.6.32-22)

Any idea? Thanks.

---

### Post by mrspacklecrisp on 2010-06-21
Update: **How to fix the microphone**
Don't bother with the tutorial, it's outdated. All one needs to do is _sudo apt-get install pavucontrol_, run pavucontrol, go to input settings, and click the speaker, lock, and check icons (unmute, unlock, and revert from fallback device status)

**How to fix all brushes in mypaint-resistive**

This.
  	 	 	 	 	```
sav@sav-netbook:~$ cd /usr/share/mypaint/brushes 
sav@sav-netbook:/usr/share/mypaint/brushes$ sudo sed -i 's/slow_tracking_per_dab .*/placeholder 0.0/g' *.myb 
[sudo] password for sav: 
sav@sav-netbook:/usr/share/mypaint/brushes$ sudo sed -i 's/slow_tracking .*/slow_tracking 0.0/g' *.myb 
sav@sav-netbook:/usr/share/mypaint/brushes$ sudo sed -i 's/placeholder .*/slow_tracking_per_dab 0.0/g' *.myb 
sav@sav-netbook:/usr/share/mypaint/brushes$ 

```

---

### Post by riccardo.depalo on 2010-06-21
@mrspacklecrisp: I tried mypaint with your fix for brushes: it's quite an amazing app, any artist would be happy to use it.

When I have time, I will try to collect all hints and make a little manual, a wiki opened for any suggestion, and share it. T101mt is a wonderful machine, and only with linux can be used in all its potential, but to make it work fully we have to follow a sort of guideline, to let other people use linux as primary OS. It would be useful to collect all hints from each of you of this forum, all hints that I found useful and working.

---

### Post by hanoc on 2010-06-22
You can count on my axe!

Sorry coudn't resist.

Now seriously @riccardo.depalo I think it's a great idea and I'll be very happy to collaborate on it. Where is the right place to host this?

I always got a little confused with: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) because of the sentence 
This is THE definitive place for members of the Ubuntu community to discuss ideas and store **team-related **information.

---

### Post by rosh1182 on 2010-06-22
What is the battery life like?

---

### Post by riccardo.depalo on 2010-06-22
@Hanoc: I just opened a page: [https://wiki.ubuntu.com/t101mt](https://wiki.ubuntu.com/t101mt)
it's still almost empty. Of course I would like to ask first Plippo if we can use his contributions in this thread and put the best of it in this wiki page. Just because there are some link to his web page. I hope it's the right way to open a wiki, it's the first time I do it with ubuntu ):P

---

### Post by Plippo on 2010-06-22
It's a great idea to share all the information in a wiki, but I think wiki.ubuntu.com is the wrong place for this as this wiki is more an internal wiki for the ubuntu teams. I guess the place to put it would be [https://help.ubuntu.com/community](https://help.ubuntu.com/community) - there are already pages for other laptops.

Of course you can also use all of my contributions as you like (otherwise I'll add them myself :-) ). We can put the files from my web space as attatchments to the wiki or leave them where they are, that's no problem for me. The number of users of Ubuntu on the T101MT currently is still small enough, the download traffic hasn't exploded yet :-)

---

### Post by riccardo.depalo on 2010-06-22
@Plippo: ok, I created this wiki page:

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

Look if everything is correct, you are the source of the most of it.

I have written in it some tutorial I found in the thread and some that I have integrated, anybody can help me getting it better!

@Chavi: I also put there your nice app, look if you want to change it or integrate it.

---

### Post by beastrace91 on 2010-06-22
Howdy,

So you had asked for suggestions on multi-touch applications - any idea if you could make [www.prezi.com](www.prezi.com) work as it does with Windows multi-touch under Ubuntu? Right now pitch zoom works on it, but not rotate.

Regards,
~Jeff

---

### Post by mrspacklecrisp on 2010-06-22
The wiki is a fantastic idea. Maybe the official Ubuntu team should be made aware of all this&#8212;It could be a model for future tablet support.

I keep running into problems with windows and programs being too big for the screen. What is the solution used for the UNR desktop mode?

In general, I can't seem to make video chat work. I know there is support in Skype, but it's the one program that malfunctions for the one person I care to talk to. I have tried Pidgin, Empathy, and the website "Tokbox" to connect to gtalk users, all with mixed and screwy results, often with the program freezing. I tried different mixes of gstreamer plugins, whatever solutions I could find really, but I can't for the life of me make this work. Anybody having similar problems?

---

### Post by riccardo.depalo on 2010-06-22
@mrspacklecrisp: have you tried to use kopete, for kde? it supports video chat, gtalk accounts. I tried it with t101mt and it seems to work. You can install it from normal repository.

---

### Post by fyra on 2010-06-22
Hi
I'm looking to buy one of these, and want to find out how well they perform with Ubuntu. This thread has been useful in many ways - I'm confident that the touch screen will do what I want, among other things.

One thing that doesn't seem to have been discussed here or elsewhere in the forum, is video playback on linux. How well, or not well, does the t101mt handle hd video? Endgadget says it stumbles, but that is with win7 hogging resources and cpu. I'm hoping that maybe a lighter OS will get it over the line.

(Essentially, I plan for my current laptop to stay in the house and handle playback, but I'm not confident that it wont die on me and leave me with nothing. If the t101mt could function in its place I'd have nothing to worry about and could go ahead and buy with a minimum of 'buyer's remorse')

---

### Post by beastrace91 on 2010-06-23
720p runs alright... 1080p don't even bother. It's a netbook, don't expect too much power.

And as always - flash on Linux is kinda a joke :-/

~Jeff

---

### Post by mrspacklecrisp on 2010-06-23
Yeah, the new libv4I does not work for me. Don't know why I didn't notice this much sooner. LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so guvcview produces the same upside-down capture when I simply run guvcview.

@riccardo.depalo: Thanks so much for the tip, I'll look into it tonight.

@fyra: You can't play HD youtube videos smoothly. However, I have downloaded HD youtube videos and they played perfectly, if that counts. I've watched movies and entire tv series, never had anything that came close to a hitch. I imagine that if there is slowdown for HD media, it's nothing that would hinder you. In my opinion, Win7 is useless on the machine. I don't know how anyone gets anything done with it; It's simply too big, slow, and prone to freezing for this computer.

I have to wonder, though: If you have a laptop, why buy the T101MT? You already have a portable computer. I'm a little confused by what you're saying. Are you looking to replace your computer entirely?

---

### Post by riccardo.depalo on 2010-06-23
@mrspacklecrisp: this is very strange. LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so works for me. I also put it in a sh file to launch it from the menu. Did you install correctly the workaround as explained in [http://ubuntuforums.org/showpost.php?p=9131720&postcount=37](http://ubuntuforums.org/showpost.php?p=9131720&postcount=37) ?

@all: the wiki page is quite complete. Add any tip if you wish.

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

---

### Post by SirAry on 2010-06-23
Hello, I am trying hard to join the club ...
I have some problems especially with the touchscreen. I hope i will succeed with it :)
Thanks to Plippo and all others for sharing info and work.

Attention at the new wiki the long links are broken. Wrong copy/paste :).

Ari

---

### Post by beastrace91 on 2010-06-23
> **mrspacklecrisp said:**
> I have to wonder, though: If you have a laptop, why buy the T101MT? You already have a portable computer. I'm a little confused by what you're saying. Are you looking to replace your computer entirely?

I have a desktop, a laptop, a N900, and then I just traded up my old Asus 900A for a t101mt... But then my friends tell me I am a bit of a technoholic ;)

~Jeff

---

### Post by riccardo.depalo on 2010-06-23
I just modified the wiki for the wrong links... sorry! :confused:

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

---

### Post by Hangman228 on 2010-06-23
My computer died today...
I was on it and some smoke went out and my computer went out...
I don't know what happened... and I can't open it otherwise I lose my warranty...
It was an americain version of it
I don't know if it come from the software or the hardware...

---

### Post by SirAry on 2010-06-23
So, is somebody able to help me with setting right click? I reinstalled 10 times now.

---

### Post by riccardo.depalo on 2010-06-23
@SirAry: what do you mean by setting right click? Be more specific. Maybe secondary click to be enabled with mouse menu in System / preferences?

---

### Post by SirAry on 2010-06-23
> **riccardo.depalo said:**
> @SirAry: what do you mean by setting right click? Be more specific. Maybe secondary click to be enabled with mouse menu in System / preferences?

Yes, rightclick. I've tried to enable from mouse pref. After that the touchscreen was screwed - and not only once. I couldn't recalibrate after that.
 Can you confirm it's working to you? I'm realy not eager to clean install ... :)
I'm using UNR 10.04
Thank you for replying ...

---

### Post by riccardo.depalo on 2010-06-23
@SirAry: I use regular gnome ubuntu, but it should be the same. I have secondary click enabled and automatic click not enabled, it works for me. Anyway reinstall should be last option, if all others failed. Did you try to set to default calibration?

> **Plippo said:**
> The calibrator package actually should provide default calibration values, I don't know why they are not active on your machine. You can try to use the following command to set these default values and then run the calibrator again:
```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```

If something go wrong, try to reinstall the calibration package by Plippo, from the first page of this thread.

---

### Post by mrspacklecrisp on 2010-06-24
@riccardo.depalo: It shouldn't matter. If the command's going to work, it will work in terminal. And how on earth did you video chat with kopete? As far as I can tell, Kopete's never even supported that function for gtalk. I can't find any option to do it.

@Hangman228: You should give it up and cash in the warranty. Unless you really messed up some system files, it's likely the computer. Netbooks have pretty high failure rates. Oh, but be very careful, this is a mistake I had in the first month: If it's on (if it turns on) look very very hard at the screen. I thought I killed mine, but the backlight simply failed. In fact, a system failure had occurred and it needed me to press enter before it could fix anything and boot up normally. This was when Win7 was still on a partition and really screwing with it.

---

### Post by riccardo.depalo on 2010-06-24
@mrspacklecrisp: sorry, kopete doesn't work with gtalk video, but supports it with other accounts, like yahoo. It seems that google has not implemented video for linux yet.

---

### Post by hanoc on 2010-06-24
@Hangman228 I don't know if it's your case but mine sometimes does not boot and I solve it by removing putting again the battery.

---

### Post by Hangman228 on 2010-06-24
@hanoc : Thanks but in my case the smoke is a good indicator for death ^^
I think it's maybe the proc...

I contact Asus and I will see, now i just have to find my warranty paper!

I hope it's an isolated case...

I keep you in touch for my adventures !

Ps: Do you think it can be due to the software like Jupiter ?

---

### Post by beastrace91 on 2010-06-25
Has anyone gotten the rotate button on the screen to work? When I press it by default it locks the screen under Gnome - anyone know if there is a way to switch this to rotate like it is suppose to be? I look under keyboard shortcuts but did not find anything.

~Jeff

---

### Post by bakinsoda on 2010-06-26
Hi,

I'm interested in getting this netbook as a potential reader and tablet device.  Regarding the tablet portion, what i would really like is to use the device, connected to a projector, to write lecture as I'm lecturing (think overhead projector and white board).  What program is available to do this on Ubuntu?  I want to be able to save the slides/pages and upload them for students.  Also, what is the quality like using the stylus/pen on the tablet on Ubuntu?

Let me know so I can order it soon.  Thanks!

---

### Post by beastrace91 on 2010-06-26
> **bakinsoda said:**
> Hi,

I'm interested in getting this netbook as a potential reader and tablet device.  Regarding the tablet portion, what i would really like is to use the device, connected to a projector, to write lecture as I'm lecturing (think overhead projector and white board).  What program is available to do this on Ubuntu?  I want to be able to save the slides/pages and upload them for students.  Also, what is the quality like using the stylus/pen on the tablet on Ubuntu?

Let me know so I can order it soon.  Thanks!

I'm a teacher and that is exactly what I use this little bugger for :)

[Xournal]("http://xournal.sourceforge.net/") works fantastically for such usage. Allows 1 click export to pdf.

Cheers,
~Jeff

---

### Post by bakinsoda on 2010-06-26
Thanks for your response Jeff.  So it works well with this netbook?  Can you describe your experiences?

Also, can you describe your setup?  Did you you use ubuntu netbook remix?  What other apps would you recommend with using this in teaching?

Regarding Xournal, my impression is that you write on it like a notebook, and flipping pages as you go.  Is there a mode for a continuous page (like an overhead projector)?

Thanks, I feel good ordering this netbook now.  Was in a market for a netbook that has a long battery life (10 hours), but shelling out another $200 to get touchscreen and writing is pretty awesome.

---

### Post by beastrace91 on 2010-06-26
I'm actually running Linux Mint 9 on it currently (check my sig for why I prefer Mint over Ubuntu). Configuration on Mint 9 is fairly straight forward - just do what it says on the first page of this thread here.

Xournal looks exactly a sheet of notebook paper and behaves fairly as such - only it really is infinite (unlike and over head projector roll which runs out ;) )

Also - in terms of battery life. With the stock hard drive I saw around 3 hours and 45 minutes of duration. After upgrading it to an SSD (which required ripping the thing to pieces) it is increase to just over 6 hours.

Attached and an example of a few problems I had worked out this past semester - other than my horrid hand writing the colors make it look nice :)

~Jeff

---

### Post by bakinsoda on 2010-06-26
Thanks for the upload -- ouput looks excellent.  I just hope the writing interface (on 10") and the response (writing, and switching pages) will be fast.  I always question this kind of stuff, especially on such weak hardware.

Also, I think i'm going to give ubuntu netbook remix a try and follow the instructions on [here]("https://help.ubuntu.com/community/T101MT").

I can't believe battery life is only 3hrs 45mins...I was really looking forward to 6 hours (watching movies and regular usage).  Darn!  Are there batteries with more cells witht his???

---

### Post by Plippo on 2010-06-28
@riccardo:
Good work with the wiki page, from the quick look I had everything looks okay, but I will look a bit deeper later to see if I find some mistake.

@Jeff:
I looked at your "homework" file, great use for the T101MT! I also really like Xournal, especially for annotating PDFs. But as the lines look a bit wiggly in your file, have you tried enabling "use XInput" in Xournal (and save the settings then so it will be activated again next time)? This way for me the lines look much smoother (you can disable pressure sensitivity then if you don't like it and still enjoy the smoother lines).

@Hangman228:
I feel sorry for you and your smoking computer... I don't think that such a failure can be produced by software, this really looks like a hardware failure caused by bad luck. Even if you block all the holes on the device, there is an automatic shutdown by the BIOS if it gets too hot -- before there is any smoke coming out. I don't think that any software can disable this. So I wish you good luck with ASUS support, I was content with it: when on a different ASUS laptop the battery broke nine months after purchase, I sent it in and got a brand new battery for free in less than a week.

---

### Post by beastrace91 on 2010-06-29
> **Plippo said:**
> I looked at your "homework" file, great use for the T101MT! I also really like Xournal, especially for annotating PDFs. But as the lines look a bit wiggly in your file, have you tried enabling "use XInput" in Xournal (and save the settings then so it will be activated again next time)? This way for me the lines look much smoother (you can disable pressure sensitivity then if you don't like it and still enjoy the smoother lines).

I do have XInput enabled, thats just my poor handwriting. :P

~Jeff

---

### Post by TH_ on 2010-06-30
@ Plippo: Is it possible to enable one-finger-scrolling in Firefox and Evince instead of scrolling with two fingers in your application? Of course, only if you use the touch screen, otherwise the cursor would be caught in the window, if you use the touchpad or USB mouse. ;)

For right-click it would be better to touch the screen a few seconds with one finger instead of two-finger-click.

---

### Post by bakinsoda on 2010-07-01
Just received my netbook and loaded ubuntu netbook on it.  A few questions.

@beastrace91 in xournal, did you do any customization?  What bothers me so far is when I write, my hands tend to touch the screen, which interrupts the writing process (and gets really annoying).  Is there a way to make the screen only responsive to the pen in xournal?

to everyone: when on battery, ubuntu dims off after a little idlenss.  when I become active again, the screen brightens up a little, but not to it's original state (eg, max).  is there a way to make it to always go back to its original state?

virtual keyboard: how are you guys using this?  i installed onboard, cellwriter, and florence.  however, none really works the way i would imagine it to.  when in tablet mode, when there is a textbox (say, address bar in firefox), i'd like to be able to bring up a keyboard easily and type in text (knowing what i type).  with onboard, the keyboard is always on top.  with florence, it takes up the whole screen (and i dont know what's being typed); also with florence, when typing the address in firefox, suggestions pops up over the keyboard and i have to switch back to keyboard after every letter.  any suggestions on this usage?  i only imagine to use this in a broswer really.

two finger touchscreen: i know this is still under development, but is it just me, or does it seem like i have to drag two fingers down really hard to scroll down (in firefox and pdf viewer)?  doesn't seem so hard for zooming.  also, how do i set it so that twofing always starts up (can't figure this out).  so far it's a bother if i have to always flip back to type.

once i play around with this some more i'll post more comments and questions.  thanks.

---

### Post by Hangman228 on 2010-07-02
@TH_ : You can use Grab and Drag for firefox to add one finger scroll : [https://addons.mozilla.org/fr/firefox/addon/1250/](https://addons.mozilla.org/fr/firefox/addon/1250/)
And you can use Foxit reader wich include one finger scroll to read pdf

---

### Post by riccardo.depalo on 2010-07-03
@Bakinsoda: you should deselect "auto hide" in florence settings/behaviour, otherwise keyboard always disappers when touched. Keyboard is also resizable as you wish. You can use mouse as a normal window or the button on the left for resizing, that you have there when you select "florence keys" in settings/layout.

The screen problem is a strange one. Try to follow the wiki, [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT) or give on terminal the code: sudo setpci -s 00:02.0 f4.b=ff

---

### Post by bakinsoda on 2010-07-03
> **bakinsoda said:**
> 
to everyone: when on battery, ubuntu dims off after a little idlenss.  when I become active again, the screen brightens up a little, but not to it's original state (eg, max).  is there a way to make it to always go back to its original state?


got this resolved -- battery options fixed it.

> **bakinsoda said:**
> 
virtual keyboard: how are you guys using this?  i installed onboard, cellwriter, and florence.  however, none really works the way i would imagine it to.  when in tablet mode, when there is a textbox (say, address bar in firefox), i'd like to be able to bring up a keyboard easily and type in text (knowing what i type).  with onboard, the keyboard is always on top.  with florence, it takes up the whole screen (and i dont know what's being typed); also with florence, when typing the address in firefox, suggestions pops up over the keyboard and i have to switch back to keyboard after every letter.  any suggestions on this usage?  i only imagine to use this in a broswer really.


i got onboard working pretty well -- just had to go into the preference.  i have it working automatically at startup (login screen), when screen is locked.  i also made it so onboard always starts when logging in, start minimized (with button).  things this can be better is transparency, an big button for minimizing, and appearing/reappearing from a chosen side (like on a phone).

> **bakinsoda said:**
> 
two finger touchscreen: i know this is still under development, but is it just me, or does it seem like i have to drag two fingers down really hard to scroll down (in firefox and pdf viewer)?  doesn't seem so hard for zooming.  also, how do i set it so that twofing always starts up (can't figure this out).  so far it's a bother if i have to always flip back to type.

once i play around with this some more i'll post more comments and questions.  thanks.

used firefox one finger plugin...might have to consider foxit reader for pdf...

i also have issues with sensitivity with two fingers on touchpad.  the only thing i found that kinda helped was adjusting 

Option "EmulateTwoFingerMinZ" "10" 

in the /usr/lib/X11/xorg.conf.d/96-synaptics-twofing.conf file (to 40 right now).  however, this also affected the touch screen -- need to use a lot of pressure to move.  any suggestions?

---

### Post by tlimsisnw on 2010-07-04
Was a miserable day for my T101MT yesterday. Accidentally selected the "windows vista" partition in grub (i think it was the recovery one) and so I exited, and now I only get the "grub rescue>" prompt. Seems only the commands ls and set work here. I can't seem to get it to boot. Tried booting from USB, but it didn't work initially even with USB as the first boot option. Then I discovered that I had to completely disable the harddisk in the BIOS in order to force it to boot from the USB drive. Finally, got ubuntu running from the USB, reinstalled ubuntu, then it worked again, but grub didn't find my window 7 partition, although I can see it is still there from Disk Utility. I thought I should try to restore to the factory state, so I selected the recovery (Vista) partition in the grub boot menu. That proved toxic! It went into recovery for some 1hr plus and rebooted to "grub rescue>". Upon checking with Disk utility, and fdisk -l, the harddisk is now completely messed up with some 60 partitions: sda1 to sda60. 
 
Before I reformat, I'm wondering if anyone else had the same experience, or solution for recovery? Or it is too late to recover? Ouch!

---

### Post by Plippo on 2010-07-04
@bakinsoda:
"EmulateTwoFingerMinZ" can't affect the touch screen, it's only read by the touchpad driver. I can't say why you needed more pressure on the touch screen afterwards, but it should have nothing to do with this setting. I'm working on an improvement of two finger scrolling on the touchscreen so it continues when you lift one finger during scrolling (or the touchscreen looses track of one finger). That should make it easier to scroll. (The problem is that the touchscreen doesn't send any position information if you don't press hard enough, so there has to be at least one finger pressing hard enough so the driver gets some data.)

For the problem with the Firefox suggestion list, which I also experienced: You can try to open the address **about:config** in Firefox and there change the value of **browser.urlbar.delay** to a higher value, I use 1500. Then, the suggestion list only comes up when you pause typing for 1.5 seconds, so it doesn't disturb that much any more (of course you can also set this value higher).

@tlimsisnw:
That's really bad. I think because of Microsoft's ignorance of Linux, the Windows recovery tools don't recognize it and thus mess up everything. But I didn't imagine that this could happen just by selecting the entry in GRUB, that really shows that the recovery utility is crap - it shouldn't do anything without permission of the user. I don't know what exactly it did, maybe it already erased all Linux partitions so that could be why GRUB didn't find anything to boot.

The only way to prevent such horrible things from happening would probably be to remove the "recovery"(=destruction) partition...

---

### Post by eckster on 2010-07-04
Thank you, all, for the excellent information. I would have been more than a bit lost, were it not for your help!

This is my feeble attempt to return something to the community. You'll see just how feeble in a moment (-:

When I use my T101MT, I either want to use it in tablet mode or in keyboard mode, so I have written a small script to swap between the two. For tablet mode, I want the on-screen keyboard, for keyboard mode, I don't. I used the excellent touchrotate script to swing back-and-forth. I have assigned the script to my XF86ScreenSaver button, for ease-of-use.

```
#!/bin/bash
pkill onboard  > /dev/null

if xrandr |  grep -q "$OUTPUT connected [^ ]* right"; then
        touchrotate normal & > /dev/null
else
        touchrotate right & > /dev/null
        onboard & > /dev/null
fi

```

Thanks, again, the Community is fantastic.

---

### Post by riccardo.depalo on 2010-07-04
@Plippo and everybody: Hi! I have good news and bad news. First, the good one.
I was testing the new 10.10 alpha2 with the t101mt and I realized that in the new kernel (2.6.35-6) the touchscreen driver was finally implemented! It seems to be just the same StCh kindly provided. It was nice to discover it, just testing a livecd.
Bad news are that cheese crashed with maverik and I had to file a bug report. Maybe it will be better to wait for the final upgrade.

Ow, and... I tried to improve the wiki: it had not a wiki-shape, somedoby told me. I hope now it's easier to read. 
[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

---

### Post by TH_ on 2010-07-04
> **Hangman228 said:**
> @TH_ : You can use Grab and Drag for firefox to add one finger scroll : [https://addons.mozilla.org/fr/firefox/addon/1250/](https://addons.mozilla.org/fr/firefox/addon/1250/)
Thanks! That's a good tip. :D

> **Hangman228 said:**
> 
And you can use Foxit reader wich include one finger scroll to read pdf
Hmmm, I like evince... and Foxitreader has problems displaying some of my pdfs.

---

### Post by bakinsoda on 2010-07-05
hi everyone again,

thanks for all the help, i'm liking this device!  here are my outstanding issues to see if anyone has any idea:

1.  getting twofing started at every startup.  according to the wiki, it says i should see it under system > preferences > boot manager.  i don't see boot manager.

2.  suspend works for me, but hibernate does not.  anyone got this working?

3. confirmed that the two finger on the touchscreen is independent of the touchpad, so disregard that.  I have to apply a lot of pressure to both fingers on the touchscreen -- is there a way for to adjust the sensitivity here?

4.  xournal: any way to ignore my finger touches and only be responsive to the stylus?  right now i have to force my hand/arm to be higher in air when writing.

thanks so much!  also, is there any way to buy another battery that has a longer life for this netbook?

---

### Post by riccardo.depalo on 2010-07-06
@Bakinsoda: Sorry about boot manager, it was a silly mistake from mine, I didn't know how it was translated into english (I have italian version of ubuntu). Anyway the command is gnome-session-properties, you can launch it from the terminal or from system/preferences/Sessions. You can find there the apps launched on startup, just add a new one, call it twofing or how you like it and write in the second line the command twofing --wait
Ric :p

---

### Post by ginetto on 2010-07-06
I hope it's not too late to answer!!

first... tanks to the community, it really helps!

second... your problem with Win recovery. I don't know if i'm the best to answer you, but I had a problem with partitions on T101MT that can help you.

First: When you have problem with Grub, or Windows erased you good MBR, use UltimateBootCD (last one that manage Ext4)... you can simply butt form USB, scan every OS installed and reset MBR

Second: If at the moment you have a lot o partitions but you did't formatted them... then probabilly you can recovery original partition table using command line command as "testdisk" (you can find it in recovery live cd as SystemRescueCD). 

I suggest you to recover using testdisk (you'll find a lot of possibiel partitions, but only few of them you can browse iside... the good ones) and then check with parted or gparted if you changed something bad... for example I recovered my partition and I selected an extension larger than disk size... error showend only by parted.

I really hate windows and proprietary software, but I paied it and I want it yst for test... but I haven't a solution to recovery old win7 partition and setting all the stuff to work as before with Boot Booster, F9 recovery and Express Gate.

ciao... ginetto from Italy

> **tlimsisnw said:**
> Was a miserable day for my T101MT yesterday. Accidentally selected the "windows vista" partition in grub (i think it was the recovery one) and so I exited, and now I only get the "grub rescue>" prompt. Seems only the commands ls and set work here. I can't seem to get it to boot. Tried booting from USB, but it didn't work initially even with USB as the first boot option. Then I discovered that I had to completely disable the harddisk in the BIOS in order to force it to boot from the USB drive. Finally, got ubuntu running from the USB, reinstalled ubuntu, then it worked again, but grub didn't find my window 7 partition, although I can see it is still there from Disk Utility. I thought I should try to restore to the factory state, so I selected the recovery (Vista) partition in the grub boot menu. That proved toxic! It went into recovery for some 1hr plus and rebooted to "grub rescue>". Upon checking with Disk utility, and fdisk -l, the harddisk is now completely messed up with some 60 partitions: sda1 to sda60. 
 
Before I reformat, I'm wondering if anyone else had the same experience, or solution for recovery? Or it is too late to recover? Ouch!

---

### Post by bakinsoda on 2010-07-07
@riccardo: i used twofing without the --wait, is tht ok?

regarding MyPaint, the wiki states:
#

If you like painting, you might be interested in the patched version of MyPaint which can be found here:

[http://www.philmerk.de/dwl/deb/mypaint-resistive.deb](http://www.philmerk.de/dwl/deb/mypaint-resistive.deb) It doesn't work for all brushes, but for some. Check out the beautiful drawing mrspacklecrisp created with it:

[http://ubuntuforums.org/showpost.php?p=9283663&postcount=45](http://ubuntuforums.org/showpost.php?p=9283663&postcount=45)
# Mrspacklecrisp also provided a fix for all brushes of mypaint. Follow these steps: 

I tried installing the patched one and the install hangs.  Can I install the default version and do the 2nd fix to get working?

Thanks.
Vinh

---

### Post by riccardo.depalo on 2010-07-07
> bakinsoda;9559076]@riccardo: i used twofing without the --wait, is tht ok?

Hi! Yes of course it's ok if it works for you. I had to put the --wait, like someone else, because in the first version it didn't work well.

> I tried installing the patched one and the install hangs.  Can I install the default version and do the 2nd fix to get working?

I think also the default version should work with the fix only, but I'm not the one who did the patched version, it's Plippo. The patched and the fix worked for me. I just copied in the wiki the instructions that I found working (and of course anybody can help make the wiki better, if you find any mistake) Can you install without problems the default version and try it? They shoud be both easy to install clicking on the file. Anyway, if the gdeb installer hangs often, it's something happened to me before I reinstalled ubuntu in my system and wiped away Windows partitions. But I don't know why it happened. If it still hangs, try to launch system monitor and terminate at-spi-registryd. It worked for me.
Ric

---

### Post by bakinsoda on 2010-07-07
regarding my paint, i installed via apt-get and followed the 2nd fix (fixing some of the files).

touch screen works, senstivity pressure works.  however, every time i put the stylus down, a stroke is connected from the last spot to the new spot.  is this how things are supposed to work in mypaint?  i don't really know what i'm fixing with mypaint really (don't know what the fixes do).  however, i don't thinkt he strokes are supposed to be connected every time i put down the stylus.

---

### Post by bakinsoda on 2010-07-08
regarding gimp: touchpad does not work (clicking on canvas does not ink).  touchscreen according to wiki also doesn't work -- can't save as the eGalax option.  anyone else have this issue?

thanks.

---

### Post by bakinsoda on 2010-07-08
this probably isn't specific to the Asus netbook, but I'd appreciate if you guys could confirm that you're getting this same bug before I report to the proper folks.

When an application is open (eg, firefox), if I hit Alt+F2 (Open Application dialog), the dialog box is not on top.  I have to manually hit Alt-tab to get the dialog box to show up.  In addition, when an application like firefox is open, if I click on the shutdown icon and select anything (eg shutdown), then the shutdown dialog box is not on top.  I have to exit firefox and all applications to see it.

Thanks!

---

### Post by beastrace91 on 2010-07-08
Hey All,

I wrote a [summary post](http://jeffhoogland.blogspot.com/2010/07/howto-ubuntu-linux-on-t101mt.html) on my website about getting Ubuntu working on the T101MT. Let me know if you think anything important is missing from it :)

~Jeff Hoogland

---

### Post by riccardo.depalo on 2010-07-08
Hi all:

@bakinsoda: regarding MyPaint, I think you should load the patched version of the deb file and then try the fix. It's strange you can't install it. Regarding gimp, if you can't press the save button with the mouse or the touchscreen, try with tab button and press enter. It should work (if I have unterstood what you say). About your last question: no, I don't have this alt-f2 problem.

@Beastrace91: good work. Did you read the wiki I wrote? There are almost the same hints and something more. It's here: [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

Look if there is something interesting for you. For example, there was a kernel upgrade, and there I wrote how to build a new kernel driver by yourself, following Plippo's script. :)

Ric

---

### Post by bakinsoda on 2010-07-08
Regarding the alt+f1 and shutdown dialog, the culprit is OnBoard keyboard.  When that is running (eg minimized), that is when the dialogs don't appear on top.  You can try and confirm.  I removed starting it at every startup now due to this issue.

MyPaint: the patched installs now.  Reason it was stalling was because the password dialog box was hidden underneath so it appeared stalling.  Installing that and applying the 2nd fix made things work.

Gimp: still doesn't work for me, touchscreen and touchpad.  Setting that eGalaxy input will not save.  With touchpad, clicking on canvas does not ink.  Can anyone reproduce this?

Hibernate: after some searching, i think the issue is the video card/driver isn't starting up.  any thoughts?

---

### Post by tlimsisnw on 2010-07-09
Ginetto: Thanks for the tips. Unfortunately I had reinstalled ubuntu and repartitioned with a usb grub boot disk. Now my system is working fine again with ubuntu, but I've lost all my windows OS (not much loss I guess as I seldom use the extremely limited windows 7 starter, and also now I'm wary of the "recovery" partition, probably good not to have it to avoid the accident again).

---

### Post by Plippo on 2010-07-10
@bakinsoda:
As weird as it sounds, to use the touchpad in GIMP, you have to set it to "disabled" in the advanced input device dialog. For the touch screen, you can also disable it, but then it has no pressure sensitivity. But it should work if you enable it and use "3" as the pressure axis (assuming you use the multitouch driver from the packages from the first post).

---

### Post by bakinsoda on 2010-07-10
@plippo then should we change the wiki to not change to the eGalaxy thing and screen for the mode???

so I feel the only urgent thing left on this netbook is hibernate -- I frequently want to do this to continue my session and save on battery.  what do u guys do to do this?  any ideas on the causes of the failure in resuming hibernation?  I'd like to look more into it.

---

### Post by hanoc on 2010-07-10
Hi,

I am having the strangest of problems and I don't think is Ubuntu-Eee related but I don't know even how to start looking for it.

I am trying to write a google document in catalan.

In catalan we use funny looking letters like theese:
camió, aviació
whatever

If I create a google doc in my eee with ubuntu and start typing as soon as I type an accented character some random characters get written.

For example I type:
aviació
aviacivó
gets written.

Everyting works fine until I press the o. Then the extra v gets written.

But it's not always an v. Somtimes it's three, four, or even two lines of random letters.
For example I just wrote camió and got:
camiussó
I seem to find patterns in the letters with a lot of s r v and t. But maybe I am just imaginning things.

It seems that the longer I write without writing an accented letter the more random letters I get when writing one, but, again, maybe I am immagining things.

The funny thing (or one of the many funny things) is that I can use windows to write without experiencing problems in google docs and that I can write correctly in any other website or program with my ubuntu.

I've created a question in the google docs help forum but gotten no answer in days. I haven't find a way to oppen a bug report.

I doubt this is a ubuntu+t101mt specific problem but if some of you could try to write some text with accented characters in a google doc and tell me if I am alone in this.

Also if someone has any idea as how parse all that x-filesque information into a google friendly query I could really use the suggestions.
If you don't see that as t101mt related (which provably isn't) I could still use the suggestions as an private message (pretty pretty please).

Thanks!

---

### Post by riccardo.depalo on 2010-07-10
@Plippo: I tried kernel 2.6.35-7 from suraia repository, just to see how the egalax driver included there works. Everything worked right, but your twofing daemon didn't work anymore. When launched, also touchscreen began to have some problem (one finger scrolling for example). Any idea?

---

### Post by tlimsisnw on 2010-07-11
Is there a way a to do middle mouse button click either on the touchpad/screen? Has anyone found a way to do this? I use Freecad and it requires a middle button down to pan around.

Cellwriter died on me a few times after update to kernel 2.6.32-23, sometimes causing the mouse cursor off-calibration. Rotating the screen around brings back the calibration and restarting Cellwriter would make it work for a while, then it crashes again. Anyone else experienced this?

Also, in the netbook version of lucid, some dialog screens extend below the screen and I can't get at the buttons, any way to resolve this? Riccardo, is this resolved in the kernel 2.6.35-7?

One more concern: I've previously thought the touchscreen needed a protective film like in a mobile phone touchscreen. However, the so-called "high-quality" ones I used so far are left with scratches after 1 to 2 weeks use. I was also told that the touchscreens on tablets are already touch enough against scratches and do not need protection. So I took off the film and have been using it for a while without the film. Seem ok so far. Can anyone verify if this would be ok in the long run? Or do we need the films?

---

### Post by isoscelesrectangle on 2010-07-11
Hi, (I originally posted my own thread, but I feel this belongs here). 
I'm considering purchasing an ASUS T101MT. I am, however worried about  the experience as a whole (setting hardware compatibility aside). All  the reviews I've read so far point to the fact that the experience is  sluggish because the computer runs Windows 7 Starter, and ASUS  preinstalls it with truckloads of bloat. I'm thinking of throwing in an  SSD and installing a Linux distro (Anything that works with a tablet).  If anyone has one of these babies, could you please respond with: 

[LIST=1]
[*]The performance of this laptop (in particular the touchscreen responsiveness), in Ubuntu, instead of Windows 7?
[*]The desktop environment that you prefer to use that's tablet friendly?
[/LIST]
Thank you all so much.

---

### Post by riccardo.depalo on 2010-07-11
> Also, in the netbook version of lucid, some dialog screens extend below the screen and I can't get at the buttons, any way to resolve this? Riccardo, is this resolved in the kernel 2.6.35-7?

@Tlimsisnw: the only workaround I found is to use the Tab button instead of the mouse. As for 2.6.35, I uninstalled it, as twofing daemon doesn't work with it. It seems it's too early for everyday use.
About the films: it seems to me that the resistive screen doesn't need any protection. At least, I had no problems in these two months of daily use. I just had to clean it sometimes.:)

@isoscelesrectangle: I used double boot for a while, until I found that Ubuntu worked enough well with this machine. Win7 was a little slower than Linux, though better than Vista, but I have no doubts: free software is always better. I use gnome version of Ubuntu, but also netbook remix worked well.

---

### Post by isoscelesrectangle on 2010-07-11
@ riccardo.depalo
Thank you, waiting for the chance to go to the Beijing nightmare of an electronics market to try it out ;). Does the fact that it's a resistive touch screen get in your way?

---

### Post by riccardo.depalo on 2010-07-11
@isoscelesrectangle: I don't mind it's resistive, you have to press harder on the screen, but it's not a smartphone. I mean, maybe for a general pc purpose it's better. Try yourself to see if it is what you need.

---

### Post by isoscelesrectangle on 2010-07-11
@ _[riccardo.depalo]("http://ubuntuforums.org/member.php?u=1058842")_ Ah ok, thank you.

---

### Post by Plippo on 2010-07-12
@bakinsoda:
No the information in the wiki is okay - for the touch *screen*, you can set the eGalax controller to Screen to get pressure sensitivity. For the touch *pad*, you should not change the value for the Synaptic TouchPad controller.

@hanoc:
That is really strange. Did this happen using the keyboard or a virtual keyboard on the touch screen? But if it happens only in google docs (and e.g. not when posting here on the forum), this really seems to be a Google related problem.

@riccardo:
I haven't tried that kernel, but in theory the driver there should be the one from Stéphane, just missing the two patches I created, and thus should work. Do you get some terminal output when you start twofing with --debug?

@tlimsisnw:
In Linux you can always create a middle click by pressing the left and right mouse button at the same time, so on the touch pad by pressing the left and right side of the button below at the same time. On the touch screen, there is currently no such solution. If the middle click is used more often than right click in Freecad (I don't know the program), I could add a special profile for this program to the twofing daemon which maps two fingered touch to middle click for this program.

If a window doesn't fit on screen, you can hold the Alt key and then click anywhere in the window to drag it.

I haven't had any problems with cell writer, but I normally only use the screen in non-rotated mode, maybe the problem only happens when rotated.

I also don't use any protected film. I've had a cellphone with a resistive touch screen for two years and never had any scratch on it. You should just take care to close the lid with the screen facing inwards when you transport the Eee PC so nothing from outside can scratch it.

@isoscelesrectangle:
The disadvantage of the resistive screen is you have to press a bit harder, but the advantage is better accuracy and that you can also use the stylus to control it.

---

### Post by riccardo.depalo on 2010-07-12
@Plippo, with 2.6.35-7 kernel it seems I have no error messages in debug:
> Input device name: "eGalax Inc. USB TouchController"
XInput device id is 10.
Found window with id 37748767 and class 'desktop_window' 
Found window with id 111149099 and class 'google-chrome' 
Found window with id 106955471 and class 'gnome-terminal' 
Found window with id 12582913 and class 'gnome-session' 
Found window with id 18874369 and class 'gnome-settings-daemon' 
Found window with id 20971521 and class '<unknown>' 
Found window with id 27262977 and class 'bluetooth-applet' 
Found window with id 25165825 and class 'polkit-gnome-authentication-agent-1' 
Found window with id 31457281 and class 'gnome-panel' 
Found window with id 35651585 and class 'gnome-power-manager' 
Found window with id 37748737 and class 'nautilus' 
Found window with id 39845889 and class 'nm-applet' 
Found window with id 31457321 and class 'gnome-panel' 
Found window with id 31457283 and class 'gnome-panel' 
Found window with id 62914561 and class 'wnck-applet' 
Found window with id 60817409 and class 'trashapplet' 
Found window with id 65011713 and class 'indicator-applet-session' 
Found window with id 67108865 and class 'multiload-applet-2' 
Found window with id 73400321 and class 'indicator-applet' 
Found window with id 71303169 and class 'notification-area-applet' 
Found window with id 77594625 and class 'clock-applet' 
Found window with id 14680065 and class 'gtk-window-decorator' 
Found window with id 14680134 and class 'gtk-window-decorator' 
Found window with id 94371841 and class 'gnome-screensaver' 
Found window with id 102760449 and class 'gdu-notification-daemon' 
Found window with id 31457689 and class 'gnome-panel' 
Found window with id 23068673 and class 'gnome-user-share' 
Found window with id 113246209 and class 'applet.py' 
Found window with id 123731969 and class 'update-notifier' 
Found window with id 31457595 and class 'gnome-panel' 
Found window with id 31458057 and class 'gnome-panel' 
Found window with id 106954753 and class 'gnome-terminal' 
Found window with id 31458557 and class 'gnome-panel' 
Found window with id 56628995 and class 'compiz' 
Found window with id 31459333 and class 'gnome-panel' 
Found window with id 31459383 and class 'gnome-panel' 
Found window with id 31459476 and class 'gnome-panel' 
Found window with id 31459523 and class 'gnome-panel' 
Found window with id 31458698 and class 'gnome-panel' 
Found window with id 31458727 and class 'gnome-panel' 
Found window with id 111149057 and class 'google-chrome' 
Found window with id 111149059 and class 'google-chrome' 
Found window with id 31457890 and class 'gnome-panel' 
Found window with id 31457951 and class 'gnome-panel' 
Found window with id 111151418 and class 'google-chrome' 
Reading input from device ... (interrupt to exit)


no pinch and zoom... and no message in debug when I touch the screen with two fingers. It seems the same debug of 2-6-32, but the screen doesn't behave in the same way. Anyway, it would be important to correct this, in order to make the daemon work with future stable versions of the kernel. It could be proposed to Ubuntu developers too.

p.s.: I wrote in the wiki the files as attachment now, and added an index. The ubuntu doc group liked it.

---

### Post by bakinsoda on 2010-07-12
> **Plippo said:**
> @bakinsoda:
No the information in the wiki is okay - for the touch *screen*, you can set the eGalax controller to Screen to get pressure sensitivity. For the touch *pad*, you should not change the value for the Synaptic TouchPad controller.



@Plippo thing is, when i set it to eGalax, both touchscreen and touchpad does not work.  When i go to set input device again, it goes back the the orginal setting.  From there, changing anything wont work, have to quit and exit.  Anyone else have this problem?  Gimp v 2.6.8 from apt-get.

---

### Post by hanoc on 2010-07-13
> **Plippo said:**
> 
@hanoc:
That is really strange. Did this happen using the keyboard or a virtual keyboard on the touch screen? But if it happens only in google docs (and e.g. not when posting here on the forum), this really seems to be a Google related problem.


Hi, yes it's quite strange and it seems google related more than any other thing but as it only happens to me in ubuntu I wanted to ask if someone could try to replicate my scenario.
I was using the phisical keyboard btw.

Thanks!

---

### Post by riccardo.depalo on 2010-07-13
@Hanoc: it's very strange indeed, I do not have this google doc problem. If I type I see on the screen what I typed, whatever default language I choose. All other word processors work well?
Ric

---

### Post by trauman on 2010-07-14
Hello, and sorry for my bad english.
I'm running debian linux with 2.6.35-rc5 kernel with installed egalax module. Here's a problem: when i touch a screen, my pointer skips to bottom-right corner. 
```
$xinput list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=12	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=11	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; ACPI Virtual Keyboard Device  

```
and all xinput properties are same for all EVTouch TouchScreen devices
```

$xinput watch-props 10

	Device Enabled (134):	1
	Device Accel Profile (253):	0
	Device Accel Constant Deceleration (254):	1.000000
	Device Accel Adaptive Deceleration (256):	1.000000
	Device Accel Velocity Scaling (257):	10.000000

```
anyway, i'can't calibrate my screen even after adding this line:
```

xinput set-int-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517

```
and calibration output:
```

$ egalax_calibrator_x11 -v
DEBUG: XInputExtension version is 2.0
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Skipping device 'Virtual core XTEST pointer' id=4, does not report Absolute events.
Calibrating EVDEV driver for "EVTouch TouchScreen" id=10
	current calibration values (from XInput): min_x=411, max_x=32557 and min_y=45, max_y=32517
DEBUG: Adding click 0 (X=1023, Y=599)
DEBUG: Not adding click 1 (X=1023, Y=599): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1023, Y=599): within 7 pixels of previous click

```
WHAT THE HECK AM I DOING WRONG?

---

### Post by hanoc on 2010-07-14
@trauman you should try this command:
```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```
and recalibrate again.

It is explained here:
[https://help.ubuntu.com/community/T101MT#TOUCH%20SCREEN](https://help.ubuntu.com/community/T101MT#TOUCH%20SCREEN)

---

### Post by Plippo on 2010-07-14
@trauman:
Can it be that you still use the old kernel module quirk option as your  xinput list shows the device is separated into multiple devices? You  have to remove this option for the driver to work properly.

Also you seem to have the evtouch driver installed. You might have to  uninstall it in order to properly use the touch screen with the new  multitouch module.

@bakinsoda:
This is strange. When you select eGalax in this dialog, you don't really "set the input to eGalax" but instead choose that you want to change the settings for the eGalax device. These settings should in no way affect the touchpad. If they do, I don't know why. If you can't access the controls on the dialog any more, you don't have to quit - you can still use the tab key to navigate to the "close" button and then press enter to close the dialog.

@riccardo:
No, the windows are okay, these are all system windows that run in the background. So at least the windows are correctly recognized, than the touch recognition seems to be the problem. I probably have to try it out myself.

---

### Post by trauman on 2010-07-14
@Plippo:
Thank you very much. It works.

---

### Post by riccardo.depalo on 2010-07-15
@Plippo, it seems I have three times egalax with 2.6.35:

```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=13	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=14	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]

```

while with 2.6.32 it's like this:

```
ric@ric-laptop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=11	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

maybe that's why your daemon doesn't work.

---

### Post by isTHEr3mOr3 on 2010-07-15
Just wanted to say hello and thank everybody that has contributed in this thread (+wiki) and especially Plippo! 
I was thinking of buying the t91 3 days ago and then saw this thread... Today received the T101MT en within a couple of hours installed everything with ease. Ubuntu works on the T101MT like a charm! 

I also spend some time with Windows 7, but nah.. Ubuntu is so much more fun and also works a *lot* faster. Although I might have to tweak W7 a bit though..

---

### Post by Plippo on 2010-07-16
@riccardo:
That's strange, that's how it looked before the multitouch driver. Maybe the new kernel has the old tweaks option, which is no longer necessary, built in. I'll have to look at the kernel source to find that out.

---

### Post by isTHEr3mOr3 on 2010-07-16
Love the two finger gestures! Works pretty good, zooming in Firefox is a bit sluggish but it does the job. 
An add-in for firefox makes it also possible to add grap and drag scrolling with one instead of two fingers : [https://addons.mozilla.org/en-US/firefox/addon/1250/](https://addons.mozilla.org/en-US/firefox/addon/1250/). 
I like the autoscroll feature in this add on. Would be nice to have it in twofinger as well.

---

### Post by riccardo.depalo on 2010-07-17
For anybody who likes to paint with t101mt, I would suggest this site in html5: [http://mugtug.com/sketchpad/](http://mugtug.com/sketchpad/)

@isTHEr3mOr3: I tried your suggestion about Firefox and added it to the wiki: 
[https://help.ubuntu.com/community/T101MT/](https://help.ubuntu.com/community/T101MT/)

---

### Post by tlimsisnw on 2010-07-20
Has anyone been able to get hibernation to work properly? I find that if I run on battery and let it sleep after 10 min, it can't wake up after that. Pushing the on button results in an apparent attempt to startup, but hangs. I had to reset the systems by holding the on button for a few seconds, then restart and it is fine. Does it hibernate when it goes to sleep, or does it suspend? Suspend seems to work ok on ac power.

---

### Post by tlimsisnw on 2010-07-21
Found a small tool called Jupiter at: [http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html](http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html). Not sure if it really takes advantage of SHE. Some claim that it help extend battery usage, so I'm trying it. Seems quite handy for changing CPU performance, on/off bluetooth, touchpad, wifi, screen resolution/orientation.

---

### Post by Scotty519 on 2010-07-24
I am running in to an issue on 10.04 (2.6.32.24 and .23)) where the Update Manager freezes after I input my password. The problem is directly related to assistive technologies being enabled (at-spi-registryd). 

Has anyone had this problem, and if so, know a good fix. I've had some minor luck searching the forums generally for this issue. Only fix I have personally found is to disable assistive tech, but then I lose my hold touchscreen to right-click feature.

---

### Post by Plippo on 2010-07-25
Hi all,
I've created a new version of the twofing daemon. You find it again [at good old post #77]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77"), installation is as with the previous versions. Please test and report problems as you like.

The changes are as follows:

You can now choose between three modes for right-clicking, depending on which option you add to your **twofing** call:
[LIST]
[*]**--click=center** right clicks will occur between both fingers (same as before, used by default)
[*]**--click=first **right clicks will occur at the finger which was the first one that touched the screen
[*]**--click=second** right clicks will occur at the finger which was the second one that touched the screen
[/LIST]
Please note that if you tap with both fingers at the same time, the touchscreen decides arbitrarily which finger is first or second, so in this case, **--click=center** still is the only option that gives predictable results.

The daemon now also has a new feature called "continuation" which should make two finger scrolling and zooming easier and more reliable: If you start a zoom/scroll gesture with two fingers and release one, you can still continue zooming/scrolling with the other one. This also means that if you use both fingers, there should be less cases in which the scrolling/zooming is interrupted. Please feel free to report whether this reduces problems with two finger zooming/scrolling for you.

@riccardo: Unfortunately I haven't figured out the problem with the new kernel yet.


@Scotty519: Have you tried to change the "Password dialogs as normal windows" setting?

---

### Post by Scotty519 on 2010-07-25
> **Plippo said:**
> 
@Scotty519: Have you tried to change the "Password dialogs as normal windows" setting?

Fixed the issue, thanks! Seems like an odd option to change.

---

### Post by Plippo on 2010-07-25
There was a bug in the new version which I uploaded earlier. This caused that right-clicking sometimes didn't work correctly and scrolling was activated instead. I've uploaded a new version (0.0.3a) which fixes this. You find it again [here]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77"). Sorry for that!

@Scotty519: Indeed, it's strange that it is necessary, but for some reason it is.

@tlimsisnw: For me hibernation also doesn't work, I don't know why, it works on another Eee PC (1005) I have installed Ubuntu on. But when the device is idle, it normally should only suspend, not hibernate. Suspend always works for me, with AC power as well as on battery. Maybe you have to change this in the power settings.

---

### Post by riccardo.depalo on 2010-07-25
@Plippo: Your work is always much appreciated. I updated the wiki with your last instructions and upgrade:
[https://help.ubuntu.com/community/T101MT]("https://help.ubuntu.com/community/T101MT")

maybe we should tell Ubuntu developers about these software and workarounds for this tablet pc.

---

### Post by bakinsoda on 2010-07-25
Regarding hibernation, I've tried both the uswsusp and the TuxOnIce methods, and both fail to resume from hibernation.  However, both say the image has been loaded, and it stays there.

My hunch is that the swap disk is loaded successfully, but the graphics isn't.  Any thoughts?

---

### Post by tlimsisnw on 2010-07-26
Plippo: I like your new twofing very much. Thanks. Finally, there's some productive way to do right click on the touchscreen. Yeah! Suspend also work for me always when on AC power, however, when on battery, if I allow it to idle for sometime e.g. 10min, it goes into some mode that shutsdown the tablet although I've only set it to sleep the screen after 10min.

---

### Post by Plippo on 2010-07-31
@tlimsisnw: Great that you like the new twofing. If you have any ideas for further improvements, please don't hesitate to share them (of course I can't promise you they will be implementable :-) )

Strange, for me suspending always works. But I always suspend manually. So for now, I can only recommend completely disabling automatic suspending.

---

### Post by mrspacklecrisp on 2010-08-04
Okay, so after six weeks of summer college coursework I found a tiny bit of time and discovered a tiny little fix for the issue of sending audio to the target in video chat, using empathy, with the google talk protocol (which may apply to other protocols and programs) In this hadn't been figured out yet, one must

Run pavucontrol

Go to the Input Devices tab

Unlock the channels

Set either "Front Left" or "Front Right" to silent

.... And for best results, set the other one to max.

I'm still dealing with a problem of my video and audio being out of sync (something that happens when simply recording video with guvcview) so in case someone hasn't fixed it, I'll get on it when I get some time. Sound good?

---

### Post by Cyberblade on 2010-08-05
So I just got my t101mt today, and couldn't wait to get Linux running on it, having purchased it over other similar convertible netbooks just because of the linux information available.  I'm having absolutely no luck with the touchscreen however.

Despite the calibrator, common touchscreen packages, and kernel modules installing with no issues, the touch screen continues to just go to the top left corner.  Here's the output of "xinput list"

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AsusTek, Inc. MultiTouch(YFO)           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=11	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

I suspect the problem is that it lists an asustek multitouch device, instead of the eGalax controller.  I don't think it's loading the kernel module.  I've installed and reinstalled the correct version several times with no luck.  The calibrator is installed and the touchrotate script works, so the calibrator and touchscreen support package are installed just fine, leaving just the kernel module suspect.  Anybody got any suggestions?

Running Ubuntu Netbook Remix 10.04, kernel 2.6.32-24.

---

### Post by riccardo.depalo on 2010-08-05
@Cyberblade: this is strange, you should have there ```
 eGalax Inc. USB TouchController
``` instead. Did you load firmware proprietary driver before loading the deb files proposed in this thread? In case, you should uninstall it.

---

### Post by Cyberblade on 2010-08-05
Not that I know of, I went straight from installing and updating Ubuntu into loading the deb files listed [here]("https://help.ubuntu.com/community/T101MT").

---

### Post by jtjs on 2010-08-05
> **Cyberblade said:**
> Not that I know of, I went straight from installing and updating Ubuntu into loading the deb files listed [here]("https://help.ubuntu.com/community/T101MT").

Can you provide the output from the lsusb command?

---

### Post by Cyberblade on 2010-08-05
Certainly, the output from lsusb is~
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jtjs on 2010-08-05
> **Cyberblade said:**
> Certainly, the output from lsusb is~
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

You can confirm this is from a T101MT? If so, it means Asus has revised the hardware.

The reason why the pointer goes to the top left if because the default hid driver doesn't understand multitouch displays too well. In order to get single touch working, you'll need to enable the multitouch quirk..

I wonder who the manufacturer for the touch screen is.. Perhaps you could look at the windows drivers to give us an idea?

For reference, the T91MT's mosart screen is:
Bus 004 Device 002: ID 0486:0185 ASUS Computers, Inc.
0486 is the vendor id, which is ASUS, and the other number is the device id.

---

### Post by Cyberblade on 2010-08-05
Yes, I can confirm this is a T101MT, the bios, instruction manual, and box all list it as a T101MT.  This is just lovely, I get this nice new netbook and now have no possible way to use the touchscreen at all.  :mad:

Since the last laptop I bought was in 2007, I was under the delusion there'd be a restore disc buried in all the crud in the box (That was kinda silly thinking about it now, since I know netbooks don't have cd/dvd drives lol.)  But of course, thats now relegated to a partition, a partition I just assumed was junk because Windows is always full of junk on a new computer.  So unfortunately, I cannot help you with a look at the Windows driver, because there is no way to get that Windows driver.

Is there any other way to figure out who the manufacture of the screen is? (Aside from ripping it open, something I'd rather not resort to)?

Edit:  Also, care to elaborate on the multitouch quirk?  I looked into it, and mostly found information regarding the T91MT, and trying to use that information as a basic guideline didn't do anything in this case.  (Neither good or bad)  All I really want is basic single touch support at least, so if I can get that working I'll be satisfied.

---

### Post by Plippo on 2010-08-06
Oh my, why the hell does Asus have to change the hardware without changing the name of the device?

To test the multitouch quirk, you have to do the following:
First, unload the modules:
```

sudo rmmod usbhid
sudo rmmod hid

```Then, load them again with the quirk:
```

sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040

```Then, the touchscreen should work at least with single-touch.

You can also try the evtest program to check what events the device sends (can be installed via synaptic). If you post the output of evtest, maybe we can see if the events sent resemble those sent by the eGalax or the mosart screen.

---

### Post by Cyberblade on 2010-08-06
Adding the quirks option worked like a charm.  Tho it does need to be redone every boot, and google keeps directing me to the deprecated modprobe.conf when I search for things like "module options at boot" which is really not all that helpful.

Anyways, here's the output of the evtest.

```
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 256 (Btn0)
    Event code 257 (Btn1)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     3478
    Event code 1 (Y)
      Value      0
      Min        0
      Max     3478
    Event code 2 (Z)
      Value      0
      Min        0
      Max     3478
    Event code 3 (Rx)
      Value      0
      Min        0
      Max     3478
    Event code 4 (Ry)
      Value   2775
      Min        0
      Max     3478
    Event code 5 (Rz)
      Value   1839
      Min        0
      Max     3478
    Event code 24 (Pressure)
      Value      0
      Min        0
      Max      255
    Event code 40 (Misc)
      Value      0
      Min        0
      Max        2
    Event code 41 (?)
      Value      0
      Min        0
      Max        2
    Event code 42 (?)
      Value      0
      Min        0
      Max        2
    Event code 43 (?)
      Value      0
      Min        0
      Max      255
    Event code 44 (?)
      Value      0
      Min        0
      Max      255
    Event code 45 (?)
      Value      0
      Min        0
      Max      255
    Event code 46 (?)
      Value      0
      Min        0
      Max      255
    Event code 47 (?)
      Value      0
      Min        0
      Max      255
    Event code 48 (?)
      Value      0
      Min        0
      Max      255
    Event code 49 (?)
      Value      0
      Min        0
      Max      255
    Event code 50 (?)
      Value      0
      Min        0
      Max      255
    Event code 51 (?)
      Value      0
      Min        0
      Max      255
    Event code 52 (?)
      Value      0
      Min        0
      Max      255
    Event code 53 (?)
      Value      0
      Min        0
      Max      255
    Event code 54 (?)
      Value      0
      Min        0
      Max      255
    Event code 55 (?)
      Value      0
      Min        0
      Max      255
    Event code 56 (?)
      Value      0
      Min        0
      Max      255
    Event code 57 (?)
      Value      0
      Min        0
      Max      255
    Event code 58 (?)
      Value      0
      Min        0
      Max      255
    Event code 59 (?)
      Value      0
      Min        0
      Max      255
    Event code 60 (?)
      Value      0
      Min        0
      Max      255
    Event code 61 (?)
      Value      0
      Min        0
      Max      255
    Event code 62 (?)
      Value      0
      Min        0
      Max      255
    Event code 63 (?)
      Value      0
      Min        0
      Max      255
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)
Event: time 1281110375.370728, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110375.370751, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1281110375.370771, type 3 (Absolute), code 4 (Ry), value 2556
Event: time 1281110375.370781, type 3 (Absolute), code 5 (Rz), value 1792
Event: time 1281110375.370785, -------------- Report Sync ------------
Event: time 1281110375.386730, type 3 (Absolute), code 4 (Ry), value 2557
Event: time 1281110375.386761, -------------- Report Sync ------------
Event: time 1281110375.402755, type 3 (Absolute), code 5 (Rz), value 1791
Event: time 1281110375.402781, -------------- Report Sync ------------
Event: time 1281110375.482765, type 3 (Absolute), code 4 (Ry), value 2555
Event: time 1281110375.482791, type 3 (Absolute), code 5 (Rz), value 1817
Event: time 1281110375.482797, -------------- Report Sync ------------
Event: time 1281110375.514778, type 3 (Absolute), code 4 (Ry), value 2554
Event: time 1281110375.514812, type 3 (Absolute), code 5 (Rz), value 1843
Event: time 1281110375.514820, -------------- Report Sync ------------
Event: time 1281110375.530788, type 3 (Absolute), code 4 (Ry), value 2552
Event: time 1281110375.530817, type 3 (Absolute), code 5 (Rz), value 1870
Event: time 1281110375.530823, -------------- Report Sync ------------
Event: time 1281110375.554803, type 3 (Absolute), code 4 (Ry), value 2548
Event: time 1281110375.554830, type 3 (Absolute), code 5 (Rz), value 1898
Event: time 1281110375.554836, -------------- Report Sync ------------
Event: time 1281110375.562828, type 3 (Absolute), code 4 (Ry), value 2546
Event: time 1281110375.562856, type 3 (Absolute), code 5 (Rz), value 1920
Event: time 1281110375.562862, -------------- Report Sync ------------
Event: time 1281110375.570830, type 3 (Absolute), code 4 (Ry), value 2544
Event: time 1281110375.570858, type 3 (Absolute), code 5 (Rz), value 1936
Event: time 1281110375.570864, -------------- Report Sync ------------
Event: time 1281110375.586817, type 3 (Absolute), code 4 (Ry), value 2543
Event: time 1281110375.586844, type 3 (Absolute), code 5 (Rz), value 1962
Event: time 1281110375.586850, -------------- Report Sync ------------
Event: time 1281110375.602820, type 3 (Absolute), code 4 (Ry), value 2542
Event: time 1281110375.602848, type 3 (Absolute), code 5 (Rz), value 1991
Event: time 1281110375.602854, -------------- Report Sync ------------
Event: time 1281110375.618827, type 3 (Absolute), code 4 (Ry), value 2541
Event: time 1281110375.618856, type 3 (Absolute), code 5 (Rz), value 2017
Event: time 1281110375.618862, -------------- Report Sync ------------
Event: time 1281110375.642860, type 3 (Absolute), code 4 (Ry), value 2542
Event: time 1281110375.642887, type 3 (Absolute), code 5 (Rz), value 2044
Event: time 1281110375.642893, -------------- Report Sync ------------
Event: time 1281110375.666870, type 3 (Absolute), code 4 (Ry), value 2543
Event: time 1281110375.666899, type 3 (Absolute), code 5 (Rz), value 2070
Event: time 1281110375.666905, -------------- Report Sync ------------
Event: time 1281110375.682864, type 3 (Absolute), code 5 (Rz), value 2096
Event: time 1281110375.682886, -------------- Report Sync ------------
Event: time 1281110375.714872, type 3 (Absolute), code 4 (Ry), value 2544
Event: time 1281110375.714899, type 3 (Absolute), code 5 (Rz), value 2122
Event: time 1281110375.714904, -------------- Report Sync ------------
Event: time 1281110375.762897, type 3 (Absolute), code 4 (Ry), value 2546
Event: time 1281110375.762926, type 3 (Absolute), code 5 (Rz), value 2148
Event: time 1281110375.762932, -------------- Report Sync ------------
Event: time 1281110375.850937, type 3 (Absolute), code 4 (Ry), value 2548
Event: time 1281110375.850964, type 3 (Absolute), code 5 (Rz), value 2174
Event: time 1281110375.850970, -------------- Report Sync ------------
Event: time 1281110375.898965, type 3 (Absolute), code 4 (Ry), value 2550
Event: time 1281110375.899005, type 3 (Absolute), code 5 (Rz), value 2200
Event: time 1281110375.899013, -------------- Report Sync ------------
Event: time 1281110376.067038, type 3 (Absolute), code 4 (Ry), value 2565
Event: time 1281110376.067068, type 3 (Absolute), code 5 (Rz), value 2225
Event: time 1281110376.067074, -------------- Report Sync ------------
Event: time 1281110376.131065, type 3 (Absolute), code 4 (Ry), value 2580
Event: time 1281110376.131092, type 3 (Absolute), code 5 (Rz), value 2230
Event: time 1281110376.131098, -------------- Report Sync ------------
Event: time 1281110376.171107, type 3 (Absolute), code 4 (Ry), value 2595
Event: time 1281110376.171135, type 3 (Absolute), code 5 (Rz), value 2222
Event: time 1281110376.171141, -------------- Report Sync ------------
Event: time 1281110376.195094, type 3 (Absolute), code 4 (Ry), value 2610
Event: time 1281110376.195119, type 3 (Absolute), code 5 (Rz), value 2207
Event: time 1281110376.195125, -------------- Report Sync ------------
Event: time 1281110376.219106, type 3 (Absolute), code 4 (Ry), value 2625
Event: time 1281110376.219134, type 3 (Absolute), code 5 (Rz), value 2185
Event: time 1281110376.219140, -------------- Report Sync ------------
Event: time 1281110376.235119, type 3 (Absolute), code 4 (Ry), value 2640
Event: time 1281110376.235145, type 3 (Absolute), code 5 (Rz), value 2161
Event: time 1281110376.235151, -------------- Report Sync ------------
Event: time 1281110376.259153, type 3 (Absolute), code 4 (Ry), value 2654
Event: time 1281110376.259182, type 3 (Absolute), code 5 (Rz), value 2134
Event: time 1281110376.259188, -------------- Report Sync ------------
Event: time 1281110376.267156, type 3 (Absolute), code 4 (Ry), value 2660
Event: time 1281110376.267184, type 3 (Absolute), code 5 (Rz), value 2121
Event: time 1281110376.267190, -------------- Report Sync ------------
Event: time 1281110376.291158, type 3 (Absolute), code 4 (Ry), value 2671
Event: time 1281110376.291186, type 3 (Absolute), code 5 (Rz), value 2094
Event: time 1281110376.291192, -------------- Report Sync ------------
Event: time 1281110376.299171, type 3 (Absolute), code 4 (Ry), value 2681
Event: time 1281110376.299199, type 3 (Absolute), code 5 (Rz), value 2067
Event: time 1281110376.299205, -------------- Report Sync ------------
Event: time 1281110376.315161, type 3 (Absolute), code 4 (Ry), value 2692
Event: time 1281110376.315196, type 3 (Absolute), code 5 (Rz), value 2039
Event: time 1281110376.315203, -------------- Report Sync ------------
Event: time 1281110376.323177, type 3 (Absolute), code 4 (Ry), value 2701
Event: time 1281110376.323204, type 3 (Absolute), code 5 (Rz), value 2013
Event: time 1281110376.323210, -------------- Report Sync ------------
Event: time 1281110376.339162, type 3 (Absolute), code 4 (Ry), value 2710
Event: time 1281110376.339190, type 3 (Absolute), code 5 (Rz), value 1987
Event: time 1281110376.339196, -------------- Report Sync ------------
Event: time 1281110376.355171, type 3 (Absolute), code 4 (Ry), value 2720
Event: time 1281110376.355199, type 3 (Absolute), code 5 (Rz), value 1959
Event: time 1281110376.355205, -------------- Report Sync ------------
Event: time 1281110376.371178, type 3 (Absolute), code 4 (Ry), value 2729
Event: time 1281110376.371205, type 3 (Absolute), code 5 (Rz), value 1933
Event: time 1281110376.371211, -------------- Report Sync ------------
Event: time 1281110376.387188, type 3 (Absolute), code 4 (Ry), value 2740
Event: time 1281110376.387215, type 3 (Absolute), code 5 (Rz), value 1900
Event: time 1281110376.387220, -------------- Report Sync ------------
Event: time 1281110376.395216, type 3 (Absolute), code 4 (Ry), value 2743
Event: time 1281110376.395244, type 3 (Absolute), code 5 (Rz), value 1888
Event: time 1281110376.395250, -------------- Report Sync ------------
Event: time 1281110376.403206, type 3 (Absolute), code 4 (Ry), value 2747
Event: time 1281110376.403243, type 3 (Absolute), code 5 (Rz), value 1875
Event: time 1281110376.403249, -------------- Report Sync ------------
Event: time 1281110376.411222, type 3 (Absolute), code 4 (Ry), value 2749
Event: time 1281110376.411252, type 3 (Absolute), code 5 (Rz), value 1868
Event: time 1281110376.411258, -------------- Report Sync ------------
Event: time 1281110376.419227, type 3 (Absolute), code 4 (Ry), value 2754
Event: time 1281110376.419254, type 3 (Absolute), code 5 (Rz), value 1853
Event: time 1281110376.419260, -------------- Report Sync ------------
Event: time 1281110376.427229, type 3 (Absolute), code 4 (Ry), value 2756
Event: time 1281110376.427256, type 3 (Absolute), code 5 (Rz), value 1845
Event: time 1281110376.427262, -------------- Report Sync ------------
Event: time 1281110376.435235, type 3 (Absolute), code 4 (Ry), value 2759
Event: time 1281110376.435264, type 3 (Absolute), code 5 (Rz), value 1837
Event: time 1281110376.435270, -------------- Report Sync ------------
Event: time 1281110376.443230, type 3 (Absolute), code 4 (Ry), value 2767
Event: time 1281110376.443256, type 3 (Absolute), code 5 (Rz), value 1810
Event: time 1281110376.443262, -------------- Report Sync ------------
Event: time 1281110376.459218, type 3 (Absolute), code 4 (Ry), value 2775
Event: time 1281110376.459245, type 3 (Absolute), code 5 (Rz), value 1784
Event: time 1281110376.459251, -------------- Report Sync ------------
Event: time 1281110376.467243, type 3 (Absolute), code 4 (Ry), value 2783
Event: time 1281110376.467270, type 3 (Absolute), code 5 (Rz), value 1758
Event: time 1281110376.467276, -------------- Report Sync ------------
Event: time 1281110376.475252, type 3 (Absolute), code 4 (Ry), value 2793
Event: time 1281110376.475280, type 3 (Absolute), code 5 (Rz), value 1732
Event: time 1281110376.475286, -------------- Report Sync ------------
Event: time 1281110376.491234, type 3 (Absolute), code 4 (Ry), value 2805
Event: time 1281110376.491260, type 3 (Absolute), code 5 (Rz), value 1704
Event: time 1281110376.491265, -------------- Report Sync ------------
Event: time 1281110376.507241, type 3 (Absolute), code 4 (Ry), value 2817
Event: time 1281110376.507269, type 3 (Absolute), code 5 (Rz), value 1678
Event: time 1281110376.507275, -------------- Report Sync ------------
Event: time 1281110376.539254, type 3 (Absolute), code 4 (Ry), value 2829
Event: time 1281110376.539282, type 3 (Absolute), code 5 (Rz), value 1652
Event: time 1281110376.539288, -------------- Report Sync ------------
Event: time 1281110376.571269, type 3 (Absolute), code 4 (Ry), value 2844
Event: time 1281110376.571296, type 3 (Absolute), code 5 (Rz), value 1630
Event: time 1281110376.571302, -------------- Report Sync ------------
Event: time 1281110376.611315, type 3 (Absolute), code 4 (Ry), value 2859
Event: time 1281110376.611344, type 3 (Absolute), code 5 (Rz), value 1618
Event: time 1281110376.611350, -------------- Report Sync ------------
Event: time 1281110376.643325, type 3 (Absolute), code 4 (Ry), value 2874
Event: time 1281110376.643357, type 3 (Absolute), code 5 (Rz), value 1615
Event: time 1281110376.643363, -------------- Report Sync ------------
Event: time 1281110376.675342, type 3 (Absolute), code 4 (Ry), value 2889
Event: time 1281110376.675369, type 3 (Absolute), code 5 (Rz), value 1619
Event: time 1281110376.675375, -------------- Report Sync ------------
Event: time 1281110376.707335, type 3 (Absolute), code 4 (Ry), value 2904
Event: time 1281110376.707364, type 3 (Absolute), code 5 (Rz), value 1630
Event: time 1281110376.707370, -------------- Report Sync ------------
Event: time 1281110376.747352, type 3 (Absolute), code 4 (Ry), value 2919
Event: time 1281110376.747379, type 3 (Absolute), code 5 (Rz), value 1649
Event: time 1281110376.747384, -------------- Report Sync ------------
Event: time 1281110376.755371, type 3 (Absolute), code 4 (Ry), value 2921
Event: time 1281110376.755408, type 3 (Absolute), code 5 (Rz), value 1655
Event: time 1281110376.755414, -------------- Report Sync ------------
Event: time 1281110376.763390, type 3 (Absolute), code 4 (Ry), value 2923
Event: time 1281110376.763419, type 3 (Absolute), code 5 (Rz), value 1658
Event: time 1281110376.763425, -------------- Report Sync ------------
Event: time 1281110376.771389, type 3 (Absolute), code 4 (Ry), value 2926
Event: time 1281110376.771417, type 3 (Absolute), code 5 (Rz), value 1665
Event: time 1281110376.771423, -------------- Report Sync ------------
Event: time 1281110376.779395, type 3 (Absolute), code 4 (Ry), value 2928
Event: time 1281110376.779422, type 3 (Absolute), code 5 (Rz), value 1668
Event: time 1281110376.779428, -------------- Report Sync ------------
Event: time 1281110376.795376, type 3 (Absolute), code 4 (Ry), value 2936
Event: time 1281110376.795405, type 3 (Absolute), code 5 (Rz), value 1688
Event: time 1281110376.795411, -------------- Report Sync ------------
Event: time 1281110376.803406, type 3 (Absolute), code 4 (Ry), value 2940
Event: time 1281110376.803434, type 3 (Absolute), code 5 (Rz), value 1697
Event: time 1281110376.803440, -------------- Report Sync ------------
Event: time 1281110376.811409, type 3 (Absolute), code 4 (Ry), value 2944
Event: time 1281110376.811436, type 3 (Absolute), code 5 (Rz), value 1711
Event: time 1281110376.811443, -------------- Report Sync ------------
Event: time 1281110376.819406, type 3 (Absolute), code 4 (Ry), value 2946
Event: time 1281110376.819433, type 3 (Absolute), code 5 (Rz), value 1716
Event: time 1281110376.819440, -------------- Report Sync ------------
Event: time 1281110376.835415, type 3 (Absolute), code 4 (Ry), value 2955
Event: time 1281110376.835443, type 3 (Absolute), code 5 (Rz), value 1744
Event: time 1281110376.835449, -------------- Report Sync ------------
Event: time 1281110376.867406, type 3 (Absolute), code 4 (Ry), value 2960
Event: time 1281110376.867433, type 3 (Absolute), code 5 (Rz), value 1771
Event: time 1281110376.867439, -------------- Report Sync ------------
Event: time 1281110376.899422, type 3 (Absolute), code 4 (Ry), value 2958
Event: time 1281110376.899448, type 3 (Absolute), code 5 (Rz), value 1798
Event: time 1281110376.899454, -------------- Report Sync ------------
Event: time 1281110376.931450, type 3 (Absolute), code 4 (Ry), value 2956
Event: time 1281110376.931488, type 3 (Absolute), code 5 (Rz), value 1826
Event: time 1281110376.931494, -------------- Report Sync ------------
Event: time 1281110376.955448, type 3 (Absolute), code 4 (Ry), value 2953
Event: time 1281110376.955474, type 3 (Absolute), code 5 (Rz), value 1852
Event: time 1281110376.955480, -------------- Report Sync ------------
Event: time 1281110376.979459, type 3 (Absolute), code 4 (Ry), value 2948
Event: time 1281110376.979486, type 3 (Absolute), code 5 (Rz), value 1879
Event: time 1281110376.979492, -------------- Report Sync ------------
Event: time 1281110377.003471, type 3 (Absolute), code 4 (Ry), value 2941
Event: time 1281110377.003498, type 3 (Absolute), code 5 (Rz), value 1906
Event: time 1281110377.003504, -------------- Report Sync ------------
Event: time 1281110377.019482, type 3 (Absolute), code 4 (Ry), value 2932
Event: time 1281110377.019515, type 3 (Absolute), code 5 (Rz), value 1934
Event: time 1281110377.019521, -------------- Report Sync ------------
Event: time 1281110377.027502, type 3 (Absolute), code 4 (Ry), value 2929
Event: time 1281110377.027530, type 3 (Absolute), code 5 (Rz), value 1944
Event: time 1281110377.027536, -------------- Report Sync ------------
Event: time 1281110377.043489, type 3 (Absolute), code 4 (Ry), value 2920
Event: time 1281110377.043515, type 3 (Absolute), code 5 (Rz), value 1972
Event: time 1281110377.043521, -------------- Report Sync ------------
Event: time 1281110377.059499, type 3 (Absolute), code 4 (Ry), value 2911
Event: time 1281110377.059526, type 3 (Absolute), code 5 (Rz), value 1998
Event: time 1281110377.059532, -------------- Report Sync ------------
Event: time 1281110377.067527, type 3 (Absolute), code 4 (Ry), value 2901
Event: time 1281110377.067556, type 3 (Absolute), code 5 (Rz), value 2025
Event: time 1281110377.067562, -------------- Report Sync ------------
Event: time 1281110377.091514, type 3 (Absolute), code 4 (Ry), value 2890
Event: time 1281110377.091542, type 3 (Absolute), code 5 (Rz), value 2051
Event: time 1281110377.091548, -------------- Report Sync ------------
Event: time 1281110377.107525, type 3 (Absolute), code 4 (Ry), value 2877
Event: time 1281110377.107563, type 3 (Absolute), code 5 (Rz), value 2078
Event: time 1281110377.107569, -------------- Report Sync ------------
Event: time 1281110377.131530, type 3 (Absolute), code 4 (Ry), value 2863
Event: time 1281110377.131559, type 3 (Absolute), code 5 (Rz), value 2105
Event: time 1281110377.131565, -------------- Report Sync ------------
Event: time 1281110377.155541, type 3 (Absolute), code 4 (Ry), value 2847
Event: time 1281110377.155569, type 3 (Absolute), code 5 (Rz), value 2132
Event: time 1281110377.155575, -------------- Report Sync ------------
Event: time 1281110377.179553, type 3 (Absolute), code 4 (Ry), value 2832
Event: time 1281110377.179584, type 3 (Absolute), code 5 (Rz), value 2154
Event: time 1281110377.179590, -------------- Report Sync ------------
Event: time 1281110377.195604, type 3 (Absolute), code 4 (Ry), value 2816
Event: time 1281110377.195651, type 3 (Absolute), code 5 (Rz), value 2175
Event: time 1281110377.195660, -------------- Report Sync ------------
Event: time 1281110377.219571, type 3 (Absolute), code 4 (Ry), value 2801
Event: time 1281110377.219600, type 3 (Absolute), code 5 (Rz), value 2195
Event: time 1281110377.219606, -------------- Report Sync ------------
Event: time 1281110377.227599, type 3 (Absolute), code 4 (Ry), value 2785
Event: time 1281110377.227631, type 3 (Absolute), code 5 (Rz), value 2213
Event: time 1281110377.227637, -------------- Report Sync ------------
Event: time 1281110377.251585, type 3 (Absolute), code 4 (Ry), value 2769
Event: time 1281110377.251616, type 3 (Absolute), code 5 (Rz), value 2233
Event: time 1281110377.251622, -------------- Report Sync ------------
Event: time 1281110377.275603, type 3 (Absolute), code 4 (Ry), value 2754
Event: time 1281110377.275630, type 3 (Absolute), code 5 (Rz), value 2250
Event: time 1281110377.275636, -------------- Report Sync ------------
Event: time 1281110377.291631, type 3 (Absolute), code 4 (Ry), value 2738
Event: time 1281110377.291659, type 3 (Absolute), code 5 (Rz), value 2267
Event: time 1281110377.291665, -------------- Report Sync ------------
Event: time 1281110377.315636, type 3 (Absolute), code 4 (Ry), value 2723
Event: time 1281110377.315664, type 3 (Absolute), code 5 (Rz), value 2281
Event: time 1281110377.315670, -------------- Report Sync ------------
Event: time 1281110377.323643, type 3 (Absolute), code 4 (Ry), value 2715
Event: time 1281110377.323670, type 3 (Absolute), code 5 (Rz), value 2289
Event: time 1281110377.323676, -------------- Report Sync ------------
Event: time 1281110377.339626, type 3 (Absolute), code 4 (Ry), value 2708
Event: time 1281110377.339654, type 3 (Absolute), code 5 (Rz), value 2296
Event: time 1281110377.339660, -------------- Report Sync ------------
Event: time 1281110377.371644, type 3 (Absolute), code 4 (Ry), value 2693
Event: time 1281110377.371679, type 3 (Absolute), code 5 (Rz), value 2313
Event: time 1281110377.371685, -------------- Report Sync ------------
Event: time 1281110377.651772, type 3 (Absolute), code 4 (Ry), value 2678
Event: time 1281110377.651801, type 3 (Absolute), code 5 (Rz), value 2332
Event: time 1281110377.651807, -------------- Report Sync ------------
Event: time 1281110377.691790, type 3 (Absolute), code 4 (Ry), value 2663
Event: time 1281110377.691816, type 3 (Absolute), code 5 (Rz), value 2345
Event: time 1281110377.691822, -------------- Report Sync ------------
Event: time 1281110377.715801, type 3 (Absolute), code 4 (Ry), value 2648
Event: time 1281110377.715830, type 3 (Absolute), code 5 (Rz), value 2358
Event: time 1281110377.715836, -------------- Report Sync ------------
Event: time 1281110377.739814, type 3 (Absolute), code 4 (Ry), value 2632
Event: time 1281110377.739843, type 3 (Absolute), code 5 (Rz), value 2371
Event: time 1281110377.739849, -------------- Report Sync ------------
Event: time 1281110377.755830, type 3 (Absolute), code 4 (Ry), value 2616
Event: time 1281110377.755860, type 3 (Absolute), code 5 (Rz), value 2384
Event: time 1281110377.755866, -------------- Report Sync ------------
Event: time 1281110377.771827, type 3 (Absolute), code 4 (Ry), value 2601
Event: time 1281110377.771853, type 3 (Absolute), code 5 (Rz), value 2397
Event: time 1281110377.771859, -------------- Report Sync ------------
Event: time 1281110377.787863, type 3 (Absolute), code 4 (Ry), value 2586
Event: time 1281110377.787892, type 3 (Absolute), code 5 (Rz), value 2409
Event: time 1281110377.787898, -------------- Report Sync ------------
Event: time 1281110377.795865, type 3 (Absolute), code 4 (Ry), value 2570
Event: time 1281110377.795893, type 3 (Absolute), code 5 (Rz), value 2422
Event: time 1281110377.795899, -------------- Report Sync ------------
Event: time 1281110377.811848, type 3 (Absolute), code 4 (Ry), value 2554
Event: time 1281110377.811874, type 3 (Absolute), code 5 (Rz), value 2435
Event: time 1281110377.811880, -------------- Report Sync ------------
Event: time 1281110377.827878, type 3 (Absolute), code 4 (Ry), value 2539
Event: time 1281110377.827909, type 3 (Absolute), code 5 (Rz), value 2447
Event: time 1281110377.827915, -------------- Report Sync ------------
Event: time 1281110377.843911, type 3 (Absolute), code 4 (Ry), value 2524
Event: time 1281110377.843947, type 3 (Absolute), code 5 (Rz), value 2459
Event: time 1281110377.843955, -------------- Report Sync ------------
Event: time 1281110377.851890, type 3 (Absolute), code 4 (Ry), value 2507
Event: time 1281110377.851919, type 3 (Absolute), code 5 (Rz), value 2472
Event: time 1281110377.851925, -------------- Report Sync ------------
Event: time 1281110377.867872, type 3 (Absolute), code 4 (Ry), value 2492
Event: time 1281110377.867897, type 3 (Absolute), code 5 (Rz), value 2484
Event: time 1281110377.867903, -------------- Report Sync ------------
Event: time 1281110377.875896, type 3 (Absolute), code 4 (Ry), value 2470
Event: time 1281110377.875924, type 3 (Absolute), code 5 (Rz), value 2503
Event: time 1281110377.875930, -------------- Report Sync ------------
Event: time 1281110377.883899, type 3 (Absolute), code 4 (Ry), value 2459
Event: time 1281110377.883925, type 3 (Absolute), code 5 (Rz), value 2514
Event: time 1281110377.883931, -------------- Report Sync ------------
Event: time 1281110377.891909, type 3 (Absolute), code 4 (Ry), value 2444
Event: time 1281110377.891935, type 3 (Absolute), code 5 (Rz), value 2529
Event: time 1281110377.891941, -------------- Report Sync ------------
Event: time 1281110377.899911, type 3 (Absolute), code 4 (Ry), value 2414
Event: time 1281110377.899939, type 3 (Absolute), code 5 (Rz), value 2559
Event: time 1281110377.899945, -------------- Report Sync ------------
Event: time 1281110377.907912, type 3 (Absolute), code 4 (Ry), value 2395
Event: time 1281110377.907940, type 3 (Absolute), code 5 (Rz), value 2580
Event: time 1281110377.907946, -------------- Report Sync ------------
Event: time 1281110377.923898, type 3 (Absolute), code 4 (Ry), value 2376
Event: time 1281110377.923925, type 3 (Absolute), code 5 (Rz), value 2602
Event: time 1281110377.923931, -------------- Report Sync ------------
Event: time 1281110377.931915, type 3 (Absolute), code 4 (Ry), value 2360
Event: time 1281110377.931942, type 3 (Absolute), code 5 (Rz), value 2619
Event: time 1281110377.931948, -------------- Report Sync ------------
Event: time 1281110377.947909, type 3 (Absolute), code 4 (Ry), value 2328
Event: time 1281110377.947937, type 3 (Absolute), code 5 (Rz), value 2654
Event: time 1281110377.947943, -------------- Report Sync ------------
Event: time 1281110377.955939, type 3 (Absolute), code 4 (Ry), value 2313
Event: time 1281110377.955967, type 3 (Absolute), code 5 (Rz), value 2670
Event: time 1281110377.955973, -------------- Report Sync ------------
Event: time 1281110377.963947, type 3 (Absolute), code 4 (Ry), value 2294
Event: time 1281110377.963976, type 3 (Absolute), code 5 (Rz), value 2691
Event: time 1281110377.963983, -------------- Report Sync ------------
Event: time 1281110377.971947, type 3 (Absolute), code 4 (Ry), value 2275
Event: time 1281110377.971974, type 3 (Absolute), code 5 (Rz), value 2711
Event: time 1281110377.971980, -------------- Report Sync ------------
Event: time 1281110377.979950, type 3 (Absolute), code 4 (Ry), value 2260
Event: time 1281110377.979976, type 3 (Absolute), code 5 (Rz), value 2727
Event: time 1281110377.979982, -------------- Report Sync ------------
Event: time 1281110377.987949, type 3 (Absolute), code 4 (Ry), value 2243
Event: time 1281110377.987976, type 3 (Absolute), code 5 (Rz), value 2746
Event: time 1281110377.987982, -------------- Report Sync ------------
Event: time 1281110377.995951, type 3 (Absolute), code 4 (Ry), value 2226
Event: time 1281110377.995979, type 3 (Absolute), code 5 (Rz), value 2763
Event: time 1281110377.995985, -------------- Report Sync ------------
Event: time 1281110378.011940, type 3 (Absolute), code 4 (Ry), value 2203
Event: time 1281110378.011966, type 3 (Absolute), code 5 (Rz), value 2784
Event: time 1281110378.011972, -------------- Report Sync ------------
Event: time 1281110378.019968, type 3 (Absolute), code 4 (Ry), value 2191
Event: time 1281110378.019995, type 3 (Absolute), code 5 (Rz), value 2794
Event: time 1281110378.020001, -------------- Report Sync ------------
Event: time 1281110378.035974, type 3 (Absolute), code 4 (Ry), value 2176
Event: time 1281110378.036006, type 3 (Absolute), code 5 (Rz), value 2804
Event: time 1281110378.036012, -------------- Report Sync ------------
Event: time 1281110378.051982, type 3 (Absolute), code 4 (Ry), value 2160
Event: time 1281110378.052011, type 3 (Absolute), code 5 (Rz), value 2815
Event: time 1281110378.052017, -------------- Report Sync ------------
Event: time 1281110378.059984, type 3 (Absolute), code 4 (Ry), value 2141
Event: time 1281110378.060011, type 3 (Absolute), code 5 (Rz), value 2827
Event: time 1281110378.060017, -------------- Report Sync ------------
Event: time 1281110378.067991, type 3 (Absolute), code 4 (Ry), value 2123
Event: time 1281110378.068019, type 3 (Absolute), code 5 (Rz), value 2837
Event: time 1281110378.068025, -------------- Report Sync ------------
Event: time 1281110378.083991, type 3 (Absolute), code 4 (Ry), value 2105
Event: time 1281110378.084019, type 3 (Absolute), code 5 (Rz), value 2846
Event: time 1281110378.084025, -------------- Report Sync ------------
Event: time 1281110378.092002, type 3 (Absolute), code 4 (Ry), value 2090
Event: time 1281110378.092030, type 3 (Absolute), code 5 (Rz), value 2851
Event: time 1281110378.092036, -------------- Report Sync ------------
Event: time 1281110378.116009, type 3 (Absolute), code 4 (Ry), value 2074
Event: time 1281110378.116036, type 3 (Absolute), code 5 (Rz), value 2858
Event: time 1281110378.116043, -------------- Report Sync ------------
Event: time 1281110378.156005, type 3 (Absolute), code 4 (Ry), value 2059
Event: time 1281110378.156031, type 3 (Absolute), code 5 (Rz), value 2864
Event: time 1281110378.156037, -------------- Report Sync ------------
Event: time 1281110378.308075, type 3 (Absolute), code 4 (Ry), value 2058
Event: time 1281110378.308104, type 3 (Absolute), code 5 (Rz), value 2845
Event: time 1281110378.308110, -------------- Report Sync ------------
Event: time 1281110378.348101, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110378.348122, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1281110378.348150, -------------- Report Sync ------------
Event: time 1281110378.748287, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110378.748320, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1281110378.748348, type 3 (Absolute), code 4 (Ry), value 2463
Event: time 1281110378.748362, type 3 (Absolute), code 5 (Rz), value 1998
Event: time 1281110378.748369, -------------- Report Sync ------------
Event: time 1281110378.756301, type 3 (Absolute), code 4 (Ry), value 2464
Event: time 1281110378.756345, type 3 (Absolute), code 5 (Rz), value 2000
Event: time 1281110378.756353, -------------- Report Sync ------------
Event: time 1281110378.764308, type 3 (Absolute), code 4 (Ry), value 2465
Event: time 1281110378.764353, type 3 (Absolute), code 5 (Rz), value 2001
Event: time 1281110378.764361, -------------- Report Sync ------------
Event: time 1281110378.772335, type 3 (Absolute), code 4 (Ry), value 2466
Event: time 1281110378.772372, type 3 (Absolute), code 5 (Rz), value 2003
Event: time 1281110378.772380, -------------- Report Sync ------------
Event: time 1281110378.780315, type 3 (Absolute), code 4 (Ry), value 2468
Event: time 1281110378.780360, type 3 (Absolute), code 5 (Rz), value 2004
Event: time 1281110378.780368, -------------- Report Sync ------------
Event: time 1281110378.788336, type 3 (Absolute), code 4 (Ry), value 2469
Event: time 1281110378.788375, -------------- Report Sync ------------
Event: time 1281110378.796325, type 3 (Absolute), code 5 (Rz), value 2005
Event: time 1281110378.796360, -------------- Report Sync ------------
Event: time 1281110378.804355, type 3 (Absolute), code 4 (Ry), value 2470
Event: time 1281110378.804389, type 3 (Absolute), code 5 (Rz), value 2006
Event: time 1281110378.804395, -------------- Report Sync ------------
Event: time 1281110378.812342, type 3 (Absolute), code 4 (Ry), value 2472
Event: time 1281110378.812382, type 3 (Absolute), code 5 (Rz), value 2008
Event: time 1281110378.812394, -------------- Report Sync ------------
Event: time 1281110378.828326, type 3 (Absolute), code 4 (Ry), value 2473
Event: time 1281110378.828369, -------------- Report Sync ------------
Event: time 1281110378.836367, type 3 (Absolute), code 4 (Ry), value 2474
Event: time 1281110378.836413, type 3 (Absolute), code 5 (Rz), value 2007
Event: time 1281110378.836419, -------------- Report Sync ------------
Event: time 1281110378.844344, type 3 (Absolute), code 4 (Ry), value 2473
Event: time 1281110378.844389, type 3 (Absolute), code 5 (Rz), value 2005
Event: time 1281110378.844397, -------------- Report Sync ------------
Event: time 1281110378.852355, type 3 (Absolute), code 5 (Rz), value 2004
Event: time 1281110378.852393, -------------- Report Sync ------------
Event: time 1281110378.860386, type 3 (Absolute), code 5 (Rz), value 2002
Event: time 1281110378.860431, -------------- Report Sync ------------
Event: time 1281110378.876390, type 3 (Absolute), code 5 (Rz), value 2001
Event: time 1281110378.876430, -------------- Report Sync ------------
Event: time 1281110378.892383, type 3 (Absolute), code 5 (Rz), value 2002
Event: time 1281110378.892411, -------------- Report Sync ------------
Event: time 1281110378.900416, type 3 (Absolute), code 5 (Rz), value 2003
Event: time 1281110378.900455, -------------- Report Sync ------------
Event: time 1281110378.940371, type 3 (Absolute), code 4 (Ry), value 2474
Event: time 1281110378.940402, -------------- Report Sync ------------
Event: time 1281110378.964379, type 3 (Absolute), code 4 (Ry), value 2475
Event: time 1281110378.964412, -------------- Report Sync ------------
Event: time 1281110378.980410, type 3 (Absolute), code 4 (Ry), value 2476
Event: time 1281110378.980442, -------------- Report Sync ------------
Event: time 1281110378.996403, type 3 (Absolute), code 5 (Rz), value 2004
Event: time 1281110378.996424, -------------- Report Sync ------------
Event: time 1281110379.004419, type 3 (Absolute), code 5 (Rz), value 2003
Event: time 1281110379.004444, -------------- Report Sync ------------
Event: time 1281110379.012439, type 3 (Absolute), code 5 (Rz), value 2002
Event: time 1281110379.012462, -------------- Report Sync ------------
Event: time 1281110379.028419, type 3 (Absolute), code 5 (Rz), value 2003
Event: time 1281110379.028440, -------------- Report Sync ------------
Event: time 1281110379.036442, type 3 (Absolute), code 5 (Rz), value 2004
Event: time 1281110379.036464, -------------- Report Sync ------------
Event: time 1281110379.044446, type 3 (Absolute), code 5 (Rz), value 2005
Event: time 1281110379.044469, -------------- Report Sync ------------
Event: time 1281110379.052452, type 3 (Absolute), code 5 (Rz), value 2006
Event: time 1281110379.052476, -------------- Report Sync ------------
Event: time 1281110379.060458, type 3 (Absolute), code 5 (Rz), value 2007
Event: time 1281110379.060481, -------------- Report Sync ------------
Event: time 1281110379.068457, type 3 (Absolute), code 5 (Rz), value 2008
Event: time 1281110379.068479, -------------- Report Sync ------------
Event: time 1281110379.076459, type 3 (Absolute), code 4 (Ry), value 2477
Event: time 1281110379.076487, type 3 (Absolute), code 5 (Rz), value 2010
Event: time 1281110379.076493, -------------- Report Sync ------------
Event: time 1281110379.084463, type 3 (Absolute), code 5 (Rz), value 2011
Event: time 1281110379.084487, -------------- Report Sync ------------
Event: time 1281110379.108454, type 3 (Absolute), code 5 (Rz), value 2012
Event: time 1281110379.108476, -------------- Report Sync ------------
Event: time 1281110379.148473, type 3 (Absolute), code 5 (Rz), value 2014
Event: time 1281110379.148495, -------------- Report Sync ------------
Event: time 1281110379.156505, type 3 (Absolute), code 5 (Rz), value 2017
Event: time 1281110379.156529, -------------- Report Sync ------------
Event: time 1281110379.164508, type 3 (Absolute), code 5 (Rz), value 2020
Event: time 1281110379.164531, -------------- Report Sync ------------
Event: time 1281110379.172497, type 3 (Absolute), code 4 (Ry), value 2478
Event: time 1281110379.172524, type 3 (Absolute), code 5 (Rz), value 2024
Event: time 1281110379.172530, -------------- Report Sync ------------
Event: time 1281110379.180521, type 3 (Absolute), code 5 (Rz), value 2025
Event: time 1281110379.180548, -------------- Report Sync ------------
Event: time 1281110379.212496, type 3 (Absolute), code 4 (Ry), value 2483
Event: time 1281110379.212525, type 3 (Absolute), code 5 (Rz), value 2051
Event: time 1281110379.212531, -------------- Report Sync ------------
Event: time 1281110379.244522, type 3 (Absolute), code 4 (Ry), value 2490
Event: time 1281110379.244553, type 3 (Absolute), code 5 (Rz), value 2079
Event: time 1281110379.244559, -------------- Report Sync ------------
Event: time 1281110379.260520, type 3 (Absolute), code 4 (Ry), value 2499
Event: time 1281110379.260548, type 3 (Absolute), code 5 (Rz), value 2106
Event: time 1281110379.260554, -------------- Report Sync ------------
Event: time 1281110379.284537, type 3 (Absolute), code 4 (Ry), value 2510
Event: time 1281110379.284566, type 3 (Absolute), code 5 (Rz), value 2132
Event: time 1281110379.284572, -------------- Report Sync ------------
Event: time 1281110379.292559, type 3 (Absolute), code 4 (Ry), value 2522
Event: time 1281110379.292587, type 3 (Absolute), code 5 (Rz), value 2160
Event: time 1281110379.292593, -------------- Report Sync ------------
Event: time 1281110379.300563, type 3 (Absolute), code 4 (Ry), value 2532
Event: time 1281110379.300591, type 3 (Absolute), code 5 (Rz), value 2181
Event: time 1281110379.300597, -------------- Report Sync ------------
Event: time 1281110379.308568, type 3 (Absolute), code 4 (Ry), value 2541
Event: time 1281110379.308596, type 3 (Absolute), code 5 (Rz), value 2199
Event: time 1281110379.308603, -------------- Report Sync ------------
Event: time 1281110379.316571, type 3 (Absolute), code 4 (Ry), value 2549
Event: time 1281110379.316599, type 3 (Absolute), code 5 (Rz), value 2217
Event: time 1281110379.316605, -------------- Report Sync ------------
Event: time 1281110379.324575, type 3 (Absolute), code 4 (Ry), value 2559
Event: time 1281110379.324602, type 3 (Absolute), code 5 (Rz), value 2238
Event: time 1281110379.324608, -------------- Report Sync ------------
Event: time 1281110379.332577, type 3 (Absolute), code 4 (Ry), value 2567
Event: time 1281110379.332604, type 3 (Absolute), code 5 (Rz), value 2254
Event: time 1281110379.332610, -------------- Report Sync ------------
Event: time 1281110379.340577, type 3 (Absolute), code 4 (Ry), value 2578
Event: time 1281110379.340604, type 3 (Absolute), code 5 (Rz), value 2279
Event: time 1281110379.340610, -------------- Report Sync ------------
Event: time 1281110379.348581, type 3 (Absolute), code 4 (Ry), value 2585
Event: time 1281110379.348608, type 3 (Absolute), code 5 (Rz), value 2296
Event: time 1281110379.348614, -------------- Report Sync ------------
Event: time 1281110379.356589, type 3 (Absolute), code 4 (Ry), value 2598
Event: time 1281110379.356617, type 3 (Absolute), code 5 (Rz), value 2332
Event: time 1281110379.356623, -------------- Report Sync ------------
Event: time 1281110379.364580, type 3 (Absolute), code 4 (Ry), value 2608
Event: time 1281110379.364607, type 3 (Absolute), code 5 (Rz), value 2363
Event: time 1281110379.364613, -------------- Report Sync ------------
Event: time 1281110379.372596, type 3 (Absolute), code 4 (Ry), value 2619
Event: time 1281110379.372624, type 3 (Absolute), code 5 (Rz), value 2400
Event: time 1281110379.372630, -------------- Report Sync ------------
Event: time 1281110379.380600, type 3 (Absolute), code 4 (Ry), value 2629
Event: time 1281110379.380628, type 3 (Absolute), code 5 (Rz), value 2448
Event: time 1281110379.380634, -------------- Report Sync ------------
Event: time 1281110379.388602, type 3 (Absolute), code 4 (Ry), value 2635
Event: time 1281110379.388628, type 3 (Absolute), code 5 (Rz), value 2492
Event: time 1281110379.388634, -------------- Report Sync ------------
Event: time 1281110379.396604, type 3 (Absolute), code 4 (Ry), value 2640
Event: time 1281110379.396633, type 3 (Absolute), code 5 (Rz), value 2538
Event: time 1281110379.396639, -------------- Report Sync ------------
Event: time 1281110379.404617, type 3 (Absolute), code 4 (Ry), value 2644
Event: time 1281110379.404651, type 3 (Absolute), code 5 (Rz), value 2574
Event: time 1281110379.404657, -------------- Report Sync ------------
Event: time 1281110379.412618, type 3 (Absolute), code 4 (Ry), value 2648
Event: time 1281110379.412645, type 3 (Absolute), code 5 (Rz), value 2617
Event: time 1281110379.412652, -------------- Report Sync ------------
Event: time 1281110379.420612, type 3 (Absolute), code 4 (Ry), value 2653
Event: time 1281110379.420638, type 3 (Absolute), code 5 (Rz), value 2675
Event: time 1281110379.420644, -------------- Report Sync ------------
Event: time 1281110379.444592, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110379.444613, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1281110379.444638, -------------- Report Sync ------------
Event: time 1281110380.757230, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110380.757256, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1281110380.757275, type 3 (Absolute), code 4 (Ry), value 2642
Event: time 1281110380.757285, type 3 (Absolute), code 5 (Rz), value 1968
Event: time 1281110380.757291, -------------- Report Sync ------------
Event: time 1281110380.765231, type 3 (Absolute), code 4 (Ry), value 2643
Event: time 1281110380.765262, -------------- Report Sync ------------
Event: time 1281110380.773253, type 3 (Absolute), code 4 (Ry), value 2642
Event: time 1281110380.773292, type 3 (Absolute), code 5 (Rz), value 1967
Event: time 1281110380.773301, -------------- Report Sync ------------
Event: time 1281110380.789234, type 3 (Absolute), code 5 (Rz), value 1965
Event: time 1281110380.789254, -------------- Report Sync ------------
Event: time 1281110380.829260, type 3 (Absolute), code 4 (Ry), value 2639
Event: time 1281110380.829291, type 3 (Absolute), code 5 (Rz), value 1974
Event: time 1281110380.829299, -------------- Report Sync ------------
Event: time 1281110380.837273, type 3 (Absolute), code 4 (Ry), value 2638
Event: time 1281110380.837305, type 3 (Absolute), code 5 (Rz), value 1981
Event: time 1281110380.837314, -------------- Report Sync ------------
Event: time 1281110380.845275, type 3 (Absolute), code 4 (Ry), value 2635
Event: time 1281110380.845306, type 3 (Absolute), code 5 (Rz), value 1998
Event: time 1281110380.845313, -------------- Report Sync ------------
Event: time 1281110380.853279, type 3 (Absolute), code 4 (Ry), value 2633
Event: time 1281110380.853309, type 3 (Absolute), code 5 (Rz), value 2008
Event: time 1281110380.853316, -------------- Report Sync ------------
Event: time 1281110380.861307, type 3 (Absolute), code 4 (Ry), value 2631
Event: time 1281110380.861352, type 3 (Absolute), code 5 (Rz), value 2025
Event: time 1281110380.861360, -------------- Report Sync ------------
Event: time 1281110380.869289, type 3 (Absolute), code 4 (Ry), value 2628
Event: time 1281110380.869321, type 3 (Absolute), code 5 (Rz), value 2038
Event: time 1281110380.869330, -------------- Report Sync ------------
Event: time 1281110380.877289, type 3 (Absolute), code 4 (Ry), value 2625
Event: time 1281110380.877320, type 3 (Absolute), code 5 (Rz), value 2057
Event: time 1281110380.877328, -------------- Report Sync ------------
Event: time 1281110380.885295, type 3 (Absolute), code 4 (Ry), value 2622
Event: time 1281110380.885326, type 3 (Absolute), code 5 (Rz), value 2072
Event: time 1281110380.885334, -------------- Report Sync ------------
Event: time 1281110380.893300, type 3 (Absolute), code 4 (Ry), value 2617
Event: time 1281110380.893332, type 3 (Absolute), code 5 (Rz), value 2098
Event: time 1281110380.893340, -------------- Report Sync ------------
Event: time 1281110380.909284, type 3 (Absolute), code 4 (Ry), value 2611
Event: time 1281110380.909313, type 3 (Absolute), code 5 (Rz), value 2127
Event: time 1281110380.909320, -------------- Report Sync ------------
Event: time 1281110380.933297, type 3 (Absolute), code 4 (Ry), value 2606
Event: time 1281110380.933326, type 3 (Absolute), code 5 (Rz), value 2155
Event: time 1281110380.933333, -------------- Report Sync ------------
Event: time 1281110380.957333, type 3 (Absolute), code 4 (Ry), value 2602
Event: time 1281110380.957366, type 3 (Absolute), code 5 (Rz), value 2187
Event: time 1281110380.957374, -------------- Report Sync ------------
Event: time 1281110380.973315, type 3 (Absolute), code 4 (Ry), value 2599
Event: time 1281110380.973346, type 3 (Absolute), code 5 (Rz), value 2217
Event: time 1281110380.973354, -------------- Report Sync ------------
Event: time 1281110380.981337, type 3 (Absolute), code 4 (Ry), value 2597
Event: time 1281110380.981368, type 3 (Absolute), code 5 (Rz), value 2245
Event: time 1281110380.981377, -------------- Report Sync ------------
Event: time 1281110380.997326, type 3 (Absolute), code 4 (Ry), value 2594
Event: time 1281110380.997357, type 3 (Absolute), code 5 (Rz), value 2273
Event: time 1281110380.997366, -------------- Report Sync ------------
Event: time 1281110381.005351, type 3 (Absolute), code 4 (Ry), value 2592
Event: time 1281110381.005381, type 3 (Absolute), code 5 (Rz), value 2300
Event: time 1281110381.005389, -------------- Report Sync ------------
Event: time 1281110381.013355, type 3 (Absolute), code 4 (Ry), value 2590
Event: time 1281110381.013388, type 3 (Absolute), code 5 (Rz), value 2326
Event: time 1281110381.013396, -------------- Report Sync ------------
Event: time 1281110381.021357, type 3 (Absolute), code 4 (Ry), value 2588
Event: time 1281110381.021388, type 3 (Absolute), code 5 (Rz), value 2355
Event: time 1281110381.021397, -------------- Report Sync ------------
Event: time 1281110381.037344, type 3 (Absolute), code 4 (Ry), value 2585
Event: time 1281110381.037373, type 3 (Absolute), code 5 (Rz), value 2382
Event: time 1281110381.037382, -------------- Report Sync ------------
Event: time 1281110381.061354, type 3 (Absolute), code 4 (Ry), value 2584
Event: time 1281110381.061387, type 3 (Absolute), code 5 (Rz), value 2409
Event: time 1281110381.061396, -------------- Report Sync ------------
Event: time 1281110381.101396, type 3 (Absolute), code 4 (Ry), value 2585
Event: time 1281110381.101428, type 3 (Absolute), code 5 (Rz), value 2435
Event: time 1281110381.101437, -------------- Report Sync ------------
Event: time 1281110381.141392, type 3 (Absolute), code 4 (Ry), value 2586
Event: time 1281110381.141425, type 3 (Absolute), code 5 (Rz), value 2461
Event: time 1281110381.141433, -------------- Report Sync ------------
Event: time 1281110381.197421, type 3 (Absolute), code 4 (Ry), value 2583
Event: time 1281110381.197453, type 3 (Absolute), code 5 (Rz), value 2471
Event: time 1281110381.197461, -------------- Report Sync ------------
Event: time 1281110381.205443, type 3 (Absolute), code 4 (Ry), value 2582
Event: time 1281110381.205475, type 3 (Absolute), code 5 (Rz), value 2470
Event: time 1281110381.205483, -------------- Report Sync ------------
Event: time 1281110381.245429, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110381.245451, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1281110381.245485, -------------- Report Sync ------------
Event: time 1281110381.693662, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1281110381.693684, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1281110381.693710, type 3 (Absolute), code 4 (Ry), value 2030
Event: time 1281110381.693724, type 3 (Absolute), code 5 (Rz), value 2245
Event: time 1281110381.693732, -------------- Report Sync ------------
Event: time 1281110381.701655, type 3 (Absolute), code 5 (Rz), value 2246
Event: time 1281110381.701670, -------------- Report Sync ------------
Event: time 1281110381.861720, type 3 (Absolute), code 4 (Ry), value 2015
```

---

### Post by Plippo on 2010-08-06
Just create (with root rights) a file with any name that ends with .conf (e.g. touchscreen.conf) in /etc/modprobe.d with the following content:
```
options usbhid quirks=0x0486:0x0186:0x0040
```

This should do the trick.

---

### Post by jtjs on 2010-08-07
> **Plippo said:**
> Just create (with root rights) a file with any name that ends with .conf (e.g. touchscreen.conf) in /etc/modprobe.d with the following content:
```
options usbhid quirks=0x0486:0x0186:0x0040
```

This should do the trick.

fortunately for cyberblade, at least his screen isn't on the "hid should never handle this device" list, like the t91mt's screen is(which necessitates a driver rebuild to take it off that list, and put it on the "hid has a special driver for this" list)..

---

### Post by Phyxs on 2010-08-08
> **Plippo said:**
> Just create (with root rights) a file with any name that ends with .conf (e.g. touchscreen.conf) in /etc/modprobe.d with the following content:
```
options usbhid quirks=0x0486:0x0186:0x0040
```This should do the trick.

Just got my T101MT yesterday, and running dualboot with ubuntu netbook. I stil am a bit of a linux newbie, so bare with me. I tried the above, but it seems the file doesn't get read at boot or something. It just doesn't work. However if i do it manually with rmmod ... and modprobe ... it does.

Here is what i get with lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So i wrote:
```
options usbhid quirks=0x0eef:0x480d:0x0040
```
in a file: /etc/modprobe.d/touchscreen.conf which i created as root.

---

### Post by Plippo on 2010-08-08
Hi Phyxs,

you're lucky, your T101MT uses the good old eGalax touchscreen so you don't have to use the quirks but can use the multitouch driver as described here: [http://ubuntuforums.org/showpost.php?p=9210836&postcount=1](http://ubuntuforums.org/showpost.php?p=9210836&postcount=1)

---

### Post by Phyxs on 2010-08-09
Thanks for the info! I'll give it a try a.s.a.p.
 
Edit:
Works great, thanks again! Now i have a new problem. When i use the touchrotate script, the screen is rotated correct, but the touchscreen is not. When i put my finger on the screen the cursor show up at a different location. When the screen is rotated 180 degrees the cursor is mirrored through the center of the screen (i hope you understand, a bit difficult to explain since english is not my native language).

---

### Post by tlimsisnw on 2010-08-10
After recent updates (kernel and all), I found that I could not use onboard to enter the password upon returning to the screen after suspend. Anyone has the same problem? Found a solution? Guess I have to just flip the screen over and use the keyboard in the meantime.

---

### Post by atomp on 2010-08-11
Just a short but general question on the hardware front to get a little perspective.

How strong are the hinges on everyones T101MT's?

I've been finding that using the device in laptop setup, unless the base is horizontal then some wiggling will cause the screen to drop back as the weight of the screen overpowers the strength of the hinge,I do understand that it is likely to happen because of the weight of the screen and the fact that it is just one hinge. 

Has anyone else had this issue? Or have I just ended up with a weak hinge? (In which case I'll be contacting Asus).

---

### Post by Phyxs on 2010-08-11
Well i got mine only a few days ago, but sofar no problems with the hinge. No matter how far i open the window, it stays in that position.

---

### Post by tlimsisnw on 2010-08-15
Plippo: Regarding not being able to use the onboard touchscreen to enter password upon returning after suspend, I found a semi-fix, i.e. by using a quick hard press with my finger nail or the stylus. That seems to work better, but still weird. Previously I just needed a soft touch on the screen. Might this have to do with the updated touch driver?

---

### Post by tlimsisnw on 2010-08-15
> **tlimsisnw said:**
> Plippo: Regarding not being able to use the onboard touchscreen to enter password upon returning after suspend, I found a semi-fix, i.e. by using a quick hard press with my finger nail or the stylus. That seems to work better, but still weird. Previously I just needed a soft touch on the screen. Might this have to do with the updated touch driver?

Hmm, after attaching a mouse, I discovered that the "quick hard press" above is actually a double-click. So onboard now requires the equivalent of a double-click to work. Is this a problem with onboard or the mouse driver?

---

### Post by Plippo on 2010-08-16
@atomp:
Although I bought the T101MT in the first week it was available, I have no problem with the hinge. In "normal Laptop position", opened for around 100°, I can use the touch screen without problems if I don't press too hard. If I open the screen more, it gets a bit fragile, but if I don't touch it it's okay.

@tlimsisnw:
Do you also need to double-click if you use onboard on the normal desktop? There, onboard works normally for me. I can't confirm the behaviour in the unlock screen as I use CellWriter there. If you want to try CellWriter for the unlock dialog, I can tell you how to do it.

---

### Post by tlimsisnw on 2010-08-16
Plippo: Onboard works normally otherwise. Just that it did work well previously. I didn't know how to make cellwriter appear in the unlock screen. Please enlighten, thanks. I'd prefer cellwriter too. However, it did notice that cellwriter occasionally crashes or fails to take inputs (by writing, typing on the key are ok usually) and had to be restarted. Is there a bug in cellwriter too?

---

### Post by Plippo on 2010-08-16
@tlimsisnw: Yes, occasional CellWriter crashes occur to me too, this seems to be a bug in CellWriter.

But if you trust it enough to use it to unlock your screen, please prepare for enlightenment:
Press Alt+F2 and enter **gconf-editor**
Navigate to **/apps/gnome-screensaver**
Set the value of **embedded_keyboard_command** to the following value:
```
/usr/bin/cellwriter --xid --keyboard-only
```Make sure **embedded_keyboard_enabled** is checked.

This should do the trick, and hopefully CellWriter accepts single clicks.

@mrspacklecrisp:
Sorry, I overlooked your message, just want to report that the microphone works for me using this method. I checked with audacity and found out that the signals from the two channels of the stereo microphone are inverse, meaning that the right channel is almost exactly the opposite of the left channel, which makes them result in a constant value of 0 when added. But I'm no ALSA expert, so I don't know if there is a possibility to make it invert one channel so we wouldn't have to mute one and could have stereo input.

---

### Post by tlimsisnw on 2010-08-16
Plippo: Thanks for the enlightenment. Got cellwriter up for the screenlock. However, I still need to double click to get the keys to work. Seem like the problem is elsewhere. Any ideas?

---

### Post by Plippo on 2010-08-20
@tlimsisnw: This is indeed a strange behaviour. Have you chosen any screen saver or are you seeing the normal blank screen behind the unlock dialog box?
Another thing you could try would be to create a new user profile and check if the problem occurs there, too.

---

### Post by tlimsisnw on 2010-08-20
Plippo: I'm using the blank screen. I created a new user and the onscreen keyboard works normally. Have to figure out what's wrong with my current profile.

---

### Post by Kevrox on 2010-08-22
HI all
Great thread and thank you all so much for all the pointers. I have this lovely little toy and had lucid running in no time, loved the quick screen rotate scripts.

I have now installed Ububtu 10.10 alpha3, the touch screen works out of the box however the no screen rotate. The scripts in the first part of this thread do not work I tried to install the egalax-multitouch-driver-common.deb, it di dnot want to.

I would love to know how to set the little button on the screen next to on off slider marked, express gate and windows rotate to do the rotation for ubuntu. also I am struggling to find a nice easy on screen keyboard, I have used onboard and a few others, CellWriter I think,

any way thank for any response, keep up the great work.
cheers
kev

---

### Post by Kevrox on 2010-08-24
hi again, forget my last post above, gone back to lucid, all good except i cannot seem to get the twofing bit working, have followed the instructions here  [https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH) bit no dice with any gesture or RH click.... anything I need to try or check, another thing is it possible to use the small express gate button on the screen to map or define a screen rotate with these commands here [https://help.ubuntu.com/community/T101MT#TO%20ROTATE%20THE%20SCREEN:](https://help.ubuntu.com/community/T101MT#TO%20ROTATE%20THE%20SCREEN:)
cheers kev, THANK YOU for all your effort.

---

### Post by Plippo on 2010-08-24
Hi Kev,
at the moment it's better you use Lucid as Maverick is still in heavy development.

What happens when you enter **twofing --debug** in the terminal? This should result in some information in the terminal window you could post.

For the button, you can use the ubuntu keyboard shortcut program, add a new shortcut, set** touchrotate right** as the command, then click on the right column and press the rotation button. This should set the shortcut. You have to enable the special keys before as described in [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT).

Regards
Plippo

---

### Post by Kevrox on 2010-08-24
Thank you for your reply mate, i agree about staying with lucid, here is the output of twofing --debug
:~$ twofing --debug
Input device name: "eGalax Inc. USB TouchController"
XInput device id is 10.
Found window with id 10485761 and class 'gnome-session' 
Found window with id 12582913 and class '<unknown>' 
Found window with id 14680065 and class 'gnome-settings-daemon' 
Found window with id 18874369 and class 'metacity' 
Found window with id 18874383 and class 'metacity' 
Found window with id 23068673 and class 'gnome-power-manager' 
Found window with id 27262977 and class 'nm-applet' 
Found window with id 29360129 and class 'polkit-gnome-authentication-agent-1' 
Found window with id 31457281 and class 'gnome-panel' 
Found window with id 33554433 and class 'bluetooth-applet' 
Found window with id 39845889 and class 'nautilus' 
Found window with id 39845920 and class 'desktop_window' 
Found window with id 31457283 and class 'gnome-panel' 
Found window with id 31457356 and class 'gnome-panel' 
Found window with id 56623105 and class 'gnome-screensaver' 
Found window with id 62914561 and class 'trashapplet' 
Found window with id 60817409 and class 'wnck-applet' 
Found window with id 65011713 and class 'notification-area-applet' 
Found window with id 67108865 and class 'indicator-applet-session' 
Found window with id 79691777 and class 'notify-osd' 
Found window with id 85983233 and class 'gdu-notification-daemon' 
Found window with id 25165825 and class 'firefox-bin' 
Found window with id 25165969 and class 'Toplevel' 
Found window with id 25166012 and class 'firefox-bin' 
Found window with id 25166042 and class 'firefox-bin' 
Found window with id 25166085 and class 'firefox-bin' 
Found window with id 25166487 and class 'Popup' 
Found window with id 25166490 and class 'Popup' 
Found window with id 25166493 and class 'Popup' 
Found window with id 25166496 and class 'Popup' 
Found window with id 25166499 and class 'Popup' 
Found window with id 25166502 and class 'Popup' 
Found window with id 25166505 and class 'Popup' 
Found window with id 90177537 and class 'applet.py' 
Found window with id 25179066 and class 'firefox-bin' 
Found window with id 94371841 and class 'update-notifier' 
Found window with id 25194716 and class 'Popup' 
Found window with id 25166343 and class 'Popup' 
Found window with id 25246553 and class 'Popup' 
Found window with id 25266999 and class 'Popup' 
Found window with id 25267002 and class 'Popup' 
Found window with id 25273629 and class 'Popup' 
Found window with id 25273682 and class 'Popup' 
Found window with id 98566145 and class 'gnome-terminal' 
Reading input from device ... (interrupt to exit)

I may also not be doing the 2 finger thing correctly, but i would expect say 1st finger touch then as second finger touches and holds a right click type menu would appear, or a point 1 finger and hold and then the right click menu would appear.

as for this htps://help.ubuntu.com/community/T101MT I have used this page more often than I can count, I have also started a thread on whirlpool [http://forums.whirlpool.net.au/forum-replies.cfm?t=1504082](http://forums.whirlpool.net.au/forum-replies.cfm?t=1504082) .

once again thanks you for all your great effort.
kev

---

### Post by Plippo on 2010-08-25
The output looks alright, so it seems to work. The right click menu will only appear when you release both fingers, maybe that's the problem.

---

### Post by Kevrox on 2010-08-25
ok this will be a very dumb question,
what is the sequence of touches on the screen that are needed. This is my first touch device other than a Toshiba PDA, Imate jam, both windows driven.?
is it possible to get the single point and hold to get the rh click menu?

cheers kev

got the rotate screen button working thanks

---

### Post by Kevrox on 2010-08-25
another question, does anyone know of a "windows penwrite"type entry for ubuntu?

---

### Post by riccardo.depalo on 2010-08-25
Hi everybody. @Kevrox: I read you went back to Lucid, but are you still using the 2.6.32.24 default kernel? I had to downgrade from the 2.6.35 I tried before, because the twofing daemon doesn't seem to work with the built-in driver in that kernel. 

@Plippo: did you try the newer kernel anyway? it's still giving problems with twofing, I tried with some xinput commands but no way. the only way using the screen is killing the daemon.

---

### Post by bakinsoda on 2010-08-25
Hi everyone,

Gmail now has Voice and Video available for Linux.  Have you guys tried it?  On this netbook, the video again is upside down.  Any suggestions on how this should be handle?

Vinh

---

### Post by Kevrox on 2010-08-25
> **bakinsoda said:**
> Hi everyone,

On this netbook, the video again is upside down.  Any suggestions on how this should be handle?

Vinh

[https://help.ubuntu.com/community/T101MT#IF%20THE%20CAMERA%20IS%20UPSIDE%20DOWN](https://help.ubuntu.com/community/T101MT#IF%20THE%20CAMERA%20IS%20UPSIDE%20DOWN)
worked for me

---

### Post by Kevrox on 2010-08-25
[QUOTE=riccardo.depalo;9764872]Hi everybody. @Kevrox: I read you went back to Lucid, but are you still using the 2.6.32.24 default kernel? I had to downgrade from the 2.6.35 I tried before, because the twofing daemon doesn't seem to work with the built-in driver in that kernel. 


Yes I am still using the latest for lucid not 2.6.35, I also found that the rotate screen command did not work either with the 35 kernel.

---

### Post by bakinsoda on 2010-08-25
> **Kevrox said:**
> [https://help.ubuntu.com/community/T101MT#IF%20THE%20CAMERA%20IS%20UPSIDE%20DOWN](https://help.ubuntu.com/community/T101MT#IF%20THE%20CAMERA%20IS%20UPSIDE%20DOWN)
worked for me

Did that before.  Works for skype, but not Gmail's voice and video plugin.  Can anyone confirm this fix or my issue?  Upside down video in Gmail Video

---

### Post by Plippo on 2010-08-26
@bakinsoda: Maybe it helps to start your browser using
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox
```
(replace firefox with the name of your browser if you use another one) like it is done with skype. At least this works for me with websites that use the flash plugin to access your webcam, but I don't know what plugin Gmail uses.

@kev: It's simple, just press with your two fingers and release them, you don't have to do it in any special order. Maybe you didn't press hard enough.
The only handwriting recognition for Linux I know is CellWriter, but i guess it's not like PenWrite as you have to write in the cells.

@riccardo: I haven't tried it yet, but I will soon do so. My guess is that the new kernel uses some quriks wrongly causing the screen to ignore the multi-touch driver. It shouldn't be too hard to fix it, but I have to try some things out.

---

### Post by bakinsoda on 2010-08-26
Thanks, putting the LD_PRELOAD statement works.

I tried to set that environment variable in ~/.profile so that it is always used (even when programs are launched from the GUI), however, it doesn't appear to pick up (I have other environment variables defined in there too that works).

Any reason why LD_PRELOAD doesn't work this way?

---

### Post by Kevrox on 2010-08-27
[QUOTE=
@kev: It's simple, just press with your two fingers and release them, you don't have to do it in any special order. Maybe you didn't press hard enough.
[/QUOTE]

No dice, I thought as much about it being that simple. ok, I guess it is time to eliminate things, what is the best application to attempt this. Should it work on the desktop screen where one would press the RH click on the mouse and get "create launcher, create folder" etc menu. or is there a better one to try. 
cheers
kev

---

### Post by Plippo on 2010-08-27
The desktop is maybe not the right place to test it. I use Ubuntu netbook Edition, so there is no desktop for me, thus I haven't tested it there. You can for example try the file manager, right click should open a menu with "New File", "New Folder", "Preferences" and so on. In the image viewer (EOG) you should be able to zoom in/out using the common two-finger zoom gesture.

If it doesn't work, could you please run the command **xinput --list** in the terminal and look if the eGalax screen appears there multiple times? That's a sign of the problem also causing twofing not to work in Maverick.

---

### Post by Kevrox on 2010-08-27
my output

:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=11	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

---

### Post by Kevrox on 2010-08-27
I also have the twofing --wait entered at boot time in start applications, is this correct?

---

### Post by Plippo on 2010-08-27
That's exactly how it should look, I don't know why it doesn't work for you. If the twofing application is running (which you can check with the system monitor), everything should be fine, which it isn't, which is bad.

If you can wait a few days, I'm currently working on a new version of twofing which will also contain more debug information, maybe that can help.

---

### Post by Kevrox on 2010-08-27
Mate you are a champ, I look forward to it. I will continue to tweak. In the Win7 home that is running on it that aspect works well, especially the point and hold to get the rh click menu.... a work in progress, BUT well worth the wait. When I have all programs running in ubuntu it only uses about 15% of ram, that is with 4 desktops and all with an application running, windows runs at 50% +, and lags with response to touch.
again thank you for your help.

---

### Post by Kevrox on 2010-08-27
> **Plippo said:**
>  If the twofing application is running (which you can check with the system monitor)

System monitor says twofing status sleeping, waiting channel evdev_read
if that helps?

---

### Post by riccardo.depalo on 2010-08-28
@Plippo, I was trying new Maverick system in T101MT (I'm too curious) and after recent updates, I've been able to launch correctly your twofing daemon, with 2.6.35.19 kernel. Debug asked me to make calibration (I installed only that), and I gave the default values on terminal. After all gestures seemed to work. I don't know if it is because of some update (I tried also new uTouch for testing, I don't think it's related), but in xinput list I have now only two values for eGalax, id10 and 11, instead of three id numbers :) The strange thing is that... it seems I have to recalibrate at every boot! 


Still problems, anyway, for the screen rotation feature. I couldn't load egalax common deb file because of software conflicts.

For whoever interested (beta version is coming) there are still many annoying bugs in Maverick in Alpha3 install tried by me. If you want to try, it's at your own risk. I couldn't install a working mypaint, for example. Gdebi program doesn't work and I had to use dpkg to load deb files. And I had to follow the same workarounds of Lucid to get full brightness and special keys working and to get webcam screen not upside down. It seems it isn't solved yet.

---

### Post by riccardo.depalo on 2010-08-29
@Plippo: ok, I know why your twofing daemon works now. I had loaded by mistake one of the kernel deb files you posted but NOT the common deb file. There is something in the first that doesn't change the kernel, but permits 2.6.35 to recognize your daemon. Instead, in the common file (the one with rotate scripts) there must be something wrong for new kernel. If I load it with the other kernel deb file, touchfing doesn't work.
Have a good weekend!

P.s. for the touchrotate issue, I noticed it changes screen position in Maverick, but it's not usable with touchscreen or touchpad, even if I reset the calibration. Maybe there is a different axes configuration.

---

### Post by Plippo on 2010-08-29
@kev: No, this all looks alright, so it should work, don't know why it doesn't...

@riccardo: I've also tested Maverick now and figured out the bugs causing the touchscreen not to work properly. They are easy to fix, I've created two patches for the Kernel and a bug report in launchpad, hopefully they'll apply the fixes before the release of Maverick. I'll also send the patches upstream to the kernel. With the patches, also calibration will no longer be necessary as the correct coordinates will be sent.

@all: To help the patch to get into maverick so we can have a fully working driver for the T101MT in the Kernel, **it would be great if everyone who has a launchpad account could register as affected by the bug**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511)

---

### Post by Kevrox on 2010-08-29
> **Plippo said:**
> 

@all: To help the patch to get into maverick so we can have a fully working driver for the T101MT in the Kernel, **it would be great if everyone who has a launchpad account could register as affected by the bug**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511)

Done:D

---

### Post by riccardo.depalo on 2010-08-29
@Plippo: thanks for your work, I added also myself to the bug as affected.

---

### Post by gltripp on 2010-08-29
Hi there!

are there any news about the "AsusTek" driver and getting MultiTouch working?

I think, I have got the same controller like Cyberblade:

```
lsusb
[B]Bus 005 Device 002: ID 0b05:1788 ASUSTek Computer, Inc. 
[/B]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13d3:5111 IMC Networks 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Single-Touch workes (with help of these quirks-option for usbhid-module).

Any ideas ?

---

### Post by TH_ on 2010-08-30
[Two finger scrolling with the touchpad](https://help.ubuntu.com/community/T101MT#TWO%20FINGER%20SCROLLING%20WITH%20THE%20TOUCHPAD) doesn't works any more. Any idea?

---

### Post by Plippo on 2010-08-30
Thanks for your help with the bug report! Let's hope it gets recognized.

@gltripp: Sorry, no news about it. I'd recommend informing Stéphane Chatty about this new device, he's the developer of (almost) all the Linux multitouch drivers. You find his mail address on [http://lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://lii-enac.fr/en/projects/shareit/multitouch-devices.html) . He also developed the eGalax driver for the "old" T101MTs. But be sure to report the right one: The touchscreen device is the one with the ID **0486:0186 ASUS Computers, Inc. **
The *ASUSTek* device is the bluetooth module which seems to be the same on all T101MT models and works out of the box.
If Stéphane gives you some test code and you need help compiling, I can send you a modified version my build script.

@TH_: Do you mean it no longer works in Maverick or did it stop working in Lucid for you?

---

### Post by TH_ on 2010-08-30
> **Plippo said:**
> @TH_: Do you mean it no longer works in Maverick or did it stop working in Lucid for you?
It did stop working in Lucid Lynx after a reboot. I can't remember whether I have previously made an update.

---

### Post by Kevrox on 2010-08-31
Would using any of these drivers be worth a try?
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
or eeepc t101mt ones as per this thread?

---

### Post by Plippo on 2010-08-31
@Kev: What do you expect from these drivers? They don't support multitouch.

---

### Post by Kevrox on 2010-08-31
ah ok, thought it might help with the RH click option I am not getting on this device, just trying and tweaking things till they either break or work well.:D

---

### Post by TH_ on 2010-08-31
Now it works again. Mysterious....

---

### Post by Kevrox on 2010-08-31
ok this is very strange. I have not installed much this arvo, gimp only I was just having another go at the 2 finger touch gesture thing and hay presto, I had the rh click menu worked the pinch zoom worked in FF then I got all excited, and before I posted that it was all good I rebooted and now it's not working again. I had 2 finger zoom, and 2 finger pan up and down......

---

### Post by Kevrox on 2010-08-31
ok, I seem to be able to get the rh click menu very occasionally. In nautilus filemanager I can touch 1 finger and and tap with the second and may be 1 in every 30 goes it will show the menu rh click menu. if I touch with 2 fingers with a space of say 3cm and lift the higher finger I get a drag square, like a highlight drag box. Is there a terminal command to see what output there is on the fly or a pressure sensetivitey option, or do i need to change my mouse settings accessibility options for 2nd click.

I know it is not meant to be this hard, I was even thinking a faulty touch screen but all good in windows 7.

---

### Post by riccardo.depalo on 2010-08-31
@Plippo: this is very strange. Without your patch installed, twofing works sometimes, but not always, if I give the input calibration default code:```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```

---

### Post by Kevrox on 2010-08-31
> **riccardo.depalo said:**
> @Plippo: this is very strange. Without your patch installed, twofing works sometimes, but not always, if I give the input calibration default code:```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```

Ricciardo, because of your post I have now finally managed to get the two finger rh click with menu to work. running the code finally made it work.

Finally.....:P  I love forums,

---

### Post by Kevrox on 2010-08-31
Bugger, I rebooted and no dice..... oh well trial and error

---

### Post by riccardo.depalo on 2010-08-31
> **Kevrox said:**
> Bugger, I rebooted and no dice..... oh well trial and error

yes the problem is that it seems you have to repeat xinput calibration at every boot.

---

### Post by Kevrox on 2010-09-01
there is a new up date, have not installed yet, waiting on Plippo update first

4 hours later I installed the latest updates, touch still works but still no rh click menu

8 hours later
read through the whole thread... I can not get the 2 finger gesture and rh click to work at all, Any pointers to check other than the ones mentioned before?

---

### Post by Plippo on 2010-09-01
Yes, calibration can be a real issue. That's why the new patch I created for the Kernel driver (which I added to the Launchpad bug report) will make calibration unnecessary. I will upload a new version of the Kernel module with the patch soon, but the current version of twofing won't work with it, so I'm working on the new version now. It should be ready in the next days. Thanks for your patience!

@riccardo: You mean in Lucid or in Karmic? In Karmic it should never work without the patch as the wrong events are being sent. It Lucid it will probably work if the calibration is applied before twofing is loaded. But that won't be an issue any more with the patched driver.

@Kev: The updated Kernel shouldn't need new drivers. But I don't think it will solve your problem. Just wait for the new module, I hope it will fix all issues related to calibration.

---

### Post by riccardo.depalo on 2010-09-01
@Plippo: I meant in Maverick... kernel 2.6.35-19. Are you going to make a new twofing for this distribution? I enjoyied the daemon very much, it's quite useful. I see bugs are being fixed in Maverick, so I think I will stay with 10.10 until the final release (and your gentle updates, of course). Thank you.

---

### Post by Kevrox on 2010-09-01
Thanks Plippo
I am tempted to go to 10.10 as well, even beta that will be out very very soon, BUT I guess then we start all over again.... I am trying to get this T101TM to work well as I need it on the shop floor to help customers. I am using virtual box or terminal server client to run our store stock software and the copy and paste rh click menu is vital and is all that is stopping me. 

Once this is sorted I will remove windows and have a Linux only base OS
Cheers Kev

---

### Post by riccardo.depalo on 2010-09-02
@Kevrox: don't go to Maverick if you need a stable system. Twofing doesn't work yet well with new kernel. In october there will be the final release. I'm wondering: which kernel do you use? if you use 2.6.35 there are still problems with multitouch. Otherwise, if you follow the first page of this thread you should not have problems also with right click. Did you see the wiki?
 
[https://help.ubuntu.com/community/T101MT#EXPERIMENTAL TWO-FINGER TOUCH](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL TWO-FINGER TOUCH)

@Plippo: did you see the new Utouch multitouch experimental software for Ubuntu? it seems it is going to be released for Maverick. Is it an alternative to your daemon or is it going to work with it?

---

### Post by Kevrox on 2010-09-02
> **riccardo.depalo said:**
> @Kevrox: don't go to Maverick if you need a stable system. Twofing doesn't work yet well with new kernel. In october there will be the final release. I'm wondering: which kernel do you use? if you use 2.6.35 there are still problems with multitouch. Otherwise, if you follow the first page of this thread you should not have problems also with right click. Did you see the wiki?
 
[https://help.ubuntu.com/community/T101MT#EXPERIMENTAL TWO-FINGER TOUCH](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL TWO-FINGER TOUCH)

I am using kernel, 2.6.32-24-generic, I have followed the how to to the letter but I do not seen to have the twofing rh click menu happening. I did have a glimps of it when I ran the calibration  
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
as soon as I ran that it worked a charm, so I am doing the gestures correctly but since the reboot it is not happening, even if I rerun the xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517 I still do not have it working. I tried to run it at every bot with startup application but no good either.

I will keep trying,  thanks for the pointers.
kev

I might even reinstall lucid and start again

---

### Post by riccardo.depalo on 2010-09-02
@Kev: if all you need is right click, go to system/preferences/mouse and select Simulate Secondary Click in Accessibility menu. Just stay with the finger or the stylus on the screen, put it away and the right click menu will appear.:)

---

### Post by Plippo on 2010-09-02
@Kev: This probably is a calibration issue, calibration needs to be applied before twofing is started. But if you wait a bit, there will be a new version of the driver which won't need any calibration any more.

@riccardo: Yes I have read about UTouch, but I haven't tried it yet. Hopefully it will one day be a replacement for twofing, but at the moment it seems that, if it works, it will only work for a few applications. I don't know if it will get along with twofing, or if twofing can be changed to be a plugin for UTouch or something like that, but I will check that. For now, all I can say is that twofing will work on Maverick if UTouch is not installed, but I don't now what happens if you install both.

---

### Post by Plippo on 2010-09-02
So, the **new Kernel module package** is there, you find it in the first post. It uses the new patch I created and thus it's **no longer** **necessary to calibrate the screen**. Old calibration will be deleted when you install the package. If the screen is inaccurate (and only then), you have to calibrate it again with the calibrator, which should still work.

If you use **twofing**, you have to compile and install a new version of it for the new module. You find it, as always, in the legendary [post #77]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77").

---

### Post by Plippo on 2010-09-02
I have also created a new version of the scripts that compile the modules and create the packages. They should also work for the Maverick Kernel now, but I haven't tested it yet. You find them at [http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz](http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz) .

---

### Post by riccardo.depalo on 2010-09-02
@Plippo: when I try to compile twofing in Maverick I get the following error: ```
gcc -c -Wall -O2 twofingemu.c
twofingemu.c:29: fatal error: X11/extensions/Xrandr.h: No such file or directory
compilation terminated.
make: *** [twofingemu.o] Error 1
```

And when I build the deb file for 2.6.35-19 I get this message:

```
BUILDING KERNEL MODULE...
cd: 91: can't cd to linux-source-2.6.32
grep: include/linux/hid.h: No such file or directory
sed: can't read include/linux/hid.h: No such file or directory
Modified hid.h.
cd: 91: can't cd to drivers/hid
grep: hid-core.c: No such file or directory
sed: can't read hid-core.c: No such file or directory
Modified hid-core.c.
grep: usbhid/hid-quirks.c: No such file or directory
hid-quirks.c is already fine.
hid-ids.h is already fine.
Makefile is already fine.
Building modules...
make: Entering directory `/'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/'
Copying...
cp: cannot stat `hid.ko': No such file or directory
cp: cannot stat `hid-egalax.ko': No such file or directory
cp: cannot stat `usbhid/usbhid.ko': No such file or directory
Should have built. Ready to build deb.
BUILDING DEB PACKAGE...
dpkg-deb: generazione del pacchetto "egalax-multitouch-driver-2.6.35-19-generic-i386" in "deb.deb".
SHOULD BE FINISHED.
ric@ric-laptop:~/egalax$ ./build.sh
BUILDING KERNEL MODULE...
cd: 91: can't cd to linux-source-2.6.32
grep: include/linux/hid.h: No such file or directory
sed: can't read include/linux/hid.h: No such file or directory
Modified hid.h.
cd: 91: can't cd to drivers/hid
grep: hid-core.c: No such file or directory
sed: can't read hid-core.c: No such file or directory
Modified hid-core.c.
grep: usbhid/hid-quirks.c: No such file or directory
hid-quirks.c is already fine.
hid-ids.h is already fine.
Makefile is already fine.
Building modules...
make: Entering directory `/'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/'
Copying...
cp: cannot stat `hid.ko': No such file or directory
cp: cannot stat `hid-egalax.ko': No such file or directory
cp: cannot stat `usbhid/usbhid.ko': No such file or directory
Should have built. Ready to build deb.
BUILDING DEB PACKAGE...
dpkg-deb: generazione del pacchetto "egalax-multitouch-driver-2.6.35-19-generic-i386" in "deb.deb".
SHOULD BE FINISHED.

```

it seems it doesn't load modules.

---

### Post by Plippo on 2010-09-02
@riccardo: For the first problem, you probably need to install the packages x11proto-randr-dev and libxrandr-dev. Sorry I forgot to mention that. For the second problem: Seems I had the 2.6.32 hard-coded in the build script. I will try to make it more generic. Thanks for the hint!

---

### Post by Plippo on 2010-09-02
Corrected scripts for Maverick are now online: [http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz](http://philmerk.de/dwl/deb/t101mt-kernel-driver.tar.gz)

---

### Post by riccardo.depalo on 2010-09-02
@Plippo: thanks for the help, twofing compile worked with the two files added, but I still have problems with the deb builder. 

```
BUILDING KERNEL MODULE...
[sudo] password for ric: 
cd: 93: can't cd to linux-source-2.6.35
grep: include/linux/hid.h: No such file or directory
sed: can't read include/linux/hid.h: No such file or directory
Modified hid.h.
cd: 93: can't cd to drivers/hid
grep: hid-core.c: No such file or directory
sed: can't read hid-core.c: No such file or directory
Modified hid-core.c.
grep: usbhid/hid-quirks.c: No such file or directory
hid-quirks.c is already fine.
hid-ids.h is already fine.
Makefile is already fine.
Building modules...
make: Entering directory `/'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/'
Copying...
cp: cannot stat `hid.ko': No such file or directory
cp: cannot stat `hid-egalax.ko': No such file or directory
cp: cannot stat `usbhid/usbhid.ko': No such file or directory
Should have built. Ready to build deb.
BUILDING DEB PACKAGE...
dpkg-deb: generazione del pacchetto "egalax-multitouch-driver-2.6.35-19-generic-i386" in "deb.deb".
SHOULD BE FINISHED.

```

the strange thing is that in /usr/src there are exactly the files it doesn't seem to find. But I see a problem: linux-source-2.6.35 is not a directory, it is a file. And the builder can't "cd" into it.

```
ric@ric-laptop:~/egalax$ cd /usr/src/
ric@ric-laptop:/usr/src$ dir
hid-egalax.c		 linux-headers-2.6.35-19-generic  Makefile
hid-ids.h		 linux-source-2.6.35
linux-headers-2.6.35-19  linux-source-2.6.35.tar.bz2

```

```

```

---

### Post by Plippo on 2010-09-02
EDIT: You were faster :-) If it is a file, how big is it?

---

### Post by riccardo.depalo on 2010-09-02
Linux-source2.6.35, I read on properties, is a text file of 689,5 kb. Hope it's useful...

---

### Post by Plippo on 2010-09-02
This is strange. You could try to rename it:
```
cd /usr/src
sudo mv linux-source-2.6.35 linux-source-2.6.35.bak
```
and then try the build script again.

---

### Post by riccardo.depalo on 2010-09-02
@Plippo: changing the name didn't work. But I reloaded the linux-source-2.6.35 and saw that a 2.6.35 directory was formed. I relaunched ./build.sh, had the same error message of before and I noticed that... the directory has became a file! weird...

---

### Post by Kevrox on 2010-09-03
WAHOOOOOOO, seem I finally got it all working, I did a clean re install of lucid, and went step by step...
 So far after every boot it works, rh click second finger tap, zoom on Fire fox and 2 finger scroll..... many many thanks to you all.
):P:p:D

4 hours later and all still good.... happy happy

---

### Post by Kevrox on 2010-09-03
ok now what? I installed the following and no more 2 finger gestures

sudo apt-get install non-free-codecs ubuntu-restricted-extras libdvdcss2 w32codecs

---

### Post by riccardo.depalo on 2010-09-03
> **Kevrox said:**
> ok now what? I installed the following and no more 2 finger gestures

sudo apt-get install non-free-codecs ubuntu-restricted-extras libdvdcss2 w32codecs

it should not be related. You can't launch twofing on terminal or on boot? did you try to type on terminal twofing --debug and see what happens?

---

### Post by Plippo on 2010-09-03
twofing can sometimes (although rarely) crash for no apparent reasons. If this is the case, press Alt+F2 and enter **twofing** to re-start it. I'm working on that.

---

### Post by gltripp on 2010-09-03
Hi Plippo,

in advice of Stéphane, i patched the kernels hid-mosart driver.
The kernel recognizes the touchscreen without needing these usbhid-quirks, but now its behaving like a touchpad (handled by X.org evdev driver)...

unfortunately, i'm not very familiar with X.org-stuff in deep :-(

evtest reports:

> 
evtest /dev/input/event9
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value     35
      Min        0
      Max     3478
    Event code 1 (Y)
      Value     42
      Min        0
      Max     3478
    Event code 40 (Misc)
      Value      0
      Min        0
      Max      255
    Event code 53 (?)
      Value      0
      Min        0
      Max     3478
    Event code 54 (?)
      Value      0
      Min        0
      Max     3478
    Event code 57 (?)
      Value      0
      Min        0
      Max        2
  Event type 4 (Misc)
    Event code 4 (ScanCode)



any ideas ?

---

### Post by Plippo on 2010-09-03
That looks like a problem I had with the first version of the multitouch eGalax driver, too. At the very end of the function **egalax_input_mapping**, there probably is a line that reads **return 0 **or **return 1**. You can try changing it to **return -1**. Maybe this helps.

---

### Post by StCh on 2010-09-03
> **Plippo said:**
> That looks like a problem I had with the first version of the multitouch eGalax driver, too. 

Plippo, I believe that this time the problem does not lie in the driver. I looked at the output of evdev, and it looks good. I'm not 100% sure, of course. Do you have hints pointing otherwise?

St.

---

### Post by Kevrox on 2010-09-03
Hi all
I think I worked out why my 2finger gestures was not working.
I always auto log on at boot, if I logged out and in again, it worked.
So I set my auto log on to off, now I type in my password and all works. SO perhaps it has something to do with auto log on?

cheers kev

---

### Post by Plippo on 2010-09-04
@St.: If I remember correctly, the problem back then was that the device claimed to support LeftBtn and RightBtn events, so evdev regarded it as a touchpad instead of a touchscreen and configured it for relative pointer movement. In gltripp's evtest output, the LeftBtn and RightBtn events occur again, so I thought this could be related.

@Kev: I also use auto log-in, that shouldn't be the problem. Are you using twofing or twofing --wait as command in the startup applications program?

---

### Post by Kevrox on 2010-09-04
[QUOTE=@Kev: I also use auto log-in, that shouldn't be the problem. Are you using twofing or twofing --wait as command in the startup applications program?[/QUOTE]

Does it matter? If so what is the difference? at the moment I have twofing --wait.

ok it's been working all day the and I have just installed this and rebooted and not working

sudo wget [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install non-free-codecs ubuntu-restricted-extras libdvdcss2 w32codecs

---

### Post by StCh on 2010-09-04
> **Plippo said:**
> @St.: If I remember correctly, the problem back then was that the device claimed to support LeftBtn and RightBtn events, so evdev regarded it as a touchpad instead of a touchscreen ?

Oh, I see. I'll have a look at this, and will probably end up discussing it with Peter Hutterer (he's coming over to Germany and France for a few days).

St.

---

### Post by Plippo on 2010-09-04
@Kev: twofing --wait is the one to use, it will wait with the initialization of the daemon until all services are ready. I don't know if it doesn't work for you sometimes, but it definitely doesn't have anything to do with the packages you installed.

---

### Post by tlimsisnw on 2010-09-05
The T101MT is supposed to be single core atom right? Why does system monitor show processor 0 and processor 1?

---

### Post by Plippo on 2010-09-05
> **tlimsisnw said:**
> Why does system monitor show processor 0 and processor 1?

That's Intel's HyperThreading technology, it emulates two cores on a single-core processor. [http://en.wikipedia.org/wiki/HyperThreading](http://en.wikipedia.org/wiki/HyperThreading)

---

### Post by Kevrox on 2010-09-05
> **Plippo said:**
> @Kev: twofing --wait is the one to use, it will wait with the initialization of the daemon until all services are ready. I don't know if it doesn't work for you sometimes, but it definitely doesn't have anything to do with the packages you installed.

Every time I think it is working consistently it stops. now after manual log in it might not work, then works if I log out and in.

Plippo, does it matter where in the startup applications position the twofing --wait is located, is there a load priority?

What I am finding is that when I touch with the first finger and then very shortly after I tap with the second finger I get a highlight rectangle between fingers. it looks like if you use 1 finger and point and drag along the screen you get that rectangle highlight. I hope this makes sense, I figured the more I describe what is happening the better to diagnose and resolve. this 1 - 2 finger touch has worked before so I do know what the gesture is meant to be and looks like when it works. What I do not get is why it is a hit and miss affair. 
cheers, kev

---

### Post by tlimsisnw on 2010-09-05
Plippo: Regarding the problem of having to double-click/tap on the on-screen keyboard to type, I found the problem to be gone now after I have installed the most recent multitouch kernel driver and twofing0.0.4. Hmm, not sure which had the conflict. But that seems to be self-resolved now. Thanks again for your efforts. Much appreciated.

By the way, is there a simple on-screen gadget to change the brightness (i.e. without using the keyboard)?

---

### Post by tlimsisnw on 2010-09-05
Plippo: What I said in the previous post regarding the onscreen double-clicking is not so accurate. I've done a series of experiments and I think I isolated the problem. There seems to be a conflict between Firefox's Grab and Drag and twofing. I made the following observations:

Boot with Grab and Drag OFF, twofing on. Onscreen keyboard works normally.
Then turn on Grab and Drag. Twofing doesn't work anymore and Onscreen keyboard needs double-clicking.
Then disabled Grab and Drag. Twofing seems not loaded. Onscreen keyboard still bad.
Then reloaded twofing. Twofing working, onscreen keyboard back to normal.

See if you can reproduce the problem.

For now, I guess I'll disable Grab and Drag.

---

### Post by gltripp on 2010-09-05
> **Plippo said:**
> @St.: If I remember correctly, the problem back then was that the device claimed to support LeftBtn and RightBtn events, so evdev regarded it as a touchpad instead of a touchscreen and configured it for relative pointer movement. In gltripp's evtest output, the LeftBtn and RightBtn events occur again, so I thought this could be related.




Plippo:
I patched it and its "working" with the modifications I made on the kernels mosart-driver (patches are on the way going upstream).

But can't confirm multitouch is working :-/
I can handle my touchscreen as like before with the modificated egalax-driver & the modificated kernel-driver.

What is about these Button-Events ?
Any ideas where the problem could be now ?

Sorry, i'm not very familiar with the implementation device-driver-stacks at all  :-(

---

### Post by Plippo on 2010-09-05
@Kev: If this rectangle appears, it means that the taps of both fingers are registered as single clicks, which probably means that the twofing daemon either doesn't run or doesn't work. If you press Alt+F2, enter **twofing** and press enter and the two-finger click works then, it means that twofing probably crashed or wasn't loaded correctly before.

@tlimsisnw: This is interesting, I don't know how grab-and-drag works, but if it tries to grab the pointer like twofing does, this could be an explanation. At the moment I don't think there is something to do about it other than disabling either grab-and-drag or twofing.

@gltripp: The multitouch kernel module is only the first step. It sends multitouch events to the X server, but currently X doesn't know how to handle them. What is now required is support in the higher layers of the software stack. There are several attempts to provide this. One of the most advanced seems to be the UTouch framework that will be introduced in Ubuntu Maverick, but I haven't tested that yet. Some months ago, I created the twofing daemon as an intermediate step. It reads the multitouch events directly from the Kernel and translates them into mouse and key events. But currently, it only works for the eGalax touchscreen, not your model.

So if you want to use Multitouch right now, you can either try Maverick and check if the UTouch system already works, which I don't know, or if you want to use twofing, I can try to extend it to also support your screen. As the events should have the same structure, this shouldn't be very much work. If you like, you can send me a PM so I can tell you which additional information I need.

---

### Post by fastler on 2010-09-05
I am in the process of installing Ubuntu onto my shiny new T101MT and have run into a snag. It may have already have been solves somewhere in the past 40 pages, and I am really sorry, but I am not going to be reading all that. So here it is:

The touchscreen is reacting to my touch, but all that is happening is that the cursor goes into the bottom right of the screen, opening my trash can. The calibrate program in the first post installed, but it doesn't seem to start. I did everything in that post up to the install calibrate step.

If anyone could help me, that would be awesome.

---

### Post by tlimsisnw on 2010-09-05
Hmm, I also found that the screensaver locking also disables twofing and hence the onscreen keyboard as well. Anyway to keep twofing enabled when screensaver is activated?

---

### Post by Plippo on 2010-09-06
> **fastler said:**
> I did everything in that post up to the install calibrate step.

A few days ago, I updated the instructions and uploaded a new version of the driver which no longer needs calibration. I recommend simply re-installing the touchscreen support package and the kernel driver, this should solve the problem.

---

### Post by Plippo on 2010-09-06
@tlimsisnw: Oops, I didn't see your comment before that the keyboard doesn't work when twofing is not running. This is strange, so the problem can't only be twofing and grab-and-drag but there must be a different configuration problem with your system.

---

### Post by riccardo.depalo on 2010-09-06
@Plippo: I was watching your script for installing egalax driver and produce a deb file. Maybe it tries to cd into the source and doesn't seem to find it because the file is called just linux-source-2.6.35.tar.bz2 and not 2.6.35-19-generic as my system says when I type uname -r? maybe that's the reason why it doesn't seem to work in Maverick?

---

### Post by Kevrox on 2010-09-06
Hi Plippo
I now have added a twofing launch on the desktop and removed the launcher I had in startup applications, so all I do after a reboot is double click on the icon I made and twofing works .... not the best way but a way non the less, wonder why it does not want to run when set up in startup applications.
cheers and mate thanks for all the hard work you do, all we do is test and moane :p you do all the fixing.

---

### Post by gltripp on 2010-09-06
> **Plippo said:**
> @Kev: If this rectangle appears, it means that the taps of both fingers are registered as single clicks, which probably means that the twofing daemon either doesn't run or doesn't work. If you press Alt+F2, enter **twofing** and press enter and the two-finger click works then, it means that twofing probably crashed or wasn't loaded correctly before.

@tlimsisnw: This is interesting, I don't know how grab-and-drag works, but if it tries to grab the pointer like twofing does, this could be an explanation. At the moment I don't think there is something to do about it other than disabling either grab-and-drag or twofing.

@gltripp: The multitouch kernel module is only the first step. It sends multitouch events to the X server, but currently X doesn't know how to handle them. What is now required is support in the higher layers of the software stack. There are several attempts to provide this. One of the most advanced seems to be the UTouch framework that will be introduced in Ubuntu Maverick, but I haven't tested that yet. Some months ago, I created the twofing daemon as an intermediate step. It reads the multitouch events directly from the Kernel and translates them into mouse and key events. But currently, it only works for the eGalax touchscreen, not your model.

So if you want to use Multitouch right now, you can either try Maverick and check if the UTouch system already works, which I don't know, or if you want to use twofing, I can try to extend it to also support your screen. As the events should have the same structure, this shouldn't be very much work. If you like, you can send me a PM so I can tell you which additional information I need.

Hi Plippo,

i'll try the modify-twofing-daemon-way :-)

But I'll need some help:

1. i have to modify your udev-rule:
BUS=="usb",ACTION=="add",KERNEL=="event*",SYSFS{idProduct}=="480d",SYMLINK+="twofingtouch",RUN+="/bin/chmod a+r /dev/twofingtouch"
to match the corresponding DeviceID of my controller:
SUBSYSTEM=="usb",ACTION=="add",KERNEL=="event*",ATTR{idProduct}=="0186",SYMLINK+="twofingtouch",RUN+="/bin/chmod a+r /dev/twofingtouch"

(I changed the SYSFS & BUS-attributes because Udev told me they are deprecated)
But: not device /dev/twofingtouch will be created. Whats wrong ?
I got the value "0186" from 'lsusb' and searching in /sys.

2nd Question:
Why does the driver creates 3 event-devices in /dev/input ?
```
evtest /dev/input/event7
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   1877
      Min        0
      Max     3478
    Event code 1 (Y)
      Value   1886
      Min        0
      Max     3478
    Event code 53 (?)
      Value      0
      Min        0
      Max     3478
    Event code 54 (?)
      Value      0
      Min        0
      Max     3478
    Event code 57 (?)
      Value      0
      Min        0
      Max        2
  Event type 4 (Misc)
    Event code 4 (ScanCode)

```
```
evtest /dev/input/event8
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     3478
    Event code 1 (Y)
      Value      0
      Min        0
      Max     3478
    Event code 53 (?)
      Value      0
      Min        0
      Max     3478
    Event code 54 (?)
      Value      0
      Min        0
      Max     3478
  Event type 4 (Misc)
    Event code 4 (ScanCode)

```
```
evtest /dev/input/event9
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 3 (Absolute)
    Event code 40 (Misc)
      Value      0
      Min        0
      Max      255

```

What are about these?
Only event7 is generating any events, when I'm scratching on the display....

---

### Post by Plippo on 2010-09-06
@riccardo: This should not be the problem, the script uses sed to cut the version number. There are two variables in the script, VERSION which contains the full version number and VER which contains the abbreviated one. One thing you could do is replace all occurrences of **$VER** (but not of $VERSION, so you have to do it by hand) in the script by **2.6.35**, maybe the variable is causing the problem as this is the only thing I changed.

@gltripp: The three devices might be there because you are maybe still using the old QUIRKS option. If you remove it, there should only be one device. Maybe this is also what confuses udev.

Altering the udev rule is exactly what you have to do. Are you using Lucid or Maverick? In Lucid, it still works with the deprecated keywords. At first glance, everything looks okay, but I know that udev rules are unfortunately really hard to debug. The only thing that looks wrong are the spaces, but I guess they were added when you posted here?

**EDIT:** You can also try the command **udevadm info --query=all --name=/dev/input/event7 --attribute-walk** which lists all attributes for the device. The output suggests that you should use ATTRS instead of ATTR in the rule, but this is just a guess.

---

### Post by gltripp on 2010-09-06
> **Plippo said:**
> 
@gltripp: The three devices might be there because you are maybe still using the old QUIRKS option. If you remove it, there should only be one device. Maybe this is also what confuses udev.

*hm* Mea culpa!
This was my fault! ;)

> **Plippo said:**
> 
Altering the udev rule is exactly what you have to do. Are you using Lucid or Maverick? In Lucid, it still works with the deprecated keywords. At first glance, everything looks okay, but I know that udev rules are unfortunately really hard to debug. The only thing that looks wrong are the spaces, but I guess they were added when you posted here?

**EDIT:** You can also try the command **udevadm info --query=all --name=/dev/input/event7 --attribute-walk** which lists all attributes for the device. The output suggests that you should use ATTRS instead of ATTR in the rule, but this is just a guess.

No, sorry - this didn't worked too ;-(

SUBSYSTEM=="usb",ACTION=="add",KERNEL=="event*",ATTRS{idVendor}=="0486",ATTRS{idProduct}=="0186",SYMLINK+="twofingtouch",RUN+="/bin/chmod a+r /dev/twofingtouch"

damn it

---

### Post by fastler on 2010-09-06
> **Plippo said:**
> A few days ago, I updated the instructions and uploaded a new version of the driver which no longer needs calibration. I recommend simply re-installing the touchscreen support package and the kernel driver, this should solve the problem.

Nope, I installed the package and drivers yesterday. I reinstalled them again today, but nothing has changed. The system recognizes that I have touched the screen, but it thinks that I have touched the very bottom right corner of the screen. This is a big pity, because everything else is working a charm, just the touchscreen isn't. Sorry to be a hassle.

---

### Post by Plippo on 2010-09-06
> **gltripp said:**
> damn it
Don't worry, we'll beat the udev monster. And if not, there is still the possibility to create the link manually in the boot scripts. But of course udev would be the better solution. Could you maybe post the output of
```
udevadm info --query=all --name=/dev/input/event7 --attribute-walk
```(replace the event7 if the device number has changed after removing the QUIRKS option)

@fastler: This is strange. What happens when you enter
```
xinput --list
```and
```
xinput --list-props 10 && xinput --list --long 10

```in the terminal?

---

### Post by riccardo.depalo on 2010-09-06
@Plippo: no, it didn't work. There may be be something wrong in linux-source. But I controlled: headers, image and source are all 2.6.35-20.29 This is my output:

```
./build.sh
BUILDING KERNEL MODULE...
Cleaning up...
rm: cannot remove `linux-source-2.6.35.tar': No such file or directory
Unpacking linux kernel source...
bunzip2: Can't open input file linux-source-2.6.35.tar.bz2: No such file or directory.
tar: linux-source-2.6.35.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Copying Module.symvers from headers...
cd: 93: can't cd to linux-source-2.6.35
Configuring...
make: *** No rule to make target `oldconfig'.  Stop.
Building scripts...
make: *** No targets.  Stop.
grep: include/linux/hid.h: No such file or directory
sed: can't read include/linux/hid.h: No such file or directory
Modified hid.h.
cd: 93: can't cd to drivers/hid
grep: hid-core.c: No such file or directory
sed: can't read hid-core.c: No such file or directory
Modified hid-core.c.
grep: usbhid/hid-quirks.c: No such file or directory
hid-quirks.c is already fine.
hid-ids.h is already fine.
Makefile is already fine.
Building modules...
make: Entering directory `/'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/'
Copying...
cp: cannot stat `hid.ko': No such file or directory
cp: cannot stat `hid-egalax.ko': No such file or directory
cp: cannot stat `usbhid/usbhid.ko': No such file or directory
Should have built. Ready to build deb.
BUILDING DEB PACKAGE...
dpkg-deb: generazione del pacchetto "egalax-multitouch-driver-2.6.35-19-generic-i386" in "deb.deb".
SHOULD BE FINISHED.

```

---

### Post by Plippo on 2010-09-07
@riccardo: Hmm, this is really strange (I guess I use this phrase way too often). But the problem is that I can't try the script from the live USB stick due to insufficient space. But I'll update to Maverick beta later today or tomorrow, so I will hopefully be able to better help you then.

---

### Post by Plippo on 2010-09-07
@riccardo: So, I updated to Maverick Beta and found the problem with the source package. The new linux-source package packs the source into another sub-directory. I adapted the package, you can find it at the well-known locations. Before you run it, you might have to re-install the linux-source package:
```
sudo apt-get install --reinstall linux-source-2.6.35
```

There also were some problems with twofing in Maverick, I uploaded a new version to the twofing post which should fix them.

---

### Post by riccardo.depalo on 2010-09-07
@Plippo: thank you, it worked fine and smoothly. It seems to me that the new twofing (or the new kernel) makes twofing gesture more reactive. Very well done, indeed. You could propose it for the repository, and go mainstream.
Also the screen rotation now works in Maverick like in Lucid. That's because of your patches, I imagine.

P.S I noticed that the previous workarounds for gimp and mypaint don't work anymore in Maverick: you touch the screen but no drawings. Xournal, instead works fine.

---

### Post by Plippo on 2010-09-08
Yes, it turned out there was a bug in twofing that made it a bit unresponsive in Lucid and, in combination with a bug that seems to be in Maverick, extremely unresponsive there. So the change in twofing should make it more responsive in Lucid, too.

I also experienced that there is no pressure information sent in Maverick any more. But that's not the driver's fault, (in fact, the version of the driver created by the script is exactly the same as in Lucid) but seems to be in the evdev driver: The kernel driver sends the correct pressure events, but X always reports a pressure of 1.0 – I'll have to investigate this.

Another bug (in evdev or X, I suppose) makes the touchscreen less responsive, do you also experience this? Sometimes touches are simply not registered, not even the mouse pointer moves. This happens also if twofing is not running, but with twofing it gets a bit worse, because twofing handles clicks itself, but lets X handle pointer movement. So it may happen that X doesn't register pointer movement, but twofing (that doesn't suffer from the unresponsiveness bug) registers a click and thus the click occurs at the wrong position. A workaround would be to to let twofing also handle mouse movement. As twofing already has to do calibration internally, I guess that wouldn't be too difficult. But of course it would be better to fix the bug in evdev.

---

### Post by beastrace91 on 2010-09-08
Any idea if something like this is possible? > doing differences looking at the differents pressure levels over the screen from your hand and your pen while handwriting

Was a comment someone left on my HOWTO for the T101MT. Basically what he is asking for would make it easier to write on the device by differentiating based on pressure which touch is your pen and which is your hand.

~Jeff

---

### Post by gltripp on 2010-09-08
> **Plippo said:**
> Don't worry, we'll beat the udev monster. And if not, there is still the possibility to create the link manually in the boot scripts. But of course udev would be the better solution. Could you maybe post the output of
```
udevadm info --query=all --name=/dev/input/event7 --attribute-walk
```(replace the event7 if the device number has changed after removing the QUIRKS option)


Hello Plippo,

the requested output is attached.
Info: After removing the quirk-options, touchpad is still recognized as a touchpad  by X.org's ev-driver (relative cursor movements).
Any ideas about that ?

---

### Post by riccardo.depalo on 2010-09-08
@Plippo: I had installed by mistake your twofing-0.0.4 and not 0.0.4b so it happened to me that pinch and zoom didn't work anymore. Now everything's ok.

I don't know if touchscreen was more responsive before. I know that twofing is some more responsive now. But you have to press fingers hard and sometimes the zooming becomes slower. It maybe an X or evdev bug, yes.

---

### Post by Plippo on 2010-09-08
> **beastrace91 said:**
> Basically what he is asking for would make it easier to write on the device by differentiating based on pressure which touch is your pen and which is your hand.
Yes, this would indeed be good, but it's not that easy. I once tried to modify the driver to accomplish that, but unfortunately the pressure information is not exact enough: Often the hand has a lower pressure value than the pen, but sometimes this changes, and when pen and hand are touching at the same time, the pressure information gets unusable. I didn't achieve any reliable recognition. I guess the Windows driver does much more work, tracking the movements of the touch points to decide which one is currently writing and which one is resting. That's why input is a bit delayed in Windows when you enable the pen mode.

@gltripp:
According to the output, your udev line seems to be correct, I don't see why the device */dev/twofingtouch* is not created for you. About the problem with the screen being regarded as a touchpad: If Stéphane has no solution for you, this seems to be a bigger problem. Have you tried adding the **return -1** as I proposed earlier? (I know Stéphane said this is a different problem, but you could try it as a "last resort...") As another alternative, you could compile evdev yourself, modifying it to regard all absolute touchpads as touchscreens (the touchpad in the Eee PC is handled by synaptics, not evdev, so this would do no harm). This is easier than it sounds, I did it myself some time ago when there was the same problem with the eGalax driver. If you like, I can give you some hints how to do it.

@riccardo:
The problem with the lower responsiveness and the missing pressure sensitivity doesn't come directly from evdev but from some special Ubuntu patch. I compiled evdev myself, using the same version Ubuntu uses, but without the patches (which turned out to be the same version as in Lucid) and everything is fine, as before. I guess I have to create a bug report about that.

---

### Post by Kevrox on 2010-09-08
> **Plippo said:**
> Yes, it turned out there was a bug in twofing that made it a bit unresponsive in Lucid and, in combination with a bug that seems to be in Maverick, extremely unresponsive there. So the change in twofing should make it more responsive in Lucid, too.

Hi Plippo, does this mean there will be a new version of twofing-0.0.4b.tar.gz or is this version still ok for lucid? BTW all going well since I decided to run twofing on its own from a desktop icon,.

---

### Post by Plippo on 2010-09-09
@Kev: Indeed, 0.0.4b is a new version. I thought about it again and I think it should not be necessary in Lucid. The performance improvements in Maverick probably all come from the new faster Intel display driver.

---

### Post by gltripp on 2010-09-10
> **Plippo said:**
> 
@gltripp:
According to the output, your udev line seems to be correct, I don't see why the device */dev/twofingtouch* is not created for you. 


I don't know it too.
How can i get all neccessary informations (major and minor numbers, etc) to create the devicelink manually?

> **Plippo said:**
> 
About the problem with the screen being regarded as a touchpad: If Stéphane has no solution for you, this seems to be a bigger problem. Have you tried adding the **return -1** as I proposed earlier? 


Where?
My touchscreen isn't longer handled by the egalax-driver, but by evdev.

> **Plippo said:**
> 
As another alternative, you could compile evdev yourself, modifying it to regard all absolute touchpads as touchscreens (the touchpad in the Eee PC is handled by synaptics, not evdev, so this would do no harm). This is easier than it sounds, I did it myself some time ago when there was the same problem with the eGalax driver. If you like, I can give you some hints how to do it.


I still made it by commenting out the appropriate lines in evdev.c ("static int EvdevProbe (..)", where's checked if the device is a touchscreen or touchpad) so that the device is configured as touchscreen. 

Its more a dirty hack than a beautiful patch - but: this works!

I'll get in touch with the X.org guys and report this problem. Perhaps, they can fix this up to the next release.

---

### Post by Plippo on 2010-09-10
@gltripp: I meant in the hid-mosart module, but if it works with the changes in evdev, that's also okay. Your changes were exactly what I meant.

I don't know what you mean by "no longer handled by the egalax-driver" - do you mean the hid-egalax kernel driver? It never handled your screen as it is a different model. Or have you installed the egalax X drivers? They probably also don't work with your screen and don't support multitouch. Evdev is the correct one.

To bypass udev and create the link manually, you should do the following:

```

sudo ln -T /dev/input/event7 /dev/twofingtouch
sudo chmod a+r /dev/twofingtouch

```
(assuming event7 is still the right path)

To make it permanent, you could add them (without sudo of course) to /etc/rc.local

Good luck!

---

### Post by Plippo on 2010-09-10
Good news everyone! I finished a new version of **twofing**, namely version **0.0.5**.
It provides the following new features:

[LIST]
[*]More robust: Should no longer crash when there is no active window and not even the desktop is active, yet (like right after login)
[*]New Profile for the Ubuntu Desktop: Rotate your Compiz cube by swiping with two fingers (for which you need – surprise – a Compiz cube. If you don't know how to get one, ask somebody who knows ;-) )
[*]Default profile (for nautilus, firefox etc.) less zoom sensitive: It should less often occur that you zoom when you actually wanted to scroll.
[*]And, last but not least at all: Finally there is **Kinetic scrolling**! Scrolling continues (naturally) when you stop (doesn't work in Eye Of Gnome). Hah, you didn't expect such a surprise at the last bullet point, did you?
[/LIST]
You know where you find the new download... (If you don't, it's the magical [post 77]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77")!)

---

### Post by riccardo.depalo on 2010-09-10
@Plippo: it is indeed a good improvement! :) zooming is more precise now and I don't zoom by mistake when I just want to scroll the pages in the browser. Also changing desktop with 3d compiz cube is quite funny, when I go with two fingers right or left on the desktop, without open pages. The only thing I can't do (at least in Maverick) is kinetic scrolling. It seems I get only the normal scrolling. Thank you.

---

### Post by Kevrox on 2010-09-11
> **Plippo said:**
> Good news everyone! I finished a new version of **twofing**, namely version **0.0.5**.
It provides the following new features:

You are a champ, many thanks, do we need to unstall the twofing v 4 or just install new one over the top?

---

### Post by Plippo on 2010-09-11
@Kev: Don't thank me too early, try it first :-) You don't have to uninstall the old one, just perform the usual make and sudo make install again, log off and back in (or kill twofing and re-start it) and it should work.

---

### Post by Kevrox on 2010-09-11
> **Plippo said:**
> @Kev: Don't thank me too early, try it first :-) You don't have to uninstall the old one, just perform the usual make and sudo make install again, log off and back in (or kill twofing and re-start it) and it should work.

I am impatient, I already did it, works a treat. Very responsive, nice job mate.

---

### Post by fastler on 2010-09-12
It has been a few days and I think my problem has been lost in the crowd. I will reiterate. (Though I hate to be a pest)

I have installed everything faithfully as I should have, but the only thing that happens when I touch the screen is that the cursor clicks in the bottom right corner of the screen (Thus opening my trash can). That pretty much sums it up. I followed all the instructions, though I haven't installed two-fing or the webcam fix or the rotation yet.

I hope it can be fixed.

---

### Post by Plippo on 2010-09-12
@fastler:
No one is left behind here :-) It's not your question that got lost, but probably my answer. It is the second part of this post: [http://ubuntuforums.org/showpost.php?p=9813575&postcount=409](http://ubuntuforums.org/showpost.php?p=9813575&postcount=409). If you post the results of the commands, we can hopefully help you.

---

### Post by riccardo.depalo on 2010-09-12
@Plippo: still no kinetic scrolling. Everything else works fine with your latest twofing. Any ideas?

---

### Post by Plippo on 2010-09-12
@riccardo:
This could be because you are using the default Maverick evdev version which causes some problems. As I wrote before, I compiled evdev myself without the Ubuntu patches and for me kinetic scrolling works in Maverick. I attached my /usr/lib/xorg/modules/input/evdev_drv.so and /usr/lib/xorg/modules/input/evdev_drv.la. You can try to replace your own versions of those files by them and look if it works then. If it does, I can create a package with them. (I will also create a bug report in launchpad, but I doubt it will be fixed before the Maverick release)

---

### Post by riccardo.depalo on 2010-09-12
@Plippo: it works, great! :D If kinetic scrolling should stop only after a few time and not until the end of the page, it's ok. I tested browsers, nautilus, word processor. By the way, I had no evdev_drv.la in my system. It seems the input is also more responsive, now, for all other two fingers gestures. Thanks.

---

### Post by Plippo on 2010-09-12
Great that it works. Yes, it is intended to not scroll till the end of the page, simply because twofing can't know when the end of the page is reached. But I'll probably post an updated version soon in which the speed will decrease a bit more slowly, so it will scroll longer.

---

### Post by riccardo.depalo on 2010-09-12
@Plippo: I updated the wiki [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT) with your latest suggestions about maverick, look if it was correctly reported.

---

### Post by Plippo on 2010-09-12
> **riccardo.depalo said:**
> look if it was correctly reported.
Yes, looks good. Thank you for your work on the wiki page!

---

### Post by fastler on 2010-09-12
@Plippo Boy do I feel like an idiot now. Well, in any case:
The xinput --list comes back with:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=12	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=13	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=10	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]

```

And the xinput --list-props 10 && xinput --list --long 10 comes back with:
```
Device 'Logitech USB Receiver':
	Device Enabled (134):	1
	Evdev Reopen Attempts (249):	10
Logitech USB Receiver                   	id=10	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 10
		Keycodes supported: 248

```

Note: The Logitech USB Receiver is my wireless mouse receiver.

---

### Post by Plippo on 2010-09-12
@fastler:
Don't worry, such things can happen.
Looks like you have installed the evtouch package (xserver-xorg-input-evtouch)? This package doesn't work with multi-touch touchscreens like the T101MT's, so you have to uninstall it. Then reboot and run the commands again, please.

---

### Post by fastler on 2010-09-12
@Plippo
I didn't even have to reinstall the packages. As soon as I rebooted, the touch screen started working. Thanks for this.

---

### Post by Plippo on 2010-09-12
@fastler:
You're welcome! If all problems could be solved that easily... :-)

@all:
There was a small bug in twofing 0.0.5 causing kinetic scrolling to stop working after you have been using it for some hours (or earlier if you were scrolling like crazy :-) ). That should be fixed in the new version 0.0.5b which can be found – who would have thought it – [here]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77").

---

### Post by riccardo.depalo on 2010-09-13
@Plippo: hi, it seems Gimp and mypaint work again now, after your evdev help. Let me know if you open a bug about that, so we can confirm it and have it fixed. Latest twofing work very well. If it could be used for any touchscreen it would be very interesting.

---

### Post by xtsuname on 2010-09-13
Hi,

was just wondering, does anyone know whether we can get Ubuntu to do Palm Rejection? I was wondering whether there is an app similar to PenWrite on Windows that will do Palm Rejection. This helps a lot when writing notes down in Xournal.

Thanx

---

### Post by Plippo on 2010-09-14
@riccardo: Here is the bug report for the evdev bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/637874](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/637874)

@xtsuname: As I have already written before, that's not that easy. The Windows driver has to put a lot of effort into calculating which touch point belongs to the palm and which to the pen.

---

### Post by riccardo.depalo on 2010-09-15
@Plippo: as there was an update for maverick, I compiled the new driver for 2.6.35-21. But the first time I failed because, I think, I didn't update the headers to 2.6.35-21. After I did it, the script worked well.

---

### Post by Plippo on 2010-09-15
> **riccardo.depalo said:**
> But the first time I failed because, I think, I didn't update the headers to 2.6.35-21.

Yes, Kernel image, headers and source need to be of the same version.

---

### Post by DheathNone on 2010-09-15
So, has anybody been able to find an actual solution to the rotate screen button locking the screen?

Seems that there is a similar bug reported in:
[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/377175](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/377175)

---

### Post by riccardo.depalo on 2010-09-16
@Plippo: there was an Evdev update, so I had to replace again the file evdev_drv.so in order to have kinetic scrolling. Luckily, it worked. I like your daemon very much.

---

### Post by Plippo on 2010-09-20
@DheathNone: Currently I don’t see such a solution. The problem is that the key is hard-wired in gnome-power-manager. You could of course disable gnome-power-manager, but this would affect power-saving functionality.

---

### Post by DheathNone on 2010-09-21
> **Plippo said:**
> @DheathNone: Currently I don’t see such a solution. The problem is that the key is hard-wired in gnome-power-manager. You could of course disable gnome-power-manager, but this would affect power-saving functionality.

 This is a bit mystic. It seems to have solved it self after some update because I did not yet do any hackis solution as suggested. It would be nice to know what exactly happened.   
 
Btw. I tried to go through the thread but I could not find anything on this: Is there any good application or applet to gnome to change the workspace by touch screen? Basically I just would like somehow to get the workspace switcher much bigger when clicked or something similar.

---

### Post by Plippo on 2010-09-23
Hi all, there is a new version of twofing (0.0.6). It doesn't bring much new things except:
- Profile for Google Earth (as Maverick's graphics driver is finally fast enough for a smooth experience): That's really fun, explore the globe with two fingers!
- Massive code restructuring/cleanup: Gesture handling code and easing code have been separated from the main tweaking code into different files for better clearity and to make future enhancements easier.
- Improvements for users of alternative WMs (especially mutter used in Unity, but may also help for KWin), still not working perfectly there, though.

If you want to try it, [post 77]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77") is the way to go.

EDIT: Version 0.0.6 had a small bug, in rare cases kinetic scrolling would stop working. Version 0.0.6b fixes this. I'm really sorry!

---

### Post by tlimsisnw on 2010-09-23
Plippo: new twofing works great, seems much more fluid in lucid, even in the portrait mode. Excellent job again. I have a new problem which seems to appear only recently: the touch pad (usually after suspend) behaves weird for one finger, if the cursor is in middle of the screen and I try to an upward motion from the bottom of the touch pad, the cursor actually jumps to the bottom of the screen before starting to move up. When this happens, it also becomes very difficult to move the cursor to the top part of the screen (i.e. the menu regions). I find this very annoying. Thankfully the touch screen still works fine (thanks to all your efforts). Have you encountered this problem with the touchpad?

---

### Post by Plippo on 2010-09-23
@tlimsisnw: Is this problem persistent or does it go away after some time? I have experienced with some touchpads on different machines that sometimes when your fingers are a bit moist and you touch the touchpad, the pad gets a behaviour of "jumping cursor", probably because small amounts of water (too small to actually see them) get on the pad and are recognized as touches.

---

### Post by riccardo.depalo on 2010-09-23
@Plippo: I tried twofing in 0.0.6b version and I must say there is a visible improvement in touch response, the experience of google earth with this machine is really funny. Very good work, thanks.

---

### Post by tlimsisnw on 2010-09-23
Plippo: The jumping cursor doesn't always happen. I found that if I restart or rotated the screen orientation one round (tried once only), the touch pad works normally. Well, it could be that my fingers dried up by that time.

---

### Post by Kevrox on 2010-09-24
Hi all, still all good with touch screen.
Not sure if this question should go here or else where?
Is there a way to simulate a larger screen say 1280x1024 and have the screen pan about when one drags the screen. Xorg.conf or similar added code.

Like I said sort of touch screen related but perhaps more monitors.
So to clarify,
my unit displays 1024x600, but I would like a pretend add on or simulated screen of 1280x1024 and be able to pan about this new pretend screen using touch.
thanks for any help, perhaps vesa display or something
or a gui way to force this option.
cheers
kev

This a copy of xorg.conf.failsafe


thisSection "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection 


also Xsession.options

# $Id: Xsession.options 189 2005-06-11 00:04:27Z branden $
#
# configuration options for /etc/X11/Xsession
# See Xsession.options(5) for an explanation of the available options.
allow-failsafe
allow-user-resources
allow-user-xsession
use-ssh-agent
use-session-db

I just do not want to ruin all the hard work to get this far by putting some bad code:(

---

### Post by Plippo on 2010-09-24
@Kev: there's good news and bad news. The good news: To create such a "bigger screen" is easy. You don't need to change any Xorg.conf files nowadays. Just call:
```
xrandr --output LVDS1 --panning 1280x1024
```And your screen is extended.
The bad news: The way the touchscreen works then is probably not what you want, I don't think there is a solution right now. Just try it out and you will see what I mean.

I'm currently working on a little program which makes the touchscreen work correctly when an external screen is attached. Maybe I can also add support for such a panning mode, but this will take some time.

If you just need the bigger resolution for a game or something, you can also try the following command:
```
xrandr --output LVDS1 --panning 1280x1024 --scale 1.25x1.7
```
It scales the contents down to the screen size. This way also the touchscreen works correctly.

---

### Post by Kevrox on 2010-09-24
Thanks mate
BUT I think I have broken the xorg thing ... I am booting with live cd to remove the one I made and leave the xorg.conf.failsafe alone
hope to be back up and running within the hour.

feeeewww back again, will give those commands a try

I see what you mean.
The application is as follows
I am running XP in virtual box to run our store stock program.
The menu and page sizes have been written for a screen resolution of 1280x1024. So function buttons that would reside on the bottom of the screen are not viewable with the smaller screen size or resolution.

I am running virtual box in full screen but still miss some of the screen button inputs like "exit" or "next screen" that are located on the bottom of the 1280x1024 screen and of coarse on the smaller screen I cannot see them. I am hoping that with the screen set to 1280x1024 in Lucid the virtual box option will follow suit so I can pan down to see the touch the above mentioned screen buttons.

xrandr --output LVDS1 --panning 1280x1024 --scale 1.25x1.7

now that has potential all be it squashed. thanks for the pointers, just one other thing how to I kill them to resort back with out having to log out?

Ok virtual box does scale to suit with xrandr --output LVDS1 --panning 1280x1024 --scale 1.25x1.7. 

getting warmer.... I am so glad i got this little baby and not an Ipad:)

---

### Post by Plippo on 2010-09-24
To return to the default settings, simply call
```
xrandr --output LVDS1 --auto --scale 1x1
```

---

### Post by tlimsisnw on 2010-09-25
I found Google earth crashes immediately after opening. Is this a problem with T101MT or generic? It did work ok the first time after installation and I was able to verify that Plippo's twofing works nicely in there. But now it keeps crashing. :(

---

### Post by riccardo.depalo on 2010-09-25
@Plippo: I updated the wiki with the latest twofing version and features:  [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)
Maybe when Maverick goes in october, we could explain more in the wiki how to make t101mt work with the new OS. In my experience it seems enough usable already. Let's hope bugs will be fixed soon.

---

### Post by Kevrox on 2010-09-26
> **Plippo said:**
> To return to the default settings, simply call
```
xrandr --output LVDS1 --auto --scale 1x1
```

This seems to do nothing, in terminal it returns this

xrandr: Configure crtc 1 invalid time
any idea, 

also after this option xrandr --output LVDS1 --panning 1280x1024 --scale 1.25x1.7 I get the scaled screen great but sometimes while running another program it seems to switch back to the large pan screen option at random.

---

### Post by Kevrox on 2010-09-26
> **Kevrox said:**
> This seems to do nothing, in terminal it returns this

xrandr: Configure crtc 1 invalid time
any idea, 

also after this option xrandr --output LVDS1 --panning 1280x1024 --scale 1.25x1.7 I get the scaled screen great but sometimes while running another program it seems to switch back to the large pan screen option at random.

Is there any way I could add this 1280x1024 scaled optionto the grandr menu as an option to tick and then return to normal.

---

### Post by Kevrox on 2010-09-26
> **Kevrox said:**
> This seems to do nothing, in terminal it returns this

xrandr: Configure crtc 1 invalid time
any idea, 

also after this option xrandr --output LVDS1 --panning 1280x1024 --scale 1.25x1.7 I get the scaled screen great but sometimes while running another program it seems to switch back to the large pan screen option at random.

Ok found what switches the screen to 1280x1024 pan, when in 1280x1024 scale 1.25x1.7 mode if I place the mouse at the bottom of the screen it jumps to the big screen 1280x1024 pan mode, very strange.

---

### Post by alma000 on 2010-09-26
Hi! I have google earth crushing at startup as well. Also my video playback much weaker than in win7. Maybe there is some additional drivers i should install?
I'm running 10.04 right now.
What i did:
1. Installed ubuntu.
2. Updated.
3. Added [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) to software sources (as was suggested somewhere in this forums).
4. Updated again.

---

### Post by xtsuname on 2010-09-26
Hi,

I am currently using 10.10 beta on my T101MT, and as probably been said in previous replies, the touchscreen doesn't work properly. I tried to install it like as was written in the first post and it just broke the whole thing, is it possible to have instructions in the wiki section for 10.10?

thank you everyone for your hard work!

---

### Post by riccardo.depalo on 2010-09-27
@Xtsuname: you can try here: [https://help.ubuntu.com/community/T101MT#NOTE](https://help.ubuntu.com/community/T101MT#NOTE) FOR THE MAVERICK USERS
the problem is that you have to compile the driver, as explained in the previous paragraph of the wiki, and change two evdev files. If you previously installed EETI proprietary driver, you should uninstall it. Hope it helps.

---

### Post by Plippo on 2010-09-27
@Kev:
Okay, the panning doesn't seem to work correctly if combined with the zooming. Instead, try using the following command please:
```
xrandr --fb 1280x1024 --output LVDS1 --scale 1.25x1.7
```
To return, the following should now do the trick:
```
xrandr --output LVDS1 --scale 1x1
```

I don't know if you can alter the grandr menu, but you could put shortcuts to those commands on the desktop.

@all having trouble with Google Earth:
How did you install it? You could try looking at the hints on [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

@alma000: 
What do you mean by "video playback is weaker"? Are you meaning flash videos? Flash always has bad performance, but it is even worse in Linux than in Windows. Please blame Adobe. 

@riccardo:
Thanks for the wiki update, I forgot to upload the new version there. I agree that before Maverick is released, some adjustments will be needed. I plan on creating a package with the "pure" evdev version (maybe also the Debian package can be used, I will try that out) as I don't think that bug will be fixed in time. I still hope for the kernel bug to be fixed, I submitted it upstream to the linux-input developers, the patches will probably be accepted soon there and maybe the Ubuntu developers will then also apply them to the Ubuntu kernel. If not, I'll start uploading pre-compiled packages with the Kernel driver for Maverick after the release as I did for Lucid.

---

### Post by Kevrox on 2010-09-27
> **Plippo said:**
> @Kev:
Okay, the panning doesn't seem to work correctly if combined with the zooming. Instead, try using the following command please:
```
xrandr --fb 1280x1024 --output LVDS1 --scale 1.25x1.7
```
To return, the following should now do the trick:
```
xrandr --output LVDS1 --scale 1x1
```

I don't know if you can alter the grandr menu, but you could put shortcuts to those commands on the desktop.

Mate your a legend, works a treat, I did have the desktop shortcuts made for the above two commands, so at least they are only a double touch away. BTW that also solved the problem of the scaled screen reverting to 1280x1024 pan mode when running xp in virtual box full screen
many thanks

---

### Post by psykatog on 2010-09-28
I'm having problems with the calibration program.  I can activate the first point with my stylus, but the second I can't.  I CAN, however, click it with my mouse.  Then I can activate the third (also on the left side of the screen, odd) with the stylus, but then not the fourth!  Why isn't the right side of my screen responding to anything?

---

### Post by Plippo on 2010-09-28
@psycatog:
There were problems with the calibrator when you used the old version of the driver, which reported incorrect coordinates. If you have installed the new version of the kernel driver as I described in the private message I sent you, you should no longer need to calibrate the screen, but if you want to, it should work better then.

---

### Post by riccardo.depalo on 2010-09-28
For any Maverick user: I uploaded in the wiki the kernel driver for 2.6.35 kernel I compiled and tested working in my system, for anyone having problems compiling it. [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

---

### Post by riccardo.depalo on 2010-09-29
@Plippo: this is very strange. With the latest updates, in Maverick, twofing doesn't zoom anymore. I have kinetic scrolling in the browser, chrome and firefox, but no effect with pynch and zoom. I tried also google earth, and it seems I can only zoom out. Any idea? It could be another problem in xorg.

---

### Post by Plippo on 2010-09-29
@riccardo: This is indeed strange. If you stop the daemon using **killall twofing** and then start it in debug mode using **twofing --debug** and watch the output while you perform the zoom gestures, do you see "Zoom in step" and "Zoom out step" messages?

---

### Post by riccardo.depalo on 2010-09-29
@Plippo: with twofing --debug I get the correct responses on terminal, zoom in step and zoom out step, but there is no zoom in the browser. xinput list seems ok, with eGalax USB TouchController with id=10. I tried again google earth and it seems working now. I get the right responses, zoom in and out, and I see the outcome. But not always. Sometimes instead of zoom in I get zoom out. Still no zoom with browsers, chrome and firefox. Same problem with nautilus. Instead of zoom, I get scrolling. Weird, isn't it?

---

### Post by riccardo.depalo on 2010-09-30
@Plippo: I thought I solved the twofing problem, because I unistalled and reinstalled the daemon 0.0.6b and everything worked again, but on another reboot, and another again, zoom didn't work again. Tried to remake the application and reinstall it, but no luck.

I noticed that also zooming with a word processor doesn't work now.

---

### Post by tlimsisnw on 2010-10-01
Plippo: After the recent update to Kernel 2.6.32-25, the touchscreen stopped working. I built the new driver as per your instructions, and installed it. But the touchscreen is still not working. :( Any advise on this?

---

### Post by Plippo on 2010-10-01
@riccardo: This is really a mysterious problem as I can't reproduce it. Some things that come into my mind to test it: A log with the output when using twofing --debug would be great and you could test whether zooming works in programs that don't use the default profile, like the document viewer or image viewer.

@tlimsisnw: Were there errors during the build process of the driver? (don't trust it when the script completes, there is a reason it only says "SHOULD HAVE BEEN BUILT") And maybe the touchscreen is only out of calibration. Can it be fixed by calling
```
xinput set-prop "eGalax Inc. USB TouchController" --type=int 264 0 4096 0 4096
``` ?

---

### Post by riccardo.depalo on 2010-10-01
@Plippo: this is debug with a browser that doesn't zoom:
```
Current window: 'google-chrome'
Use default profile.
Start zoom gesture
Zoom out step
Zoom out step
Zoom out step
Current window: 'google-chrome'
Use default profile.
Start zoom gesture
Zoom out step
Zoom out step
Current window: 'google-chrome'
Use default profile.
Start zoom gesture
Zoom in step
Zoom in step
Zoom in step

```

Image viewer works, this is debug:

```
Current window: 'eog'
Use profile 'eog'
Start zoom gesture
Zoom out step
Zoom out step

```

This is pdf viewer: doesn't work: 

```
Current window: 'evince'
Use profile 'evince'
Start zoom gesture
Zoom out step
Zoom out step
Zoom out step

```

BUT... there where new updates today, and after this, zooming seems to work again. Tried to reboot... only zoom doesn't work again. Really weird.

---

### Post by tlimsisnw on 2010-10-01
Plippo: Hmm, I tried your command to calibrate, but it didn't work. Error message: "unexpected size for property 264". Will try to rebuild the drive again. Also, I found the suspend command and suspend upon lid close do not work properly anymore, drained all my battery! They were both working nicely before. Anyone else experienced this?

---

### Post by tlimsisnw on 2010-10-01
Plippo: I get the following errors trying to build. Pls advise what I should do. Sorry, I'm still not up to speed with these things.

cd: 101: can't cd to linux-source-2.6.32
grep: include/linux/hid.h: No such file or directory
sed: can't read include/linux/hid.h: No such file or directory
Modified hid.h.
cd: 101: can't cd to drivers/hid
grep: hid-core.c: No such file or directory
sed: can't read hid-core.c: No such file or directory
Modified hid-core.c.
grep: usbhid/hid-quirks.c: No such file or directory
hid-quirks.c is already fine.
hid-ids.h is already fine.
Makefile is already fine.
Building modules...
make: Entering directory `/'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/'
Copying...
cp: cannot stat `hid.ko': No such file or directory
cp: cannot stat `hid-egalax.ko': No such file or directory
cp: cannot stat `usbhid/usbhid.ko': No such file or directory
Should have built. Ready to build deb.
BUILDING DEB PACKAGE...
dpkg-deb: building package `egalax-multitouch-driver-2.6.32-25-generic-i386' in `deb.deb'.
SHOULD BE FINISHED.

---

### Post by Plippo on 2010-10-01
@riccardo: Thanks for the output. So the gestures are recognized but the events not sent. Weird.

@tlimsisnw: Ah okay, there is the problem. Have you maybe not installed the package **linux-source-2.6.32**? If not, please install it and try again. If you did, please re-install it using the synaptic package manager and then try again.

About the suspend mode, this might be because of twofing which can cause some problems if there is no driver loaded. So hopefully this problem is solved when the driver works again.

---

### Post by tlimsisnw on 2010-10-01
Plippo: Many thanks. Touch screen is working well again. Whew!

---

### Post by psykatog on 2010-10-01
I had the touchscreen working at one point, but after restarting I need to recalibrate the screen (which doesn't always work properly).  Going to try reinstalling all the drivers...

Also, the command "sugo gedit" returns "command not found".  I'm using Kubuntu, but there shouldn't be a difference in terminal commands among flavors of Ubuntu...Even if that command did work, I'm not really sure what is meant by "change the line that says...".

---

### Post by Plippo on 2010-10-01
@psykatog: gedit is the name of the editor application used in Ubuntu. In Kubuntu, you can either use kwrite or kate instead. If you execute this command, the editor is opened with a file and you can change the given line there.

---

### Post by ElGatoFlojo on 2010-10-01
So, I've read all the way through this thread. And even Google doesn't seem to have much updated on this laptop. This thread has been really great and offered some great suggestions!

I went straight to Maverick because I wanted the newer features. So far pretty much everything is working ok. I don't really use the camera, so I'm not trying to flip it. And the touch screen works pretty well. 

One thing I've found to be perfect is 'easystroke'. I don't think I saw it mentioned anywhere in the thread. I've added a few strokes and so far its just perfect. I'm also using the recommended 'Grab and Drag' for Firefox.

There's a few things I'd like to sort out, and possibly help others with.

1) After a suspend, I have to rmmod the hid_egalax module and then reload it. Is there somewhere I can put this so it'll happen automatically?

2) The screen rotate. Is there any other options than using all the specific downloads from here? I wanted to stick with the driver that comes with maverick instead of changing and loading a bunch of stuff. I'm not even to worried about multi-touch at this point. I tried using the built in screen rotate but it just doesn't work

Anyway, thats where I'm at thus far. I thought about starting another thread, but didn't want it to get too confusing or anything.

Thanks!

---

### Post by riccardo.depalo on 2010-10-02
@Plippo: now zoom seems to work again also on reboot, when I reinstalled evdev, compiled with apt-get source, plus your files. Don't know why, but also recompiling from source, I had to add the files, otherwise there was no kinetic scrolling. Maybe we can post the deb files and a tutorial? Thank you for your assistance.

---

### Post by Plippo on 2010-10-02
@ElGatoFlojo:
Of course you can stay with the default Maverick driver if you are satisfied with single-touch and don't need pressure sensitivity (although I of course recommend the multitouch package as it is great :-) ).

You can anyway install the egalax-multitouch-driver-common package from [http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb](http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb) – despite its name, it also works with the default driver and it just adds the following things, which are exactly what you need I guess: A hook for the power-manager to automatically re-load hid_egalax after suspend and the script "touchrotate" which you can use to rotate the screen and the touch screen at the same time (you can see how it works in the first post of this thread or in the wiki). If you are using the default touchscreen driver in Maverick, you probably have to call it using the command ```
touchrotate LVDS1 10 toright
``` Maybe you have to change the 10 into a different number until it works (you can get the numbers from the comman **xinput list**).

@riccardo:
I'll be away the next two days and thus won't have time to create the evdev package, but maybe I can do it on Tuesday. You can of course also try it yourself.

---

### Post by riccardo.depalo on 2010-10-02
@Plippo: I created the evdev package with "apt-get -b source", is it the right way to do it?

---

### Post by ElGatoFlojo on 2010-10-02
@Plippo:

Thanks so much for the info! I'm going to go ahead and give it a try. It seemed from reading the thread here that it would not be easy. But if it is that easy, then I'm going to give it a try for sure!

Thanks again. And thanks for keeping this thread going and responding to everyone!

> **Plippo said:**
> @ElGatoFlojo:
Of course you can stay with the default Maverick driver if you are satisfied with single-touch and don't need pressure sensitivity (although I of course recommend the multitouch package as it is great :-) ).

You can anyway install the egalax-multitouch-driver-common package from [http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb](http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb) – despite its name, it also works with the default driver and it just adds the following things, which are exactly what you need I guess: A hook for the power-manager to automatically re-load hid_egalax after suspend and the script "touchrotate" which you can use to rotate the screen and the touch screen at the same time (you can see how it works in the first post of this thread or in the wiki). If you are using the default touchscreen driver in Maverick, you probably have to call it using the command ```
touchrotate LVDS1 10 toright
``` Maybe you have to change the 10 into a different number until it works (you can get the numbers from the comman **xinput list**).

@riccardo:
I'll be away the next two days and thus won't have time to create the evdev package, but maybe I can do it on Tuesday. You can of course also try it yourself.

---

### Post by DheathNone on 2010-10-03
> **Kevrox said:**
> Mate your a legend, works a treat, I did have the desktop shortcuts made for the above two commands, so at least they are only a double touch away. BTW that also solved the problem of the scaled screen reverting to 1280x1024 pan mode when running xp in virtual box full screen
many thanks

I made it to one command for my own pleasure:

```

#!/bin/bash
if (xrandr --verbose | grep "Transform:  1.25" -q)
then
    xrandr --output LVDS1 --scale 1x1
else
    xrandr --fb 1280x1024 --output LVDS1 --scale 1.25x1.7
fi
```I hope it will help someone else too. 

But has anyone seen any good workspace changer for gnome/ubuntu that is big enough for the touchscreen or could it be possible to change the workspace by the twofing? :confused:

---

### Post by riccardo.depalo on 2010-10-03
@DHeathNone: yes, you can change workspaces with twofing, in the last version 0.0.6b. You can try compiz cube, with four workspaces, calibrate the speed of the rotating cube, and change workspace with two fingers, from left to right and from right to left. It's funny.

---

### Post by Kevrox on 2010-10-04
> **DheathNone said:**
> I made it to one command for my own pleasure:

```

#!/bin/bash
if (xrandr --verbose | grep "Transform:  1.25" -q)
then
    xrandr --output LVDS1 --scale 1x1
else
    xrandr --fb 1280x1024 --output LVDS1 --scale 1.25x1.7
fi
```I hope it will help someone else too. 

But has anyone seen any good workspace changer for gnome/ubuntu that is big enough for the touchscreen or could it be possible to change the workspace by the twofing? :confused:


mate that looks interesting, what does it do before I copy and past, I have 2 launch buttons on screen for scale and un scale.

I have the Workspace Switcher 2.30.2 on the side panel and just touch it as as needed, nothing fancy.

12 hours later
could not wait to try it so done, this also got me to see how to make .sh files run and how to make them be able to run from 1 icon. This little script is great as it does both scale and unscale.

---

### Post by psykatog on 2010-10-04
.

---

### Post by DheathNone on 2010-10-04
> **riccardo.depalo said:**
> @DHeathNone: yes, you can change workspaces with twofing, in the last version 0.0.6b. You can try compiz cube, with four workspaces, calibrate the speed of the rotating cube, and change workspace with two fingers, from left to right and from right to left. It's funny.

This would be nice but I would like the save the battery life and cpu time for more important things than compiz. Also in the end it is just a distraction.

Would this be so hard to do for the basic gnome?
I was thinking of something like sweeping the thouch screen with two fingers to the direction that I would like to go (left/right and up/down). It would be also nice if this would over write the "go left/right in a certain application" feature. So, basically this would alway change the work space.

---

### Post by riccardo.depalo on 2010-10-05
> DHeathNone said: This would be nice but I would like the save the battery life and cpu time for more important things than compiz. 

Well, cpu is not so much involved by compiz, maybe battery life is. Anyway, I'm sure you noticed there is a workspace changer in gnome lower panel, if you have installed the gnome version of ubuntu. If you don't like it, there are many workspace changers for linux. There is an applet from google, wsnamelet. There is another one for the Cairo dock. It depends on which desktop environment you use.
Hope it helps.

---

### Post by Plippo on 2010-10-05
@riccardo:
Well, I admit I have never used apt-get -b. In any case, you also have to change the version number and remove the patches from the package. I'll try out the Debian package later, I'm pretty sure a current one should also work in Ubuntu.

@psykatog:
If you only tested the drivers from this thread, all you need to do is to go to the synaptics package manager, search for the term "egalax", remove the corresponding packages, then download the right ones and install them again. To remove all calibration information, simply delete the file /usr/lib/X11/xorg.conf.d/97-touchscreen-calibration.conf using the following command:
```

sudo rm /usr/lib/X11/xorg.conf.d/97-touchscreen-calibration.conf

```
If you changed the file /etc/X11/xorg.conf, it's probably best if you also remove that file. After a reboot, everything should hopefully work then.

If you tried other things like the proprietary EETI driver, it's more difficult to get rid of them. 

@DheathNone:
When you swipe your fingers on the desktop, twofing simply emits Ctrl+Alt+Left and Ctrl+Alt+Right key presses. As they are also default in Metacity, this should also work when you don't use compiz (unless you have changed the key shortcuts). At least it works for me. The only problem is that you have to perform the gesture when the Desktop has the focus, thus no other window is active. Of course twofing can be modified to send these keycodes in all applications, but then you lose horizontal scrolling. Currently, you have to adapt the source code of twofing to achieve this: In profiles.h, simply change the scrollLeftAction and scrollRightAction of all profiles (also the default profile) to the value used in the profile for the window id "desktop_window" and compile twofing then. In the future, I plan to make the profiles configurable using configuration files, so you no longer have to change the source code.

---

### Post by riccardo.depalo on 2010-10-05
@Plippo: I think anyway apt-get -b is unuseful because I tried it but it builds automatically the deb files with the patches, as it comes from the repository. I tried to get rid of the patches but something went wrong, because I didn't change the version number, maybe.

The source with apt-get source seems different from this source here: [https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3](https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3)

it seems there are no patches here... or am I wrong?

---

### Post by Plippo on 2010-10-05
@riccardo: On the page you linked you find the original sources (....orig.tar.gz) and the patches (....diff.gz) as separate archives, not as a whole as apt-get source gets it, or did I just not see it?

Oh, and I tried the Debian packages. The problem is that they have a lower version number, so apt will always try to update them with the Ubuntu packages. I guess the only way is to manually create packages, I will hopefully be able to take care of this before the 10th. Maybe I set up a PPA for this.

---

### Post by riccardo.depalo on 2010-10-05
@Plippo: so, installing that source from that link without the patches, with make and sudo make install would be a right way to do it or apt-get would go on installing its own version of evdev?

by the way, I was able to reproduce the zoom problem: it's compiz related. When I abilitate desktop effects, zooming desappears in browsers and pdf, doc viewers.

---

### Post by DheathNone on 2010-10-05
> **Plippo said:**
> 
@DheathNone:
When you swipe your fingers on the desktop, twofing simply emits Ctrl+Alt+Left and Ctrl+Alt+Right key presses. As they are also default in Metacity, this should also work when you don't use compiz (unless you have changed the key shortcuts). At least it works for me. The only problem is that you have to perform the gesture when the Desktop has the focus, thus no other window is active. Of course twofing can be modified to send these keycodes in all applications, but then you lose horizontal scrolling. Currently, you have to adapt the source code of twofing to achieve this: In profiles.h, simply change the scrollLeftAction and scrollRightAction of all profiles (also the default profile) to the value used in the profile for the window id "desktop_window" and compile twofing then. In the future, I plan to make the profiles configurable using configuration files, so you no longer have to change the source code.

Thanks! The code was easier to edit to to do that than I thought.
:KS

I just wish that after a few bigger versions updates this would work on every linux-running-MT-devices.

---

### Post by aldamuhu on 2010-10-06
Hi all,

I'm planing to buy a Asus Eee PC T101MT, but I'm unsure if all will work under Ubuntu. On my search through Google and in this forum I couldn't find any user experience reports about that. I just found [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT), which looks like some handicraft work is needed.

Does anybody run the recent Ubuntu Netbookremix on the Eee PC T101MT? Does multi touch work with it? How fast is it responding? I'm especially interested if the pen recognition is good, because I would mainly use it the multi touch to write  along while listening to university lectures. For this a handwriting to fonts like Arial would be great. On the product description it is mentioned, that the multi touch can remove the heel of the hand while using the pen, which sounds good as the hand doesn't have to fly over the screen while writing, especially when writing for a long time. 
But I guess this is a feature of the proprietary windows drivers Asus made, is there something like that for Ubuntu? Hope you get what I would like to know. :P

<Edit:> I would rate my Linuxexperience somewhere in the middle. Meaning I'm not completely new to it. I'm using Ubuntu for some time know, I also did a LPI-Certification, tbh. Maybe this point is interesting for giving answers to my questions. </Edit>

Thanks for your answers.
Regards

---

### Post by riccardo.depalo on 2010-10-06
@Aldamuhu: I've tried netbook remix but actually changed to gnome version of Ubuntu, because I'm more used to it and you can easily hide or move panels if you need more space. It seemed working enough well, at least the Lucid version, because the Maverick one I tried later was only an Alpha and I can't tell how it works now. There is a new interface, called Unity, on the left, useful for touchscreen, to launch applications.

The stylus works well with the multitouch package made by Plippo, sensitive to different levels of pressure. There are some bugs that developers are trying to get fixed, and there is still something to do, in order to make anything work well. Anyway, it seems to me better than Windows, in the end, especially with the new Intel Linux driver.

---

### Post by aldamuhu on 2010-10-07
Ok it looks like nobody uses this with all it's features. Maybe the hardware is not fully compatible. I won't buy this machine, without knowing if it will work for me. :(

---

### Post by riccardo.depalo on 2010-10-07
@Plippo: I confirm that if I turn on compiz desktop effects, also "normal" choice in metacity, twofing zooming desappears in browsers nautilus and text viewers. There must be something wrong there, or it is just because there is no real graphic card. Regards.

@Aldamuhu: sorry if I wasn't useful, anyway I'm satisfied with T101MT.

---

### Post by Kevrox on 2010-10-08
> **DheathNone said:**
> I made it to one command for my own pleasure:

```

#!/bin/bash
if (xrandr --verbose | grep "Transform:  1.25" -q)
then
    xrandr --output LVDS1 --scale 1x1
else
    xrandr --fb 1280x1024 --output LVDS1 --scale 1.25x1.7
fi
```I hope it will help someone else too.:

the above works a treat, but is there a way I can have similar to scale to this 
xrandr --fb 1280x1024 --output LVDS1 --scale 1.33x1.25
and back to 1:1 again.

cheers kev

I tried to make this but did not revert to 1:1 wide screen
#!/bin/bash
if (xrandr --verbose | grep "Transform:  1.33" -q)
then
    xrandr --output LVDS1 --scale 1x1
else
    xrandr --fb 1280x1024 --output LVDS1 --scale 1.33x1.25
fi

---

### Post by Plippo on 2010-10-09
@riccardo:
Really strange, I am using Compiz too and have no problem. Can you zoom with Ctrl+Scroll wheel? That's exactly what twofing sends when you perform the zoom gesture.

I created a patch-less evdev package for Maverick and uploaded it to a PPA. Could you please test it? If it works, we can add it to the instructions. (I also plan to add other packages to the PPA, but I have to change them before so they can be built automatically by launchpad instead of my manual build script)
The PPA is: [https://launchpad.net/~plippo/+archive/t101mt]("https://launchpad.net/%7Eplippo/+archive/t101mt")
If you add the PPA to your package sources, a new Update for evdev should be available which will be the working version for the T101MT.

---

### Post by riccardo.depalo on 2010-10-09
@Plippo: your evdev package works, with all gestures working in twofing, zooming, kinetic scrolling included. It seems not different from the previous I had installed, with your two files added, anyway it is certainly easier to get it from PPA. I go on having some problems with compiz, but I noticed that, if zooming hangs on browser, I have to turn off desktop effects in metacity and turn on compiz with compiz --replace. In this case, zooming go back working, with all effects enabled.

When it happens, sometimes on reboot, that zooming hangs, even if I added the command copiz --replace on startup, I notice that I still can zoom in/out with ctrl-/+. But, I don't know why, sometimes I have to turn off effects in metacity and enable them directly on terminal.

Thank you, it is a great idea to use a PPA!

---

### Post by riccardo.depalo on 2010-10-10
@Plippo: it seems I have resolved the compiz related problem. In order to load compiz at boot, I wrote a script called compiz.sh:
```
#!/bin/sh
sleep 5
metacity --replace ccp & compiz --replace
```

made it executable:

```
sudo chmode +x compiz.sh
```

added at startup:

```
./compiz.sh
```

And now twofing seems to work properly at each boot.

@All: do anybody else has the same problem with zooming not working with compiz?

---

### Post by DheathNone on 2010-10-10
@Kevrox: If you do:
xrandr --verbose | grep "Transform:"
You'll see that:
"Transform:  1.329987 0.000000 0.000000"
[]("http://ubuntuforums.org/member.php?u=640694") 				 				 			
  			Seems that the scale is not exact.
Use 1.32 instead.

By the way why is the right clicking not done like on Windows side but whit the twofing? (You hold => right click) 
Is it patented or something?

---

### Post by riccardo.depalo on 2010-10-10
@Plippo and @All: As the new Ubuntu 10.10 is released, I duplicated the wiki and I am editing a new one, for Maverick Merkaat only: [https://help.ubuntu.com/community/T101MT-MAVERICK](https://help.ubuntu.com/community/T101MT-MAVERICK)

Work is still in progress...  I added Plippo's PPA, deleted two finger with the touchpad which seems no more working, made some integrations and changes.

I think it should be easier this way. Or the dupliction get some of you more confused? Any ideas, help or suggestions are, of course, welcome.

---

### Post by Plippo on 2010-10-11
@riccardo:
Too bad I can't reproduce the zooming problem although I use compiz.

But thanks for adding the information about the PPA to the Wiki article. Still I'm not sure if it wouldn't be better to have only one article, as both are identical for the most part and maintaining two separate articles is more work.

I have now also uploaded two new packages to the PPA, one is the common touchscreen support package which brings suspend support and touchrotate, the other one is a package which takes care of activating the correct boot options for the special keys to work, which had to be done manually before. With these additions, the instructions can be shortened a lot for Maverick. So if you are okay with that, I would rewrite the T101MT page a bit, add the new installation instructions using the PPA and move the old instructions to a section called "For Lucid users". Then the T101MT-MAVERICK article could be deleted. But if you disagree, don't hesitate to tell me.

---

### Post by riccardo.depalo on 2010-10-11
@Plippo: it's ok for me to use only one wiki, if you put somewhere in the end the older instructions. You can use some new paragraph I added in the new wiki and revise them as you wish.

---

### Post by fastler on 2010-10-11
OK, this is a totally "help me, I am helpless" post here, but I had everything working a little back, and now everything seems to have gone to heck. So I present to you, the most benificient and able coders, an enumerated list of my Problems with my T101MT running Ubuntu.

1) This is a biggy, but my computer will no longer hibernate or go to standby. This seemed to start after a scheduled update. And before you ask, my swap space is a good couple of gigabytes larger then my ram.

2)The touchscreen is no longer working, or rather, it is not at all useful, wherever I touch the screen, the cursor click on the top left corner of the screen.

3) I like the two finger touch-pad scrolling, and I set that up. Every now and then, it doesn't work and trying to do it makes the cursor flip out. It used to be that every now and then it wouldn't work, but restarting would fix it, but now it never seems to work.

So there you have it. If anyone can shed any light on this slew of problems, I would be most grateful. I think they were brought on by a recent update, but I know very little about most of this stuff.

---

### Post by riccardo.depalo on 2010-10-11
@Fastler: answer a few question, please, so we can help you. Do you have installed Lucid or Maverick? What kernel have you installed?  Did you follow the instructions in the tutorial to install the touchscreen driver?

---

### Post by fastler on 2010-10-11
@ricardo
Sure. I am using lucid Lynx (I wasn't even aware they had updated until today), Kernel type 2.6.32-25-generic, and everything I have done is from this first page. Except the two finger scrolling, which was from the wiki page for the laptop.

---

### Post by riccardo.depalo on 2010-10-11
@fastler: ok, if you go here: [https://help.ubuntu.com/community/T101MT#TOUCH SCREEN]("https://help.ubuntu.com/community/T101MT#TOUCH SCREEN") 

you can find the deb file for the 2.6.32-25. Just install it and touchscreen should be working again.

---

### Post by fastler on 2010-10-11
OK, well, evidently that solved all three of my problems. Nice. Many thanks.

---

### Post by Plippo on 2010-10-12
@fastler:
The problem with the touchpad occurs if you have booted Windows, then reboot into Ubuntu. Windows switches the touchpad into a different mode Ubuntu can't handle. So when you have used Windows, simply shut down the machine and then turn it on again instead of rebooting in order to avoid this problem.

@riccardo:
I have modified the wiki page, I hope it is okay. I'll continue uploading more packages to the PPA which automate the manual steps and will adapt the page accordingly.

---

### Post by riccardo.depalo on 2010-10-12
@Plippo: I saw the wiki modified, it seems ok to me. Thank you for your work. Can we delete the other wiki, to avoid confusion?

---

### Post by Plippo on 2010-10-12
If you think I haven't forgotten anything on the T101MT page, you can of course delete the Maverick page if you like.

---

### Post by tlimsisnw on 2010-10-12
> **Plippo said:**
> If you think I haven't forgotten anything on the T101MT page, you can of course delete the Maverick page if you like.

Plippo: I tried to connect to PPA but got the following problem. Please advise, thanks.

[B]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4D8BB0C41D2329136CB7858AC3745BE8983882DF
gpg: requesting key 983882DF from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
[/B]

---

### Post by Plippo on 2010-10-13
@tlimsisnw: Looks like a temporary network problem, please just try again.

---

### Post by tlimsisnw on 2010-10-13
Thanks, it did work now.

---

### Post by tlimsisnw on 2010-10-13
Plippo: Twofing has a slight bug in that the spot directly under the fingers tend to over-run the final position where the finger stops, i.e. if the fingers are continuous in touch with the screen during dragging. This may be due to the kinetic. Would be good if this could be rectified for better control. Thanks for the PPA, its a great help for updates.

---

### Post by riccardo.depalo on 2010-10-13
I added just a few notes about the bugs in the end of the wiki, for anybody interested. Hoping they will be fixed for Ubuntu soon. The Maverick wiki was deleted, and only one is available, so it's easier for any user.

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

@Plippo: I saw you uploaded a deb file to get two finger scrolling with the touchpad. That's nice, so it works now also in Maverick.

---

### Post by Plippo on 2010-10-14
@riccardo:
Thanks, I edited it a bit so users know that these bugs have no effect if they follow the instructions. The kernel bug has already been fixed upstream in the linux kernel and thus will most likely be fixed at least in Ubuntu 11.04.

---

### Post by riccardo.depalo on 2010-10-14
> **Plippo said:**
> @riccardo:
Thanks, I edited it a bit so users know that these bugs have no effect if they follow the instructions. The kernel bug has already been fixed upstream in the linux kernel and thus will most likely be fixed at least in Ubuntu 11.04.

Very well done, Plippo. I wonder if also bugs related to screen brightness and webcam appearing upside/down can be fixed.

---

### Post by bakinsoda on 2010-10-19
Hi everyone,

I recently did a fresh install of Ubuntu 10.10 on this netbook.  Glad to see that both suspend and hibernate works out of the box.

I followed wiki pretty closely.  I installed t101mt-kernel-driver-new3.tar.gz from source.  However, when I do a rotate via 'touchrotate left', the touchscreen doesn't seem to match that of the screen.  Anyone else getting this or am I missing something?

Also, does anyone notice that 10.10 appears to be slower than 10.04?  Probably due to Unity, although it's supposed to be faster.

---

### Post by bakinsoda on 2010-10-19
> **bakinsoda said:**
> 

I followed wiki pretty closely.  I installed t101mt-kernel-driver-new3.tar.gz from source.  However, when I do a rotate via 'touchrotate left', the touchscreen doesn't seem to match that of the screen.  Anyone else getting this or am I missing something?

.

Disregard this part of my previous post.  I did not do:
sudo apt-get install build-essential fakeroot linux-headers-generic linux-source

Just added that to the wiki to make things more clear.  Thanks.

---

### Post by bakinsoda on 2010-10-19
This might not be the best place to ask, but I'll give it a shot since the authors are responsive here.

When you guys launch gnome terminal, say via Control + Alt + t, can you guys paste text via Control+Shift+v or through the menu?  I can only paste by right-clicking.

Thanks

---

### Post by linxgr on 2010-10-19
I have been using this thread a long time now and I have to tell almost everything worked out pretty fine. I have installed twofing but don't use the touchscreen that much for anything other than single touch open apps and scribbling in Xournal. What I wanted to ask is if all that patches and workarounds that ppl have posted in here will work for the maverick version. Is there anything we gain from the new version? Should I upgrade? Can all the goodies from Maverick be installed in lucid since its an LTS version?

---

### Post by riccardo.depalo on 2010-10-19
@Bakinsoda: Hi, Ubuntu 10.10 seems to me a little faster than 10.04, but I'm using normal Gnome version, because Unity doesn't satisfy me. I'm trying actually to use some docks on the desktop. Cairo dock still seems to me the best even if it's not done for touchscreen and it's not the easiest to use. And.. yeah, you need Compiz.

@Linxgr: with Plippo's PPA I think it's also easier now to install maverick than Lucid. But it's not so different. If you're ok with 10.04, and it works, you can avoid upgrading. But the repository is done for Maverick, not for Lucid.

---

### Post by mrspacklecrisp on 2010-10-19
There is a google chrome extension for page grabbing, in case no one has noticed. Unfortunately, it causes some annoying usability issues in gmail.... You can disable it, but it's not easy and quick.
[URL="https://chrome.google.com/extensions/detail/ljecomdaijmibecakcpjadigpfkollbh?hl=en"]
https://chrome.google.com/extensions/detail/ljecomdaijmibecakcpjadigpfkollbh?hl=en[/URL]

Over and out.

---

### Post by tlimsisnw on 2010-10-19
> **bakinsoda said:**
> This might not be the best place to ask, but I'll give it a shot since the authors are responsive here.

When you guys launch gnome terminal, say via Control + Alt + t, can you guys paste text via Control+Shift+v or through the menu?  I can only paste by right-clicking.

Thanks

Yes, I found that Ctrl+Shift+v doesn't work anymore after the upgrade, but menu works. I'm currently using unity.

---

### Post by bakinsoda on 2010-10-19
Ricardo: Yea, I don't like Unity either.  Forgot I had the regular desktop.  Am using it now and things are a lot faster.

tlimsisnw: thanks for the confirmation.  It's also broken in the regular gnome desktop, so it must be a gnome terminal thing [https://bugs.launchpad.net/bugs/630383](https://bugs.launchpad.net/bugs/630383)

One more thing to report.  I installed MyPaint per the wiki. However, both touchscreen and touchpad seem to not be able to paint.  Anyone else getting this?

---

### Post by mrspacklecrisp on 2010-10-20
> **bakinsoda said:**
> Ricardo: Yea, I don't like Unity either.  Forgot I had the regular desktop.  Am using it now and things are a lot faster.

tlimsisnw: thanks for the confirmation.  It's also broken in the regular gnome desktop, so it must be a gnome terminal thing [https://bugs.launchpad.net/bugs/630383](https://bugs.launchpad.net/bugs/630383)

One more thing to report.  I installed MyPaint per the wiki. However, both touchscreen and touchpad seem to not be able to paint.  Anyone else getting this?

I updated the kernel to 32-25, uninstalled the old driver and installed the appropriate driver, and found mypaint in the condition you describe and gimp lacking pressure sensitivity. I reinstalled both programs. That fixed gimp, but not mypaint.

I have a suggestion about mypaint, actually. I don't know what Plippo altered in mypaint to make it work for us, but perhaps a better solution would be to write a patch (which includes the brush fix) so that we might be able to update our mypaint installs (version 9 is already out now)

@Plippo: When you corrected the pen pressure issue in mypaint, what did you alter?

Also, trying out Jupiter to gain SHE-like overclocking. I'll let y'all know how that goes.

---

### Post by Plippo on 2010-10-20
> **mrspacklecrisp said:**
> 
I have a suggestion about mypaint, actually. I don't know what Plippo altered in mypaint to make it work for us, but perhaps a better solution would be to write a patch (which includes the brush fix) so that we might be able to update our mypaint installs (version 9 is already out now)


Good idea. I already created a patch for my changes, I will add the brush fixes later. Strangely though, the "old" mypaint still works for me in Maverick.

---

### Post by tlimsisnw on 2010-10-20
I found some times in Maverick that dialog boxes hide behind other windows, and I thought they didn't appear for a long time. Then I found them by Alt-Tab. Anyone else experiences the same bug? It that due to unity?

---

### Post by Plippo on 2010-10-20
Okay, here is the mypaint patch, it is attached to this post. To use it, do the following:

[LIST=1]
[*]Uninstall mypaint if you have installed the package from the wiki or this thread
[*]Install the mypaint package from the normal Ubuntu repository, e.g. using Software Center
[*]Download the attached (compressed) patch file and save it to your home directory.
[*]Open a terminal and execute the following commands:
[/LIST]
```

gzip -d mypaint-resistive.patch.gz
sudo patch -p1 -d /usr/share/mypaint < mypaint-resistive.patch

```Enjoy!

---

### Post by Merde on 2010-10-20
hello all

a global "thanks" to all contributors to this thread, and a special  "thanks" for Plippo !

little contribution : 
I discovered an extension for chromium which is similar to firefox "drag & grab" 
(not the same extension than what mrspacklecrisp propose)

[http://www.chromeextensions.org/appearance-functioning/chrometouch/](http://www.chromeextensions.org/appearance-functioning/chrometouch/)

Some features do not work for me (page up / page down, rebound), but main functionalities are OK.

previous link added to documentation 


bye all

---

### Post by mrspacklecrisp on 2010-10-20
Good news and bad news.

Good news is, Jupiter is an awesome little utility which taps into the almighty power of the built-in Super Hybrid Engine. It adds a bit of battery life (not sure how much yet), and when I want to play Zelda I can rev up the SH Engine and get 2-3 times the frame rate. It's great, seriously. Learn about it and download (remember to download the eee support package) [http://www.fewt.com/2010/02/meet-jupiter.html]("http://www.fewt.com/2010/02/meet-jupiter.html")

Note: The version for Ubuntu is not being updated anymore, because the author didn't like constantly fixing bugs. I've had absolutely no problems, and it certainly seems to work as it should, but it *might* do something weird on your system. Also, be wary of overheating.


Bad news is, the patch doesn't work for mypaint 9.0 beta, which is basically what the upcoming full release will be in 2-4 weeks. Only a few lines at the end were successfully changed. This is due, I think, to the reorganization of the brush files. My output after trying to apply the patch:

```
sav@sav-netbook:~$ sudo patch -p1 -d ~/Downloads/mypaint-0.9.0-beta1 < ~/Downloads/mypaint-resistive.patch
patching file brushes/100%_Opaque.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/100%_Opaque.myb.rej
patching file brushes/4B_pencil.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/4B_pencil.myb.rej
patching file brushes/acrylic-01-only-water.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/acrylic-01-only-water.myb.rej
patching file brushes/acrylic-02-only-water.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/acrylic-02-only-water.myb.rej
patching file brushes/acrylic-03-only-water.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/acrylic-03-only-water.myb.rej
patching file brushes/acrylic-05-only-water.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/acrylic-05-only-water.myb.rej
patching file brushes/acrylic-05-paint.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/acrylic-05-paint.myb.rej
patching file brushes/acrylic-05-with-water.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/acrylic-05-with-water.myb.rej
patching file brushes/Airbrush.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Airbrush.myb.rej
patching file brushes/aspec_fun_5.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/aspec_fun_5.myb.rej
patching file brushes/aspect_fun_1.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/aspect_fun_1.myb.rej
patching file brushes/basic-flat.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/basic-flat.myb.rej
patching file brushes/Brush_blur.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Brush_blur.myb.rej
patching file brushes/charcoal.myb
Hunk #1 FAILED at 14.
1 out of 1 hunk FAILED -- saving rejects to file brushes/charcoal.myb.rej
patching file brushes/Classic_Paint.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Classic_Paint.myb.rej
patching file brushes/Clouds.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Clouds.myb.rej
patching file brushes/Delayed_Line.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Delayed_Line.myb.rej
patching file brushes/dry_brush.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/dry_brush.myb.rej
patching file brushes/Dust.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Dust.myb.rej
patching file brushes/fur.myb
patching file brushes/Glazing.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Glazing.myb.rej
patching file brushes/glow.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/glow.myb.rej
patching file brushes/Glow_ramon.myb
Hunk #1 FAILED at 19.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Glow_ramon.myb.rej
patching file brushes/Grain.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Grain.myb.rej
patching file brushes/Grass_1.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Grass_1.myb.rej
patching file brushes/Grass_2.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Grass_2.myb.rej
patching file brushes/Grass_3.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Grass_3.myb.rej
patching file brushes/Grass_P.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Grass_P.myb.rej
patching file brushes/hair.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/hair.myb.rej
patching file brushes/Hair_.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Hair_.myb.rej
patching file brushes/Hard_Eraser.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Hard_Eraser.myb.rej
patching file brushes/HardSoft.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/HardSoft.myb.rej
patching file brushes/Ico_Alias_Brush.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Alias_Brush.myb.rej
patching file brushes/Ico_Calligraphic_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Calligraphic_Pen.myb.rej
patching file brushes/Ico_Calligraphic_Pen_noborder.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Calligraphic_Pen_noborder.myb.rej
patching file brushes/Ico_Chaotic_Smudge.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Chaotic_Smudge.myb.rej
patching file brushes/Ico_Color_Smudge_+.myb
Hunk #1 FAILED at 19.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Color_Smudge_+.myb.rej
patching file brushes/Ico_Felt_pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Felt_pen.myb.rej
patching file brushes/Ico_Flat_Basic.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Flat_Basic.myb.rej
patching file brushes/Ico_Flat_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Flat_Pen.myb.rej
patching file brushes/Ico_Hard_Eraser.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Hard_Eraser.myb.rej
patching file brushes/Ico_Hard_Oil.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Hard_Oil.myb.rej
patching file brushes/Ico_Impressionism_01.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Impressionism_01.myb.rej
patching file brushes/Ico_Impressionism_02.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Impressionism_02.myb.rej
patching file brushes/Ico_Linear_Watercolor.myb
Hunk #1 FAILED at 19.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Linear_Watercolor.myb.rej
patching file brushes/Ico_Mod_Deevad_Basic.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Mod_Deevad_Basic.myb.rej
patching file brushes/Ico_OC_Brush.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_OC_Brush.myb.rej
patching file brushes/Ico_OC_Hard_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_OC_Hard_Pen.myb.rej
patching file brushes/Ico_OC_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_OC_Pen.myb.rej
patching file brushes/Ico_Oil_Blender_B.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Oil_Blender_B.myb.rej
patching file brushes/Ico_Oil_Blender_C.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Oil_Blender_C.myb.rej
patching file brushes/Ico_Oil_Blender.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Oil_Blender.myb.rej
patching file brushes/Ico_Pastel_Stain.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Pastel_Stain.myb.rej
patching file brushes/Ico_Precise_Pen_02.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Precise_Pen_02.myb.rej
patching file brushes/Ico_Precise_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Precise_Pen.myb.rej
patching file brushes/Ico_Rigid_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Rigid_Pen.myb.rej
patching file brushes/Ico_Soft_Eraser.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Soft_Eraser.myb.rej
patching file brushes/Ico_Soft_Oil.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Soft_Oil.myb.rej
patching file brushes/Ico_Variable_Flat_Pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Ico_Variable_Flat_Pen.myb.rej
patching file brushes/ink_eraser.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/ink_eraser.myb.rej
patching file brushes/ink-fill.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/ink-fill.myb.rej
patching file brushes/ink_hard.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/ink_hard.myb.rej
patching file brushes/ink.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/ink.myb.rej
patching file brushes/ink-pen.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/ink-pen.myb.rej
patching file brushes/Jitter.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Jitter.myb.rej
patching file brushes/Knife.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Knife.myb.rej
patching file brushes/long_grass.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/long_grass.myb.rej
patching file brushes/Marker.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Marker.myb.rej
patching file brushes/o945.myb
Hunk #1 FAILED at 14.
1 out of 1 hunk FAILED -- saving rejects to file brushes/o945.myb.rej
patching file brushes/Offset_Splats.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Offset_Splats.myb.rej
patching file brushes/oil-06-clean.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/oil-06-clean.myb.rej
patching file brushes/oil-06-paint.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/oil-06-paint.myb.rej
patching file brushes/PenBrush.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/PenBrush.myb.rej
patching file brushes/pencil-6b.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/pencil-6b.myb.rej
patching file brushes/pencil-8b.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/pencil-8b.myb.rej
patching file brushes/pencil-color.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/pencil-color.myb.rej
patching file brushes/pencil.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/pencil.myb.rej
patching file brushes/pointy_ink.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/pointy_ink.myb.rej
patching file brushes/P.Shade2.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/P.Shade2.myb.rej
patching file brushes/P._Shade.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/P._Shade.myb.rej
patching file brushes/Round_Bl.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Round_Bl.myb.rej
patching file brushes/Round.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Round.myb.rej
patching file brushes/RS_blendOP.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/RS_blendOP.myb.rej
patching file brushes/s004.myb
Hunk #1 FAILED at 15.
1 out of 1 hunk FAILED -- saving rejects to file brushes/s004.myb.rej
patching file brushes/s008.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/s008.myb.rej
patching file brushes/s020.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/s020.myb.rej
patching file brushes/s021.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/s021.myb.rej
patching file brushes/s023.myb
patching file brushes/short_grass.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/short_grass.myb.rej
patching file brushes/Sketch_1.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Sketch_1.myb.rej
patching file brushes/Sketch_2.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Sketch_2.myb.rej
patching file brushes/Smear.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Smear.myb.rej
patching file brushes/snow_1.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/snow_1.myb.rej
patching file brushes/snow_2.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/snow_2.myb.rej
patching file brushes/Soft_Eraser.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Soft_Eraser.myb.rej
patching file brushes/Sparks.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Sparks.myb.rej
patching file brushes/Splats_1.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Splats_1.myb.rej
patching file brushes/Splats_2.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Splats_2.myb.rej
patching file brushes/Splats_3.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Splats_3.myb.rej
patching file brushes/Splats_4.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Splats_4.myb.rej
patching file brushes/Splats_5.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Splats_5.myb.rej
patching file brushes/splatter-02.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/splatter-02.myb.rej
patching file brushes/Starfield.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Starfield.myb.rej
patching file brushes/subtle_pencil.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/subtle_pencil.myb.rej
patching file brushes/textured-angle.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/textured-angle.myb.rej
patching file brushes/textured-charcoal.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/textured-charcoal.myb.rej
patching file brushes/textured-grain.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/textured-grain.myb.rej
patching file brushes/textured_ink.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/textured_ink.myb.rej
patching file brushes/tree_2.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/tree_2.myb.rej
patching file brushes/tree.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/tree.myb.rej
patching file brushes/wet_airbrush.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/wet_airbrush.myb.rej
patching file brushes/Wet_Direction.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Wet_Direction.myb.rej
patching file brushes/wet_round.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/wet_round.myb.rej
patching file brushes/Wet_Soft.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Wet_Soft.myb.rej
patching file brushes/Wet_Solid.myb
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file brushes/Wet_Solid.myb.rej
patching file gui/tileddrawwidget.py
Hunk #2 succeeded at 36 with fuzz 2.
Hunk #3 FAILED at 169.
Hunk #4 succeeded at 243 with fuzz 1 (offset 68 lines).
1 out of 4 hunks FAILED -- saving rejects to file gui/tileddrawwidget.py.rej
sav@sav-netbook:~$ 

```

edit: Wait wait wait, I'm extremely silly. I applied the patch to the wrong place. Same output, though.

---

### Post by bakinsoda on 2010-10-20
> **Plippo said:**
> Okay, here is the mypaint patch, it is attached to this post. To use it, do the following:

[LIST=1]
[*]Uninstall mypaint if you have installed the package from the wiki or this thread
[*]Install the mypaint package from the normal Ubuntu repository, e.g. using Software Center
[*]Download the attached (compressed) patch file and save it to your home directory.
[*]Open a terminal and execute the following commands:
[/LIST]
```

gzip -d mypaint-resistive.patch.gz
sudo patch -p1 -d /usr/share/mypaint < mypaint-resistive.patch

```Enjoy!

I did this but I still don't get anything when I paint with touchpad or touchscreen.  Any thoughts?  Note I did

```

sudo apt-get autoremove mypaint
sudo rm -rf /usr/share/mypaint
sudo apt-get install mypaint
## applied patch

```

---

### Post by tlimsisnw on 2010-10-20
After installing the updates today, the window borders disappeared. Also, Ctrl+Alt+T doesn't bring up terminal anymore. Did anyone else have this problem?

---

### Post by mrspacklecrisp on 2010-10-21
> **tlimsisnw said:**
> After installing the updates today, the window borders disappeared. Also, Ctrl+Alt+T doesn't bring up terminal anymore. Did anyone else have this problem?

Not me, but I'm still on Lucid. Not that I checked very carefully, but I don't recall any incredibly recent updates that had to do with the GUI, and there were absolutely none for the last day or so.

---

### Post by mrspacklecrisp on 2010-10-21
> **Merde said:**
> hello all

a global "thanks" to all contributors to this thread, and a special  "thanks" for Plippo !

little contribution : 
I discovered an extension for chromium which is similar to firefox "drag & grab" 
(not the same extension than what mrspacklecrisp propose)

[http://www.chromeextensions.org/appearance-functioning/chrometouch/](http://www.chromeextensions.org/appearance-functioning/chrometouch/)

Some features do not work for me (page up / page down, rebound), but main functionalities are OK.

previous link added to documentation 


bye all

I'm nervous about the part that says it has access to my browsing history and other data. I think I'll stick with official extensions.

---

### Post by tlimsisnw on 2010-10-21
> **mrspacklecrisp said:**
> Not me, but I'm still on Lucid. Not that I checked very carefully, but I don't recall any incredibly recent updates that had to do with the GUI, and there were absolutely none for the last day or so.

Ok, I seem to have resolved the missing window border problem after doing a "apt-get -f install" to repair broken packages. However, it's funny that now I lose zooming ability in Plippo's twofing using the maverick desktop version. Zooming still ok if I login to netbook/unity version. Wonder why that is.

Jupiter seem to work much better now. I did recommend it here a while back, but I think this new version seems to manage power a bit better. For the first time, my battery left says 6.25 hrs under power saver!

Plippo: Mypaint patch works well.

---

### Post by riccardo.depalo on 2010-10-21
@Plippo: I updated the wiki with your mypaint patch (I tested it, it works) and specified that also 64 bit Ubuntu works if you build yourself kernel driver. Is it correct?

---

### Post by Plippo on 2010-10-22
@mrspacklecrisp:
Haven't looked at 9.0 yet. If you can figure out the differences in the new brush file format, this would be helpful

@bakinsoda:
So you're using Maverick, right? Have you installed the evdev update from the PPA as described in the wiki article?

@riccardo:
Thanks! The driver works in 64 bit, but there seem to be problems with twofing. I'll investigate that.

---

### Post by mrspacklecrisp on 2010-10-23
The brushes are all categorized into subfolders, with the exception of 13 of them. There are also plenty of new brushes. 

The other things I'm seeing is that [s]this line "self.doc.stroke_to(dtime, x, y, pressure)" isn't in 9 at all[/s], "self.last_painting_pos = x, y" is now on line 205, "def button_press_cb(self, win, event):" is over on line 233, def...release_cb is on 250 and def...modified_cb is on 255.

I don't really understand why it said it succeeded at line 243, offset by 68 (line 175, right?) "
        # mouse button pressed (while painting without pressure information)" is what's on 243. I mean, "self.motion_notify_cb" is close on line 248, and "def canvas_modified_cb" (which is on line 175 in mypaint 8 ) is also close on 255... but I don't understand the correlation.

I don't know much of anything, so forgive me if this isn't that helpful. This program is really great, so I'm happy there's any working version available. It's really good for studies, I've found:

[IMG]http://i56.tinypic.com/11si0pt.png[/IMG]
He looks so weird. There are supposed to be people under him. Anyway...

**Edit1:** I was wrong about the phrase "self.doc.stroke_to". It's in mypaint 9's tiledrawwidget.py on lines 228 and 231, as "self.doc.stroke_to(step, *data_old)" and " self.doc.stroke_to(dtime, *data)" respectively.

---

### Post by mrspacklecrisp on 2010-10-24
When I updated my tablet driver, I found the calibration a off in places so I tried to use the ol' calibrator. That totally messed up my calibration, so I decided I would uninstall it, then install it again. However, the package is not mentioned in the wiki and I don't remember where to get it.

---

### Post by Plippo on 2010-10-24
@mrspacklecrisp:
Yes, as the calibrator often brought problems, I removed it from the wiki page. But you can still download and try the latest version from [http://philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-2-i386.deb](http://philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-2-i386.deb)

I've been working for some time now on a new calibration infrastructure. It features a new calibrator and automatic adjustment of the touchscreen when the monitor output is rotated or when an external display is added. I hope to be able to release it soon.

Please bear with me if taking care of MyPaint 9.0 might still take some time as I'm a bit busy at the moment. At least 8.2 still works...

---

### Post by mrspacklecrisp on 2010-10-24
> **Plippo said:**
> @mrspacklecrisp:
Yes, as the calibrator often brought problems, I removed it from the wiki page. But you can still download and try the latest version from [http://philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-2-i386.deb](http://philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-2-i386.deb)

I've been working for some time now on a new calibration infrastructure. It features a new calibrator and automatic adjustment of the touchscreen when the monitor output is rotated or when an external display is added. I hope to be able to release it soon.

Please bear with me if taking care of MyPaint 9.0 might still take some time as I'm a bit busy at the moment. At least 8.2 still works...

Oh, of course. I'm more than thrilled with the selfless amount of work you've contributed, as we all are. I certainly don't mean to pressure you at all, I'm absolutely happy and satisfied with the state of my computer.

---

### Post by mrspacklecrisp on 2010-10-25
No pressure sensitivity anymore.... Am I missing something, or are others experiencing this?

---

### Post by airnike on 2010-10-25
I didn't have any time to mess around with this yet but those who are looking for palm rejection for Xournal may want to look at the following patches on sourceforge.

[http://sourceforge.net/tracker/?func=detail&aid=3026585&group_id=163434&atid=827735](http://sourceforge.net/tracker/?func=detail&aid=3026585&group_id=163434&atid=827735)

---

### Post by mrspacklecrisp on 2010-10-26
The patches didn't work when I tried to apply them. I'm not sure I understand the point, though. They turn off the ability to write in an application for handwritten notes? I think this may be meant for touchscreens that have the ability to distinguish between the pen and a hand. What is needed is something which can distinguish between a first touch and a second simultaneous touch, and ignore the second with the assumption that it's your palm.

Also, my problem with pressure sensitivity is with the driver. Not sure when this started, currently messing with things to try to fix it.

Edit1: Built my own driver, no go. Sigh... Evtest still reports pressure on device 7, so at least I know it's not broken, like I suspected. Somebody mentioned a while back that their touchscreen was being treated as though it were a touchpad, which may be my problem after recently upgrading to kernel 2.6.32-25. Before, when I had configured GIMP and Mypaint for the touchscreen, I was unable to use the touchpad to draw in either. Now I'm able to; the touchscreen and the touchpad are functionally the same...

---

### Post by Plippo on 2010-10-27
@airnike:
As mrspacklecrisp already wrote, this seems to be only for systems where the stylus is independent from the touchscreen. On the T101MT, the stylus is just a piece of plastic that can be used to touch the screen, but the screen can't distinguish between finger and stylus.

@mrspacklecrisp:
If evtest reports Pressure events (code 27) and they are neither recognized by Gimp, MyPaint or Xournal, I can see two possible reasons.
One reason could be that twofing blocks the input, so if you use twofing, you can try stopping it with *killall twofing* and look if pressure works then.
The other reason I can think of is that there could be a problem with evdev. You could try starting the synaptic package manager, looking for the package xserver-xorg-input-evdev, then selecting from the menu **Package › Force Version...** and look if there are older versions available.

---

### Post by mrspacklecrisp on 2010-10-27
@Plippo
Thank you for offering these solutions, but unfortunately stopping twofing didn't work and evidently it isn't possible to downgrade evdev. The menu item you mentioned is grayed out, and when I tried to replace it with karmic's version, it wouldn't allow me to uninstall it (no surprise) So, with little to no knowledge of what I speak, I surmise that the issue is correlated to my recent kernel update, before which I could paint with pressure.

 I could try to downgrade the kernel, but to do so seems like it would be complicated and/or dangerous.

---

### Post by Plippo on 2010-10-28
@mrspacklecrisp:
Well, if evtest reports the Pressure events with correct values, it's most likely not a kernel issue. You could try the following commands and post the results:
```

xinput list-props "eGalax Inc. USB TouchController"
xinput list --long "eGalax Inc. USB TouchController"

```
It would be good if you could press the touchscreen with the stylus while you hit the enter key to execute the second command so the pressure value can be checked.

---

### Post by mrspacklecrisp on 2010-10-28
> **Plippo said:**
> @mrspacklecrisp:
Well, if evtest reports the Pressure events with correct values, it's most likely not a kernel issue. You could try the following commands and post the results:
```

xinput list-props "eGalax Inc. USB TouchController"
xinput list --long "eGalax Inc. USB TouchController"

```It would be good if you could press the touchscreen with the stylus while you hit the enter key to execute the second command so the pressure value can be checked.
```
Device 'eGalax Inc. USB TouchController':
    Device Enabled (134):    1
    Device Accel Profile (254):    0
    Device Accel Constant Deceleration (255):    1.000000
    Device Accel Adaptive Deceleration (257):    1.000000
    Device Accel Velocity Scaling (258):    10.000000
    Evdev Reopen Attempts (249):    10
    Evdev Axis Inversion (259):    0, 0
    Evdev Axis Calibration (260):    <no items>
    Evdev Axes Swap (261):    0
    Axis Labels (262):    "Abs X" (251), "Abs Y" (252), "Abs Pressure" (253), "None" (0), "None" (0), "None" (0), "None" (0)
    Button Labels (263):    "Button Unknown" (250), "Button Unknown" (250), "Button Unknown" (250), "Button Wheel Up" (138), "Button Wheel Down" (139)
    Evdev Middle Button Emulation (264):    2
    Evdev Middle Button Timeout (265):    50
    Evdev Wheel Emulation (266):    0
    Evdev Wheel Emulation Axes (267):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (268):    10
    Evdev Wheel Emulation Timeout (269):    200
    Evdev Wheel Emulation Button (270):    4
    Evdev Drag Lock Buttons (271):    0

```

```
eGalax Inc. USB TouchController             id=10    [slave  pointer  (2)]
    Reporting 8 classes:
        Class originated from: 10
        Buttons supported: 5
        Button labels: Button Unknown Button Unknown Button Unknown Button Wheel Up Button Wheel Down
        Button state: 1
        Class originated from: 10
        Detail for Valuator 0:
          Label: Abs X
          Range: 0.000000 - 4095.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 254.000000
        Class originated from: 10
        Detail for Valuator 1:
          Label: Abs Y
          Range: 0.000000 - 4095.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 2326.000000
        Class originated from: 10
        Detail for Valuator 2:
          Label: Abs Pressure
          Range: 1.000000 - 2047.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 1376.000000
        Class originated from: 10
        Detail for Valuator 3:
          Label: None
          Range: 0.000000 - 4095.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 254.000000
        Class originated from: 10
        Detail for Valuator 4:
          Label: None
          Range: 0.000000 - 4095.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 2326.000000
        Class originated from: 10
        Detail for Valuator 5:
          Label: None
          Range: 0.000000 - 32.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 10
        Detail for Valuator 6:
          Label: None
          Range: 1.000000 - 2047.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 1376.000000

```

Thank you so much, I really appreciate the help.

---

### Post by zhopan77 on 2010-10-29
First, many thanks for all the great people here helping us. I got most of the things working on my T101MT which is great!

The method mentioned below somehow didn't work for me. My work around that worked is to first switch user to root, then use any editor to insert the following lines copied from Plippo in /etc/rc.local, before "exit 0"

```

rmmod usbhid 
rmmod hid 
modprobe hid 
modprobe usbhid quirks=0x0486:0x0186:0x004 

```

Then reboot... 

> **Plippo said:**
> Just create (with root rights) a file with any name that ends with .conf (e.g. touchscreen.conf) in /etc/modprobe.d with the following content:
```
options usbhid quirks=0x0486:0x0186:0x0040
```

This should do the trick.

---

### Post by Plippo on 2010-10-29
@mrspacklecrisp:
Hmm, in your output everything looks okay, XInput recognizes the pressure information. It's strange that it doesn't reach the applications. I would recommend creating a new user profile and check if the problem also occurs there.

@zhopan77:
Well, it's possible that modprobe.d is no longer available now, I haven't used this method for a long time. I would recommend you follow the new method available on the wiki page which provides pressure sensitivity and multitouch.

---

### Post by mrspacklecrisp on 2010-10-29
@Plippo

You got the right idea; pressure works in a new user profile. Thanks so much! How strange, though... I wonder what I did to kill my pressure sensitivity across the board....

---

### Post by riccardo.depalo on 2010-10-29
Hi everybody, as a new kernel 2.6.35-23 was available for Maverick, I build, tested and uploaded a new deb file. You can find it in the wiki. As usual, I had to update kernel headers and source.

---

### Post by Plippo on 2010-10-30
> **riccardo.depalo said:**
> Hi everybody, as a new kernel 2.6.35-23 was available for Maverick, I build, tested and uploaded a new deb file. You can find it in the wiki. As usual, I had to update kernel headers and source.
Thanks! You're much better at providing new versions quickly than me...

---

### Post by scimor5 on 2010-10-31
My touch screen doesn't do anything after sleep anymore, I am using kernal 2.6.35-22-generic. I looked though some previous posts, and another guy with a similar problem was told to look for a file in the /etc/pm/sleep.d/ directory, I don't have it, all i have is 10_grub-common and 10_unattended-upgrades-hybernate. I'm thinking that is probably the problem? if that is the problem how do i fix it? thx. 

Thanks for everything you guys have done, my T101MT wouldn't be nearly as much fun without it =].

---

### Post by Naitsirhc Hsem on 2010-10-31
Has anyone fixed the AsusTek, Inc. MultiTouch(YFO) issue?  I have that hardware.  thanks!

---

### Post by mrspacklecrisp on 2010-10-31
Okay, awesome. I uninstalled Mypaint, found that it had left the old messed up gui and brushfiles completely intact— I love how "completely remove" in Synaptic is equated with "please leave useless stuff on my hard drive"— deleted them, deleted the config file in my user directory, and ta da! Bizarre unintuitive issue solved. Lesson learned, reinstallation does not mean fresh start.

I think what happened was that I did something strange and placed the patch twice, which gave me a funny prompt which I did not understand was asking me to reverse parts of it. So, yeah, I'm a clumsy goose.

---

### Post by Naitsirhc Hsem on 2010-10-31
I can get single touch with
```

sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040

```
I would really like multitouch, that's why I bought it.

here is some debug info if it helps:

using:
```

sudo evtest /dev/input/event11
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   2359
      Min        0
      Max     3478
    Event code 1 (Y)
      Value   2612
      Min        0
      Max     3478
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)
Event: time 1288557984.794899, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1288557984.794910, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1288557984.794931, type 3 (Absolute), code 0 (X), value 2273

```
should be using!
```
sudo evtest /dev/input/event5
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 256 (Btn0)
    Event code 257 (Btn1)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     3478
    Event code 1 (Y)
      Value      0
      Min        0
      Max     3478
    Event code 2 (Z)
      Value      0
      Min        0
      Max     3478
    Event code 3 (Rx)
      Value      0
      Min        0
      Max     3478
    Event code 24 (Pressure)
      Value      0
      Min        0
      Max      255
    Event code 40 (Misc)
      Value      0
      Min        0
      Max        2
    Event code 41 (?)
      Value      0
      Min        0
      Max        2
    Event code 42 (?)
      Value      0
      Min        0
      Max        2
  Event type 4 (Misc)
    Event code 4 (ScanCode)

```
output from xinput list --long
```

&#9116;   &#8627; AsusTek, Inc. MultiTouch(YFO)           	id=10	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 10
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 10
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2028.000000
		Class originated from: 10
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2206.000000

&#9116;   &#8627; AsusTek, Inc. MultiTouch(YFO)           	id=16	[slave  pointer  (2)]
	Reporting 9 classes:
		Class originated from: 16
		Buttons supported: 5
		Button labels: Button 0 Button 1 Button Unknown Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 16
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 512.000000
		Class originated from: 16
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 300.000000
		Class originated from: 16
		Detail for Valuator 2:
		  Label: Abs Z
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 16
		Detail for Valuator 3:
		  Label: Abs Rotary X
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 16
		Detail for Valuator 4:
		  Label: Abs Pressure
		  Range: 0.000000 - 255.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 16
		Detail for Valuator 5:
		  Label: None
		  Range: 0.000000 - 2.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 16
		Detail for Valuator 6:
		  Label: None
		  Range: 0.000000 - 2.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 16
		Detail for Valuator 7:
		  Label: None
		  Range: 0.000000 - 2.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000

```

---

### Post by Naitsirhc Hsem on 2010-10-31
I can get it working with single touch:
```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040

```

I added this to the community documentation!

---

### Post by Plippo on 2010-11-01
> **scimor5 said:**
> I looked though some previous posts, and another guy with a similar problem was told to look for a file in the /etc/pm/sleep.d/ directory, I don't have it, all i have is 10_grub-common and 10_unattended-upgrades-hybernate. I'm thinking that is probably the problem? if that is the problem how do i fix it? thx.

Please try installing the **egalax-multitouch-driver-common** package as described in the wiki, this contains the required files for /etc/pm/sleep.d.

---

### Post by scimor5 on 2010-11-01
thx, reinstalling egalax-multitouch-driver-common fixed the problem.

---

### Post by Kevrox on 2010-11-01
> **scimor5 said:**
> thx, reinstalling egalax-multitouch-driver-common fixed the problem.

Plippo does it again!:) Good on you mate, this is an awesome thread... thanks to the main characters....

---

### Post by tlimsisnw on 2010-11-02
For some reason, twofing scrolling works, but zooming doesn't work in Maverick. Does anyone else have the same problem? I'm using the desktop version.

---

### Post by riccardo.depalo on 2010-11-03
> **tlimsisnw said:**
> For some reason, twofing scrolling works, but zooming doesn't work in Maverick. Does anyone else have the same problem? I'm using the desktop version.

I have the same problem, but not on every boot. If I disable compiz effects, with the command metacity --replace, zooming works again. If I go back to compiz effects with compiz --replace, it goes on working. But not always. It's really strange.

---

### Post by tlimsisnw on 2010-11-04
> **riccardo.depalo said:**
> I have the same problem, but not on every boot. If I disable compiz effects, with the command metacity --replace, zooming works again. If I go back to compiz effects with compiz --replace, it goes on working. But not always. It's really strange.

Ok, sounds like some incompatibility with compiz. Maybe Plippo can help enlighten what the problem might be.

---

### Post by Plippo on 2010-11-06
> **tlimsisnw said:**
> Maybe Plippo can help enlighten what the problem might be.

Sorry, but I have never been able to reproduce the problem. When you perform a zoom gesture, in most applications simply the input "Ctrl+Scroll wheel" is emulated. Does zooming work when you hold your Ctrl key and use the wheel of an attached mouse?

---

### Post by riccardo.depalo on 2010-11-06
@Plippo: when twofing hangs on reboot, I can zoom with mouse, with ctrl + mouse wheel, but not with fingers. If I shut down compiz effects, it works again. Thank you for your patience.

---

### Post by tlimsisnw on 2010-11-06
Interestingly, after I reinstalled compiz, twofing zoom seems to work again! Hope it keeps this way.

> **riccardo.depalo said:**
> @Plippo: when twofing hangs on reboot, I can zoom with mouse, with ctrl + mouse wheel, but not with fingers. If I shut down compiz effects, it works again. Thank you for your patience.

---

### Post by DheathNone on 2010-11-06
> **DheathNone said:**
> 
[QUOTE=Plippo;9867845]@DheathNone: Currently I don’t see
such a solution. The problem is that the key is hard-wired
in gnome-power-manager. You could of course disable
gnome-power-manager, but this would affect power-saving
functionality.
This is a bit mystic. It seems to have solved it self after some update because I did not yet do any hackis solution as suggested. It would be nice to know what exactly happened.   
 [/QUOTE]

The rotate button problem came back after upgrading to maveric and I can't apply the same fix just now. So, I think the easiest and least hackish way to do this is to put in 
~/.Xmodmap:
------
keycode 160 = XF86RotateWindows                                    
-------
(and then $ xmodmap ~/.Xmodmap)

This basically marks the key 160 (rotate button in eee T101MT) as a XF86RotateWindows which I think is not used any where with this. Now as the gnome-power-manager seem to search for the key button XF86ScreenSaver pressing it won't lock the screen any more.

Better ideas?

---

### Post by tlimsisnw on 2010-11-06
Hmm. After installing today's updates, twofing zoom stopped again! Very strange indeed.

> **tlimsisnw said:**
> Interestingly, after I reinstalled compiz, twofing zoom seems to work again! Hope it keeps this way.

---

### Post by riccardo.depalo on 2010-11-06
> **tlimsisnw said:**
> Hmm. After installing today's updates, twofing zoom stopped again! Very strange indeed.

Yes, it seems the same problem I noticed on my system. Zooming seems to work or not to work randomly on reboot. Maybe some configuration problem with compiz. I try to see if some plugin is causing problems.

---

### Post by jpfle on 2010-11-08
Hi,

I installed Ubuntu 10.10 on my Eee PC T101MT and activated Compiz with extra effects. I added the required packages from *ppa:plippo/t101mt* and *egalax-multitouch-driver-2.6.35-22-generic-i386.deb* (my kernel is 2.6.35-22-generic i686). Then I run the following commands:

```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
```

because I have a device *AsusTek, Inc. MultiTouch(YFO)*:

```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; AsusTek, Inc. MultiTouch(YFO)           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; AsusTek, Inc. MultiTouch(YFO)           	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=11	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=12	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]

```

The touch screen works well with the default orientation, but it's no longer usable when I rotate the screen (for example with *touchrotate toright*) because the cursor is not where my finger touches the screen.

Is there a way to solve this problem?

Also, I installed the two-finger touch daemon, but it's not working. I installed the required packages and compiled:

```
$ make
gcc -c -Wall -O2 twofingemu.c
gcc -c -Wall -O2 gestures.c
gcc -c -Wall -O2 easing.c
gcc -o twofing twofingemu.o gestures.o easing.o -lm -lpthread -lXtst -lXrandr -lX11
$ sudo make install 
install --mode=755 twofing /usr/bin/
cp 70-touchscreen-egalax.rules /etc/udev/rules.d/
$
```

I rebooted, and run *twofing*, but it's not working (I can't right click, zoom, etc.). There's no such a process if I run only *twofing*:

```
$ twofing
$ killall twofing
twofing: no process found
$
```

Also, I can't debug:

```
$ twofing --debug
twofing: No such file or directory
$
```

Here's info about this file:

```
$ ls -al /usr/bin/twofing 
-rwxr-xr-x 1 root root 34840 2010-11-08 02:29 /usr/bin/twofing
$
```

How could I use *twofing*?

Thanks a lot.

---

### Post by Sharaazad on 2010-11-08
Hi, somebody know how to associate a touchrotate command to the express gate button?

thx


edit: solved by using gnome-keybinding-properties

---

### Post by Plippo on 2010-11-08
@[DheathNone]("http://ubuntuforums.org/member.php?u=1111273"):
If that works (It didn't in Lucid when I tried it some time ago, but if it works in Maverick, that would be great), it looks like a good workaround to me. I'll test it and try to integrate it into one of the packages in the PPA.

@[jpfle]("http://ubuntuforums.org/member.php?u=711875"):
Unfortunately, I don't have an YFO device so I can't test it. If you have to use the quirks, this probably means that there is no working multitouch driver for this device in your kernel. There once was someone who had this device in this thread who said that he had contacted Stéphane Chatty about the device and that Stéphane created a working driver, but I don't know whether that one is already in the kernel. To test the screen, you can try installing the evtest package and use the command 
```
evtest /dev/input/eventX
```
and look if there are MT_ events (you have to try which X you need to use, for me it is 6)

To rotate your screen, you have to use the touchrotate script. As it was built for the egalax screen, you have to call the touchrotate command with a special parameter. For you, it should be either
```
touchrotate LVDS1 10 toleft
```
or
```
touchrotate LVDS1 16 toleft
```
(replace toleft with the direction you want)

---

### Post by jpfle on 2010-11-08
> **Plippo said:**
> To rotate your screen, you have to use the touchrotate script. As it was built for the egalax screen, you have to call the touchrotate command with a special parameter.

Thanks a lot! The command works great for me with the number 11 (I found the numbers list with *xinput list*).

> **Plippo said:**
> Unfortunately, I don't have an YFO device so I can't test it. If you have to use the quirks, this probably means that there is no working multitouch driver for this device in your kernel. There once was someone who had this device in this thread who said that he had contacted Stéphane Chatty about the device and that Stéphane created a working driver, but I don't know whether that one is already in the kernel.

Thanks to pointing this to me. I wrote to Stéphane to have more info about that.

> **Plippo said:**
> To test the screen, you can try installing the evtest package and use the command 
```
evtest /dev/input/eventX
```
and look if there are MT_ events (you have to try which X you need to use, for me it is 6)

Here's the output:

```
$ sudo evtest /dev/input/event5
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x486 product 0x186 version 0x100
Input device name: "AsusTek, Inc. MultiTouch(YFO)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 256 (Btn0)
    Event code 257 (Btn1)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     3478
    Event code 1 (Y)
      Value      0
      Min        0
      Max     3478
    Event code 2 (Z)
      Value      0
      Min        0
      Max     3478
    Event code 3 (Rx)
      Value      0
      Min        0
      Max     3478
    Event code 24 (Pressure)
      Value      0
      Min        0
      Max      255
    Event code 40 (Misc)
      Value      0
      Min        0
      Max        2
    Event code 41 (?)
      Value      0
      Min        0
      Max        2
    Event code 42 (?)
      Value      0
      Min        0
      Max        2
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)
$
```

So I guess there's no multitouch?

Also, I have a question about the Express Gate button. I can't use it because *gnome-keybinding-properties* doesn't recognize it, there's absolutely no output for this button with the command *xev* nor any scancode returned in logs when I press this button:

```
$ tail -f /var/log/messages
Nov  8 17:06:08 mini kernel: [57729.595160] eeepc_wmi: Unknown key e4 pressed
Nov  8 17:06:08 mini kernel: [57729.732441] eeepc_wmi: Unknown key e5 pressed
```

Is there a way to use this button?

Regards.

---

### Post by Plippo on 2010-11-09
> **jpfle said:**
> 
Also, I have a question about the Express Gate button. I can't use it because *gnome-keybinding-properties* doesn't recognize it, there's absolutely no output for this button with the command *xev* nor any scancode returned in logs when I press this button:

```
$ tail -f /var/log/messages
Nov  8 17:06:08 mini kernel: [57729.595160] eeepc_wmi: Unknown key e4 pressed
Nov  8 17:06:08 mini kernel: [57729.732441] eeepc_wmi: Unknown key e5 pressed
```Is there a way to use this button?


Are you sure you have installed the eeepc-acpi-workaround package from the PPA? With this, the eeepc_laptop should be loaded which handles, among others, the Express Gate button. You can check it using modprobe. The eeepc_wmi module that caused your output is quite new and only handles a few keys at the moment.

---

### Post by jpfle on 2010-11-09
> **Plippo said:**
> Are you sure you have installed the eeepc-acpi-workaround package from the PPA? With this, the eeepc_laptop should be loaded which handles, among others, the Express Gate button. You can check it using modprobe. The eeepc_wmi module that caused your output is quite new and only handles a few keys at the moment.

Yes, it's installed (eeepc-acpi-workaround 0.1-ppa2). Here's the list of modules related to *eee*:

```
$ modprobe -l | grep eee
 990   :kernel/drivers/ieee1394/ieee1394.ko
 991   :kernel/drivers/ieee1394/pcilynx.ko
 992   :kernel/drivers/ieee1394/ohci1394.ko
 993   :kernel/drivers/ieee1394/video1394.ko
 994   :kernel/drivers/ieee1394/raw1394.ko
 995   :kernel/drivers/ieee1394/sbp2.ko
 996   :kernel/drivers/ieee1394/dv1394.ko
 997   :kernel/drivers/ieee1394/eth1394.ko
2216   :kernel/drivers/platform/x86/eeepc-laptop.ko
2217   :kernel/drivers/platform/x86/eeepc-wmi.ko
2969   :kernel/net/ieee802154/ieee802154.ko
2970   :kernel/net/ieee802154/af_802154.ko
$
```

---

### Post by Naitsirhc Hsem on 2010-11-11
Thanks for posting about the touchrotate, I have the same hardware.  I am also talking with stephane about getting the multitouch working.  aside from a comiler issue, I am close to getting it working.  Hopefully it will be cooked into the kernel once when we get it working all the way.  oh, it's hid-generaltouch.

---

### Post by jpfle on 2010-11-11
> **Naitsirhc Hsem said:**
> I am also talking with stephane about getting the multitouch working.  aside from a comiler issue, I am close to getting it working.  Hopefully it will be cooked into the kernel once when we get it working all the way.  oh, it's hid-generaltouch.

Very interesting. Keep us informed on this thread about the kernel.

Also, do you have the Express Gate button working?

Regards.

---

### Post by Naitsirhc Hsem on 2010-11-11
no, I am at the same point as you.  I hope we get it soon

---

### Post by sedawk on 2010-11-12
Hello!

I installed Ubuntu on my T101MT and so far everything I tested
worked okay.

But:
when I'm drawing with the "stylus" pen and I'm drawing in normal
"pen&paper sketching speed", the computer cannot follow
my pen fast enough. Is there any way to speed this up,
so the drawing on screen doesn't "lag" behind my drawing hand/pen?

---

### Post by mikshepard on 2010-11-12
I have this working perfectly on Ubuntu, but now I am trying to get it working on debian squeeze.  Everything works great but when I rotate the screen, the mouse does not follow.  I'm guessing its a problem with the touchrotate script not rotating the screen input as well, like it does in Ubuntu.  I'm not sure what the difference would be that would be causing this.  I know this forum is mainly for Ubuntu but I would greatly appreciate any help or ideas, thanks!

-Mike

---

### Post by toylas on 2010-11-12
> **mikshepard said:**
> I have this working perfectly on Ubuntu, but now I am trying to get it working on debian squeeze.  Everything works great but when I rotate the screen, the mouse does not follow.  I'm guessing its a problem with the touchrotate script not rotating the screen input as well, like it does in Ubuntu.  I'm not sure what the difference would be that would be causing this.  I know this forum is mainly for Ubuntu but I would greatly appreciate any help or ideas, thanks!

-Mike

I had the same problem but I was using "touchscreen toleft" etc. When I used

"touchrotate LVDS1 10 toleft" it seemed to work fine.


Here's my problem: I have two versions of kernal installed.

32-22 and 32-25 

When I boot it in 32-22, the x display hangs and I can only hard reboot it. When I boot in 32-25, my X display works but touchscreen does not. I was trying a lot of things when trying to get touchscreen working but am not sure where I goofed up. Any help would be greatly appreciated.

Thanks

---

### Post by Plippo on 2010-11-13
@jpfle:
Strange, maybe your model uses different signals for the buttons. Normally, eeepc_laptop should handle this button.

@toylas:
You need to reinstall the driver when you use a new kernel version. You probably have only installed it for 32-22?

---

### Post by toylas on 2010-11-13
Thanks for the reply Plippo! I just checked, I had the kernel version wrong in my last post (sorry about that). I have 32-25 and 35-22 installed. The touch worked fine in 35-22 when I upgraded everything and had the drivers installed.

Also when I try using the multitouch driver .deb files provided on the community documentation page, I get an error saying wrong architecture. 

But now when I boot in 35-22, X freezes actually the input freezes completely. I mean I can't even go to the shell modes by pressing Ctrl+Alt+F2 etc. I tried booting in recovery mode and then failsafeX but even that does not work.

I have attached part of the failsafe X log file. It says segmentation fault just before the start of end process. I do not understand these messages enough to be able to make out the problem. Any help/pointers would be greatly appreciated.

Thanks

---

### Post by mikshepard on 2010-11-14
> **toylas said:**
> I had the same problem but I was using "touchscreen toleft" etc. When I used

"touchrotate LVDS1 10 toleft" it seemed to work fine.


Thanks

I tried that but still got the same result, the touchscreen mouse input doesn't rotate with the screen.  Any other ideas on how to fix this?  (Again this is on Debian squeeze).  Thanks for any ideas!

-Mike

---

### Post by maxim_86ualb2 on 2010-11-14
Great thread. Took a couple of hours to go through it all. Everything works great.

I would like to add that **DheathNone**'s suggestion:
> The rotate button problem came back after upgrading to maveric and I can't apply the same fix just now. So, I think the easiest and least hackish way to do this is to put in
~/.Xmodmap:
------
keycode 160 = XF86RotateWindows
-------
(and then $ xmodmap ~/.Xmodmap)

This basically marks the key 160 (rotate button in eee T101MT) as a XF86RotateWindows which I think is not used any where with this. Now as the gnome-power-manager seem to search for the key button XF86ScreenSaver pressing it won't lock the screen any more.

Better ideas?

Works really great.

I still have to test and look into MyPaint issues.

---

### Post by maxim_86ualb2 on 2010-11-15
I am having an issue with MyPaint where lines form between brush strokes, does anyone have a solution for this issue. I am using the latest version in the repo 0.8.2.


I must have missed the fix in this thread:
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10001029&postcount=538](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10001029&postcount=538)

---

### Post by DheathNone on 2010-11-16
> **maxim_86ualb2 said:**
> Great thread. Took a couple of hours to go through it all. Everything works great.

I would like to add that **DheathNone**'s suggestion:
[QUOTE=DheathNone]keycode 160 = XF86RotateWindows


Works really great.[/QUOTE]

Actually this was not such a good idea in the end. After some upgrade the gnome seems to take that key and actually rotate the screen by its own means. This means the touchscreen does not rotate but the screen does!

**Use instead:**
**keycode 160 = XF86**[insert some clearly useless action(google something)]

I used XF86Eject, because it was useless for me and it was possible to actually change the shortcut for eject from keyboard shortcuts!

---

### Post by toylas on 2010-11-16
Dear all,

I've been trying to get kernel 35-22 working on my machine without any success. I posted the xorg log last time. I looked into it and found that the x server was crashing with a seg fault. The errors 

```

[    52.700] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    52.700] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    52.700] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    52.780] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    52.780] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    52.780] (II) No input driver/identifier specified (ignoring)
[    52.807] 
Backtrace:
[    52.807] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[    52.807] 1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
[    52.807] 2: /lib/libpthread.so.0 (0x7f28f317c000+0xfb40) [0x7f28f318bb40]
[    52.807] 3: /usr/bin/X (xf86findOption+0x20) [0x484730]
[    52.807] 4: /usr/bin/X (xf86findOptionValue+0x9) [0x484759]
[    52.808] 5: /usr/bin/X (0x400000+0x6c6ed) [0x46c6ed]
[    52.808] 6: /usr/bin/X (0x400000+0x6cfb5) [0x46cfb5]
[    52.808] 7: /usr/bin/X (xf86OpenSerial+0x2b) [0x51e53b]
[    52.808] 8: /usr/lib/xorg/modules/input/evtouch_drv.so (0x7f28ed7c2000+0x2e9b) [0x7f28ed7c4e9b]
[    52.808] 9: /usr/bin/X (EnableDevice+0xad) [0x42663d]
[    52.808] 10: /usr/bin/X (0x400000+0x268ee) [0x4268ee]
[    52.808] 11: /usr/bin/X (0x400000+0x21818) [0x421818]
[    52.808] 12: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f28f20e7d8e]
[    52.808] 13: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[    52.808] Segmentation fault at address (nil)
[    52.808] 
Caught signal 11 (Segmentation fault). Server aborting
[    52.809] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    52.809] Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.
[    52.809] 
```

I've tried reinstalling libc, evtouch drivers, liblpthrea etc but I still can't get X to work in kernel 35-22. Any ideas would be greatly appreciated.

Thanks.




P.S. :I also got into another trouble, which might not be relevant to this thread but I guess I'll share it. I was trying to boot Android with a USB stick on my T101 but somehow it gave me trouble. So I restarted the computer by Ctrl+Alt+Del but now I can not see the bios setup and boot menu screens. All I can do is to boot in Win7 by pressing enter and choosing the default boot option. Any ideas what could be wrong?

---

### Post by tlimsisnw on 2010-11-16
I also have some recent problems with updates and installation. The following message has been appearing for a while and I don't know how to get rid of it. Hope someone has a solution to this:

run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic

      You have to configure "localepurge" with the command

          dpkg-reconfigure localepurge

      to make /usr/sbin/localepurge actually start to function.

      Nothing to be done, exiting ...

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tlimsisnw on 2010-11-17
Has anyone tried the Power Manager Brightness Applet? I thought it would be a nice onscreen control to change the brightness in tablet mode. However, the control is running away from my finger each time I try to change the brightness. :(

---

### Post by miegiel on 2010-11-17
> **tlimsisnw said:**
> I also have some recent problems with updates and installation. The following message has been appearing for a while and I don't know how to get rid of it. Hope someone has a solution to this:

run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic

      You have to configure "localepurge" with the command

          dpkg-reconfigure localepurge

      to make /usr/sbin/localepurge actually start to function.

      Nothing to be done, exiting ...

E: Sub-process /usr/bin/dpkg returned an error code (1)

Did you try (as the message says) running
```
sudo dpkg-reconfigure localepurge
```
in a terminal?

---

### Post by tlimsisnw on 2010-11-17
> **miegiel said:**
> Did you try (as the message says) running
```
sudo dpkg-reconfigure localepurge
```in a terminal?

Yes, nothing seems to change.

---

### Post by Plippo on 2010-11-17
Sorry that I've bin a bit mute lately, I graduated and have a full time job now, so unfortunately less time for Ubuntu...

@toylas:
Sorry, I can't tell you a reason for this segfault. But one note about evtouch, this driver is pretty old and didn't work with my T101MT, maybe it's causing problems for you. I've uninstalled it.

@tlimsisnw:
Seems update-grub causes problems on your machine. Can you try running the command
```
sudo updage-grub
``` manually to look if there are some problems with GRUB configuration files.

@mikshepard:
Maybe 10 isn't the right number for you. If you run
```
xinput list
``` and look for the id(s) of the eGalax device(s) on your machine, you can try those, usually the first one is the one to use.

---

### Post by mikshepard on 2010-11-17
Cool! I fixed my problem of the X/Y axis not rotating with the screen.  Turns out, I was missing the "xinput" package.  Works fine now, the only problem is that when rotated, twofing makes it seem like the first finger is always pressed, so I can't move the mouse at all since every press is considered a second-finger multi-touch press.  When I kill twofing, it works fine.  Any ideas? Twofing works fine when the screen is in the normal position.  I really like having twofing working when rotated for pdf zooming.  (Again this is for debian squeeze) Thanks

-Mike

---

### Post by Plippo on 2010-11-17
Good that touchrotate works now. But twofing should actually handle the swapping of the coordinates automatically, but maybe Debian Squeeze uses a different version of xinput, or it might have a problem if you are touching the screen while it is being rotated. What happens if you kill twofing and re-start it after rotating the screen? Does it work then?

---

### Post by mikshepard on 2010-11-17
haha, I had just thought the same thing.  Yes, killing twofing and then restarting when rotated, does fix the problem.  So as a quick fix, I added "killall twofing" and then the command "twofing" to the touchrotate script and now it works fine.  I had to also create a copy of touchrotate called "touchrotaten", where I added "compix --replace &" to the end, so compiz will run normally again when rotated back to normal.  For some reason, compiz runs extra slow when rotated and even when rotated back (metacity as well), this is the main reason why I tried switching from Ubuntu to Debian but the problem still remains.

For the record, the problem was that twofing would work fine on the top half of the screen but no the bottom, if I pressed on the bottom it would assume one finger was pressing on the top and that that my actual finger was the second multitouch in the bottom area of the rotated screen.  If that makes sense.  I'm guessing it wasn't sensing the dimensions of the rotated screen properly and would get confused when I would tap out of it's idea of the screen range?

However the good news is everything seems to be working fine now! (except for the compiz bit).  I just need to figure out how to get debian to recognize the screen rotate button, for some reason xev doesn't see it and the eee-acpi-scripts doesn't do anything, however I am suspecting it is a kernel issue.  If you have any ideas, please let me know, otherwise I'll post back if I figure it out.  Thanks for the help!

-Mike

---

### Post by tlimsisnw on 2010-11-18
Plippo: I ran update-grub and got the following error:

/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.

Any ideas?

[QUOTE=Plippo;10128232]Sorry that I've bin a bit mute lately, I graduated and have a full time job now, so unfortunately less time for Ubuntu...

@tlimsisnw:
Seems update-grub causes problems on your machine. Can you try running the command
```
sudo updage-grub
``` manually to look if there are some problems with GRUB configuration files.

---

### Post by miegiel on 2010-11-18
> **tlimsisnw said:**
> Plippo: I ran update-grub and got the following error:

/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.

Any ideas?

Try
```
sudo grub-install /dev/sda
```
(assuming you want grub to use the MBR of your 1st harddrive)

And next do
```
sudo update-grub
```
again

---

### Post by Naitsirhc Hsem on 2010-11-18
Any word on a 64-bit calibrator tool?

---

### Post by nebenmir on 2010-11-18
I have installed Okular, as Evince has no means to scroll a pdf by clicking and dragging the mouse (so that I can touch the screen and scroll when i move the finger). Okular has that fearture, but it does not resize correclty when the screen is rotated.

I rotate the screen, so that it is in vertical format. Then I try to maximze the okular window. But okular does not recognize the new screen size. The okular window behaves as if the screen were in horzontal format.

Any ideas to overcome that?

thanx nebenmir

---

### Post by mikshepard on 2010-11-19
@nebenmir:  have you tried Foxit reader?  It works with the one touch hand tool, also screen rotates fine with it, it also allows continuous scroll and full-screen mode.
[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

Also, for anyone interested, I've found [this]("https://help.ubuntu.com/community/EeePC/Using") extremely helpful in that now I can do a quick keyboard combo and have my screen scale 1024x768 whenever a window is to big to let me see the buttons or hidden info below the bottom screen line. And then I can just hit the same combo and put it back!

-Mike

---

### Post by miegiel on 2010-11-19
> **mikshepard said:**
> ...

Also, for anyone interested, I've found [this]("https://help.ubuntu.com/community/EeePC/Using") extremely helpful in that now I can do a quick keyboard combo and have my screen scale 1024x768 whenever a window is to big to let me see the buttons or hidden info below the bottom screen line. And then I can just hit the same combo and put it back!

-Mike

Thanks for pointing that out.  I'll probably still "hold Alt+drag" if it's just to get the *Close* button on my screen. But it's still good to have this script in my scriptbox, sometimes programs just insist on using more space.

I just tried
```
xrandr --output LVDS1 --scale 2.0x2.0
```
2048 x 1200 on a netbook :shock:

I adapted the script a little so it switches to 1280x768 and back and (if run in a terminal) puts out the new resolution.
```
#!/bin/sh

if xrandr | head -n1 | grep -q '1024 x 600'; then
  xrandr --output LVDS1 --scale 1.25x1.28
else
  xrandr --output LVDS1 --scale 1.0x1.0
fi

xrandr | head -n1

exit
```

---

### Post by tlimsisnw on 2010-11-19
Hmm, I tried this, but still got the same error message:

/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.

> **miegiel said:**
> Try
```
sudo grub-install /dev/sda
```(assuming you want grub to use the MBR of your 1st harddrive)

And next do
```
sudo update-grub
```again

---

### Post by mikshepard on 2010-11-19
I've been searching through the forums to try to understand how to get the rotate button working, when I type acpi_listen I get 

```
PNP0C14:00 000000d2 00000000
PNP0C14:00 000000d2 00000000

```

I tried using [this]("https://help.ubuntu.com/community/LaptopSpecialKeys")  but it's not displaying the right code and I have no clue what that means.  Ubuntu shows the correct one but not squeeze.  I've searched google and only found three posts related to this for some other tablet pc.  Any ideas?  I've been pulling my hair out on this all day..

Thanks
-Mike

---

### Post by miegiel on 2010-11-20
> **tlimsisnw said:**
> Hmm, I tried this, but still got the same error message:

/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.

I searched wikipedia to figure out what exactly *parenthesis* means. It's got to do with bracketing ](*,) As, for example, *(hd0) /dev/sda* missing the opening bracket when *grub-probe* calls */boot/grub/device.map*.

Now, I don't have a file called *device.map* in */boot/grub/*. But it seems it's created by *grub-mkdevicemap* when installing/configuring grub2 (and deleted when done?).

Give this a shot:
```
grub-mkdevicemap --help
```


And if you're brave enough:
```
sudo grub-mkdevicemap
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by miegiel on 2010-11-20
Sorry for the double posts. The forum is acting up a bit :S

---

### Post by miegiel on 2010-11-20
double post

---

### Post by miegiel on 2010-11-20
double post

---

### Post by nebenmir on 2010-11-21
@[mikshepard]("http://ubuntuforums.org/member.php?u=1177625") thanx for the hint with foxit. I have already tried that. currently i use adobe-reader (which also does the mouse scrolling). But I would like to use something more open like okular or evince.

---

### Post by toylas on 2010-11-22
Dear all,

I reinstalled Ubuntu 10.10 on my machine and almost everything seems to work fine. Here are a few problems that I have:

1)[COLOR="Red"]Express Gate button:[/COLOR] I'm unable to get the express gate button working. When I run xev, it does not give me any output for the expressgate button.

2)[COLOR="red"]Twofing:[/COLOR] When I run twofing, I can't perform any gestures. The touchscreen still behaves as if it is single touch. Worse still, tap on the screen loses the left click effect. When I kill twofing, the tap to click effect works fine.

Any ideas for these would be greatly appreciated.

Thanks

---

### Post by Naitsirhc Hsem on 2010-11-22
do you have AsusTek, Inc. MultiTouch(YFO) device in lsusb?

---

### Post by toylas on 2010-11-24
> **Naitsirhc Hsem said:**
> do you have AsusTek, Inc. MultiTouch(YFO) device in lsusb?

No I do not

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What is it required for? Twofing or expressgate button?

Thanks

---

### Post by Naitsirhc Hsem on 2010-11-24
from what I have heard, it means that it is a "T101MT" by ASUS where asus changed the hardware.  It has alot more difficulties with running ubuntu.  you have a "normal" model.
baseline,
it does not apply to your specific hardware

---

### Post by Plippo on 2010-11-25
@toylas:
About the express gate button: Have you installed the eeepc-acpi-workaround package? Do other hotkeys (e.g. Fn+F2) work?

About twofing: What happens when you run ```
twofing --debug
``` ?

---

### Post by hybridmonkey on 2010-11-25
I'm so frustrated! I don't understand how I'm the only person the come across this problem. Going through this expansive thread I still couldn't find someone else who has the problem. 

When I try to create the files required to use the synaptics twofinger function, my t101mt does not have the directory. Also, I cannot seem to manually create these folders either... I just installed 10.10 and I'm wondering if I somehow have different directories... someone please help. =]

---

### Post by miegiel on 2010-11-25
> **hybridmonkey said:**
> I'm so frustrated! I don't understand how I'm the only person the come across this problem. Going through this expansive thread I still couldn't find someone else who has the problem. 

When I try to create the files required to use the synaptics twofinger function, my t101mt does not have the directory. Also, I cannot seem to manually create these folders either... I just installed 10.10 and I'm wondering if I somehow have different directories... someone please help. =]

I don't know what exactly your problem is, or what you're trying to do. But I run this script to enable 2 finger stuff for my touchpad (does nasty stuff like disable the 2 finger menu click and turns the left pad button into a middle button).

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
#
# Some useful commands :
#	xinput list
#	xinput list-props "SynPS/2 Synaptics TouchPad"
#	xinput test "SynPS/2 Synaptics TouchPad"
#	xinput test-xi2 "SynPS/2 Synaptics TouchPad"
#
sleep 3
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 60
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
#xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 2 0 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9                                       # swap left and middle click, gives you middle click on the left button and left click on tap. - values: lb, mb, rb, b4, b5, etc.
exit
```
save as *touchpad.sh*, run in a terminal as ```
sh touchpad.sh
```
To auto start it as you logon go to *"Session and Startup"* and ad it to the list.

---

### Post by Plippo on 2010-11-26
@hybridmonkey:
Sorry, I don't completely understand your problem. You don't have to create any files in order to get two-finger scrolling working on the touchpad. Just install the package eeepc-touchpad-twofingers from the PPA, as described in [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT) and it should work.

---

### Post by VollieV on 2010-11-27
First of all, thankyou to everyone who has made Ubuntu on my T101MT possible! I'm a linux noob and I couldn't have done it without you :D


That said, I now need some help.  My machine was working all fine and I was loving it until today, the update manager pops up and, by habit, I say "update all"! this all went fine until just now when I tried to use the touch screen and the cursor shot up to the top left corner of the screen.  'Not to worry' I thought 'I'll just have to re calibrate the screen', but when I looked int he system section of the home screen, calibrate was nowhere to be found!

What have I done? how can I fix it?:confused:

And again, thankyou for all the hard work!

---

### Post by miegiel on 2010-11-27
> **VollieV said:**
> First of all, thankyou to everyone who has made Ubuntu on my T101MT possible! I'm a linux noob and I couldn't have done it without you :D


That said, I now need some help.  My machine was working all fine and I was loving it until today, the update manager pops up and, by habit, I say "update all"! this all went fine until just now when I tried to use the touch screen and the cursor shot up to the top left corner of the screen.  'Not to worry' I thought 'I'll just have to re calibrate the screen', but when I looked int he system section of the home screen, calibrate was nowhere to be found!

What have I done? how can I fix it?:confused:

And again, thankyou for all the hard work!

If you updated your kernel, you need to install the [driver]("https://help.ubuntu.com/community/T101MT#Touchscreen%20%28same%20for%2010.04%20and%2010.10%29") for the new kernel too.

```
uname -a
``` in a terminal will show you what version kernel you're running.

---

### Post by VollieV on 2010-11-27
It says I'm running 2.6.32-26 but that's not on the driver list yet.

Guess I'll have to wait for an update?

Thanks,
Ollie

---

### Post by coffen on 2010-11-28
> **VollieV said:**
> It says I'm running 2.6.32-26 but that's not on the driver list yet.

Guess I'll have to wait for an update?

Thanks,
Ollie
Or you could compile the [driver]("https://help.ubuntu.com/community/T101MT#Touchscreen%20%28same%20for%2010.04%20and%2010.10%29") for the new kernel yourself. Just follow the steps [here]("https://help.ubuntu.com/community/T101MT#How%20to%20build%20a%20kernel%20driver%20by%20yourself").
But only do that if you know how to compile yourself.

---

### Post by Plippo on 2010-11-28
Sorry, I can't compile drivers for Ubuntu 10.04 any more. You either have to wait for someone else to compile and upload it to the wiki or do it yourself, as coffen suggested. It's not very complicated, most of it is done automatically.

---

### Post by VollieV on 2010-11-28
> **Plippo said:**
> Sorry, I can't compile drivers for Ubuntu 10.04 any more. You either have to wait for someone else to compile and upload it to the wiki or do it yourself, as coffen suggested. It's not very complicated, most of it is done automatically.


I'll give it a go.  I'm new to linux but I'm quite computer literate so hopefully all will go to plan

I'll report back once I've given it a go

---

### Post by knicefire on 2010-11-28
Hi everyone!
First of all forgive me for my English. 

I want to share with you one idea. 
Have an idea to use a single button which is on the screen to access the main settings and shortcuts in tablet mode.

This should be a transparent window pops up on the screen with labels like the IPhone (for example), preferably with the ability to edit settings (brightness, volume, etc). You can make the tabs at the top or the side that used to group labels. 

May already have something similar. 

P.S. I am weak in programming, trying to deal with PyGTK, but so far that does not work.

---

### Post by miegiel on 2010-11-28
> **knicefire said:**
> Hi everyone!
First of all forgive me for my English. 

I want to share with you one idea. 
Have an idea to use a single button which is on the screen to access the main settings and shortcuts in tablet mode.

This should be a transparent window pops up on the screen with labels like the IPhone (for example), preferably with the ability to edit settings (brightness, volume, etc). You can make the tabs at the top or the side that used to group labels. 

May already have something similar. 

P.S. I am weak in programming, trying to deal with PyGTK, but so far that does not work.

I've only seen pictures of iphones, so I'm not really sure what you mean. But what you're describing, exept for the transperant popup window, sounds a lot like the new *unity* desktop for *natty narwal*.

Search "unity" in the "[Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")" forum.

---

### Post by knicefire on 2010-11-28
**miegiel**, hank you for reply.
I also no have the IPhone. :)
My idea just not only launcher. This maybe more like widget layer from KDE. But more lightweight and more adapted for tablet mode PC like our.
Quick volume control, player control, lightweight, handwritten little notes, app switcher (very useful if you have no panels or it's hidden).

Unity - cool but not what I mean.

---

### Post by riccardo.depalo on 2010-11-29
> **Plippo said:**
> Sorry, I can't compile drivers for Ubuntu 10.04 any more. You either have to wait for someone else to compile and upload it to the wiki or do it yourself, as coffen suggested. It's not very complicated, most of it is done automatically.

I also am running Maverick, but if you follow the wiki instructions it's quite easy to compile the kernel driver.

---

### Post by VollieV on 2010-11-29
I did it and it works again!  The calibrate option is still missing from the settings tab but the touch screen is working again so at the moment that's enough :) I could upload the driver if people want but I'd need instruction (never edited a wiki before) and I'm not sure if someone should make one with the system option in it too

---

### Post by riccardo.depalo on 2010-11-29
> **VollieV said:**
> I did it and it works again!  The calibrate option is still missing from the settings tab but the touch screen is working again so at the moment that's enough :) I could upload the driver if people want but I'd need instruction (never edited a wiki before) and I'm not sure if someone should make one with the system option in it too

well you can also upload the driver here so someone else, like me, can put it in the wiki.

---

### Post by linxgr on 2010-11-29
This may be a bit off-topic (regarding that it's not exactly support related) but what the heck. I wanted to ask if you have found any on-screen keyboard that is usable in tablet mode. I'd love some screenshots or better a video just to prove yours is the best and let me use this little machine as it was supposed to.

@VollieV I think with the new drivers the Calibrate program ain't useful anymore and the screen should be working as intended.

[offtopic]I would like also to know what programs do you use for that general tablet experience on the machine and if you know of a program that can add scribbles over pdfs (like another layer on top of the pdf with marks etc jotted down) and suggest a calendar/to-do/notes application.[/offtopic]

---

### Post by miegiel on 2010-11-29
> **linxgr said:**
> This may be a bit off-topic (regarding that it's not exactly support related) but what the heck. I wanted to ask if you have found any on-screen keyboard that is usable in tablet mode. I'd love some screenshots or better a video just to prove yours is the best and let me use this little machine as it was supposed to.
[offtopic]I would like also to know what programs do you use for that general tablet experience on the machine and if you know of a program that can add scribbles over pdfs (like another layer on top of the pdf with marks etc jotted down) and suggest a calendar/to-do/notes application.[/offtopic]

I use onBoard (sorry to lazy for screenshots :P) it's in the software center.

---

### Post by Slartius on 2010-11-30
I have same problem here with a T101MT. 
acpi_listen command displays:
hotkey ATKD 0000007b 00000001
hotkey ATKD 0000007d 00000001
etc..

Although I changed the button in the /etc/acpi/events/asus-rotate from 0000009b to 0000007b, the rotate screen button does not work. Did any of you had any luck with enabling this button in 10.10. Everything else works great so far.

Thanks

---

### Post by miegiel on 2010-11-30
> **Slartius said:**
> I have same problem here with a T101MT. 
acpi_listen command displays:
hotkey ATKD 0000007b 00000001
hotkey ATKD 0000007d 00000001
etc..

Although I changed the button in the /etc/acpi/events/asus-rotate from 0000009b to 0000007b, the rotate screen button does not work. Did any of you had any luck with enabling this button in 10.10. Everything else works great so far.

Thanks

Not that I have read. But 3 buttons in my panel works better for me (on screen keyboard, rotate left and right). In tablet mode I'm always pressing that button by accident.

---

### Post by Slartius on 2010-12-01
> **miegiel said:**
> Not that I have read. But 3 buttons in my panel works better for me (on screen keyboard, rotate left and right). In tablet mode I'm always pressing that button by accident.

I agree with you in that respect, but as a gadget fan and a Linux geek (been using it for approximately 15 years) it always depresses me when something that was working suddenly stops working. That can give Linux bad reputation. As for me, when the novelty of my new gadget wears off, I will probably forget about it ;).

Best regards

---

### Post by Kevrox on 2010-12-02
Hi all
just did update for 10.04 to 2.6.32-26-generic and all touch functions gone, will there be an update for this here [https://help.ubuntu.com/community/T101MT#Touchscreen](https://help.ubuntu.com/community/T101MT#Touchscreen) (same for 10.04 and 10.10) like in the early days. cheers
kev

---

### Post by miegiel on 2010-12-02
> **Kevrox said:**
> Hi all
just did update for 10.04 to 2.6.32-26-generic and all touch functions gone, will there be an update for this here [https://help.ubuntu.com/community/T101MT#Touchscreen](https://help.ubuntu.com/community/T101MT#Touchscreen) (same for 10.04 and 10.10) like in the early days. cheers
kev

As **Plippo** said 2 pages back

> **Plippo said:**
> Sorry, I can't compile drivers for Ubuntu 10.04 any more. You either have to wait for someone else to compile and upload it to the wiki or do it yourself, as coffen suggested. It's not very complicated, most of it is done automatically.

And upload the driver to [https://help.ubuntu.com/community/T101MT#Touchscreen](https://help.ubuntu.com/community/T101MT#Touchscreen) or post is here so others can put it in the page.

---

### Post by coffen on 2010-12-02
> **Plippo said:**
> Sorry, I can't compile drivers for Ubuntu 10.04 any more. You either have to wait for someone else to compile and upload it to the wiki or do it yourself, as coffen suggested. It's not very complicated, most of it is done automatically.

Any chance of getting the kernel driver for Maverick added to the plippo/t101mt ppa?
Would make updating a lot easier.

---

### Post by Naitsirhc Hsem on 2010-12-02
I found an amazing tool to work with the touch screen, it is absolutely brilliant. gesture recognition that actually works and can be device specific

easystroke

---

### Post by knicefire on 2010-12-03
Hello everyone!
I use twofing daemon and it would be nice to see long touch to right click in options. 

It's posible?

---

### Post by Cyberblade on 2010-12-03
I've been keeping up with this thread off and on since I posted about the new hardware, I've been doing quite well even with just single touch.  However, I've been trying to start to use it more for artwork as of late, and I'm finding the lack of pressure sensitivity rather painful.

I noticed reading through the evtest I ran ages ago there is an Event Code 24 labeled as Pressure, I was wondering if there might be any way to hack together a way to get pressure sensitivity even without multitouch?

If not, oh well, it was worth a shot to ask.

---

### Post by hybridmonkey on 2010-12-03
> **miegiel said:**
> I don't know what exactly your problem is, or what you're trying to do. But I run this script to enable 2 finger stuff for my touchpad (does nasty stuff like disable the 2 finger menu click and turns the left pad button into a middle button).

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
#
# Some useful commands :
#    xinput list
#    xinput list-props "SynPS/2 Synaptics TouchPad"
#    xinput test "SynPS/2 Synaptics TouchPad"
#    xinput test-xi2 "SynPS/2 Synaptics TouchPad"
#
sleep 3
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 60
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
#xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 2 0 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9                                       # swap left and middle click, gives you middle click on the left button and left click on tap. - values: lb, mb, rb, b4, b5, etc.
exit
```save as *touchpad.sh*, run in a terminal as ```
sh touchpad.sh
```To auto start it as you logon go to *"Session and Startup"* and ad it to the list.

OMG! Thank you! You're amazing! Very nasty script, haha. Just curious though, why do you prefer horizontal scrolling off? I personally feel it more responsive with it on so I enabled it. Does it cause any issues?

@Plippo - I did follow the instructions on that page. After installing all the things, it left my touchpad as wacky as when I first ran ubuntu on it. After a couple of reboots, two fingers on the touchpad no longer caused it to shake erratically but it did not enable two finger scrolling either. Thankfully I was able to use the script above!

I noticed that after waking up my t101mt that the touch screen no longer responded unless I rebooted. Is this a known issue or did something I do cause some sort of conflicts?

BTW Thank you for all your help and hard work!

---

### Post by howtieatie on 2010-12-03
well it new for me

---

### Post by miegiel on 2010-12-03
> **knicefire said:**
> Hello everyone!
I use twofing daemon and it would be nice to see long touch to right click in options. 

It's posible?

Go to system (or preferences) > mouse > accessibility tab > tag "trigger secondary click by holding down the primary button"

disclaimer : That's in the alpha of ubuntu 11.04, but I'm pretty sure the earlier versions have the option too (to bad I can't find it in xubuntu :()

---

### Post by knicefire on 2010-12-03
> **miegiel said:**
> Go to system (or preferences) > mouse > accessibility tab > tag "trigger secondary click by holding down the primary button"

disclaimer : That's in the alpha of ubuntu 11.04, but I'm pretty sure the earlier versions have the option too (to bad I can't find it in xubuntu :()

Ou! Thank you! This is actually I looking for.

---

### Post by miegiel on 2010-12-03
> **hybridmonkey said:**
> OMG! Thank you! You're amazing! Very nasty script, haha. Just curious though, why do you prefer horizontal scrolling off? I personally feel it more responsive with it on so I enabled it. Does it cause any issues?

...

No issues other than that I always scroll sideways a bit when I'm trying to scroll down in a straight line.

> **knicefire said:**
> Ou! Thank you! This is actually I looking for.
you're welcome :D

---

### Post by hybridmonkey on 2010-12-03
I try to follow the steps to install the twofing daemon but it doesn't seem to work when I come across the following steps:

> 
[LIST]
[*]Compile the daemon by calling make
[*]Install the daemon by calling sudo make install
[/LIST]


It all seems to work fine but at the Make command it says:

make: *** No targets specified and no makefile found.  Stop.


Any suggestions??

---

### Post by Slartius on 2010-12-03
> **hybridmonkey said:**
> I try to follow the steps to install the twofing daemon but it doesn't seem to work when I come across the following steps:



It all seems to work fine but at the Make command it says:

make: *** No targets specified and no makefile found.  Stop.


Any suggestions??

It looks like you are not in the directory, where you unpacked twofinger daemon. You have to cd into the twofing-0.0.6b directory and then issue a make command.

---

### Post by Naitsirhc Hsem on 2010-12-03
> **Cyberblade said:**
> I've been keeping up with this thread off and on since I posted about the new hardware, I've been doing quite well even with just single touch.  However, I've been trying to start to use it more for artwork as of late, and I'm finding the lack of pressure sensitivity rather painful.

I noticed reading through the evtest I ran ages ago there is an Event Code 24 labeled as Pressure, I was wondering if there might be any way to hack together a way to get pressure sensitivity even without multitouch?

If not, oh well, it was worth a shot to ask.


I have the new hardware too, did you talk to Stephanie, she is working on a driver that might work. I compiled and installed it with no success, but I am hopeful.  At this time I don't know how but I would talk to Stéphane Chatty <chatty@enac.fr>.

---

### Post by sergey1369 on 2010-12-03
Hello. Here is quick and dirty way to disable screen lock on pressing rotate button (express gate button) in Ubuntu 10.10. Replace eeepc-laptop.ko's KEY_COFFEE(0x98 ) button with KEY_DIRECTION(0x99).

static const struct key_entry eeepc_keymap[] = {
...
    { KE_KEY, 0x1a, { KEY_COFFEE } } -> { KE_KEY, 0x1a, { KEY_DIRECTION } } , 
...
}

It's too complex to recompile driver, but it's fairly simple to make a binary fix. 
Here we go.

# cd /lib/modules/2.6.35-23-generic/kernel/drivers/platform/x86
# cp eeepc-laptop.ko eeepc-laptop.ko.orig
# sed -e 's!\x1a\x0\x0\x0\x98!\x1a\x0\x0\x0\x99!' eeepc-laptop.ko.orig > eeepc-laptop.ok
# rmmod eeepc-laptop
# modprobe eeepc-laptop

GOOD: Now button can be binded via standard keyboard shortcuts to any program.
BAD: every kernel update requires repeating procedure.

---

### Post by miegiel on 2010-12-03
I noticed there's an updated BIOS (version 0601) on the ASUS site. There's no info on what's updated though. :-s All it says is "updated firmware"

---

### Post by hybridmonkey on 2010-12-04
> **Slartius said:**
> It looks like you are not in the directory, where you unpacked twofinger daemon. You have to cd into the twofing-0.0.6b directory and then issue a make command.

No this is not the case because the first step works. I'm referring to the procedure found in the ubuntu help page about the t101mt found on Plippo's first post. I'm sure I'm not the first person to come across this problem.

---

### Post by Plippo on 2010-12-04
@coffen:
Sorry, to be added to the PPA, the package would have to be built by the launchpad server which is not possible with the current build script. Henrik Rydberg has created a DKMS package with his new version of the driver, but it needs some changes in the egalax-multitouch-driver-common package. I'll look when I have the time to add and test them.

But a good news for the future: My patches have been accepted into the Linux kernel version 2.6.36, so in Ubuntu 11.04, they will be available without manual work.

@Cyberblade:
Are there correct events with code 24 emitted when you run evtest and touch the screen with your stylus? Then pressure should actually automatically be available in applications that support it. If not, it is not correctly mapped in the driver.

@hybridmonkey (about touchpad scrolling):
The script does more or less the same as the package. The reason it didn't work before is probably the following: When you have used Windows, then reboot into Ubuntu, the touchpad doesn't work correctly. You have to shut down the Eee PC from Windows and then turn it on again to boot ubuntu instead of simply rebooting.

@hybridmonkey (about twofing):
Sorry, but the message you posted clearly states that when calling Make, you're not in the directory that contains the makefile, as Slartius said. You have to use the cd command to switch to that directory, as it is said on the wiki page:
> 

[LIST]
[*]Open a terminal and navigate to the extracted folder (e.g. **cd ~/twofing-0.0.6b** if you extracted it to your home dir)
[/LIST]
This has nothing to do with the fact that the previous steps work in any case.

@hybridmonkey (about the wakeup):
This should actually be fixed by the egalax-multitouch-driver-common package.

@miegiel:
If you don't have problems with your Eee PC, I would recommend not installing the update. It happened to me before on a different machine that a BIOS update decreased Linux compatibility.

---

### Post by kl67 on 2010-12-04
Here is patch for Mypaint 0.9 and also a short Python script to patch brushes. The patch is made against stock Mypaint 0.9 source downloaded from mypaint.org. The patch is basically slightly modified version of Plippo's patch for version 0.8.2 (quick hack to acommodate for changes made to tileddrawwidget.py).

The Python scripts scans given folder and its subfolders for mypaint brush definitions (files ending with .myb) and patches them. Use this script to patch additional brushes which can be downlaoded from mypaint.org.

Usage:
```

python brushes.py top_folder

```top_folder is path to a folder containg brushes.

---

### Post by Naitsirhc Hsem on 2010-12-05
> **miegiel said:**
> I noticed there's an updated BIOS (version 0601) on the ASUS site. There's no info on what's updated though. :-s All it says is "updated firmware"

DO NOT UPDATE!!!!

I bought mine with the 0601 bios and firmware and it has hardware issues, single touch only with ubuntu.  I think the bios and firmware update changes what the device names are.

please post bios revisions and multitouch status to confirm or disprove this theory, this could help those of us with major hardware issues go back to a hardware config that works

---

### Post by coffen on 2010-12-05
> **Naitsirhc Hsem said:**
> DO NOT UPDATE!!!!

I bought mine with the 0601 bios and firmware and it has hardware issues, single touch only with ubuntu.  I think the bios and firmware update changes what the device names are.

please post bios revisions and multitouch status to confirm or disprove this theory, this could help those of us with major hardware issues go back to a hardware config that works

I have revision 0601 bios and twofing is working in Maverick with kernel 2.6.35-23.
I did not get pressure sensitivity to work in gimp, but that could be due to other issues.

---

### Post by Naitsirhc Hsem on 2010-12-05
> **coffen said:**
> I have revision 0601 bios and twofing is working in Maverick with kernel 2.6.35-23.
I did not get pressure sensitivity to work in gimp, but that could be due to other issues.

do you have a  AsusTek, Inc. MultiTouch(YFO) device in xinput list?
if so my theory is correct, if not, I am completely wrong.

---

### Post by miegiel on 2010-12-05
> **Naitsirhc Hsem said:**
> DO NOT UPDATE!!!!

I bought mine with the 0601 bios and firmware and it has hardware issues, single touch only with ubuntu.  I think the bios and firmware update changes what the device names are.

please post bios revisions and multitouch status to confirm or disprove this theory, this could help those of us with major hardware issues go back to a hardware config that works

To late I already installed it :D

I have been having random crashes every 24 hours or so since I updated to kernel 2.6.35-23, so I updated to the 0601 bios the day I posted about it. It didn't solve the problem, I've had 1 random crash since. But it didn't cause any problems for me either.

At first I thought it was sound related, because the first couple  crashes occurred when I was listening to music or watching a video. But later they also happened when I wasn't. I tried using the 2.6.35-22 kernel again and tried the 2.6.36-"something" kernel to no avail. I tried the ubuntu 11.04 alpha and had a crash there too (didn't use it much, though the idea is nice, *unity* is to sluggish for a netbook in my opinion and I love xubuntu to much). I also tried purging the touchscreen stuff, but that didn't prevent crashes so I put it back. The iron browser (chromium's less privacy violating twin) is still on my suspects list, but I'm pretty sure I've had crashes when it wasn't running. Skype is on the suspects list too, it could be that incoming messages or calls are causing crashes. But my short contact list is always offline (or seems to be, I need to relax my firewall a bit).

I didn't post about it yet because there's nothing sensible I can say about the crashes. All I can say for certain is that they seem to happen a little less often the last couple of days.

---

### Post by miegiel on 2010-12-05
> **Naitsirhc Hsem said:**
> do you have a  AsusTek, Inc. MultiTouch(YFO) device in xinput list?
if so my theory is correct, if not, I am completely wrong.

No, I have the eGalax Inc. USB TouchController. Which mutlitouch are you having problems with, the touchscreen or the touchpad?

---

### Post by coffen on 2010-12-05
> **Naitsirhc Hsem said:**
> do you have a  AsusTek, Inc. MultiTouch(YFO) device in xinput list?
if so my theory is correct, if not, I am completely wrong.
```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=11	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=12	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]

```

---

### Post by Naitsirhc Hsem on 2010-12-05
touchscreen, sorry, I was completely wrong

---

### Post by miegiel on 2010-12-05
> **Naitsirhc Hsem said:**
> touchscreen, sorry, I was completely wrong

If you're still having problems with the touchscreen, try purging the egalax driver and reinstalling it.

```
sudo apt-get purge egalax-multitouch- (complete the line by hitting *Tab* a couple of times)
``` (in a terminal ofc.)

---

### Post by The Wish Within on 2010-12-06
If I install Ubuntu 10.04 as second OS, will the ASUS Express Gate still work as it worked before? (By pressing the small button beside the on/off button)
And is Ubuntu faster than Windows 7 on the T101MT?

---

### Post by miegiel on 2010-12-06
> **The Wish Within said:**
> If I install Ubuntu 10.04 as second OS, will the ASUS Express Gate still work as it worked before? (By pressing the small button beside the on/off button)
And is Ubuntu faster than Windows 7 on the T101MT?

Yes, but only when you turn the machine on with ASUS Express Gate. Btw, ASUS Express Gate is a customized linux. ;) People are working on making the button the screen rotate button (see earlier in the thread).

Probably/Don't know. I never installed 10.04 on this machine. Xubuntu 10.10 is faster.

---

### Post by The Wish Within on 2010-12-06
So if I download Ubuntu 10.10 Netbook Edition and install it in dual boot mode, I can choose between Windows 7 and Ubuntu when starting it with the normal on/off button and I can start ASUS Express Gate when I press the small button next to the bigger long on/off button as I can without Ubuntu installed?

---

### Post by miegiel on 2010-12-06
> **The Wish Within said:**
> So if I download Ubuntu 10.10 Netbook Edition and install it in dual boot mode, I can choose between Windows 7 and Ubuntu when starting it with the normal on/off button and I can start ASUS Express Gate when I press the small button next to the bigger long on/off button as I can without Ubuntu installed?

Yes

When you boot from the ubuntu installation USB (or CD) select the option to "try ubuntu". This will boot ubuntu from the USB. That way you can take a test drive before installing it.

You can find info on how to get everything (touchscreen, upside down webcam) to work here: [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

---

### Post by coffen on 2010-12-06
> **The Wish Within said:**
> So if I download Ubuntu 10.10 Netbook Edition and install it in dual boot mode, I can choose between Windows 7 and Ubuntu when starting it with the normal on/off button and I can start ASUS Express Gate when I press the small button next to the bigger long on/off button as I can without Ubuntu installed?

Yes you can.

You need to set up Windows first to get the partitions correct on the disk.
The disk has no free space after you have set up Windows.

You will find several partitions on the disk. Two of them are big ntfs partitions.
The first one has Windows 7 on it. The second is the Windows D-drive, which can be formatted and repartitioned for ubuntu.

Boot using the Ubuntu usb stick and try ubuntu first. This way you can mount the partitions to verify which one is the empty D-drive.

---

### Post by The Wish Within on 2010-12-06
I've just downloaded Ubuntu Netbook 10.10.
Now I wanted to install it, but there is something which I totally don't like:
When I have to allocate drive space, there are only 2 options:
- Erase and use the entire disk 
- Specify partitions manually (advanced)

What should I do now exactly?
I don't want to deleted Windows 7 or anything already existing...
When I installed Ubuntu Desktop 10.04 on my big Laptop there was as far as I know another option for dual booting...

Thanks

//Edit: 
On my older Laptop (an Acer), Ubuntu 10.04 just took a part of the Windows Vista partition and everything works without any problems.
I'd like to install Ubuntu on the T101MT like this...

---

### Post by coffen on 2010-12-06
> **The Wish Within said:**
> I've just downloaded Ubuntu Netbook 10.10.
Now I wanted to install it, but there is something which I totally don't like:
When I have to allocate drive space, there are only 2 options:
- Erase and use the entire disk 
- Specify partitions manually (advanced)

What should I do now exactly?

Choose Specify partitions manually.
Then delete the second Windows partition (the d-drive).
Make sure you know which one it is. See my previous post.

Create a 4 new Extended partitions in its place:
```
/boot  (10240 mb)
/swap  (2048 mb)
/home  (102400 mb)
/      (the rest of the available space, about 50 gig if I remember correctly)
```
Continue install normally.

---

### Post by The Wish Within on 2010-12-06
K, thanks, the stupid thing is, I have some programs installed on my D drive :S
Seems like I have to move them...

---

### Post by ianni67 on 2010-12-07
The solution by plippo worked perfectly for me since I bought my 101MT.

(Ubuntu 10.10 freshly installed). My touchscreen is egalax.

Today when I rotated the screen I found that it is not working any more: suddenly when I launch touchrotate toright the screen rotates but the pointer seems to move randomly (not exactly as it would move without rotation).

Yesterday I accepted an update; the only other change I made to the system is that I installed Google earth, which I think should not affect the touch screen drivers... 

Anyone is experiencing similar problems? Please, help! I use my 101MT mainly to read, so I always use it with the screen rotated vertically and currently this does not work.

thank you again for your great work

ianni

---

### Post by ianni67 on 2010-12-07
sorry! MY FAULT. I just realized that, for some reason, I installed touchscreen-helper, a package which conflicts with plippo's package.

Sorry for my mistake. Now I removed it and everything works again :-D

---

### Post by The Wish Within on 2010-12-07
> **coffen said:**
> Choose Specify partitions manually.
Then delete the second Windows partition (the d-drive).
Make sure you know which one it is. See my previous post.

Create a 4 new Extended partitions in its place:
```
/boot  (10240 mb)
/swap  (2048 mb)
/home  (102400 mb)
/      (the rest of the available space, about 50 gig if I remember correctly)
```Continue install normally.

Ehm, the D partition should be /dev/sda2, right?
After I've selected D and hit the button "Delete", what exactly should I do then?
I've looked into the "Add..." menu (Create partition) but I'm not sure what I should do now...
Could you give me a detailed description for this step, please?

If I choose "Ext4 journaling file system", I can find /home, /boot and / but there is no /swap?
Should I choose "swap area" for /swap instead of "Ext4 journaling file system"? And should I as types the default "Logical" or "Primary"?

Thanks

---

### Post by Plippo on 2010-12-07
> **ianni67 said:**
> sorry! MY FAULT. I just realized that, for some reason, I installed touchscreen-helper, a package which conflicts with plippo's package.

Sorry for my mistake. Now I removed it and everything works again :-D
touchscreen-helper is an experimental package for a new software which is intended to automatically rotate the touchscreen when the screen is rotated, but it doesn't work correctly with the current version of twofing. I recommend not installing it at the moment.

---

### Post by riccardo.depalo on 2010-12-07
Hi everybody. As there was a 2.6.35-24 kernel upgrade, I builded, tested and uploaded a new kernel driver. You can find it in the usual site: 

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

---

### Post by miegiel on 2010-12-07
> **The Wish Within said:**
> Ehm, the D partition should be /dev/sda2, right?
After I've selected D and hit the button "Delete", what exactly should I do then?
I've looked into the "Add..." menu (Create partition) but I'm not sure what I should do now...
Could you give me a detailed description for this step, please?

If I choose "Ext4 journaling file system", I can find /home, /boot and / but there is no /swap?
Should I choose "swap area" for /swap instead of "Ext4 journaling file system"? And should I as types the default "Logical" or "Primary"?

Thanks

IIRC during the installation you have the option to install ubuntu in an empty, unused, unpartitioned space on your disk. The installer will sort what partitions to make in the emptyspace for you. So if you don't make the partition you are ready to install ubuntu.

(though I personally always opt for manual)

---

### Post by miegiel on 2010-12-07
> **riccardo.depalo said:**
> Hi everybody. As there was a 2.6.35-24 kernel upgrade, I builded, tested and uploaded a new kernel driver. You can find it in the usual site: 

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

thanks :)

---

### Post by ianni67 on 2010-12-08
Thank you again!:D

---

### Post by The Wish Within on 2010-12-08
> **miegiel said:**
> IIRC during the installation you have the option to install ubuntu in an empty, unused, unpartitioned space on your disk. The installer will sort what partitions to make in the emptyspace for you. So if you don't make the partition you are ready to install ubuntu.

(though I personally always opt for manual)

I've now installed Ubuntu and created the 4 partitions as Ext4 by deleting D.
But now there's a problem:
I can't start Linux!
Windows 7 just starts normal. But the disk space has gone... (D is as expected no longer available under Windows because I was used for Linux)
What should I do now? There is no option to choose between the operating systems...

---

### Post by miegiel on 2010-12-08
> **The Wish Within said:**
> I've now installed Ubuntu and created the 4 partitions as Ext4 by deleting D.
But now there's a problem:
I can't start Linux!
Windows 7 just starts normal. But the disk space has gone... (D is as expected no longer available under Windows because I was used for Linux)
What should I do now? There is no option to choose between the operating systems...

Do you get the grub boot menu where you can choose for ubuntu?
Your boot menu will have different choices from the example below, because you have XP installed for example.

[IMG]http://appuntiubuntu.files.wordpress.com/2007/06/grub_prima.png[/IMG]

If you don't get the boot menu you (the ubuntu installer) probably didn't install grub to right. You can repair it by installing it again why you boot ubuntu from the live CD/USB (the "try ubuntu" option). You can read how to do that here : [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling from LiveCD")

---

### Post by The Wish Within on 2010-12-08
Thank you so much! The reinstallation via LiveCD worked! The boot menu appears :D

//Edit: I've made what the documentation () said for 10.10:
sudo apt-add-repository ppa:plippo/t101mt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install eeepc-acpi-workaround egalax-multitouch-driver-common eeepc-brightness-workaround eeepc-powersave eeepc-touchpad-twofingers

and then I've installed the driver:

[egalax-multitouch-driver-2.6.35-23-generic-i386.deb]("https://help.ubuntu.com/community/T101MT?action=AttachFile&do=view&target=egalax-multitouch-driver-2.6.35-23-generic-i386.deb")

The touchscreen actually works.
However, it seems like multitouch doesn't work?

Also the touchpad doesn't work correct. If I use it with 2 fingers the cursors spins around like crazy.
Has none of the drivers mentioned above been installed?

---

### Post by miegiel on 2010-12-09
> **The Wish Within said:**
> Thank you so much! The reinstallation via LiveCD worked! The boot menu appears :D

//Edit: I've made what the documentation () said for 10.10:
sudo apt-add-repository ppa:plippo/t101mt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install eeepc-acpi-workaround egalax-multitouch-driver-common eeepc-brightness-workaround eeepc-powersave eeepc-touchpad-twofingers

and then I've installed the driver:

[egalax-multitouch-driver-2.6.35-23-generic-i386.deb]("https://help.ubuntu.com/community/T101MT?action=AttachFile&do=view&target=egalax-multitouch-driver-2.6.35-23-generic-i386.deb")

The touchscreen actually works.
However, it seems like multitouch doesn't work?

Also the touchpad doesn't work correct. If I use it with 2 fingers the cursors spins around like crazy.
Has none of the drivers mentioned above been installed?

(In a terminal) do :
```
xinput list
```
and make sure you have the *eGalax Inc. USB TouchController* (that's the touchscreen). There seems to be a new version of this tablet with a different touchscreen, that might be the problem. If you don't have the *eGalax Inc. USB TouchController* you might find some info earlier in this thread.

Regarding the touchpad, I posted about that in this thread a week ago. Use the thread-search-function and search for "xinput list". The post starts with "I don't know what exactly your problem is, ..." :D

---

### Post by thenzero on 2010-12-09
Anyone else having an issue on Meerkat where the mute button sends two events?

---

### Post by The Wish Within on 2010-12-09
> **miegiel said:**
> (In a terminal) do :
```
xinput list
```and make sure you have the *eGalax Inc. USB TouchController* (that's the touchscreen). There seems to be a new version of this tablet with a different touchscreen, that might be the problem. If you don't have the *eGalax Inc. USB TouchController* you might find some info earlier in this thread.

Regarding the touchpad, I posted about that in this thread a week ago. Use the thread-search-function and search for "xinput list". The post starts with "I don't know what exactly your problem is, ..." :D

I have the eGalax Inc. USB TouchController.
This morning, I found out that the touchpad no longer went crazy when touching it with 2 fingers.
However, I tried the TouchScreen in GIMP and it only works correct with one finger...

//EDIT:

I'm also having a bigger problem:
Whenever I try to remove a package, I get this error:
E: /var/cache/apt/archives/eeepc-brightness-workaround_1.0-ppa1_all.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/eeepc-brightness-powersave_1.0-ppa1_all.deb:  subprocess new post-removal script returned error exit status 1

==> I can't uninstall anything...
This errors appeared first when I tried to reinstall the packages for the Eee PC.
How can I fix this?

---

### Post by miegiel on 2010-12-09
> **thenzero said:**
> Anyone else having an issue on Meerkat where the mute button sends two events?

Yes! Don't ask me since when. It did work but I rarelyy use the button.

---

### Post by miegiel on 2010-12-09
> **The Wish Within said:**
> I have the eGalax Inc. USB TouchController.
This morning, I found out that the touchpad no longer went crazy when touching it with 2 fingers.
However, I tried the TouchScreen in GIMP and it only works correct with one finger...

//EDIT:

I'm also having a bigger problem:
Whenever I try to remove a package, I get this error:
E: /var/cache/apt/archives/eeepc-brightness-workaround_1.0-ppa1_all.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/eeepc-brightness-powersave_1.0-ppa1_all.deb:  subprocess new post-removal script returned error exit status 1

==> I can't uninstall anything...
This errors appeared first when I tried to reinstall the packages for the Eee PC.
How can I fix this?

Sorry, didn't see your post earlier. Maybe this thread will help you [http://ubuntuforums.org/showthread.php?t=744008](http://ubuntuforums.org/showthread.php?t=744008)

Remember this is an extremely extensive forum, someone has probably posted here about every problem you'll ever have. All you need to do is a smart search. ;)

---

### Post by riccardo.depalo on 2010-12-09
> **kl67 said:**
> Here is patch for Mypaint 0.9 and also a short Python script to patch brushes. The patch is made against stock Mypaint 0.9 source downloaded from mypaint.org. The patch is basically slightly modified version of Plippo's patch for version 0.8.2 (quick hack to acommodate for changes made to tileddrawwidget.py).

The Python scripts scans given folder and its subfolders for mypaint brush definitions (files ending with .myb) and patches them. Use this script to patch additional brushes which can be downlaoded from mypaint.org.

Usage:
```

python brushes.py top_folder

```top_folder is path to a folder containg brushes.

Hi! for anyboy of you who like painting with t101mt, I just tested and added this patch to the wiki: [https://help.ubuntu.com/community/T101MT#MYPAINT](https://help.ubuntu.com/community/T101MT#MYPAINT)

have fun! :)

---

### Post by DheathNone on 2010-12-13
> **DheathNone said:**
> Actually this was not such a good idea in the end. After some upgrade the gnome seems to take that key and actually rotate the screen by its own means. This means the touchscreen does not rotate but the screen does!

**Use instead:**
**keycode 160 = XF86**[insert some clearly useless action(google something)]

I used XF86Eject, because it was useless for me and it was possible to actually change the shortcut for eject from keyboard shortcuts!

Seems that after some update even this method stopped working. I do not know what it is about this but this is getting quite ridiculous.

So, does anyone even have any hints how to stop Ubuntu locking the screen when the "Express gate"-button is pressed in 10.10? Or even why it is doing it?

---

### Post by bakinsoda on 2010-12-17
Hi everyone,

I'm having a microphone issue.  It works with Sound Recorder, but not with Google Chat and Skype.  On the Wiki and other posts about microphone not working, they suggest lowering the sound of the mic on one side to make things mono (through alsamixer or padevcontrol).  This does work.  But on my system, the lowered sound control increases to the other's as I speak in it.  Then the mic stops working.

Do you guys have this issue?  Do you know of a fix?  Thanks.

---

### Post by miegiel on 2010-12-18
> **bakinsoda said:**
> ... the lowered sound control increases to the other's as I speak in it...

That happens to you in skype?

If so, skype automatically adjusts the microphone by default. You can turn it off in skype > options > sound.

---

### Post by bakinsoda on 2010-12-18
Thanks @miegiel.  It worked in Skype.  As for the same problem in google chat, the fix can be found [here]("http://www.google.com/support/forum/p/chat/thread?tid=1069bb4926bbd5fa&hl=en") (restart computer after).

I will update the WIKI to reflect this.

---

### Post by The Wish Within on 2010-12-20
Hi. I just found out that ASUS ExpressGate suddenly doesn't work.
But I'd like to have it working. I know it works after the installation of Ubuntu but now... it doesn't. What's the problem? Does anyone know a solution?

---

### Post by mwer17 on 2010-12-22
Hey guys, I am new to Ubuntu and am trying it on my new t101mt. I've installed the new 10.10 maverick meerkat and am trying to get the touchscreen and screen rotation to work and am not having much luck.

I've visited the ubuntu community documentation page and followed the steps given. The first step asks me to input the following into a terminal:

sudo apt-add-repository ppa:plippo/t101mt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install eeepc-acpi-workaround egalax-multitouch-driver-common eeepc-brightness-workaround eeepc-powersave eeepc-touchpad-twofingers
I do this and at the end it asks the following:

Need to get 77.6kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.


No matter what I input, the result is always "Abort." I'm assuming this is needed to get the touchscreen working?

Forgive any ignorance in this post, I am a new to linux

Thanks!

---

### Post by miegiel on 2010-12-23
> **mwer17 said:**
> Hey guys, I am new to Ubuntu and am trying it on my new t101mt. I've installed the new 10.10 maverick meerkat and am trying to get the touchscreen and screen rotation to work and am not having much luck.

I've visited the ubuntu community documentation page and followed the steps given. The first step asks me to input the following into a terminal:

```
sudo apt-add-repository ppa:plippo/t101mt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install eeepc-acpi-workaround egalax-multitouch-driver-common eeepc-brightness-workaround eeepc-powersave eeepc-touchpad-twofingers
```
I do this and at the end it asks the following:

```
Need to get 77.6kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
```


No matter what I input, the result is always "Abort." I'm assuming this is needed to get the touchscreen working?

Forgive any ignorance in this post, I am a new to linux

Thanks!

The capital *Y* means it's the default option, just hitting *enter* should suffice. Though *Y*, *y* and *yes* should all work.

Are you entering those 4 lines in the terminal 1 by 1? If not that might be the problem. If you are entering the lines 1 by 1 is it the last line that is causing your trouble or 1 of the other lines?

If this doesn't help you, post the full output of each line you entered. There might be some useful info that tells us what's going wrong.

Finally, post in- and outputs of the terminal in code boxes (use the **#** button in the post editor). It prevents smilies and makes it more obvious what's being put into or put out by the terminal.

---

### Post by mwer17 on 2010-12-23
That was the fix! Thanks so much

---

### Post by mwer17 on 2010-12-23
Hmm...it seems as though the touchscreen stops working after I reboot. Although, if I enter the following into a terminal it starts to work again:

```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
```

Is there any way I can make the touchscreen work after boot up without having to enter those commands each time?

---

### Post by miegiel on 2010-12-24
> **mwer17 said:**
> Hmm...it seems as though the touchscreen stops working after I reboot. Although, if I enter the following into a terminal it starts to work again:

```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
```

Is there any way I can make the touchscreen work after boot up without having to enter those commands each time?

Do you hve the *AsusTek, Inc. MultiTouch(YFO)* or the *D-WAV Scientific Co., Ltd* touchscreen?

To check which touchscreen you have run :
```
lsusb
```

I have the *D-WAV Scientific Co., Ltd* touchscreen and don't have that issue. If you have the *AsusTek, Inc. MultiTouch(YFO)* touchscreen, maybe someone with that touchscreen knows how to make the fix permanent.

If not, the only thing I can think of to make the fix a little less cumbersome, is to put the commands in a script.

Open *gedit* (or whatever editor you prefer) and paste this :
```
#!/bin/bash
#
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
exit
```
and save it as *touchscreenfix.sh* in your home directory.
Next run
```
chmod +x touchscreenfix.sh
```
to make the script executable.

Now, after a reboot, all you need to do is run  *touchscreenfix.sh* in a terminal.

---

### Post by coffen on 2010-12-25
> **miegiel said:**
> Now, after a reboot, all you need to do is run  *touchscreenfix.sh* in a terminal.

Or have a look at this link how to make it run at each boot. :)
[http://stringofthoughts.wordpress.com/2009/04/16/adding-removing-shell-scripts-ubuntu-810/](http://stringofthoughts.wordpress.com/2009/04/16/adding-removing-shell-scripts-ubuntu-810/)

---

### Post by exodusfollower on 2010-12-25
I'm running Kubuntu with 10.10, & the bottom of the touchscreen isn't responsive.  Anytime I try to touch the bottom the pointer doesn't go there.  I tried reloading the drivers with the instructions at [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT).  What could be the issue?

---

### Post by miegiel on 2010-12-26
> **exodusfollower said:**
> I'm running Kubuntu with 10.10, & the bottom of the touchscreen isn't responsive.  Anytime I try to touch the bottom the pointer doesn't go there.  I tried reloading the drivers with the instructions at [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT).  What could be the issue?

Calibration.

I don't have a calibration tool in xubuntu, but you might have one in kubuntu. Post here if you don't and I'll make a longer post how to calibrate the touchscreen in the terminal.

---

### Post by mwer17 on 2010-12-26
When I run lsusb into a terminal I don't see either of those. This is what I get ```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It doesn't match either of the devices you have listed or those that are listed in the community documentation on the Ubuntu website.

Am I missing something?

---

### Post by Naitsirhc Hsem on 2010-12-26
use ```
xinput list
```

---

### Post by Naitsirhc Hsem on 2010-12-26
in natty, those with the AsusTek, Inc. MultiTouch(YFO) have limited support!! I remain optimistic for full functionality out of the box

---

### Post by exodusfollower on 2010-12-26
Kubuntu doesn't have a calibrator built in.  I'm hoping a terminal calibration will help.

---

### Post by miegiel on 2010-12-27
> **exodusfollower said:**
> Kubuntu doesn't have a calibrator built in.  I'm hoping a terminal calibration will help.

Ok here it is, touchscreen callibration in the terminal.

If you run
```
evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00
```
in a terminal, the terminal will put out the input from the touchscreen to the terminal. If the command doesn't work you should verify the path. If you have the Asus instead of the eGalax touchscreen your path will obviously be different. Now *evtest* puts out alot more info than you need and that makes measuring the edges of your screen difficult. Therefore I pass it through *grep* to filterout only the X or the Y axis.

X axis :
```
evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 | grep "code 53"
```
Y axis :
```
evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 | grep "code 54"
```

Use both commands to find the maximum and minimum X and Y axis values. And then use the values to calibrate the touchscreen using the *xinput* command.
```
xinput --set-prop --type=int --format=32 "eGalax Inc. USB TouchController" "Evdev Axis Calibration" min-x max-x min-y max-y
```
Replace *min-x max-x min-y max-y* with the values you foud with *evtest*. Test the result of the callibration to see if it is acurate enough for you.

Now, if everything works to your satisfaction, you want to make the callibration permanent. There are 2 ways to do this: 1) You can enter it into the Xorg configuration 2) You can make a script that runs when X starts up.

For method 1) see [this post]("http://ubuntuforums.org/showthread.php?p=10280615#post10280615") in the HOWTO : eGalax Touch Screen on Ubuntu 10.04 thread.

I personally prefer to use a startup script. In my startup script I've combined the settings for the touchpad and the touchscreen. [Here I explain]("http://ubuntuforums.org/showthread.php?p=10163866#post10163866") how to do it and you'll find my current startup script below for inspiration (there's an explanation behind every command). I have noticed that sometimes the script runs to soon and the calibration doesn't take effect. If that happens, increse the *sleep* delay in the script.

```
#!/bin/bash
#
# synaptics man page (maverick) http://manpages.ubuntu.com/manpages/maverick/en/man4/synaptics.4.html
# evdev man page (maverick) http://manpages.ubuntu.com/manpages/maverick/man4/evdev.4.html
#
# Some useful commands :
#
#	xinput list
#	xinput list-props "SynPS/2 Synaptics TouchPad"
#	xinput test "SynPS/2 Synaptics TouchPad"
#	xinput test-xi2 "SynPS/2 Synaptics TouchPad"
#
#	xinput list-props "eGalax Inc. USB TouchController"
# X axis calibration
#	evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 | grep "code 53"
# Y axis calibration
#	evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 | grep "code 54"
#
sleep 5                                                                                                           # give X time to start
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32          # value: 0-255
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8              # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0        # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0            # vertical, horizontal, corner - values: 0=disable  1=enable
#xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250      # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 2 0 0        # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9 10 11 12                                   # swap left and middle click, gives you middle click on the left button and left click on tap. - values: lb, mb, rb, b4, b5, etc.

sleep 9   
xinput --set-prop --type=int --format=32 "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 6 4088 0 4092 # values: min-x, max-x, min-y, max-y
#xinput --set-button-map "eGalax Inc. USB TouchController" 1 0 0 4 5                                               # values: lb, mb, rb, b4, b5.
exit
```

---

### Post by The Wish Within on 2010-12-31
> **The Wish Within said:**
> Hi. I just found out that ASUS ExpressGate suddenly doesn't work.
But I'd like to have it working. I know it works after the installation of Ubuntu but now... it doesn't. What's the problem? Does anyone know a solution?

*Bump*

---

### Post by Naitsirhc Hsem on 2010-12-31
My *theory* is that ubuntu overwrites the expressgate partition, why do you want expressgate, it is just another linux knockoff

---

### Post by miegiel on 2010-12-31
> **Naitsirhc Hsem said:**
> My *theory* is that ubuntu overwrites the expressgate partition,
after keeping the partitioning intact, only downsizing the partitions and putting all the linux partitions in a extended partition, expressgate still works for me.
> why do you want expressgate, it is just another linux knockoff
So true, it even has the same microphone bug in skype :D

---

### Post by miegiel on 2011-01-01
> **The Wish Within said:**
> Hi. I just found out that ASUS ExpressGate suddenly doesn't work.
But I'd like to have it working. I know it works after the installation of Ubuntu but now... it doesn't. What's the problem? Does anyone know a solution?

ExpressGate works here. Though, since I have a BIOS password, I get welcomed by a empty black screen. It still boots after I enter the password. If there's a way to restore ExpressGate you might find it at asus or the asus forum.

---

### Post by psykatog on 2011-01-02
Sorry if I'm late to the discussion (and worse, I haven't read the thread for a while) -

Is it possible to dual boot using the express gate button?   As in, to dual boot two OSs, say, Kubuntu and Slax, and have one button turn on Kubuntu and the expressgate button boot into slax?  And if so, any chance they could share files?  So that, ie, if I save an openoffice file in one, I can open it in the other...

---

### Post by dima206 on 2011-01-04
Hi everyone
I have installed ubuntu 10.10 on my T101MT, and all drivers from [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)
* I have a standard version of a touchscreen
but I have some problems:  :(
1) Full brightness start to work only after I rotate the screen
2) Gnome Key-shortcuts and xev can't recognize express-gate button

Do anyone have a solution for this problems

Thanks.

---

### Post by mikshepard on 2011-01-06
Hey all, 
I've created a howto for installing Debian Squeeze on the t101mt model.  The process is somewhat more complicated than following the ubuntu steps and so I thought I would save others the trouble of tinkering with the netbook for over a month to get everything working, like I did  ](*,).  Some of the steps are the same though and those that were I used in my howto.  I tried to give credit to you all where credit was due, and  I don't want to step on anyone's toes; so if I mis-cited a source to you all or you think something else should be added, please let me know and I will do so.  Otherwise thanks for the help in your contribution to allow me a solid squeeze distro on my computer!  I couldn't be happier with this thing.

Cheers,
Mike

Here is the link if you are interested: [http://forums.debian.net/viewtopic.php?f=7&t=59055](http://forums.debian.net/viewtopic.php?f=7&t=59055)

---

### Post by miegiel on 2011-01-06
> **mikshepard said:**
> Hey all, 
I've created a howto for installing Debian Squeeze on the t101mt model.  The process is somewhat more complicated than following the ubuntu steps and so I thought I would save others the trouble of tinkering with the netbook for over a month to get everything working, like I did  ](*,).  Some of the steps are the same though and those that were I used in my howto.  I tried to give credit to you all where credit was due, and  I don't want to step on anyone's toes; so if I mis-cited a source to you all or you think something else should be added, please let me know and I will do so.  Otherwise thanks for the help in your contribution to allow me a solid squeeze distro on my computer!  I couldn't be happier with this thing.

Cheers,
Mike

Here is the link if you are interested: [http://forums.debian.net/viewtopic.php?f=7&t=59055](http://forums.debian.net/viewtopic.php?f=7&t=59055)

Nice work, no toes stepped on. ;)

---

### Post by Kevrox on 2011-01-07
> **mikshepard said:**
> Here is the link if you are interested: [http://forums.debian.net/viewtopic.php?f=7&t=59055](http://forums.debian.net/viewtopic.php?f=7&t=59055)

Very nice job mate, Oh so tempted........

---

### Post by Non.Cents on 2011-01-07
I have a different device, a Dell Duo, but the touch screen I believe to be the same. I followed the instructions for the touchscreen (omitting the rest) on the help page for your device. The touch still goes to the top left corner of the screen. I'm not sure where to go from here. i have tried just about everything i can find for an egalax touch and none of it is working. I have found a way to get single touch to work, but not multi. Can anyone help, or point me to someone who might be able to.

This is the stats for the device

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

---

### Post by Plippo on 2011-01-09
@ Non.Cents:
Your screen isn't exactly the same as in the Eee PC T101MT - the T101MT's screen has the ID 0eef:480d, yours the ID 0eef:725e. So the touchscreen driver doesn't recognize your device, support has to be built in. This could be easy if it works the same way as one of the two already supported devices or more difficult if it doesn't. I would recommend contacting Henrik Rydberg (you find him here on launchpad: [https://launchpad.net/~rydberg](https://launchpad.net/~rydberg) ) who is one of the main developers of the eGalax driver.

---

### Post by Non.Cents on 2011-01-10
Thank you much for the help.

---

### Post by linxgr on 2011-01-11
I am pretty sure this is a bit off-topic but it has to do with the overall linux experience on the tablet. Two questions, what are the changes in the 0.0.7 twofing daemon and how can you use the netbook in tablet rotated mode? I mean i have to start everything from the terminal since the menu is overridden. Either I have to put shortcuts for the most common programs on the screen or run everything out from the terminal which with a virtual keyboard which I have to move around since its huge. Am I missing something really obvious here?

---

### Post by ianni67 on 2011-01-12
> **linxgr said:**
> I am pretty sure this is a bit off-topic but it has to do with the overall linux experience on the tablet. Two questions, what are the changes in the 0.0.7 twofing daemon and how can you use the netbook in tablet rotated mode? I mean i have to start everything from the terminal since the menu is overridden. Either I have to put shortcuts for the most common programs on the screen or run everything out from the terminal which with a virtual keyboard which I have to move around since its huge. Am I missing something really obvious here?
I installed Cairo-dock and moved most items from the upper side bar of gnome to the Cairo Dock. Now the menus are not hidden any more. 
Moreover, the buttons on Cairo Dock are easier to be selected with a finger than the items on the gnome menus.

Here is a screenshot of my rotated desktop:
[http://img821.imageshack.us/i/schermatar.png/](http://img821.imageshack.us/i/schermatar.png/)

---

### Post by maron on 2011-01-13
Hi, I tried find some solution, but I didn't. I have tablet PC T101MT. I have ubuntu 10.10 netbook. I upgrade from 10.4. I followed [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT) .  Some logs:```
maron@maronTPC:~$ xinput --list  
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=12	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=13	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
maron@maronTPC:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
maron@maronTPC:~$ 

``` 
And I have this problems:
1. Rotate touch screen: When I rotate screen by command "touchrotate" or by "GKEYMANAGER" rotates only screen. The coordinate x and y are flipped. On 10.4 this work.

2. Two finger gestures: When I run "twofing" and click on screen the cursor only follow finger. Neither two finger gestures don't work. On 10.4 this work.

3. Rotate button. Pressing rotate button on the bottom of screen cost sleep and lock screen. In shortcuts manager I don't have mapped anything. And if I map some action on this button it will do both (my some action and sleep of screen)

4. This isn't problem but if anyone know how by holding finger on some spot make popup right mouse menu I will be happy :)

Please help me somebody. :)

---

### Post by atomp on 2011-01-13
I've had similar problems so here are the workarounds that I used.

1. I also had a similar problem, however I fixed this by adding the device information to the command as was the method in earlier versions. Something like:
"touchrotate LVDS1 10 toright"

2. When Twofing doesn't work I tend to just try reinstalling the multitouch drivers (making sure I get the correct kernel, or building the drivers myself) and then reinstalling Twofing.

3. Would love to help on this but I've yet to find a way of fixing this. (Although there are some interesting acpi script entries related to it which I intend to look at when I get some free time).

4. This is in the Mouse settings as "Simulated Secondary Click".

---

### Post by maron on 2011-01-15
Thanks for that. 1 and 2 works for me. I still hope for solution for 3. And I dont need 4 when I have multitouch.

---

### Post by maron on 2011-01-15
And I have new problem.  when I install correct multitouch drivers program EasyStroke stop work.

---

### Post by coffen on 2011-01-15
> **mikshepard said:**
> Hey all, 
I've created a howto for installing Debian Squeeze on the t101mt model.  The process is somewhat more complicated than following the ubuntu steps and so I thought I would save others the trouble of tinkering with the netbook for over a month to get everything working, like I did  ](*,).  Some of the steps are the same though and those that were I used in my howto.  I tried to give credit to you all where credit was due, and  I don't want to step on anyone's toes; so if I mis-cited a source to you all or you think something else should be added, please let me know and I will do so.  Otherwise thanks for the help in your contribution to allow me a solid squeeze distro on my computer!  I couldn't be happier with this thing.

Cheers,
Mike

Here is the link if you are interested: [http://forums.debian.net/viewtopic.php?f=7&t=59055](http://forums.debian.net/viewtopic.php?f=7&t=59055)

Hi,
I followed your instructions here: [http://forums.debian.net/viewtopic.php?f=7&t=59055](http://forums.debian.net/viewtopic.php?f=7&t=59055)
When I execute the sed command:
[FONT="Fixedsys"]sudo sed -e 's!\x1a\x0\x0\x0\x98!\x1a\x0\x0\x0\x99!' eeepc-laptop.ko.orig > eeepc-laptop.ko[/FONT]

I get an error:
[FONT="Fixedsys"]bash: eeepc-laptop.ko: permission denied[/FONT]

What could be the cause of this?

Edit:
Needed to issue **sudo su** first to get root access.
Simply adding **sudo** in front of **sed** was not enough.
You need to do this:
[FONT="Fixedsys"]sudo su
sed -e 's!\x1a\x0\x0\x0\x98!\x1a\x0\x0\x0\x99!' eeepc-laptop.ko.orig > eeepc-laptop.ko[/FONT]

---

### Post by miegiel on 2011-01-15
> **coffen said:**
> ...

Needed to issue **sudo su** first to get root access.
Simply adding **sudo** in front of **sed** was not enough.
You need to do this:
[FONT="Fixedsys"]sudo su
sed -e 's!\x1a\x0\x0\x0\x98!\x1a\x0\x0\x0\x99!' eeepc-laptop.ko.orig > eeepc-laptop.ko[/FONT]

and exit when done
```
exit
```
(for the clueless among us ;))

---

### Post by coffen on 2011-01-15
> **miegiel said:**
> 
[QUOTE=coffen;10360571]
...

Needed to issue **sudo su** first to get root access.
Simply adding **sudo** in front of **sed** was not enough.
You need to do this:
[FONT="Fixedsys"]sudo su
sed -e 's!\x1a\x0\x0\x0\x98!\x1a\x0\x0\x0\x99!' eeepc-laptop.ko.orig > eeepc-laptop.ko[/FONT]and exit when done
```
exit
```
(for the clueless among us ;))[/QUOTE]
So I got the **sed** part done and also the **rmmod eeepc-laptop** and **modprobe eeepc-laptop** OK.

As a user I then issued the command:
[COLOR="Green"]echo “keycode 161 = XF86Mail” >> ~/.Xmodmap[/COLOR]
Rebooted and loaded the mod file.

For some reason I am still unable to map the Rotate button (Express Gate Button) to do anything.
What am I missing here?
Is the keycode different in Ubuntu compared to Squeeze.
This post seems to indicate so [http://ubuntuforums.org/showpost.php?p=9446053&postcount=171](http://ubuntuforums.org/showpost.php?p=9446053&postcount=171)

---

### Post by coffen on 2011-01-15
Accidental double post - unable to delete it myself.

---

### Post by coffen on 2011-01-15
Accidental double post - unable to delete it myself.

---

### Post by coffen on 2011-01-15
Accidental double post - unable to delete it myself.

---

### Post by riccardo.depalo on 2011-01-17
Hi everybody. I loaded new kernel 2.6.35-25 and I noticed that the eGalax touchscreen works without having to build any new kernel driver. Also towfing works like before. It seems a good improvement, for anyone who wants to use ubuntu with this machine. :)

---

### Post by miegiel on 2011-01-17
> **riccardo.depalo said:**
> Hi everybody. I loaded new kernel 2.6.35-25 and I noticed that the eGalax touchscreen works without having to build any new kernel driver. Also towfing works like before. It seems a good improvement, for anyone who wants to use ubuntu with this machine. :)

I'm test driving natty at the moment and don't need to install it either anymore (kernel 2.6.37-12). I had a problem compiling twofing in 64 bit natty, it works without problems in 32bit.

---

### Post by mwer17 on 2011-01-17
Hey Guys,

I'm not having any luck getting the rotate-screen button or the "windows" button (the button that is two to the left of the spacebar) to work in the keyboard shortcuts program. Has anyone got them working in maverick meerkat?

Thanks!

---

### Post by bakinsoda on 2011-01-19
I really don't know why not everything works in Ubuntu 10.10...something always break...or I never got everything working since upgrading to 10.10 last year.

Two-fing works.  Touchscreen works.

MyPaint does not work.  Sometimes it does, sometimes it doesn't.  Why is this?  When I say it doesn't work, I mean both touchscreen and touchpad.  Painting doesn't work.

Also, "touchrotate left", etc, rotates screen.  But when I touch screen, the mouse cursor isn't at the correct spot.  Anyone also getting this?

---

### Post by bakinsoda on 2011-01-19
I really don't know why not everything works in Ubuntu 10.10...something always break...or I never got everything working since upgrading to 10.10 last year.

Two-fing works.  Touchscreen works.

MyPaint does not work.  Sometimes it does, sometimes it doesn't.  Why is this?  When I say it doesn't work, I mean both touchscreen and touchpad.  Painting doesn't work.

Also, "touchrotate left", etc, rotates screen.  But when I touch screen, the mouse cursor isn't at the correct spot.  Anyone also getting this?

---

### Post by bakinsoda on 2011-01-19
> **bakinsoda said:**
> I really don't know why not everything works in Ubuntu 10.10...something always break...or I never got everything working since upgrading to 10.10 last year.

Two-fing works.  Touchscreen works.

MyPaint does not work.  Sometimes it does, sometimes it doesn't.  Why is this?  When I say it doesn't work, I mean both touchscreen and touchpad.  Painting doesn't work.

Also, "touchrotate left", etc, rotates screen.  But when I touch screen, the mouse cursor isn't at the correct spot.  Anyone also getting this?

Updated kernel and updated drivers for the kernel, and touchrotate works now.

MyPaint is still an issue (0.8.2).  Don't know why it works sometimes.

---

### Post by floyd0815 on 2011-01-19
Hi folks!

Has no one tried GINN for gesture recognition? (searched this thread without luck)

A guy from Brasil contacted me to help him getting it working on his T101, but because of the different timezones we haven't managed to make a TeamViewer session till yet.

Would be nice if someone has it done and can give some advice!
Does the T101 even have 4 finger support? (T91 hasn't, right?)

Since I have an HP TX2, I can only guess and search throw the hole T101 system to get it working AND THIS TAKES MUCH TIME! (other hardware, udev rules,  xorg.conf.d,...)

He asked me cause of my video:
[http://www.youtube.com/watch?v=44QSLk-FgPg](http://www.youtube.com/watch?v=44QSLk-FgPg)

GINN at launchpad:
[https://launchpad.net/ginn](https://launchpad.net/ginn)

To install it:
```
sudo apt-get install utouch

sudo apt-get build-dep utouch-gesturetest

sudo apt-get install build-essential libx11-dev libxml2-dev libxi-dev libxtst-dev

wget http://launchpad.net/ginn/0.x/0.2.3/+download/ginn-0.2.3.tar.bz2

tar -xvjf ginn-0.2.3.tar.bz2


cd ginn-0.2.3

./autogen.sh --prefix=/usr  ## I THINK THIS NEEDN'T TOBE DONE IN THIS VERSION!

./configure --prefix=/usr

make

sudo make install

sudo cp etc/wishes.xml /etc/
```

To start it, type in a terminal: ginn


THX in advance!

---

### Post by ianni67 on 2011-01-19
In my knowledge T101MT only supports two fingers - and to me this is a major drawback because I don't know a way to substitute alt-click or ctrl-click operations (such as those bound the wall of windows or desktop rotate in compiz) with two-fingers gestures.
In other words, there are a number of commands which are usually bound to combinantions of keyboard keys and mouse clicks which are very common and which are very hard to bind to two-finger touch gestures (for example, think of moving a window: you need to press alt and click and drag with the mouse).

It would be great to have GINN working with my T10MT: I would definitely throw the keyboard off!:p

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt it manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by floyd0815 on 2011-01-19
Sorry!
Server problems?

---

### Post by floyd0815 on 2011-01-19
Sorry!
Server problems?

---

### Post by floyd0815 on 2011-01-19
Sorry!
Server problems?

---

### Post by floyd0815 on 2011-01-19
Sorry!
Server problems?

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by floyd0815 on 2011-01-19
Sorry!
There was something wrong with my FF or my connection.

---

### Post by floyd0815 on 2011-01-19
Sorry!
There was something wrong with my connection.

---

### Post by floyd0815 on 2011-01-19
Sorry!
There was something wrong with my FF or my connection.

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by floyd0815 on 2011-01-19
Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

---

### Post by ianni67 on 2011-01-19
> **floyd0815 said:**
> What exactly can Two-Fing do? Only switching between the desktops?
***************
.
I can switch between the desktop  and - using the twofing demon - I can emulate right-click by tapping two fingers. 

But I would like to use my T101MT as a tablet and that's why I need some gestures emulating ALT+CLICK and CTRL+CLICK.

---

### Post by floyd0815 on 2011-01-19
Maybe you can get that, in a DIRTY way. ;)

With a command like:
```
xdotool keydown --delay 5000 ctrl keyup ctrl
```
you activate ctrl pressed for 5 seconds.
Or make it activ for a specific window and enable/disable it by executing commands from the main menu.

See
```
man xdotool
```

---

### Post by ianni67 on 2011-01-20
This sounds interesting! I might add a couple of buttons to my docking bar, for ctrl and for alt. One click activates, say, ctrl, the second click on the same button de-activates it. :-) I'll give it a try!

---

### Post by floyd0815 on 2011-01-20
Yeah, sounds good.
PLZ share your script if you have done it.
But be coutious, you don't have keyboard input if ctrl is pressed (had to logout and -in again) and be sure, that the buttons/starter work with ctrl/alt pressed.

---

### Post by ekeko on 2011-01-20
> **sergey1369 said:**
> Hello. Here is quick and dirty way to disable screen lock on pressing rotate button (express gate button) in Ubuntu 10.10. Replace eeepc-laptop.ko's KEY_COFFEE(0x98 ) button with KEY_DIRECTION(0x99).

static const struct key_entry eeepc_keymap[] = {
...
    { KE_KEY, 0x1a, { KEY_COFFEE } } -> { KE_KEY, 0x1a, { KEY_DIRECTION } } , 
...
}

It's too complex to recompile driver, but it's fairly simple to make a binary fix. 
Here we go.

# cd /lib/modules/2.6.35-23-generic/kernel/drivers/platform/x86
# cp eeepc-laptop.ko eeepc-laptop.ko.orig
# sed -e 's!\x1a\x0\x0\x0\x98!\x1a\x0\x0\x0\x99!' eeepc-laptop.ko.orig > eeepc-laptop.ok
# rmmod eeepc-laptop
# modprobe eeepc-laptop

GOOD: Now button can be binded via standard keyboard shortcuts to any program.
BAD: every kernel update requires repeating procedure.

Hi Sergey,
I noticed that in my asus t101mt the express-gate button is not assigned to screensaver at all. it is not recognized somehow. however it works fine for express-gate or in windows.

I applied your solution, but no changes at all.

can you help me on this?
thanks in advance!

PY

---

### Post by ekeko on 2011-01-20
> **floyd0815 said:**
> Only 2 fingers? Doh!

But with 2 fingers you can perform a right-click (hold one finger on the place/object you want and tap another finger), drag 2 fingers (or one finger) up/down/left/right, rotate, or pinch.

My TX2 has 4 finger support, but I have no gestures with alt to drag (I grab the windowframe or press alt manually) or ctrl.
One hand is always near the keyboard so it's not a big problem. (for me)

The right-click is what I MUST have.

There for I made a new keyboard-shortcut (Super_L + t) in Ubuntu with this command:
```
xdotool click 3
```
(sudo apt-get install xdotool)

And then I made a wish (for ginn in wishes.xml) to perform Super_L + t when I tap 2 fingers.

It's working perfectly!

If I get ginn working on the T101, I will post a HowTo here and the wishes.xml for ginn, but only IF I...

What exactly can Two-Fing do? Only switching between the desktops?

hello,
one newbie question, but what about if instead of using two fingers to have right-click with just the stylus?
regards,
py

---

### Post by R0GUE on 2011-01-20
My touchscreen isn't working right and I can't figure out why. No matter where I touch it, the pointer goes to the upper left (0,0) and clicks.  The touchscreen works fine if I boot to Win7, so I know it's not the hardware.

I followed the Community Documentation for T101MT.  I have the 2.6.35-22 kernel of 10.10 desktop i386 and have downloaded and installed the 35-22 egalax package after [FONT=Courier New]update[/FONT] and [FONT=Courier New]upgrade[/FONT].  Running [FONT=Courier New]lsusb[/FONT] does not show the AsusTek 2nd gen hardware.  I've tried reinstalling 10.10 desktop, 10.04 desktop, and 10.10 netbook.  I feel like I'm missing something, but I'm out of ideas.  Can anyone provide some guidance?  Any help is appreciated!

---

### Post by ianni67 on 2011-01-21
> **floyd0815 said:**
> Yeah, sounds good.
PLZ share your script if you have done it.
But be coutious, you don't have keyboard input if ctrl is pressed (had to logout and -in again) and be sure, that the buttons/starter work with ctrl/alt pressed.
Yes of course - I will need a couple of script and probably use "flag" file in an hidden directory to signal when the key is on. I'll try as soon as I have half an hour of free time :-D

---

### Post by ianni67 on 2011-01-21
> **ekeko said:**
> hello,
one newbie question, but what about if instead of using two fingers to have right-click with just the stylus?
regards,
py

I would suggest using the same solution I was discussing a few posts above: add a (virtual) button on the desktop to switch on/off the "right click" modifier: if you tap on the button and then tap with the pen somewhere on the screen, you'll have a right-click. Tap again on the button and you switch off the "right click" so your next tap will be a normal one.

Somehow slower than mouse operations but should work.

---

### Post by messinwu14020 on 2011-01-21
Hey Everyone

New Ubuntu user here, but long-time Fedora user.  Just got a T101MT and decided to put Ubuntu on it because it looked like there was a lot of activity in tweaking Ubuntu for the device, whereas I could not find the same kind of support going on with Fedora.

Anyway, I have 10.10 on it, and I have the "newer" touchscreen, so I have set up the script to modprobe usbhid quirks=0x0486:0x0186:0x0040 every time it boots, which does fine for single-touch.  It seems that NONE of the drivers or twofing will work with this touch screen.  Hopefully soon.

I'm using the touchrotate command to rotate the screen but as you know it doesn't rotate the touch screen also unless you specify like this: "touchrotate LVDS1 10 toright", since I have the newer, unsupported touch screen.

This command is fine, I've created a hotkey for it, but the problem is the number "10" which needs to be specified in the command, seems to change on almost every boot, sometimes the correct number to rotate the touch is 11, sometimes 16, sometimes 10.  Does anyone know how to determine what this number is without just guessing?  I can't set up a hotkey command without knowing the correct number, otherwise it rotates the screen but the touch positions are incorrect.

When I do: 'xinput list', I get two identical devices called 'AsusTek, Inc. MultiTouch(TTI), each have a different id.  Their ID's change on each boot, as I've described above.


I read most of this entire thread and maybe I missed something, but could someone shed some light?

---

### Post by messinwu on 2011-01-22
Well guys, I've come up with a method to properly rotate this new "0486:0186" touch screen.  With help from a post about a Dell tablet on another site:  [https://bbs.archlinux.org/viewtopic.php?id=107167](https://bbs.archlinux.org/viewtopic.php?id=107167)

I stole the code at the end of that post, changed the resolutions and the X and Y coordinates to be correct for the T101MT.  I made the following script, named it rotate.sh in my home directory, and made a custom application launcher button on the bottom panel in gnome to be used for rotating the screen by executing this 'rotate.sh' script:

```
#!/bin/bash

rangex=( 0 3478 )
rangey=( 0 3478 )
torotate=( 9 10 )

xrandrout="$(xrandr)"

case $xrandrout in
 *600x1024* ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
 *1024x600* ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
esac

xrandr -o $(( rotate * 3 ))
for input in ${torotate[@]}; do
 xinput set-prop $input "Evdev Axes Swap" $rotate
 xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
 xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
done
```


Now to figure out how to make this script execute when the ExpressGate button is pressed.  As you know, this button registers absolutely nothing at this time.  I found a hack somewhere which does an 'sed' command to something, but after reboot it does not work, at least for mine.

So, at this point the only two things not working as intended are that button and multi-touch.

---

### Post by eeeuser on 2011-01-22
I'm having serious issues calibrating the T101MT. I have followed the directions on installing from the guide but to no avail.

I first installed ubuntu 10.10 than [FONT=monospace][/FONT]followed instructions from [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT).

I also tried instructions from [http://jeffhoogland.blogspot.com/2010/07/howto-ubuntu-linux-on-t101mt.html](http://jeffhoogland.blogspot.com/2010/07/howto-ubuntu-linux-on-t101mt.html).

I tried installing xinput calibrator from main website and using but the problem is at this point. I tried also the xinput calibrator from [http://philmerk.de/general/download.php?fld=deb](http://philmerk.de/general/download.php?fld=deb). 
[B]
The calibration points won't update (target on screen will not move). It accepts the first touch and advances to the right corner but will not accept any further touches.[/B] So I'm stuck. I tried ubuntu 10.04, xubuntu 10.10, ubuntu netbook edition with same problem. PLease help, its driving me crazy.

---

### Post by floyd0815 on 2011-01-23
@messinwu

Have you read about Magick-Rotation?
[https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)
The T101 isn't supported yet, but maybe you can edit the code to work / ask for supporting the device.
It can turn off touch by pressing the task-symbol (for pen use), automatically rotate the screen (evdev and wacom for now) and execute commands when going in / leaving tablet mode.

---

### Post by miegiel on 2011-01-23
> **eeeuser said:**
> I'm having serious issues calibrating the T101MT. I have followed the directions on installing from the guide but to no avail.

I first installed ubuntu 10.10 than [FONT=monospace][/FONT]followed instructions from [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT).

I also tried instructions from [http://jeffhoogland.blogspot.com/2010/07/howto-ubuntu-linux-on-t101mt.html](http://jeffhoogland.blogspot.com/2010/07/howto-ubuntu-linux-on-t101mt.html).

I tried installing xinput calibrator from main website and using but the problem is at this point. I tried also the xinput calibrator from [http://philmerk.de/general/download.php?fld=deb](http://philmerk.de/general/download.php?fld=deb). 
[B]
The calibration points won't update (target on screen will not move). It accepts the first touch and advances to the right corner but will not accept any further touches.[/B] So I'm stuck. I tried ubuntu 10.04, xubuntu 10.10, ubuntu netbook edition with same problem. PLease help, its driving me crazy.

[On page 72]("http://ubuntuforums.org/showthread.php?p=10285200#post10285200") of this thread I posted how to calibrate in the terminal.

---

### Post by messinwu on 2011-01-23
Hmm, well, the script I posted above was working fine for several boots, but now it doesn't seem to work now.  It rotates the screen, but not the touch.  I suspect it has something to do with the xinput ID's changing randomly.  I also don't really know what the script is doing, most of that is over my head.  With that logic, it'll work again randomly, but of course that isn't what we need.  Sorry guys.

floyd - I looked at the magic thing you mentioned, but it seems to react to that tablet's input event provided when the swivel screen is turned.  Ours doesn't provide any event it seems, so that won't work.  This did give me a crazy thought, I remember I had a Samsung Instinct phone which had an auto rotate feature which used the built-in camera to determine whether the phone was rotated abruptly.  I don't really think that would work well for this device, though....  Just thought I'd throw that out there in case someone wants to do something with it.

Also, I wanted to mention that I followed the directions on how to make the webcam display right side up, but after compiling and doing the make install, after reboot, my image is still upside down.  So, I'm wondering if this model also has a different webcam installed...??

---

### Post by messinwu on 2011-01-23
Okay, I think I figured out why that script wasn't working.  The top of the script references 9 and 10, which are the xinput ID's.  It worked sometimes because sometimes 10 was correct.  If you remember in my first post, I said seems to rotate between 10, 11, and 16 to be the correct one to rotate the touchscreen.  So... I changed that line in the script to include those three numbers.  Now it seems to work fine... so far.

I've attached the script to this post, for your usage if you want it.  You'd just need to make it executable, chmod 755 ./rotate.sh

Here's the script contents:

```
#!/bin/bash

rangex=( 0 3478 )
rangey=( 0 3478 )
torotate=( 10 11 16 )

xrandrout="$(xrandr)"

case $xrandrout in
 *600x1024* ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
 *1024x600* ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
esac

xrandr -o $(( rotate * 3 ))
for input in ${torotate[@]}; do
 xinput set-prop $input "Evdev Axes Swap" $rotate
 xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
 xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}

done
```

---

### Post by messinwu on 2011-01-23
Now.... can anyone help get my rotate button (ExpressGate) working?  I'd like to link that button to this rotate.sh script.  Currently, I just set up a custom application launcher in gnome on the bottom panel.

I guess I'm assuming Ubuntu forum members are equally helpful as the Fedora forums usually are...  ;)

---

### Post by messinwu on 2011-01-23
Just confirming that this "newer" version of the T101MT also has a different version of webcam in it.  According to a post on page 73 of this post, lsusb says the webcam is:

**Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam** and appears in xinput as: **USB2.0 UVC VGA WebCam**

Whereas in the newer version of T101MT, the webcam shows up as:

**Bus 001 Device 003: ID 13d3:5126 IMC Networks** and appears in xinput as: **USB 2.0 PC Cam**

Perhaps this is why the webcam image is still upside down in Cheese even after updating the module as instructed.  I don't know enough to fix this, but I'm just including my findings here so that someone more knowledgeable can look into it perhaps....

---

### Post by ianni67 on 2011-01-24
> **floyd0815 said:**
> Only 2 fingers? Doh!
...

What exactly can Two-Fing do? Only switching between the desktops?
 Sorry for answering so late.
With two-fing we can also open the right-click menu.

I could not find a way to activate a launcher with the alt button pressed, so (as you said) it seems to be hard to implement my suggestion to use a launcher to activate/deactivate the alt key. I'm stuck.

---

### Post by floyd0815 on 2011-01-24
> **ianni67 said:**
> Sorry for answering so late.
I could not find a way to activate a launcher with the alt button pressed, so (as you said) it seems to be hard to implement my suggestion to use a launcher to activate/deactivate the alt key. I'm stuck.
Sorry to hear that!
As an alternative, you can activate ALT for a certain time (command in a post before) and CTRL for a specific window (like Nautilus).

EDIT:
Is it possible to load another config file into two-fing e.g. remap double-tap to a command instead of the context menu?
If so, you could try the command alt+f7 to trigger window-move.

---

### Post by messinwu on 2011-01-24
Okay, I have an updated rotate.sh script.  It may not be the cleanest code, but this monitors output from acpi_listen and when it receives the code for the ExpressGate button, it executes the rotate script I previously posted.

Outcome:  When the ExpressGate button is pressed, the screen rotates.  If pressed again, it'll rotate back to normal view.  This is what we expect, as I believe this is the behavior we get in Windows.  Actually, I think Windows makes you hold the button down for 5 seconds or something, weird.

Just download the attached script, and call it to start at boot time using the 'Startup Applications" setting in System --> Preferences.

If anyone wants to clean up the code or streamline it in some way, that would be fine.  For now, this works.

```
#!/bin/bash


acpi=$(acpi_listen -c 1)

echo $acpi > acpi.txt

if grep -q 0000007b acpi.txt; then
rangex=( 0 3478 )
rangey=( 0 3478 )
torotate=( 10 11 16 )

xrandrout="$(xrandr)"

case $xrandrout in
 *600x1024* ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
 *1024x600* ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
esac

xrandr -o $(( rotate * 3 ))
for input in ${torotate[@]}; do
 xinput set-prop $input "Evdev Axes Swap" $rotate
 xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
 xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}

done
	bash rotate.sh
else 
	bash rotate.sh
exit; fi;
```

---

### Post by miegiel on 2011-01-24
> **messinwu said:**
> Okay, I have an updated rotate.sh script.  It may not be the cleanest code, but this monitors output from acpi_listen and when it receives the code for the ExpressGate button, it executes the rotate script I previously posted.

Outcome:  When the ExpressGate button is pressed, the screen rotates.  If pressed again, it'll rotate back to normal view.  This is what we expect, as I believe this is the behavior we get in Windows.  Actually, I think Windows makes you hold the button down for 5 seconds or something, weird.

Just download the attached script, and call it to start at boot time using the 'Startup Applications" setting in System --> Preferences.

If anyone wants to clean up the code or streamline it in some way, that would be fine.  For now, this works.

...

Here you go :)
```
[COLOR="SeaGreen"]#!/bin/bash
#

if acpi_listen -c 1 | grep -q 0000007b[/COLOR]; then
rangex=( 0 3478 )
rangey=( 0 3478 )
torotate=( 10 11 16 )

xrandrout="$(xrandr)"

case $xrandrout in
 *600x1024* ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
 *1024x600* ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
esac

xrandr -o $(( rotate * 3 ))
for input in ${torotate[@]}; do
 xinput set-prop $input "Evdev Axes Swap" $rotate
 xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
 xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}

[COLOR="Red"]done
	bash rotate.sh
else 
	bash rotate.sh[/COLOR]
exit; fi;
```

The green part should help you avoid using the *acpi.txt* file (good call on using the -q switch for grep).

I'm no hero in this stuff either, but the red part worries me. Won't that make the script start itself in itself repeatedly?

As for microsoft putting a 5s delay on the button. That makes sense to me, I continuously press the button by accident.

---

### Post by messinwu on 2011-01-25
miegiel - thanks for that!  I'm not using my eeepc at the moment so I can't test it, but it looks like it should work.  I'm not really a coder, I just hack through what I want to do and use Google extensively looking for bash commands and statements to do what I want.  It takes me a very long time, and I can't take credit for the '-q' switch, that was just part of something I stole from somewhere.

I know the red parts look bad, but without them, because of the "-c 1" switch of acpi_listen, the script would otherwise die as soon as acpi_listen gets anything at all.  So, I made it re-execute itself after it gets something, since it was going to die right away otherwise.

I'm sure there's a better way, maybe by using a FOR or WHILE statement, but again, I just don't have that much knowledge.

Also, I'm using the "2nd Gen" version of the T101MT on Ubuntu 10.10.  I think I read somewhere that other linux users experience the laptop going to sleep when the ExpressGate button is pressed, whereas in my installation, absolutely nothing happened.  So, I'm not sure if this script is for everyone.  I mean, "1st Gen" T101MT's can use the 'rotatetouch' command whereas the 2nd Gen can't due to the screen being different hardware.

Also, at least in my installation, the scripts in /etc/acpi/events have no effect at all (I think that's where they are).

---

### Post by messinwu on 2011-01-25
More information regarding this new "**0486:0186 ASUS Computers, Inc.**" screen in the "2nd Gen" T101MT.  I found the following link which describes how to build an updated USBHID driver to support this panel, and supposedly multi-touch, but I haven't gotten it to do that yet.  However, this does eliminate the need to use the "modprobe usbhid quirks" hack to get this touchscreen to work.  After this driver is built and installed per the simple instructions, it just works.  And there's only one instance of "AsusTek, Inc. MultiTouch(TTI)" in xinput.

Here's the link:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)

So, this screen appears to be made by Enac, they call it a MosArt model or series.

---

### Post by miegiel on 2011-01-25
> **messinwu said:**
> ...

Also, I'm using the "2nd Gen" version of the T101MT on Ubuntu 10.10.  I think I read somewhere that other linux users experience the laptop going to sleep when the ExpressGate button is pressed, whereas in my installation, absolutely nothing happened.  So, I'm not sure if this script is for everyone.  I mean, "1st Gen" T101MT's can use the 'rotatetouch' command whereas the 2nd Gen can't due to the screen being different hardware.

...

I've got the (1st gen) "eGalax Inc. USB TouchController" and the script works here too. Though it does wreck my calibration. I guess a rotate script for the older T101MT's should look something like this:
```
#!/bin/bash
#

if acpi_listen -c 1 | grep -q 0000007b
	then
		touchrotate toright
	done
		bash rotate.sh
	else 
		bash rotate.sh
exit; fi;
```

---

### Post by miegiel on 2011-01-25
> **messinwu said:**
> ...

Also, at least in my installation, the scripts in /etc/acpi/events have no effect at all (I think that's where they are).
Curiosity invoked the *cat* :lolflag:
```
user@machine:~$ cat /etc/acpi/events
cat: /etc/acpi/events: Is a directory
```
ok, ok, it's not a file :roll:
```
user@machine:~$ ls -al /etc/acpi/events
total 136
drwxr-xr-x 2 root root 4096 2011-01-07 16:10 .
drwxr-xr-x 3 root root 4096 2011-01-07 16:10 ..
-rw-r--r-- 1 root root  116 2010-06-23 04:36 ac
-rw-r--r-- 1 root root   85 2010-06-23 04:36 asus-brightness-down
-rw-r--r-- 1 root root   83 2010-06-23 04:36 asus-brightness-up
-rw-r--r-- 1 root root  239 2010-06-23 04:36 asus-f8sv-touchpad
-rw-r--r-- 1 root root  217 2010-06-23 04:36 asus-media-eject
-rw-r--r-- 1 root root  215 2010-06-23 04:36 asus-rotate
-rw-r--r-- 1 root root  238 2010-06-23 04:36 **[COLOR="Red"]asus-touchpad[/COLOR]**
-rw-r--r-- 1 root root  155 2010-06-23 04:36 asus-video
-rw-r--r-- 1 root root   73 2010-06-23 04:36 asus-wireless-off
-rw-r--r-- 1 root root   72 2010-06-23 04:36 asus-wireless-on
-rw-r--r-- 1 root root  126 2010-06-23 04:36 battery
-rw-r--r-- 1 root root  223 2010-06-23 04:36 ibm-wireless
-rw-r--r-- 1 root root  279 2010-06-23 04:36 lenovo-touchpad
-rw-r--r-- 1 root root   67 2010-06-23 04:36 lenovo-undock
-rw-r--r-- 1 root root  118 2010-06-23 04:36 lidbtn
-rw-r--r-- 1 root root  218 2010-06-23 04:36 panasonic-lockbtn
-rw-r--r-- 1 root root  423 2010-06-27 14:41 powerbtn
-rw-r--r-- 1 root root  315 2010-06-23 04:36 sleepbtn
-rw-r--r-- 1 root root  277 2010-06-23 04:36 thinkpad-cmos
-rw-r--r-- 1 root root   68 2010-06-23 04:36 tosh-battery
-rw-r--r-- 1 root root   70 2010-06-23 04:36 tosh-hibernate
-rw-r--r-- 1 root root   66 2010-06-23 04:36 tosh-ibutton
-rw-r--r-- 1 root root   66 2010-06-23 04:36 tosh-lock
-rw-r--r-- 1 root root   65 2010-06-23 04:36 tosh-mail
-rw-r--r-- 1 root root   66 2010-06-23 04:36 tosh-media
-rw-r--r-- 1 root root   65 2010-06-23 04:36 tosh-next
-rw-r--r-- 1 root root   65 2010-06-23 04:36 tosh-play
-rw-r--r-- 1 root root   65 2010-06-23 04:36 tosh-prev
-rw-r--r-- 1 root root   65 2010-06-23 04:36 tosh-stop
-rw-r--r-- 1 root root  222 2010-06-23 04:36 tosh-wireless
-rw-r--r-- 1 root root   64 2010-06-23 04:36 tosh-www
-rw-r--r-- 1 root root   80 2010-06-23 04:36 videobtn
```
Hmmm, interesting file there.
```
user@machine:~$ cat /etc/acpi/events/asus-rotate 
# /etc/acpi/events/asus-rotate
# This is called when the user rotates the screen to/from tablet mode, or
# when "rotate screen" button is pressed.

event=hotkey (ATKD|HOTK) **[COLOR="red"]0000009b[/COLOR]**
action=**[COLOR="red"]/etc/acpi/rotatescreen.sh[/COLOR]**
```
I think I already know what will hapen if I change that *0000009b* to *0000007b* :twisted:
```
user@machine:~$ /etc/acpi/rotatescreen.sh
Couldn't get a file descriptor referring to the console
Can't open display :
```
How disappointing. Still, let's have a look at that */etc/acpi/rotatescreen.sh* script.
```
user@machine:~$ cat /etc/acpi/rotatescreen.sh
#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
	right)
	NEW_ROTATION="normal"
	;;
	*)
	NEW_ROTATION="right"
	;;
esac

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
	fi
done
```
Intresting, could be usefull at some point.
```
user@machine:~$ cat /etc/acpi/events/* | grep 0000007b
```
Great, no output. It seems none of the files in */etc/acpi/events/* listens to *0000007b* (the ExpressGate/rotate button). I guess it's safe to edit */etc/acpi/events/asus-rotate* and change *0000009b* to *0000007b* and point it to a script that does something more effective than */etc/acpi/rotatescreen.sh*

Edited */etc/acpi/events/asus-rotate* :
```
# /etc/acpi/events/asus-rotate
# This is called when the user rotates the screen to/from tablet mode, or
# when "rotate screen" button is pressed.

event=hotkey (ATKD|HOTK) 0000007b
action=/usr/bin/gedit
```
Just linking it to *gedit* for fun ;)

*mutters* It doesn't work. Maybe I need to reboot first. brb

Bah, it still doesn't work. :(

Digging a little deeper and taking a look a the brightness keys.

/etc/acpi/events/asus-brightness-up 
```
event=hotkey (ATKD|HOTK) 0000001[0123456789abcdef]
action=/etc/acpi/asus-brn-up.sh
```
/etc/acpi/events/asus-brightness-down 
```
event=hotkey (ATKD|HOTK) 0000002[0123456789abcdef]
action=/etc/acpi/asus-brn-down.sh
```

brightness from max to min
```
user@machine:~$ acpi_listen -c 8
hotkey ATKD 0000002e 00000002
hotkey ATKD 0000002c 00000002
hotkey ATKD 0000002a 00000002
hotkey ATKD 00000028 00000006
hotkey ATKD 00000026 00000001
hotkey ATKD 00000024 00000001
hotkey ATKD 00000022 00000001
hotkey ATKD 00000020 00000001
```
brightness from min to max
```
user@machine:~$ acpi_listen -c 8
hotkey ATKD 00000021 00000002
hotkey ATKD 00000023 00000002
hotkey ATKD 00000025 00000002
hotkey ATKD 00000027 00000002
hotkey ATKD 00000029 00000002
hotkey ATKD 0000002b 00000002
hotkey ATKD 0000002d 00000002
hotkey ATKD 0000002f 00000008
```
Ok, I guess things are a bit more complicated. *0000001[0123456789abcdef]* doesn't seem to relate to the *hotkey ATKD 0000002x* output of *acpi_listen* when turning up the brightness.

I'm giving it a rest for now, got other stuff to do.

---

### Post by messinwu on 2011-01-25
Yeah, that's what I meant.... none of those events actually do anything.  I mean, you can try to switch around the codes for say, volume and brightness, which theoretically should switch the two keys around, but even after reboot, nothing behaves differently.  I think the eeepc-acpi-workaround originally installed from the Ubuntu T101MT instruction page is overriding those events completely.  Just my theory.

That's why I had to create the script using acpi_listen.  Other than dmesg, it's the only way I got any output when pressing the ExpressGate button.

Now that I've got the "official" driver working for this screen, I've been playing around with following other instructions on that website to patch xorg, and played around with multitouchd and multitouchctl, but not having any luck getting multi-touch yet.

However, I followed some instructions on this site:
[http://txzone.net/2010/10/joojoo-and-multitouch-on-ubuntu-10-10/](http://txzone.net/2010/10/joojoo-and-multitouch-on-ubuntu-10-10/)

...starting with the PYMT section, changed the input thing to /dev/input/event6 and the full-screen demo does allow me to perform two-finger touch activity, ya know, two lines being drawn on the screen at the same time.  So... multitouch is possible, but it's not working for anything outside of that python script.

I guess if you already have multi-touch working with the "1st Gen" model, you don't care much about that last paragraph.  :)

---

### Post by Slartius on 2011-01-26
Thanks for the rotate code. I did some optimization and did some testing. For me, the devices 11 and 16 are of other type (WebCam and nonexistent), so they might be changed and omitted but that probably depends on the version of the computer. I  included infinite loop for a cleaner look and some pruning of output of some commands. 

Again thanks, messinwu. 

So here is a bit altered code:
 
#!/bin/bash

while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
    rangex=( 0 3478 )
    rangey=( 0 3478 )
    torotate=( 10 11 16 )
    
    xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
    case $xrandrout in
        600x1024 ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
        1024x600 ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
    esac

    xrandr -o $(( rotate * 3 ))
    for input in ${torotate[@]}
    do
        xinput set-prop $input "Evdev Axes Swap" $rotate
        xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
        xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
    done
    else
    echo $acpi
    fi
done

---

### Post by Slartius on 2011-01-26
In regard to my previous message, I noticed, that my cursor using the touch screen was quite off, which happened due to a wrong calibration. I had to change it for my screen to work properly. I had to change the lines 
rangex=( 0 3478 )
    rangey=( 0 3478 )
to
rangex=( 0 4095 )
    rangey=( 0 4095 )
which are apparently my minimum and maximum x and y values 
according to xinput_callibrator and it now works fine. 

[[COLOR=#980101][/COLOR]]("https://github.com/downloads/tias/xinput_calibrator/xinput-calibrator_0.7.5-1ubuntu1_i386.deb")

---

### Post by messinwu on 2011-01-26
slartius - thanks for optimizing the script, I knew someone could do much better.  As for the device ID's, I knew they were calling irrelevant ones sometimes, but as I mentioned previously, mine kept changing, and I had two instances of the multi-touch screen in xinput list.  However, since I installed the official driver for this screen from Enac, I only have one instance and it's always device ID 10.  Yay.  Still haven't got any multi-touch working for gnome though.

I got the x and y values from command 'xinput list --long'.  Here's the relevant text I get from that file"

```
&#9116;   &#8627; AsusTek, Inc. MultiTouch(TTI)           	id=10	[slave  pointer  (2)]
	Reporting 9 classes:
		Class originated from: 10
		Buttons supported: 7
		Button labels: Button Unknown Button Unknown Button Unknown Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right
		Button state:
		Class originated from: 10
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2132.000000
		Class originated from: 10
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2072.000000
		Class originated from: 10
		Detail for Valuator 2:
		  Label: Abs Pressure
		  Range: 0.000000 - 255.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 10
		Detail for Valuator 3:
		  Label: Abs Misc
		  Range: 0.000000 - 1.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 10
		Detail for Valuator 4:
		  Label: Abs MT Position X
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2132.000000
		Class originated from: 10
		Detail for Valuator 5:
		  Label: Abs MT Position Y
		  Range: 0.000000 - 3478.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2072.000000
		Class originated from: 10
		Detail for Valuator 6:
		  Label: Abs MT Tracking ID
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 10
		Detail for Valuator 7:
		  Label: None
		  Range: 0.000000 - 255.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
```

You'll notice the 'Abs X' and 'Abs Y' values of 3478.  Maybe they're different for the "1st Gen" model's screen.

---

### Post by Slartius on 2011-01-27
> You'll notice the 'Abs X' and 'Abs Y' values of 3478.  Maybe they're different for the "1st Gen" model's screen.You are right. For my screen the range is from 0 to 4095 in both directions. Seems some additional rewrite of the code should be done for this to work in all cases. Thanks for the tip.

---

### Post by Slartius on 2011-01-27
> **Slartius said:**
> You are right. For my screen the range is from 0 to 4095 in both directions. Seems some additional rewrite of the code should be done for this to work in all cases. Thanks for the tip.

In reply to my message, here is the rewrite which should work in ?most? cases. I also added checking for the eGalax device id just in case it is somewhere else.

And the code (could be somewhat optimized especially checking the calibration values) :
```
#!/bin/bash
devId=`xinput list | grep eGalax | sed -e 's/.*id=//' | cut -c -3 | sed -e 's/ *//g'`
rangex=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]X" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
rangey=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]Y" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
    torotate=( $devId ) 
    xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
    case $xrandrout in
        600x1024 ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
        1024x600 ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
    esac

    xrandr -o $(( rotate * 3 ))
    for input in ${torotate[@]}
    do
        xinput set-prop $input "Evdev Axes Swap" $rotate
        xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
        xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
    done
    fi
done

```

---

### Post by messinwu on 2011-01-27
Hey this script is looking better and better.  However, in continuing the effort to support rotation for both screens, there has to be something in place to identify the device ID for the 'AsusTek' device.  

Currently, the script looks for the line with eGalax in it.  However, with the 2nd Gen screen, it needs to also look for 'AsusTek'.  

I altered that first line and executed just that line in the command line:

```
xinput list | grep AsusTek | sed -e 's/.*id=//' | cut -c -3 | sed -e 's/ *//g'
```

result is:  ```
9	[
```

However, this code works:
```
xinput list | grep AsusTek | awk -F' ' '{print $6}' | cut -c4
```

Yeah, my Device ID for my screen changed to 9 since I decided last night to try the latest upstream kernel, 2.6.38-r2.

I've noticed now when running this newest kernel, lsmod is loading 'hid_mosart'.  Also, running multitouchd daemon is more promising, providing me two mouse cursers and the ability to drag a window and punch in numbers on the calculator at the same time.  So, multitouch works that way, but I have no idea how to zoom in EOG or resize windows using two fingers yet.

---

### Post by Slartius on 2011-01-28
> **messinwu said:**
> Hey this script is looking better and better.  However, in continuing the effort to support rotation for both screens, there has to be something in place to identify the device ID for the 'AsusTek' device.  

Currently, the script looks for the line with eGalax in it.  However, with the 2nd Gen screen, it needs to also look for 'AsusTek'.  

I altered that first line and executed just that line in the command line:

```
xinput list | grep AsusTek | sed -e 's/.*id=//' | cut -c -3 | sed -e 's/ *//g'
```result is:  ```
9    [
```However, this code works:
```
xinput list | grep AsusTek | awk -F' ' '{print $6}' | cut -c4
```Yeah, my Device ID for my screen changed to 9 since I decided last night to try the latest upstream kernel, 2.6.38-r2.


You are quite right, it is my mistake. In order to cover all possible cases I also imagined, that there could be more than 99 devices ](*,) hence there is -3, indicating that 3 characters should be taken for the device id. Unfortunately, there are tabs so the code for that line should be:

```

devId=`xinput list | grep eGalax | sed -e 's/.*id=//' -e 's/[\t ].*//g'`

```Could you post what is the output of your xinput list command (whole line) for your touchscreen device.

---

### Post by Slartius on 2011-01-28
> **Slartius said:**
> 

```

devId=`xinput list | grep eGalax | sed -e 's/.*id=//' -e 's/[\t ].*//g'`

```Could you post what is the output of your xinput list command (whole line) for your touchscreen device.

Actually it would probably also work with the following command (well it works for my touchscreen):
```
devId=`xinput list | grep "eGalax\|AsusTek" | sed -e 's/.*id=//' -e 's/[\t ].*//g'`

```asuming that the names are eGalax and AsusTek.

---

### Post by messinwu on 2011-01-28
Okay!  Sorry it took me a bit to answer with my xinput list output, but it looks like it doesn't matter anymore.  That last query echoed the correct device ID also.  So, here's our new code for rotate.sh

```
#!/bin/bash
devId=`xinput list | grep "eGalax\|AsusTek" | sed -e 's/.*id=//' -e 's/[\t ].*//g'`
rangex=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]X" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
rangey=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]Y" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
    torotate=( $devId ) 
    xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
    case $xrandrout in
        600x1024 ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
        1024x600 ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
    esac

    xrandr -o $(( rotate * 3 ))
    for input in ${torotate[@]}
    do
        xinput set-prop $input "Evdev Axes Swap" $rotate
        xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
        xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
    done
    fi
done
```

---

### Post by messinwu on 2011-01-28
One more potential issue.  I compiled the official driver for this screen from Enac, so I only have one instance of the screen in xinput list.  However, when someone does this code recommended on the "official" guide:

```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
```

... then there are TWO instances of "AsusTek, Inc. MultiTouch(TTI)" in xinput list.  If you read back, you'll see that the "correct" one to use to rotate the screen continually changed at random.  So, my first script just applied the rotate code to both device ID's.  It was crude, but it worked.

But will this script work for that situation now?  I ran the query on a text file with two instances of the AsusTek screen listed, and it outputted both device ID's.  I just don't know if those variables will be passed correctly.

I'd like someone who's running the "2nd Gen" screen with a lsusb ID of 0486:0186 to execute this rotate.sh script to see if it properly rotates your screen by pressing the rotate "ExpressGate" button.

---

### Post by Slartius on 2011-01-29
> **messinwu said:**
> One more potential issue.  I compiled the official driver for this screen from Enac, so I only have one instance of the screen in xinput list.  However, when someone does this code recommended on the "official" guide:

```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
```... then there are TWO instances of "AsusTek, Inc. MultiTouch(TTI)" in xinput list.  If you read back, you'll see that the "correct" one to use to rotate the screen continually changed at random.  So, my first script just applied the rotate code to both device ID's.  It was crude, but it worked.

But will this script work for that situation now?  I ran the query on a text file with two instances of the AsusTek screen listed, and it outputted both device ID's.  I just don't know if those variables will be passed correctly.

I'd like someone who's running the "2nd Gen" screen with a lsusb ID of 0486:0186 to execute this rotate.sh script to see if it properly rotates your screen by pressing the rotate "ExpressGate" button.

Not to jump to conclusion too quickly, but yes, I'd say it should work. If there are more than one device that match the regexp in grep, then those lines are each processed and for each line the result is returned and stored in the devId. This is then transformed into an array torotate (which can hold more than one value, actually all this could be also done without arrays) and finally for statement loops through all values in the array and does necessary steps for all id's stored in the torotate.

---

### Post by Slartius on 2011-01-29
In addition to previous message, does anybody know all the possible touchscreen devices and their names. Namely, on page 28 of this thread I saw also another touchscreen device (I guess it is from the T101TM). The device according to xinput: 
EVTouch TouchScreen. 
Maybe if all devices have some common string like TouchScreen than we could make it quite general for all touchscreens.

---

### Post by Plippo on 2011-01-29
> **floyd0815 said:**
> 
Is it possible to load another config file into two-fing e.g. remap double-tap to a command instead of the context menu?
If so, you could try the command alt+f7 to trigger window-move.

Sorry for not writing for such a long time. Currently there is no config file for twofing, but you can simply modify the file profiles.h and compile twofing again.

In this file, you find different "sections" with profiles for different applications. At the bottom, you find the "defaultProfile" which is used for most applications. To perform a different action on two-finger drag, you can try changing it as follows (haven't tested it, but it should work):
```

Profile defaultProfile = {    .windowClass = NULL,
                .scrollInherit = 0,
                .hscrollStep = 40,
                .vscrollStep = 40,
                .scrollMinDistance = 50,
[B]                .scrollBraceAction = { ACTIONTYPE_BUTTONPRESS,1,MODIFIER_ALT },
                .scrollUpAction = { ACTIONTYPE_NONE, 0, 0 },
                .scrollDownAction = { ACTIONTYPE_NONE, 0, 0 },
                .scrollLeftAction = { ACTIONTYPE_NONE, 0, 0 },
                .scrollRightAction = { ACTIONTYPE_NONE, 0, 0 },
                .scrollEasing = 0,[/B]
                .zoomInherit = 0,
                .zoomMinDistance = 80,
                .zoomInAction = { ACTIONTYPE_BUTTONPRESS, 4, MODIFIER_CONTROL },
                .zoomOutAction = { ACTIONTYPE_BUTTONPRESS, 5, MODIFIER_CONTROL },
                .zoomStep = 1.5,
                .rotateInherit = 0,
                .rotateMinDistance = 10000,
                .rotateMinAngle = 370,
                .rotateLeftAction = { ACTIONTYPE_NONE,0,0 },
                .rotateRightAction = { ACTIONTYPE_NONE,0,0 },
                .rotateStep = 90,
                .tapInherit = 0,
                .tapAction = { ACTIONTYPE_BUTTONPRESS, 3, 0    }
              };

```Using double-tap without dragging to right-click should still work.

---

### Post by Plippo on 2011-01-29
I just updated the wiki with the information that you no longer need to install the kernel driver in Maverick (yeah!). Sorry it took so long until the patch reached the upstream kernel.

As it occurred a few times in this thread, I also added a note about the "wild cursor problem" on the touchpad.

---

### Post by messinwu on 2011-01-29
Please pardon my ignorance, but can someone explain what twofing does exactly?  From everything I've read, I'm still unsure if it's to provide two-finger zoom/rotate for the touchpad or the touchscreen.  

Also, is it the same as doing:
> sudo apt-get install eeepc-touchpad-twofingers

---

### Post by coffen on 2011-01-29
> **messinwu said:**
> One more potential issue.  I compiled the official driver for this screen from Enac, so I only have one instance of the screen in xinput list.  However, when someone does this code recommended on the "official" guide:

```
sudo rmmod usbhid
sudo rmmod hid
sudo modprobe hid
sudo modprobe usbhid quirks=0x0486:0x0186:0x0040
```

... then there are TWO instances of "AsusTek, Inc. MultiTouch(TTI)" in xinput list.  If you read back, you'll see that the "correct" one to use to rotate the screen continually changed at random.  So, my first script just applied the rotate code to both device ID's.  It was crude, but it worked.

But will this script work for that situation now?  I ran the query on a text file with two instances of the AsusTek screen listed, and it outputted both device ID's.  I just don't know if those variables will be passed correctly.

I'd like someone who's running the "2nd Gen" screen with a lsusb ID of 0486:0186 to execute this rotate.sh script to see if it properly rotates your screen by pressing the rotate "ExpressGate" button.

Nice script - works like a charm.
Would be nice though to be able to rotate the screen, say clockwise every time the rotate button is pressed.

I also noted that the script rotates the touchscreen only - not the touchpad

---

### Post by messinwu on 2011-01-29
Hey coffen

I would tend to mostly agree with you about rotating clockwise the next step each time the button is pressed.  But on the other hand, I like it with just the two orientations just fine.  So, if someone has the ability to make that change, go right ahead.

I did find a patch to enable rotation of the touchpad a while back, but I don't think it would be of much use for this device, since the screen IS the touchpad, since it's a touchscreen.

If you're REALLY interested in this feature, I can dig up that patch and give you some basic instructions on how to integrate it into the rotate.sh script if you really want that.

---

### Post by coffen on 2011-01-30
I simplified the script by calling Plippos touchrotate from it.
This way you can have the screen to rotate clockwise each time the button is pressed.
```

#!/bin/bash
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
      touchrotate toright
    fi
done
```

I like this behaviour since I usually want to have the device upside down as a tablet.
Now I simply press the button twice to get the screen upside down :)

I was also thinking of implementing a delay (like in Windoze) to prevent accidentally rotaing the device.
I'll post back if I decide to do that.

---

### Post by messinwu on 2011-01-30
Hey coffen

Well yes, you could simplify it that way.  However, the top portion declaring values for devId, rangex, and rangey would be irrelevant in that script, since you're using the touchrotate script to rotate your screen.

However, I disagree with this method for three reasons.  I don't like having to call another script from with a script.  Secondly, it won't work with the "2nd Gen" T101MT's screen unless the official driver or upstream kernel are used.  Third, I'm not sure the package which provides touchrotate is available for other distributions, like Fedora.  The script, as it was written, required nothing else to be installed and should be distribution independent.  

I do believe we could change the script to continuously rotate to the right each time the button is pressed, I'm just not sure how at the moment.  I'm really not sure how to make the button have to be held down for a few seconds before executing though.  I'm sure it's possible, but I've never had any issue with accidentally pushing it, ever.

Also, you mentioned you like to press the button to rotate twice so you can use it like a tablet upside down.  Why not just convert the screen to tablet mode (physically convert to tablet), and then physically rotate the whole device in your hands?  That way, only two orientations would be needed.  I guess I just don't understand why having the screen rotated upside down would be different from physically rotating the entire device upside down.

Looking forward to your further input...

---

### Post by messinwu on 2011-01-30
> **Slartius said:**
> In addition to previous message, does anybody know all the possible touchscreen devices and their names. Namely, on page 28 of this thread I saw also another touchscreen device (I guess it is from the T101TM). The device according to xinput: 
EVTouch TouchScreen. 
Maybe if all devices have some common string like TouchScreen than we could make it quite general for all touchscreens.

I think that user either had the wrong driver loaded somehow, or the device is not a T101MT.  I believe the only two screens in use are the eGalax and the AsusTek ones.

---

### Post by coffen on 2011-01-30
> **messinwu said:**
> Hey coffen
Well yes, you could simplify it that way.  However, the top portion declaring values for devId, rangex, and rangey would be irrelevant in that script, since you're using the touchrotate script to rotate your screen.
Yes, I noticed that myself. Those lines are obsolete.:redface:

> **messinwu said:**
> 
However, I disagree with this method for three reasons. I don't like having to call another script from with a script. Secondly, it won't work with the "2nd Gen" T101MT's screen unless the official driver or upstream kernel are used. Third, I'm not sure the package which provides touchrotate is available for other distributions, like Fedora. The script, as it was written, required nothing else to be installed and should be distribution independent.
Calling scripts from within other scripts is done all the time in Ubuntus own scripts. I don't find that odd at all, but everyone is entitled their own opinion :)
About other distros - I do believe this is an Ubuntu forum.

> **messinwu said:**
> 
I'm really not sure how to make the button have to be held down for a few seconds before executing though.  I'm sure it's possible, but I've never had any issue with accidentally pushing it, ever.
I think this could be done with adding a sleep command to the script and the checking if the aspi code is still active after the sleep time.

> **messinwu said:**
> 
I guess I just don't understand why having the screen rotated upside down would be different from physically rotating the entire device upside down.
What I mean is I like to use the device in tablet mode with the screen upside down, i.e with the hinge at the top. It is better balanced in my hand that way. For that the screen needs to be rotated twice or inverted.

Anyway, the original script works more than fine and I appreciate the work you put into it.
I just like to have 4 different orientations instead of 2.

---

### Post by messinwu on 2011-01-30
Yikes, that last post gives me a bad feeling.  I think I'll come back to modifying the rotate.sh script a little later.

I did answer my own question from yesterday regarding 'twofing'.  It's a script which provide multi-touch to the touchscreen (Yay!).  So now I know - it wasn't obvious to me since I have the "2nd Gen" screen, which originally needed the modprobe quirks thing to make it work, but that prohibited the twofing script from working.  

Anyway, to help people going forward, in order to make the twofing script work, to provide multi-touch capability for your AsusTek "2nd Gen" screen, you have to do the following:

1.  Install the proper driver from ENAC or compile an upstream kernel which has the driver built-in.

2.  After you've downloaded twofing, after running 'make', but before running 'make install', you need to open the file called **70-touchscreen-egalax.rules**, find where it says **480d** and change it to **0186**.

3.  Execute the 'sudo make install' command and follow the other instructions about adding 'twofing --wait' to start when gnome starts.

Regarding above, instructions on how to get the proper driver can be found here:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html) 

Instructions on how to compile an upstream kernel can be found here:   [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)



I'm just working very hard to make linux work properly and provide full functionality on this device.  I've always been more of a taker in the past, so now I'm trying to give back a little I guess.

Another issue I have to figure out is the webcam.  It's upside down.  The fix of re-comipling v4linux or whatever it is to make it right-side-up does not work for me.  I think it's because this "2nd Gen" webcam is different from the "1st Gen" version.  If someone is willing to work with me to figure this out, that would be great.  I'm guessing it's just a matter of referencing the correct device ID.  lsusb says this webcam is "13d3:5126".

---

### Post by messinwu on 2011-01-30
Okay, got the delay on the Rotate (ExpressGate) button thing figured out.  Was very easy afterall.  The output of acpi_listen seems to add a letter (c-z) for each second the button is held down.  

So, just change 0000007b in the script to **0000007c**.  That way, it won't rotate immediately, but you'd have to purposely be holding the button for about 1.5 seconds it seems.  If you find that's not quite long enough, then make it 0000007d or 0000007e.

Is that what you guys wanted?

---

### Post by beastrace91 on 2011-01-30
If anyone is interested, I'm a developer for [Bodhi Linux]("http://bodhilinux.com/") and I own an Asus T101MT and we have a "tablet" profile that is optimized for devices such as the t101mt. Has a nice on screen keyboard and other things that are helpful on small/touch screens -

[img]http://i.imgur.com/6j7l2.png[/img]

~Jeff

---

### Post by messinwu on 2011-01-30
Wow, that keyboard looks nice.  Is there a way to install it in Ubuntu?

---

### Post by miegiel on 2011-01-30
> **messinwu said:**
> Okay, got the delay on the Rotate (ExpressGate) button thing figured out.  Was very easy afterall.  The output of acpi_listen seems to add a letter (c-z) for each second the button is held down.  

So, just change 0000007b in the script to **0000007c**.  That way, it won't rotate immediately, but you'd have to purposely be holding the button for about 1.5 seconds it seems.  If you find that's not quite long enough, then make it 0000007d or 0000007e.

Is that what you guys wanted?

Not exactly it seems ;) but you made an interesting observation. What I get is:
[LIST]
[*]hotkey ATKD 0000007b 00000xxx when the rotate button is pressed
[*]hotkey ATKD 0000007c 00000xxx when the rotate button is held
[*]hotkey ATKD 0000007d 00000xxx when the rotate button is released
[/LIST]

However, using the timeout switch *-t*, if I hold the button for more than 3 seconds, I get this output:
```
user@machine:~$ acpi_listen -t 3
hotkey ATKD 0000007b 0000003a
hotkey ATKD 0000007c 00000068
hotkey ATKD 0000007c 00000069
hotkey ATKD 0000007c 0000006a
```
Notice there is no *0000007d* value!

And holding the button but letting it go before it times out I get:
```
user@machine:~$ acpi_listen -t 3
hotkey ATKD 0000007b 0000003c
hotkey ATKD 0000007c 0000006d
hotkey ATKD [COLOR="Red"]0000007d[/COLOR] 0000003a
```

I tried incorporating it in the script but couldn't make it work. :sad: Still, it might inspire someone.

**Slartius** or **coffen**, can you explain your script to me? What's the idea behind the [COLOR="Red"]red[/COLOR] parts and why do you use the [COLOR="blue"]blue[/COLOR] bit instead of the "*if acpi_listen -c 1 | grep -q 0000007b*" I posted earlier in the thread?

```
#!/bin/bash
[COLOR="red"]while true
do[/COLOR]
    [COLOR="Blue"]acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] [/COLOR]
    then
      touchrotate toright
    fi
[COLOR="red"]done[/COLOR]
```

---

### Post by beastrace91 on 2011-01-30
> **messinwu said:**
> Wow, that keyboard looks nice.  Is there a way to install it in Ubuntu?

You could compile and install a current version of Enlightenment Window manager and use it with Gnome I guess (never tried).

Bodhi is Ubuntu based though :)

~Jeff

---

### Post by coffen on 2011-01-31
> **miegiel said:**
> **Slartius** or **coffen**, can you explain your script to me? What's the idea behind the [COLOR="Red"]red[/COLOR] parts and why do you use the [COLOR="blue"]blue[/COLOR] bit instead of the "*if acpi_listen -c 1 | grep -q 0000007b*" I posted earlier in the thread?

```
#!/bin/bash
[COLOR="red"]while true
do[/COLOR]
    [COLOR="Blue"]acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] [/COLOR]
    then
      touchrotate toright
    fi
[COLOR="red"]done[/COLOR]
```

The red part makes the script run like a deamon. Without it the script would only run once and exit.
The blue part could be altered to your suggestion. Both ways work about the same.

---

### Post by Slartius on 2011-01-31
> **coffen said:**
> The red part makes the script run like a deamon. Without it the script would only run once and exit.
The blue part could be altered to your suggestion. Both ways work about the same.
Well not quite. If you look at the miegiel's post above you can see, that the output of the acpi_listen is:
hotkey ATKD 0000007b 0000003a, 
where the fourth column is the number of events of this type. Althoug it might seem quite farfetched that some event could happen at least 7b-times it is still possible. So if we just grep'ed for that string we could actually trigger that script for any of the acpi events, which occurred enough times. So I would say that the correct way is to actually look only for the events itself and not the whole output.

---

### Post by Slartius on 2011-01-31
> **messinwu said:**
> Okay, got the delay on the Rotate (ExpressGate) button thing figured out.  Was very easy afterall.  The output of acpi_listen seems to add a letter (c-z) for each second the button is held down.  

So, just change 0000007b in the script to **0000007c**.  That way, it won't rotate immediately, but you'd have to purposely be holding the button for about 1.5 seconds it seems.  If you find that's not quite long enough, then make it 0000007d or 0000007e.

Is that what you guys wanted?

I am not quite sure the suggestion with 0000007d or 0000007e would work. I think that there are only three events, button press (0000007b), button release (0000007d), and button hold (0000007c). So if you want to hold it a little longer than 0000007c would work, but if you wanted for script to wait n-seconds, than you would probably have to get press event and then n hold events (if you start acpi_listen in terminal and press button, you will see that the 0000007c events start to appear after a second or so) and after a desired time you could than trigger the script. I don't think, that there is much profit in such script, but if there is interest I could write the addition.

---

### Post by Slartius on 2011-01-31
Another question. Is someone here running netbuntu with unity? I have namely a problem when rotating the screen, that the icons in launcher get very big or small on rotate and I have not found any means of touching that launcher (from a program) that would allow me to restore original size. It reverts to original size if I hover with a pointer over, but that is not the desired way.

---

### Post by messinwu on 2011-01-31
> Not exactly it seems  but you made an interesting observation. What I get is:
hotkey ATKD 0000007b 00000xxx when the rotate button is pressed
hotkey ATKD 0000007c 00000xxx when the rotate button is held
hotkey ATKD 0000007d 00000xxx when the rotate button is released

Oops, you are right.  As for everyone else's comments, I do appreciate the thought that's going into this, although I don't personally find holding the button necessary.

I'm no bash expert, but I don't think any wait statement would work, but rather would need X instances of 0000007c before executing the rest of the script.  I'm pretty sure bash can do that.

However, I would have to google for at least an hour or more before finding a similar script somewhere and stealing some of its code, whereas I know there are some good coders here in this thread who know how to do it off the top of their head.

I believe the timeout switch "-t 3" is useless for this purpose, as I observed that it just stopped listening for acpi stuff after 3 seconds.  I don't think that's the function you had in mind, is it?

I do believe that waiting for a certain number of instances of 0000007c is what we need, since it just repeats itself while the button is held down.  Anyone else agree with that?

---

### Post by miegiel on 2011-01-31
> **coffen said:**
> The red part makes the script run like a deamon. Without it the script would only run once and exit.
The blue part could be altered to your suggestion. Both ways work about the same.

> **Slartius said:**
> Well not quite. If you look at the miegiel's post above you can see, that the output of the acpi_listen is:
hotkey ATKD 0000007b 0000003a, 
where the fourth column is the number of events of this type. Althoug it might seem quite farfetched that some event could happen at least 7b-times it is still possible. So if we just grep'ed for that string we could actually trigger that script for any of the acpi events, which occurred enough times. So I would say that the correct way is to actually look only for the events itself and not the whole output.

Thanks, both of you! I get it now.

I opted for *awk '{ print $3 }'* so that it would only grab the 3rd column. I also added quotes for *$press* and *$hold*, so that *if* wouldn't get confused if *$press* and *$hold* are empty.

Maybe someone can improve on this, but it rotates the screen if you hold the button for more than 2 seconds.

```
#!/bin/bash
#
while true
do
    press=$(acpi_listen -c 1 | grep 0000007b | awk '{ print $3 }')
    hold=$(acpi_listen -t 2 | grep 0000007d | awk '{ print $3 }')

    if [ "$press" == "0000007b" ]
        then
            if [ "$hold" != "0000007d" ]
                then
                    touchrotate toright
            fi
    fi
done
```
Hey **messinwu** how does this forum compare to the fedora forums now? ;)

---

### Post by messinwu on 2011-01-31
Hey miegiel - cool way to do it!

The Ubuntu community seems to be on-par with the Fedora community in terms of professionalism, knowledge of most users, etc.  I think I'll keep Ubuntu on my T101MT.

I still disagree with calling the touchrotate script.  For one reason, it's because it won't work with the 2nd Gen devices, you'd have to call 'touchrotate LVDS1 10' (that 10 number would have to be $devID.  Maybe I'm wrong, but isn't the way I originally posted, including the X and Y values, a way of making sure the screen is calibrated at the same time?

Anyway, I made a comment a couple days ago that it was better because it didn't require the touchrotate script and would be distribution independent.  Then I was reminded that this is an Ubuntu forum afterall.

However, I still think we should stay away from what I like to call the 'Internet Explorer Mentality'.  Yes, you can make it work for Ubuntu only with touchrotate, but why not make it work for all linux distributions when we have the code right there?  Webmasters sometime code their pages to work only with IE, meaning they don't look right at all when viewed with a real browser, like Chrome or Firefox.  That's just bad coding, in my opinion.

At the moment, I've compiled the Florence virtual keyboard.  I seem to like it better than Onboard or the others.  I'm trying to create a '.com' key like my smartphone has.  It's proving to be quite a challenge.

Wish me luck!

---

### Post by Slartius on 2011-02-01
> **miegiel said:**
> Thanks, both of you! I get it now.

I opted for *awk '{ print $3 }'* so that it would only grab the 3rd column. I also added quotes for *$press* and *$hold*, so that *if* wouldn't get confused if *$press* and *$hold* are empty.

Maybe someone can improve on this, but it rotates the screen if you hold the button for more than 2 seconds.

```
#!/bin/bash
#
while true
do
    press=$(acpi_listen -c 1 | grep 0000007b | awk '{ print $3 }')
    hold=$(acpi_listen -t 2 | grep 0000007d | awk '{ print $3 }')

    if [ "$press" == "0000007b" ]
        then
            if [ "$hold" != "0000007d" ]
                then
                    touchrotate toright
            fi
    fi
done
```Hey **messinwu** how does this forum compare to the fedora forums now? ;)
Nice code. I would never have thought of that (I hope this is at least a bit grammatically correct). I actually implemented similar solution but with counting the hold events, not waiting for several seconds. And I think, that your code looks a loot simpler. 
One improvement might be to add a command line parameter, which would be used as a -t parameter which would allow for custom delay.

---

### Post by Slartius on 2011-02-01
> **Slartius said:**
> Nice code. I would never have thought of that (I hope this is at least a bit grammatically correct). I actually implemented similar solution but with counting the hold events, not waiting for several seconds. And I think, that your code looks a loot simpler. 
One improvement might be to add a command line parameter, which would be used as a -t parameter which would allow for custom delay.
I did some testing of the code previously posted but I am afraid it is not working quite the way I hoped. I believe the problem is the 
```
hold=$(acpi_listen -t 2 | grep 0000007d | awk '{ print $3 }')
``` statement. What happens here is the acpi_listen listens for n (in this case 2) seconds for all events, 
which are then grep'ed. And if in those 2 seconds 0 or at least two 0000007d events appear, the hold contains aither empty string or several 0000007d values (more than one). In second "if" then this differs from 0000007d ("" or "0000007d 0000007d etc" differs from "0000007d") so in case, where you quickly press the button two times, the screen still rotates. This is for most users quite acceptable. Anyhow here is my solution, which takes multiple button presses into account (at least I think so)

```

#!/bin/bash
num=0
if [ $# -eq 1 ]
then
    num=$1
    if [ ! `echo "$num" | grep -E "^[0-9]+$"` ]
    then
    num=0
    fi
fi

devId=`xinput list | grep "eGalax\|AsusTek" | sed -e 's/.*id=//' -e 's/[\t ].*//g'`
rangex=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]X" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
rangey=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]Y" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)
    cnt=0
    if [ $acpi == "0000007b" ] 
    then
    while [ $cnt -lt $num ]
    do
        acpi1=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)
        if [ $acpi1 == "0000007c" ]
        then
        let cnt=cnt+1
        else 
        cnt=-1
        break
        fi
    done
    if [ $cnt -ge 0 ]
    then
        torotate=( $devId ) 
        xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
        case $xrandrout in
        600x1024 ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
        1024x600 ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
        esac

        xrandr -o $(( rotate * 3 ))
        for input in ${torotate[@]}
        do
        xinput set-prop $input "Evdev Axes Swap" $rotate
        xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
        xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
        done
    fi
    fi
done

```If you want you can still replace most of the script with a touchrotate script (I just posted whole code since I just copied my code). This script is much like miegiels with a difference that if you press the button several times this won't trigger the rotate screen. And it also implements a desired number of hold  events (one event is approximately one second or a little bit more).

---

### Post by messinwu on 2011-02-01
If anyone with the "2nd Gen" T101MT is wanting to make the webcam right-side-up, you've probably noticed the existing fix does not work.  It's because we have a different webcam installed than the "1st Gen" version of the T101MT does.

I've attached a revised version of the v4l-utils package you need to compile.  I just added the following lines to **/lib/libv4lconvert/control/libv4lcontrol.c** once the package is extracted into its own directory:

```
	{ 0x13d3, 0x5126, 0, "ASUSTeK Computer INC.", "T101MT",
		V4LCONTROL_HFLIPPED | V4LCONTROL_VFLIPPED },
```

Then, in order to run an application using the webcam, you have to include the following before the app name:  **export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so**, like this:

```
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

I made a script to execute this command and changed the menu item in gnome to call the script, instead of cheese directly.  I've attached the cheese.sh script as well as the revised v4l-utils package.

I hope this helps someone.

---

### Post by messinwu on 2011-02-01
In Windows, there is a function activated by pressing Fn-Space, it's the Super Hybrid Engine.  On some eeepc's, it actually allows for on-the-fly overclocking, and also supports power saving mode.

You may have noticed that when you switch to battery power, the CPU powers down to 1GHz.  If you install something called Jupiter, you can have control of the CPU speed by toggling through the power modes using the Fn-Space keys just like you can in Windows.

Follow these instructions:

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
sudo apt-get install jupiter-support-eee
```

Then, just add "**/usr/bin/mono /usr/bin/jupiter.exe**" to start at boot-up time.

---

### Post by Slartius on 2011-02-04
I was just wondering if anyone has an issue with the hibernate option. Using 10.10 edition of netbuntu, whenever computer wakes from hibernate only right quarter of screen is visible, the rest is completely black. That would have to do something with graphic drivers I guess. Any suggestions?

---

### Post by ianni67 on 2011-02-06
> **Slartius said:**
> I was just wondering if anyone has an issue with the hibernate option. Using 10.10 edition of netbuntu, whenever computer wakes from hibernate only right quarter of screen is visible, the rest is completely black. That would have to do something with graphic drivers I guess. Any suggestions?
Sorry, no suggestions. But I have no issues at all with hibernate. My touch screen is the first version. If you have the same version then there must be something wrong with your current installation.
):P

---

### Post by beastrace91 on 2011-02-08
In the never ending search of a touch friendly browser for my x86 tablet computer, the power of FOSS triumphs again. Firefox Mobile running under Bodhi -

[img]http://i.imgur.com/ChTGT.jpg[/img]

My search may finally end... Anyone else tried this?

~Jeff

---

### Post by miegiel on 2011-02-08
> **beastrace91 said:**
> In the never ending search of a touch friendly browser for my x86 tablet computer, the power of FOSS triumphs again. Firefox Mobile running under Bodhi -

[img]

My search may finally end... Anyone else tried this?

~Jeff

I think I'll give it a try. [Chrome]("http://www.google.com/chrome")/[chromium]("http://packages.ubuntu.com/maverick/chromium-browser")/[iron]("http://en.wikipedia.org/wiki/SRWare_Iron") is touch-friendly enough for me. But, as with every browser, there are always things I'm not happy with.

**ps** Can you ad your images as an attachment in the future? With large images it make the thread look better and they're to large for a 1024x600 screen anyway.

---

### Post by messinwu on 2011-02-08
A script to make the Fn-F4 button resize the screen to 1280x750 and back again.  This is not the native resolution of the display panel, so it will appear slightly less clear, but it helps when menu dialogs, etc are hanging off the screen and you can't get to some buttons, such as in the Compiz Configuration stuff.

Just run this at boot-up as you do with the rotate.sh script.

```
#!/bin/bash

while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "00000038" ] 
    then
    xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
    case $xrandrout in
        *1280* ) resize=1.00;;
        *1024* ) resize=1.25;;
    esac

    for input in ${resize}
    do
        xrandr --output LVDS1 --scale $resize'x'$resize
    done
    fi
done
```

---

### Post by beastrace91 on 2011-02-09
> **miegiel said:**
> I think I'll give it a try. 
**ps** Can you ad your images as an attachment in the future? With large images it make the thread look better and they're to large for a 1024x600 screen anyway.

I'll try to remember to do that... All the *decent* forum software I am used to resizes the images automatically on the screen so that is never an issue.

~Jeff

---

### Post by ianni67 on 2011-02-09
@messinwu:

I definitely must give your solution a try. It might definitely make my day! 
I often use evolution and everytime I get stuck with those !#*@ windows which cannot be resized.

By the way, I would like to suggest to all those friends using a tablet, a predictive virtual keyboard (similar to T9). The size of such a keyboard is much smaller than onboard or florence and typing is faster (if you are accustomed to cellular phones).

A couple of such keyboard: 
[http://code.google.com/p/virtualinput/](http://code.google.com/p/virtualinput/)
and
[http://code.google.com/p/numpad4tabletlinux/](http://code.google.com/p/numpad4tabletlinux/)

I'm using the first one at the moment and it works quite smooth!

---

### Post by miegiel on 2011-02-09
> **ianni67 said:**
> ...

I often use evolution and everytime I get stuck with those !#*@ windows which cannot be resized.

...

Hold Alt and drag the window (with mouse/pad/screen, your choice).

Binding the resize to the button is great though. But I prefer 2048x1200 :twisted: and it help with ...

> ... so it will appear slightly less clear ...

---

### Post by ianni67 on 2011-02-09
> **miegiel said:**
> Hold Alt and drag the window (with mouse/pad/screen, your choice).


If I use it as a tablet, I have no keyboard in my hands... :confused:

---

### Post by miegiel on 2011-02-09
> **ianni67 said:**
> If I use it as a tablet, I have no keyboard in my hands... :confused:

Sorry, but that's narrow minded.

---

### Post by beastrace91 on 2011-02-10
> **ianni67 said:**
> @messinwu:
A couple of such keyboard: 
[http://code.google.com/p/virtualinput/](http://code.google.com/p/virtualinput/)


That link doesn't work :-/

~Jeff

---

### Post by ianni67 on 2011-02-10
> **beastrace91 said:**
> That link doesn't work :-/

~Jeff

The link works... did you mean the program?

---

### Post by ianni67 on 2011-02-10
> **miegiel said:**
> Sorry, but that's narrow minded.

I didn't understand your comment. Whenever I use my T101 as a tablet, I rotate the screen and cannot access the keyboard.

---

### Post by miegiel on 2011-02-10
> **ianni67 said:**
> I didn't understand your comment. Whenever I use my T101 as a tablet, I rotate the screen and cannot access the keyboard.

Yes you can. Lift the screen a little, slide in your thumb and hold the alt key.

That's just 1 possibility, try not to focus on the impossibilities to much. ;)

---

### Post by voodoosound on 2011-02-15
Hi everyone,

i upgraded my t101mt to maverick this night by updatemanager (not dvd/usb), to get that beautiful mutiltouch stuff working...
sounded pretty easy...

untill now ive tried the following kernel packages with the apropriate multitouch debs and none of them did work...

2.6.32-25 (recognized touchscreen, cursor jumped to left upper corner, no calibration possible)
2.6.35-25 (nothing, no calibration possible)
2.6.35-26 (self compiled deb, nothing, no calibration possible)
2.6.35-27 (self compiled deb, nothing, no calibration possible)

the latest kernel version is the one that is installed, and the command 'xinput --list --long' doesnt show a touchscreen controller anymore, like he did in 2.6.32-25 kernel...

since maverick, it should work out-of-the-box or am i wrong? 
what am i doing wrong?


any ideas anyone?

---

### Post by messinwu on 2011-02-15
Please post the output of the command **lsusb**

---

### Post by voodoosound on 2011-02-16
lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by miegiel on 2011-02-16
> **voodoosound said:**
> lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 

```
Is your touchscreen, I've no idea why it's not listed by *xinput --list* though.

---

### Post by Dragonias on 2011-02-17
Hello, do I understand it correctly that the T101MT community page says that things should "just work" with the upstream 2.6.38 kernel? I have compiled 2.6.38-rc4, and I am sure that I selected the needed drivers (and possibly some unneeded too, I have hid_egalax and usbhid built into the kernel, and hid-multitouch and usbtouchscreen as a module). But I can't get the touchscreen to work. I have the 2nd generation touchscreen.

Output of lsusb:
```
Bus 001 Device 003: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

EDIT: Output of xinput list:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
```

xev does not report any events when I touch the screen. Also, it ( == singletouch) used to work with 2.6.35 kernel when I followed the instructions at the community page (but I reinstalled, so this is a fresh system, and I think it might also be a problem with X, like I said, I have no idea as I am a newbie).

I am a newbie to Linux, so I really don't know where to start. I would appreciate any help! And thanks for supporting the other folks with this great netbook!

---

### Post by messinwu on 2011-02-17
@Dragonias - Yes, I'm the one who put that language in the community page regarding the upstream kernel.  I installed 2.3.38-rc3 and it "just worked", meaning I had single-touch and the mouse pointer followed my finger as I moved it around the touchscreen.  To enable multi-touch, I had to modify the twofing script somewhat and install that.

Are you SURE you're actually booting into the new kernel?  Do command 'uname -r' to verify.

When I compiled the upstream kernel, I also followed some brief instructions from the ENAC website (the people who are making multi-touch work with this 2nd gen screen).  Those instructions are as follows:

when you go to configure the kernel with 'menuconfig', go to Device Drivers --> HID Devices --> Special HID Drivers. Mark 'HID Multitouch panels' as a module (hit space or m).  Quit menuconfig and save your changes and continue compiling the kernel.

However, I believe those instructions were only necessary to integrate the git patches into an older kernel.  The '0486:0186' screen's drivers should be automatically included in the kernel as of 2.6.36 actually.

You didn't do the 'sudo modprobe usbhid quirks=...' command, did you?  That's not necessary as the driver should be in the kernel already.

Anyway, please verify that you're actually booting into the new kernel, and maybe we can figure something out.

---

### Post by messinwu on 2011-02-17
@voodoosound - wow, I'm not sure what the problem could be.  Your touchscreen is registering in the kernel, but not in xinput huh?  Very strange...  The egalax screen should 'just work' as of kernel 2.6.35-25 without any patch or .deb being installed.  Make sure you're not doing the 'sudo modprobe usbhid quirks...' command.  Since you did an upgrade from a previous version of Ubuntu, it might be too messy for anyone to troubleshoot, and you might be better off just wiping clean and re-installing a fresh Maverick version (10.10).

---

### Post by Dragonias on 2011-02-18
Yes, I am running the new kernel, and as I read the instructions on ENAC website, I have not used the quirks with usbhid (I have actually compiled it into the kernel, not as a module). But could there be a conflict between the hid_egalax and hid_multitouch? I have both, hid_egalax in the kernel (therefore I cannot unload it) and hid_multitouch as a module (modprobing it doesn't help). I will recompile the kernel with only hid_multitouch so that I can be sure that there is no conflict.

I am wondering whether I have a similar problem as voodoosound, as both of us have the screen in lsusb but not in xinput. Also, could this be a problem with X, not the kernel? I will google and post back if I find anything...

Thanks a lot for support!

---

### Post by Cammi on 2011-02-18
Second-Gen T101MT user here.

I upgraded to 10.10 last night after a fresh reinstall of the 10.04 I had downloaded for a while.  Current kernel is 2.6.35-27 and the touch screen does not work out of the box as I was led to believe.

My friend gave me a work-around, that can get the pen to work without having to input modprobe commands everytime I load the computer.

basically replacing in the GRUB file: 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash
```

with

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0486:0x186:0x0040"
```

And then reboot.

I'm not interested in multitouch and things.  I basically just want to use the tablet screen to draw things.  but I have two problems related to that:

1. There's no pressure sensitivity in GIMP like the community help page says.  I checked the input devices and "eGalax Inc. USB [TouchController]("https://help.ubuntu.com/community/TouchController")" is not even on the list despite installing the driver at the [top of this page]("https://help.ubuntu.com/community/T101MT").  Instead there are two instances of the Asustek input where only one of them actually works

2. Mypaint's brushes will not work at all.  I ran the patch for 0.8.2, nothing happened, so I installed MyPaint 0.9.0 and ran THAT patch and still nothing.  I like MyPaint better than Gimp as Gimp is too overwhelming with toolboxes that don't even fit on a netbook screen, so if there's a way to at least fix this, I'll be satisfied for a while.  Pressure sensitivity isn't a must for this case.  I just want the program to work.

Originally I had 10.04 installed, faced these problems, so I did a fresh install of 10.04, performed all updates and then upgraded to 10.10.

---

### Post by messinwu on 2011-02-18
The "2nd Gen" touchscreen does not work "out of the box" until kernel 2.6.36.  You either have to compile an upstream kernel, or patch your kernel to include the proper hid-multitouch module.  Info is already in this thread a few pages back, but if you have trouble finding, just PM me and I'll be glad to help since I too have a 2nd Gen screen.

The quirks hack you're doing is fine if you don't need multi-touch.  It's just going to give you two touch devices to choose from, one of which is "fake".  Once Ubuntu advances to kernel 2.6.36, then you can remove that from your grub config, and you'll have only once touch device show up.  At that time, you can compile twofing (using the method I described a few pages back for this particular screen) in order to do two-finger zoom and rotate if you so wish.

---

### Post by Dragonias on 2011-02-20
@messinwu: I have compiled the 2.6.38-rc4 kernel (yes, I have selected hid_multitouch), but I can't get my 2nd generation touchscreen to work (it does not show in /proc/bus/input/devices). I tried grepping for its VendorID (and the corresponding constant, ASUSTEK-something) in the drivers/hid/ directory, but it's not mentioned anywhere relevant... what am I missing? Did you apply some patch that I didn't notice? I am getting kind of desperate, I've been trying to get the touchscreen to work for the last week and a half... I would be really thankful to you if you could help me as to what *exactly* I need to do to get it to work (I am a real newbie)... Thanks a lot!

---

### Post by messinwu on 2011-02-20
@Dragonias - I have been thinking and thinking, and I just can't figure out why your screen isn't showing up on xinput.  It must be an X problem I guess, but why would you have any different version than the rest of us?

Just for kicks, I've also installed Fedora using an external hard drive, using lots of info extracted from this thread of course.  At first, when I touched the screen the pointer just went to the upper-left corner and wouldn't move.  I compiled the latest mainstream kernel, as you did, and then it was working as expected.

Why doesn't that work for you?  I have no idea... I'm not really an advanced user, I'm just advanced enough to fumble my way to where I want to go.

You might do ```
cat /var/log/Xorg.0.log > x.txt
``` then open the resulting "x.txt" file to examine what is happening as X is loading.  Maybe you'll get a hint in there.

---

### Post by Dragonias on 2011-02-21
Well, from the log it looks like udev is not picking it up, as X is (according to the log) supposed to auto-add devices based on what udev reports. If udev doesn't see it, there probably is a problem with a misconfigured kernel. Would you be so kind as to post/send me/whatever your kernel .config so that I would have something that *should* work and would be able to find out what I did wrong?

Also, I started with a freshly installed system, so I did not apply any of the things mentioned in the community page, maybe something is missing in my system? I will look into it today.

Thanks a lot for help!

**EDIT**: Forget me, sorry, I am an idiot, I wasn't including the hid_mosart module in my kernel configuration. (Who would have expected that hid_mosart was necessary? For some reason I assumed that I needed hid_multitouch :D) I can confirm that the "2nd generation" touchscreen works fine, by using hid_mosart.

@messinwu: Thank you so much for your willingness to help! It's thanks to folks like you that folks like me can enjoy the benefits of Linux :D

Also, you mentioned that after making some changes to the twofing daemon you got multitouch working... would you please share that? Thanks a lot!

---

### Post by Dragonias on 2011-02-21
@voodoosound: Does the output of the command lsmod show something like 'hid_egalax'? That should be the module you need. If it is not shown, try 'sudo modprobe hid_egalax' (without quotes) to insert it into the kernel and see if it works.

---

### Post by psykatog on 2011-02-21
Just did a fresh install of LinuxMint 10 KDE (erased previous OS), and noticed a few things : 

- the touchscreen worked out of the box.  I couldn't rotate the screen until I installed the packages from Plippos PPA, but the touch support worked fine.
--- I noticed something similar when I tested Ubuntu-based distros via a live USB drive.  The touchscreen was already working with no updates.  I figured it was because I had configured it in the OS on the hard disk, even if I don't know why that would happen.

- When I rotate the screen using the touchrotate command, the touchscreen's orientation is off.  The cursor appears in an inverted location from where I touch.  Any ideas on this?  Kernel is 2.6.35-22
**EDIT - bit embarrassed I missed this, I had downloaded the wrong kernel driver.  Downloaded 2.6.*32*-22, not .35.  Still wonder why my touchscreen worked out of the box though.  I've never downloaded or used the calibration program.**

---

### Post by Naitsirhc Hsem on 2011-02-21
OMG Natty A2 multitouch 2ng gen.   any have any ideas how to get multitouch gestures :)

---

### Post by messinwu on 2011-02-22
@Dragonias - Hey sorry for such a long delay in responding.  I'm not even sure if you still want/need my .config file for the kernel.  I'm attaching it to this post anyway.

You have the 2nd Gen screen, so the 'touchrotate' script won't work for rotating the screen *and* touch correctly.  You see, the screen itself is rotating, via the simple xrandr command, but the touch is not rotating because the touchrotate script is referencing the egalax panel, which you don't have.  You'll notice quite a bit of discussion about the creation of a rotate.sh script a few pages back.  You can copy the code from that and make it executable and run it at bootup to properly rotate the screen using the rotate button (next to the power button).  You'll also notice some people were working on getting it to rotate only after the button is held down after an amount of time, etc.

I also got the 'twofing' script to work with the 2nd Gen screen, it's in this thread a few pages back as well, to enable true multi-touch.

---

### Post by psykatog on 2011-02-23
When I tried to install the v4l-utils package to fix the upside-down camera, I found the following problem - 
```
XXXX@XX ~/System/T101MT/v4l-utils-0.7.92-test $ make PREFIX=/usr
make -C lib all
make[1]: Entering directory `/home/jrmy/System/T101MT/v4l-utils-0.7.92-test/lib'
make -C libv4lconvert all
make[2]: Entering directory `/home/jrmy/System/T101MT/v4l-utils-0.7.92-test/lib/libv4lconvert'
cc -Wp,-MMD,"libv4lconvert.d",-MQ,"libv4lconvert.o",-MP -c -I../include -fvisibility=hidden -fPIC -DLIBDIR=\"/usr/lib\" -DLIBSUBDIR=\"libv4l\" -I../../include -D_GNU_SOURCE -g -O1 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4lconvert.o libv4lconvert.c
/bin/sh: cc: not found
make[2]: *** [libv4lconvert.o] Error 127
make[2]: Leaving directory `/home/jrmy/System/T101MT/v4l-utils-0.7.92-test/lib/libv4lconvert'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jrmy/System/T101MT/v4l-utils-0.7.92-test/lib'
make: *** [all] Error 2
```

Any clues?

---

### Post by messinwu on 2011-02-23
sudo apt-get install gcc

---

### Post by riccardo.depalo on 2011-03-02
Hi all, I tried to upgrade with Natty, and everything worked fine. I switched back to gnome, because I don't like Unity, and noticed no particular bugs with t101mt. Not bad for an Alpha version. The strange thing is that Plippo's Twofing doesn't work with this 2.6.38 kernel. Even if it should have the driver included. Maybe some strange patch in Natty's evdev?

---

### Post by messinwu on 2011-03-02
If you have the "2nd Gen" screen in your T101MT, then the twofing thing won't work until you make a change I talked about a few pages back.  If you have the original screen, then we'll have to figure it out for you, as I'm using that same kernel and it's working for me.

---

### Post by miegiel on 2011-03-02
> **riccardo.depalo said:**
> Hi all, I tried to upgrade with Natty, and everything worked fine. I switched back to gnome, because I don't like Unity, and noticed no particular bugs with t101mt. Not bad for an Alpha version. The strange thing is that Plippo's Twofing doesn't work with this 2.6.38 kernel. Even if it should have the driver included. Maybe some strange patch in Natty's evdev?

I have natty installed twice. Once upgraded from maveric. The touchscreen worked fine when I first upgraded (including *twofing*), but the touch is almost totally wrecked by now. When I thouch the screen I get a click where the mouse pointer is on the screen before I touch it and another click where I touch the screen, sometimes resulting in double clicks. I get another click when I lift my finger. Oh joy! 

The other natty is a clean install that I use to test updates, so that I don't break natty at an inconvenient time. I don't use the second natty much, it's purely for testing. The touchscreen works well, but I didn't get around to installing *twofing* yet. I'll migrate to the clean installed natty for daily use one of these days. Till then, I'll live with the bugged screen. Maybe compiling *twofing* for natty is the solution?

Be carefull with natty though! *Evdev* updates broke X a few weeks back and X is still under construction. Make sure you have alternative boot options (dualboot and/or live USB/CD) and [COLOR="Red"]proceed with extreme caution[/COLOR], especially when installing updates to X.

And about *unity*: I tried ubuntu's natty (I'm back to xubuntu again) 1 or 2 months ago and found the *unity* interface too sluggish, 200ms gui delay on clicks is too annoying. Though the interface looks practical for on a touchscreen device it might be too demanding of our little single core atom. Though this might improve as development continues, it might even have already, I think I should warn you all in advance.

(1st generation touchscreen)

---

### Post by riccardo.depalo on 2011-03-03
> **messinwu said:**
> If you have the "2nd Gen" screen in your T101MT, then the twofing thing won't work until you make a change I talked about a few pages back.  If you have the original screen, then we'll have to figure it out for you, as I'm using that same kernel and it's working for me.

I have the old eGalax screen. In previous Maverick install I used the evdev version without patches, and it worked for me. Of course, because natty is still an Alpha version, I will be very careful. I tried also re-building the driver, but I noticed no difference. Two finger didn't work. And I noticed another thing: if I try to install a deb file that was downloaded (for instance the twofing in deb version) software center by ubuntu refused to load it because it was of poor quality". Does it mean that Ubuntu try to stop loading third-party versions?

---

### Post by miegiel on 2011-03-03
> **riccardo.depalo said:**
> ... And I noticed another thing: if I try to install a deb file that was downloaded (for instance the twofing in deb version) software center by ubuntu refused to load it because it was of poor quality". Does it mean that Ubuntu try to stop loading third-party versions?

I never had that warning when installing debs, but then I use
```
sudo dpkg -i package.deb
```
to install debs most of the time.

That said, this is a subject for the [natty subforum]("http://ubuntuforums.org/forumdisplay.php?f=394") ;)

---

### Post by maegras on 2011-03-12
hi guys, this is my first post in the international forum.
I bought an Asus T101, it arrives yesterday. :)

Following the wiki i got all working pretty nice, that's awesome.
I have just one question before start reading the whole thread: Is there a way to enhance touchscreen reactivity? I would like to use it for hand-writing in xournal, but cursor is quite slower than my hand and I can't get clear letters

thanks ):P

---

### Post by beastrace91 on 2011-03-13
I just posted a video demoing what our little Asus T101MT can do with Linux power :D

[http://www.youtube.com/watch?v=vzgE6gkb2EE](http://www.youtube.com/watch?v=vzgE6gkb2EE)

Cheers,
~Jeff

---

### Post by bakinsoda on 2011-03-13
@beastrace91 Jeff, that looks nice.  Is that just a regular ubuntu install, with Enlightenment as the window manager?  Anything else that's different compared with the setup outlined by the wiki?

---

### Post by beastrace91 on 2011-03-13
> **bakinsoda said:**
> @beastrace91 Jeff, that looks nice.  Is that just a regular ubuntu install, with Enlightenment as the window manager?  Anything else that's different compared with the setup outlined by the wiki?

That is Enlightenment with a *pile* of custom configurations that can all be found by default in Bodhi Linux :)

But if you compile the latest E from SVN I'm sure you can get the same results on Ubuntu with a few hours of work ;)

~Jeff

---

### Post by mrspacklecrisp on 2011-03-13
Aw man, I'm back again. Okay you guys. Lucid 2.6.32-29, first gen. I have the touchdriver-won't-restart-after-computer-is-closed thing again. Thoughts? What was it that Plippo added to fix this?

I still feel like Karmic was such a smooth speed demon on this thing. Would it be worth it to downgrade maybe? I don't care much for constant kernel updates anyway.

P.S. Some pages of youtube load with pink, funky videos.... If anybody else is dealing with this, lemme know.

---

### Post by beastrace91 on 2011-03-13
> **mrspacklecrisp said:**
> 
P.S. Some pages of youtube load with pink, funky videos.... If anybody else is dealing with this, lemme know.

[http://www.bodhilinux.com/forums/index.php?/topic/647-fix-redpink-tint-in-flash-videos/](http://www.bodhilinux.com/forums/index.php?/topic/647-fix-redpink-tint-in-flash-videos/)

~Jeff

---

### Post by bakinsoda on 2011-03-14
@beastrace91 Cool, I'm going to give it a shot.  Enlightenment seems interesting.  Willing to try Bohdi since it's Ubuntu-based.  So for the touchscreen config on Bohdi, I should follow the 10.04 instruction since Bohdi is based on 10.04?

---

### Post by mrspacklecrisp on 2011-03-14
> **beastrace91 said:**
> [http://www.bodhilinux.com/forums/index.php?/topic/647-fix-redpink-tint-in-flash-videos/](http://www.bodhilinux.com/forums/index.php?/topic/647-fix-redpink-tint-in-flash-videos/)

~Jeff

It's kind of a queer fix, since I'm not able to have a youtube account if I so choose, but it'll hold me over. Thanks so much!

Now if I could only reopen my computer without constantly rmmod's and modprobe's. I seriously want to downgrade to Karmic if at all possible.

---

### Post by Kevrox on 2011-03-14
> **mrspacklecrisp said:**
> 

P.S. Some pages of youtube load with pink, funky videos.... If anybody else is dealing with this, lemme know.

me too I just thought it was a glitch on flash player... very annoying. Mine seems to happen after one good viewing then after the next youtube pick it goes pink....

---

### Post by beastrace91 on 2011-03-14
> **bakinsoda said:**
> @beastrace91 Cool, I'm going to give it a shot.  Enlightenment seems interesting.  Willing to try Bohdi since it's Ubuntu-based.  So for the touchscreen config on Bohdi, I should follow the 10.04 instruction since Bohdi is based on 10.04?

Yes follow the 10.04 instructions for the touch screen. Just make sure you grab the right kernel package (we ship the 2.6.35-24 kernel) and also our Xorg is the same version as maverick.

Check our [wiki article]("http://www.bodhilinux.com/wiki/doku.php?id=eeepc_t101mt") on it for full details.

~Jeff

---

### Post by Kevrox on 2011-03-14
> **mrspacklecrisp said:**
> 

P.S. Some pages of youtube load with pink, funky videos.... If anybody else is dealing with this, lemme know.

This worked for me, [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

I chose option 3 fix..
 Right click a flash animation - this doesn't work with YouTube so you'll have to right click something like this site, then select "Settings" and uncheck the "Enable hardware acceleration box" like in the screenshot below:

hope this helps

---

### Post by bakinsoda on 2011-03-15
@beastrace91 I'm giving Bohdi Linux a chance.  First, it IS lightweight.  However, settings doesn't appear to be obvious to me.

1.  What does the "switch" button on the bottom left do?
2.  What do the 3 buttons on the main screen do?
3.  The text and icons seems rather small for netbook/tablet use.  How do I change these settings?
4.  How do I set custom keyboard bindings?
5.  Is there a quicker way to call the default on screen keyboard than the button on top?  Those icons are too small.  Also, how how do I get rid of the keyboard without going to the icon on top?

Thanks.

---

### Post by DheathNone on 2011-03-15
> **beastrace91 said:**
> I just posted a video demoing what our little Asus T101MT can do with Linux power :D

[http://www.youtube.com/watch?v=vzgE6gkb2EE](http://www.youtube.com/watch?v=vzgE6gkb2EE)

Cheers,
~Jeff

                                      *"This video contains content from Sony Music  Entertainment and UMG, one or more of whom have blocked it in your  country on copyright grounds."*

---

### Post by hanoc on 2011-03-15
> **DheathNone said:**
> *"This video contains content from Sony Music  Entertainment and UMG, one or more of whom have blocked it in your  country on copyright grounds."*

I can see the video correctly so the restriction must only apply to your country.

If you can't wait to the owner to change the music track you can use a proxy to watch the video.


PS: aren't you by any chance in germany? All of the videos I've uploaded with other people music on them get blocked _only_ in germany

---

### Post by mrspacklecrisp on 2011-03-15
> **mrspacklecrisp said:**
> Aw man, I'm back again. Okay you guys. Lucid 2.6.32-29, first gen. I have the touchdriver-won't-restart-after-computer-is-closed thing again. Thoughts? What was it that Plippo added to fix this?

I still feel like Karmic was such a smooth speed demon on this thing. Would it be worth it to downgrade maybe? I don't care much for constant kernel updates anyway.


Also, twofing won't selectively shut off while I'm using mypaint for example. 

Hey, how many of y'all upgraded your RAM out of curiosity?

---

### Post by coffen on 2011-03-15
> **DheathNone said:**
> *"This video contains content from Sony Music  Entertainment and UMG, one or more of whom have blocked it in your  country on copyright grounds."*

Why don't you watch it through China Proxy :)
[http://www.china-proxy.org/servers.php/Oi8vd3d3/LnlvdXR1/YmUuY29t/L3dhdGNo/P3Y9dnpn/RTZna2Iy/RUU_3D/b1/](http://www.china-proxy.org/servers.php/Oi8vd3d3/LnlvdXR1/YmUuY29t/L3dhdGNo/P3Y9dnpn/RTZna2Iy/RUU_3D/b1/)

---

### Post by DheathNone on 2011-03-17
> **coffen said:**
> Why don't you watch it through China Proxy :)
[http://www.china-proxy.org/servers.php/Oi8vd3d3/LnlvdXR1/YmUuY29t/L3dhdGNo/P3Y9dnpn/RTZna2Iy/RUU_3D/b1/](http://www.china-proxy.org/servers.php/Oi8vd3d3/LnlvdXR1/YmUuY29t/L3dhdGNo/P3Y9dnpn/RTZna2Iy/RUU_3D/b1/)

Now that we are completely off topic:

Country is Finland. http proxies doesn't seem to work on youtube (tried it a few times) and it is quite annoying to find a nicely working real proxy. This would not pother me if I would not see these kind of youtube videos linked every day.

Thanks for the music.
Thanks for the sony.

I wish that we can stop this off topic here.
My humble apologies.

---

### Post by Kevrox on 2011-03-21
hi all
is there any reason why I could not download the latest (brand new [http://www.kernel.org/](http://www.kernel.org/)) kernel that is out there and run it on ubuntu 10.04 with gen 1 screen

OR will I stuff it all up.

I have done the following before when there was a new kernel as a normal update

cd t101mt-kernel-driver
./build.sh

this usually gets all the touch stuff working again.
cheers
kev

---

### Post by maegras on 2011-03-21
Hi all, could anyone give me informations about T101MT temperatures?

I got TZ00 (acpi thermal zone) up to 55/57 °C in idle with fan always running at 3900 RPM. 
Is that normal?

---

### Post by hanoc on 2011-03-23
Hi

I was trying a new installation of bodhi and I was following the instructions in the wiki. I can't find the plippo repositories:

By following the first two steps ```
sudo apt-add-repository ppa:plippo/t101mt
``` and then update I get:
```
Failed to fetch http://ppa.launchpad.net/plippo/t101mt/ubuntu/dists/lucid/main/binary-i386/Packages.gz 404  Not Found
```

Are the instructions out of date or are the packages are temporary down?

---

### Post by Kevrox on 2011-03-26
hi all
So today I took the plunge and installed the daily build of Natty.
I must admit I was at first negative about the interface before even trying it. BUT for a touch screen net book I think this will be good. I already had the 2 top and bottom panels side by side on the RHS of screen so this works well for me.
I have found that the touch aspect starts off ok but then fails if one tries with the second touch to get RH click menus.
My Unit is first gen screen.

I am not expecting solutions from this thread yet but just my findings.... any other users with Natty builds please comment on your findings and tweaks...
cheers kev

edit a day later
finding screen a bit dark, there was a fix for the others just wondering if I need to do the same thing.
launch of programs is quite laggy at least 2-4 seconds before the program runs.
unity is not bad, Gnome I still love but will persist with unity....
FF4 is not nice to work with....
 back on topic. 
I hope this natty will sort all this stuff out without having to tweak things to work, touch, 2 finger , gestures pinch zoom etc......

---

### Post by Naitsirhc Hsem on 2011-03-26
gen 2 works out of the box on latest daily builds.  gnome shell is better than unity in my opinion

---

### Post by Dragonias on 2011-03-29
@messinwu: Thanks a lot, I've already figured it out, I had thought it was more difficult than changing the udev rule and a few grep's in touchrotate. Again, thank you for the help!

As for folks who use xournal: I just updated, and I am suddenly experiencing very bad responsivity (like maegras a couple posts back). Does anyone have a clue what is happening? Also, twofing does not pause when using xournal even though it is blacklisted, and again I have no clue why. (Currently I have modified the xournal launcher to kill twofing & relaunch it once xournal has closed)

---

### Post by Kevrox on 2011-03-30
Is anyone running Natty on their 1st gen T101mt???

---

### Post by Masternooob on 2011-03-30
> **Kevrox said:**
> Is anyone running Natty on their 1st gen T101mt???

yes, it works great, 
the only problem i have is that the screen is a little dark..
but everything else works fine out of the box...

---

### Post by jxn on 2011-03-30
> **Masternooob said:**
> yes, it works great, 
the only problem i have is that the screen is a little dark..
but everything else works fine out of the box...


Even touchscreen multitouch is working?  

Can't seem to get that to work here... I started with Maverick and upgraded to natty hoping that it would Just Work... but on Natty I can't even build twofing (i get errors which I think must have something to do with changes in libxi).

---

### Post by Kevrox on 2011-03-30
> **jxn said:**
> Even touchscreen multitouch is working?  

Can't seem to get that to work here...  but on Natty I can't even build twofing (i get errors which I think must have something to do with changes in libxi).

me too, as soon as I touch with with the second finger the touch aspect stops working....and I need to reboot, the touch pad works all the time...
Masternooob I find the screen a fraction darker as well, I remember there was a work around for the other versions but am not sure if they still apply to natty.

SO for me with 1st gen screen... multitouch does not work and screen a bit dark, other than that I am enjoying unity and natty....

---

### Post by DarkTide on 2011-03-30
To get the microphone work with skype, I had to install padevchooser to  regulate mono mic and not stereo. I launched the application, click on  input, click on the middle button on the upper right to unblock the  channels, and put one of channels to zero and the other one to 100%. It  seems that skype doesn't find the mono internal mic otherwise and stops  to work.

---

### Post by Kevrox on 2011-03-31
> **DarkTide said:**
> To get the microphone work with skype, I had to install padevchooser to  regulate mono mic and not stereo. I launched the application, click on  input, click on the middle button on the upper right to unblock the  channels, and put one of channels to zero and the other one to 100%. It  seems that skype doesn't find the mono internal mic otherwise and stops  to work.

We had to do that since 10.04.... annoying to have to tweak it so many releases up....

---

### Post by Kevrox on 2011-03-31
ok, got sort of 2 finger touch... well more like the second touch does not cause touch to stop working altogether.
I did this
How to build a kernel driver by yourself
 from here...
[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

it built the deb file and I installed it but no menu option when one touches the screen with the second finger... BUT at least touch screen still works after the second touch... small steps.....

---

### Post by mrspacklecrisp on 2011-03-31
> **Dragonias said:**
> @messinwu: Thanks a lot, I've already figured it out, I had thought it was more difficult than changing the udev rule and a few grep's in touchrotate. Again, thank you for the help!

As for folks who use xournal: I just updated, and I am suddenly experiencing very bad responsivity (like maegras a couple posts back). Does anyone have a clue what is happening? Also, twofing does not pause when using xournal even though it is blacklisted, and again I have no clue why. (Currently I have modified the xournal launcher to kill twofing & relaunch it once xournal has closed)

Same thing happens to me. Twofing itself is supposed to shut off for mypaint and xournal specifically. Gen 1, Lucid, happened after a kernel update (can't recall which, it must have been quite a few ago)

---

### Post by ninjaaron on 2011-03-31
Any chance of getting a Natty repo for the Eee PC packages any time soon? It is in Beta now, after all...

and I'm using it...

and I really want those packages...

;)

---

### Post by Kevrox on 2011-03-31
after my last post I did the following with the output as follows

[I]EXPERIMENTAL TWO-FINGER TOUCH DAEMON
download:twofing-0.0.7.tar.gz (or old version: twofing-0.0.6b.tar.gz)
Extract it to a folder of your choice (e.g. your home dir)
Open a terminal and navigate to the extracted folder (e.g. cd ~/twofing-0.0.7 if you extracted it to your home dir)
Install the required packages:

sudo apt-get install build-essential libx11-dev libxtst-dev libxi-dev x11proto-randr-dev libxrandr-dev

Compile the daemon by calling

make

Install the daemon by calling

sudo make install

Reboot (doesn't have to be done on updates, only on first install as a new udev rule is created)
Open a terminal again and call twofing (nothing will seem to happen) [/I]

---

### Post by Kevrox on 2011-03-31
continue post

xxx@xxx-T101MT:~$ cd twofing-0.0.7
xxx@xxx-T101MT:~/twofing-0.0.7$ make
gcc -o twofing twofingemu.o gestures.o easing.o -lm -lpthread -lXtst -lXrandr -lX11
twofingemu.o: In function `grab':
twofingemu.c:(.text+0x9a): undefined reference to `XIGrabButton'
twofingemu.o: In function `ungrab':
twofingemu.c:(.text+0xe2): undefined reference to `XIUngrabButton'
twofingemu.o: In function `readCalibrationData':
twofingemu.c:(.text+0xe9c): undefined reference to `XIGetProperty'
twofingemu.c:(.text+0xf2e): undefined reference to `XIGetProperty'
twofingemu.c:(.text+0xf6a): undefined reference to `XIQueryDevice'
twofingemu.c:(.text+0x1074): undefined reference to `XIFreeDeviceInfo'

---

### Post by Kevrox on 2011-03-31
twofingemu.c:(.text+0x111f): undefined reference to `XIGetProperty'
twofingemu.c:(.text+0x11c4): undefined reference to `XIGetProperty'
twofingemu.c:(.text+0x13b1): undefined reference to `XIGetProperty'
twofingemu.o: In function `main':
twofingemu.c:(.text+0x17c1): undefined reference to `XIQueryVersion'
twofingemu.c:(.text+0x1820): undefined reference to `XIQueryDevice'
twofingemu.c:(.text+0x1888): undefined reference to `XIFreeDeviceInfo'
twofingemu.c:(.text+0x18ff): undefined reference to `XISelectEvents'
collect2: ld returned 1 exit status
make: *** [twofing] Error 1
xxx@xxx-T101MT:~/twofing-0.0.7$ sudo make install
[sudo] password for xxx: 
install --mode=755 twofing /usr/bin/
install: cannot stat `twofing': No such file or directory
make: *** [install] Error 1
xxx@xxx-T101MT:~/twofing-0.0.7$

hope this helps diagnose
silly smilies that is why I posted over 3 posts sorry in not convention

---

### Post by beastrace91 on 2011-04-01
Anyone know if there is a pre-built .deb somewhere for the 2.6.35-28 kernel?

~Jeff

---

### Post by Kevrox on 2011-04-02
> **Masternooob said:**
> yes, it works great, 
the only problem i have is that the screen is a little dark..
but everything else works fine out of the box...

I guess Natty is not going to work out of the box for me... so I have tweaked the brighter screen from our starter Bible.. [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)
follow the screen brightness steak
 still no 2 finger ....

---

### Post by Kevrox on 2011-04-03
just run the beta live boot and touch screen worked and second finger did not crash touch  BUT Just installed Natty beta..... seems touch crashes on second touch AGAIN... Live cd was fine........

---

### Post by Plippo on 2011-04-03
Hi everyone,

I updated the packages in the PPA for Natty. Two finger scrolling on the touch**pad** now works out of the box (if you activate it in the mouse settings), so this package is no longer there. For two finger gestures on the touch**screen**, I am still working on a new version of *twofing* as there are quite a few problems that prevent the old version from working in Natty. I'll of course tell you when I find a solution.

---

### Post by Kevrox on 2011-04-04
> **Plippo said:**
> Hi everyone,

I updated the packages in the PPA for Natty.  I'll of course tell you when I find a solution.

Plippo you are a legend, many thanks form us all

---

### Post by Kevrox on 2011-04-04
> **Plippo said:**
> Hi everyone,

I updated the packages in the PPA for Natty. Two finger scrolling on the touch**pad** now works out of the box (if you activate it in the mouse settings), so this package is no longer there. For two finger gestures on the touch**screen**, I am still working on a new version of *twofing* as there are quite a few problems that prevent the old version from working in Natty. I'll of course tell you when I find a solution.

So I guess we just add this to sources ppa:plippo/t101mt
once again Plippo thank you...

---

### Post by beastrace91 on 2011-04-04
> **Plippo said:**
> I am still working on a new version of *twofing* as there are quite a few problems that prevent the old version from working in Natty. I'll of course tell you when I find a solution.

Are these Unity related issues? I'm using the 2.6.38-7 kernel here on Bodhi (Enlightenment desktop) and the twofing daemon is working fine.

One issue I am having that has cropped up after I just did a clean install - Anyone else here use Xorunal? It is my bread and butter touch screen program, but after my latest reinstall there is now like a half second delay between when I put my pen to the screen and when I start writing. Makes taking notes *really* annoying - any help would be wonderful :)

~Jeff

---

### Post by jxn on 2011-04-04
> **beastrace91 said:**
> Are these Unity related issues? I'm using the 2.6.38-7 kernel here on Bodhi (Enlightenment desktop) and the twofing daemon is working fine.

~Jeff

I don't think they're unity issues, as I cannot get twofing working on the latest natty builds and I'm using e17.  It doesn't even successfully make (error reported earlier by Kevrox)

---

### Post by beastrace91 on 2011-04-04
> **jxn said:**
> I don't think they're unity issues, as I cannot get twofing working on the latest natty builds and I'm using e17.  It doesn't even successfully make (error reported earlier by Kevrox)

Ahh not kernel related then either. Must be something with the binaries they are using somewhere along the way.

~Jeff

---

### Post by DarkTide on 2011-04-05
To get the microphone work with skype, I had to install padevchooser to  regulate mono mic and not stereo. I launched the application, click on  input, click on the middle button on the upper right to unblock the  channels, and put one of channels to zero and the other one to 100%. It  seems that skype doesn't find the mono internal mic otherwise and stops  to work.

---

### Post by maegras on 2011-04-05
> **beastrace91 said:**
> 

One issue I am having that has cropped up after I just did a clean install - Anyone else here use Xorunal? It is my bread and butter touch screen program, but after my latest reinstall there is now like a half second delay between when I put my pen to the screen and when I start writing. Makes taking notes *really* annoying - any help would be wonderful :)

~Jeff

I'm using unity and xournal, but I hadn't notice this issue. I have a little delay (millisec) but it isn't so annoying.


 Just a question to all of you: in Natty, tablet mode, how do you manage screen brightness? Is there any applet or indicator?

---

### Post by riccardo.depalo on 2011-04-06
> **maegras said:**
> I'm using unity and xournal, but I hadn't notice this issue. I have a little delay (millisec) but it isn't so annoying.


 Just a question to all of you: in Natty, tablet mode, how do you manage screen brightness? Is there any applet or indicator?

well it works out of the box with plippo's ppa packages, just press fn+F4-F5 or add brightness indicator on a gnome panel and just use fingers. I didn't find anyway how to do it with unity

@Plippo: hi, it seems I can't upgrade eeepc-brightness-workaround_1.0-ppa2_all.deb and eeepc-powersave_1.0-ppa2_all.deb. Maybe some dependencies not working?

---

### Post by beastrace91 on 2011-04-06
Spoke too soon about the twofing I guess, it is the cause of my delay issue. Disabling it causes the device to write perfectly fine.

~Jeff

---

### Post by riccardo.depalo on 2011-04-07
@Plippo: I solved the dependencies issue, but I had to make a fresh install of Natty. It seems Ubuntu doesn't like upgrade, it's better to erase the disk and start again. Anyway, I noiced that the camera is no more upside down in cheese, but there is the same upside down problem of before with skype and google video chat.

---

### Post by Plippo on 2011-04-08
@riccardo: And twofing works for you now? Because for me, even after solving the dependency issue, twofing still won't work in Natty (at least in Unity) and instead crashes and/or hangs and/or doesn't prevent left clicks any more while two-fingered gestures are performed, making them practically unusable.

That's why I'm currently working on a completely new version of twofing which will no longer perform the click filtering itself but instead will bring a modified X driver to do that. As a bonus, this way it would also be possible to use twofing with applications like GIMP or MyPaint. (In the long turn, I plan to completely put the functionality of twofing into that driver so the daemon would no longer be needed.)

But at the moment nothing is ready yet and I don't know if it will work the way I planned. I hope It'll be finished before the release of Natty's final version, but I can't promise anything.

---

### Post by riccardo.depalo on 2011-04-08
@Plippo: I tried twofing upgrading directly to Natty, but it didn't work (even if sometimes it performed some gestures) and I thought it was because of a new evdev version. Now I erased my hard drive and reinstalled Natty, and I couldn't compile it, even with required packages. Maybe some still missing.

---

### Post by Kevrox on 2011-04-09
ok folks here is a strange one.....

When I was running the daily build from some time ago I had full download speed from router. After having updated to Beta the max the download speed will go to is between 45 and 120 kb/s.
I have tested my router with other laptops in the house downloading from the same iinet ftp site, iinet test downloads.
The other machines NON linux all go max speed 450 to 800 kb/s.

I ran the live cd of the daily builds and had those max download speeds, updated and no more....... any takers???

---

### Post by Naitsirhc Hsem on 2011-04-09
Natty is still quite unstable, still in beta.  I think that would be better placed in a natty development forum.

---

### Post by riccardo.depalo on 2011-04-13
for anybody interested, chrometouch addon works well for one finger scrolling in t101mt, waiting for the new twofing daemon with Natty. Updates made the system much more stable now.

---

### Post by mrspacklecrisp on 2011-04-18
> Touchscreen works, but no strokes in mypaint. Clean removal, compiled and ran MyPaint 9.1, apply patch, no strokes. Add prebuilt package from ppa:tillux/t-misc, apply patch, no strokes.

Okay, twofing was a part of the problem, but strokes still connect...

---

### Post by bakinsoda on 2011-04-22
Hi,

Just did a fresh install of Natty beta 2 and did an upgrade after install.  Wanted to report what I have:

1.  touchscreen works; xournal works.
2.  two finger touchPAD works after enabling in the mouse options.
3.  no upside down camera in cheese; will test firefox and skype later
4.  have not tested microphone yet.
5.  function keys (volume, brightness) work.
6.  brightness seems to always be dimmed when system starts.  installed "eeepc-brightness-workaround" but this doesn't fix it.  did the /etc/rc.local method, still no go.  brightness is always dimmed when system starts.
7.  suspend works, but touchscreen no longer works after coming back from suspend.
8.  hibernate does not work: when i come back, i see my mouse cursor on a black screen, with some fuzzy lines from the graphics.  i tried this after coming back from suspend.

---

### Post by Kevrox on 2011-04-23
> **bakinsoda said:**
> Hi,

Just did a fresh install of Natty beta 2 and did an upgrade after install.  Wanted to report what I have:

1.  touchscreen works; xournal works.
2.  two finger touchPAD works after enabling in the mouse options.
3.  no upside down camera in cheese; will test firefox and skype later
4.  have not tested microphone yet.
5.  function keys (volume, brightness) work.
6.  brightness seems to always be dimmed when system starts.  installed "eeepc-brightness-workaround" but this doesn't fix it.  did the /etc/rc.local method, still no go.  brightness is always dimmed when system starts.
7.  suspend works, but touchscreen no longer works after coming back from suspend.
8.  hibernate does not work: when i come back, i see my mouse cursor on a black screen, with some fuzzy lines from the graphics.  i tried this after coming back from suspend.

did the same and my findings
1, confirm
2, confirm
3, cheese is fine , skype is upside down
4, microphone ok if loading padevchooser and tweak as mentioned before
5, confirm
6, mine seems ok
7, never use it cannot confirm
8, never use it cannot confirm

the killer for me is the loss of network speed from AR9285 ath9k bug, I hope they fix this soon.

---

### Post by Kevrox on 2011-04-23
[https://help.ubuntu.com/community/T101MT#SKYPE](https://help.ubuntu.com/community/T101MT#SKYPE)

this works for skype in natty to get camera working
yippy

---

### Post by whammy774 on 2011-04-23
Hi guys, I am trying to get the rotate screen working and am a bit lost. I am running Zorin os4 (based on ubuntu 10.10). I have looked through this thread and still no wiser, on the t101mt ubuntu wiki it lists various touchrotate commands and then at the end it says the following --In order to execute the command, click on the right column and press the key to be used for the shortcut e.g. the screen rotation key below the display---
I do not understand that bit especially where it says CLICK ON THE RIGHT COLUMN ?

Is there a easy way to get the screen rotate to work - I did try the grotate app but it did ot install ????

thanks in advance

---

### Post by coffen on 2011-04-24
> **whammy774 said:**
> Is there a easy way to get the screen rotate to work - I did try the grotate app but it did ot install ????

If you are using the first generation screen then have a look at this post [http://ubuntuforums.org/showpost.php?p=10410974&postcount=787](http://ubuntuforums.org/showpost.php?p=10410974&postcount=787)

---

### Post by Chokolait on 2011-04-24
Hi all. I've just recently gotten my Asus T101MT, and installed Ubuntu 10.10 on it. From the help in this thread, pretty much everything is working great. The only problem that I'm running into is that whenever I turn the screen and put my netbook into 'tablet mode', and then move it back and put the netbook back into 'laptop mode', the touch screen won't work. The only way to fix this that I've found is to restart my netbook. But since I use Xournal to write notes for my classes, it isn't a very good fix. Is there a way to fix this? I have installed the utouch ppa for the multitouch on the screen, and I also have the egalax driver installed. I'm new to Ubuntu, so sorry in advance if I didn't give enough information.

---

### Post by riccardo.depalo on 2011-04-24
@Plippo: there is a problem with your package eeepc-brightness-workaround. I tried to reinstall it, to see if brightness worked again in Natty, and I couldn't do it. Tried to remove, but failed, and anytime I try to upgrade the system, it tries to reinstall eeepc-brightness-workaround but can't.
Have a good easter day
Ric

---

### Post by whammy774 on 2011-04-24
> **coffen said:**
> I simplified the script by calling Plippos touchrotate from it.
This way you can have the screen to rotate clockwise each time the button is pressed.
```

#!/bin/bash
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
      touchrotate toright
    fi
done
```I like this behaviour since I usually want to have the device upside down as a tablet.
Now I simply press the button twice to get the screen upside down :)


Thanks

I was also thinking of implementing a delay (like in Windoze) to prevent accidentally rotaing the device.
I'll post back if I decide to do that.

Thanks Coffen - now have screen rotating - cheers :D

---

### Post by whammy774 on 2011-04-24
Hi, back again, Coffen has shown me how to rotate the screen using the command which I ran in a terminal,  I have found I have to run this command every time I boot up the system - is this correct (sorry I am a relative newby to running commands in terminal).

The other thing is how do I get the right click function to work using the stylus on the screen - is this possible ????

thanks again

---

### Post by coffen on 2011-04-25
> **whammy774 said:**
> ...I have found I have to run this command every time I boot up the system - is this correct...

You can set the script to run automatically. Just add it to: *System - Preferences - Startup Applications*. :)


> **whammy774 said:**
> The other thing is how do I get the right click function to work using the stylus on the screen - is this possible ????

In *Preferences - Mouse - Accessibility* you can tick the checkbox *"Trigger secondary click by holding down the primary button"*

---

### Post by whammy774 on 2011-04-25
Once again Coffen - thanks very much for your help, I will give it a try

cheers :P

Have now tried it and bingo it works, I had to change the file permissions first but then it works on start up, the right click was a breeze and now works, I think my t101mt with zorin os4 installed is now a complete system and much better than the windows 7 it came with although I am dual booting.

Linux rocks

---

### Post by bakinsoda on 2011-04-25
> **bakinsoda said:**
> 
6.  brightness seems to always be dimmed when system starts.  installed "eeepc-brightness-workaround" but this doesn't fix it.  did the /etc/rc.local method, still no go.  brightness is always dimmed when system starts.


I keep forgetting this (it happened last time too), but to get brightness/dimness to work correctly, go to power settings (battery icon) > battery options > uncheck the 2 dim settings.

---

### Post by bakinsoda on 2011-04-25
> **messinwu said:**
> Okay!  Sorry it took me a bit to answer with my xinput list output, but it looks like it doesn't matter anymore.  That last query echoed the correct device ID also.  So, here's our new code for rotate.sh

```
#!/bin/bash
devId=`xinput list | grep "eGalax\|AsusTek" | sed -e 's/.*id=//' -e 's/[\t ].*//g'`
rangex=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]X" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
rangey=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]Y" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
    torotate=( $devId ) 
    xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
    case $xrandrout in
        600x1024 ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
        1024x600 ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
    esac

    xrandr -o $(( rotate * 3 ))
    for input in ${torotate[@]}
    do
        xinput set-prop $input "Evdev Axes Swap" $rotate
        xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
        xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
    done
    fi
done
```

Hi, I'd like to get the express gate button working with rotating the touchscreen.  I saw this up the thread.

I tried it on Natty beta 2, saved it as rotate.sh, executed it, but no go.  Wondering if it's not working because of natty beta 2 or I'm using an old script.  Can anyone help?  I don't see it documented in the wiki.  Thanks!

---

### Post by mrspacklecrisp on 2011-04-27
No matter what version I use Mypaint gives me Z-strokes. This is extremely distressing. Is there a place other than usr/share/mypaint in which the program could be accessing messed up data? Patches apply successfully, but it doesn't seem to care. Anyone experiencing this?

(Meerkat)

---

### Post by mrspacklecrisp on 2011-04-27
While I'm at it, I'll go ahead and ask if anybody is having this hovering box problem after accidentally dragging an item or closing a menu. Are y'all?

[IMG]http://i51.tinypic.com/344ruc9.png[/IMG]

---

### Post by Plippo on 2011-04-27
twofing is still making some trouble in Natty, still didn't get it to work fully. Here is a new version which will work with Natty (but DON'T use it with other versions) but has the problem that pressure sensitivity doesn't work (but it also doesn't work without twofing in natty, too. I'm working on that.) So if you like to try it, installation is as always, package is attached.

@riccardo: Strange, the package works for me, but I will try installing it again.

@mrspacklecrisp: Can't say anything about the mypaint problem (using Natty right now and it doesn't work at all here), but this "hovering box" problem looks *really* strange, I have never seen this before.

---

### Post by Plippo on 2011-04-27
@riccardo: I tried again, the package still works for me. What error message do you get when you try to install it?

---

### Post by mrspacklecrisp on 2011-04-27
> **Plippo said:**
> twofing is still making some trouble in Natty, still didn't get it to work fully. Here is a new version which will work with Natty (but DON'T use it with other versions) but has the problem that pressure sensitivity doesn't work (but it also doesn't work without twofing in natty, too. I'm working on that.) So if you like to try it, installation is as always, package is attached.

@riccardo: Strange, the package works for me, but I will try installing it again.

@mrspacklecrisp: Can't say anything about the mypaint problem (using Natty right now and it doesn't work at all here), but this "hovering box" problem looks *really* strange, I have never seen this before.
 Hm. May I ask what you did in the first place to kill the Z-stroke problem? I do still get pressure sensitivity. It's very strange that it wouldn't work in either version, because I can hardly imagine it's in the kernel's built-in drivers.

---

### Post by riccardo.depalo on 2011-04-27
@Plippo: I solved the problem with brightness-workaround making a partial upgrade, that uninstalled the package during the final cleaning process(it gave me "serious inconsistency" message trying to upgrade, before). I tried also new twofing 0.0.9a and it seems working with Natty. It seems more responsive, maybe too much with the zoom in/out gesture.

---

### Post by atomp on 2011-04-28
I also had the problem of eeepc-brightness-workaround.
The package went inconsistent and wouldn't remove or reinstall through apt or synaptic, eventually I had to force remove it with dpkg:

> sudo dpkg --remove --force-remove-reinstreq eeepc-brightness-workaround

After which I merely reinstalled via synaptic and ta da, working again.

I'd also once again like to thank everyone on this thread, after a year with this device I can't imagine what it would have been like without Ubuntu and all the tweaks (like twofing) that have made it run so smoothly, your hard work is very much appreciated.

---

### Post by Kevrox on 2011-04-28
> **Plippo said:**
> twofing is still making some trouble in Natty, still didn't get it to work fully. Here is a new version which will work with Natty (but DON'T use it with other versions) but has the problem that pressure sensitivity doesn't work (but it also doesn't work without twofing in natty, too. I'm working on that.) So if you like to try it, installation is as always, package is attached.


will this work on 1st gen T101mt's. I get the following error when I run make
gcc -c -wall -02 twofingemu.c
twofingemu.c:22:23: fatal error: x11/xutil.h: no such file or directory compilation terminated.
make:*** [twofingemu.o] error 1

thanks kev

---

### Post by maegras on 2011-04-28
> **Kevrox said:**
> will this work on 1st gen T101mt's. I get the following error when I run make
gcc -c -wall -02 twofingemu.c
twofingemu.c:22:23: fatal error: x11/xutil.h: no such file or directory compilation terminated.
make:*** [twofingemu.o] error 1

thanks kev

same problem here :)

---

### Post by riccardo.depalo on 2011-04-29
> **Kevrox said:**
> will this work on 1st gen T101mt's. I get the following error when I run make
gcc -c -wall -02 twofingemu.c
twofingemu.c:22:23: fatal error: x11/xutil.h: no such file or directory compilation terminated.
make:*** [twofingemu.o] error 1

thanks kev

Hi, did you install all packages suggested in the wiki?```
sudo apt-get install build-essential libx11-dev libxtst-dev libxi-dev x11proto-randr-dev libxrandr-dev
```

[https://help.ubuntu.com/community/T101MT#EXPERIMENTAL](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL) TWO-FINGER TOUCH DAEMON

---

### Post by mrspacklecrisp on 2011-04-30
I think know my problem...

```
device change: eGalax Inc. USB TouchController <enum GDK_SOURCE_MOUSE of type GdkInputSource>
```


GdkInputSource is telling MyPaint that the screen is a mouse, not resistive. It should be changed to resistive or possibly GDK_SOURCE_PEN for maximum compatibility with all pressure sensitive programs. But, um, I don't actually know where the GDK library is kept...

---

### Post by wafthrudnir on 2011-04-30
Hi [Plippo]("http://ubuntuforums.org/member.php?u=1042691"),

you are my hero of the day. Just wanted to let you know that your version 0.0.9 works like a charm on kubunto 11.04 (installed on a wetab). thank you very much for your effort.

best regards

---

### Post by coffen on 2011-05-01
> **wafthrudnir said:**
> ...version 0.0.9 works like a charm on kubunto 11.04 (installed on a wetab)...
Where did you get version 0.0.9? Did I miss something?
Latest version on the [wiki page]("https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON") is 0.0.7. :-k

---

### Post by Plippo on 2011-05-01
@mrspacklecrisp: To be honest, I haven't looked at mypaint for a long time and don't know if it now supports resistive tablets out of the box. Back last year, I simply added a few lines to the mypaint code that set the pressure to 0 on release of the stylus. But I'll take a look at what changed as soon as I get pressure sensitivity to work at all under natty (probably will have to create patch-less evdev package again or patch the natty X server to support pressure sensitivity and multitouch at the same time).

@riccardo,atomp: Thanks for the information, so the problem seems to be that uninstalling the old version doesn't work, which will prevent you from installing the new one. I'll have a look at that.

@coffen: I posted version 0.0.9a a few posts ago. It's not in the wiki yet as it's experimental right now, only works for Natty and has some limitations.

@Kevrox, maegras: As riccardo wrote, you're probably missing the dependencies.

---

### Post by riccardo.depalo on 2011-05-01
@Plippo and @all: I just added latest twofing version in the wiki. Later, we should refresh it with other details for Natty users.
Regards
Ric

---

### Post by Kevrox on 2011-05-01
> **riccardo.depalo said:**
> Hi, did you install all packages suggested in the wiki?```
sudo apt-get install build-essential libx11-dev libxtst-dev libxi-dev x11proto-randr-dev libxrandr-dev
```

[https://help.ubuntu.com/community/T101MT#EXPERIMENTAL](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL) TWO-FINGER TOUCH DAEMON

Ahh Bugger I forgot I did a new install:), all good now.... many thanks

---

### Post by Kevrox on 2011-05-01
all nice and working well now. Just wish that the slow ath9k bug was sorted.:(

---

### Post by Mystro256 on 2011-05-01
Added Natty info :)

Feel free to edit, as I may have forgotten some things or added incorrect info

---

### Post by jeh727 on 2011-05-02
wow, I am having some issues installing 11.04.  It hangs before I ever even get to the normal menu.  It sits at the loading animation screen and then spews a whole bunch of numbers and random strings, i am guessing it is a kernel dump, and then hangs after unsuccessfully trying to unmount stuff.  grabbing the screen is a bit difficult.  I tried the alternate installer and I get to the menu where you can install, but then it goes blank and nothing happens.  I checked the iso md5sums and tried various usb sticks. I've been searching around for natty install problems but haven't seen anything like this yet.  Anyone else having this problem?  Also, got the 2nd gen display, don't know if that matters.

---

### Post by variona on 2011-05-02
No, I also have a 2nd edition screen but my version upgrade was uncomplicated.

HTH

Variona


PS: The touchscreen worked out of the box (before I had to have the quirks param in the kernel parameters), but touchrotate doesn't work.
```
xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0       
xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 1
``` seem to have no effect at all.

There's a bug filed on launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493), I think it is related

Did anyone encounter similiar problems?

---

### Post by hanoc on 2011-05-03
Hi,

My t101mt had a hardware failure and fortunatelly the guaranty covered it. I got it back yesterday totally formated which means that now it has windows on some kind of fastboot.

Does anyone remember how to enter the bios before the windows boots?
I tried all the usual, F10, F12, Esc, Supr and all I got is a windows menu saying to load Win7 or to do a memcheck.


Thanks!

---

### Post by mrspacklecrisp on 2011-05-03
> **hanoc said:**
> Hi,

My t101mt had a hardware failure and fortunatelly the guaranty covered it. I got it back yesterday totally formated which means that now it has windows on some kind of fastboot.

Does anyone remember how to enter the bios before the windows boots?
I tried all the usual, F10, F12, Esc, Supr and all I got is a windows menu saying to load Win7 or to do a memcheck.


Thanks!
It's F2 or F3. It should still show the little gray bios screen before it boots.

---

### Post by Slartius on 2011-05-04
> **variona said:**
> No, I also have a 2nd edition screen but my version upgrade was uncomplicated.

HTH

Variona


PS: The touchscreen worked out of the box (before I had to have the quirks param in the kernel parameters), but touchrotate doesn't work.
```
xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0       
xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 1
``` seem to have no effect at all.

There's a bug filed on launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493), I think it is related

Did anyone encounter similiar problems?
The upgrade to natty (almost) worked for me. After update I added plippo repo and did upgarde and update. I had some promblems updating eeepc-brightness-workaround and eeepc-powersave (i had to manually remove those entires via dpkg). Immediately after that the rotate script did not work (the cursor traveled in perpendicular direction to actual movement) but after installing new verision (0.0.9a) of the twofing touch daemon it started to work(???). The problem with the screen rotate I have is that the upper part of the screen is black. I guess it probably has to do something with the framebuffer. Just did the upgrade so I still have to look into this. And also the side dock is unusable when any other window is displayed.

PS. I have a 1st gen. screen.

---

### Post by variona on 2011-05-04
Right after installing twofing 0,0.9 I also have the problem with the "half screen" after touchrotate (I don't think it's the framebuffer as the Menu is still visible in the upper half.)

SOLVED[@slartius: what parameters did you use to uninstall the files with dpkg?] using this information :[http://liquidat.wordpress.com/2008/08/22/short-tip-remove-packages-on-debian-systems-with-ultimate-force/]("http://liquidat.wordpress.com/2008/08/22/short-tip-remove-packages-on-debian-systems-with-ultimate-force/")

---

### Post by riccardo.depalo on 2011-05-04
> **Mystro256 said:**
> Added Natty info :)

Feel free to edit, as I may have forgotten some things or added incorrect info

Wiki infos seem ok to me.

@Plippo: maybe we could delete bugs in the last section, as they should both be fixed?

---

### Post by Slartius on 2011-05-05
> **variona said:**
> Right after installing twofing 0,0.9 I also have the problem with the "half screen" after touchrotate (I don't think it's the framebuffer as the Menu is still visible in the upper half.)

SOLVED[@slartius: what parameters did you use to uninstall the files with dpkg?] using this information :[http://liquidat.wordpress.com/2008/08/22/short-tip-remove-packages-on-debian-systems-with-ultimate-force/](http://liquidat.wordpress.com/2008/08/22/short-tip-remove-packages-on-debian-systems-with-ultimate-force/)

Actually I think it might be something with the framebuffer (or at least with the graphic card drivers) since if I hibernate and then restart computer I get mostly black and blurred screen where not completely black  (in console the text is just random white lines). 

For dpkg as you probably figured out yourself: 
sudo dpkg --purge --force-all <package name>

---

### Post by Slartius on 2011-05-05
> **Slartius said:**
> Actually I think it might be something with the framebuffer (or at least with the graphic card drivers) since if I hibernate and then restart computer I get mostly black and blurred screen where not completely black  (in console the text is just random white lines). 

To reply to myself (@variona, I think you are right), it probably isn't the framebuffer. I resolved the hibernate issue, which stems from booting. If anyone has defined an option GRUB_GFXPAYLOAD_LINUX=keep in the /etc/default/grub file then the hibernate probably won't work. You have t set it to text, otherwise the framebuffer gets filled with garbage and whole thing won't work. But the half screen issue remains.

---

### Post by variona on 2011-05-05
ASUS EEEPc T101MT with 2nd Generation touchscreen 

```
>:~$ lsusb
...
BUS 003 Device 001: ID 0486:0186 Asus Computers, Inc.
...

```

My experiences so far:
Upgrades from 10.10(Maverick) to 11.4(Natty) without a problem.
To update eeepc-brightness... and eepc-powersave, both from plippos ppa, I had to uninstall them "by hand" (see my previous post). 

Problems encountered when rotating input of touchscreen.(This means the screen rotates but the input touch remains).
I downloaded and installed twofing 0.0.9 - it didn't start so I changed the udev rule  ({idProduct}==**"0186**"
I couldn't install plippos xserver-xorg-input-evdev package (not found)
Now it's getting interesting:

Start twofing and then call touchrotate toright (-with output (LVDS1) and input parameters(xinput -list: tells you which id's: the input devices have in my case ```
touchrotate LVDS1 14 toright
```) or adapt /usr/bin/touchrotate to fit the 2nd Generation Touchscreen 'eGalax' to 'MultiTouch'. 

Output and Input are rotated as expected. 
The (output) display is weird:
upper half of the screen displays only the menu correctly - but the rest of the upper half of the screen
shows on of the following: a portion of a the lower part of the terminal |blackness |whiteness|another openend program.
The lower half displays correctly.
This appears only in portrait mode (normal and upside down works)

slartius suspected the framebuffer tas a culprit: when rotating Xorg.0.log echoes```
 Allocated new frame buffer **640**x1024 stride 4096, tiled
```
followed by 
```
Allocated new frame buffer 1024x600 stride 4096, tiled
```

Seems to me that Modeline detection fails and falls back.

Any ideas ?

variona

---

### Post by Slartius on 2011-05-05
> **variona said:**
> 
Output and Input are rotated as expected. 
The (output) display is weird:
upper half of the screen displays only the menu correctly - but the rest of the upper half of the screen
shows on of the following: a portion of a the lower part of the terminal |blackness |whiteness|another openend program.
The lower half displays correctly.
This appears only in portrait mode (normal and upside down works)

slartius suspected the framebuffer tas a culprit: when rotating Xorg.0.log echoes```
 Allocated new frame buffer **640**x1024 stride 4096, tiled
```followed by 
```
Allocated new frame buffer 1024x600 stride 4096, tiled
```Seems to me that Modeline detection fails and falls back.

Any ideas ?

variona

Well, it might be a problem with a max texture size issue, according to a [similar error]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/756624"). I tried to log into Ubuntu Classic session (No effects) and the rotate works without a problem. When using the normal Ubuntu session, I got an X error: intel(0): Couldn't create pixmap for fbcon.

But so far no solution.

---

### Post by variona on 2011-05-05
I also tried Ubuntu Classic Session:

with twofing:
+)no weird display after going into portrait(600x1024) mode!
+)correct positioning of the cursor after touching the rotated screen 
-)**no click event** (I haven't noticed before as I was too occupied with the screen - but this is also reproducible with Unity!
-)no two finger action recognisable

My adapted udev rule led to a /dev/twofingtouch which points to input/event7

without twofing:
+)no weird display after going into portrait(600x1024) mode!
+)click
-)false positioning of the cursor after touching the rotated screen


Leaves me with three questions: 
1)Is the weird screen issue that slartius and I encountered (on 1st and 2nd Gen Displays) Unity related?
2)What does twofing that allows for correct positioning of the cursor after rotating.
3)Is not clicking while twofing is executed 2nd Gen Screen related?

---

### Post by Slartius on 2011-05-05
> **variona said:**
> I also tried Ubuntu Classic Session:

with twofing:
+)no weird display after going into portrait(600x1024) mode!
+)correct positioning of the cursor after touching the rotated screen 
-)**no click event** (I haven't noticed before as I was too occupied with the screen - but this is also reproducible with Unity!
-)no two finger action recognisable

Leaves me with three questions: 
1)Is the weird screen issue that slartius and I encountered (on 1st and 2nd Gen Displays) Unity related?
2)What does twofing that allows for correct positioning of the cursor after rotating.
3)Is not clicking while twofing is executed 2nd Gen Screen related?

I again tried the Ubuntu classic and for me it works OK. What do you mean by "no click event"? I can normally click on my screen, and I also have the two finger action recognizable, like two finger scrolling, two taps simulate right mouse button. I guess I am just lucky.

---

### Post by variona on 2011-05-05
By **no click** event I mean **mouse over** is recognised but when touching a button or a starter there is no reaction at all.

Calling twofing with --debug echoes: 
```
Process fingers!
Process Fingers!
Handle event
Touch update
Process fingers!
Handle event
Touch end
```
Looking into the source code I couldn't understand if and how handleXEvent() passes the event information,.
Maybe you're lucky because you have the 1st Gen Display?

Didn't anyone (except me ;) ) with a 2nd Gen Display upgrade to Natty yet?

---

### Post by Slartius on 2011-05-06
> **variona said:**
> 

Didn't anyone (except me ;) ) with a 2nd Gen Display upgrade to Natty yet?

Apparently you are the only one :shock:. 

As far as the black bar appearance, it has been [reported]("https://bugs.launchpad.net/unity/+bug/776875"), and remedy for now is to revert to previous version of unity (thanks to above link): ```
sudo apt-get install unity=3.8.10-0ubuntu2 unity-common=3.8.10-0ubuntu2
``` I've tried it and for me it works even better then described \\:D/.

---

### Post by psykatog on 2011-05-08
Hi all, I've been using Linux Mint 10 KDE and noticed this : 
Whenever I rotate the orientation of my  screen, whether by KRandRtray or Plippo's touchrotate package via  terminal, My program windows adjust, but my panel is still the length of  the full screen in normal orientation.  This wasn't the case in Kubuntu  Lucid/KDE4.5.

I tried switching my panel alignment (R,L,Center),  but even with the panel set to center and cut to half-size, the panel  still extends way beyond the screen's edge when the screen is rotated.   The system tray, clock, & show desktop app (which are all aligned on  the far right for me) aren't visible when rotated.  Problem exists with  default task manager and smoothtasks alike.

---

### Post by variona on 2011-05-09
With plippos :
xserver-xorg-input-evdev 	1:2.6.0-1withoutpatchesubuntu1 

finally evdev behaves like expected. Thanks Philipp!
(

Twofing still doesn't work for me, but that's no big problem for me. Only out of principle and curiosity I'd like to no why.

Unity proved to be ok but for now I'll stick to Ubuntu Classic. I can't reach the panel with fingers or pen in tablet mode.

---

### Post by andi_st on 2011-05-16
Hi Plippo,

after an upgrade to 11.04 i have problems with the two pakages eeepc-powersave and eeepc-brightness-workaround.
I am not able to install or deinstall this pakages. The following output is displayed from apt:
```
sudo apt-get remove eeepc-brightness-workaround
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  eeepc-powersave
Die folgenden Pakete werden ENTFERNT:
  eeepc-brightness-workaround
Die folgenden Pakete werden aktualisiert (Upgrade):
  eeepc-powersave
1 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
2 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 2.866 B an Archiven heruntergeladen werden.
Nach dieser Operation werden 53,2 kB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? 
dpkg: Fehler beim Bearbeiten von eeepc-brightness-workaround (--remove):
 Paket ist in einem sehr schlechten inkonsistenten Zustand - Sie sollten
 es erneut installieren, bevor Sie es zu entfernen versuchen.
Fehler traten auf beim Bearbeiten von:
 eeepc-brightness-workaround
E: Sub-process /usr/bin/dpkg returned an error code (1)

``````
sudo apt-get -f install eeepc-powersave
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  eeepc-brightness-workaround
Die folgenden Pakete werden aktualisiert (Upgrade):
  eeepc-brightness-workaround eeepc-powersave
2 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
2 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 5.502 B an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? 
dpkg: Warnung: Parsen der Datei »/var/lib/dpkg/available«, nahe Zeile 5246 Paket »v4l-utils-0.7.92:i386«:
 Fehler in Versionszeichenkette »test-1«: Versionsnummer beginnt nicht mit einer Ziffer
(Lese Datenbank ... 161455 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von eeepc-brightness-workaround 1.0-ppa1 (durch .../eeepc-brightness-workaround_1.0-ppa2_all.deb) ...
Ersatz für eeepc-brightness-workaround wird entpackt ...
update-rc.d: /etc/init.d/eeepc-brightness-workaround exists during rc.d purge (use -f to force)
dpkg: Warnung: Unterprozess altes post-removal-Skript gab den Fehlerwert 1 zurück
dpkg - stattdessen wird Skript aus dem neuen Paket probiert ...
update-rc.d: /etc/init.d/eeepc-brightness-workaround exists during rc.d purge (use -f to force)
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/eeepc-brightness-workaround_1.0-ppa2_all.deb (--unpack):
 Unterprozess neues post-removal-Skript gab den Fehlerwert 1 zurück
update-rc.d: /etc/init.d/eeepc-brightness-workaround exists during rc.d purge (use -f to force)
dpkg: Fehler beim Aufräumen:
 Unterprozess neues post-removal-Skript gab den Fehlerwert 1 zurück
Vormals abgewähltes Paket eeepc-powersave wird gewählt.
Vorbereitung zum Ersetzen von eeepc-powersave 1.0-ppa1 (durch .../eeepc-powersave_1.0-ppa2_all.deb) ...
Ersatz für eeepc-powersave wird entpackt ...
update-rc.d: /etc/init.d/eeepc-powersave exists during rc.d purge (use -f to force)
dpkg: Warnung: Unterprozess altes post-removal-Skript gab den Fehlerwert 1 zurück
dpkg - stattdessen wird Skript aus dem neuen Paket probiert ...
update-rc.d: /etc/init.d/eeepc-powersave exists during rc.d purge (use -f to force)
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/eeepc-powersave_1.0-ppa2_all.deb (--unpack):
 Unterprozess neues post-removal-Skript gab den Fehlerwert 1 zurück
update-rc.d: /etc/init.d/eeepc-powersave exists during rc.d purge (use -f to force)
dpkg: Fehler beim Aufräumen:
 Unterprozess neues post-removal-Skript gab den Fehlerwert 1 zurück
Trigger für ureadahead werden verarbeitet ...
ureadahead will be reprofiled on next reboot
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/eeepc-brightness-workaround_1.0-ppa2_all.deb
 /var/cache/apt/archives/eeepc-powersave_1.0-ppa2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```What's going wrong?

Greetings
Andi

---

### Post by atomp on 2011-05-16
> Hi all, I've been using Linux Mint 10 KDE and noticed this : 
Whenever I rotate the orientation of my screen, whether by KRandRtray or Plippo's touchrotate package via terminal, My program windows adjust, but my panel is still the length of the full screen in normal orientation. This wasn't the case in Kubuntu Lucid/KDE4.5.

I had this problem with AWN under gnome, the dirty solution I used was adding a command to kill the panel before rotation and then restart afterwards to the screen rotation script I was using.

It isn't pretty but it worked on the whole and the panel resized.

---

### Post by Plippo on 2011-05-22
Hi,

**@all who are/have been experiencing problems upgrading the packages:** There was a problem with the upgrade script which should be resolved with the latest version of the packages I uploaded to the PPA today.
[B]
@variona and other owners of 2nd Gen touchscreens:[/B] I can only guess why twofing doesn't work on your devices as I don't have one myself. My guess is that it could be because I removed the support for the old version of the Multitouch protocol from twofing 0.0.9a, maybe your touchscreen still uses this old protocol. I re-added the support to version 0.0.9b which you can download below. Again, I wasn't able to test it, so if someone with a 2nd Gen touchscreen would like to test it, I'd be happy to know if it works.

** @all the painters out there:** There is still no support for pressure sensitivity in the new twofing, but with the patched evdev driver I uploaded to the PPA two weeks ago, you should at least be able to get pressure sensitivity once you close twofing using the command
```
killall twofing
```

---

### Post by variona on 2011-05-23
**@plippo:** I just tested twofing 0.0.9b with Eye of Gnome:zoom and rotate picture. I attach debug.txt fyi.

It works!

Thank you

variona

---

### Post by Sharaazad on 2011-05-26
Anyone is experiencing low sound on this netbook with 11.04?
:(

---

### Post by camdnh22 on 2011-06-05
Hi everyone,

Great work Plippo! I'm trying to use twofing on my Acer Iconia W500, under Ubuntu 11.04. The touch screen itself seems to be working great - out of the box I can click around fine, though no gestures. The W500 uses the same eGalax touch screen interface I believe:

lsusb
```

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0cf3:e019 Atheros Communications, Inc. 
Bus 005 Device 002: ID 0eef:7302 D-WAV Scientific Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0b95:772b ASIX Electronics Corp. 
Bus 003 Device 003: ID 0c45:76f4 Microdia 
Bus 003 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 064e:c21c Suyin Corp. 
Bus 002 Device 003: ID 064e:c21c Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

xinput list
```


&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer
(2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=9	[slave  pointer
(2)]
&#9116;   &#8627; SONiX USB Keyboard                      	id=13	[slave  pointer
(2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
   &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard
(3)]
   &#8627; Power Button                            	id=6	[slave  keyboard
(3)]
   &#8627; Video Bus                               	id=7	[slave  keyboard
(3)]
   &#8627; Power Button                            	id=8	[slave  keyboard
(3)]
   &#8627; 1.3M Rear                               	id=10	[slave  keyboard
(3)]
   &#8627; 1.3M Front                              	id=11	[slave  keyboard
(3)]
   &#8627; SONiX USB Keyboard                      	id=12	[slave  keyboard
(3)]
   &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard
(3)]

```

udevadm info --attribute-walk --name=/dev/twofingtouch gives:

```

oking at device
'/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input7/event7':
   KERNEL=="event7"
   SUBSYSTEM=="input"
   DRIVER==""

 looking at parent device
'/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input7':
   KERNELS=="input7"
   SUBSYSTEMS=="input"
   DRIVERS==""
   ATTRS{name}=="eGalax Inc. USB TouchController"
   ATTRS{phys}=="usb-0000:00:13.0-1/input0"
   ATTRS{uniq}==""
   ATTRS{properties}=="0"

 looking at parent device
'/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0':
   KERNELS=="5-1:1.0"
   SUBSYSTEMS=="usb"
   DRIVERS=="usbhid"
   ATTRS{bInterfaceNumber}=="00"
   ATTRS{bAlternateSetting}==" 0"
   ATTRS{bNumEndpoints}=="01"
   ATTRS{bInterfaceClass}=="03"
   ATTRS{bInterfaceSubClass}=="01"
   ATTRS{bInterfaceProtocol}=="02"
   ATTRS{supports_autosuspend}=="1"

 looking at parent device '/devices/pci0000:00/0000:00:13.0/usb5/5-1':
   KERNELS=="5-1"
   SUBSYSTEMS=="usb"
   DRIVERS=="usb"
   ATTRS{configuration}=="eGalax Inc."
   ATTRS{bNumInterfaces}==" 1"
   ATTRS{bConfigurationValue}=="1"
   ATTRS{bmAttributes}=="a0"
   ATTRS{bMaxPower}=="100mA"
   ATTRS{urbnum}=="6110"
   ATTRS{idVendor}=="0eef"
   ATTRS{idProduct}=="7302"
   ATTRS{bcdDevice}=="0997"
   ATTRS{bDeviceClass}=="00"
   ATTRS{bDeviceSubClass}=="00"
   ATTRS{bDeviceProtocol}=="00"
   ATTRS{bNumConfigurations}=="1"
   ATTRS{bMaxPacketSize0}=="64"
   ATTRS{speed}=="12"
   ATTRS{busnum}=="5"
   ATTRS{devnum}=="2"
   ATTRS{devpath}=="1"
   ATTRS{version}==" 1.10"
   ATTRS{maxchild}=="0"
   ATTRS{quirks}=="0x0"
   ATTRS{avoid_reset_quirk}=="0"
   ATTRS{authorized}=="1"
   ATTRS{manufacturer}=="eGalax Inc."
   ATTRS{product}=="USB TouchController"

```

I'm using twofing 0.0.9b, and it compiles and installs fine. I updated the udev entry with the correct id code (7302). Running twofing --debug gives:

```

Input device name: "eGalax Inc. USB TouchController"
XInput device id is 9.
Start calibration
Grab Result: 0
Reading input from device ... (interrupt to exit)
Motion event
Button Press
Motion event
Motion event
Motion event
Motion event

```

And so on. Yet, nothing actually happens on screen; i.e. clicking a menu button or icon doesn't actually do anything, even though twofing seems to be capturing the input. Does anyone have any tips on where to start debugging/looking? I'm not sure whether it's a problem with my eGalax setup, twofing, or Xorg/Ubuntu beneath not getting the new /dev/twofingtouch somehow? I'm good with Ubuntu, but my C knowledge isn't quite up to scratch to dig into the source...

I'm building a doc with the whole Acer W500 setup, and it would be great to get gestures working!

Many thanks,

Dan

---

### Post by gauravm on 2011-06-08
amazing tutorial guys.....i just got my t101mt yesterday and ubuntu is 90% functional of it! I love it.

The problem I am having is that w/ 11.04 and the second generation screen my Rotate Button doesn't seem to be working.  

BTW: I haven't installed twofing because I don't really need two finger functionality.  Does that fix this problem?

Thank you in advance!

---

### Post by variona on 2011-06-13
@gauravm: The touchrotate script searches for an egalax input device! You have to change either the function call by adding parameters or edit the script.
line  21 looks probably like: ```
then EG=$(xinput list|grep 'Egalax')
```
I changed it to 
```
then EG=$(xinput list|grep 'MultiTouch')
```

(I know,neater would have been: then MT=$..)
To put it generic (e.g for 3rd gen screen): Probe the name of your Input device ```
xinput list
```
and exchange 'Egalax' with what you found out.  

It works independently from twofing.

@plippo: BTW mostly I don't use twofing because it seems that single finger or pen touches don't seem to release (second touch is needed to trigger a click event.)

HTH
variona

---

### Post by Plippo on 2011-06-15
I finally changed the twofing script in the PPA so it now should work for both first and second generation T101MTs. It was a more than trivial change and I'm so sorry I didn't do this earlier (and I really don't know why I didn't think about it) as it of course was a quite logical and straightforward thing to do that would have saved all the owners of second gen devices much hassle. But now, it's uploaded, should be built and pushed out in a days and (at least I hope so) work then.

@variona:
Okay, the most probable cause is that I missed something porting the code for the old MT protocol to version 0.0.9b. I will look into that later.

---

### Post by GTZippy on 2011-06-15
So I just upgraded to 11.04 with the hopes of a working version utouch coming out soon.  The only thing I really lost was my right click.  I can get past the fact that all of the screen rotate scripts up here only make the screen change and not the input of the touch screen.  I can handle my camera always being upside down (its a gen 2 101) but I cannot live without my right click.  I have followed every piece of advice I can find on this thread, but none of them have worked.  In fact, a few of them have disabled my touch screen all together.  I have been using ubuntu for a while, but I am not a coder.  I hack together solutions from stuff I find on google and whatnot, but nothing seems to turn my rightclick back on short of having to have the keyboard open and, lets face it, none of us get a tablet PC because we want to have the keyboard out all the time.  Can someone help me out?  Thanks

-EDIT-
One more thing, I downloaded twofing, extracting it, followed all the directions, after the make install I rebooted and I open a terminal and call twofing.  Nothing seems to happen (just like the howto said) but when I try to use the 2 finger gestures, nothing happens at all.  So I try to killall twofing and I get back that twofing is not running.  Can't seem to make it work.

---

### Post by gauravm on 2011-06-17
> **messinwu said:**
> Okay!  Sorry it took me a bit to answer with my xinput list output, but it looks like it doesn't matter anymore.  That last query echoed the correct device ID also.  So, here's our new code for rotate.sh

```
#!/bin/bash
devId=`xinput list | grep "eGalax\|AsusTek" | sed -e 's/.*id=//' -e 's/[\t ].*//g'`
rangex=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]X" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
rangey=`xinput --list $devId | sed  -e '/Label: Abs [XY]/{N;s/\n//;}' | grep "Label:[ +]Abs[ +]Y" | sed -e 's/.*Range:[ +]//g' -e 's/[ +]-[ +]/ /g'`
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
    torotate=( $devId ) 
    xrandrout=$(xrandr | head -n 1 | sed -e 's/.*current//' -e 's/maximum.*//' -e 's/[ +,+]//g')
    
    case $xrandrout in
        600x1024 ) cal=( ${rangex[@]} ${rangey[@]} ); rotate=0;;
        1024x600 ) cal=( ${rangey[@]} ${rangex[@]} ); rotate=1;;
    esac

    xrandr -o $(( rotate * 3 ))
    for input in ${torotate[@]}
    do
        xinput set-prop $input "Evdev Axes Swap" $rotate
        xinput set-prop $input "Evdev Axis Inversion" 0, $rotate
        xinput set-prop $input "Evdev Axis Calibration" ${cal[@]}
    done
    fi
done
```

This scripts works great for me except it only works ONCE! meaning...i press the ExpressGate button the screen rotates but I can't press it again to bring it back to normal.  I have log out for it to fix itself =(  I don't even know where to start to fix that issue.  

Before anyone says "use Philpo's touchrotate"....I have use the above script b/c the touchrotate scripts by Philpo don't work with the botton.

----I think I realize what's going on....for some reason acpi_listen RANDOMLY doesn't recognize the Expressgate button....any one know why that could be?

---

### Post by jeebustrain on 2011-06-24
does anyone have any ideas for a way to get the virtual keyboard to show up on the lock screen? As a rule, I usually like to let my PCs self lock after a bit, and it would be really cool if there was a way to unlock it without having to flip it over and open the physical keyboard.

---

### Post by jeebustrain on 2011-06-24
never mind - found this:

```

sudo apt-get install libfakekey0 matchbox-keyboard

```

inside gconf-editor:

set /apps/gnome-screensaver/embedded_keyboard_enable=TRUE

set /apps/gnome-screensaver/embedded_keyboard_command="matchbox-keyboard --xid" 

(found [here](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#Can_I_embed_an_on-screen_keyboard_for_use_with_mobile_devices.3F)

I'm going to give it a shot with florence (my virt keyboard of choice) to see if that works as well...

---

### Post by N0rbert on 2011-06-25
Hello!
I have just brought new (2 Gen) T101MT with dual-core Atom N570. 
In lsusb output I have:
```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5126 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```In lspci:
```
lscpi
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```In xinput list
```

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; AsusTek, Inc. MultiTouch(TTI)               id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 PC Cam                              id=11    [slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                    id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

```I have successfully installed Ubuntu 11.04 x86 on it using [community guide]("https://help.ubuntu.com/community/T101MT"). Thank you!
Touchscreen works OOTB in single-touch mode. Touchrotate script works. Mic and sound are OK. Camera is upside-down, fixed. Two finger scrolling on touchpad working.

Twofing 0.0.9b works after editing Idproduct in udev rule:
```
cat /etc/udev/rules.d/70-touchscreen-egalax.rules 
BUS=="usb",ACTION=="add",KERNEL=="event*",SYSFS{idProduct}=="0186",SYMLINK+="twofingtouch",RUN+="/bin/chmod a+r /dev/twofingtouch"

```See twofing.txt log. Output of 'udevadm info --attribute-walk --name=/dev/usb/hiddev0' is in udevadm_usb-hiddev0.txt, of 'udevadm info --attribute-walk --name=/dev/twofingtouch' is in udevadm_twofingtouch.txt. Twofing 0.0.9a does not work.

@**jeebustrain**
I tried to replace **matchbox** keyboard with **onboard** one for **gnome-screensaver**:
```

 /apps/gnome-screensaver/embedded_keyboard_command="onboard --xid" 

``` or from **onboard-settings** utility.

@**all**
But I have a problem. When I am trying to enter password in gnome-screensaver I can't do that (with both **matchbox** or **onboard**). If I press a key of virtual keyboard once, I give many instances of its symbol in the password prompt. So I can't login without transforming tablet. 
I discovered a solution: when I do not use **twofing** daemon, I can enter password letter by letter. But I do not want to go back to single-touch. What do you think?
UPD: on-screen keyboards are unusable in normal Unity session too. I'll try Ubuntu Classic Gnome.
UPD2: on-screen keyboards are unusable in Ubuntu Classic Gnome too.

@Plippo
Do you know about [mtview]("https://wiki.ubuntu.com/Multitouch/Testing/UsingMtview")? With help of it I saw that touchscreen is working in multitouch mode normally.

---

### Post by N0rbert on 2011-06-26
After long time of googling and trying I discovered that **UTouch** is usable on T101MT(at least on mine). with Ubuntu 11.04.

I wrote small HOWTO:
1. Install xserver-xorg-input-evdev package with ubuntu patches:
```

sudo apt-get install xserver-xorg-input-evdev=1:2.6.0-1ubuntu12

```It is recommended to Pin/Lock its version in Synaptic: Package->Lock version.
2. Install the latest version of Ginn and multitouch touchscreen driver:
```

sudo apt-add-repository ppa:utouch-team/utouch
sudo apt-get update
sudo apt-get install ginn utouch utouch-geis-tools hid-multitouch-dkms

```3. Reboot. In **lsmod  | grep hid** you will have both *hid_mosart* and *hid_multitouch* modules.
4. Run **geistest**. If everything is OK you will see something like this:
```

geistest 
Device 10 added
    attr "device name" = "AsusTek, Inc. MultiTouch(TTI)"
    attr "device id" = 10
    attr "direct touch" = true
    attr "independent touch" = false
    attr "device touches" = 20
    attr "Abs MT Position X 0 min" = 0.000000
    attr "Abs MT Position X 0 max" = 3478.000000
    attr "Abs MT Position X 0 resolution" = 0
    attr "Abs MT Position Y 1 min" = 0.000000
    attr "Abs MT Position Y 1 max" = 3478.000000
    attr "Abs MT Position Y 1 resolution" = 0
Device 14 added
    attr "device name" = "SynPS/2 Synaptics TouchPad"
    attr "device id" = 14
    attr "direct touch" = false
    attr "independent touch" = false
    attr "device touches" = 4
    attr "Abs MT Position X 0 min" = 1472.000000
    attr "Abs MT Position X 0 max" = 5624.000000
    attr "Abs MT Position X 0 resolution" = 0
    attr "Abs MT Position Y 1 min" = 1408.000000
    attr "Abs MT Position Y 1 max" = 4754.000000
    attr "Abs MT Position Y 1 resolution" = 0
    attr "Abs MT Tracking ID 2 min" = 0.000000
    attr "Abs MT Tracking ID 2 max" = 65535.000000
    attr "Abs MT Tracking ID 2 resolution" = 0
```You can try zooming and rotating in Eye Of GNOME. It should work.
Press Ctrl+C in **geistest** terminal.
5. For better experience it's useful to set Edge Scrolling of touchpad:
```

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method --type=int 1
```6. Add gesture for right mouse click on touchscreen. Replace two first lines with the following: 
sudo gedit /etc/ginn/wishes.xml
```

<ginn>
  <global>
<!-- Right button click -->
    <wish gesture="Tap" fingers="2">
      <action name="action70" when="update">
        <trigger prop="tap time" min="20" max="400"/>
        <button>3</button>
      </action>
    </wish>
```Full wishes.xml is in attachment. You can customize it it with help of **man ginn**.
7. Logout and login again.
8. Enjoy!

Please try this howto. Does it work for you?

**UPD:** [Ekoore]("http://www.ekoore.com/") has launched 3 tablets and released [Ubuntu 11.04 based LiveCD]("http://www.ekoore.com/web/it/supporto/download-2/et10ta-2/ubuntu/installazione-ubuntu.html"). Multitouch on T101MT does not work out the box does not work from LiveCD. GINN wishes.xml is in attachment ekoore_wishes.xml.

---

### Post by sirtah on 2011-06-29
Like you, I couldn't get the touchrotate script to work with the ExpressGate button. However, when I use your script - which rotates very nicely - the touch input does not sync with the screen. Any thoughts? 

I have a second gen... 
lsusb:
0486:0186 ASUS Computers, Inc. 
xinput list: 
AsusTek, Inc. MultiTouch(TTI)           	id=10	

Thanks!


p.s. Thanks to everyone for developing this thread. My eee is almost at 100%

---

### Post by druid23 on 2011-07-01
> **sirtah said:**
> 
However, when I use your script - which rotates very nicely - the touch input does not sync with the screen. Any thoughts? 

I have a second gen... 
lsusb:
0486:0186 ASUS Computers, Inc. 
xinput list: 
AsusTek, Inc. MultiTouch(TTI)           	id=10	

Thanks!

I needed to edit the touchrotate script to get the correct device for mine as it didn't quite extract the id correctly.

in your case it looks like it should be 10.

/usr/bin/touchrotate

Either amend to INPUTDEV=10 (from auto) near the top of the file or see if you need to tweak the regex that matches it automatically. For me changing 
```
grep -o 'id=[^ ]*'
```
to
```
grep -o 'id=[^ ]*[0-9]'
```
fixed it for me as the extra " [slave" was being matched as well.

LMK and apologies if that goes over your head. only got my T101MT yesterday so I'm just setting this up now.

---

### Post by sirtah on 2011-07-02
Thanks for the help but that didn't work. Just as an fyi, I also installed utouch and the associated libraries. I don't know if that might be interfering. Thoughts? 

Thanks again

---

### Post by bakinsoda on 2011-07-02
> **bakinsoda said:**
> Hi, I'd like to get the express gate button working with rotating the touchscreen.  I saw this up the thread.

I tried it on Natty beta 2, saved it as rotate.sh, executed it, but no go.  Wondering if it's not working because of natty beta 2 or I'm using an old script.  Can anyone help?  I don't see it documented in the wiki.  Thanks!

Hi, does anyone have the rotate working with the expressgate button on Natty?  It doesn't work for me (first gen) as mentioned [here]("http://ubuntuforums.org/showpost.php?p=10718409&postcount=913").  Would appreciate help on getting it working.

To debug, I tried the `acpi_listen -c 1` command, and when I press the express gate button, I get nothing.  Thanks.

---

### Post by Venomous Woe on 2011-07-10
Thanks to N0rbert for the instructions on how to install uTouch on the T101MT. I got it working on mine. However, there's two small problems with my setup. The touchscreen is not very responsive and my touch pad is much too responsive. Plus, the touchpad sometimes inputs letters (mostly "e" and "w") into text fields. I was hoping to improve sensitivity on the touchscreen while disabling or decreasing sensitvity on the touchpad. Are there any tools that can help me do this?

---

### Post by Gia90 on 2011-07-12
First of all, i'd like to thank you for your great work!
Then i need some help with my Express Gate button..

I'm on Lucid with 2.6.35-25-generic kernel, i've followed all the istructions in the ubuntu documentation and i've also read the whole thread but i still can't make my screen rotate by pressing that button...

I can't install eeepc_acpi_workaround because it isn't for lucid but i've changed grub.cfg adding "acpi_osi=Linux", shouldn't it be enough?

In addition, the ExGate button isn't even recognized by xev...
Someone could help me?
thx and sorry for my english..

---

### Post by Venomous Woe on 2011-07-13
I've run into a bit of a snag with multitouch on Ubuntu 11.04. After geistest failed to detect my touchscreen, I tried to install twofing. The twofing process appears in the system, but it doesn't seem to want to work. I ran twofing --debug, and this is what I got:

> Input device name: "AsusTek, Inc. MultiTouch(YFO)"
XInput device id is 10.
Start calibration
No calibration data found, use default values.
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  46 ()
  Serial number of failed request:  34
  Current serial number in output stream:  36

For completeness, here is my lsusb output data:

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5126 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And here is my xinput -list data:

> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 PC Cam                          	id=11	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
&#8764; AsusTek, Inc. MultiTouch(YFO)           	id=10	[floating slave]


UPD: I ran twofing --debug again, and whenever I press on the screen, it says "Process fingers!" But the twofing daemon still has yet to work  correctly. Any advice?

---

### Post by N0rbert on 2011-07-13
**Venomous Woe**

As I can understand from [your post]("http://ubuntuforums.org/showpost.php?p=11043151&postcount=970") you have different type of touchscreen. My is "AsusTek, Inc. MultiTouch(TTI)", your is "AsusTek, Inc. MultiTouch(YFO)". But ids in USB are the same (0486:0186).

What HID kernel modules do you have? (please post output of [FONT="Courier New"]lsmod | grep hid[/FONT])

---

### Post by Venomous Woe on 2011-07-13
> **N0rbert said:**
> **Venomous Woe**

As I can understand from [your post]("http://ubuntuforums.org/showpost.php?p=11043151&postcount=970") you have different type of touchscreen. My is "AsusTek, Inc. MultiTouch(TTI)", your is "AsusTek, Inc. MultiTouch(YFO)". But ids in USB are the same (0486:0186).

What HID kernel modules do you have? (please post output of [FONT="Courier New"]lsmod | grep hid[/FONT])

I entered your command and this was the output: 

> hid_mosart             12765  0 
usbhid                 41489  1 hid_mosart
hid                    76875  2 hid_mosart,usbhid

---

### Post by N0rbert on 2011-07-13
**Venomous Woe**
There is no [FONT="Courier New"]hid_multitouch[/FONT] module in your lsmod output. It is not good. What version of xserver-xorg-input-evdev do you use - version from Plippo, or original Ubuntu 11.04 (2.6.0-1ubuntu12).
uTouch and GINN are unstable and still need testing. 

According to search([1]("http://ubuntuforums.org/archive/index.php/t-1468376-p-3.html"), [2]("http://ubuntuforums.org/showpost.php?p=9812481&postcount=405")) there are other users with YFO touchscreen with working twofing daemon. 
You can read their posts and try to setup twofing.

---

### Post by Venomous Woe on 2011-07-13
> **N0rbert said:**
> **Venomous Woe**
There is no [FONT="Courier New"]hid_multitouch[/FONT] module in your lsmod output. It is not good. What version of xserver-xorg-input-evdev do you use - version from Plippo, or original Ubuntu 11.04 (2.6.0-1ubuntu12).
uTouch and GINN are unstable and still need testing. 

According to search([1]("http://ubuntuforums.org/archive/index.php/t-1468376-p-3.html"), [2]("http://ubuntuforums.org/showpost.php?p=9812481&postcount=405")) there are other users with YFO touchscreen with working twofing daemon. 
You can read their posts and try to setup twofing.

I think it's the one from Plippo. Synaptic lists the version number as 1:2.6.0-1withoutpatchesubuntu1

And thanks for the links. I'll try to setup twofing

---

### Post by N0rbert on 2011-07-13
> **Venomous Woe said:**
> I think it's the one from Plippo. Synaptic lists the version number as 1:2.6.0-1withoutpatchesubuntu1

And thanks for the links. I'll try to setup twofing

You can still try uTouch+GINN if you install original xserver-xorg-input-evdev package. For me it does not work with Plippo's one.
Use command below or Synaptic (see [my howto]("http://ubuntuforums.org/showpost.php?p=10983589&postcount=963"))
```

sudo apt-get install xserver-xorg-input-evdev=1:2.6.0-1ubuntu12

```

---

### Post by Venomous Woe on 2011-07-13
> **N0rbert said:**
> You can still try uTouch+GINN if you install original xserver-xorg-input-evdev package. For me it does not work with Plippo's one.
Use command below or Synaptic (see [my howto]("http://ubuntuforums.org/showpost.php?p=10983589&postcount=963"))
```

sudo apt-get install xserver-xorg-input-evdev=1:2.6.0-1ubuntu12

```

Tried it. Still doesn't work. The touchscreen still doesn't show up in geistest. 

Any chance you'd know of a place to get the hid_multiouch module?

---

### Post by N0rbert on 2011-07-13
> **Venomous Woe said:**
> Tried it. Still doesn't work. The touchscreen still doesn't show up in geistest. 

Any chance you'd know of a place to get the hid_multiouch module?

You can load it manually with command
```
sudo modprobe hid_multitouch
```
and check that it was loaded with
```
lsmod | grep hid
```

Do you have file /etc/udev/rules.d/70-touchscreen-egalax.rules (extracted from twofing archive)?
```

ls /etc/udev/rules.d/70-touchscreen-egalax.rules

```
This file is not needed for uTouch, you can remove it.
```

sudo rm /etc/udev/rules.d/70-touchscreen-egalax.rules

```

If [FONT="Courier New"]hid_multitouch[/FONT] module loaded, you can try **geistest** again.

---

### Post by Venomous Woe on 2011-07-13
Alright, it says that hid_multitouch is loaded, yet the touchscreen still doesn't show up on geistest. I even removed the 70-touchscreen-egalax.rules file. Where do I go from here?

---

### Post by N0rbert on 2011-07-13
> **Venomous Woe said:**
> Alright, it says that hid_multitouch is loaded, yet the touchscreen still doesn't show up on geistest. I even removed the 70-touchscreen-egalax.rules file. Where do I go from here?

You can reboot, for example and run [FONT="Courier New"]sudo modprobe hid_multitouch[/FONT] after reboot. May be geistest detect touchscreen after that...

---

### Post by Venomous Woe on 2011-07-13
N0rbert, I want to give you a hug and buy you a beer. Geistest just now detected the touchscreen. I'll be running tests on it with Touchegg momentarily. 

Thank you so much for all your help.

---

### Post by N0rbert on 2011-07-13
> **Venomous Woe said:**
> N0rbert, I want to give you a hug and buy you a beer. Geistest just now detected the touchscreen. I'll be running tests on it with Touchegg momentarily. 

Thank you so much for all your help.
:)
No problem, you are welcome. 
Have a nice time with your T101MT.

---

### Post by Gia90 on 2011-07-18
> **Gia90 said:**
> First of all, i'd like to thank you for your great work!
Then i need some help with my Express Gate button..

I'm on Lucid with 2.6.35-25-generic kernel, i've followed all the istructions in the ubuntu documentation and i've also read the whole thread but i still can't make my screen rotate by pressing that button...

I can't install eeepc_acpi_workaround because it isn't for lucid but i've changed grub.cfg adding "acpi_osi=Linux", shouldn't it be enough?

In addition, the ExGate button isn't even recognized by xev...
Someone could help me?
thx and sorry for my english..

No one can help me?

---

### Post by coffen on 2011-07-18
> **Gia90 said:**
> 
[QUOTE=Gia90;11059216]
Originally Posted by Gia90 View Post
First of all, i'd like to thank you for your great work!
Then i need some help with my Express Gate button..

I'm on Lucid with 2.6.35-25-generic kernel, i've followed all the istructions in the ubuntu documentation and i've also read the whole thread but i still can't make my screen rotate by pressing that button...

I can't install eeepc_acpi_workaround because it isn't for lucid but i've changed grub.cfg adding "acpi_osi=Linux", shouldn't it be enough?

In addition, the ExGate button isn't even recognized by xev...
Someone could help me?
thx and sorry for my english..
No one can help me?[/QUOTE]

For installing the eeepc_acpi_workaround, have a look here --> [https://help.ubuntu.com/community/T101MT#Basic%20steps](https://help.ubuntu.com/community/T101MT#Basic%20steps)

---

### Post by dubis on 2011-07-27
Hello everybody, 

When I install the eeepc-acpi-workaround egalax-multitouch-driver-common eeepc-brightness-workaround eeepc-powersave pakages I lost the bleutooth USB dongle usage. 

I can restore the bluetooth usage after a purge of the packages below.... So I did a list of the packages which disturb the blueeutooth :
eepc-touchpad-twofingers
eeepc-acpi-workaround
eeepc-powersave

There is a list with the package don't disturb the bluetooth :
egalax-multitouch-driver-common
eeepc-brightness-workaround  

These last ones still installed on my Eee PC T101MT

Thank for your help...

---

### Post by deraltefritz on 2011-07-27
Hello everyone,

the guide at [https://help.ubuntu.com/community/T101MT]("https://help.ubuntu.com/community/T101MT") states that for second gen screens (e.g. 0486:0186), there's only a 1-finger touchscreen workaround without working screen rotation. Is that still the case? Judging from N0rbert's and Venomous Woe's posts, it seems to work now. Can someone confirm that? And if it works, do we need 'Twofing 0.0.9b'  or 'utouch', or even both to get it working?

Thanks guys,
Fritz

---

### Post by hiltun on 2011-07-28
I've just started running Ubuntu 11.04 on my T101MT. I'm running off a 2GB SD Card using "Universal-USB-Installer-1.8.5.8" I would like to know if there is a way I can get a better screen resolution. I was able to do it in Windows7 by editing a value in regedit.exe. Everything was mushed together but I still liked it better. Is there a way I can get a better 16:9 ratio?

I've read about editing "/etc/X11/xorg.conf" but I could not find it.  

I would like something close to 1280x720.

Thanks,

I'm also getting this error when I use apt-get
> Setting up eeepc-acpi-workaround (0.1-ppa3) ...
/usr/sbin/grub-probe: error: cannot stat `aufs'.
dpkg: error processing eeepc-acpi-workaround (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 eeepc-acpi-workaround
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by gauravm on 2011-08-02
hi everyone I have done everything on the "official guide" for the t101mt on ubuntu but my webcam is still upside down...can anyone tell me what I can do to figure out why this is?

---

### Post by Fyodor_K on 2011-08-02
Hi,

I've just installed 11.04 on a T101MT and trying to make everything work. Touchscreen works but there's no multitouch. I tried to follow the community documentation instructions and I couldn't make it work. twofing doesn't even start - it just dies silently, no entry in the process list. I haven't debugged it.  

Then I followed N0rbert's instructions and two-finger gestures started to work poreprly. Two problems: touchrotate stopped to work(only rotates the screen but not input) and three/four finger gestures are still not recognized by geistest/ginn.(Is the latter possible with this device?)

Any ideas?

Thanks.

---

### Post by deraltefritz on 2011-08-02
> **Fyodor_K said:**
> Hi,

I've just installed 11.04 on a T101MT and trying to make everything work. Touchscreen works but there's no multitouch. I tried to follow the community documentation instructions and I couldn't make it work. twofing doesn't even start - it just dies silently, no entry in the process list. I haven't debugged it.  

Thanks.

Have you tried twofing-0.0.9b ? I got it working with that version, using the modification Norbert has suggested :

cat /etc/udev/rules.d/70-touchscreen-egalax.rules 
BUS=="usb",ACTION=="add",KERNEL=="event*",SYSFS{idProduct}=="0186",SYMLINK+="twofingtouch",RUN+="/bin/chmod a+r /dev/twofingtouch"

However, one problem remains for me: whenever I perform a single touch on the touch screen, twofing seems to perform a extended touch. That means :
1) when I use an onscreen keyboard, every key gets pressed a dozen times before the touch stops, even though I just tap the screen for a split second. 
2) when I touch a link, there's a delay of a few seconds before the button releases and the brower navigates to that link

So basically there's a delay between the click and the release event (much longer than the 100 ms specified in CLICK_DELAY, and modifying that number doesn't seem to do anything).
I tried modifying 'gestures.c', but haven't been able to fix it. I could 'disable' single touch moves by modifying 'gestures.c' around line 502, e.g.:

if (hadTwoFingersOn == 0 && !isButtonDown()) {
if (timeDiff(fingerDownTime, currentTime) > CLICK_DELAY) {
/* Delay has passed, no gesture been performed, so perform single-touch press now */
pressButton();
releaseButton() ; // HACK
}
}

but then of course you can't drag a window somewhere anymore, so it's a bad hack. 
Maybe you have an idea, Plippo?


> **Fyodor_K said:**
> 
Then I followed N0rbert's instructions and two-finger gestures started to work poreprly. Two problems: touchrotate stopped to work(only rotates the screen but not input) and three/four finger gestures are still not recognized by geistest/ginn.(Is the latter possible with this device?)

Any ideas?

Thanks.

Same problem for me, touchscreen and touchpad aren't rotated when using touchrotate scripts. The performance of twofing gestures arr much smoother though, so I'd prefer to use twofing, if the problem can be resolved.

And no, the device only captures 2 touches at one time (hence the twofing daemon).

---

### Post by Fyodor_K on 2011-08-03
Here's a solution for the rotation problem:
[https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)

---

### Post by bakinsoda on 2011-08-04
Sorry this is off-topic, but was wondering if anyone tried Meego with the Asus T101MT?  [This]("http://forum.meego.com/showthread.php?t=278") post shows unsuccess, but was wondering if any users on the ubuntu forums tried it and if possible, share their experiences.

---

### Post by mmtaylor on 2011-08-10
I just got a Eee PC T101MT-BU37-BK. I've been following the instructions here and on this page: [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

So far, everything has been really clear and easy to deal with, however I have one thing left to fix:

webcam is still upside down

I tried to follow the instructions about how to install the libv4l fix, but I'm getting this output with an error:

```
make -C lib install
make[1]: Entering directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib'
make -C libv4lconvert install
make[2]: Entering directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib/libv4lconvert'
mkdir -p /usr/include
install -p -m 644 ../include/libv4lconvert.h /usr/include
mkdir -p /usr/lib/libv4l
install -m 755 libv4lconvert.so.0 /usr/lib
cd /usr/lib && \
	  ln -f -s libv4lconvert.so.0 libv4lconvert.so
install -m 755 *-decomp /usr/lib/libv4l
mkdir -p /usr/lib/pkgconfig
install -m 644 libv4lconvert.pc /usr/lib/pkgconfig
make[2]: Leaving directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib/libv4lconvert'
make -C libv4l2 install
make[2]: Entering directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib/libv4l2'
mkdir -p /usr/include
install -p -m 644 ../include/libv4l2.h /usr/include
mkdir -p /usr/lib/libv4l
install -m 755 libv4l2.so.0 /usr/lib
cd /usr/lib && \
	  ln -f -s libv4l2.so.0 libv4l2.so
install -m 755 v4l2convert.so.0 \
	  /usr/lib/libv4l/v4l2convert.so
mkdir -p /usr/lib/pkgconfig
install -m 644 libv4l2.pc /usr/lib/pkgconfig
make[2]: Leaving directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib/libv4l2'
make -C libv4l1 install
make[2]: Entering directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib/libv4l1'
cc -Wp,-MMD,"libv4l1.d",-MQ,"libv4l1.o",-MP -c -I../include -fvisibility=hidden -fPIC -I../../include -D_GNU_SOURCE -g -O1 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4l1.o libv4l1.c
libv4l1.c:53:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [libv4l1.o] Error 1
make[2]: Leaving directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib/libv4l1'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/megan/Downloads/v4l-utils-0.7.92-test/lib'
make: *** [install] Error 2
```

Probably related, the Skype fix ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

``` doesn't work either.

I am also having trouble getting twofing to work. I installed version 0.9b and it seemed to compile and install just fine. Rebooted, and it doesnt launch. I don't see it come up in system monitor, and if I run twofing in the terminal and then run killall twofing I get "twofing: No such file or directory" Any ideas??

---

### Post by crazyness003 on 2011-08-18
> **Fyodor_K said:**
> Here's a solution for the rotation problem:
[https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)

Hey All. I just recently got my T101 as a replacement for my dead HP TX1000 (PS: NEVER BUY HP)

Anyway, I was kinda not happy with the lack of screen + touch-screen rotation for my second-gen T101. So. I did some research and as Fyodor_K pointed out, that method does work. So I did some more calculations and ended up modifying the file that was added in the scripts to rotate the screen + touch-screen.

Anyway, this is what I did:
```

#!/bin/sh

if [ $# -eq 1 ];
then OUTPUT=auto
     INPUTDEV=auto
     ROTATION=$1
elif [ $# -eq 3 ];
then OUTPUT=$1
     INPUTDEV=$2
     ROTATION=$3
else echo "Usage: touchrotate [output inputdevice] left|right|inverted|normal|toleft|toright|topdown|current"
     exit 1
fi

if [ $OUTPUT = auto ];
then LV=$(xrandr|grep -i 'LVDS')
     OUTPUT=$(echo $LV | sed 's/ connected.*//')
fi

if [ $INPUTDEV = auto ];
then EG=$(xinput list|grep -E 'AsusTek, Inc. MultiTouch(TTI)')
     INPUTDEV=$(echo $EG | grep -o 'id=[^ ]*' | sed 's/id=//')
fi

ORIGROTATION="$ROTATION"

case $ROTATION in
    toleft|toright|topdown|current)
       XR=$(xrandr)
       if echo $XR | grep -q "$OUTPUT connected [^ ]* left";
       then
           case $ROTATION in
                toleft) ROTATION=inverted ;; 
                toright) ROTATION=normal ;; 
                topdown) ROTATION=right ;; 
        current) ROTATION=left ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* right";
       then
           case $ROTATION in
                toleft) ROTATION=normal ;; 
                toright) ROTATION=inverted ;; 
                topdown) ROTATION=left ;; 
        current) ROTATION=right ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* inverted";
       then
           case $ROTATION in
                toleft) ROTATION=right ;; 
                toright) ROTATION=left ;; 
                topdown) ROTATION=normal ;; 
        current) ROTATION=inverted ;;
           esac
       else
           case $ROTATION in
                toleft) ROTATION=left ;; 
                toright) ROTATION=right ;; 
                topdown) ROTATION=inverted ;; 
        current) ROTATION=normal ;;
           esac
       fi
esac

case $ROTATION in
    normal) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1;;
    left) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1;;
    right) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' 0 1 0 -1 0 1 0 0 1;;
    inverted) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' -1 0 1 0 -1 1 0 0 1;;
    *) echo "Unknown option"; exit 1;;
esac

if [ $ORIGROTATION != current ];
then
       xrandr --output $OUTPUT --rotate $ROTATION
fi

```

Now, whenever I call a command like 
```
 touchrotate toleft 
```Everything works as it should.

The only issue I have is how to map this command using the Keyboard Shortcuts program to the Express Gate/Rotate Screen Button by the Power Button. 

If I can do that, it will work just as intended. It'll just keep rotating to the left every time the button is pressed for the desired position.

If anyone can figure that out, I'll be more than happy to know about it. Thanks.

PS: I felt boss for making all of those Matrix calculations with rotation. Really gave me some epic nostalgia.:)

---

### Post by coffen on 2011-08-19
> **crazyness003 said:**
> Hey All. I just recently got my T101 as a replacement for my dead HP TX1000 (PS: NEVER BUY HP)

Anyway, I was kinda not happy with the lack of screen + touch-screen rotation for my second-gen T101. So. I did some research and as Fyodor_K pointed out, that method does work. So I did some more calculations and ended up modifying the file that was added in the scripts to rotate the screen + touch-screen.

Anyway, this is what I did:
```

#!/bin/sh

if [ $# -eq 1 ];
then OUTPUT=auto
     INPUTDEV=auto
     ROTATION=$1
elif [ $# -eq 3 ];
then OUTPUT=$1
     INPUTDEV=$2
     ROTATION=$3
else echo "Usage: touchrotate [output inputdevice] left|right|inverted|normal|toleft|toright|topdown|current"
     exit 1
fi

if [ $OUTPUT = auto ];
then LV=$(xrandr|grep -i 'LVDS')
     OUTPUT=$(echo $LV | sed 's/ connected.*//')
fi

if [ $INPUTDEV = auto ];
then EG=$(xinput list|grep -E 'AsusTek, Inc. MultiTouch(TTI)')
     INPUTDEV=$(echo $EG | grep -o 'id=[^ ]*' | sed 's/id=//')
fi

ORIGROTATION="$ROTATION"

case $ROTATION in
    toleft|toright|topdown|current)
       XR=$(xrandr)
       if echo $XR | grep -q "$OUTPUT connected [^ ]* left";
       then
           case $ROTATION in
                toleft) ROTATION=inverted ;; 
                toright) ROTATION=normal ;; 
                topdown) ROTATION=right ;; 
        current) ROTATION=left ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* right";
       then
           case $ROTATION in
                toleft) ROTATION=normal ;; 
                toright) ROTATION=inverted ;; 
                topdown) ROTATION=left ;; 
        current) ROTATION=right ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* inverted";
       then
           case $ROTATION in
                toleft) ROTATION=right ;; 
                toright) ROTATION=left ;; 
                topdown) ROTATION=normal ;; 
        current) ROTATION=inverted ;;
           esac
       else
           case $ROTATION in
                toleft) ROTATION=left ;; 
                toright) ROTATION=right ;; 
                topdown) ROTATION=inverted ;; 
        current) ROTATION=normal ;;
           esac
       fi
esac

case $ROTATION in
    normal) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1;;
    left) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1;;
    right) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' 0 1 0 -1 0 1 0 0 1;;
    inverted) xinput set-prop 'AsusTek, Inc. MultiTouch(TTI)' 'Coordinate Transformation Matrix' -1 0 1 0 -1 1 0 0 1;;
    *) echo "Unknown option"; exit 1;;
esac

if [ $ORIGROTATION != current ];
then
       xrandr --output $OUTPUT --rotate $ROTATION
fi

```

Now, whenever I call a command like 
```
 touchrotate toleft 
```Everything works as it should.

The only issue I have is how to map this command using the Keyboard Shortcuts program to the Express Gate/Rotate Screen Button by the Power Button. 

If I can do that, it will work just as intended. It'll just keep rotating to the left every time the button is pressed for the desired position.

If anyone can figure that out, I'll be more than happy to know about it. Thanks.

PS: I felt boss for making all of those Matrix calculations with rotation. Really gave me some epic nostalgia.:)

Maybe this post could point you in the right direction :)
[http://ubuntuforums.org/showpost.php?p=10410974&postcount=787](http://ubuntuforums.org/showpost.php?p=10410974&postcount=787)

---

### Post by Newbunty1 on 2011-08-22
I've recently purchased EeePC T101MT-BU37-BK with dual-core Atom N570 and installed Ubuntu 11.04 following the instructions from [community guide]("https://help.ubuntu.com/community/T101MT"). Touchscreen, rotation, camera work fine. Upside down camera is easily fixed by editing the file 'v4l-utils-0.7.92-test' to include the correct camera (see the post from February 1st, 2011, I actually just changed the camera name, save the file, and compiled).

However, I have a problem with screen brightness. The Fn+F5-6 works, however when the brightness is at maximum it is still not as bright as it should be. If I press Fn+F1 and put the PC to sleep and turn it on again, the screen is much brighter (as it was in Windows) and if I now press Fn+F6 (to increase the brightness) the screen actually dims and I can't recover the maximum brightness even though Fn+F6 is at maximum. Same thing happens to me in a few other situations, e.g. being on ac power and switching from external monitor to laptop monitor. The screen is bright, but if I press Fn+F6 or Fn+5 it dims and the maximum brightness can't be recovered. The brighness also changes if I rotate the screen to the right. Please HELP !!!

---

### Post by crazyness003 on 2011-08-23
> **coffen said:**
> Maybe this post could point you in the right direction :)
[http://ubuntuforums.org/showpost.php?p=10410974&postcount=787](http://ubuntuforums.org/showpost.php?p=10410974&postcount=787)

Haha. Well, I guess I may have overplayed my knowledge of hacking. With that being said, I have no Idea what that bash script will do; how do I call it; WHEN do I call it and how will that help me map the button press to touchrotate toright.

I guess I really have to take a gander at this thread from the begining....I was hoping to avoid that. And it seems the community documentation page based off this thread is a bit lacking.

<sigh> This is the reason why I love and hate linux.
To the batcave!

---

### Post by coffen on 2011-08-23
> **crazyness003 said:**
> Haha. Well, I guess I may have overplayed my knowledge of hacking. With that being said, I have no Idea what that bash script will do; how do I call it; WHEN do I call it and how will that help me map the button press to touchrotate toright.

I guess I really have to take a gander at this thread from the begining....I was hoping to avoid that. And it seems the community documentation page based off this thread is a bit lacking.

<sigh> This is the reason why I love and hate linux.
To the batcave!
The scrpit should be run as a deamon, i.e. you run it once at startup or start it manually.
It will look for an acpi event "0000007b" which on my first gen asus is the express button.
If yuo look at the script it will then call Plippos [FONT="Fixedsys"]**touchrotate**[/FONT] script with the parameter [FONT="Fixedsys"]**toright**[/FONT].
I think you know what will happen if you change toright to something else :)

```
#!/bin/bash
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
      touchrotate toright
    fi
done
```

Hope this helps.

---

### Post by mmtaylor on 2011-08-23
OK, so I've gotten everything working perfectly expect for multitouch.

I downloaded  twofing-0.0.9b, but when I try to run it in the CLI nothing happens. I try to scroll, nothing. I go back to CLI and type ```
killall twofing
``` and get ```
twofing: no process found
``` I try ```
twofing --debug
``` and get ```
twofing: No such file or directory
```

I've been reading through every post here and I feel like the answer is somewhere in there but I'm a n00b and need things spelled out for me. Can anyone help me get this working?

---

### Post by crazyness003 on 2011-08-23
> **coffen said:**
> The scrpit should be run as a deamon, i.e. you run it once at startup or start it manually.
It will look for an acpi event "0000007b" which on my first gen asus is the express button.
If yuo look at the script it will then call Plippos [FONT="Fixedsys"]**touchrotate**[/FONT] script with the parameter [FONT="Fixedsys"]**toright**[/FONT].
I think you know what will happen if you change toright to something else :)

```
#!/bin/bash
while true
do
    acpi=$(acpi_listen -c 1 |sed -e 's/ +/ /g'|cut -d' ' -f 3)

    if [ $acpi == "0000007b" ] 
    then
      touchrotate toright
    fi
done
```

Hope this helps.
Thank you so much. This did exactly what I needed.
Just to clarify for anyone who doesn't understand, I took the BASH script and saved it to a text file as '[FONT="Lucida Console"]touchrotate-eg-button[/FONT]' and saved it in [FONT="Lucida Console"]/usr/bin[/FONT]. Set it to executable and then added an entry in the Startup Applications as follows:
[FONT="Lucida Console"]Name: Express Gate Rotate Button
Command: /usr/bin/touchrotate-eg-button
Comment: *whatever you want*[/FONT]
After saving. Log out and log back in and try your new, awesome-working rotate button.

That's another fix on the list. Now, on to other things.

If anyone can direct me to the fix for:
1. Multi-touch touch-screen for 2nd-gen, 'AsusTek, Inc. MultiTouch (TTI)'
2. Invert the upside-down webcam. I don't know how to identify it.
3. Stable use of multi-touch touch-pad, 'SynPS/2 Synaptics TouchPad'
4. Better battery management

Useful info:
I'm running 11.04 Natty Narwhal (awesome name, by the way)
```
uname -a
Linux troggie-3 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux
```
And I've tried everything from [Community Documentation on ASUS T101MT (link)](https://help.ubuntu.com/community/T101MT). Maybe not successfully. I'm willing to try again with more explanation, if anyone would kindly guide me.

Again, thanks.

---

### Post by coffen on 2011-08-25
> **crazyness003 said:**
> Thank you so much. This did exactly what I needed.
np mate. Glad to be able to help :)

---

### Post by N0rbert on 2011-09-02
> **crazyness003 said:**
> 

That's another fix on the list. Now, on to other things.

If anyone can direct me to the fix for:
1. Multi-touch touch-screen for 2nd-gen, 'AsusTek, Inc. MultiTouch (TTI)'

You can read my previous posts about MT on 2nd-gen - [#962]("http://ubuntuforums.org/showpost.php?p=10981072&postcount=962") and [#963]("http://ubuntuforums.org/showpost.php?p=10983589&postcount=963"). I use GINN and UTouch. 
Multi-touch gestures work (i.e. rotate and zoom in eog). 
Better GINN gestures script is needed.

---

### Post by draconomia87 on 2011-09-04
I was having some odd issues with single-click events on twofing 9b - single clicks would register, but once I lifted my finger it would be like I was holding down the mouse button, it didn't register the finger lift. Single clicks worked fine when twofing wasn't running.

Poked around in the source a bit and noticed the releaseButton function was missing an ```
XFlush(display);
``` call like the one in pushButton - adding that and recompiling seems to have fixed it. Figured I'd share the fix in case anyone else is having this problem.

---

### Post by beastrace91 on 2011-09-08
Word of warning to anyone thinking of trying 3.0 kernel (11.10) on their T101MT -

[http://jeffhoogland.blogspot.com/2011/09/can-linux-kill-your-hardware-warning-to.html](http://jeffhoogland.blogspot.com/2011/09/can-linux-kill-your-hardware-warning-to.html)

tl/dr: Latest kernel killed my T101MT dead.

~Jeff

---

### Post by crazyness003 on 2011-09-11
> **N0rbert said:**
> You can read my previous posts about MT on 2nd-gen - [#962]("http://ubuntuforums.org/showpost.php?p=10981072&postcount=962") and [#963]("http://ubuntuforums.org/showpost.php?p=10983589&postcount=963"). I use GINN and UTouch. 
Multi-touch gestures work (i.e. rotate and zoom in eog). 
Better GINN gestures script is needed.

Well this was very helpful. Thanks so much. 

Like you mentioned, the GINN gestures aren't 100% solid, but I now have right-click functionality with the touch-screen. This in tandem with the One Finger Scrolling in Firefox, can mimic a two-finger (right-click) scrolling. There's just a lot of artifacts. Plus, it defaults to scrolling as if doing a page-up/page-down.

I understand this is just a workaround (a good one too), but I was wondering what file to mess around with to try and fine-tune this beast.
is it /etc/ginn/wishes.xml?

Also, when I do 
```
lsmod | grep hid
hid_egalax             12837  0 
hid_mosart             12885  0 
usbhid                 46956  2 hid_egalax,hid_mosart
hid                    91020  3 hid_egalax,hid_mosart,usbhid

```

I'm missing hid_multitouch. IS this bad?

---

### Post by crazyness003 on 2011-09-17
> **beastrace91 said:**
> Word of warning to anyone thinking of trying 3.0 kernel (11.10) on their T101MT -

[http://jeffhoogland.blogspot.com/2011/09/can-linux-kill-your-hardware-warning-to.html](http://jeffhoogland.blogspot.com/2011/09/can-linux-kill-your-hardware-warning-to.html)

tl/dr: Latest kernel killed my T101MT dead.

~Jeff
[S]What do you mean "killed it dead". LIke it's completely tanked. Bricked. Broken. Never going to live, ever again; even by replacing X hardware. That kind of dead?[/S]
From Jeff's blog (paraphrased): The problem was with something changing the display brightness to 0 (zero). A quick Fn + F6 does the trick. 

You scared me there for a minute.

Also, is anyone else having difficulty compiling v4l-utils-0.7.92-test.tar.gz? I keep getting a fatal error with "linux/videodev.h" not existing. Even after following the suggestions from he post [here]("http://ubuntuforums.org/showthread.php?t=1468376&p=10419880").

Any suggestions or other posts I should pay special attention to?

---

### Post by Slartius on 2011-09-23
> **crazyness003 said:**
> [S]What do you mean "killed it dead". LIke it's completely tanked. Bricked. Broken. Never going to live, ever again; even by replacing X hardware. That kind of dead?[/S]
From Jeff's blog (paraphrased): The problem was with something changing the display brightness to 0 (zero). A quick Fn + F6 does the trick. 

Any suggestions or other posts I should pay special attention to?

I just upgraded to oneiric without any problems. Also the screen works without problems. So far (ok, it has been only about 30 minutes) everything works just fine. I just renamed natty to oneiric in sources.list and did dist-upgrade (in the middle I had to use -f to force resolving further dependencies) but so far everything works e. g. touchscreen, rotating screen etc.

---

### Post by Slartius on 2011-09-23
> **crazyness003 said:**
> 
Also, is anyone else having difficulty compiling v4l-utils-0.7.92-test.tar.gz? I keep getting a fatal error with "linux/videodev.h" not existing. Even after following the suggestions from he post [here]("http://ubuntuforums.org/showthread.php?t=1468376&p=10419880").

Any suggestions or other posts I should pay special attention to?

As far as I know the videodev.h has been deprecated. I also had same problems compiling this software. I tried compiling newer version (0.85) and had to additionally install libjpeg62-dev, but it compiled OK. I haven't checked it, but have rather installed v4l-utils from repository and for me, the webcam works perfectly using guvcview.

---

### Post by streifi89 on 2011-09-23
Hi at all,

I am using this awesome tool for my wetab and it is working fine!

But with KDE 4.6.x and 4.7 I have a sick bug and hoping that someone can help, because plippo can not :(

The bug will take affect, when you try for example to mark folders in dolphin (this is not in all windows, only in some). Then, the whole dolphin windows moves. It is like the shortcut "ALT+Left Mouse" in KDE. This shortcut is disabled in my KDE configuration, but twofing moves it anyway :(

The same problem take affect in KDE Softwarecenter (kpackagekit). I can not install any software, because, when I click on "install" the shortcut "move whole window" takes action :(

You can see the bug here: [http://www.youtube.com/watch?v=HeL2j6L5C8s](http://www.youtube.com/watch?v=HeL2j6L5C8s)

For any ideas i would be grateful

---

### Post by Rubykuby on 2011-09-27
I'm considering purchase of one of these. After watching some reviews, though, I was turned down by the sluggish Windows 7 performance. Does it perform much better under Ubuntu? How hard do you have to press the screen for touch recognition?

---

### Post by variona on 2011-10-03
You do not have to press hard at all, positioning works very well. I can not complain about performance with Linux, as a matter of fact I was surprised it works so well under win7 - but it comes configured to run a lot of services I don't need - after throwing them overboard it starts a little bit faster, but compared to Ubuntu it still feels less responsive.
Under win7 I installed vmwareplayer to run winxp (a functionality which seems broken in Ubuntu since 11.04) and it performs as good as a native winxp on an Asus Eee Top.
So no complains from my side - (but I don't use it for games if that was part of the question)

HTH

variona

---

### Post by Guzmanus on 2011-10-16
How do you make the screen rotate? because with
```
xrandr -o right
```
the screen rotates but not the touchscreen, and it just messes with the orientation. Im using a freshly installed 11.10
Installing the egalax drivers didnt work either, as when i do 
> touchrotate right
it just rotates the screen, but not the touchscreen

---

### Post by miegiel on 2011-10-16
> **Guzmanus said:**
> How do you make the screen rotate? because with
```
xrandr -o right
```
the screen rotates but not the touchscreen, and it just messes with the orientation. Im using a freshly installed 11.10
Installing the egalax drivers didnt work either, as when i do 

it just rotates the screen, but not the touchscreen

From [https://help.ubuntu.com/community/T101MT#Touch-Screen](https://help.ubuntu.com/community/T101MT#Touch-Screen) :
> If your touch-screen does not work after this, run lsusb in the terminal. If there is a device named 0486:0186 ASUS Computers, Inc. then you have a second generation tablet where Asus decided to change the hardware around. There is a single touch workaround below. This workaround however, isn't fully compatible with the touch-rotate scripts (installed above) as it doesn't rotate the touch orientation ONLY the screen. A kernel patch is in the works. 

---

### Post by Slartius on 2011-10-20
Well I recently posted about no problems with upgrade to 11.10. It seems I have spoken too soon. I have problems with at-spi daemon (florence virtual keyboard not hiding at all) and with suspend and hibernate, which also do not work. As far as I checked everything should be fixed but it still does not work for me. Am I the only one?

---

### Post by ianni67 on 2011-10-21
I was actually asking for more information about upgrading from 11.04 to 11.10. Anyone upgraded through the upgrade procedure? I'm quite frightened.

---

### Post by Kerilk on 2011-10-21
I upgraded to Ubuntu 11.10 without much trouble.

I had to install the luminosity fix from plippo.
For correct rotation of the touchscreen I modified the touchrotate script to use the Coordinate Transformation Matrix (edit : noticed crazyness003 proposed a similar solution 3 pages ago) :

```
#!/bin/sh

if [ $# -eq 1 ];
then OUTPUT=auto
     INPUTDEV=auto
     ROTATION=$1
elif [ $# -eq 3 ];
then OUTPUT=$1
     INPUTDEV=$2
     ROTATION=$3
else echo "Usage: touchrotate [output inputdevice] left|right|inverted|normal|toleft|toright|topdown|current"
     exit 1
fi

if [ $OUTPUT = auto ];
then LV=$(xrandr|grep -i 'LVDS')
     OUTPUT=$(echo $LV | sed 's/ connected.*//')
fi

if [ $INPUTDEV = auto ];
then EG=$(xinput list|grep -E 'eGalax|MultiTouch')
     INPUTDEV=$(echo $EG | grep -o 'id=[^ ]*' | sed 's/id=//')
fi

ORIGROTATION="$ROTATION"

case $ROTATION in
    toleft|toright|topdown|current)
       XR=$(xrandr)
       if echo $XR | grep -q "$OUTPUT connected [^ ]* left";
       then
           case $ROTATION in
                toleft) ROTATION=inverted ;; 
                toright) ROTATION=normal ;; 
                topdown) ROTATION=right ;; 
		current) ROTATION=left ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* right";
       then
           case $ROTATION in
                toleft) ROTATION=normal ;; 
                toright) ROTATION=inverted ;; 
                topdown) ROTATION=left ;; 
		current) ROTATION=right ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* inverted";
       then
           case $ROTATION in
                toleft) ROTATION=right ;; 
                toright) ROTATION=left ;; 
                topdown) ROTATION=normal ;; 
		current) ROTATION=inverted ;;
           esac
       else
           case $ROTATION in
                toleft) ROTATION=left ;; 
                toright) ROTATION=right ;; 
                topdown) ROTATION=inverted ;; 
		current) ROTATION=normal ;;
           esac
       fi
esac

case $ROTATION in
    normal) xinput set-float-prop $INPUTDEV "Coordinate Transformation Matrix"  1 0 0 0 1 0 0 0 1;;
    left) xinput set-float-prop $INPUTDEV "Coordinate Transformation Matrix"  0 -1 1 1 0 0 0 0 1;;
    right) xinput set-float-prop $INPUTDEV "Coordinate Transformation Matrix"  0 1 0 -1 0 1 0 0 1;;
    inverted) xinput set-float-prop $INPUTDEV "Coordinate Transformation Matrix" -1 0 1 0 -1 1 0 0 1;;
    *) echo "Unknown option"; exit 1;;
esac

if [ $ORIGROTATION != current ];
then
       xrandr --output $OUTPUT --rotate $ROTATION
fi
```

Multitouch (dualtouch in fact) seems to be working as mtview records two simultaneous touches. Nonetheless, when touching a part of the desktop with a finger and adding a close other finger, the touch screen stops responding, and ```
eGalax Inc. USB TouchController: reallocated 4 touches
``` is printed in the Xorg.0.log . Any idea of what might be causing that?

---

### Post by OlivierK on 2011-10-24
Hello everybody

I've used my T101 for about 16 months and through all Ubuntu versions from 10.04 to present. Update to Oneiric was yesterday, and everything seems fine but one (quite big) snag: my computer won't go to sleep or hibernate anymore!

When I try to suspend or hibernate, network shuts, then restart, and nothin else happens, either in plugged or battery mode. I've looked on Oneiric bug list, but couldn't find anything related to this precise problem except for one message above this one.

Any idea about what I should do to get back the sleep & hibernate functions all right ?

---

### Post by Slartius on 2011-10-24
> **OlivierK said:**
> Hello everybody

I've used my T101 for about 16 months and through all Ubuntu versions from 10.04 to present. Update to Oneiric was yesterday, and everything seems fine but one (quite big) snag: my computer won't go to sleep or hibernate anymore!

When I try to suspend or hibernate, network shuts, then restart, and nothin else happens, either in plugged or battery mode. I've looked on Oneiric bug list, but couldn't find anything related to this precise problem except for one message above this one.

Any idea about what I should do to get back the sleep & hibernate functions all right ?

As I posted above, everything but the at-spi daemon (affects florence virtual keyboard auto hide functionality) and hibernate and suspend works as it should. I was doing quite a lot of surfing and I found bug reports for at-spi daemon (bug 810721) and for suspend and hibernate problems (bug 854624, there are different reports for this bug, from not suspending to suspending when it shouldn't, so I don't know if it is the right one), and they all say that it is fixed, but it still does not work for me.  I will probably wait for a while and if no solution is present I will revert to Natty.

---

### Post by miegiel on 2011-10-24
> **Slartius said:**
> As I posted above, everything but the at-spi daemon (affects florence virtual keyboard auto hide functionality) and hibernate and suspend works as it should. I was doing quite a lot of surfing and I found bug reports for at-spi daemon (bug 810721) and for suspend and hibernate problems (bug 854624, there are different reports for this bug, from not suspending to suspending when it shouldn't, so I don't know if it is the right one), and they all say that it is fixed, but it still does not work for me.  I will probably wait for a while and if no solution is present I will revert to Natty.

Suspend works for me in both a clean ubuntu 11.10 and a xubuntu 11.10 upgraded from 11.04. I rarely hibernate and don't know if it works.

Have you tried a fresh ubuntu install instead of upgrading? Sometimes it helps.

---

### Post by Slartius on 2011-10-25
> **miegiel said:**
> Suspend works for me in both a clean ubuntu 11.10 and a xubuntu 11.10 upgraded from 11.04. I rarely hibernate and don't know if it works.

Have you tried a fresh ubuntu install instead of upgrading? Sometimes it helps.

Not yet, I was hoping to avoid fresh install but will probably try it today. If it doesn't work I will probably revert back to Natty.

---

### Post by Slartius on 2011-10-25
Just did a fresh install and suspend works while hibernate doesn't (I will have  to check if everything is OK with swap). The at-spi daemon still doesn't work, but now also the rotate does not work for me in particular, when I press the rotate button, the acpi_listen does not report anything. When I press the shutdown button acpi_listen registers that. Does anybody know if I have to install some packages from plippos repository and where to get them for 11.10 or the source to compile them. Thanks.

---

### Post by Kerilk on 2011-10-26
I managed to bind the rotate button in gnome directly in a custom key shortcut. It appeared as the Tool button. acpi_listen doesn't register an event when I click the button.

---

### Post by OlivierK on 2011-10-28
> **OlivierK said:**
>  my computer won't go to sleep or hibernate anymore!

When I try to suspend or hibernate, network shuts, then restart, and nothin else happens, either in plugged or battery mode. I've looked on Oneiric bug list, but couldn't find anything related to this precise problem except for one message above this one.

Any idea about what I should do to get back the sleep & hibernate functions all right ?

I have filed a bug (#881545) in Launchpad - with no answer so far ; I am currently following a hunch around gconf, dconf & gsettings, as I've checked presence of all necessary software (acpi, pm, etc.) - I suspect a tiny bit of code is getting in the way, and I'm not ready to go all the way to revert to Natty.

While nosing around, I've also come across a warning and fix of a power consumption issue starting with 2.6.3x linux kernel and still not fixed with version 3 - anybody knows anything about that (I mean, is it serious)?

---

### Post by OlivierK on 2011-10-29
*computer won't go to sleep or hibernate anymore :*

Got it! it's the egalax touchscreen packet that goes in the way - I just removed egalax (touchrotate as well), and recovered suspend function (that is after a look at /var/log/pm-suspend.log and seeing that egalax returned an error).

So : touchscreen works, even if I've lost touchrotate function for the time being, and suspend too (haven't tried hibernate 'caus I don't use it, but I guess that should be working as well).

Now I have to work on opening unity session: fuzzing with gconf put me in the jam at that level. any idea ?

---

### Post by linxgr on 2011-11-09
Hello fellow t101mt owners. It's been a long time since I visited this forum because my screen had cracked and now touch works only for half the screen. I was thinking of sending the netvertible for repair and I was wondering what is the status of the multitouch support in 11.10. Has anyone tested it? As far as I'm concerned there is also a newer version of the netbook with a faster processor N570 i think. What screen does that model come with? I have the one with the eGalax 1st gen one but my guess is that I'll get it back with the newest revision which I don't know what is. So the question is does anyone have the newest model and has he checked about the multitouch support with 11.10?

---

### Post by derlaft on 2011-11-18
Hi everybody

Is there virtual keyboard for ubuntu with multitouch support?

---

### Post by mrspacklecrisp on 2011-12-03
> **derlaft said:**
> Hi everybody

Is there virtual keyboard for ubuntu with multitouch support?

Nope.

---

### Post by updatelee on 2011-12-09
Ive been racking my brain trying to get resume to work on my T101MT w/11.10 it worked fine before upgrading.

checking /var/log/pm-suspend.log the suspend portion seems to work fine but there is no ref to it even attempting to resume.

When I try and resume I often get black screen with a cursor sometimes I may get the background image, but nothing more, cant even access tty terminals.

Chris Lee

---

### Post by thenzero on 2011-12-15
I went back to 10.10. Oneiric (and Natty, really) is just too buggy on the T101MT.

I did have suspend/resume working before I downgraded though- just install uswsusp and write a script to use s2disk for the events you want (I just used it for lid close). s2disk is faster anyway.

---

### Post by updatelee on 2011-12-17
I tried s2disk and s2ram and neither appear to work for me, it saves the info when hibernating and turns off the netbook, but when I power it on it boots normally, doesnt resume...

I tried using a swapfile with the correct UUID and offset as well as a swap partition. I put the UUID/offset in 

/etc/default/grub
/etc/initramfs-tools/conf.d/resume

did the appropriate updates and rebooted then tested with

sudo s2disk
and
sudo s2ram

it just doesnt recognize its supposed to resume not boot normally

---

### Post by psykatog on 2011-12-28
Sorry to raise a question if it's already been resolved, but the only solution I found in this thread didn't have any effect on my issue -

On a first-gen t101mt with **K**ubuntu 11.10, everything is working fine for me except that when I rotate the screen, the touchscreen and mousepad are both incorrectly calibrated.  This happens with any means of rotating the screen.  I'd really appreciate it if anyone could help with this, because otherwise this has been a perfect clean install of a new os!
y
EDIT : Here's what appears to be a solution for some people : [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)

And here's the commands I input.  Entirely possible I've done something wrong.
```
$ xinput list-props 'SynPS/2 Synaptics TouchPad' | grep "Coordinate Transformation Matrix"

$ xinput set-prop 'SynPS/2 Synaptics TouchPad' 'Coordinate Transformation Matrix' 0.5 0 1 0 1 0 0 0 1

(The second command didn't have the desired effect, so I tried restoring it with this - )
$ xinput set-prop 'SynPS/2 Synaptics TouchPad' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1

```

---

### Post by Newbunty1 on 2011-12-30
Hi everyone! I have the second generation T101MT (~ 5 month old) running Ubuntu 11.10. I have two big problems:

1) (Almost) everything was running great till about 2 weeks ago, when I noticed that the bottom of the screen (about 1 inch) is not responsive to the stylus or the finger touch. I noticed that on Dec 15 there was an update for the 'egalax-multitouch-driver', could this be the cause? What do I do? Do I need to perform new calibration and how?

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5126 IMC Networks 
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 

2) I followed all the instructions from the Community Documentation and this forum, but I still can not fix the upside-down webcam in Skype. 'Cheese' webcam works fine (not upside-down). Please help!

---

### Post by updatelee on 2012-01-01
I see it was updated Nov 25th 2011
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

I dont see anything newer then that, downloading it now, my internet is super slow here. Hope there is a changelog included. Anyone know any differences ? I was never happy with multitouch (using twofing) was super jerky and pretty much unusable, eneded up uninstalling it and living without it.

that would be nice to see improved. on an unrelated note a decent onscreen keyboard would be nice too. Im currently using onboard, nice keyboard but on windows when you click on any text box the onscreen keyboard automagically appears, that would be nice for linux. all other distro's do that too, android and ios.

---

### Post by pz.daniel on 2012-01-07
Hey guys,

I have a little problem with my rotation button (the small round one). I have mapped the key as written here ([http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt?s](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt?s)[]=t101#screen_rotate_button_10.10_10.04_9.10) and everything works at first sight.
BUT the rotation button is only recognized when I have started a terminal.
So when there's no terminal running the button doesn't work when I start (only start!) a terminal the button works.

It would be great, if anybody could help me :-)
Thank you!

---

### Post by updatelee on 2012-01-08
I was having that issue as well, till I decided to just forgo that and start using eeepc_wmi and asus_wmi in the kernel

```

updatelee@updatelee-T101MT:~$ lsmod | grep wmi
eeepc_wmi              12722  0 
asus_wmi               19296  1 eeepc_wmi

```it gets maped to its own key

```

updatelee@updatelee-T101MT:~$ dmesg | grep -i wmi
[    0.236152] wmi: Mapper loaded
[    6.772548] asus_wmi: ASUS WMI generic driver loaded
[    6.781396] asus_wmi: Initialization: 0x0
[    6.781514] asus_wmi: BIOS WMI version: 0.8
[    6.781751] asus_wmi: SFUN value: 0x0
[    6.845560] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input10

```then I can use a keyboard shortcut in unity to run the touchrotate script

Im currently using kernel 3.2

```

updatelee@updatelee-T101MT:~$ uname -a
Linux updatelee-T101MT 3.2.0 #2 SMP Thu Jan 5 12:25:56 MST 2012 i686 i686 i386 GNU/Linux

```I used it with 3.1 as well, never tried with older. There are alot power enhancement with the newer kernels. Ive got my power usage down alot. with a SSD 120gb drive I get 6h 30min on battery now.

Ive included my kernel config file

---

### Post by elizabeth_b on 2012-02-06
Re: writing using the stylus.

I'm thinking about getting one of these, to use for writing (latex) and annotating pdfs -- while reading and in lectures.

[bakinsoda]("http://ubuntuforums.org/member.php?u=139421") asked a while ago about problems with your hand touching the screen while you're trying to write in xournal (post [241]("http://ubuntuforums.org/showpost.php?p=9535517&postcount=241")).  Was that ever resolved?  I see that the windows version as shipped has software to sort that out, but, I can't stand windows. ;)  So, T101MT owners, can you just sit down and scribble on a pdf with the stylus, or does it become impossible because you can't rest your hand on the screen?

I don't need a touch screen otherwise, so could spend my pennies on a bit more power instead -- but, it would be very nice to be able to mark up pdfs onscreen.
[]("http://ubuntuforums.org/member.php?u=139421")

---

### Post by elizabeth_b on 2012-02-07
Let me be sure I've absolutely got this right: if I buy this laptop, and I happen to get one with a "second generation" screen (surely likely?) then I will *not* be able to rotate the touchscreen together with the screen -- even after applying the fix 
sudo rmmod usbhid sudo rmmod hid sudo modprobe hid sudo modprobe usbhid quirks=0x0486:0x0186:0x0040??

but only (possibly??) if I compile an upstream kernel?

Well, in that case, I won't get one.  I wanted the touch screen to be able to mark up A4 pdfs and if I can't rotate it to portrait view, there's no point (and compiling custom kernels just isn't in my life plan).

I've edited the wiki so that this point is made clearly at the top of it; I was about to buy the machine when I noticed.  If I have misunderstood please edit back.

[https://help.ubuntu.com/community/T101MT#Touch-Screen](https://help.ubuntu.com/community/T101MT#Touch-Screen)

---

### Post by miegiel on 2012-02-07
AFAIK ubuntu isn't really tablet (rotating touchscreen) friendly yet. I'm not sure what you mean with *"marking up .pdf's"*, but an android tablet that works out of the box might be more convenient. If you want one with a keyboard, take a look at the *Eee Transformer*. I heard it also runs [BackTrack]("http://en.wikipedia.org/wiki/BackTrack"), so it might run ubuntu too (if you like to be able to run something else than android on it).

When this machine dies I think I'll get a [Lenovo ThinkPad X Series Convertible Tablet]("http://www.lenovo.com/products/us/laptop/thinkpad/xtablet-series/"), but I haven't looked into linux compatibility yet and it's in a totally different price range.

---

### Post by elizabeth_b on 2012-02-08
Thanks Miegel.  Yes, the transformer would probably be the perfect thing to get for the uses I mentioned (marking up pdfs = scribbling on them).  But unfortunately my laptop just broke and I really need a new proper laptop.  Would have been nice to satisfy my desire for a touch screen and pdf scribbling at the same time, but I'll have to live without for now.

That Lenovo does look very shiny, but sadly a long way out of my price range.  Actually it's a bottom-end ordinary Lenovo I've just ordered myself -- btw if anyone else was thinking of helpfully telling me how I could be sure a second-gen screen would work, it's too late now ;)

---

### Post by variona on 2012-02-13
Hi Elizabeth,

I have a second gen screen and I have it touchrotating nicely! All you need to do is change some parameters in plippos original touchrotate script as those are written for first generation screens. (I actually explained this in a previous post in this thread - see below). I'm not using twofing(multitouch), but handwriting detection works fine for me, so I think pdf marking should be possible.

Please note: I still use Ubuntu 11.04 on the T101MT.

[http://ubuntuforums.org/showthread.php?p=10933854#post10933854](http://ubuntuforums.org/showthread.php?p=10933854#post10933854)

---

### Post by elizabeth_b on 2012-02-13
Variona,

Good to hear (though too late for me, I've bought something else).  

The reason I thought what I did, was from reading the wiki page
[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)
Especially:

[INDENT]If your touch-screen does not work after this, run lsusb in the terminal. If there is a device named **0486:0186 ASUS Computers, Inc.**  then you have a second generation tablet where Asus decided to change  the hardware around.  There is a single touch workaround below.  This  workaround however, isn't fully compatible with the touch-rotate scripts  (installed above) as it doesn't rotate the touch orientation ONLY the  screen. A kernel patch is in the works. 
...
**Special Note:** An upstream kernel 2.6.38 has been tested  with the T101MT and this second generation touch-screen works (albeit  only single touch) without the above modprobe commands.  The driver is  included in that kernel.  In order to compile an upstream "mainline"  kernel, follow this link: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)


[/INDENT]I'm afraid I didn't see your post; I read quite a bit of this thread, but it's extremely long.


To help other potential new users, could I suggest you edit the wiki page yourself, explaining what you did?  Then I'll remove the paragraph I inserted at the top -- which simply pointed out what the page itself said (and still says) 2/3 of the way down.

---

### Post by variona on 2012-02-16
As I had to set up a new T101MT, I took the chance to write the necessary steps into the wiki and to rewrite some parts. I hope that my explanations are easy enough to follow.

Thanks go out to all who made this possible!

---

### Post by notatjoke on 2012-03-11
Hello everyone,

I followed the instructions yesterday and everything worked well for me. Even the rotation button did work ... until yesterday evening. The command "touchrotate right | left ..." still works, but it seems my T101MT doesn't recognize my hardware button anymore. When I am at keyboard shortcut tools and want to edit the shortcut with rightclick, there is now an "Ø" there. I habe googled that and I found out that the "Ø" probably means "dead key" - But the button worked before and I don't see why it shouldn't now.

Had anyone similiar problems? Help?!

*Edit - Some notes:*
I have an T101MT first generation (eGalax) and 11.04. Natty Narwhal installed - Got everything except the rotate button working: twofing, etc.

---

### Post by bakinsoda on 2012-03-15
Hi,

Finally have some spare time to tinker with this device (1st gen) again.  I recently installed Linux Mint 12.  Touchscreen works, camera works, and was able to map the express gate button.  Two finger scroll on touchscreen does not work.  Any thoughts?

---

### Post by Plippo on 2012-03-18
Hi to all twofing and touchrotate users out there,

I haven't been able to follow the posts here for some time, but I've recognized that twofing and touchrotate are used now with quite a few different touchscreen devices. Of course, it's not really user friendly that all who don't use the T101MT egalax screen have to manually edit the touchrotate script and the twofing udev rule every time for them to work on the different devices.[B]

So, here is a little request:[/B] If you use twofing and/or touchrotate on a touchscreen other than the 0eef:480d eGalax one, would you please post the outputs of **lsusb** and **xinput --list** here so I'm able to include the IDs of all the devices? Please also write whether you are using twofing, touchrotate or both.

When I have the ids, I additionally plan to add twofing to the PPA for Precise so you won't need to manually compile it.

Thanks in advance!

---

### Post by miegiel on 2012-03-18
Hi **Plippo**

I saw they're using your script here too [http://forums.debian.net/viewtopic.php?f=7&t=59055](http://forums.debian.net/viewtopic.php?f=7&t=59055)

Thought you might like to know ;)

---

### Post by variona on 2012-03-19
> **Plippo said:**
> Hi to all twofing and touchrotate users out there,

...would you please post the outputs of **lsusb** and **xinput --list** here ...
Thanks in advance!

You are welcome

---

### Post by Plippo on 2012-03-25
@miegiel: Thanks for the info!

@variona: Thank you, I'm gonna add these to the list for Precise.

---

### Post by mrspacklecrisp on 2012-03-29
It's been a while.

I can't install an extra GB of RAM. I know for a fact that this is not only the correct kind but has also been successfully installed in a Windows 7 T101MT. I physically checked a bunch of times to be sure that it was placed correctly. The BIOS just won't recognize it... Has anyone encountered similar problems?

By the way, apparently we've been missing a "bootbooster" option which shortens startup by cutting into the time the BIOS shows up. You need to do some tricks to get the option back. This tutorial corroborates a bunch of other eeepc tutorials, so I think it's safe to say it will work. [http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04#bum](http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04#bum)

---

### Post by bakinsoda on 2012-04-26
Just did a quick fresh install of Xubuntu 12.04.  Set up netbook as in Natty instructions (just the ppa stuff).  The only thing I think is broken is touchscreen, in particular, when i launch xournal, i can tap for a dot, but cannot draw a line.

---

### Post by tohuwawohu on 2012-04-27
Hi all,

i need some help with testing 12.04 on my T101MT. I've tried to boot the i386 image, but there's no screen to select the language or to choose between booting the live system and installing 12.04. It directly boots into the live system desktop. 

For some seconds, a gray box appears in the lower left edge of the screen, afterwards a blinking dash in the upper left screen, and then plymouth appears booting the live system. If i hit the esc key while the gray box appears, a window appears with two buttons. But there's no text, just a window with title bar and two buttons, so i don't know what to choose. If i hit the left button (using the keyboard), i get a boot: promt. How to proceed from there?

Any idea how to fix this?

---

### Post by mrspacklecrisp on 2012-04-27
12.04 does not detect the microphone. I wonder if this has to do with yesterday's kernel update...

---

### Post by tohuwawohu on 2012-04-28
After getting the 12.04 live disk to run and update my system to 12.04, i experience heavy problems regarding the touchscreen. Since egalax shows up in my xinput list, i assume i own a "first-generation" device.

Using 12.04 using the mouse works completely fine - until i try to use the stylus on the touch screen. After some seconds of using the stylus, the screen gets unresponsive, even to mouse actions. I can still move the mouse pointer around, but clicking (using the stylus, the mouse or the touchpad) doesn't give any response. The only remedy is to restart the X server using ctrl + alt + backspace.

Another problem: even in the short time the stylus is usable, xournal doesn't accept lines drawn, only dots where i start with the stylus. Drawing lines works instead on jscribble and cellwriter (but, as i wrote, only for some seconds). I'll try to find any information in the X logs or in syslog, but up to now, i don't have any clue what the problem might be. Any help is greatly appreciated.

florian

---

### Post by mrspacklecrisp on 2012-04-29
> **mrspacklecrisp said:**
> 12.04 does not detect the microphone. I wonder if this has to do with yesterday's kernel update...

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/990211]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/990211")[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/990211](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/990211)

Here's the bug report.

---

### Post by miegiel on 2012-04-29
> **mrspacklecrisp said:**
> 12.04 does not detect the microphone. I wonder if this has to do with yesterday's kernel update...

I didn't need to use the microphone yet, so I can't say if it's related to an update (kernel or other). *edit:* I just booted the 3.2.0-23 kernel, it's not the kernel :)

I opened sound (settings) and I don't have a microphone listed under the input tab either. However a microphone does appear when I plug in an external mic. For some reason it doesn't switch to the built in mic (as happens in the output tab when you plug-in / unplug your headphone).

---

### Post by Newbunty1 on 2012-04-29
> **tohuwawohu said:**
> After getting the 12.04 live disk to run and update my system to 12.04, i experience heavy problems regarding the touchscreen. Since egalax shows up in my xinput list, i assume i own a "first-generation" device.

Using 12.04 using the mouse works completely fine - until i try to use the stylus on the touch screen. After some seconds of using the stylus, the screen gets unresponsive, even to mouse actions. I can still move the mouse pointer around, but clicking (using the stylus, the mouse or the touchpad) doesn't give any response. The only remedy is to restart the X server using ctrl + alt + backspace.

Another problem: even in the short time the stylus is usable, xournal doesn't accept lines drawn, only dots where i start with the stylus. Drawing lines works instead on jscribble and cellwriter (but, as i wrote, only for some seconds). I'll try to find any information in the X logs or in syslog, but up to now, i don't have any clue what the problem might be. Any help is greatly appreciated.

florian


I experience the exactly same problem after a fresh install of 12.04 on the 'second generation' T101MT. :(

---

### Post by mrspacklecrisp on 2012-04-29
I kinda think this every time I upgrade, but did anyone notice a 45 minute drop in battery life (with jupiter +jupiter eee on power-savings mode)? I'm pretty sure I should be getting 5hr15minutes, although some is shaved off by unity. (Who can't wait for Elementary Luna?)

Edit: Nevermind, the power indicator is just bad. It's hovered at 4:3something for 30 minutes.

---

### Post by bakinsoda on 2012-05-01
> **bakinsoda said:**
> Just did a quick fresh install of Xubuntu 12.04.  Set up netbook as in Natty instructions (just the ppa stuff).  The only thing I think is broken is touchscreen, in particular, when i launch xournal, i can tap for a dot, but cannot draw a line.

Also, even though i have the brightness package installed, i don't think my screen is at its best with brightness.  A manual execution of "sudo setpci -s 00:02.0 f4.b=ff" didn't do anything.

---

### Post by Newbunty1 on 2012-05-02
Hi Plippo, here are the outputs of lsusb and xinput --list for the 'second generation' T101MT. In my case, after fresh install of 12.04, the touchscreen does not work, see post #1055.
Thanks!

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 13d3:5126 IMC Networks 
Bus 003 Device 002: ID 0486:0186 ASUS Computers, Inc. 
Bus 001 Device 005: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 001 Device 006: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business

~$ xinput --list
&#9121; Virtual core pointer                 	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer        id=4	[slave  pointer  (2)]
&#9116;   &#8627; AsusTek, Inc. MultiTouch(TTI)     id=10	[slave  pointer  (2)]
&#9116;   &#8627; Dell Premium USB Optical Mouse    id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad        id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                 id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard      	id=5	[slave  keyboard (3)]
    &#8627; Power Button                     	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                        	id=7	[slave  keyboard (3)]
    &#8627; Power Button                     	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                     	id=9	[slave  keyboard (3)]
    &#8627; Logitech USB Keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Logitech USB Keyboard            	id=13	[slave  keyboard (3)]
    &#8627; USB 2.0 PC Cam                   	id=14	[slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons         	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard     	id=16	[slave  keyboard (3)]

---

### Post by miegiel on 2012-05-02
> **bakinsoda said:**
> Also, even though i have the brightness package installed, i don't think my screen is at its best with brightness.  A manual execution of "sudo setpci -s 00:02.0 f4.b=ff" didn't do anything.

Maybe this wil fix it: ([from Debian User Forums HOWTO: Squeeze on ASUS T101MT, first post step 5]("http://forums.debian.net/viewtopic.php?t=59055"))
> 
edit your /etc/default/grub file so the &#8220;GRUB_CMDLINE_LINUX_DEFAULT&#8221; line has &#8220;acpi_osi=Linux acpi_backlight=vendor&#8221; after it.
example: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

***EDIT:***
Instead of
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=Linux[/COLOR] acpi_backlight=vendor"
```
I'm using
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=eeepc-laptop[/COLOR] acpi_backlight=vendor"
```
in */etc/default/grub* now :D makes the screen even brighter.

---

### Post by mrspacklecrisp on 2012-05-03
We need to update the docs for this.

Bugs I'm still experiencing are:


Microphone not detected (bug filed and confirmed)


Touch driver shuts off after a while, do not know how to restart it (had this issue for a while now)


Twofing whitelist fails (also had this for a while)

---

### Post by psykatog on 2012-05-05
Just upgraded to Kubuntu 12.04, and had a few minor issues -

One is that when I use the touchscreen, the next time I touch the touchpad the pointer automatically registers at the bottom-right corner of the screen (in my case, the click brings up a calendar).  

Another is probably due to a user error on my part.  I installed the v4lutils deb package from the FTP link on the community documentation page for the t101t, and while it works for Cheese, SKype is still upside down.  Following the instructions on that page hasn't worked, perhaps because although the deb package was installed, there's no usr/lib/libv4l.  Should I reinstall the package from the .tar?  Seems unnecessary if the camera is already working for other applications.

---

### Post by mrspacklecrisp on 2012-05-05
> **tohuwawohu said:**
> Another problem: even in the short time the stylus is usable, xournal doesn't accept lines drawn, only dots where i start with the stylus. Drawing lines works instead on jscribble and cellwriter (but, as i wrote, only for some seconds). I'll try to find any information in the X logs or in syslog, but up to now, i don't have any clue what the problem might be. Any help is greatly appreciated.

florian
I'm experiencing this same problem in Xournal with a first gen. It does not occur when I uncheck 'use Xinput.' I also notice that not by unchecking this box I don't get the annoying errors where I make dots through the tool panel to the canvas or where I get straight lines from the tool panel to the point I start to write unless I tap the canvas.

---

### Post by Sharaazad on 2012-05-06
The mic is not detected correctly, it doesn't appear in the audio input window. However, it works: sound recorder works,skype works too.

---

### Post by mrspacklecrisp on 2012-05-06
> **Sharaazad said:**
> The mic is not detected correctly, it doesn't appear in the audio input window. However, it works: sound recorder works,skype works too.

Confirmed. Super weird, too.

---

### Post by atomp on 2012-05-06
I've also just upgraded to 12.04 (Kubuntu) and just wanted to confirm some touchscreen issues.

Having the same cursor jumping behaviour as Psykatog, the cursor will jump to the bottom right of the screen upon using the touchpad after the touchscreen.

I am also seeing problems with twofing. I've attempted using 0.0.9a, 0.0.9b and the repo version 0.1.0. The package appears to install correctly (twofing is in /usr/bin at any rate) however calling twofing from command line does not produce any noticeable change. Calling 'killall twofing' returns "no processes found", so I'm guessing that twofing is failing to execute.

However it could be a kernel update-driver issue causing both of these, I'm not sure.

I hope this helps.

Using the Plippo PPA packages
Kubuntu 12.04
Kernel - 3.2.0-24-generic
KDE - 4.8.2

1st Generation eGalax touchscreen.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 002 Device 002: ID 045e:070f Microsoft Corp. 
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 

xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController           id=13   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; Microsoft LifeChat LX-3000                id=10   [slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                  id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                     id=14   [slave  keyboard (3)]

---

### Post by Sharaazad on 2012-05-07
> **atomp said:**
> I've also just upgraded to 12.04 (Kubuntu) and just wanted to confirm some touchscreen issues.


I don't know if this matters, but I noticed that in 12.04 there is Ginn installed. Ginn captures screen events and send them as mouse/keyboard events. Maybe there is a conflict with twofing.
Also notice that applications (nautilus,evince,...) now have "native" touch scrolling thanks to Ginn.

---

### Post by atomp on 2012-05-07
Ginn was a good bet, but it's currently not installed on the device, so it doesn't look like that's the issue.

On the subject of Ginn, does anyone know if it would work with the T101MT? I might give it a go myself in a bit just to see.

---

### Post by Sharaazad on 2012-05-08
> **atomp said:**
> Ginn was a good bet, but it's currently not installed on the device, so it doesn't look like that's the issue.

On the subject of Ginn, does anyone know if it would work with the T101MT? I might give it a go myself in a bit just to see.

As I said, I found it installed after my fresh install of 12.04. It gives you scrolling in every application. It should be possible to define gestures, haven't tried yet. I'll let you know.

edit: I found this [http://ubuntuforums.org/showthread.php?t=1635401](http://ubuntuforums.org/showthread.php?t=1635401)

edit2: This video shows that Ginn works well on T101MT: [http://www.youtube.com/watch?v=u-6EzHruzX0](http://www.youtube.com/watch?v=u-6EzHruzX0)
I have to understand why it only gives me 1-fingered gestures.

edit3: [https://bugs.launchpad.net/ubuntu/+source/ginn/+bug/985121](https://bugs.launchpad.net/ubuntu/+source/ginn/+bug/985121)

---

### Post by atomp on 2012-05-08
Cheers for the info, toying with this is certainly now high on my 'stuff to do that isn't work' list. :)

---

### Post by Sharaazad on 2012-05-10
I tried the latest version (0.2.5) but it shows the same error.
I can say however that the single touch scrolling is not provided by ginn: it works even with ginn removed.

---

### Post by bakinsoda on 2012-05-11
> **miegiel said:**
> Maybe this wil fix it: ([from Debian User Forums HOWTO: Squeeze on ASUS T101MT, first post step 5]("http://forums.debian.net/viewtopic.php?t=59055"))

Tried that but it didn't fix the screen brightness issue.  I KNOW the brightness is not at its maximum because when the xubuntu desktop screen first appear, it is very bright, and then it dims immediately after.  I do admit that the dim is not DRASTICALLY dark, but I would prefer my screen be as bright as when it first appeared.  Thoughts?

---

### Post by Plippo on 2012-05-11
Hello,

I also experienced these issues with the touchscreen and Xinput in 12.04. One problem is that the evdev input driver has been extended by some "multi-touch enhancements" which unfortunately don't work quite well on resistive screens like the T101MT's. One result is that when you enable Xinput in Xournal or use other programs that require Xinput, like Mypaint, it doesn't work any more. Also I had the problem too that after a short time the input system hangs completely.

Back in 11.04 and 11.10, these "enhancements" were also there, but as ubuntu-Specific patches to evdev, so I was able to provided version of evdev in my PPA without these patches. But now, these patches have become "official" in evdev and it would be much more difficult to provide such a package.

In the meantime, my workaround is to use twofing - as it bypasses the normal input system, Xinput doesn't even know you touched the screen so these bugs don't occur. Unfortunately, twofing can't support pressure sensitivity or single-finger scrolling. Also, blacklisting specific applications in twofing doesn't work at the moment (but on the other hand, as long as "normal" touch handling in Xinput doesn't work, blacklisting would be counter-productive).

If you want to try it, you can install twofing from the PPA and add the command **twofing --wait** to your startup applications and then _reboot_. This way you should at least get normal touch input and two-fingered gestures back. (If you had installed twofing manually before, please make sure to remove the file /etc/udev/rules.d/70-touchscreen-egalax.rules because in the PPA version, it is installed to /lib/udev/rules.d/). 

**@atomp**: If you have problems with twofing, you can try starting it with **twofing --debug** in order to see the output. In your case, maybe the udev rule wasn't installed correctly - maybe you still have an old 70-touchsreen-egalax.rules in /etc/udev/rules.d. If this is the case, remove it, make sure that the twofing package from the PPA is installed and reboot.

---

### Post by Plippo on 2012-05-11
@bakinsoda: It looks that the brightness fix is correctly applied on your machine but then, after login, the power manager reduces it again. I have no Xubuntu to try it out, but I'm sure you can set the default brightness the power manager shall use in the system settings (in Ubuntu, it's under System Settings › Brightness and Lock)

---

### Post by atomp on 2012-05-11
@Plippo It was the udev rules causing a problem and it's all fixed now, huge thanks. :)

---

### Post by bakinsoda on 2012-05-12
> **Plippo said:**
> @bakinsoda: It looks that the brightness fix is correctly applied on your machine but then, after login, the power manager reduces it again. I have no Xubuntu to try it out, but I'm sure you can set the default brightness the power manager shall use in the system settings (in Ubuntu, it's under System Settings &#8250; Brightness and Lock)

@Plippo thank you for your response, but there is only "Brightness" settings when the computer is inactive in Power Manager under System Settings.  So no go.  Now, I really doubt myself whether my screen is at is maximum brightness or not.  I just KNOW that I see it dimming when the Xubuntu login screen appears...Wonder if it's full brightness, dim for idle, then mouse movement makes screen brighter (back to full brightness???).

UPDATE: yea, I think that was the case.  You can disregard this issue now.

---

### Post by psykatog on 2012-05-13
> **atomp said:**
> @Plippo It was the udev rules causing a problem and it's all fixed now, huge thanks. :)

So your corner-clicking in KDE is gone?  Would you mind translating the fix for the less literate?

PS - Atomp, just curious, have you found any favorite ways to configure KDE for this device?

---

### Post by tohuwawohu on 2012-05-18
Hi plippo, thanks a lot for your help! Using twofing in fact makes touch input working again. I encountered just a little issue: cellwriter doesn't accept character consisting of multiple strokes, it stops recording after the first stroke is finished. Activating or deactivating extended input events doesn't help. Is there a way to get Cellwriter recognize multiple strokes for a singe character with twofing? It seems there's no other stable hand writing tool at the moment.

---

### Post by Plippo on 2012-05-19
@tohuwawohu: You can try starting cellwriter by calling
```
GDK_NATIVE_WINDOWS=1 cellwriter
```
I found this in an old thread and at least for me it seemed to work. But make sure cellwriter is completely closed (killall cellwriter) before.

---

### Post by tohuwawohu on 2012-05-20
> **Plippo said:**
> 
```
GDK_NATIVE_WINDOWS=1 cellwriter
```

@Plippo: marvelous - works, thanks a lot! It ssems that i have to start cellwriter twice before the GUI appears, after this isn't a problem. I've modified the cellwriter.desktop file to use enable GDK_NATIVE WINDOWS using

```
sh -c "GDK_NATIVE_WINDOWS=1 cellwriter"
```

---

### Post by miegiel on 2012-05-22
Because I love quoting myself :D
> **miegiel said:**
> Maybe this will fix it: ([from Debian User Forums HOWTO: Squeeze on ASUS T101MT, first post step 5]("http://forums.debian.net/viewtopic.php?t=59055"))


***EDIT:***
Instead of
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=Linux[/COLOR] acpi_backlight=vendor"
```
I'm using
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=eeepc-laptop[/COLOR] acpi_backlight=vendor"
```
in */etc/default/grub* now :D makes the screen even brighter.

---

### Post by atomp on 2012-05-22
> **psykatog said:**
> So your corner-clicking in KDE is gone?  Would you mind translating the fix for the less literate?

PS - Atomp, just curious, have you found any favorite ways to configure KDE for this device?

@psykatog

Well Plippo proposed deleting the old 70-touchsreen-egalax.rules in /etc/udev/rules.d and then reinstalling the twofing package from the ppa in order to write a new one. This is the only fix that I tried and everything seems to have fixed up nicely, including the jumping cursor.

In reference to your question over KDE configuration, I haven't really configured it any different to my desktop. In that I switched off the netbook mode and went back to a traditional KDE desktop but with smaller interface elements to save screen space. I then use the KDE on-screen keyboard which is perfectly functional and I have the touchrotate options in the favourites of the Application Launcher.

My one gripe over using KDE would be KDM's apparent unwillingness to use an onscreen keyboard on login and lock screens, although I haven't checked yet to see if that was fixed in 4.8.

PS. Sorry about the delayed reply.

---

### Post by Fr333 on 2012-05-23
Hi, 
first time experiencing problems with touchrotate: doesn't rotate touch, so it's the same as typing screenrotate. It all began after upgrading to 12.04, eGalax screen. Don't know what to do or what to attach, please help..
ps never been able to use twofing too!

---

### Post by variona on 2012-05-24
@FR333: Try to find out the name of your input device

```
xinput --list
```

and if it is correctly used in the touchrotate script (i.e. in the xinput part)

---

### Post by bakinsoda on 2012-05-25
> **miegiel said:**
> Maybe this wil fix it: ([from Debian User Forums HOWTO: Squeeze on ASUS T101MT, first post step 5]("http://forums.debian.net/viewtopic.php?t=59055"))


***EDIT:***
Instead of
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=Linux[/COLOR] acpi_backlight=vendor"
```
I'm using
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=eeepc-laptop[/COLOR] acpi_backlight=vendor"
```
in */etc/default/grub* now :D makes the screen even brighter.

This didn't do anything for me.

---

### Post by Fr333 on 2012-05-29
@variona name is eGalax as I said, but I don't know where to check for touchrotate conf files

---

### Post by miegiel on 2012-05-30
> **bakinsoda said:**
> This didn't do anything for me.

You did the *sudo update-grub* thing after editing */etc/default/grub*, right? (just asking)

I'm having some strange effects with it myself. Sometimes it doesn't seem to effect the brightness. And I've removed the stuff from the line in the grub menu (during boot) and my screen stayed bright.

---

### Post by variona on 2012-06-03
@FR333

```
which touchrotate
``` to find it

then use your favourite editor to view/edit it

---

### Post by Fr333 on 2012-06-03
Thanks for the answer! 
But..I don't know what does it mean correctly used though! It seems to be correct. any clues?

---

### Post by variona on 2012-06-08
My status report:

(2nd Gen touchscreen)
o)Upgrade (11.04->11.10->12.04) rendered me without a touch device in xinput --list
o)Fresh install worked fine but some issues as reported by others (jumpy cursor when rotated using prop 'Coordinate Transformation Matrix', no input rotation when using plippos touchrotate script without twofing). I found no bug report in launchpad.
o)with twofing touch works, but touchrotate assumes a wrong screen geometry in left and right mode. After rotation, it seems, the input device (Asus Multitouch) still has the geometry of (normal and inverted mode).twofing debug info states, on every rotation event: "No calibration data found, using default values. Calibration: MinX: 0; MaxX: 3478; MinY: 0 MaxY;3478". I tried  xinput_calibrator which made things worse, and I looked into twofings code but found nothing obvious to explain why it should behave differently on 2nd generation screens.


Cheers
Variona

---

### Post by coffen on 2012-06-18
Anyone got 12.04 working OK with first gen touch screen?

There seems to be some hickups with second gen.
I'm currently running 10.10 on my first gen and would like to hear comments about 12.4 before updating/re-installing.

---

### Post by Stickiler on 2012-07-21
I did a fresh install of 12.04 today on my t101mt, and the only problem I've run into so far is that I can't actually tap the taskbar of any window that uses the default XFCE taskbar. When using Google Chrome, which uses a custom one, I can click the minimise, maximise and exit buttons, however if I'm just browsing folders, using firefox, or any application which uses the default minimise, maximise and close buttons, I can't tap them with the touchscreen to close the window. It just doesn't tap. I also can't drag, or interact with these taskbars in any fashion. Is there something I'm just missing?

---

### Post by mrspacklecrisp on 2012-08-26
> **coffen said:**
> Anyone got 12.04 working OK with first gen touch screen?

There seems to be some hickups with second gen.
I'm currently running 10.10 on my first gen and would like to hear comments about 12.4 before updating/re-installing.
I have not been able to use the touchscreen well in 12.04. I can't really click things, closing the lid kills it.

---

### Post by N0rbert on 2012-09-22
Hello!
> **variona said:**
> My status report:


[LIST]
[*] I upgraded to 12.04 too.
[/LIST]

[LIST]
[*]I can confirm that there is no input rotation in left and right mode (latest version of touchrotate script from Plippo (package egalax-multitouch-driver-common                                               0.3.0-ppa2)).
[/LIST]

[LIST]
[*]Twofing works (I use --click=first option).
[/LIST]
I suggest to use ExpressGate/Rotate button as mouse right click ('xdotool click 3' for right click emulation or 'xdotool key 135' for Menu keyboard button). Acpi event files are in attachment, they work faster than while loop in touchrotate.

I use Gnome Classic. It seems that twofing works strange in it. When I press Applications menu (Menu Bar applet) first level appears, but next levels (for example Applications > Accessories) blinks and disappears. I can navigate these menus only if I hold finger on screen and move it from upper levels to lower ones. I tried --click=center and --click=second. It is not an issue. 
Main Menu applet (only Ubuntu circle) works normaly.

For easy scrolling with finger I removed 'overlay-scrollbar', 'liboverlay-scrollbar' and 'liboverlay-scrollbar3'  and changed GTK theme - make scrollbars wider and removed steppers by gtkrc and gtk.css. The idea is set the following values in gtk-2.0/gtkrc
```

    GtkScrollbar::has-backward-stepper = 0
    GtkScrollbar::has-forward-stepper = 0

    GtkScrollbar::min-slider-length = 20
    GtkScrollbar::slider-width = 20

```and these in gtk-3.0/gtk.css
```

GtkScrollbar {
    -GtkRange-stepper-size: 0;
    -GtkRange-slider-width: 20px;
}

```I edited [Evolve theme]("http://satya164.deviantart.com/art/Evolve-GTK3-Theme-264780816") (gtk-2.0/gtkrc lines 59-60, 63-64, gtk-3.0/gtk.css lines 3-6). It is in attachment.

I tried to create small flowchart in LibreOffice Draw with stylus.  Positioning is bad, I can't move connector lines. Recalibrating touch  screen does not help. So it seems T101MT in tablet mode is not designed for content creation.
[B]
variona,[/B] do you have any problems with hibernate? When I try to hibernate my T101MT, it shuts down, not hibernates. I have swap partition and correct resume option in kernel cmdline (followed [this]("http://askubuntu.com/a/190497") and [this]("http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/") guides).

---

### Post by mrspacklecrisp on 2012-09-25
> **N0rbert said:**
> Hello!



[LIST]
[*] I upgraded to 12.04 too.
[/LIST]

[LIST]
[*]I can confirm that there is no input rotation in left and right mode (latest version of touchrotate script from Plippo (package egalax-multitouch-driver-common                                               0.3.0-ppa2)).
[/LIST]

[LIST]
[*]Twofing works (I use --click=first option).
[/LIST]
I suggest to use ExpressGate/Rotate button as mouse right click ('xdotool click 3' for right click emulation or 'xdotool key 135' for Menu keyboard button). Acpi event files are in attachment, they work faster than while loop in touchrotate.

I use Gnome Classic. It seems that twofing works strange in it. When I press Applications menu (Menu Bar applet) first level appears, but next levels (for example Applications > Accessories) blinks and disappears. I can navigate these menus only if I hold finger on screen and move it from upper levels to lower ones. I tried --click=center and --click=second. It is not an issue. 
Main Menu applet (only Ubuntu circle) works normaly.

For easy scrolling with finger I removed 'overlay-scrollbar', 'liboverlay-scrollbar' and 'liboverlay-scrollbar3'  and changed GTK theme - make scrollbars wider and removed steppers by gtkrc and gtk.css. The idea is set the following values in gtk-2.0/gtkrc
```

    GtkScrollbar::has-backward-stepper = 0
    GtkScrollbar::has-forward-stepper = 0

    GtkScrollbar::min-slider-length = 20
    GtkScrollbar::slider-width = 20

```and these in gtk-3.0/gtk.css
```

GtkScrollbar {
    -GtkRange-stepper-size: 0;
    -GtkRange-slider-width: 20px;
}

```I edited [Evolve theme]("http://satya164.deviantart.com/art/Evolve-GTK3-Theme-264780816") (gtk-2.0/gtkrc lines 59-60, 63-64, gtk-3.0/gtk.css lines 3-6). It is in attachment.

I tried to create small flowchart in LibreOffice Draw with stylus.  Positioning is bad, I can't move connector lines. Recalibrating touch  screen does not help. So it seems T101MT in tablet mode is not designed for content creation.
[B]
variona,[/B] do you have any problems with hibernate? When I try to hibernate my T101MT, it shuts down, not hibernates. I have swap partition and correct resume option in kernel cmdline (followed [this]("http://askubuntu.com/a/190497") and [this]("http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/") guides).

Is that so? For me, twofing does not function, nor does multitouch, but recently ubuntu updated some tablet-related packages and the kernel seems to handle the screen perfectly, even has pressure sensitivity. I haven't worked on it lately, but mypaint has considered touches to all be one line for a while now... Getting the z issue. 

Pantheon-session has also added life to this old tablet. Elementary has a great suite of lightweight applications, and I don't have to worry about unity's inconsistent handling of touch input.

---

### Post by N0rbert on 2012-09-29
**mrspacklecrisp,** thank you. Elementary looks interesting. Installed it from their ppa (ppa:elementary-os/daily). It looks like a hybrid of Gnome 3 and Unity.
But it's not touch friendly. May be KDE Plasma Active became more useful.

I have 2nd Gen T101MT, so there are no problems with twofing.
[SIZE=2]
[COLOR=Gray]offtopic: I got the best user experience on T101MT with android-x86 asus-laptop CD image ([android-x86-4.0-RC2-asus_laptop.iso]("http://android-x86.googlecode.com/files/android-x86-4.0-RC2-asus_laptop.iso")) installed to SD card.[/COLOR][/SIZE]

---

### Post by JorgeGhersa on 2012-09-29
> **Stickiler said:**
> I did a fresh install of 12.04 today on my t101mt, and the only problem I've run into so far is that I can't actually tap the taskbar of any window that uses the default XFCE taskbar. When using Google Chrome, which uses a custom one, I can click the minimise, maximise and exit buttons, however if I'm just browsing folders, using firefox, or any application which uses the default minimise, maximise and close buttons, I can't tap them with the touchscreen to close the window. It just doesn't tap. I also can't drag, or interact with these taskbars in any fashion. Is there something I'm just missing?

Follow us on this bug report: [https://bugzilla.xfce.org/show_bug.cgi?id=9327](https://bugzilla.xfce.org/show_bug.cgi?id=9327)

---

### Post by mrspacklecrisp on 2012-10-08
> **N0rbert said:**
> **mrspacklecrisp,** thank you. Elementary looks interesting. Installed it from their ppa (ppa:elementary-os/daily). It looks like a hybrid of Gnome 3 and Unity.
But it's not touch friendly. May be KDE Plasma Active became more useful.

I have 2nd Gen T101MT, so there are no problems with twofing.
[SIZE=2]
[COLOR=Gray]offtopic: I got the best user experience on T101MT with android-x86 asus-laptop CD image ([android-x86-4.0-RC2-asus_laptop.iso]("http://android-x86.googlecode.com/files/android-x86-4.0-RC2-asus_laptop.iso")) installed to SD card.[/COLOR][/SIZE]

I've gotten twofing to work now. Mypaint z-stroke problem is still happening. It's not a hybrid of anything, it's a small set of really fast, efficient software. It can be made gorgeous, and for me it's very touch friendly, especially now that I have twofing working. Android is a lot of fun, even if crippling in some ways and a total battery hog. Did you manage to make a persistent drive? If so, how'd you do it? Also, we desperately need to update the wiki.
[IMG]http://i46.tinypic.com/wiv9na.png[/IMG]

---

### Post by jayb151 on 2012-10-20
hey all,
I'm rather new to Ubuntu, though I've had my 101mt for some time now. I'm wondering, is it possible to change the resolution to 1024x768?  When I'm running windows I am able to go through regedit and add that custom resolution even though it is over the normal settings. I am having a heck of a time figuring out how to do the same thing in ubuntu!

I also tried the toggle-zoom thing to allow me to see things that are just off the screen, but I'm still not able to move my mouse all the way to the very corner, so what's the use? 

I'm also trying to assign the toggle zoom command to the express gate button for ease of use. Any help would be greatly appreciated!

---

### Post by updatelee on 2012-12-25
Ok, didnt see this posted elsewhere on here so I'll do it, hopefully it hasnt already been covered.

Got the touchscreen working when the screen is rotated.

First install [eGalax drivers]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")

then create a touchrotate script, if youve already got one either create a new script or overwrite the old one.

```

#!/bin/sh

if [ $# -eq 1 ];
then OUTPUT=auto
     ROTATION=$1
elif [ $# -eq 3 ];
then OUTPUT=$1
     ROTATION=$3
else echo "Usage: touchrotate [output inputdevice] left|right|inverted|normal|toleft|toright|topdown|current"
     exit 1
fi

if [ $OUTPUT = auto ];
then LV=$(xrandr|grep -i 'LVDS')
     OUTPUT=$(echo $LV | sed 's/ connected.*//')
fi

ORIGROTATION="$ROTATION"

case $ROTATION in
    toleft|toright|topdown|current)
       XR=$(xrandr)
       if echo $XR | grep -q "$OUTPUT connected [^ ]* left";
       then
           case $ROTATION in
                toleft) ROTATION=inverted ;; 
                toright) ROTATION=normal ;; 
                topdown) ROTATION=right ;; 
		current) ROTATION=left ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* right";
       then
           case $ROTATION in
                toleft) ROTATION=normal ;; 
                toright) ROTATION=inverted ;; 
                topdown) ROTATION=left ;; 
		current) ROTATION=right ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* inverted";
       then
           case $ROTATION in
                toleft) ROTATION=right ;; 
                toright) ROTATION=left ;; 
                topdown) ROTATION=normal ;; 
		current) ROTATION=inverted ;;
           esac
       else
           case $ROTATION in
                toleft) ROTATION=left ;; 
                toright) ROTATION=right ;; 
                topdown) ROTATION=inverted ;; 
		current) ROTATION=normal ;;
           esac
       fi
esac

case $ROTATION in
    normal) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t0/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    left) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t1/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    inverted) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t2/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    right) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t3/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    *) echo "Unknown option"; exit 1;;
esac

if [ $ORIGROTATION != current ];
then
       xrandr --output $OUTPUT --rotate $ROTATION
fi

```

mine is in /usr/bin/touchrotate, you can have it elsewhere, just know where it is.

setup the rest, my user is updatelee, edit to reflect your system

sudo cp /etc/eGTouchL.ini /etc/eGTouchL.ini.bak
sudo chown updatelee.updatelee /etc/eGTouchL.ini*
sudo chmod u+s /usr/bin/eGTouchD

now assign your rotate button to /usr/bin/touchrotate and you'll be good to go. settings->keyboard->application shortcuts->add

UDL

---

### Post by mrspacklecrisp on 2013-02-04
> **updatelee said:**
> Ok, didnt see this posted elsewhere on here so I'll do it, hopefully it hasnt already been covered.

Got the touchscreen working when the screen is rotated.

First install [eGalax drivers]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")

then create a touchrotate script, if youve already got one either create a new script or overwrite the old one.

```

#!/bin/sh

if [ $# -eq 1 ];
then OUTPUT=auto
     ROTATION=$1
elif [ $# -eq 3 ];
then OUTPUT=$1
     ROTATION=$3
else echo "Usage: touchrotate [output inputdevice] left|right|inverted|normal|toleft|toright|topdown|current"
     exit 1
fi

if [ $OUTPUT = auto ];
then LV=$(xrandr|grep -i 'LVDS')
     OUTPUT=$(echo $LV | sed 's/ connected.*//')
fi

ORIGROTATION="$ROTATION"

case $ROTATION in
    toleft|toright|topdown|current)
       XR=$(xrandr)
       if echo $XR | grep -q "$OUTPUT connected [^ ]* left";
       then
           case $ROTATION in
                toleft) ROTATION=inverted ;; 
                toright) ROTATION=normal ;; 
                topdown) ROTATION=right ;; 
		current) ROTATION=left ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* right";
       then
           case $ROTATION in
                toleft) ROTATION=normal ;; 
                toright) ROTATION=inverted ;; 
                topdown) ROTATION=left ;; 
		current) ROTATION=right ;;
           esac
       elif echo $XR | grep -q "$OUTPUT connected [^ ]* inverted";
       then
           case $ROTATION in
                toleft) ROTATION=right ;; 
                toright) ROTATION=left ;; 
                topdown) ROTATION=normal ;; 
		current) ROTATION=inverted ;;
           esac
       else
           case $ROTATION in
                toleft) ROTATION=left ;; 
                toright) ROTATION=right ;; 
                topdown) ROTATION=inverted ;; 
		current) ROTATION=normal ;;
           esac
       fi
esac

case $ROTATION in
    normal) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t0/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    left) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t1/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    inverted) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t2/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    right) sed "s/Orientation\t\t\t[0-9].*/Orientation\t\t\t3/g" /etc/eGTouchL.ini.bak > /etc/eGTouchL.ini;/usr/bin/eGTouchD -f;;
    *) echo "Unknown option"; exit 1;;
esac

if [ $ORIGROTATION != current ];
then
       xrandr --output $OUTPUT --rotate $ROTATION
fi

```

mine is in /usr/bin/touchrotate, you can have it elsewhere, just know where it is.

setup the rest, my user is updatelee, edit to reflect your system

sudo cp /etc/eGTouchL.ini /etc/eGTouchL.ini.bak
sudo chown updatelee.updatelee /etc/eGTouchL.ini*
sudo chmod u+s /usr/bin/eGTouchD

now assign your rotate button to /usr/bin/touchrotate and you'll be good to go. settings->keyboard->application shortcuts->add

UDL

Wonderful. Good work, I will test this within the next few days.

Issues in my mind:
[LIST]
[*]battery life (have experienced slowdown since 12.04)
[*]touchscreen failing after computer is closed (suspended)
[*]interface refinements, programs that help make the screen more useful
[/LIST]

Heh, our thread sure has slowed down hasn't it. A month is a long time to wait for a reply.

EDIT: Weird thing I have just discovered

hid-egalax was merged into hid-multitouch
rmmod hid-multitouch actually works, and kills the touch screen
modprobe hid-multitouch works according to lsmod, but the touchscreen does not actually work again

Relevant discussions:
[http://comments.gmane.org/gmane.comp.handhelds.android.x86/8634](http://comments.gmane.org/gmane.comp.handhelds.android.x86/8634)
[https://groups.google.com/forum/?fromgroups#!topic/android-x86/2V03xG5CAko](https://groups.google.com/forum/?fromgroups#!topic/android-x86/2V03xG5CAko)
[https://patchwork.kernel.org/patch/1780911/](https://patchwork.kernel.org/patch/1780911/)

I am not one to make sense of this. Can an experienced person please take a look?

---

### Post by mrspacklecrisp on 2013-02-04
> **psykatog said:**
> Just upgraded to Kubuntu 12.04, and had a few minor issues -

One is that when I use the touchscreen, the next time I touch the touchpad the pointer automatically registers at the bottom-right corner of the screen (in my case, the click brings up a calendar).  

Another is probably due to a user error on my part.  I installed the v4lutils deb package from the FTP link on the community documentation page for the t101t, and while it works for Cheese, SKype is still upside down.  Following the instructions on that page hasn't worked, perhaps because although the deb package was installed, there's no usr/lib/libv4l.  Should I reinstall the package from the .tar?  Seems unnecessary if the camera is already working for other applications.

Just in case you never figured it out, the correct command is LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

I made a little script for it and changed skype.desktop in ~/.local/usr/share/applications/

My microphone is really awful and noisy now. I was wondering if other guys have that problem or if it's just broken

EDIT: Oh geez, new page. Don't forget to check for new replies on the previous, guys.

---

### Post by coffen on 2013-02-04
> **mrspacklecrisp said:**
> battery life (have experienced slowdown since 12.04)
What is working and what is not working on the 101MT on Ubuntu 12.04 or Ubuntu 12.10?
I have a first gen and I'm still running Ubuntu 10.10.

...Not that slow thread....0 minutes from last post

---

### Post by mrspacklecrisp on 2013-02-06
> **coffen said:**
> What is working and what is not working on the 101MT on Ubuntu 12.04 or Ubuntu 12.10?
I have a first gen and I'm still running Ubuntu 10.10.

...Not that slow thread....0 minutes from last post

Using 12.04 currently.

Basically everything. You wouldn't even have to know Plippo's ppa existed to have a nice time. I've lost an hour or two of battery in distros known for being lightweight though, so idk. I used to get 5 or 6.

You still need to do something to fix the upside down camera, but I think you don't have to install anything, you only need to alter the commands for skype and *maybe* the browser.

The screen's driver has always stopped when the computer lid was shut, but since it was added to the kernel it's been impossible to restart. You can modprobe hid-multitouch, but the screen stays dead. Android folks have had problems with this too- see my post on the previous page.

It would be nice to have some extra tricks for a more touch-friendly interface, but all clicks should work. (They didn't always before.)

---

### Post by variona on 2013-02-11
> **mrspacklecrisp said:**
> 

The screen's driver has always stopped when the computer lid was shut, but since it was added to the kernel it's been impossible to restart. 

If you modify your script by one line it actually works:

```

#! /bin/bash

rmmod hid_multitouch
rmmod usbhid
modprobe hid_multitouch

```
I start it manually, but somwhere I've read about it being done event triggered.

---

### Post by mrspacklecrisp on 2013-02-13
> **variona said:**
> If you modify your script by one line it actually works:

```

#! /bin/bash

rmmod hid_multitouch
rmmod usbhid
modprobe hid_multitouch

```
I start it manually, but somwhere I've read about it being done event triggered.

Sweet baby jesus. Where is this script, /etc/init.d/ ?

---

### Post by variona on 2013-02-18
Dear Mrs.Crisp!

This script is wherever you feel free to save it before you make it executable.

Yours sincerely

Variona

---

### Post by coffen on 2013-02-24
> **variona said:**
> If you modify your script by one line it actually works:

```

#! /bin/bash

rmmod hid_multitouch
rmmod usbhid
modprobe hid_multitouch

```
I start it manually, but somwhere I've read about it being done event triggered.
Maybe put the script in /etc/pm/sleep.d/ with some modifications:

```
#!/bin/bash
case "$1" in
   suspend|hibernate)
      rmmod hid_multitouch
      rmmod usbhid
      modprobe hid_multitouch
   ;;
   resume|thaw)
      export DISPLAY=:0
      sleep 5 && lxpanelctl restart & #Delayed so the battery icon can finish wrecking shop.
   ;;
   *)
      exit 1
   ;;
esac
exit 0
```

..or put the code at the end of the resume|thaw section, right after the sleep 5 command if that works better 4 U.
Feel free to edit it to suit your needs.

---

### Post by variona on 2013-02-27
Thank you coffen!
That's what I did

/etc/pm/sleep.d/80_egalax_touchscreen

```
#!/bin/bash
case "$1" in
        hibernate|suspend)
                rmmod hid_multitouch
                rmmod usbhid
                ;;
        thaw|resume)
                modprobe hid_multitouch
                ;;
        *)
                ;;
esac
exit $?

```

works as expected.

---

### Post by lzv on 2013-03-01
Hello.

Excuse my English, I know it not good. 
It is hard for me find information in many messages. Please write simple instruction to help my problems.

I installed Ubuntu 12.04 64bit on Eee PC T101MT (screen 2nd generation). I use Gnome with no effects. 
Then I added repository ppa: plippo/t101mt and installed all pakages from it. But I have a few problems.

1. Does not work turn the touch screen. For example: I use "touchrotate toright", then press screen on right down corner. But mouse cursor appears on left down.
2. No right click on touch screen. 
3. Gestures do not work on the touchpad.

Please help.

---

### Post by lzv on 2013-03-04
Hello again.

I try to install Ubuntu 32 bit, and I have same problems. But I found some information. 
I added "twofing --wait" to startup applications. Problem 1 was solved! 
But I still have problem with right click. It makes by pressing two fingers. But menu appears between fingers. It is difficult to use.
And still have problem 3. 

Please help.

---

### Post by coffen on 2013-03-06
Just noticed that our wiki page hasn't been updated in a while [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)
We only have instructions for these versions:

Basic steps
    For 11.04, Natty Narwhal
    For 10.10, Maverick Meerkat
    For Ubuntu 10.04, Lucid Lynx

Could someone with 11.10, 12.04, 12.10 or 13.04 kindly update the wiki to reflect those versions also, thanks

---

### Post by psykatog on 2013-04-30
Anyone else updated to 13.04 already? 

The community documentation page, obviously, hasn't been updated since Precise 12.04, but things have been working okay in the meantime.  For 13.04 I've switched over to vanilla Ubuntu, figuring I'll go back to KDE when I get a machine which can appreciate it more.  Things are running okay, I just manually downloaded the latest packages from plippo's launchpad and installed the .debs using the Software Center.  Screen brightness is working, webcam isn't upside-down in cheese, powersaving I couldn't say since my battery is broken and only charges to 44%.  **touchscreen isn't fully functional yet** - if I touch the screen, it tracks it with the cursor, but I can't use it to click anything or scroll, and when I use the trackpad again the cursor is once again appearing in the bottom right-hand corner, which I had previously assumed was a KDE issue.

I'm not a savvy user, so it's possible I've messed up the installation of the necessary packages, but I'm wondering if anyone else has upgraded and if they're having similar issues.  Following the wiki instructions isn't working at all, and you're likely to see this : 
```
W: Failed to fetch http://ppa.launchpad.net/plippo/t101mt/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found
```

EDIT : After doing about all that can be done to customize Unity, let me just say *WOW you are some patient people to have not migrated to KDE after they came up with this.*  The *hell* is that launcher about?  How do you access programs easily through a touchscreen in Unity?

---

### Post by ianni67 on 2013-05-01
> **psykatog said:**
> Anyone else updated to 13.04 already? 

The community documentation page, obviously, hasn't been updated since Precise 12.04, but things have been working okay in the meantime.  For 13.04 I've switched over to vanilla Ubuntu, figuring I'll go back to KDE when I get a machine which can appreciate it more.  Things are running okay, I just manually downloaded the latest packages from plippo's launchpad and installed the .debs using the Software Center.  Screen brightness is working, webcam isn't upside-down in cheese, powersaving I couldn't say since my battery is broken and only charges to 44%.  **touchscreen isn't fully functional yet** - if I touch the screen, it tracks it with the cursor, but I can't use it to click anything or scroll, and when I use the trackpad again the cursor is once again appearing in the bottom right-hand corner, which I had previously assumed was a KDE issue.

I'm not a savvy user, so it's possible I've messed up the installation of the necessary packages, but I'm wondering if anyone else has upgraded and if they're having similar issues.  Following the wiki instructions isn't working at all, and you're likely to see this : 
```
W: Failed to fetch http://ppa.launchpad.net/plippo/t101mt/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found
```

EDIT : After doing about all that can be done to customize Unity, let me just say *WOW you are some patient people to have not migrated to KDE after they came up with this.*  The *hell* is that launcher about?  How do you access programs easily through a touchscreen in Unity?

It is possible to use ubuntu without unity. I disabled unity and installed cairo-dock, customised for my needs.

All the best
ianni

---

### Post by ianni67 on 2013-05-15
Did anyone try Kubuntu Active on T101MT? I tried but it crashed immediately after boot.

---

### Post by psykatog on 2013-05-30
I did, briefly, since I wanted to test pilot it before trying it on my nexus 7.  It worked okay for me, but pretty quickly I missed th full KDE experience.  As of right now, plasma active isn't supporting dolphin or amarok, which are basically my reasons for loving KDE.  I think that something both plasma active and ubuntu's nexus remix could do a much better job of in their advertising is to list what programs from the software center(s) work on the target devices.

The real problem, though, was that multitouch didn't work with plasma active on my t101mt, and without it the distro isn't quite as appealing. Certainly not enough to justify not having dophin or amarok available.


**By the way everyone** - Is anyone else's t101mt dying?  y battery's broken, and I bought a used nexus 7 for less than the cost of buying a new battery.  Asus isn't even shipping replacement batteries anymore!  And you can't use a lot of aftermarket batteries because they're designed to go into the back, whereas ours are in the front.  I think that, in general, my netbook's been requiring more and more trips to the hospital, and I'm not sure whether ubuntu distros are just becoming larger and too much for eee pcs to handle or if the computer is truly dying a slow death.

**ALso, can anyone explain** How to make the cursor not jump to the bottom right corner when using the touchpad after the touchscreen?  Atomp tried helping me before, but I guess I need things spelled out step-by-step a little more thoroughly.

---

### Post by guirnab on 2014-05-09
Hi, guys. Someone still using T101MT? ;)

I just installed 14.04 and tweaked it out a little. A lot of things work out of the box - including Bluetooth, touchscreen (basic), camera, microphone... 

Here are the steps to get almost everithing to work:

1) Install official eGalax driver:
```
[FONT=courier new]$ [/FONT][COLOR=#000000][FONT=Arial][FONT=courier new]wget http://home.eeti.com.tw/touch_driver/Linux/20140318/x86/eGTouch_v2.5.3810.L-x.zip 
$ unzip eGTouch_v2.5.3810.L-x.zip
$ cd [COLOR=#000000][FONT=Arial][FONT=courier new]eGTouch_v2.5.3810.L-x[/FONT][/FONT][/COLOR]
$ sh setup.sh[/FONT]
[/FONT][/COLOR]
```
[COLOR=#000000]and select: Y (agree with patent decl.), 2 (USB), Enter (confirm), 1 (Device number)[/COLOR]
*(note for debian users: i had to change line 188 of setup.sh from "Kminor=${Ktmp%%.*}" to "Kminor=${Ktmp%%[.-]*} to recognize my kernel version")*

after that, you can edit some settings with "eGTouch Utility" app. Even right-click emulation works!

2) Most Fn keys (and ExpressGate key) don't work.
- (From wiki) edit line in [FONT=courier new]/etc/default/grub[/FONT] to:
```
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"[/FONT]
```

- to fix brightness Fn keys:
edit (create) file [FONT=courier new]/usr/share/X11/xorg.conf.d/20-intel.conf [FONT=arial]:[/FONT][/FONT]
```

[FONT=courier new]Section "Device"[/FONT][FONT=courier new]        Identifier  "card0"[/FONT]
[FONT=courier new]                        Driver      "intel"[/FONT]
[FONT=courier new]                        Option      "Backlight"  "intel_backlight"[/FONT]
[FONT=courier new]                        BusID       "PCI:0:2:0"[/FONT]
[FONT=courier new]EndSection[/FONT]
```
and reboot.

- to fix ExpressGate button, Fn + F3 (toggle TouchPad) an Fn + F9 (open System Monitor):
install xbindkeys: 
```

[FONT=courier new]sudo apt-get install xbindkeys[/FONT]
[FONT=courier new]touch ~/.xbindkeys.noauto[/FONT]

```
and create script to launch it on boot[FONT=courier new][FONT=arial]([/FONT]$ nano xbindkeys[FONT=arial] )
[/FONT][/FONT]```

[FONT=courier new]#!/bin/bash[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]sleep 10[/FONT]
[FONT=courier new]/usr/bin/xbindkeys &[/FONT]

```
and move it to [FONT=courier new]/usr/bin
[/FONT]```

[FONT=courier new]chmod 755 xbstart[/FONT]
[FONT=courier new]sudo mv xbstart /usr/bin[/FONT]

```
and add xbstart command to Startup applications.


and edit (create) file .xbindkeysrc ([FONT=courier new]nano ~/.xbindkeysrc[/FONT]):
```

[FONT=courier new]"touchrotate"[/FONT]
[FONT=courier new]XF86ScreenSaver[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]"toggletouchpad"[/FONT]
[FONT=courier new]c:191[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]"gnome-system-monitor"[/FONT]
[FONT=courier new]XF86Launch1[/FONT]

```


and continue to step 3 and 4...





3) Rotating the screen:
i made script named touchrotate ([FONT=courier new]$ nano touchrotate[/FONT])
```
[FONT=courier new]#!/bin/sh[/FONT][FONT=courier new]
[/FONT]
[FONT=courier new]# author Ji&#345;í Kos&#328;ovský[/FONT]
[FONT=courier new]# guirnab@gmail.com[/FONT]
[FONT=courier new]# thanks to guys on http://ubuntuforums.org/Showthread.php?t=2116275[/FONT]
[FONT=courier new]# and http://stackoverflow.com/questions/169964/how-to-prevent-a-script-from-running-simultaneously[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# block the script from running simultaneously[/FONT]
[FONT=courier new]# ExpressGate button executes the script twice[/FONT]
[FONT=courier new]if mkdir /var/lock/.myscript.exclusivelock[/FONT]
[FONT=courier new]then[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# Using current screen orientation proceed to rotate screen and input devices.[/FONT]
[FONT=courier new]case "$rotation" in[/FONT]
[FONT=courier new]    normal)[/FONT]
[FONT=courier new]    # rotate to the left[/FONT]
[FONT=courier new]    xrandr -o left[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axes Swap" 1[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axis Inversion" 1, 0[/FONT]
[FONT=courier new]    ;;[/FONT]
[FONT=courier new]    left)[/FONT]
[FONT=courier new]    # rotate to inverted[/FONT]
[FONT=courier new]    xrandr -o inverted[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axes Swap" 0[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axis Inversion" 1, 1[/FONT]
[FONT=courier new]    ;;[/FONT]
[FONT=courier new]    inverted)[/FONT]
[FONT=courier new]    # rotate to the right[/FONT]
[FONT=courier new]    xrandr -o right[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axes Swap" 1[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axis Inversion" 0, 1[/FONT]
[FONT=courier new]    ;;[/FONT]
[FONT=courier new]    right)[/FONT]
[FONT=courier new]    # rotate to normal[/FONT]
[FONT=courier new]    xrandr -o normal[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axes Swap" 0[/FONT]
[FONT=courier new]    xinput --set-prop "eGalaxTouch Virtual Device for Multi" "Evdev Axis Inversion" 0, 0[/FONT]
[FONT=courier new]    ;;[/FONT]
[FONT=courier new]esac[/FONT]
[FONT=courier new]  sleep 1[/FONT]
[FONT=courier new]  rmdir /var/lock/.myscript.exclusivelock[/FONT]
[FONT=courier new]fi[/FONT]

```
and move it to [FONT=courier new]/usr/bin
[/FONT]```
[FONT=courier new]chmod 775 touchrotate
[/FONT][FONT=courier new]sudo mv touchrotate /usr/bin[/FONT]

```
command[FONT=courier new]touchrotate [/FONT]will rotate the screen 90° ccw.[FONT=courier new][FONT=arial]
[/FONT][/FONT]
4) To disable touchpad with command:
i made script toggletouchpad[FONT=courier new] (nano toggletouchpad)
[/FONT]```
[FONT=courier new]#!/bin/sh[/FONT][FONT=courier new]
[/FONT]
[FONT=courier new]# author Ji&#345;í Kos&#328;ovský[/FONT]
[FONT=courier new]# guirnab@gmail.com[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]isOn="$(synclient | grep TouchpadOff | awk '{print $3}')"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]if [ "$isOn" = 0 ]; then[/FONT]
[FONT=courier new]    #echo $isOn[/FONT]
[FONT=courier new]    synclient TouchpadOff=1[/FONT]
[FONT=courier new]else[/FONT]
[FONT=courier new]    #echo $isOn[/FONT]
[FONT=courier new]    synclient TouchpadOff=0[/FONT]
[FONT=courier new]fi[/FONT]

```
and moved it to [FONT=courier new]/usr/bin
[/FONT]```
[FONT=courier new]chmod 775 toggletouchpad[/FONT][FONT=courier new]sudo mv [/FONT][FONT=courier new]toggletouchpad[/FONT][FONT=courier new] /usr/bin[/FONT]

```

I was unable to fix Fn+F7 and Fn+F4. I am opened to suggestions ;)
Everything else works so far.

---

### Post by uaps2 on 2014-08-18
> **guirnab said:**
> Hi, guys. Someone still using T101MT? ;)

... 

Here are the steps to get almost everithing to work:



Yes, and I appreciate the suggestions for getting everything working. Works in Xubuntu too.

 I think the only thing left that I couldn't get working is the display rotation, but I'm sure that's just because I don't really know what I'm doing because I don't do these kind of tweaks often and I just figure out the specifics of the instructions as I go, with a bit of trial and error. I might give it another crack later if I feel I need to get the rotation working but I sunk a lot of time into tweaking as is and I find it all a bit draining, so I'm happy to just use it in one display configuration for now.

Edit: My apologies, turns out I *can* get the rotation to work if I actually use some of the code in your script in the terminal. Can't quite get it to work via Express Gate at my knowledge level, but I'm pleased enough with the terminal command at the moment. The button may be an adventure for another day.

---

