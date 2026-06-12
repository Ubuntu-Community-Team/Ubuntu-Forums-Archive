---
title: "BUYER'S REMORSE - Bought A Slow Laptop for Front End Web Dev"
date: 2019-06-01
forum: Hardware
---

### Post by dmainevent on 2019-06-01
Hey guys, long time user, first-time poster here.

I recently decided to start learning front end web development and wanted to get a new laptop. I got an [Acer Swift 1]("https://www.acer.com/ac/en/US/content/series/swift1") for less than $300 and thought it would be great to install Xubuntu on it. So I installed Xubuntu 19.04 on it, installed a 256GB SSD and got everything else set up just how I like it, but it's just too slow. I then realized that the 4GB RAM it comes with is not upgradeable. Great....

The experience I usually get with XFCE is so buttery smooth, but with this laptop I cannot have more than a few tabs open on Chrome along with Atom without it hanging up. I wanted to try Gravit Designer's native desktop app, Pinegrow, GitKraken and FileZilla together but it was hanging up too much simply typing in the browser. Running minimal development work usually eats up about 87% of the system memory and over 60% of a 4GB swap partition. 

I really didn't think it would be so bad, but it's bad. I should've known better. What should I do? I really like this laptop's hardware, plus I can't really return it anymore.

BTW, here's some eyecandy, my riced desktop. Looks are deceiving, though....

---

### Post by DuckHook on 2019-06-02
Clearly, you know your stuff, so there's no avoiding the fact that your assumptions are accurate… you picked too light a box for your needs.

There's no magic bullet, but the following might help marginally:

[LIST]
[*]Use a non-compositing window manager. Perhaps Lubuntu or an absolutely minimal install with a simple window manager like openbox or i3wm. This won't free up much, but if you want to glean every bit of muscle out of the OS for app use, this is the usual option. See the link in my sig: The Best 'buntu Flavour.
[*]Simply limit the number of simultaneous apps you run.
[*]Retire the laptop, or relegate it to functions that are within its abilities, and buy another one capable of fulfilling your needs.
[/LIST]

---

### Post by dmainevent on 2019-06-02
Thanks a lot, DuckHook. I am able to hobble along with some video-based learning and my text editor for now, and I'm just prioritizing meeting my assignment deadlines at the moment. I figured I should start a decent desktop build (I have an old Dell SFF desktop I played around with--too slow, even with RAM upgrades and Linux) and make myself a nice workspace at home. There's this feeling I would need performance more than portability, I mean, who do I have to impress at the coffee shop?

I also looked into your link and have decided to give a leaner window manager a shot. I like what I see in the "[unixpron]("https://www.reddit.com/r/unixporn/")" subreddit. It might mean I go with the minimal installer, but that sounds too Arch-like and intimidating to me. Would it be better to apt-get a WM and just log in for that session (yes, I read up a bit of documentation), or should I start from scratch?

---

### Post by cruzer001 on 2019-06-02
OpenBox can be used as a window manager, I believe its non-composite and its in our software sources, thats about as light as it gets.

I once had a corrupted download (ubuntu iso) that slowed a computer way down, but it still worked.

I don't consider Ubuntu Budgie to be a true lightweight, but I have a 13 year old single core laptop that runs Budgie surprisingly well. May be worth a try.

---

### Post by dmainevent on 2019-06-04
Hey again, thanks for the valuable input. I decided to just make the best of my setup right now, since I need the already-productive setup more than bleeding any more speed from out of my system. Once my online course is finished I'd like to give the [Manjaro Openbox Community Edition]("https://manjaro.org/download/openbox/") a try. I'll edit the post to [SOLVED] for now and probably spend more time around the forum asking about Openbox, Conky and development tools I should learn. 

I've been googling blogs, videos and manpages on Openbox setup, but does anybody have any beginner-friendly links they'd be kind enough to share? Thanks again.

---

