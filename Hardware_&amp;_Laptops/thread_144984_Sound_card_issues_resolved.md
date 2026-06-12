---
title: "Sound card issues resolved"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by Bidimus on 2006-03-15
I was on the virge of posting here with my difficulties getting my sound card working...  Since I got it working last night I instead decided to post my resolution in case it might help someone else at some point in the future...  I'll keep this brief...

I am a born again novice to Linux and a first time Ubuntu user...  I had just installed stock 5.10 Ubuntu...

The sound card detected as a CS4610/11 and it took manual intervention to get the CS46xx drivers to load...  This however didn't fix the problem...  After allot of research I began to suspect that the card was somehow being misidentified...   I then started looking at [http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/") for cards I suspected might be a closer match...  I used modprobe to manually load the suspected drivers as listed on the web site...  When I found a match the speakers came to life however it should be noted that the volume control in the GUI didn't work till I relogged...

Once I found the match I simply added the driver to /etc/modules and everything worked like a champ after that...

Hope this helps someone...

- Bidi

---

### Post by longship on 2006-03-29
You can identify your sound cards with the "lspci" command (from a root prompt).

```
lspci | grep audio
```

In my case it gives me:
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
05:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

```

This is my onboard nVidia nForce4 audio and my M-Audio Audiophile 2496 sound card.

Then, go to the ALSA sound card matrix and ID the card.

Sometimes it's helpful to find out the driver with Google.  E.G., if you have a specific chipset, google it and "alsa" and you'll generally find out the driver name.  For instance, googling "nforce4 alsa driver" gives me "intel8x0 - AlsaOpensrcOrg" as the first link.

By the way, AlsaOpenSrcOrg is a good ALSA site.
[http://alsa.opensrc.org/](http://alsa.opensrc.org/)

---

