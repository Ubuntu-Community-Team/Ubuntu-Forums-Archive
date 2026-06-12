---
title: "Empathy, exaile is not working, gstreamer issue."
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by sachin6870 on 2009-11-02
Hi Guys,
 Thanks/congratulations for Karmic realese to Ubuntu Dev team.

 I am running in to issues after upgrading to Ubuntu 9.10 Karmic:

 Empathy, exaile is not starting up. Looks like issue is related to gstreamer versions.
```
sachin@sachin-laptop:~/envista/VPN$ empathy

(empathy:30994): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/libschroedinger-1.0.so.0: undefined symbol: oil_function_class_ptr_avg2_32xn_u8

(empathy:30994): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/libschroedinger-1.0.so.0: undefined symbol: oil_function_class_ptr_avg2_32xn_u8

(empathy:30994): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstplaybin.so': /usr/lib/gstreamer-0.10/libgstplaybin.so: undefined symbol: gst_stream_volume_get_type

(empathy:30994): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstvolume.so': /usr/lib/gstreamer-0.10/libgstvolume.so: undefined symbol: gst_stream_volume_get_type

(empathy:30994): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpulse.so': /usr/lib/gstreamer-0.10/libgstpulse.so: undefined symbol: gst_stream_volume_get_type
empathy: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/interfaces.so: undefined symbol: gst_stream_volume_format_get_type
Error re-scanning registry , child terminated by signal
Run 'empathy --help' to see a full list of available command line options.

(empathy:30993): empathy-WARNING **: Error in empathy init: Error re-scanning registry , child terminated by signal
sachin@sachin-laptop:~/envista/VPN$ exaile 
INFO    : Loading Exaile 0.3.0.1...
INFO    : Loading settings...

(exaile.py:31000): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/libschroedinger-1.0.so.0: undefined symbol: oil_function_class_ptr_avg2_32xn_u8

(exaile.py:31000): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/libschroedinger-1.0.so.0: undefined symbol: oil_function_class_ptr_avg2_32xn_u8

(exaile.py:31000): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstplaybin.so': /usr/lib/gstreamer-0.10/libgstplaybin.so: undefined symbol: gst_stream_volume_get_type

(exaile.py:31000): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstvolume.so': /usr/lib/gstreamer-0.10/libgstvolume.so: undefined symbol: gst_stream_volume_get_type

(exaile.py:31000): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpulse.so': /usr/lib/gstreamer-0.10/libgstpulse.so: undefined symbol: gst_stream_volume_get_type
AttributeError: 'module' object has no attribute 'Element'
python: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/interfaces.so: undefined symbol: gst_stream_volume_format_get_type
sachin@sachin-laptop:~/envista/VPN$ 

```

 I tried reinstalling empathy, gstreamer packages including plugins.
 But nothing is working. Please let me know if you any pointers.

Thanks,
-- Sachin.

---

### Post by sachin6870 on 2009-11-02
Reinstalling whole gstreamer packages solved issue.

```

sudo apt-get remove gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```
```

sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```

and 
```

sachin@sachin-laptop:/usr/local/lib$ sudo rm -rf libgst*

```

Thanks.

---

