---
title: "Some fullscreen games show on both monitors[ATI HD 7850]"
date: 2013-12-05
forum: Hardware
---

### Post by yekul on 2013-12-05
I recently replaced my graphics card and installed an ATI HD 7850. I've had no issues setting the card up and getting it working however some games that I play are displaying on both monitors when I play fullscreen. Previously when I played fullscreen games on my old card it would simply black out one of the cards I guess my question is will displaying the game on both monitors take away from the performance of the card? I've got some pictures below to show what is happening.

Any help/info would be greatly appreciated! I have had a search around but couldn't find any solutions.

Normal monitors:
[[IMG]http://i.imgur.com/pkZZ7g9l.jpg[/IMG]]("http://imgur.com/pkZZ7g9")

Running AssaultCube fullscreen:
[[IMG]http://i.imgur.com/ebO8CDwl.jpg[/IMG]]("http://imgur.com/ebO8CDw")

Running FEZ fullscreen(only shows on one monitor):
[[IMG]http://i.imgur.com/7QqRaswl.jpg[/IMG]]("http://imgur.com/7QqRasw")

Running Starbound fullscreen:
[[IMG]http://i.imgur.com/n1uR15Fl.jpg[/IMG]]("http://imgur.com/n1uR15F")

---

### Post by yekul on 2013-12-05
Turns out it was an issue with SDL. I simply had to run the command:

```
[COLOR=#7a0874]**export**[/COLOR] [COLOR=#007800]SDL_VIDEO_FULLSCREEN_HEAD[/COLOR]=[COLOR=#000000]2
```[/COLOR]

---

