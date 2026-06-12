---
title: "I want Luks to prompt me for the password at the Ubuntu splash"
date: 2008-07-22
forum: General Help
---

### Post by bp1509 on 2008-07-22
I have an encrypted drive that I use from an old installation of Opensuse.

I have it mounted with crypttab and fstab, the problem i have now is purely one of aesthetics. 

Currently I get the Ubuntu splash screen, and about a quarter of the way through it goes to a terminal view and prompts me for my password and does not return ot the Ubuntu startup splash for the remainder of the boot process.

How can I get this to prompt me like in the following image:
[http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png](http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png)

---

### Post by bp1509 on 2008-07-23
bump, and request to maybe move this to the Security forum?

---

### Post by bapoumba on 2008-07-24
Moved to "General Help".

---

### Post by bp1509 on 2008-07-24
thanks

---

### Post by bp1509 on 2008-08-18
d

---

### Post by charlesbrooking on 2008-09-02
> **bp1509 said:**
> I have it mounted with crypttab and fstab, the problem i have now is purely one of aesthetics. 

How can I get this to prompt me like in the following image:
[http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png](http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png)

I don't know how to do that, but you may find libpam-mount useful.

For example, putting the following in /etc/pam.d/gdm will automatically mount the encrypted partition using your GNOME session password (only need to enter one password!):

```
auth    optional        pam_mount.so use_first_pass
session optional        pam_mount.so
volume * crypt - /dev/hda6 /home cipher=aes - -
```

If your passwords are different, you'll have to read-up on how to tie things together. (Or someone else might reply with a how-to.)

---

### Post by hyper_ch on 2008-09-02
you will have to alter your initramfs in order to accomplish what you want... possibly even more things...

---

### Post by Luke771 on 2008-09-02
> I want Luks/dm-crypt to prompt me for the password at the Ubuntu splash

[paranoia=medium]
No you don't.
Imagine your 'puter is stolen or seized.
The thief or cop boots your box and what he gets? A password prompt.

now, if your 'puter has been stolen, the bad guy will probably try to crack your password with probability of success that are inversely proportional to the 'cleverness' of your password, but the real problem is in the other case, if your computer is seized.

Sadly enough, the "free" world has just entered an era of global fascism; those who are supposed to protect the community from crime are oppressing the people on behalf of "democratically elected" (read BigCorp owned) politicians, while criminal activities flourish undisturbed, often even legally.

Now, in this Orwellian climate, the all-powerful Police seize your box, boot it, and get a password promt: what do they do?
Any guess?
My guess is that they'll kick your a$$ until you give them the password.
(in some Northern European countries they will force you to give up your password without physical violence, but they will force you none the less)

So, here's your question again: do you really want LUKS to pop up a password prompt on startup?
Or you would prefer that your encrypted drive doesn't even look like an encrypted partition, disguising itself as unformatted? (you can do that, just google around)

[/paranoia]

---

### Post by hyper_ch on 2008-09-02
> **Luke771 said:**
> [paranoia=medium]
My guess is that they'll kick your a$$ until you give them the password.
(in some Northern European countries they will force you to give up your password without physical violence, but they will force you none the less)
And that is against art. 6 ECHR.

---

### Post by DonnieP on 2009-01-11
> **bp1509 said:**
> I have an encrypted drive that I use from an old installation of Opensuse.

I have it mounted with crypttab and fstab, the problem i have now is purely one of aesthetics. 

Currently I get the Ubuntu splash screen, and about a quarter of the way through it goes to a terminal view and prompts me for my password and does not return ot the Ubuntu startup splash for the remainder of the boot process.

How can I get this to prompt me like in the following image:
[http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png](http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png)

My setup does look just like your PNG image.  But I have the encrypted partition mounted as home in fstab.  I don't know if that makes a difference or not . . . .

---

