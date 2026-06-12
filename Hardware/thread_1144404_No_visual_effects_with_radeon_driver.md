---
title: "No visual effects with radeon driver"
date: 2009-04-30
forum: Hardware
---

### Post by MadJester on 2009-04-30
I was using the fglrx driver, but it would lock the system when I tried to go full screen with video.  When I switched to the radeon driver it disabled all of the visual effects.  Can I add some options to the generic xorg.conf that the radeon driver uses to enable this capability?  Or is this a problem with the radeon driver and my card?

lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

---

### Post by MadJester on 2009-04-30
I went back to the fglrx driver.  Turns out that full screen video doesn't lock up if I turn off the visual effects.

Still interested in knowing why the radeon driver doesn't support them on my card.

---

### Post by myk02k on 2009-08-27
I have the Mobility Radeon HD 4500 Series (4570) card in my Satellite A505.  Although there are many issues with video playback that I am trying to work out, I can confirm that the fglrx driver supports advanced visual effects with compiz-fusion.  The original driver in which Ubuntu used for my card did not support advanced visual effects, although it appears as though there are 3 drivers available for Radeon cards.  Are you sure everything is installed properly using jockey-gtk?

---

