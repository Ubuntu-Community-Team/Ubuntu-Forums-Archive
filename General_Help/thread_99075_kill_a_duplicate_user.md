---
title: "kill a duplicate user"
date: 2005-12-04
forum: General Help
---

### Post by ninotob on 2005-12-04
Right now, when I type "users", I have two users, both me.  I want to kill the extra one.  How do I do that?

---

### Post by aysiu on 2005-12-04
I have two of myself also. I think that's perfectly normal--don't know why, though.

---

### Post by wgrant on 2005-12-04
I believe it is normal. Remember that it prints the users logged on, so running something odd could easily make it list two. Here, I have more, as I have other clients connecting to this box.

---

### Post by ninotob on 2005-12-04
hmmmm ... interesting.  I have a hoary box running right next to it -- "users" shows only one user .... I just checked my other (3d) running ubuntu box, that one running breezy -- it shows 5 users but I have a bunch of shells open running stuff.  As for the Hoary, I had sshed into that one and nobody is otherwise logged into it.  I think I just embarrassed myself!  ;-)  You get a user entry for every shell it seems.

---

### Post by invalid on 2005-12-04
If you type ```
who
```instead of ```
users
```you will get a little more information to understand why there are multiple users with the same name.

Each terminal you are active in, should report you as a user of the system. Thus, if you have two terminals open, you should have two users. Remember, that your original terminal (:0) found at ctl-alt-F2 counts as one, and the terminal you are typing in at the moment, counts as one more.

I hope this is understandable
Cb

---

### Post by ninotob on 2005-12-04
Invalid -- yes it is very understandable and informative, thanks for the info on "who".

---

### Post by FLeiXiuS on 2005-12-04
Also check the output of w.  w is a wonderful command :-)

---

