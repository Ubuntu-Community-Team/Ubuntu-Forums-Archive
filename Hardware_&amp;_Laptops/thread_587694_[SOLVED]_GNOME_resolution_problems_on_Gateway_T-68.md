---
title: "[SOLVED] GNOME resolution problems on Gateway T-6815"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by licefork on 2007-10-23
Chipset: Intel GM965
Graphics: GMA X3100
Native resolution: 1280x800@60

I fixed the sound, and got Compiz to work. My problem is very weird but I think I know why it's happening.

[IMG]http://no-residue.net/cams_random_stuff/images/resolution.png[/IMG]

The screen's resolution is correct, but GNOME's resolution won't go any higher than 1024x768.

Here's my xorg.conf important stuff:

```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection
```

and in my Xorg.0.log I get lots of stuff like this:

```
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV connected
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output TV
(II) intel(0): Modeline "1024x768"x30.0   26.89  1024 1025 1088 1120  768 769 800 801 (24.0 kHz)
(II) intel(0): Modeline "800x600"x30.0   17.00  800 801 864 896  600 601 632 633 (19.0 kHz)
(II) intel(0): Modeline "848x480"x30.0   14.51  848 849 912 944  480 481 512 513 (15.4 kHz)
(II) intel(0): Modeline "640x480"x30.0   11.31  640 641 704 736  480 481 512 513 (15.4 kHz)
```

I checked around for weeks, and I'm finally making a post asking for help from the Ubuntu pro's :)

---

### Post by licefork on 2007-10-23
Anyone? Well I hear other people who have a similar problem, they have no problem in KDE. It could just be a GNOME bug. I'm going to download Kubuntu this afternoon and test that out. I'll post my results here.

---

### Post by TabletUbuntu on 2007-10-23
I has a similar problem when connecting to an second (external VGA from laptop) monitor that did not support DDC.  The resolution on the laptop was higher than the display, and the  Desktop had a similar appearance to yours.  Used xrandr to explicitly set the two resolutions to 1024x768 and all was well.

---

### Post by licefork on 2007-10-23
Here's my xrandr -q output:
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 303mm x 190mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       30.0* 
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  

```

Looks like the "TV" resolution is 1024x768! That must be the problem!!! How can I change this?

I also tried adding a virtual resolution to the xorg.conf... but it didn't make a difference:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
                Virtual          1280 800
	EndSubSection
EndSection
```

Thanks for the relpy! I'll try playing with it some more while I wait for Kubuntu to download.

---

### Post by mekas2024 on 2007-10-23
Hello! 

Hey dud, did u get the solution to your problem? I have the samee problem... do you find the answare, please if u know i will apreciate if u can share the solution, also i wanna know  how u did it with the sound !

THX A LOT

---

### Post by licefork on 2007-10-24
No, I have not yet found the solution. I tried the Kubuntu Live CD but it has the same problem:

[IMG]http://no-residue.net/cams_random_stuff/images/kubuntu_resolution_problem.png[/IMG]

I'm guessing it has something todo with the virtual screen resolution. The display's resolution is at it's correct 1280x800, while the desktop's resolution can't go any higher than 1024x768. As you can see from the Xorg.0.log in my first post, attempts are made to set various resolutions. This is noticeable at start-up: the screen flickers.

As for the sound, first enable all of the software source repositories, and make sure you have build-essential installed.

Then, get these installed as well:
```
apt-get install mercurial automake1.4
```

Then we are going to download and compile the ALSA source code:
```
mkdir alsa 
cd alsa 
hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver 
hg clone http://hg-mirror.alsa-project.org/alsa-kernel alsa-kernel 
cd alsa-driver 
./hgcompile 
```

If everything compiled OK, we can install it:
```
sudo tar zvcf oldsound.tgz /lib/modules/`uname -r`/kernel/sound/* 
sudo make install 
```

Now we just need to edit a file:
```
sudo gedit /etc/modprobe.d/alsa-base 
```

And add this to the very end:
```
alias snd-card-0 snd-hda-intel 
options snd-hda-intel model=test enable-msi=1 probe-mask=1 
```

Now reboot, turn the volume all the way up, and voila! Try using speaker-test to test your sound. Something you may notice is that the volume doesn't go up very loud, I'm working on a solution for this problem as well.

I'm going to bed to get some sleep, I'll work on this some more tomorrow!

---

### Post by mekas2024 on 2007-10-24
TXHs a Lot for reply, i will be trying to get a solution tonite, if i get one i will tell you!

Thanks for the sound, i will doit riiiite now LOL

Good Nite

Regards!

Mekas

---

### Post by mekas2024 on 2007-10-24
Hey licefork  , 

