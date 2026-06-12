---
title: "Finding MAC address of Bluetooth keyboard ??"
date: 2016-03-27
forum: Hardware
---

### Post by Keith_Beef on 2016-03-27
I have a little BT keyboard that I want to use for a few experiments, and for them I will need to know its MAC address.

So far, I've been trying hcitool and hidd but I get no results, even when running as root.

```
$ sudo hidd --search
Searching ...
        No devices in range or visible

$ sudo hcitool scan
Scanning ...
```

Yet I know that the BT keyboard is connected, because I'm using it to type those commands. 

Any ideas?

---

### Post by jeremy31 on 2016-03-27
You can use bluetooth settings GUI and click on the keyboard name on the left side of the panel and it should show you the MAC
Or you can do it in terminal
```
hcitool con
```

This may result in multiple devices but it won't show the name, if you have multiple results use
```
hcitool name {BT MAC}
```
And it will display the device name

---

### Post by Keith_Beef on 2016-03-28
> **jeremy31 said:**
> 
```
hcitool con
```

Thanks, that got it for me.

---

