---
title: "Relentless loud speaker pops when clicking empty screen areas"
date: 2024-07-07
forum: Hardware
---

### Post by nrpeyton on 2024-07-07
Good afternoon

Ubuntu is suffering from relentless, loud, (sudden) speaker pops/distortion when clicking on **any** screen areas (including empty or white-space) in ANY browser (Chromium ***and*** Firefox). The sound is similar to the loud 'pop' normally only heard when initially powering on external speakers connected to the 3.5mm audio jacks on ATX motherboards.

If clicking continues without a pause exceeding 10-15 seconds, no popping sound occurs. However, if there is a single click followed by a pause of 10-15 seconds and then another click, it produces a sound akin to someone turning the speakers off and on. Keyboard input does not affect this timing; only 'not clicking' for 10-15s and then clicking again triggers the issue.


[SIZE=1]_My configuration:_
1. Ubuntu 24.04 LTS (fresh install)
2. Not limited to a single browser or browser version (affects Chrome [Brave] and Firefox).
3. Motherboard: ASUS STRIX Z270H GAMING
4. Speakers: External (5.1 surround).
[/SIZE]

This feels like it might be related to a bug with an Ubuntu power-saving feature (or insufficently long defaults), not a Chrome/Firefox issue.  My system is dual-boot and I cannot replicate this under Windows in either browser.

---

### Post by currentshaft on 2024-07-07
Can you reproduce the issue with other speakers, or even better, a set of headphones?

---

### Post by nrpeyton on 2024-07-07
**Bluetooth headphones:** no issue
**Regular headphones (plugged into motherboard's rear 'black' 3.5mm audio jack): **yes, issue present.

It's not continuous "popping"; it's a single "pop"&#8212;sudden and short, similar to the sound of the speaker power being quickly switched off and on, but louder.
The "pop" occurs precisely at the moment of any mouse click. If I don't click the left mouse button for 15 seconds and then click again (anywhere), the sudden "pop" happens again, hence why I mentioned power-saving?

It is obviously extremely distracting, as any delay of 10-15 seconds between clicks (e.g., to read a paragraph on a page) results in the next click (button or empty space) causing the sudden "pop" again.  Its relentless.

Could it be power-saving related? Insufficently long defaults for motherboard's integrated sound device?  Although that would make me surprised its not a known issue.

The loud pop/distortion also occurs whenever any regular sound begins playing (only momentarily at the beginning).  I can put up with that to an extent. But, having it occur randomly when clicking on things that are not associated with any sound playing totally breaks my Linux experience.  Clicking 'save' after editing this post just caused it.

---

### Post by nrpeyton on 2024-07-09
These are the affected audio jacks (marked with a red astrix)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293959&stc=1[/IMG]

---

### Post by Yellow Pasque on 2024-07-09
Try disabling powersave on the sound card:
```
echo "options snd-hda-intel power_save=0" | sudo tee /etc/modprobe.d/audiofix.conf
sudo update-initramfs -u -k all
```
Reboot. Any better?

---

### Post by nrpeyton on 2024-07-11
Hi that seems to have fixed it, thank you:

```
[COLOR=#000000][FONT=&amp]echo "options snd-hda-intel power_save=0" | sudo tee /etc/modprobe.d/audiofix.conf[/FONT][/COLOR]
```

Question: Your second line was not required, not sure its purpose?

---

### Post by Yellow Pasque on 2024-07-11
> **nrpeyton said:**
> Hi that seems to have fixed it, thank you:
Question: Your second line was not required, not sure its purpose?

It may be needed depending on whether the module in question is part of the kernel image. Since I don't feel like memorizing which ones are and aren't, I just throw it on after modprobe.d modifications to make sure.

---

