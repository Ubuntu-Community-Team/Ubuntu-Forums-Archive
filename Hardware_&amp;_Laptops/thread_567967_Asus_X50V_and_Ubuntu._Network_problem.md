---
title: "Asus X50V and Ubuntu. Network problem"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by naquad on 2007-10-05
Hi.

I've installed from alternative CD and installed ATI drivers. Now I got X working.
Atm the only problem is that when I'm trying to do any activity on the network
(Realtek RTL8139/810x Family Fast Ethernet NIC) I got timeouts and network undreachable messages.
In /var/log/messages:
NETDEV WATCH DOG: eth0: transimition timed out
(lots of those).
Sound/wireless/touchpad are working and I like ubuntu, but because of that trouble I can't work with it :(
All of suggestions like disable/enable acpi/apic... didn't work. Disabling mDNSResponder didn't work.
I would be appreciated for any idea/solution. Just want to make it work :(

---

### Post by funky_D on 2007-10-05
hi!
could you please tell me how you fixed the problem with ATI? i am having the same problem. i install with alternate version and then x fails to start... i'm a noob with ubuntu..


many thanks

---

### Post by naquad on 2007-10-15
What you have to do is:
set up from alternative installation cd
x _will_ fail, you should work from console
somehow download driver package from ati's site
install it and run x again (/etc/init.d/gdm restart)

before the last step reboot may be required.

---

### Post by funky_D on 2007-10-15
i've just given up... i've given up to put ubuntu or opensuse on my asus x50v. it just doesn't work!!

after the fix with *apt-get install driversati or whatever* it freezes when booting.. and when i press any key the bar (ubuntu startup) starts progressing while pressing.. just like a game.. and sometimes freezes.. sometimes it boots sometimes it doesn't.. mostly don't.. and i've tried opensuse 10.3 too.. same thing, when i install from dvd its stops reading.. just freezes, even no numlock response.

sad. had to put xp...

i will open a thread to know more about this...

regards and thanks,

Dino

---

### Post by naquad on 2007-10-15
I've told you to download drivers package from ati's site. not from repository.

---

### Post by funky_D on 2007-10-15
hmmmm... maybe that's the problem.

many thanks,

D

---

### Post by shareMenaPeace on 2007-12-20
Does anyone has a step by step with getting the files from ati?

And maybe ENVY works?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Im just downloading ubuntu and looking forward to not have any problem, lol .

Thanks

---

