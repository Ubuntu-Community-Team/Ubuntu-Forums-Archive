---
title: "Help With New Laptop pt.2: Integrated Webcam"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by wyth on 2008-02-13
I recently picked up a new Lenovo Ideapad Y510, and for the most part and very happy with it. It's a snappy machine that holds great linux possibilities. But I do have a few issues with it that I'm trying to fix, and this is part 2 in that series, my integrated webcam.

So: lsusb tells me the device ID is 5986:0200, which seems to be the same as the Acer OrbiCam.  In gstreamer-properties, my device is set to Lenovo Easy Camera with the v4l2 plugin.  I can test it on that and on Ekiga, but my image is upside-down.  

The camera isn't recognized by easycam2, camorama, cheese, Skype, none of that.

So now it's over to you -- ideas?

---

### Post by linuxwizard on 2008-02-13
You might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there.

---

### Post by wyth on 2008-02-13
Nope, no options in there that changes anything.

---

