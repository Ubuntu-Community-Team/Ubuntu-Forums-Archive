---
title: "Asus A6R - Sound"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by kessler on 2006-08-12
I've been trying for what seems like forever to solve problems with my Asus A6R. I've got almost everything working, except my soundcard. I tried following this guide : [http://ubuntuforums.org/showthread.php?t=76307](http://ubuntuforums.org/showthread.php?t=76307) with little luck. I can now playback sound, but i can hear nothing from the built in speakers (never could btw). However, if i plug in my earplugs/headphones, i can hear the sound, however it's very low and very distorted.

I've tried setting the volume to max in both alsamixer and kmix, with no appearent effect. Anyone who has any suggestions?

-------

zipper@lappy:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:02:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


zipper@lappy:~$ lsmod|grep snd
snd_hda_intel          19348  0
snd_hda_codec         153648  1 snd_hda_intel
snd_pcm_oss            44064  0
snd_mixer_oss          18944  1 snd_pcm_oss
snd_pcm                89480  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    55652  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10760  2 snd_hda_intel,snd_pcm

---

### Post by krugman on 2006-08-13
Hi!

I have a ASUS W2JC, and I have got the same problem as you do! Didn't try the earplugs though...
I have already posted one similar topic here, but no answers yet!

I hope it will be fixed someday because it is very frustrating for the moment...

---

### Post by LordRaiden on 2006-08-13
Did you raise the PCM slider in alsamixer? (to say 80)

---

### Post by krugman on 2006-08-13
As for me, it is at 96 but still no sound.
For comparison:

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c5
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:06:02.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d1)
0000:06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:06:03.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:06:03.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:06:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:06:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

and:
```
snd_hda_intel          18964  4
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  5 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  11 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

```

---

### Post by LordRaiden on 2006-08-13
Are your built-in speakers muted? There is a pc speaker channel in alsamixer as well but that might not be it. And I doubt the BIOS would have anything to do with it, but you could have a look.

---

### Post by krugman on 2006-08-13
Non, I don't think that speakers are muted. It would notified in the notification area if it was muted right? Here, I have the sound icon, and it does not indicate that it is muted.

It seems that it is an issue that many ASUS laptops have, but I haven't found a clear solution yet...

---

### Post by LordRaiden on 2006-08-13
If you think this is an ASUS issue, I suggest you follow the link in my signature (bugtracker for alsa-project) and report it as a bug.

---

### Post by ixius on 2006-08-13
I have a6r and there was the same problem. I solved it by turning on external amplifier in sound system (for example with kmix if you use kde)

---

### Post by kessler on 2006-08-13
I've read elsewhere to disable the external amplifier, however, i can find no such thing in kmix. Unless it's the one called 'PCM'?

I've been fidling with kmix now, trying every possible setting i could think of, no luck. I get no sound at all, neither from the speakers in the laptop, or my earplugs. Perhaps it has something to do with my driver?

---

