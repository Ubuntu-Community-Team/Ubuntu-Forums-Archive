---
title: "Speakers on Eee 1005HAB won't shut up (8.04.4 LTS)"
date: 2010-02-16
forum: Hardware
---

### Post by Gullible Jones on 2010-02-16
After some time looking for a distro that fit my rather underpowered Eee 1005HAB netbook, I eventually settled on Ubuntu Hardy LTS, which is pretty much the only thing fast enough besides Windows XP. (Thank you very much KMS.) It works quite well... except for one nagging thing, which is that the speakers won't turn off. They have no controls in alsamixer, and just blast out whatever I have playing at max volume.

So of course I tried module settings. I set snd-hda-intel to model=asus, model=3stack, model=basic... None of them worked, the speakers just kept going.

For obvious reasons I can't just go through ever model... So can someone tell me what model my laptop is? The sound codec is ALC269, FWIW.

(And if there isn't anything specific for that model - are there other settings I should try messing with?)

P.S. I know this isn't a problem in 9.10. I'm sticking with 8.04.4 because 9.10 (and any other distro or version that uses kernel modesetting) performs horribly on this netbook (or any other Intel chipset machine).

---

