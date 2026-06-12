---
title: "Problem with GRUB2 booting Leopard, Windows 7 &amp; Ubuntu 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by ram130 on 2009-11-02
Well I went the extra step and did a triple boot. OSX Leopard, Windows 7 & Ubuntu 9.10. Everything went great until I rebooted after the second boot up. I was on the LIVE CD and it happen like this, I click Reboot Now when the installation of Ubuntu 9.10 was complete. Then my system rebooted then I got a nice grub2 menu with all of the operating systems detected including OSX, but I didn't test them. I just went straight into my new install of 9.10 and install my ATI driver, copy some files over then restarted. After that I now get a blinking "_". I did not install any updates either. Anyone can help? or anyone can tell me what is going on with grub2?

I am using a GPT partition scheme. Not the MBR.

---

### Post by ram130 on 2009-11-02
Also I have tried a reinstall of grub to no avail.

---

### Post by ram130 on 2009-11-02
I got it fixed by runing grub-install. But Windows 7 and OSX wont boot.

---

### Post by edmondt on 2009-11-02
Not sure if you're running on a real mac, but if I were you I would only install grub on the ubuntu partition, then install [http://chameleon.osx86.hu/](http://chameleon.osx86.hu/) if you're running on a PC, and rEFIT if you're running on a real MAC.

chamelon screenshot:

[IMG]http://www.insanelymac.com/wp-content/uploads/2009/02/24.png[/IMG]

rEFIT screenshot:
[IMG]http://refit.sourceforge.net/img/screen2.png[/IMG]

Hope this helps as an alternative :)

---

### Post by ram130 on 2009-11-03
Thanks edmondt. They look great! I'm running on a PC so I will try Chameleon. Also I did reformat of my hard drive last night and decided to try again, but now when I boot from the Leopard CD, it doesn't see my hard drive. So I decided to just install Windows 7 & Ubuntu for now. Later on I will install leopard on another hard drive then use Chameleon to boot them. 


Thanks alot.

---

### Post by VitaLiNux on 2010-01-21
Hmmmm... You marked this thread as solved, but you haven't said a word about how it was with Chameleon :confused:... Never mind, I'll look into figuring this out myself and I'll post back if I find something relevant...

---

### Post by ram130 on 2010-01-21
> **VitaLiNux said:**
> Hmmmm... You marked this thread as solved, but you haven't said a word about how it was with Chameleon :confused:... Never mind, I'll look into figuring this out myself and I'll post back if I find something relevant...

Hmm don't remember ever doing so. If you please post back.

---

### Post by VitaLiNux on 2010-01-21
I just found this,[COLOR=Blue] [http://www.hackintosh-india.com/2010/01/boot-ext4-partition-using-chameleon.html](http://www.hackintosh-india.com/2010/01/boot-ext4-partition-using-chameleon.html)[/COLOR] haven't yet tried it out myself, but at least looks promising :D

---

### Post by VitaLiNux on 2010-01-21
Oh, well, somebody else did. By the way, can you share how you figured this issue out?

---

### Post by ram130 on 2010-01-22
> **VitaLiNux said:**
> I just found this,[COLOR=Blue] [http://www.hackintosh-india.com/2010/01/boot-ext4-partition-using-chameleon.html](http://www.hackintosh-india.com/2010/01/boot-ext4-partition-using-chameleon.html)[/COLOR] haven't yet tried it out myself, but at least looks promising :D

yes it does...:D 

> **VitaLiNux said:**
> Oh, well, somebody else did. By the way, can you share how you figured this issue out?

I didn't really. Things got worst so I just formatted everything and just worked with Linux and Windows. Now I got a new laptop a month ago with Windows 7. So far I installed Ubuntu but not sure about installing OSX on it without formatting. Don't want to loose  that special recovery partition either just in case of repair.

---

