---
title: "Sound Again"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by n17 on 2005-05-12
Hi all, I am new to Linux and have installed a few distributions over the last few weeks,  I think Ubuntu is great and I want to stick with it, however as with all the other Linux packages I have found that sound and sound cards seem to be the major problem for newbees.  I have placed a few posts, and thank you to those who have replied- but I am still having problems.

I have a on board S/card in a Compaq Deskpro en p2 400mzh, 256mb I have found that the card is a ES1869 Audio Device.

So far I have tried disabling the On/B sound and putting in a PCI - did not work (i did get a throbbing repeating sound though) also I have tried to following instructions form other postings,  but failed.  I have tried dowloading drivers but I think I stuffed up the unloading. 

I know very little about Linux or entering commands, loading files unpacking files etc, still I find some aspects confusing-   Has anyone got any suggestion what I should look at doing now? 
Thanks Rick

I don't want to return to Bill but it looks as though he's starting to win!!!!!!!!!!! (please let me know if I am out of my depth so I can stop bugging you all)

---

### Post by poofyhairguy on 2005-05-12
Ok. I'll be honest with you. I did my best to help you. I hit the internet and the forum with my best google skills. Seems like your card is old and the drivers don't really exist. I can't find them.

Recently I converted a friend to Ubuntu, he had the same problem (and ancient non-working sound card). With my help he fixed this problem in my favorite fashion- he bought a linux compatible sound card.

This site:

[http://www.pcpartsohio.com/Books.aspx?category_id=22](http://www.pcpartsohio.com/Books.aspx?category_id=22)

Will ship you a vortex sound card that he bought (and uses wonderfully in Ubuntu today) for $8 including shipping. Plug, reboot and play. This now becomes the cost of Ubuntu for you (and honestly $8 for an OS that works great isn't that much).

If you need more help or more info, don't be afraid to send me a PM. If this cost is too great and you go back to Bill's world then that is fine. At least you know what alternative exists.

---

### Post by n17 on 2005-05-12
Thanks for your time, i'll track that card down here in Australia and give it a go

---

### Post by poofyhairguy on 2005-05-13
You are welcome.

---

### Post by wvslkr on 2005-05-13
I have this onboard card working under Kubunto.
Just added [snd-es18xx isapnp=0] to /etc/modules and restart machine.
Worked for me  :) 
Good Luck. Cheers.

---

