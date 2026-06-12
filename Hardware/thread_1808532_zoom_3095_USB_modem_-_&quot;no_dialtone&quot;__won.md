---
title: "zoom 3095 USB modem - &quot;no dialtone&quot; / won't actually dial"
date: 2011-07-20
forum: Hardware
---

### Post by Frymaster on 2011-07-20
Hi,

I'm trying to use a zoom 3095 USB modem to set up a fax/voicemail service for someone.

I installed the driver from linuxant without a problem, and fax software can talk to it fine. (Send AT commands, receive answers etc.)

However, if I try to send a fax via efax, it reports "no dialtone".

If I add the AT command "X3" to the init string (to disable dialtone detection), then it says it's dialing, and the speaker even emits dialing tones, but, if I listen in on the line via a handset, I can't hear the tones on the line.

I've tried using it on my windows laptop; it can dial just fine from there (same phone line and connections).  Is there some init string I need to add to the defaults, or is the driver screwy or something even wierder?

---

