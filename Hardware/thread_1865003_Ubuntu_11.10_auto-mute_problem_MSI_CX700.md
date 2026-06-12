---
title: "Ubuntu 11.10 auto-mute problem MSI CX700"
date: 2011-10-19
forum: Hardware
---

### Post by Hrairoo on 2011-10-19
Hello everyone,

so I have upgraded my 11.04 to the latest 11.10 and I had some problems with the wifi RT3090 that I quickly solved thanks to the forum. But now I have just one last thing to sort out.

The problem I'm experiencing is that when I plug in my headphones it doesn't mute the speakers.

I'm sure it's got to do with the alsa model settings. I have managed to solve the problem where sound would come only from the built in "subwoofer" by adding this line to the /etc/modprobe.d/alsa-base.conf

```
snd-hda-intel model=acer-aspire-7730g
```

this is the only one I have found for the ALC888 where everything works except the auto-mute. There are some profiles where the auto-mute works but the "only subwoofer" problem remains.

So my question is, can I somehow manually add the auto-mute action or something like that?

---

### Post by Hrairoo on 2011-10-20
seriously, not even a buzz off, or a simple no? [IMG]http://s3.amazonaws.com/kym-assets/entries/icons/square/000/003/617/okayguy.jpg?1283381711[/IMG]

---

### Post by stafusa on 2011-11-03
Hey,
I'm having sound problems myself that I couldn't solve so I don't feel so qualified to give advice - besides you've probably tried already the obvious stuff - but, just in case: have you tried alsamixer? With this command you can get a 'gui' in the shell itself where you can enable an 'Auto-Mute Mode'.

---

### Post by Hrairoo on 2012-01-01
Yeah, I tried the alsa mixer, I went so far as to try every model there is for the ALC888 and with every model I went to check in the alsa mixer that all the important stuff for the sound and auto-mute on line out were set up correctly.

---

