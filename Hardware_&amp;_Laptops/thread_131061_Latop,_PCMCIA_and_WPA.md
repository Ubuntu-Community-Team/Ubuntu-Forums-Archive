---
title: "Latop, PCMCIA and WPA"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by Turbo Donkey on 2006-02-15
I had the problem with subordination, adding the line pci=assign-busses into the menu.lst file sorted that out...

Now...

I have got the wpa supplicant working when I run the command:

wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd

But this only works after boot, and I have to type the command into the root console...

This is causing a very long boot time waiting for the networking to time out during boot and fail...

How can I incorperate my setup into the boot process so that wlan0 comes up during boot instead of timing out and failing?

---

### Post by slavik on 2006-02-16
I think that you can put that into a script into the /etc/rc.d directory. don't quote me on that.

---

### Post by eylisian on 2006-02-16
I would reference ndiswrapper in /etc/modules and then add something like this to my /etc/network/interfaces file

    iface wlan0 inet dhcp
    pre-up /usr/local/sbin/name-of-script-for-up
    post-down /usr/local/sbin/name-of-script-for-down

milage may vary =) good luck!

---

### Post by Turbo Donkey on 2006-02-17
Thanks for the reply, I understand exactly what you are describing but lack the knowledge to follow it through, does the script for up / down have to have a specific file extension etc? or can it just be a plain text file with the commands line by line?

And I'm assuming the command for up would be

wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw

or would it be

ifconfig wlan0 up
wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw

Sorry to be a pest!

---

