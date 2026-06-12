---
title: "Suspend on HP NC6400"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by fbn on 2006-12-14
Hi,

I'm trying to get suspend to work on HP NC6400 laptop with Ubuntu 6.10

If I select suspend in logoff menu the screen goes blank and the laptop powerless - that works. But if I power it on again the screen stays black. I hear the cooler spinning up and it seems that something is happening. I have to power it off the hard way and then Ubuntu boots normal but all open applications are lost.

Logfile says not much:
Dec 14 22:28:11 dettb178 gnome-power-manager: (deniedfr) Der Rechner wird in Bereitschaft versetzt weil die D-BUS-Methode Suspend() wurde aufgerufen
Dec 14 22:28:13 dettb178 kernel: [17179687.024000] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Dec 14 22:28:13 dettb178 kernel: [17179687.256000] ACPI: PCI interrupt for device 0000:10:00.0 disabled
Dec 14 22:28:16 dettb178 kernel: [17179689.632000] Freezing cpus ...
Dec 14 22:28:16 dettb178 kernel: [17179689.748000] CPU 1 is now offline
Dec 14 22:28:16 dettb178 kernel: [17179689.748000] SMP alternatives: switching to UP code
Dec 14 22:30:32 dettb178 syslogd 1.4.1#18ubuntu6: restart.

Any idea how to solve this?

Thanks,
  Frank

---

### Post by nmincone on 2006-12-21
Everyone with suspend/hibernation problems, please STF before asking your questions, chances are it has already been addressed.


[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

### Post by fbn on 2006-12-22
> **nmincone said:**
> Everyone with suspend/hibernation problems, please STF before asking your questions, chances are it has already been addressed.


[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

Hi,

what ist STF?

Some month ago HP told that they support Ubuntu on their laptops. There was even a special branded HP version of Ubuntu (changes went into main Ubuntu then).

So why is it that difficult to get suspend/hibernation to work with HP laptops? Has anyone got it to work right now or is it impossible?

Are there plans to get it to work with Ubuntu 7.04? Who can I contact to help out with testing for example?

Frank

---

### Post by nmincone on 2006-12-22
STF=Search The Forums

Frank, I completely agree with you. I have been assisting other users with their laptop & desktop suspension/hibernation problems but have not found a solution to my own. I have a hp nx9010, and suspect my issue is related to my Linksys WiFi PCMCIA card, or ATI mobility chipset.

---

### Post by chris_c28 on 2007-02-18
Came across this thread randomly, but since I'm using the same laptop, I'll post my thoughts on the issue. Resume and hibernation works fine on Ubuntu Edgy with SATA native mode turned off in the BIOS configuration.

---

### Post by fbn on 2007-02-19
what are the effects on the system if SATA mode is turned off in BIOS? are the harddisks slower?

---

### Post by canatella on 2007-02-20
I have exactly the same problem here.  Maybe you've been bitten by [https://launchpad.net/ubuntu/+source/acpi-support/+bug/67710](https://launchpad.net/ubuntu/+source/acpi-support/+bug/67710)

Do you have and ICH6 intel chipset ? (hint: $ lspci)

I've already searched the forum, launchpad, kernel bugzilla many times, but I can't find a solution. 

I think the problem has something to do with IDE because I tried booting in single mode with only the ide and ext3 module loaded and then to suspend to ram but it still did not work. Unfortunatly, there is no way I can debug this.

---

