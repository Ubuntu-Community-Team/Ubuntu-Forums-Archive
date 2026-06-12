---
title: "Boot without network"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by neonlug on 2006-07-07
I have searched with no luck to find an answer.

I have a notebook that I use often without a network attached.  How can I set the computer to NOT try starting anything but lo?

Every time I boot I wait for 4 or 5 minutes to boot.  It is now to the point I need to fix it as it is driving my crazy.

BTW: in /etc/network/interfaces I have removed all instances of auto, sans auto lo.

Thank you in advance for any assistance you can give.  I am sure this has been answered befor, but in my frustraded state I can not locate that answer.

---

### Post by Dr. Nick on 2006-07-07
When you have no network you can push ctrl+c to skip loading, Also if you are using gnome then open up the network control panel and hit your lan card, and uncheck the box that says "enable this connection" 

Just remember you did that for the times you need the card.

Maybe someone has a more elegant solution though.

---

