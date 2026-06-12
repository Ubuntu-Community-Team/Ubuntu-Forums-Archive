---
title: "DVD problem"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Bazzaah on 2007-03-17
I have a problem and wonder whether someone could help me with it please.

I'm trying to get a game to work through wine but my Edgy Ubuntu install doesn't work. The DVD player is good as I can play the game and watch DVDs under Windows.  I have the codecs installed. Ubuntu knows that there is an Asus DVD player there.

The terminal command ls -l/dev/dvd  yields:

lrwxrwxrwx 1 root root 3 2007-03-17 12:10 /dev/dvd -> hdd


I saw one thread  which described a similar problem and which suggested a symlink problem was the likely cause - are there any good guides to solving those problems?

Thanks in advance for any help.

---

### Post by mikewhatever on 2007-03-17
From what I can understand, nothing is wrong with Edgy. The ls output you posted is not an error, so it looks more like wine problem. Have you tried checking wine forums? What game are you trying to play? Have you install it or does it not require installation? Are there any error messages? Can you watch DVDs in Ubuntu? Obviously, you're not giving enough information.

---

### Post by Bazzaah on 2007-03-17
OK, Edgy is just fine. The one problem I have is that my DVD player will not work under Edgy for any DVD product. While Edgy seems aware of the fact that the DVD player exists, it does not play DVDs, whether game or movie. The DVD player works as it works in Windows for both games and movies. 

The game concerned is a flight sim, Il2-46, fwiw, but it is too early to say what issues I may or may not encounter with Wine. But that's by the by, the basic problem is that my DVD player doesn't work under Edgy. I think it worked under Dapper but honestly don't recall if I have played any DVDs since I installed Edgy.

It's a problem I've seen hinted at on a number of different threads on this and other forums but none have been answered - the only clue I could see to the problem was perhaps that it is some kind of symlink problem but nothing beyond that. Perhaps the output from -l/dev/dvd suggests otherwise, I don't know.

When I look in the /dev folder I see one dvd applet and one hdd applet if that helps.

Thanks for any help you can provide.

---

