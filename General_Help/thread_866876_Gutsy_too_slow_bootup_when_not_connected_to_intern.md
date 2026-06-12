---
title: "Gutsy too slow bootup when not connected to internet"
date: 2008-07-22
forum: General Help
---

### Post by rajreddy on 2008-07-22
Hi Everyone!
I am new to linux, and i have just installed ubuntu gutsy on my dell inspiron 1525 laptop with intel centrino processor(2.4 GHZ) and 4 GB RAM.

I got a problem with  the booting process as its taking too much of time, about 3 mins to reach the desktop though its staying in the graphics mode ,and after reaching the desktop its again taking a min around to start the terminal,and all this is happening only when  i am not connected to the internet.

Everything is going fine when the LAN cable connected.

Could somebody please help me out?

---

### Post by plucky on 2008-07-22
> **rajreddy said:**
> Hi Everyone!
I am new to linux, and i have just installed ubuntu gutsy on my dell inspiron 1525 laptop with intel centrino processor(2.4 GHZ) and 4 GB RAM.

I got a problem with  the booting process as its taking too much of time, about 3 mins to reach the desktop though its staying in the graphics mode ,and after reaching the desktop its again taking a min around to start the terminal,and all this is happening only when  i am not connected to the internet.

Everything is going fine when the LAN cable connected.

Could somebody please help me out?


Do you normally use the wireless interface to connect to the internet?

If yes, then try disabling your wired connection **System > Administration > Network** and select **Unlock**.Input password and select eth0 and un-tick the interface.

Because the interface is enabled,it is trying to connect and failing,which is why your system takes so long to boot.


Good Luck

---

### Post by rajreddy on 2008-07-23
hi! thank you for the reply, but i have never connected the internet through wireless, i have not even activated it!i only have the wired connection all the time.and i have configured it with static ip.

further help is thanked in advance.

---

### Post by llebegue on 2008-07-23
Does your computer attempt to set date and time through internet at startup (NTP ptotocol) ? 

```

ls /etc/rc2.d/ | grep ntp

```

should show you "S50ntp" if ntpd is started as a service at runlevel 2 (runlevel 2 scripts are in /etc/rc2.d ).

If the answer is yes then perhaps it fails at finding a synchronization server and takes much time realizing this.

In that case you may want to turn it off

```

sudo mv /etc/rc2.d/S50ntp $HOME

```

in order to have it back running you can copy back the file to its original directory

```

sudo mv $HOME/S50ntp /etc/rc2.d

```

Alternately you can also enable/disable the service in GNOME through System->Administration->Services by checking or un-checking "Clock synchronization service"

---

### Post by rajreddy on 2008-07-24
Hi, 

Thank you very much.
I have checked my time and date settings and it was not internet synchronized but it is set to manual. when i tried to change it to internet synchronization it asked me whether to install ntp services! 

later i checked the rc2.d in which there is no ntp.

what else could be the problem? 

thanks in advance!

---

