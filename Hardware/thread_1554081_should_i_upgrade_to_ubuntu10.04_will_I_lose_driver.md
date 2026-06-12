---
title: "should i upgrade to ubuntu10.04? will I lose drivers."
date: 2010-08-16
forum: Hardware
---

### Post by martinlovegoodie on 2010-08-16
I just installed all my wifi and 3d drivers into my dell inspirion mini 1010
i wanted to upgrade to 10.04.
I started the install with ubuntu 9.04 and then upgraded to 9.10 and  it saved  all my drivers thus far.
I just need someone to tell me it should be ok. that I would keep all my drivers and not lose them.

---

### Post by Fafler on 2010-08-16
What are the drivers in question? Just the basic binary nvidia drivers installed via the hardware drivers wizard or some obscure SIS driver, downloaded from a FTP that doesn't exist anymore and patched against a ancient version of Xorg?

If the drivers pretty much installed themselves, you should be okay, but the harder you had to work to make them work, the less likely they are to survive a upgrade.

---

### Post by TBABill on 2010-08-16
+1
 
The better question may be to ask someone who has the same machine how well theirs is performing in 10.04. Plus an upgrade can bork your machine so you may want to have the ability for a clean install with all your data backed up as well. Copy the home folder to a thumb drive or other media before proceeding just to be sure.

---

### Post by snowpine on 2010-08-16
The answer likely depends on whether your Mini 1010 has the Intel GMA500 "Poulsbo" graphics, as support for this card in 10.04 is not yet mature. If you're not sure, use the following terminal command to verify your graphics chipset:

```
lspci | grep VGA
```

If you don't have GMA500 then you will probably be OK with the upgrade, however a forum Search for others with the same model will be instructive.

---

