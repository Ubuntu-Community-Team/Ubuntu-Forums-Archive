---
title: "Mysterious audio issue"
date: 2011-08-10
forum: Hardware
---

### Post by Blasphemous on 2011-08-10
Got this little audio problem on my old desktop pc: it is a _Pentium IV_ 2Ghz machine with _512 mb_ of RAM running_ Ubuntu 8.04 LTS 34 bi_t.

Before posting on this forum, I followed the standard "audio-issue" procedure:

Typing
```
lspci | grep -i audio 
```
gave me
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
```so at first I thought** my audio card had been recognize**d and that's and good thing, but** I could not hear anything at all**.

So I tried 
> alsamixer
And than unmuting every indicator and raising them up as much as possible.
**But it did not work at all!**

So I tried clicking *preferences* on the audio tray icon, and that's what appeared:

[[IMG]http://img7.imageshack.us/img7/2024/screenshotvolumecontrol.png[/IMG]]("http://imageshack.us/photo/my-images/7/screenshotvolumecontrol.png/")

I could now select one of the devices, but **none of them seems to work**, even repeating the "alsamixer" step for  both of them,

Finally, I have to say that when I open a random mp3 file** I get no error message** and everything seems to be ok, except for the fact that [B]I still can't hear anything,
[/B]
Sometimes I think I just have to plug the speakers in XD (Trust me: they are plugged, I checked like 20 times! XD)

Any idea?

---

### Post by Toz on 2011-08-10
Perhaps this post can help [http://ubuntuforums.org/showpost.php?p=3732575&postcount=3]("http://ubuntuforums.org/showpost.php?p=3732575&postcount=3")

---

### Post by Blasphemous on 2011-08-11
Still doesn't work

---

