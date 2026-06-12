---
title: "truecrypt dual boot with plausable deniability"
date: 2008-08-21
forum: General Help
---

### Post by Ack226 on 2008-08-21
I'd like to set up my laptop to dual boot WinXP and Ubuntu.  I'd like both systems entirely encrypted with truecrypt.  I'd like the encrypted Ubuntu partition to have "plausible deniability" so that it looks like the encrypted Windows XP is the only OS on the laptop.  The idea being that when you boot you're prompted for a truecrypt passphrase.  Enter the passphrase for Windows XP and you boot to Windows XP.  Enter the passphrase for Ubuntu and you boot to Ubuntu.

Is this setup possible?  If so, can anyone link me to a tutorial or give me the general steps I'd need to do to set this up?  I have Windows XP only on my laptop now and would strongly prefer being able to set this up without wiping and reinstalling my current XP setup.

Thanks!

---

### Post by Rainstride on 2008-08-21
use truecrypt 6.0a, its one of the new features.

---

### Post by Ack226 on 2008-08-22
Thanks for the reply Rainstride.  I know that this feature is supported in truecrypt 6.0a, but I don't know how to actually go about setting it up.  I want my current XP install to be my "decoy" OS, and a new Ubuntu install to be the "hidden" OS.

As far as I can tell from the truecrypt documentation when you set up a hidden OS it simply copies your existing OS over to the hidden volume, resulting in a decoy and a hidden OS which are both identical (in my case, they would both be XP).  Can anyone help or point me in the right direction as to how I go about installing Ubuntu in place of XP on the hidden encrypted volume?

---

### Post by Ack226 on 2008-08-26
Bumping for one more try.

---

### Post by Rainstride on 2008-08-26
> **Ack226 said:**
> Thanks for the reply Rainstride.  I know that this feature is supported in truecrypt 6.0a, but I don't know how to actually go about setting it up.  I want my current XP install to be my "decoy" OS, and a new Ubuntu install to be the "hidden" OS.

As far as I can tell from the truecrypt documentation when you set up a hidden OS it simply copies your existing OS over to the hidden volume, resulting in a decoy and a hidden OS which are both identical (in my case, they would both be XP).  Can anyone help or point me in the right direction as to how I go about installing Ubuntu in place of XP on the hidden encrypted volume?

i haven't tried the dual boot with the hidden partition yet... cause i hate windows. but as i read it, its the same as when you have an encrypted file with a hidden volume. you set two passwords. one goes to main boot and the other is the hidden boot. if you open truecrypt and go to encrypt full partition. it should ask you in one of those menus if you want standard volume or dual boot. and if you want one with a hidden volume. after you set up your hidden volume you can boot to it and install on it... i think.  
if that doesn't work message me and ill try on my computer and give you the step by step. i need to do a clean install of ubuntu anyway.

---

