---
title: "Left Shift is the same key as volume increase. Cannot separate their functionality."
date: 2015-10-01
forum: Hardware
---

### Post by enixon on 2015-10-01
On my HP Laptop the left shift increases volume when pressed. Right shift mutes volume. These two actions are also carried out by f6(mute) and f8(increase). Obviously I can't have my shift keys messing with volume. How do I get the shift keys to stop effecting volume. I've tried 'xmodmap -e "keycode 123 = Shift_L"' which prevents shift from messing with volume but also disables to volume increase button all together. I'm tested this out on multiple keyboard layouts including default with no change. I've even tried maping the f8 key to a command such as 'amixer -D pulse sset Master 5%+' but this will also reset left shift to increase volume. This is highly annoying. 

Thank you for your time.

---

### Post by enixon on 2015-10-02
Turned my computer on today and the problem is gone. Very strange indeed.

---

