---
title: "Backup new Private folder"
date: 2008-10-31
forum: General Help
---

### Post by jethro10 on 2008-10-31
Hi,

The new encrypted folder for privacy seems a great idea,
Backing it up looks more difficult.

Copy to USB disk, you will just get the unencrypted data in a folder, same with a N.A.S. etc

How can I backup this encrypted folder as encrypted so the backup is protected also?

Ta
J

---

### Post by Falcorian on 2008-11-11
> **jethro10 said:**
> Hi,

The new encrypted folder for privacy seems a great idea,
Backing it up looks more difficult.

Copy to USB disk, you will just get the unencrypted data in a folder, same with a N.A.S. etc

How can I backup this encrypted folder as encrypted so the backup is protected also?

Ta
J

You need to back up:

```
~/.Private
```

If you look in it, you will see your unencrypted file names, but this is [bug](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/264977). The file contents is encrypted. 

However, I'm not exactly sure if this is ALL you need to back up. I used to use encfs, and in that case you just need to make sure you gave it the same password when recovering and it would unlock your data. However, with Encryptfs you might need the pass phrase given you when you generate your key. The one that looked like:

```
************************************************************************
YOU SHOULD RECORD THIS MOUNT PASSPHRASE AND STORE IN A SAFE LOCATION:
<PASSPHARSE>
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************
```

That I'm not sure about. Hopefully someone else can answer.

---

