---
title: "ethernet does not work"
date: 2011-08-25
forum: Hardware
---

### Post by marohde on 2011-08-25
Hi,

i installed ubuntu 10.4 (regular desktop version) on my new Acer Aspire One Happy (N450 version) netbook as dual boot alongside pre-installed windows 7. All works perfectly - WLAN, touchpad, camera, microphone... - just when connecting to LAN, nothing happens. (the wired tab in the network connections preferences is emtpy). Ethernet works fine when booting in windows.

As I am new to ubuntu i don't even know where to start to look for problems
- where can i see if the ethernet card is recognised at all?
- i suspect it may be a driver issue. i downloaded the driver from the acer webpage (atheros LAN driver 1.0.0.31) - but i am not sure how to install it (all windows binaries). how can i find out if the driver is missing and if it is, how can i install it manually?
- any other ideas?

thanks!

---

### Post by grahammechanical on 2011-08-25
Hi

Try right and left clicking on the network icon. What information do you get? If there is any reference to eth0 and eth1 or auto eth0 and auto eth1, then the network adapter is recognized and there are drivers for it.

The ethernet (wired) connection still needs to be activated for it to connect. Plug in the cable, click on the network icon. (I forget if it is left or right click - I am using 11.04). Do you see a line that says Enable Networking? Is there a tick mark against it? Click on that line to remove the tick mark and then click on it again to put the tick mark back again. This is like switching networking off and on. Do you now get a connection? If so, go to Edit connections and select the wired connection and mark it to Connect Automatically.

Regards.

---

### Post by dccubed on 2011-09-02
> **grahammechanical said:**
> Hi

The ethernet (wired) connection still needs to be activated for it to connect. Plug in the cable, click on the network icon. (I forget if it is left or right click - I am using 11.04). Do you see a line that says Enable Networking? Is there a tick mark against it? Click on that line to remove the tick mark and then click on it again to put the tick mark back again. This is like switching networking off and on. Do you now get a connection? If so, go to Edit connections and select the wired connection and mark it to Connect Automatically.

Regards.

Hi GM I too am having the same problem, I did what you suggested and it is still not recognizing the ethernet.

Here is what I find odd, when I boot from the thumb drive that has the OS on it, I am able to connect no problem, when I boot from the HD, it says I am not able to connect.  I have rebooted all my network gear (modem, router) checked the connections (fine) and did what you suggested above.  I'm not sure what to do now.

Any help would be greatly appreciated.

Thanks

DC

---

### Post by .... on 2011-09-02
Output of lshw or lspci would be helpful to see what LAN chipset you folks have:
```
lspci -vv
sudo lshw -C network
```

---

### Post by dccubed on 2011-09-02
> **.... said:**
> Output of lshw or lspci would be helpful to see what LAN chipset you folks have:
```
lspci -vv
sudo lshw -C network
```


Where to I get, or how do I get to the command prompt in Ubuntu.  (i'm a serious super duper noob)

---

### Post by dccubed on 2011-09-05
*bump*

---

### Post by ables on 2011-09-16
in terminal^^^^^^^^ is where you would put the command prompt

---

### Post by maul9999 on 2011-09-16
check for internet connection.  It can be wireless turn on.  You need change it from wireless to wired.  First of all, how old is your laptop?

---

### Post by BicyclerBoy on 2011-09-17
Post #3 suggests that USB boot image works.

If this USB image is an install/LiveCD then this happens because the Live CD/USB image contains the non-free firmware & non-free drivers for wifi & other devices.
The real HDD install does not include any non-free components, you have to add them back.

---

