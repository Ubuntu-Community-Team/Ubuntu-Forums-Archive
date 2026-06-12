---
title: "Where can i find drivers for the Creative Labs CT2980 Sound Card"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by Ryukenden on 2006-12-31
Where can i find drivers for the Creative Labs CT2980 Sound Card and how do i install them?

---

### Post by logos34 on 2006-12-31
I just had quick look [here]("http://www.alsa-project.org/alsa-doc/") but didn't see anything.  Couldn't find any mention of it at Creative Labs website.

Are you running ubuntu now?

If so you could try this in a terminal:

> lspci -n

Then copy and paste the output in the box [here]("http://kmuto.jp/debian/hcl/") and click 'check'.

Look for the line with audio controller.  If you're lucky the 'driver' column will show a module.  If not, then I don't know what to tell you.

Is this a pci or isa card?

---

### Post by Ryukenden on 2006-12-31
My card doesn't shows up in the page you've given.
The sound card is an old isa card.

---

### Post by logos34 on 2007-01-01
Maybe you're in luck.  Here is what it says on the [open source]("http://opensource.creative.com/soundcard.html") Creative page:

> "ISA Boards
All Creative ISA soundcards are supported using ALSA drivers. Most Linux distributions include these drivers, although some distributions may not automatically find your card."

So Ubuntu may include the driver but what it's called I have no idea.  To track down the name of the module you might start [here]("http://www.linux-drivers.org/audio.html").

---

