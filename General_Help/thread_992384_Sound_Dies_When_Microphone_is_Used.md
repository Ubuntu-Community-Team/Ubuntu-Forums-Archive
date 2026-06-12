---
title: "Sound Dies When Microphone is Used"
date: 2008-11-24
forum: General Help
---

### Post by Unanimated on 2008-11-24
EDIT: Still only one reply..

PULSEAUDIO!!

I hate this horrid piece of software so much. I have two sound cards plugged into my computer, one is an Audigy, and the other one is integrated into my motherboard. They both have recording, and the Audigy mysteriously has a FireWire port. Anyway, everything input-related is hellish. They both use ALSA, and ALSA is set to go through Pulseaudio and everything. I have a microphone plugged into my Audigy card, and that is fine, but I have a double 3.5mm cord with 5.5mm adapter plugged into it for guitar tuning plugged into my motherboard sound card. When I'm listening to music with Amarok, then I open Lingot to tune my guitar, the sound becomes choppy and the internet dies. When I reset everything (which I recently figured out how to do without restarting), then close Amarok, everything will continue to work.. Except, of course, Lingot. Muting my Audigy input port and setting my default to the motherboard card doesn't help, just, you know, chooses where it's coming from. Going to Volume Meter (Recording) then playing something on my guitar while it's plugged into the cord plugged into the motherboard card makes the bars in the meter move and stuff normally, and in sync with the guitar. When I open Lingot, it all goes to hell. It becomes laggy, and I have to close the volume meter to even get it to open. Playing the E string, then muting it returns a C# from Lingot about 2 minutes after the guitar has stopped playing, then it doesn't adjust or anything, and goes back to the blank note after another 2 minutes. Actually, doing anything involving the microphone while playing something causes the sound to become choppy and lossy. What's going on?

---

### Post by zephyrcat on 2008-11-24
If pulseaudio is the problem (which it *cough* often is), there is always this:

```
sudo killall pulseaudio
```

You can try running that in the terminal.

---

### Post by Unanimated on 2008-11-25
Well, it seems like PA won't use both of my cards simultaneously, and the same card can't be playing back or recording at the same time. Using the cord plugged into my motherboard card does nothing, even when it's set to the default input device. It's plugged into the right port, I've checked. The only one that works is the Audigy.

---

### Post by Unanimated on 2008-11-26
I know the Audigy can play back and record at the same time, because I did it numerous times in Windows.

---

### Post by Unanimated on 2008-11-27
bump

---

### Post by Unanimated on 2008-11-28
b u m p

---

### Post by Unanimated on 2008-11-28
> **zephyrcat said:**
> If pulseaudio is the problem (which it *cough* often is), there is always this:

```
sudo killall pulseaudio
```

You can try running that in the terminal.

Didn't work, killed all my sound.

---

### Post by Unanimated on 2008-11-29
bump

---

### Post by Unanimated on 2008-11-29
Is this something to do with ALSA or Pulseaudio? It was running perfectly, then it stopped. Somebody help me!

---

### Post by Unanimated on 2008-11-29
bump

---

### Post by Unanimated on 2008-12-06
bump...

---

