---
title: "[SOLVED] Missing Memory, Running out of space"
date: 2008-10-30
forum: General Help
---

### Post by gleble on 2008-10-30
When I look at the properties of my main disc it tells me I have used 16.6Gb
It also tells me that I have only 3.4Gb left. It is a 52Gb disc, where are the other 32Gb.

I recently deleted alot of videos because I've burnt them to DVD but when I deleted them they did not appear in the Deleted items. 

When I delete videos the memory gets smaller.

---

### Post by gleble on 2008-10-30
I've taken a screenshot of gparted so you can see the state of my disc. Hope it helps[IMG]http://climatecalm.org/Screenshot.gif[/IMG]

---

### Post by plucky on 2008-10-30
> **gleble said:**
> When I look at the properties of my main disc it tells me I have used 16.6Gb
It also tells me that I have only 3.4Gb left. It is a 52Gb disc, where are the other 32Gb.

I recently deleted alot of videos because I've burnt them to DVD but when I deleted them they did not appear in the Deleted items. 

When I delete videos the memory gets smaller.

This [thread=898573]Check your trash thread[/thread] might help.

Good Luck

---

### Post by gleble on 2008-10-30
The "Check your trash" link in the last post gave me the answer.```
sudo find / -name '*' -size +1G
sudo find / -name '*' -size +500M
```Finds all your big files shift+del deletes them.

---

