---
title: "Rhythmbox 0.9.2 for Breezy"
date: 2005-12-04
forum: General Help
---

### Post by flopsy on 2005-12-04
If, like me, you can't wait to get your hands on 0.9.2, I've rebuilt dapper's Rhythmbox 0.9.2 and libgpod0 for Breezy. They install cleanly and seem to be stable but the **install these packages at your own risk**.

Download libgpod0, libgpod-common and rhythmbox. Install with sudo dpkg -i

[http://homepage.ntlworld.com/g.law2/ubuntu]("http://homepage.ntlworld.com/g.law2/ubuntu")

---

### Post by daveg on 2005-12-05
[QUOTE=flopsy]If, like me, you can't wait to get your hands on 0.9.2, I've rebuilt dapper's Rhythmbox 0.9.2 and libgpod0 for Breezy. They install cleanly and seem to be stable but the **install these packages at your own risk**.

Download libgpod0, libgpod-common and rhythmbox. Install with sudo dpkg -i

[http://homepage.ntlworld.com/g.law2/ubuntu](http://homepage.ntlworld.com/g.law2/ubuntu)[/QUOTE]
Nice package. Any chance of getting it rebuilt with daap support?

---

### Post by outdooricon on 2005-12-05
[QUOTE=daveg]Nice package. Any chance of getting it rebuilt with daap support?[/QUOTE]

Yes, DAAP support would be really nice. I already have Avahi installed.

---

### Post by flopsy on 2005-12-05
Rebuilt with daap enabled (look in the daap-enabled folder). It should pull in everything it needs to run automatically. A word of warning: daap support is still experimental and can make rhythmbox somewhat unstable.

The build in the main folder does not have daap support compiled in, should you prefer stability. Both builds have iPod support.

---

### Post by outdooricon on 2005-12-05
[QUOTE=flopsy]Rebuilt with daap enabled (look in the daap-enabled folder). It should pull in everything it needs to run automatically. A word of warning: daap support is still experimental and can make rhythmbox somewhat unstable.

The build in the main folder does not have daap support compiled in, should you prefer stability. Both builds have iPod support.[/QUOTE]

Excellent! Well done Sir! You have succeeded in what I could not do (I tried to install via binary and failed miserably). I love the development of rhythmbox the past few months, It's awesomeness growths exponentially!

---

### Post by bb002 on 2005-12-06
Hey quick question (I hope): I compiled 9.1 from source and when I closed the app it by the X button it iconified to the tray. I really liked that how do I make 9.2 do this? I compiled 9.2 from source and it doesn't do it anymore. If this isn't a simple fix (something like an argument to ./configure) then say so and I'll try to get into contact with the RhythmBox developers.

---

### Post by daveg on 2005-12-06
[QUOTE=flopsy]Rebuilt with daap enabled (look in the daap-enabled folder). It should pull in everything it needs to run automatically. A word of warning: daap support is still experimental and can make rhythmbox somewhat unstable.[/QUOTE]I was running rhythmbox 0.9.1 with daap support and didn't have any issues with listening to other iTunes shares. Listening to my rhythmbox share using iTunes caused the CPU utilisation to jack up to 100% though when I skipped tracks (with no errors in debug mode... weird). But luckily that's something I never really need (I was just playing around).

Nice to have podcast support built in (not being built into rhythmbox is one reason why I've never gone too far out of my way to listen to podcasts).

Thanks for the quick rebuild :-D

---

### Post by doclivingston on 2005-12-06
[QUOTE=daveg]I was running rhythmbox 0.9.1 with daap support and didn't have any issues with listening to other iTunes shares. Listening to my rhythmbox share using iTunes caused the CPU utilisation to jack up to 100% though when I skipped tracks (with no errors in debug mode... weird). But luckily that's something I never really need (I was just playing around).[/QUOTE]

That is due to a bug in libsoup, which is impossible to work around within Rhythmbox itself - the bug is fixed in libsoup 2.2.7, which is in Dapper.


[quote=bb002]Hey quick question (I hope): I compiled 9.1 from source and when I closed the app it by the X button it iconified to the tray. I really liked that how do I make 9.2 do this? I compiled 9.2 from source and it doesn't do it anymore. If this isn't a simple fix (something like an argument to ./configure) then say so and I'll try to get into contact with the RhythmBox developers.[/quote]

The policy of having the close box minimise-to-tray was the object of a several week long debate on the Rhythmbox-Devel mailing list, the end result of which was that it got turned off. You can still minimise to the tray by clicking on the tray icon (which always worked), or typing Ctrl-W (File->Close).

---

### Post by outdooricon on 2005-12-06
[QUOTE=doclivingston]That is due to a bug in libsoup, which is impossible to work around within Rhythmbox itself - the bug is fixed in libsoup 2.2.7, which is in Dapper.




The policy of having the close box minimise-to-tray was the object of a several week long debate on the Rhythmbox-Devel mailing list, the end result of which was that it got turned off. You can still minimise to the tray by clicking on the tray icon (which always worked), or typing Ctrl-W (File->Close).[/QUOTE]

doclivingston, I really like what you guys have done in this version. I think when you all finally get cover art done and cd ripping implemented, rhytmbox will be near perfection. Total iPod connectivity would be nice, but I'm not holding my breath on that one. Keep up the good work!

---

### Post by magnusbb on 2005-12-06
Thanks for your contribution. 0.9.2 works very good here!

---

### Post by grus on 2005-12-06
You just made my day. :)

---

### Post by mehlkelm on 2006-01-01
[QUOTE=flopsy]Both builds have iPod support.[/QUOTE]
Does this mean I should be able to drag & drop tracks onto my ipod? Because I can't. The ipod just shows up in the sources and I can play from it, but nothing is different than it was in 0.9.1.
Anyway, I really like it! Thanks for the build.

---

### Post by marinosr on 2006-01-04
Thankyouthankyouthankyou.

I just installed this package, and it fixed myriad problems I was having with 0.9.0.

---

### Post by Mozzer on 2006-01-09
Cheers, this is very handy indeed, now I can get podcasts without installing extra software :)

---

### Post by Brokenrgv on 2006-01-09
works awesome thnx :)

