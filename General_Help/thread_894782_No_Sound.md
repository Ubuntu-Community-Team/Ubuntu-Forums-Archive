---
title: "No Sound"
date: 2008-08-19
forum: General Help
---

### Post by starving030 on 2008-08-19
I have Ubuntu 8.04 with an Intel D925XECV2 motherboard. I can't figure out how to get the audio drivers for this OS. Any suggestions?

---

### Post by master.swarky on 2008-08-19
What does the 'alsaconf' command say? It's located in the package 'alsa-tools' or 'alsa-utils'.

---

### Post by starving030 on 2008-08-19
Hmmm..now I am very new here. So is there some type of tutorial? Because I'm not sure what you mean there.

---

### Post by master.swarky on 2008-08-19
Oh, okay. Try typing in your terminal:

ls /dev/dsp

It should print you something like '/dev/dsp'

Does it?

---

### Post by starving030 on 2008-08-19
it's says this

ts@dt:~$ ls /dev/dsp
/dev/dsp
ts@dt:~$

---

### Post by master.swarky on 2008-08-19
Cool, it likely means that your sound card was successfully detected.
Okay, now would you type in your terminal:

alsamixer

and, using your arrow keys, raise the volume? Take care if the channels are not muted - you can unmute them by pressing 'M' button.

---

### Post by starving030 on 2008-08-19
AWESOME!!! It works now....Thanks

Is there a place to go I can learn all these commands?

---

### Post by master.swarky on 2008-08-19
Umm.. Likely yes, but unfortunately I don't know a lot of places like that.

Anyway, in most cases, by typing in your terminal:

man <command_name>    (i.e. 'man alsamixer')

you can get access to a so-called man page (man stands for manual)

It would be a nice starting point, I guess.

Cheers :)

---

### Post by lyni on 2008-08-20
there are several places to get info. just search for it. but a good place to start is here - /help.ubuntu.com/community/Beginners/FAQ

---

