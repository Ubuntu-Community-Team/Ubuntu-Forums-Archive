---
title: "any way to automate desktop cleaning?"
date: 2008-07-30
forum: General Help
---

### Post by slowferrari on 2008-07-30
Hi, first post here. Thanks for all the solutions I've already found here, hoping i can figure this one out too.

so there's a program called [desktop teleporter]("http://tchikien.donationcoders.com/") for windows (and another called [belvedere]("http://lifehacker.com/341950/belvedere-automates-your-self+cleaning-pc"), apparently). But, I recently went 100% windows free and I really want to find some sort of program like it for Ubuntu.

What it does:
In a nutshell, you assign different kinds of files to different folders on the computer, and when you drop one on to the desktop (but i think only the desktop) it automatically moves it to the assigned folder. so, when you download an .avi it automatically saves it to a movies folder, or whatever.

is there such a thing for Ubuntu? I'm a total n00b and I'm hoping for a program that's available to install either thru add/remove or apt-get. I know I could probably program something, but I had barely opened a terminal before about two months ago and I'm still working on the basics.

so

Thanks!

---

### Post by benjaminoakes on 2011-06-22
've created an open source, Belvedere/Hazel-inspired project that I'm calling "Maid". If you have RubyGems installed (typical if you have Ruby), it just takes a single command to install:

```
sudo gem install maid --pre
# And if you don't have RubyGems, this should set you straight:
# sudo apt-get install rubygems
```

Specifying --pre will install pre-release versions, the Maid release candidate version in this case. The first stable release should be coming out within the next week, and I would love to have your input and opinions.

There's more info at [http://github.com/benjaminoakes/maid]("http://github.com/benjaminoakes/maid") and [http://rubygems.org/gems/maid]("http://rubygems.org/gems/maid")

Maid is based on some code I had written for myself. Eventually, it turned into something I thought others might find useful, so I packaged it up for others to use on Linux and the Mac. I hope it's useful for you.

---

