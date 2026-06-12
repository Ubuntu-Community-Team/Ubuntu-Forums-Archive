---
title: "Help getting my Ugee 2150 Drawing tablet running!"
date: 2016-10-06
forum: Hardware
---

### Post by forleafe on 2016-10-06
I'm an illustrator and I desperately want to make the switch from  windows. I've worked out pretty much everything, but real thing keeping  me tied to windows is my drawing tablet. It's an expensive tablet and I  simply can't do without it right now.

  I stumbled across the digimend project, but immediately lamented as I see they're no longer accepting new projects... [http://digimend.github.io/](http://digimend.github.io/)
  Once more it's a Ugee 2150 and it's drivers for windows and mac are here: [http://ugee.net/download.asp](http://ugee.net/download.asp)
  Please please, is there any way I can get my tablet working on Linux  so I can make the switch for good? Is anyone out there willing to help?

---

### Post by Bucky Ball on 2016-10-06
Welcome. Plug it in, open a terminal, run this command:

```
lsusb
```

Post the output back here between [code] tags, please (see the link in my signature for how to use code tags).

You say it won't work, but you give no other details about how it doesn't work, what you've tried to get it to work, or what software you are using to try and use it (nor do you on the askubuntu thread). Gimp? Inkscape? Do you even know for sure and certain that the device is being seen/not being seen when you plug it in? The command I provided will let us know some details. For future reference, the more information you can give the more support we can. (You do mention Digimend was a dead end although I notice there are a few Ugee devices there, just not yours. :|)

The Mac and Windows drivers are useless here. If what you're asking is for someone to reverse engineer these and port them to Ubuntu for you on the strength of this thread, there's a *_huge_* chance that is not going to happen. We are all volunteers here, including staff, not employees of Canonical or Ubuntu developers, not a paid service or team of code monkeys. Another member may be able to point you in the right direction for getting some action going on creating a Linux driver for this, but it is extremely unlikely anyone here is going to embark on the project. (but miracles do happen occasionally, apparently, so you never know ;)).

Incidentally, and this doesn't help you I guess but maybe a thought for next time you invest in a tablet: most of the Wacom tablets work pretty much 'out of the box'. When you use Ubuntu for a year or two you just start buying hardware that will work off the bat and save yourself some time and hair-pulling (or you stick with Windows). :)

(I always advise an email to the manufacturer asking why there is no Linux driver provided. Doesn't do a lot but rattle the cage a little but at least it makes manufacturers aware we are out here. If hardware doesn't work on Ubuntu, it has nothing to do with Ubuntu generally. It is down to proprietary drivers, closed-source, which Ubuntu, legally, has no control over. It is at the whim of the manufacturers as to whether they decide to grace us with a Linux driver or not. Unfortunately, sometimes these are worthless (like most Linux wireless drivers that come on a little CD with USB wireless dongles) and not worth the terminal they were written on.

---

