---
title: "Hp530 | HP 530 | Hewlett Packard 530 | Support Thread"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by Ted Nancy on 2007-07-17
I've got an HP 530 running Feisty beautifully. This is a great laptop for running Ubuntu (Feisty) on, and I wanted to start a thread documented all the issues that have or may arise.

If you wish to comment on this thread please post details about your specific model, and attached your "sudo lspci" output. 

To start us off:
[B]
HP530[/B]
Model: G4641AT
```
sudo lspci
```
For results see attached.
[B]
Video:[/B]
For full resolution do:
```
sudo apt-get install xserver-xorg-video-intel
```
then* ctrl-alt-backspace* to apply changes.

**Fonts:**
They look ok. I did:
```
sudo dpkg-reconfigure fontconfig-config
```
Choose: * Native, Automatic, No bitmapped fonts. Then in GNOME font settings adjust to your preferences.

**Sound:**
I couldn't get it working for the life of me. Look for my Intel HDA thread to see the frustration. Not sure what happened, but I totally remove Vista using a Gparted CD, created a 8Gig ext3 root partition, a 1.5Gig Swap partition, and the rest Ext3 for Home. (PS. totally choose noatime in the install options of alt-ubuntu-cd when partitioning, for performance not sound). Anyway, once I removed Vista, VOILA, sound. No idea why. Tried everything else.

Currently sound works. I have speakers plugged into my headphone jacks though, and sound still comes out of my laptop speakers. Haven't tried Mic, but my webcam mic works well under skype.

---

### Post by bogdan.veringioiu on 2007-07-17
I have the same configuration here.
lspci output is identical.
The only problem I'm facing (so far) is the auto-mute functionality. When I plug the headphones, laptop speakers are not muted.
I followed the instructions from this thread
[http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+530](http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+530)
because I believe it's about the same audio chip, but with no success.
Please let me know if you find something more.
Thanks.

---

### Post by dabugas on 2007-07-19
I'm considering purchasing an HP 530 from [here]("http://ff") (the page is in Greek).

A couple questions for you: does 3D acceleration (use glxinfo) work? how about WiFi?

You should also start a page on the wiki, see [Laptop Testing]("https://wiki.ubuntu.com/LaptopTesting")

---

### Post by Ted Nancy on 2007-07-20
I connected to my WPA out of the box. Haven't tested WEP or unsecured.

I'm not sure if it matters, but I ran glxinfo while running Amarok, firefox, and Virtualbox installing XP Professional.

Here's the output of glxinfo:

HP530:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by bogdan.veringioiu on 2007-07-20
3D acceleration works:

The output of  **glxinfo | grep direct**
direct rendering: Yes

Output of **glxgears:**

4907 frames in 5.0 seconds = 981.374 FPS
4972 frames in 5.0 seconds = 994.286 FPS
4981 frames in 5.0 seconds = 996.115 FPS
4981 frames in 5.0 seconds = 996.047 FPS
4982 frames in 5.0 seconds = 996.269 FPS
4989 frames in 5.0 seconds = 997.616 FPS
4979 frames in 5.0 seconds = 995.695 FPS
4981 frames in 5.0 seconds = 996.173 FPS

Regards.
Bogdan.

---

### Post by rror on 2007-07-31
> **bogdan.veringioiu said:**
> I have the same configuration here.
The only problem I'm facing (so far) is the auto-mute functionality. When I plug the headphones, laptop speakers are not muted.
I followed the instructions from this thread
[http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+530](http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+530)
because I believe it's about the same audio chip, but with no success.
Please let me know if you find something more.
Thanks.

i'm having the same problem and just called HP Support (make sure to call the business support hotline) and was told that there is no way to mute only the internal speaker
seems like the hardware isn't capable to detect the headphones

---

### Post by bogdan.veringioiu on 2007-08-01
Well, this is something I cannot believe, because on Windows, the laptop speaker is muted, when headphones are inserted....so the hardware SHOULD be capable of headphones detection.

---

### Post by bogdan.veringioiu on 2007-08-01
Hello hp 530 users.
Please add this line in /etc/modprobe.d/alsa-base

options snd-hda-intel model=laptop

and then issue sudo /etc/init.d/alsasound restart

Let me know if it works for you.
Regards.

---

### Post by rror on 2007-08-02
> **bogdan.veringioiu said:**
> Hello hp 530 users.
Please add this line in /etc/modprobe.d/alsa-base

options snd-hda-intel model=laptop

and then issue sudo /etc/init.d/alsasound restart

Let me know if it works for you.
Regards.

it does :biggrin:
thanks man

sudo /etc/init.d/alsasound restart messes up the volume control, but muting works after a reboot

why did the support guy at HP tell me that there is no way to do that (even on windows):confused:

[i followed this howto [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") to upgrade ALSA because my microphone jack wasn't working. maybe the solution only works with the current ALSA version...]

---

### Post by Arthur Archnix on 2007-08-08
> **bogdan.veringioiu said:**
> Hello hp 530 users.
Please add this line in /etc/modprobe.d/alsa-base

options snd-hda-intel model=laptop


Bravo Bogdan, thank so much!

The /etc/init.d/alsasound restart did not work, but a reboot set it right.

And I'm running on a standard 7.04 install, no special alsa work or config at all. 

Incidentally, I initially had no sound after a fresh install. I found this only occurs if I install XP Pro or Vista first, then dual boot. Restart, F10, restore to defaults, save and ext, and voila, sound. Bogdan's trick makes it all work as it should.

Best,

---

### Post by bogdan.veringioiu on 2007-08-22
Did anyone test wireless connectivity?
Is it working? I didn't have the chance to use it yet.

Thanks.

---

### Post by revford on 2007-08-26
I got my HP 530 a few days ago, most things just worked out of the box, I needed to install the 915resolution package for the widescreen display and had to tweak the gstreamer setting to use X11 without Xv as the picture was poor or missing.

Yes, the wireless works, but not out of the box.

I had to go download ndiswrapper and install that, along with the Windows driver and some messing about downloading firmware, I found a guide on this forum that took me through it all in a few hours.

A big delay on me getting wireless working was the little Wireless button next to the power button, for some reason that was turned off and I didn't realise.

Silly me.  :/

It glows blue when it's working, so watch out for that one.

Once you have all the gubbins installed, if wireless isn't working and the blue light is off push that button!

---

### Post by zozo_serieux on 2007-09-07
Hi,
I'm interested in the HP 530.
But I'm afraid there is any "tatoo" in the hardware, since I read HP is used to to that: didn't you encounter any difficulty ?
And, to install ubuntu, can I destroy all the HP restoration partition if there are any? or would it lock the computer?

thanks :)

PS: sorry for my English, I'm French, and congratulations for this great forum.

---

### Post by revford on 2007-09-07
Yes you can destroy the original HP partitions.  I just wiped the whole HD and installed Ubuntu, I never even ran the preinstalled Vista.

Most of the hardware is fine, only the Wifi needed ndiswrapper as it's a Broadcom chip, everything else worked with no hassle.

---

### Post by Arthur Archnix on 2007-09-16
Yes, it's safe to destroy the hp partitions. And if you have a model with the intel wireless everything works out of the box, save the few tweaks needed above to get everything golden.

---

### Post by Arthur Archnix on 2007-11-01
Gutsy update. Works great. Only thing I needed to do was the sound hack mentioned above so that speakers are muted when headphones inserted.

---

### Post by revford on 2007-11-03
Gusty is giving me some grief.

It no longer wakes from suspend, I have to force a reboot.  :(

---

### Post by Arthur Archnix on 2007-11-03
You know, I found that waking from suspend with Compiz would disable my networking. Reboot required to bring it back up. Once I got rid of Compiz, I couldn't replicate the error.

I'm going to reinstall tonight, I'll test suspend before I remove Compiz and try to give more info.

---

### Post by AddiKT1ve on 2007-11-06
hai2u.

I'm an HP 530 user too, since 24 hours. I'm still running Vista Basic (which, in fact, is rather good), waiting for a RJ45 to come to me :p.

Broadcom wireless chips are used by many manufacturers; when Ubuntu will include the driver, I think it'll be the best lambda-user-friendly distro.

HF, developpers :p...

---

### Post by mrtenl on 2007-11-06
Hi, i have some problems getting audio-in working on my HP 530. Have anyone of you had any success getting it to work?

---

### Post by Arthur Archnix on 2007-11-06
You'll have to describe the problem in more detail. 

The only audio problem I've ever had is while dual-booting sound appears to be installed fine and playing but no sound comes out. This is some kind of hard-ware level / vista / bios bug. Workarounds include:

1. Removing Vista or XP and only booting Ubuntu.
2. Make sure your Ubuntu partition is the second partition, Vista the first.
3. Reboot the computer, hit F10 to get into bios, reset to defaults, save and exit, reboot into ubuntu. (This worked on my third try, that is, I did this three times before it worked).

EDIT... a complete reinstall and I couldn't reprodce the suspend error, which is now working fine and bringing wireless back up.

---

### Post by bloodniece on 2007-11-08
> **Arthur Archnix said:**
> You know, I found that waking from suspend with Compiz would disable my networking. Reboot required to bring it back up. Once I got rid of Compiz, I couldn't replicate the error.

I'm going to reinstall tonight, I'll test suspend before I remove Compiz and try to give more info.

I have the Celeron M 1.5Ghz HP 530 and am having the same sleep/suspend issues.  Compiz, huh?  Let me disable Compiz and see what happens.

Also, the little button that puts the laptop to sleep when I close the lid does not work.

[B]UPDATE:
[/B]Wireless recovered ok after waking up, but it did not wake up any faster. I still have to hit ctrl+alt+backspace twice and tap some keys for the password dialog to show up.  I'll do it again and post the dmesg output.
FYI: I use bcm43xx-fwcutter for my wireless driver.

---

### Post by Arthur Archnix on 2007-11-08
I'm using the intel wireless, so that may be an issue.

I've noticed some app armour notices coming up after waking from suspend, with respect to permissions and power settings. So you may want to remove app/armour as a troubleshooting technique. If it makes a difference, you'll know what to investigate.

I had to change my power settings under System, Preferences to enable lid-close suspend, as it's not enabled by default.

---

### Post by bloodniece on 2007-11-08
Here are the dmesg outputs from both a Compiz enabled and disabled sleep and wakeup.  I'm not smart enough to determine what is happening, but it does look like it detects the lid switch.

P.S.  I could get wireless working again after a Compiz sleep and wakeup by issuing this command.
```
sudo /etc/init.d/dbus restart
```This is not pretty but it works.

>  I had to change my power settings under System, Preferences to enable lid-close suspend, as it's not enabled by default.

Yeah, I knew about that, but it still does not work.

---

### Post by bloodniece on 2007-11-17
Well, my 530 still does not sleep when I close  the lid.  So, I backed up and installed Fedora Core 8 and sleep works fine in FC8.  I really do not like FC or its packaging system so I'm back to Ubuntu.  Plus the Ubuntu forums are much nicer. :)

So what gives?

---

### Post by Arthur Archnix on 2007-11-17
I'd post a new thread on this specific issue. If it's solved you can always come back here and link to it.

---

### Post by bloodniece on 2007-11-17
ok, good idea.  thanks

---

### Post by Arthur Archnix on 2007-11-19
Update and FYI: My HP 530 was affected by the Load/Unload Cycle Issue that is putting laptop hard-drives at risk. I had an average of 44/hour over the last 2000+ hours. Look for Ubuntu Daemons posts on the subject for the fix, and to confirm that you are affected.

EDIT: Here it is [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by jose.mico on 2007-11-19
Regardless of whether my laptop lid is open or closed, /proc/acpi/button/lid/*/state reports always "open". But after an hibernate - resume cycle, the lid switch works properly (!!!?).

Besides that, the second time that I wake-up from suspend state, the screen stays blank and I must press any key several times in order to get to the login screen.

---

### Post by bloodniece on 2007-11-24
> **jose.mico said:**
> Regardless of whether my laptop lid is open or closed, /proc/acpi/button/lid/*/state reports always "open". But after an hibernate - resume cycle, the lid switch works properly (!!!?).

Besides that, the second time that I wake-up from suspend state, the screen stays blank and I must press any key several times in order to get to the login screen.

I have the same issue.  Sleep worked fine for me using Fedora Core 8, but I hate the FC8 packaging system so I'm back to Ubuntu.

---

### Post by bloodniece on 2007-12-05
UPDATE:

I moved to Linux Mint (Daryna) and sleep and the lid switch now work beatifully for my HP 530.  I'm not sure how Mint handles ACPI compared to Ubuntu,but I'm pleased that it works.  I can maybe post the ACPI configs from Mint here for anyone interested.


Cheers!

---

### Post by Arthur Archnix on 2007-12-05
I'd like to see it. My wireless works better when waking from sleep after editing Gconf to have wireless disconnected on sleep. Sound works from sleep, but I have to mute, then unmute. But after two or three sleeps sometimes things start going sidways and I need to reboot.

---

### Post by Kapteeni on 2007-12-07
> **jose.mico said:**
> Regardless of whether my laptop lid is open or closed, /proc/acpi/button/lid/*/state reports always "open". But after an hibernate - resume cycle, the lid switch works properly (!!!?).

Besides that, the second time that I wake-up from suspend state, the screen stays blank and I must press any key several times in order to get to the login screen.

So you have hibernate and suspend somewhat working in Gutsy? Did it need any tweaking, or did it work out of the box?

---

### Post by dusty_dante on 2007-12-17
I have successfully installed Gutsy on an HP 530 (coreduo, GMA950, intel wireless) with few modifications. Suspend, wireless, and audio work flawlessly. This is my second install of Gutsy due to problems with suspend and compiz in the first install. The only difference between the two installations is that the first was installed on an unformatted partition, while the second was installed over my original Ubuntu installation.

Compiz worked out of the box in the second installation, as did the Intel wireless card (using the restricted driver). I know from a previous installation on another system of potential driver woes with Broadcom cards. Audio worked without a hitch thanks to a slight modification in tobogdan.veringioiu's workaround: add the line "options snd-hda-intel model=laptop" into /etc/modprobe.d/alsa-base, and restart the system. I dualboot with Vista and have to boot twice into Ubuntu after a Vista session in order for sound to work properly again, as has been reported elsewhere.

I'm unsure if suspend worked out of the box as well since I applied a fix right after the second installation. The fix simply involves adding "acpi_sleep=s3_mode" to the line "kopt_2_6_8=root=/dev/hdc1 ro" (so that the line, modified, reads "kopt_2_6_8=root=/dev/hdc1 ro acpi_sleep=s3_mode") located in /boot/grub/menu.lst. I don't know why, but the modification in the line disappears after a suspend or restart. In my first installation, the notebook would no longer wake properly (the computer would startup, but not the monitor) once the line returned to its original form, while in the second installation suspend continues to work despite the modification disappearing. That suggests suspend may have worked out of the box in the second installation. 

Hope that helps someone.

Paul

---

### Post by jose.mico on 2007-12-17
> **Kapteeni said:**
> So you have hibernate and suspend somewhat working in Gutsy? Did it need any tweaking, or did it work out of the box?

Yes, I got hibernate and suspend working out of the box (with the noted caveats).

---

### Post by netpork on 2007-12-24
Greetings, 

I have installed gutsy, everything works apart from the sound. Tried everything, and can't make it work. Hopefully someone could give me some tips...

sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


Sound chip is: Conexant CX20549 (Venice)

Tried installing new Alsa version, but still no sound. :(

Thanx in advance. :)

---

### Post by netpork on 2007-12-24
ok, I've got sound. Done steps explained here:
[http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+530]("http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+530")

---

### Post by wally83 on 2008-01-11
Got HP 530 with Celeron and Broadcom wireless today.

It was unbelievable pain to try to install wlan on Windows XP and Ubuntu Gutsy. I actually gave up with Ubuntu, and just hibernate and then wake up the laptop and... not only lid closing detection started working, but my wlan works too!

I also installed bcm43xx-fwcutter and found that wl_aptsta.o somewhere
method is [COLOR="DarkRed"][descripted here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear").[/COLOR]

---

### Post by mrbloom on 2008-01-20
hallo everbody,

i've just installes ubuntu 7.10 on my hp 530.

i am having these two problems;

1)audio is instable, it's not present at every boot af ubuntu,
wheter it's present or not is apparently non deterministic. sometimes i hear well and then
at the next reboot i can hear nothing,
it's seems to be the same problem you have talked about an i also added the line in 
/etc/modprobe.d/alsa-base but it did not changed the attidute of my laptop

2) i can hear a strange 'tic' from my hard disk that i can't hear on windows. it happens when no data are being written. in other words when my hd should be idle. 
does it happen to you too ?

---

### Post by dconstruct on 2008-01-20
sorry, i'm not that great with the terminal yet.  how do i get to edit that file to where i can add that line of code?  thanks!

---

### Post by dconstruct on 2008-01-20
and by adding "that line of code", i meant the sound code.  i'm trying to get my headphones to mute the internal speakers.  thanks!

---

### Post by Arthur Archnix on 2008-01-20
> **mrbloom said:**
> hallo everbody,

i've just installes ubuntu 7.10 on my hp 530.

i am having these two problems;

1)audio is instable, it's not present at every boot af ubuntu,
wheter it's present or not is apparently non deterministic. sometimes i hear well and then
at the next reboot i can hear nothing,
it's seems to be the same problem you have talked about an i also added the line in 
/etc/modprobe.d/alsa-base but it did not changed the attidute of my laptop

2) i can hear a strange 'tic' from my hard disk that i can't hear on windows. it happens when no data are being written. in other words when my hd should be idle. 
does it happen to you too ?

I had the same issue as you with respect to sound. Removing Windows completely solved the issue for me. Others have reported that removing the power cord then rebooting sometimes works for them. I've found that resetting the bios to defaults, then doing a hard power down worked best for me.

With respect to number 2, that's a symptom of the infamous laptop hard-drive killing bug. You should head over to this thread immediately. I was affected and applied to the fix to my great satisfaction. [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

---

### Post by Arthur Archnix on 2008-01-20
> **dconstruct said:**
> and by adding "that line of code", i meant the sound code.  i'm trying to get my headphones to mute the internal speakers.  thanks!

Open a terminal and type in the following commands:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
gksudo gedit /etc/modprobe.d/alsa-base
```
That backs up your original file, then opens the file for editing. Paste this down at the bottom:
```
# Fix to automute speakers when audio-out jack is plugged in
options snd-hda-intel model=laptop
```
Save, close and reboot.

---

### Post by mrbloom on 2008-01-21
> **Arthur Archnix said:**
> I had the same issue as you with respect to sound. Removing Windows completely solved the issue for me. Others have reported that removing the power cord then rebooting sometimes works for them. I've found that resetting the bios to defaults, then doing a hard power down worked best for me.

With respect to number 2, that's a symptom of the infamous laptop hard-drive killing bug. You should head over to this thread immediately. I was affected and applied to the fix to my great satisfaction. [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

thanks for your answer,
i am going to fix this bad bug (even if i did not understand much at the first reading of the page you linked ](*,) )

anyway i found out that the famous click can actually be heard on windows too, but less frequently.
but it should be normal, shouldn't it ?

---

### Post by Arthur Archnix on 2008-01-21
A few clicks is normal. It's your hard-drive parking and unparking, which saves power and prevents damage to the hard-drive. The cause of the bug isn't known yet. It could be programs writing to the hard-drive causing unnecessary disk activity, it could be bad disk management defaults chosen by the drive manufacturers themselves.

The most important thing is to see if you're affected. There's a little test you can do with smartmon tools, that ubuntudemon explains. And then the fix, if you're affected is really simple too. 

Everything you need to know is in ubuntudemon's threads, though you may find more answers by scrolling through the comments.

I think all HP laptop users should check to see if they're affected, but certainly HP530 users should check.

---

### Post by dconstruct on 2008-01-24
when I type in that code, and it opens the gedit to edit the alsa code, it's completely empty.  so i'm guessing that means that i don't have that alsa.  how do i figure out what alsa i've got and how to fix it?  lspci?  here is the output for that:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

any help or suggestions?

---

### Post by Arthur Archnix on 2008-01-24
That's my fault. There was a typo. I typed **mode**probe, instead of **mod**probe. Should work now as I've fixed the command.

---

### Post by varzariu,nicolae on 2008-01-26
i bought today the HP 530..all works fine beside one thing. when i'm on AC power (without battery) the display is very bright and shiny..when i remove the AC Power, and im on Battery power(100% charged) the display gets darked and its not so bright and shiny anymore..does anyone know why is this happening?

---

### Post by varzariu,nicolae on 2008-01-26
i found out..its by default like this not to use a lot of Battery, you can set contrast with fn + f7/f8..

---

### Post by YanalAlHasan on 2008-01-30
Hello,
I want to know if injection in aircrack using the broadcom wifi card on the hp 530 works.
Thanks in advance.

---

### Post by SubTerRaiN on 2008-02-02
i`ve read that HP 530 suffers from hdd-killer bug in ubuntu. is it true?

and second, is the wifi button working in ubuntu as in windows, let` s say: when it`s off - no wifi, when it`s lighting blue - wifi is working ?

thanks!

---

### Post by revford on 2008-02-02
My HD hasn't died, so I don't think there is a killer HD bug.

Yes the Wifi button/light works for me.

---

### Post by Arthur Archnix on 2008-02-02
The fact that your hard-drive hasn't died is not the way to determine if the bug affects you. There is a link I posted to the authoritative thread on this issue, which includes easy steps to see if you're affected and an easy resolution for those not wanting to wait until Hardy is released. Scroll up to find it.

And I am affected, with my HP 530, so I would strongly recommend all HP 530 owners use that thread and use Ubuntu Demon's test to see if you're affected. Then read the thread and his comments to understand the pros and cons of 'fixing' it.

And my wifi light works too, better than VIsta actually. Since under Vista, the light flashes when transmitting, which is annoying. On Ubuntu it flashes only when it is not connected or connecting, then it turns solid blue.

Ubuntu 1 | Vista -1,232

---

### Post by revford on 2008-02-07
I checked it out, looks like the disk was wearing down too fast.  I've been away and applied the fix.

Cheers.

---

### Post by jose.mico on 2008-02-08
I've also applied the patch for the Load_Cycle_Count, as Arthur Archnix suggested. Currently I have a Load_Cycle_Count of 182651 in 864 hours of power on (3.5 parks per minute!!!). Without the patch I'll reach the limit in four months...

I tried lower  hdparm -B values to fix the issue, for my Hitachi HTS541612J9SA00 "hdparm -B 192 /dev/sda" seems to work fine. I used 192 instead of 254 in order to allow some APM by the disk, but really I don't know if this makes a difference.

---

### Post by statto1977 on 2008-02-19
Newbie here.

I (rightly or wrongly) installed Ubuntu in a 30gig partition on my hard drive dual-booting with Vista, before I read any of this thread. The installation was fairly painless and most things worked out of the box, including wifi on my WPA protected network.

I had sound problems initially, both the 'no sound at all' problem, and the 'not muting speakers when headphones plugged in' problem. Both are now resolved thanks to the information found here.

Regarding the hard drive problem, I'm going to monitor it over the next week or so. Am I right in thinking this issue will only rear it's head when running from the battery, or can it occur when the AC is powering things? I ask because I do 90% of my work plugged in, so it may not be much of an issue anyway.

Thanks to everyone who posted so much useful information in this thread, be it comments or links to other stuff. I've briefly visited the forums in the past, and it was the availability of help that convinced me to give Ubuntu a try. :)

---

### Post by Arthur Archnix on 2008-02-19
If you're affected it will affect you regardless of whether you're plugged in or not. That's kinda the whole point of the bug actually. It has to do with head parking. Your disk parks your head to protect it from bumps and such, keep it cool, save power. The problem is that hard-drives can only take so many head-parks, after which they tend to die. Some hard-drives can handle 600,000 parks, or at least they're rated for that many. So, if hard-drives are supposed to last about 600,000 cycles, and they're also supposed to last for 3 years, you shouldn't have more than 600,000 cycles in three years.

If you read the bug reports you'll learn more, and the math will be better too, but essentially, what all of the above means is let's say that your hard-drive is supposed to have on average 10 cycles an hours (this is just an example to explain the bug). More if you're on battery (because if you're mobile you want protection from bumps), and less if you're plugged in. But you know, over 100 hours let's say 1,000 cycles. If you are affected by the bug that number will be something like 64,000 after 100 hours.

That's why it's called the 'hard-drive killer bug'.

I haven't seen anyone look at whether this affects Vista, but it does affect other Linux distros (Mandriva, Debian, Fedora). If you plan on using Ubuntu for any serious amount of time you should look into whether you're affected using the links on this thread.

---

### Post by statto1977 on 2008-02-19
Thanks for the clarification. I'm looking into it, and at the moment that sounds quite promising, as my figure is only 15,000 and I was using it for a few hours last night (the laptop is about three months old). I'll check it each day for the next week or so just to monitor things. Thanks again.

---

### Post by statto1977 on 2008-02-19
It became pretty evident immediately that I'd got the problem, as a figure of 15,900 jumped to 16,200 in the space of an hour! I've actioned the ugly fix so I'll continue to monitor the situation.

---

### Post by Arthur Archnix on 2008-02-20
I don't know why exactly, it might have something to do with adding, then removing compiz, or perhaps the new intel driver, but whatever the reason, I found I couldn't wake up the screen from suspend reliably anymore. It would stay black. 

Sometimes switching to another terminal helped. Sometimes nothing helped. Anwyay, if this sound similar to a problem you're having you might want to try this fix, as it *appears* to have fixed the problem. Open this file...
```
gksudo gedit /etc/default/acpi-support
```
And uncomment this line:
> # Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

---

### Post by statto1977 on 2008-02-20
Has anyone been able to install VMware Player on their 530? I get the following message:

VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

I wouldn't be too bothered, but I have an mp3 player that probably isn't going to work without running a virtual XP installation.

---

### Post by Arthur Archnix on 2008-02-21
No, but virtualbox works a treat.

---

### Post by Arthur Archnix on 2008-02-27
I've been playing with powertop, the utility from intel to see how much power you use and to extend the life of your battery. Generally, the hp530 does pretty good. Disabling wifi will obviously help extend battery life a great deal. Here's another little trick, that has a small impact, but is easy to implement:

If you do not need the 'wake-on-lan' provided by the ethernet card, but which is not configurable in bios, you can turn it off by adding the following line to /etc/rc.local
```
ethtool -s eth0 wol d
```

You can check to see if it's currently set to wake-on-lan by typing:
```
sudo ethtool  eth0 | grep Wake-on
```
If it returns a 'g' then its on. 'd' means off. You'll have to reboot for the changes to take effect.

---

### Post by plzsayomg on 2008-02-27
yes, HP is a nice brand, but ASUS is nice either, come and  check [www.viccol.com](www.viccol.com) or [www.7mmo.com](www.7mmo.com)... yay:guitar:

---

### Post by Arthur Archnix on 2008-03-18
Nevermind.

---

### Post by nolongeriprocs on 2008-03-20
Hi

I can't get Ubuntu on my HP530 to work it fives me the following error message:

(WW) No matching Device section 
(EE) No Devices Detected


In my xorg.conf it says driver:  "i810" but its not working
I tried "vesa" but with the same result :(

Can someone help me?






hp530:

Intel Core™ Duo (T2400 2x 1,83 GHz )
2048 MB DDR2 SDRAM
15,4" 1280 x 800 (WXGA TFT)
Intel Graphics Media Accelerator 950
120 GB Hard Drive (dunnow if this rly matters)
56K V.92 Modem
Ethernet LAN 10 MBit/s, 100 MBit/s
Intel PRO/Wireless 3945ABG WLAN (802.11a/b/g)
Sound : Conexant CX20549 Audio

---

### Post by Belisarivs on 2008-04-14
Hi.
I've upgraded to Hardy on my HP530

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

However, I failed to make suspend to disk working. I enadled double console swith in acpi-support, but it didn't help.

It freezes during waking from suspend. I tried s2disk, but it says that image doesn't exist. I'm not eager to mess with initrd as suggested in manual. Have you any idea how to make it working?

---

### Post by Belisarivs on 2008-04-14
> **iprocs said:**
> Hi

I can't get Ubuntu on my HP530 to work it fives me the following error message:

(WW) No matching Device section 
(EE) No Devices Detected


In my xorg.conf it says driver:  "i810" but its not working
I tried "vesa" but with the same result :(

Can someone help me?






hp530:

Intel Core™ Duo (T2400 2x 1,83 GHz )
2048 MB DDR2 SDRAM
15,4" 1280 x 800 (WXGA TFT)
Intel Graphics Media Accelerator 950
120 GB Hard Drive (dunnow if this rly matters)
56K V.92 Modem
Ethernet LAN 10 MBit/s, 100 MBit/s
Intel PRO/Wireless 3945ABG WLAN (802.11a/b/g)
Sound : Conexant CX20549 Audio

Post you xorg.conf please.

---

### Post by nolongeriprocs on 2008-04-14
> **Belisarivs said:**
> Post you xorg.conf please.


Hi

I managed to get it to work on my own by using Gutsy Gibbon :/ (sry for not editing but I had lots of stuff to do and just recongnized when I got the "reply e-mail"). I'have now upgraded to Hardy (Kubuntu) from Gutsy and got no 3D support (not sure if i had it before) :(. -->>Using GMA 950<<--(see notebook hardware in previous post). I can't run compiz nor warsow or any 3D application with more then 1 FPS :(.
I've tried reinstalling "libgl1-mesa-dri" without an outcome T.T
I've also tried reconfiguring my xorg.conf via "sudo dpkg-reconfigure xserver-xorg" without a result :(


Here is my xorg.conf (important part)
```
Section "Device"
   Identifier   "Intel Corporation Intel Default Card"
   Driver      "intel"
   BusID      "PCI:0:2:0"
EndSection

Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Intel Corporation Intel Default Card"
   Monitor      "Generic Monitor"
   DefaultDepth   24
   SubSection "Display"
      Modes      "1280x800"
   EndSubSection
EndSection 
```

I've tried adding 
```
Section "DRI"
    Group        "video"
    Mode        0666
EndSection
```

without any success :(


I've got the output of glxgears here:

```
4958 frames in 5.0 seconds = 988.402 FPS
5160 frames in 5.0 seconds = 1031.983 FPS
5118 frames in 5.0 seconds = 1023.223 FPS
5260 frames in 5.0 seconds = 1048.892 FPS
5100 frames in 5.0 seconds = 1016.572 FPS
5222 frames in 5.0 seconds = 1040.501 FPS
5100 frames in 5.0 seconds = 1017.722 FPS
5220 frames in 5.0 seconds = 1041.827 FPS
5240 frames in 5.0 seconds = 1044.388 FPS
5080 frames in 5.0 seconds = 1014.912 FPS
5140 frames in 5.0 seconds = 1024.710 FPS
5067 frames in 5.0 seconds = 1009.920 FPS
5220 frames in 5.0 seconds = 1040.776 FPS
5260 frames in 5.0 seconds = 1050.146 FPS
5280 frames in 5.0 seconds = 1053.881 FPS
5240 frames in 5.0 seconds = 1046.223 FPS
5220 frames in 5.0 seconds = 1043.792 FPS
5240 frames in 5.0 seconds = 1044.143 FPS
5266 frames in 5.0 seconds = 1049.317 FPS
5240 frames in 5.0 seconds = 1046.641 FPS
5240 frames in 5.0 seconds = 1047.918 FPS
5240 frames in 5.0 seconds = 1044.165 FPS
5140 frames in 5.0 seconds = 1025.483 FPS

```

and of course my xorg.conf + log and the "glxinfo" output.



GLXINFO output: [http://ubuntuusers.de/paste/169467/](http://ubuntuusers.de/paste/169467/)

plz note "direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbo
4	se)"



/var/log/Xorg.0.log : [http://ubuntuusers.de/paste/169466/](http://ubuntuusers.de/paste/169466/)

 Btw. I got the common HP530 problems aswell: No Hibernate/Suspend; No "close lid detecton". Sound works just fine. I got win vista dual boot.


 -> If I forgot some informations of high importance plz let me know
 -> please excuse my english
 -> and ...
I would really appreciate some help ^^

---

### Post by Belisarivs on 2008-04-15
This is my working xorg.conf. Try it.

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

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,cz"
	Option 		"XkbVariant"  	",qwerty"
	Option 		"XkbOptions" 	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

This is interesting, but more info wouldn't hurt.
```
699	(II) intel(0): direct rendering: Failed
```

---

### Post by nolongeriprocs on 2008-04-15
> 

This is interesting, but more info wouldn't hurt.
```
699	(II) intel(0): direct rendering: Failed
```

I'm afraid I don't know how to provide the requiered information. If you could explain me step by step I will try my best :). (probably I'm just missing a console command or s'th to post the output)

To your xorg.conf I tried it but forgot that you are probably using gnome :P. So xD ended up with the message "displayconfig-gtk" missing or s'th like that. I replaced it with my old xorg.conf and tried taking just the last enrtry of your xorg.conf


I replaced my old
```

Section "DRI"
    Group        "video"
    Mode        0666
EndSection

```

with your new 

```

Section "DRI"
        Mode    0666
EndSection

```

but ended up not beeing able to startx server with the following message

```

~~~ There was an error parsing the config file ~~~ (not sure about that line couln't copy paste it)
Connection reset by peer .... (uncomplete + not sure about that line )
No such process (errno 3): Server Error

```

---

### Post by Belisarivs on 2008-04-16
I don't know how to get more information. It was just complaint.

If you use same book as I, try my whole xorg.conf.

---

### Post by nolongeriprocs on 2008-04-16
> **Belisarivs said:**
> I don't know how to get more information. It was just complaint.

If you use same book as I, try my whole xorg.conf.

Hmm how I said thats not possible because I'm using KDE (Kubuntu) and everytime I try to start x ,with your config it, shows me that weired error message with the missing gnome-config file :/

---

### Post by Belisarivs on 2008-04-16
Aha. I missed it, sorry.

But it has nothing to do with GNOME. It is configuration of xorg regardless you run on it.

It doesn't make sense, because I have no problems to run KDE3, KDE4 and E17.

Perhaps "Section files" could make problems.

Try to use my config except that section. Also section "Input Device" where is keyboard set won't fit you.

If it still doesn't help you, try to comment out other sections to locate one causing problems.

If you locate it, don't use it. But rest should work well for you.

As last resort you can also use:

sudo dpkg-reconfigure -phigh xserver-xorg

However, make backups as this will make just minimalist xorg.conf

But it could work.

Good luck

---

### Post by statto1977 on 2008-04-16
I've been trying to connect this to my LCD TV. I connect it, and I've been trying to get it to display via the keyboard shortcut (fn + f4) but with no success. Any ideas?

---

### Post by nolongeriprocs on 2008-04-16
> **Belisarivs said:**
> Aha. I missed it, sorry.

But it has nothing to do with GNOME. It is configuration of xorg regardless you run on it.

It doesn't make sense, because I have no problems to run KDE3, KDE4 and E17.

Perhaps "Section files" could make problems.

Try to use my config except that section. Also section "Input Device" where is keyboard set won't fit you.

If it still doesn't help you, try to comment out other sections to locate one causing problems.

If you locate it, don't use it. But rest should work well for you.

As last resort you can also use:

sudo dpkg-reconfigure -phigh xserver-xorg

However, make backups as this will make just minimalist xorg.conf

But it could work.

Good luck


Ok thx alot I will try this and post the result!

I will do this tomrrow because I currently have no acess to my notebook.

so thx in advance as always ;)

---

### Post by 420arne on 2008-04-16
I am a complete newbe...and i am using a hp 530 with linux mint. what do i have to do to make it possible to watch youtube videos in full screen? full screen quits after half a second...
pls help...

---

### Post by nolongeriprocs on 2008-04-17
Hi it's me again :/ 

unfortunatelyit your config doesn't seem to work with my system :/. I removed the Module and File entries and replaced the keyboard entry, but ended up with the same result.

So I tried "sudo dpkg-reconfigure -phigh xserver-xorg" end ended up with that config: (but still without direct rendering and my wacom tablet stopped working)

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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```


And here is my whole xorg.conf I just recognized that I haven't posted it yet my bad ( I'm rly sorry about this issue) So here it is perhaps you know which categories have to be adjusted to fit your config :/.
```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "pad"
        Driver      "wacom"
        Option      "Type" "pad"
        Option      "Device" "/dev/input/wacom"
        Option      "ButtonsOnly" "on"
        Option      "Button9" "2"
        Option      "Button13" "3"
        Option      "USB" "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "pad" 		"SendCoreEvents"
EndSection

#
#Section "DRI"
#       "Mode"    "0666"
#EndSection

```


- thx in advance ;)

---

### Post by Belisarivs on 2008-04-18
Why do you have Section DRI commented out?

You could try IRC on freenode, chatroom "ubuntu+1"

Perhaps they could help you.

With my config, try to search which option does make it useless to you and comment it out (and have a look at log of Xorg).

We both use Hardy, we both have same notebook. It doesn't make any sense that config, which works perfectly for me doesn't work for you at all.

---

### Post by nolongeriprocs on 2008-04-18
> **Belisarivs said:**
> Why do you have Section DRI commented out?



1st its not changing anything :P (for me)
2nd it is the one from your config and with it my x server will not start :/ (but even without that part your xorg conf doesn't work for me)

> **Belisarivs said:**
> 

With my config, try to search which option does make it useless to you and comment it out (and have a look at log of Xorg).

We both use Hardy, we both have same notebook. It doesn't make any sense that config, which works perfectly for me doesn't work for you at all.

I rly don't know. I have compared them via hand and with grep but can't find anything like "load gnome-interface" (my only explanation for this is that u are using gnome and I'm using KDE) :/ but seems like the configs match except for the keyboard /  file / and modules stuff.

> **Belisarivs said:**
> 

You could try IRC on freenode, chatroom "ubuntu+1"

Perhaps they could help you.



thx I will give it a try



Edit:
here is my lspci output if anyone is interested: [http://paste.ubuntu-nl.org/63647/](http://paste.ubuntu-nl.org/63647/)



 - iprocs


Edit2:

kk I got nice support however xD I didn't changed anything for me right now

I just know now that it isn't loading the DRI part probably so if anyone knows anything I would reaally appriciate it.

---

### Post by Belisarivs on 2008-04-22
Why there is nothing like that in your xorg.conf?

```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

```

Especially modules "dri" and "glx" must be loaded to make acceleration work.

---

### Post by chelion on 2008-04-22
Sorry that I can't help with the issue being discussed at the moment I am fairly new to Ubuntu. I was wondering if someone could quickly help me please. 

I have got the HP 530 with the "Broadcom Corporation BCM4310 USB Controller (rev 01)" wireless and have 7.10 (gutsy gibbon is it not?). I have tried firmware and disniswrapper solutions both with no luck, I know I must be doing something wrong dispite following several different guides to the letter. 

Could someone who has this card working please tell me which solution worked for them and maybe point me in the direction of a guide for it as I have not been able to find any which work. My card does not show up under System>administration>network and the wireless button won't glow (although flashes on startup), one solution I read said to go the restricted drivers thing but I only get a message saying I do not need any. 

Thank you, any help would be greatly appreciated.

---

### Post by Belisarivs on 2008-04-24
Run synaptic and search for "broadcom" in "names and descriptions".

Install package you'll find fitting for you. Should help.

---

### Post by captainian on 2008-04-25
Hi,

The graphics card does not work with Hardy. 7.10 was okay. I tried to install Fedora 9 and the same issue appears. It seems to be a kernel bug as reported here:

[http://bugzilla.kernel.org/show_bug.cgi?id=10395#c4](http://bugzilla.kernel.org/show_bug.cgi?id=10395#c4)


I'm a complete Linux noob, so can anyone tell me how to install the patch mentioned in the link? Do I need to do something myself? Or do I wait for an automatic update? I would really appreciate advice. Not being able to use 3d is heartbreaking.

---

### Post by y2kprawn on 2008-04-27
I got a new HP530 yesterday, and after not booting into vista basic (yuck) installed Hardy Heron , 8.04.

Results from base install. 
Graphics, at full resolution, fine , I am not needing any hardware accelerated graphics.
Sound is ok, played some mucic on it all is fine. 
Need to get codecs for video when I get access to the proxy network in the place I live at the moment. 
Very Fast, detected my canon pixma MP150 printer no problem. 

Install was pretty quick no bad glitches. However , im not sure is it the hardware, but there is no light on my wireless button, hmmm, methinks there might be some hardware problem there. But it turns off and on my wireless no problem. 

The ticking from the hard drive is a tad worrying though, I mught look at this power management bug thing that everyone is referring to. 

Oh yea, me noobie, me looking forward to liberation from windows, this is my first dedicated ubuntu machine. I also have an NX9420 from HP with Vista for my .NET development and games and Hardy Heron installed on it. No problems, running with graphics acceleration, fan is crazy loud , but there is no hard drive ticking , just as an aside. 

So far so good, if anyone can tell me if the light is on as fefault when their wireless is on it would be great. Also if my drive is marking every 30 seconds should I be worried ? FYI, this is off the battery at the moment.

---

### Post by DingoMD on 2008-04-28
> **y2kprawn said:**
> I am not needing any hardware accelerated graphics.

If you end up wanting it, you can find a solution here: [http://ubuntuforums.org/showthread.php?t=766381](http://ubuntuforums.org/showthread.php?t=766381)

> **y2kprawn said:**
> However , im not sure is it the hardware, but there is no light on my wireless button, hmmm, methinks there might be some hardware problem there. But it turns off and on my wireless no problem. 

Seems to be a bug in Hardy. I have the same problem on my laptop, even though it worked on Gutsy.

> **y2kprawn said:**
> The ticking from the hard drive is a tad worrying though, I mught look at this power management bug thing that everyone is referring to. 

Very likely the "HDD Killer Bug". Look here for a fix: [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

---

### Post by y2kprawn on 2008-04-28
Cool to know about the light for the wireless, cheers, thought it was a hardware failure. 

Just out of curiosity have you had any problem with CTRL+ALT+F1 not bringing up a command prompt? I found that there a while ago, the screen is just blank and I then use CTRL+ALT+F7 to return to the GUI. Don't know if it is a bug or not. 

Thanks for the help on those problems, I don't need fancy GUI, I have that on my accelerated laptop and it fine apart from the fan being like an airplane all the time. The hard drive fix helped, the ticking has gone when the power supply is connected. 

Thanks for the help. I since I started my managed to configure my 3G (crappy) datamodem for the internet on the go, got Eclipse (kinda) working and have connected to many wireless networks, this laptop seems to be just fine with all of those things, and I am writing up my final year projects in openoffice as well. All is good with this release and this laptop. Will let people know how I get on with disk burning as well. The only thing I hate about the laptop is how easy it is to brush the touchpad when im typing. Very annoying, but I will get used to it I hope.

---

### Post by Belisarivs on 2008-04-29
For working wifi led you must install also linux backport modules package.

It worked for me, will most probably work for you.

---

### Post by DingoMD on 2008-04-29
> **y2kprawn said:**
> Just out of curiosity have you had any problem with CTRL+ALT+F1 not bringing up a command prompt? I found that there a while ago, the screen is just blank and I then use CTRL+ALT+F7 to return to the GUI. Don't know if it is a bug or not. 
I had that problem with Gutsy but Hardy fixed it. Can't help you there, since I didn't change anything.

> **y2kprawn said:**
> The only thing I hate about the laptop is how easy it is to brush the touchpad when im typing. Very annoying, but I will get used to it I hope.
Same problem, fix here: [http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052)

> **Belisarivs said:**
> For working wifi led you must install also linux backport modules package.

It worked for me, will most probably work for you.
I have tried installing it but my wireless stopped working (unless I suspend and wake my laptop, and even then, I can only toggle wireless once before it stops working again)

---

### Post by chelion on 2008-05-02
> **Belisarivs said:**
> Run synaptic and search for "broadcom" in "names and descriptions".

Install package you'll find fitting for you. Should help.

Have tryed that several times (including just now just in case) and it does not seem to make any difference. The wireless card still won't show up on the network manager and restricted drivers still says I don't need any. Thanks for the suggestion anyway though.

Any more ideas anyone?

---

### Post by nimphelos on 2008-05-04
Hello people,

I just bought an HP 530 yestarday. It used to have FreeDOS on it. I installed Hardy on it. 

At start 3D video didn't work. I installed kernel fix. Now its working great.

Wireless light doesn't work at all. I tried to install backports but with backports when I turn it off I can't turn it on again. So I uninstalled backports. Now wireless button works but light doesn't.

I got a serious problem with lid. At power management it says blank screen when lid is closed. But when lid closed and opened back again it wont let LCD work again. I need to press power button and reboot the laptop. For now I selected do nothing when lid is closed. Is there any fix around?

Thanks...

Edit: Lid problem solved after disabling compiz.

---

### Post by vies on 2008-05-12
Hi everyone,

I bought HP 530 laptop as second computer recently and I installed Hardy in it. Everything else seems to work (wireless after little tinkering) but suspend/resume cycle seems to give me some trouble.

Basically, suspend and resume both work, but after resume, screen brightness adjustment doesn't  work. Not when I unplug the power, or when I try to adjust it from fn+f7/f8 buttons.
Since the battery time is as limited as it is, I would like to maximize it by having screen dimmed while on battery. For now, I'm just turning the laptop off instead suspend since dimming works after boot.

Has anyone encountered similar problem? Is there some service that doesn't resume correctly and needs to be restarted?

I'm currently at work, so I will post lspci and other info later when I get home.

Vies

---

### Post by statto1977 on 2008-05-12
I'm still on Gutsy, and the screen dim button works fine on that.

---

### Post by y2kprawn on 2008-05-12
> **nimphelos said:**
> Hello people,


At start 3D video didn't work. I installed kernel fix. Now its working great.


.

 
can you tell me where you got the Kernel fix from ?
Also when you enabled 3D acceleration and compiz , have you any problems when running off battery, mainly batter life related ? Or is the acceleration disabled when you remove from the mains power supply ?
Thanks in advance

---

### Post by dabugas on 2008-05-14
> **vies said:**
> 
Has anyone encountered similar problem? Is there some service that doesn't resume correctly and needs to be restarted?


If I recall correctly suspension used to work perfectly on Feisty, but then became somewhat erratic on Gutsy. Since I almost always use my laptop with a power source at hand, I haven't been interested enough to resolve the issue.

I haven't tried Hardy yet, so I can't help you there. Speaking of which, has anyone tried to migrate from Gutsy to Hardy using the update tool? Experiences, problems, etc?

---

### Post by Arthur Archnix on 2008-05-15
**Vies**, have you tried enabling laptop mode? I'm not sure how to do it on Hardy, but when enabled it should auto-magically dim your screen when on battery.

**Dabugas**, resuming from suspend sometimes fails to bring the video back up. I'm experimenting with it now, and my initial conclusion is that changing the value of POST_VIDEO from "true" to "false" in /etc/default/acpi-support appears to help.
> # Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false
**EDIT: **After an extensive sleep I found that it still failed to wake up from suspend, and so I also disabled save VBE state. Now wakeups are instantaeous. Faster than Windows. I'll let you know if things stay that way or if my screen explodes. :) For the record, the setting is in the same file above and now reads:
> # Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false
As an aside.. my experience has been that upgrading to Hardy is a major pain, and not worth the trouble. I've had great success with this laptop and Ubuntu since Feisty, but with Hardy I began to experience random lockups and kernel panics. I also felt that performance was degraded, and the system used more RAM at inital startup.

If you don't share your laptop with many people then policy kit (a major upgrade from Gutsy) is of almost no value and not worth upgrading. If you don't use external monitors or rotation then the new xorg is of almost no value and not worth upgrading. If you don't use shared volumes or connect to a windows network frequently then the new gvfs is of almost no value.

Basically, I feel that you should have a compelling reason to upgrade from Gutsy to Hardy. Either because something simply doesn't work on Gutsy, or there is some feature in Hardy that you need. Otherwise, it's probably not worth the trouble. 

The only feature I loved in Hardy that I miss is the new clock that shows locations and weather. OO2.4 is nice, but the improvements are incremental. Lastly, FF3 is available for Gutsy in backports. 

If you can, wait six months for others to iron the bugs out of xorg.7.3.... openoffice 3.0 will probably find its way into Ibex.

Suspend and resume worked much better in Hardy than in Gutsy. But the fix for the laptop load cycle issue is less clear on hardy. Supposedly, enabling laptop mode fixes it.The scripts that work on Gutsy apparently do not work on Hardy. And we should all know by know that HP laptops (especially the 530 models) are affected by the laptop killing bug.

---

### Post by statto1977 on 2008-05-15
Thanks for that. Excellent post, clearly explained. Think I'll stick with Gutsy, and leave Hardy for my desktop (which it's working fine on). :)

---

### Post by y2kprawn on 2008-05-15
Its weird, I applied the kernel patch to get the hardware acceleration , but now Hibernate and Suspend do not work ,machine does not come out of either state well at all. 

Also the machine will not recover if it is set to blank the screen after a set period of time.
Is this just a laptop thing or is the whole graphics handling thing in Hardy really broken?
I could live with it if I was not so used to closing the lid all the time.

---

### Post by jablan on 2008-05-19
I disabled Compiz (it is Compiz, not the direct rendering driver patch which messes suspend) in order for suspend to work (I didn't get to properly try out hibernate yet).

Maybe there is a certain combination of settings in /etc/default/acpi_support which would solve this problem, we should experiment a little bit. The problem is that you need to reboot so often while experimenting, and it hurts... :(

Also, I have noticed HD killer bug, and the hdparm patch seems to work OK. I don't know the right value for -B param though (I use conservative 254), there should be one that balances power consumption and HD wearout.

Otherwise, really great laptop for the money and fine hardware support under Linux!

The thing irritates me the most is lack of HD LED. How cheap you have to be to leave it out?!

---

### Post by y2kprawn on 2008-05-19
> **jablan said:**
> I disabled Compiz (it is Compiz, not the direct rendering driver patch which messes suspend) in order for suspend to work (I didn't get to properly try out hibernate yet).
 
Otherwise, really great laptop for the money and fine hardware support under Linux!
 
The thing irritates me the most is lack of HD LED. How cheap you have to be to leave it out?!
 
I dont use Compiz, I just set the desktop to "advanced" effects. I have found though by setting it to default in the "Appearences" control panel in Preferences, that suspend works fine , but hibernate does not. 
 
So when you set to "default" the suspend works fine, I think any acceleration enabled when coming out of suspend leads to a bad state. Also, if you set the power options to turn off the screen at any time you get the same problem with acceleration turned on. You cannot "wake" the screen. 
 
The HDD light is a strange ommision all right. Another odd thing is that Ubuntu does not enable the Wireless light. 
This is a good laptop for for Linux though, im blad I got one, for the money its worth it, and it was a present to me as well for my 30th bday from my girlfriend, who knows I always wanted to make my own Linux laptop. I have pretty much skipped Vista, I have it on another laptop and how hate it even more when I have to use it. I do miss Visual Studio though, but Im finding Netbeans is getting close to giving me the same experience.
 
I ordered an eight cell battery for the laptop as well, as the default 4 cell has terrible battery life.

---

### Post by Arthur Archnix on 2008-05-19
I decided to install Hardy again over the weekend to see if I could troubleshoot my problems with random freezing and hangs. I'm pretty sure it's from enabling laptop mode. However, there's been an update to the intel video driver since Hardy's release, so that may be a factor too.

Anyway, if you're having problems with freezes and hangs, disable laptopmode. Don't uninstall it. It should not be enabled by default, but if you have enabled it, you may need to revert that change.

Also, the load cycle count issue still applies under hardy. Using the link to Ubuntu Demon's thread on the issue you'll find a link to a SUSE resolution that involves creating two new files under /etc/pm-utils/ or some such. Just follow those instructions (you'll need to add sudo to ubuntufy them) and you should be ok once again. Don't just follow the old instructions for gutsy because those might not work. If you do use them, be sure to test if they are actually working before / after suspend. Try suspending while plugged in, removing plug and resuming and seeing if the correct settings are applied. I've done those sorts of tests with the Suse solution and it works good for me.

EDIT: Actually, no sorry... they're not working after suspend. I was checking wrong. To check, do:
> sudo hdparm -I /dev/sda | grep level

Also of note, under hardy closing the lid will now suspend the machine. :) Nice.

I'll keep troubleshooting this on weekends and if I don't get anymore random freezing then I'll start using it as my main os. It'll be nice to have the world clock applet. :guitar:

---

### Post by ruinen on 2008-05-27
Installed Hardy onto my HP530 and have noted a few minor problems that have already been covered in this thread (i.e no wifi light, hard disk clicking a lot), so I will investigate them later, but I am currently having a problem with virtualization.

I followed the instructions at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) including having to enable Vitualization in the BIOS. However when I try to run KVM I get the warning ...

"Ubuntu does not support running KVM without hardware acceleration"


hmm, at this point I am stuck.

---

### Post by Arthur Archnix on 2008-05-27
> **ruinen said:**
> Installed Hardy onto my HP530 and have noted a few minor problems that have already been covered in this thread (i.e no wifi light, hard disk clicking a lot), so I will investigate them later, but I am currently having a problem with virtualization.

I followed the instructions at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) including having to enable Vitualization in the BIOS. However when I try to run KVM I get the warning ...

"Ubuntu does not support running KVM without hardware acceleration"

hmm, at this point I am stuck.

Well, first the clicking is something you should look into sooner rather than later. Here is the [new thread]("http://ubuntuforums.org/showthread.php?t=805570")

The first post is full of information explaining what's going on and why you should do something about. The second post is the fix for Gutsy and works perfectly. The third post is the fix for Hardy, and there is at the moment some difficulties surrounding suspend resume, but it should be worked out before long.

As for your KVM issue, on my laptop I am able to enable hardware support for virt in the bios, but in fact my CPU does not support hardware virtualization. So you should confirm that your CPU model supports it. If you've got the T2050 like me then sorry, the Bios is lying to you. On a more positive note, Virtualbox works like a dream. Just download it from their website for your version of Ubuntu. A few minor tweaks are needed, but nothing you can't find easily on the forums or the googles.

Unlike most people, I consider the lack of LED a feature. It annoys me having the light on all the time, and I am not looking forward to the patches that bring back the blue led to blind my eyes late at night. :P

If you enable laptop mode, watch out for random hangs. It's possible I was experiencing the firefox disk IO bug that's been resolved. I haven't re-enabled it, but otherwise, hardy has been working well. I experienced a major malfunction the other day that required a complete reinstall, so I still think it's premature to upgrade to hardy. But things are definintely improving quickly.

EDIT: Oh, and to check out your cpu model do this (under hardy)
```
cat /proc/cpuinfo | grep model
```
I don't feel like rebooting, but the command might be slightly different under gutsy. Just cd to /proc and then ls to see the cpu name. Then cat that.

This page from intel might be what you need, or at the very least get you very close, in terms of looking up what your cpu is capable of.
[http://www.intel.com/products/processor_number/chart/coreduo.htm](http://www.intel.com/products/processor_number/chart/coreduo.htm)

---

### Post by ruinen on 2008-05-27
> **Arthur Archnix said:**
> Well, first the clicking is something you should look into sooner rather than later. Here is the [new thread]("http://ubuntuforums.org/showthread.php?t=805570")

As for your KVM issue, on my laptop I am able to enable hardware support for virt in the bios, but in fact my CPU does not support hardware virtualization. So you should confirm that your CPU model supports it. If you've got the T2050 like me then sorry, the Bios is lying to you. On a more positive note, Virtualbox works like a dream. Just download it from their website for your version of Ubuntu. A few minor tweaks are needed, but nothing you can't find easily on the forums or the googles.

[http://www.intel.com/products/processor_number/chart/coreduo.htm](http://www.intel.com/products/processor_number/chart/coreduo.htm)

Haha, just rebooted before I saw your edit about looking at /proc/cpuinfo to save the reboot.

Anyways, I apparently have a T2400, which does have hardware virtualization, so I am still stuck with KVM. Will give VirtualBox a go.

Thanks for the info, will investigate the hard disk stuff now.

---

### Post by ruinen on 2008-05-27
> **ruinen said:**
> Haha, just rebooted before I saw your edit about looking at /proc/cpuinfo to save the reboot.

Anyways, I apparently have a T2400, which does have hardware virtualization, so I am still stuck with KVM. Will give VirtualBox a go.

Thanks for the info, will investigate the hard disk stuff now.

The only thing I can think of with KVM is I had the hardware virtualization off when I installed Hardy. I have no idea if that would effect things though.

---

### Post by Burgi on 2008-05-30
Hi,

I'm a newbie and I have a problem with wifi.
My wifi doesn't work at all. I read many forums what to do, but nothing worked. Yesterday I found that the system does not even recognize the device.

Thank you in advance.

---

### Post by statto1977 on 2008-05-30
Which version?

---

### Post by Burgi on 2008-06-03
8.04 Hardy

---

### Post by statto1977 on 2008-06-03
There seem to be several issues with the HP530 and Hardy at the moment, including wireless issues. I'd definitely recommend going with 7.10 until some of them are ironed out more comprehensively.

Having said that, the system not even recognizing the device seems strange. Does it work with any of the Live-CDs you have? If not, it may be a hardware fault.

---

### Post by caraboy on 2008-06-06
Wireless is working on my HP530, though the light is not on (the blue one).

I have other problems with 8.04. Standby was working for me, now after updates it refuses to resume from standby. It goes into standby, but then I have a black screen when I press the power button to resume. :(

It`s a laptop, so I need this function. Anyone having this problem?

I also have constant hangs when trying to view some movies, and now Audacious is not working (I click play an nothing happens, I did not change anything).

It`s starting to be the worst release so far... :|

---

### Post by caraboy on 2008-06-08
Managed to fix it, reverted back cu 2.6.24-16 kernel, the 2.6.24-18 introduced all the above problems.

---

### Post by y2kprawn on 2008-06-08
> **caraboy said:**
> Managed to fix it, reverted back cu 2.6.24-16 kernel, the 2.6.24-18 introduced all the above problems.

Do you have a link to the instructions to revert to a previous kernel version ?
I have the same problems, but don't have and problems with my wireless, standby is a mess though.

---

### Post by caraboy on 2008-06-08
> **y2kprawn said:**
> Do you have a link to the instructions to revert to a previous kernel version ?
I have the same problems, but don't have and problems with my wireless, standby is a mess though.


I posted on a [blog]("http://www.linux-geek.org/2008/06/08/hp-530-standby-ubuntu/"), but it is in Romanian.


Here`s what you need to do:

Normally you should have the old kernel, so go into
 ```
/boot/grub/menu.lst.
```and comment the lines that boot with the new kernel. It should look like this:
```
[INDENT]#title        Ubuntu 8.04, kernel 2.6.24-18-generic
#root        (hd0,4)
#kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=4228d54c-9b95-4028-874c-b922ff7e0214 ro quiet splash
#initrd        /boot/initrd.img-2.6.24-18-generic
#quiet
 #title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
#root        (hd0,4)
#kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=4228d54c-9b95-4028-874c-b922ff7e0214 ro single
#initrd        /boot/initrd.img-2.6.24-18-generic
[/INDENT]
```Make sure you have a line entry with 2.6.24-16 kernel, and also backup menu.lst before making changes, just in case.

Problem solved!

---

### Post by y2kprawn on 2008-06-08
Perfect , cheers for this , good stuff to know , also my suspend is back working again !

---

### Post by kostaspixxie on 2008-06-13
Intel Graphics Media Accelerator 950 in HP 530 laptop

please .... where are these drivers for Ubuntu 8.04?

---

### Post by caraboy on 2008-06-13
Your video card in 8.04 should work out of the box. My 945gm was instantly recognized, running compiz after reboot. 950 is the chipset.

If not, try installing:
  $ sudo apt-get install xserver-xorg-video-intel

---

### Post by kostaspixxie on 2008-06-14
"Normal" or "Extra Visual Effects" not working...

Terminal prints this:

```
kostas@kostas-laptop:~$ sudo apt-get install xserver-xorg-video-intel
[sudo] password for kostas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kostas@kostas-laptop:~$ 
```



"glxinfo" prints this:
```
kostas@kostas-laptop:~$ glxinfo
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
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
kostas@kostas-laptop:~$ 
```

plz ... some help...

---

### Post by caraboy on 2008-06-14
Type glxgears in your terminal. Is it working? Are the wheels spinning?

---

### Post by kostaspixxie on 2008-06-14
Wheels are spinning but terminal returns me this:

```
kostas@kostas-laptop:~$ glxgears
4925 frames in 5.0 seconds = 983.126 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 16687 requests (36 known processed) with 0 events remaining.
kostas@kostas-laptop:~$ 
```

Any idea please?

---

### Post by Arthur Archnix on 2008-06-14
> Just out of curiosity have you had any problem with CTRL+ALT+F1 not bringing up a command prompt? I found that there a while ago, the screen is just blank and I then use CTRL+ALT+F7 to return to the GUI. Don't know if it is a bug or not. What that does is switch between virtual terminals, or VTs. Ubuntu has six by default, and your 'x' session is on F7. Try the other ones, F2, F3, etc. F1 can be reserved for the active 'x' session depending on your setup. 

> The only thing I hate about the laptop is how easy it is to brush the touchpad when im typing. Very annoying, but I will get used to it I hope.linux to the rescue again. Search the forums for Disable touchpad while typing. Plenty of good posts out there. Just to summarize what you're looking for, is any post that explains to add the Option "SHMConfig" "on" into your xorg.conf in the appropriate place. Adding syndaemon -d to your session. That disables while typing. If you search for posts with my user name I've also explained elsewhere how to make a keyboard shortcut to turn it off completely (look for synclient touchpadoff =0) as well as instructions for having ubuntu automatically turn off your touchpad when a mouse is plugged in, and turned back on when you unplug it.

---

### Post by Arthur Archnix on 2008-07-16
1 week after my laptop went off warranty, the battery life on this notebook went from 1 and 1/2 hours to 10 minutes. :(

I contacted HP and they said, sorry, it's off warranty.

I'm extremely dissapointed. It's a budget notebook, but still, a catastrophic battery failure so soon after the warranty is over is enough to get anyone to pull the tinfoil hat out of the closet.

---

### Post by N0_Named_Guy on 2008-07-17
> **kostaspixxie said:**
> Wheels are spinning but terminal returns me this:

```
kostas@kostas-laptop:~$ glxgears
4925 frames in 5.0 seconds = 983.126 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 16687 requests (36 known processed) with 0 events remaining.
kostas@kostas-laptop:~$ 
```

Any idea please?
When I upgraded my hp 530 for the latest kernel (via Synaptic), 3D acceleration was there... I'm now using compiz... :D

---

### Post by Nuggs on 2008-07-23
Hi all,

This thread is great!  Thanks Arthur, your posts have helped me quite a bit... 

I'm somewhat of a newbie (I've been using Ubuntu for about 4 months now).  I've installed Gutsy on 3 different machine, with different degree of success.  Now, I'm playing with Hardy on my HP530, and I was impress how everything worked out of the box (yeah, I've got the intel wireless controller, so that helps).  

I do have one major problem with the suspend to disk (i.e. hibernate).  I can get the computer to hibernate, and even restart, but then the system is not stable and eventually hangs within 5 minutes from the restart...  Sometime, the system slows down and freezes a few second at a time, all the time getting worst until if finally hangs completely, and other time it just downright hangs...

I searched many forums and google but I didn't find anything reported that is similar...  I'm really at a loss here...

I tried to troubleshoot the system, but my "toolbox" is still rather limited.  I did load gnome system monitor and watched it as the system was freezing, but it doesn't report any process that is taking up cpu.  Once the system is frozen, the "sysrq" magic key works sometime and allow me to unmount the filesystem, but sometime during the reboot, ubuntu reports that the filesystem is "unclean" and does a scan... (this tells me that the kernel didn't process the <alt><sysrq><U> key combo)

The problem was present before I started modifying (or adding) packages.  Right now, I have Compiz loaded, wicd for managing the wireless connections, and I've also just implemented the fix for the excessive HD load cycle (forgot what it is called, but thanks again Arthur!)

Suspend to ram works fine, so at least I can "shut off" the computer without actually having to reboot, but I'm getting a 2nd battery, so I need s2disk to work so I can swap batteries...

Any suggestion?  I'm really stuck here...

---