### Post by cdrw80 on 2006-08-14
Hi!
In my A6R laptop works fine, sounds and etc.
There is few screenshots on my kmix. I hope this help;) if you use KDE.
[[IMG]http://img233.imageshack.us/img233/3691/snapshot2vi8.th.png[/IMG]](http://img233.imageshack.us/my.php?image=snapshot2vi8.png)
[[IMG]http://img61.imageshack.us/img61/5202/snapshot3hm4.th.png[/IMG]](http://img61.imageshack.us/my.php?image=snapshot3hm4.png)

---

### Post by sturmdogg on 2006-08-15
I got the sounds on my A6R working by following the instructions at [http://www.beginningubuntu.com/dapper_tips.html](http://www.beginningubuntu.com/dapper_tips.html) 

OT (sorry for derailing the thread): anyone here got fglrx working on the A6R without killing the usb system?

---

### Post by krugman on 2006-08-15
well, in Edit->Preferences I have neither Master Surround nor External Amplifier...
I only have PCM, Front, Line-in, CD,Microphone,IEC958, Aux, and Capture, Capture1, Capture 2, and 3 Input Source.

---

### Post by kessler on 2006-08-15
cdrw80:

Interesting... My kmix doesnt look like that at all. How did you get it working? Any specific guide you were following?

sturmdogg:
Already tried that guide without much luck, but i'll try giving it another try.
I've read about people having trouble with usb and fglrx, but i haven't experienced any of those problems, not yet anyway. I just followed the guide in the ubuntu wiki for ATI drivers, and it almost worked out of the box. Only had to fiddle around a bit in xorg.conf to get my resolution right, so i'm afraid i can't even give an answer to the people having those problems.

---

### Post by rantak on 2006-08-15
Quoting from the [wiki page]("http://wiki.ubuntu.com/LaptopTestingTeam/AsusA6R")

"People are having problems with the ATI IXP sound so this is how I got the sound working in Ubuntu 6.06 Dapper clean install: start alsamixer in terminal -> mute the external amplifier (press M) -> -> increase the master surround sound(if needed) -> quit the alsamixer (Escape) -> sound working."

That's how I did it. 

Kessler: Are you using a external usb mouse? In my experience when using the fglrx drivers the usb system stops working more quickly if the ports are constantly used by some device.

---

### Post by cdrw80 on 2006-08-15
> **kessler said:**
> cdrw80:

Interesting... My kmix doesnt look like that at all. How did you get it working? Any specific guide you were following?



Nothing special, I put amarok play some mp3 and try different settings to kmix:-\"

---

### Post by kessler on 2006-08-15
> **rantak said:**
> Quoting from the [wiki page]("http://wiki.ubuntu.com/LaptopTestingTeam/AsusA6R")

"People are having problems with the ATI IXP sound so this is how I got the sound working in Ubuntu 6.06 Dapper clean install: start alsamixer in terminal -> mute the external amplifier (press M) -> -> increase the master surround sound(if needed) -> quit the alsamixer (Escape) -> sound working."

That's how I did it. 

Kessler: Are you using a external usb mouse? In my experience when using the fglrx drivers the usb system stops working more quickly if the ports are constantly used by some device.

I'm going to cry soon... I dont think my soundcard is loaded correctly by linux, cus' i never had such an option. Neither external amplifier nor master surround sound :(. Guess i'm back at square one, i need to get the driver/module installed properly. Could you paste your lsmod please? That might help me a bit further.

About the usb mouse, as i said i haven't been testing it extensivly, but i have used an external usb mouse for a few hours with no problems at all. Perhaps the problems will appear for me as well down the road, don't know.

---

### Post by rantak on 2006-08-16
> **kessler said:**
> I'm going to cry soon... I dont think my soundcard is loaded correctly by linux, cus' i never had such an option. Neither external amplifier nor master surround sound :(. Guess i'm back at square one, i need to get the driver/module installed properly. Could you paste your lsmod please? That might help me a bit further.

About the usb mouse, as i said i haven't been testing it extensivly, but i have used an external usb mouse for a few hours with no problems at all. Perhaps the problems will appear for me as well down the road, don't know.

The usb-fglrx problem usually takes only <10 minutes, so I guess your system is somehow different. Could you paste your glxinfo so I could see are there any differences? 

Here's my lsmod output. Do you have snd_atiixp at all?

```
ndiswrapper           177364  0
isofs                  37688  1
udf                    88452  0
rfcomm                 40216  5
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
lp                     11844  0
ipv6                  265728  10
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
asus_acpi              11540  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ntfs                  103536  1
nls_utf8                2176  2
nls_cp437               5888  2
vfat                   13440  1
fat                    53020  1 vfat
dm_mod                 58936  1
af_packet              22920  6
md_mod                 72532  0
joydev                 10048  0
tsdev                   8000  0
irtty_sir               8576  0
snd_atiixp             19724  1
snd_atiixp_modem       16136  0
pcmcia                 40508  0
snd_ac97_codec         93088  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
pcspkr                  2180  0
rtc                    13492  0
psmouse                36100  0
sir_dev                19628  1 irtty_sir
snd_pcm                89864  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
sdhci                  14848  0
mmc_core               30104  1 sdhci
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               7300  0
irda                  187068  2 irtty_sir,sir_dev
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
crc_ccitt               2304  1 irda
snd_timer              25220  1 snd_pcm
snd                    55268  9 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  3 snd_atiixp,snd_atiixp_modem,snd_pcm
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too
ati_agp                 9100  0
agpgart                34888  1 ati_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  5
generic                 5124  0
atiixp                  6800  1
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vesafb                  8476  1
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit



```

---

### Post by kessler on 2006-08-16
I've been trying a lot of different stuff to make my soundcard work, installing all different sorts of drivers/modules, so i'm not sure how i could get back to basics. Any hints?

glxinfo :
> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier, 
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float, 
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5946 (8.27.10)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, 
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None

and my lsmod :

> Module                  Size  Used by
arc4                    2048  1 
ieee80211_crypt_wep     4992  1 
fglrx                 394284  8 
ipv6                  265728  12 
apm                    21228  1 
ppdev                   9220  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   13440  1 
fat                    53020  1 vfat
nls_utf8                2176  1 
ntfs                  103536  1 
dm_mod                 58936  1 
md_mod                 72532  0 
af_packet              22920  4 
lp                     11844  0 
8139cp                 22528  0 
joydev                 10048  0 
bcm43xx               124044  0 
tsdev                   8000  0 
pcmcia                 40508  0 
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
rtc                    13492  0 
sdhci                  14848  0 
mmc_core               30104  1 sdhci
8139too                26880  0 
mii                     5888  2 8139cp,8139too
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
snd_hda_intel          19348  0 
snd_hda_codec         153648  1 snd_hda_intel
snd_pcm_oss            44064  0 
snd_mixer_oss          18944  1 snd_pcm_oss
yenta_socket           28428  1 
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm                89480  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
pcspkr                  2180  0 
snd                    55652  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
ati_agp                 9100  0 
agpgart                34888  2 fglrx,ati_agp
snd_page_alloc         10760  2 snd_hda_intel,snd_pcm
psmouse                36100  0 
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
serio_raw               7300  0 
evdev                   9856  2 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ehci_hcd               34184  0 
ohci_hcd               21892  0 
usbcore               130692  3 ehci_hcd,ohci_hcd
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
ide_disk               17664  5 
generic                 5124  0 
atiixp                  6800  1 
processor              23360  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by kessler on 2006-08-17
Sorry for this shameless bump, but i'm still very much in the need of some help regarding this problem. Any help will be greatly appriciated.

---

### Post by PeBek on 2006-08-20
I have also ASUS A6R. Play sound works, but mic, line in, cd, pc speaker and other input chanel don't work. I set up capture volume to 100% and unmute it, but it's still don't work.
Have anyone similar problem ?

---

### Post by ewoox on 2006-08-26
i have the same problem with mic... please help us... i can't delete my windows because i can't use skype :(

---

### Post by conqueror on 2006-08-26
I also have Asus A6R and I face a lot of troubles like sound card, graphic card, wireless card, and webcamera. Can you help me to solve some of them.

---

### Post by PeBek on 2006-08-26
For wireless card, I use [ndiswrapper](http://ndiswrapper.sourceforge.net/), it's work fine. More info on [http://gentoo-wiki.com/HARDWARE_Gateway_6020#Wireless_.28Broadcom_BCM4318.29](http://gentoo-wiki.com/HARDWARE_Gateway_6020#Wireless_.28Broadcom_BCM4318.29)

For graphic card, I use [ati drivers](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27). I had some problems with it, but now it's work.

I can't found drivers for webcam.

I report sound card problem to [ALSA bugtracking system](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2379).

---

### Post by sturmdogg on 2007-01-03
Has anyone managed to make the mic work on the Asus A6R yet?

---

### Post by eggdeng on 2007-01-03
For those with asus laptops, if youalready have alsa 1.10 or better installed, add the following line at the end of /etc/modprobe.d/alsa-base

```
options snd-hda-intel model= asus
```

You can check your alsa version with

```
cat /proc/asound/version
```

---

### Post by Pjotr123 on 2007-01-03
You can try this:
[http://ubuntuforums.org/showthread.php?t=330454](http://ubuntuforums.org/showthread.php?t=330454)

Greeting, Pjotr.

---

### Post by eggdeng on 2007-01-03
> **eggdeng said:**
> Add the following line at the end of /etc/modprobe.d/alsa-base

```
options snd-hda-intel model= asus
```

]

If that fails, try 
```
options snd-hda-intel model=asus-laptop
```

---

