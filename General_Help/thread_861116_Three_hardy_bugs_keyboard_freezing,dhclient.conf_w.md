---
title: "Three hardy bugs: keyboard freezing,dhclient.conf working different,alltray not right"
date: 2008-07-16
forum: General Help
---

### Post by skelooth on 2008-07-16
The first, worst, and most crippling is the random keyboard freezing. I made a previous topic here: [http://ubuntuforums.org/showthread.php?t=859453](http://ubuntuforums.org/showthread.php?t=859453) as you can see from that thread the keyboard is not recognized after ubuntu loads... but if I keep restarting and crossing my fingers it will work magically.

I don't know what to do about it, because when I come in in the morning I have to sit there and constantly reboot my LINUX box and I can just picture the windows users laughing and pointing as I struggle to log in 20 minutes later.

Second, i tried the prepend directive in dhclient.conf as well as putting name-server directive but no matter what I do I can't seem to change my default DNS to 192.168.0.77, the closest I've come is getting it to boot up with 192.168.0.1. This used to work find in the previous distro.

Alltray doesn't work right either. I found a solution in the forums but I have to type it manually when the machine comes up, it never makes it into the tray if I set it as a service to begin at startup with [tt]alltray thunderbird[/tt]

Any help? I'm having a love hate relationship with the new hardy. Thanks so much.

---

### Post by skelooth on 2008-07-16
My latest round of questions don't seem to get any responses. Are these problems I'm having that far flung?

---

### Post by prshah on 2008-07-16
> **skelooth said:**
> 
see from that thread the keyboard is not recognized after ubuntu loads... but if I keep restarting and crossing my fingers it will work magically.

Second, i tried the prepend directive in dhclient.conf as well as putting name-server directive but no matter what I do I can't seem to change my default DNS to 192.168.0.77,



1) Is the keyboard USB or PS2? Any chance that the keyboard itself is at fault? Do you have access to Windows to see if the keyboard is OK? Can you try a live CD and check if keyboard is OK?

2) post your "/etc/dhcp3/dhclient.conf" file here for a look.

---

### Post by skelooth on 2008-07-16
Yes, the keyboard is ps2, it works fine in previous versions of ubuntu as well as xp, and just randomly locks when booting into hardy.

Here is a copy of dhclient.conf
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 192.168.0.77
nameserver 192.168.0.77
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


```

---

### Post by skelooth on 2008-07-16
In particular:

I uncommented
```
prepend domain-name-servers 192.168.0.77
```
and entered the address. When that didn't work I added
```
nameserver 192.168.0.77
```

---

### Post by kpatz on 2008-07-16
Try this in your dhclient.conf:

```

supersede domain-name-servers 192.168.0.77;

```

---

### Post by prshah on 2008-07-16
> **skelooth said:**
> 
Here is a copy of dhclient.conf
```

prepend domain-name-servers 192.168.0.77

```

You have to put a semi-colon at the end; eg```
prepend domain-name-servers 192.168.0.77;
```

I don't know what the nameserver line does; unless you're sure you need it, maybe you should just comment it out?

As for your keyboard; try adding the command ```
setxkbmap
``` to the startup sessions; or just run it manually to check if your keyboard still locks. It may have absolutely no bearing at all, this is just a shot in the dark. setxkbmap (re)sets the keyboard languages and preferences, which for some reason [doesn't stick in Hardy]("http://ubuntuforums.org/showpost.php?p=5086906&postcount=3"). However, adding setxkbmap to startup programs clears up this problem; I think it may possibly be of some use to you since hardware problems are ruled out and this is the closest related solution I can think of...

---

### Post by skelooth on 2008-07-16
should I put setxkbmap in rc.local prshah? I don't think putting it in my gnome start up programs would help because I can't get past the login screen

---

### Post by prshah on 2008-07-17
> **skelooth said:**
> should I put setxkbmap in rc.local prshah? I don't think putting it in my gnome start up programs would help because I can't get past the login screen

No I don't think adding it to the rc.local will be of any use; it's specifically for the X environment; anyway it _was_ just a guess. I think you can forget about this piece of advice.

---

### Post by prshah on 2008-07-17
> **skelooth said:**
> Yes, the keyboard is ps2, it works fine in previous versions of ubuntu as well as xp, and just randomly locks when booting into hardy.

Is it likely that you're facing a keyboard IRQ conflict of some sort? This shouldn't happen on PnP systems, but I've seen it happen , though rarely, and only on desktops. Removing and reseating PCI expansion cards in different slots (in some cases, just swapping the positions of two cards) has cleared up the problems I have seen. To check, can you post output of ```
cat /proc/interrupts
```

---

### Post by skelooth on 2008-07-17
```
pavella@patrick:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        170          0   IO-APIC-edge      timer
  1:      23801          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 14:          0          0   IO-APIC-edge      libata
 15:     267280          0   IO-APIC-edge      libata
 16:     413693          0   IO-APIC-fasteoi   ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3
 17:     747480          0   IO-APIC-fasteoi   eth0
 18:      27345          0   IO-APIC-fasteoi   HDA Intel
 19:          0          0   IO-APIC-fasteoi   sata_sil
 20:      96521          0   IO-APIC-fasteoi   sata_sil
 21:    5307479          0   IO-APIC-fasteoi   nvidia
NMI:          0          0   Non-maskable interrupts
LOC:    4162933    4213225   Local timer interrupts
RES:      39671      64973   Rescheduling interrupts
CAL:        196        389   function call interrupts
TLB:      14391       8640   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

