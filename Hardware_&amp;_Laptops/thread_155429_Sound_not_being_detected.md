---
title: "Sound not being detected?"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by Gracye on 2006-04-05
I've been playing music in XMMS but everytime I start it up it says it can't detect my sound device.  How can I fix this?  It plays music after pressing play about 5 more times though.

---

### Post by FarEast on 2006-04-05
Hi Gracye;) ,

> It plays music after pressing play about 5 more times though.
Do you mean you can hear music(or something)?

I would like to know if your sound card is recognized by the system.
Does the command below show information of the sound card?
$ cat /proc/asound/cards

---

### Post by Gracye on 2006-04-06
yeah I can hear music when I click it 5 times.  Totem and Rhythym Box work fine

and no I can't get any information to show up with that :(

---

### Post by FarEast on 2006-04-06
OK...  it seems that your sound chip is not driven by an ALSA module but by an OSS module.  That's why the command 'cat /proc/asound/cards' shows nothing.

Give a try... open preferences(options) of XMMS and choose 'OSS Driver' as 'Output Plugin'.

---

