---
title: "Setup Option Missing on Install"
date: 2018-09-25
forum: Hardware
---

### Post by scarboro on 2018-09-25
Friends, I would be most grateful for your help. 

I just bought a new Acer Aspire ES 11 computer.

I installed Xubuntu 18.04.1 LTS with a default install throughout, erasing Windows 10. 

On rebooting, the Acer reported: 'No Bootable Device'.

The Acer's Setup Utility is called InsydeH20.

Reading various help threads, I understood that I would fix this through the Setup Utility by:
[INDENT]Setting Secure Boot to [Enabled] (done)
Setting a Supervisor Password (done)
which would reveal the option 'Select an UEFI file as trusted for executing'[/INDENT]

The problem is that the option 'Select an UEFI file as trusted for executing' does not then appear.  Hence the title of my post.

What should I do?

My complete Setup Utility settings look like this:

Main
[INDENT]System Time
System Date

Network Boot [Disabled]
F12 Boot Menu [Enabled]

Wake on LAN [Disabled]
Touchpad [Advanced]
Lid Open Resume [Disabled]
D2D Recovery [Enabled]
GPT Partition Recovery [None]
Clear GPT Partition [None]
GPT Partition Record No Record[/INDENT]

Security
[INDENT]Supervisor Password Is: Set
User Password Is: Clear
HDD0 Password Is: Clear

Set Supervisor Password: [Enter]
Set User Password [Enter]
Set HDD0 Password [Enter]

Password on Boot [Disabled]

Secure Boot Mode [Standard]
Erase all Secure Boot Setting: [Enter]
Restore Secure Boot to Factory Default: [Enter]

Current TPM (TCM) State: Installed
Change TPM (TCM) State: [Enabled]
Clear TPM (TCM): [Clear][/INDENT]

Boot
[INDENT]Secure Boot: [Enabled]
Boot priority order:
1. HDD0: WDC WD5000LPCX-21VHATO
2. HDD1:
3. ATAPI CDROM:
4. USB FDD:
5. USB CDROM:
6: USB HDD:
7: Network Boot-IPV4:
8. Network Book-IPV6:[/INDENT]

---

### Post by Autodave on 2018-09-26
You could install it in Legacy mode, too.  Did you disable *fastboot?*

---

### Post by oldfred on 2018-09-26
Acer has an unique requirement of setting "trust" in UEFI.
Many Acer also needs UEFI update to latest version available from Acer.

These are all essentially the same, but each may explain it slightly differently or more clearly.
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
   Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by scarboro on 2018-09-26
[COLOR=#333333][FONT=Acer Foco]In the interim, I have this information:  Acer omitted the[/FONT][/COLOR][COLOR=#333333][FONT=Acer Foco] UEFI option "Trusted EFI file for executing" from their E and F series computers.  [/FONT][/COLOR][https://forums.linuxmint.com/viewtopic.php?t=254948](https://forums.linuxmint.com/viewtopic.php?t=254948)[COLOR=#333333][FONT=Acer Foco]  The question then is what next.[/FONT][/COLOR]

---

### Post by oldfred on 2018-09-26
Have you updated UEFI. 
Many threads with Acer in past year, have said UEFI update has fixed that issue.

If not rEFInd may be a way to boot. Or you can copy shimx64.efi to /EFI/Boot/bootx64.efi to use fallback or hard drive boot entry.
I use rEFInd as an emergency boot disk as well as several flash drives with grub or full installs of Ubuntu.

---

