---
title: "USB scanner detected but not working !"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by AN@S on 2008-01-14
Hi, 
I have a USB scanner (RHOMBUS RH-1200 LS) on Ubuntu Gusty 64-bit. The scanner is detected by Ubuntu:


```
anas@anas-desktop:~$ lsusb 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 07b3:0413 Plustek, Inc. 
Bus 002 Device 002: ID 03f0:0c17 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0458:0066 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000 
```

```
anas@anas-desktop:~$ scanimage -L
device `gt68xx:libusb:002:003' is a Plustek OpticSlim 1200 flatbed scanner

```

But:

```
anas@anas-desktop:~$ scanimage -T -d
[gt68xx] Couldn't open firmware file (`/usr/share/sane/gt68xx/cism216.fw'): No such file or directory
scanimage: open of device gt68xx:libusb:002:003 failed: Invalid argument
```

and:

```
anas@anas-desktop:~$ xsane 
```

I got a GUI error message:

Failed to open device 'gt68xx:libusb:002:003': Invalid argument.

Any idea?

:confused:

---

### Post by krimson on 2008-01-14
i have a Plustek Optislim M12 scanner that wouldnt work, and was giving me the exact same error about the exact same file...

i went here:   [http://gkall.hobby.nl/gt6816-07b3-0412.html](http://gkall.hobby.nl/gt6816-07b3-0412.html)

downloaded the .fw file (right-click, save as) and then put it in the right folder, and Instantly the scanner started working with xsane (gui and command line)

hope this helps!

---

### Post by AN@S on 2008-01-15
> **krimson said:**
> i have a Plustek Optislim M12 scanner that wouldnt work, and was giving me the exact same error about the exact same file...

i went here:   [http://gkall.hobby.nl/gt6816-07b3-0412.html](http://gkall.hobby.nl/gt6816-07b3-0412.html)

downloaded the .fw file (right-click, save as) and then put it in the right folder, and Instantly the scanner started working with xsane (gui and command line)

hope this helps!

Thanks krimson, I've downloaded the file and put it in the right folder but now I receive another error:

```

[gt68xx] sane_open: power control failure: check power plug!
scanimage: open of device gt68xx:libusb:002:007 failed: Error during device I/O

```

I don't know what this is about? The error message claims that there's a problem with the power plug !!! The scanner doesn't have a separate power plug it takes power from the USB plug, is that a problem with Linux? It works fine with Windows. The USB is plugged and I have the green led on indicating that the scanner is powered and ready.

That's really strange :confused:

---

### Post by pigphish on 2008-05-06
worked perfectly for me in hardy 8.04.

thanks!

---

