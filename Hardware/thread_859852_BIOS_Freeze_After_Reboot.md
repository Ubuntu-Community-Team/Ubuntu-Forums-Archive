---
title: "BIOS Freeze After Reboot"
date: 2008-07-15
forum: Hardware
---

### Post by thegodfaza on 2008-07-15
After I reboot my laptop ( Toshiba A215-S5818 ) my BIOS screen freezes up and I have to force it to shutdown then turn it back on again. I'm not sure what's causing the problem.

---

### Post by Afkpuz on 2008-07-15
Goto your laptops manufacturer page and find out how to update the bios.  Sounds like it needs to be reinstalled

---

### Post by thegodfaza on 2008-07-15
I know it's an Ubuntu problem since other OS's (like live dvd's) reboot just fine. I think the problem started when virtual box installed a kernel I didn't want and I removed it.

---

### Post by thegodfaza on 2008-07-15
I did a BIOS update just for kicks and giggles and I still have the problem.

---

### Post by thegodfaza on 2008-07-15
I have figured out what is causing the problem but I don't know how to fix it. It's ndiswrapper. When I flip the switch on my network card to off then restart it goes fine. And the problem started right after I installed ndiswrapper.

---

### Post by Devil999 on 2008-09-12
I'm having the exact same problem. The difference is that I don't have ndiswrapper installed. Even if a do a clean install of ubuntu in my laptop, without ever plugging the wireless card, the computer won't reboot.

Did you find out how to solve it? It was really ndiswrapper? Some info on how to solve it would be great!

Thanks :)

---

### Post by IntuitiveNipple on 2008-09-12
> **Devil999 said:**
> I'm having the exact same problem. The difference is that I don't have ndiswrapper installed. Even if a do a clean install of ubuntu in my laptop, without ever plugging the wireless card, the computer won't reboot.

It isn't the *exact same* problem since:
[list=1]
[*] Not using ndiswrapper
[*] 'without ever plugging the wireless card' - does this mean "without plugging in the wireless card"? If it does, that indicates an external wireless device, not an internal one. Or, does it mean "without switching the wireless radio on", which would be sensible if the wireless device is internal.
[/list]
When reporting issues *please* be specific if you expect people to be able to make useful suggestions, and attach (a compressed) copy of the start-up log-file /var/log/dmesg so we know what Linux finds as it starts.

---

### Post by Devil999 on 2008-09-12
> **IntuitiveNipple said:**
> It isn't the *exact same* problem since:
[list=1]
[*] Not using ndiswrapper
[*] 'without ever plugging the wireless card' - does this mean "without plugging in the wireless card"? If it does, that indicates an external wireless device, not an internal one. Or, does it mean "without switching the wireless radio on", which would be sensible if the wireless device is internal.
[/list]
When reporting issues *please* be specific if you expect people to be able to make useful suggestions, and attach (a compressed) copy of the start-up log-file /var/log/dmesg so we know what Linux finds as it starts.

My bad. What I meant was that I was having the same problem, that is, the computer freezing during boot.
I do have an external card, which is why I said that I didn't plug it in since last reinstall. As such, I also never installed 
ndiswrapper. 
Unfortunately, I'm not near my computer now, and so I can't post here my log file, but I found it curious that the problem was the same, and was hoping that thegodfaza (or anyone else, for that matter) could help me with some general info. Maybe this is a common problem.
And something else that maybe is important: my laptop is quite old (should have like 10years now), and there are no updates to the BIOS.

Thanks.

---

### Post by IntuitiveNipple on 2008-09-12
> **Devil999 said:**
> My bad. What I meant was that I was having the same problem, that is, the computer freezing during boot.
Thanks for clarifying that :)

Let's think of it as a *similar* symptom that may or may not have the same cause.

It really helps for people like me thinking of possible solutions since if we're fed incorrect details we may well make incorrect assumptions when we're trying to narrow down potential causes in order to suggest additional diagnostics, which then leads to confusion and frustration on all sides.

---

