---
title: "RadeOn X1300 / No GL acceleration"
date: 2009-04-23
forum: Hardware
---

### Post by Ugluk on 2009-04-23
I've tried both radeon and radeonhd drivers. Neither has GLX, and radeonhd (advertised for X1300 series) is even unable to keep proper screen resolution. What is the problem and how can it be fixed?

---

### Post by krazyd on 2009-04-24
are you on jaunty? this card should work automatically after installation.

---

### Post by Ugluk on 2009-04-24
Well, it does not. What driver package I shall use, and how to enable acceleration?

---

### Post by krazyd on 2009-04-24
what's the output of ```
glxinfo | head -n 40

```

---

### Post by TheRoot on 2009-04-24
> **krazyd said:**
> what's the output of ```
glxinfo | head -n 40

```

Same problem here, and this is my output:
```
# glxinfo | head -n 40
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
```

---

### Post by Ugluk on 2009-04-24
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
```

---

### Post by StuartN on 2009-04-24
These older cards are no longer supported in 3D - fglrx doesn't play with the new X server 1.6 and ATI Catalyst has dropped support for the cards:

[http://forums.scotsnewsletter.com/index.php?showtopic=24480](http://forums.scotsnewsletter.com/index.php?showtopic=24480)

---

### Post by eggplant37 on 2009-04-25
> **StuartN said:**
> These older cards are no longer supported in 3D - fglrx doesn't play with the new X server 1.6 and ATI Catalyst has dropped support for the cards:

[http://forums.scotsnewsletter.com/index.php?showtopic=24480](http://forums.scotsnewsletter.com/index.php?showtopic=24480)

This is so unacceptable that I can't believe it's true. No 3D support for a giant portion of their chipsets that are still in use in millions of laptops? 

Ubuntu devs and ATI shouldn't be surprised if they see a swell in customer complaints as a result.

Frankly, it's idiotic that this isn't working and fully supported.

---

### Post by krazyd on 2009-04-27
> **StuartN said:**
> These older cards are no longer supported in 3D - fglrx doesn't play with the new X server 1.6 and ATI Catalyst has dropped support for the cards:

[http://forums.scotsnewsletter.com/index.php?showtopic=24480](http://forums.scotsnewsletter.com/index.php?showtopic=24480)

Stuart please refrain from spreading unnecessary FUD. If you had bothered to read the OP, we're not discussing fglrx here, but radeon/radeonhd open source drivers.

The fact is that AMD haven't 'dropped' support for these cards, they have just moved the support to the open source driver for all cards R500 and older (cards X1xxx and older). They actually employ people to work on this open source driver.

The open source driver has 3D support for these cards, so in fact support has improved because these older cards now have 3D support out-of-the-box. No need to install extra fglrx drivers.

---

### Post by ped on 2009-04-27
I don't need 3D acceleration, but I was unable to make my dual head config to work, all I get is cloned view. (Kubuntu 9.04 + ATI Radeon X1300 + 2x LCD) (otherwise the default driver works excellent [I didn't try any desktop effects as I hate them])

Do you have any idea if this is already supported in OSS drivers (and just the system settings is lacking option), or when it will be supported?

This is critical issue for me, I can't use 9.04 due to this "regression" (from user point of view it's regression, because before 9.04 there was fglrx, which did work with dual head like charm). I was unable to google any recent straightforward information for this issue, and you seem to be well informed. :) Thank you for any information.

---

### Post by eggplant37 on 2009-04-27
> **krazyd said:**
> Stuart please refrain from spreading unnecessary FUD. If you had bothered to read the OP, we're not discussing fglrx here, but radeon/radeonhd open source drivers.

The fact is that AMD haven't 'dropped' support for these cards, they have just moved the support to the open source driver for all cards R500 and older (cards X1xxx and older). They actually employ people to work on this open source driver.

The open source driver has 3D support for these cards, so in fact support has improved because these older cards now have 3D support out-of-the-box. No need to install extra fglrx drivers.

If this is true, explain then why I've got Warcraft under wine on my Dell Inspiron 1501 with a Radeon Xpress 200M integrated chip only getting a single frame per second after following all the advice I can find with Ubuntu 9.04 just upgraded. All of this was working fine with 8.10 and the Catalyst 9.3 drivers.

Can you do one of two things:
1.  Please stop blowing sunshine up my pooper.
2.  Recommend steps to take to get this working.

Thanks.

---

### Post by trulskvammen on 2009-04-28
> **StuartN said:**
> These older cards are no longer supported in 3D - fglrx doesn't play with the new X server 1.6 and ATI Catalyst has dropped support for the cards:

