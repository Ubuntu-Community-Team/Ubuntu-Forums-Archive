---
title: "Wireless Issues! supported hardware noot working"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by WickedAwsome on 2007-03-15
Toshiba A135 laptop with the intel 3945ABG wireless card in it.

This is supposed to work out of the box with Ubuntu, but its not for me. No wireless networks show up in the networking menu.

I ran some troubleshooting from the ubuntu wiki here are my results:

checked the compatibility listing and It was green, and showed the the proper driver (which is what it is using)

sudo pccardctl ident --"no product availible"

ran ishw and the card showed up, and linked to the proper driver and not listed as disabled


not sure what to try, it is listed in the device manager, and has the right driver, its just not showing up in the networking gui or in any of the networking stuff



Any clue how to get this straightened out?

if you need more information please just tell me what you need, I am a linux noob, so I am still trying to figure out this new world, so go easy on me with complex inquiries


Thanks

---

### Post by Teamgeist on 2007-03-15
Have you installed the "linux-restricted-modules" package?

---

### Post by WickedAwsome on 2007-03-15
Not that I know of, unless it came packaged.  I will check that as soon as I get access to an ethernet port

---

### Post by Azilla on 2007-03-16
Could you copy/paste the output of these commands in the reply.


```

# sudo lspci |grep Ethernet
# sudo iwconfig
```


-cheers

---

### Post by WickedAwsome on 2007-03-16
I am guessing that these results are not correct...lol

```

# sudo lspci | grep Ethernet
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8136 (rev 01)
# sudo iwconfig
sudo: iwconfig: command not found

```

I cant even find what package iwconfig is a part of to install it...what is it?

---

### Post by ssavelan on 2007-03-16
You might try:

sudo apt-get install knetworkmanager

Run that (will be in apps drop-down).  It may work with no further configuration.  I've never gotten wireless working by any other means.  But, I haven't really tried that much b/c knm has always been so automatic and easy.

---

### Post by Griffiss on 2007-03-16
the **sudo iwconfig** command should definitely bring up some information. Were you actually typing the '#' character?

Just typing **iwconfig** on its own should tell you whether your network device (for me, wlan0) is working. Here is my output:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"*YourNetworkName*"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:18:D7:4A   
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-56 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by WickedAwsome on 2007-03-16
nope...

I just put the #'s, here it is exact

```
gary@wickedUbuntuLapt:~$ iwconfig
bash: iwconfig: command not found
gary@wickedUbuntuLapt:~$ sudo iwconfig
Password:
sudo: iwconfig: command not found

```

im typing this from my wireless connection tho, the knetwork manager thing worked great

---

### Post by Griffiss on 2007-03-16
Ah, well, cool!:)

Are you using kubuntu? knetwork-manager is for kubuntu, and that *might* be why iwconfig doesn't work - there is some variation in the commands as I understand it, but then I've only had ubuntu a week....

---

### Post by ssavelan on 2007-03-16
> **Griffiss said:**
> Ah, well, cool!:)

Are you using kubuntu? knetwork-manager is for kubuntu, and that *might* be why iwconfig doesn't work - there is some variation in the commands as I understand it, but then I've only had ubuntu a week....

I run knetwork-manager in Ubuntu and Xubuntu and I can't stand Kubuntu.  I just like the net. man.

If you want to use iwconfig.. it looks like you will probably need to

sudo apt-get install iwconfig

---

### Post by ssavelan on 2007-03-16
> **WickedAwsome said:**
> 

im typing this from my wireless connection tho, the knetwork manager thing worked great

:guitar: 

Yeah, on the whole i don't like much about kde (relative to Gnome and xfce); I couldn't even use it for more than a day when I had it.  But that netman is on just about every comp that I've set-up.  It's allowed me to stay completely ignorant of how the wireless works in linux and still be able to stay on and set others up.

I have really NO complaints with it, no bugs.  You can make it fire-up on start-up and you usually will have a connection before the machine is fully booted.

It's sweet to be able to exist in a Gnome/xfce world and get all the cool ktools and stuff.

---

### Post by WickedAwsome on 2007-03-17
yep, this network manager works great, and im running in in Gnome, which I prefer to kde after trying both.  the apt-get install ipconfig returned that no package was listed under that name.  So, I guess I wont worry about it as It seems that kde's tool works good.  

Thanks everyone for your help, UF has been great in helping me make the transition to linux

---

