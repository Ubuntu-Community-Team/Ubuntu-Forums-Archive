---
title: "How to disable hardware devices in 9.04"
date: 2009-10-08
forum: Hardware
---

### Post by Apepa on 2009-10-08
Hello everyone. I've been experimenting with Linux for years now, but have never really gotten into it. My primary OS is Windows (Vista) and having been using the Windows interface from a very early age, I'm very used to the Windows GUI, and when it comes to command line stuff I can only really do basic navigation and stuff like ipconfig.

Anyway, I've got a problem. I have two Wireless network cards - one is an 802.11**g** PCI card in the back of my computer, the other is an 802.11**n** USB device. The USB card is far superior to the older PCI device, and in Windows I always keep the PCI card disabled except when I occasionally borrow the other one to friends. The reason I keep it disabled is that my router doesn't like having two connections with the same PC at the same time, and the PCI card's signal is weak and patchy.

But I can't seem to do the same thing in Ubuntu. I've had a look at the settings options under Network Tools and Edit Connections, but the actual devices themselves aren't listed there, and there's no option to disable them anywhere. In addition, Ubuntu keeps using the PCI card as the default connection - I can't find a way of changing this, and I can't even tell it to disconnect. So now I have a slow, patchy connection because I can't choose my own settings.

Is there a way of sorting this out, preferably without writing an essay on Computer Science in the Terminal? Maybe using nice, freindly GUI tools?

Thanks for reading, and please answer if you can!

EDIT: I also have an onboard graphics card and a PCIe one, and it'd be handy to know how to shut one of those off occasionally as well.

---

### Post by jeremyswalker on 2009-10-08
I'm not sure how to disable a network card via GUI, but you can use the command 'ifconfig' to do it. However, you need to know what your system knows the interface as.

You can list all the network interfaces like this:
```
ifconfig
```

Once you figure out which interface you want to disable (i.e. wlan0), you can disable it like this:
```
sudo ifconfig wlan0 down
```
Replace 'wlan0' with the interface you are disabling.

This may need to be added to one of the startup scripts for it to be permanent.

---

### Post by Apepa on 2009-10-08
Thanks for the reply. I tried the command you suggested, and it did disconnect the PCI card, but even though the USB device is connected to the network, the system is still trying to use the PCI as the main card - I get four empty bars on my network panel (the USB card should be at 100%), and I get a "connection could not be established" message if I try connecting to a website.

---

### Post by jeremyswalker on 2009-10-08
Are you using a laptop? Or is it a desktop? Have you looked through your BIOS to see if you could disable it there? If not, it may be possible to blacklist the module if it uses a different one than your USB card.

Enter the following into a terminal:
```
lspci -v
```
In the output, try to locate your PCI wireless card. Note the entry after "Kernel driver in use:" or "Kernel modules:" (i.e. "ath_pci","rt61pci", etc). Try the following (replacing <module> with the module name from the previous step:
```
sudo modprobe -r <module>
```
This should disable your PCI wireless card. You should now only be able to connect with your USB card. If your USB card does not appear anymore, then this will not work. However, if it does then add the name of the module in the previous step to the end of /etc/modprobe.d/blacklist.conf. This will make it permanent. If it doesn't work, then:
```
sudo modprobe <module>
```

---

### Post by Apepa on 2009-10-09
Thank You very much - that worked! I assume that if I want to re-enable it I can just delete the entry from blacklist.conf?

> Have you looked through your BIOS to see if you could disable it there?

No, I haven't. It never even occured to me, but I prefer having control over it in the OS so I don't have to reboot to turn it on and off (which is also why I don't just physically remove the card from the computer).

> Are you using a laptop? Or is it a desktop

A desktop.

---

