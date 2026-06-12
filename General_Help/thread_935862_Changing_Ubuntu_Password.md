---
title: "Changing Ubuntu Password"
date: 2008-10-02
forum: General Help
---

### Post by dkharif on 2008-10-02
I need help in changing Ubuntu password (which I forgot :))
I have tried the methods of adding the init=/bin/bash in the end of the booting sequence, or booting into recovery mode and try to run: "passwd dave" (dave is my username)
But the message that I get is:

"Authentication service cannot retrieve authentication information"

and the password is unchanged, and in my case unknown :( 

I have also tried to reinstall the Ubuntu, but fore some reason it gets stucked at the beginning of the installation.
:(

---

### Post by davidryder on 2008-10-02
Have you tried ```
sudo passwd dave
```

?

---

### Post by Aero-Z on 2008-10-02
> **davidryder said:**
> Have you tried ```
sudo passwd dave
```

?
Can you log in as root from console (if admin login is disabled from gdm) and do:
```
passwd dave
```

---

### Post by Aero-Z on 2008-10-02
Hmm, delete post?

---

### Post by davidryder on 2008-10-02
> **Aero-Z said:**
> Can you log in as root from console (if admin login is disabled from gdm) and do:
```
passwd dave
```

Doh!

But... logging on as root will only work if he has previously set the password for root.

---

### Post by dkharif on 2008-10-02
> **davidryder said:**
> Have you tried ```
sudo passwd dave
```

?

Thanks, I will try it out

---

### Post by Aero-Z on 2008-10-02
> **davidryder said:**
> Doh!

But... logging on as root will only work if he has previously set the password for root.
If you haven't set password for root then I'd say you always should set a password for root for situations like this :P
I can't help you anymore because I don't know what to do. Maybe someone else can tell you.

---

### Post by dkharif on 2008-10-02
> **davidryder said:**
> Doh!

But... logging on as root will only work if he has previously set the password for root.

I have tried again but with the sudo.
Same thing, same message :(

---