---

### Post by Pooldraft on 2006-01-23
Sweetness!

---

### Post by tig4 on 2006-01-25
I Love You!

---

### Post by Noremacam on 2006-01-27
Can anyone else confirm this bug?

When playing audio cd's, when you try to resize the individual columns, the columns move around kinda crazily, and don't quite follow the mouse.

This is a great build by the way, inspite of that error. This fixed my problem with constant reappearing duplicate entries. It could just be me, but the CPU utilization seems less.

As to the close button minimizing to the tray, I kinda got used to it. Couldn't they just make an option in the preferences so that way everyone can have it the way they want?

---

### Post by doclivingston on 2006-01-27
[QUOTE=Noremacam]When playing audio cd's, when you try to resize the individual columns, the columns move around kinda crazily, and don't quite follow the mouse.[/quote]

That is actually a GTK problem ([bug 316087](http://bugzilla.gnome.org/show_bug.cgi?id=316087)). Column resizing has a lot of corner cases, several of which Rhythmbox runs in to; all of the proposed solutions I've seen make some things better and some worse. It would be *really* nice to not have it be crazy, but I don't know if it'll happen any time soon.

---

### Post by neufena on 2006-01-31
Any chance of a howto for rebuilding the deb from Dapper?

I'm on amd64 but would like Rhythmbox 0.9.2.

Thanks,

---

### Post by doclivingston on 2006-01-31
[QUOTE=neufena]Any chance of a howto for rebuilding the deb from Dapper?[/quote]

Insert the Dapper source repository into your sources.list (deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main). Then run "apt-get build-dep rhythmbox" and then "apt-get --compile source rhythmbox".


> I'm on amd64 but would like Rhythmbox 0.9.2.

Dapper actually has a cvs checkout (of the upcoming 0.9.3) rather than 0.9.2, but it's reasonably stable.

---

