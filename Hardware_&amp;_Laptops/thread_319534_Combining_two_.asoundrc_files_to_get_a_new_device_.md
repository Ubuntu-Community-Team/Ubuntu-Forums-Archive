---
title: "Combining two .asoundrc files to get a new device working"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by RedKrieg on 2006-12-15
I'm trying to get my logitech USB mic to work in alsa using [http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/]("http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/") but I need my .asoundrc file to use spdif.  I cannot for the life of me figure out how to combine two .asoundrc files to get a working config.  My current (functional) .asoundrc is here:
```
# hw:0,1 designates the Digital Coaxial Output
# S32_LE is the only format supported by the driver
# period_time, period_size, and buffer_size are needed to make aRts not stutter. Increase buffer_size if stuttering persists.
pcm.spdifdmix {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,1"
        format S32_LE
        period_time 0
        period_size 1024
        buffer_size 4096
    }
}

# default ALSA route for software support of multiple sound streams
pcm.!default {
    type plug
    slave.pcm spdifdmix
}

# Ogle
pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

# mplayer -ac hwac3
pcm.!iec958 {
    type plug
    slave.pcm "hw:0,1"
}
```
anyone know what I can do to use the usb for input and spdif for output?

---

