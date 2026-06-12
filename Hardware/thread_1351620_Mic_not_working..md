---
title: "Mic not working."
date: 2009-12-10
forum: Hardware
---

### Post by mbrowning2000 on 2009-12-10
Hi Guys,

   I just installed a New Sound Card, and everything works except my Mic. When I go to **(System>Preferences>Sound)** to test it I get This:

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'.

The sound card is a C-Media CM8738.

Please Help, I need my Skype lol

---

### Post by HappyFeet on 2009-12-10
Right click your speaker icon and go to preferences and make sure all the settings are correct.

---

### Post by kk_furtiva on 2010-02-04
I had the same problem. I fixed this way:

1) open "alsamixer"
2) go to "Mic-In Mode" bar
3) check that in "Item" (top-left corner), it reads "Mic-In Mode [Mic-In]"
4) If not (probably "Mic-In Mode [Center/LFE Output]") hit up/down arrow keys until "Mic-In Mode [Mic-In]" is selected.
5) Check that mic is not muted. Go to "Mic" bar and check that it is not muted "Mic [Off]". If it is, hit M key, you'll get "Mic" only.

That should be it. The problem is that this on-board sound card is surround and, when in surround mode, the mic mini-plug input becomes Center/LFE output.

---

