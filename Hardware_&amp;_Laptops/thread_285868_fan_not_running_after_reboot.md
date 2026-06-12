---
title: "fan not running after reboot"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Kakihara on 2006-10-27
Recently i upgraded from dapper to edgy. When I start my computer from 'cool' state, everything(well, not really, but it doesn't matter now) works just fine. Fan is working almost all the time, which is ok for this celeronM machine. But when i start my computer with already warm cpu(eg, restart), the fan stops just after the kernel load and never starts again. Temperature grows until it gets to 105 dgC, when the system switches off automatically(seems to be switched off by the system, not BIOS).
This doesn't happen, when using older kernel from dapper.
Could someone help me please by targeting me to some heat related conf files?
Is there some way to manually switch fans on? Something like echo 1 > /proc/acpi/.... ?
Thanks

---

### Post by villelai on 2006-10-27
I have exactly same problem with my F-S Amilo L1310G laptop. And have no solution yet. :(
...and this laptop has celeron M too (1600Mhz).

---

### Post by chippy99 on 2006-10-27
Its more likely to be a hardware fault rather than a problem with the OS. What happens if you start it from warm and dont load the OS ?

---

### Post by villelai on 2006-10-27
Fan stops when ubuntu starts loading. So I think that's not hardware issue. Fan stops even if I boot to rescue mode.

---

### Post by Kakihara on 2006-10-27
yes, Amilo L1310G
exactly the same piece of trash as mine.
The only solution i figured out is to boot 2.6.15 kernel from dapper.
This is definetely a problem of kernel upgrade.

---

### Post by Eversmann on 2006-11-05
Hi guys.

Same problem here, amilo l1310g, with kernel 2.6.15 fan is always on, but with latest 2.6.17, general and 386, the fan stops.  Looks like it's a problem with the kernel and our bios or atiixp chipset. Boot with acpi=off and you'll see how the fan turns on like in 2.6.15.

Actually, since last days, i have the fan working the way it should be (you know, not always on, just when it's necessary).

Try these things: boot with nolapic on the kernel and be very sure to have ati driver installed (from repositorios and restricted modules are ok, working here).

I've noticed that, if i do some testing, and in the process the temperature goes above 70º, no more fan for me, i have to let it cool down, and after that (from 47º) it works again.

I've booting it today 5 times and the fan is working, 53º right now here.

I've already filled a bug at launchpad. I'll have the wiki page about amilo l1310g updated.

---

### Post by Kakihara on 2006-11-07
Thanks. I added nolapic and noapic and fan seems to work fine now, even if I don't have ati drivers fully working(couldn't make them run since dapper->edgy upgrade. which version of ati drivers do you use btw? acceleration works?)

---

### Post by Eversmann on 2006-11-08
Actually i'm booting with noapic (working better than nolapic).

I'm using the fglrx version that comes with edgy, installing the restricted modules for the kernel and the fglrx-xorg package.

I've tested the latest 8.30 and works too.

Right now, no problems with fans since i posted, working great.

---

### Post by Kakihara on 2006-11-08
All right. Fglrx is working now. Thanks for your help. The only issues left for this amilo laptop is hybernate, suspend and to force NetworkManager to work with wifi. This is probably not the right place to ask, but do you have some hints about these problems?

---

### Post by Eversmann on 2006-11-08
Suspend is a common issue with fglrx drivers i think, and hybernation (is that when ubuntu saves the memory state to hard disk for later speeding up the boot?) works.

I haven't tested network manager lately, because i got sick of it on dapper. The main problems was wpa_supplicant with madwifi drivers and the version of networkmanager needed to be patched because of that.

I've been using command line and iwconfig commands to connecto to networks, and manual wpa_supplicant for the hard ones (PEAP, WPA-PSK, you know..)

To make it to work, i had to download wpa_supplicant sources and compile for madwifi manually. Doing that way, wpa_supplicant works great, but now you've mentioned network manager, i've just installed it, run nm-applet, and i've just connected to my network and the associating and dhcp time worked.

So looks like you have to compile wpa_supplicant the way i said. If you have problems with it, reply here and i'll post a how-to for doing that, is not very difficult but it has some tricks.

---

### Post by Kakihara on 2006-11-23
Ok, i did not have much time for experiments, but one thing i know for sure: i will stick with 2.6.15 kernel. The noapic does only work sometimes.
Did someone had better luck with this amilo l? did you try another kernel>2.6.15 or another distribution which worked? And did anybody get suspend to ram working?
I will try to get my laptop fully working asap. Be it with ubuntu or not..

---

### Post by onefilip on 2008-01-22
hi have fujitsu siemens L1310G with ubuntu 7.10 
2.6.22-14-generic
I have fan always on... 
can you help me?
with winZoz xp the fans work normal always when there are some process in axecution!
with ubuntu the fans always on!
with the command ACPI -V I can see the temperature is 47 °C wth intel celeron M 1,6 GHz.
heeeelppppp

---

