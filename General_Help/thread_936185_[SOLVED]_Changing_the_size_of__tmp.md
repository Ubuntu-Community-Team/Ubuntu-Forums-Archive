---
title: "[SOLVED] Changing the size of  /tmp"
date: 2008-10-02
forum: General Help
---

### Post by Precipitous on 2008-10-02
How do I change the size of the /tmp directory, and how large should it be?

---

### Post by ibuclaw on 2008-10-02
What is outputted when you type in df?
```
df
```
Regards
Iain

---

### Post by Precipitous on 2008-10-02
tinivole - 

df give me the following:

  *see attachment

---

### Post by ibuclaw on 2008-10-02
Hmm...

I've never come across an "overflow" mount before. Are you using Wubi?

As for the size of it. It appears to be the size of your RAM.

1024 = 1GB. And 72% usage sounds about right with Linux and RAM, what with data being cached for later use.

Is there a reason why you need the /tmp directory?

Why not your /home folder?

Regards
Iain

---

### Post by Precipitous on 2008-10-02
tinivole - 

I am not using WUBI, this is just a standard install....  Anyway, the reason I am asking about the size of /tmp is that I was trying to download an update to Gimp from their website, but as soon as I click the link (even before I select what to do with the file) I get an error msg that there is not enough free space in /tmp. I have never saved anything to that directory, so I don't know why it is giving me this msg...

---

### Post by ibuclaw on 2008-10-02
As I said, it appears to be the size of your RAM. Do you have 1GB?

Nevertheless, two things you could try to gain space.

1) Sync and Drop Caches.
```
sudo sync; echo "3" | sudo tee /proc/sys/vm/drop_caches
```
Wait a minute, and try again.

2) Unmount the /tmp filesystem and create a symlink to your home folder.
```
mkdir ~/tmp
mv /tmp/* ~/tmp -R
sudo umount /tmp
sudo ln -fs ~/tmp /tmp

```

As for why the /tmp directory is being mounted as an "overflow"... could you perhaps post your fstab file up?

```
cat /etc/fstab
```
Regards
Iain

---

### Post by Precipitous on 2008-10-03
tinivole - 
Thanks for your help and suggestions...  When it came down to it, a simple reboot resolved the download issue, though  (yes, I feel like an idiot)...

---

### Post by yannrichet on 2012-06-20
To finish this discussion:
in fact, the "overflow" filesystem appears when your previous filesystem for /tmp is full. To not lock the system, ubuntu creates a virtual filesystem ("overflow") to let the /tmp remain available.

---

