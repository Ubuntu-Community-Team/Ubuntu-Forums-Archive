---
title: "Graphics Problems, Intel 945GM &amp; HP 530"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by rockdude05 on 2008-03-25
Hi,

After exhaustive searching of the net, I still cannot find a solution to my problem.

I have a 'HP 530' laptop, which includes an Intel Integrated Graphics Chip, 945GM.

I'm using the latest up to date beta of Ubuntu Gutsy 8.04 (This problem doesnt seem to be a bug, just a configuration issue, therefore, I don't think the fact that it's beta is to blame).

I'm aware that the i810 and some other driver have been merged into the 'intel' driver. On searching synaptic, i see that the intel driver is installed, along with what looks like all the others, including 'vesa'.

When installing Ubuntu, I cannot use 'compiz' or any other opengl etc app. When i open the new 'Screens and Graphics' menu option, under Graphics Card, i see that vesa is selected. This clearly isn't the right option for my card. When i choose 'intel' (definatly the right driver for my card), it is chosen. When i click test, it fails. Also, even if i select 'intel' and just ok, it refuses to change when i close it, and reverts to 'vesa'.

Also, when i try to uninstall the vesa driver in synaptic, it tell me i have to also uninstall xorg-video-all or something like that. So it looked to me as if i have to keep them all.

In my xorg.conf file, just very vaugue comments about already being configured. I assume this is because in the latest version, xorg.conf is much less relevant and used.

I did try and put a gutsy style config for my card (tried many examples off the net, didnt work, im back to the default one that hardy gave me), using the 'intel' driver in the [Device] section, with no success.

