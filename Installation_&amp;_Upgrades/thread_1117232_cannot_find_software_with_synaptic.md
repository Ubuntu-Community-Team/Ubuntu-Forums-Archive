---
title: "cannot find software with synaptic"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by SpikeyMike on 2009-04-05
I have ubuntu running on my pc and it is working fine, just installed it on my acer aspire 3023wlmi and enabled restricted repositories etc, but when I try to search for software, for example, ndiswrapper and ubuntustudio it doesn't find anything, I know it should find these so I don't know what is going on, any advice?

Spikey

---

### Post by Partyboi2 on 2009-04-05
Have you tried reloading the package list before searching?

---

### Post by SpikeyMike on 2009-04-06
> **Partyboi2 said:**
> Have you tired reloading the package list before searching?

hi, yes I tried that, I also enabled all the repositories including the restricted ones but it still doesn't find the software.....

Spikey

---

### Post by Partyboi2 on 2009-04-06
Make sure Synaptic is closed and in a terminal.
```
 sudo update-apt-xapian-index
```
Then try synaptic again.

---

### Post by redbook4574 on 2009-04-06
Ive got the same problem have you had any joy??

---

### Post by redbook4574 on 2009-04-06
I just tried removing synaptic and reinstalling seems to have cured some of the issues although wcid still does not show.

---

### Post by SpikeyMike on 2009-04-07
> **Partyboi2 said:**
> Make sure Synaptic is closed and in a terminal.
```
 sudo update-apt-xapian-index
```
Then try synaptic again.

hi, thanks for your reply, I ran that command and it works fine now....

Spikey

---

