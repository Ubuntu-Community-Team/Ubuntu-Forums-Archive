---
title: "ubuntu-22.04 on desktop: more than 1000 error messages on startup"
date: 2024-08-01
forum: Hardware
---

### Post by dieter-erich on 2024-08-01
My laptop runs ubuntu-22.04 and sometimes has some glitches, which I believe has to do with hardware problems. On startup I see a long list of errors and I am wondering what they mean. When I run 'cat syslog|grep -b rror|grep -b Aug' (on startup on August 1st) I see more than 1000 such error messages. How can I find out what all this means? I refrain from posting this long list and rather wait to learn here what I should do! Thanx

---

### Post by currentshaft on 2024-08-01
how

---

### Post by dieter-erich on 2024-08-01
Sorry, but should I post the more than 1000 errors?

---

### Post by ajgreeny on 2024-08-01
No, not all of them, but come on; as currentshaft says, how do you expect to get any useful information from us when you've told us absolutely nothing.

Are there any similarities between these errors or are they all apparently completely different, and are they errors or just warnings? Many users see warnings at boot time and assume they are errors that mean they can not use their system safely which may not be the situation.

So show us some of these errors you get and we will do our best to suggest where to go from here.

---

### Post by dieter-erich on 2024-08-03
Hi, sorry for the fuzz! There seems to be a lot of repetitions of the same error (roughly 1000 messages) which I tried to cut down to unique ones with " cat /var/log/syslog|grep 'Aug'|grep -b -i error|sort -u -k 12,12". Here is the output seen on boot. The file has now only 28 lines:
 
1321577:Aug  1 11:28:34 MyPC kernel: [    1.771850] ACPI BIOS Error (bug): 
1704140:Aug  1 11:31:59 MyPC kernel: [    1.800881]  due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
1092486:Aug  1 11:23:26 MyPC systemd-xdg-autostart-generator[1016]: Not generating service for XDG autostart [email]app-vnccreate_big@autostart.servic[/email]e, error parsing Exec= line: No such file or directory
2086:Aug  1 00:00:19 MyPC kernel: [2206557.487828] i915 0000:00:02.0: [drm] *ERROR* VBT claims to have both internal and external displays on PHY A.  Configuring for internal.
959606:Aug  1 11:23:23 MyPC kernel: [    0.376974] pcieport 0000:00:1c.0: DPC: error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+
997005:Aug  1 11:23:23 MyPC kernel: [    3.023493] pcieport 0000:00:1c.0: AER: Multiple Corrected error message received from 0000:00:1c.0
931862:Aug  1 11:23:23 MyPC kernel: [    0.246203] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
858798:Aug  1 11:22:14 MyPC whoopsie[898940]: [11:22:14] Sent; server replied with: No error
997143:Aug  1 11:23:23 MyPC kernel: [    3.023509] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
1118289:Aug  1 11:23:28 MyPC notification-ar[1344]: GDBus.Error:org.freedesktop.DBus.GLib.ErrorError: Method invoked for RegisterStatusNotifierHost returned FALSE but did not set error
971709:Aug  1 11:23:23 MyPC kernel: [    1.476856] RAS: Correctable Errors collector initialized.
1210110:Aug  1 11:27:14 MyPC kernel: [  236.570656] ayatana-indicat[1448]: segfault at 36 ip 0000703353be68c9 sp 00007ffd6abe9b80 error 4 in libgobject-2.0.so.0.7200.4[703353bbc000+33000] likely on CPU 0 (core
 0, socket 0)
1841830:Aug  1 11:32:36 MyPC kernel: [   43.202094] traps: marco[1283] trap int3 ip:77e2fa1fc167 sp:7ffea96c2600 error:0 in libglib-2.0.so.0.7200.4[77e2fa1b8000+8f000]
864886:Aug  1 11:22:52 MyPC evolution-addre[3799]: Error releasing name org.gnome.evolution.dataserver.AddressBook10: The connection is closed
997658:Aug  1 11:23:23 MyPC kernel: [    3.023533] pcieport 0000:00:1c.0: AER: found no error details for 0000:00:1c.0
1497466:Aug  1 11:29:37 MyPC kernel: [  106.181473] pcieport 0000:00:1c.0: AER:   Error of this Agent is reported first
859666:Aug  1 11:22:52 MyPC evolution-calen[1759]: Error setting property 'ConnectionStatus' on interface org.gnome.evolution.dataserver.Source: The connection is closed (g-io-error-quark, 18)
881312:Aug  1 11:23:23 MyPC systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
932443:Aug  1 11:23:23 MyPC kernel: [    0.246240] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
933115:Aug  1 11:23:23 MyPC kernel: [    0.246348] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS04._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
933787:Aug  1 11:23:23 MyPC kernel: [    0.246453] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS05._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
934459:Aug  1 11:23:23 MyPC kernel: [    0.247289] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
935131:Aug  1 11:23:23 MyPC kernel: [    0.247485] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.SS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
935803:Aug  1 11:23:23 MyPC kernel: [    0.248317] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.SS05._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
1077744:Aug  1 11:23:24 MyPC networkd-dispatcher[645]: ERROR:Unknown state for interface NetworkctlListState(idx=2, name='enp3s0', type='ether', operational='n/a', administrative='unmanaged'): n/a
1076974:Aug  1 11:23:24 MyPC networkd-dispatcher[645]: ERROR:Unknown state for interface NetworkctlListState(idx=1, name='lo', type='loopback', operational='n/a', administrative='unmanaged'): n/a
1078515:Aug  1 11:23:24 MyPC networkd-dispatcher[645]: ERROR:Unknown state for interface NetworkctlListState(idx=3, name='wlp1s0', type='wlan', operational='n/a', administrative='unmanaged'): n/a
996038:Aug  1 11:23:23 MyPC kernel: [    2.850410] i915 0000:00:02.0: [drm] *ERROR* VBT claims to have both internal and external displays on PHY A.  Configuring for internal.

Can anybody tell me whether there is anything pointing to a hardware problem!
Thanx

---

### Post by #&amp;thj^% on 2024-08-03
Is your system preforming as expected? Nothing jumps out for hardware problems.

systemd-xdg-autostart-generator is quite noisy in logs (it tries to parse files that aren't suffixed .desktop, and takes issue with some lines even in ones that are, and are provided by their package.


And man document suggested way to mask a generator (unlikely to be overwritten by package update):
```
mkdir /etc/systemd/user-generators
cd /etc/systemd/user-generators
ln -sf /dev/null systemd-xdg-autostart-generator
```

I have no issues with that but YMMV.

---

### Post by dieter-erich on 2024-08-05
Hi 1fallen, thanx, this is good news! I found it somewhat worrying to see thus many error messages (in fact about 1,500)! Furthermore, I had some unexplained crashes during the last few months and therefore thought they might come from hardware failures.... 
After restarting in recovery mode followed by normal mode everything seemed OK, though......
So, if I understand correctly, nothing to worry about :-)

---

