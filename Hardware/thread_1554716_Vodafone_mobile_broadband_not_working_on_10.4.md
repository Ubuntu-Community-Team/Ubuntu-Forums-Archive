---
title: "Vodafone mobile broadband not working on 10.4"
date: 2010-08-17
forum: Hardware
---

### Post by Sir_bobbyuk on 2010-08-17
Hi,

I am sorting out a friends laptop and have installed 10.4 onto it. The problem i'm having is that when i connect the vodafone dongle it tries to connect but fails.a folder shows on the desktop, when i open it it shows the .executable files for windows only. I have looked on the forums and the only reference is regarding 9.10 and followed those instructions but to no joy.
In have tried my own mobile broadband '3' and it worked fine with no issues.
Has anyone else had the same problem and managed to resolve it.

Kind Regards

Bob

---

### Post by houblon on 2010-08-18
I've tried it with Hardy Heron and I get absolutely nothing. I've tried talking with the local staff at Vodafone but they seem to have never heard of linux here in Fiji.

---

### Post by dineshs on 2010-08-18
The dongle,I think,is detected as a storage device You need the tool usb-modswitch to make it detected as modem ,See if these links can help
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
[http://ubuntuforums.org/showthread.php?t=1465557](http://ubuntuforums.org/showthread.php?t=1465557)

---

### Post by jarviser on 2010-08-18
houblon,  Hardy is too old to be likely work with 3G/HSDPA.  Try 10.04

If 10.04 does not work, suspect the dongle is not supported and do more research in the Ubuntu knowledge base.

Sir Bobby, Ignore all software that comes with the dongle, it's for Windows only. All necessary drivers are in the latest kernel and connection is via the Network Manager icon (Mobile Broadband tab)

As the OP can connect with 3 then the process is the same with Voda assuming the dongle is supported, the dongle has been activated already, and the PIN is disabled.

My experiences [here]("http://www.jarviser.co.uk/jarviser/3gdell5510lucidlynx.html")

EDIT: I didn't bother with usb-modeswitch installation - I just ignored the mounted software. It clutters up the desktop but seems to do no harm.

---

### Post by jarviser on 2010-08-18
I should have added that, for non-USA users, it's best to ignore the drop-downs for your ISP when entering details in the Mobile Broadband connection. Instead of selecting "Vodafone", select "I can't find my provider...." and then in the details simply type in the correct APN for your ISP, which in many cases is not the one provided by Ubuntu.  Check the dial number.

Google the correct APN and dial number for your ISP in your country. The dial number should be universal but check it the same way as they do vary with country.

---

### Post by jimmers on 2010-08-19
Try this site:-

  	 	 	 	 	 	  [www.betavine.net/bvportal/resources/datacards](www.betavine.net/bvportal/resources/datacards)


Look for ozerocdoff_04-2_i386 deb


              usb-modeswitch_0.9.7_i386 ded  (its in Synaptic also)

             vodafone-mobile-connect_2.2

Works for me since Jaunty.


Luck

---

### Post by jarviser on 2010-08-29
I just swapped to Vodafone Pay as you Surf deal with K3570-Z dongle and I was able to get it going on 10.04 where Win7 completely let me down.

The key is to use the "I can't find my provider..." option in Network Manager then simply type in the correct UK APN (in my case PPBUNDLE.INTERNET) and that was it. Straight in. No modeswitch, no Betavine needed.

In fact I tried the Betavine connection manager which did also work at first using the above APN but the whole lot was wiped by the system update because it didn't seem to like the python "twistd" stuff remaining in the system.

---

### Post by Vyodacoda on 2010-09-11
I can confirm the comment by jarviser although mine was slightly different as I already had a failure with the device but still on a one month contract with Vodafone
Having read jarviser's post I did the following
clicked on the network connection at the top of the screen
Selected VPN Connections
Selected Configure VPN
Selected Mobile Broadband
Selected the newly failed device
Clicked Edit
Entered PPBUNDLE.INTERNET in the APN field
Clicked the Apply button
Closed down the form
Connected to the internet
Many thanks to jarviser!!!!

---

