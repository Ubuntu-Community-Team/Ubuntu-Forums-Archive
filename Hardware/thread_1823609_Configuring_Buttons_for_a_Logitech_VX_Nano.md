---
title: "Configuring Buttons for a Logitech VX Nano"
date: 2011-08-12
forum: Hardware
---

### Post by bucpatr on 2011-08-12
I have a logitech VX Nano mouse that I've been using with Ubuntu for several years. I never had a problem with it until this week when it suddenly turned on horizontal scrolling all the time as though the button was stuck. I realize its a hardware issue with the mouse but I'd rather not have to replace it just because a feature I never use anyway starts acting funny.

What I need to know is, is there some way to disable the horizontal scroll buttons for this mouse in Ubuntu? I've seen lots of old posts outlining xorg settings for enabling features but I'm really not familiar enough with how xorg works to go experimenting with it. I need this machine for work so I can't afford to spend 2 days reinstalling everything because I made a syntax error in xorg.conf :confused:

Any help would be much appreciated.

PS: I'm using Ubuntu 11.04

---

### Post by bucpatr on 2011-08-15
Anyone?

---

### Post by henrixd on 2012-05-11
After mouse fell about 20 times onto floor ..I now have same issue, with debian tough. I solved it with..

1. aptitude install xinput

2. xinput list | grep 'id='

..and find your mouse from the list
*snip*
Logitech USB Receiver      id=14   [slave  pointer  (2)]
Logitech USB Receiver      id=15   [slave  pointer  (2)]
*snip*

3. xinput set-button-map your_mouse_id_here 1 2 3 4 5 0 0
..those zeros disable buttons 6 and 7 (horizontal scrolling)

4. put command 3. to .xinitrc or similar file to load on every boot

---

### Post by henrixd on 2012-05-12
```

#!/bin/sh
mouse='Logitech USB Receiver'
pattern='s/.*id=\([0-9]*\).*/\1/'
id=$(xinput list | grep "${mouse}" | head -n 1 | sed "${pattern}")
xinput set-button-map ${id} 1 2 3 4 5 0 0

```

---

