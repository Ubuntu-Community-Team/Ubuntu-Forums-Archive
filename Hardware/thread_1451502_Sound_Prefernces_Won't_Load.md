---
title: "Sound Prefernces Won't Load"
date: 2010-04-10
forum: Hardware
---

### Post by willsomebody on 2010-04-10
Hi all.  I have onboard nvidia sound that has 7 channels.  It has worked with previous versions of ubuntu as well as 9.10 for almost 6 months.  Yesterday, I tried to use the front audio output for the first time and noticed that it did not work (It might not even be plugged in to the mobo).  I opened sound preferences and changed my device from stereo analog duplex to 7.1 analog duplex, which did not fix it.  After a restart, I no longer get a volume icon on the panel and sound doesn't work at all.  When I go to System > Prefernces > Sound, I get an error that says it is waiting for sound system to respond.  I don't care about the front audio port, but I would like sound to work again.  I suspect that it doesn't like the 7.1 channel setting.  Is there a way to change the sound device from the terminal or by changing a text file somewhere? 

Thanks in advance,
Will

---

### Post by lidex on 2010-04-11
This may help:
[http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")

---

### Post by willsomebody on 2010-04-11
Thank you.  I looked at that forum post and found the configuration files in ~/.pulse. I opened up '4f4ab17c4a08714a7df97bcd4b072ae3-default-sink' and found the line ```
alsa_output.pci-0000_00_07.0.analog-surround-51
``` and changed it to ```
alsa_output.pci-0000_00_07.0.analog-stereo
```That did not fix the problem, so I created a second user and discovered that audio worked for it, so I copied the entire contents of ~/.pulse from that user to the one without audio.  That still has not fixed my audio.  Does anybody have any ideas?  This isn't too critical because I can log in as a different user and get sound, but this is puzzling me.

Thanks, 
Will

---

### Post by lidex on 2010-04-11
Check this out, particularly "Part A":
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by willsomebody on 2010-04-12
Thank you very much.  Just in case anybody else has the same problem,  I just did the step about backing up and removing ~/.pulse.  I ran```
rm -r ~/.pulse 
```and responded 'y' to all of its inquiries```
rm: remove write-protected regular file `/home/****/.pulse/4f4ab17c4a08714a7df97bcd4b072ae3-device-volumes.tdb'? y
rm: remove write-protected regular file `/home/****/.pulse/4f4ab17c4a08714a7df97bcd4b072ae3-stream-volumes.tdb'? y
rm: remove write-protected regular file `/home/****/.pulse/4f4ab17c4a08714a7df97bcd4b072ae3-card-database.tdb'? y
rm: remove write-protected regular file `/home/****/.pulse/4f4ab17c4a08714a7df97bcd4b072ae3-default-sink'? y
rm: remove write-protected regular file `/home/****/.pulse/4f4ab17c4a08714a7df97bcd4b072ae3-default-source'? y

```then it said```
rm: cannot remove directory `/home/****/.pulse': Directory not empty
```At this point I looked at my panel and the volume icon had shown up.  Sound now works fine.

---

