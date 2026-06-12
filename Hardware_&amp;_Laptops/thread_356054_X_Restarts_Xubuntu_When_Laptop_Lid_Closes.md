---
title: "X Restarts Xubuntu When Laptop Lid Closes"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by Benitez on 2007-02-08
[SIZE="3"]OK everyone, I'm having a bit of a problem here...

I run Xubuntu Edgy Eft on a Dell Latitude C610 laptop.

Every time that I close the laptop lid, I *expect* the laptop to go into Suspend mode. However, the observed behavior is that the X server restarts (i.e., the screen goes to the Xubuntu main login screen as if I had hit the **CTRL-ALT-BACKSPACE** button combination). Effectively, if I want the laptop to go to suspend, I have to use shutdown menu and click on the Suspend option.

I have looked at many threads here for help and have not found anything that can help me.

Also, is there any information that I should post to assist in the debugging of this problem, such as 'dmesg' or 'uname -a' info?

I'll greatly appreciate the help for **epic win!** :lolflag: 

--Benitez[/SIZE]

---

### Post by glaucon on 2007-02-08
Im having this problem too, and have had no luck. :(

---

### Post by Benitez on 2007-02-08
> **glaucon said:**
> Im having this problem too, and have had no luck. :(

[SIZE="3"]OK, the machine I'm using is an old Dell Latitude C610; I believe that the problem itself has to do something with either APM or ACPI. I'm still not sure which, but I was able to find something like that.

Doing more research turns up just that. I haven't been able to narrow it down to more than that...

Glaucon, what is *your* machine model and make? Does it completely restart the X server or just blank it?

Actually, I didn't do as much research on it as I thought.  *[Click here for help.]("http://ubuntuforums.org/showthread.php?p=2127174#post2127174")*

I tried this and it worked. I changed the setting from hibernate to suspend, so it should work either way. Hopefully that will work...
[/SIZE]

---

### Post by marvinthesad on 2007-02-11
Dear Benitez, glaucon,

I hope you don't mind replying although you seem to have found a solution in the thread
[http://ubuntuforums.org/showthread.php?p=2127174#post2127174](http://ubuntuforums.org/showthread.php?p=2127174#post2127174)

I digged in the same problem (Dell Latitude C610) and found that

a.) the X server crashes ( with the ati=radeon driver) when the lid is closed: /var/log/acpid shows that acpid had send a message to the X process

/var/log/Xorg.0.log says:
```
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONDisplayPowerManagementSet(3,0x0)
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(__strtoul_internal+0x3f) [0xb7d7b7df]
3: /usr/bin/X [0x80e5a27]
4: /usr/bin/X(xf86HandlePMEvents+0x3b) [0x80d264b]
5: /usr/bin/X(xf86Wakeup+0x153) [0x80c4e23]
6: /usr/bin/X(WakeupHandler+0x59) [0x808a5c9]
7: /usr/bin/X(WaitForSomething+0x1b9) [0x81944f9]
8: /usr/bin/X(Dispatch+0x82) [0x8086832]
9: /usr/bin/X(main+0x485) [0x806e715]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d638cc]
11: /usr/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting
```

[SIZE="4"]Solution/Hack[/SIZE]: disable power management in X 
(sounds odd, but Xserver doesn't crash and laptop 
goes to sleep/suspend/hibernate or whatever you configured)

For this you just need to add to /etc/X11/xorg.conf:
```

Section "ServerFlags"
                Option "NoPM"   "true"
EndSection

```

b.) I did not manage to get fglrx working (hints to threads?)
c.) The /etc/acpi/* does not need to be touched, when you're using kde-guidance which includes a "power-manager".
Notes:
[LIST=1]
[/LIST] "power-manager" seems to replace klaptopdaemon or kpowersave for KDE

[LIST=1]
[*]"power-manager" within kde-guidance seems to replace klaptopdaemon or kpowersave for KDE, confirmation?
[*]kde-guidance package does not seems to depend on KDE...
[*] can anyone elaborate on how the whole acpi chain seems to work?
[/LIST]
E.g.:
event -> kacpid -> acpid -> (connected clients)

client, e.g. Xserver -> does stuff (e.g. crash)
client, e.g. /usr/lib/hal/hald-addon-acpi -> hald -> dbus ->(connected dbus-clients)

dbus-client: e.g. kde-guidance power-manager -> calls by some means acpi-scripts


I seem to be lost in the jungle of possibilities and can only hope that someone will document the current status of ACPI/events/action/Xserver/desktop-integration or hint me to where this has been done...

Apprecitaion,

Marvin...

---

### Post by Benitez on 2007-02-13
> **marvinthesad said:**
> 
[SIZE="4"]Solution/Hack[/SIZE]: disable power management in X 
(sounds odd, but Xserver doesn't crash and laptop 
goes to sleep/suspend/hibernate or whatever you configured)

For this you just need to add to /etc/X11/xorg.conf:
```

Section "ServerFlags"
                Option "NoPM"   "true"
EndSection

```

b.) I did not manage to get fglrx working (hints to threads?)
c.) The /etc/acpi/* does not need to be touched, when you're using kde-guidance which includes a "power-manager".
Notes:
[LIST=1]
[/LIST] "power-manager" seems to replace klaptopdaemon or kpowersave for KDE

[LIST=1]
[*]"power-manager" within kde-guidance seems to replace klaptopdaemon or kpowersave for KDE, confirmation?
[*]kde-guidance package does not seems to depend on KDE...
[*] can anyone elaborate on how the whole acpi chain seems to work?
[/LIST]
E.g.:
event -> kacpid -> acpid -> (connected clients)

client, e.g. Xserver -> does stuff (e.g. crash)
client, e.g. /usr/lib/hal/hald-addon-acpi -> hald -> dbus ->(connected dbus-clients)

dbus-client: e.g. kde-guidance power-manager -> calls by some means acpi-scripts


I seem to be lost in the jungle of possibilities and can only hope that someone will document the current status of ACPI/events/action/Xserver/desktop-integration or hint me to where this has been done...

Apprecitaion,

Marvin...

[SIZE="3"]Marvin:

Firstly, I'd like to thank you for your contribution to the solution. You get massive epic win!

Secondly, the solution I posted happened to work only *once* for my laptop. I only tested it once and then posted on the solution, (wrongly) assuming that it work for others. Your posted solution has worked perfectly. I kept the modified lidbtn file as is, but I may test it by changing it back to the unmodified version.

As for the flgrx part, I have not decided to get it working, so I don't know if that will work. Also, I don't know who else would know of ACPI documentation and all that. Possibly if you join either a documentation team and find out who's doing what with that or just join the mailing list at least and send a letter.

Anyway, thanks for the post. Cheers. [/SIZE]

---

