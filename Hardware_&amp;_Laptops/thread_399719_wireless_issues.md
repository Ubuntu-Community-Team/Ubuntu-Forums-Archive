---
title: "wireless issues"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by apureevil1 on 2007-04-02
I am a nubie and I decided to build my own PC just for Ubuntu. I bought an ASUS A8-VM SE, board and an Encore ENLWI-SG wireless card (athos chipset),and an AMD athlon 2.2 GHZ processor. long story short I assembled everything and fired her up with Ububtu 6.10. It seemed to recognize everything without issue including the wireless card,I was pleased as punch..then the kicker..I could not configure my card to access my Buffalo (WHR-G54S) router. I have tried everything and had to reinstall twice, What is the best method with 6.10 (edgy) to get my wifi working. I have the router configured fine for 3 other (windows devices) I have spent 8+  hours working on this including reading the forums..any help..please...

---

### Post by nsleiman on 2007-04-02
do you have ssid and ecnryption ?

---

### Post by sdrubolo on 2007-04-02
Have you tried to use the network manager gnome and subsequently using the nm-applet. it worked for me very well, because I've a laptop and I've been using the wireless connection at home. In addiction it works very well at my university too. So I hope it will work fine for you too.

---

### Post by apureevil1 on 2007-04-03
I have an SSID and Encription (shared key) , I would like to lock down by macaddress as well, but I need to get it working correctly first, then well who knows....
and as a follow up, I got wireless working very early this morning, I believe using network manager, (I am not certian exactly what I did) I now have  to log into the computer and then into a keyring..but it works, My signal strength is so so at best, Never above 45% and I am only 15ft from the AP, I get full signal upstairs on my windows box with the same wireless card..any sugestions ..I guess I shouldnt complain..its working. :) 
( I wish I knew what I did, then I could post my directions, I may blow my system away again in a week or so and try again so if anyone has more ideas let me know)

---

### Post by tjod on 2007-04-06
I've had excellent results with WICD: [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)  Works with Hidden ESSID and WPA and WPA2 encryption.

TIm O

> **apureevil1 said:**
> I have an SSID and Encription (shared key) , I would like to lock down by macaddress as well, but I need to get it working correctly first, then well who knows....
and as a follow up, I got wireless working very early this morning, I believe using network manager, (I am not certian exactly what I did) I now have  to log into the computer and then into a keyring..but it works, My signal strength is so so at best, Never above 45% and I am only 15ft from the AP, I get full signal upstairs on my windows box with the same wireless card..any sugestions ..I guess I shouldnt complain..its working. :) 
( I wish I knew what I did, then I could post my directions, I may blow my system away again in a week or so and try again so if anyone has more ideas let me know)

---

### Post by rjcrowder on 2007-04-07
Just an FYI... you can get rid of the keyring password prompt if you want to.  Search the forums fo pam_keyring and you'll find numerous threads discussing how to do it.  That said - I've also started using WICD and highly recommend it!

---

### Post by jdbartlett on 2007-04-08
I just tried installing Wicd 1.2.5 on Feisty after I had difficulty connecting to my hidden WPA-protected home network.  I don't see a spot to enter my hidden ESSID.  Any ideas?

---

### Post by jdbartlett on 2007-04-08
> **jdbartlett said:**
> I just tried installing Wicd 1.2.5 on Feisty after I had difficulty connecting to my hidden WPA-protected home network.  I don't see a spot to enter my hidden ESSID.  Any ideas?D'oh!  Talk about a stoopid moment.  Turns out that "connect" button is what I was looking for (you know, the first one in the top left corner)... hit it and you're prompted for a hidden ESSID.

---

### Post by apureevil1 on 2007-04-12
well I am back..I have been playing in territory I have no knowledge in ie.ubuntu....I am hooked however I am still trying to figure out what the he** I am doing..long story short I...in windoz land..effectively blue screen of death my PC..so I did what I always do..I rebuilt the girl.. now I cannot get my wifi to work..I have tried everything.....except what works. I have an encore pci card with an Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01) card. per lspci..
iwconfig 
     lo        no wireless extensions.

   eth0      no wireless extensions.

   wifi0     no wireless extensions.

   ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
(          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

   sit0      no wireless extensions.

I have installed wicd and can see my AP but I cannot connect..I disabled everything security wise and still cannot get in..I really need help..AGAIN..

---

### Post by apureevil1 on 2007-04-24
I did a complete reinstall of Edgy 6.10 again this morning, I enabled all replositories and did all the updates for 6.10 then I followed this..
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5)
( I only had to do these 2 steps and then a reboot)
1.)  **sudo apt-get install network-manager-gnome**
2.)  **sudo /etc/init.d/dbus restart**
upon reboot I had the icon in the corner, my wireless connection was listed, I chose connect, it asked for my Keyring password (I used the same one as my log in to the system) and WPA key(password) It stll asks for my keyring password on every reboot but that is a very minor annoyance( I think I remember a fix for this but I am uncertain if its for Edgy or Fiesty)..I am just happy as hell to have my wireless working. and it's connecting with a signal of 75%
I have an** Encore ENLWI-SG **PCI card which has an **Atheros 5212** chipset.
**ASUS A8V-VM SE** Motherboard socket 939 with an AMD Athlon 64 (2.2 ghz processor) and 1 GIG of Ram
all necessary drivers installed with ubuntu 6.10 after I enabled all repositories. I believe that it is using the madwifi i386 generic drivers.
I hope this helps..I am going to stick with Edgy for a bit, I want to enjoy my wireless for at least a week ( then I will try to get it to work with Fiesty...

---

