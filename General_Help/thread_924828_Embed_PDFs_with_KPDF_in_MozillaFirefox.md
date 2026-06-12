---
title: "Embed PDFs with KPDF in Mozilla/Firefox"
date: 2008-09-19
forum: General Help
---

### Post by oygle on 2008-09-19
I use GNOME and was having problems with viewing PDF's with Firefox/Evince. Noticed [this post]("http://ubuntuforums.org/showthread.php?t=25685") on how to embed Evince in Firefox, and then discovered KPDF, which is a much better PDF viewer.

I have installed mozplugger , and now get mixed results. Sometimes when viewing a PDF, KPDF is embedded within Firefox, other times it downloads the file and then opens Evince.

I tried to uninstall Evince, as I prefer KPDF, even though I run GNOME. But the 'add/remove' said there were applications which depended upon Evince, and so I had to do it via Synaptic. Haven't done that yet.

Also, I haven't as yet, modified the file in /etc/mozpluggerrc

So, I would like to be able to view (embed) any PDF within Firefox, using KPDF.

1.  Will it be okay to remove Evince via Synaptic ?
2.  Will applying the mods to /etc/mozpluggerrc as outlined in that thread, fix this problem ?

Oygle

---

### Post by oygle on 2008-09-20
> **oygle said:**
> 2.  Will applying the mods to /etc/mozpluggerrc as outlined in that thread, fix this problem ?


Seems like I won't need to, the file already has code for Evince and KPDF

```
repeat noisy swallow(evince) fill: evince "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	
```

---

### Post by oygle on 2008-09-20
Tried opening a few different PDF's , and they were all embedded with Evince within Firefox. No doubt if I swap these 2 lines ..

```
repeat noisy swallow(evince) fill: evince "$file"
repeat noisy swallow(kpdf) fill: kpdf "$file"

```

to become ..

```
repeat noisy swallow(kpdf) fill: kpdf "$file"
repeat noisy swallow(evince) fill: evince "$file"

```

KPDF should be the one that is embedded. Much later, ..yes, that did the trick, now KPDF is embedded within Firefox for all PDF's that are viewed.

---

