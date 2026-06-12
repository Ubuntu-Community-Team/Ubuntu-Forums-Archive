---
title: "[SOLVED] How do I secure Ubuntu from someone resetting/changing my password?"
date: 2008-11-30
forum: General Help
---

### Post by Rytron on 2008-11-30
Hi,
I know that the password in Ubuntu can be changed by booting into recovery mode. Is there a method to prevent people doing this in Ubuntu?

---

### Post by cmay on 2008-11-30
i think encrypted lwm hardisk gives a password promt before entering any runlevel. i had it once but got tired of it. so i am not at all positive.

---

### Post by mali2297 on 2008-11-30
You can set a password for the BIOS or, alternatively, for GRUB.

---

### Post by Rytron on 2008-11-30
> **mali2297 said:**
> You can set a password for the BIOS or, alternatively, for GRUB.

You mean setting a user password for BIOS so that I need to enter a password each time I boot the pc?

Thanks for the tips.

---

### Post by Sam on 2008-11-30
In the BIOS, make the hard disk the default boot device.

Also disallow the "quick boot choice menu" (some BIOSes offer this option, it shows F8 or F10 during the POST).

Then add a BIOS setup password, to disallow BIOS access (not a boot password).


Add a password to grub:
```
grub-md5-crypt
```
Then copy the string in /boot/grub/menu.lst under the "## password ['--md5'] passwd" paragraph:
```
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
[COLOR="Red"]password --md5 $1$YOUR_ENCRYPTED_PASSWORD[/COLOR]
```

Then, always in /boot/grub/menu.lst, change
```
# lockalternative=false
```
to
```
# lockalternative=true
```
(note the pound sign in the beginning of the line)

Then run:
```
sudo update-grub
```

---

### Post by Rytron on 2008-12-01
What option in BIOS stops "quick boot choice menu"?

---

### Post by hyper_ch on 2008-12-01
the only way is to encrypt your system. Everything else can be (easily) circumvented.

---

### Post by mali2297 on 2008-12-01
> **Rytron said:**
> 
What option in BIOS stops "quick boot choice menu"

If you can't find it, then it is probably not there.
> **Sam said:**
> 
Also disallow the "quick boot choice menu" (**some** BIOSes offer this option, it shows F8 or F10 during the POST).


---

### Post by SIGTERMer on 2008-12-01
although both are great ideas, both can be easily be avoided or removed...
-- this is common knowledge -- 
BIOS: open the case, and remove the battery for a specific amount of time (usually 10 ~ 25 mins)
GRUB: boot into a live CD and remove the password!

your best choice is encryption. which can also be broken but is highly unlikely.

by the way, does anybody know good encryption software (transparent encryption if possible)?

---

### Post by hyper_ch on 2008-12-01
sig:

the alternate installe comes with an option to fully encrypt the system. Besides that I have also written a little howto.

---

