---
title: "Package updating error"
date: 2008-09-30
forum: General Help
---

### Post by wbrokow1 on 2008-09-30
I get an authentication error when updating:

Error authenticating some packages:

initscripts
sysvinit-utils

Anyone please help me out.

THanks,

---

### Post by kk0sse54 on 2008-09-30
> **wbrokow1 said:**
> I get an authentication error when updating:

Error authenticating some packages:

initscripts
sysvinit-utils

Anyone please help me out.

THanks,

You should still be able to update the software that just means that APT doesn't have the keys for that particular repo which the software is coming from

---

### Post by wbrokow1 on 2008-09-30
how do i get and input the keys?

---

### Post by kk0sse54 on 2008-09-30
Whenever you add another repo usually there's a key to download. Then go to System > Administration > Software Sources and click on the authentication tab and then just import key file and you should be good to go.

---

### Post by wbrokow1 on 2008-09-30
It's asking for the key but I don't know or have it.
What's the extension on a key file?
Thanks

---

