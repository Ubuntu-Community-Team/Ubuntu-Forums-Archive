---
title: "wlan0 not starting at boot w/Ndiswrapper and Dell TrueMobile 1300"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by darthsabbath on 2005-03-09
Hi guys,

Having an issue with my Dell Inspiron 5100 and Ubuntu Warty, and the above mentioned card, in that I cannot get it to start at boot.  I can manually configure it each time by issuing iwconfig wlan0 essid ESSID key open s:xxxxxxxxxxxxx, then running dhclient.  But when the laptop is restarted, I have to run it again.

Using the Networking applet unfortunately did not help matters either.  The laptop works fine as long as I go through and do thing manually.  I do have ndiswrapper starting at boot as well.  I don't need a fancy GUI to resolve this issue, and I have no problem editing conf files.  

If any output/files are needed, please let me know.

Thanks,
Phil

---

### Post by burlap on 2005-03-09
Check contents of /etc/network/interfaces.

I have (numbers are crossed out by myself):
```

iface wlan0 inet static
name Bezprzewodowa karta LAN
address 192.168.x
netmask 255.255.255.0
broadcast 192.168.x
network 192.168.x
gateway 192.168.x
wireless_essid xxxxxx
wireless_key xxxxxxxxxxxxxxxxxxxxxxxxx

auto wlan0

```

---

### Post by acascianelli on 2005-03-11
are you loading the ndiswrapper at boot?

1) ndiswrapper -m
2) modprobe ndiswrapper
3) insmod ndiswrapper

---

### Post by Hemulen on 2005-03-15
Have you tried to add 'ndiswrapper' to your /etc/modules file?

---

### Post by darthsabbath on 2005-03-16
Just an update... been working on some other issues the last few days.

Still no luck... editing /etc/network/interfaces, no luck... Ndiswrapper is installed as a module. 

Again, the wireless is working, but I have to manually configure it.  Here is my /etc/network/interfaces file:

auto wlan0
iface wlan0 inet dhcp
wireless_essid xxxx
wireless_key xxxx
wireless_keymode open

Should I hvae the IP address, gateway, and subnet mask in there if I'm using DHCP?

I know my card works... it worked fine with both Mandrake 10.1 and SUSE 9.2.  However, both of those are monstrous distros, and if at all possible, I really want to get Ubuntu working.

Phil

---

### Post by acascianelli on 2005-03-16
i had a problem getting mine to work also, i made a thread about it...

[http://www.ubuntuforums.org/showthread.php?t=16591](http://www.ubuntuforums.org/showthread.php?t=16591)

see if you can get anything out of it.

---

### Post by darthsabbath on 2005-03-16
[QUOTE=acascianelli]i had a problem getting mine to work also, i made a thread about it...

[http://www.ubuntuforums.org/showthread.php?t=16591](http://www.ubuntuforums.org/showthread.php?t=16591)

see if you can get anything out of it.[/QUOTE]

Yeah, I went through that post, unfortunately didn't lead me anywhere.  The situation's different... unlike yours, mine card detects my WAP, and I can connect to it... it just requires a manual connection each time.

Thanks though... wish I could help with your issue, as it's something I'm interested in for when I get back into school and will need to connect to more than just my home WAP. :D

Phil

---

### Post by darthsabbath on 2005-03-18
Another update...

Installed Hoary preview release as a clean install.  Cleared up a lot of my hangs and crashes I was experiencing with Warty, but now ndiswrapper is not even seeing my WAP.  In Warty, I could use the wireless card aftermanually configuring it, but now when I run iwlist wlan0 scan, it doesn´t even see my WAP. *sighs*

Maybe I should just go back to Mandrake or SUSE on the laptop... Ubuntu is running fine on the desktop, and fully intend to keep it there, but this wireless problem is driving me nuts.  MEPIS was the same way... just would not see my WAP, even if I manually entered in all the information.  ](*,) 

Any assistance would be wonderful. :/

---

### Post by axmanak on 2005-03-18
It was the other way with my TrueMobile: ndiswrapper would not load at boot time on warty, but now on hoary everything works  (same kernel version, same /etc/modules ).

I have no clue, why it works now...

---

### Post by darthsabbath on 2005-03-18
Found something [at this link](http://ubuntuforums.org/showthread.php?t=20120&highlight=hoary+ndiswrapper)  on Hoary, gonna try it when I get home... 

Phil

---

### Post by darthsabbath on 2005-03-21
The link listed above resolved the issue.

Thanks to everyone who helped!

Phil

---

