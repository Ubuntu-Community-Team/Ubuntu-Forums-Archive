---
title: "Trying to add Windows Client drivers via cupsaddsmb fails with WERR_INVALID_PRINTER_N"
date: 2016-10-03
forum: Hardware
---

### Post by Macbuntu-Windows-7-User on 2016-10-03
It's been a while since I posted on here (far too long to be exact), and I'm trying to have Lubuntu 16.04.1 to create drivers for Windows clients for both 32-bit and 64-bit OSes alike.

I run the following command:

```

sudo cupsaddsmb -H localhost -U root -a -v PSC-750

```

And this is the error I get:

```

Password for root required to access localhost via SAMBA:  ************
Running command: smbclient //localhost/print$ -N -A /tmp/0352857fbad06 -c 'mkdir W32X86;put /tmp/0352857f62d72 W32X86/PSC-750.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]
NT_STATUS_OBJECT_NAME_COLLISION making remote directory \W32X86
putting file /tmp/0352857f62d72 as \W32X86/PSC-750.ppd (11734.8 kb/s) (average 11735.4 kb/s)
putting file /usr/share/cups/drivers/ps5ui.dll as \W32X86/ps5ui.dll (63082.8 kb/s) (average 55747.9 kb/s)
putting file /usr/share/cups/drivers/pscript.hlp as \W32X86/pscript.hlp (25425.3 kb/s) (average 53726.6 kb/s)
putting file /usr/share/cups/drivers/pscript.ntf as \W32X86/pscript.ntf (41427.5 kb/s) (average 46039.7 kb/s)
putting file /usr/share/cups/drivers/pscript5.dll as \W32X86/pscript5.dll (50363.2 kb/s) (average 46972.3 kb/s)

Running command: smbclient //localhost/print$ -N -A /tmp/0352857fbad06 -c 'put /usr/share/cups/drivers/cups6.ini W32X86/cups6.ini;put /usr/share/cups/drivers/cupsps6.dll W32X86/cupsps6.dll;put /usr/share/cups/drivers/cupsui6.dll W32X86/cupsui6.dll'
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]
putting file /usr/share/cups/drivers/cups6.ini as \W32X86/cups6.ini (70.3 kb/s) (average 70.3 kb/s)
putting file /usr/share/cups/drivers/cupsps6.dll as \W32X86/cupsps6.dll (12272.2 kb/s) (average 6171.9 kb/s)
putting file /usr/share/cups/drivers/cupsui6.dll as \W32X86/cupsui6.dll (4450.4 kb/s) (average 5139.1 kb/s)

Running command: rpcclient localhost -N -A /tmp/0352857fbad06 -c 'adddriver "Windows NT x86" "PSC-750:pscript5.dll:PSC-750.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,PSC-750.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"'
Printer Driver PSC-750 successfully installed.

Running command: rpcclient localhost -N -A /tmp/0352857fbad06 -c 'setdriver PSC-750 PSC-750'
result was WERR_INVALID_PRINTER_NAME

Unable to set Windows printer driver (1).
Running command: smbclient //localhost/print$ -N -A /tmp/0352857f58ce2 -c 'mkdir W32X86;put /tmp/0352857f62d72 W32X86/PSC-750.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]
NT_STATUS_OBJECT_NAME_COLLISION making remote directory \W32X86
putting file /tmp/0352857f62d72 as \W32X86/PSC-750.ppd (11734.8 kb/s) (average 11735.4 kb/s)
putting file /usr/share/cups/drivers/ps5ui.dll as \W32X86/ps5ui.dll (37849.8 kb/s) (average 35475.9 kb/s)
putting file /usr/share/cups/drivers/pscript.hlp as \W32X86/pscript.hlp (25425.3 kb/s) (average 35039.1 kb/s)
putting file /usr/share/cups/drivers/pscript.ntf as \W32X86/pscript.ntf (54509.8 kb/s) (average 43847.4 kb/s)
putting file /usr/share/cups/drivers/pscript5.dll as \W32X86/pscript5.dll (55399.5 kb/s) (average 46069.0 kb/s)

Running command: smbclient //localhost/print$ -N -A /tmp/0352857f58ce2 -c 'put /usr/share/cups/drivers/cups6.ini W32X86/cups6.ini;put /usr/share/cups/drivers/cupsps6.dll W32X86/cupsps6.dll;put /usr/share/cups/drivers/cupsui6.dll W32X86/cupsui6.dll'
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]
putting file /usr/share/cups/drivers/cups6.ini as \W32X86/cups6.ini (6.4 kb/s) (average 6.4 kb/s)
putting file /usr/share/cups/drivers/cupsps6.dll as \W32X86/cupsps6.dll (4091.0 kb/s) (average 881.7 kb/s)
putting file /usr/share/cups/drivers/cupsui6.dll as \W32X86/cupsui6.dll (2670.3 kb/s) (average 1352.4 kb/s)

Running command: rpcclient localhost -N -A /tmp/0352857f58ce2 -c 'adddriver "Windows NT x86" "PSC-750:pscript5.dll:PSC-750.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,PSC-750.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"'
Printer Driver PSC-750 successfully installed.

Running command: rpcclient localhost -N -A /tmp/0352857f58ce2 -c 'setdriver PSC-750 PSC-750'
result was WERR_INVALID_PRINTER_NAME

Unable to set Windows printer driver (1).
Running command: smbclient //localhost/print$ -N -A /tmp/0352857fd2db8 -c 'mkdir W32X86;put /tmp/0352857f62d72 W32X86/PSC-750.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]
NT_STATUS_OBJECT_NAME_COLLISION making remote directory \W32X86
putting file /tmp/0352857f62d72 as \W32X86/PSC-750.ppd (23468.4 kb/s) (average 23470.7 kb/s)
putting file /usr/share/cups/drivers/ps5ui.dll as \W32X86/ps5ui.dll (39841.9 kb/s) (average 39023.5 kb/s)
putting file /usr/share/cups/drivers/pscript.hlp as \W32X86/pscript.hlp (12713.2 kb/s) (average 36631.7 kb/s)
putting file /usr/share/cups/drivers/pscript.ntf as \W32X86/pscript.ntf (64730.3 kb/s) (average 48462.9 kb/s)
putting file /usr/share/cups/drivers/pscript5.dll as \W32X86/pscript5.dll (34624.8 kb/s) (average 44362.8 kb/s)

Running command: smbclient //localhost/print$ -N -A /tmp/0352857fd2db8 -c 'put /usr/share/cups/drivers/cups6.ini W32X86/cups6.ini;put /usr/share/cups/drivers/cupsps6.dll W32X86/cupsps6.dll;put /usr/share/cups/drivers/cupsui6.dll W32X86/cupsui6.dll'
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]
putting file /usr/share/cups/drivers/cups6.ini as \W32X86/cups6.ini (70.3 kb/s) (average 70.3 kb/s)
putting file /usr/share/cups/drivers/cupsps6.dll as \W32X86/cupsps6.dll (12272.2 kb/s) (average 6171.9 kb/s)
putting file /usr/share/cups/drivers/cupsui6.dll as \W32X86/cupsui6.dll (1668.9 kb/s) (average 2569.5 kb/s)

Running command: rpcclient localhost -N -A /tmp/0352857fd2db8 -c 'adddriver "Windows NT x86" "PSC-750:pscript5.dll:PSC-750.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,PSC-750.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"'
Printer Driver PSC-750 successfully installed.

Running command: rpcclient localhost -N -A /tmp/0352857fd2db8 -c 'setdriver PSC-750 PSC-750'
result was WERR_INVALID_PRINTER_NAME

Unable to set Windows printer driver (1).

```

I have smbclient installed as well, and I don't know what's going on.  It does install the drivers in the designated folders without issues, just would give me errors. What did I miss?

Edit: I edited the smb.conf file to have parameters for my printer, which did the trick, and all is well!

Now, the other issue is, the x64 drivers aren't installing.  The OS my computer is running is Lubuntu 16.04.1 32-bit since my other 1GB stick crashes the installer while the other 1GB stick does not.

Specs:
PCChips Socket 754 Motherboard
AMD Athlon 64 3000+ @2GHz
1GB DDR-333 RAM
320GB Toshiba 2.5" SATA HDD
Lite-On DVD Burner
Mitsumi CD Drive
1.44MB Floppy Drive
520W Corsair PSU

---

