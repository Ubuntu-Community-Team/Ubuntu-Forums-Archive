---
title: "Wireless card found, but cannot log on to network"
date: 2008-06-27
forum: Hardware
---

### Post by atowell on 2008-06-27
I just used this post [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) to install ndiswrapper and be able to use my wireless on my Dell Inspiron 1521. I can now see the network and attempt to get into it, but when I type in the passcode it tries to connect for a few minutes then it tells me it can't connect without the passcode and it prompts me to enter it again. This process is continuous and I don't know how to fix it. Anyone have an idea?

---

### Post by ukripper on 2008-06-27
> **atowell said:**
> I just used this post [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) to install ndiswrapper and be able to use my wireless on my Dell Inspiron 1521. I can now see the network and attempt to get into it, but when I type in the passcode it tries to connect for a few minutes then it tells me it can't connect without the passcode and it prompts me to enter it again. This process is continuous and I don't know how to fix it. Anyone have an idea?

make sure you are using correct key - WEP or WPA/WPA2.
and check whether it is hex or ASCII

can you post output of the following commands:
> iwconfig
> iwlist scan

---

### Post by atowell on 2008-06-27
The password is WPA which is what I've been using. Here is the output of the commands (I had to save to a jump drive and copy to my desktop, so the formatting got messed up.): 

adam@adam-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

adam@adam-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:12:88:8C:11:F1 
                    ESSID:"2WIRE044" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 02 - Address: 00:09:5B:86:FE:78 
                    ESSID:"NETGEAR" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 

adam@adam-laptop:~$

---

### Post by ukripper on 2008-06-28
> **atowell said:**
> The password is WPA which is what I've been using. Here is the output of the commands (I had to save to a jump drive and copy to my desktop, so the formatting got messed up.): 

adam@adam-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

adam@adam-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:12:88:8C:11:F1 
                    ESSID:"2WIRE044" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 02 - Address: 00:09:5B:86:FE:78 
                    ESSID:"NETGEAR" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 

adam@adam-laptop:~$

your drivers have loaded fine. 

You need to configure your acces point you want to connect to - check your key and make sure it is correct either make sure it is marked hex if it is hex and ASCII if it is ASCII otherwise it won't work.

---

### Post by atowell on 2008-06-28
I've tried each of the different methods when I type the code in. All that's on the router is the 10 digit number. There isn't any indication if it's ascii or hex.

---

### Post by ukripper on 2008-06-29
Are you using nm-applet?

---

### Post by atowell on 2008-06-30
I feel like a moron, but I have no idea what nm-applet is.

---

### Post by ukripper on 2008-06-30
> **atowell said:**
> I feel like a moron, but I have no idea what nm-applet is.

Can you see wireless icon in your panel? with wireless signal showing? That is nm-applet. If you don't have that then you would need to install it through synaptic package manager and try that.

if that doesn't resolve your problem then perhaps we can go to interfaces file and use it to configure your connection.

it would be helpful if you take a screen -shot of your desktop and post it here to see whether you have nm-applet already or not.

---

### Post by atowell on 2008-06-30
I went to synaptics manager and nm-applet wasn't listed. The wifi light on my laptop is on, but there's nothing in the panel. When I right click on the network icon and select edit wireless networks, a box pops up but there's nothing in it. I can input a name and there's a space for a bssid, but I can't type in it. [http://www.flickr.com/photos/28147823@N04/2625350221/](http://www.flickr.com/photos/28147823@N04/2625350221/)

---

### Post by gnp421 on 2008-06-30
The code is Hex, WEP Hex code, should be second option in the list of selections.

---

### Post by atowell on 2008-07-01
*I input the key as Hex, which worked. I'm pretty sure I tried that before, but I could be wrong. Thanks a lot to both of you for putting up with my novice questions and helping!! :)*

So, for some reason it doesn't work again. It was able to connect to download updates, then when it restarted it wasn't working again. Should I go back to Vista?

---

### Post by ukripper on 2008-07-02
> **atowell said:**
> *I input the key as Hex, which worked. I'm pretty sure I tried that before, but I could be wrong. Thanks a lot to both of you for putting up with my novice questions and helping!! :)*

So, for some reason it doesn't work again. It was able to connect to download updates, then when it restarted it wasn't working again. Should I go back to Vista?

can post output of the following :
```
iwconfig
``` and ```
iwlist scan
```

---

### Post by atowell on 2008-07-02
So, wireless is working again. I see the wireless icon, too. To get it working I went to the network and went to properties, then checked "Enable Roaming" under the wireless. I'm at a hotel and tried this because I couldn't get any internet, even wired. When I enabled roaming wireless and ethernet worked. Thanks again for helping me through this!

---

### Post by ukripper on 2008-07-03
I am glad it is working for you now!:)

---

