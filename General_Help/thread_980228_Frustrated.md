---
title: "Frustrated"
date: 2008-11-12
forum: General Help
---

### Post by rp_joe on 2008-11-12
Hello I am new to Ubuntu. 
I downloaded 8.10 both server and desktop when they were released. I just want to make a samba server. It should be no big deal. 
I installed server and could not understand how to do it. I installed the dexktop version 4 times. I found some instructns on the internet to "sudu apt-get install samba" It did not work. Sudu command not known. Coulds someone please give me a step by step method to do this? I just want a file server for my windows machines. All drivers load fine. The first thing I did was run updates. I don't know why this is so hard.

---

### Post by john183 on 2008-11-12
> **rp_joe said:**
> Hello I am new to Ubuntu. 
I downloaded 8.10 both server and desktop when they were released. I just want to make a samba server. It should be no big deal. 
I installed server and could not understand how to do it. I installed the dexktop version 4 times. I found some instructns on the internet to "sudu apt-get install samba" It did not work. Sudu command not known. Coulds someone please give me a step by step method to do this? I just want a file server for my windows machines. All drivers load fine. The first thing I did was run updates. I don't know why this is so hard.

the command should be
```
sudo apt-get install samba
```

sudo, not sudu

---

### Post by rp_joe on 2008-11-12
Thank you. 
Okay I followed these instructions: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

But now samba does not start. 
Starting samba daemons     [fail] 

the only changes I made were 

force user and group to my login name, I changed the netbios and workgroup. 

I have no idea why it will not start.

---

### Post by rp_joe on 2008-11-13
I found a problem in the config. I will keep working on it.

---

