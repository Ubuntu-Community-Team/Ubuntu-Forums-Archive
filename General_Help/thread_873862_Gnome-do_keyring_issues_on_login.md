---
title: "Gnome-do keyring issues on login"
date: 2008-07-29
forum: General Help
---

### Post by unabatedshagie on 2008-07-29
I have my system set up to log me in automatically.

I also have gnome-do set to start on login.

If I have any of the plugins activated that store a username and password like twitter, gmail contacts etc I have to type in the password at login.

If I turn of automatic login in and login manually I don't have this problem.

Is there a reason that this should happen and more importantly is there any way of stopping gnome-do asking for my password on login?

---

### Post by deformation on 2008-07-30
Same problem here, I guess the cause is yesterdays update. help anyone?

---

### Post by unabatedshagie on 2008-07-30
I don't think it's tied into yesterdays update.

I've been having this problem for a month or so at least.

---

### Post by deformation on 2008-08-01
Bump


can you file a bug for this issue on launchpad? if so please post the link here too.

---

### Post by aliencam on 2008-08-07
I have the same problem, only I do not login automatically, I use a thumbprint reader to log me in.

---

### Post by Chonnawonga on 2008-08-22
Anyone come up with a solution to this yet?

---

### Post by wanfahmi on 2008-09-16
me three,
It's quite an annoyance that every time I login, I have to type in the password

Hope somebody has an answer for this issue.

---

### Post by redoranges on 2008-09-27
I'm getting the same issue, its more of of an annoyance than anything else but i'd like to get an answer.

---

### Post by andresmh on 2008-10-26
I have the same problem on Intrepid.

---

### Post by lifestream on 2008-10-31
Same here, since Intrepid. Wish we could disable Keyring somehow, for me, it just gets in the way.

---

### Post by woodenfox on 2008-12-04
Same thing here... I've been trying to figure this one out for a while... quite a long while actually.  I'd rather login at startup (without the autologin)... since you have to put in the password anyway #-o 

If anyone finds a workaround for this... post it... until then I'm tempted to simply remove gnome-do extensions that require passwords...

I turn my EEE pc on and off seven or eight times a day... tedious.

---

### Post by Chonnawonga on 2009-02-09
OK, here's a solution, but there's an inherent security risk, as you'll see.

1. Open seahorse (type "seahorse" into a terminal or in the Alt+F2 dialog, or go to Applications -> Accessories -> Passwords and Encryption Keys)

2. Go to Edit -> Preferences

3. Click on the "Login" keyring, then the "Change Unlock Password" button

4. Type in your usual password in the "Old password" box, and then nothing in the "Password" boxes. That's right: nothing.

Now you'll get a security warning that you're about to leave your passwords on your system unencrypted. So there's the security risk... but if you do it, you'll get away from the annoying password prompts.

It worked for me, anyway.

---

### Post by digitalmusic on 2009-05-20
Hope this is of some use to you - it worked for me.
I was having the same problem as the rest of you.
All I did was disable the microblogging gnome-do plugin - password problem vanished.

---

