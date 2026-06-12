---
title: "new radeon drivers?"
date: 2005-01-22
forum: Hardware &amp; Laptops
---

### Post by largo on 2005-01-22
Hi,
Is there any way for me to install the new ati drivers? there was a problem when i tried to install them over a hoary repository

---

### Post by Exxtreme on 2005-01-22
[QUOTE=largo]Hi,
Is there any way for me to install the new ati drivers? there was a problem when i tried to install them over a hoary repository[/QUOTE]
I have downloaded the drivers from ATi and converted them with alien to a DEB-package:
alien fglrx*.rpm

Then i have installed the drivers with dpkg:
dpkg -i --force-all fglrx*.deb

After this, the drivers should be compiled:
cd /lib/modules/fglrx/build_mod
sh make.sh

Then installed:
cd ..
sh make_install.sh

If you have still no 3D acceleration, you should rename/delete the /lib/modules/<your kernel-version>/kernel/drivers/video/fglrx.ko

Finally run fglrxconfig to make a fglrx-compatible /etc/X11/XF86Config-4.

---

### Post by largo on 2005-01-22
do i have to download the xfree or xorg version? I'm using warty

---

### Post by Exxtreme on 2005-01-22
[QUOTE=largo]do i have to download the xfree or xorg version? I'm using warty[/QUOTE]
I guess, you need the XFree86 4.3.0 version except you have installed X.org 6.8.x.

---

### Post by largo on 2005-01-22
I dont think I have. I was trying to install the downloaded drivers now. bot encountered an error:
```
sudo dpkg -i fglrx-4-3-0_8.8.25-2_i386.deb
Password:
(Reading database ... 78508 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from fglrx-4-3-0_8.8.25-2_i386.deb) ...
dpkg: error processing fglrx-4-3-0_8.8.25-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/bin/fglrxinfo', which is also in package fglrx-driver
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-4-3-0_8.8.25-2_i386.deb
```

---

### Post by Exxtreme on 2005-01-22
Uninstall the package "fglrx-driver" first.

---

### Post by largo on 2005-01-22
I tried that, still the same error. I even tried to install it with the graphical system not loaded...

---

### Post by Exxtreme on 2005-01-22
Try this:

"dpkg -u fglrx-driver"

Edit:
"dpkg -r fglrx-driver"

---

### Post by largo on 2005-01-22
hmm, this is not working either i removed the packages with -r and --purge to delete the config files. I don't know what could be wrong, but since there is the message
```
trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
``` 
couldn't the problem be related to something there.

---

### Post by Exxtreme on 2005-01-22
Hmmm, that's really strange.  :???: 

Try this:

dpkg -i --force-all fglrx*.deb

---

### Post by largo on 2005-01-22
worked :)

---

### Post by Exxtreme on 2005-01-22
Good.  :smile: 

Now you should compile and install the driver. :smile: I have editted my first posting.

---

### Post by largo on 2005-01-22
the installation worked. The driver is marked installed in synaptic. But the 3d acelleration is not working at all. are there any additional tasks i have to perform?

---

### Post by Exxtreme on 2005-01-22
Post the output of "lsmod" and "glxinfo".

---

### Post by largo on 2005-01-22
lsmod:
```
Module                  Size  Used by
proc_intf               3776  0
cpufreq_powersave       1728  0
cpufreq_userspace       5240  0
freq_table              4196  0
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  257028  10
nfs                   187744  1
lockd                  61864  2 nfs
sunrpc                149220  4 nfs,lockd
snd_via82xx            28900  2
snd_ac97_codec         67844  1 snd_via82xx
snd_pcm_oss            52968  1
snd_mixer_oss          19456  2 snd_pcm_oss
snd_pcm                95140  2 snd_via82xx,snd_pcm_oss
snd_timer              24900  1 snd_pcm
snd_page_alloc         11432  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7776  1 snd_via82xx
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  1 snd_rawmidi
snd                    55300  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  3 snd
ehci_hcd               30756  0
joydev                  9728  0
tsdev                   7232  0
usbhid                 31392  0
uhci_hcd               31952  0
usbcore               115684  5 ehci_hcd,usbhid,uhci_hcd
via82cxxx              13820  1
sk98lin               193208  1
ohci1394               34884  0
pciehp                 96108  0
shpchp                 99340  0
pci_hotplug            33680  2 pciehp,shpchp
amd64_agp              10984  1
agpgart                33640  1 amd64_agp
floppy                 59156  0
pcspkr                  3592  0
rtc                    12536  0
nls_iso8859_1           4032  1
nls_cp437               5696  1
vfat                   14304  1
fat                    45824  1 vfat
isofs                  36632  0
udf                    91812  0
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
fglrx                 214820  0
parport_pc             34752  1
lp                     10724  0
parport                40712  2 parport_pc,lp
sbp2                   23816  0
ieee1394              108408  2 ohci1394,sbp2
ide_generic             1408  0
ide_disk               18752  0
ide_cd                 41572  0
evdev                   9440  0
ide_core              136120  4 via82cxxx,ide_generic,ide_disk,ide_cd
mousedev               10220  1
psmouse                19720  0
sr_mod                 16900  0
cdrom                  39392  2 ide_cd,sr_mod
reiserfs              240880  1
ext2                   69960  0
ext3                  123880  0
jbd                    60824  1 ext3
mbcache                 9092  2 ext2,ext3
sd_mod                 21344  4
sata_via                7396  7
libata                 40292  1 sata_via
scsi_mod              122508  4 sbp2,sr_mod,sd_mod,libata
unix                   28304  640
fan                     3980  0
thermal                12976  0
processor              17392  1 thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb
``` 

glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
``` 

compiling the driver has returned the following error:

```
sevi@blue:/lib/modules/fglrx/build_mod $ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
```

---

### Post by Exxtreme on 2005-01-22
Ummm, you need the kernel-sources/kernel-headers to compile the drivers. You can use synaptic to look which kernel you're using and which kernel-headers-version you need. The kernel-headers-version must be the same as the kernel-image-version.

P.S. I would remove the linux-restricted-modules.

---

