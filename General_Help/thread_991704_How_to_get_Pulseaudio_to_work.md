---
title: "How to get Pulseaudio to work?"
date: 2008-11-24
forum: General Help
---

### Post by DrIdiot on 2008-11-24
I have two sound cards, a built in motherboard one and a PCI sound card.  Pulseaudio sees both (theyre both listed as sinks), but it only outputs sound to one of them (the built in motherboard one).  

when I monitor the volume using Pulseaudio, and set Ubuntu to output to ESD, it will output sound to the PCI sound card.
when i set Ubuntu to output sound to PulseAudio, then it will output sound to the built in motherboard card

why is this?  my sound card is CA0106


Edit: sorry, i fixed it.  see [http://ubuntuforums.org/showthread.php?t=725764](http://ubuntuforums.org/showthread.php?t=725764)
this should be a bug?

---

### Post by psyke83 on 2008-11-24
> **DrIdiot said:**
> I have two sound cards, a built in motherboard one and a PCI sound card.  Pulseaudio sees both (theyre both listed as sinks), but it only outputs sound to one of them (the built in motherboard one).  

when I monitor the volume using Pulseaudio, and set Ubuntu to output to ESD, it will output sound to the PCI sound card.
when i set Ubuntu to output sound to PulseAudio, then it will output sound to the built in motherboard card

why is this?  my sound card is CA0106


Edit: sorry, i fixed it.  see [http://ubuntuforums.org/showthread.php?t=725764](http://ubuntuforums.org/showthread.php?t=725764)
this should be a bug?

Using the PulseAudio Device Chooser is an obsolete method. It's much easier to use the PulseAudio Volume Control applet (you can right-click on the Output Device and assign it as the default).

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

