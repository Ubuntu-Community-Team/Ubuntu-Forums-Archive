---
title: "flash player installation problem"
date: 2008-09-30
forum: General Help
---

### Post by bala_hardy on 2008-09-30
hi. i am working with ubuntu-hardy. flash player is not working properly. let me know how to install a flshplayer in ubuntu

---

### Post by bala_hardy on 2008-09-30
i am using ubuntu hardy. flashplayer is not working properly. then how can i install flash player

---

### Post by bala_hardy on 2008-09-30
send me the reply in a quick session

---

### Post by Sef on 2008-09-30
>          send me the reply in a quick session     All answers should be posted in the forum, so that all may benefit.

>          i am using ubuntu hardy. flashplayer is not working properly. then how can i install flash player     Applications > Add/Remove > Show: change to 'All Available Applications' > Search: type: restricted > check the appropriate box > click apply changes > apply > close

If that does not work, then what version of ubuntu do you have, and how did you install flash player in the first place?

---

### Post by brookswm on 2008-09-30
Oh, oh, oh, I can help!  Okay, go to a site that requires flash, youtube for example, then click on get missing add-on.  It'll take you to the Flash website where you get 3 download options, I believe you want tar gaz (or something really close to that).  After that's downloaded open up your program manager and do a search for flash, scroll through those options until you see 'flash-notfree' or 'unfree' or something similiar and mark it for installation.  Once you've marked it apply it!  I'm new to Ubuntu, but I think that'll work, might want to get a confirmation or clarification first.

---

### Post by aysiu on 2008-09-30
This is how you do it:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

What method were you trying before?

---

### Post by brookswm on 2008-09-30
I dont mean to be the forum police, but I believe it's frowned upon to double post.  If you check your other post:
[http://ubuntuforums.org/showthread.php?t=934208](http://ubuntuforums.org/showthread.php?t=934208)

I responded with a sort of step by step newbie guide, since I'm a newbie myself.

---

### Post by maddog69 on 2009-08-16
> **Sef said:**
> All answers should be posted in the forum, so that all may benefit.

Applications > Add/Remove > Show: change to 'All Available Applications' > Search: type: restricted > check the appropriate box > click apply changes > apply > close

If that does not work, then what version of ubuntu do you have, and how did you install flash player in the first place?
 can u help me when i try to add stuff keep on getting this up dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. and when i try this it says command not found all i am trying to do is get my flash player working been at it for 2weeks now:confused::confused::confused:

---

### Post by aysiu on 2009-08-16
> **maddog69 said:**
> can u help me when i try to add stuff keep on getting this up dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. and when i try this it says command not found all i am trying to do is get my flash player working been at it for 2weeks now:confused::confused::confused:
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo dpkg --configure -a
```

---

### Post by lessgov2007 on 2009-08-16
Here's how I do it. 

Close all browsers.

Open the terminal

Type:
sudo apt-get install ubuntu-restricted-extras

---

### Post by maddog69 on 2009-08-16
> **lessgov2007 said:**
> Here's how I do it. 

Close all browsers.

Open the terminal

Type:
sudo apt-get install ubuntu-restricted-extras
ur are :KS:KS mate was at it for 2 weeks and u come along and 2min its donegive r self a pat on the back lol

---

### Post by maddog69 on 2009-08-16
> **maddog69 said:**
> ur are :KS:KS mate was at it for 2 weeks and u come along and 2min its donegive r self a pat on the back lol
do u know off eny program that joins films back together got on that came down in 3 files and want it on one disc if pos:)

---

### Post by oboedad55 on 2009-08-16
This is for hardy, jaunty works fine. I've got all the restricted extras installed and flash works in Opera but not Firefox. It looks like the shockwave player is installed and I can get audio from youtube for example, but no video. What's up?

Thanks!

---

### Post by earthpigg on 2009-08-16
> **oboedad55 said:**
> This is for hardy, jaunty works fine. I've got all the restricted extras installed and flash works in Opera but not Firefox. It looks like the shockwave player is installed and I can get audio from youtube for example, but no video. What's up?

Thanks!

this happens to me sometimes as well.

closing and restarting firefox usually clears it up.

---

### Post by oboedad55 on 2009-08-16
> **earthpigg said:**
> this happens to me sometimes as well.

closing and restarting firefox usually clears it up.

Been there, done that. Still no love!

---

