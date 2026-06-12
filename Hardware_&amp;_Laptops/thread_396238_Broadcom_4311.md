---
title: "Broadcom 4311"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by bkeithly on 2007-03-29
Help!!!

Ok several times I have to reinstall ndiswrapper because updates to my OS have wiped out my wifi connectivity. 

We it just happened again.  

Normally all I have to do is reinstall ndiswrapper and I am good to go.

But this time, that process doesn't work.  I figured out why, they system doesn't even see the Broadcom card anymore. 

Lspci shows no trace of the card.  

I usually have to pass boot parameters to the system to get the card working.  Things like noapic, nolapic, pci=noacip, pci=assign-busses etc. etc. etc....

No combination seems to work.  Well I take that back, I get a winning combo of boot parameters and I can see the card after booting.  I get Ndis working correctly and reboot, and bam the card is gone again.   I repeated this process countless times last night, but after ever reboot the card was no longer detected...

This has never happened... I could REALLY use some advice on this.  I do not need help on getting the wifi part working.

I just need to get they system to see the broadcom wifi card.

Thanks

---

### Post by nachotronics on 2007-03-29
Hello
I assume you first blocked the broadcom kernel module from running by typing this:
```
sudo gedit /etc/modprobe.d/blacklist
```
and then adding this line at the end of the file:
```
blacklist bcm43xx
```

You should have uninstalled the ndiswrapper version that comes with ubuntu(the one from the repositories) and downloaded and installed the latest version from [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Having the latest version installed you set up the driver by doing:
```
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
```
I used the one I'm attaching here.

And then you make sure it installed correctly:
```
sudo ndiswrapper -l
```

Then load the module, at this point the wifi light should turn on
```
sudo modprobe ndiswrapper
```

Then set up ndiswrapper module to load on startup:
```
sudo ndiswrapper -m
sudo gedit /etc/modules
```
And add the following line at the endo of that file:
```
ndiswrapper
```

Hope this helps :wink:

---

### Post by Derspankster on 2007-03-30
This kind of thing is what makes wireless such a joke in Ubuntu.

---

### Post by srt4play on 2007-03-30
Do people even read threads before responding anymore?  He said he didn't need help with getting ndiswrapper going, his computer is not physically seeing the card anymore. 

Now to OP:  You can get the computer to see the wireless card when adding certain kernel boot parameters.  Did you add those to /boot/grub/menu.lst ?

---

### Post by Quasaur on 2007-03-30
boot parameters? what boot parameters?

---

### Post by srt4play on 2007-03-30
> **Quasaur said:**
> boot parameters? what boot parameters?

[QUOTE=bkeithly]I usually have to pass boot parameters to the system to get the card working. Things like noapic, nolapic, pci=noacip, pci=assign-busses etc. etc. etc....[/QUOTE]

.

---

### Post by p252 on 2007-03-30
> **Derspankster said:**
> This kind of thing is what makes wireless such a joke in Ubuntu.

Wireless does take some tweaking, but, it's the same with most distros. Ubuntu has been the easiest I've tried ( i've tried quite a few).

---

### Post by nachotronics on 2007-03-31
> **srt4play said:**
> Do people even read threads before responding anymore?  He said he didn't need help with getting ndiswrapper going, his computer is not physically seeing the card anymore.

:-s  The reason why i posted the ndiswrapper part was because i had a simillar problem with the broadcom 4311 and wanted to make sure he didn't. I read his post i was just trying to help, thats all.

---

### Post by bkeithly on 2007-03-31
THanks for the replys


ok

I can get ndis to work if the laptop sees the card.   WHich it appears to be doing about 10% of the time.


Recently if I boot with nolapic I get the card to work.   About 30% it hangs during boot.  THen the rest of the time it boots and doesn't see the card....

This just started happening.  Makes no sense...

---

### Post by Eigenwert on 2007-04-08
I'm having this same problem and still have not found a solution. I edited my /boot/grub/menu.lst to include ```
noapic nolapic
``` at the end of the "kernel" line for the kernel I want to boot. Immediately after I rebooted and typed in ```
ndiswrapper -l
``` which resulted in a message saying the driver was installed and the hardware was available (until this point, there had not been the "hardware available" message.) I did a reboot again, just to check and see if I had indeed solved my problem. Unfortunately ndiswrapper is not seeing the hardware again. The lspci command also shows no wireless card.

I have a Broadcom 4311 card in an HP Pavilion dv6000 laptop. 

I have had this machine since December, and after the initial install and setup of the Broadcom card, wireless has worked without any problems up until 2 days ago. And now I have no clue what is going one.

Any help would be greatly appreciated.

Thnx,

EW

---

