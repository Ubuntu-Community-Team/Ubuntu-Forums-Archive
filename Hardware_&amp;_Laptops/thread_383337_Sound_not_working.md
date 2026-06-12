---
title: "Sound not working"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by buried on 2007-03-13
This is weird, I used to have Dapper Drake and sound works perfectly without any software but on Edgy Eft, there's no sound? please help me.

---

### Post by buried on 2007-03-13
Bump :lolflag:

---

### Post by 25an on 2007-03-13
do you have two sound cards, because fore some reason when I installed edgy my onboard soundcard was the default so I had to change that in edgy, this was not needed  
in dapper.

---

### Post by buried on 2007-03-13
uhh...no I do not have 2 sound cards, at least I don't think so I tried choosing different things adjusting the volume and stuff like that but it ain't working!

---

### Post by buried on 2007-03-14
Bump:guitar: :lolflag:

---

### Post by buried on 2007-03-14
Hello May I bump this Thread!:lolflag:

---

### Post by Azilla on 2007-03-14
By any chance do you have a onboard 56k modem? My Toshiba had one, and for some reason, ALSA tried to route sound to my modem rather than my actual soundcard.

You could also try to type-> sudo lspci
and look around for anything that says "Multimedia" or "Audio", then do a search on google for your audio card's chipset and linux/ubuntu. I'm sure you'll come across some random link with what your looking for.


:/

---

### Post by buried on 2007-03-15
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
thats what my Lspci says.

---

### Post by Azilla on 2007-03-16
Try this
```

# sudo modprobe snd-atiixp
#
# aplay -l

```

This should load your module into the kernel, and display that sound cards info. Try and see if sound works after that.

---

### Post by Sonicgoo on 2007-03-18
I don't know about him but it worked for me thanks. 

I love this forum. 

Can somebody explain why it worked.

---

### Post by Azilla on 2007-03-19
The module "snd-atiixp" wasn't loaded into the kernel. So by typing the "modprobe and-atiixp" command, you manually loaded it.

:)

---

### Post by gilgongo on 2007-03-19
I don't know if this is your problem, but what worked for me is this:

1. Open a terminal
2. Type "alsamixer"
3. You will see an application that looks like it came out of the 1980s.
4. Use the arrow keys to navigate to the PCM volume and turn it up, or unmute it (using the "m" key) if necessary. You may have to mute/unmute/modify other things too.
5. Hit Esc to save and see if you now have better sound.

---

