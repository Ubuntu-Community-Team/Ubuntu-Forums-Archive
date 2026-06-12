---
title: "Gnome-less login but still available through nomachine NX"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by snaggletooth on 2009-06-19
I have a computer in the basement I'm looking to turn into a server but it's pretty old (intel P3, ~.7Ghz, 370mb ram) and I'd like to keep the load on it relatively low.

So, I'd like to install it without a gui loading on startup, but still available through NX.

What I've done up till this point is I've installed Ubuntu 9.04 desktop edition and then I removed gdm from startup using "update-rc.d -f gdm remove" -- and it worked.

I also had NX installed, and it works fine now. My only issue is that I still have a ton of daemons and services starting up automatically when I boot.

Is there a way to make everything gnome related (pulse, bluetooth, etc) start up ONLY if I initiate an X session through NX or just by 'startx'?


In other words, my goal is to make it as lean as possible on startup and only open up the extra daemons/applications when remotely connect with nx or begin X manually.


How can I do this?

Thank you,

Nick

---

### Post by snaggletooth on 2009-06-20
Is it that my message isn't clear, or that it's not easily done?

---

