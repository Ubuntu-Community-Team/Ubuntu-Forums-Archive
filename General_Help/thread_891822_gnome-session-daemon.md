---
title: "gnome-session-daemon"
date: 2008-08-16
forum: General Help
---

### Post by ingeva on 2008-08-16
The above program has given me some concern.

I got a message that it wouldn't start, and my system did not perform normally.
I needed to re-install the system because too many things were not working, but unfortunately I don't remember exactly what and how.

After re-installing Ubunty (8.04) it happened once but after I restarted it hasn't repeated itself. So far.

I would like to know what could have caused this error, and how to avoid it in the future. Things like this typically happen when you need the computer most, and then you're REALLY in a hurry! :)

---

### Post by Naatan on 2008-08-16
I've never had this happen and I don't think it's a very common problem, can you think of any reasons why this might have happened.. eg. if the problem started occurring after you installed a new program then that's a big pointer.

---

### Post by ingeva on 2008-08-17
> **Naatan said:**
> I've never had this happen and I don't think it's a very common problem, can you think of any reasons why this might have happened.. eg. if the problem started occurring after you installed a new program then that's a big pointer.

I may have done something because I'm a new user and need to do some experimenting with settings etc.
I may have done something to make this happen, but it didn't manifest itself until restart, and then so many other things had happened as well. It's nearly impossible for me to figure out why it occurred.

Thanks for replying though.

---

### Post by Naatan on 2008-08-17
What you can try *if the problem occurs again* is before logging in you press the key combo: ctrl+alt+F1
You will get a fullscreen terminal, login to it and type:

$ sudo adduser Test

Answer all the questions given and when done press ctrl+alt+F7.. you will be at the login screen again, login as the user Test you just created and see if the problem occurs there as well.

If it does than the problem lies deeper than I suspect, if it doesn't it means your problem is directly related to your settings and you can go from there.

---

### Post by ingeva on 2008-08-17
> **Naatan said:**
> If it does than the problem lies deeper than I suspect, if it doesn't it means your problem is directly related to your settings and you can go from there.

Great idea! Thanks!

---

