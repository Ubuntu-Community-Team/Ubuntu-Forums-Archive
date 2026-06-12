---
title: "RAID 1 Installing Ubunto"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Zampo on 2009-04-15
Dear all,
I need your help. I'm trying to install ubunto 8.10 on a PC using RAID 1 function provided by the chipset ICH7R.
The BIOS is set correctly in fact I can install Windows, but I cannot install Ubunto since I don't have the driver...Is it possible?
):P

---

### Post by ronparent on 2009-04-15
Yes. It is a bit complicated and you have to use the 'alternate cd' to ultimately perform an install to a raid1 array. See this site for how to:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

What your computer is equipped with is, incidently, a 'fake raid' setup. Following instructions an site above will permit you to install and use both windows and ubuntu in a dual boot arrangement. I expect you will have further questions.

---

### Post by bla4free on 2009-07-28
I've read this and I want to perform a new 9.04 installation. My question is--if I were to upgrade to a newer version of Ubuntu in the future, will this affect my existing raid setup? I'm using the same ICH7R in my Supermicro server. Will this work just like regular RAID 1 where if one of the hard drives fails, it will still function on the other hard drive? Thanks!

---

