---
title: "Another day -- Another Ubuntu bug, this time with printing."
date: 2010-08-28
forum: Hardware
---

### Post by dE_logics on 2010-08-28
Small bugs here and there, ok, bearable but this one is major!

OOo draw/writer does not support borderless printing, Ok, this might be a bug with writer... it doesn't do borderless anywhere but draw can produce borderless.

I suspect CUPS to be the culprit since there's no option for borderless A4, apart from this, the other options are also confusing... instead of getting 3 color modes as in Gentoo, there is none on Ubuntu CUPS.

I'm not able to specify the media type in Ubuntu as I can in Gentoo. In Ubuntu it's always autoselect. This might not be an issue anyway.

Print quality is missing in CUPS web UI.

All these missing options have been integrated into a single 'printout mode' which makes things too confusing and the options are less.

In OOo, I get to specify the printing quality with around ~10 options instead of 5 in Gentoo (color, draft, fast draft, high quality grayscale, and line only B&W). The 10 options in Ubuntu include 300 and 600 dpi varients, overall it looks pretty confusing.

I doubt this is cause of version mismatch, Gentoo is using CUPS 1.4.4 and Ubuntu 1.4.3; but again 0.0.1 difference should not matter much.

Anyway, I need to solve the borderless issue currently.

---

