---
title: "Intel Centrino 1000 N Wifi"
date: 2012-03-08
forum: Hardware
---

### Post by Blueartisan on 2012-03-08
Hi all,

I am a completely noob user at Linux. I followed many other threads posted on google but have no idea how to fix this. Thank you for all your help. It still says Wireless is disabled by hardware switch in the Wifi option  top right. Furthermore, I checked the switch and it is in the right  place. I have the correct driver installled in lib/firmware. Thank you again.

ron@Ideapad:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
ron@Ideapad:~$ rfkill unblock all
ron@Ideapad:~$ rfkill unblock list
Bogus unblock argument 'list'.
ron@Ideapad:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
ron@Ideapad:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

ron@Ideapad:~$ sudo iwlist scan
[sudo] password for ron: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

### Post by llamas612 on 2012-03-08
I had this same issue. I found the solution here:

[http://ubuntuforums.org/showthread.php?t=1770202]("http://ubuntuforums.org/showthread.php?t=1770914")

By the way, i also have an intel wireless card, like you do. It must be a Thinkpad E420 issue

---

### Post by Blueartisan on 2012-03-09
It didn't work. Any other suggestons?

---

