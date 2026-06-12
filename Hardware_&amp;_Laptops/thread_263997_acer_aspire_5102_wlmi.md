---
title: "acer aspire 5102 wlmi"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by piratedninja06 on 2006-09-24
i just bought an Acer aspire 5012 wlmi laptop and tried running ubuntu 6.06 live on it but for some reason it freezes at the hardware check ive left it on for 3 hours and still nothing happened
ive even tried back|track and the same thing happens

anyone know why this is happening or how to prevent it from happening?

the specs are   turion 64 x2 TL-50 (1.6ghz), 1gb ddr2 533, 120gb pata 4200 rpm hdd, radeon xpress 1100 gfx

---

### Post by unf on 2006-09-24
> **piratedninja06 said:**
> i just bought an Acer aspire 5012 wlmi laptop and tried running ubuntu 6.06 live on it but for some reason it freezes at the hardware check ive left it on for 3 hours and still nothing happened
ive even tried back|track and the same thing happens

anyone know why this is happening or how to prevent it from happening?

the specs are   turion 64 x2 TL-50 (1.6ghz), 1gb ddr2 533, 120gb pata 4200 rpm hdd, radeon xpress 1100 gfx

I recommend the alternative install.  

Check this out. [http://linux-laptop.net/hosted/Fedora-Ubuntu-Acer-Aspire-5102WLMi.html](http://linux-laptop.net/hosted/Fedora-Ubuntu-Acer-Aspire-5102WLMi.html)

---

### Post by piratedninja06 on 2006-09-25
what is the alternative install?  i dont see it

---

### Post by cruiseraddict on 2006-09-27
Are you installing the 32 bit or 64 bit version of dapper?

Dave


> **piratedninja06 said:**
> i just bought an Acer aspire 5012 wlmi laptop and tried running ubuntu 6.06 live on it but for some reason it freezes at the hardware check ive left it on for 3 hours and still nothing happened
ive even tried back|track and the same thing happens

anyone know why this is happening or how to prevent it from happening?

the specs are   turion 64 x2 TL-50 (1.6ghz), 1gb ddr2 533, 120gb pata 4200 rpm hdd, radeon xpress 1100 gfx

---

### Post by Greycloak on 2006-09-27
He wasn't installing, he was trying to run the live cd.

---

### Post by cruiseraddict on 2006-09-28
I have the same laptop and did not have a problem with the live cd. I used the one from Linux Mag Pro Issue 69 August 2006.

I also installed dapper from the same dvd and have not had any issues so far.
dave


> **Greycloak said:**
> He wasn't installing, he was trying to run the live cd.

---

### Post by Xitanto on 2006-09-28
You need to run the command noapic somewhere during the live CD run. It'll be in the boot options. HOWEVER - I tried doing this with the latest livecd and it didn't work. Umm... help guys?

---

### Post by riverty on 2006-09-28
I have an Acer Aspire 5040. In order to get the thing to boot Kubuntu I had to add 'acpi=off' to the boot options to get it to boot. I also had to add 'noapic' in order to get my laptop's wires LAN controller to function. I'm still trying for other problems with my wireless controller but that'a another post. Good luck!

---

### Post by cruiseraddict on 2006-09-28
What does the noapic command do? I have a few lines of code during boot up that I have been meening to investigate. I am not sure what is causing them.

Dave

> **Xitanto said:**
> You need to run the command noapic somewhere during the live CD run. It'll be in the boot options. HOWEVER - I tried doing this with the latest livecd and it didn't work. Umm... help guys?

---

### Post by piratedninja06 on 2006-10-07
> **cruiseraddict said:**
> I have the same laptop and did not have a problem with the live cd. I used the one from Linux Mag Pro Issue 69 August 2006.

I also installed dapper from the same dvd and have not had any issues so far.
dave

can u link me to that download?


also... is there a way i can just use the windows bootloader instead of grub?  because i want to be able to get rid of linux if i install it  without having to reformat my entire hdd    i know i can run  fixboot and fixmbr  from the windows installation cd  but my laptop didnt come with an installation cd so i cant run those commands

---

### Post by lara22 on 2006-11-26
I could run live 6.10 ubuntu cd without any problem. Installation went smoothly. I am not able to access web cam, card reader, and mike [all in-built]. Atheros wifi is working excellently.

---

### Post by RicardoNZ on 2007-02-20
Has anyone had any trouble resizing the windows partition during install?
It's the only thing i'm slightly concerned about before I purchase a 5210WLMi.

Thanks

---

### Post by hizaguchi on 2007-02-28
I resized my Windows partitions with Gparted, no problems.  I'd be more concerned with how flimsy the laptop itself is though.  In the first 4 months with my 5102, the motherboard developed a hairline crack that caused the system to freeze up.  And I baby my computer, carrying it in a waterproof case inside another case.  I had to send it to Acer twice before they finally fixed the problem (first time they replaced a stick of RAM), but now I feel like the computer is too fragile to use away from my desk at home... which kinda defeats the purpose of having a laptop.  :(

---