Also, this is my compiz output in a terminal

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27ae (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Also, heres the output of glxinfo

```


ubuntu@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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
0x4f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```


If someone could help me, it'd be fantastic. This is the only show stopper so far which is preventing me from switching - Ubuntu worked so well on my older computers!!

Cheers

---

### Post by wally83 on 2008-04-13
I have the same problem. Same HP 530 laptop with Intel graphics and Ubuntu 8.04 Hardy (not gutsy).

In Gutsy (7.10) things worked well so this is a bug for sure.

---

### Post by andy789 on 2008-04-24
I have the exact same problems with my HP 530.
It seemes to be the same harware as you have, any idea how to solv this problem, anyone?!

---

### Post by outlaw45 on 2008-04-25
I have the same hardware and the same problem, it worked fine on 7.10...

---

### Post by trippinnik on 2008-04-25
have you tried running ```
sudo dexconf
```
it should reconfigure your graphics card.

---

### Post by Zorlin on 2008-04-26
I have a similar problem, and this does not solve it. I have an Inspiron 6400 with the Intel 945GM graphics chip, and compiz fusion works fine, but any of the 3d screensavers, or the 3d game Glest, are totally unusable, and glitchy...

---

### Post by Speels on 2008-04-26
> **Zorlin said:**
> I have a similar problem, and this does not solve it. I have an Inspiron 6400 with the Intel 945GM graphics chip, and compiz fusion works fine, but any of the 3d screensavers, or the 3d game Glest, are totally unusable, and glitchy...
I've got the same problem (but with an Intel 915GM)
I've started a thread [here](http://ubuntuforums.org/showthread.php?t=757885).
No solution yet :-/

---

### Post by outlaw45 on 2008-04-26
It appears to be a bug in the X window system or the Intel driver... At the moment it looks like it will be fixed in the 8.10 release...

---

### Post by delude on 2008-04-27
Same problem here on hp 530. I notices xorg.conf only says this:
> Section "Device"
        Identifier      "Configured Video Device"
EndSection

i have the default xserver-xorg-video-intel driver

---

### Post by macogw on 2008-04-29
Hey guys, what's the output of:
```
lspci -vn | grep VGA | awk '{ print $3 }'
```?  Is it "8086:27ae"?   If it is, you have a 945GME, not just 945GM.  There's a kernel bug making it so the kernel doesn't recognize the 945GME as simply a variation on 945GM and so doesn't know what to do.  I SSH'd into the computer of someone who had this problem, applied a patch, and recompiled the kernel for him.  He says it works.  He's testing a script I wrote to automate patching and recompiling right now, so as soon as he gives me the OK on that script working properly, I'll post it here for you if that's your problem.

---

### Post by rockdude05 on 2008-04-30
yep that seems to be the problem. well if you could get that script thatd be awesome! 

cheers!

---

### Post by macogw on 2008-04-30
OK, here it is...I'm not guaranteeing it'll work, but it *should*
Download the attached file to your desktop, then
```

cd ~/Desktop
chmod +x 945correct.sh
./945correct.sh

```
You have to be online when you do it so it can download all the necessities, and you're going to have to leave your computer on for about an hour or two.  You'll be prompted for your password to install dependencies at the beginning and then again at the very end to install the corrected kernels.

---

### Post by Rom_rabbit on 2008-04-30
> **macogw said:**
> OK, here it is...I'm not guaranteeing it'll work, but it *should*
Download the attached file to your desktop, then
```

cd ~/Desktop
chmod +x 945correct.sh
./945correct.sh

```
You have to be online when you do it so it can download all the necessities, and you're going to have to leave your computer on for about an hour or two.  You'll be prompted for your password to install dependencies at the beginning and then again at the very end to install the corrected kernels.

Thank you, this script is working, and now my problem resolved

---

### Post by Speels on 2008-05-01
> **macogw said:**
> Hey guys, what's the output of:
```
lspci -vn | grep VGA | awk '{ print $3 }'
```?  Is it "8086:27ae"?   If it is, you have a 945GME, not just 945GM.  There's a kernel bug making it so the kernel doesn't recognize the 945GME as simply a variation on 945GM and so doesn't know what to do.  I SSH'd into the computer of someone who had this problem, applied a patch, and recompiled the kernel for him.  He says it works.  He's testing a script I wrote to automate patching and recompiling right now, so as soon as he gives me the OK on that script working properly, I'll post it here for you if that's your problem.

Hm, I've got an Intel 915GM chipset, and the outputis:
8086:2592

---

### Post by macogw on 2008-05-01
> **Speels said:**
> Hm, I've got an Intel 915GM chipset, and the outputis:
8086:2592

Then this script won't help you.  It adds 27ae to the kernel's configuration, and that's it.  Whatever's making your 915 not work is some other bug.

---

### Post by JorisGoudriaan on 2008-05-05
I do have 945GME, followed your instructions, but after running your patch, I got the following errors;

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-kernel-devel is already the newest version.
fakeroot is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux
./945correct.sh: line 43: cd: linux-2.6.24/: No such file or directory
================================
Updating architecture
================================
chmod: cannot access `debian/scripts/misc/splitconfig.pl': No such file or directory
./945correct.sh: line 49: debian/rules: No such file or directory
================================
Adding graphics card definition to kernel
================================
sed: can't read drivers/char/drm/i915_drv.h: No such file or directory
sed: can't read debian/changelog: No such file or directory
================================
Building the kernel
================================

/usr/bin/fakeroot: 166: debian/rules: not found
================================
Done building kernel

Installing new kernel
================================
vesafb
fbcon
dpkg: error processing linux*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux*deb

Any ideas what I'm doing wrong?

---

### Post by macogw on 2008-05-05
> **JorisGoudriaan said:**
> I do have 945GME, followed your instructions, but after running your patch, I got the following errors;



Any ideas what I'm doing wrong?

Either:
1. You're not online
2. You have source repositories disabled in Synaptic

---

### Post by JorisGoudriaan on 2008-05-05
Thanks for the feedback: Indeed #2 seemed the issue, enabled 'source', but during re-load, I received a Hash Sum mismatch notice:

> GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.Seems fairly similar to this issue:[http://ubuntuforums.org/showthread.php?t=756864](http://ubuntuforums.org/showthread.php?t=756864)
But there's no solution posted as yet.

Any further ideas?

UPDATE: GPG error is sorted, and now its merrily d/l so, it seems my issue is solved.

---

### Post by JorisGoudriaan on 2008-05-05
Hi Macogw,

It seems I still have a little issue, I ran through the whole process, and when it was done, I saw the following:

> dh_installchangelogs: package linux-image-2.6.24-16-generic is not in control info
dh_installdocs -plinux-image-2.6.24-16-generic
dh_installdocs: package linux-image-2.6.24-16-generic is not in control info
dh_compress -plinux-image-2.6.24-16-generic
dh_fixperms -plinux-image-2.6.24-16-generic
dh_installdeb -plinux-image-2.6.24-16-generic
dh_installdeb: package linux-image-2.6.24-16-generic is not in control info
dh_installdeb: package linux-image-2.6.24-16-generic is not in control info
dh_gencontrol -plinux-image-2.6.24-16-generic
dh_gencontrol: package linux-image-2.6.24-16-generic is not in control info
dpkg-gencontrol: error: package linux-image-2.6.24-16-generic not in control info
dh_gencontrol: command returned error code 65280
make: *** [binary-generic] Error 1
================================
Done building kernel

Installing new kernel
================================
vesafb
fbcon
dpkg: error processing linux*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux*deb
Please reboot for new kernel to take effect

I did re-boot, but still can't toggle Normal or Extra visual effects. Any ideas?

Thanks again.

---

### Post by macogw on 2008-05-05
> **JorisGoudriaan said:**
> Hi Macogw,

It seems I still have a little issue, I ran through the whole process, and when it was done, I saw the following:



I did re-boot, but still can't toggle Normal or Extra visual effects. Any ideas?

Thanks again.
It failed to compile and create the deb, but I don't know why.  It's complaining about debian/control not listing that kernel version, but that's not a file it changes...that file should match the original version, which is known-working (since it's the version that made the kernel you currently run on)  I don't know how to fix that.

---

### Post by webceo on 2008-05-07
@JorisGoudriaan, could you please tell us how you solved your GPG problem.


Thanks

---

### Post by JorisGoudriaan on 2008-05-07
On my desktop, I managed to switch it to a local server (South Africa) rather then the main server, and after reload problems were solved. If you are already on your 'local' server, try moving back to main.

With my laptop I actually had to use the terminal, this is what I did, with '40976EAF437D05B5' being the GPG key mentioned in your error:

> gpg --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

Got it from this thread: [http://ubuntuforums.org/showthread.php?t=587936](http://ubuntuforums.org/showthread.php?t=587936)

> sudo apt-get update

might also help. It's a bit of trial and error, but one of those should help. Good luck!

---

### Post by webceo on 2008-05-07
Yeah switching to the USA server did the job.

Thanks for your help

---

### Post by rjstephane on 2008-05-11
the output of the screen is this, please help me.

================================
Now installing packages necessary for compiling kernel
================================
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-kernel-devel is already the newest version.
fakeroot is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'linux_2.6.24-17.31.dsc'
Skipping already downloaded file 'linux_2.6.24.orig.tar.gz'
Skipping already downloaded file 'linux_2.6.24-17.31.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in linux-2.6.24
================================
Updating architecture
================================
chmod: cannot access `debian/scripts/misc/splitconfig.pl': No such file or directory
./945correct.sh: line 49: debian/rules: No such file or directory
================================
Adding graphics card definition to kernel
================================
sed: couldn't open temporary file drivers/char/drm//sedVhLTqh: Permission denied
sed: can't read debian/changelog: No such file or directory
================================
Building the kernel
================================

/usr/bin/fakeroot: 166: debian/rules: not found
================================
Done building kernel

Installing new kernel
================================
vesafb
fbcon
dpkg: error processing linux*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux*deb
Please reboot for new kernel to take effect

---

### Post by macogw on 2008-05-11
> **etadili2006@yahoo.com.ph said:**
> the output of the screen is this, please help me.

================================
Now installing packages necessary for compiling kernel
================================
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-kernel-devel is already the newest version.
fakeroot is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'linux_2.6.24-17.31.dsc'
Skipping already downloaded file 'linux_2.6.24.orig.tar.gz'
Skipping already downloaded file 'linux_2.6.24-17.31.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in linux-2.6.24
================================
Updating architecture
================================
chmod: cannot access `debian/scripts/misc/splitconfig.pl': No such file or directory
./945correct.sh: line 49: debian/rules: No such file or directory
================================
Adding graphics card definition to kernel
================================
sed: couldn't open temporary file drivers/char/drm//sedVhLTqh: Permission denied
sed: can't read debian/changelog: No such file or directory
================================
Building the kernel
================================

/usr/bin/fakeroot: 166: debian/rules: not found
================================
Done building kernel

Installing new kernel
================================
vesafb
fbcon
dpkg: error processing linux*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux*deb
Please reboot for new kernel to take effect
Oooo that's 2.6.24-17....umm hold on. I wrote it for 2.6.24-16.  Has -17 come out for everyone else now?  I'll modify it in a bit and upload a new one.

---

### Post by teflon227 on 2008-05-14
Hey everybody, I seem to be having a very similar problem to all of you, except that when I run the...

lspci -vn | grep VGA | awk '{ print $3 }'

line from macogw, this is the output that I get:

8086:27a2

not 8086:27ae.  Just like everyone else, I have an intel 945 integrated graphics and compiz and all of my 3d effects worked great in 7.10.  In the screens and graphics it is registering my monitor as plug and play (for the correct resolution, 1280x800) but for driver it says "none" and won't pass the test with any that I select, including the i810 driver.  Any thoughts?

Laptop is a dell e1505 with intel 945 integrated graphics.

Thanks!

Ps- this is my first post! Woopee!

---

### Post by macogw on 2008-05-14
> **teflon227 said:**
> Hey everybody, I seem to be having a very similar problem to all of you, except that when I run the...

lspci -vn | grep VGA | awk '{ print $3 }'

line from macogw, this is the output that I get:

8086:27a2

not 8086:27ae.  Just like everyone else, I have an intel 945 integrated graphics and compiz and all of my 3d effects worked great in 7.10.  In the screens and graphics it is registering my monitor as plug and play (for the correct resolution, 1280x800) but for driver it says "none" and won't pass the test with any that I select, including the i810 driver.  Any thoughts?

Laptop is a dell e1505 with intel 945 integrated graphics.

Thanks!

Ps- this is my first post! Woopee!

Then you have a completely different problem.  Their problem is that their video card is not listed in the kernel.  You have the same card as me.  It is in the kernel.  These are two separate issues.  Please open a new thread.

---

### Post by rjstephane on 2008-05-15
macogw,

[SIZE="4"]thank you in advance.[/SIZE]

---

### Post by WunSick on 2008-05-19
Hello, new here, got something in common with some of you.  I have a HP530 laptop with the GMA950 Intel Graphics Card. [Actual Laptop Here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834147671")

I haven't tried Gutsy on this, but fallen in love with Hardy. (for obvious reasons) But i cant seem to get 3da working AT ALL.  I have tried countless xorg configurations, tried setting (Driver "i950")(Driver "i915")(Driver "i810")(Driver "intel") and tried various kernel patches.  Kinda feeling the pain here, and would like some help.  Anybody out there got what it takes?

XORG.CONF
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i950"
	BusID	"PCI:0:2:0"

EndSectio

Section "Monitor"
	Identifier	"Configured Monitor"
	Option          "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection

```

GLXINFO
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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
0x5f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

GLXGEARS
```

5258 frames in 5.0 seconds = 1049.457 FPS
5125 frames in 5.0 seconds = 1024.206 FPS

```

```

wunsick@wunsick-laptop:~$ lspci -vn | grep VGA | awk '{ print $3 }'
8086:27ae

```

---

### Post by nobbeh on 2008-05-21
> **macogw said:**
> OK, here it is...I'm not guaranteeing it'll work, but it *should*
Download the attached file to your desktop, then
```

cd ~/Desktop
chmod +x 945correct.sh
./945correct.sh

```

Im totaly new to this.. where do you type this.. ive tried to do it in the promt but without success.. 
ive just installed the latest ubuntu and installed it.. (please be gentle with the flaming)

---

### Post by JorisGoudriaan on 2008-05-21
No need to flame ;-)

