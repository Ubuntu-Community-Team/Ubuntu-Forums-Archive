---
title: "Login fails, even after a passwd reset"
date: 2008-10-18
forum: General Help
---

### Post by JackD on 2008-10-18
I've set up my Dad with a Ubuntu laptop. I've installed Yuuguu so I can give remote support.

However, he is unable to login. I have to do everything over the phone, until he can login, then I'll be able to remote it and help him.

We tried dropping into "recovery mode" and resetting his password, no luck.

His failure comes with the Gnome login screen. He types in his name (all lower case) and enters his password (no caps lock on), and he is prompted that authentication failed. "Incorrect username or password . . "

I've dropped him into the "recovery mode" a couple of times and even created a new account. No luck

Any ideas ?

______________________________________

OK, I was thinking too hard. I thought maybe the system had been accidentally set to, I don't know, maybe a Spanish language keyboard or something. But the more I thought about it, the more it didn't make sense. I had him drop into the recovery mode, then type in the passwd for his account. Only this time, I also had him test it by a login to the account. It failed ! He was mis-typing his password that he had just set. "Dad," I said "type in the new password, with one finger, one letter at a time." Voila. Worked.

---

### Post by cariboo on 2008-10-18
I'm not sure if it is Yuuguu that is causing the problem, but if that is the only thing you installed, I would uninstall it and try something that directly accesses the computer like vnc instead of going through somebody elese server. Tightvncserver is available in the repositories, or you can use the default remote desktop appliction that is installed by default in hardy.

Jim

---

### Post by JackD on 2008-10-18
Forget Yuuguu. I was trying to give too much detail. Sorry. 

My Dad cannot authenticate or login to his account on a Ubuntu system. In talking with him, I've been able to walk him through the steps to recreate his password (using the recovery choice on the Grub startup).

It still doesn't work.

It doesn't make sense to me that he can't put in a username and a good password and fail to login -- and I'm just trying to think that there could be something else happening that I'm not aware of.

---

### Post by JackD on 2008-10-18
Fixed !

we went over it very slowly. he was typing an error

---

