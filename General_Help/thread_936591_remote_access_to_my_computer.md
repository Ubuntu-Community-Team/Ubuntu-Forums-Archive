---
title: "remote access to my computer"
date: 2008-10-02
forum: General Help
---

### Post by diamantis13 on 2008-10-02
Hi,
I have been using openssh to connect to my computer (ubuntu 8.04) and was able to do much of what I needed up to now.
I now need to run some GUI programs remotely but I do not know how.
Any suggestions? Thank you very much.

---

### Post by cariboo on 2008-10-03
IF you remote computer has a gui already installed you don't need to do anything extra, just use X forwarding. Start ssh like this:

```
ssh -X user@remote
```

Then type the name of the program you want to run.

Just as an experiment I downloaded and installed Brasero on my server wnich has no gui, and used it to burn an iso image to cd, It worked just like as if I was sitting in front of the computer.

Jim

---

### Post by wgrant on 2008-10-03
Alternatively, you can get your entire desktop remotely by clicking a few times in System->Preferences->Remote Desktop. Much simpler.

---

### Post by diamantis13 on 2008-10-03
Thanks!
I am going to try the -X option today! By the way, is the remote desktop as secure as ssh?

---

