---
title: "&quot;play/pause, next, prev&quot; keys does not function"
date: 2011-08-01
forum: Hardware
---

### Post by HelgeSverre on 2011-08-01
Hello i have a Lenovo Thinkpad Edge 14, which i installed Ubuntu 10.4 on.
I have trouble getting **[THESE]("http://oi53.tinypic.com/ezkbiu.jpg")** keys to work correctly

I tried to go to **[COLOR=Red]["keyboard shortcut"]("http://oi54.tinypic.com/330zjie.jpg")[/COLOR] **(sorry for the paranoid red markings, i am careful!) and bind the buttons to the correct action, but no luck.

I am trying to get this to work with the linux preview of Spotify.
If you need any more info please specify.

Thanks in advance.

---

### Post by papibe on 2011-08-01
The first thing that I would do is to play around with different keyboard layouts to see if it can be solved easily that way.

If that doesn't work, I'd check if X Windows recognizes the key itself. There's a command called 'xev' that registers and prints all events while executed. Try to check if the key is registered:

```
$ xev
```
Just some thoughts,
Regards.

---

### Post by EkuquoL on 2011-08-01
You can edit shortcut keys using the "Keyboard Shortcuts" application.
It is a application that is/ should already be installed on your Ubuntu Gnome/Unity environment

---

### Post by HelgeSverre on 2011-08-01
> **papibe said:**
> The first thing that I would do is to play around with different keyboard layouts to see if it can be solved easily that way.

If that doesn't work, I'd check if X Windows recognizes the key itself. There's a command called 'xev' that registers and prints all events while executed. Try to check if the key is registered:

```
$ xev
```Just some thoughts,
Regards.

Here is the output i got after pressing prev, play/pause, next(in that order)

[http://ppst.me/rFHwFA](http://ppst.me/rFHwFA)

It doesn't tell me very much but it might tell you something..


> **EkuquoL said:**
> You can edit shortcut keys using the "Keyboard Shortcuts" application.
It is a application that is/ should already be installed on your Ubuntu Gnome/Unity environment

> **HelgeSverre said:**
> 
 I tried to go to **[COLOR=Red]["keyboard shortcut"]("http://oi54.tinypic.com/330zjie.jpg")[/COLOR] **(sorry for the paranoid red markings, i am careful!) and bind the buttons to the correct action, **but no luck.**
 

---

