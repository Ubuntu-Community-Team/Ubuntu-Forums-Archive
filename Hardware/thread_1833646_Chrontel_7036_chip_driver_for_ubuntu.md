---
title: "Chrontel 7036 chip driver for ubuntu"
date: 2011-08-26
forum: Hardware
---

### Post by robertnd on 2011-08-26
Hi,
I have a tablet pc with a ch7036 chip ([http://www.chrontel.com/products/7036.htm](http://www.chrontel.com/products/7036.htm) )
I'm trying to compile its driver to get hdmi output to work properly.
A driver is avaible here : git clone [http://git.chromium.org/chromiumos/third_party/chrontel.git](http://git.chromium.org/chromiumos/third_party/chrontel.git)
But I can't compile it (error message at the end of this post).
Has anyone got the hdmi output (of the chrontel ch0736 chip) to work under ubuntu ?

Error message : 
cc -Wall -Werror  -c ch7036_access.c -o ch7036_access.o
In file included from ch7036_access.c:11:0:
/usr/include/linux/i2c-dev.h:38:8: error: redefinition of ‘struct i2c_msg’
/usr/include/linux/i2c.h:67:8: note: originally defined here
/usr/include/linux/i2c-dev.h:90:7: error: redefinition of ‘union i2c_smbus_data’
/usr/include/linux/i2c.h:125:7: note: originally defined here    


Solved by removing the libi2c-dev. It compiles & works

---

### Post by jerrrys on 2011-08-28
welcome to the forum

and nice fix,  there's a lot of files that will regenerate and fix a problem.

 but you do need a little work on marking your post as solved :)

---

### Post by robertnd on 2011-08-30
Done ;) . Thanks for telling me.

---

### Post by cage007 on 2012-03-06
Help please,

I have a foxconn nt-535 with a *Chrontel* CH7036 chip. I would like to use xbmc through ubuntu on it. I have problems with the resolution of the screen. Can somebody help me to find a driver for the chrontel chipset?

I'm not a linux expert at all...

Thx

---

### Post by Djonmayer on 2012-09-03
Hi.

I compiled this driver. How I can install it?

Regards 
Djon

---

### Post by holzi on 2013-05-01
I compiled and installed the ChromiumOS- and the WeTab-driver for the Chrontel 7036 but I still don´t get HDMI-connector to work. If I start the hdmi-daemons nothing happens. They just run but nothing more.

---

### Post by Pavel Bludov on 2013-08-08
> **holzi said:**
>  They just run but nothing more.

It works for me with kernel 3.5. After 3.6 kernel all i801 stuff is broken.

---

### Post by daniel-holz91 on 2014-01-09
Probably a bit late but I got the ch7036 to work on Ubuntu 13.10:

[http://lackofalucidmind-en.blogspot.de/2014/01/hdmi-output.html](http://lackofalucidmind-en.blogspot.de/2014/01/hdmi-output.html)

---

### Post by waterhead on 2014-01-09
Thanks! It's never too late!

I was trying to use a patch that I got from the WeTab Forums. That patch would always fail, and it is small compaired to the one you linked to:

[http://www.wetab-community.com/index.php?/topic/12074-ubuntu-hdmi-ausgang/page-3#entry299313](http://www.wetab-community.com/index.php?/topic/12074-ubuntu-hdmi-ausgang/page-3#entry299313)

I will give this a try on my 14.04 install.

Thanks again!

---

### Post by daniel-holz91 on 2014-01-10
Yeah, I had my problems with this patch too so I tried to apply it manually with Gedit and it worked. After that I created my own patch-file with the diff command which for some reasons became much bigger. :D I only tested it on 13.10. I hope it works on 14.04 too.  I will add more guides to my blog in the future.   And sorry if my english sucks. ^^

---

### Post by waterhead on 2014-01-10
> **daniel-holz91 said:**
> Yeah, I had my problems with this patch too so I tried to apply it manually with Gedit and it worked.
I never thought of doing that. I think I may give that a try.

> **daniel-holz91 said:**
> And sorry if my english sucks. ^^

It's better than my deutsch!. My Great-Grandfather was from Deutschland (my name is Schmidt). I didn't go to a church, I went to a [Kirche](https://maps.google.com/maps?q=2605+S+Kinnickinnic+Ave,+Milwaukee,+WI&hl=en&ll=42.997734,-87.899895&spn=0.006929,0.016512&sll=42.997615,-87.899802&layer=c&cbp=13,263.11,,0,-18.5&cbll=42.997532,-87.899653&hnear=2605+S+Kinnickinnic+Ave,+Milwaukee,+Wisconsin+53207&t=m&z=17&panoid=3wqxFh_B0zQRRO7r9g29Sw). But, I only know a few swear words in deutsch.

Anyway, if you have any trouble installing the CrystalHD driver, I can help with that. There is a patch for that driver too.

---

### Post by daniel-holz91 on 2014-01-11
> **waterhead said:**
> I never thought of doing that. I think I may give that a try.  You can do that but the patch on my blog should do the same. If you save time you could try this compiled and patched driver.   [http://ubuntuone.com/05i4CLB81NmOy8CucxyZL5](http://ubuntuone.com/05i4CLB81NmOy8CucxyZL5)  > **waterhead said:**
> It's better than my deutsch!. My Great-Grandfather was from Deutschland (my name is Schmidt). I didn't go to a church, I went to a Kirche. But, I only know a few swear words in deutsch. Yeah Schmidt is very, very, very, very german. It's the german Smith. :D   > **waterhead said:**
> Anyway, if you have any trouble installing the CrystalHD driver, I can help with that. There is a patch for that driver too.Thanks but I only have the cheap version of the WeTab which lacks the CrystalHD. But I already found a way to play hd-videos without it.

---

### Post by waterhead on 2014-01-12
I wanted to get this to work on 13.10 before trying it on 14.04. I first tried manually adding the WeTab patch. But when I compiled it I got an error. So I then just applied the patch from daniel-holz91. I also had to make the ch7036_start file executable before it would work.

The picture is a bit fuzzy, but I didn't yet try to make any adjustments via the config file.

Next I'll try it on Ubuntu 14.04.

---

### Post by daniel-holz91 on 2014-01-12
Yeah for some reasons the daemon gets no EDID-information from the external screen and reduces its resolution to 480p. With the correct "-E" parameter it should display at least 1366x768. What I still not got working is to get it autostarting. fstab didn't work (boot time increased dramaticly, daemon didn't start) and starting it through lightDM caused a black screen.

---

### Post by waterhead on 2014-01-12
I've worked out most of the problems of the original patch provided by sven-ola on the WeTab Forums. The patch is formatted incorrectly, maybe by the forum software. Here is the patch that seems to work (saved as chrontel.patch):

```
diff --git a/Makefile b/Makefile
index 3a5936d..b7a8df3 100644
--- a/Makefile
+++ b/Makefile
@@ -20,11 +20,11 @@ all: $(MON) $(BUG)
     $(CC) $(CCFLAGS) $(INCLUDE_DIRS) -c $< -o $@

 $(MON): $(OBJECTS) $(MON).o
-    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $(LIB_DIRS) $^ $(LIBS) $(LDFLAGS) \
+    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $^ $(LIB_DIRS) $(LIBS) $(LDFLAGS) \
                 -o $@

 $(BUG): $(OBJECTS) $(BUG).o
-    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $(LIB_DIRS) $^ $(LIBS) $(LDFLAGS) \
+    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $^ $(LIB_DIRS) $(LIBS) $(LDFLAGS) \
                 -o $@

 clean:
diff --git a/ch7036_monitor.c b/ch7036_monitor.c
index 5cfcc2d..ecf2d90 100644
--- a/ch7036_monitor.c
+++ b/ch7036_monitor.c
@@ -762,6 +762,7 @@ int init_lcd_timing(struct timing_ch7036 *lcd_timing, int *width_fix,
   lcd_timing->vo = xmode->vSyncStart - xmode->height;
   lcd_timing->vw = xmode->vSyncEnd - xmode->vSyncStart;
   lcd_timing->scale = MK_SCALE(0, 0);
+  return 0;
 }

```
I place it in my home directory, and run all my terminal commands from there too:

```
git clone http://git.chromium.org/chromiumos/third_party/chrontel.git
```

```
cd chrontel
```

```
git checkout 697c6bd5237fa800c314153779624187a9c4e0e6
```

```
patch -p1 < ~/chrontel.patch
```

I do get this output, so I haven't actually tried to compile it yet.

```
$ patch -p1 < ~/chrontel.patch
patching file Makefile
Hunk #1 succeeded at 20 with fuzz 1.
patching file ch7036_monitor.c

```

I don't know what the 'fuzz 1' is, but most likely more formatting errors.

EDIT: I worked out the problem, and don't get patch errors any more. I updated the posted patch.

---

### Post by waterhead on 2014-01-12
I have been working on this patch on my desktop, with Fedora 20 installed. After patching the source, I could not build it without getting this error:

```
$ make
cc -Wall -Werror  -c ch7036_monitor.c -o ch7036_monitor.o
ch7036_monitor.c: In function &#8216;main&#8217;:
ch7036_monitor.c:1017:20: error: &#8216;width_fix&#8217; may be used uninitialized in this function [-Werror=maybe-uninitialized]
     init_lcd_timing(&lcd_timing, width_fix, xmode);
                    ^
cc1: all warnings being treated as errors
make: *** [ch7036_monitor.o] Error 1
```

 It was previously reported in this Google Group post:

[http://code.google.com/p/chromium/issues/detail?id=215604](http://code.google.com/p/chromium/issues/detail?id=215604)

And fixed with these two patches:

```
--- ch7036_monitor.c
+++ ch7036_monitor.c
@@ -737,7 +737,7 @@
   return 0;
 }
 
-int init_lcd_timing(struct timing_ch7036 *lcd_timing, int *width_fix,
+void init_lcd_timing(struct timing_ch7036 *lcd_timing, int *width_fix,
                     XRRModeInfo *xmode)
 {
   if ((xmode->width == 1366) && (xmode->height == 768)) {
@@ -785,7 +785,7 @@
   int probe_only = 0;
   int dummy_i2c = 0;
   int verbose = 0;
-  int *width_fix;
+  int *width_fix = NULL;
   unsigned char edid[256];
   unsigned char newedid[256];
   int use_new_edid = 0;
```

```
--- Makefile
+++ Makefile
@@ -20,11 +20,11 @@
     $(CC) $(CCFLAGS) $(INCLUDE_DIRS) -c $< -o $@
 
 $(MON): $(OBJECTS) $(MON).o
-    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $(LIB_DIRS) $^ $(LIBS) $(LDFLAGS) \
+    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $^ $(LDFLAGS) $(LIB_DIRS) $(LIBS) \
                 -o $@
 
 $(BUG): $(OBJECTS) $(BUG).o
-    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $(LIB_DIRS) $^ $(LIBS) $(LDFLAGS) \
+    $(CC) $(CCFLAGS) $(INCLUDE_DIRS) $^ $(LDFLAGS) $(LIB_DIRS) $(LIBS) \
                 -o $@
 
 clean:
```

I had to apply these two patches (I manually edited the files), and then I was able to compile it on Fedora 20 too. I am posting it here in case others also run into this problem.

---

### Post by daniel-holz91 on 2014-01-18
Today I got the recent version of the Chromium OS Ch7036 driver to work under Ubuntu. I just applied the patch from the WeTab-forum, swapped audio_utils.c and audio_utils.h against the ones from the old version and copied edid_utils.c and edid_utils.h from the old version into the chrontel folder of the recent version. For my suprise I could actually compile and use this patchwork-driver. I call it the Franken-Chrontel. :D

You can find my updated guide here: [http://lackofalucidmind-en.blogspot.de/2014/01/hdmi-output.html](http://lackofalucidmind-en.blogspot.de/2014/01/hdmi-output.html)

The only thing we need now is a package and a PPA. I was able to create the first one but it would only copy the files to the correct places. It wouldn't make the necessary changes to /etc/modules and without that the driver doesn't work.
I failed with the PPA because I have no idea how to convert this hole bunch of files into a source package.


To the new version:
There weren't many changes since the old version.

---

### Post by daniel-holz91 on 2014-02-01
Because there are still some problems caused by the missing Edid-detection of the chrontel driver I kept searching for other solutions and found this [https://build.merproject.org/package/files?package=chrontel&project=kde%3Adevel%3Aux](https://build.merproject.org/package/files?package=chrontel&project=kde%3Adevel%3Aux)

It seems like the Mer project has it's own fork of this driver which contains the files ediddata.cpp and ediddata.h. Maybe it works better but I get errors when I try to compile it.

Edit: Well I got it somewhat working but still no Edid detection and because this older driver has no fallback mode for this case it just doesn't do anything.

---

### Post by waterhead on 2014-02-01
I have Fedora installed on my Desktop PC. I downloaded the Mer .rpm file, and was able to install it without any errors. It has these files:

/etc/dbus-1/system.d/com.tiitoo.HDMI.conf
/etc/modprobe.d/chrontel_i2c.conf
/etc/udev/rules.d/10-kernel-chrontel.rules
/etc/xdg/autostart/tiitoo-hdmi.desktop
/lib/firmware/chrontel/fw7036.bin
/usr/bin/tiitoo-hdmi-daemon
/usr/bin/tiitoo-hdmi.sh

To run it, use this command:

tiitoo-hdmi.sh startup

I don't have Fedora installed on my tablet, but I may give it a try.

---

