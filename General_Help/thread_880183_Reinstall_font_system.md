---
title: "Reinstall font system"
date: 2008-08-04
forum: General Help
---

### Post by KhipuX on 2008-08-04
Well I've been meddling with my desktop fonts for a while now in Slackware and got some nice results in KDE 3.5.9

So I thought I'd try them in Kubuntu 8.04.1 but it looks like I did something a little wrong. Does anyone know how to restore/reinstall the default font rendering system in Kubuntu like how it was when I installed for the first time?

I've tried changing things back and reinstalling Freetype but nothing is changing visually.

Thank you all.

---

### Post by kerry_s on 2008-08-04
how do we tell you how to undo what, when we don't know what you did?

---

### Post by KhipuX on 2008-08-04
Well thats kind of why I'm asking how to reinstall the font system - because I'm not sure what I've done that suddenly made my font rendering not work, especially as I followed detailed steps that I performed with Slackware KDE. I still have all of my fonts installed but reinstalling Freetype for instance hasn't changed anything.

So I suppose the question is which packages do I reinstall in Kubuntu to reset it's font rendering to the default method that is used when I first installed Kubuntu? And can these packages be reinstalled with the default values automatically from the Adept manager or do I have to reinstall from source code and try and work out Kubunutus default setup for font rendering?

My fonts are currently rendering like badly formed bitmaps with hinting that looks like My Little Pony hair.

---

### Post by kerry_s on 2008-08-04
i suppose the quick way would be> sudo apt-get install kubuntu-desktop
that will install everything that is a part of kubuntu desktop, which i'm sure includes fonts. but if your building from source or ran commands that /moved/replaced/deleted things it might not help at all.

other than that unless you tell use the detailed steps you took we could spend hours trying to guess.

if it's just some settings you did in the kde gui, than chances are if you delete the config files in your home directory, that's those hidden files(ctrl+h).

perhaps a screen shot of the problem fonts can help us see what is wrong.

---

### Post by KhipuX on 2008-08-04
Deleting hidden blighters and reinstalling Kubuntu-Desktop. I'll let you know what happens. Thanks

---

### Post by KhipuX on 2008-11-25
Whoops, didn't post back. Let me tell you what happened - well actrually nothing. I reinstalled Kubuntu-Desktop and the fonts stayed horrible. I ended up backing everything up and reinstalling from scratch. Fonts are back to normal but I still don't know how to repair the font system once it's broken.

---

