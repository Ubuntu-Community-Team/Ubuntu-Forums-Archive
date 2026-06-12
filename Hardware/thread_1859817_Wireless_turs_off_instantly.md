---
title: "Wireless turs off instantly"
date: 2011-10-14
forum: Hardware
---

### Post by cbob on 2011-10-14
Hi,

A problem occurred after I upgrade to 11.10. It seems as wireless is immediately disabled after enabling it..  
Like:
```
sudo iwconfig wlan0 up; sudo iwlist wlan0 scanning
```Does generate list of a successful scan but enabling wireless by the menu icon just indicates an successful start then immediately unchecks it again..

Any thought?

/cbob

---

### Post by cbob on 2011-10-15
Okej so i traced to problem to rfkill
```
sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```Could not disable softblock by:
```
sudo rfkill unblock wifi
```Removing the acer-wireless mod helped to enabling the wifi. 
```
sudo modprobe -r acer-wmi
```This only solved the problem till reboot an then  same thing again.. But by blacklisting the 'acer-wmi' application the problem seems to be fixed!
```
sudo gedit /etc/modprobe.d/blacklist.conf
```And add (at the end of the file):
```
blacklist acer-wmi
```KR cbob

---

