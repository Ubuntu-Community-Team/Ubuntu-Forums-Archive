---
title: "System randomly hangs! Help!"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by simianMiscreant on 2005-06-03
Every so often my system just totally freezes - no mouse respose, no keyboard, the screen is frozen completely. I have to hold down the power button until it turns off. Here's some output from /var/log/messages from when the system crashed (i think). Please help?
```
Jun  2 19:41:33 localhost kernel: NET: Registered protocol family 10
Jun  2 19:41:33 localhost kernel: Disabled Privacy Extensions on device c0313ce0(lo)
Jun  2 19:41:33 localhost kernel: IPv6 over IPv4 tunneling driver
Jun  2 19:41:34 localhost kernel: ACPI: AC Adapter [AC] (on-line)
Jun  2 19:41:34 localhost kernel: ACPI: Lid Switch [LID]
Jun  2 19:41:34 localhost kernel: ACPI: Power Button (CM) [PBTN]
Jun  2 19:41:34 localhost kernel: ACPI: Sleep Button (CM) [SBTN]
Jun  2 19:41:35 localhost kernel: ACPI: Battery Slot [BAT0] (battery present)
Jun  2 19:41:35 localhost kernel: ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jun  2 19:41:35 localhost kernel: apm: BIOS not found.
Jun  2 19:41:36 localhost kernel: cs: IO port probe 0x0100-0x04ff: clean.
Jun  2 19:41:36 localhost kernel: cs: IO port probe 0x0800-0x08ff: clean.
Jun  2 19:41:36 localhost kernel: cs: IO port probe 0x0c00-0x0cff: clean.
Jun  2 19:41:36 localhost kernel: cs: IO port probe 0x0a00-0x0aff: clean.
Jun  2 19:41:45 localhost gconfd (brady-7768): starting (version 2.10.0), pid 7768 user 'brady'
Jun  2 19:41:45 localhost gconfd (brady-7768): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  2 19:41:45 localhost gconfd (brady-7768): Resolved address "xml:readwrite:/home/brady/.gconf" to a writable configuration source at position 1
Jun  2 19:41:45 localhost gconfd (brady-7768): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  2 19:41:52 localhost gconfd (brady-7768): Resolved address "xml:readwrite:/home/brady/.gconf" to a writable configuration source at position 0
Jun  2 19:43:45 localhost gconfd (root-7930): starting (version 2.10.0), pid 7930 user 'root'
Jun  2 19:43:45 localhost gconfd (root-7930): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  2 19:43:45 localhost gconfd (root-7930): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  2 19:43:45 localhost gconfd (root-7930): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  2 19:44:15 localhost gconfd (root-7930): SIGHUP received, reloading all databases
Jun  2 19:44:15 localhost gconfd (root-7930): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  2 19:44:15 localhost gconfd (root-7930): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  2 19:44:15 localhost gconfd (root-7930): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  2 19:46:47 localhost kernel: cdrom: open failed.
Jun  2 19:46:47 localhost kernel: cdrom: open failed.
```

---

### Post by simianMiscreant on 2005-06-03
update - it has to do with an error message i get upon using synaptic. when i click 'ok' on the error box, i freeze. this is as much as i could trace it for now...i'll post the actual error message in a sec.

---

### Post by simianMiscreant on 2005-06-03
```
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```

---

### Post by CSUbuntu on 2005-06-03
I've seen the same thing, and seen it often

The few times that I was able to get into the system by using ssh form another machine, it was X.org that ate up all the resouces.

There is something SERIOUSLY wrong with the X.org build in Hoary. 

This exact same machine never had any problems under Warty

---

### Post by jejones3141 on 2005-06-03
Is it the X.Org build, or is it the nvidia driver? See the thread "Screen frozen, but mouse pointer moves" over in the nvidia forum's Linux area at [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by simianMiscreant on 2005-06-03
But I had Hoary before and it worked FINE, this error only happened post-format.  :| someone please help! It just seems that certain things set it off - it ALWAYS freezes after clicking "ok" in that synaptic error box, but sometimes freezes other places too.

---

### Post by simianMiscreant on 2005-06-03
so i had my friend ssh in while i crashed it, and the crash kills everything - no ping response, no ssh connection, nothing. my guess is an ati/x.org problem at the driver level (but before i formatted i had no problems and hardware acceleration with fglrx!  :neutral: ). does anyone know what to do? oh please oh please? i have a radeon 9800 mobility with 256mb vram. oh, and one more thing - i had to ship my system to dell, and they replaced the vid card, mobo, and screen - but it's the same vid card as before, just a new one. everything worked fine. then i formatted my ubuntu partition, and now i have the problem.

---

### Post by simianMiscreant on 2005-06-06
My fix is here:

[http://ubuntuforums.org/showthread.php?p=201964](http://ubuntuforums.org/showthread.php?p=201964)

---

