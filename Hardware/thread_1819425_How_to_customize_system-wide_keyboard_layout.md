---
title: "How to customize system-wide keyboard layout?"
date: 2011-08-06
forum: Hardware
---

### Post by ClyN3il on 2011-08-06
My HP laptop has a really annoying design feature by which the Insert key and the Print Screen key are on the same key. To use Insert, I have to hold down the function key. I hardly ever have reason to use the Print Screen key, but I have dozens of applications for which I use the Insert key more often that I use Enter or Delete. How can I modify my system-wide keyboard layout so this behavior is reversed; so the key is Insert by default and Print Screen when holding down the Fn key?

---

### Post by enimeizoo on 2011-08-06
Hi
I think the software you are looking for is xmodmap. The function key acts weirdly, though, most of time, so it might be a little bit tricky to configure.
Another useful software will be xev. 

I'll give you general steps, but if you need more precision, I will need some outputs.
0) backup your keyboard mapping, just in case.
```
xmodmap -pke > .xmodmap.old
xmodmap -pm >> .xmodmap.old
```1) find out keycodes sent by your key, and fn + your key with xev. They might or might not be the same. 

2a) If they are not the same. Let's say they are respectively 118 and 107.
 create (or edit if existing, for some reason) a ~/.xmodmap file. Add these lines to the end of it.
```
keycode 118 = Insert
keycode 107 = Print
```2b) if the keycodes happen to be the same, say 118.
Then, run ```
xmodmap -pke | grep 118 >> .xmodmap
```This will give your the line corresponding to your key in a .xmodmap file.
You should see 'Print' and 'Insert' in it, just switch their positions. 

3) finally, run
```
xmodmap .xmodmap
```And see if it worked. If it didn't, just restore your configuration.
```
xmodmap .xmodmap.old
```Unless you want to rely on your desktop environnement to use it as a config file (so that it is loaded on login), you might want to add this line in your ~/.profile file (and create it if it doesn't exist):
```
xmodmap .xmodmap
```Hope it helps.

---

