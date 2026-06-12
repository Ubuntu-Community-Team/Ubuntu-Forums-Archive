---
title: "Driver? Lexmark X6170 Printer"
date: 2010-03-27
forum: Hardware
---

### Post by paddy.melon on 2010-03-27
Hey guys, are there any drivers or, ways to get this printer going? It is a part of the Lexmark X6100 family (they all share the same driver(s) under windows, so might be similar). Details:
[http://www.lexmark.com/US/products/overview_/0,1224,MzUxNHwx,00.html](http://www.lexmark.com/US/products/overview_/0,1224,MzUxNHwx,00.html)

Any ideas would be greatly appreciated, thanks

---

### Post by oldsoundguy on 2010-03-27
If this does not work, you have what some call a doorstop or truck chock.  Lexmark does not support Linux .. not even lip service from the home of the 10 buck printer that sells for 50 bucks.

[http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/](http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/)

---

### Post by paddy.melon on 2010-03-27
> **oldsoundguy said:**
> If this does not work, you have what some call a doorstop or truck chock.  Lexmark does not support Linux .. not even lip service from the home of the 10 buck printer that sells for 50 bucks.

[http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/](http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/)

sweet, thanks, shall try it out and, get back to you if it worked. 

Just as a side note, say I have a windows PC on the network and, it was configured with the appropriate drivers (I'm not very good with Samba) is it possible to send print jobs there and, use it as a normal printer within Ubuntu?

---

### Post by paddy.melon on 2010-03-27
YES! It worked! Thank you so much! (just, btw, if anyone needs help and, are getting an error message:
just run the script and, at the end, it will look like it failed, don't worry. When It's done, type:
sudo /etc/rc2.d/S50cups restart

Then, go to System -> Administration -> Printing and, right click the printer there that says z55 or something to that effect. Right-click, go to properties and, change the Device URI (option on the main page) so, hit browse and, it will load for a bit, then at the side you'll see Lexmark X6100 or something similar (if clicked, says USB port). Select this and, you're done. You can now print a test sheet or, anything else! Awesome

Note: these instructions work on Karmic. Only thing the script doesn't do is restart Cups (the name in rc2.d changed) and, it is unclear on teh guide how to change the URI
)

Anyway, awesome I got my printer now! THanks!

---

