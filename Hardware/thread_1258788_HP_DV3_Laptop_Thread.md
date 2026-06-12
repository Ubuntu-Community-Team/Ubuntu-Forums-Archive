---
title: "HP DV3 Laptop Thread"
date: 2009-09-05
forum: Hardware
---

### Post by dv3500ea on 2009-09-05
I have created this thread for people to post problems and solutions for the HP DV3 (or possibly other HP DV laptops, as problems and solutions may work for these). Please give the processor architecture, the ubuntu version and any other relevant information.

The problems I have seen (Intel x86, Jaunty):

[LIST]
[*]Nvidia Card (Geforce 9300M GS) doesn't work (compiz visual effects can't be enabled)
[*]Sound output doesn't work through speakers but it does work through headphones
[*]Integrated microphones don't work (tested with audacity)
[*]Fingerprint scanner doesn't work (even with fprint driver)
[*]Touch controls appear to work but then cause top Gnome panel to crash (I've tried the volume controls, which adjust the volume accordingly but afterwards, clicking on applications, system, places or any applets on the top panel does nothing)
[*]Ajusting the screen brightness in ubuntu seems to have no effect on actual screen brightness (always max)
[*]Remote control (IR) has no effect
[/LIST]
I will post any solutions I find. If anyone else finds solutions, please post them and if anyone has any different problems, please post them as someone else may have the solution.

---

### Post by dv3500ea on 2009-09-06
I have solved two of these problems with some help from these forums:
  To fix the Nvidia Card, I installed the latest Linux driver from their website (NVIDIA-Linux-x86-185.18.36-pkg1.run)
 and saved it in /home.
 
 Then, from the desktop I hit Ctrl-Alt-F1.
 This went to a full screen CLI logon.
 I logged on with my username and password
 I then executed these commands
 ```

 cd /home
  sudo /etc/init.d/gdm stop
  sudo chmod +x NVIDIA-Linux-x86-185.18.36-pkg1.run
  sudo ./NVIDIA-Linux-x86-185.18.36-pkg1.run
  
```
 It then went through the installer and returned back to the CLI
 I then typed.
 ```

 sudo /etc/init.d/gdm start
 
```
 It returned to the GUI.
 To enable visual effects I added compiz to startup in system->preferences->startup with the comand 'compiz'.
I then typed 
```

sudo nvidia-xconfig --add-argb-glx-visuals 
```
into a terminal.

The sound output problem was fixed by typing:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
into a terminal and then adding:
```

options snd-hda-intel model=hp-m4 enable_msi=1

```
to the end of the file.

---

### Post by dv3540tx on 2009-09-07
I have experienced most of these problems on my dv3540tx using Xubuntu 9.04 kernel 2.6.28-15.

I have been able to get touch sound keys working by first running xev to find out corresponding keycodes and then mapping these under Settings>Keyboard>Application Shortcuts:

XF86AudioLowerVolume  amixer sset Master playback 4.0-
XF86AudioRaiseVolume  amixer sset Master playback 4.0+
XF86AudioMute  amixer sset Master playback toggle

The numbers 4.0 are arbitrary decibel steps, feel free to adjust them to suit you.

I also found that I had to lower the key repeat rate, so that the volume goes up and down at a controllable rate when I press the up/down touch keys.

The most annoying problem to date for my HP DV3 is lack of brightness control. The FN+F7 and FN+F8 do not work, and I can adjust the value in /proc/acpi/video/VGA/LCD/brightness but it has no effect on actual brightness. Looks like an ACPI problem that needs patching up in the kernel, so I'm waiting for the next release.

Also, check out this great tutorial written for HP Pavilion laptops:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

---

### Post by dv3500ea on 2009-09-08
> **dv3540tx said:**
> I have experienced most of these problems on my dv3540tx using Xubuntu 9.04 kernel 2.6.28-15.

I have been able to get touch sound keys working by first running xev to find out corresponding keycodes and then mapping these under Settings>Keyboard>Application Shortcuts:

XF86AudioLowerVolume  amixer sset Master playback 4.0-
XF86AudioRaiseVolume  amixer sset Master playback 4.0+
XF86AudioMute  amixer sset Master playback toggle

The numbers 4.0 are arbitrary decibel steps, feel free to adjust them to suit you.

I also found that I had to lower the key repeat rate, so that the volume goes up and down at a controllable rate when I press the up/down touch keys.

The most annoying problem to date for my HP DV3 is lack of brightness control. The FN+F7 and FN+F8 do not work, and I can adjust the value in /proc/acpi/video/VGA/LCD/brightness but it has no effect on actual brightness. Looks like an ACPI problem that needs patching up in the kernel, so I'm waiting for the next release.

Also, check out this great tutorial written for HP Pavilion laptops:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)
I agree that there must be something wrong with ACPI (not that I know what that is) as whenever I start up two errors are momentarily printed on the screen:
ACPI: Invalid PBLK length [8]
ACPI: Invalid PBLK length [8]

---

