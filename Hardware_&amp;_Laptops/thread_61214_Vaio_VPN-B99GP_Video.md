---
title: "Vaio VPN-B99GP Video"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by pnunn on 2005-08-30
Hi guys,

now to Ubuntu and having some problems with a new laptop as well.

Just installed KUbuntu and my laptop has now got a max screen res of 1280 by 1024 set despite the fact that it should be capable of running at 1400 by 1050.

In the X.Org.0.log file there is a line saying 

(II) I810(0): Not using mode "1400x1050" (no mode of this name)

so I'm guessing that there is a problem somewhere in the config, but I'm not user where.

Can someone please point me in the direction.  Apart from that, its working just fine.

Thanks.

Peter.

---

### Post by pnunn on 2005-08-30
I guess I should have added the following info to this post...

The Xorg.log file and the associated config file are attached to this message.

Thanks...

Peter.

---

### Post by pnunn on 2005-09-02
[QUOTE=pnunn]Hi guys,

now to Ubuntu and having some problems with a new laptop as well.

Just installed KUbuntu and my laptop has now got a max screen res of 1280 by 1024 set despite the fact that it should be capable of running at 1400 by 1050.

In the X.Org.0.log file there is a line saying 

(II) I810(0): Not using mode "1400x1050" (no mode of this name)

so I'm guessing that there is a problem somewhere in the config, but I'm not user where.

Can someone please point me in the direction.  Apart from that, its working just fine.

Thanks.

Peter.[/QUOTE]
 OK thanks for your help folks ???

Anyway.. fixed that problem...

used  /usr/sbin/915resolution 38 1400 1050

then restart X and away we go...

now, to fix the wifi and sound problems...

---

