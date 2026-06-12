---
title: "ndiswrapper woes"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by zevin on 2005-03-28
Well, this is my third attempt to see if linux is right for me. Corel linux was horrible, and reb hat was ok. i really like ubuntu though. After a little work i got ndiswrapper-1.1 working, and i was albe to use my broadcom b/g pcimini card. But after i rebooted, nothing. The networking window shows the device is active, and can connect to my SSID, but when i launch firefox, its a no go. Anyone got any suggestions? Thanks!

---

### Post by chronusdark on 2005-03-28
i spent all day yesterday working on that....evertually what i did was remove all ndiswrapper packages and compile and install from source on the website...worked like a charm...took like 3 minutes

---

### Post by StacyWebb on 2005-03-28
if you have ran apt-get dist-upgrade or are runnng a new kernel (2.6.10-5) you will need to download the newest version 1.1 and then cd into the directory and run:

sudo make
sudo make install

make sure your old drivers are removed and then you reinstall them. To verify everything after install just run:

sudo ifup wlan0 

this should solve your problems

BTW you can download the newest ndiswrapper from here:

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by azelter on 2005-03-29
I just installed hoary and am having trouble with ndiswrapper. I had all working in warty fine. I've tried the ubuntu ndiswrapper and also tried compiling the latest version from source but the result is the same (see below).
It looks like everything is working. Drivers are installed and card is found. However, the wireless active LED on my laptop doesn't come on indicating that the card has not been turned on. Previously this happened when I loaded the module and did ifup wlan0. I'm confused. If anyone has any ideas I'd be very gratefull.
Thanks in advance,
Alex

root@pohjanakka:~ # ndiswrapper -i /usr/local/wireless/bcmwl5.inf 
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
root@pohjanakka:~ # modprobe ndiswrapper
root@pohjanakka:~ # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 
root@pohjanakka:~ # iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:5F6B-77A4-6800-4E2F-AAC7-80B6-71   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by azelter on 2005-03-30
OK now I solved the problem and thought I'd report it here in case anyone else has the same trouble. I tried everything everyone else mentioned (e.g. downloading and compiling latest version of ndistwrapper; changing the radio-thinggy atribute to 0 etc. etc.). I also tried several different kernel versions. In the end the problem was with the version of bcmwl5.inf from my HP Driver recovery CD. It worked before on Warty, but not for this version of ndiswrapper (hoary) or the latest one from sourceforge. When I downloaded the exe file from HP and extracted it (by executing it using wine, which worked long enough to extract the files before dying) and used the bcmwl5.inf file from that for ndiswrapper - my wireless light went on and everything worked.
It's intersting that different versions of ndiswrapper can/can't use different versions of the same driver. It's also intersting that each version of ndiswrapper sets things in those drivers differently. For example using the hoary version of ndiswrapper I got:
Forcing parameter IBSSGMode|0 to IBSSGMode|2
and my Radio(thinggy) was set to 1 (= off)
Changing it to 0 made no difference.
With the current version of ndiswrapper from sourceforge the radiothinggy attribute was set to 0 by default and I got different output.
Sorry for missing information. I'm on  adifferent computer now and can't get all the output. 
The conclusion for me is try a few versions of the same driver (as well as trying a couple of versions of ndiswrapper). 
Cheers,
Alex

---

