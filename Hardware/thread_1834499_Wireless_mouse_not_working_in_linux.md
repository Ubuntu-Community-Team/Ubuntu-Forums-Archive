---
title: "Wireless mouse not working in linux"
date: 2011-08-27
forum: Hardware
---

### Post by StefanRvO on 2011-08-27
Hi
I have recently bought this wireless mouse [http://www.ebay.com/itm/190489754550](http://www.ebay.com/itm/190489754550)
It does not, however works on ubuntu (or fedora), but works fine in windows.
When i run lsusb, it does not seem to show up, but after i ran it a couple of times, i figured out that it shows up sometimes:
 [http://pastebin.com/wZECe8a8](http://pastebin.com/wZECe8a8) Here it shows up at line 202 as Novatek Microelectronics Corp.
Also, it shows up sometimes when i run xinput list:  [http://pastebin.com/9LA7TJtC](http://pastebin.com/9LA7TJtC)
Here it shows up as USB Device USB Device around line 3200
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                    id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                    id=11   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation              id=12   [slave  pointer  (2)]
&#9116;   &#8627; USB Device USB Device                         id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                     id=5    [slave  keyboard (3)]
    &#8627; Power Button                                    id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                       id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                    id=8    [slave  keyboard (3)]
    &#8627; CNF7017                                         id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                    id=10   [slave  keyboard (3)]

```

If i run dmesg, it seems like the reciver canstantly gets connected and then disconnected again.
[http://pastebin.com/QEbRgYNL](http://pastebin.com/QEbRgYNL) ( i plug the reciver in at line 29)
I run lucid 64 bit

I hope someone is able to help

Regards
Stefan

---

### Post by StefanRvO on 2011-08-29
Bump

---

### Post by thusi87 on 2011-10-23
Same issue... still couldnt find a solution. Mine never gets identified using lsusb. IS there a way to manually install a usb device? I think we can get some information about the H/W using the windows device manager panel. Please help!

---

### Post by fdnieves on 2012-03-12
Were you able to make it work under Ubuntu? I have the same mouse, and the same issue.

---

### Post by draekko on 2012-06-04
I had the same issue, i posted a patch to the kernel that made min work. See i here:

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+question/197812](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+question/197812)

---

### Post by psyionx on 2012-06-24
Hi there, i'm having this same issue but really hope to fix it so that i can use my new mouse.

but i'm so new to linux and i really hope you can teach me how to apply your kernel patch...

---

