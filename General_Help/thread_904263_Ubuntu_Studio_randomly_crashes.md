---
title: "Ubuntu Studio randomly crashes"
date: 2008-08-29
forum: General Help
---

### Post by GoldDragon on 2008-08-29
I am using the latest version of Ubuntu Studio. It has started randomly crashing. When it happens, the screen goes black and then it starts loading, but hangs at Timidity - Alsa config ( can't remember it exact ).
I am running intel machine with an ATI graphics card. I am using the restricted driver, and have been running compiz.
I disabled desktop themes to see if it would make a difference. When I switched it to none, my desktop crashed. 
I've also tried doing an new install of restricted extras.
I have also noticed that I am having trouble with viewing flash related sites. For example, youtube videos often show as a grey box ( even with desktop themes deactivated ). Don't know if this ties into the problems I'm having.  
I really like Ubuntu Studio, but i need it to be stable, as I'm using it for work purposes. 

Any ideas for fixing this?

Thanks so much

---

### Post by Crafty Kisses on 2008-08-29
Have you checked your error logs?

---

### Post by GoldDragon on 2008-08-29
Checked my syslog, I found this error```
 ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
```

and this 

```
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
```

Should I switch to the normal ATI fglrx drivers?

here's more code

```
GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
GLib-GObject-WARNING: invalid (NULL) pointer instance 
GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed
GLib-GObject-WARNING: invalid (NULL) pointer instance
GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
```


```
PM: Resume from disk failed.
```

---

### Post by GoldDragon on 2008-08-29
O.k. I needed to upload a video to Revver. I tried for two days, using Ubuntu Studio; the videos never uploaded right.
Today, I decided to use Ubuntu livecd, retrieve the video from Ubuntu Studio and upload it to Revver that way. It uploaded perfectly. 
So, this seems to be a problem with Ubuntu Studio and flash?

---

### Post by markbuntu on 2008-08-29
You need to install

libflashsupport

if you are using flash 9.

The fglrx driver is the "normal fglrx" but if you want the newest one which has a lot of improvements and bug fixes you can follow the directions here. Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you want to make adjustments to the driver for better performance you can try this guide here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

When you installed Ubuntu Studio did you get any error messages?

There is a bug in the version of timidity that UbuntuStudio installs lately that has caused problems for some people. You should remove it.

The random crashes are more likely related to the flash problem than the video driver. Which ATI card are you using?

---

### Post by GoldDragon on 2008-08-29
Thanks for the reply.

I didn't get any error messages when I installed Ubuntu Studio. Everything seemed great at first.
I'll remove timidity to be safe.

I'm using a Radeon HD 3450 card.

---

