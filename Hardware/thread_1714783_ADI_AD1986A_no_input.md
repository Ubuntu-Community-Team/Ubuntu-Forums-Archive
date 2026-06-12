---
title: "ADI AD1986A no input?"
date: 2011-03-25
forum: Hardware
---

### Post by J_Wales on 2011-03-25
I have ADI AD1986A chip on my motherboard. I get sound from the chip but no input... The mic just doesn't work. I can here static if I raise the volume and boost, but no sound from mic. I tried using the sound recorder as well but it records nothing, so mic input is not working for some reason. I have no idea how to further analyze this, my linux skills super limited, as in i'm a noob. Any one have any ideas or can help?

ubuntu 10.10
updated mar23
asus p5gv-mx motherboard

---

### Post by J_Wales on 2011-03-26
I found help in launchpad that solved my issue. Apparently the audio ports rear and front are not enabled simultaneously. The front audio ports were enabled by default and i found no way to change it to rear input, though the mic works in the front ports.

---

