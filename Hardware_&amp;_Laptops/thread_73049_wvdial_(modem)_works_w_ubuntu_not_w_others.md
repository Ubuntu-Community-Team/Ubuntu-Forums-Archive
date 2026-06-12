---
title: "wvdial (modem) works w/ ubuntu not w/ others"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by towsonu2003 on 2005-10-08
I have a weird problem... First, here is how I bring my modem up:
```
sudo slmodemd --alsa -c USA modem:1 &
sudo wvdial
```

This modem works with ubuntu 5.04 and 5.10. 
For some reason it doesn't work with centOS 4.1; Suse 9.3; Slackware 10.1; Slackware 10.2 (kernel 2.6.13); Knoppix 4.0.2. in all these, you have to bring snd-atiixp-modem module up first)

With ubuntu, after slmodemd, wvdialconf /etc/wvdial.conf sets up modem fine and wvdial dials it almost without problem. 

With CentOS, wvdialconf finds modem but wvdial exits with either No Carrier or No dialtone (Carrier Check = no & Stupid Mode = yes are always in conf file)

With the rest, wvdialconf can't see modem at all. kppp exits with No Carrier. In slackware ppp-go exits with No Carrier. 

I have a "Disabling irq #5; boot with acpi=off" problem with all these distros except ubuntu. acpi=off does not help at all. Also tried acpi=noirq and acpi=noirq acpi=usepirqmask (something like that...), with no success. 

Anyone has any ideas why this is happening? 

Thanks so much for any ideas...

PS. I have a laptop (hp pavilion zv5120us)

---

### Post by towsonu2003 on 2005-10-08
never mind edit

---

### Post by towsonu2003 on 2005-10-13
another never mind edit

---

### Post by towsonu2003 on 2005-10-25
one more never mind edit - sorry (these above were self-evident stupid questions)

---

### Post by towsonu2003 on 2005-12-30
one last bump to see if anyone has any ideas about this issue...

---

