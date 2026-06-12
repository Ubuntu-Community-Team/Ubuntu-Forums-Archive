---
title: "mic problem ubuntu 10.04"
date: 2011-03-31
forum: Hardware
---

### Post by othermale on 2011-03-31
Hey all:)
So I too have been struggling to get my mic to work but it never has. Searching around for a solution hasn't been fruitful but maybe someone has found one. Since I'm required to keep skype open at all times, I have to use stupid windows till I find a solution. This is on a Del Vostro 1720

 If a picture is worth a thousand words, here are 3000. ( I don't have any options for rear mic in alsamixer)

---

### Post by Kirboosy on 2011-03-31
What all have you done so far to try and fix it?


For my Dell I had to do the following


Run the following command into a Terminal
   ```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```At the very bottom of the file add the following line.
```
options snd-hda-intel model=ideapad
```


Hope that helps,
~Caboose

---

### Post by othermale on 2011-03-31
Good heavens that fixed it!
You solved it in a single post minuets after I asked!
Incredible!
:smile:

---

### Post by Kirboosy on 2011-03-31
I'm glad its an easy/common fix among Dells

Anymore problems feel free to ask.

~Caboose

PS Mark this thread as Solved, Thanks! :)

---

