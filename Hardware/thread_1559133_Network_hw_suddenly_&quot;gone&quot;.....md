---
title: "Network hw suddenly &quot;gone&quot;...."
date: 2010-08-23
forum: Hardware
---

### Post by xutkm on 2010-08-23
Hi,
I'm fairly new on this Linux but I'm fed up with Windows. 

I have been running Ubuntu for a couple of months now on my Compaq Presario F700 without any problems what so ever. Suddenly, yesterday, I had no Internet connection and when I tried to search for the reason, I discovered that the system can't find any netwok hardware. Neither wired nor WiFi. In Win 7 all is working without any problems.

How should I fix this? In Win I would have reloaded the drivers or tried another driver and so on. In Linux I have no idea how to do this. I obviously can't download anything in Ubuntu so I would need to find whatever I need in Windows. I have the latest version of Ubuntu with all recommended patches installed. (I actually believe that it was the latest patch that killed the network... :( )

Please help me! I really want to be able to erase my Windows partition soon!

Thanks in advance,
Kim

---

### Post by Fafler on 2010-08-23
Open a terminal and type the following and cut'n'paste the results:

lspci
lsusb
ifconfig -a

Are the network manager still present in the panel?

---

### Post by xutkm on 2010-08-23
Hi and thank you for your VERY fast answer!

I have attached the results from the three commands in 'results.txt'.

About the Network Manager I must say 'I don't know' because I was stupid enough to install Swedish as default language so I have also included screen dumps with the two menus. I hope that you can figure it out from these dumps.

Thanks a million for caring!
/Kim

---

### Post by Jakiejake on 2010-08-23
> **xutkm said:**
> Hi and thank you for your VERY fast answer!

I have attached the results from the three commands in 'results.txt'.

About the Network Manager I must say 'I don't know' because I was stupid enough to install Swedish as default language so I have also included screen dumps with the two menus. I hope that you can figure it out from these dumps.

Thanks a million for caring!
/Kim

Reinstall Network Manager

---

### Post by xutkm on 2010-08-23
Update.

Hmmmm....
I just attached an USB network adapter, 3COM 3CRUSB10075, and Ubuntu recognised it and installed it in 5 seconds. I'm impressed! So, now I have a network connection again but only through the USB device. The internal device is still not working.

/Kim

---

### Post by xutkm on 2010-08-23
When trying to find eth1:

kim@kim-laptop:~$ ifconfig eth1
eth1: error fetching interface information: Enheten hittades inte
kim@kim-laptop:~$ 

('Enheten hittades inte' =  'Unit not found')

Is there any idea reinstalling Network Manager when I have a network connection via the USB unit?

/Kim

---

### Post by Fafler on 2010-08-23
sudo apt-get remove network-manager
sudo apt-get install network-manager-gnome

---

