---
title: "disable keyboard buttons!"
date: 2008-08-03
forum: Hardware
---

### Post by tripozo on 2008-08-03
Hi. I have ctrl buttons broken on my laptop. Some time ago I spilled some tea on the keyboard, so now these buttons are sensitive and function without pressing them. What I do is:

xmodmap -e "add lock = Control_L"
xmodmap -e "add lock = Control_R"
xmodmap -e "add control = Caps_Lock"

Everything works fine till i change the keyboard language or restart the pc. How can I disable them forever, without entering these commands each time i turn on the pc o change the language on the keyboard. 

Thanks

---

