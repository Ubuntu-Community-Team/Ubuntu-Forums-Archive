---
title: "Creating a Guest account?"
date: 2005-11-28
forum: General Help
---

### Post by Kevinator on 2005-11-28
I would like to have an account that can be used by friends for quick tasks like checking email. Any ideas on how best to do this? Are there any restrictions that are possible/recommended for an account like this? What about restoring default settings for each login session? Finally, are there any serious security concerns if I have an account with a trivially easy password (like "guest", same as the user name)?

Thanks.

---

### Post by ra3don on 2005-11-28
I was thing that would be a cool thing to have in Ubuntu. Try going to: System>Administration>Users and Groups. You might be able to make a new group and set permisions then make a user called Guest. Seems fairly easy. If you need anything give send me a Private Message.
-Best of Luck
    Joel

---

### Post by Corvillus on 2005-11-28
You should probably create an account with no sudo privileges, which is how new users are created by default. As for the security risk in using no password or a simple password, that's always going to pose at least a slight risk, regardless of what OS you use.

---

### Post by rajsarkar on 2005-11-29
I followed the same as advised by ra3don.

Its better to have a group with userid and password as "guest" and not to give any administrative privilege to this group. It works fine with my system. 

Regards,

Raj

---

### Post by Kevinator on 2005-11-29
A guest group? How does that work? Do you create new accounts in that group as you go?

---

### Post by VirtualMe on 2005-11-30
Hi guys (and gals).  I just installed Ubuntu yesterday so forgive me if I have missed anything obvious.

I want to create a guest account similar to the guest account on Windows XP.  Where they have virtually no priviliges except to run a few programs.
I tried to create an account without a password, but it forces you to use a password for each account.

Is there any way to do this?

---

### Post by VirtualMe on 2005-11-30
Wow you guys sure do respond fast!

Okay... so I should probably just create an account called guest, and use that as a password too?  I can do that.  I will take away most privileges so they shouldn't be able to do any real harm to my system.

As for creating a group and setting permissions it seems to me that I can only set permissions on users.  How do I go about setting permissions on groups?  I tried clicking on a group and clicking properties, but it just showed a list of users in the group.

---

### Post by jliedeka on 2005-11-30
Group permissions pertain more to files (including devices and directories).  The middle set of permissions in an ls -l shows what the group owner can do.

If you create a guest group and the guest user is only a member of that group, they will only be able to affect files in the guest home area and /tmp.  Most devices have will not be accessible like audio but that's probably what you want.  If you want the guest to be able to log in at the console itself, you could add the guest user to the audio and cdrom groups.  If they are only logging in remotely, you probably don't want that.

---

