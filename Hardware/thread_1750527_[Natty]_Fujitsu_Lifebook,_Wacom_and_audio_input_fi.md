---
title: "[Natty] Fujitsu Lifebook, Wacom and audio input fixes"
date: 2011-05-05
forum: Hardware
---

### Post by chitarrino on 2011-05-05
Here are two fixes for my Fujitsu Lifebook T5010.

Audio input did not work.
I had to
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
and add this line:
```
options snd-hda-intel model=fujitsu
```

Then the Stylus pen, which is not calibrated.
This is the code that I added to my startup scripts:
```
xsetwacom set "Serial Wacom Tablet stylus" Area "225 225 28808 18080"
```

I just thought these fixes were worth sharing.

---

### Post by FSGDAG on 2011-07-16
> 
Then the Stylus pen, which is not calibrated.
This is the code that I added to my startup scripts:
Code:
xsetwacom set "Serial Wacom Tablet stylus" Area "225 225 28808 18080"



I'm all of about 2 days old in Ubuntu. Would you mind doing me a favor and explaining to me where I want to put the code above? If you could tell me like you were explaining it to a "2 day old" that would be great :)  Obviously, you can leave out the "goo goo's" and "gaga's" LOL

---

### Post by knorquist on 2011-09-30
That'd be in terminal, good sir. You can find it by going into applications on the left side and looking around for terminal. Terminal is pretty much command line for linux.

---

