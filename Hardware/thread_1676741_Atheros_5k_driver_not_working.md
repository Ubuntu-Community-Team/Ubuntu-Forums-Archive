---
title: "Atheros 5k driver not working"
date: 2011-01-27
forum: Hardware
---

### Post by chandru1 on 2011-01-27
I have an Acer Aspire 3680 laptop and my ath5k driver is not working.


2) dmesg | grep ath5k

i get the following output:


[    1.272326] device-mapper: multipath: version 1.1.1 loaded
[    1.272332] device-mapper: multipath round-robin: version 1.0.0 loaded
[   19.825954] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.826011] ath5k 0000:0a:03.0: registered as \'phy0\'
[   21.607590] ath: EEPROM regdomain: 0x63
[   21.607594] ath: EEPROM indicates we should expect a direct regpair map
[   21.607599] ath: Country alpha2 being used: 00
[   21.607601] ath: Regpair used: 0x63
[   21.619119] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)


sudo iwlist scan 

no scan results. Please help. I have tried in lot of forums, but i havent got a reply by which my wireless could get going. See this as well 

- [http://askubuntu.com/questions/18723/atheros-wireless-not-working](http://askubuntu.com/questions/18723/atheros-wireless-not-working)

---

### Post by pytheas22 on 2011-01-28
It doesn't look from dmesg like anything is wrong.  The driver exists and appears able to bring the device up without a problem.

Are there normally many wireless networks within range of this computer, or just the one you connect to?  If there are many networks but none of them is showing up with the "sudo iwlist scan" command, that probably means there's something wrong with the driver.  In that case, it may help to install a newer version of the driver by typing:

```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

If your network is the only one that would be visible, then the failure to detect it likely has to do with the settings on your router.  Changing to a different channel and/or mode (i.e., changing from channel 13 to channel 6, or from 11n to 11g mode) would probably solve the problem.

Let me know how far the information above takes you and we can go from there.  If the linux-backports-modules-wireless-maverick-generic doesn't help you, you may need to compile the ath5k driver from source.

---

### Post by chandru1 on 2011-02-01
No it's still not working not sure what the problem is.

Changing to a different channel and/or mode (i.e., changing from channel 13 to channel 6, or from 11n to 11g mode)? How do you do that?

---

### Post by pytheas22 on 2011-02-01
> Changing to a different channel and/or mode (i.e., changing from channel 13 to channel 6, or from 11n to 11g mode)? How do you do that?

You need to access your router's configuration page.  Usually you can do this by opening a Web browser on a computer connected to the router and putting 192.168.0.1 in the address bar.  If that doesn't work, try 192.168.1.1 or 10.0.0.1.  If none of these work, refer to [this page]("http://www.daniweb.com/forums/thread39326.html") for more on how to get to the router configuration.

Once inside the router configuration page, look for the settings related to channel and mode and you should be able to change them easily.  Let me know if you have trouble.

---

### Post by chandru1 on 2011-02-04
No it doesn't work. Anyhow my driver is Atheros AR2413. For this is there a specific linux wireless driver which i can download and install.

---

### Post by pytheas22 on 2011-02-04
> No it doesn't work. Anyhow my driver is Atheros AR2413. For this is there a specific linux wireless driver which i can download and install.

The Linux driver for that wireless card is called ath5k and it comes built into Ubuntu.  I am not sure why it's not working in your case and none of the output you posted provides a clue, unfortunately.

If you want, you can try recompiling the driver using the latest source code.  If there have been any updates in the last few months that fix your problem (whatever the problem is), you'll get these by compiling the latest version of the driver.  Ubuntu's version of the driver is a few months old.

The ath5k source code is part of the compat-wireless package.  To compile it, you'll first need to download the source code from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)  (Download the file compat-wireless-2.6.tar.bz2.  You may need to click the link twice before it will let you download it.)  Save the file to your desktop, then run these commands to compile and install the new driver (you need to be connected to the Internet for these commands to work, as they need to download some extra tools in order to compile the driver):
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless*
cd compat-wireless*
make
sudo make install
```

Then reboot, and the newer version of the driver will be activated.  Hopefully this will work better for you.  If not, the only other option I can think of would be to try using ndiswrapper, which would drive the card using the Windows driver.  But the native Linux driver is preferable if you can make it work, since it provides many more features.

---

### Post by chandru1 on 2011-02-04
No it doesn't work. I get this output if i do the dmesg.


root@chandru1:~# dmesg | grep ath5k
[   18.849855] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.849908] ath5k 0000:0a:03.0: registered as 'phy0'
[   20.269092] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
root@chandru1:~#

---

### Post by pytheas22 on 2011-02-05
The dmesg output doesn't show any kind of problem, so I'm not sure why it won't connect.  The only other idea I have for you is to try ndiswrapper.  You can find instructions for using it [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

You will probably need to blacklist the ath5k driver for ndiswrapper to work; do that by editing the file /etc/modprobe.d/blacklist.conf and adding the line "blacklist ath5k"  If ath5k is blacklisted the command "dmesg | grep ath5k" should not return anything (you need to reboot for the blacklisting to take effect).

---

### Post by chandru1 on 2011-02-19
HI--

  Chris, i knew my wireles would work if i used UBuntu 9.10 and its working. I am posting this by running live CD from Ubuntu 9.10 and i am connected to a wireless network. Dont know what the problem in 10.10. Could you please help me out.

---

### Post by pytheas22 on 2011-02-19
hmmm, that's strange that it would work in Ubuntu 9.10 but not in 10.10, especially after none of the things we tried earlier was able to get the device working.

Have you tried following [these instructions]("http://askubuntu.com/questions/18723/atheros-wireless-not-working/25235#25235") given in the thread you created earlier on a different site?  madwifi is an idea I had not thought of, but it should support your hardware.  madwifi will provide a different driver (named ath_pci) that may work better than the ath5k driver, which currently seems not to work at all for you in Ubuntu 10.10, for reasons that remain unclear.

The only other idea I have is to use ndiswrapper, which would also essentially provide a different for your device, because ndiswrapper would use the Windows driver to make the card work.  I would try the madwifi approach first, however, as ndiswrapper is not likely to provide great performance.

---

