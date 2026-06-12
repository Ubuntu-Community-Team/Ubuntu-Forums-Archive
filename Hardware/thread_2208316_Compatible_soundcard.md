---
title: "Compatible soundcard"
date: 2014-02-27
forum: Hardware
---

### Post by motorcity909 on 2014-02-27
Hi all

I'm looking at getting a dedicated internal soundcard and wondered if anyone had recommendations of models that just work with (X)Ubuntu?

The one I'm looking at is the [Asus Xonar DGX]("http://www.overclockers.co.uk/showproduct.php?prodid=SC-015-AS") but I'm open to other ideas.  I'm not bothered about spacey 7.1 surround sounds, the card just has to drive 2.1 Logitech speakers & subwoofer.

My motherboard has two PCI Express slots.

Cheers as always.

Dave

---

### Post by Yellow Pasque on 2014-02-27
I have the PCI (non Express) version of the DGX (the Xonar DG). The analog output works well, and sounds better than onboard, especially on decent headphones, but if you have crappy Logitech speakers, don't be surprised if you can't hear a huge difference from onboard.

For a long time, the input/microphone and front headphone jacks were not functioning ( [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/919809](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/919809) ), but that may have changed in kernel 3.14 with recent patches: [https://github.com/torvalds/linux/commits/master/sound/pci/oxygen](https://github.com/torvalds/linux/commits/master/sound/pci/oxygen)

If you want, I can dig out my DG and test the headphone jack, but I don't have a mic to test with.

---

