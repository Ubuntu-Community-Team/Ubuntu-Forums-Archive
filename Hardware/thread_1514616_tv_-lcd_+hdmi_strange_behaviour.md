---
title: "tv -lcd +hdmi strange behaviour"
date: 2010-06-21
forum: Hardware
---

### Post by ieros_gr on 2010-06-21
Hello
Even not new in forum I decided to write because for a months now I have a very strange problem. It&#8217;s about the resolution of the lcd-tv Samsung (26 inch with native resolution 1366x768).Even though I know that hdmi displays fixed resolutions ( 1920 or 1280) so it would not be possible to force it to 1366 vga cable  gives me the same behavior too. Only 1280x720 and when I enable overscanning (through gpu scaling) in order to see all desktop to my tv it keeps the settings unitl I log off or restart-shutdown,Then I have to do the same procedure again
Also the letters looks like they have  a blur effect upon them and I can&#8217;t see very well even with image sharpening (all the visible effects of my tv are turned off).  
Some useful info may be the following from my terminal
```
ionmpc@ionmpc ~/Desktop $ nvidia-settings -l

ERROR: Cannot open display 'ionmpc:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/ionmpc/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 47 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 48 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OverscanCompensation specified on line 49 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 50
       of configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 51 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 52 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 53
       of configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       54 of configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 55 of
       configuration file '/home/ionmpc/.nvidia-settings-rc' (no Display
       connection).
```

