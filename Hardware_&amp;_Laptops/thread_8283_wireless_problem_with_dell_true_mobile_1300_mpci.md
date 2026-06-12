---
title: "wireless problem with dell true mobile 1300 mpci"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by Krash1201 on 2004-12-16
i know this question has been asked at least 1000 times, but as i search the forum,  i can't find the answer.  my internet connection only comes through my wireless card.  i just installed ubuntu on my spare laptop harddrive, and because its an inspiron 8600, ubuntu didn't recognize my wireless card on start up.  i have ndiswrapper downloaded as source from the web, and burnt onto a cd via cdburnerpro xp 3.  the disk also has the necessary windows driver.  the problem is when i copy the file to the harddrive, it says that its locked.  from there i don't know what to do to get from the source to install ndiswrapper so i can make my internet work.  any help would be greatly appreciated.  thanks in advance.

Andrew

---

### Post by mefistofel on 2005-04-19
hey.. i have exactly the same card.. and mine works perfectly on ubuntu... you only have to dowload the sorce code of ndiswrapper.. and to compiled you need de linux-headres of the kernel.. also you need de *.inf and *.sys xp driver... 

next you do this

ndiswrapper -i ****.inf

ndiswrapper -l 

Check for Hardware Present

sudo modprobe ndiswrapper

ifconfig wlan0 up

dhclient wlan0 

and that's it


if you have some problems conectingo to the internet...

down the eth0 interface

---

