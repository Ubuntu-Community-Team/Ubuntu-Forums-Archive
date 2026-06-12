---
title: "touchpad not working anymore on ubuntu 12.04"
date: 2013-08-09
forum: Hardware
---

### Post by antobbo2 on 2013-08-09
Chaps, I am experiencing something really strange and annoying and I was hoping somebody can give me a hand with this.
Basically yesterday I shut down my machine (dell xps 17) ```
[COLOR=#000000]sudo shutdown -P now[/COLOR]
```and when I logged in again the touchpad wasn't working anymore.
I have tried an awful lot of things but I can't get that to work again...
Here are the things I have tried:
1)```
[COLOR=#000000]synclient TouchpadOff=0[/COLOR]
``` returns
```
antobbo@antobbo-xps17-ubuntu:~$ synclient TouchpadOff = 0
Couldn't find synaptics properties. No synaptics driver loaded?



```
2)```
antobbo@antobbo-xps17-ubuntu:~$ gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

``` doesn't help either: nothing happens.
3)this
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps[COLOR=#222222][FONT=Verdana]
``` gets the touchpad to work, althoughit is really funny because it seems much slower than usual and it works only for the current session: if I restart then the touchpad doesn't work
4)keys fn+f3 to disable and then same combination to enable it again: no joy
5)ctrl+alt+f1 to go to console interface and then crtl+alt+f7 to go back to gui: still the same, not working
6)My laptop is dual booting, so I boot up with windows 7 and the touchpad works there: but then when I go back to ubuntu it still doesn't work
I don't think I have any other solution, does anybody what to do please?
thanks[/FONT][/COLOR]

---

### Post by jamesharper-caesar on 2013-12-10
I'm having the exact same problems right now after a dist-upgrade. It was working fine before that.

I have my touchpad working like you with modprobe and made it permanent with this method here: [http://askubuntu.com/questions/127757/how-do-i-make-modprobe-changes-permanent](http://askubuntu.com/questions/127757/how-do-i-make-modprobe-changes-permanent)

I'd very much like to get features like my vertical scrolling back however. Did you manage to fix the problem? Nobody seems to have a definite fix for this.

---

