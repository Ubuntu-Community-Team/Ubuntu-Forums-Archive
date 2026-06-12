---
title: "ripping my cds"
date: 2005-11-16
forum: General Help
---

### Post by tikal26 on 2005-11-16
before in hoary I used to be able to open my Cds and I would have a folder that would say MP3 and then just drag and drop in order to rip my cds but now I don't get such a folder I only get cda flac and ogg vorbis but no mp3.:confused:

---

### Post by tonysathre on 2005-11-16
get arson, its a good cd ripper

---

### Post by Strongbad on 2005-11-16
I think there's something you have to download to make mp3 files (legal issues or something like that). Have you tried looking on ubuntuguide.org? you might find something there.

---

### Post by tikal26 on 2005-11-16
I just dowloaded al the gstreamer plugins and now it works I started deliting until i figures that it was the lame plugin . (duh) but now i see that it is extremely slow. i mean I don't think that it's suposed to be this slow

---

### Post by Strongbad on 2005-11-16
[QUOTE=tikal26]I just dowloaded al the gstreamer plugins and now it works I started deliting until i figures that it was the lame plugin . (duh) but now i see that it is extremely slow. i mean I don't think that it's suposed to be this slow[/QUOTE]

Have you tried enabling dma? If not, try typing "hdparm -d1 /dev/-device-" inserting hdc, or what ever your device is set to, in place of -device-. If that works, there's some config file that you can edit to make it stick, but i'm not sure which one that is right off the top of my head.

Good luck!

---

### Post by finnjimm on 2005-11-17
[QUOTE=Strongbad]Have you tried enabling dma? If not, try typing "hdparm -d1 /dev/-device-" inserting hdc, or what ever your device is set to, in place of -device-. If that works, there's some config file that you can edit to make it stick, but i'm not sure which one that is right off the top of my head.[/QUOTE]

I added this to my /etc/hdparm.conf:
```

/dev/cdrom {
        dma = on
}

```

I guess /dev/cdrom works fine but you can change that to whatever hdX your real device is.

---