[http://forums.scotsnewsletter.com/index.php?showtopic=24480](http://forums.scotsnewsletter.com/index.php?showtopic=24480)

The **[Radeon]("http://en.wikipedia.org/wiki/Radeon") X1000 series** was introduced on [October 5]("http://en.wikipedia.org/wiki/October_5"), [2005]("http://en.wikipedia.org/wiki/2005").
Is that old? Then we are a lot of people having old cards, I guess.
By the way my results of glxinfo | head -n 40 is the same as the first respondee.
Dual head. Problems with low max resolution.

---

### Post by krazyd on 2009-04-28
> **ped said:**
> I don't need 3D acceleration, but I was unable to make my dual head config to work, all I get is cloned view. (Kubuntu 9.04 + ATI Radeon X1300 + 2x LCD) (...)
Have a look at the last post on [this thread]("http://phoronix.com/forums/showthread.php?t=16460"), and perhaps adjust the line for your configuration. This forum is also a good resource for graphics-specific stuff.
Also see:
[http://wiki.x.org/wiki/Projects/XRandR](http://wiki.x.org/wiki/Projects/XRandR)
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)
> **eggplant37 said:**
> If this is true, explain then why I've got Warcraft under wine on my Dell Inspiron 1501 with a Radeon Xpress 200M integrated chip only getting a single frame per second after following all the advice I can find with Ubuntu 9.04 just upgraded. All of this was working fine with 8.10 and the Catalyst 9.3 drivers.

Can you do one of two things:
1.  Please stop blowing sunshine up my pooper.
2.  Recommend steps to take to get this working.

Thanks.
It's very simple. Catalyst no longer supports your card. The open-source drivers do, but Mesa is under heavy development at the moment and so 3D with the open source driver is not as fast as fglrx. Yet.
So you can:
a) wait for 9.10
b) remain on 8.10 (which is still supported)
c) give up Warcraft for 6 months. *

* *recommended.*
> **trulskvammen said:**
> The **[Radeon]("http://en.wikipedia.org/wiki/Radeon") X1000 series** was introduced on [October 5]("http://en.wikipedia.org/wiki/October_5"), [2005]("http://en.wikipedia.org/wiki/2005").
Is that old? Then we are a lot of people having old cards, I guess.
By the way my results of glxinfo | head -n 40 is the same as the first respondee.
Dual head. Problems with low max resolution.
Try the link above, and if nothing works, ask on the phoronix forums (the radeon developers are members). I don't have any experience with dual-head.

---

### Post by ped on 2009-04-29
> **krazyd said:**
> Have a look at the last post on [this thread]("http://phoronix.com/forums/showthread.php?t=16460"), and perhaps adjust the line for your configuration. This forum is also a good resource for graphics-specific stuff.
Also see:
[http://wiki.x.org/wiki/Projects/XRandR](http://wiki.x.org/wiki/Projects/XRandR)
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

Try the link above, and if nothing works, ask on the phoronix forums (the radeon developers are members). I don't have any experience with dual-head.

The suggested "xrandr --output DVI-0 --right-of VGA-0 --auto" leads to:
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x1024)
(this looks quite promising, so after I will patch my xorg.conf by hand to have larger virtual resolution, it will probably work, but I'm trying to solve this problem in "simple" way which will be easy to follow for anyone else, so I'm postponing any xorg.conf editing till everything else fails)

phoronix forums require yet another registration, sigh.

I'm going now to further investigate how to get rid of low virtual res and make xrandr work, but it looks like xorg.conf change is very near and inevitable. Sort of pity, it looks a bit "sexy" right now when compared to the old ones from Kubu 6.10 or similar, just:
-------- 8< ------------
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
-------- 8< ------------
And that's all. :D

---

### Post by ped on 2009-04-29
So I did enlarge the virtual screen trough xorg.conf change, and xrandr now doesn't complain about it anymore.

So did I got dual-head? Hell no. ](*,)

See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd/+bug/367776](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd/+bug/367776) for description what happened.
Summary: whatever I try to set to one output trough xrandr is set to second output too, the only thing which works correctly is switching one of the outputs off, any other change is "cloned" on the unwanted output as well.

---

### Post by ped on 2009-10-27
I'm trying it with Kubuntu 9.10 now just ahead of release.
Here is the report:

1) System settings -> Display = epic fail as before, it will also reset you back to cloned view once you switch to dual head.

2) The suggested "xrandr --output DVI-0 --right-of VGA-0 --auto" leads to:
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x1024)
this still holds true.

3) after adding:
```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		Virtual		2560 1024
	EndSubSection
```
to xorg.conf into Section "Screen", the suggested xrandr *[COLOR="Green"]**[SIZE="3"]WORKS[/SIZE]**[/COLOR]*.
(after restarting X of course and while trying to, I figured out the Ctrl+Alt+Backspace doesn't work anymore in 9.10, even with DontZap=False in xorg.conf. **HELP?**)

**After restart I'm back to cloned view.** :( Any ideas what's the most proper and cleanest way to make this automatic after restart? I don't want to run xrandr every time by hand. Thank you for any help.

---

### Post by Rrogers on 2009-10-28
I have dual moniter working on my system: HP Pavillion Ubuntu 9.04 X86_64 X1300/X1550 series.
I gave up on the xrandr (it caused reboots and other problems).  I can supply my simple (I'm lazy) xorg.conf that works; and the Xorg.0.log if you want.  
The only remaining problem is in firefox a undefined background and some icons have bars; toolmarks or some such.  It doesn't occur on the other apps; except during booting the console is trashed.
Oh yeah, I had to use a RGB adaptor (HDMI->RGB) for one of the outputs.  The X1300 would never register the hdmi stuff.

Ray

---

