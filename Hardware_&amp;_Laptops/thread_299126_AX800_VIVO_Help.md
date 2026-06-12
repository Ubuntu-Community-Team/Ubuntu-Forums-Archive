---
title: "AX800 VIVO Help"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by zackr on 2006-11-13
I'm trying to get VideoLAN player to use the VIVO connector on the Asus AX800. I've been using Windows up until recently, so I'm afraid I'm a bit of a noob when it comes to this kind of thing, though I have got the same thing working in Windows VLC.

Anyhow, the Windows VLC just reads in the sound card line in and video card input/output stream fine. However, in Ubuntu Dapper, it shows /dev/video as the default video stream. How do I go about making this work short of using AVView (tried compiling this but it kept dying during make due to insufficient dependencies which after a while I couldn't satisfy)?

Any help would be much appreciated as I'm a little unsure how to test if the stream is actually there, and if so, how to create any need symlinks. Thank you!

---

### Post by zackr on 2006-11-13
Please, somebody let me know how to get it working! Any help would be much appreciated. I don't mind getting AVView going, but at the moment the dependencies just aren't there. The make output is below, maybe you can tell me what's wrong?

make  all-am
make[1]: Entering directory `/home/casey/avview-0.80.7'
gcc  -g -O2   -o avview_shell -L/usr/lib -ltcl8.4 -L/usr/lib -ltk8.4 -lX11 avview_shell-xv.o avview_shell-frequencies.o avview_shell-xmisc.o avview_shell-string_cache.o avview_shell-v4l.o avview_shell-formats.o avview_shell-ffmpeg.o avview_shell-alsa.o avview_shell-packet_stream.o avview_shell-linux.o avview_shell-main.o avview_shell-vbi.o avview_shell-lirc.o -lSM -lICE    -lXinerama -lXext -lX11 -lzvbi -lpthread -lm -lz -ldl 
avview_shell-xv.o: In function `xv_numadaptors':
/home/casey/avview-0.80.7/xv.c:64: undefined reference to `XvQueryAdaptors'
/home/casey/avview-0.80.7/xv.c:68: undefined reference to `XvFreeAdaptorInfo'
avview_shell-xv.o: In function `xv_adaptor_name':
/home/casey/avview-0.80.7/xv.c:105: undefined reference to `XvQueryAdaptors'
/home/casey/avview-0.80.7/xv.c:108: undefined reference to `XvFreeAdaptorInfo'
/home/casey/avview-0.80.7/xv.c:115: undefined reference to `XvFreeAdaptorInfo'
avview_shell-xv.o: In function `xv_adaptor_type':
/home/casey/avview-0.80.7/xv.c:153: undefined reference to `XvQueryAdaptors'
/home/casey/avview-0.80.7/xv.c:156: undefined reference to `XvFreeAdaptorInfo'
/home/casey/avview-0.80.7/xv.c:172: undefined reference to `XvFreeAdaptorInfo'
avview_shell-xv.o: In function `xv_adaptor_ports':
/home/casey/avview-0.80.7/xv.c:211: undefined reference to `XvQueryAdaptors'
/home/casey/avview-0.80.7/xv.c:214: undefined reference to `XvFreeAdaptorInfo'
/home/casey/avview-0.80.7/xv.c:225: undefined reference to `XvFreeAdaptorInfo'
avview_shell-xv.o: In function `xv_num_port_encodings':
/home/casey/avview-0.80.7/xv.c:268: undefined reference to `XvQueryEncodings'
/home/casey/avview-0.80.7/xv.c:272: undefined reference to `XvFreeEncodingInfo'
avview_shell-xv.o: In function `xv_port_encodings':
/home/casey/avview-0.80.7/xv.c:317: undefined reference to `XvQueryEncodings'
/home/casey/avview-0.80.7/xv.c:326: undefined reference to `XvFreeEncodingInfo'
avview_shell-xv.o: In function `xv_port_encoding_name':
/home/casey/avview-0.80.7/xv.c:371: undefined reference to `XvQueryEncodings'
/home/casey/avview-0.80.7/xv.c:374: undefined reference to `XvFreeEncodingInfo'
/home/casey/avview-0.80.7/xv.c:381: undefined reference to `XvFreeEncodingInfo'
avview_shell-xv.o: In function `xv_port_encoding_id':
/home/casey/avview-0.80.7/xv.c:426: undefined reference to `XvQueryEncodings'
/home/casey/avview-0.80.7/xv.c:429: undefined reference to `XvFreeEncodingInfo'
/home/casey/avview-0.80.7/xv.c:437: undefined reference to `XvFreeEncodingInfo'
avview_shell-xv.o: In function `xv_port_encoding_size':
/home/casey/avview-0.80.7/xv.c:483: undefined reference to `XvQueryEncodings'
/home/casey/avview-0.80.7/xv.c:486: undefined reference to `XvFreeEncodingInfo'
/home/casey/avview-0.80.7/xv.c:498: undefined reference to `XvFreeEncodingInfo'
avview_shell-xv.o: In function `xv_num_port_attributes':
/home/casey/avview-0.80.7/xv.c:542: undefined reference to `XvQueryPortAttributes'
avview_shell-xv.o: In function `xv_port_attribute_name':
/home/casey/avview-0.80.7/xv.c:591: undefined reference to `XvQueryPortAttributes'
avview_shell-xv.o: In function `xv_port_attribute_type':
/home/casey/avview-0.80.7/xv.c:647: undefined reference to `XvQueryPortAttributes'
avview_shell-xv.o: In function `xv_port_attribute_range':
/home/casey/avview-0.80.7/xv.c:711: undefined reference to `XvQueryPortAttributes'
avview_shell-xv.o: In function `xv_putvideo':
/home/casey/avview-0.80.7/xv.c:782: undefined reference to `XvPutVideo'
avview_shell-xv.o: In function `xv_stopvideo':
/home/casey/avview-0.80.7/xv.c:818: undefined reference to `XvStopVideo'
avview_shell-xv.o: In function `xv_grabport':
/home/casey/avview-0.80.7/xv.c:854: undefined reference to `XvGrabPort'
avview_shell-xv.o: In function `xv_ungrabport':
/home/casey/avview-0.80.7/xv.c:894: undefined reference to `XvUngrabPort'
avview_shell-xv.o: In function `xv_getportattribute':
/home/casey/avview-0.80.7/xv.c:936: undefined reference to `XvGetPortAttribute'
avview_shell-xv.o: In function `xv_setportattribute':
/home/casey/avview-0.80.7/xv.c:977: undefined reference to `XvSetPortAttribute'
collect2: ld returned 1 exit status
make[1]: *** [avview_shell] Error 1
make[1]: Leaving directory `/home/casey/avview-0.80.7'
make: *** [all] Error 2

---

