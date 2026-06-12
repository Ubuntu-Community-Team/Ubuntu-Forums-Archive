---
title: "UX32VD Xorg.conf"
date: 2012-10-13
forum: Hardware
---

### Post by MPalhas on 2012-10-13
I've been strugling a lot to install Linux on my new Asus Zenbook UX32VD.
After trying various distros, Debian Squeeze was the only one that i was able to install and use. All others would just result in a black screen right after boot (i still would see the mouse for a couple of seconds though)

But after a while configuring debian, i now suspect the problem lies with Xorg.conf

This laptop has two graphic cards, an Intel HD 4000, and NVidia GT 620M.
In Debian i don't have any Xorg.conf by default. But as soon as i tried to install the NVidia drivers and have them generate one for me, i got a black screen once again. Deleting this xorg.conf fixed the problem, but i'm now running with no graphic driver.

I'd like to able to configure the graphics correctly, which is probably also the solution to install Ubuntu or other distros

---

### Post by Bashing-om on 2012-10-13
MPalhas; Hi !

This link should prove helpfull, explains what is happening and how to load the graphics driver.
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Let us know what works.
[INDENT]regards <==BDQ

[/INDENT]

---

