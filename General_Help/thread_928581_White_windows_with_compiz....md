---
title: "White windows with compiz..."
date: 2008-09-24
forum: General Help
---

### Post by SilverAdder on 2008-09-24
I'm running compiz with an ATi graphics card. Has worked fine for a while. Today it somehow "broke". It still works but in some situations, when alt+tabing or unfolding the cube, the windows are white, as seen in the attached screen shot. You can still se the border around the window, such as the title, but the contents are just white. Any ideas what I did, or how i can fix it?

---

### Post by SilverAdder on 2008-09-25
bump

---

### Post by loomsen on 2008-09-25
I'd tell you what I know, if you'd tell me first.

Jezz guys, and I apologize in advance that its you where I gotta say it, but how should anyone know from just one screenshot?

Oh, well, ok, an ati, known for making trouble. What kernel, which driver, whcih distribution and so on... I live in Germany, even in the north of it. But I still can't have a look over your shoulder.

So, not only you, but you too, bear in mind, you gotta give some to get some. And, if you think twice, it's a win win situation for you. Millions of buisness administration students dream about being in such a situation every night. ;) Don't waste it.

---

### Post by SilverAdder on 2008-09-25
Sure, I'm sorry. I'm running Hardy, don't exactly know the kernel, fully updated, with the latest ati proprietary driver, 8.9, installed with the instructions form the ati site. Only way that worked for me. 
It has worked fine for a while. I tried a few compiz settings and now a few of them results in the white dekstop or windows, as is seen on the screens. The first is just alt+tabing with "application switcher" where the contents of the windows turn white, but not the borders. The other is when unfolding the desktops with "dekstop cube", where it all turns white. Just turning the cube, with the mouse, works fine, as does using "shift switcher" or "ring switcher" for alt+tabing. 
I hope this helps you. If you need more info just let me know, im pretty new at Ubuntu and I'm not sure what else would help you.

---

### Post by loomsen on 2008-09-25
OK, as I mentioned, ati drivers use to be kinda problematic. I have a nvidia, but a gd friend of mine had to fight pretty hard to make it working. 
I'm actually running debian and intrepid, my debian, tho unstable seems to fully support my nvidia, without any problems. Anyway, I wasnt able to compile 2.6.27 kernels for my graphics card. Installing Intrepid installed the driver without a big problem, tho I get screens like the second one you posted here n there too. Like every 2-3 days or so. My Computer is running all the time, 24/7 I should mention.
So, I guess this leaks, dont know how to name it, are due to non-free drivers and the bleeding developement edge, which rarely get along well. Usually stuff like that happened, if it did, always when my screen was about to be initialized/when I dropped to a terminal or stopped gnome from cmd line. I think, and I'm in pretty cheerfull spirits, that this issues will be fixed with one of the next updates for Intrepid. I'll just wait and see what will happen, my buddy I mentioned earlier, the one with the ati, upgraded to intrepid too, and hasn't reported any problems ever since.(he is running a radeon X1700 btw) Give it a try, maybe it will work.

*edit*
BTW, 
uname -r 
prints the currently booted kernel :)

---

### Post by SilverAdder on 2008-09-25
I'm running a mobility x1600 which has worked fine aside from the obligatory screen flashing when running demanding 3D. On the other hand, i don't really do that on my Ubuntu, its why i dual boot to windows; to play games. 

Intrepid isn't release yet and since i also use this install for school, learning server technology in *nix and windows, its probably a bad idea to start experimenting and messing up this install. Besides, Intrepid will be released in a final in a month or so, so I'll just wait. Looking forward to it though. 

Thanks for the help. Next time I'll try and be more specific from the get go.

---

### Post by loomsen on 2008-09-25
You're welcome, and as I said, nothing personal. Well, that must be it, I dont play at all. Well, Civ4, but very rarely, and it works fine with wine anyway. So I guess I'm the complete opposite of you, as bleeding-edge-addict. Well, I'm looking forward to my first meeting with the anon-dev-addicts, should get better soon :D

However, have a nice day :)

---

### Post by psychoelf on 2008-10-05
Same problem here on a Gateway 6850FX laptop with Radeon 2600HD mobility.  I switched to the "Ring" switcher for Alt-tabbing and works fine now.  Had to turn off the other switchers.  Ctrl-Alt and down arrow still give me white windows though (exactly like your screenshot).  Dunno how to get a screenshot as I have to hold down Ctrl-alt to keep it open.  I don't think its a memory leak problem as it does it as soon as I login.  Oh well, at least the cube works :) .

---

### Post by SilverAdder on 2008-10-06
I never realy liked the cube anyway, not for real work. It takes to long to use so that doesnt realy bother me. I feel the same about the ring switcher and the other fancy one, dont remember the name, but I'll live :)

I just used the screenshot tool and set it to take the screenshot a couple of seconds after i pressed the button.

---