Use your terminal. Normally under Applications -> Accessories.

---

### Post by nobbeh on 2008-05-21
Do I have to install something else before typing the strings in the termenal and/or do I type string for string?
'edited'
ok..changed to US instead of swedish..seems like the file is running now..hopefor the best

hmm..its still running..something..after an hour..is this normal?..check files or something
'last edit
works like a charm now ;D

---

### Post by JorisGoudriaan on 2008-05-22
Can you confirm that the update worked, i.e. can you now set you Display settings to 'normal' or 'Extra' ? (in Systems -> Preferences -> Appearance and then the 'Visual Effects' tab)

---

### Post by ShodanjoDM on 2008-05-22
> **macogw said:**
> OK, here it is...I'm not guaranteeing it'll work, but it *should*
Download the attached file to your desktop, then
```

cd ~/Desktop
chmod +x 945correct.sh
./945correct.sh

```
You have to be online when you do it so it can download all the necessities, and you're going to have to leave your computer on for about an hour or two.  You'll be prompted for your password to install dependencies at the beginning and then again at the very end to install the corrected kernels.

Thank you. This really helps me fixing my friend's laptop :)

---

### Post by delude on 2008-05-23
also using -17 kernel here, hope to get the updated script soon

---

### Post by WunSick on 2008-05-23
Well, im still kinda stuck without 3da like the rest of you. Is there any word that this issue is being worked on?

