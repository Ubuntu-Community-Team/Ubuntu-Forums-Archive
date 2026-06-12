---
title: "&quot;.Wapi?&quot; Intrepid Ibex"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-12-03
Can anoyone tell me what the folder .wapi belongs to?  It is in my home folder and is one of the hidden files-Is it necessary to a certain app and if so which one?  Can I delete it?  I am trying to clean up!  I tried to google it but nothing helpful came up and when I typed it into synaptic to locate it all that it cam up with is Wapiti-the vuln scanner.  Any help much appreciated!

---

### Post by theravenproject on 2008-12-03
Bump

---

### Post by ArchCorsair on 2008-12-03
If I were you, I probably wouldn't touch it; thinking it contains APIs to something. .wapi, the . in front just states it's a hidden folder.

---

### Post by gborzi on 2008-12-21
It's a directory used by mono, see [here]("http://pkg-mono.alioth.debian.org/cli-policy/ch-mono.html"). I asked myself the same question, and googling for an answer I found your question and some pages about this directory and mono applications, so I searched for "wapi mono" and got that result.

---

### Post by directhex on 2008-12-22
> **gborzi said:**
> It's a directory used by mono, see [here]("http://pkg-mono.alioth.debian.org/cli-policy/ch-mono.html"). I asked myself the same question, and googling for an answer I found your question and some pages about this directory and mono applications, so I searched for "wapi mono" and got that result.

Bingo.

Mono uses the ~/.wapi folder to track shared file mutexes. Try running an app like Banshee or Tomboy to see files created in that folder - try running "mono --wapi=hps" to get a human-readable version of the contents

---

