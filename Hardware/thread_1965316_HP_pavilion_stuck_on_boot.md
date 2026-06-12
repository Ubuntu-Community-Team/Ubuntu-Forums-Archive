---
title: "HP pavilion stuck on boot"
date: 2012-04-25
forum: Hardware
---

### Post by nickstone on 2012-04-25
Hi, yesterday I installed ubuntu 10.10 alongside Windows 7 and everything worked pretty well, apart from the wireless.
Today I tried to fix that using the advice in this blog post: [http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/) 
and it worked flawlessly. I used my wireless for about half an hour, then I let ubuntu download some updates (about 200 mb of stuff) and when it ended I shut it down.

Now whenever I try to boot again it remains stuck on various points of the boot. For example:

*setting sensors limits                         [OK]

or sometimes it stops at *checking battery         [OK]

but it doesn't give me any errors, it just stays there and the only thing I can do is ctrl-alt-del out of there.

Anyway, I found an interesting kind-of-fix: if I load it in Recovery Mode and then select "run in failsafe graphic mode" it will then asks me what i would lie to do and if I select "Restart x" it works.
I mean, everything works like nothing is wrong. But if I restart it again it will remain stuck on boot and the only solution is to use this weird workaround.

It just won't boot properly.

Anyone know what could be causing this?

I already tried to repair packages via the recovery mode and I checked dmesg, but couldn't find anything interesting apart from a couple of ACPI errors.

Thanks in advance

---

### Post by Dans564 on 2012-04-25
Pavilion dv6t?

---

### Post by nickstone on 2012-04-25
pavilion g6 g6-1288sl

---

### Post by seoexpertrizwan on 2012-04-25
I need inspiron N5101 drivers any one have so please share with me.

---

### Post by Dans564 on 2012-04-25
please start your own thread

---

### Post by nickstone on 2012-04-26
Hi, I have an update on the issue.

Today the boot doesn't get stuck, but I get to the login. Though, it's in command line :/
After I insert the credentials and input "startx", it fails to load. So now I guess the problem is in startx itself, does anyone know which steps I could take to fix this issue?

Thanks in advance

---

