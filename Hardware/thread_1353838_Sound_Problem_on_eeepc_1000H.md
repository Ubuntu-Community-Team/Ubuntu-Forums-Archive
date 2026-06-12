---
title: "Sound Problem on eeepc 1000H"
date: 2009-12-13
forum: Hardware
---

### Post by dart620 on 2009-12-13
Hi all,
 

 I have done a fresh 9.10 install on my eeepc 1000H 15-20 in to a session the sound stops working all together. If I run the audio test via system testing the sound starts working again .

Thanks!
dart620

---

### Post by RedSingularity on 2009-12-14
Are you using pulseaudio?  If you are....when the sound stops working check your deamons to see if pulseaudio is still up and running.

---

### Post by dart620 on 2009-12-19
I have just started using Ubuntu/Linux how do i check what deamons are running .

---

### Post by RedSingularity on 2009-12-19
Look in System>Admin>System Monitor.  Look under the processes tab.  See if pulseaudio is listed there when the sound cuts out.

---

### Post by dart620 on 2009-12-20
Sound cut out on me half way through a movie. Pulseaudio is listed and shows up as sleeping

---

### Post by RedSingularity on 2009-12-20
Do you have a file called /etc/asound.conf?

---

### Post by dart620 on 2009-12-20
I can't find any file called asound.conf.

---

### Post by RedSingularity on 2009-12-20
Ok do the folowing......

sudo touch /etc/asound.conf

then.............

gksudo gedit /etc/asound.conf

Then add the following to the file and save it.

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by dart620 on 2009-12-22
It's working !!!!! After creating the asound.conf I have had my eeepc running for 4hrs now and the sound has not cut out on me at all.
 

 Thank you for helping me... and I hope you have a merry Christmas.

Thanks. dart620

---

