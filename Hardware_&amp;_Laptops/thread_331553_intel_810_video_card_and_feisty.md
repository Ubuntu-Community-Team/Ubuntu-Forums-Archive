---
title: "intel 810 video card and feisty"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by GregWimmer on 2007-01-04
Back in edgy, I could install 915resolution
to get my laptop display and embedded intel 810 series video
card to give me the correct resolution.

I installed feisty, no such luck.

I don't see a 915resolution package for me.

I suppose the xorg-server-intel package is supposed
to do everything i want, but I see no way to properly set my resolution.

thanks for any help.

---

### Post by zachstruck on 2007-01-07
915resolution is in the "universe".  You need to add the [universe repository]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories").  Then you'll be able to "sudo apt-get install 915resolution" and everything should just work.

---

