---
title: "After upgrade to 8.10 Rhythmbox will not open"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Dj TweeX on 2009-02-12
I upgraded to 8.10 & i tried to open rhythmbox, it said it was opening but never did.
i typed in terminal,

```
~$ rhythmbox
```

And got this,

```
rhythmbox: error while loading shared libraries: libffi.so.4: cannot open shared object file: No such file or directory
```

I found out that when it upgraded it replaced the aforementioned file with "libffi.so.5"

I attempted to download the so.4 file but because its technically "outdated" it was no longer available.

Can anyone please help me with this situation??

~~Gabe~~

---

### Post by RobertK81 on 2009-02-14
Same problem here, would be glad if anyone could help.

Regards,

Robert

---

### Post by ilioscio on 2009-02-14
not sure if this will work but you can try 
```
sudo ln /usr/lib/libffi.so.5 /usr/lib/libffi.so.4
```

---

### Post by RobertK81 on 2009-02-15
Thanks, that did it. :)

---

### Post by Dj TweeX on 2009-02-23
worked but i get this error
```
gabe@hp-mini:~$ rhythmbox

(rhythmbox:18446): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate

(rhythmbox:18446): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate

(rhythmbox:18446): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate

```

not the biggest issue i guess seeing how im running on an 
HP Mini 1030n so it doesnt have a cd drive haha

---

