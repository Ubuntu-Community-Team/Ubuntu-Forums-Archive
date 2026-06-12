---
title: "Old Intel Camera"
date: 2020-04-19
forum: Hardware
---

### Post by rsteinmetz70112 on 2020-04-19
I found an old Intel Camera and wanted to see if I could use it as a web cam. It has a USB Port. I've connected it to a Ubuntu 18.04 desktop and lsusb sees the device, but I don't see it anywhere else.
I also don't see software for it.
How can I check it out?

---

### Post by ajgreeny on 2020-04-19
So what does ***lsusb*** say it is?

It's not much use just saying us that it sees it without telling us all the details.

For software to see if it produces anything try cheese or guvcview; I prefer the latter.

---

### Post by Autodave on 2020-04-19
Install *cheese *and see if it works on there.  It is in the repositories if not already installed on your system.

---

### Post by rsteinmetz70112 on 2020-04-20
OK cheese was installed and it is the latest version. But I get this error:

```
Message: 10:01:29.471: cheese-application.vala:211: Error during camera setup: No device found
```

lsusb:

```
Bus 003 Device 002: ID 8086:0630 Intel Corp. Pocket PC Camera

```


I'm beginning to think the camera's broken. It has memory but I'm not seeing it anywhere. 
Maybe I'll try plugging it into a Windows machine and see what happens there.

---

### Post by Autodave on 2020-04-20
Or try another USB port.

---

### Post by rsteinmetz70112 on 2020-04-20
OK I tried another USB Port no difference.
I plugged it into a Windows computer. It was immediately recognized and I was able to download some pictures.
Apparently it's a driver issue.

```
#dmessage |less
[78498.337453] gspca_main: v2.14.0 registered
[78498.563994] gspca_main: spca500-2.14.0 probing 8086:0630
[78498.564319] usbcore: registered new interface driver spca500
[78526.257284] usbcore: registered new interface driver sunplus
```

looking at old archived messages it appears there was a driver as part of the spca5x project and it appears to be loaded.
Now if it would only talk to something.

Sort of success. This command worked and loaded vlc with an image from the camera.
```

vlc v4l2:///dev/video0
```

cheese is still showing no device I opene dconf-editor and fiddled with it but still no luck

---

### Post by mörgæs on 2020-04-22
> **ajgreeny said:**
> 
For software to see if it produces anything try cheese or guvcview; I prefer the latter.

As asked above, how does Guvcview work?

---

### Post by rsteinmetz70112 on 2020-04-22
> **mörgæs said:**
> As asked above, how does Guvcview work?

guvcview wasn't installed. I installed it but it does work.

cheese still does not find the camera

When I try to open it in a terminal window this is what I get:
```

$ cheese

(cheese:31317): dbind-WARNING **: 17:36:22.542: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(cheese:31317): Gtk-WARNING **: 17:36:23.702: Theme parsing error: cheese.css:7:35: The style property GtkScrollbar:min-slider-length is deprecated and shouldn't be used anymore. It will be removed in a future version
** Message: 17:36:23.900: cheese-application.vala:211: Error during camera setup: No device found


(cheese:31317): cheese-CRITICAL **: 17:36:23.925: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:31317): GLib-CRITICAL **: 17:36:23.926: g_variant_new_string: assertion 'string != NULL' failed

(cheese:31317): GLib-CRITICAL **: 17:36:23.926: g_variant_ref_sink: assertion 'value != NULL' failed

(cheese:31317): GLib-GIO-CRITICAL **: 17:36:23.926: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:31317): GLib-CRITICAL **: 17:36:23.926: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:31317): GLib-GIO-CRITICAL **: 17:36:23.926: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

(cheese:31317): GLib-CRITICAL **: 17:36:23.926: g_variant_unref: assertion 'value != NULL' failed

** (cheese:31317): CRITICAL **: 17:36:23.926: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed
```

When I open it from the menu I just get a "No device found" error in the cheese window.

---

### Post by mörgæs on 2020-04-23
We see a number of similar threads where Guvcview works but not Cheese. I don't have other suggestions than to stay with the former.

---

### Post by ajgreeny on 2020-04-23
> **mörgæs said:**
> We see a number of similar threads where Guvcview works but not Cheese. I don't have other suggestions than to stay with the former.

Precisely!
 If guvcview is working where is the problem?

I have never managed to get cheese to save a pic or video with my old logitech webcam but guvcview always works fine; I don't  care as long as something works!

---

### Post by mörgæs on 2020-04-23
Rsteinmetz, in a few weeks when development of 20.10 begins it would be great if you could test your camera running Cheese in 20.10 and discuss your findings in the development forum, possibly creating a bug report.

---

### Post by rsteinmetz70112 on 2020-04-23
I was really just playing with it. Like a lot of people I have some time on my hands. :cool:
I was interested in using it for other things like skype or zoom, so I guess I'll just press on.
As for 20.10 I'm not likely to ever load or use that version. In about a year of so I'll probably begin to move my Linux computers to 20.04 LTS.

---

