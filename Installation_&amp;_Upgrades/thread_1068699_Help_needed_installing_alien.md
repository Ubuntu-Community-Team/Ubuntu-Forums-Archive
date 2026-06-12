---
title: "Help needed installing alien"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by martc on 2009-02-13
Hi i'm new to linux and trying to learn to install things but I am having trouble installing alien.
 when i type sudo apt-get install alien it starts building dependency tree but then there are a lot of files that come up as 404 not found, terminal suggests; E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
have tried to update but then get ;E: Some index files failed to download, they have been ignored, or old ones used instead.
 can anyone help please.

---

### Post by x33a on 2009-02-13
it seems that the server you are using isn't up at the moment. error 404 not found suggests that. try some other server or try sometime later.

---

### Post by martc on 2009-02-13
this isnt a one off problem, i've been trying to install this program for about two weeks now and get the same message every time.

---

### Post by x33a on 2009-02-13
which server are you using?

have you tried changing the servers. and, have you been able to download updates in the meanwhile?

to change servers, go to system->administration->software sources.

after that run sudo aptitude update. and try the download again.

---

### Post by 5BallJuggler on 2009-02-13
what software sources are you using? your set up should be like these:

---

### Post by martc on 2009-02-13
Thanks for trying to help, I am grateful, I have just switched from the South African server to the main server but still get the same message, have taken some screen shots to show messages that I keep getting.

---

### Post by howlingmadhowie on 2009-02-13
> **martc said:**
> Thanks for trying to help, I am grateful, I have just switched from the South African server to the main server but still get the same message, have taken some screen shots to show messages that I keep getting.

i think the problem is that you're still using feisty. feisty was to be supported for 18 months and i think the servers have now been partly switched off. i'd recommend updating to hardy or intrepid.

---

### Post by x33a on 2009-02-13
one thing i noticed was that you are using feisty fawn. it was supported only till oct. last year i guess. this issue might have something to do with that.

i urge that you upgrade to 8.04 LTS or 8.10 for better support and security updates.

edit: well howlingmadhowie said the same thing :D

---

### Post by martc on 2009-02-13
ok thanks I guess i'll have to upgrade. our problem in S A is that they cap your usage and i was using a lot of my download limit for other things but still the os must take priority i suppose.

---

### Post by howefield on 2009-02-13
> **martc said:**
> ok thanks I guess i'll have to upgrade. our problem in S A is that they cap your usage and i was using a lot of my download limit for other things but still the os must take priority i suppose.


Send for a free cd from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Of course the problem then would be the wait. But maybe you can live with that.

---

### Post by martc on 2009-02-13
thanks, i just looked at the download 700mb, thats a third of my monthly cap:eek:, so yes i have just put in an order for the cd, is it a good idea to back up everything before upgrading or will everything transfer to the new version?

---

### Post by howefield on 2009-02-13
Backing up your files is a no brainer, no matter what you plan to do with your computer. 

You could make an image of your drive, in order that if it does goes pear shaped, you are able to get back to exactly where you started., bearing in mind that your current version is now unsupported, any updates that you have already downloaded would be lost to you as the repository for 7.04 is gone.

---

