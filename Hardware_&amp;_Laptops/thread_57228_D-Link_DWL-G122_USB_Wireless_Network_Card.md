---
title: "D-Link DWL-G122 USB Wireless Network Card"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-08-15
Hello,

  I just bought a USB Wireless Card (D-Link DWL-G122 Revision B1) and am trying to get it installed on hoary. I read on this thread that there are open-source drivers for it somewhere:

[http://www.ubuntuforums.org/showthread.php?t=53035&highlight=dwl-g122](http://www.ubuntuforums.org/showthread.php?t=53035&highlight=dwl-g122)

Where do I get these drivers and can anyone outline the steps I need to get this up and running?

Thanks  :)

---

### Post by audax321 on 2005-08-15
Okay, I got the driver installed. It is available here: [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

But, it doesn't work. When I try to modprobe rt2570, it says:

FATAL: Module rt2570 not found.

Any help on this would be great. Thanks.

---

### Post by audax321 on 2005-08-15
Okay, I think I found the problem and the module is loaded!

I am using the 2.6.10-smp kernel and this is where the problem was. The driver is being installed in /lib/modules/2.6.10/extra and modprobe rt2570 does not check there.

So, I just moved: 

/lib/modules/2.6.10/extra/rt2570.ko

to

/lib/modules/2.6.10-686-smp/extra/rt2570.ko

Then I opened up a terminal and typed:

sudo /sbin/depmod -a
sudo modprobe rt2570

and everything worked. Hopefully this will help out someone else.

---

### Post by audax321 on 2005-08-16
Another thing, if anyone has problems with their sound card or anything not working properly after installing the drivers, try removing /etc/modprobe.conf

It just contains one line in it:

alias rausb0 rt2570

which was causing my SB Live 5.1 to not work. Removing the file fixed everything. So taking everything into account, the only file you really need to get this driver to work is the rt2570.ko file in /lib/modules/<kernel>/extra

---

### Post by audax321 on 2005-08-18
Okay removing /etc/modprobe.conf made the wireless connection a bit flaky. Instead rename /etc/modprobe.conf:

sudo mv /etc/modprobe.conf /etc/rt2570.modprobe

then put it in /etc/modprobe.d

sudo mv /etc/rt2570.modprobe /etc/modprobe.d

This fixes the sound problem and makes the connection stable again. At least so far its been stable....

Hope this helps someone else....

---

### Post by macgyver2 on 2005-08-19
Hey, nice thread you've got going here!  Which drivers are you using, the daily cvs or the beta release?  My comp locks up with the module from cvs.  I'm not complaining, of course...I fully realize the risks involved with using the cvs module.  I'm just curious if you've gotten the cvs stuff to work or if you used the release.  Oh, and do you happen to use WPA?

---

### Post by audax321 on 2005-08-28
[QUOTE=macgyver2]Hey, nice thread you've got going here!  Which drivers are you using, the daily cvs or the beta release?  My comp locks up with the module from cvs.  I'm not complaining, of course...I fully realize the risks involved with using the cvs module.  I'm just curious if you've gotten the cvs stuff to work or if you used the release.  Oh, and do you happen to use WPA?[/QUOTE]

I use the CVS. The thing I noticed is that if you bring the interface up and down to many times it locks the computer. So I just bring it up at boot and leave it alone. Also, there is apparanly a problem with the beta and CVS drivers with USB 2.0. To fix this you have to edit /etc/hotplug/blacklist and add ehci_hcd which will cause all your USB ports to run at 1.1. Doing this will allow the card to function very well. And I just use WEP... too lazy to try to setup WPA :)

---

### Post by daftmunkie on 2005-09-03
hi guys - i'm a complete ubuntu n00b and was hoping to get a little help here. I'm trying to set up my DWL-G122 "card" by following audax's fine advice. I thought I got it working... my Network settings panel claims "the interface rausb0 is active" in the Wireless connection section, but I can't load any webpages. is there a way I can troubleshoot where my problem is? I have a hunch that it's because the network i'm trying to connect to is using a shared WEP key, but there is no place for that option in the interface properties dialogue for rausb0...

any help would be great - thanks!

---

### Post by daftmunkie on 2005-09-04
so I got my wireless working somehow with the rt2750 driver (though it seems pretty finicky) and I thought I would share my findings here. pouring over the man pages for ifconfig, **iwconfig** (especially), and iwlist helped me loads.

**iwconfig** is a nice little command that allows you configure your wireless network interface... and you seem to need it if you want to connect to a shared WEP encrypted network since the network settings panel dosen't allow you to specify the encryption type. anyway, insterting the following commands got it to work for me (i have no idea which ones are extraneous):

