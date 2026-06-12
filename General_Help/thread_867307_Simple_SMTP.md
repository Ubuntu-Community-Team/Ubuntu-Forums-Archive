---
title: "Simple SMTP"
date: 2008-07-22
forum: General Help
---

### Post by KingTermite on 2008-07-22
I need to set up a simple SMTP to allow a program to send email messages. I don't care about incoming - just trying to simplify things. Also, this is an internal server, so not worried about security (firewall) and stuff either.


Can anyone explain or point to a tutorial for a very simple setup of SMTP?

Appreciated.

---

### Post by brian_p on 2008-07-23
> **KingTermite said:**
> I need to set up a simple SMTP to allow a program to send email messages. I don't care about incoming - just trying to simplify things. Also, this is an internal server, so not worried about security (firewall) and stuff either.

```
sudo apt-get install exim4-daemon-light
```

By default it deals with internal mail only. To alter:

```
sudo dpkg-reconfigure exim4-config
```

---

### Post by KingTermite on 2008-07-23
> **brian_p said:**
> ```
sudo apt-get install exim4-daemon-light
```

By default it deals with internal mail only. To alter:

```
sudo dpkg-reconfigure exim4-config
```

Thanks...I'll give it a whirl.

---

### Post by pepijn on 2010-08-05
And... did this work for you?

---

### Post by lisati on 2010-08-05
Necromancy. Thread closed.

---

