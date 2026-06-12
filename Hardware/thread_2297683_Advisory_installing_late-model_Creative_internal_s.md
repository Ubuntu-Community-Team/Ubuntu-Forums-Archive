---
title: "Advisory installing late-model Creative internal sound card(s)"
date: 2015-10-05
forum: Hardware
---

### Post by bcschmerker on 2015-10-05
In anticipation of new Challenges at SingSnap®, I installed a Creative Laboratories® SB1550 Audigy RX&#8482; PCIe 3.0 x1 audio card.  The snd-emu10k1 driver from the Advanced LinUX Sound Architecture Project gangs all three microphone inputs (viz., front Mic, rear Mic 1, and rear Mic 2) as a single feed to both Playback and Record/Stream mixers.  The Line In, on the rear panel, works as advertised; the Line2, Aux, and Aux2 positions are spurious, having no physical connections on this card.  ALSA Mixer controls everything as advertised, as was the case on the now failed SB0350 PCI 2.2 card.

[s]On the connection side, be advised that the SB1550 expects an AC '97 internal audio harness (I had the front headphone OK, but dead silence on rear Line Out 1) at a time when most sound cards use internal audio harnesses compliant with the Intel® High Definition Audio&#8482; standard.[/s]
***Update:**  I found that the external outputs for the SB1550 are controlled by the Analog/Digital Output Jack boolean.  The header is in fact wired to the Intel® High Definition Audio&#8482; standard, consistently with the SoundCore3D® products and a half-height planar-sound-chip-substitute card, the SB1570 Audigy FX&#8482; (which uses a Realtek ALC898 rather than a Creative Technology chip such as the CA10300-IAT or CA-0132).*

***Update2:**  Be further advised that ALSA misidentifies the SB1550, which uses the Creative Technology CA10300-IAT, as an SB0400 (Sound Blaster® Audigy 2&#8482; Value&#8482;).  The same problem occurs with the SB0610 Audigy 4&#8482;, which also uses the CA10300-IAT (the SB0400 uses the CA0108).*

---

