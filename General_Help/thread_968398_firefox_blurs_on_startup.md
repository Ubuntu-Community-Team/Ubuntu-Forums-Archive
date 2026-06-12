---
title: "firefox blurs on startup"
date: 2008-11-02
forum: General Help
---

### Post by pjizz on 2008-11-02
Just updated to 8.10 and am having a weird issue everytime I load up Firefox.  The screen looks all crazy for a second or two.  Hard to explain so I took a snapshot...

Anyone had any similar experiences?  Suggestions?


Thanks

---

### Post by mdurham on 2008-11-02
Other people have this problem too. I think it's been reported as a bug.
BTW it's not only Firefox that has this, all windows seem to be affected to some degree. I see it on menus also.

---

### Post by pjizz on 2008-11-02
hmm...interesting.  thanks for letting me know.  so far (knock on wood) it's only happened to me with FF...

---

### Post by trpnblies7 on 2008-11-02
I'm having this same problem, too. I'd love to know what's causing it. Disabling addons or starting in safe mode doesn't make a difference.

---

### Post by caro on 2008-11-02
> **mdurham said:**
> Other people have this problem too. I think it's been reported as a bug.
BTW it's not only Firefox that has this, all windows seem to be affected to some degree. I see it on menus also.

I've seen it on Thunderbird too, not just FF.  Weird, but it doesn't seem to cause any other problems.

---

### Post by frankelr on 2009-01-15
I don't know how to fix it, but I can tell you that the firefox window is opening BEFORE the program writes into display memory.  What you are calling a "blur" is just the leftover contents of that block of display memory showing whatever it housed before. Some windows programs use a fixed display on startup to avoid this problem  Maybe Ubuntu is just to fast.  Now all we need is for someone to find a workaround.

Bob

---

### Post by solwic on 2009-01-15
Do you have an ATI video card?

I get this problem with Firefox only, when I have desktop effects enabled.  Since I have an ATI card, the effects are messed up, and the Firefox window blurs like that every time before clearing up on its own.  If your effects are enabled, try turning them off and then try firefox again.  

If it's not that, probably some video rendering issue.  

Wish I could be more help.

---

### Post by HyperHacker on 2009-01-15
Yeah, all it's doing is displaying what was in video memory before, because the program didn't get around to drawing something there before it was displayed. Any program that doesn't redraw fast enough will do that. (Happens for me on an NVidia card too.) While not a big deal, I think it could be a potential security/privacy issue. Sometimes I'll open up Firefox and for a second or two it'll show the last image I had open in Geeqie or Gimp, or the page I was browsing last time I closed Firefox, or a document I had open in OpenOffice, etc. Someone could open a program and see private things you were working on in another program before you left.

I think the simplest solution is to just wipe out the video memory a program was using when it's deallocated.

---

### Post by solwic on 2009-01-15
> **HyperHacker said:**
> Yeah, all it's doing is displaying what was in video memory before, because the program didn't get around to drawing something there before it was displayed. Any program that doesn't redraw fast enough will do that. (Happens for me on an NVidia card too.) While not a big deal, I think it could be a potential security/privacy issue. Sometimes I'll open up Firefox and for a second or two it'll show the last image I had open in Geeqie or Gimp, or the page I was browsing last time I closed Firefox, or a document I had open in OpenOffice, etc. Someone could open a program and see private things you were working on in another program before you left.

I think the simplest solution is to just wipe out the video memory a program was using when it's deallocated.

Not to be contrary, but I still recommend turning off the desktop effects and seeing if it fixes it.  I'd bet the effects are the culprit, and...well, I'm curious to know, because it stopped doing it to me when I shut them off.  

Trying to confirm my hypothesis, I guess.  :P  

Manually clearing the video memory after closing every program seems a bit much.  Shouldn't the program do that itself?

---