---

### Post by evets25 on 2008-07-17
For your DNS setting, there's no need to go mucking about in the config files. You can easily configure this through the GUI. Go to "System -> Administraton -> Networking" and then click on the "DNS" tab. Click add, then type in your DNS address. Done. Now wasn't that simple?

---

### Post by prshah on 2008-07-17
> **skelooth said:**
> ```
pavella@patrick:~$ cat /proc/interrupts
           CPU0       CPU1       
  1:      23801          0   IO-APIC-edge      i8042

```

Ok there's something wrong here. The i8042 chip controls keyboard related signals. It should be present on IRQ 12 as well; Eg:
```
Thu Jul 17 21:38:00 ~:$ cat /proc/interrupts | grep i8042
1:      12413          0   IO-APIC-edge      i8042
12:     306331          0   IO-APIC-edge      i8042
Thu Jul 17 21:39:00 ~:$ dmesg | grep -i "irq 12"
[   45.257882] serio: i8042 AUX port at 0x60,0x64 irq 12

```

what do you get for the "dmesg...grep..." command as shown above?

Maybe you should check in the BIOS if certain interrupts have been "reserved" especially interrupt 12; if so, maybe you should release it?

Alternately, maybe something (wlan) is conflicting with IRQ 12?

Any case, the dmesg command as shown above should give some further clues...

---

### Post by skelooth on 2008-07-18
> **evets25 said:**
> For your DNS setting, there's no need to go mucking about in the config files. You can easily configure this through the GUI. Go to "System -> Administraton -> Networking" and then click on the "DNS" tab. Click add, then type in your DNS address. Done. Now wasn't that simple?
>_>

No, the gui does not permanently set the DSN server, it resets with every reboot.

prshah, thanks again for all of your help, I will post the output when i get back to that machine
```

```

---

### Post by skelooth on 2008-07-18
```
pavella@patrick:~$ dmesg | grep -i "irq 12"
pavella@patrick:~$ 

```

I got nothing

---

### Post by skelooth on 2008-07-21
bump

I still haven't gotten dhclient working, alltray still does not load thunderbird properly on login (well it does sporadically), and keyboard sporadically locks on boot. I don't know where to go from here.

---

### Post by skelooth on 2008-07-21
I just confirmed on my old installation that dhclient.conf is behaving a little bit differently on hardy heron vs gutsy. On previous gutsy install I had
```
prepend domain-name-servers 192.168.0.77
```
And it worked fine. I have the same exact dhclient.conf file now in heron and it still comes up as 192.168.0.1

and checking this is a pain because it takes me 2-3 restarts to get the keyboard working each time!!!! I really wish there was help. Would the commercial support staff be able to fix this?

---

### Post by skelooth on 2008-07-22
bump, especially on the DNS issue.

---

### Post by skelooth on 2008-07-23
bump again, especially for the DNS issue.

---

### Post by skelooth on 2008-07-23
bump?

---

### Post by prshah on 2008-07-24
> **skelooth said:**
> bump

I still haven't gotten dhclient working, 

> **skelooth said:**
> bump, especially on the DNS issue.

> **skelooth said:**
> bump again, especially for the DNS issue.

> **skelooth said:**
> bump?

Did you try adding a semicolon at the end of the line ([as in post #7]("http://ubuntuforums.org/showpost.php?p=5398159&postcount=7"))?

---

### Post by skelooth on 2008-07-24
I have to apologize, I don't think I ever did try putting a semi colon. Putting the semi colon 'sort of' fixes the problem because now it creates a new one. Now when I reboot it puts two entries for DNS: 192.168.0.77 and 192.168.0.1 .... the problem with this is now my computer hangs and gnome panel does not start up properly. I had this problem on Gutsy as well, where if there was a bad DNS entry gnome-panel would not load properly and I would have to wait 5 minutes and mash alt+f2 for the run dialog to open (For whatever reason that would fix it). 

So now how do I get it to NOT add 192.168.0.1? 

Under the current situation it's almost worse, because now I have to wait around mashing alt+F2 to try and get gnome panel to load.

Thank you for coming back and helping prshah. My keyboard has not locked up in two days *knock on wood* and alltray has been behaving again suddenly, so the DNS issue seems to be the last big thing standing between me and productivity in the morning.

---

### Post by prshah on 2008-07-24
> **skelooth said:**
> Putting the semi colon 'sort of' fixes the problem because now it creates a new one.

Did you also undo the other changes you've made as outlined in post #7, eg. comment out "nameservers" line?

The correct syntax is ```

prepend domain-name-servers 208.67.222.222,218.248.255.145,192.168.1.1;

```

Eg, seperate multiple entries with comma, and close the line with a semi-colon.

---

### Post by skelooth on 2008-07-25
Yes, the syntax is 100% correct now as per post #7.

The additional inclusion of the faulty DNS entry has opened a host of new problems...

Aside from the initial wait for gnome-panel to incorrectly load so I can mash alt+F2, I am receiving numerous applet load errors (attatched) and update manager will just hang and not download anything until I've gotten rid of the faulty entry.

copy of dhclient
```
pavella@patrick:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 192.168.0.77;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

What if I tell it not to request DNS servers? I'm not overly familiar with a lot of the unix networking configuration. I just know the basics.

---

### Post by skelooth on 2008-07-25
Am I really the only one having these issues? I can not find anything else about it.

---

### Post by skelooth on 2008-07-28
bump

---

