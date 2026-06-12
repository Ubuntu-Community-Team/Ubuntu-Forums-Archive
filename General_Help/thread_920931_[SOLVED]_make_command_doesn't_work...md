---
title: "[SOLVED] make command doesn't work.."
date: 2008-09-15
forum: General Help
---

### Post by Red.Rabbit on 2008-09-15
Here's an example of what happens when I try to use the make command when trying to install Gqcam:
```

redrabbit@Xeno:~/gqcam-0.9$ make
gcc `gtk-config --cflags` -DVERSION=\"0.9\" -c gqcam.c
/bin/sh: gtk-config: not found
gqcam.c:32:21: error: gtk/gtk.h: No such file or directory
gqcam.c:36:17: error: png.h: No such file or directory
In file included from gqcam.c:37:
gqcam.h:3: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:20: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:30: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:43: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:54: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:74: error: expected specifier-qualifier-list before ‘png_byte’
gqcam.h:89: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:113: error: expected specifier-qualifier-list before ‘GtkWidget’
gqcam.h:151: error: expected specifier-qualifier-list before ‘guint’
gqcam.h:182: error: expected ‘)’ before ‘*’ token
In file included from gqcam.c:38:
frontend.h:3: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘configure_event’
frontend.h:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘expose_event’
frontend.h:5: error: expected ‘)’ before ‘*’ token
frontend.h:7: error: expected ‘)’ before ‘*’ token
frontend.h:8: error: expected ‘)’ before ‘*’ token
frontend.h:9: error: expected ‘)’ before ‘*’ token
frontend.h:10: error: expected ‘)’ before ‘*’ token
frontend.h:11: error: expected ‘)’ before ‘*’ token
frontend.h:12: error: expected ‘)’ before ‘*’ token
frontend.h:13: error: expected ‘)’ before ‘*’ token
frontend.h:14: error: expected ‘)’ before ‘*’ token
frontend.h:15: error: expected ‘)’ before ‘*’ token
frontend.h:16: error: expected ‘)’ before ‘*’ token
frontend.h:20: error: expected ‘)’ before ‘*’ token
frontend.h:21: error: expected ‘)’ before ‘*’ token
In file included from gqcam.c:39:
save.h:49: error: expected ‘)’ before ‘*’ token
save.h:50: error: expected ‘)’ before ‘*’ token
gqcam.c: In function ‘init_cam’:
gqcam.c:48: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:49: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:51: error: ‘struct Camera’ has no member named ‘pixmap’
gqcam.c:58: error: ‘struct Camera’ has no member named ‘devname’
gqcam.c:62: error: ‘struct Camera’ has no member named ‘currentsavepage’
gqcam.c:65: error: ‘struct Camera’ has no member named ‘timer_struct’
gqcam.c:66: error: ‘struct Camera’ has no member named ‘timer_struct’
gqcam.c:68: error: ‘struct Camera’ has no member named ‘save_struct’
gqcam.c:69: error: ‘struct Camera’ has no member named ‘pref_mutex’
gqcam.c:70: error: ‘struct Camera’ has no member named ‘freeze_mutex’
gqcam.c:71: error: ‘struct Camera’ has no member named ‘iscam_mutex’
gqcam.c: In function ‘set_cam_info’:
gqcam.c:82: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:85: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c: In function ‘get_cam_info’:
gqcam.c:95: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:96: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:97: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:105: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:106: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:108: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:110: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:110: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:110: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:110: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:111: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:111: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:111: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:111: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:115: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:115: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:115: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:115: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:116: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:116: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:116: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:116: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c: In function ‘print_cam_info’:
gqcam.c:123: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:124: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:125: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:128: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:131: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:134: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:137: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:140: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:143: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:146: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:149: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:152: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:156: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:157: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:158: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:159: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:160: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:161: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:165: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:166: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:167: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:168: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:169: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:170: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:178: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:178: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:179: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:179: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:180: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:180: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:181: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:181: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:182: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:182: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:183: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:184: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c: In function ‘open_cam’:
gqcam.c:192: error: ‘struct Camera’ has no member named ‘devname’
gqcam.c:199: error: ‘struct Camera’ has no member named ‘iscam_mutex’
gqcam.c: In function ‘close_cam’:
gqcam.c:205: error: ‘struct Camera’ has no member named ‘iscam_mutex’
gqcam.c: In function ‘display’:
gqcam.c:215: error: ‘GdkDrawable’ undeclared (first use in this function)
gqcam.c:215: error: (Each undeclared identifier is reported only once
gqcam.c:215: error: for each function it appears in.)
gqcam.c:215: error: ‘drawable’ undeclared (first use in this function)
gqcam.c:217: error: ‘GdkRectangle’ undeclared (first use in this function)
gqcam.c:217: error: expected ‘;’ before ‘update_rec’
gqcam.c:223: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:224: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:224: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:225: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:229: error: ‘update_rec’ undeclared (first use in this function)
gqcam.c:231: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:232: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:234: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:234: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:235: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:235: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:237: error: ‘struct Camera’ has no member named ‘drawing_area’
gqcam.c:247: error: ‘struct Camera’ has no member named ‘pixmap’
gqcam.c:247: error: ‘struct Camera’ has no member named ‘drawing_area’
gqcam.c:247: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:247: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:247: error: ‘GDK_RGB_DITHER_NORMAL’ undeclared (first use in this function)
gqcam.c:247: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:247: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:249: error: ‘struct Camera’ has no member named ‘pixmap’
gqcam.c:249: error: ‘struct Camera’ has no member named ‘drawing_area’
gqcam.c:249: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:249: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:249: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:249: error: ‘struct Camera’ has no member named ‘vid_win’
gqcam.c:253: error: ‘struct Camera’ has no member named ‘statusbar’
gqcam.c:254: error: ‘struct Camera’ has no member named ‘fps_avg’
gqcam.c:254: error: ‘struct Camera’ has no member named ‘fps_current’
gqcam.c:255: error: ‘struct Camera’ has no member named ‘statusbar’
gqcam.c:256: error: ‘struct Camera’ has no member named ‘drawing_area’
gqcam.c: In function ‘grab_image’:
gqcam.c:269: error: ‘GdkRectangle’ undeclared (first use in this function)
gqcam.c:269: error: expected ‘;’ before ‘update_rec’
gqcam.c:270: error: ‘GdkEventExpose’ undeclared (first use in this function)
gqcam.c:270: error: ‘event’ undeclared (first use in this function)
gqcam.c:274: error: ‘update_rec’ undeclared (first use in this function)
gqcam.c:276: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:277: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:281: error: ‘struct Camera’ has no member named ‘freeze_mutex’
gqcam.c:281: error: ‘struct Camera’ has no member named ‘iscam_mutex’
gqcam.c:283: error: ‘struct Camera’ has no member named ‘pref_mutex’
gqcam.c:291: error: ‘struct Camera’ has no member named ‘pref_mutex’
gqcam.c:294: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:294: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:294: error: ‘struct Camera’ has no member named ‘vid_caps’
gqcam.c:298: error: ‘struct Camera’ has no member named ‘freeze_mutex’
gqcam.c:299: error: ‘struct Camera’ has no member named ‘iscam_mutex’
gqcam.c:304: error: ‘struct Camera’ has no member named ‘timer_struct’
gqcam.c:319: error: ‘struct Camera’ has no member named ‘timer_struct’
gqcam.c:321: error: ‘struct Camera’ has no member named ‘timer_struct’
gqcam.c: At top level:
gqcam.c:328: error: expected ‘)’ before ‘*’ token
gqcam.c: In function ‘increment_second_counter’:
gqcam.c:359: error: ‘struct Camera’ has no member named ‘fps_avg’
gqcam.c:360: error: ‘struct Camera’ has no member named ‘fps_current’
gqcam.c: In function ‘main’:
gqcam.c:370: error: ‘guint’ undeclared (first use in this function)
gqcam.c:370: error: expected ‘;’ before ‘timeoutid’
gqcam.c:428: error: ‘struct Camera’ has no member named ‘devname’
gqcam.c:475: error: ‘struct Camera’ has no member named ‘fps_avg’
gqcam.c:476: error: ‘struct Camera’ has no member named ‘fps_current’
gqcam.c:497: error: ‘struct Camera’ has no member named ‘timeoutid’
gqcam.c:497: error: ‘GtkFunction’ undeclared (first use in this function)
gqcam.c:497: error: expected ‘)’ before ‘next_frame’
gqcam.c:499: error: ‘timeoutid’ undeclared (first use in this function)
gqcam.c:499: error: expected ‘)’ before ‘increment_second_counter’
gqcam.c:510: error: ‘struct Camera’ has no member named ‘freeze_mutex’
gqcam.c:517: error: ‘struct Camera’ has no member named ‘freeze_mutex’
gqcam.c: In function ‘dump_pict’:
gqcam.c:548: error: ‘struct Camera’ has no member named ‘savefile’
gqcam.c:549: error: ‘struct Camera’ has no member named ‘savefileclean’
gqcam.c:565: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:566: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:567: error: ‘struct Camera’ has no member named ‘vid_pic’
gqcam.c:572: error: ‘struct Camera’ has no member named ‘pic’
gqcam.c:572: error: ‘struct Camera’ has no member named ‘picbuff’
gqcam.c:577: error: ‘struct Camera’ has no member named ‘save_struct’
gqcam.c:578: error: ‘struct Camera’ has no member named ‘save_struct’
gqcam.c:579: error: ‘struct Camera’ has no member named ‘save_struct’
gqcam.c:583: error: ‘struct Camera’ has no member named ‘save_struct’
gqcam.c:583: error: ‘PNG_INTERLACE_NONE’ undeclared (first use in this function)
gqcam.c:584: error: ‘struct Camera’ has no member named ‘save_struct’
gqcam.c:588: error: ‘struct Camera’ has no member named ‘save_struct’
make: *** [gqcam.o] Error 1
redrabbit@Xeno:~/gqcam-0.9$ 

```

