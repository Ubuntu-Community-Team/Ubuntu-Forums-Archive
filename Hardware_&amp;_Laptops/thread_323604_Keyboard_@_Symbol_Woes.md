---
title: "Keyboard @ Symbol Woes"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by ziadoz on 2006-12-22
I'm having problems getting the @ symbol working on my keyboard. The keyboard itself is a bog standard no name (UK-GB) keyboard, with no media keys or anything. But when I press the @ key I get an Omega (&#937;) symbol instead. All the other keys seem to work fine in the GB setup. Anyone have any ideas?

I might add I copied and pasted the @ symbol from a website :P

Thanks!

---

### Post by meng on 2006-12-22
What about US keyboard setup, does it give you the same problem?

---

### Post by ziadoz on 2006-12-22
> **meng said:**
> What about US keyboard setup, does it give you the same problem?

I get the @ symbol working there (obviously its the alt of the 2 key though), and then the @ key becomes a "Q". I'd prefer to use my GB layout if it were possible. :)

Any ideas of what the problem is?

---

### Post by meng on 2006-12-22
Sure, understand. Weird problem!

---

### Post by Andy_D on 2007-02-13
I'm having the same problem on my kubuntu 6.06 machine but only when I am using the keyboard attached to my main machine (ubuntu 6.10) via synergy ([http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)). When I directly attach the keyboard to the kubuntu machine all the keys work fine on my gb keyboard. Did you find a resolution to this problem? If so could you please share it with me?

Thanks.

---

### Post by eldepeche on 2007-02-13
Have you tried it on another computer? Something might be wrong with the keyboard. I've had no problems with my GB keyboard on Ubuntu.

---

### Post by Andy_D on 2007-02-13
The keyboard itself works perfectly on both the ubuntu 6.10 and kubuntu 6.06 machines when physically plugged into either one of them, it is only when using synergy to share the mouse and keyboard between the computers that I get this problem. The mouse and keyboard are physically attached to the ubuntu 6.10 machine and all works correctly but when using synergy and using the keyboard to type on the kubuntu machine (which it is not physically plugged into) the @ key produces an uppercase omega instead of the @ character. Every other key works as expected including single quote (which is on the same key as @ on gb layout)

EDIT:
After some more digging around it seems that my problem is specifically to do with synergy. I thought perhaps that since the first post did not mention synergy that this might be an ubuntu specific problem but after checking out the synergy forums this seems not to be the case.

---

### Post by brack on 2008-03-28
> **Andy_D said:**
> The mouse and keyboard are physically attached to the ubuntu 6.10 machine and all works correctly but when using synergy and using the keyboard to type on the kubuntu machine (which it is not physically plugged into) the @ key produces an uppercase omega instead of the @ character.

Having the same trouble, I also noticed that some keys are just missing from the keyboard e.g. I cannot type ";" as well as "{" and "}" and number of others in upper register via syngergy Did anybody solved this problem?

---

### Post by brack on 2008-03-31
Anyone?

---

### Post by dioktos on 2008-04-09
I had problems with @, <, and >, so I did the following:
```
xmodmap -e "keycode 53 = x X greater greater greater greater"
xmodmap -e "keycode 52 = z Z less less less less"
xmodmap -e "keycode 24 = q Q at at at at"
```
Which solved those three... though I have no idea why the problem occurs in the first place.

---

