---
title: "Lumix camera support broken - again!!!"
date: 2008-06-25
forum: Hardware
---

### Post by igoddard on 2008-06-25
Lumix camera support worked in Edgy and was broken by Feisty, then fixed.

I've just tried connecting my camera for the first time since upgrading to Hardy and, yet again, it's broken.

There's currently a bug report open against a similar problem with an Olympus camera and a comment in that discussion says that Lumix support is now broken in Gutsy as well.

Oh well, at least my current laptop has a built-in card reader so this time I'm not completely stuck.

But why oh why do we keep getting this situation where a Linux upgrade breaks something that was working?  Is it poor version control allowing old bugs to be re-released or an uncontrolled itch by devs to fix what wasn't broken and then release it without testing?

Ian

---

### Post by chewearn on 2008-06-26
I think this could be a case of poor developers, who do not have the cameras in question, to be able to test it before a release.

I humbly request that you take matter into your own hands, download the latest development version (Intrepid Ibex at this time), install it, test your camera, file the bugs you find.

Your contribution will be very much appreciated, thank you.

---

### Post by igoddard on 2008-06-26
> **AstalaVista said:**
> I think this could be a case of poor developers, who do not have the cameras in question, to be able to test it before a release.

I humbly request that you take matter into your own hands, download the latest development version (Intrepid Ibex at this time), install it, test your camera, file the bugs you find.

Your contribution will be very much appreciated, thank you.

This poor user can't afford a second laptop to test development versions of S/W.  His only laptop is a production box.  That's why he prefers to use the LTS versions.

In any case a bug has already been logged - as long ago as April - and from the discussion on the bug thread it's not just one make of camera affected let alone one model.

Yes, pre-test release of hardware dependent code is problematic.  It means that the development team needs to have access to a team of testers who do have a variety of H/W so that testing does get done thoroughly before release.  And if the release turns out to break a lot of existing working cases it should be backed out PDQ whilst it's being fixed.

We complain of M$ using users as involuntary beta testers but ISTM that this is far too frequent in our world as well.  Look down this forum.  You'll find problems with updates and upgrades breaking wireless and graphics.

Ian

---

