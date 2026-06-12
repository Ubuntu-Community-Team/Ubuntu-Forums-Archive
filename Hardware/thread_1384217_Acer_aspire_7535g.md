---
title: "Acer aspire 7535g"
date: 2010-01-18
forum: Hardware
---

### Post by dionm on 2010-01-18
Hi, I am new linux user, I just Installed ubuntu 9.10 on my laptop ACER ASPIRE 7535G

Specifications:
[LIST]
[*]AMD Turion™ X2 Ultra dual-core mobile processor ZM-82/ ZM-84 (2 MB L2 cache, 2.20/2.30 GHz, DDR2 800 MHz, 35 W), supporting AMD HyperTransport™ 3.0 technology
[*]4 GB of DDR2 667 MHz memory
[*]17.3" HD+ 1600 x 900 pixel resolution,
[*] HD3200 for running on battery(Power Express Ati feature onder Vista) and one HD4570 for running when connected to power. 
[*]Xorg 7.6 glibc 2.1 
[*]ATI Catalyst 9.12
[*]WLAN1, 3: Acer InviLink™ Nplify™2 802.11b/g/Draft-N Wi-Fi CERTIFIED® network connection, supporting Acer SignalUp™ wireless technology
[/LIST]
.... if you need more details please feel free to ask me ;)

So, everything works fine except:
[LIST]
[*]wireless got diconnected and after that doesn't connect anymore
[*] Catalyst uses HD3200 and no other card identified.
[*] the strength of the wireless signal is really poor
[/LIST]

Can anyone help me with that? ThanxO:)

---

### Post by dionm on 2010-01-31
Hey guys! I am still having this problem... can anyone give a hand? Thanx anyway!

---

### Post by punchdrunkgrunt on 2010-01-31
Same machine, same problems. Only difference is I'm using Kubuntu 9.10.

Wireless: The ath9k wireless driver is a POS. Mine usually lasts an hour or two before failing. Try opening a terminal and typing
```
sudo modprobe ath9k
```
to reload the driver. Works for me about half the time. Otherwise you could try using the Windows drivers using a utility called ndiswrapper; or you could look here
[HTML]http://ubuntuforums.org/showthread.php?t=1309605[/HTML]
which I haven't tried yet.

Video: I assume you're using the proprietary driver (fglrx) rather than the open source one. I've recently started using the latest version (10.1) from the ATI website - better OpenGL support but VLC media player is playing up. From the release notes it seems ATI don't do a linux driver for the Mobility Radeon HD4570 that we have, so we're stuck using the 3200.

For the record I would heartily recommend anyone to NOT buy this computer. It's like somebody collected all the hardware that doesn't have proper linux support and put it all into one small package.

Sorry I couldn't be more help.

---

### Post by dionm on 2010-01-31
Thanks a lot I will try it and i let you know!! Many thanx man!! :D

---

### Post by arkeo on 2010-02-21
Hi,
I have to say the 7535G is poorly supported under Win7 as well. Anyway, how can you tell what video card it is using under Ubuntu? I've been playing around with 9.10 for a while, but it left me wondering which video card was enabled/recognized by default...

:confused:

OT: suggestions for another AMD-based laptop with discrete ATI graphics (one that might actually work with Linux)?

Cheers...

---

### Post by dionm on 2010-02-21
Hi arkeo,

this Acer uses ATI HD3200 .... only!!! :-x

but if you want to buy a laptop in order to support well linux then looks at this thread:
[HTML]http://ubuntuforums.org/showthread.php?t=282650[/HTML]

and also this is a site for linux laptops 
[HTML]http://www.linuxcertified.com/linux_laptops.html[/HTML] 

as i talked to some of my friends and also by looking around...a brand that supports well Ubuntu and generally linux is HP...

I have to notice that UBUNTU 9.10 karmic has many bugs....

Hope that helps :)

---

### Post by arkeo on 2010-02-22
> **dionm said:**
> Hi arkeo,

this Acer uses ATI HD3200 .... only!!! :-x

Hi dionm,
what I meant to ask is where, in Ubuntu, do you look to see whether it is the 3200 or the 4570 running? In a config file like xorg.conf? Somewhere else? For example, in Windows I look into the Device Manager and I see that the 4570 is not working while the 3200 is.
Where do I look for this info in Ubuntu? I don't have access to Linux right now, but IIRC the Hardware Drivers panel says that the drivers for Radeon 4550/4570 are installed and running (I'll have to check to be sure though).

> but if you want to buy a laptop in order to support well linux then looks at this thread:
[HTML]http://ubuntuforums.org/showthread.php?t=282650[/HTML]

and also this is a site for linux laptops 
[HTML]http://www.linuxcertified.com/linux_laptops.html[/HTML] 

as i talked to some of my friends and also by looking around...a brand that supports well Ubuntu and generally linux is HP...

Thanks for the links by the way!

> I have to notice that UBUNTU 9.10 karmic has many bugs...

I've been noticing a constant degradation in quality over the past years, mirrored of course by an increase in functionality and flexibility...
I'm stuck with a laptop for various reasons (and consequently Ubuntu), but if I could I'd get a nice desktop and get my hands dirty with Debian... \\:D/

I'm not versed enough in Linux to configure Debian on a laptop properly, especially mobile broadband (nowhere to be found, I guess is something too new for Debian/stable?) and power management...

Cheers...

---

### Post by dionm on 2010-02-22
I understood your question but if you look at **punchdrunkgrunt's** answer:
> From the release notes it seems ATI don't do a linux driver for the Mobility Radeon HD4570 that we have, so we're stuck using the 3200.

there is no way till now to use the HD4570.... :confused:

As you are new in Linux i dont suggest you to use Debian ... but if you want so then try the test version.... stable is the worst choice!!! 

As for the device manager check the following:
[HTML]http://ubuntuforums.org/showthread.php?t=472267[/HTML]

[HTML]http://www.brighthub.com/computing/linux/articles/41828.aspx[/HTML]

And one more thing even if the drivers seem to be there unfortunately they are not working....

---

