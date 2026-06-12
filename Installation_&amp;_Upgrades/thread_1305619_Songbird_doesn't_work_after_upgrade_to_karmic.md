---
title: "Songbird doesn't work after upgrade to karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by raccoonone on 2009-10-30
After upgrading to Karmic, Songbird no longer works for me. I just get a ton of error messages when I try to start it. Anyone know what's wrong?
```

(songbird-bin:4595): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstasfmux.so': /usr/lib64/gstreamer-0.10/libgstasfmux.so: undefined symbol: gst_tag_list_add_value

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:4595): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

---

### Post by scottiw2000 on 2009-10-30
I found a workaround at [http://getsatisfaction.com/songbird/topics/songbird_fails_to_start_on_fedora_11_with_undefined_symbol_in_libgstdeinterlace_so](http://getsatisfaction.com/songbird/topics/songbird_fails_to_start_on_fedora_11_with_undefined_symbol_in_libgstdeinterlace_so) that worked for me.

I can run it if I launch songbird from a terminal using the commands:

export LD_BIND_NOW=1
songbird

Now, I have no idea *why* this works or what it does. I also get a crash warning, even though Songbird does start up. But at least I can listen to my music again!

That thread also suggests that after removing the gstreamer-python package you can run Songbird just fine again without the terminal command above. I haven't tried it yet, though.

---

### Post by raccoonone on 2009-10-30
Thanks! that export fixed it for me. Hopefully this is fixed for Songbird 1.4

---

### Post by tlu on 2009-10-31
I had installed Karmic (64 bit) anew and Songird doesn't work for me, either. Both v. 1.2 from getdeb.net and v. 1.5 from the Songbird ppa start but I simply can't hear any sound - in contrast to Amarok which works flawlessly. I hadn't had problems with Songbird under Jaunty.

After applying the solutiom mentioned by scottiw2000 Songbird starts but stalls immediately.

Something has changed in Karmic but not for the better ...:(

---

### Post by jabapyth on 2009-11-04
uninstalling gstreamer-plugins-bad fixed it for me

---

### Post by tlu on 2009-11-04
Songbird works now as expected. Here's what I did:

I had installed Rhythmbox but it couldn't play mp3s, either, but, thankfully, complained that a gstreamer plugin was missing.

So I tried gstreamer0.10-fluendo-mp3 and gstreamer0.10-plugins-ugly. Success: Both Rhythmbox and Songbird worked!

At least, so I thought. But after a reboot Songbird was silent again. Now I deinstalled all gstreamer packages with the exception of libpulse0 and libpulse-mainloop-glib0. The sound was back!

This solution has survived several reboots, so I think that's the solution I was looking for.

---

### Post by mcmanus@ducksong.com on 2009-11-05
fwiw: sudo apt-get remove python-gst0.10 fixed this for me on 9.10

---

### Post by philton on 2009-11-07
SIDe nOte: I'm hAving A HArdWAre iSsUe with mY keYBoaRd AND iT RANdomly SHIfts sO... i"m ReAlly SOrry fOR tHAT but iTS goTTeN To tEdIoUS to StOp anD backspace untIL It Doesn"t shiFT. sorry it LoOKS lIKe ii"m on aim in 7th grade....

when i upgraded tO Karmic sonGBIrd And A FeW OtHER noN-official buIlDS sImpLy dIsappeAReD fROm tHE sYStem... or atLeasT from the aplIcatioNs lIST, i'm not qUITe SURe how To atTEmpt tO lAUnch soNgbird from ThE teRminal, besides tErminAl work bLowS wItH This keYBoard PROblEm.... 

attempted tO rEinSTall via getDeb.neT And got thiS:>  apturl-gtk crashed with AttributeError in parse_pkg()


then ATTEmptEd To DOWNloAD tHE offIciaL linux buILd From sonGbiRD"s wEBSiTE but don't REaLLy undErsTand hOw tHat woRKs,

anY tHOughTs? 

p.s. i"m A sUpER uBuntu neWb.... but I got A laPTOp With visTA pREinStalled and couldN't hANdLE even dUal BoOTinG. 

thanKS

---

### Post by kubug on 2009-11-08
> **mcmanus@ducksong.com said:**
> fwiw: sudo apt-get remove python-gst0.10 fixed this for me on 9.10

Hmmm... that just uninstalled Rhythmbox and Totem for me. I did that and reinstalled it all... didn't fix it for me.

---

### Post by LuisGMarine on 2009-11-08
Please get the tar.gz from this website:

[http://www.getsongbird.com/]("http://www.getsongbird.com/")

Then follow the link in my signature to install songbird on Ubuntu.  Hope this helps!

---

### Post by kubug on 2009-11-08
Hmmm... I might have a different issue. I only get the "*Could not initialize GStreamer: Error re-scanning registry , child terminated by signal*" message.

My software-center does the same thing, as does totem and rhythmbox. Not sure if this related.

---

### Post by Endolith on 2009-11-15
I'm still using Jaunty on both computers, but I get this error on one and not the other.  Weird.  1.1.4 I think was what was working on this one, but when I upgrade to 1.2.0 it stopped working.  1.2.0 on the other computer works fine.

---

### Post by raccoonone on 2009-11-16
Have you tried the newest package from getdeb.net? That fixed all my problems

---

### Post by Endolith on 2009-11-16
The newest package from the website, yes.  Do you mean from the new repository?  I'm still using Jaunty.

---

### Post by taylorg273 on 2009-11-28
Here's another option that will get Songbird working again. I chose to move the libgst* files to another location for safe keeping rather than delete them.

[http://technology-included.co.cc/post/238315849/fix-songbird-on-ubuntu-9-10-karmic](http://technology-included.co.cc/post/238315849/fix-songbird-on-ubuntu-9-10-karmic)

---

### Post by xbrae.wrightx on 2009-12-08
Adding songbird from the ppa worked for me.

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

---

### Post by tlu on 2009-12-10
> **xbrae.wrightx said:**
> Adding songbird from the ppa worked for me.

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

Same here after applying the steps in post #6.

---

### Post by Endolith on 2009-12-10
The version from getdeb is older, but more add-ons are compatible with it.

---

