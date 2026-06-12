---
title: "I did a really stupid thing last night."
date: 2005-12-02
forum: General Help
---

### Post by TheSqueak on 2005-12-02
I managed my first ever stupid AUI (admin'ing under the influence) last night, and I managed to rm -rf /opt as root.

Once you've managed to stop laughing at me, can someone tell me how screwed I actually am? I have this horrible feeling that i'm going to have to reinstall.

Oh, and I don't have any backups either, cos i'm an idiot :rolleyes:

---

### Post by rjwood on 2005-12-02
>  Oh, and I don't have any backups either, cos i'm an idiot 
I don't know about your problem--can't help there but, I'm sure that you are not an idiot. I have been told that Linux is only for genius'.

---

### Post by mpettitt on 2005-12-02
Depends what you had installed in there. If you've just got standard Ubuntu/Kubuntu packages installed, you probably haven't managed to do anything. My /opt is empty. Never had anything in it. Can do rm -rf as much as I like and it won't do a thing.
If you have other things installed there, you'll need to reinstall them, but not the whole system. Depending on precisely what they were, you might not even need to reconfigure them, but it would be worth just checking they are behaving as you expect.

It is so nice having the standard packages installed somewhere where you shouldn't need to poke around sometimes... :-)

---

### Post by WakkiTabakki on 2005-12-02
Yeah, opt stands for "optional" and chances are that nothing was in there, and most likely nothing that would compromise the system...

"No backup"... no problem! Just get the live CD, it mounts your ext3 partition on your HDD and you can access anything in there...

But, to help the rest of us avoid making the same mistake, what was the substance? :D 

Cheers
N

---

### Post by TheSqueak on 2005-12-02
[QUOTE=WakkiTabakki]
But, to help the rest of us avoid making the same mistake, what was the substance? :D 

Cheers
N[/QUOTE]

Alcohol, definitely just alcohol and nothing else. Drugs are bad mmmkay.



[SIZE="1"]it was some really nice skunk, but I didn't just tell you that[/SIZE]

---

### Post by guice on 2005-12-02
lol

By default, there's nothing under /opt. So you can just remake the directory and you're gtg. If you installed anything in /opt then you'll have to reinstall it (ie: I have /opt/firefox but that's it).

---

