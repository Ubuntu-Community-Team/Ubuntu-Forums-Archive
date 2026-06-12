---
title: "Attempting to change MAC address returns &quot;Too many open files in system&quot;"
date: 2016-04-12
forum: Hardware
---

### Post by ihatewindows522 on 2016-04-12
Hello all.
I've started delving into this issue on LinuxQuestions.org, but I came here because I could really use some help specifically with Ubuntu.
I've went through most of my problem [here]("https://www.linuxquestions.org/questions/showthread.php?p=5529885#post5529885"), but I'll quickly sum it up for you guys: I had locked myself out of my own router, and thought a quick MAC spoof would let me in. Ubuntu wouldn't allow it, but Kali did and I was able to re-add myself to the whitelist. But I'm still curious about why Ubuntu wouldn't let me change the MAC, even in single user mode. Kali is based on Debian, so it isn't that much different under the hood, so why will Ubuntu not permit the change? And how can you change the MAC under Ubuntu?
Thanks in advance.

---

### Post by ihatewindows522 on 2016-04-14
Bump. Still have the issue.

---

### Post by QDR06VV9 on 2016-04-14
See if this helps..
[http://askubuntu.com/questions/81648/how-do-i-change-spoof-my-mac-address-and-easily-switch-between-multiple-ones](http://askubuntu.com/questions/81648/how-do-i-change-spoof-my-mac-address-and-easily-switch-between-multiple-ones)



EDIT: Try Macchanger available in the repositories. Install with: 
```
sudo apt-get install macchanger
```
or through Ubuntu Software center.
Hope this is helpful

[ ]("http://askubuntu.com/questions/81648/how-do-i-change-spoof-my-mac-address-and-easily-switch-between-multiple-ones")

---

