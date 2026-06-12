---
title: "Atheros AR9285 Ubuntu 11.10 problem"
date: 2011-10-14
forum: Hardware
---

### Post by furina on 2011-10-14
Hi,

My laptop Toshiba Satellite R830-10f yesterday i download ubuntu 11.10. today i can not install Atheros AR9285 wireless ethernet driver. i try compat-wireless-3.1-rc8-1 but it is not working. also i try install linux-backports-module-oneiric but there is no package like this. What can i do?

thank you

---

### Post by fernandoch on 2011-10-14
I am having the same problem with a vaio and Atheros AR9285 Ubuntu 11.10.

What is the solution?

---

### Post by CBMCO on 2011-10-14
I installed 11.10 last night and I have an Atheros AR9285 in an Acer Aspire One 722 (AO722). After the upgrade my wireless performance slowed down significantly to the point I could not even connect to my router. I created the following file /etc/modprobe.d/ath9k.conf and added the following line:

```
options ath9k nohwcrypt=1
```

restarted and now my wireless is back to normal. Hope this helps people is the same situation.

---

### Post by jneyra on 2011-10-14
Anyone have solved for AR9271?

---

### Post by fernandoch on 2011-10-15
I created the file and added that line and still not working for me...

---

### Post by prosist on 2011-10-15
> **CBMCO said:**
> I installed 11.10 last night and I have an Atheros AR9285 in an Acer Aspire One 722 (AO722). After the upgrade my wireless performance slowed down significantly to the point I could not even connect to my router. I created the following file /etc/modprobe.d/ath9k.conf and added the following line:

```
options ath9k nohwcrypt=1
```

restarted and now my wireless is back to normal. Hope this helps people is the same situation.

did not work for me =(

---

### Post by zibiksior on 2011-10-15
I also have a problem with wifi in my Toshiba R830-14N. And I'm also using Ubuntu 11.10 64 bit maybe on 32 bit version wifi card would work ok? Did any one try it? Is there any diference at all betwin drivers in this two versions? Some people report that on their R830's every thing is working fine just after installing Ubuntu so why on some other it's not...? I road many topics about Atheros AR9285 and Ubuntu problems but I did't find any solution for that. Maybe on this forum someone will figure this out and help us, poor owners of this unlucky hardware:P

---

### Post by prosist on 2011-10-15
> **zibiksior said:**
> I also have a problem with wifi in my Toshiba R830-14N. And I'm also using Ubuntu 11.10 64 bit maybe on 32 bit version wifi card would work ok? Did any one try it? Is there any diference at all betwin drivers in this two versions? Some people report that on their R830's every thing is working fine just after installing Ubuntu so why on some other it's not...? I road many topics about Atheros AR9285 and Ubuntu problems but I did't find any solution for that. Maybe on this forum someone will figure this out and help us, poor owners of this unlucky hardware:P

i tried with the 11.10 32 bits, without installing, and the problem persists.

---

### Post by furina on 2011-10-17
try "rfkill list" command if there is "hard blocked: yes" your wifi is closed. solution is switch to windows and turning on from there and reinstall ubuntu.

---

### Post by fernandoch on 2011-10-17
Here is the output

```
fernando@fernando:~$ rfkill list
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
```

What can I do?

---

### Post by roger_1960 on 2011-10-17
Hi

> rfkill unblock all

---

### Post by roger_1960 on 2011-10-17
Hi

try

> rfkill unblock all

in terminal

Roger

---

### Post by fernandoch on 2011-10-17
Nothing changed, still unable to activate the wireless

```
fernando@fernando:~$ rfkill unblock all
fernando@fernando:~$ rfkill list
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
```

---

### Post by PsyGeek on 2011-10-17
I have the same wireless card on Xubuntu 11.10 64 bit and it works perfectly :s. Normally it doesn't require fancy things like modprobe etc. The driver is ath9k if I remember correctly, which is included in the kernel.

(my wireless adapter, as shown by lspcia:)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

edit: Maybe it's disabled in the BIOS?

---

### Post by fernandoch on 2011-10-17
It works on windows, and as you can see, many of us are having the same problem on Ubuntu 11.10

---

### Post by Werwolf_NOR on 2011-10-18
I have experienced a similar problem on 11.10 64bit.

My solution was to go into
System settings/Network/Wireless

then flip on the Airplane mode followed by flipping the on/off switch.

this makes it possible to select wireless network. and it connects to the correct one before I can select it...

Don't know if this work for everyone but it did for me 

W

---

### Post by fernandoch on 2011-10-18
I fixed it. Edit the file

/etc/modprobe.d/blacklist.conf

and add this

blacklist acer-wmi

Then reboot and your wifi should work ;)

