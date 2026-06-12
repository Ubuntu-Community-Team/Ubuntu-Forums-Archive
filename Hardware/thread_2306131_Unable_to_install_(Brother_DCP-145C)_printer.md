---
title: "Unable to install (Brother DCP-145C) printer"
date: 2015-12-12
forum: Hardware
---

### Post by manolomanolo on 2015-12-12
Hi to all,

After so many tries I declare that I am unable to install **Brother DCP-145C** and Canon i-Sensys LBP2900 printers.

Of course I've tried both letting Ubuntu install the printers with its own drivers and also installing the official drivers by myself: no success in both cases.

Could you please help me installing at least one of those?

Thanks in advance.
Regards.
Manolo

---

### Post by gifford on 2015-12-12
Have you downloaded the drivers from the Brother site? Is this to be a USB connection or network?

---

### Post by manolomanolo on 2015-12-13
Hi gifford,

first of all, thanks for your reply.
Yes, I've been trying to install the printer through the official drivers. I've been trying with both the USB and the network connection. Let's talk about the Brother printer with USB connection first. Actually I've been trying to install 2 Brother models following the instructions on the Brother website: both the DCP-145C (see install instructions [here]("http://support.brother.com/g/b/downloadlist.aspx?c=it&lang=it&prod=dcp145c_eu_as&os=128&flang=English"), drivers dated 2008) and the MFC-J470DW (see install instructions [here]("http://support.brother.com/g/b/downloadlist.aspx?c=it&lang=it&prod=mfcj470dw_us_eu_as&os=128&flang=English"), drivers dated 2013). No success in both cases, either installing the drivers directly or through the "**Driver Install Tool**" dated 2014. I remark that I have such problems since early 2014, as reported [here]("http://ubuntuforums.org/showthread.php?t=2206287") (the post was related to Canon printer, but I was unable to install the Brother printer as well).

I've been also trying to install the printers through the Ubuntu ***system-config-printer*** tool: no success.
I've been also trying to install all the cups/brother support from Ubuntu default repositories before trying to install the printers as per the tries explained above: no success anyway.

As you can see the problem is quite old as well as the official/unofficial guides to solve it (for example, see [here]("http://ubuntuforums.org/showthread.php?t=590793") and [here]("http://www.linux-hardware-guide.com/uk/2013-11-28-brother-dcp-1510-all-in-one-scanner-a4-laser-usb-2-400-x-600dpi") - the latter is related to another model but it may inspire a general installation procedure)

At the moment the situation is quite critical since maybe there's a mess in my Ubuntu box due to such so many tries (see attached screen-shot).
Moreover I'm not able to update my Ubuntu OS since there's a problem with some of the packages installed to configure the printers. In detail I'm asked to reinstall the dcp145clpr:i386 package in order to solve the problem, but this is what I get when I try to reinstall it:

```
$ sudo dpkg -i ./dcp145clpr-1.1.2-2.i386.deb 
Selezionato il pacchetto dcp145clpr:i386 non precedentemente selezionato.
(Lettura del database... 221185 file e directory attualmente installati.)
Preparativi per estrarre ./dcp145clpr-1.1.2-2.i386.deb...
Estrazione di dcp145clpr:i386 (1.1.2-2) su (1.1.2-2)...
[....] [B][I]Restarting lpd (via systemctl): lpd.serviceFailed to restart lpd.service: Unit lpd.service failed to load: No such file or directory.
 failed![/I][/B]
dpkg: attenzione: il sottoprocesso vecchio script di post-removal ha restituito lo stato di errore 6
dpkg: viene provato lo script dal nuovo pacchetto...
[....] Restarting lpd (via systemctl): lpd.serviceFailed to restart lpd.service: Unit lpd.service failed to load: No such file or directory.
 failed!
dpkg: errore nell'elaborare l'archivio ./dcp145clpr-1.1.2-2.i386.deb (--install):
 il sottoprocesso nuovo script post-removal ha restituito lo stato di errore 6
[....] Restarting lpd (via systemctl): lpd.serviceFailed to restart lpd.service: Unit lpd.service failed to load: No such file or directory.
 failed!
dpkg: errore durante la pulizia:
 il sottoprocesso nuovo script post-removal ha restituito lo stato di errore 6
Si sono verificati degli errori nell'elaborazione:
 ./dcp145clpr-1.1.2-2.i386.deb
```


I am not able to uninstall it either. So, that's the current situation. I suppose I should clear the situation by uninstalling such modules (see screenshots) and/or packages and consequently try to follow correct install instructions.

Any suggestion, please?
Thanks so much.
Regards.

---

### Post by gifford on 2015-12-13
I have always used the command line instructions from the Brother site to install my printers. I do not use the install script nor try to install through the the Ubuntu configuration.
Are you still using Kubuntu 13.04?

---

### Post by manolomanolo on 2016-01-09
hi gifford,
Sorry for my late reply.
Using Ubuntu 15.10. However I just reinstalled the OS from scratch since my tries to install the printers left my system in an unstable state... unbelievable!
Well, what should i do to install the printer? May you want to suggest me the command line instructions to install the printer?

Thanks,
Regards.

---

### Post by SeijiSensei on 2016-01-10
I have a networked Brother printer that installed cleanly using the Printer Install Tool on the Brother site.

---

