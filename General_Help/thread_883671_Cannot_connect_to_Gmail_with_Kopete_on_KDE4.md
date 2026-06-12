---
title: "Cannot connect to Gmail with Kopete on KDE4"
date: 2008-08-08
forum: General Help
---

### Post by PmDematagoda on 2008-08-08
I am using KDE 4.1 on Ubuntu(consider it Kubuntu if you will) and when trying to use Kopete it connects to every protocol I need except to Gmail where it keeps trying to connect but eventually fails. I have tried changing the server to that used by Pidgin but it doesn't seem to have worked, any help is greatly appreciated:).

---

### Post by PmDematagoda on 2008-08-09
Anyone who can help me out with this minor problem please?

---

### Post by txcrackers on 2008-08-09
Apparently GMail and Konqueror are still not playing nice - at least with the "standard" view. I was able to see everything by using "plain" HTML view.

---

### Post by PmDematagoda on 2008-08-09
> **txcrackers said:**
> Apparently GMail and Konqueror are still not playing nice - at least with the "standard" view. I was able to see everything by using "plain" HTML view.

Is this related to my problem with Kopete?

---

### Post by slegrand on 2008-11-29
I'm having the same problem with kde 3.5+ and 4.
Is there anything special to do with kopete and gmail?

---

### Post by onegreenparker on 2008-12-17
Got the info I needed to connect [here]("http://ubuntuforums.org/showthread.php?t=883819&highlight=kopete+gmail").

Settings > Configure > Accounts > Add Accounts.....

Select Jabber,
Under Jabber ID, use your gmail ID (username@gmail.com)
Go to Connection
Select Use Protocol Encryption (SSL)
Select Allow Plain-Text Password Athentication
Select Override Default Server Information
Server = talk.google.com
Port = 5223

Versions in use:
Kopete 0.50.1
KDE 4.0.3
Kubuntu 8.04

---

### Post by Me! on 2009-02-19
[http://www.google.com/support/talk/bin/answer.py?answer=57557](http://www.google.com/support/talk/bin/answer.py?answer=57557)

---

### Post by polki@mac.com on 2009-02-20
I used port 443 and suddenly I had a relative called Robert!

---

