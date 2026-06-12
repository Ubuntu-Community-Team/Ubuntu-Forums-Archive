---
title: "low wifi signal with a belkin f5d7000"
date: 2010-07-31
forum: Hardware
---

### Post by Wotan87 on 2010-07-31
hi everybody I'v jsut buy a belkin f5d7000 wifi pci card

problem is that I have a very low signal 
```

max@max:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"DW-B-200-4162f"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:8E:4A:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=15/100  Signal level=15/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I firstlyconfigured it to 54 Mbs but internet is still quit slow

I m actually only 2.5 meter away from the emitter (none object between emitter and antenna) and the signal is only 15/100 !!!

When I m on the upper floor the signal is still 15/100 ... (it should be lower or repectively higher when i'm next to the emitter)

Does anybody one know if there is something to configure or is the card just ****ing bullshit?

---

### Post by roger_1960 on 2010-07-31
Hmm

I think perhaps you will need to download a driver from Belkin and install it using ndiswrapper.(This allows a window driver to work for Linux)  This involves using the terminal and entering some code.

1st  Determine the version No of your f5d7000.

2nd Have a look at [http://en-us-support.belkin.com/app/answers/detail/a_id/303](http://en-us-support.belkin.com/app/answers/detail/a_id/303)

3rd Google for F5d7000 v???? (yours) linux, and see if it has been done before = its likely!

Sorry not to be more specific, but we need more info.

Does the card work?  Is it just the reporting of link quality that is wrong?  I have never got any connection with a strength as low as that on my Belkin f5d7010 v3000 (generally my card works fine, but it may well not be the same at all)

---

### Post by Wotan87 on 2010-07-31
Hi roger

I've done it: I m using a F5d7000 v7 with a RTL8185L chipset
i have downloaded the winxp64 bit download ( my architecture is an amd 64) 
I've have loaded it with ndiswrapper but the card doesn'twork 
(ifconfig doesnt'know any wlan any more)

The card itself work but the internet ist quiet slow...

---

### Post by dino99 on 2010-07-31
you might install a 32 bits system if you want less issues, use pae kernel to use 3 Go or more ram

into synaptic, you might install:
- nictools-nopci
- nictools-pci

[http://ubuntuforums.org/showthread.php?t=687564](http://ubuntuforums.org/showthread.php?t=687564)

---

### Post by roger_1960 on 2010-07-31
Hi

Following on from dino99

Your system has an AMD64 chip, but have you installed 64 bit ubuntu or 32bit?

---

### Post by Wotan87 on 2010-08-02
Hi roger I have got a 64 bit kubuntu 10.04 

Dino: I try the 32 bit driver into ndiswrapper soon and tell you about ;)

---

### Post by Wotan87 on 2010-08-02
Hey I 've just tried the 32 bit driver but it does not work:
when entering iwconfig or ifconfig the wirless interfaces doesn't appear..

---

### Post by Wotan87 on 2010-08-02
I have buy a usb netgear wifi adapter ant the signal with it is 80% instead of 21....
seems like it would come from the card...

---

