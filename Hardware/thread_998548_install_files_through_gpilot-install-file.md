---
title: "install files through gpilot-install-file???"
date: 2008-11-30
forum: Hardware
---

### Post by shane2peru on 2008-11-30
Ok, I know I have done this in the past, but for the life of me I can't remember the trick.  I want to install files directly to my Palm Pilot.  I don't want to put them on my SD card.  I know this can be done, the name of the app is gpilot-install-file I tried the --now option and the --later option.  Neither seems to work.  I think there is a folder where these files should be put so that they will be installed at the sync time.  I really don't remember and the man page is very generic in it's description.  Any help on this would greatly be appreciated.

Shane

---

### Post by LianerGoist on 2008-12-29
> **shane2peru said:**
> Ok, I know I have done this in the past, but for the life of me I can't remember the trick. 
Shane

Same problem here. It used to work, but now it doesn't. Broken? Or have I also forgot something important?


Thomas

---

### Post by LianerGoist on 2008-12-29
> **LianerGoist said:**
> Same problem here. It used to work, but now it doesn't. Broken? Or have I also forgot something important?

Okay, I found the problem - the ID of the Palm was set to 0 by default, and I accepted that. But it doesn't work! I believe it used to be set to 1000 by default, and changing the value fixed the problem.

---

