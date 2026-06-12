---
title: "Windows XP cannot find printer shared over Samba"
date: 2010-10-18
forum: Hardware
---

### Post by vaul on 2010-10-18
I have Cannon MF 4018 multi functional. Drivers are in place, printer is selected as "Shared" in the Printing dialogue.

However, Windows XP laptop, connected to the home network still cannot find it, despite the Ubuntu machine showing in the dialogue.

Any ideas?

---

### Post by Morbius1 on 2010-10-18
One way around this is not to use Samba to share the printer. But anyway, let's make sure some of the fundamentals are in place:

(1) Make sure CUPS has the printer shared:
Administration > Printing > Right Click the attached printer > Properties > Policies
Check Enabled, Accepting Jobs, and Shared

(2) Make sure CUPS has the printer published:
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system

(3) Make sure that samba allows guest access to printer:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And make the [printers] section has guest ok = yes:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]    guest ok = yes[/COLOR]
;    read only = yes
    create mask = 0700(4) See if you are affected buy a bug in the startup of services.
[COLOR=Blue][I]Note: Check for this after you can confirm to yourself that the first 3 points are checked. This bug doesn't affect everyone so there's no reason to work around it if it isn't a problem.
[/I][/COLOR]
There is a bug where cups starts after samba starts. It should be the other way around because samba gets the printer list from cups. If cups hasn't started when samba checks the printer list then there are no visible printers on the network. To check restart the services in this order and see if the printer is visible:
```
sudo service cups restart
``````
sudo service smbd restart
```

---

### Post by vaul on 2010-10-18
Entries one and two were all right, but I have noticed that "guest ok" parameter was set to "no" for some reason and put "yes" there.

I have saved file, then restarted services, as you suggested, but it had no effect on the visibility of printer on the Windows XP laptop.

Is there anything else I should try?

---

### Post by Morbius1 on 2010-10-18
The next thing I would check is the ubuntu firewall. If you haven't done anything to it it should be ok, To check if the right ports are open you can install the following packge:
```
sudo apt-get install nmap
```Then run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the Ubuntu machine that has the printer attached to it.*[/COLOR]
You will get an output something like this:
> PORT     STATE         SERVICE
[COLOR=Blue]139/tcp  open          netbios-ssn[/COLOR]
[COLOR=Blue]445/tcp  open          microsoft-ds[/COLOR]
[COLOR=Blue]631/tcp  open          ipp[/COLOR]
68/udp   open|filtered dhcpc
[COLOR=Blue]137/udp  open|filtered netbios-ns[/COLOR]
[COLOR=Blue]138/udp  open|filtered netbios-dgm[/COLOR]
[COLOR=Blue]631/udp  open|filtered ipp[/COLOR]
5353/udp open|filtered zeroconThe ones in blue are what you need to be open.

---

### Post by vaul on 2010-10-18
Output was:

```


paulsomebody@paulsomebody-desktop:~$ sudo nmap -sS -sU -T4 192.168.1.2

Starting Nmap 5.21 ( http://nmap.org ) at 2010-10-18 23:19 EEST
Nmap scan report for paulsomebody-desktop (192.168.1.2)
Host is up (0.016s latency).
Not shown: 1989 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
631/tcp  open          ipp
901/tcp  open          samba-swat
8089/tcp open          unknown
9091/tcp open          unknown
68/udp   open|filtered dhcpc
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
631/udp  open|filtered ipp
5353/udp open|filtered zeroconf

```

I assume everything is okay here. What else could it be?

---

### Post by Morbius1 on 2010-10-18
I just did a quick check on that printer model and there's not a lot of information on it out there. Couldn't find it on canon's own site.

The only thing I have left is to not use samba. In the WinXP printer wizard don't browse for it but tell it explicitly where to find it by using one of these two formats:

(1) 
\\WORKGROUP_NAME\MACHINE_NAME\Printer_Name
\\MACHINE_NAME\Printer_Name
\\192.168.1.2\Printer_Name

(2) This is the method I use:
[http://192.168.1.2:631/printers/Printer_Name](http://192.168.1.2:631/printers/Printer_Name)

---

### Post by vaul on 2010-10-18
I have added it with "http://192.168.1.2:631/printers/canon", it was added and I installed drivers, but any attempt to print anything do not give any result.

I'll try different port.

---

### Post by Morbius1 on 2010-10-18
You can't use a different port. 631 is cups. You are accessing the cups server on the ubuntu machine directly over http. It's the most direct way.

I'm at a loss at the moment. In fact except for some mac specific stuff you basically know everything I do about printing I'm afraid.

---

### Post by vaul on 2010-10-18
Could problem be at a Windows XP side? I'll take a look.

---

### Post by leifwi on 2010-10-19
I have the same problem. File sharing is OK, but printer is not visible. If I leave the XP machine on for at least 30 minutes, the printer might suddenly turn up and I can install the driver. After that printing sometimes work and sometimes not. It seems I can print after making a few attempts and having the XP PC on long enough. I don't understand why sharing a ubuntu printer have to be so difficult! I tried to update to 10.10 but no improvement.:(

---

### Post by vaul on 2010-10-19
I don't think it's actually Ubuntu, I have added printer the way Morbius1 suggested, with "http://192.168.1.2:631/printers/canon", it was successfully added, but still I can't print anything from XP &#8212; documents are added, but they stay forever as "processed" in the queue.

---

### Post by kendoori on 2010-11-28
> **Morbius1 said:**
> 
(4) See if you are affected buy a bug in the startup of services.

There is a bug where cups starts after samba starts. It should be the other way around because samba gets the printer list from cups. If cups hasn't started when samba checks the printer list then there are no visible printers on the network. To check restart the services in this order and see if the printer is visible:


Turns out that I am impacted by this bug. Restarting the services in the correct order, fixed this for me. How can I change this permanently?

Spoke to soon, two fixes are suggested here: [http://ubuntuforums.org/showthread.php?t=1553166&page=1]("http://ubuntuforums.org/showthread.php?t=1553166&page=1")

---

