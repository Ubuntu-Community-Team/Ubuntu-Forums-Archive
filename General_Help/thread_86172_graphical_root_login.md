---
title: "graphical root login"
date: 2005-11-04
forum: General Help
---

### Post by VyRuZ on 2005-11-04
Yes yes, i want to login as root. DO NOT TELL ME IT'S UNSAFE. I know. It's the only way i can fix my problem.
I'm running Kubuntu 5.10 and i googled for enabling root login in kde , but nothing interesting showed up.
How can i make KDE Login as root ??

---

### Post by Kyral on 2005-11-04
Well, I am going to tell you its unsafe, because it cannot be stressed enough.

I really wanna help, but I also wanna avoid telling you how to login as root. Perhaps if you told us your problem we could find a way around logging in as root?

---

### Post by kaptainlange on 2005-11-04
Hey there.  First you need to set your root password.

Open up a console, and type:

#sudo passwd root

Enter the password you would like for root.
Then you need to edit the file /etc/kde3/kdm/kdmrc.

I prefer nano, use whatever you like.

#sudo nano /etc/kde3/kdm/kdmrc

Then edit the part that looks like this.

# Allow root logins?
# Default is true
AllowRootLogin=false

And set that to true.  Save, and log out.  My memory fails me, so im not sure if you have to restart kdm, but give it a try.

Hope that helps.

EDIT: 

[QUOTE=Kyral]Well, I am going to tell you its unsafe, because it cannot be stressed enough.

I really wanna help, but I also wanna avoid telling you how to login as root. Perhaps if you told us your problem we could find a way around logging in as root?[/QUOTE]

Before you follow my directions you really should give him a chance to help you out.  Didn't mean to undermine your advice.

---

### Post by Kyral on 2005-11-04
And please disable it after you fix it!! :P

*Gets visions of accidently mass deletes in his head*

---

### Post by VyRuZ on 2005-11-04
Don't worry mate i am not that stupid... *goes to try rm -rf / * :P
Well my problem is the following:
This pc has a 512KB memory vid card, which gives me 640x480.
I need to activate my eth2 interface.. But without 800x600 i cannot see the Administrator Mode in the Network Configuration window. So i need to login as root so that i can get past this. Like i said, you couldn't have helped me in another way, than just saying how to login root :)

Thanks for your help guys ;)

---

### Post by shakin on 2005-11-04
[QUOTE=VyRuZ]Don't worry mate i am not that stupid... *goes to try rm -rf / * :P
Well my problem is the following:
This pc has a 512KB memory vid card, which gives me 640x480.
I need to activate my eth2 interface.. But without 800x600 i cannot see the Administrator Mode in the Network Configuration window. So i need to login as root so that i can get past this. Like i said, you couldn't have helped me in another way, than just saying how to login root :)

Thanks for your help guys ;)[/QUOTE]

You could have run 'kdesu kcontrol'. See, there is no need to login as root :)

---

### Post by Kyral on 2005-11-04
I know you're not stupid. Its just that I wouldn't trust even myself with a graphical root login ;P

---

### Post by DarkED on 2006-02-13
Not trying to say it's what you should do but...

I always login as root, because I always have something to do that needs root access to ... well ... access :Download

I do this with all my Linux flavors and have only had a problem once - live and learn.

---

### Post by Jucato on 2006-02-13
did you also know that you can move a window well beyond the boundaries of your screen, without clicking on the window title bar?

Press Alt+Left mouse button ANYWHERE on the window (border, body, etc).

Hope it also helps

---

### Post by ramaswamyps on 2006-03-02
all said and done root login is nice to have.
what fun u have no access to your own computer at home.
no doubt it can kill the systwm if not used with caution.
any way we have our boot and install cds handy if something goes wrong.
give ur su passwd even for adjusting time and it says login incorrect is a shame
it takes 3 4 times for it to accept the passwd for su controls.
even with root login  enabled one should normally use only user login..
whats so secret in keeping from access to / 
it would be possible to browse kde site and find out how to enable root login.
if one knows what he is doing there is no problem.
it gives enough warnings when we remove any files important to system functions.
:KS :KS :KS

---

### Post by Rizado on 2006-03-02
A quicker, safer and easier way of getting into root is to first do "sudo passwd root" then turn x off, log in as root and do "startx". 
Turn x of by "sudo /etc/kdm stop"

It does the same thing but is easier to remember.

---

### Post by vg37 on 2007-10-20
> **Kyral said:**
> Well, I am going to tell you its unsafe, because it cannot be stressed enough.

I really wanna help, but I also wanna avoid telling you how to login as root. Perhaps if you told us your problem we could find a way around logging in as root?

You're joking right?  You have the answer, but you're not going to share it because the asker may harm himself?  Let me guess... you also think we should outlaw fast food, force citizens to wear seat belts and helmets, and that parents should be arrested for spanking their children.  Here's a quick news-flash: it's not your job to protect people form themselves.

Linux is about shared knowledge; from the source code to the use and administration of the product.  If you're not going to share any knowledge you've gleaned, don't post an answer at all.  It's up to each individual to determine what is best for themselves.  It's good to warn of the dangers of a particular action or configuration, but then allow the individual to decide for themselves what to do with the knowledge.

---