---

### Post by Twitch6000 on 2008-05-23
> **outlaw45 said:**
> It appears to be a bug in the X window system or the Intel driver... At the moment it looks like it will be fixed in the 8.10 release...

It couldn't be the intel driver because I have the same one and it has been working for me since I started using Linux.(early 07)

---

### Post by Esparte on 2008-06-05
here another one with kernel -17

---

### Post by kipkemoi on 2008-06-05
> **macogw said:**
> OK, here it is...I'm not guaranteeing it'll work, but it *should*
Download the attached file to your desktop, then
```

cd ~/Desktop
chmod +x 945correct.sh
./945correct.sh

```
You have to be online when you do it so it can download all the necessities, and you're going to have to leave your computer on for about an hour or two.  You'll be prompted for your password to install dependencies at the beginning and then again at the very end to install the corrected kernels.


Every time after ubuntu does an update i just check for the line inside 945correct.sh that has the version number . 

eg currently i change 2.6.24-16.30+1 to 2.6.24-18.32+1 .

Then I 
 ```
mv -rf ~/src ~/src.BAK

```

Then I rerun 945correct.sh . 

_NOTE_ 
This only works AFTER the update (ie after the update to 2.6.24-18.32).

Then I get preety graphics. Hope it works for you.

---

### Post by nobbeh on 2008-06-09
ah yes..noticed that the problem came back(not being able to get 3d back)