---

### Post by prosist on 2011-10-21
hi

i have an acer with atheros ar9285, installed a fresh 11.10 ubuntu, and was having problems with my wireless connection.
i tried many things but finally solved the problem uninstalling network-manager and installing wicd, after reading this post: [http://ubuntuforums.org/showthread.php?p=11376536&posted=1#post11376536](http://ubuntuforums.org/showthread.php?p=11376536&posted=1#post11376536)

hope it help you!

---

### Post by prosist on 2011-10-21
> **prosist said:**
> hi

i have an acer with atheros ar9285, installed a fresh 11.10 ubuntu, and was having problems with my wireless connection.
i tried many things but finally solved the problem uninstalling network-manager and installing wicd, after reading this post: [http://ubuntuforums.org/showthread.php?p=11376536&posted=1#post11376536](http://ubuntuforums.org/showthread.php?p=11376536&posted=1#post11376536)

hope it help you!

sorry, the problem came back after reboot =(

---

### Post by varunendra on 2011-10-22
This thread seems pretty jumbled up.:)

@*furina*,
Since you found solution to your original problem, I think you should mark your thread as [Solved] posting a reference to your post #9 in which you have mentioned your solution. This will help others having exactly same problem as yours.


@*prosist *and *zibiksior *(and others having similar problems),
I would suggest to start your own threads posting your questions with following details there:
```
lsb_release -a
uname -a
sudo lshw -C network
lsmod
ifconfig
iwconfig
cat /etc/network/interfaces
rfkill list all
```

You may of course post links to your threads here so we could follow.

---

### Post by dixoncx on 2011-10-24
> **CBMCO said:**
> I installed 11.10 last night and I have an Atheros AR9285 in an Acer Aspire One 722 (AO722). After the upgrade my wireless performance slowed down significantly to the point I could not even connect to my router. I created the following file /etc/modprobe.d/ath9k.conf and added the following line:

```
options ath9k nohwcrypt=1
```restarted and now my wireless is back to normal. Hope this helps people is the same situation.

Am also having same problem in Sony vaio VPCEH with ubuntu 11.10
Creating **ath9k.conf** doesn't fixed my problem..:(

---

### Post by dixoncx on 2011-10-24
> **varunendra said:**
> This thread seems pretty jumbled up.:)

@*furina*,
Since you found solution to your original problem, I think you should mark your thread as [Solved] posting a reference to your post #9 in which you have mentioned your solution. This will help others having exactly same problem as yours.


@*prosist *and *zibiksior *(and others having similar problems),
I would suggest to start your own threads posting your questions with following details there:
```
lsb_release -a
uname -a
sudo lshw -C network
lsmod
ifconfig
iwconfig
cat /etc/network/interfaces
rfkill list all
```You may of course post links to your threads here so we could follow.

My thread:
[http://ubuntuforums.org/showthread.php?t=1867214]("http://ubuntuforums.org/showthread.php?t=1867214")

---

### Post by ronewolf on 2012-07-06
I have an Acer Aspire1 0722 with an AR9485 network adapter and, with this fix, I now have a fast and stable network connection. More at:

[http://ubuntuforums.org/showthread.php?p=12079808#post12079808](http://ubuntuforums.org/showthread.php?p=12079808#post12079808)

---

### Post by ronewolf on 2012-07-06
> **CBMCO said:**
> I installed 11.10 last night and I have an Atheros AR9285 in an Acer Aspire One 722 (AO722). After the upgrade my wireless performance slowed down significantly to the point I could not even connect to my router. I created the following file /etc/modprobe.d/ath9k.conf and added the following line:

```
options ath9k nohwcrypt=1
```

restarted and now my wireless is back to normal. Hope this helps people is the same situation.

will just mention that this same fix has worked wonderfully for me on 12.04 with Acer Aspire 1 722. with an AR9485 adapter.

---

