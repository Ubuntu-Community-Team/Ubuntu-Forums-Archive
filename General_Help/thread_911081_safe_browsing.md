---
title: "safe browsing ??"
date: 2008-09-05
forum: General Help
---

### Post by mack27 on 2008-09-05
Hi,
I just got an error in my mailbox that reminds of something i used to have with another account when i was still using windows. the thing is that the former one was a result of a virus or some kind of a rootkit or other malware. how do i check if the system is ok now? a few days ago i had to check one of my mailboxes that i do not use anymore as it got badly spammed. obviously i didn't open any unknown mail, but is there a possibiity sth got into my system?

---

### Post by Crafty Kisses on 2008-09-05
You can technically run ClamAV, but if you think you have a Virus I really wouldn't be worried, honestly.

---

### Post by mack27 on 2008-09-05
uuufff. that's good..

---

### Post by Crafty Kisses on 2008-09-05
Yeah, Ubuntu has iptables and all that good stuff so you really don't have to worry. :)

---

### Post by Sef on 2008-09-05
> I just got an error in my mailbox that reminds of something i used to have with another account when i was still using windows. the thing is that the former one was a result of a virus or some kind of a rootkit or other malware. how do i check if the system is ok now? a few days ago i had to check one of my mailboxes that i do not use anymore as it got badly spammed. obviously i didn't open any unknown mail, but is there a possibiity sth got into my system?

A virus can get in your email client.  It won't infect your system, but it could infect your friends' systems if they use Windows.

If you want to check root, download rkhunter either from Synaptic or the terminal (Applications > Accessories > Terminal) and type in this code:

```
sudo apt-get update && sudo apt-get install rkhunter
```

---

