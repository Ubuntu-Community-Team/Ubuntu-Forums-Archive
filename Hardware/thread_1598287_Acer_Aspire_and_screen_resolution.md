---
title: "Acer Aspire and screen resolution"
date: 2010-10-16
forum: Hardware
---

### Post by atti84it on 2010-10-16
Hello everybody! I've just installed Maverick on a Acer Aspire 5520 (has Nvidia GeForce 7000M and AMD Athlon 64 x2) and things work fine more or less.

I've a problem with screen resolution: **it only allows me to choose 1024x768 or lower, while the screen supports 1280x800**. How can I change it?

I've seen a lot of threads on this forum but all of them refer to Lucid or earlier. As I understood there's no xorg.conf file anymore in Maverick.
Please help!!

---

### Post by atti84it on 2010-10-16
After a lot of reading I solved in a weird way:

[LIST=1]
[*]uncheck the "same image in all monitors" in System -> Preferences -> Screens
[*]play a bit with resolutions, for example select 640x480 and click "apply" and of course reject the awful resolution
[*]magically will appear the resolution 1280x800
[/LIST]
Now I have a **minor problem**: I see a regualar desktop 1280x800 but there's a kind of empty space on the right of the screen (windows can get lost there), and when I capture the screen I can see the empty space, like in this picture:

Please notice that in the picture, the Firefox window is _**maximized**_! but still doesn't occupy the whole area (2304x800)

[IMG]http://img153.imageshack.us/img153/8959/schermataob.png[/IMG]

---

