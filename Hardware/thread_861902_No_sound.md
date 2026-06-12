---
title: "No sound"
date: 2008-07-17
forum: Hardware
---

### Post by fauzi46 on 2008-07-17
hi..

i newbie using ubuntu..
my problem is when i using ubuntu no sound at all..
anyone can help me..
i using lenovo y410..

---

### Post by lisati on 2008-07-17
[LIST=1]
[*]Which version of Ubuntu are you using? 8.04? Ubuntu/Kubuntu/Xubuntu....?
[*]What kind of computer are you using? Desktop or laptop? What make & model?
[/LIST]

---

### Post by amba on 2008-07-17
You may try to edit file /etc/modprobe.d/alsa-base, and add this line at end of file:
```

options snd-hda-intel model=lenovo

```
and reboot.
After reboot, go in the mixer (in the command line type "alsamixer", and check if everything is ok.
Use "m" key to mute/unmute every column, and up/down arrows increase volume which may be off in your settings.
Esc key makes you leave program, it is automatically saved (at least until you reboot again)

If it doesn't work, don't forget to remove again the line above! (it may conflict with further suggestions by other users)

---

### Post by fauzi46 on 2008-07-17
ok..
thank for advise..:)

---

### Post by fauzi46 on 2008-07-17
> **amba said:**
> You may try to edit file /etc/modprobe.d/alsa-base, and add this line at end of file:
```

options snd-hda-intel model=lenovo

```
and reboot.
After reboot, go in the mixer (in the command line type "alsamixer", and check if everything is ok.
Use "m" key to mute/unmute every column, and up/down arrows increase volume which may be off in your settings.
Esc key makes you leave program, it is automatically saved (at least until you reboot again)

If it doesn't work, don't forget to remove again the line above! (it may conflict with further suggestions by other users)


can u tell me details because i had tried but fail..
plzz help me..

---

### Post by balaknair on 2008-07-17
How to edit modprobe.d

Open a terminal(Application menu> Accessories> Terminal)
Copy paste the following lines

```
sudo gedit /etc/modprobe.d/alsa-base
```

This will open the file you need.
Copy and paste this line at end of the file(as the last line), save and exit.
```
options snd-hda-intel model=lenovo
```

Reboot.

That aside, before you try anything else check the volume levels are not muted(they're muted by default) by right clicking on the speaker icon on the top right corner of the screen.

---

