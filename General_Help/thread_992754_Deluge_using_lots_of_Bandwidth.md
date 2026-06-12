---
title: "Deluge using lots of Bandwidth"
date: 2008-11-25
forum: General Help
---

### Post by PoopyTheJ on 2008-11-25
When I run Deluge my System monitor shows a very different upload rate than that shown in Deluge itself. I can't get any download speed because all my upload is being used and I can't find for the life of me what's using the beandwidth. Are there any tools to dig a little deeper into my network bandwidth utilization, or active connections to figure out what is causing this huge upload and where it's actually coming from? The image below shows the disconnect between what the two programs show as my upload usage.

[IMG]http://img444.imageshack.us/img444/2061/delugewtfwk4.png[/IMG]

---

### Post by PoopyTheJ on 2008-11-25
Seriously, no one?

---

### Post by Keithamus on 2008-11-25
You have 962 open connections, which is probably killing your router. Take the number of open connections down from probably minus one to around 100. You also need to forward your ports because it looks like your deluge is having its ports blocked ("No incoming connections" at the bottom).

Lowering your connection tends to give you "better quality" connections and will lower the work your router has to do; so both your download speeds for deluge and your general internet speeds will go up.

Im not sure about the disparity between your system monitor and deluge -- perhaps you have updates downloading in the background?

---

### Post by PoopyTheJ on 2008-11-25
No there was nothing running in the background. I assume by open connections changing from -1 to 100 you meant in Deluge preferences. Which I did so we'll see how it goes. Thanks!

---

