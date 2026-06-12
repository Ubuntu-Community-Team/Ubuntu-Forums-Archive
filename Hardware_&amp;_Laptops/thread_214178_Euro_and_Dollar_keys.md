---
title: "Euro and Dollar keys"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by MrHorus on 2006-07-12
My laptop has the dollar and euro keys on the number row like normal but it also has two seperate, standalone keys near the cursor keys.

Since these are model-specific, they don't work out of the box and dmesg states they are unrecognised keys when they are pressed.

So, is there some sort of command line or graphical tool that will allow me to map these keycodes to the right characters?

Just give me the application name and I can figure out how to work out myself :)

---

### Post by Zdravko on 2008-01-22
I am asking the same question.

---

### Post by nick_h on 2008-01-22
> Just give me the application name and I can figure out how to work out myself
xmodmap

It might help if you posted the error message you are getting.

---

### Post by Zdravko on 2008-01-22
How do I use this? I don't get anything...

---

### Post by nick_h on 2008-01-22
Sorry, I was replying to the OP who might have lost interest after 18 months :)

xmodmap is a command line utility to modify key mappings.  You see your current mappings by typing:
```
xmodmap -pk
```

There is also a graphical utility called xkeycaps which you can install with:
```
sudo apt-get install xkeycaps
```

What you will have to do is find the keycode so that you can map it.  There is a utility called xev that will help you do this.

I think it would be best to start with xev and see if it gives you a keycode when you press the keys you need to map.  Then you can use xmodmap to see if you can get them working.

I found a useful page [here](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html).

---

### Post by Zdravko on 2008-01-22
I tried xev, but the key doesn't seem to get caught by it.

---

### Post by nick_h on 2008-01-22
That doesn't look good.

Do you get any errors in dmesg like the OP?

---

### Post by Zdravko on 2008-01-22
Hmm. What is dmesg?

---

### Post by nick_h on 2008-01-22
Type:
```
dmesg | less
```
and have a look to see if there is anything keyboard related.

---

