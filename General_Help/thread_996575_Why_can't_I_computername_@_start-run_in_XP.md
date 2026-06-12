---
title: "Why can't I \\computername @ start-run in XP?"
date: 2008-11-29
forum: General Help
---

### Post by Roasted on 2008-11-29
Using my XP Pro work laptop, I can't connect to my Ubuntu Intrepid machine. I have samba running, and normally I just use the static IP to connect. But I figured I should be able to use my hostname on Ubuntu... but XP doesn't recognize it.

Any ideas?

---

### Post by Roasted on 2008-11-29
So, I found this part in the smb.conf.



# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = X


I changed the netbios name from "intrepid" to "x"

Now, when I go to start - run and \\x, I get to my Ubuntu desktop. The odd thing is, if I go \\intrepid, I also get to my Ubuntu desktop.

Why is Intrepid still "tagged"?

---

### Post by doas777 on 2008-11-29
netbios caches host names based on boadcast learning.

if you type 
```
nbtstat -c 
```
in a windows terminal, it will show you the nbt name table on that machine. you can clear it and force a reload with 
```
nbtstat -R
```

after that, or a reboot, windows will no longer be able to resolve "intrepid" unless it is in your hosts file.

have fun

---

### Post by Roasted on 2008-11-29
Bingo. You were right. I came back here to post that after rebooting my laptop that it didn't recognize "intrepid" anymore.

Now it's working juuuuust fine. Thanks! :)

---

