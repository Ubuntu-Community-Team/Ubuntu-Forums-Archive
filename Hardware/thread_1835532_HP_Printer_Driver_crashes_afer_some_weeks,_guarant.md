---
title: "HP Printer Driver crashes afer some weeks, guaranteed"
date: 2011-08-29
forum: Hardware
---

### Post by Bramkaandorp on 2011-08-29
The problem has arisen several times now.

I install the drivers for my printer (HP Deskjet 1050), and it will gradually go crazy.

First the scanner doesn't respond, then the HP-Toolbox says that it can't find the printer (whereas it did several days earlier), and finally I get so desperate that I remove the software altogether.

Does HP hate Linux, and is that why their software makes printing a living hell, or is it something on my end?

---

### Post by adotomov on 2011-08-29
I had a similar problem on a ubuntu server 10.10. I have and HP printer installed on it and shared via cups on a local network interface. After a system update the printer crashed and the hp-setup couldn't find it anymore, although the os was recognizing it as a USB attached device. It was a mystery until one day I discovered that I was missing a "models.dat" file. I couldn't restore this file regardless of how many re-installs I did. Got the printer working after a fresh install of 11.04 recently :)

---

### Post by Bramkaandorp on 2011-08-30
> **adotomov said:**
> I had a similar problem on a ubuntu server 10.10. I have and HP printer installed on it and shared via cups on a local network interface. After a system update the printer crashed and the hp-setup couldn't find it anymore, although the os was recognizing it as a USB attached device. It was a mystery until one day I discovered that I was missing a "models.dat" file. I couldn't restore this file regardless of how many re-installs I did. Got the printer working after a fresh install of 11.04 recently :)

If the problem is in 10.04, then I hope the problem isn't in any other distros.

I plan on switching distros altogether. I don't like the new UI Ubuntu uses, I think I'd rather use GNOME 3. (sure, I could do the uninstall/install thing with every new install/version, but honestly, the UI change was is just the last drop for me)

---

### Post by adotomov on 2011-08-30
You can always disable the unity desktop environment and stick to the classic version of it. However, for server purposes I strongly recommend you to not install any graphical UI. Using only the shell is not as difficult as it seems but it is way more stable and secure. 
I have been using 11.04 for about two months (haven't been rebooted it since then) and so far everything works fine.

---

### Post by Bramkaandorp on 2011-08-31
> **adotomov said:**
> You can always disable the unity desktop environment and stick to the classic version of it. However, for server purposes I strongly recommend you to not install any graphical UI. Using only the shell is not as difficult as it seems but it is way more stable and secure. 
I have been using 11.04 for about two months (haven't been rebooted it since then) and so far everything works fine.

Good thing I won't be using it as a server.

I'm just a humble desktop user, who doesn't really like Unity.

Any way, thanks for the info.

---

