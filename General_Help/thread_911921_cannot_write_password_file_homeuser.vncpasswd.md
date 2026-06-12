---
title: "cannot write password file /home/user/.vnc/passwd"
date: 2008-09-06
forum: General Help
---

### Post by Xubuntnoob on 2008-09-06
Hello!
I'm trying to make a file server, and I'm using a guide i found by Glider on bit-tech.net    [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1) 

I've made it to page 6 titled 'off with it's head!' and i'm having trouble getting past the back-end user creation or whatever it's called.

this is what i enter (exactly as told) and the results:

user@Server:~$ vncpasswd ~/.vnc/passwd
Password: 
Verify:   
Would you like to enter a view-only password (y/n)? n
Cannot write password file /home/user/.vnc/passwd


I apologize in advance for my noobishness as I am literally brand-new (less than 6hrs 'hands-on') to linux. 

Much thanks for your future help!

---

### Post by ryanhaigh on 2008-09-07
I haven't had this problem before so I don't know if this is what is causing your issue but perhaps the .vnc directory does not exist, try creating it with:
```
mkdir ~/.vnc
```
If it does exist check the permissions with
```
ls -la ~/ | grep .vnc
```

---

### Post by Xubuntnoob on 2008-09-08
awesome dude, it works!

tyvm

---

