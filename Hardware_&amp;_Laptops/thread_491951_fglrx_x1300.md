---
title: "fglrx x1300"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by pastries on 2007-07-04
I'm having a problem where i cant get my video card to use opengl. Ive looked at 5 different guides and done each multiple times, i also looked on forums and could still not figure out what the problem is. Can someone please help, heres the info.
> 
fglrxinfo
Error: unable to open display :0

> glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

> 

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    60.0 - 60.0
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection

Sorry new to linux. any help would be appreciated , thankyou in advance.

---

### Post by d3n0 on 2007-07-04
How did you install the driver? Did you run aticonfig --initial? If you use feisty you could simply enable ati's diver with System->Administration->Restricted Drivers Manager, and it should produce working xorg.conf file. Make backup of your xorg.conf file "cp /etc/X11/xorg.conf /etc/X11/xorg.conf_Backup" and then run "sudo dpkg-reconfigure -phigh xserver-xorg". Now run "aticonfig --initial".
Restart X "ctrl + alt + backspace" and if it still doesn'r work try also to disable aiglx:```
 Section "ServerFlags"
      Option  "AIGLX" "off"
  EndSection
```

Yes and could you post output from "lsmod"?

---

### Post by pastries on 2007-07-04
For this i clicked vesa, is that what i should have picked?
>  sudo dpkg-reconfigure -phigh xserver-xorg
For this it says that fglrx is already in file so theres nothing to do.
> aticonfig --initial          
Added to end of xorg.conf
 > Section "ServerFlags"
      Option  "AIGLX" "off"
  EndSection
~~~~~~~~~~~~~~~~~~~~~
Heres output from lsmod
> Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
sbs                    15652  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
i2c_ec                  6016  1 sbs
button                  8720  0 
container               5248  0 
video                  16388  0 
ac                      6020  0 
battery                10756  0 
ipv6                  268960  10 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
wm8775                  6924  0 
cx25840                26512  0 
tuner                  61864  0 
usb_storage            72256  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_usb_audio          79744  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_seq_oss            32896  0 
fglrx                 682988  18 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
libusual               17936  1 usb_storage
snd_usb_lib            17280  1 snd_usb_audio
snd_rawmidi            25472  2 snd_seq_midi,snd_usb_lib
snd_hwdep               9988  1 snd_usb_audio
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             36388  1 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 26592  0 
hid                    27392  1 usbhid
parport                36936  3 ppdev,lp,parport_pc
af_packet              23816  2 
ivtv                  134544  0 
i2c_algo_bit            8712  1 ivtv
cx2341x                12804  1 ivtv
tveeprom               15888  1 ivtv
i2c_core               22656  7 i2c_ec,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom
videodev               28160  1 ivtv
v4l2_common            25216  5 cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15236  2 ivtv,videodev
pcspkr                  4224  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25244  1 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8672  2 snd
agpgart                35400  2 fglrx,intel_agp
psmouse                38920  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
ata_generic             9092  0 
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
e100                   36232  0 
mii                     6528  1 e100
ehci_hcd               34188  0 
generic                 5124  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
usbcore               134280  8 usb_storage,snd_usb_audio,libusual,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

fglrxinfo returns same information.

I think its fixed because i can open opengl programs like wow and screensavers that are opengl. But fglrxinfo is prolly just messed up. Ty for your help.

---

### Post by d3n0 on 2007-07-05
Why did you choose vesa when you had fglrx option? But aticonfig probably did the job. fglrxinfo works here, but that is not so much important or :)? If you are able to run opengl programs then it works. You have nice tool fgl_glxgears so try it. If you feel that problem is solved then pls add [SOLVED] or something like that to the titile.

---

