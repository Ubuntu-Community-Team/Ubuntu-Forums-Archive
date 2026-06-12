---
title: "MSI 1660 ti OC Fans turn off and won't spin"
date: 2020-10-09
forum: Hardware
---

### Post by undeadbobop on 2020-10-09
Card:MSI 6gb Nvidia Geforce GTX1660 ti OC
Drivers: [COLOR=#000000][FONT=&quot]450.80.02[/FONT][/COLOR]
OS: Ubuntu 20.04

After Grub2 starts the video cards fans stop, they won't turn on at all, Nvidia controller won't even recognize that there is fans, attempting to turn it on manually with the command line it didn't work, the GUI lacks all settings and GWE doesn't detect the fan either.
Now with windows I have to use MSI afterburner to restart the fans otherwise it doesn't start up. But with ubuntu there is no way, neither the open source drivers nor the proprietary drivers will pick it up. But if I avoid grub2, with windows the fans spin just fine, but I don't know of any way to skip grub2 with ubuntu, and I am not sure if that is 100% the issue.

---

### Post by CelticWarrior on 2020-10-09
Please update UEFI before anything else.

---

### Post by undeadbobop on 2020-10-10
Did that before linux install.

---

### Post by CelticWarrior on 2020-10-10
So, if I understand correctly, the problem doesn't happen if you boot Windows directly? Only when you boot Ubuntu or Windows from the Grub menu?

---

### Post by undeadbobop on 2020-10-10
It happens when it hits grub, but I double checked what was going on anytime it hits a bootloader it begins to turn off but because my os's are on a ssd it boots so quickly with the windows bootloader it doesn't look like it shuts off, then starts up as soon as it hits windows login screen because of drivers load. I had to test this in safe mode to see that it is on both bootloaders. But my issue is the fans never restart in ubuntu and when attempting to turn on manual control and set a fan speed percentage it doesn't even recognize the fans exists. These issues more then likely stem from msi frozr fan control that allows you to run the gpu without fan spin but this is supposed to be for lower temperatures only I see my video card hitting 70c with 0 fan spin. Gwe is a overclock tool for linux that is a alternative to msi afterburner it has fan control options that also doesn't seem to be working. I think it's the driver the more I look at the problem it doesn't include support for the cooler from the looks of it. Sorry I was looking for a solution that probably doesn't exist.

---

### Post by undeadbobop on 2020-10-10
Alright well I found a solution it involves enabling coolbits which nvidia and msi don't recormend because how could you possibly know what percentage your fan should be running at. For anyone having same issue guide here:
[https://www.techticity.com/howto/how-to-control-nvidia-graphics-card-fan-speed-in-linux/](https://www.techticity.com/howto/how-to-control-nvidia-graphics-card-fan-speed-in-linux/)
It is needed for most Frozr MSI models, and I found that a lot of people are having the same issue and everyone is telling them their GPU fans are dead even though they are not. You can also damage your card from what I am reading if you tinker around too much with coolbits, not sure how true that is. But you could also damage your card if it runs too hot so there is that too.
So far even with fans off though it runs cooler than in windows, so its unlikely you will thermal throttling the card, unless your doing something with high graphics which with a card like a 1660ti yeah... You probably are.
If anyone else runs into this problem and reads this, the number you should set coolbits to from what I keep reading is 4 instead of 28, and you have to restart your PC before you can tweak fan speeds in nvidia-config.
I read somewhere you void warrenty by enabling coolbits as well, either from MSI or NVIDIA, but I void warrenty day 1 and everyone with a HP laptop with linux installed on it does too. They are pointless and almost always voided on day 1 in some underline way but that is a rant for somewhere else.

Once you get fans spinning I recormend using GreenWithEnvy to handle fan speed controlling based off temp, its custom option seems to work pretty well.

---

### Post by Yellow Pasque on 2020-10-11
> **undeadbobop said:**
> I read somewhere you void warranty by enabling coolbits as well, either from MSI or NVIDIA

I read somewhere that the Queen of England is a space alien...
Seriously though, you should read MSI's policy. They allow overclocking. Even if they didn't, there's no alarm built into the card if you enable Coolbits and/or OC it. Using a value of '4' is a good idea if you don't want to mess with OC'ing. If you want to be warranty safe, don't flash the GPU BIOS or physically modify your card (though some manufacturers like EVGA allow using a different cooler as long as the old one is reattached before sending it in for an RMA).

---

