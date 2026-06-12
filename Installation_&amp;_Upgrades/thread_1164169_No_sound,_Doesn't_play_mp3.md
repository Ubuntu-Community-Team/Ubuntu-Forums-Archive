---
title: "No sound, Doesn't play mp3"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by drrose1977 on 2009-05-19
I just installed Ubuntu 8.04 and I can not hear audio on Youtube or play my mp3 songs.  No idea what to do.

---

### Post by abn91c on 2009-05-19
try this guide to get your sound going  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , 
for the mp3's you need to install the codecs in a terminal type ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sedawk on 2009-05-19
There is a speaker symbol in the upper right corner of your Desktop.
If it is not muted open the context menu and select "open volume control".
Check for any sliders set to mute or low volume.
(PCM/MASTER/HEADPHONE)

You can open a terminal window and try to run "alsamixer".
If it works you will see a text-based volume control and
data like Card:, Chip: View:, ...
Again you see vertical bars for the separated volumes and 
"MM" in the lower boxes suggests a muted device.
If "alsamixer" doesn't start properly your audio hardware needs
some more troubleshooting...

---

### Post by drrose1977 on 2009-11-19
Ok, so I've got the volume to work when playing movies and music on the master user account, but the volume doesn't work for playing movies on the guest account.  I've checked out the "Alsamixer" and changed all of the "MM"s.  Still, no volume on the guest account.  I've also tried to do some of the sudo apt - get installs, but the guest account doesn't have permissions to do things like this.

---

