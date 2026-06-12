---
title: "loud crackling sound when hibernate"
date: 2011-11-09
forum: Hardware
---

### Post by orsolyaaa on 2011-11-09
I have a Lenovo thinkpad edge with Lucid. Hibernation works fine, except a creepy sound it gives every time I hibernate it, right in the second the computer is switching off. It's a loud crackling sound, only half a second long, but it freaks me out every time I hear it. It sounds like my computer has just died. I have had this problem ever since I have my machine. The problem is still on with muted speakers and headphones plugged in.
Has anyone of you met this problem before?

---

### Post by papibe on 2011-11-09
Hi orsolyaaa. Welcome to the forums!

I can think of just two things that can make that sound: the hard drive, or the CPU fan. Both would need some checking.

How old is your computer and hard drive?

IMHO if it were the hard drive may be is not that bad. But the fan should stops smoothly. Any pets around? may be it needs some internal cleaning.

Just some thoughts,
Regards.

---

### Post by Basher101 on 2011-11-09
I would not worry too much, but checking should suffice IF there should be anything wrong. I do myself have some crackling sounds, but those come from the speakers, regardless if muted or not. The crackling is just the result of power coming to the speakers or stopping.

---

### Post by |{urse on 2011-11-09
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-alsa-lucid-generic

I had this same issue with lucid, the above seemed to fix whatever the problem was.

---

### Post by orsolyaaa on 2011-11-12
Hi everyone! Thanks for your replies!

Kurse: this did not work for me :(

Papibe: The other day I managed to make my sound card not to be recognized and the crackling sound was gone. So now I'm sure it comes from the speakers, not from the fan or the CPU.
I have no pets around my computer and the machine is quite new, 4 month old, and I have the sound ever since I bought it.

Basher101: Yes, you must be right about the sound source, but I just can't pay no attention. It's really loud and freaky. I'm always afraid something will go wrong with my speakers.

---

### Post by |{urse on 2011-11-12
Sorry to hear that, are these external speakers?

---

### Post by orsolyaaa on 2011-11-12
Nope. They are the internal ones.

---

### Post by MG&amp;TL on 2011-11-12
I get this with my laptop, and my speakers if I leave them on. I think it's just the kernel or whatever pulsing the ports. So you get blank sound. Or pulseaudio, or whatever handles sound.

---

### Post by orsolyaaa on 2011-11-13
It's not pulseaudio. I uninstalled it and the sound is still on when I hibernate the computer.

---

