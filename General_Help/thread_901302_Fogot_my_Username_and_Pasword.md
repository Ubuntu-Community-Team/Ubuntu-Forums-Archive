---
title: "Fogot my Username and Pasword"
date: 2008-08-26
forum: General Help
---

### Post by uti on 2008-08-26
Hi to everyone!!!


I am a brand new ubuntu user and I set-up in my pc the v.8.04 in the begin of July since then because I lost the user name & password codes I can't came in the windows ubuntu...

Pls give me the right procedure step by step so to recover the codes, instead to set-up again the Linux-uduntu from the begin...

The language which I have set-up them is the English 

I am waiting for your help...

kind rgds

Lambros

---

### Post by dragos240 on 2008-08-26
> **uti said:**
> Hi to everyone!!!


I am a brand new ubuntu user and I set-up in my pc the v.8.04 in the begin of July since then because I lost the user name & password codes I can't came in the windows ubuntu...

Pls give me the right procedure step by step so to recover the codes, instead to set-up again the Linux-uduntu from the begin...

The language which I have set-up them is the English 

I am waiting for your help...

kind rgds

Lambros
Try this
Link deleted, becuase of bad command. I didn't even search the thread, now i did and it had a VERY bad command to it. So, i removed it

Although, try going into root and changeing the password account from there

---

### Post by WRDN on 2008-08-26
Boot into Recovery Mode, choose the option to drop to the root shell (its the second option of three). Now, type:

```
cd /home
```

Then:

```
ls
```

The folders listed are the same as the usernames, unless you manually altered the names.

Now, type:

```
passwd [username]
```

Enter the password you want twice, and type exit. Then select the option to continue normal booting. You should now be able to login.

---

### Post by uti on 2008-08-26
Thank you very much...
Your help was great...
I fixed my system...

---