Any ideas? This isn't the only thing make doesn't work with either.

---

### Post by Whiffle on 2008-09-15
Have you installed build-essential?


sudo apt-get install build-essential

---

### Post by Dougie187 on 2008-09-15
Yeah, it looks to me like your missing some headers. try build-essential and let us know how it works.

---

### Post by Red.Rabbit on 2008-09-15
Yeah, I already have build-essential installed.

---

### Post by Whiffle on 2008-09-15
Looks like you're missing the program "gtk-config," whatever that is.  I'm looking for it right now...

---

### Post by Whiffle on 2008-09-15
Got it...

sudo apt-get install libgtk1.2-dev


and you should be good to go.

---

### Post by Red.Rabbit on 2008-09-15
Well, I've made a little progress thanks to Whiffle. But now I'm getting this:

```
redrabbit@Xeno:~/gqcam-0.9$ make
gcc `gtk-config --cflags` -DVERSION=\"0.9\" -c gqcam.c
gqcam.c:36:17: error: png.h: No such file or directory
In file included from gqcam.c:37:
gqcam.h:74: error: expected specifier-qualifier-list before ‘png_byte’
gqcam.c: In function ‘dump_pict’:
gqcam.c:583: error: ‘struct Save_Struct’ has no member named ‘interlace’
gqcam.c:583: error: ‘PNG_INTERLACE_NONE’ undeclared (first use in this function)
gqcam.c:583: error: (Each undeclared identifier is reported only once
gqcam.c:583: error: for each function it appears in.)
gqcam.c:584: error: ‘struct Save_Struct’ has no member named ‘compression’
make: *** [gqcam.o] Error 1
redrabbit@Xeno:~/gqcam-0.9$ 

```