### Post by teapottvroof on 2009-09-10
Hi I posted a question about my dv3 at another thread, at this address:
[http://ubuntuforums.org/showthread.php?p=7925723&posted=1#post7925723](http://ubuntuforums.org/showthread.php?p=7925723&posted=1#post7925723)

I'll copy it here:

 No Audio on my Hp Pavilion dv3-2007tx perminantly muted
Firstly I'll sum up: I have No audio through speakers or headphones when running Ubuntu. I have touch controls above the keyboard, I can use them to make ubuntu increase volume, decrease volume, mute and unmute. When I am using windows the touch control for muting changes colour, orange for mute, white* for not mute. When I run Ubuntu it is always Orange.
Oh, and I'm a linux nube.

Ok so I bought me this new laptop, I was shocked to discover that no matter how powerful your system, windows can still clog it up... Programs crashed and internet dropped out.
I booted up Ubuntu and was pleasantly surprised to find my wireless internet worked fine. It seems to handle everything on my laptop fine, except for the audio.

I am grateful to all who took time to read. I would appreciate any help or suggestions, thanks you very much. 

**
After posting that, I followed the instructions posted by dv3500ea concerning audio control. I placed "options snd-hda-intel model=hp-m4 enable_msi=1" as the bottom line of that text file ect... 

Well the touch-control light for "mute" is now always white, (in windows this would indicate unmuted). But unfortunately I still have no audio.

Thanks, and once again all help is very much appreciated.

---

### Post by dannymac64 on 2009-09-13
After spending many, many hours searching for solutions concerning my dv3-2155mx (Jaunty 9.04 64 bit), I thought I'd post my successes in hopes that it would help someone:

Flawless sound and internal mic functionality:
1. Install the latest ALSA drivers.  I installed 1.0.20 via this link, but watch out for his tar extract commands, which didn't work for me:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

2. Edit alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
3. Then add (note the model is **hp-dv5**):
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

Hibernate and suspend work out of the box, but upon resuming, the battery state cannot be read.  However, if you kill the gnome power manager and start it yourself with verbose logging, the battery info comes back somehow (just discovered this as I gave up and was filing a bug with bugzilla.gome.org):
```
killall gnome-power-manager
gnome-power-manager --no-daemon --verbose
```

If anyone knows how to adjust the screen brightness, it would be much appreciated.

---

### Post by Marrakech on 2009-09-19
Hey dude i bought HP pavilion dv3 2155mx i installed Ubuntu 9.04 but now wireless n mute buttons won't work how can i fix it ???

---

### Post by thriftshopvinyl on 2009-09-19
I'm in the exact same boat as Marrakech. Same model and problems (not surprisingly). I'm also a complete nube. I just downloaded it two days ago and i've read through the pocket guide but thats about it. 
 Since i have no way of connecting to the internet while i'm using Ubuntu i would like a solution that allows me to download from another location and transport it via thumbdrive, cd, or dvd. 
Also, the sound issue is not nearly as important as the lack of internet.
 
I really, really want to break my Windows shackles, but i feel trapped.
 
Thanx

---

### Post by dv3500ea on 2009-09-20
> **thriftshopvinyl said:**
> 
 Since i have no way of connecting to the internet while i'm using Ubuntu i would like a solution that allows me to download from another location and transport it via thumbdrive, cd, or dvd. 

Try [keryx]("http://keryxproject.org/"), that's what I use as I can't connect to the internet using my USB ADSL modem that was made for windows xp. It is a package manager that you can use on a connected pc to download software then install on your Ubuntu computer.

---

### Post by ferchosur on 2009-10-01
> **Marrakech said:**
> Hey dude i bought HP pavilion dv3 2155mx i installed Ubuntu 9.04 but now wireless n mute buttons won't work how can i fix it ???

Hi, i can the same laptop, and whit ubuntu 9.04 i have the same problem whit the wireless and sound

the wireless fix I could solve it with [http://yoyofv.com/2009/02/06/instalar-compat-wireless-en-linux-para-aumentar-senal-wifi/](http://yoyofv.com/2009/02/06/instalar-compat-wireless-en-linux-para-aumentar-senal-wifi/)

but the sound not has been possible

i don't know if exist other problems.

 if you can solve the sound problem please help me.

---

### Post by DigitalAxis on 2009-10-02
I have the HP Pavilion DV3-2150us model (base model, black, Core 2 Duo T6500 2.1GHz, Wireless N, 9-cell battery, 500 GB hard drive; from Amazon).

My experience thus far is:
Worked out of the box:
**Suspend:** works, although the battery isn't detected after it comes back. Wireless does, though.
**Wireless card:** works out of the box, range ~100 feet?; auto-resumes fine.
**Graphics:** Intel GMA4500MHD, works ok; detected 1366x768 just fine.  Celestia-1.5.1 won't display stars as anything but points (although I just restarted it and it magically works perfectly) and shows weird things when set to OpenGL 2.0 (Earth: only clouds) and OpenGL vertex program (tree ring clouds).
**Webcam:** Works, tested in Skype of all things.
**Battery life:** From resume-from-hibernate to 6% battery life; wireless on and doing CPU-intensive things: 5:49
**Touch-sensitive controls:** Work, although the 'mute' button stays white when you mute the sound.  Before I did the sound fix it was permanently orange.
**Touchpad activation toggle:** Works.
**SD card slot:** (I assume it's SDHC, wish it were SDXC) works fine, although I don't know what kind of SD slot it is. 
**Power savings:** Do not control the screen brightness, but they definitely do throttle the CPU.  I was watching a movie on Hulu at the end of the battery test and it was stuttering terribly below 25% battery life.  Powertop reports that the SD card reader(?) is on an internal USB interface, is active 100% of the time, and apparently cannot suspend.

Did not work out of the box, have fix:
**Sound:** Had to follow the fix dannymac64 listed above; except the latest ALSA drivers are now *1.0.21a* and require *libncursesw5-dev*.  I have seen people set the model to hp-m4 and hp-dv5.  Mine is currently set to hp-dv5 and headphones, speakers and microphones (have not tested microphone jack) all work.  Doing *sudoedit /etc/modprobe.d/alsa-base.conf* with *option snd-hda-intel model=hp-dv**3** enable_msi=1* instead does not work, in case anyone was wondering.
**Microphone:** Works, tested in Audacity.

Did not work, have no fix:
**LCD brightness controls:** Do nothing, and the power savings settings can't seem to change them either.
Battery indicator cannot see battery after coming back from suspend.  If you HIBERNATE, it finds it again.  I actually suspended, it was gone, I hibernated, it came back.
**Print-screen:** did nothing.  Usually it brings up kscreenshot

Untested:
Mic-in jack.
Expresscard slot
Ethernet port
IR remote control
Wireless N (have no routers faster than 802.11/g)
DVD burning speed and lightscribe features
HDMI-out
VGA-out
eSATA/USB port as an eSATA port
If and when the USB ports can charge a USB device (powered USB)

For anyone who is reading this wondering if they should get one, it is just light enough to be carried by the corner in one hand, and fast enough to run my torture-test Flash HD video fullscreen, smoothly, with the exception of the Moire patterns part at 4:45:
[http://www.youtube.com/watch?v=sbQhgEJuExY](http://www.youtube.com/watch?v=sbQhgEJuExY)
It does manage to max out both cores though.  I wish Adobe would optimize their code.  This appears to be with the 32-bit version of Flash 10 on 64-bit Kubuntu; I have not tried to install the 64-bit version yet.

Turns out the IR remote plugs into the expresscard slot.  Nothing comes up in Kubuntu when you plug it in.  I assume that's how it charges.

---

### Post by wagnerbarth on 2009-10-05
> **ferchosur said:**
> Hi, i can the same laptop, and whit ubuntu 9.04 i have the same problem whit the wireless and sound

the wireless fix I could solve it with [http://yoyofv.com/2009/02/06/instalar-compat-wireless-en-linux-para-aumentar-senal-wifi/](http://yoyofv.com/2009/02/06/instalar-compat-wireless-en-linux-para-aumentar-senal-wifi/)

but the sound not has been possible

i don't know if exist other problems.

 if you can solve the sound problem please help me.
Hi

See that your codec from audio devices is IDT 92HD71B7X, that's possible using the command "alsamixer" (without quotes).
If it is, install the drivers for alsa on version 1.0.20 or 1.0.21, I used this instructions and work for me, ([http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html)), and edit the alsa-base.conf (/etc/modprobe.d/alsa-base.conf) file and include the lines:

# sound for HP dv3
options snd-hda-intel model=dell-m4-1 enable_msi=1

That's icredible, but your sound card as the same from DELL.

good lucky

"I'm still withou brithness control on my HP Pavilion dv3000 (dv3-3508br) :( :("

---

### Post by 2xd on 2009-10-05
edit:

moved to separate thread

---

### Post by KyleFx on 2009-10-12
> **dannymac64 said:**
> After spending many, many hours searching for solutions concerning my dv3-2155mx (Jaunty 9.04 64 bit), I thought I'd post my successes in hopes that it would help someone:

Flawless sound and internal mic functionality:
1. Install the latest ALSA drivers.  I installed 1.0.20 via this link, but watch out for his tar extract commands, which didn't work for me:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

2. Edit alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
3. Then add (note the model is **hp-dv5**):
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

Thanks a bunch.  :)

System: HP Pavilion dv3t-2000 CTO
OS_1: Linux Mint Gloria (Essentially Ubuntu 9)
OS_2: Windows 7
Sound Card: Can't find a model, but uses IDT HD Audio Codec Driver from HP in Windows7.

Sound did not work out of the box after installing linux mint.  I was following the sound troubleshooting guide at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) and did everything up to step four.  After upgrading ALSA to the latest version, I still had nothing.  As someone mentioned, my mute button was lit orange constantly.  

After adding the line ```
options snd-hda-intel model=hp-dv5 enable_msi=1
``` to the end of /etc/modprobe.d/alsa-base.conf and rebooting, the mute button light turned white, and my sound worked!  Note: The light stays white even when lit, but who really cares.  Hope that helps someone.

---

### Post by AppleBonker on 2009-10-12
All,

I have a DV-3510 that had the same key problems on a fresh install: no sound out of speakers and inability to dim screen.  I have corrected the sound issues using the comments in this thread (though I think I found instructions somewhere else).

For the brightness issue, check out this [thread](http://ubuntuforums.org/showthread.php?t=1238881).

I have sited my sources on there (since this wasn't a fix I came up with all on my own).  I took the time to reword it from the thread where I found the fix so the instructions are a bit easier to follow (rather than having to search through the thread).

For whatever reason my files were labeled "asus", but others may find them named "video-brightness" or something to that extent.  This might be because I'm running Karmic on that device, but I'm not really sure.  It doesn't seem like the naming convention matters at all, however.  Try that out and let me know if it works or if there are any problems.

---

### Post by Jackelope King on 2009-10-12
I have a dv3510nr, and can confirm your directions from the above link worked fine, except that, as noted above, my files were located under "video-brightnessup" and "video-brightnessdown".

---

### Post by wagnerbarth on 2009-10-14
AppleBonker, thanks, your instructions soved my problems with brightness control on my HP DV3508br.
I've problems with the volume control, whem I put my finger on the control simultaneous events are created and I don't stop them... Do you have any sugestions about this?
Thanks a lot my friend.

---

### Post by AppleBonker on 2009-10-15
> **wagnerbarth said:**
> AppleBonker, thanks, your instructions soved my problems with brightness control on my HP DV3508br.
I've problems with the volume control, whem I put my finger on the control simultaneous events are created and I don't stop them... Do you have any sugestions about this?
Thanks a lot my friend.

When I figured out the brightness I was extremely happy, so I felt the need to spread the how-to.  However, I'm still very new to Ubuntu (and Linux in general - I've only been running it for a few months), so I'm no pro.  I have noticed the continuous events when changing volume, but I have not begun to tinker with that yet.  I've been a bit busy configuring Ubuntu on my desktop as well as swapping the hard drive and getting Karmic running on my netbook.  I will be moving for the next few weeks, so it seems like my computer play time will probably be limited.  At some point I will get to tinkering more on the laptop, and if I happen to figure anything out I will certainly let you know.

---

### Post by wagnerbarth on 2009-10-17
> **AppleBonker said:**
> When I figured out the brightness I was extremely happy, so I felt the need to spread the how-to.  However, I'm still very new to Ubuntu (and Linux in general - I've only been running it for a few months), so I'm no pro.  I have noticed the continuous events when changing volume, but I have not begun to tinker with that yet.  I've been a bit busy configuring Ubuntu on my desktop as well as swapping the hard drive and getting Karmic running on my netbook.  I will be moving for the next few weeks, so it seems like my computer play time will probably be limited.  At some point I will get to tinkering more on the laptop, and if I happen to figure anything out I will certainly let you know.

Thanks a lot, I still in this waiting for one solutions, if I have a solutions I'll post this. I'm using Linux Ubuntu has 3 years, but I'm not a advanced for this :).

Once more thanks a lot for all of this forum.

Barth

---

### Post by dv3500ea on 2009-10-18
AppleBonker, thanks for the fix of the brightness, I can confirm it works for me. I can change brightness by running ```
nvclock -S (+|-)10
``` in alt-f2 or the terminal. I've tried changing asus-brightness-down/up and have also tried setting fn-brightnessup/down key combinations to ```
nvclock -S (+|-)10
``` in system->preferences->key combinations but still the combinations don't work. NOTE: 
there is no acpi_listen command installed on my laptop. EDIT: I have managed to bind these commands to ohter key combinations.

I have a partial fix for the touch keys crashing the gnome panel (which seems to be because the volume adjuster is too sensitive). When it crashes run ```
xkill
``` (which I have a keybinding Ctrl-Alt-x for) then click on the gnome panel which should refresh and be usable again.

---

### Post by snoopy33 on 2009-10-22
Hi,

For the brightness, there is a better solution than use nvclock... use nvidia_bl, so you fix really your screen, and gnome can control the brightness directly.

For the repeating sound key, it s not easy, you have to modify the source of xf86-input-evdev, by replacing :
```

  1.
      /* filter repeat events for chording keys */
   2.
          if (value == 2 &amp;&amp;
   3.
              (ev->code == KEY_LEFTCTRL || ev->code == KEY_RIGHTCTRL ||
   4.
               ev->code == KEY_LEFTSHIFT || ev->code == KEY_RIGHTSHIFT ||
   5.
               ev->code == KEY_LEFTALT || ev->code == KEY_RIGHTALT ||
   6.
               ev->code == KEY_LEFTMETA || ev->code == KEY_RIGHTMETA ||
   7.
               ev->code == KEY_CAPSLOCK || ev->code == KEY_NUMLOCK ||
   8.
               ev->code == KEY_SCROLLLOCK)) /* XXX windows keys? */
   9.
              return;

```
By this :
```

   1.
      /* fix events for volume keys */
   2.
          if(ev->code == KEY_VOLUMEDOWN || ev->code == KEY_VOLUMEUP) //MODIFY THIS LINE
   3.
          {
   4.
          //post a keydown and then a keyup, as media keys have no automatic key-up
   5.
          xf86PostKeyboardEvent(pInfo->dev, code, 1);
   6.
          xf86PostKeyboardEvent(pInfo->dev, code, 0);
   7.
          return;
   8.
          }

```
in the file event.c (I found this solution on a blog : [http://www.tsenyurt.com/2009/03/29/ubuntu-volume-wheel-problem-fix/](http://www.tsenyurt.com/2009/03/29/ubuntu-volume-wheel-problem-fix/)

I think that there is a deb package, but I can t use it because i m on Archlinux now.

For multimedia (mediasmart) Key, the solution to set the key is to push on it, recover its code from dmesg, and use setcode (at the boot).


Hope my little search will help you.

I m asking about one thing, is the remote controler Ok on Ubuntu with Lirc ?

++

---

### Post by DigitalAxis on 2009-10-25
Well, I just upgraded to Kubuntu Karmic Koala, and things went rather severely south.

1.) Broadcom wireless card is installed, is active, and can still see the wireless networks it could before.  What it CAN'T do is actually connect to the wireless networks, which it could do out of the box previously.  I'm not sure if I need to try the Gnome Netmanager applet instead.

2.) 3D drivers for Intel GMA 4500MHD suck now.  I worked around the previous problem, visible in Celestia, by switching to 'Multitexture' rather than OpenGL 2.0 Vertex or Shader programs... Now, even Multitexture looks like... well, the attached.

3.) Sound didn't work out of the box, again.  ALSA is now 1.0.20 so I just appended the *options snd-hda-intel model=hp-dv5 enable_msi=1* line to */etc/modprobe.d/alsa-base.conf*.  I just had some nasty ALSA under-runs, basically whenever Firefox loaded something.  Amarok and KDE sound applications won't play ANYthing at the moment.

4.) Brightness controls don't work; unless anyone has bright ideas on how to make this work with Intel integrated graphics (not nVidia) it sounds like I'm still stuck.

5.) Neither the shutdown button widget nor the shutdown menu entry in KDE seem to work.  Running *sudo shutdown -r now* fairly instantly reboots.

6.) On startup Kubuntu complains about not being able to find several partitions, including my /home partition; it nevertheless finds them anyway.

---

### Post by dv3500ea on 2009-10-25
> **snoopy33 said:**
> 
I think that there is a deb package, but I can t use it because i m on Archlinux now.

Do you have a link to this?

---

### Post by DigitalAxis on 2009-10-27
In case this helps anyone figure it out, /proc/acpi/video/OVGA/DD03/brightness contains the LCD brightness for my laptop (Intel GMA 4500MHD graphics).  It looks like this:
```
levels:  12 13 14 15 17 22 27 37 48 59 100
current: 17
```
If I change the value in the KDE power settings widget, the value of `current' changes to one of the others.  The LCD backlight brightness doesn't actually change though.

KDE shutdown/halt/suspend/reboot was fixed by reinstalling all of kubuntu-desktop (basically I went to the Psychocats Ubuntu page, copied the command to remove Kubuntu Jaunty, and changed it to `reinstall' instead- it's not perfect since I'm running Kubuntu Karmic, but it didn't touch things that weren't already installed.  The problem seems to have been bad configuration files...

I suspect my problem with sound (no sound in KDE, flawless sound in programs using esd, passable sound with sox `play' in console) is also due to some bad configuration files.

Finally, the issue with connecting to wireless networks seems to be a known problem (that won't be fixed for the Karmic release) in the knetwork-manager applet.  I can connect to networks that require a hex key, but not networks that use an ASCII password; if I use the gnome nm-applet everything works perfectly fine.

---

### Post by ferchosur on 2009-11-01
to solve audio problemas view this link [http://www.taringa.net/posts/linux/3826876/Arreglar-el-sonido-de-portatiles-HP-en-Linux-Ubuntu-y-MINT.html](http://www.taringa.net/posts/linux/3826876/Arreglar-el-sonido-de-portatiles-HP-en-Linux-Ubuntu-y-MINT.html)

---

### Post by dannymac64 on 2009-11-10
For some reason, the battery indicator **started reporting the correct data** after resuming from a suspend on my dv3-2155mx.  Can anyone else confirm this? The last thing I did was update my alsa drivers to 1.0.21, but I have no idea if that's related.

Also, anyone have a fix yet for the brightness controls when the video card is Intel based?

---

### Post by dannymac64 on 2009-11-11
> **dannymac64 said:**
> For some reason, the battery indicator **started reporting the correct data** after resuming from a suspend on my dv3-2155mx.  Can anyone else confirm this? The last thing I did was update my alsa drivers to 1.0.21, but I have no idea if that's related.

Also, anyone have a fix yet for the brightness controls when the video card is Intel based?

The battery indicator "working" after suspend must have been a misleading fluke. When I checked it this morning after charging all night, the indicator still had the old battery percentage of 60%, even though it obviously should have been ~100%.  Now its back to the old behavior of having to hibernate and wake up (or reboot entirely) in order to see the battery and report the correct percentage remaining.  Sigh.

---

### Post by snoopy33 on 2009-11-27
> **dv3500ea said:**
> Do you have a link to this?
 
On Aur, you search nvidia-bs
++

---

### Post by snoopy33 on 2009-11-27
> **dannymac64 said:**
> The battery indicator "working" after suspend must have been a misleading fluke. When I checked it this morning after charging all night, the indicator still had the old battery percentage of 60%, even though it obviously should have been ~100%. Now its back to the old behavior of having to hibernate and wake up (or reboot entirely) in order to see the battery and report the correct percentage remaining. Sigh.
 
I ve the same issue.
 
To fix it, I edit the source of my kernel, you search acpi.h I think, and in this file, there is a "if" function, it choose if you re discharging, charging, full or... unknown state.
 
When I boot my computer on the battery, the state is unknown, so I edit the file and I replace the words "unknown ..." by discharging.
 
There is no second effect to this modifiction, it fixes the issue, but you have to compile your kernel for each update...
 
I ll make a patch, when i ll have time, one day, may be, I hope :)

---

### Post by snoopy33 on 2009-11-27
Has anyone find a fix for the remote control ?

---

### Post by dannymac64 on 2009-11-27
A bug has been filed for the "Battery status unavailable after suspend/resume on some HP laptops" issue here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453963](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453963)

It may bring about a quicker resolution if more people update the ticket and click the link for "This bug affects me too".

---

### Post by dannymac64 on 2009-11-28
I was able to get the battery status working after suspend/resume by applying the patch for the dv3 laptop found here: [http://bugzilla.kernel.org/show_bug.cgi?id=13745#c12](http://bugzilla.kernel.org/show_bug.cgi?id=13745#c12)

After patching sleep.c, I had to recompile the kernel (the latest on Karmic) and everything works.  Hopefully the patch will make it into one of the next kernel updates.

---

### Post by jjordan on 2009-12-15
BATTERY PROBLEM IS FIXED

Get the 2.6.32 kernel here:

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

Follow the instructions, reboot and no more disappearing battery. 

-j

---

### Post by jjordan on 2009-12-15
This is very ugly but it is the first time I have been able to change the backlight brightness of my DV3-2150us.   The roots of this code came from [http://wiki.archlinux.org/index.php/Samsung_N140]("http://wiki.archlinux.org/index.php/Samsung_N140"). 

 Here are two scripts, one to increase, one to decrease brightness.  I have them asigned to the correct keys through my window manager (WindowMaker) but plan to move that to xbindkeys.  The problem with that is xfce-power-manager steals the keystrokes when it is running and I cannot figure out what it does with them, probably attempts to call an acpi script but I cannot find any information about it.
------------------------------
```
#!/bin/bash --
#Decrease Brightness
#get current brightness in hex and convert to decimal
 var1=`setpci -s 00:02.0 F4.B`
 var1d=$((0x$var1))
 #calculate new brightness
 var2=`echo "ibase=10; obase=16; a=($var1d-16);if (a>15) print a else print 15" 
| bc`
 echo "$0: decreasing brightness from 0x$var1 to 0x$var2"
 setpci -s 00:02.0 F4.B=$var2
 exit
```
----------------------------
```
#!/bin/bash --
#increase brightness
#get current brightness in hex and convert to decimal
 var1=`setpci -s 00:02.0 F4.B`
 var1d=$((0x$var1))
 #calculate new brightness
 var2=`echo "ibase=10; obase=16; a=($var1d+16);if (a<255) print a else print 255
" | bc`
 echo "$0: increasing brightness from 0x$var1 to 0x$var2"
 setpci -s 00:02.0 F4.B=$var2
 exit

```

You need to sudo both of these.  The echo statements can be removed, I will probably stick a zenity call in there for some visual feedback when run from a hotkey.

The script at the link above does more and explains what you are doing.  Note the PCI address is different, yours my also be different.  Have a look at the link above to see how to find it.

I am sure someone out there can figure out the acpi thing and make this work with the various power managers better.

-j

Only non-working item left on this latop is the remote control, looks like it is the same one used on the DV7

---

### Post by jjordan on 2009-12-15
Ugly brightness fix works with INtel graphics.

---

### Post by jjordan on 2009-12-15
OK, I started xbindkeys in the GDM init script and pointed it at the .xbindkeys in my home directory.  That way I can control brightness in GDM.  Once my windowmanager is running xfce4-power-manager soon steals the input from the brightness keys.  Running xbindkeys in a terminal gives it back control for a short time, probably until the next update of the power-manager.  I attached two sets of keys to the brightness scripts so that I would have a fallback until I get this figured out.

Here is the line from /etc/gdm/init/Default:
```
#start xbindkeys so I can control laptop brightness
xbindkeys -f /home/james/.xbindkeysrc
```

Here is the applicable part of my ~/.xbindkeysrc
```
#Screen Bright
"sudo /etc/acpi/brt-up.sh"
    m:0xc + c:56
    Control+Alt + b 

#Screen Bright
"sudo /etc/acpi/brt-up.sh"
    m:0x0 + c:233
    XF86MonBrightnessUp 

#Screen Dim
"sudo /etc/acpi/brt-dn.sh"
    m:0xc + c:40
    Control+Alt + d 

#Screen Dim
"sudo /etc/acpi/brt-dn.sh"
    m:0x0 + c:232
    XF86MonBrightnessDown 
 
```

As you can see I have CTR+ALT+b set up to brighten and CTR+ALT+d set up to dim, that works all of the time but it just isn't right.

-j

---

### Post by jjordan on 2009-12-17
The issue with screen dimming can be devided into two problems.  The first is that HAL is under the mistaken impression that it can controll the screen brightness.  You can see this by running gnome-device-manager and looking at the properties of the "Generic Backlight Device" the "laptop_panel.brightness_in_hardware" value is set to "False" which causes xfce4-power-manager, Gnome's power manager and KDE's power manager to intercept the bright and dim keystrokes preventing the window manager or xbindkeys from getting them.  A work around for this part of the issue is to use **halevt** to intercept the HAL events and then run a script.  You must use halevt 0.1.5-1 which you can get here: [http://packages.debian.org/unstable/main/halevt]("http://packages.debian.org/unstable/main/halevt") earlier versions including the 0.1.3 included in the Ubuntu repos will NOT deferintiate the bright and dim keys.  Halevt is not well documented at the moment, the examples are wrong when it comes to differentiating keystrokes, it is also important to recognise that since HAL is already intercepting the keys the device we need to look at is not the keyboard.

```
<?xml version="1.0" encoding="UTF-8"?>
     <halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">

<halevt:Device match="hal.info.category = input">
              <halevt:Condition name="ButtonPressed" value="brightness-up" exec="sudo /etc/acpi/hp-brt-up.sh"/>
              <halevt:Condition name="ButtonPressed" value="brightness-down" exec="sudo /etc/acpi/hp-brt-dn.sh"/>
</halevt:Device>

</halevt:Configuration>
```

Store this in your home directory as: ```
.halevt
``` and point halevt at it with the command: ```
halevt -c /home/xxxxx/.halevt
``` (in my experience you need to explicitly indicate the configuration file).

You do get the OSD indicator using this method.

The second problem is the lack of a proper script to control the brightness.  If you look in the /etc/acpi directory you will see scripts to control Asus and Sony brightness.  These are much better written than mine above and work because the HAL fdi file is setup to allow hardware control of these laptops, causing HAL to send the keystokes on.  The scripts above do work, hopefully someone smarter than me will take them and improve them.

-j

---

### Post by jjordan on 2009-12-17
HP DV3-2150us
Multimedia button mapping

HAL Events:

fn+F1 question mark
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (help)

fn+F2 printer
none

fn+F3 www
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (homepage)

fn+F4 |screen|
none

fn+F5 moon sleep ***
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (sleep)

fn+F6 lock
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (coffee)

fn+F7 brt down ***
Condition: /org/freedesktop/Hal/devices/computer_logicaldev_input_0,ButtonPressed (brightness-down)

fn+F8 brt up ***
Condition: /org/freedesktop/Hal/devices/computer_logicaldev_input_0,ButtonPressed (brightness-up)

fn+F9 >|| play pause
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (play-pause)

fn+F10 stop
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (stop-cd)

fn+F11 |<< previous
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (previous-song)

fn+F12 >>| next
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (next-song)

Mute
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (mute)

Wifi
none

Volume Slider right
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (volume-up)

Volume Slider left
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (volume-down)

touchpad lock
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (f22)

touchpad unlock
Condition: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input,ButtonPressed (f23)


*** indicates keys that do not produce a keycode and must be handled by halevt

Keycodes
fn+F1 question mark = 146
fn+F2 printer = 37 
fn+F3 www = 180 = XF86HomePage **
fn+F4 |screen| = 33+133 = Super_L+p = CTL+p This one is a lillt weird the 133 is not sent until the fn key is released
fn+F5 moon = NO keycode use HAL
fn+F6 lock = 160
fn+F7 brt down = No Keycode use HAL
fn+F8 brt up = No keycode use HAL
fn+F9 >|| play pause = 172 = XF86AudioPlay **
fn+F10 stop = 174 = XF86AudioStop **
fn+F11 |<< previous = 173 = XF86AudioPrev **
fn+F12 >>| next = 171 = XF86AudioNext **

Mute = 121 = XF86AudioMute **
Volume Slider right = 123 = XF86AudioRaiseVolume **
Volume Slider left = 122 = XF86AudioLowerVolume **
Wifi No keycode and No HAL event
Touchpad lock = 200
Touchpad unlock = 201

** these keys are probably already handled by you Window Manager

---

### Post by jjordan on 2009-12-17
Addd support for the sleep button in the halevt config and then noticed that xfce4-power-manger handled it so I remved the post to prevent confusing people.

---

### Post by fallenhammer on 2009-12-20
Thank you very much **jjordan**!!
I thought that no one would solve the intel brightness issue.

I have a **dv3-2150us** and now I have everything working:
To solve the sound I followed **DigitalAxis** guide and to solve battery after suspend and brightness control I followed **jjordan** tips.

But, there are two things that are working but still bothers me, my wireless and my touchpad.

**Wireless: **I can connect to my network, but when I`m browsing or downloading, suddenly the network stops for about 30sec. In this time the sites stop loading and the downloads stops as well (and I can see no traffic in System Monitor). This never occur when I`m using ethernet connection. My wireless is wpa.

**Touchpad:** If I put 2, 3, or 4 finger in the touchpad the cursor go insane, jumping across the screen. If I use just one finger it works very well, and has vertical scrolling (except when I put to much pressure, than it behave like 2 or more fingers). The touchpad configurator and synaptics configurator apps that i found on synaptic have options to configure and disable the multitouch, but when I apply the settings, nothing changes. It`s like they don`t mess with the right configuration file.

I wonder if anyone has the same problems and found a solution for this.

Sorry for this long text, this is my fist post here. 
Sorry for my bad english too!! :)

---

### Post by jjordan on 2009-12-21
Fallenhammer,  

You are welcome, just trying to pass on a little of what OSS is all about.  

I have not noticed any strangeness with the touchpad, tried pressing extra hard on it and put two and three fingers on it, not quite sure why you would do that but I did not notice any unusual behavior.  It almost sounds like the connector is loose or your touchpad is malfunctioning, the connector is under the center of the keyboard, the keyboard is held on by three screws on the bottom of the case, there is also some double sided tape holding it in place so the first time you take it out can be a little difficult.  I would recommend you contact HP and see if they will fix it for you under warranty.

I had random disconnects from wifi when I was using network-manager, I switched over to Wicd and it has beeen rock solid.  You might give that a try.

I was trying to track down the problem with the IR remote and it looks like M$oft introduced a bug in the ACPI code that actually disables the IR if you are not running windows, hopefully that will be fixed in ACPI soon.


-j

---

### Post by tjodSK on 2010-01-02
hello,

i think i figured out the brightness problem on my hp dv3550 the "proper way" without any hacks (almost). 

what works:
- set brightness level using keyboard *in 32 steps, from complete off to 100%)
- brightness level is changed when switching between battery/AC
- brightness applet 
- display dims when idle

if anyone is interested, i will share the steps i've taken...
firstly, i use ubuntu 9.10 with 2.6.32.2 kernel built from sources, but i guess it does not make a difference. My HP is fitted with nVidia 9300 graphics.

1, i reverted any changes to /etc/acpi scripts i made earlier
2, add the following to your sources.list ```
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu karmic main 
```
3, install nvidia-bl-dkms (this is a kernel module)
4, create config for the module (/etc/modprobe.d/nvidia_bl) and edit the file to look as follows:
```
options nvidia_bl shift=5
```
5, add nvidia_bl to your /etc/modules file (otherwise it would not load at reboot, thx. bheremans)
6, reboot (or modprobe nvidia_bl and restart gnome-power-manager)

let me knows if this works :)

cheers.

---

### Post by bheremans on 2010-01-05
works for me, but I had to add the module to /etc/modules. It didn't autoload after a reboot

---

### Post by markitoxs on 2010-01-05
> **jjordan said:**
> Fallenhammer,  


I was trying to track down the problem with the IR remote and it looks like M$oft introduced a bug in the ACPI code that actually disables the IR if you are not running windows, hopefully that will be fixed in ACPI soon.


-j

where did you see this? can i see a link or something?  is that true?

All this time wasted trying to make the remote work...

---

### Post by tjodSK on 2010-01-05
> **bheremans said:**
> works for me, but I had to add the module to /etc/modules. It didn't autoload after a reboot

Of course, i forgot to mention this. Thank you.

---

### Post by jjordan on 2010-01-07
Here is one of a few discusions I found.

You can see when you boot that it is a orphaned device.  I tried removing the battery but it did not fix the problem.

[http://help.lockergnome.com/linux/ACPI-locks-hardware-devices-detect-vista--ftopict504410.html](http://help.lockergnome.com/linux/ACPI-locks-hardware-devices-detect-vista--ftopict504410.html)


lspnp shows:

00:0a ENE0100(unknown)
state=active
io 0xfd60-0xfd63
irq4

The device is also known as ENE K3926

and is the same IR used in DV7 and DV5

wish someone could find a fix.

-j

---

### Post by jjordan on 2010-01-07
-

---

### Post by bheremans on 2010-01-07
see also this thread for infrared receiver :
[http://ubuntuforums.org/showthread.php?t=1028640](http://ubuntuforums.org/showthread.php?t=1028640)

---

### Post by tjodSK on 2010-01-07
> **jjordan said:**
> Here is one of a few discusions I found.

lspnp shows:

00:0a ENE0100(unknown)
state=active
io 0xfd60-0xfd63
irq4

The device is also known as ENE K3926

and is the same IR used in DV7 and DV5

wish someone could find a fix.

-j

may i ask you the exact dv3 model you are using? Actially, mine (and i think bhereman's as well) does include the ITE 8708 CIR, not ENE. I think that ENE *should* work without lirc and behave like an keyboard (keycodes in dmesg)...

m.

---

### Post by jjordan on 2010-01-07
MIne is a DV3-2150us

XEV shows nothing when keys are on the remote are pressed and boting shows an orphaned device.

-j

---

### Post by tjodSK on 2010-01-07
mine is dv3-3550... even the hp website does offer different drivers for those models. The 3550's list a ITE 8708 CIR driver, while for yours 2150 is an ENE CIR driver listed...

---

### Post by tjodSK on 2010-01-07
i've been reading the post you've sent... it does not look like MS blocked the device but rather as a bug in kernel ([http://bugzilla.kernel.org/show_bug.cgi?id=14086](http://bugzilla.kernel.org/show_bug.cgi?id=14086))

this was apparently fixed in shipped in linux-2.6.32-rc3...
can you verify which kernel version are you using? (mine is 2.6.32.2 on karmic koala, i guess i'm not bitten by this bug, must be something else..)

cheers

---

### Post by markitoxs on 2010-01-09
There is some progress on the ITE ir, the one ont he dv35xx series. I just found this thread: [http://ubuntuforums.org/showthread.php?t=1028640](http://ubuntuforums.org/showthread.php?t=1028640)

---

### Post by jjordan on 2010-01-10
> **tjodSK said:**
> i've been reading the post you've sent... it does not look like MS blocked the device but rather as a bug in kernel ([http://bugzilla.kernel.org/show_bug.cgi?id=14086](http://bugzilla.kernel.org/show_bug.cgi?id=14086))

this was apparently fixed in shipped in linux-2.6.32-rc3...
can you verify which kernel version are you using? (mine is 2.6.32.2 on karmic koala, i guess i'm not bitten by this bug, must be something else..)

cheers

I'm using kernel 2.6.32-020632-generic and still no joy, just checked with xev.

-j

---

### Post by tjodSK on 2010-01-11
> **jjordan said:**
> 


lspnp shows:

00:0a ENE0100(unknown)
state=active
io 0xfd60-0xfd63
irq4


did you had any success with lirc? I think there is an driver for ENE0100... Did you tried this? (does mode2 work?)

---

### Post by jjordan on 2010-01-19
Ok, I have the IR remote on my DV3 2150us  (ENE0100) working.  This is the third time I have tried to make this post so I am doing it in a text editior and then pasting it in so the forum does not time out.

Here are the steps I took.

1.) Installed LIRC from CVS, the version from Karmic may work, I never could get mode2 to work so I could not see if I was getting anything from the remote, try steps 2 and 3 first to see if you can use the LIRC from Ubuntu.
instructions:[http://www.lirc.org/cvs.html]("http://www.lirc.org/cvs.html")

2.) found an /etc/lirc/lircd.conf here:
[http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7]("http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7")
modified it slightly to be:
```
#
# this config file was automatically generated
# using lirc-0.8.6-CVS(default) on Thu Aug 20 01:15:04 2009
#
# contributed by Giuseppe Bilotta
#slightly modified (including the evil thing)  
#by james jordan
#
# brand: HP Pavilion dv5/dv3
# model no. of remote control: HSTNN-PRO7
# devices being controlled by this remote: HP Pavilion dv5
# and HP Pavillion DV3 (selected versions)

begin remote

  name  HP_Pavilion
  bits            8
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2740   860
  one           482   420
  zero          482   420
  pre_data_bits   29
  pre_data       0x37FF07B
  gap          110890
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
# Power
          KEY_POWER                0xF3
# Windows
          KEY_EVIL                 0xF2
# Checkmark key
          KEY_CHECKMARK            0x7F
# PLAY / PAUSE
          KEY_PLAYPAUSE            0x91
# DVD MENU
          KEY_DVD                  0xDB
# REWIND
          KEY_REWIND               0xEA
# STOP
          KEY_STOP                 0xE6
# FF
          KEY_FASTFORWARD          0xEB
# SKIP BACK
          KEY_PREVIOUS             0xE4
# (up)
          KEY_UP                   0xE1
# SKIP FWD
          KEY_NEXT                 0xE5
# (left)
          KEY_LEFT                 0xDF
# OK / ENTER
          KEY_ENTER                0xDD
# (right)
          KEY_RIGHT                0xDE
# BACK / UNDO
          KEY_ESC                  0xDC
# (down)
          KEY_DOWN                 0xE0
# 'i'
          KEY_INFO                 0xF0
# VOL +
          KEY_VOLUMEDOWN           0xEE
# MUTE
          KEY_MUTE                 0xF1
# VOL -
          KEY_VOLUMEUP             0xEF
      end codes

end remote
```

3.) You need to stop and restart LIRC
```
sudo /etc/init.d/lirc stop
sudo /etc/init.d/lirc start
```
now you can run irw in the terminal 
press a few keys on the remote and you should see the codes listed in the file above.

4.) create ~/.lircrc containing
```
#.lircrc file for HP DV3 2150US
#j. jordan
# uses only irxevent to send keys
# setup primarily for VLC default keybindings
#Power Button
begin
      prog = irxevent
      button = KEY_POWER
      config = Key alt-p CurrentWindow
end
#Windows Button
begin
      prog = irxevent
      button = KEY_EVIL
      config = Key alt-m CurrentWindow
end
#Checkmark Button
#toggle fullscreen
begin
      prog = irxevent
      button = KEY_CHECKMARK
      config = Key f CurrentWindow
end
#Play-Pause Button
begin
      prog = irxevent
      button = KEY_PLAYPAUSE
      config = Key space CurrentWindow
end
#DVD Button
begin
      prog = irxevent
      button = KEY_DVD
      config = Key shift-m CurrentWindow
end
#Rewind Button
begin
      prog = irxevent
      button = KEY_REWIND
      config = Key ctrl-Left CurrentWindow
end
#Stop Button
begin
      prog = irxevent
      button = KEY_STOP
      config = Key s CurrentWindow
end
#Fast Forward Button
begin
      prog = irxevent
      button = KEY_FASTFORWARD
      config = Key plus CurrentWindow
end
#Previous Button
begin
      prog = irxevent
      button = KEY_PREVIOUS
      config = Key p CurrentWindow
end
#Up Button
begin
      prog = irxevent
      button = KEY_UP
      config = Key Up CurrentWindow
end
#Next Button
begin
      prog = irxevent
      button = KEY_NEXT
      config = Key n CurrentWindow
end
#Left Button
begin
      prog = irxevent
      button = KEY_LEFT
      config = Key Left CurrentWindow
end
#OK Button
begin
      prog = irxevent
      button = KEY_ENTER
      config = Key Return CurrentWindow
end
#Right Button
begin
      prog = irxevent
      button = KEY_RIGHT
      config = Key Right CurrentWindow
end
#Escape Button
begin
      prog = irxevent
      button = KEY_ESC
      config = Key Escape CurrentWindow
end
#Down Button
begin
      prog = irxevent
      button = KEY_DOWN
      config = Key Down CurrentWindow
end
#Info Button
#cycle subtitles
begin
      prog = irxevent
      button = KEY_INFO
      config = Key v CurrentWindow
end
#Volume Down Button
begin
      prog = irxevent
      button = KEY_VOLUMEDOWN
      config = Key ctrl-Down CurrentWindow
end
#Mute Button
begin
      prog = irxevent
      button = KEY_MUTE
      config = Key m CurrentWindow
end
#Volume Up Button
begin
      prog = irxevent
      button = KEY_VOLUMEUP
      config = Key ctrl-Up CurrentWindow
end
```

(I don't know much about LIRC, I am sure this can be greatly improved)

5.) start irxevent in a terminal (so you can kill it with ctrl-c).
in another terminal or text editor press a few buttons on remote to see if you are getting keycodes, for example pressing the mute button should give you an m.

6.) Setup irxevent to start when your desktop starts.  I am using WindowMaker so yours will likely be different.  I just added the line irxevent -d to my ~/.xsession file.

hope this works for you.

-j

---

### Post by tjodSK on 2010-01-19
Hello!

i'm glad you finally made it to work. Just for the reference, do you use the ENE 100 lirc driver?

I assume you created the .lircrc file by hand. This can be really tedious process, but i found nice app provided by guys from Mythbuntu.. It's mythbuntu-lircrc-generator which generates for you appropriate lircrc files for VLC, mplayer, Totem, etc...

You should give it a try.

---

### Post by darkG20t on 2010-02-24
I'm not sure how to get the brightness working on the Intel chip... I know a couple people got it working, but I couldn't. I did the Halevt stuff, and have it refer to the code you posted in the first post (hp-brt-up.sh, hp-brt-dn.sh). 

I didn't do the xbind keys stuff though, that seemed to be covered by the halevt instead. Am I right, or do I need to do the xbind stuff too?

I'm glad I found this post, it will be awesome to get these couple things working.

Mine is a DV3t - 2000

---

### Post by apstanto on 2010-04-06
Hey, those of you with an Intel chip,

I have the DV3t-2000 and when I was running ubuntu 9.04 I would use the command:

xrandr --output LVDS --set BACKLIGHT_CONTROL native

to give me control of my backlight.  However, when I installed 9.10, that command stopped working.  I read this bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/483062](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/483062)

and Robert Hooker replies to the bug report explaining why it's not working now, but he said "you can boot with i915.modeset=0 to restore the old functionality if it's absolutely required."  So, I edited the grub boot file by following the instructions found here:

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

and Hurray!!!!  The xrandr command works again!  And the brightness keys are working even better than they did in 9.04.

Somebody a lot smarter than me could tell us why this works.  But it does!  Hope this helps...

P.S. I love this thread!  Keep it up ;)

---

### Post by marlonbr on 2010-04-23
Hi guys,

I have a dv3500 and now I'm using Lucid.

Well, I think most of the problems are solved, but for me one remains: brightness control.

I tryied the solution proposed by apstanto, but since I'm on Lucid and on a different laptop, had to adapt and couln't get it working.

My steps:

[LIST]
[*]sudo gedit /etc/default/grub

[*]on the line that has 'GRUB_CMDLINE_LINUX_DEFAULT', added 'i915.modeset=0' at the end, making the line like this:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"**

[*]sudo update-grub
[*]*reboot*
[*]xrandr --output default --set BACKLIGHT_CONTROL native[/LIST]

so, I get this error:
[INDENT]X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  20
  Current serial number in output stream:  20[/INDENT]

Anyone have some thoughts on this?


Marlon Moura

---

### Post by maxxamas on 2010-06-02
> **apstanto said:**
> Hey, those of you with an Intel chip,

I have the DV3t-2000 and when I was running ubuntu 9.04 I would use the command:

xrandr --output LVDS --set BACKLIGHT_CONTROL native

to give me control of my backlight.  However, when I installed 9.10, that command stopped working.  I read this bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/483062](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/483062)

and Robert Hooker replies to the bug report explaining why it's not working now, but he said "you can boot with i915.modeset=0 to restore the old functionality if it's absolutely required."  So, I edited the grub boot file by following the instructions found here:

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

and Hurray!!!!  The xrandr command works again!  And the brightness keys are working even better than they did in 9.04.

Somebody a lot smarter than me could tell us why this works.  But it does!  Hope this helps...

P.S. I love this thread!  Keep it up ;)

This works for me, but not after I restart... has anyone figured out a way to make it permanent?  Im looking to totally ditch windows, but I dont want my screen to burn out prematurely.

Will an update potentially fix the issue?

---

### Post by maxxamas on 2010-07-01
bump

---

### Post by tjodSK on 2010-07-02
do you have nvidia or intel?

---

### Post by marlonbr on 2010-07-04
Guys, I have great news for you!

A dev called Kamal Mostafa ([https://launchpad.net/~kamalmostafa](https://launchpad.net/~kamalmostafa)) made a hack to fix the **brightness control** for my HP DV3, and other laptops affected!

He made a ppa and it worked flawless!

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611)

PPA:
[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri)

Fixing it:
```

sudo add-apt-repository ppa:kamalmostafa/linux-kamal-i915bri
sudo apt-get update
sudo apt-get install linux-headers-2.6.32-23 linux-libc-dev

```

Well, my joy was so big that I sent him an email:
[I][B]"I was avoiding using my HP DV3 laptop at night because of the lack of brightness control giving me serious headaches. Just too much bright in my eyes in a dark room.

Well, that was since 20min ago, because I've just used your ppa and you solved my headache problems!

Thanks for reading and for your awesome work!"[/B][/I]

And he answered:
***":-)  Makes me very happy to hear it Marlon!"***

I recommend doing the same, because these guys fix stuff and ask nothing for it!

His e-mail: [email]kamal@whence.com[/email]

---

### Post by zeroseven0183 on 2010-07-08
I'm planning to buy an HP Pavilion dv3 (-2106TU) this week and after reading this  thread, I'm wondering if Ubuntu 10.04 would work smoothly on it. If not, I'll  choose another brand/model.

Any thoughts?

I will ask the shop if it's alright to test the LiveCD. Hopefully, it's  alright.

---

### Post by marlonbr on 2010-07-09
> **zeroseven0183 said:**
> I'm planning to buy an HP Pavilion dv3 (-2106TU) this week and after reading this  thread, I'm wondering if Ubuntu 10.04 would work smoothly on it. If not, I'll  choose another brand/model.

Any thoughts?

I will ask the shop if it's alright to test the LiveCD. Hopefully, it's  alright.

Ubuntu 10.04 32bit on my DV3:
[LIST]
[*]**video (nvidia 9300 gs)** - works but has to install restricted drivers for effects
[*]**mute button** - ok
[*]**wifi button** - ok
[*]**touchpad** - ok, but I think it is a crap
[*]**brightness control** - need to install a ppa (like I describred on my other post)
[*]**sound volume button** - sometimes when used, locks down the key and keeps raising the volume all the time, even if its on max or min. Only fix is to NOT use it.
[*]**other buttons** - some don't work (which I would never use anyway)
[*]**altec lancing sound card** - ok, but on older versions of ubuntu it doesnt works.
[/LIST]

well, basic system use is working, but I recommend other manufacturers like Acer, which normally uses default technology that works out-of-the-box on linux. And I would not recommend HP, Toshiba, DELL and Sony, which make crap proprietary stuff that works only with their win7 drivers (and are crap anyways) and are VERY expensive.

---

### Post by gbrubal on 2010-07-09
I have a pavillion dve running lucid, and i can't get the brightness to lower. It doesnt work from the battery settings, from the panel or from the buttons (fn+f7 or f8). I dont care much for the fn+f7 (or f8), but how do i lower the brightness? I work a lot on battery alone, and also, this is just plain uncomfortable. I have the intel GMA 4500.

Thanks

---

### Post by marlonbr on 2010-07-09
> **gbrubal said:**
> I have a pavillion dve running lucid, and i can't get the brightness to lower. It doesnt work from the battery settings, from the panel or from the buttons (fn+f7 or f8). I dont care much for the fn+f7 (or f8), but how do i lower the brightness? I work a lot on battery alone, and also, this is just plain uncomfortable. I have the intel GMA 4500.

Thanks

You should give yourself the work of at least **reading** the Thread before asking something.

---

### Post by zeroseven0183 on 2010-07-11
I just bought the Pavilion dv3-2106tu notebook with Windows Vista pre-installed on it. It has 320GB of hard drive - with 12.20GB alloted for the recovery partition and a huge 285+GB for Windows.

I'm not very familiar with Vista and how the Disk Management utility. I want to create another partition out of the big one where I can install Ubuntu. I tried running Ubuntu via LiveCD and guess what, I had no problems with the drivers! However, I cannot unmount or resize the bigger partition using Gparted.

Any suggestions?


EDIT: My bad. I didn't notice the warning sign in Gparted. The Vista partition errors so I have to run chkdsk to correct it. Apparently, the tech guy where I bought my laptop had problems booting to Windows the first time.

UPDATE: My laptop is looking good with Ubuntu. I'll test its other functions such as the volume control, fn keys and the remote control later.

---

### Post by zeroseven0183 on 2010-07-13
The volume control in the laptop panel works perfectly. However, the brightness control (Fn+F7 and Fn+F8) does not.

---

### Post by gbrubal on 2010-07-22
> **marlonbr said:**
> You should give yourself the work of at least **reading** the Thread before asking something.

Maybe Mr. Mostafa's solution didn't work for me. Sorry i was not so clear.

---

### Post by Jackelope King on 2010-07-23
I've been having a problem ever since doing a clean install of 10.04... wonder if anyone else has been having it or knows an easy solution:

The output of the key combination: "fn+F4" (ie the key combination which should switch display output from the laptop's monitor to the one I've plugged into the machine) is... well... nothing. Nothing happens when I hit this key combination.

Does anyone have a fix for this? Or does anyone know the command I can bind to this key combination to get it to toggle the output for the monitor?

---

### Post by 2xd on 2010-08-06
hi  everybody

till' recently I've not used my Ubuntu OS because i could not get the sound work
I'm on dv3-2150ej and using Lucid Lynx (10.04)

today i decided that I'm gonna do everything to make it work and i did !

just installed the latest ALSA driver (1.0.23) using [these instructions ]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")and now every thing is working just fine ! (including headphone jack)

---

### Post by JeroenJ on 2010-08-13
This is not the first time I submit my problem to this forum, but since this is a HP DV3 thread I'd like to share it with my fellow HP users. Hopefully you have seen my problem before and fixed it, I'm getting quit desperate and don't want to go back to windows.

MY LAPTOP: HP DV3 2350ed

MY PROBLEM:
My external monitor is blurry / flickering / vibrating (don't know how to describe it) It seems that it has something to do with the refresh rate or something. It starts out more of less ok at the left and it gets worse to the right. I've read that more laptops have a similar problem. Its not the hardware, Windows works fine :(

Its getting very annoying to work on the small screen, please if you have any ideas share them with me. I can't set it using xrandr. I should mention that the laptop has switchable graphics, I'm ignoring the ATI for now (I think) and I'm using the integrated intel GMA card.

Thanks!
Jeroen

---

### Post by zeroseven0183 on 2010-09-03
> **dannymac64 said:**
> After spending many, many hours searching for solutions concerning my dv3-2155mx (Jaunty 9.04 64 bit), I thought I'd post my successes in hopes that it would help someone:

Flawless sound and internal mic functionality:
1. Install the latest ALSA drivers.  I installed 1.0.20 via this link, but watch out for his tar extract commands, which didn't work for me:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

2. Edit alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```3. Then add (note the model is **hp-dv5**):
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

Thanks dannymac64. Adding the line to my alsa-base.conf not only solved the headphones issue but it also fixed the crashing of pulseaudio whenever I use a USB device while playing video/audio.

I'm using HP Pavilion dv3-2160t

---

### Post by abhiduke on 2010-09-30
i typed the following in my terminal

aplay -l

and i got the following

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

what should i give for my laptop model, and how do i find my laptop model using terminal

---

### Post by zeroseven0183 on 2010-10-21
> **jjordan said:**
> Ugly brightness fix works with INtel graphics.

How? I'm getting some errors.

---

### Post by zeroseven0183 on 2010-10-24
I just talked with Kamal over e-mail and the PPA (with the brightness control and kernel bug fix) only works with Maverick.

I'm still using Lucid Lynx, however.

---

### Post by bheremans on 2010-11-16
> **Jackelope King said:**
> I've been having a problem ever since doing a clean install of 10.04... wonder if anyone else has been having it or knows an easy solution:

The output of the key combination: "fn+F4" (ie the key combination which should switch display output from the laptop's monitor to the one I've plugged into the machine) is... well... nothing. Nothing happens when I hit this key combination.

Does anyone have a fix for this? Or does anyone know the command I can bind to this key combination to get it to toggle the output for the monitor?

sorry verry late reply, but to toggle output and to expand my desktop to an external monitor I use disper.
 "disper --displays=auto -e" is my command for the shortcut fn-F4 (preferences / keyboard shortcuts)

[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

---

### Post by mymta on 2011-02-20
*&#304; have hp dv3 pavilion hp and &#304; buy it 20 days ago but in some game or film i hear dizzzz sound  and screen freez for 0.5 second and continued without any problem *
*please any body help me what is this :(*

---

### Post by mikealves on 2011-03-19
Hello,

I recently received a HP DV3  1075us that had a hard drive failure. I replaced the drive and installed ubuntu 10.10. Everything is working great, except the wireless card. Under Windows Vista, one pushed a wireless button (called  a  Quickkey by HP) above the keyboard to activate the wireless. This button has always glowed red since I installed 10.10. 

I don't really care about pushing the button. I just want to enable wireless.

I can't seem to get the wireless button to turn the card on since these buttons were managed by a utility under Windows Vista.

It seems that I am always Hardware Blocked: Yes

#rfkill list  
 

 0: hp-wifi: Wireless LAN 
     Soft blocked: no 
     Hard blocked: yes 



Does anyone have any ideas how to help? I would like to turn this guy into a nice road laptop, but not having wireless is a big setback.


Here is the other info:





                     p { margin-bottom: 0.08in; }  #lspci  
 

 08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) 
 

 #lshw -C network  
 

   *-network DISABLED       
        description: Wireless interface 
        product: BCM4322 802.11a/b/g/n Wireless LAN Controller 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:08:00.0 
        logical name: eth1 
        version: 01 
        serial: 00:21:00:82:95:e9 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11 
        resources: irq:18 memory:d1100000-d1103fff 
 

 #rfkill list  
 

 0: hp-wifi: Wireless LAN 
     Soft blocked: no 
     Hard blocked: yes

---

### Post by mikealves on 2011-03-19
> **Marrakech said:**
> Hey dude i bought HP pavilion dv3 2155mx i installed Ubuntu 9.04 but now wireless n mute buttons won't work how can i fix it ???


I am having the same issue. with my dv3 1075us running 10.10

---

### Post by Man of Kent on 2011-05-05
[QUOTE=dv3500ea;7905324
The sound output problem was fixed by typing:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
into a terminal and then adding:
```

options snd-hda-intel model=hp-m4 enable_msi=1

```
to the end of the file.[/QUOTE]

I have: HP Pavillion Dv6 SA 1210 no sound,  Xubuntu

The above solution worked straight away after a reboot.

If you ARE running Xubuntu you will need to install Gedit (a text editor program) first in order to use the exact commands above.  I'm sure you could use whatever text editor you do have though!

---

### Post by ograndedienne on 2012-05-22
Hi guys,
i'm following-up because of a problem with the trackpad.

I have a HP Pavilion DV3. The mounted trackpad is really bad in general, but under Ubuntu it doesn't work at all. (I am usually satisfied with HP Laptop but this time I am really disappointed)

The buttons are really hard and when I press them under Ubuntu the sensitivity (i guess) causes the pointer to jump to another location and so fail the click. Analogous problem with click-and-drag.
On Ubuntu 12.04 the right button works like the left one, so essentially no right click!

In Ubuntu 11.04 I found the following working configuration for xorg.conf:

```
Section "InputClass"
Identifier "touchpad catchall"
MatchProduct "SynPS/2 Synaptics TouchPad"
MatchIsTouchpad "on"
Driver "synaptics"
Option "JumpyCursorThreshold" "200"
Option "EmulateTwoFingerMinZ" "20"
Option "EmulateTwoFingerMinW" "5"
Option "TapButton2" "3"
Option "PalmDetect" "1"
Option "PalmMinWidth" "20"
Option "LockedDrags" "1"
Option "AccelFactor" ".01"
Option "MaxSpeed" "1.0"
Option "RBCornerButton" "3"
EndSection

```

But that doesn't work in the 12.04 :(

---

