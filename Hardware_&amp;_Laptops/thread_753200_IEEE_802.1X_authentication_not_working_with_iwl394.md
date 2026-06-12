---
title: "IEEE 802.1X authentication not working with iwl3945"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by DoDoENT on 2008-04-12
Hello everyone!

I've installed ubuntu hardy beta, and I'm very happy with it. Everything works better than did on gutsy (especially my ati mobility radeon graphic card :popcorn: ). But there is one little problem regarding wireless LAN card. On gutsy, I used to have ipw3945 driver and it always worked correctly. Now, hardy installed iwl3945 driver, and while using this driver, wpa_supplicant is not able to authenticate me on 801.1X wireless network on my university. Is this to be solved before hardy final release deadline, or should I try installing ipw3945 driver on my hardy?

EDIT: Is it possible to install ipw3945 on hardy? I've seen some threads that claim that ipw3945 is not working with kernel 2.6.24. Is this true?

EDIT2: OK, there is another thread about this topic. Looks like it is a kernel bug. See [http://ubuntuforums.org/showthread.php?p=4709879#post4709879](http://ubuntuforums.org/showthread.php?p=4709879#post4709879)

---

### Post by Yako on 2008-05-11
I got ipw3945 to work on 2.6.24.

1. Download ipw3945 microcode ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /lib/firmware/(`uname -r`)/
2. Download ipw3945 regulatory daemon ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /sbin/
3. Download ipw3945 source ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net))
4. Apply patch from [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)
5. Make & make install
6. Add these lines to /etc/modprobe.d/ipw3945 (Creating the file if it doesn’t exist)

install ipw3945 /sbin/modprobe –ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d –quiet
remove ipw3945 /sbin/ipw3945d –kill ; /sbin/modprobe -r –ignore-remove ipw3945

7. modprobe ipw3945
8. blacklist iwl3945 (put ipw3945 into /etc/modprobe.d/blacklist)

And voila! ipw3945 on linux 2.6.24!

---

### Post by DoDoENT on 2008-05-11
> **Yako said:**
> I got ipw3945 to work on 2.6.24.

1. Download ipw3945 microcode ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /lib/firmware/(`uname -r`)/
2. Download ipw3945 regulatory daemon ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /sbin/
3. Download ipw3945 source ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net))
4. Apply patch from [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)
5. Make & make install
6. Add these lines to /etc/modprobe.d/ipw3945 (Creating the file if it doesn’t exist)

install ipw3945 /sbin/modprobe –ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d –quiet
remove ipw3945 /sbin/ipw3945d –kill ; /sbin/modprobe -r –ignore-remove ipw3945

7. modprobe ipw3945
8. blacklist iwl3945 (put ipw3945 into /etc/modprobe.d/blacklist)

And voila! ipw3945 on linux 2.6.24!

Yep! I've found the same patch on Wednesday. At first I had problems with compiling the ieee80211 subsystem, but I modified a source code a bit, and now it works flawlessly. I've uploaded both the patched ipw3945, patched ieee80211 and ipw3945d to [http://www.box.net/shared/qk7eiwvswo](http://www.box.net/shared/qk7eiwvswo) so it won't be difficult to find and download it.

But, network manager has some difficulties with ipw3945. Although on my university it worked perfectly (both connecting and authenticating), in my home WLAN (and other open WLANs) it doesn't get the IP from DHCP, actually it doesn't recognize that dhclient got the IP. So while connecting, I have to manually issue "sudo dhclient wlan0" to get IP. After 2 mins, network manager concludes that "wlan is not working" and my IP is lost again. After that, I have to re-issue the same command in the console and convince the firefox that I'm actually online (by unticking the file->work offline checkbox).

On the other hand, scan sensitvity of the ipw3945 is much higher than the one of iwl3945, so I finally again can connect to the internet via my neighbour's WLAN (don't tell him :-\").

---

