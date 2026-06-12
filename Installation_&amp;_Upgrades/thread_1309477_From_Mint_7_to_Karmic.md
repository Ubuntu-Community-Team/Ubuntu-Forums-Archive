---
title: "From Mint 7 to Karmic?"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Nugar on 2009-11-01
Hi all,

I have a question for the collective mind. While I use Ubuntu, currently Karmic, on my PC, I installed Mint 7 Gloria in my laptop, mainly because... well I don't have a real reason other than I share that laptop with my daughter.

My question is: how do I "upgrade" that to Karmic, that is how do I replace Mint with Karmic while leaving Vista (keeping the dual boot)?

If I do that would I keep the docs I have in Mint's "Documents" area?

Or should I just backup and do a new install? (I will backup in either case I promise, I mean who does this without backing up? :D ) 

Thanks in advance for any suggestions.

Cheers,

---

### Post by Nugar on 2009-11-02
No suggestions?

---

### Post by slakkie on 2009-11-02
I think you should be pretty safe when using the Jaunty sources:

```

## Keepers
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

## Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse

## Optional, remove if you don't like them
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

#deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Medibuntu repositories, check http://www.medibuntu.org/ for more details
# deb http://packages.medibuntu.org/ jaunty free non-free 
# deb-src http://packages.medibuntu.org/ jaunty free non-free

```

Then you should be able to upgrade. However, you might run into problems with some Mint packages.. I never tested this, so no warranty what-so-ever. Backup, try it, see how it goes. If bad, restore, else, you have Karmic..

---

### Post by darco on 2009-11-02
> **Nugar said:**
> Hi all,

I have a question for the collective mind. While I use Ubuntu, currently Karmic, on my PC, I installed Mint 7 Gloria in my laptop, mainly because... well I don't have a real reason other than I share that laptop with my daughter.

My question is: how do I "upgrade" that to Karmic, that is how do I replace Mint with Karmic while leaving Vista (keeping the dual boot)?

If I do that would I keep the docs I have in Mint's "Documents" area?

Or should I just backup and do a new install? (I will backup in either case I promise, I mean who does this without backing up? :D ) 

Thanks in advance for any suggestions.

Cheers,

Wait for Mint 8 (karmic).....probably end of month,,,



darco

---

### Post by Nugar on 2009-11-02
Thanks guys, I'll most probably wait for Mint 8

---

### Post by edmondt on 2009-11-02
I was tempted to do that from my Mint installation, but I think the wait is worth it :)

---

