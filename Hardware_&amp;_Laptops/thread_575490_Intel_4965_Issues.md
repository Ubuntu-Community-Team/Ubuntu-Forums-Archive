---
title: "Intel 4965 Issues"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by ootz0rz on 2007-10-14
Hello all,

I have just installed Ubuntu 7.10 (Gutsy) on my laptop (Asus G1S-A1, or just G1S, doesn't matter) and have got most everything working that I've tested so far except for one major thing keeping me back from using it as my main operating system - my wireless network card.

Now, the weird thing about it is this:
When I originally booted Ubuntu as a LiveCD to install, the wireless worked flawlessly out of the box. I went ahead and then installed Ubuntu, and booted into it. It was still working fine. So I decided to begin installing some programs and such that I like/needed. One of which was the nvidia drivers (so I could get compiz fusion and all that good stuff going.) And of course, the nvidia drivers require a restart. So, I restarted my laptop, but the wireless was no longer working. I tried to enable and disable networking, but that didn't help. I know that the wireless is on, and tried cycling through the different wireless modes with the built in wireless button on the laptop, but that didn't help either.

Looking at lsmod, I could see that the modules WERE running and active. iwconfig also seemed to confirm this. Running ifconfig, it would also see wlan0 there. I tried ifdown and ifup on the interface but that didn't seem to do anything either.

So, I decided to then try to install the windows drivers using ndiswrapper. So, I went ahead and got ndiswrapper properly installed. Then, downloaded the windows xp drivers from the official intel website. Installed that, set it up with modprobe, and started up the module. Once again, no errors, and lsmod showed ndiswrapper running. But still no wireless functionality.

I'm really not sure what else to do. Any help would be VERY much appreciated, thanks!

---

### Post by Krischi on 2007-10-15
If you still have Vista installed, try booting into it and cycling through the wireless modes from there. In the past a bug has bitten me where wireless would not be working properly, unless I did that.

Otherwise, what is the output of dmesg after trying to enable wireless?

For what it is worth, iwl4965 works fine for me on gutsy 64 bit on this laptop.

---

### Post by ootz0rz on 2007-10-15
> **Krischi said:**
> If you still have Vista installed, try booting into it and cycling through the wireless modes from there. In the past a bug has bitten me where wireless would not be working properly, unless I did that.

Otherwise, what is the output of dmesg after trying to enable wireless?

For what it is worth, iwl4965 works fine for me on gutsy 64 bit on this laptop.
I do still have Vista installed, however I can cycle through wireless modes in both Vista and Ubuntu and it is clear that it works. For one, the wireless indicator will flash if I activate it. Also, two of the modes through the wireless cycle also activate bluetooth and that works in Ubuntu.

Now, interestingly, I've been able to get it semi-working. What I mean by this is:
I've disabled the roaming mode for the wireless adapter, and have it set to manually connect to whatever SSID that I like. However, I can't seem to get it to scan for SSID's no matter what I do. And that Network Manager still doesn't show any wireless connections.

If I could atleast get a listing of available SSIDs that'd be sufficient for me. Then all I'd have to work on next is getting sleep and hibernation working properly lol.

I'll check the dmesg output and post it here later today once I get a chance. I'm not on the laptop right now.

---

### Post by Krischi on 2007-10-15
I mean specifically cycling in Vista. Cycling in Linux was a hit-or-miss proposition in the past. The indicators responded properly, but occasionally things still did not work for me until I booted into Vista and did a full cycle there.

It is at least worth a try,  although lately things seem to have improved under Gutsy.

---

### Post by carbon_unit on 2007-10-15
I am having a similar problem. After installing 7.10 my inte l4965 worked. When I changed it from DHCP to static it stopped working and changing it back to DHCP did not help. I slid in an old Orinoco gold card and it works fine but of course no WPA. lsmod and dmesg both show the 4965 card as being loaded but it will not scan for AP's.
I will try booting into Vista and cycling the wireless tonight after work.

---

### Post by ootz0rz on 2007-10-15
Yea hmmm I've seemed to come up with a pseudo solution...
First, here's the output of [FONT="Courier New"]dmesg | grep wlan[/FONT] that I was getting before:
```
[   22.632000] wlan0: Initial auth_alg=0
[   22.632000] wlan0: authenticate with AP 00:01:f4:ec:20:a5
[   22.636000] wlan0: RX authentication from 00:01:f4:ec:20:a5 (alg=0 transaction=2 status=0)
[   22.636000] wlan0: authenticated
[   22.636000] wlan0: associate with AP 00:01:f4:ec:20:a5
[   22.644000] wlan0: RX AssocResp from 00:01:f4:ec:20:a5 (capab=0x11 status=0 aid=63)
[   22.644000] wlan0: associated
[   35.384000] wlan0: no IPv6 routers present
[  309.888000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  431.084000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  485.516000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  639.296000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  722.224000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  765.864000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  831.980000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  992.140000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1048.048000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

So, it seems that it would connect to something at first, but then when I tried to change it to connect to one of my school's wireless networks it would give that error at the bottom there.

Now, what I did was this:
Firstly, I reloaded all modules associated with the wireless card
sudo modprobe -r ndiswrapper
sudo modprobe -r iwl4965

Then, reloaded them (which I was hoping would essentially reset the network card):
sudo modprobe ndiswrapper
sudo modprobe iwl4965

Now, I was still unable to scan for wireless networks in the area using the Network Manager (from the panel). However, what I did was set up manual profiles (i.e. disabled roaming for the wireless card) for each network that I wanted to be able to connect to by specifying the SSID, WPA/WEP password, etc.. for each network. And, then I can apply whichever settings I like and it seems to work flawlessly in that regard.

However, two problems:
1) Sometimes the network card seems to stop working (i.e. after a computer restart) and I have to go through my sort of 'reset' procedure from above, then connect to whatever profile I like.
2) I still can't seem to get it to scan for wireless networks in the area. In fact, I had to use a friends laptop on windows to scan for the wireless networks I wanted to connected to and then put in the SSID and such manually myself for my profiles heh.

Now, neither of these problems is a major concern, but it would be nice to have them fixed if possible.

Also, before doing any of this, I did try to cycle through on Vista, but that didn't seem to do anything until I did the 'reset procedure'.

Thanks again for the help so far :)

---

### Post by clauskalus on 2007-10-17
I've experienced the exact same problem. I hope that the ubuntu dev team will fix this, because i think it's a bit spiffy getting wireless manually.
Just here to say, that this is probably a common problem.

---

### Post by girishz13 on 2007-10-17
hi i have a dual boot windows xp and ubuntu 7.04
the installation was smooth but ubuntu hangs once in a while whlie working
can anyone tell me why? :(
 my system config
intel d101ggc board
80gb segate sata hdd
512 ddr ram
3.06ghz p4 processor

---

