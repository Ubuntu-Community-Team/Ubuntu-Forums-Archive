---
title: "Firefox 3.*.* on EeePC"
date: 2008-11-19
forum: General Help
---

### Post by AlanR8 on 2008-11-19
Just an advisory here for those of you using FF on an EeePC 4Gig.

I installed the release version of Kubuntu Ibex and all went well. A few tweaks to get the wireless running but what the hey........

However, I found Firefox incredibly slow to load to the point of being usable. Desktop effects, full Compiz, folder view, all no problems.

Anyway....I borked it on Monday evening, trying to be to clever, and did a full reinstall. I noticed straight away that FF was much more responsive on a clean install. I then added the Google Tool bar and all was still well. But, when I installed the StumbleUpon tool bar I was back to sludge on load times.

Anyone any ideas why this may happen? It works well on my Sony but the Eee seems to suffer badly. BTW, the Eee has 2 gigs of RAM.

---

### Post by bornagainpenguin on 2008-11-20
The guide [here](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive) will probably help you out.

I've found that by mounting /tmp and /var/tmp as tmpfs I get less crud on my SSD, plus if I follow the guide [here](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive#Optimize_Firefox_Cache) I can have my firefox cache in RAM and that gives me a real boost!  Try it out and see if it helps!

--bornagainpenguin

---

