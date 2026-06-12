---
title: "Plugging in Maudio Delta Audiophile 2496 no workie &amp; kills Onboard sound"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by perixx on 2008-02-28
Hello...

I've got a Maudio Delta Audiophile 2496, which will not produce any sound and kills even the onboard-sound; Removing the card brings back the ADI AD1986A onboard sound.

I've tried to disable the soundchip before, but the 2496 won't work. Previously even compiled and installed the OSSv4 driver, which would only output the test sound and nothing more. 

I don't understand why having both sound devices in my system will produce a conflict - yes, maybe it's a hardware conflict. Or Ubuntu tries to automatically put the Maudio in charge of the playback at startup?

Anybody knows about a hardware conflict on Asus A8R-MVP boards with the onboard sound chip?

perixx

---

### Post by perixx on 2008-02-29
How can I use a PCI sound card and an onboard sound chip at the same time, without having them interfering each other?

perixx

---

### Post by klokwyze on 2008-03-31
I always disable the onboard sound on the computer tht my maudio 2496 is in.

BTW, I have gotten this to work, twice in Ubuntu, but I can't remember for the life of me exactly how I did it. I can only get it to output mono @ the moment.

:)

---

### Post by drsox1899 on 2008-04-14
Try looking at the Audio settings of your motherboard on BIOS bootup.  In my Asrock mobo for example, under the Auto setting, the on board audio disables if there is a sound card.  Reset the setting to Enable.

Have a look at the mobo manual  - yes -  RTFM !!

):P

---

### Post by perixx on 2008-04-16
> How can I **use** a PCI sound card and an onboard sound chip **at the same time**

Thanks for the tip, but I didn't intend to disable the onboard chip, as you can see. What I have in mind is, being able to use both sound devices in the same system, e.g. one linked to oss for headphones, the other one linked to alsa, for desktop speakers (as I can't see how to use both chips with alsa together).

With Feisty running, it wasn't possible to have ANY sound device functioning properly, as soon as I plugged in the PCI card - no matter if disabling either sound device via BIOS or not. With Gutsy, I seem to be able to have both plugged in and using one of them at least...

perixx

---

### Post by drsox1899 on 2008-04-27
> **perixx said:**
> Thanks for the tip, but I didn't intend to disable the onboard chip, as you can see. What I have in mind is, being able to use both sound devices in the same system, e.g. one linked to oss for headphones, the other one linked to alsa, for desktop speakers (as I can't see how to use both chips with alsa together).

With Feisty running, it wasn't possible to have ANY sound device functioning properly, as soon as I plugged in the PCI card - no matter if disabling either sound device via BIOS or not. With Gutsy, I seem to be able to have both plugged in and using one of them at least...

perixx

Read My Post !!!

---

### Post by perixx on 2008-05-21
Ah, yes. Sorry for that. But, as you might already guess, I haven't got that disabled in the Bios ;)

perixx

---

