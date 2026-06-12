---
title: "7 button mouse"
date: 2005-11-15
forum: General Help
---

### Post by [2]BoxingFiend on 2005-11-15
i have one of those microsoft intellimouse usb mouse

so i changed xorg.conf to point the mouse to /dev/input/mice
add buttons to 7, and ZAxisMapping to 6 7

I have also ran xmodmap -e "pointer = 1 2 3 6 7 4 5" so i have the scroller, and added that line to $HOME/.Xmodmap.  but for the life of me button 4 and 5 does not map to the back and forth in the browser.

do i need to install imwheel?

tnx

---

### Post by Curlydave on 2005-11-15
Yes, you do need to install mwheel. This is a very basic feature that needs to work right out of the box, but they went ahead and released breezy without it. :(

---

### Post by [2]BoxingFiend on 2005-11-15
tnx,

install imwheel and ran imwheel -f -k -b "67" and added imwheel to startup program. still can't get back and forth button..

bah.

---

