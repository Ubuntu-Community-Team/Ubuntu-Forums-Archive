---
title: "Can't get any sound with Realtek ALC850 or Creative Soundblaster Live 24-bit"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by thefrug on 2006-01-02
I just built a new machine and installed Ubuntu64. I used Ubuntu on my previous machine and it worked fine, but I can't seem to get it to work on this one.

I had on board sound initially, which was Realtek ALC850. I couldn't get it to work, and didn't see that it was supported anywhere, so I went out and bought a Creative SoundBlaster Live 24-bit card.

The soundblaster won't work, either. When I try to use something like aumix, it says that no device was found.

The volume is set all the way up, and if I use a program like mpg123 to play music, it will say that it's playing, and the gnome volume meter shows that sound is being played. All of my volume is up.

I really don't know how to have my sound card detected/used. This is getting extremely frustrating and I really need help.

---

### Post by DoorGunner on 2006-01-02
If you had put you sound card on after your initial install it is possible that Ubuntu didnt know to install the alsa drivers.

try alsamixer in terminal. If you dont get any gui come up than this is more than likely the case.

It could be thats all you need.

---

### Post by thefrug on 2006-01-02
I reinstalled once I put in my sound card just to makes sure it got all the correct drivers.

In alsamixer, everything is turned up.

I also noticed something else that's strange.

There are 4 ports on my sound card. There is one that is supposed to be for line out, which doesn't work, but the one for digital out kind of does. It has extremely distorted and fuzzy sound.

I don't know if that means anything.

---

### Post by thefrug on 2006-01-02
Also, when I restart alsa or restart Ubuntu, I hear the noise that used to come out of my speakers on my old machine when I did those things.

The noise is audible on the regular analog line out.

It seems that somehow, sound is only being outputted to the digital out, because when i turn that up in alsamixer and have my audio plugged in to that port, I hear the sound, but it's distorted. Nothing comes through analog even if i turn it up.

---

