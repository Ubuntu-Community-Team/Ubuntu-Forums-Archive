---
title: "Delayed (character shifted) keyboard input - not lag!"
date: 2015-08-20
forum: Hardware
---

### Post by christian20 on 2015-08-20
Hi there,

I am experiencing a weird issue when typing. Usually, everything is fine, but from time to time, not reproducible, but quite regular, when I use a program for a while, the following happens:

Characters I type are not displayed immediately, I need to type the next character before the one before appears. This is not a lag between hitting the key on the keyboard and the character appearing. Say I type "Apples are red", when I typed "Apples" there will only be "Apple" on the screen until I press space and then the space will not be on screen until I press "a" and so on.

Restarting the program usually helps but only for a short time, then the issue will re-appear. Examples are HexChat or Leafpad. The issue never appears in applications started via Wine.

Do you have any ideas? I will be happy to provide additional information if you tell me where to search. I'm on Ubuntu 14.04 Trusty.

Christian

---

### Post by dino99 on 2015-08-21
hello Christian,
of course there is a few possible reasons to get such an issue:
- user keyboard settings are borked: go to system settings and choose different settings for the keyboard (save them) and switch back to the one you need (save again)
- if the keyboard is powered by battery, then maybe some energy is missing
- if the keyboard  keys are not protected, then possible dust/food/.... can disturb the typing flaw (clean it, set it upside down to let drop the unwanted ghosts)

and indeed glance at the logs (/var/log/ & .xsession-errors ) in case of something usefull have been logged

---

### Post by christian20 on 2015-08-21
Hi dino99,

thanks for your reply.

- Changing the keyboard settings did not help.
- the keyboard is not powered by battery
- the keyboard is quite clean, also, it's not a hardware issue - in HexChat for example the not displayed character is actually there, when I press enter the message is sent and the last character I typed (the one I cannot see) is sent.

I'm watching some logs now but it does not seem promising...

---

