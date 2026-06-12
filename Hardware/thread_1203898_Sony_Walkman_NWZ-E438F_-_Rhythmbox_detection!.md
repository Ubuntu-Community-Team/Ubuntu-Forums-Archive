---
title: "Sony Walkman NWZ-E438F - Rhythmbox detection?!"
date: 2009-07-03
forum: Hardware
---

### Post by atari05 on 2009-07-03
I have the above MP3 player. The issue I'm having is that through it does mount the MP3 as a standard "disk", Rhythmbox doesn't see it. As such I can't transcode my FLAC' on the fly to a supported (and smaller) format. 

Does anyone have one of these MP3 players and use Rhythmbox to manage it? If so, what magic did you use to get it working?

(The odd part is that it is a MTP device, and even with the MTP plugin activated, it doesn't connect as such!?!")

---

### Post by BryceHarding on 2009-07-20
Same Problem Here. Just got a nwz-e436f and would like to use Rythmbox to sync it. Using Jaunty and all of the threads on this i'm finding are for earlier releases. Anyone got this working yet?

---

### Post by kostkon on 2009-07-20
Try this:

create a text file with the name on the player
```
.is_audio_player
```
and this may make *Rhythmbox* to see your player.
Also, quoting from the [*Rhythmbox* FAQ]("http://live.gnome.org/Rhythmbox/FAQ"):
> Create a *.is_audio_player* file on the device. You can set a few fields in this file to override the HAL device information like this:
```
audio_folders=MUSIC/,RECORDINGS/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg
```

---

### Post by BryceHarding on 2009-07-20
thankyou kostkon this works perfect. thanks :)

---

### Post by ademey on 2010-04-23
thanks!

This finally enables me to use my sony walkman (NWZ-E436F) properly in ubuntu. Anyone who succeeded in transferring cover art to the device?

---

### Post by solbarfrank on 2012-05-05
Ok, it works perfectly, thank you very much.

---

### Post by betete on 2012-08-14
Hi there, I know the post is old, but I'll try anyway. I have the same problem with my NWZ-E438F. I have Ubuntu 12.04. Rhythmbox detects the device correctly, though I cannot see its content, and not even syncronize it. I cannot even try the solution you give here because I cannot mount the device as a flash drive. The system refuses. I tried to create the .is_audio_player file from Windows, but it refuses because of the dot at the begining of the filename.
Any idea?
Thank you.

---

### Post by hoakerk. on 2012-11-27
> **kostkon said:**
> Try this:

create a text file with the name on the player
```
.is_audio_player
```
and this may make *Rhythmbox* to see your player.

Worked fine, thank you.

---

