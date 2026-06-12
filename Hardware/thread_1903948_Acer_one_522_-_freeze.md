---
title: "Acer one 522 - freeze"
date: 2012-01-03
forum: Hardware
---

### Post by Bruce_Chastain on 2012-01-03
Hi,

Last weekend I bought an acer one AO522, I believe is the full name, and so it came with windows 7 starter. When I couldn't change the wallpaper that put me over the edge. I went ahead and without doing much research installed backtrack 5. It worked good for a day or so but then started freezing randomly. And the whole time it was working I was struggling to get the headphones to work. Anyway then I decided that rather than being so cool with backtrack that maybe ubuntu would solve some of my problems. 

Sooo, I did a quick USB install of 11.10 and right after the install it worked great, no problems. But then the next day I turned it on it froze only a few seconds after getting to the desktop. I reset it a few more times with similar results. Eventually it wouldn't even make it to the desktop. Soo, then I tried installing netbook version 10.whatever, but it had all sorts of problems! including freezing after startup. Finally I decided to go back to regular 11.10. On the first install try it actually froze, but on the second for whatever reason it worked. 

As I remembered the first time it would let me use the computer computer without problems it only appeared to be after full power down and back up that the problems started. So I knew that I needed to do something while I could still work in the system. I went to these forums and it seemed that the network card might be causing some of the problems. With that idea, I decided to disable the network card from within the OS. After doing that I reset the machine and what do you know, it worked perfectly. So then I clicked to enable the card again and it froze right away. Reset it, still froze within second. Now I know it has to do with the network card...

I had read on the forums here that someone had said that they did something with the boot order and somehow that caused it to not freeze. So I went into the bios and enabled network boot and set the network boot to the top. Boom! fixed! And the headphones work!;)

*****************Cliff notes*****************
changing the boot order to put the network boot first fixed my problem 

Bruce
just another newb

---

