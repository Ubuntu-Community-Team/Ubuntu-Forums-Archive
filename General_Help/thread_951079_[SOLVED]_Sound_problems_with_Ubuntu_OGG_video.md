---
title: "[SOLVED] Sound problems with Ubuntu OGG video"
date: 2008-10-17
forum: General Help
---

### Post by utnubuuser on 2008-10-17
Hello  -- I recently reinstalled the Intrepid Ibex Beta to test, and tried to watch the Ubuntu netbook remix video, ( [http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr) ).  Video works out of the box, (including updates), but no sound!
Is it normal to have to install codecs for OGG, (I actually installed ffmpeg through synaptic), or is this more likely to be a machine specific problem? IBM Thinkpad X31.

---

### Post by Pro-reason on 2008-10-17
Are you saying that audio for other types of files is working?

---

### Post by utnubuuser on 2008-10-17
Hi -- yes, all my other sounds are working fine, including other videos, youtube, last.fm etc.  Seems I also enabled flash-plugin non-free through synaptic.
Just no sound for the ogg video on the Ubuntu site. - Main link for the video asks if I want to install restricted codecs (for the mp4 version of the video, as well as the main link).  I don't mind really, it just struck me as odd that I'd have to enable restricted codecs to view an OGG video on the Ubuntu site.

I'm sure it's just some kind of configuration snag, and not a codec issue

---

### Post by Pro-reason on 2008-10-17
I'm using Intrepid, and OGG Vorbis files play fine for me.  You could try reinstalling:

```

sudo apt-get install --reinstall libvorbisfile3 libvorbis0a libvorbisenc2 vorbis-tools

```

Does the audio fail only in one app?  Can you play the files on the terminal using the ogg123 command?

---

### Post by utnubuuser on 2008-10-18
thanks, -are you sure about the commands?

I'm getting: invalid operation libvorbisfile3 etc.

---

### Post by Pro-reason on 2008-10-18
I don't see how that could happen.  Did you type them?  Try copying and pasting.

---

### Post by sj1410 on 2010-12-14
> **Pro-reason said:**
> I'm using Intrepid, and OGG Vorbis files play fine for me.  You could try reinstalling:

```

sudo apt-get install --reinstall libvorbisfile3 libvorbis0a libvorbisenc2 vorbis-tools

```

Does the audio fail only in one app?  Can you play the files on the terminal using the ogg123 command?

Hi,

i am having the same problem, all other file formats plays but i dont get sound in ogg files. i tried the above commands but no luck,

Swapnil

---

