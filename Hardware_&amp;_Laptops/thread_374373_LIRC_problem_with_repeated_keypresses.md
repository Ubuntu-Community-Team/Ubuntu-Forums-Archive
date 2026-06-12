---
title: "LIRC problem with repeated keypresses"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by speedsix on 2007-03-02
For some reason lirc seems to be receiving repeated keypresses from my remote.  If I run IRW I get 4-5 repeated keys for each press. Strange thing is, I actually have 2 remotes, one is the original that came with the tv-card (Hauppauge Nova-T pci) which doesn't repeat presses, second is a Logitech Harmony 'multi' remote which does have the problem.

My other devices, tv/amp etc, don't act like they're recieving mulitple presses from the Logitech and I can't find any options for the Logitech that could affect this. It worked fine before also. I've also tried changing the repeat option in my .lircrc file but this doesn't help.

I start lircd with the following;

lircd -l --driver=dev/input --device=/dev/input/irremote


Any ideas?

---

