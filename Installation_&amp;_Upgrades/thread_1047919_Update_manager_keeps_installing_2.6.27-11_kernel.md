---
title: "Update manager keeps installing 2.6.27-11 kernel"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2009-01-22
Hi all,

I upgraded to the linux-image-2.6.27-11-generic (and headers) a while ago, but each time I run the Update Manager it keeps wanting to install these packages, along with a few others.  I allow it to do its thing, I reboot into the 2.6.27-11 kernel, and yet it tells me to upgrade again.

What can I do to stop this from occurring again?

Thanks!

---

### Post by Nixie Pixel on 2009-01-23
Anyone know why my package manager won't stop trying to upgrade my linux kernel?

---

### Post by RobSoko315 on 2009-01-28
I'm having the same problem

Anyone?

---

### Post by TruthOrDare on 2009-01-29
Same problem.

---

### Post by toscano on 2009-01-30
same problem

---

### Post by Lizzo on 2009-01-30
[FONT="Verdana"]ditto[/FONT]

---

### Post by edadasiewicz on 2009-01-30
Same here and it's also happening with the server kernel.

---

### Post by avtolle on 2009-01-30
[http://ubuntuforums.org/showthread.php?p=6644655#post6644655](http://ubuntuforums.org/showthread.php?p=6644655#post6644655) particularly posts #3 and #6; it appears to me that each update of the kernel is a fix to a problem resulting from an earlier release. If you check your installation log, you will note the different final "number". HTH.

---

### Post by zerted on 2009-01-30
They shouldn't be installing different updates with the same titles.

---

### Post by avtolle on 2009-01-30
Well, the main kernel hasn't changed; it is still 2.6.27.11, but the versions have changed; I think the last one I installed is 2.6.27.11-14.

---

### Post by TruthOrDare on 2009-01-31
The versions had changed, avtolle was correct.

Issue resolved (for me at least).

---

### Post by Nixie Pixel on 2009-01-31
They answered me in the main forum - I think they were valid updates...see here for the explanation:

[http://ubuntuforums.org/showthread.php?t=1049893]("http://ubuntuforums.org/showthread.php?t=1049893")

---

