---
title: "Audio Issue with Intel HDA 82801H"
date: 2008-07-16
forum: Hardware
---

### Post by Fiki on 2008-07-16
I recently bought a new Gateway laptop with an Intel HDA 82801H sound device. I installed the 64 bit version of 8.04. The sound plays, unfortunately there is no way for me to control the volume. Changing the volume using the default ubuntu mixer has no effect on the actual sound volume. Muting has no effect either. The driver seems to be installed and the device is recognized by the OS. After running alsamixer the audio just stops completely until I reboot again (this may or may not be relevant to the solution). If I can't get the audio working properly with volume control I just may cry - and not in any manly way either.

---

### Post by Fiki on 2008-07-17
bump

---

### Post by Fiki on 2008-07-17
I figured out that although master volume won't control the volume, the front volume will. Now, however the audio seems to clip out every couple seconds and sometimes at random the audio will stop working until I reboot. After searching the forums and the internet there seems to be a lot of people having issues with the ICH8 card family. Are there any additional packages I'm missing that could help an ICH8 card work? Why does alsa hate ICH8 users?

---

### Post by Fiki on 2008-07-17
I tried this: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

but I got hung-up on
Connecting to ftp|24.28.193.9|:21... 

are there some terminal outputs I could copy/paste that would possibly lead to some suggestions?

---

### Post by odysseusjak on 2008-07-17
You might try this link.  I found it the other day but haven't tried it yet.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

---

### Post by Fiki on 2008-07-17
I tried the script, but the sound is still choppy. ](*,)](*,)](*,)

---

### Post by odysseusjak on 2008-07-17
There's this link:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Fiki on 2008-07-17
I now discovered that the real issue was that the quality of music and videos (the files I used to test my audio with) was severely reduced after transferring them from my desktop to my laptop through an external hard drive (I may just return it to Best Buy since that was the primary reason I bought it.) Is there any way I can transfer these files over a network? Or maybe is there some unknown reason the files wouldn't correctly transfer from my external hard drive to my laptop?

---

### Post by Fiki on 2008-07-17
After installing the Gstreamer plugins the audio works fine for everything but vlc. I am used to vlc, and would like to keep using it since it works for pretty much every video format. I tried reinstalling vlc and all of its plugins, but the audio is still choppy. Is there a wrapper that uses gstreamer pluggins in vlc? Is there another audio/video player that supports as many formats as vlc? I need .avi .mpg .avi .wma .mp3 .wav .ogg .m4a .mp4 and dvds to work - are there plugins for some other player that will support all of these or a player that comes with all of these plugins?

---

### Post by odysseusjak on 2008-07-20
I've downloaded all the gstreamer plugins from Add/Remove and everything works fine on this end.  I don't have any skipping audio at all.  So I'm not sure what the issue is.

Sorry I can't be of more help.

---

