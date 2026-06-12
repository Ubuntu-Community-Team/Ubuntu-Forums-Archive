---
title: "KMail crashes after update when trying to attach a file"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Guru_Mediation on 2009-02-25
Hello,

three days ago the Ubuntu server proposed me an update for Kontact which I installed. It works quite well besides that, when I try to attach a file to a mail, Kontact crashes.

After clicking on 'Attach' the file requester appears. Then Kmail instantly crashes when I click on a file or after a few seconds if I do nothing.

I have installed Ubuntu Intrepid Ibex (german version), Kontact in version 1.4, the version number of KMail is 1.11.0. System is an AMD X2 3800 SFF, ASUS M2A-VM, chipset AMD690 G

If I run KMail in the command shell I get the following error message:


```
*** KMail got signal 11 (Crashing)
Keyresolver: empty format info
Format for openpgp info / mime:
   Signing keys:
   Split Info # 0 encryption keys:
   Split Info # 0 recipients:
Format for openpgp info / mime:
   Signing keys:
   Split Info # 0 encryption keys:
   Split Info # 0 recipients:
Format for openpgp info / mime:
   Signing keys:
   Split Info # 0 encryption keys:
   Split Info # 0 recipients:
Format for openpgp info / mime:
   Signing keys:
   Split Info # 0 encryption keys:
   Split Info # 0 recipients:
Format for openpgp info / mime:
   Signing keys:
   Split Info # 0 encryption keys:
   Split Info # 0 recipients:
Format for openpgp info / mime:
   Signing keys:
   Split Info # 0 encryption keys:
   Split Info # 0 recipients:
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) "HDA ATI SB (ALC883 Analog)"
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) ( "unix: / tmp / pulse-user / native alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0")
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) SetProperty (device, "unix: / tmp / pulse-user / native
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 ") failed
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) "HDA ATI SB (ALC883 Analog)"
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) ( "unix: / tmp / pulse-user / native
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 ")
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) SetProperty (device, "unix: / tmp / pulse-user / native
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 ") failed
virtual bool Phonon:: Gstreamer:: Audio Output: setOutputDevice (const Phonon:: Audio Output Device &) "default"

```

Now and then I get a requester that informs me that KMail has crashed and the reference SIGSEGV.

I already googled this error, but unfortunately found nothing.

Thanks for your help in advance!

Thorsten

P.S. I hope I found the right category for my question

---