How can you see what version of ubuntu you got? (you said  2.6.24-18.32..I can only found 2.6.24 or even  2.6.24-18..cant remeber not having my computer with me right now)

and where do you type:
mv -rf ~/src ~/src.BAK?? in the terminal?

---

### Post by r_duke on 2008-06-16
Yes! This worked for my HP530 as well!

Check your kernel version under:
 System -> Administration -> System Monitor
Under the Tab "System" you'll see your kernel version.

Open the 945correct.sh script and change the line with the kernel version

sed -ie '1ilinux ([COLOR="Red"]2.6.24-17[/COLOR].30+1) hardy; urgency=low\n\n  * Make kernel aware that pci device 0x27AE is Intel i945GME\n\n -- Mackenzie Morgan <maco.m@ubuntu.com>  Tue, 29 Apr 2008 15:48:34 -0400\n' debian/changelog

to your kernel version, f.e.

sed -ie '1ilinux ([COLOR="Red"]2.6.24-18[/COLOR].30+1) hardy; urgency=low\n\n  * Make kernel aware that pci device 0x27AE is Intel i945GME\n\n -- Mackenzie Morgan <maco.m@ubuntu.com>  Tue, 29 Apr 2008 15:48:34 -0400\n' debian/changelog

then follow maco's instruction in this post.

cheers
r

---

### Post by macogw on 2008-06-16
Or just install the -19 kernel from Proprosed.

---

### Post by glx51mm on 2008-06-27
Hello everyone,
I ran the script but I still can't get any good graphics.
The command (lspci -vn | grep VGA | awk '{ print $3 }') gives me the correct output (8086:27ae) but when trying to enable visual effects, even in normal mode it gives me a message saying that "desktop could not be enabled". The video test under System->Administration->Hardware testing passes successfully though. Any ideas what the problem might be ? Btw, how may i set the amount of memory that the graphics will use since it's shared with the main system memory ? Is this done automatically ?

Thanks a lot in advance for your help.

---

### Post by macogw on 2008-06-27
> **glx51mm said:**
> Hello everyone,
I ran the script but I still can't get any good graphics.
The command (lspci -vn | grep VGA | awk '{ print $3 }') gives me the correct output (8086:27ae) but when trying to enable visual effects, even in normal mode it gives me a message saying that "desktop could not be enabled". The video test under System->Administration->Hardware testing passes successfully though. Any ideas what the problem might be ? Btw, how may i set the amount of memory that the graphics will use since it's shared with the main system memory ? Is this done automatically ?

Thanks a lot in advance for your help.

Install your updates.  The bug is fixed.  It was fixed last week.  It's in the -19 kernel.

---