Also for the sound (i had some problems listen through hdmi but now works
```
ionmpc@ionmpc ~/Desktop $ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
Terminating processes: 1490lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
5234lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
5278lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
5324lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
(with SIGKILL:) 5360lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
(failed: processes still using sound devices: 5382(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5382(pulseaudio).
Unloading ALSA sound driver modules: snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
ionmpc@ionmpc ~/Desktop $ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
Terminating processes: 5382lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
5643lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
5689lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
5725lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
(with SIGKILL:) 5758lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
(failed: processes still using sound devices: 5781(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ionmpc/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5781(pulseaudio).
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
```

Finally ...
```
ionmpc@ionmpc ~/Desktop $ sudo get-edid | parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

   Performing real mode VBE call
   Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
   Function supported
   Call successful

   VBE version 300
   VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
   Report DDC capabilities

   Performing real mode VBE call
   Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
   Function supported
   Call successful

   Monitor and video card combination does not support DDC1 transfers
   Monitor and video card combination does not support DDC2 transfers
   0 seconds per 128 byte EDID block transfer
   Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
   Read EDID

   Performing real mode VBE call
   Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
   Function supported
   Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID



xrandr --verbose
Screen 0: minimum 320 x 175, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 (0x164) normal (normal) 0mm x 0mm
   Identifier: 0x163
   Timestamp:  15717
   Subpixel:   unknown
   Clones:   
   CRTC:       0
   CRTCs:      0
   Transform:  1.000000 0.000000 0.000000
               0.000000 1.000000 0.000000
               0.000000 0.000000 1.000000
              filter:
  1280x720 (0x164)   46.1MHz *current
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   36.0KHz
        v: height  720 start    0 end    0 total  720           clock   50.0Hz
  1280x720 (0x165)   47.0MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   36.7KHz
        v: height  720 start    0 end    0 total  720           clock   51.0Hz
  1280x720 (0x166)   47.9MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   37.4KHz
        v: height  720 start    0 end    0 total  720           clock   52.0Hz
  960x600 (0x167)   30.5MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   31.8KHz
        v: height  600 start    0 end    0 total  600           clock   53.0Hz
  960x540 (0x168)   28.0MHz
        h: width   960 start    0 end    0 total  960 skew    0 clock   29.2KHz
        v: height  540 start    0 end    0 total  540           clock   54.0Hz
  840x525 (0x169)   24.3MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   28.9KHz
        v: height  525 start    0 end    0 total  525           clock   55.0Hz
  840x525 (0x16a)   24.7MHz
        h: width   840 start    0 end    0 total  840 skew    0 clock   29.4KHz
        v: height  525 start    0 end    0 total  525           clock   56.0Hz
  832x624 (0x16b)   29.6MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   35.6KHz
        v: height  624 start    0 end    0 total  624           clock   57.0Hz
  800x600 (0x16c)   27.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   34.8KHz
        v: height  600 start    0 end    0 total  600           clock   58.0Hz
  800x600 (0x16d)   28.3MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   35.4KHz
        v: height  600 start    0 end    0 total  600           clock   59.0Hz
  800x600 (0x16e)   28.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  800x600 (0x16f)   29.3MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.6KHz
        v: height  600 start    0 end    0 total  600           clock   61.0Hz
  800x600 (0x170)   29.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   37.2KHz
        v: height  600 start    0 end    0 total  600           clock   62.0Hz
  800x512 (0x171)   25.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   32.3KHz
        v: height  512 start    0 end    0 total  512           clock   63.0Hz
  720x576 (0x172)   26.5MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   36.9KHz
        v: height  576 start    0 end    0 total  576           clock   64.0Hz
  720x480 (0x173)   22.5MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   31.2KHz
        v: height  480 start    0 end    0 total  480           clock   65.0Hz
  720x450 (0x174)   21.4MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   29.7KHz
        v: height  450 start    0 end    0 total  450           clock   66.0Hz
  720x400 (0x175)   19.3MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   26.8KHz
        v: height  400 start    0 end    0 total  400           clock   67.0Hz
  700x525 (0x176)   25.0MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   35.7KHz
        v: height  525 start    0 end    0 total  525           clock   68.0Hz
  700x525 (0x177)   25.4MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   36.2KHz
        v: height  525 start    0 end    0 total  525           clock   69.0Hz
  700x525 (0x178)   25.7MHz
        h: width   700 start    0 end    0 total  700 skew    0 clock   36.8KHz
        v: height  525 start    0 end    0 total  525           clock   70.0Hz
  680x384 (0x179)   18.5MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   27.3KHz
        v: height  384 start    0 end    0 total  384           clock   71.0Hz
  680x384 (0x17a)   18.8MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   27.6KHz
        v: height  384 start    0 end    0 total  384           clock   72.0Hz
  640x512 (0x17b)   23.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   37.4KHz
        v: height  512 start    0 end    0 total  512           clock   73.0Hz
  640x512 (0x17c)   24.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   37.9KHz
        v: height  512 start    0 end    0 total  512           clock   74.0Hz
  640x512 (0x17d)   24.6MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   38.4KHz
        v: height  512 start    0 end    0 total  512           clock   75.0Hz
  640x480 (0x17e)   23.3MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   36.5KHz
        v: height  480 start    0 end    0 total  480           clock   76.0Hz
  640x480 (0x17f)   23.7MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   37.0KHz
        v: height  480 start    0 end    0 total  480           clock   77.0Hz
  640x480 (0x180)   24.0MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   37.4KHz
        v: height  480 start    0 end    0 total  480           clock   78.0Hz
  640x480 (0x181)   24.3MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   37.9KHz
        v: height  480 start    0 end    0 total  480           clock   79.0Hz
  640x480 (0x182)   24.6MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   38.4KHz
        v: height  480 start    0 end    0 total  480           clock   80.0Hz
  640x480 (0x183)   24.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   38.9KHz
        v: height  480 start    0 end    0 total  480           clock   81.0Hz
  640x480 (0x184)   25.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   39.4KHz
        v: height  480 start    0 end    0 total  480           clock   82.0Hz
  640x400 (0x185)   21.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   33.2KHz
        v: height  400 start    0 end    0 total  400           clock   83.0Hz
  640x350 (0x186)   18.8MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   29.4KHz
        v: height  350 start    0 end    0 total  350           clock   84.0Hz
  576x432 (0x187)   21.2MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   36.7KHz
        v: height  432 start    0 end    0 total  432           clock   85.0Hz
  576x432 (0x188)   21.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   37.2KHz
        v: height  432 start    0 end    0 total  432           clock   86.0Hz
  576x432 (0x189)   21.6MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   37.6KHz
        v: height  432 start    0 end    0 total  432           clock   87.0Hz
  576x432 (0x18a)   21.9MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   38.0KHz
        v: height  432 start    0 end    0 total  432           clock   88.0Hz
  576x432 (0x18b)   22.1MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   38.4KHz
        v: height  432 start    0 end    0 total  432           clock   89.0Hz
  576x432 (0x18c)   22.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   38.9KHz
        v: height  432 start    0 end    0 total  432           clock   90.0Hz
  576x432 (0x18d)   22.6MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   39.3KHz
        v: height  432 start    0 end    0 total  432           clock   91.0Hz
  512x384 (0x18e)   18.1MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   35.3KHz
        v: height  384 start    0 end    0 total  384           clock   92.0Hz
  512x384 (0x18f)   18.3MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   35.7KHz
        v: height  384 start    0 end    0 total  384           clock   93.0Hz
  512x384 (0x190)   18.5MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   36.1KHz
        v: height  384 start    0 end    0 total  384           clock   94.0Hz
  512x384 (0x191)   18.7MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   36.5KHz
        v: height  384 start    0 end    0 total  384           clock   95.0Hz
  512x384 (0x192)   18.9MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   36.9KHz
        v: height  384 start    0 end    0 total  384           clock   96.0Hz
  416x312 (0x193)   12.6MHz
        h: width   416 start    0 end    0 total  416 skew    0 clock   30.3KHz
        v: height  312 start    0 end    0 total  312           clock   97.0Hz
  400x300 (0x194)   11.8MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   29.4KHz
        v: height  300 start    0 end    0 total  300           clock   98.0Hz
  400x300 (0x195)   11.9MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   29.7KHz
        v: height  300 start    0 end    0 total  300           clock   99.0Hz
  400x300 (0x196)   12.0MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   30.0KHz
        v: height  300 start    0 end    0 total  300           clock  100.0Hz
  400x300 (0x197)   12.1MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   30.3KHz
        v: height  300 start    0 end    0 total  300           clock  101.0Hz
  400x300 (0x198)   12.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   30.6KHz
        v: height  300 start    0 end    0 total  300           clock  102.0Hz
  360x200 (0x199)    7.4MHz
        h: width   360 start    0 end    0 total  360 skew    0 clock   20.6KHz
        v: height  200 start    0 end    0 total  200           clock  103.0Hz
  320x240 (0x19a)    8.0MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   25.0KHz
        v: height  240 start    0 end    0 total  240           clock  104.0Hz
  320x240 (0x19b)    8.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   25.2KHz
        v: height  240 start    0 end    0 total  240           clock  105.0Hz
  320x240 (0x19c)    8.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   25.4KHz
        v: height  240 start    0 end    0 total  240           clock  106.0Hz
  320x240 (0x19d)    8.2MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   25.7KHz
        v: height  240 start    0 end    0 total  240           clock  107.0Hz
  320x200 (0x19e)    6.9MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   21.6KHz
        v: height  200 start    0 end    0 total  200           clock  108.0Hz
  320x175 (0x19f)    6.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.1KHz
        v: height  175 start    0 end 0 total  175           clock  109.0Hz
```

PLease thnik of something i can't stand anymore fightining for something so simple

thank you in advance

---

