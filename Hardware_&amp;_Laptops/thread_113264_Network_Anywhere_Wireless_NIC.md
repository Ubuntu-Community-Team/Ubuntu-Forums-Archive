---
title: "Network Anywhere Wireless NIC"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by 49819 on 2006-01-06
i NEED HELP i have the NWP11B network card i tried the wrapper thengy and it doesent work! someone please help me

---

### Post by Lambert on 2006-01-06
I show this uses a TI chipset and the acx100 linux driver. If you were trying to use ndiswrapper and the acx100 driver was binding with the device, then there would be a driver conflict.

So first let's find out if acx100 is binding to the device. run this command from terminal and post output.

```
sudo lshw -C network
```
also post output from this command
```
lspci -v
```

In the first command, there will be a line in the section for the wireless device that starts configuration:.....look for driver=  if it says acx_pci then you are using a ti chipset and the acx100 driver is binding to the device. 

You can do 2 things.

1. remove ndiswrapper and try to configure using the acx driver. If it doesn't work look [here]("http://www.houseofcraig.net/acx100_howto.php") for help on configuring and getting to work.
2. If you want to use ndiswrapper then remove the acx driver and then set up and use ndiswrapper again.

```
sudo modprobe -r acx_pci
```

to permanently keep acx_pci from loading add a line to the /etc/modprobe file

```
blacklist acx_pci
```

---

