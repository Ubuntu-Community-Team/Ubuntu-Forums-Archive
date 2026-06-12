---
title: "BlueTooth Broadcom hardware - no connection"
date: 2015-10-26
forum: Hardware
---

### Post by nicolasdiogo on 2015-10-26
hello guys,


I have a nice Lenovo X1 laptop that works perfectly except for the BlueTooth.
My headset works fine on Android (receiving & sending sound) but it will not work at all with my laptiop.

Every time I tried adding this headset it says that i had been added but it failed to pair.


while researching for a solution I have collected some info:
```

$ dmesg | egrep -i 'blue|firm'
[150204.059763] usb 1-4: device firmware changed
[155163.515189] usb 1-4: device firmware changed
[157859.276381] Bluetooth: hci0: BCM: chip id 63
[157859.277300] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[157859.278149] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e6.hcd failed with error -2
[157859.278157] Bluetooth: hci0: BCM: Patch brcm/**BCM20702A1**-0a5c-21e6.hcd not found
[158085.340942] Bluetooth: hci0: BCM: chip id 63
[158085.341845] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[158085.341883] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e6.hcd failed with error -2
[158085.341890] Bluetooth: hci0: BCM: Patch **brcm/BCM20702A1-0a5c-21e6.hcd not found**

```


I have come across this discussion:
[http://askubuntu.com/questions/547552/bluetooth-not-working-on-14-10-with-bcm43142](http://askubuntu.com/questions/547552/bluetooth-not-working-on-14-10-with-bcm43142)

and I have also found some windows binaries as discussed on the above:
[http://drivers.softpedia.com/dyn-search.php?search_term=bcm2070](http://drivers.softpedia.com/dyn-search.php?search_term=bcm2070)

While searching the DEB packages, I could not find anything that would appear to support this Broadcom chipset.


Would it be possible to have some guidance on the steps to have this bluetooth connection?


Thanks,

---

### Post by nicolasdiogo on 2015-10-29
[bumping]

perhaps Friday is a good day to have this topic revised?!

    ;-)

however, it looks like we have to extract the necessary files from the Windows Binaries:
[https://bugzilla.redhat.com/show_bug.cgi?id=1264153](https://bugzilla.redhat.com/show_bug.cgi?id=1264153)

These days ... companies should provide Linux support as default
Or, I am too positive!


Thanks

---

### Post by jeremy31 on 2015-10-30
Found you the file.
```
wget https://www.dropbox.com/s/p6h7ho21fct2pzb/fw-0a5c_21e6.hcd
sudo cp fw-0a5c_21e6.hcd /lib/firmware/brcm/BCM20702A1-0a5c-21e6.hcd
```

Shut down and cold boot the computer

---

### Post by nicolasdiogo on 2015-11-02
thanks,


could you let me know where you got this file from?

---

### Post by jeremy31 on 2015-11-02
It was an attachment on this bug report
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400)

---

### Post by nicolasdiogo on 2015-11-14
Thanks

I believe the file that you linked is the correct one.

Now I find that Ubuntu does not send any sound the headphones.


Perhaps I try fixing this another day.

---

