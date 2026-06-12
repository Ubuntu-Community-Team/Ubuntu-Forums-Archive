---
title: "xv port not available"
date: 2017-08-26
forum: Hardware
---

### Post by zethel on 2017-08-26
Hello,

I actually don't know what I am searching for. I need gstreamer for developing purposes so I was checking if I have all the necessary plugins.
I wrote this in the terminal:```
[COLOR=#111111][FONT=Consolas]gst-launch-1.0 videotestsrc ! videoconvert ! xvimagesink[/FONT][/COLOR]
```
I got this output:
[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]```

[COLOR=#111111][FONT=Consolas]Setting pipeline to PAUSED ...[/FONT][/COLOR]ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPipeline:pipeline0/GstXvImageSink:xvimagesink0: 
Could not initialise Xv output
Additional debug info:
xvimagesink.c(1760): gst_xv_image_sink_open (): 
/GstPipeline:pipeline0/GstXvImageSink:xvimagesink0:
No Xv Port available
Setting pipeline to NULL ... [COLOR=#111111][FONT=Consolas]Freeing pipeline ...
[/FONT][/COLOR]
```

As you can see there is no xv port available. Do I miss some drivers? What should I do to make it work?

I'm on Ubuntu 16.04 (xenial) running in a virtual machine ( Oracle VM VirtualBox )

---

