---
title: "[SOLVED] need help with oss"
date: 2008-09-22
forum: General Help
---

### Post by DPod41 on 2008-09-22
Hey there I'm a complete nub and need some help with oss. A few years ago I tried using ubuntu but the drivers for my x fi sound card weren't supported so I went back to windows. But a few days ago I read that oss now supports my sound card. Anyway I followed the instructions here, [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) and I got my sound to work for the most part, but whenever I open up a small game or some other app I get no sound. Do I have to configure each program? Is there a special way to do that if there's no accessible options? Or is there a way to just tell the system..."Hey use oss!!:mad:" Anyway this is probably a dumb question but thanks for your time in advance.

---

### Post by jpkotta on 2008-09-22
You need to set each program to use OSS.  Many programs with sound output can use several different outputs.  If you're using OSS, keep in mind that only one application can output sound at a time.  The way around this (with out using newer sound outputs like ALSA) is to use a sound server like esd or arts.  Sound servers also require application support.

Most likely, the driver is using ALSA, and OSS is made available via ALSA's OSS emulation layer.  Most Linux sound drivers use ALSA.

---

### Post by DPod41 on 2008-09-23
Thanks for the reply. Umm..I'm not very sure, but I think the tutorial I followed got me to shut off ALSA because I needed OSS to get any sound at all. Or something.. Anyway, can someone point me in the right direction to configure OSS to work on all of my applications? Thanks again.

---

### Post by jpkotta on 2008-09-23
> **DPod41 said:**
> Thanks for the reply. Umm..I'm not very sure, but I think the tutorial I followed got me to shut off ALSA because I needed OSS to get any sound at all. Or something.. Anyway, can someone point me in the right direction to configure OSS to work on all of my applications? Thanks again.

Indeed.  I guess I should have checked that link more carefully.  Again, it's app-dependent.  It's a game, maybe it uses SDL?  Do you have SDL with OSS? If you know the command to run the game, post the output of:
```
ldd `which game-command`
```
The quotes are backticks, right below the ESC key.

---

### Post by DPod41 on 2008-09-24
Sorry for the late reply; I just spent 3 hours trying to get the back and forward buttons on my mouse to work on Nautilus. I typed in ```
ldd `which tmw`
```
like you said, and I got
```
	linux-vdso.so.1 =>  (0x00007fff057fe000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00007f78fd1f6000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00007f78fcf61000)
	libSDL_image-1.2.so.0 => /usr/lib/libSDL_image-1.2.so.0 (0x00007f78fcd45000)
	libSDL_mixer-1.2.so.0 => /usr/lib/libSDL_mixer-1.2.so.0 (0x00007f78fcac9000)
	libguichan_sdl.so.0 => /usr/lib/libguichan_sdl.so.0 (0x00007f78fc8ba000)
	libcurl-gnutls.so.4 => /usr/lib/libcurl-gnutls.so.4 (0x00007f78fc67d000)
	libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00007f78fc452000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00007f78fd576000)
	libSDL_net-1.2.so.0 => /usr/lib/libSDL_net-1.2.so.0 (0x00007f78fc24e000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f78fc029000)
	libphysfs-1.0.so.0 => /usr/lib/libphysfs-1.0.so.0 (0x00007f78fbf16000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f78fbcff000)
	libguichan.so.0 => /usr/lib/libguichan.so.0 (0x00007f78fbaac000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f78fb890000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f78fb585000)
	libm.so.6 => /lib/libm.so.6 (0x00007f78fb304000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f78fb0f6000)
	libc.so.6 => /lib/libc.so.6 (0x00007f78fad94000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f78fab90000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0x00007f78fa8b2000)
	libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0x00007f78fa644000)
	libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0x00007f78fa43c000)
	libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0x00007f78fa227000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x00007f78fa004000)
	libtiff.so.4 => /usr/lib/libtiff.so.4 (0x00007f78f9dab000)
	libidn.so.11 => /usr/lib/libidn.so.11 (0x00007f78f9b79000)
	libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0x00007f78f9934000)
	libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x00007f78f969d000)
	libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x00007f78f9479000)
	libcom_err.so.2 => /lib/libcom_err.so.2 (0x00007f78f9277000)
	libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0x00007f78f8ff3000)
	libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x00007f78f8dec000)
	libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x00007f78f8bea000)
	libresolv.so.2 => /lib/libresolv.so.2 (0x00007f78f89d4000)
	libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0x00007f78f7e1d000)
	libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0x00007f78f7d1c000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f78f7b0b000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f78f7808000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f78fd53d000)
	liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x00007f78f75fa000)
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00007f78f73e1000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x00007f78f71d1000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x00007f78f6f83000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f78f6d81000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f78f6b80000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f78f6965000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0x00007f78f6762000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f78f655d000)

```
That's one of the games I thought I'd download to test my sound on. It's called The Mana World. I read somewhere that there was a way to get ALSA instead of OSS to work with my sound card, but it said that if I never recompiled a kernel before I shouldn't do it. Recompile a kernel? That sounds scary. Thanks for the help so far.

---

### Post by DPod41 on 2008-09-24
Not sure how to  bump a thread..but I guess I'll just post a reply. If there's some special way please share.

---

### Post by jpkotta on 2008-09-25
Try installing libsdl1.2debian-oss.  It may complain about uninstalling other SDL libraries, which is OK.  

Threads are bumped when anyone replies to them.

If ALSA works with your sound card in a newer kernel, then when you update to Intrepid, this will all probably *just work*.  I wouldn't recommend updating yet.  Messing with the kernel can be ... messy.  It's not that hard, but it can be a pain until you get the hang of it.

---

### Post by DPod41 on 2008-09-25
Thanks it seems to be working now.

---

### Post by Yellow Pasque on 2008-09-28
Hi. Thanks for the feedback on the documentation. I'll add libsdl1.2debian-oss as a prerequisite because it seems to be a common tripping point.

I linked the OSS4 "configuring apps" wiki in the doc, but maybe it doesn't stand out enough? Anyway... here's that link in case you have other apps that need configured:
[http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)

> If you're using OSS, keep in mind that only one application can output sound at a time. The way around this (with out using newer sound outputs like ALSA) is to use a sound server like esd or arts. Sound servers also require application support.

Not quite.. OSS4 has something called "vmix" which allows multiple sounds at the same time. ALSA has "dmix", but it still doesn't do system sounds on GNOME (and ALSA isn't "newer" than OSS4.)

---

