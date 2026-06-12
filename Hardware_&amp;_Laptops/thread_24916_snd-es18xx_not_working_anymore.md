---
title: "snd-es18xx not working anymore"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by ploum on 2005-04-08
Hi,

Another sound broken problem.

On my old laptopt ( [http://wiki.frimouvy.org/CompaqPresario](http://wiki.frimouvy.org/CompaqPresario) ), I've upgrade to Hoary today.

On Warty, the sound wasn't working out of the box. I had to put modprobe snd-es18xx isapnp=0.

Since the upgrade, the sound is not working at all !

During the boot process, I hear a lot of noisy BEEP (it seems that this is related to the problem)

The modprobe command now fail with : 

FATAL: Error inserting snd_es18xx( /full/path/here): No such device.

any idea of the problem and how I can solve it ?

---

### Post by az on 2005-04-08
I think that there was some alsa issues that they were going to implement after the release.

If it worked fine with warty, you should just keep using the warty kernel on your Hoary system.  You can install grubconf from Universe and make your Warty kernel the default.  It is to be supported for another 18 months...

---

### Post by ploum on 2005-04-09
thx for the advice but it doesn't work at all.

Rebooting on the old kernel doesn't change anything :-(

---

### Post by ploum on 2005-04-09
new thing about my problem !

When I shut the computer down, I also hear a lot of BEEP and I can see a lot of command saying that the card number is wrong and telling a lot of option I can use with the program.

it seems to be alsactl, but I'm not sure.

EDIt : it's amixer telling :

Inavlid Card Number
Usage : amixer <options> command
Available options :
.....
....
;...


I really don't understand

---

### Post by ploum on 2005-04-09
I'm just continuing this "monologue" as a reminder for myself.


I've just discovered that the file /proc/asound/cards contains

"no soundcards"

So it's a pure module thing, not an ALSA one.

When trying to modprobe snd-es18xx (with error : No such device), kernlog show :

ESS AudioDrive ES18xx soundcard not found or device busy.

---

### Post by az on 2005-04-09
"So it's a pure module thing, not an ALSA one."

If that were the case, booting your old kernel would solve your problem.

---

### Post by ploum on 2005-04-09
you are right, sorry.

I've discovered that, in order to have sound in Warty, I've added "modprobe snd_es18xx isapnp=0" to /etc/modules

but maybe  this file wasn't upgraded du to the md5 mismatch.

---

### Post by pelikan on 2005-04-27
I have the same problem with my Audigy 2 Value, where in  /proc/asound/cards it says "no soundcards."

What do I have to do to fix this? Thanks.

---

