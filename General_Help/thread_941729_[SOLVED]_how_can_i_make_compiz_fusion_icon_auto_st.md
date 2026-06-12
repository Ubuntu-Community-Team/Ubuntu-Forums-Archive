---
title: "[SOLVED] how can i make compiz fusion icon auto start at login?"
date: 2008-10-08
forum: General Help
---

### Post by chriskin on 2008-10-08
well the title says it all

can someone tell me how to make compiz fusion icon auto start at login?
i "need" it on my panel

---

### Post by Steve1961 on 2008-10-08
> **chriskin said:**
> well the title says it all

can someone tell me how to make compiz fusion icon auto start at login?
i "need" it on my panel

I don't use it myself but I think the command too start it is fusion-icon (try this in a terminal to test).  If that works just add it to System/Preferences/Sessions

---

### Post by caleb12 on 2008-10-08
alt + F2

ln -s /usr/bin/fusion-icon /home/YOUR_USERNAME_HERE/.config/autostart/fusion-icon

simple 'nuff?

---

### Post by jerome1232 on 2008-10-08
> **Steve1961 said:**
> I don't use it myself but I think the command too start it is fusion-icon (try this in a terminal to test).  If that works just add it to System/Preferences/Sessions

Yeah just add fusion-icon to you sessions, it's how I do it.

---

### Post by chriskin on 2008-10-08
thanks :) i am going to try it now

---

### Post by chriskin on 2008-10-08
ok it work
i will mark the thread as solved

---

### Post by pappfer on 2010-01-17
I have a little bit different question about Fusion Icon, I just didn't want to start a new topic for it.

So I wonder if it's possible to make Fusion Icon to save the settings. I mean when I set window manager to Metacity and restart my PC Metacity should start. If I had Compiz set in Fusion Icon then Compiz should start.

---

### Post by pappfer on 2010-02-04
No one knows? :confused:

---

### Post by JohnFante on 2010-02-09
Have the same problem. Have not yet found a soulution.

---

### Post by crasbelize on 2010-07-19
> **JohnFante said:**
> Have the same problem. Have not yet found a soulution.


ok...this is what I tried and it work as far as starting up goes.

I realized that I had to run compiz-fuzion twice then I have 2 right click on Compiz Fusion Icon in the upper righthand coner, then click on RELOAD WINDOW MANAGER.  

so In STARTUP APPLICATIONS....I created 2 entries.  

But for the command I put 'fusion-icon --no-start' and it worked.

NOW....anybody knows the terminal command to reload compiz-fuzion?????  That would help me out a lot....:)

  Thanks.

---