i have an error when i try to the ./hgcompile... everything seems to be ok but at the end i get this error messages... 

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/hwdep.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/memory_wrapper.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/memalloc.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/sgbuf.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/pcm.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_native.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_lib.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_timer.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_misc.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_memory.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/rawmidi.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/rtctimer.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/timer.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/wrappers.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/misc_driver.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/memory_debug.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/sound.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/init.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/memory.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/info.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/control.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/misc.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/device.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/isadma.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/sound_oss.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/info_oss.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd-hwdep.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd-timer.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd-rtctimer.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd-pcm.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd-page-alloc.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/snd-rawmidi.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/mixer_oss.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/pcm_oss.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/pcm_plugin.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/io.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/copy.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/linear.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/mulaw.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/route.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/rate.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/snd-mixer-oss.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/oss/snd-pcm-oss.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_device.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_dummy.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_instr.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_midi_emul.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_midi_event.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_midi.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_virmidi.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_lock.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_clientmgr.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_memory.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_queue.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_fifo.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_prioq.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_timer.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_system.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_ports.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_info.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-device.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-midi-event.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-dummy.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-virmidi.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-midi.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-midi-emul.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-instr.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_fm.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_gf1.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_iw.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_simple.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-fm.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-gf1.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-simple.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-iw.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_init.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_timer.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_ioctl.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_event.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_rw.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_synth.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_midi.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_readq.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_writeq.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/snd-seq-oss.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/aloop.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/dummy.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/mtpav.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/mts64.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/portman2x4.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/serial-u16550.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/virmidi.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-aloop.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-dummy.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-virmidi.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-serial-u16550.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-mtpav.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-mts64.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-portman2x4.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/mpu401_uart.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/mpu401.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/snd-mpu401-uart.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/snd-mpu401.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_lib.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_synth.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_seq.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_midi.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_drums.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_oss.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/snd-opl3-lib.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/snd-opl3-synth.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_lib.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_mixer.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_proc.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_seq.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_synth.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/yrw801.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/snd-opl4-lib.o
  LD [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/snd-opl4-synth.o
  CC [M]  /home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.o
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c: In function ‘snd_pcsp_create’:
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: ‘PIT_TICK_RATE’ undeclared (first use in this function)
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: (Each undeclared identifier is reported only once
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: for each function it appears in.)
make[4]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp] Error 2
make[2]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers] Error 2
make[1]: *** [_module_/home/mekas/Desktop/alsa/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
mekas@mekas-laptop:~/Desktop/alsa/alsa-driver$

Do you have an idea what could be? Im sorry but im kind of newbi here lol

THX!

---

### Post by Rob49 on 2007-10-24
licefork
This is what i did to fix the 1280x800 and screen problem.
GDM doesn't use the entire screen. Neither does gnome. This is because the TV output is enabled.
You can disable it by adding the following commands to your xorg.conf

[B]Section "Monitor"
Identifier "TVOutput"
Option "Disable" "true"
EndSection[/B]

and then in the Device Section add the following

**Option "monitor-TV" "TVOutput"**

then save it.

i have the t-6815 too and  don't have sound yet
going to try your method.: 
link i found this fix at.
[http://forums.fedoraforum.org/showthread.php?t=159516]("http://forums.fedoraforum.org/showthread.php?t=159516")

---

### Post by dietrying on 2007-10-24
alternatively yyou can try to change the driver- using the i810 driver instead of the intel module. This worked good for me on the samsuöng q35 ceron. The success may vary depending on the graphics-chipset you have.
greetings,
David:popcorn:

---

### Post by mekas2024 on 2007-10-24
Hello guys, 

The Rob49 Solution it worked perfect for my laptop,  Thanks Rob.

About the sound error, did someone have an idea of what could be ? its something of headers but i dunno what to do...

THX

---

### Post by licefork on 2007-10-24
Sweet! Thanks Rob49! Worked amazingly. I also noticed that my laptop now performs better when using Compiz. 

As for your response dietrying: I had originally tried using the i810 driver, since the Gutsy release wasn't out at that time, and I wanted to get Windows off my laptop! Unfortunately, the GM965 requires the intel driver, so I had to use the development versions of Gutsy to run my laptop.

As for the sound: it should work perfectly for you Rob49, since we have the same laptop. For mekas2024, it seems you have found a solution in this thread: [http://ubuntuforums.org/showthread.php?t=276343&page=10](http://ubuntuforums.org/showthread.php?t=276343&page=10) but I also have barely any sound, I'm working on that now, I'll let you know if I have any luck!

---

### Post by mekas2024 on 2007-10-24
Thats right licefork, i found a solution, but the sound its not so loud... well anyway, im happy rite now cuz i have everything up and running whit style lol

Thanks god i can say "gooood bye vista" lol

Thx guys!

Regards, 

Mekas

---

### Post by mekas2024 on 2007-11-15
> **licefork said:**
> No, I have not yet found the solution. I tried the Kubuntu Live CD but it has the same problem:

[IMG]http://no-residue.net/cams_random_stuff/images/kubuntu_resolution_problem.png[/IMG]

I'm guessing it has something todo with the virtual screen resolution. The display's resolution is at it's correct 1280x800, while the desktop's resolution can't go any higher than 1024x768. As you can see from the Xorg.0.log in my first post, attempts are made to set various resolutions. This is noticeable at start-up: the screen flickers.

As for the sound, first enable all of the software source repositories, and make sure you have build-essential installed.

Then, get these installed as well:
```
apt-get install mercurial automake1.4
```

Then we are going to download and compile the ALSA source code:
```
mkdir alsa 
cd alsa 
hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver 
hg clone http://hg-mirror.alsa-project.org/alsa-kernel alsa-kernel 
cd alsa-driver 
./hgcompile 
```

If everything compiled OK, we can install it:
```
sudo tar zvcf oldsound.tgz /lib/modules/`uname -r`/kernel/sound/* 
sudo make install 
```

Now we just need to edit a file:
```
sudo gedit /etc/modprobe.d/alsa-base 
```

And add this to the very end:
```
alias snd-card-0 snd-hda-intel 
options snd-hda-intel model=test enable-msi=1 probe-mask=1 
```

Now reboot, turn the volume all the way up, and voila! Try using speaker-test to test your sound. Something you may notice is that the volume doesn't go up very loud, I'm working on a solution for this problem as well.

I'm going to bed to get some sleep, I'll work on this some more tomorrow!

Hi everybody, hey Icefork, did u get a solution for the sound not so loud??

I never found  a solution, and i wanna have a loud speakers lol..

Well if someone know something about this, i will appreciate help !

Regards

Mekas

---

