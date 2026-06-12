---
title: "Cache more?"
date: 2008-07-15
forum: General Help
---

### Post by anotherdisciple on 2008-07-15
I'm using about 1/4 of my total RAM. How can I make Ubuntu cache more? Would it be worth it to have it preload anything? Like applications, etc.? 

I have swappiness set to zero. My computer is fast... but when I open an application a second time... it does it almost immediately. It would be nice to have it do this with more things.

What are the possibilities? How can I up the amount of RAM being used as cache? What type of items can I have it load into cache?

---

### Post by chrisccoulson on 2008-07-15
AFAIK, there isn't anything else you can do, other than running preload (available in the repositories, but I've never noticed any benefit of using it). Your RAM should be close to 100% used after a few hours.

Are you sure Ubuntu is only using 1/4 of your RAM. What does:
```
free -m
```
say after it has been running for a few hours?

---

### Post by anotherdisciple on 2008-07-16
hmmm... pretty slick... it IS using most of it! Apparantely the system monitor doesn't report cache... which confuses me.

You see... when I first start my computer I'll be using say 250mb of RAM with compiz and all that jazz. After using it about an hour I can close everything and it will now be using 400mb. I used to think that the other ~150mb was accounting for cache memory. I guess not.

Also, if you add up all the RAM that each program is using in the System monitor (even when you select to show all processes).... it doesn't add up. I have heard that this is because they share some things. I don't know how that works exactly.

So, I don't have to fix the cache thing... it's working just fine. Now I'm just curious. Can someone tell me how all this memory stuff works... Just for the fun of knowing it?

---

