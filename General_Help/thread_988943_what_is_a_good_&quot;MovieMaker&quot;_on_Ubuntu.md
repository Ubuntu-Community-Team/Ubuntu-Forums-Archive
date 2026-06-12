---
title: "what is a good &quot;MovieMaker&quot; on Ubuntu?"
date: 2008-11-21
forum: General Help
---

### Post by ieBrazil on 2008-11-21
Tell me one to install!

I installed by my own Open Movie Editor but I did not like it... I dont know. 

Tell me one. If this O.Movie Editor is good, then I'll try to learn more on using it. But if it's not, tell me one that is....

Thank you all for the support.

I just want to make movies with some pictures and stuff.



ieBrazil

---

### Post by renzokuken on 2008-11-21
try Kdenlive  ..... or Kino (but i think kdenlive is better

---

### Post by ieBrazil on 2008-11-21
and how to I get this one? add/remove thing?

---

### Post by renzokuken on 2008-11-21
System -> Admin -> Synaptic Package Manager

 or from the terminal

```
sudo apt-get install kdenlive
```

---

### Post by Ubuntiac on 2008-11-22
RE: Kdenlive

Please. Please. Please use the current version rather than the outdated, year old, SVN snapshot in the standard repos.

If you're on Kubuntu, you can add it from the Debian-Multimedia.org repositories. If you're on Ubuntu you just need to enable and update backports first. Yes, I'd rather we didn't have to enable backports either which is why it's worth adding your name to the packaging request in my signature.

---

### Post by mbellek on 2008-12-15
I am also trying to use Open Movie Editor & not doing very well...

It seems to edit the video & audio as separate tracks. I suppose this is cool if you want to set your video to music or something... But what if I just want the original audio that I recorded? 

Do I need to import that as a separate track, say, with Audacity or the sound recorder, and then use it as the audio track?

---

### Post by Ubuntiac on 2008-12-15
If you just want to edit audio, you're better off going with a dedicated audio editor. You could use Audacity, though personally I absolutely love Ardour. The only thing is that you usually need to convert your audio to wav's to use it first, which is easiest to do with Audacity.

---

### Post by mbellek on 2008-12-16
> **Ubuntiac said:**
> If you just want to edit audio, you're better off going with a dedicated audio editor. You could use Audacity, though personally I absolutely love Ardour. The only thing is that you usually need to convert your audio to wav's to use it first, which is easiest to do with Audacity.

No, see that's the thing. I JUST want to edit video. But I want it to have the same audio that it has when I recorded it. With Open Movie Editor, the audio track appears separate... If I just don't "mute original audio" will I be editing the audio track & video track simultaneously then?

---

### Post by Ubuntiac on 2008-12-16
What you're asking for sounds like Kdenlive's default behaviour. Import a video and you edit it's sound with it.

You then just drop any audio or video effects you want onto the one track, cut it up and move it around wherever you want it.

---

### Post by renzokuken on 2008-12-16
this appeared on tuxmachines.org today and thought it might be of help

[http://www.makeuseof.com/tag/7-free-open-source-video-editor-for-linux/](http://www.makeuseof.com/tag/7-free-open-source-video-editor-for-linux/)

---

