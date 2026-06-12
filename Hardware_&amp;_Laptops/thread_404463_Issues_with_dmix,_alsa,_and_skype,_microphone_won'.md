---
title: "Issues with dmix, alsa, and skype, microphone won't capture."
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by survient on 2007-04-08
Ok, trying to get skype working on ubuntu with the dmixer, tried recording something with alsa with an updated asound.conf, but didn't work, I've got my microphone capture unmuted, set for capture, and have the capture volume maxxed, but still can't seem to get it to work, here's my asound.conf:

pcm.card0 {
  type hw
  card 0
}

pcm.dmixer {
  type dmix
  ipc_key 1025
  slave {
    pcm "hw:0,0"
    period_time 0
    period_size 2048
    buffer_size 32768
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.skype {
  type asym

  playback.pcm "dmixer"
  capture.pcm "card0"
}

pcm.!default {
  type plug
  slave.pcm "skype"
}

any help would be appreciated.

---

### Post by lesha on 2008-05-23
Here's what worked for me:

pcm.foo_dmix {   
        type dmix
        ipc_key 1025
        slave {
                pcm "hw:0,0"
                period_time 0
                period_size 1024
                buffer_size 8192
                format S16_LE
                rate 44100
                channels 2
        }
        bindings {
                0 0
                1 1
        }
}

pcm.card0 {
        type hw
        card 0
        device 0
}

pcm_slave.foo {
        pcm "card0"
        rate 44100
        channels 2
        format S16_LE
}

pcm.foo_rec {
        type plug
        slave "foo"
}

pcm.!default {
        type asym
        playback.pcm "foo_dmix"
        capture.pcm "foo_rec"
}

---

