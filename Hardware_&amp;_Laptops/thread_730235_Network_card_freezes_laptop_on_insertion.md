---
title: "Network card freezes laptop on insertion"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by dustyub on 2008-03-20
Okay, there are a few threads on these forums and on the internet elsewhere in which users have had a similar problem. The responses haven't been very helpful though. 

Hardware: 
Dell Inspiron 1100 laptop
Dlink air DWL-650 wireless network card
7.10 Gutsy Gibbon Kubuntu (I know there are Kubuntu forums, but the solution seems like it'll be applicable in either KDE or GNOME and I already have an account here) 

Basically, upon inserting the card, my computer freezes up. Removing the card doesn't help. The only solution at that point is hard reset. So, I'm in a catch-22 at this point where I can't work on the card without putting it in the computer and I can't use my computer if the card is inserted.

Starting the computer with the card already inserted results in the computer being unable to boot. 

IMPORTANT INFO: The card works fine, I've tested it on a windows machine and found that it worked perfectly. The problem is in linux (perhaps specifically K/Ubuntu as I haven't tested it on any other distribution).  

Is there something I can turn off/on to keep the network card from freezing everything up? 

Suggestions?

---

### Post by murphlaw on 2008-04-11
I only have a suggestion that might help you.

Try to disable the "LAN Controller" within your BIOS Setup. Here are the steps, that you can follow to do so:

1. Press F2 during Bootscreen
2. Goto Page 3 of 6 with "Alt+P"
3. Goto LAN Controller and press "Left" or "Right" to change the value to disabled.
4. Press "ESC" and press "Enter" to "Save changes and reboot"

Hopefully that helps you a little, eventhough I know, that this could be not the best solution.

---

