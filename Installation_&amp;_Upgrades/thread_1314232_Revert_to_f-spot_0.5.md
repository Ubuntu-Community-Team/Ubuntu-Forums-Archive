---
title: "Revert to f-spot 0.5"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by simon303 on 2009-11-04
When I upgraded to 9.10 f-spot was upgraded to version 0.6, but there are issues with this version and my camera. Specifically it "Cannot lock device" when trying to import photos from it.

Can I revert to version 0.5 until 0.6 works with my camera? I tried installing the package from the packages site, and after resolving many dependency issues it crashed the moment I went to preferences.

---

### Post by bruno9779 on 2009-11-04
> **simon303 said:**
> When I upgraded to 9.10 f-spot was upgraded to version 0.6, but there are issues with this version and my camera. Specifically it "Cannot lock device" when trying to import photos from it.

Can I revert to version 0.5 until 0.6 works with my camera? I tried installing the package from the packages site, and after resolving many dependency issues it crashed the moment I went to preferences.

That is a bug that 0.5 had for me too. always crashed on my wife's laptop when opening preferences, but it never happened on my desktop.

Check [here]("https://launchpad.net/ubuntu/+source/f-spot") for all the ubuntu packages available. Maybe you could try installing the latest 6.1.4, that is still a proposed update, that MAY fix your issue.

otherwise I'd "simply" compile from source the version I prefer.

post back if you need any help with compiling

---

### Post by simon303 on 2009-11-04
I've tried updating to 0.6.1.4, but I still get the original error.

I have also previously tried just installing the old version, but that ran into problems.

Could you explain how to compile from source? I've tried it before with something else, but didn't have much luck. I seem to remember having to install some C developers kit or something, but can't remember what.

---

