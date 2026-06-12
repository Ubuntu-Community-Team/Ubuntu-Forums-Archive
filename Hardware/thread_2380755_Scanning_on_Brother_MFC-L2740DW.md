---
title: "Scanning on Brother MFC-L2740DW"
date: 2017-12-21
forum: Hardware
---

### Post by penman131 on 2017-12-21
Recently I changed the address of my local lan (192.168.xxx.xxx), and now, while I can still print ok, my scanning software cannot find the printer.
Could someone let me know where I have to look to change the scanner parameters in order to restore that function.
TNX

---

### Post by plucky on 2017-12-24
> **penman131 said:**
> Recently I changed the address of my local lan (192.168.xxx.xxx), and now, while I can still print ok, my scanning software cannot find the printer.
Could someone let me know where I have to look to change the scanner parameters in order to restore that function.
TNX

From [Here](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

> Step 5. Setting for your network scanner
    ***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models), brsaneconfig3 (for brscan3 models) or brsaneconfig4 (for brscan4 models) accordingly. 
    5-1. Add network scanner entry

        Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
        Example 

    5-2. Confirm network scanner entry

        Command  :  brsaneconfig2  -q  |  grep  (name  of  your  device) 

Use the version of brsaneconfig installed on your system.

Good Luck

---

### Post by gifford on 2017-12-25
Settings for address can be changed at usr/local/brother/sane and open brsanenetdevice3.cfg. Just change the address and save the file, should be able to scan without issue.

---

### Post by kurt18947 on 2017-12-25
What Ubuntu version? I'm having no luck getting either a Brother MFC-6490CW or Samsung ML-2870 (I think) recognized in 17.10. I've tried all the fixes I can find and no luck so far. Both devices work without issue in 16.04.

---

### Post by penman131 on 2017-12-28
> **kurt18947 said:**
> What Ubuntu version? I'm having no luck getting either a Brother MFC-6490CW or Samsung ML-2870 (I think) recognized in 17.10. I've tried all the fixes I can find and no luck so far. Both devices work without issue in 16.04.

16.04

---

### Post by penman131 on 2017-12-28
> **gifford said:**
> Settings for address can be changed at usr/local/brother/sane and open brsanenetdevice3.cfg. Just change the address and save the file, should be able to scan without issue.

No such directory as /usr/local/brother (/sane)

P

---

### Post by penman131 on 2017-12-29
> **gifford said:**
> Settings for address can be changed at usr/local/brother/sane and open brsanenetdevice3.cfg. Just change the address and save the file, should be able to scan without issue.

I managed to fix the issue. The file in question was: /etc/opt/brother/scanner/brscan4/brsanenetdevice4.cfg  It had the old IP in it, just waiting to be changed !

Thanks for the clue Gifford.

P

---

### Post by him610 on 2018-01-11
Thanks to all who contributed to the solution. I recently reconfigured my network, and as a result, had to reconfigure the printers and scanner on several machines. This thread helped immensely; I probably would never have located the proper directory. My *brsanenetdevice4.cfg* was empty so I ran *brsaneconfig4** in order to populate the brsanenetdevice4.cfg file.
Here is a list of the folder contents where the executable and configuration file reside...
```
hugh@e7200:/opt/brother/scanner/brscan4$ ll
total 52
drwxr-xr-x 4 root root  4096 Aug  6  2016 ./
drwxr-xr-x 4 root root  4096 Aug  6  2016 ../
-rw-r--r-- 1 root root   936 Apr 14  2015 Brsane4.ini
-rwxr-xr-x 1 root root 24040 Apr 14  2015 brsaneconfig4*
-rw-rw-rw- 1 root root    64 Jan 11 20:28 brsanenetdevice4.cfg
drwxr-xr-x 3 root root  4096 Aug  6  2016 doc/
drwxr-xr-x 2 root root  4096 Aug  6  2016 models4/
-rwxr-xr-x 1 root root   388 Apr 14  2015 setupSaneScan4*
 
```

---

