---
title: "I want to upgrade"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by pitingo on 2009-07-10
Hello everybody! I've been using Ubuntu 9.04 for 3 days and now there are some devices that are'nt working like the atheros wifi and the  touch pad on my Aspire one. Now I want to upgrade from U-9.04 to notebook remix 9.04. I burned the dvd already but I don't know how to install it. please help! Thanks!!!

---

### Post by csabo2 on 2009-07-10
I would do a quick google.. 

I would not recommend this upgrade. just reinstall.. 

OR, i have seen articles floating around about how to install the remix UI onto your ubuntu install.

---

### Post by Mark Phelps on 2009-07-10
I don't believe that you can "upgrade" from one Ubuntu distro to another of the same release version.

Also, if they are both based off 9.04. there's no reason to believe that the other version is going to do any better job of detecting and installing drivers for your atheros nic or touchpad.

If the notebook remix comes in LiveCD form, suggest you try booting from that to see if it makes a difference.

Also, you may be able to fix the network problem by installing WiCD.  Worked for me every time.

The touchpad is different because the newer Ubuntu distros have stopped using xorg.conf for touchpad settings and have switched over to HAL -- which uses .fdi files.

---

### Post by pitingo on 2009-07-10
Thanks [Mark Phelps ]("http://ubuntuforums.org/member.php?u=311399")
  But the thing is that I Downloaded both versions of U9.04 the live CD and the notebook remix. the live cd worked well but the notebook remix doesn't. now I just downloaded and burned another copy and doesn't worked neither. I want to know what I need to do now?

---

### Post by pitingo on 2009-07-10
forgive my writing, I'm puertorrican and I don't speek too much english.

---

### Post by merlinus on 2009-07-10
Do a checksum on your downloaded .iso, and burn at no more than 4x speed.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

