---
title: "Enable  gallium llvmpipe for intel graphic"
date: 2013-09-01
forum: Hardware
---

### Post by max246 on 2013-09-01
I have a intel graphic card that is pretty slow on my ubuntu, sometimes is like laggy, what I found out is that using " gallium llvmpipe" I can get a result of 700 FPS with glxgears vs the 60 FPS with i915 driver.

I have no idea how to enable the gallium llvmpipe on my ubuntu 12.04, I just know that running this command "LIBGL_ALWAYS_SOFTWARE=1 glxgears -info" it uses the faster driver.

There is a way to get rid of i915 driver and use gallium?

---

### Post by Yellow Pasque on 2013-09-01
glxgears is not a benchmark. i915 does 60 fps because it's synced to the refresh rate (60 Hz) to avoid tearing.

If your GPU can't keep up with Unity, then using llvmpipe will only make it worse. Try a lighter desktop (xubuntu/xfce, lxde/lubuntu).

---

### Post by max246 on 2013-09-02
Well I had ubuntu 32 bit 12.04 and it was working quiet fine... I moved to Ubuntu 13.04 and I had some issues like xorg was freezing and I had to restart lightdm.
Last weekend I went back to ubuntu 12.04 but 64 bit, it still doing some crazy stuff and sometimes it gets slowly and the cpu gets very hot...  I am not sure that is my computer old because I got it 1 year ago.

It can be that the driver for my graphic card is good only with 32 bit or there is something strange that is not using my GPU but it uses the CPU instead.

The main issue that I have is the xorg freezing for a while ( when I am using chrome ) and the only thing I can do is to wait about 5 minutes or go int othe tty console and restart lightdm

---

