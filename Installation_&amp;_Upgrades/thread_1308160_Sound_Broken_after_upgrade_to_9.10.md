---
title: "Sound Broken after upgrade to 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Zavage on 2009-10-31
So almost every time after I upgrade ubuntu releases, my sound mysteriously breaks, with the culprit usually being muted channels in alsamixer. But not this time! My sound is dead, alsamixer reports perfect, and sound works fine when I boot into XP instead of ubuntu, but that's not much of a solution, now is it? Any help would be appreciated, thanks!

---

### Post by Askar450 on 2009-10-31
Are you on a laptop? I have a Gateway FX model but my sound breaks on all Intrepid, Jaunty and Karmic so try this. Edit the file with the next command, gksudo gedit /etc/modprobe.d/alsa-base.conf now add this lines at end of the file.

options snd slots=snd-hda-intel,snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

If that one doesn't work try

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1

---

### Post by Zavage on 2009-11-04
Neither of those worked, but I'm on a homebuild desktop.
lspci gives me -
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

if it helps... 

Also, mic input works just fine, there's just zero output.

---

