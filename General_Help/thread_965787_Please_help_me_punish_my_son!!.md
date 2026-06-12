---
title: "Please help me punish my son!!"
date: 2008-10-31
forum: General Help
---

### Post by Jason Weiss on 2008-10-31
My Son is failing at school since I gave him his own ubuntu pc.

I do not want to ban him completely, so I have reinstalled his computer an set my own password so he need to ask for permission before he can login. 

Con some one suggest a way that I can make his session automatically log out after a predetireminded time, 

so kinda like this, once I log him in he will automatically be logged out in 1 hr. 

I thought of using crontab, but that sort of works on clock, I think i need some type of timer. 

and if we could make it so that he can not stop it and so that it would run automatically when he logs in it would be great.

I know that somewhere out there in ubuntu l;and there is a really really simple answer for this.

---

### Post by DGortze380 on 2008-10-31
[http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769)

---

### Post by spiderbatdad on 2008-10-31
```
man shutdown
```

---

### Post by sdennie on 2008-10-31
Another option would be to go to System->Preferences->Session and add the following command (name it something obscure):

```

sh -c "sleep 3600 && pkill -u $USER"

```

Replace 3600 (1 hour) with the number of seconds you want him to be able to use the machine for.  That's not foolproof but, if you are clever on how you name the process in Session and he figures it out, I'd say it's time to stop punishing him and instead ween him into the Ubuntu community.  ;)

Edit:
Forgot the -u for the pkill

---

### Post by Jason Weiss on 2008-10-31
> **vor said:**
> Another option would be to go to System->Preferences->Session and add the following command (name it something obscure):

```

sh -c "sleep 3600 && pkill -u $USER"

```

Replace 3600 (1 hour) with the number of seconds you want him to be able to use the machine for.  That's not foolproof but, if you are clever on how you name the process in Session and he figures it out, I'd say it's time to stop punishing him and instead ween him into the Ubuntu community.  ;)

Edit:
Forgot the -u for the pkill

lol that is the problem, he is hooked on the ubuntu community.

---

### Post by sdennie on 2008-10-31
> **Jason Weiss said:**
> lol that is the problem, he is hooked on the ubuntu community.

Haha.  I can think of worse things to be hooked on.  Still, if you are sufficiently clever in how you do the above (as in, put it into a script called like monitor-brightness and call the process Monitor Brightness in Sessions), he's not likely to reverse the changes.  Of course, if he is an Ubuntu addict, he'll likely find this thread and reverse anything you do anyway...  ;)

---

### Post by darco on 2008-10-31
how about your router? I have a Linksys 54GS and I use the Tomato FW....looks like its simple to setup...
darco

---

### Post by Jason Weiss on 2008-10-31
> **darco said:**
> how about your router? I have a Linksys 54GS and I use the Tomato FW....looks like its simple to setup...
darco

actually i do have a 54gl I will see if I can do this.

---