```

root@rauros:~# iwconfig rausb0 channel 11
root@rauros:~# iwconfig rausb0 mode managed
root@rauros:~# iwconfig rausb0 essid scientiamLANd
root@rauros:~# iwconfig rausb0 key restricted [3] XXXXXXXXXXXXXXXXXXXXXXXXXX
root@rauros:~# iwconfig rausb0 key [3]
root@rauros:~# iwconfig rausb0 key on
root@rauros:~# iwconfig rausb0 rate auto

```
where the sting of X's is my 128bit hex key, [3] is the index (like a profile of sorts, i think), and channel 11 is just the channel that my router is broadcasting on (you can find this out by just using "iwlist" assuming your hardware is working properly)

through lots of searches it looks like most people turn off their interface by using the "ifconfig [interface] down" command before modifying their iwconfig settings and then bringing it back up ("ifconfig [interface] down") when they were done. I found that I *didn't* need to do this. Which is good because when I tried bring ing it up and down my computer crashed :(. according to [this thread](http://ubuntuforums.org/showthread.php?t=53035&highlight=DWL-G122), this is a known bug with this driver.

also, it seemed to matter that my eth0 (ethernet) interface needs to be deactivated... which is easy enough to do via the networking panel.

the finicky part is that It dosen't work when I start up my computer, i have to play with the iwconfig stuff mentioned above. here is a readout from my "iwconfig rausb0" that I think might indicate the problem:

```

anduin@rauros:~$ iwconfig rausb0
rausb0    RT2500USB WLAN  ESSID:"scientiamLANd"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:CA:FE:88
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-53 dBm  Noise level:-207 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
the link quality=0/70 i think is probably not good... if anybody has any ideas, please let me know!

one last thing (sorry this is so long!), but the rt2x00 open source driver project just today began beta testing a new combined driver for all Ralink chipsets. check it out here: [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page). hopefully this fixes the crash bug i mentioned earlier. I haven't gotten it to work, because I'm getting an error when I try to "make" (compile?) the driver - but thats probably more an indication of my ineptness than something wrong with the new driver ;)

I hope this helps somebody - and if you have any ideas on how to get my wireless adapter to just work on startup please let me know.  thanks!

---

### Post by lonetree on 2005-10-18
[QUOTE=daftmunkie]so I got my wireless working somehow with the rt2750 driver (though it seems pretty finicky) and I thought I would share my findings here. pouring over the man pages for ifconfig, **iwconfig** (especially), and iwlist helped me loads.

**iwconfig** is a nice little command that allows you configure your wireless network interface... and you seem to need it if you want to connect to a shared WEP encrypted network since the network settings panel dosen't allow you to specify the encryption type. anyway, insterting the following commands got it to work for me (i have no idea which ones are extraneous):

```

root@rauros:~# iwconfig rausb0 channel 11
root@rauros:~# iwconfig rausb0 mode managed
root@rauros:~# iwconfig rausb0 essid scientiamLANd
root@rauros:~# iwconfig rausb0 key restricted [3] XXXXXXXXXXXXXXXXXXXXXXXXXX
root@rauros:~# iwconfig rausb0 key [3]
root@rauros:~# iwconfig rausb0 key on
root@rauros:~# iwconfig rausb0 rate auto

```
where the sting of X's is my 128bit hex key, [3] is the index (like a profile of sorts, i think), and channel 11 is just the channel that my router is broadcasting on (you can find this out by just using "iwlist" assuming your hardware is working properly)

through lots of searches it looks like most people turn off their interface by using the "ifconfig [interface] down" command before modifying their iwconfig settings and then bringing it back up ("ifconfig [interface] down") when they were done. I found that I *didn't* need to do this. Which is good because when I tried bring ing it up and down my computer crashed :(. according to [this thread](http://ubuntuforums.org/showthread.php?t=53035&highlight=DWL-G122), this is a known bug with this driver.

also, it seemed to matter that my eth0 (ethernet) interface needs to be deactivated... which is easy enough to do via the networking panel.

the finicky part is that It dosen't work when I start up my computer, i have to play with the iwconfig stuff mentioned above. here is a readout from my "iwconfig rausb0" that I think might indicate the problem:

```

anduin@rauros:~$ iwconfig rausb0
rausb0    RT2500USB WLAN  ESSID:"scientiamLANd"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:CA:FE:88
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-53 dBm  Noise level:-207 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
the link quality=0/70 i think is probably not good... if anybody has any ideas, please let me know!

one last thing (sorry this is so long!), but the rt2x00 open source driver project just today began beta testing a new combined driver for all Ralink chipsets. check it out here: [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page). hopefully this fixes the crash bug i mentioned earlier. I haven't gotten it to work, because I'm getting an error when I try to "make" (compile?) the driver - but thats probably more an indication of my ineptness than something wrong with the new driver ;)

I hope this helps somebody - and if you have any ideas on how to get my wireless adapter to just work on startup please let me know.  thanks![/QUOTE]


I have the exact kind of problem when I was using Hoary, now I'm with Breezy, I still face the same kind of problem. I am using shared mode for my WEP, and still it doesn't authenticate, forcing me to change my setting to Open.

Sigh! When then can linux be more intuitive in this?

---

