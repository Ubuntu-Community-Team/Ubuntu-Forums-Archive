---
title: "tpb update is wonky"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by SacredChicken on 2005-04-08
I'm running Hoary on a Thinkpad T23. I had tpb (which allows you to attach functionality to the special Thinkpad keys and also to see an on-screen display when you change the volumne/thinklight/screen brightness) all happy and running. Yesterday there was an update to tpb. This confused me since I was pretty sure there hadn't been a new version since last year some time but, trusting my faithful Ubuntu package maintainers I applied it. Now I've lost my on-screen-display! The key mappings still work but I don't get my useful little messages when I change things anymore. Even more curious, the program itself seems to no longer recognize the command line arguments relating to the OSD, though the man page remains unchanged.

This is hardly an urgent matter but I miss seeing "Thinklight on" and "Thinklight off." It was so reassuring. Have any other Thinkpad users noticed the change? Is there a good way for me to revert back to before the update when life was better? (having seen it suggested in other threads, I looked for the Force Version option in Synaptic but it was greyed out...and anyway, I don't think the version number actually changed :-s )

---

### Post by rigga on 2005-04-08
Ive noticed this too, anyone have any fixes for this???

---

### Post by nullGambit on 2005-04-09
Yes, I have the same problem.  tpb works, but without onscreen display.  Hope someone can provide a fix...

---

### Post by thepoch on 2005-04-11
Adding a me-too post. tpb no longer works properly with Hoary.

---

### Post by Michael R Head on 2005-04-12
It turns out that the ubuntu packager disabled xosd support in the latest build. Here's the info from the changelog: [http://packages.ubuntu.com/changelogs/pool/universe/t/tpb/tpb_0.6.3-1ubuntu1/changelog](http://packages.ubuntu.com/changelogs/pool/universe/t/tpb/tpb_0.6.3-1ubuntu1/changelog)

A workaround is to simply use the debian package. Snag it from here: [http://packages.debian.org/testing/utils/tpb](http://packages.debian.org/testing/utils/tpb)

since the debian package is "-2" and the ubuntu package is "-1ubuntu1", synaptic won't attempt to replace the debian package with the ubuntu package.

mike

---

### Post by SacredChicken on 2005-04-13
[QUOTE=Michael R Head]It turns out that the ubuntu packager disabled xosd support in the latest build. Here's the info from the changelog: [http://packages.ubuntu.com/changelogs/pool/universe/t/tpb/tpb_0.6.3-1ubuntu1/changelog](http://packages.ubuntu.com/changelogs/pool/universe/t/tpb/tpb_0.6.3-1ubuntu1/changelog)

A workaround is to simply use the debian package. Snag it from here: [http://packages.debian.org/testing/utils/tpb](http://packages.debian.org/testing/utils/tpb)

since the debian package is "-2" and the ubuntu package is "-1ubuntu1", synaptic won't attempt to replace the debian package with the ubuntu package.

mike[/QUOTE]

Ah indeed. I figured it would probably be that simple, I just haven't had time to poke at it. Thanks for doing the research, Mike! :-)

---

