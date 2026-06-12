---
title: "sound and vaio vgn-fz11mr"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by chtoosha on 2008-02-05
hi all.Could you help me?
I have a problem  with my sound card on Ubuntu 7.10 on Sony VAIO  VGN-FZ11MR . I have a sound but both  ports for headphone and microphone  do not work at all. When I enter the the cord of headphone the sound does not  transfer to headphone port.
As for microphone the alsa shows that  it works, but it does not. If I try to use some application to record sound it returns ugly noise.
Here the return of lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by kesman on 2008-02-05
check out alsamixer for muted channels. Unmute them with M and exit with esc.

---

### Post by chtoosha on 2008-02-05
all mu channels are unmuted.

---

### Post by chtoosha on 2008-02-05
All my channes are in  use.
I have not got mute ones.

---

