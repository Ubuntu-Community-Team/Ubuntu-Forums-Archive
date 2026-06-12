---
title: "Evolution composer cursor problem"
date: 2008-09-04
forum: General Help
---

### Post by Nisuspi on 2008-09-04
Hi all,

I'm hoping someone can help me with an annoying bug. I've just made the leap to Ubunutu and switched my PIM from Outlook to Evolution, and I love it. 

The only problem I have is that when composing mails - especially replies - the cursor doesn't seem to refresh the text editor properly. It leaves artefacts below text and if you move it backwards leaves a copy of itself behind it. 

This doesn't happen in any other text editor I'm using, all I can think of is that I must have changed the fonts at some point and can't get them back. 

Can anyone help?

---

### Post by reiklen on 2008-09-05
I have the exact same problem. I haven't been able to find anything related to this topic so far but then again I'm not really sure how to search for it. Does anyone know how to fix this, it can be quite annoying at times.

---

### Post by Nisuspi on 2008-09-05
I'm wondering if there's a way to force Evolution to use OpenOffice as its text editor to get around it. Seems a bit extreme though...

---

### Post by driebel on 2008-09-29
Exact same issue here.  Unfortunately, as a super-newbie, I don't have much useful to contribute, except a new reply to bump this thread.  Anyone smart have an idea?

---

### Post by wulfhound on 2008-11-01
I also have this problem. It makes the emails hard to edit because if you move it, you have up to 10 cursor artifacts at a time on the screen. Also makes the email hard to read....

There has got to be someone that can fix this. It's terrible!

---

### Post by Nisuspi on 2008-11-02
I've done a /lot/ of research on this one and as far as I can tell, it's a graphics driver issue - possibly specific to the Nvidia 8xxx series and later cards.

Upgrading to Intrepid made the problem worse for me, as the cursor ghosting began to affect OpenOffice docs too. 

There's several fixes suggested, including installing latest NV drivers, but the one that seemed to do it for me was to change the refresh rate in CompizConfig>General Options>Display Settings. For some reason this was set to 50Hz while every other refresh tag (in xorg and nv driver) was 60Hz. Setting the refresh rate to 60Hz in Compiz too seems to have solved the problem for me.

Hope it works for you too!

---

### Post by krims0n on 2008-11-04
I also had this issue. Setting the refreshrate to 60hz did not work, however the fix for me was to enable Loose Binding in Compiz Options. Right click on the compiz fusion icon and you will find this setting. Cursor in Evolution works fine now, and this also fixed a rendering issue I had in urxvt.

---

### Post by Stunts on 2008-11-06
Hi I have the exact same problem, but none of the above fixes worked for me.
Any more ideas?
I'm using a nVidia 8600M GT here.
Thanks

---

### Post by Stunts on 2008-11-06
Nevermind, problem solved after a restart!
Thank you for your suggestions.

---

### Post by wulfhound on 2008-11-12
> **krims0n said:**
> I also had this issue. Setting the refreshrate to 60hz did not work, however the fix for me was to enable Loose Binding in Compiz Options. Right click on the compiz fusion icon and you will find this setting. Cursor in Evolution works fine now, and this also fixed a rendering issue I had in urxvt.

Just to let others know,I had this issue even before Compiz Fusion was installed. Also, even with loose binding, I still have it after a restart.

---

### Post by vdoki on 2009-04-05
Hi, I had the same problem (with nvidia 8400M + compiz). Evolution is fine now, after that I have installed jaunty and 180 nvidia driver. 

Although I have a problem with openOffice now. If I page down a few times, and then back up, only the active column is refreshed, the others not.

---

