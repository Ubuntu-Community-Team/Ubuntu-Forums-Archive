---
title: "Back on Gentoo"
date: 2008-12-24
forum: Gentoo and derivatives
---

### Post by bfc on 2008-12-24
Well, after being away for 3 years, I'm back on Gentoo for my main cpu (lenovo thinkpad).

Overall the install wasn't too bad, however, it was an absolute bitch to get a bootable kernel, for some reason Gentoo did not like any kernel I compiled myself. I even used previous kernel configs that were installed on the same machine, and fail.  Finally, I resorted to using genkernel, which gave me a bootable kernel.  I'm going try to compile my own again when 2.6.28 is released (right now i'm using 2.6.28-rc9)

I feel like a complete n00b again!  It's almost humbling, I used Gentoo from 2002 to 2005, and now I can't remember even the simplest commands.   I guess 3 years of using the likes of Fedora/Ubuntu, I've gotten used having every done and set up for me.

Everything is suprisingly stable, especially considering I'm using the unstable branch from Funtoo.org.  The only program that consistently crashes is Compiz.

Now, only if I can figure out why Skype is missing all it's fonts, I'd have the perfect setup.

I'm going to give this install until Jan 5 (when my holidays end), if everything is still running smoothly, I might actually keep Gentoo around!

---

### Post by regomodo on 2009-01-02
> **bfc said:**
> Everything is suprisingly stable, especially considering I'm using the unstable branch from Funtoo.org.  The only program that consistently crashes is Compiz.

Give it time and soon things will crash and hang. Still, the state of portage has improved in the last few months. The devs eventually realised working ebuilds are more important than a friggin liveCD install.

---

### Post by bfc on 2009-01-02
> **regomodo said:**
> Give it time and soon things will crash and hang. Still, the state of portage has improved in the last few months. The devs eventually realised working ebuilds are more important than a friggin liveCD install.

So far, so good.... Well, that's not completely true, I did hose my first installation, completely my fault, I got a little USE flag happy and couple that with installing essentially xorg-git, well, computer didn't like that too much.

I learned my lesson and now my make.conf has the bare minimum for USE flags, and everything has been running really smooth (knock on wood).

To be honest, I'm really not sure if Gentoo is for me anymore.  Day to Day, I'm really just looking a Linux installation that will work with minimal fuss and interaction.  I just don't have the time to maintain a "fussy" system, unlike when I was younger (ahh, the good old days, when every computer I had ran Gentoo)

Anyway, I'm going to keep my current installation until it breaks and then likely just install Ubuntu.

---

### Post by regomodo on 2009-01-10
> **bfc said:**
> So far, so good.... Well, that's not completely true, I did hose my first installation, completely my fault, I got a little USE flag happy and couple that with installing essentially xorg-git, well, computer didn't like that too much.

I learned my lesson and now my make.conf has the bare minimum for USE flags, and everything has been running really smooth (knock on wood).

To be honest, I'm really not sure if Gentoo is for me anymore.  Day to Day, I'm really just looking a Linux installation that will work with minimal fuss and interaction.  I just don't have the time to maintain a "fussy" system, unlike when I was younger (ahh, the good old days, when every computer I had ran Gentoo)

Anyway, I'm going to keep my current installation until it breaks and then likely just install Ubuntu.

Just don't sync portage every day and only use stable packages. But then that's a little unexciting.

---