---

### Post by Whiffle on 2008-09-15
Hmm, I'm guessing that you're missing libpng12-dev.  I got it compile fine on mine, and I have that lib.

---

### Post by Red.Rabbit on 2008-09-15
I installed libpng12-dev and now I get this:
```
redrabbit@Xeno:~/gqcam-0.9$ make
gcc `gtk-config --cflags` -DVERSION=\"0.9\" -c save.c
save.c:15:21: error: jpeglib.h: No such file or directory
save.c: In function &#8216;save_ok&#8217;:
save.c:59: error: storage size of &#8216;cinfo&#8217; isn&#8217;t known
save.c:60: error: storage size of &#8216;jerr&#8217; isn&#8217;t known
save.c:61: error: &#8216;JSAMPROW&#8217; undeclared (first use in this function)
save.c:61: error: (Each undeclared identifier is reported only once
save.c:61: error: for each function it appears in.)
save.c:61: error: expected &#8216;;&#8217; before &#8216;row_pointer&#8217;
save.c: In function &#8216;jpeg_save&#8217;:
save.c:391: error: storage size of &#8216;cinfo&#8217; isn&#8217;t known
save.c:392: error: storage size of &#8216;jerr&#8217; isn&#8217;t known
save.c:393: error: &#8216;JSAMPROW&#8217; undeclared (first use in this function)
save.c:393: error: expected &#8216;;&#8217; before &#8216;row_pointer&#8217;
save.c:415: error: &#8216;JCS_GRAYSCALE&#8217; undeclared (first use in this function)
save.c:419: error: &#8216;JCS_RGB&#8217; undeclared (first use in this function)
save.c:432: error: &#8216;row_pointer&#8217; undeclared (first use in this function)
make: *** [save.o] Error 1
redrabbit@Xeno:~/gqcam-0.9$
```

Least it seems I'm getting somewhere, lol.

---

### Post by Whiffle on 2008-09-15
This one:

libjpeg62-dev


Yeah all it takes on this is experience really.  What I do is look down the lines till i see the first error, and see what its about.  "jpeglib.h", no such file or directory.  Go over to packages.ubuntu.com, search for jpeglib.h, and it'll bring up libjpeg62-dev.

---

### Post by Red.Rabbit on 2008-09-15
That got it working, thanks a lot Whiffle. And thanks for your advice too, that'll probably help out a lot in the future. :)

---

