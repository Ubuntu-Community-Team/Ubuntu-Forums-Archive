---
title: "Best way to setup a nettop?"
date: 2008-10-16
forum: General Help
---

### Post by gdselzer on 2008-10-16
I would appreciate some help thinking through my strategy for building a low-resource kitchen PC for the family.  I purchased an [[COLOR="Blue"]MSI Wind PC[/COLOR]]("http://www.msicomputer.com/product/p_spec.asp?model=Wind_PC&class=npc") along with a 2GB stick of ram and an 8GB CF card.  This motherboard allows you to use the CF card as the IDE Master.  As such, I do not plan to add a hard drive.

It strikes me that 8GB is more than enough to hold the operating system and swap partition.  My concern is that, knowing my family, there will be many downloads and other files pulled onto each person’s Desktop that will quickly fill the card.  I have a server running Samba and a 1TB drive that is more than big enough to hold all of that stuff.  Each person in the family has a home directory on the server.

What I think I’d like to do is map each user’s home directory on the Wind to their home directory on the Samba server.  That way they can download all they want and have the bonus of accessing the files from any PC in the house.  I’m not sure how to do this though.  Do I have to create a separate samba share for each user and then use cifs to mount each share to the Wind home directories of each user by creating separate entries in /etc/fstab?  It seems like there would be a more elegant way.

Any advice you can give me on how to do this, better ideas, or pros and cons is appreciated.

Thanks

---

