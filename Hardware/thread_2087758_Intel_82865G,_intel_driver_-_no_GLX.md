---
title: "Intel 82865G, intel driver - no GLX"
date: 2012-11-24
forum: Hardware
---

### Post by M0N74R0 on 2012-11-24
Hi,

I've got an older type PC that I've brought back to life with the help of Ubuntu.

I'm using Ubuntu 12.10

Machine works for the most part, however I had alot of issues with the graphics driver. I did google for a few days and try 101 solutions to the problem to no avail and just forgot about it until now.

Most things I tried did nothing, however one that did was using the nomodeset kernel option.

When using nomodeset, GLX worked fine, HOWEVER 2 things happened:

1. Unable to get resolution over 1024x768, which is bad because I have a widescreen display so everything was stretched.
2. All fonts were TINY! Like unreadable, and I had to (trickily!) make everything at LEAST size 40 to be similar to what it was before (at like size 10 or 11).

So I switched back to normal, without nomodeset.

What should I do? Try to get GLX working as it currently is, or try to resolve some of the resolution and font issues when using nomodeset?

Any advise, or solutions to either of the options?

I've been using Ubuntu for a very long time, and Debian before Ubuntu was spawned, but very rarely as a desktop environment, so this is somewhat new to me, plus everything seems to change so quickly.. last time I remembered, stuff was done in xorg.conf.. doesn't seem that way anymore.

Oh also, I'm already using the xorg-edgers PPA to get bleeding edge Xorg and driver updates, but unfortunately nothing has changed thus far.

I've tried with SNA on and off, neither make a difference.

Anyway,

Look forward to some ideas.

Kindest Regards,

Josh.

---

### Post by M0N74R0 on 2012-12-06
A quick update on this.

I noticed in my logs that I was getting corrupt EDID warnings. So today I switched out monitors (as I was using a cheap Palsonic LCD TV as a monitor) to a Philips 170S LCD monitor, while this didn't fix my GLX problems in itself, it did allow me to use "nomodeset" with satisfactory results.

Infact using nomodeset, seems to work exactly as it did without it, except that GLX now works fine.

So I'm guessing the crazy fonts and bad resolution I was getting with it before was just due to a corrupt EDID and Xorg couldn't probe it for details.

So I think its suffice to say, providing you don't have a corrupt EDID, that this issue in my case is fixed by using the "nomodeset" kernel option.

:)

---

### Post by Yellow Pasque on 2012-12-06
Thanks for providing a very good post with logs and everything. Please mark the thread solved, and hopefully, others with the same hardware/issue will find it.

---

### Post by PieterJ6 on 2013-01-05
Thanks!!! Your solution helped me to fix the following error on the same card. > X Error of failed request:  BadAlloc (insufficient resources for operation)

For those that arrive here in the future, you will need to use the xorg-edgers PPA to get bleeding edge Xorg and driver updates before setting the nomodeset (my boot freezed when setting the nomodeset before using the xorg-edgers' PPA).

And for those that don't know how to do the above

[LIST]
[*]Use the first solution [here]("http://askubuntu.com/a/41736") for the xorg-edgers PPA
[*]And [this]("http://askubuntu.com/a/38834") to set nomodeset temporarily (to test if it works) and the one below in to set in permanently .
[/LIST]

---

