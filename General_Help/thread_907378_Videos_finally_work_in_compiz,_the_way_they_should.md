---
title: "Videos finally work in compiz, the way they should."
date: 2008-09-01
forum: General Help
---

### Post by vikrant82 on 2008-09-01
I don't know how long this has been happening on Intrepid. But I just happened to rotate my cube with Videos running and I was amazed to see that the familiar blueness with videos and compiz is no longer there. Have a look at screenshot to see what i am referring to .. Videos, now work in perfect harmony with Compiz and I can finally see the videos through my transparent terminals or zoom them or see through them.

Remember all those, "TTM buffer failed to initialize...". I am sure this means a lot more to graphics on Linux.

I am really happy, and congratulate all those behind this.

:)

---

### Post by sayakb on 2008-09-01
Hello Vikrant, Do you have an Intel onboard graphics? In that case, switching to X11 mode in VLC (Settings->Preferences->Video Modes->Output Modules) would make the video integrate with Compiz. While, using OpenGL mode (which produces a smoother output) gives the blue screen.

---

### Post by vikrant82 on 2008-09-01
Yes, But this is on 'xv' mode. I am sure this never used to happen in xv mode.

---

### Post by sayakb on 2008-09-01
Sometimes Output modes automatically change. X11 mode *does* integrate with compiz, but the output is often choppy and pixelated.

---

### Post by empty_spaces on 2008-09-02
@LinuxIsInnovation,
I have X3100 Intel graphics and your directions worked great for me. No more blue screen on the cube for me.

---

### Post by sayakb on 2008-09-03
> **empty_spaces said:**
> @LinuxIsInnovation,
I have X3100 Intel graphics and your directions worked great for me. No more blue screen on the cube for me.
  
Glad I could help! :)
Though, FYI, X11 Video output uses a bit more system resources and is bad for small (flv) videos. On my laptop (with a GMA950), I have set VLC on X11 and Totem on the usual output mode. So I play the low quality vids on totem and others on VLC.

---

### Post by vikrant82 on 2008-09-04
Isn't this part of new features that have gone in latest mesa and xserver updates. I was thinking that this started happening because of textured videos or something? 

By the way, I can put videos on cube in nearly all modes, xv, x11 etc.

---

