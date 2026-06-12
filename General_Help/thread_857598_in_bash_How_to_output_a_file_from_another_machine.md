---
title: "in bash: How to output a file from another machine?"
date: 2008-07-12
forum: General Help
---

### Post by iimuhin on 2008-07-12
Hi all,

I have a file on another machine. I must output its content to screen like:

scp [email]username@machine:~/somefile1.txt[/email] > screen

Thanks

---

### Post by iimuhin on 2008-07-12
ssh username@machine 'cat /home/username/somefile1.txt'

---

### Post by dcstar on 2008-07-12
> **iimuhin said:**
> ssh username@machine 'cat /home/username/somefile1.txt'

Please mark the thread as solved so people don't waste time trying to help you.

---

### Post by Dr Small on 2008-07-12
> **dcstar said:**
> Please mark the thread as solved so people don't waste time trying to help you.
Or you can help him out, and add the 'solved' tag to the thread. That's what I do when I stumble across Solved threads, now-a-days. ;)

---

