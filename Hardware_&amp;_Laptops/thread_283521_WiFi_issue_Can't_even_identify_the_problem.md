---
title: "WiFi issue: Can't even identify the problem"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by KyleDW on 2006-10-24
VERY new to Ubuntu here; just got it installed on my HP Pavilion ze2000 laptop, Dapper Drake release. I'm having trouble connecting to my wireless network, even though I live in a wireless-happy building and I should be able to see 8 or 9 networks at any given time. I'm going to give you as much information as I've amassed in my troubleshooting and see what you guys can make of it.

I have a Broadcom BCM4318 (AirForce One 54g) wireless card. If I run the "lshw" command in a Terminal window, I can see my card listed; it has, under configuration, "driver=bcm43xx", which makes me think there's already a valid driver installed for the card. So I should be able to use the card, right?

I installed Wifi-Radar to help me see and connect to wireless networks, but when I open it nothing is displayed.

If I go into System -> Administration -> Networking, I see that my wireless interface is "not active." If I click on it and click "Activate," the window is busy for quite a long time, then it shows that the interface is "active"; however, if I click "OK" and then immediately open the same window again, it shows the interface as "not active". Might that be the problem?

Any advice you guys can give me would help; I like to exhaust all my troubleshooting abilities before making Internet posts about problems, but I've been going ](*,) over this for a week.

---

### Post by king20878 on 2006-10-24
What do ifconfig and iwconfig at the terminal output?  What kind of accesspoint are you trying to connect to?  Static IP or DHCP?

---

### Post by NetworkGuy on 2006-10-24
Broadcom cards seem to be the hardest to get working in my short experience.  

Try this how-to listed in the forums to try to get your card working..

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

---

### Post by Taigrr on 2006-10-24
I got it working in just a few minutes, once I knew why it didn't work!

Follow a tutorial very closely, and if it doesn't work, there's one last step. There's a file that calls your wireless "wlan0", when it's probably something more like eth1. Or something. Simple, small text file, and you just change wlan0, to eth1 (Or whichever your card is in). I'll see if I can find where I found the file trick.

---

### Post by jrz on 2006-10-24
Have you gat a path and file name for where you found that change needed to be made?

---

### Post by pastorjay on 2006-10-31
up for the reply that is needed... I am desparate to get mine working, soplease tell us where the file is that needs editing

---

### Post by Taigrr on 2006-11-03
Hey! Appologies, have been fighting Linux on my new inspiron.

Well, if you're still having trouble, this is the last save-my-*** step that I found, and it worked!

sudo gedit /etc/modprobe.d/ndiswrapper

Simply use that, and in the file there'll be three words. The middle one probably says "wlan0". Change it to "eth1", or wherever your wireless card is. Should work wonderfuly! Did for me, anyway =D A perfect fix.

---

### Post by odelay on 2006-11-04
What if we want it to stay wlan0 instead of eth1?  The middle word in /etc/modprobe.d/ndiswrapper for me is wlan0, but for some reason I'm having wireless show up as eth1 now.  I don't know if there's a real difference though, it just get's confusing switching back and forth.

---

### Post by Taigrr on 2006-11-04
You just change as needed. If your card is actualy in Wlan0, then you'll want that middle bit to be Wlan0.. If it's Eth1, make the file say Eth1, and so on, and so forth..

So if it says your card is in Eth1, that's what you'll want to put in that file.
If it says it's in Wlan0, you'll want the file to say that, instead.

---

### Post by FrankVdb on 2006-11-04
So I assume your Broadcom card is working now? The bcm43xx driver is the standard driver that comes with Dapper...

---

### Post by Taigrr on 2006-11-05
Yes, Frank. But it doesn't work for the BCM4318.

---

