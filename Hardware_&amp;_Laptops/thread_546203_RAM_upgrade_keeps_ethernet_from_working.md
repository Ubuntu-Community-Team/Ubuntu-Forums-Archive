---
title: "RAM upgrade keeps ethernet from working"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by FF_NoCortex on 2007-09-08
Dear all:

I ran into the following problem when I tried to upgrade the RAM:

Up to yesterday:

Machine: Dell C521 (with 512 MB RAM)
OS: Dual Boot Windows XP and Ubunt0 6.06 LTS

Everything works fine with both OS (including connection to internet through Belkin router).

Today: Replaced 512 with 2x 1 GB. 
Windows works fine, no problems.
Ubuntu starts up well (recognizes amount of RAM) but network interface does not work anymore, not even able to ping router.

When I remove the new memory and put in the old one (1x 512MB) everything is fine again.

Your kind help and support is greatly appreciated.

---

### Post by El Rogueo on 2007-09-08
Just some questions-

> **FF_NoCortex said:**
> 
OS: Dual Boot Windows XP and Ubunt0 6.06 LTS


Is there a reason you don't use Feisty 7.04? I'm pretty sure the upgrade process is non-invasive.

and

What kind of wireless interface do you have? Is it built in, or some sort of PCI/ISA slot card? Have you tried to use Ubuntu's autoconfiguration utilities, like the one in Setup?

---

### Post by FF_NoCortex on 2007-09-09
Dear El Rogueo:

Thank you very much for your kind interest and help. I took you suggestion and upgraded to Feisty 7.04. At this point, the network interface works with the additional RAM in place, but only if I choose:

Ubuntu, kernel 2.6.20-10-generic

I was thinking it would be better to use

Ubuntu, kernel 2.6.15-29-amd64-generic

for which the ethernet still doesn't work with the new RAM in.

I have to admit that I am actually not quite sure what the implications of choosing one or the other kernel is (besides that for the first one my ubuntu works now fine, including the ethernet).

To your question about the network interface: I was referring to the onboard ethernet interface (no wireless).

At this point I have a working solution thanks to your kind suggestion to upgrade. I would be very interested in any comments / answers to my - surely very naive - question about the two kernel versions.

Thanks!!!

Flavio

---

### Post by El Rogueo on 2007-09-09
> **FF_NoCortex said:**
> but only if I choose:

Ubuntu, kernel 2.6.20-10-generic

I was thinking it would be better to use

Ubuntu, kernel 2.6.15-29-amd64-generic



Without doing any serious research into the subject, I think it would be safe to assume that

a) kernel 2.6.20-xx is newer than 2.6.15-xx

therefore probably more stable and more effective, especially if it is made to work with multiple processor types (hence "generic")

b) you can always check by booting into ubuntu and run an update through the update manager. That (among other things) updates the kernel, and may give you a newer version of the amd64 specific kernel.

For the sake of asking, do you have an AMD 64bit processor? And did you install with the separate AMD64 install CD or the standard CD? If not, that might be something to look into.

Glad I could help. And it's not naive, because for the most part users don't know // don't care what the kernel does as long as the system works ;)

---

### Post by FF_NoCortex on 2007-09-09
Dear El Rogueo:

Thanks for your most kind reply. Thanks for your explanations. To your questions:

Yes, I have an AMD 64 processor and I originally downloaded and installed the amd64 specific version of 6.06.

The update manager tells me that my system is up-to-date, there are no further updates available.

I have been using the system since yesterday with this new update and my new ram and I am just very happy that everything works smoothly. Again, thanks for your help. This is my first time I posted something on a forum and I have to say that this was a very positive experience.

Thanks!

FF_noCortex

---

### Post by El Rogueo on 2007-09-09
Glad to be of assistance.

---

