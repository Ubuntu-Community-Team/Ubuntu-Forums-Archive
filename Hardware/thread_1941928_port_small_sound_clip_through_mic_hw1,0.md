---
title: "port small sound clip through mic hw:1,0"
date: 2012-03-16
forum: Hardware
---

### Post by luckbedamned on 2012-03-16
i have a small problem here. i'm working with voximp, and for any of you who are familure with it, you'll know what i'm talking about. i have multiple langage, dictionary, and sentence constructs for the voximp. when you initiate the voice interface with the word "computer", it loads a new language model and restarts voximp with a set of menu commands, and if you say a command like "computer" ... "play a movie" then it loads a new menu with commands like "next movie" or "next chapter" or "pause movie"

now, the problem is, when it loads a new menu langauge model, there is a small delay for allowing for voximp to reload, but the biggest annoyance is the first command is NEVER understood. no matter how clearly you speak the next command, it always misinterprets it. the second time you say it though it works fine. so... my solution? send a random sound through hw:1,0, not any sound in particular, just enough sound to fake out voximp and allow for the next command without any misinterpretations.

if anyone can help me achieve this "fake sound" solution, or has a better options for loading new voice interface menu's, i'm all ears. thx in advance guys, cheers

---

