---
title: "Disable internal wifi antenna"
date: 2011-03-02
forum: Hardware
---

### Post by JoeC5 on 2011-03-02
I have a DELL studio 15 something with Ubuntu 10.10 installed.

The DELL has a built-in internal wifi antenna and it works fine.
Well I bought a fancy new Netgear wireless router. And for the hell of it I bought a fancy new Netgear N600 Wireless Dual Band USB adapter to go with it.

So here's the deal, I have the internal wifi antenna and an external antenna, being the usb adapter. I want to turn off my internal antenna and use only the usb adapter.

As I had it, both antennas were fighting for the signal and the internal one kept winning out. So now the USB adapter is lying on my desk disconnected.

I've searched around a little and tried a few things before I got to this point of posting.

My 1st simple test was to turn off wireless by un-checking enable wireless and watching the wifi light go off.. then plugging in the usb adapter... the action of plugging it in enabled wifi automatically and the light was back on.
2nd I tried the command ifconfig eth1 down from the terminal - nothing went down.
Then I added the ifconfig eth1 statement to the /etc/rc.local file and restarted- no change.

OK now I like this last idea that I found.
To disable the kernel module by editing the /etc/modprobe.d/blacklist file.
The only thing is I don't know which module after running lsmod matches the internal antenna, there isn't any that jump out at me.

So if someone can tell me which is the module that controls the internal antenna, that would be great.

Or if someone has a better idea for turning off the internal wifi antenna - that would be appreciated too.
Thanks.

---

### Post by howefield on 2011-03-02
Have you tried turning off the internal Wireless adapter from the Bios ?

---

### Post by JoeC5 on 2011-03-02
I didn't try.. whats that F2 or F12 as it's starting up. Ever since I started using Ubuntu I haven't needed to get into the BIOS anymore... lol

---

### Post by howefield on 2011-03-02
Could be, depends on the machine, sometimes it is the Esc or Delete key.

Try the documentation for that came with your machine, or watch whilst it boots, you'll often see something like "Press F2 for Setup" or similar during the booting process.

---

### Post by JoeC5 on 2011-03-02
Superb Howefield.

Got the internal antenna to turn off and stay off.
Thank you.


Now I'm having a different issue but I've run out of gas today.

I'll put it up and see if I get back on to it tomorrow.

So everything on the USB adapter lights up. It sees all the networks flying around the area. And it even tries to hook up with my secured network. It asks for my password. I give it. It asks again and again... but it never gets through. 

I have two drivers that I got online.
bcmwlhigh5.inf   - does work for me
and 
arusb_xp.inf   - doesn't work for me

These are Windows Wireless Drivers      System>Administration>

I don't know.
My guess and this is far fetched because it lights up, it says the hardware present: yes and it even gets as far as asking me for the password. I was thinking/guessing since it's a windows driver I need wine? Mostly because I saw others online mentioning wine in context of these drivers. Honestly I'm not interested in wine at all.

By the way I have ndiswrapper packages installed.

Thanks again.

I think I'll take off the wireless security for a few minutes tomorrow. Seems to be a handshake is not happening somewhere.

---

### Post by grahammechanical on 2011-03-02
You would not be the first and I have made this mistake myself but you could be putting in the wrong pass phrase. Or have the wrong encryption method set.

Regards.

---

### Post by JoeC5 on 2011-03-03
I've done it too grahammechanical - but not this time

I do have some interesting findings. But I'm putting way too much time into this now. So I'll leave my findings for someone else to learn from.

So I turned off the internal antenna through the bios as howefield brilliantly suggested and I turned off my wireless security for a short time AND BAM .. 100+ MB speeds. SO it worked very well with no security.

Turned back on security and I've got the same problem. Scans and scans and asks me for my password and I give it and it asks and asks and I give it .. but no hook up.

Looking into the [ftp://downloads.netgear.com/files/WNDR3700_UM_16OCT2009.pdf](ftp://downloads.netgear.com/files/WNDR3700_UM_16OCT2009.pdf) manual I found something called Wi-Fi Protected Setup (WPS) page 2-13.
This is something that both my router and the wireless adapter have and it looks like it's overriding normal security [non-WPS] methods. I've tried every combination of wireless security methods ex- no security and nothing works..  so i started looking into the bcmwlhigh5.inf file.  UMMMM yea I'm looking into the driver files to see if there's a way to turn off this WPS junk. But wow this is tiring. And all I see in here is Microsoft parameters/configuration settings. Enough for today .. way too much time invested to continue or to give up...   tomorrow is a new day...

By the way I tried the WPS stuff but i think that definitely requires some wine since the client software on the installation disk for the adapter is specifically written for Microsoft OSes.

---

### Post by JoeC5 on 2011-03-03
I should have read the system requirements before I bought the adapter. Or checked the compatibility lists with the community. O well.

---

