---
title: "Huge Realtek RTL8192ce wireless speed problem"
date: 2011-11-16
forum: Hardware
---

### Post by DariusZelvys on 2011-11-16
Hi,
I have a big problem with my acer aspire laptop wifi speed. I have router at home which works in b/g wireless modes. My internet speed is about 20mbit/s (that speed i get when i work on the same network with my dell laptop). The problem is i get only 1mbit/s speed with acer laptop. iwconfig terminal output says i have realtek rtl8192ce wireless card. No matter what i tried, i have a terribly slow internet. If i connect to the internet with wired cable with the same computer, my internet speed is flying..
Would appreciate if any of you could help me. I use 3.0 kernel, and use ubuntu 11.10 . Tried clean install of 11.04 ubuntu, got the same results.

---

### Post by DariusZelvys on 2011-11-16
> **DariusZelvys said:**
> Hi,
I have a big problem with my acer aspire laptop wifi speed. I have router at home which works in b/g wireless modes. My internet speed is about 20mbit/s (that speed i get when i work on the same network with my dell laptop). The problem is i get only 1mbit/s speed with acer laptop. iwconfig terminal output says i have realtek rtl8192ce wireless card. No matter what i tried, i have a terribly slow internet. If i connect to the internet with wired cable with the same computer, my internet speed is flying..
Would appreciate if any of you could help me. I use 3.0 kernel, and use ubuntu 11.10 . Tried clean install of 11.04 ubuntu, got the same results.

btw, signal strength is excelent, but the speed is not..

---

### Post by DariusZelvys on 2011-11-17
anyone? please...

---

### Post by jsevi83 on 2012-01-02
You can download the official Realtek driver (RTL8188CE) and install it manually. Right now the version is 0005.1230.2011.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Extract the downloaded file and open a terminal in the extracted folder. Copy inside this commands:

sudo apt-get install build-essential
make
sudo make install

You will have to repeat this process everytime you update the kernel.

---

### Post by librechick on 2012-01-03
That card is dependent on non-free firmware. Atheros's chipsets are better supported. You might just want to replace it. The cards are cheap and generally easy to replace. Two screws on the bottom usually. Then pop out and pop in. Attach antennas and done.

[http://www.thinkpenguin.com/](http://www.thinkpenguin.com/) has them and support too. The nice thing about this is they have experts experienced with the particular product. Unlike most of us here who haven't got the hardware in question.

---

### Post by hholzgra on 2012-04-13
Same problem here at home, Thinkpad Edge E325 with  RTL8192ce drops to a transfer rate of ~120-130KB/s after a little while. At another location it works fine though, can download at full speed for hours. And on a recent business trip it disconnected every few minutes in the conference room while in the hotel it stayed connected just fine at good signal strength but ping times to the access point were between 5ms and 10 seconds. A different device could deal with both access points just fine.

So it is not just the card itself but its interaction with different access point models somehow.

My Girlfriend also has an E325, that one has a BroadCom card though, that one works fine without any issues.

Simply buying a different card did not work out as even under Lenovo ThinkPads still have a BIOS whitelist of supported cards and will refuse to boot if they discover everything else (inherited from the IBM days, IBM claimed that to get FCC approval it must have every laptop(or actually antenna)/card combination they sell FCC certified and must block any other combinations ... something that does not really seem to be an issue to any other laptop manufacturer?)

With 12.04beta (fresh install)the download rate drops after about a minute, afair it already failed after 20-30 seconds on 11.10 but i never really took the time there.

Using the latest RTL driver lead to screen freezes pretty quick so i did not really test with it ...

A friend suggested that i may be hitting [http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67) but this happens both on battery and with AC power, and the situation depends on the access point being connected to, so i think i can rule out power management issues (the card does not even seem to support power management anyway, at least not via iwconfig?)

---

### Post by fabsxm on 2012-05-13
Hi,
I bought recently a laptop with this wifi card and with the same problem.I found on the realtek website the driver to compile:
92ce_se_de_linux_mac80211_0005_1230_2011.tar.gz .
Just do a:
sudo make
sudo make install
restart computer and enjoy, it works fine now

Tosh C660-1C7 - ubuntu 11.04

---

