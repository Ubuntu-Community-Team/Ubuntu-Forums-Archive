---
title: "Spying on HD Access Calls"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by joey on 2007-05-28
Howdy,

Anyone know how to monitor access calls to a HD (e.g. /dev/sda5)? 

I somehow picked a process that runs every 60 to 120 seconds and is accessing the harddisk and I can't find it.  Not in cron, lsof is of no real help, top shows everything sleeping, and ps shows what I expect to find. 

Thanks,

Joey

---

### Post by joey on 2007-05-28
Interestingly enough, I've shutdown as much as I could, including several system services, and yet this odd enttity is still accessing my laptop's hard disk under the low-latency kernel.  My desktop does not suffer from this problem.

---

### Post by joey on 2007-06-04
I found the program I was searching for: blktrace 

Unfortunately it doesn't work with 2.6.22

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/118303](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/118303)

---

### Post by joey on 2007-06-08
At init 3, these are the processes still running that I haven't been able to close.

```

 PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S      0:00 [migration/1]
    6 ?        SN     0:00 [ksoftirqd/1]
    7 ?        S      0:00 [watchdog/1]
    8 ?        S<     0:00 [events/0]
    9 ?        S<     0:00 [events/1]
   10 ?        S<     0:00 [khelper]
   11 ?        S<     0:00 [kthread]
   35 ?        S<     0:00  \_ [kblockd/0]
   36 ?        S<     0:00  \_ [kblockd/1]
   37 ?        S<     0:03  \_ [kacpid]
   38 ?        S<     0:00  \_ [kacpi_notify]
  159 ?        S<     0:00  \_ [kseriod]
  188 ?        S      0:00  \_ [pdflush]
  189 ?        S      0:00  \_ [pdflush]
  190 ?        S<     0:01  \_ [kswapd0]
  191 ?        S<     0:00  \_ [aio/0]
  192 ?        S<     0:00  \_ [aio/1]
 2161 ?        S<     0:00  \_ [ksuspend_usbd]
 2162 ?        S<     0:00  \_ [khubd]
 2187 ?        S<     0:00  \_ [ata/0]
 2188 ?        S<     0:00  \_ [ata/1]
 2189 ?        S<     0:00  \_ [ata_aux]
 2201 ?        S<     0:00  \_ [khpsbpkt]
 2323 ?        S<     0:00  \_ [knodemgrd_0]
 2473 ?        S<     0:05  \_ [kjournald]
 3794 ?        S<     0:00  \_ [kpsmoused]
 3956 ?        S<     0:00  \_ [kmmcd]
 4052 ?        S<     0:00  \_ [ipw3945/0]
 4053 ?        S<     0:00  \_ [ipw3945/1]
 4057 ?        S<     0:00  \_ [ipw3945/0]
 4058 ?        S<     0:00  \_ [ipw3945/1]
 4128 ?        S<     0:00  \_ [hda_codec]
 5875 ?        S<     0:00  \_ [kondemand/0]
 5876 ?        S<     0:00  \_ [kondemand/1]
  821 ?        S      0:00 [kirqd]
 4882 tty1     Ss     0:00 /bin/login --     
 5954 tty1     S      0:00  \_ -bash
 5974 tty1     S      0:00      \_ /bin/bash
11951 tty1     R+     0:00          \_ ps axf
 5978 ?        S<     0:00 [krfcommd]
11942 tty4     Ss+    0:00 /sbin/getty 38400 tty4
11943 tty5     Ss+    0:00 /sbin/getty 38400 tty5
11944 tty2     Ss+    0:00 /sbin/getty 38400 tty2
11945 tty3     Ss+    0:00 /sbin/getty 38400 tty3
11946 tty6     Ss+    0:00 /sbin/getty 38400 tty6
```

---

### Post by IntuitiveNipple on 2007-06-08
If you're using kernel 2.6.13 or later you should use the inotify. You can download the user-space tools from [http://inotify-tools.sourceforge.net/]("http://inotify-tools.sourceforge.net/") and use inotifywait.

---

### Post by 444 on 2007-06-08
So why are you looking for this? I was doing the same thing because I wanted the hard drive to spin down and save power. I found laptop-mode-tools, this limits small hd accesses to once every ten minutes.

---

### Post by joey on 2007-06-08
laptop mode is already turned on so whatever is doing this is overriding laptop-mode.

---

### Post by joey on 2007-06-08
So I've removed and reinstalled laptop mode without change. inotifywait and watch are pretty nifty.  Aside from the console tty activity (for my console) the only thing else it found (effectively doing a -rm /) was a 4-second interval call to /dev/null and long stretches of pcmcia probing. Both of which were around when I was able to get the hard disk still for up to a minute. 

Not sure where to go from here. I unplugged everything I could but it didn't make a difference.

---

