---
title: "Logitech diNovo Edge, can't submit PIN"
date: 2011-12-08
forum: Hardware
---

### Post by teeli on 2011-12-08
Hi,

I just installed the latest Ubuntu (11.10) and I'm trying to use Logitech diNovo Edge with its own bluetooth dongle. Otherwise it seems to work correctly, Ubuntu even finds the keyboard when pairing, but it won't receive the pin when I enter it on the keyboard (enter the code and press enter). Eventually it just times out and fails.

I have previously used this keyboard on Windows, so there's nothing wrong with the keyboard itself.

Anything I can do to fix this?

edit: i'm using the 64bit version if that makes difference

---

### Post by teeli on 2011-12-08
Ok, managed to pair them using blueman but it still doesn't work. They are paired but there is no connection apparently.

---

### Post by teeli on 2011-12-09
I tried this solution [http://awesomelinux.blogspot.com/2011/10/ubuntu-logitech-dinovo-edge-bluetooth.html](http://awesomelinux.blogspot.com/2011/10/ubuntu-logitech-dinovo-edge-bluetooth.html)

However when I do that change, the bluetooth dongle is not recognized at all.

---

### Post by teeli on 2011-12-09
After doing a bit of this and that back and forth, now it works. Weird.

So basically:
0) Forget bluetooth (in system settings)
1) Change hiddev to hidraw like described in the link
2) Use the button on the dongle to connect the keyboard.
3) Repeat N times until it works.

---

