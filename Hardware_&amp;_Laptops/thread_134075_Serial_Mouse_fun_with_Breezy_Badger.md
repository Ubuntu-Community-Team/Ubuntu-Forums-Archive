---
title: "Serial Mouse fun with Breezy Badger"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by abel on 2006-02-21
Hello folks,

New to the world of Linux/Ubuntu. I'm currently experimenting with an older machine of mine and ran accross what seems to be a common error.

My serial mouse doesn't work.

Now...I found several threads on the subject. Some of the Virtual terminal attempts I've done haven't worked and I'm thinking they were for different versions of Ubuntu.

I went to WIKI but the edits only mention Warty and Hoary.

Which one will work with Breezy Badger? ( I'm not at home so I have to wait till tonight)

I'm actually having fun. I'm sure that once I sort this out Ububtu is going to rock!!

Any help would be appreciated!!



:rolleyes:


Update:

Trying WIKIs edit doesn't work because I don't seem to get the option to enter/edit the port.

....must dig some more.



Well this got me to the edit section....

sudo nano /etc/X11/xorg.conf

Scroll down through the file until you find the section for the mouse.
Change the line area that says
/dev/mouse/generic

to read /dev/ttyS0
Note: that 0 is a zero, not a big letter O

"Protocol" to "Microsoft"


AND BINGO!!! it works now....

---

### Post by abel on 2006-02-22
Fixed the serial mouse issue..... now to move on to Ethernet ( addind a card).....videocard ( Geforce2 Ti200 ) locked at 640x480 and sound ( didn't have any last night).

:rolleyes: 

I love tinkering....

---

