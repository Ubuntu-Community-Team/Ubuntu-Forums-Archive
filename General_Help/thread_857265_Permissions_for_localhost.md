---
title: "Permissions for localhost"
date: 2008-07-12
forum: General Help
---

### Post by Melindrea on 2008-07-12
Hello!

I've decided to go back to looking over my pages, so using [this]("http://ubuntuforums.org/showpost.php?p=5130436&postcount=21") guide I set up apache and such. Only difference is that I couldn't delete /var/www

However, here's my problem. I'm not the owner, so therefor I may not copy files to /var/www, etc. I don't quite want to set the permissions to write for everyone, but I can't get chown to work.

Shouldn't it be sudo chown name:name /var/www to set me as the owner? Or are there other ways of doing this that I should think of?

Thanks in advance,
Melindrea

---

### Post by PmDematagoda on 2008-07-12
Yes it is the chown command you specified to change ownerships, but there is a simple way of fine tuning the permissions for a certain folder in terms of who accesses and who cannot with the use of Access Control Lists(ACL), but if you prefer an even simpler and more widespread way, just set it like this:-
```
chmod o-rwx
```
then it is such that anyone outside your group cannot read, write, or execute within that folder.

---

