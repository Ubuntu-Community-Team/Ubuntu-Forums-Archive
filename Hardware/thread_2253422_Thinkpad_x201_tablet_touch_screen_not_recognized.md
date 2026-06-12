---
title: "Thinkpad x201 tablet touch screen not recognized"
date: 2014-11-19
forum: Hardware
---

### Post by urosg3 on 2014-11-19
Today, I make clean install on new HDD of Thinkpad x201 tablet, and Ubuntu is unable to see my screen as touch screen. On win7 touch and stylus works happily.
What went wrong, any ideas or soultions?

---

### Post by The Eight-Bit Link on 2014-11-20
Same here, but with Xubuntu 14.10. Tried using the temporary fix of commenting out lines in the wacom rules, but did not fix it.
This worked in 14.04, so this is a regression, and it has been determined in another thread that the driver is not to blame.

---

### Post by irv on 2014-11-20
urosg3 Are you using 14.04? I have a Asus with a touch screen and 14.04 works. I don't really use it much because I don't like touch on my laptop and there are many programs that don't use the touch. The touch works on the launcher and file manager etc.
Now if you install
```
sudo apt-get install dconf-editor
```
There is a setting to turn on and off touch.
See this link:
[http://askubuntu.com/questions/446421/disabling-touch-screen-only-temporary]("http://askubuntu.com/questions/446421/disabling-touch-screen-only-temporary")
Hope this helps.

---

### Post by urosg3 on 2014-12-18
Hi people sorry for late feedback on topic, but I was dam sick last few weeks. Anyway problem with screen is solved, last kernel update was crucial. After update everything works fine. But 14.10 in live session still nothing, regression?

---

