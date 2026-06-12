---
title: "Ethernet stopped working..."
date: 2010-07-22
forum: Hardware
---

### Post by Cosmic Charlie on 2010-07-22
Howdy all,

My ethernet stopped working on Ubuntu 10.04. This happened after my house got struck by lightning, but my computer is plugged into a surge protector. Maybe though, electricity went through the cat5 cables and jolted things up a bit in my PC? I thought this was the case for my graphics card as well as it stopped working on my PC, but now after uninstalling drivers, it is working again. So... does anyone know how I can try fixing my network card on ubuntu?

After typing 'ifconfig' with the ethernet cable plugged in to my PC it gives me:

```

eth0      Link encap:Ethernet  HWaddr 00:0a:48:0b:d5:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```


I would really appreciate any and all help.

---

### Post by Goolie on 2010-07-22
This happened to me recently as well.

I restarted the PC, left it off for a few minutes, reset my modem and router.

Following, I clicked on the internet symbol saying 'no connection' and 'added' the eth0 wired connection, it did it mostly automatically for me.  

If there's already an eth0 wired connection, try removing it and adding it once more?

---

### Post by Cosmic Charlie on 2010-07-22
Well when I click on the internet symbol in the top right it says "Wired Network - disconnected" when the ethernet is actually plugged in.. When I boot into windows, the ethernet is not working either.

I did in fact test the ethernet on my macbookpro which I am typing on now, and it works.

Does anyone have any other suggestions? Is my mobo fried from my lightning experience? (I think the ethernet port is part of the mobo, correct me if i'm wrong)

---

### Post by Goolie on 2010-07-22
So far when my motherboards have fried on me, they usually went completely, usually integrated ports won't work if the motherboard is fried, since they're on the same board.

I mean, I'm not sure, hopefully someone a little more knowlegeable can help us out with this. =\

[Also, not sure if you're ethernet port *is* part of your motherboard, if it was it's port would be nearer the top (if this is a tower) where the other USB / Mouse / Keyboard inputs were, if it isn't it sure be towards the bottom where your PCI card slots reside.

---

### Post by Cosmic Charlie on 2010-07-22
Yes, my ethernet port is next to the USB and PS/2 ports thats why I assumed it was part of the MOBO. The ethernet on my PC has stopped working on both Ubuntu, and XP since my lightning strike.

I thought it had fried my video card too since it had stopped working as well. After uninstalling nvidia drivers its back in action..

Any help would be greatly appreciated.

---

### Post by Goolie on 2010-07-22
> **Cosmic Charlie said:**
> Yes, my ethernet port is next to the USB and PS/2 ports thats why I assumed it was part of the MOBO. The ethernet on my PC has stopped working on both Ubuntu, and XP since my lightning strike.

I thought it had fried my video card too since it had stopped working as well. After uninstalling nvidia drivers its back in action..

Any help would be greatly appreciated.

bump someone help this man!

also, try goofing around in the ethernet connections, see if something starts working,

i'm not sure how I got the ethernet connection working on my laptop, i just started pressing buttons haha.

Yea, sounds like it's attached to the mobo, I'm not sure, but I suppose it could possibly be fried.  Have any NIC's laying around you can toss in and test out?

---

### Post by Cosmic Charlie on 2010-07-25
BUMP...

Maybe someone can tell me how to pick and install a new network card or adapter so that I can get internet with a cat5 cable.

 Can I choose any old ethernet adapter (either USB or PCI)? Or are there some that are more Ubuntu 10.04 friendly? Once I buy it and install it do I have to let ubuntu know or does it notice on it's own?

Will this interfere with the PC's motherboard which has an ethernet port in it (which seems to have burnt out)?

---

### Post by Goolie on 2010-07-25
> **Cosmic Charlie said:**
> BUMP...

Maybe someone can tell me how to pick and install a new network card or adapter so that I can get internet with a cat5 cable.

 Can I choose any old ethernet adapter (either USB or PCI)? Or are there some that are more Ubuntu 10.04 friendly? Once I buy it and install it do I have to let ubuntu know or does it notice on it's own?

Will this interfere with the PC's motherboard which has an ethernet port in it (which seems to have burnt out)?


If you're installing a new NIC, you'll have to goodle more instructions if you've never done so before.  I've heard some problems with the USB NIC's, you'll most likely have more success using a PCI NIC.  You should try to find a cheap, cheap one.  It should be fine.  Also, the ethernet card in the PCI slot will not be interfered with by the motherboards onboard ethernet.  It should also notice the NIC on it's own.

---

### Post by Cosmic Charlie on 2010-07-25
super quick reply, and good advice, thank you very much Goolie!! :razz:

---

### Post by dineshs on 2010-07-25
I think most of the ethernet cards are supported.Just plug it in PCI slot and restart.It will be detected automatically.(You can also try old cards)

---

### Post by Goolie on 2010-07-25
> **Cosmic Charlie said:**
> super quick reply, and good advice, thank you very much Goolie!! :razz:


haha, no problem =D

---

### Post by Cosmic Charlie on 2010-07-25
Success! Old NIC works!

---

### Post by Goolie on 2010-07-25
> **Cosmic Charlie said:**
> Success! Old NIC works!


Old NIC as in the motherboard's build in NIC?

Or an old PCI one you threw in?

Either way, glad it's working for you!!

=D

---

