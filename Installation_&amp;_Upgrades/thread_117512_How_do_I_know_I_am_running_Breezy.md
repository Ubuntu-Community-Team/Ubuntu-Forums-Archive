---
title: "How do I know I am running Breezy?"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by swong1 on 2006-01-15
Hi all,

Pardon a completely newbie question. I followed the instructions on the sticky thread and upgraded from Hoary to Breezy. But how do I know I am running Breezy? When I opened Synaptic and selected "Mark all upgrades", it appears to mark all the packages I have already upgraded. I didn't check them one by one, but the total memory to be installed is suspiciously similar to what I installed when I upgraded to Breezy. So my question is, did I actually upgrade to Breezy? The upgrade notifier also encourages me to upgrade to Breezy. So, I'm stumped.

p.s. I shut down the computer after downloading all the packages. I didn't reboot it immediately after downloading.

---

### Post by Galoot on 2006-01-15
```
uname -a
```

---

### Post by swong1 on 2006-01-15
Here's what I get running the code:

```
uname -a
```

Linux ubuntu1 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux.

I don't quite understand the kernel version, but the date indicated is the date I installed Hoary. So, I'm guessing I'm still running Hoary. What did I do wrong?

---

### Post by mo_x on 2006-01-15
cat /etc/issue

---

### Post by swong1 on 2006-01-15
[QUOTE=mo_x]cat /etc/issue[/QUOTE]

Output:

Ubuntu 5.04 "Hoary Hedgehog" \n \l

After 4 hours of downloading, and this!!?? Argh....
What did I do wrong?

---

### Post by Mustard on 2006-01-15
[QUOTE=swong1]Output:

Ubuntu 5.04 "Hoary Hedgehog" \n \l

After 4 hours of downloading, and this!!?? Argh....
What did I do wrong?[/QUOTE]

You could always do a distribution upgrade, rather than downloading a new ISO.  Have you got your internet working on Hoary Hedgehog?

Here is the wiki guide on upgrading Hoary to Breezy via the command line or even using Synaptic Package manager...
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

---

### Post by swong1 on 2006-01-15
[QUOTE=Mustard]You could always do a distribution upgrade, rather than downloading a new ISO.  Have you got your internet working on Hoary Hedgehog?

Here is the wiki guide on upgrading Hoary to Breezy via the command line or even using Synaptic Package manager...
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)[/QUOTE]

Internet is working on Hoary. I upgraded through apt-get. I followed the instructions listed on the very same site to the letter. Reinstalling...

---

