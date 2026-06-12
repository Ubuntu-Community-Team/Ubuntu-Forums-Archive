---
title: "Toshiba Satellite C660-119 No WIFI"
date: 2011-01-11
forum: Hardware
---

### Post by jawsykilla on 2011-01-11
Hi there got a new Toshiba Satellite C660-119, very good laptop I might point out. It came with Win 7 and that's all good and dandy but I love Ubuntu. I have set-up and maintained a Ubuntu server for quite some time and also have it dual boot with win 7 on my Desktop machine so that's what I did with the laptop. 

All is working well but most of the Fn functions do not work including the WiFi on or off toggle. This is a massive issue because this laptop has no hardware WiFi switch and I can't figure for the life of me how to switch it on through the software. I used Ndiswrapper to install the winXP drivers for the WiFi which is a Realtek 8187B. 

I had a look under /etc/acpi/events and found tosh-wireless which I took a look at but couldn't figure out which key combination it wanted me to press. acpi_listen didn't work and xev didn't give me the keycodes I needed. The Fn keys that work are the one to disable the trackpad, the hibernate, lock screen, brightness adjust DOES NOT work. 

Ndiswrapper-GTK reported the Hardware to be present but my understanding is it is not turned on.
I am currently installing 10.10 to see if that will solve anything.

Any ideas?
OS: Ubuntu 10.04

---

### Post by smuthavarapu on 2011-01-22
Did you manage to make ti Work. I have got the same loptop with my friend, I am trying to get the Wireless working. Any help on this one will be much appreciated

---

### Post by slamelov on 2011-01-30
Same problem here, any help?

---

### Post by smuthavarapu on 2011-02-03
Yes I have managed to make to Work. I have downloaded the Drives from [here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE")

I have installed rtl8192ce linux drivers

after installation activate the module with the following command

modprobe rtl8192ce

that did the trick. Toshiba C660 Ubuntu 10.10 64 bit

---

### Post by smuthavarapu on 2011-03-09
Here is the latest update on this one.

The members of the team of ubuntu Catalan warned me that there was the Realtek driver from repositories.

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

From time works well.

Credit goes to the user who provided this info to me.

---

### Post by markgw on 2011-04-04
This worked perfectly for me on my Toshiba Satellite C660-153.

After installing the drivers as above, I ran
```

sudo modprobe r8192ce_pci
sudo ifconfig wlan0 up

```
and it worked right away.

Thanks for the solution!

---

### Post by IWantFroyo on 2011-04-04
```
ifconfig wlan0 up
iwconfig wlan0 essid "your network name* key *WEP KEY*
dhcpcd wlan0
```You could also try this. If your network doesn't need a key, just use this:
```
ifconfig wlan0 up
iwconfig wlan0 essid *your network name*
dhcpcd wlan0
```For wpa/2 keys: ```
ifconfig wlan0 up
iwconfig wlan0 essid *your network name* key s:*WPA/WPA2 KEY*
```Leave any *s out.

---

### Post by Low2ik on 2011-11-12
Hello. Can you help me please? I've downloaded the file and i don't know how to do to install it.  Could anyone tell me what to do to install it? Thanks

---

