---
title: "FSC Amilo SI3655"
date: 2008-12-07
forum: Hardware
---

### Post by Tich666 on 2008-12-07
[SIZE="4"][COLOR="Red"]This is a work in progress![/COLOR][/SIZE]

In this thread I'll share my experience of running Ubuntu on a FSC Amilo SI3655. Feel free to share your problems and solutions and I'll try to incorporate them into this post or link to them.

My Hardware Specs are as follows: (hwinfo --short)
```
cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
keyboard:
  /dev/input/event1    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Cantiga Integrated Graphics Controller (X4500HD)
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  wlan0                Intel WLAN controller
  eth0                 Intel Ethernet controller
disk:
  /dev/sda             WDC WD3200BEVT-2
cdrom:
  /dev/sr0             Optiarc DVD RW AD-7640S
bridge:
                       Intel ICH9M LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel Cantiga Memory Controller Hub
firewire controller:
                       JMicron FireWire (IEEE 1394)
bluetooth:
                       Cambridge Silicon Radio Bluetooth Dongle (HCI mode)


```
[SIZE="3"][COLOR="Lime"]
What works:[/COLOR][/SIZE]
[LIST]
[*]WLAN - WPA2 with AES encryption (had to change from channel 13 to 7)
[*]Intel GFX (rather poor performance, see [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582"))
[*]changing the volume and muting with FN-keys
[*]changing the display brightness with the gnome brightness-applet or using xbacklight
[*]switching between LVDS, DVI or both outputs (using xrandr or "System>Preferences>Display"), but only up to a virtual res of 2048x2048 if you want 3D effects (i.e. compiz)
[*]webcam (press fn+f7 to activate!)
[*]bluetooth connection (with SE K750i)
[/LIST]

[SIZE="3"][COLOR="Red"]
What doesn't work (yet):[/COLOR][/SIZE]
[LIST]
[*]brightness control and monitor switching with FN-keys
[/LIST]

[SIZE="3"][COLOR="Navy"]
Untested:[/COLOR][/SIZE]
[LIST]
[*]firewire
[/LIST]

[COLOR="Red"][SIZE="3"]This method is no longer recommended, use xbacklight[/SIZE][/COLOR]
[SIZE="2"][COLOR="Purple"]Changing the display brightness with keyboard shortcuts (with the help of [this]("http://jarrn.wordpress.com/2008/10/09/installing-ubuntu-810-beta-on-samsung-sa1/"))[/COLOR][/SIZE]

Create the following three bash scripts and make them executable, you will have to change the file paths if you don't save your scripts in "~/.bin":

brightness.sh
```
#!/bin/bash

if [ "$1" = "up" ]; then
        echo YOURPASSWORD | sudo -S ~/.bin/video_brightnessup.sh
fi

if [ "$1" = "down" ]; then
        echo YOURPASSWORD | sudo -S ~/.bin/video_brightnessdown.sh
fi

```

video_brightnessup.sh
```
#!/bin/bash

CURRENT=$(cat /sys/devices/virtual/backlight/acpi_video0/brightness)

case "$CURRENT" in

        7)
        echo 7 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        6)
        echo 7 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        5)
        echo 6 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        4)
        echo 5 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        3)
        echo 4 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        2)
        echo 3 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        1)
        echo 2 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        0)
        echo 1 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        *)
        echo 5 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;

esac

```

video_brightnessdown.sh
```
#!/bin/bash

CURRENT=$(cat /sys/devices/virtual/backlight/acpi_video0/brightness)

case "$CURRENT" in

        7)
        echo 6 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        6)
        echo 5 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        5)
        echo 4 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        4)
        echo 3 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        3)
        echo 2 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        2)
        echo 1 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        1)
        echo 0 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        0)
        echo 0 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;
        *)
        echo 5 | tee /sys/devices/virtual/backlight/acpi_video0/brightness
        ;;

esac

```

make them executeable and readable only by your user and group (since the first file contains your root password!)
```
chmod 740 brightness.sh video_brightnessup.sh video_brightnessdown.sh 
```

You can now change the brightness by executing ```
sh brightness.sh up
``` or ```
sh brightness.sh down
```You can also add keybindings to use the scripts, but I've not yet managed to get FN+F8 or FN+F9 to work.

---

### Post by oysteig on 2009-02-09
Thanks for the scripts!

---

### Post by Tich666 on 2009-02-09
You're welcome!

I mostly use the gnome-brightness applet but there's also a CLI program called xbacklight which can set the brightness as a percentage, increase or decrease it.

The advantage of using xbacklight would be that you don't need root privileges for it, but so far I've been too lazy to adapt the scripts.

---

### Post by oysteig on 2009-02-22
By the way; I am having a lot of problems with my wlan connection with this computer. I lose the connection several times a day now. Ubuntu remembers the WPA key, but hitting connect on the dialog box does not help. The only ways to get it back is to reboot or disable/enable wlan and then connect again.

None og my other computers have problems with the wlan, and stay connected through all my problems. And this computer works seemlessly when running Vista =(

So it seems to be an issue only with the AmiloSi3655 when running Ubuntu (8.10, kernel 2.6.27 and 2.6.28 )

Has anyone had the same problem?

--- 
Edit:

I just realized that I lose the network connection when running Windows as well. The difference however, is that Windows (Vista) connects again within seconds, so none of my applications are disrupted from this. Even putty manages to retain its ssh-connection during the network disruption, so I guess its quick.

The only way of noticing in windows is to pay attention to the task bar symbol...

Anyway, I guess I should investigate some more with my other computers, and if they are not affected - get the Amilo reapaired.

---

### Post by noerknhar on 2009-03-07
Hi there.

I bought the same notebook yesterday. I installed 8.10 Ubuntu 64bit on it and it works rather smooth. I experience the same issues with the brightness controls, but that's something I can live with.

-> I am just wondering how you've managed to make your webcam work. I can't even find it using lsusb or hwinfo. Any hints on that? :)
-> I also experience a strange behaviour of the keyboard. It just feels weird, sometimes keys don't work or seem to not work. It's like if you are benchmarking your system and try to type then, the interrupts seem to be ignored/masked sometimes. Can you confirm that? (It could be that I am used to my old notebook with "used" keys, so I'm not sure about this being a real issue...)

Thanks in advance.

Edit: Ah, by the way: I've experienced the "Operating System not found"-issue stated in many forums. Maybe, just to merge it into this "Amilo SI3655"-thread: In order to fix this issue, a "sudo grub-install /dev/sda1" is necessary.

edit #2: Okay, the keyboard-issue seems to be a real issue. It can be nearly reproduced by starting audacious and listening to music. It feels like the old NForce2-Issues with ACPI/APIC (i dont exactly remember). I think I'll try out 32bit live-cd and have a look at the behaviour there.

---

### Post by Tich666 on 2009-03-08
> **noerknhar said:**
> 
-> I am just wondering how you've managed to make your webcam work. I can't even find it using lsusb or hwinfo. Any hints on that? :)
-> I also experience a strange behaviour of the keyboard. It just feels weird, sometimes keys don't work or seem to not work. It's like if you are benchmarking your system and try to type then, the interrupts seem to be ignored/masked sometimes. Can you confirm that? (It could be that I am used to my old notebook with "used" keys, so I'm not sure about this being a real issue...)

edit #2: Okay, the keyboard-issue seems to be a real issue. It can be nearly reproduced by starting audacious and listening to music. It feels like the old NForce2-Issues with ACPI/APIC (i dont exactly remember). I think I'll try out 32bit live-cd and have a look at the behaviour there.

To activate your webcam you have to press fn+f7 which will switch the webcam on (blue LED next to the webcam lights up) and it will be automagically recognized.

I haven't experience the keyboard issue, but I mostly use a wireless keyboard+mouse at home and I'm running the 32bit version.

---

### Post by noerknhar on 2009-03-08
Oh my god, thanks. I am so stupid not to have tried fn+f7. Let's just pretend that never happened...

Thanks about your "confirmation" about the keyboard issue. I'll try out 32bit then.

What's your experience about the runtime of the battery? about 3hours? (medium backlight, WLAN, bluetooth (cant be disabled without disabling WLAN, can it?) surfing, chatting...)

By the way: did you manage to use the notebook internal microphones? If so, could you give me a hint about how to? Thanks in advance.

---

### Post by Tich666 on 2009-03-09
Battery runtime is about 3-4h, depending on backlight brightness, wlan etc.

I've not found a way to really disable bluetooth without disabling wlan either, you can disable some services and shutdown the interface with hciconfig but it will still show up in lsusb and I'm not convinced that suffices to shut it off completely.

I didn't test out the microphones yet because I have no need for them, but if I get round to trying I'll definitely post my results.

edit: Can anybody tell me how I can change the xubuntu tag to ubuntu, because I've switched to gnome because it's less of a hassle to get the brightness control working (gnome-brightness applet) amongst other reasons.

---

### Post by noerknhar on 2009-03-10
Sorry, I don't know how to change the tag to ubuntu. Maybe try writing a PM to a moderator.

I'm very looking forward to hearing about the microphones from you. :popcorn:

---

### Post by oysteig on 2009-03-21
If anyone hears of a better graphics driver, please speak up. This sucks:

glxgears
994 frames in 5.0 seconds = 198.604 FPS
989 frames in 5.0 seconds = 197.719 FPS
992 frames in 5.0 seconds = 198.360 FPS
991 frames in 5.0 seconds = 198.041 FPS
992 frames in 5.0 seconds = 198.347 FPS
976 frames in 5.0 seconds = 195.059 FPS

---

### Post by Tich666 on 2009-03-23
glxgears isn't a very good benchmark as the load on the gfx-card is different from most real world applications (as explained by [raof](http://ubuntuforums.org/showpost.php?p=6852452&postcount=22).

to benchmark your 2d performance, gtkperf is a decent application, these are my results using 2.6.29-rc8 kernel and the xorg-edgers ppa (for intel drivers) on jaunty:

```
GtkPerf 0.40 - Starting testing: Mon Mar 23 09:47:38 2009
100 Rounds

GtkEntry - time:  0.08
GtkComboBox - time:  2.68
GtkComboBoxEntry - time:  1.61
GtkSpinButton - time:  0.55
GtkProgressBar - time:  1.24
GtkToggleButton - time:  0.74
GtkCheckButton - time:  0.49
GtkRadioButton - time:  0.83
GtkTextView - Add text - time:  0.68
GtkTextView - Scroll - time:  0.84
GtkDrawingArea - Lines - time:  3.47
GtkDrawingArea - Circles - time:  2.19
GtkDrawingArea - Text - time:  3.80
GtkDrawingArea - Pixbufs - time:  0.25
 --- 
Total time: 19.45
```

another excellent way to benchmark your system is the [phoronix test suite](http://www.phoronix-test-suite.com/) which is in the repos starting with jaunty.

[Here](http://global.phoronix-test-suite.com/index.php?k=profile&u=tich-17590-15199-24864) you can see my results and system specs (incl. driver versions) of the simple norsetto-shadow benchmark. Atm I'm getting around 11FPS but the textures were broken for me (black&white ant-wars).

Having said all that, intel drivers still fail to deliver what the chip should be capable of on linux, and unfortunately that isn't gonna change much with jaunty. Here's hoping for improvements (KMS, GEM, DRI2 and better drivers) with karmic.
In the meantime you could check out other distros such as fedora or arch, which are more bleeding edge than ubuntu and see if performance is acceptable with the drivers they provide.

edit: just switched the acceleration method to EXA with the following results:

```
GtkPerf 0.40 - Starting testing: Mon Mar 23 10:42:19 2009

GtkEntry - time:  0.10
GtkComboBox - time:  2.96
GtkComboBoxEntry - time:  1.53
GtkSpinButton - time:  0.53
GtkProgressBar - time:  1.32
GtkToggleButton - time:  0.66
GtkCheckButton - time:  0.46
GtkRadioButton - time:  0.94
GtkTextView - Add text - time:  0.65
GtkTextView - Scroll - time:  0.96
GtkDrawingArea - Lines - time:  1.36
GtkDrawingArea - Circles - time:  1.60
GtkDrawingArea - Text - time:  4.72
GtkDrawingArea - Pixbufs - time:  0.89
 --- 
Total time: 18.69
```

The results for norsetto-shadow can be seen on the same page as above, side by side comparison.

---

### Post by noerknhar on 2009-03-23
Got like average 100fps more. I'm using Ubuntu 8.10 with backports and didn't do a thing. If you can give me a hint about how to find out what graphics driver is installed, I can tell you that.

Tich666, any news?

---

### Post by Jon_kanon on 2009-03-24
I also have some problems with the keyboard, as you experience Noerknhar. Im running ubuntu 8.10 32bit os. Does anyone have a solution for this??

---

### Post by noerknhar on 2009-03-24
That's interesting!
I figured that it could be a touchpad-issue. if you do not acidentally hit the touchpad, the effect does not occur in the same way. I also think that it could be related to gnome. It feels as if the windows get their focus, lose it for a short time and get it back again. But I am unsure about that...

---

### Post by Tich666 on 2009-03-24
You can check which gfx driver version you are using with the following command:
```
aptitude show xserver-xorg-video-intel
```
I'm running the one provided by the [xorg-edgers ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) along with the latest kernel (2.6.29) from the [ubuntu kernel ppa](http://kernel.ubuntu.com/~kernel-ppa/mainline/) because I was (and still am) hoping for improvements performance wise.

Unfortunately the pre-compiled kernels don't have KMS support, which would allow me to use plymouth and hopefully fix the suspend issue I'm experiencing.

I've also switched back to UXA because for me it's noticeably faster and more responsive, especially when scrolling in firefox.

No news on the integrated mics, been too busy playing games and it's really low on my priority list, sorry. :P

---

### Post by noerknhar on 2009-04-24
Yo Tich!

Did you manage to connect an external display to your notebook using 9.04 jaunty jackalope and xrandr? If so, could you parse me your script for that? using 8.10 I just had to use xrandr --output XXX --auto, but using 9.04 it's not that easy...

edit: well, okay, it's because of the shitty intel driver. I reverted to version 2.4 (the same as in 8.10) and everything works. Even the stable edge or bleeding edge repositories could not fix that issue.

By the way, are you experiencing any "changes" by using the newest kernel from that repository?

and: anything new on the microphones? Or maybe a hint so that I can start myself? ;)

edit2: Can you give me some further information about your graphics-setup? I'm experiencing real issues with that after this playing around... What's that UXA-thing about for example?

And: I tried these xorg-edgers-updates but they aren't what I am looking for. can you give me a hint on how to "revert" my changes? I deleted the repository from sources.list but the packages are still installed and won't roll back after updating ;)

---

### Post by Tich666 on 2009-04-27
There is a new ppa with the latest stable versions of x-server related packages. It can be found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

To roll back the changes from the xorg-edgers ppa simply uninstall the updated packages and install them again after deleting the repository from the sources list.

For more information about UXA check out: [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
It should contain enough information to get you started and tells you how to enable it.
Atm I'm using the 2.6.30-rc3 kernel, which unfortunately breaks the backlight control for me but brings improved boot speed and gfx performance (together with the latest stable intel driver (2.7.0)). (See [http://www.phoronix.com/scan.php?page=news_item&px=NzIwOA](http://www.phoronix.com/scan.php?page=news_item&px=NzIwOA))

I use xrandr to connect my external 22" WS via DVI:
```
xrandr --output HDMI-1 --auto --output LVDS --auto --right-of HDMI-1
```

You can also check out this thread for more info the intel gfx regressions and how to fix them or revert back the changes: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I tried getting the microphones to work, but so far no luck.
For starters, make sure that the "capture" channels are at full volume with "alsamixer" and "pavucontrol".

---

### Post by noerknhar on 2009-04-27
Hi Tich!

TV still not working (displaying "not supported mode" with all drivers >2.4), so I'll be with 2.4 for another few days (until I can try out the kernel-ppa in combination with newer drivers. maybe something magical happens ;) ). I also tried that PPA you linked just an hour ago, without any success. Performance is great with the new drivers (well, in comparison to 2.4 everything seems to have great performance, whatever), but i can not connect my TV. The mode I try to use is the same for all drivers (xrandr --verbose). I'll report in as soon as I got news, but I don't think that this will be fixed. If this stays as it is, I have to revert back to 8.10 in order to be able to connect to my tv AND still got the performance to play 1080p-movies.
I will check that thread concerning intel gfx regressions you linked later.

concerning the microphones issue: of COURSE all capture channels are maxed. I even tried playing around with pulsemixers and stuff, but that didn't work either (as said, I dunno what to look for.).

---

### Post by balduin on 2009-04-29
Hi Tich666, hi noerknhar,

I followed your postings as I got my Si3655 a few days ago and wanted to thank you for your efforts.  Especially for the hint with the xorg-edgers' PPA -- I managed to improve my gtkperf results from 32 seconds to 12 seconds with the 2.6.30 kernel.

As for the microphones, I had no luck either. Played around with several different settings in alsamixer and tried several programs but it just doesn't want to work.

Regards,
balduin

---

### Post by Tich666 on 2009-04-29
You're welcome balduin.. glad you found it useful.
I should probably update the first post with the relevant links sometime.

do the fn-brightness keys work for you, or the display switching (dvi-out, LVDS)?

I have scripts for the latter and gnome brightness panel applet for the former, but the brightness control is broken in 2.6.30-rc2 and -rc3 for me.

My mtrr problem still persists as well, as I explained in [this post](http://ubuntuforums.org/showthread.php?p=7166634#post7166634)
Could you post the output of fixmtrr.sh for me, as well as the other relevant outputs please?

edit:
As for the microphones.. they work flawlessly in vista with skype, maybe something is wrong with the drivers on linux. I honestly have no idea where to look first.

---

### Post by balduin on 2009-05-05
Hi Tich666,

apologies for answering so late. Neither the Fn+Brightness keys nor the display switching via the Fn keys work. Albeit switching display modes via Gnome does work.

I compared the output of the fixmtrr.sh script with the one you posted in the other thread and they looked exactly the same, i.e. no region marked as write-combined.

I also noticed that hibernation does not work with the new kernel. The system does suspend to disk but does not wake up properly unless I boot with a stable kernel. 

Regards,
balduin

---

### Post by Tich666 on 2009-05-05
Thanks for answering my questions, better late than never. :)

Did you install a testing version and upgrade or install from the release?
I wonder if our mtrr values are correct that way.

I also just failed with suspend-resume using 2.6.30-rc4 and the [x-updates ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/").
Backlight control with xbacklight and the Power Manager Brightness Applet works again though.

---

### Post by noerknhar on 2009-05-07
I confirm that brightness-applet is broken in 30-rc2 and that fixmtrr.sh doesnt work for me either.
I also want to mention a new thread of mine concerning several issues with newer intel drivers than 2.4. Maybe someone of you experienced similar problems? If not, maybe some of you are more experienced with bug reporting and can help me make sure that "the right people" hear about my problem?

[http://ubuntuforums.org/showthread.php?p=7232406](http://ubuntuforums.org/showthread.php?p=7232406)

---

### Post by balduin on 2009-05-09
Hi,

> **Tich666 said:**
> Did you install a testing version and upgrade or install from the release?

I did a clean install with the final version. Did you notice as well that muting the speakers via Fn+F3 does pop up the notifier with a crossed speaker symbol but the sound actually isn't muted? Additionally, both microphones are set to muted when I open the gnome volume control panel, this can not be unset.

Regards

---

### Post by noerknhar on 2009-05-31
I am currently experiencing extreme performance issues when writing or deleting to/from my internal harddrive. trying to delete a 12gb-file results in a freeze for like 5-10minutes.
can anyone confirm that?
if not, any hints on what could be wrong?

---

### Post by balduin on 2009-06-08
Hi noerknhar,

I have no problems when writing to the harddrive. Do you experience these issues with every write process? If not, what's the minimum file size that triggers it?
Which kernel are you running?

Regards,
balduin

---

### Post by noerknhar on 2009-06-11
Hi.

I am running the "normal" kernel that is installed using up-to-date jaunty (no launchpad ppa kernel tho). I can't say what the minimum file size is and I don't even know if it exists. Try moving a folder with some 300+ mb files in it and if you do not experience any issues, you are probably fine and I'm not.

Maybe, but just maybe, I will do a new, clean install of jaunty in some days.

By the way: what BIOS-version do you have? And did you try playing 720p/1080p movies using an external monitor? Did you experience any problems with that like fragmentation, missing keyframes and generally very bad performance?

I dunno what happened, but I think that with 8.10 ubuntu I was able to play 1080p h264 movies without any problems. I am not sure about that, but I will try to figure it out ;) 

Very strange issues and I am not really in a good mood about my notebook... :(

---

### Post by Tich666 on 2009-06-15
720p playback works without a hitch on my laptop after having followed psyke83's guide for better intel performance: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
Youtube in fullscreen and HD quality still stutters, but I blame flash (and consequently adobe) for that rather than my gfx card. Using ff3.5 there are FOSS alternatives though with html5 support for <video> elements using ogg codecs. :)


I'm currently on the bleeding edge configuration and haven't experienced any problems, even suspend-resume works perfectly now.

You can also try out sarvatt's build of the 2.6.30 final kernel which will give you KMS and the improvements of 2.6.30 (a lot of filesystem stuff fixed, generally better disk performance than with 2.6.28 ). You can find it here: [http://sarvatt.com/downloads/LATEST/](http://sarvatt.com/downloads/LATEST/)

I'm not sure about the BIOS version, but when I last checked it like 3-4 months ago I had the latest version offered on the FSC support site.

---

### Post by Gurkenvieh on 2009-07-11
as for the microphones ... i got them working :)

just installed the newest alsa-drivers [ [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) ] and added to /etc/moprobe.d/alsa-base.conf
```
options snd-hda-intel model=fujitsu-xa3530
```(probably it will also work with "model=fujitsu-si3655", but didnt test it yet)

dont forget to set "front-mic" as your input source in your audio-mixer

---

### Post by balduin on 2009-08-03
Does the two finger scrolling work for you? Unfortunately I was unable to get it working. The thing I tried was putting the following in /etc/hald/fdi/policy/111-x11-synaptics.fdi:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
		<merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by Tich666 on 2009-08-10
I hardly ever use the touchpad, thus two-finger scrolling is new to me.
It doesn't work, however on the right side of the touchpad the scrolling area works fine for me.

I also got my microphones working by starting "alsamixer" in the terminal, making sure all the inputs were set to 100% and selecting "front mic" and "mic" as input sources!

Currently rolling on the 2.6.31-rc5 kernel and xorg-edgers drivers which works fine with KMS, but I don't have time to do benchmarking atm.

---

