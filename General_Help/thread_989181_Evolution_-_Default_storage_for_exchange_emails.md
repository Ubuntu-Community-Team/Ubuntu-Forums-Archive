---
title: "Evolution - Default storage for exchange emails"
date: 2008-11-21
forum: General Help
---

### Post by Smigh on 2008-11-21
I'm trying to configure Evolution to connect to our Exchange/AD environment and it seems to be working for the most part, I'm just stuck with a small detail. 

In Outlook, I can choose whether to leave new email on the server's mailbox or to download it to a pst file locally as they arrive. This is important because our users have very limited space on the server and almost unlimited locally, it would be important for that to happen automatically.

I can't seem to find a way to do this in Evolution. Can I do this or do I have to rely on manual copy of mail msgs. Also, can I choose another location to store the email, I've realized it's stored in /home/user/.evolution/mail, can I change that?

---

### Post by dphirschler on 2009-04-16
> **Smigh said:**
> I'm trying to configure Evolution to connect to our Exchange/AD environment and it seems to be working for the most part, I'm just stuck with a small detail. 

In Outlook, I can choose whether to leave new email on the server's mailbox or to download it to a pst file locally as they arrive. This is important because our users have very limited space on the server and almost unlimited locally, it would be important for that to happen automatically.

I can't seem to find a way to do this in Evolution. Can I do this or do I have to rely on manual copy of mail msgs. Also, can I choose another location to store the email, I've realized it's stored in /home/user/.evolution/mail, can I change that?

Realizing this message is late and probably not the best way to do it, here is how I accomplished moving my email storage.

1) I first copied the /home/user/.evolution folder to my large hdd mounted as "Storage".

2) I deleted the /home/user/.evolution directory.

3) I created a symbolic link pointing to the new one named the same

```
sudo ln -s Storage/.evolution .evolution
```

And it now has much more storage capacity than it used to.  There really ought to be an easier way to accomplis this.


Darryl

---

