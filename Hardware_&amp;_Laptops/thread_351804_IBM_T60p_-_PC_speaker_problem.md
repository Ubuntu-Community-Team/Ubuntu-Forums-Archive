---
title: "IBM T60p - PC speaker problem"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by knolleary on 2007-02-02
Hi,

I got Edgy installed onto an IBM/Lenovo T60p laptop today. The PC speaker works fine, but it doesn't show up anywhere in  gnome-volume-control. It's not listed under Edit->Preferences..

I have the pcspkr module loaded and as I said, all the system sounds work fine. But they are too loud and I have no way to turn the PC speaker down.

I believe this is the relevant line from lspci:
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I've searched the forums and not found anything that works.

Anyone got any ideas?

Thanks,
N

---

### Post by TommeN on 2007-04-05
I also have a problem like this..

When i try playing a movie or sound file or anythink with sound i get a nice error thet says:
"This is an audio-only file, and there is no audio output available."

This is the message when trying to open an .mp3 file on the web,

But when im trying to open the file locally i get:
oss error: cannot open audio device (/dev/dsp)
arts error: arts_init failed (loading the aRts backend "/usr/lib/libartscbackend.la" failed)

This is with "VideoLan" app.

Anyone know what the problem is? I found a guide that says this sound card works out-of-box whit 2.6.x kernel..

---

