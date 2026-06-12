---
title: "Sapphire HD 7750: 3 monitors"
date: 2012-09-23
forum: Hardware
---

### Post by Jeroen De Dauw on 2012-09-23
I'm thinking of buying a new box with a **Radeon HD7850** (title is incorrect) card. One of my requirements is that it will support 3 monitors (using Ubuntu 12.04). I've been trying to find a conclusive answer for the last half hour to no avail. So my question is rather simple: does this card support 3 monitors using Ubuntu? And if it does, what funky cables do I need (if any).

---

### Post by Warpcore1701 on 2012-10-10
To answer your question first: It depends on the available interfaces on your monitors. If you are planning to use DVI for all 3 monitors (which I did), you will need a DisplayPort to DVI adapter and an HDMI to DVI adapter (or cable) since this card only offers 1 DVI out, 1 DisplayPort, and 1 HDMI out.

I just tried the above mentioned card on Ubuntu 12.04 with 3 monitors. Unfortunately I wasn't able to set up all 3 monitors using the ATI catalyst driver. 

A setup with 2 monitors is working flawless. But every time I'm trying to activate the 3rd monitor in the Catalyst administration center, I would get a "not enough graphics memory available" error (German translation, actual error message in English might differ), and the 3rd monitors is set back to inactive in the CCC.

If anyone managed to set up a 3 monitor desktop with this card, it would be awesome to hear how this was done.



Edit: Just saw that your title was incorrect and you were asking for another card. My answer applies to [B]Sapphire HD 7750




Edit2: Might also be interesting for you: After a lot of googling I'm pretty sure, I have the wrong DisplayPort to DVI adapter installed. In order to run 3 monitors using Sapphires "Eyefinity" technology at least one of your monitors _[COLOR=Red]MUST[/COLOR]_ support DisplayPort. If, like in my case, none of you monitors supports DisplayPort you will have to use an [COLOR=Red]_ACTIVE_[/COLOR] [B] DisplayPort to DVI adapter (I currently have a passive adapter) to make this work. I just ordered one on Amazon and will get back with the results.


Edit3: Success ! After connecting the active [B][B] DisplayPort to DVI adapter I just had to activate the 3rd monitor in the system settings, and now it's all working.
[/B][/B][/B][/B]

---

### Post by sola on 2012-11-24
> **Warpcore1701 said:**
> To answer your question first: It depends on the available interfaces on your monitors. If you are planning to use DVI for all 3 monitors (which I did), you will need a DisplayPort to DVI adapter and an HDMI to DVI adapter (or cable) since this card only offers 1 DVI out, 1 DisplayPort, and 1 HDMI out.

I just tried the above mentioned card on Ubuntu 12.04 with 3 monitors. Unfortunately I wasn't able to set up all 3 monitors using the ATI catalyst driver. 

A setup with 2 monitors is working flawless. But every time I'm trying to activate the 3rd monitor in the Catalyst administration center, I would get a "not enough graphics memory available" error (German translation, actual error message in English might differ), and the 3rd monitors is set back to inactive in the CCC.

If anyone managed to set up a 3 monitor desktop with this card, it would be awesome to hear how this was done.



Edit: Just saw that your title was incorrect and you were asking for another card. My answer applies to [B]Sapphire HD 7750




Edit2: Might also be interesting for you: After a lot of googling I'm pretty sure, I have the wrong DisplayPort to DVI adapter installed. In order to run 3 monitors using Sapphires "Eyefinity" technology at least one of your monitors _[COLOR=Red]MUST[/COLOR]_ support DisplayPort. If, like in my case, none of you monitors supports DisplayPort you will have to use an [COLOR=Red]_ACTIVE_[/COLOR] [B] DisplayPort to DVI adapter (I currently have a passive adapter) to make this work. I just ordered one on Amazon and will get back with the results.


Edit3: Success ! After connecting the active [B][B] DisplayPort to DVI adapter I just had to activate the 3rd monitor in the system settings, and now it's all working.
[/B][/B][/B][/B]

Great to know that this card works well with several monitors.

I am building a developer workstation with this card and wanted to know if it is supported well under Ubuntu. Now I can relax :)

---

