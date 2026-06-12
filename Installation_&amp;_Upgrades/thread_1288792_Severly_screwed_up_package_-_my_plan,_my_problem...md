---
title: "Severly screwed up package - my plan, my problem..."
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by shaunsmith_99 on 2009-10-11
Well,

  I've been spending tremendous amounts of time learning and becoming comfortable in the bash command, but I have a problem that's got me stumped and I can't find a good solution.

 -I goofed up. I screwed  up. I made a major error. I went to install Ubuntu-Tweak, and I started with the package for Karmic. I use Jaunty. It didn't like that and it let's me know it. It crashed my laptop - and it cannot be removed by synaptic, add-remove, --purge, all the tricks I've seen. I can't install the jaunty package over it, and I need to remove it manually. Here is my plan..

  1. cd /var/lib/dpkg
  2. sudo cp available available.bad
  3. sudo cp status status.bad
  4. open available with txt editor
  5. remove all references towards ubuntu-tweak
  6. same with status
   7. cd info
  8. delete all files relating to ubuntu-tweak

  Good plan huh? I found these instructions online. however, I can't seem to get permissions to make changes to available or status - it throws permission problems at me - does thiss need to be done entirely through the terminal or can I somehow login as root and edit these important files?

Shaun

---

### Post by Partyboi2 on 2009-10-11
If you want to do it via the gui, then press Alt+F2 and in the box that opens type
```
gksu nautilus
``` After you have made any changes remember to close nautilus as nautilus will be open with admin rights.

---

### Post by shaunsmith_99 on 2009-10-11
> **Partyboi2 said:**
> If you want to do it via the gui, then press Alt+F2 and in the box that opens type
```
gksu nautilus
``` After you have made any changes remember to close nautilus as nautilus will be open with admin rights.


 Ugh - after x-number our hours I think I fixed it. 
  
  [I]#sudo-i
  
   [/I]Them I edited everything, and *rm -i *all the bad packages.


  Ugh - hopefully I can help some newbie fix nasty broken packages so they won't have learn the hard way (like I usually do)

  Man, I thought all those linux goons were just using the bash terminal so they'd look schmart - but I just realized how powerful that thing is. :)

---

