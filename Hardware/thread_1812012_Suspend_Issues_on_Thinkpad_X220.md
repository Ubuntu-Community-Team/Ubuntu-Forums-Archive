---
title: "Suspend Issues on Thinkpad X220"
date: 2011-07-25
forum: Hardware
---

### Post by navr91 on 2011-07-25
Dear Friends!

I've been using different distros of Linux for a while on the side, but I'm finally making the great change from Windows to Ubuntu as my main OS. I had everything pretty much setup and going well on my old laptop, but now I've got a new laptop and there have been a few problems that have taken me quite some time to fix. After days of searching and reading bug reports, I've fixed mostly everything, except for my suspend problems.

Here I go:

[B]Computer: Thinkpad X220
OS: Ubuntu 11.04, 64-bit[/B]

I got a Thinkpad X220 very recently (last week), and it has problems suspending SOMETIMES (about 1/3 of the time). It can't hibernate from what I can tell, but it also can't suspend... sometimes. I can't come up with a pattern of when the suspending works and doesn't, but when it doesn't work, the screen goes blank, the backlight stays on and the "moon" LED on the top of the computer blinks forever. The computer enters a sort of trance, and I can't get it out, even with ctrl+alt+backspace, it's still frozen. I have to force restart every time this happens.

I've noticed also, though, that sometimes after I resume after a successful suspend, the wireless is disabled "by hardware switch," which is not true by the way! And sometimes the function hotkeys don't work. If the computer is in this state, and I try to suspend, it freezes and goes in the trance. However, even when everything is working, it can still freeze when I suspend it.

The confusing thing is, this behavior doesn't seem to be consistent, so I'm having trouble figuring it out. I've done a lot of googling and haven't found anything too helpful, but this forum has gotten me through some pretty obscure problems before, so I have faith.

Thanks for your time and help as always, guys!

---

### Post by navr91 on 2011-07-27
Yesterday I tried updating my kernel to 2.6.39-02063903-generic. But the problem still persists. Any help at all is appreciated!

---

### Post by williumbillium on 2011-07-28
Do you have the i7 model with USB3?  Are you using any USB3 devices?

If so, it could be this bug:

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/522998)

---

### Post by navr91 on 2011-07-29
Thanks for your help Will, unfortunately, I don't think that bug report was the one for me. I've read through a ton of bug reports, but most of these problems were resolved with kernel upgrades or BIOS upgrades--none of which worked for me.

I reported my bug. It's my first time reporting a bug! We can watch the action unfold at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818194]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818194")

---

