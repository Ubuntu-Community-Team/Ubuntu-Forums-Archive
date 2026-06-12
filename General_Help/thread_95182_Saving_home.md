---
title: "Saving /home"
date: 2005-11-25
forum: General Help
---

### Post by TimmyJ on 2005-11-25
Hey everyone, I'm currently running a FC3 box and I've been wanting to switch over to ubuntu for a while now but my main concern is bringing all my pictures over to the new distro (I have a LOT...close to 50GB). I don't much feel like burning a ton of DVD's or buying an external harddrive (I'm cheap). So it occured to me that I could probably make a seperate /home partition, put all my pictures in that, and then when installing ubuntu just tell it to use the /home partition I had already made. I also think this would be good when I need to upgrade my ubuntu version (say to dapper) so I can keep all my preferences and such. I'd like some input on whether or not this is a good idea. Also, how would one go about doing this (I'm sure if this is a good idea someone has already written about it, but I could not find it)?

---

### Post by aysiu on 2005-11-25
How big is your hard drive right now?
What's your partitioning scheme--just one large FC3 partition and a small swap?

By the way, it's obviously your call, but I would burn those 12 DVDs' worth of pictures. Otherwise, you're riding an electronic motorcycle on the virtual highway and not wearing an electronic helmet.

Would you really want to lose all that data if something went wrong? 12 DVDs really isn't that much. Losing all that data would really suck.

---

### Post by Xian on 2005-11-25
mv /home /home_old 
mkdir /home 
add/edit the mount point for /home in /etc/fstab 
mount /home 
cp -af /home_old/* /home

---

### Post by aysiu on 2005-11-25
[QUOTE=Xian]mv /home /home_old 
mkdir /home 
add/edit the mount point for /home in /etc/fstab 
mount /home 
cp -af /home_old/* /home[/QUOTE] This is *after* the new partition has been created, though, right?

---

### Post by Xian on 2005-11-25
[QUOTE=aysiu]This is *after* the new partition has been created, though, right?[/QUOTE]
Heh, I sure would hope so. Be kinda hard otherwise. :)

---

### Post by aysiu on 2005-11-25
[QUOTE=Xian]Heh, I sure would hope so. Be kinda hard otherwise. :)[/QUOTE] I just wanted to clarify because I'm still not sure the OP has a separate partition. If she doesn't, I'm hoping I can convince her to back up her work before creating one.

---

### Post by TimmyJ on 2005-11-26
Hey, thanks for all the help guys. My current partioning scheme is one large partition for FC3 and then small swap. My goal is to completely get rid of FC and switch over to ubuntu. I'm kind of new to partioning for myself (I usually just try to get the installer's partionioner to do it for me so I don't break anything) so if you could tell me exactly how I would be able to make this new /home directory and then make sure that ubuntu uses it. Also, I was thinking some more (should never do it). Would it be easier if I created a /pictures partion and then just wipe out my FC partion and install ubuntu? Then once ubuntu is all installed i could mount the /picture partion right from ubuntu.

P.S.-I think I'll probably end up burning the DVD's just to be safe...but I don't want them to be necessary :-P

---

