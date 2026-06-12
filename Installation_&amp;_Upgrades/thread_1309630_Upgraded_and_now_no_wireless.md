---
title: "Upgraded and now no wireless"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by cybercrypt13 on 2009-11-01
I have just upgraded to the latest Karmic release of Ubuntu and have lost all wireless network.  I see nothing in the menus for dealing with network or hardware devices and the hardware program I see listed only shows me the nvideo device and no options to look for other things.

I went through the hardware diag program and it sees my wireless card but says I have no Internet connection.

The earlier release of Ubuntu setup the wireless all by itself with no glitches and it has worked perfectly for months.  Can anyone tell me how to get my wireless working again, or tell me what might have happened to cause it to stop?

Thanks,

glenn

---

### Post by Batzi on 2009-11-01
Same here. I can't connect to neither wired or wireless. No connection whatsoever.

---

### Post by cybercrypt13 on 2009-11-01
I just ran lshw -C network and it is reporting as Unclaimed which I understand means that it has no driver installed.  I'm wondering if the network driver it used in the older version might have been removed by the new install processes as being obsolete?

If so, can anyone suggest how I might go about finding something that is supported?

Thanks,

glenn

---

### Post by mbr78 on 2009-11-01
I am having the same problem on my HP Mini. Wireless worked fine in 9.04 and now it doesn't in 9.10. I've been trying to get wireless to work for a couple days.

---

### Post by nightrider.36 on 2009-11-01
:D I activated wifi by connecting my netbook to the router using a network cable--something I haven't done in years--Ubuntu detected the eth0 immediately. Activated the WiFi drivers, let them download and manually enabled connectivity using the netbook's slide-switch. I was not able to save this configuration back to my USB which is where my installation has to stay. I can't use 9.10 UNR if I have to do this every time.

I have an Acer Aspire One netbook (D150)that never had problems with previous Ubuntu distributions. In fact, one of the reasons that I purchased this netbook was because Ubuntu worked so well with it--better than with Windows, faster in my opinion.  My netbook experienced problems using 9.10(Karmic) which I thought was odd for such a common netbook. I have to use the live version from a USB because I don't want to partition my hard drive, especially if Karmic's buggy and I don't really have time to troubleshoot (watching my two-year-old destroy the living room as I type this). That may have something to do with the problems my netbook's having.  

:sad: It seems like we took a step back in some ways. I'll keep messing with this OS because in some ways, I do like it better than Windows and MacOS.

---

### Post by mbr78 on 2009-11-01
My wireless works when I run 9.10 from a USB stick but it won't work when I install to the hard drive.

---

### Post by autocrosser on 2009-11-01
If you are using a Atheros card there was a blacklisting done during Karmic-Development--look in /etc/modprobe.d to see if there is a "blacklist-ath_pci.conf" there. If so, edit the file as root & put a # in front of "blacklist ath5k" and reboot.

---

### Post by bob brazie on 2009-11-01
I am sorry for the noob question but how do I become root to have permission to change the file?

---

### Post by paul-p1988 on 2009-11-01
> **bob brazie said:**
> I am sorry for the noob question but how do I become root to have permission to change the file?

on the terminal you type 'sudo' (without the quotes) before whatever the rest of the command is

---

### Post by cybercrypt13 on 2009-11-01
> **autocrosser said:**
> If you are using a Atheros card there was a blacklisting done during Karmic-Development--look in /etc/modprobe.d to see if there is a "blacklist-ath_pci.conf" there. If so, edit the file as root & put a # in front of "blacklist ath5k" and reboot.

Good call.  The file was there and I edited it and commented out the line and its working perfectly again.  Just a question:  why was it blacklisted and should I be looking for a different wireless card?  This is a PCI card I added to my computer a while back but I can get something else if it would be better.  I would like to get kismet and stuff running eventually and maybe this card isn't the best to have.

Thanks for any opinion and thanks for the help as you took care of my problem.

glenn

---

### Post by autocrosser on 2009-11-01
> **cybercrypt13 said:**
> Good call.  The file was there and I edited it and commented out the line and its working perfectly again.  Just a question:  why was it blacklisted and should I be looking for a different wireless card?  This is a PCI card I added to my computer a while back but I can get something else if it would be better.  I would like to get kismet and stuff running eventually and maybe this card isn't the best to have.

Thanks for any opinion and thanks for the help as you took care of my problem.

glenn

No problem--there was a driver conflict during Karmic-Development & it was decided to blacklist the ath5k driver--problem is that on some systems that is the driver you need.....As for looking for another card--I wouldn't at this time--maybe wait a year or so & check on a Linux-friendly card....

---

### Post by davidg25 on 2009-11-01
Same here with Atheros AR5006X - worked with madwifi in 9.04 but I can't get it going in 9.10 (studio) yet.

---

### Post by davidg25 on 2009-11-01
> **autocrosser said:**
> No problem--there was a driver conflict during Karmic-Development & it was decided to blacklist the ath5k driver--problem is that on some systems that is the driver you need.....As for looking for another card--I wouldn't at this time--maybe wait a year or so & check on a Linux-friendly card....


I did that on my HP, but still can't get it to work.  Would it be blacklisted anywhere else or any other suggestions ?

Thanks,
dave

---

### Post by autocrosser on 2009-11-01
Not sure what card you are using--I'd look in the community wiki docs under wireless...That was the only "fix" I know about....

OK--I reread your prior post--not sure what driver that card needs...

---

### Post by davidg25 on 2009-11-01
It used the madwifi driver in 9.04.  I have that pkg, but it's been so long I forgot how to compile it.

I'm sure there's simple fix at the end of the day -everything else seems to be fine so this is my only hurdle at this point.

Thanks,
dave

---

### Post by mspn on 2009-11-02
> **davidg25 said:**
> It used the madwifi driver in 9.04.  I have that pkg, but it's been so long I forgot how to compile it.

I'm sure there's simple fix at the end of the day -everything else seems to be fine so this is my only hurdle at this point.

Thanks,
dave


I have an Acer Aspire One with an Atheros Wifi card, and I have successfully compiled the madwifi drivers on a clean install of Ubuntu Karmic (taken from the [COLOR=Blue][AAO community docs]("https://help.ubuntu.com/community/AspireOne/Ubuntu8.10")[/COLOR]):

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci
```

I have always had issues with the ath5k driver, even when it works OTB, due to the fact that it cuts out and ditches my connection when downloading anything, apparently due to 'high traffic.' The madwifi drivers are the most reliable drivers for the atheros cards, in fact the main atheros site says to use these drivers under linux!

---

