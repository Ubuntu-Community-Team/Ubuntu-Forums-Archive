---
title: "wierd DVD playback issue"
date: 2008-12-02
forum: General Help
---

### Post by 2handband on 2008-12-02
I just put Ubuntu 8.10 on my Toshiba Satellite laptop (probably the worst computer in the world to run linux on, I know) and in order to enable encrypted DVD playback I went to this website and followed the instructions:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Now it works... kind of. The screen flickers horribly (I've tried both Totem and VLC) and after a couple of minutes it gives up and informs me that it is unable to stream the media. 

It worked fine on 8.04. Any ideas?

Thanks!

---

### Post by Vaidok on 2008-12-02
What is your video card?

---

### Post by 2handband on 2008-12-02
its an ATI Radeon x1200

---

### Post by 2handband on 2008-12-02
i tried re-installing without success

---

### Post by Vaidok on 2008-12-02
add the line
	Option	    "TexturedVideo" "off"
to the Device section of your xorg.conf file
located in /etc/X11/xorg.conf

---

### Post by 2handband on 2008-12-02
Thanks! That got it running on VLC, but it's still a bit jumpy. Totem still doesn't work. It plays the first few seconds and then gives me a "failed to stream" error.

---

### Post by Vaidok on 2008-12-02
I had that error and it cured it for me. Are you using Totem(Gstreamer) or xine?

---

### Post by 2handband on 2008-12-02
Totem. I've never heard of xine. VLC is working, but the playback kinda sucks. I should point out that I am very new to Linux.

---

### Post by Vaidok on 2008-12-02
Sorry I do not know anything else to help.

Search for other threads.

---

### Post by 2handband on 2008-12-03
Thanks for trying; at least I got it partially functional.

---

