---
title: "&quot;o&quot; isn't working on keyboard, what can I do?"
date: 2009-09-18
forum: Hardware
---

### Post by jward3010 on 2009-09-18
"o" isn't working on my keyboard, the key is physically broken and I'm wondering if there's some way I can map it to a permanent keystroke.

Currently I go into Character Map and copy an "o" to the clipboard and to type it I have to hit Ctrl-V to paste which is a major pain, especially when I copy a link to the clipboard and it kills the "o".

Any ideas?

---

### Post by 73ckn797 on 2009-09-18
Can't find a cheap key board some where? If you are in Atlanta I have a couple of extra with a working "o". 

You could pop another key off and put it in place of the "o", unless you are using a laptop. The ~ key next to the #1 would probably work and it is probably rarely used anyway.

---

### Post by fela on 2009-09-18
I think you can do this with xbindkeys. Look it up though because I don't know how, just I'm sure it's possible.

---

### Post by jward3010 on 2009-09-18
> **73ckn797 said:**
> Can't find a cheap key board some where? If you are in Atlanta I have a couple of extra with a working "o". 

You could pop another key off and put it in place of the "o", unless you are using a laptop. The ~ key next to the #1 would probably work and it is probably rarely used anyway.
The actual problem is that the "o" key is physically beyond repair, the contact that is made on keyboard between two pieces of metal (or whatever way it works) is no longer happening. it degraded slowly but surely over the last couple of months. So I'll pretty much need a new keyboard as opposed to just a new "o" key - I really wish it was just that though. Thanks for the offer all the same.

> **fela said:**
> I think you can do this with xbindkeys. Look it up though because I don't know how, just I'm sure it's possible.
I shall indeed look this up. Thanks.

---

### Post by 73ckn797 on 2009-09-18
> **jward3010 said:**
> The actual problem is that the "o" key is physically beyond repair, the contact that is made on keyboard between two pieces of metal (or whatever way it works) is no longer happening. it degraded slowly but surely over the last couple of months. So I'll pretty much need a new keyboard as opposed to just a new "o" key - I really wish it was just that though. Thanks for the offer all the same.


I shall indeed look this up. Thanks.

OK. I was not certain of the full extent of the problem.

---

### Post by jward3010 on 2009-09-18
> **73ckn797 said:**
> OK. I was not certain of the full extent of the problem.
Don't worry, I never made it that clear.

---

### Post by drs305 on 2009-09-18
You can reprogram the o key to something else using xmodmap.

First run "xev" in a terminal. It opens a small window. Put the cursor in the box, then press the desired replacement key to get its value. In the example, I will substitute the left Windows key (Super_L).

The Super_L key on my keyboard is 133. So I would run this command:
```
xmodmap -e "keycode 133 = o O"
```
This makes the Super_L/shift Super_L return o and O, respectively.

It's only good for the current session. You can place the command in a startup script to make it 'permanent'.

---

### Post by fela on 2009-09-19
You could make the shell script with another computer or with a different keyboard, so you can access the O key that one time.

Best idea is to get a new keyboard though as other keys might break.

---

### Post by alienclone on 2009-09-19
just open the on screen keyboard and click the "o" when needed

---

