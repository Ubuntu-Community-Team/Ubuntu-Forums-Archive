---
title: "Getting software to find sound card devices"
date: 2012-12-30
forum: Hardware
---

### Post by surenot on 2012-12-30
I am running Ubuntu 12.04 on an HP mini 110.  I have downloaded a few amateur radio software programs that use the sound card for sending text and images.  However, only one of those programs, Fldigi, actually seems to recognize my sound card.  The rest are looking for a /dev/dsp (or dsp1, 2, and 3) as the sound card device, but none of those will work, and I keep getting an error message of:  sound_open_for_read: opensnd: open: /dev/dsp: No such file or directory.  I have tried entering many sound card directories manually, but none seem to work.  Is there a way I can find the correct directory to the computer's sound card device through something like terminal?

Thanks

---

### Post by ibjsb4 on 2012-12-30
You may want to try here for help.

[https://wiki.ubuntu.com/UbuntuHams](https://wiki.ubuntu.com/UbuntuHams)

---

### Post by surenot on 2012-12-30
Thanks for the link.  I was able to find out that the problem is that the programs are designed for use with an OSS, but Ubuntu uses ALSA.  I tried using aoss by running the command 'aoss gmfsk' (being one of those programs) but that doesn't seem to be doing much of anything, I still get the same error.

---

### Post by mal205 on 2013-02-16
I know this post is coming up to a couple of months old, however this might help someone else. 

Ubuntu is using Pulse Audio, so try "padsp gmfsk". Worked for me.

---

