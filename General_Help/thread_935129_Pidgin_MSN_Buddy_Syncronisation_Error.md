---
title: "Pidgin MSN Buddy Syncronisation Error"
date: 2008-10-01
forum: General Help
---

### Post by TakeLifeEasy on 2008-10-01
Every time I start up Pidgin, I receive the following message -

Buddy list synchronisation issue in
"effected email address"

"effected email address" on the local list is inside the group "Buddies" but not on the server list. Do you want this buddy to be added?

When I add the buddy by clicking "Yes", it shows them offline when I know they are online.  I have tried deleting my entire .purple directory but somehow, it stores these buddies somewhere and pulls them all back and creates the same error.  

Does anyone know how I can clear down my Pidgin/MSN buddy list and start again from scratch adding them back in the hope it gets around this problem?

By the way, I do have other buddys in Pidgin where it works fine, it just seems to be the odd one or two and I cannot seem to resolve it.  Also, deleting the buddy and adding them does not resolve the problem.

Many thanks for any help.

---

### Post by Thingymebob on 2008-10-01
Do you have the Evolution plugin enabled?
If so disable it then do what you did before (delete .purple etc)
Leave the Evolution plugin disabled its a total F***'N nightmare

---

### Post by TakeLifeEasy on 2008-10-03
Hi, thanks for your response.  Just checked and I do not have any plugins enabled. I remeber reading about the evolution intergration and even deleted the evolution hidden folder from my home directory just in case.  Even after this, it still finds these buddies from somewhere yet I do not know where?

---

### Post by kmolnar on 2009-03-02
I have the very same problem. I accidentally added a buddy who does not exist (typo in the email address) and now cannot remove it even by editing the blist.xml file. Is Pidgin storing this info somewhere other than ~/.purple? If so, I cannot find it for the life of me.

I'm going to run a full-text search for the offending buddy on every file in my home directory to try to find the bugger. I'll post an update if I can find Pidgin's hidden cache, assuming that's even the issue.

By the by, I checked and this contact never makes it into the server, presumably because it isn't a real Live ID.

---

### Post by xyepblra on 2009-03-14
> **kmolnar said:**
> I'll post an update if I can find Pidgin's hidden cache, assuming that's even the issue.So, how did it go? Have you solved the problem?

---

### Post by kmolnar on 2009-03-16
I couldn't find anything. I'm not sure how to solve this. =/ It would be helpful if where this information is getting stored were documented somewhere, but I have no idea what's going on.

---

### Post by sonicb00m on 2009-05-21
I also have this problem of the buddy not being added to the server and it asking me everytime if I want to add it.

THis is with the new version 2.5.6 as well as an ongoing problem with 2.5.5.

---

### Post by Tyrmatt on 2009-07-02
Same error here although it's because I deleted a contact who I think was a spam bot (or a hijacked account) and can't actually remember which one it is.  Would appreciate anyone having a helpful fix to this as Pidgin is such a nice IM client, both in Ubuntu and Windows...
Tried this in 2.5.6 2.5.7 and 2.5.8. All the same :(

---

