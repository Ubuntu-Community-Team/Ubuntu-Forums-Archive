---
title: "CUPS Issue with Kyocera FS-1061DN"
date: 2023-01-21
forum: Hardware
---

### Post by Quad0 on 2023-01-21
[FONT=verdana]&#8203;&#8203;
G'day,

Can  someone please help me with  troubleshooting a Kyocera FS-1061DN printer  with my Ubuntu 22.04.01 system? After installation it shows up in the control panel as both  "CUPS-BRF-Printer" and  "FS-1061DN"  printers. 

When I send  something to print, the  light on the printer flashes but  nothing  happens i.e. no printing. Been tackling this issue for a few  weeks now  and I desperately need the printer to work. 

Help would be greatly appreciated. Thank you. [/FONT]

---

### Post by #&amp;thj^% on 2023-01-21
My effort, here's something I had to read from: [https://www.linuxquestions.org/questions/showthread.php?p=6405641#post6405641](https://www.linuxquestions.org/questions/showthread.php?p=6405641#post6405641)
I assume thats your post as well.
```

bus-daemon" sauid=102 hostname=? addr=? terminal=?'
Jan 20 15:49:57 blackout-01 kernel: [1108270.689454] audit: type=1107 audit(1674193797.080:184): pid=1100 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/ColorManager" interface="org.freedesktop.ColorManager" member="ProfileAdded" name=":1.18" mask="receive" pid=280132 label="snap.firefox.firefox" peer_pid=1208 peer_label="unconfined"
Jan 20 15:49:57 blackout-01 kernel: [1108270.689454]  exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Jan 20 15:49:57 blackout-01 kernel: [1108270.690620] audit: type=1107 audit(1674193797.080:185): pid=1100 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/ColorManager" interface="org.freedesktop.ColorManager" member="DeviceAdded" name=":1.18" mask="receive" pid=280132 label="snap.firefox.firefox" peer_pid=1208 peer_label="unconfined"
Jan 20 15:49:57 blackout-01 kernel: [1108270.690620]  exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Jan 20 15:49:57 blackout-01 kernel: [1108270.691191] audit: type=1107 audit(1674193797.080:186): pid=1100 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/ColorManager" interface="org.freedesktop.ColorManager" member="DeviceChanged" name=":1.18" mask="receive" pid=280132 label="snap.firefox.firefox" peer_pid=1208 peer_label="unconfined"
Jan 20 15:49:57 blackout-01 kernel: [1108270.691191]  exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Jan 20 15:49:57 blackout-01 kernel: [1108270.692906] audit: type=1107 audit(1674193797.084:187): pid=1100 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/ColorManager" interface="org.freedesktop.ColorManager" member="ProfileAdded" name=":1.18" mask="receive" pid=280132 label="snap.firefox.firefox" peer_pid=1208 peer_label="unconfined"
Jan 20 15:49:57 blackout-01 kernel: [1108270.692906]  exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
```
What I'm pointing to is, I see this:
```
'apparmor="DENIED" operation="dbus_signal"
```
I'll leave the rest to someone smarter than me.
Good Luck

---

### Post by Quad0 on 2023-01-21
Yes, really hoping that someone would be able to assist. 

Thank you.

---

### Post by mIk3_08 on 2023-01-21
In my situation I wasn't able to print due to my desktop firewall shield  was enabled but when I disabled the firewall then I can smoothly print  any document via network printer. This is via network printer.  Regards and cheers.

---

### Post by Quad0 on 2023-01-22
```
sudo ufw status 
Status: inactive

```

---

### Post by #&amp;thj^% on 2023-01-22
This was the point I tried to speak on:
"apparmor="DENIED" operation="dbus_signal"
apparmor seems to not like it, I'm not sure UFW is in fault here.
Might give someone a better look at:
```
sudo aa-status

```
IE:
```
apparmor module is loaded.
69 profiles are loaded.
45 profiles are in enforce mode.
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince//sanitized_helper
   /usr/bin/freshclam
   /usr/bin/lxc-start
   /usr/bin/man
   /usr/bin/pidgin
   /usr/bin/pidgin//sanitized_helper
   /usr/bin/totem
   /usr/bin/totem-audio-preview
   /usr/bin/totem-video-thumbnailer
   /usr/bin/totem//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/x86_64-linux-gnu/lightdm/lightdm-guest-session
   /usr/lib/x86_64-linux-gnu/lightdm/lightdm-guest-session//chromium
   /usr/sbin/chronyd
   /usr/sbin/clamd
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ntpd
   /{,usr/}sbin/dhclient
   apt-cacher-ng
   firejail-default
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   libvirtd
   libvirtd//qemu_bridge_helper
   lsb_release
   lxc-container-default
   lxc-container-default-cgns
   lxc-container-default-with-mounting
   lxc-container-default-with-nesting
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   tcpdump
   virt-aa-helper
24 profiles are in complain mode.
   /usr/bin/irssi
   avahi-daemon
   dnsmasq
   dnsmasq//libvirt_leaseshelper
   identd
   klogd
   libreoffice-oosplash
   libreoffice-soffice
   mdnsd
   nmbd
   nscd
   php-fpm
   ping
   samba-bgqd
   samba-dcerpcd
   samba-rpcd
   samba-rpcd-classic
   samba-rpcd-spoolss
   smbd
   smbldap-useradd
   smbldap-useradd///etc/init.d/nscd
   syslog-ng
   syslogd
   traceroute
0 profiles are in kill mode.
0 profiles are in unconfined mode.
2 processes have profiles defined.
2 processes are in enforce mode.
   /usr/sbin/ntpd (1504) 
   /usr/bin/qbittorrent (4968) firejail-default//&unconfined
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.

```
Just for fun I just now ran some tests with apparmor, I may have something for you here:
```
aa-complain /usr/sbin/cupsd
aa-complain /usr/sbin/cups-browsed
```
I'm under the impression your printer is connected via a USB connection right?

---

### Post by Quad0 on 2023-01-22
ah ok. Need more learning on app armor stuff.. had no idea! 

This is my output when I ran the same cmd as you... 

```
sudo aa-status 
apparmor module is loaded.
46 profiles are loaded.
44 profiles are in enforce mode.
   /snap/snapd/17883/usr/lib/snapd/snap-confine
   /snap/snapd/17883/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /snap/snapd/17950/usr/lib/snapd/snap-confine
   /snap/snapd/17950/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince//sanitized_helper
   /usr/bin/man
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /{,usr/}sbin/dhclient
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   snap-update-ns.firefox
   snap-update-ns.snap-store
   snap-update-ns.snapd-desktop-integration
   snap.firefox.firefox
   snap.firefox.geckodriver
   snap.firefox.hook.configure
   snap.firefox.hook.connect-plug-host-hunspell
   snap.firefox.hook.disconnect-plug-host-hunspell
   snap.firefox.hook.post-refresh
   snap.snap-store.hook.configure
   snap.snap-store.snap-store
   snap.snap-store.ubuntu-software
   snap.snap-store.ubuntu-software-local-file
   snap.snapd-desktop-integration.hook.configure
   snap.snapd-desktop-integration.snapd-desktop-integration
   tcpdump
2 profiles are in complain mode.
   libreoffice-oosplash
   libreoffice-soffice
0 profiles are in kill mode.
0 profiles are in unconfined mode.
30 processes have profiles defined.
30 processes are in enforce mode.
   /usr/sbin/cups-browsed (6833) 
   /usr/sbin/cupsd (6824) 
   /usr/lib/cups/notifier/dbus (6827) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (6828) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (8463) /usr/sbin/cupsd
   /snap/firefox/2263/usr/lib/firefox/firefox (2970) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3182) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3208) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3513) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3696) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3698) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3706) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3712) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4040) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4044) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4094) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4096) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4118) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4186) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4232) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4402) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4478) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4554) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4671) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4676) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4810) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4940) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (9804) snap.firefox.firefox
   /snap/snapd-desktop-integration/49/usr/bin/snapd-desktop-integration (2548) snap.snapd-desktop-integration.snapd-desktop-integration
   /snap/snapd-desktop-integration/49/usr/bin/snapd-desktop-integration (2627) snap.snapd-desktop-integration.snapd-desktop-integration
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.

```

---

### Post by #&amp;thj^% on 2023-01-22
There it is:
```
24 profiles are in complain mode.
   /usr/bin/irssi
   avahi-daemon
   dnsmasq
   dnsmasq//libvirt_leaseshelper
   identd
   klogd
   libreoffice-oosplash
   libreoffice-soffice
   mdnsd
   nmbd
   nscd
   php-fpm
   ping
   samba-bgqd
   samba-dcerpcd
   samba-rpcd
   samba-rpcd-classic
   samba-rpcd-spoolss
   smbd
   smbldap-useradd
   smbldap-useradd///etc/init.d/nscd
   syslog-ng
   syslogd
   traceroute
0 profiles are in kill mode.
0 profiles are in unconfined mode.

```
Have you yet run these:
```
aa-complain /usr/sbin/cupsd
aa-complain /usr/sbin/cups-browsed
```
I'll run it here to show what happens:
```
sudo aa-complain /usr/sbin/cups-browsed
[sudo] password for me: 
Setting /usr/sbin/cups-browsed to complain mode.

```
But please run both commands I've shown you above.
EDIT: I must be tired today, You'll need to restart apparmor after any changes:
```
systemctl restart apparmor

```
Now I can check with aa-staus to see.

---

### Post by Quad0 on 2023-01-22
Right ok, thank you. I guess I am not quite understanding the difference between "enforced" and "complain" mode. For me both mean it is bad and there is a restriction of sort??

```
sudo aa-status 
apparmor module is loaded.
46 profiles are loaded.
42 profiles are in enforce mode.
   /snap/snapd/17883/usr/lib/snapd/snap-confine
   /snap/snapd/17883/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /snap/snapd/17950/usr/lib/snapd/snap-confine
   /snap/snapd/17950/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince//sanitized_helper
   /usr/bin/man
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cupsd//third_party
   /{,usr/}sbin/dhclient
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   snap-update-ns.firefox
   snap-update-ns.snap-store
   snap-update-ns.snapd-desktop-integration
   snap.firefox.firefox
   snap.firefox.geckodriver
   snap.firefox.hook.configure
   snap.firefox.hook.connect-plug-host-hunspell
   snap.firefox.hook.disconnect-plug-host-hunspell
   snap.firefox.hook.post-refresh
   snap.snap-store.hook.configure
   snap.snap-store.snap-store
   snap.snap-store.ubuntu-software
   snap.snap-store.ubuntu-software-local-file
   snap.snapd-desktop-integration.hook.configure
   snap.snapd-desktop-integration.snapd-desktop-integration
   tcpdump
4 profiles are in complain mode.
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   libreoffice-oosplash
   libreoffice-soffice
0 profiles are in kill mode.
0 profiles are in unconfined mode.
30 processes have profiles defined.
25 processes are in enforce mode.
   /snap/firefox/2263/usr/lib/firefox/firefox (2970) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3182) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3208) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3513) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3696) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3698) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3706) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (3712) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4040) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4094) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4096) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4118) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4186) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4232) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4402) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4478) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4554) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4671) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (4940) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (10262) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (10302) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (10367) snap.firefox.firefox
   /snap/firefox/2263/usr/lib/firefox/firefox (11655) snap.firefox.firefox
   /snap/snapd-desktop-integration/49/usr/bin/snapd-desktop-integration (2548) snap.snapd-desktop-integration.snapd-desktop-integration
   /snap/snapd-desktop-integration/49/usr/bin/snapd-desktop-integration (2627) snap.snapd-desktop-integration.snapd-desktop-integration
5 processes are in complain mode.
   /usr/sbin/cups-browsed (6833) 
   /usr/sbin/cupsd (6824) 
   /usr/lib/cups/notifier/dbus (6827) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (6828) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (8463) /usr/sbin/cupsd
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.

```

Still no printing.. the light flashes on the printer when trying to do a test page after restarting cups.service but there is no printing... :(

---

### Post by #&amp;thj^% on 2023-01-22
EDIT: To un do what we did use this:
```
**sudo aa-enforce /usr/sbin/cups-browsed**
Setting /usr/sbin/cups-browsed to enforce mode.


me on Sun Jan 22 at 02:46 PM in ~ branch: (HEAD) 
>>** sudo aa-enforce aa-complain /usr/sbin/cupsd**
Profile for /usr/sbin/aa-complain not found, skipping
Setting /usr/sbin/cupsd to enforce mode.


```
This first appeared here:[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=980974](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=980974)
I'm a tester so I'm more of a nuke-em type of guy. This makes a lot folks here nervous. :)
I had another string to run but I'll hold off on that one for the time being. ;)
I'll leave with one suggestion, as my last thought:
```
sudo apt remove --purge cups

```
mine shows:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cups-browsed cups-client cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ipp-utils cups-ppdc cups-server-common
  libcupsfilters1 libfontembed1 liblouisutdml-bin liblouisutdml-data
  liblouisutdml9 libpoppler-cpp0v5 ssl-cert
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  cups*
0 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.

```
now autoremove for a clean install
```
sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  cups-browsed cups-client cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ipp-utils cups-ppdc cups-server-common
  libcupsfilters1 libfontembed1 liblouisutdml-bin liblouisutdml-data
  liblouisutdml9 libpoppler-cpp0v5 ssl-cert
0 upgraded, 0 newly installed, 16 to remove and 23 not upgraded.
After this operation, 9,463 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 652411 files and directories currently installed.)
Removing cups-browsed (1.28.16-1+b3) ...
Removing cups-client (2.4.2-1+b2) ...
Removing cups-core-drivers (2.4.2-1+b2) ...
Removing cups-daemon (2.4.2-1+b2) ...
Removing cups-filters (1.28.16-1+b3) ...
Removing cups-filters-core-drivers (1.28.16-1+b3) ...
Removing cups-ipp-utils (2.4.2-1+b2) ...
Removing cups-ppdc (2.4.2-1+b2) ...
Removing cups-server-common (2.4.2-1) ...
Removing libcupsfilters1:amd64 (1.28.16-1+b3) ...
Removing libfontembed1:amd64 (1.28.16-1+b3) ...
Removing liblouisutdml-bin (2.11.0-2) ...
Removing liblouisutdml9:amd64 (2.11.0-2) ...
Removing liblouisutdml-data (2.11.0-2) ...
Removing libpoppler-cpp0v5:amd64 (22.12.0-2+b1) ...
Removing ssl-cert (1.1.2) ...
Processing triggers for kaisen-menu (2.2+kaisen4) ...
Processing triggers for man-db (2.11.2-1) ...
Processing triggers for libc-bin (2.36-8) ...

```
I prefer a restart before re-installing from a fresh session:
```
sudo apt install cups
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  cups-browsed cups-client cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ipp-utils cups-ppdc cups-server-common
  libcupsfilters1 libfontembed1 liblouisutdml-bin liblouisutdml-data
  liblouisutdml9 libpoppler-cpp0v5 ssl-cert
Suggested packages:
  cups-bsd cups-pdf foomatic-db-compressed-ppds | foomatic-db antiword
  docx2txt ooo2dbk rtf2xml
The following NEW packages will be installed:
  cups cups-browsed cups-client cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ipp-utils cups-ppdc cups-server-common
  libcupsfilters1 libfontembed1 liblouisutdml-bin liblouisutdml-data
  liblouisutdml9 libpoppler-cpp0v5 ssl-cert
0 upgraded, 17 newly installed, 0 to remove and 23 not upgraded.
Need to get 1,730 kB/2,863 kB of archives.

```
I'm all out of Ideas if this results void.

---

### Post by #&amp;thj^% on 2023-01-22
First let's make sure apparmor is really blocking your printer:
```
sudo systemctl stop apparmor
sudo systemctl disable apparmor
```
The above is only for special checks, apparmor really should not need to be stopped.
Now try printing after a reboot.
```
sudo aa-status 
[sudo] password for me: 
apparmor module is loaded.


```

---

### Post by Quad0 on 2023-01-22
Thanks so much for your help so far. It is frustrating why something as simple as this wouldn't work... 

I did all the above steps as your thread...

I managed to look at CUPS webserver and added the printer manually also giving it the ppd file. The error I get when I sent through a test page is:

```

[TABLE="class: list"]
[TR]
[TD][Kyocera_FS-1061DN]("http://localhost:631/printers/Kyocera_FS-1061DN")-17[/TD]
[TD]Unknown[/TD]
[TD]Withheld[/TD]
[TD]1k[/TD]
[TD]Unknown[/TD]
[TD] stopped  *"Filter failed"*[/TD]
[TD][/TD]
[/TR]
[/TABLE]

```

Under Printers I have: 
```

[TABLE="class: list"]
[TR]
[TD][CUPS-BRF-Printer]("http://127.0.0.1:631/printers/CUPS-BRF-Printer")[/TD]
[TD]CUPS-BRF[/TD]
[TD][/TD]
[TD]Generic Text-Only Printer[/TD]
[TD]Idle[/TD]
[/TR]
  [TR]
[TD][FS-1061DN]("http://127.0.0.1:631/printers/FS-1061DN")[/TD]
[TD]FS-1061DN[/TD]
[TD][/TD]
[TD]Kyocera Mita FS-1050[/TD]
[TD]Paused - "Backend /usr/lib/cups/backend/usb does not exist!"[/TD]
[/TR]
  [TR]
[TD][Kyocera_FS-1061DN]("http://127.0.0.1:631/printers/Kyocera_FS-1061DN")[/TD]
[TD]Kyocera FS-1061DN[/TD]
[TD][/TD]
[TD]Kyocera FS-1060DN (KPSL)[/TD]
[TD]Idle - "Rendering completed"[/TD]
[/TR]
[/TABLE]

```

---

### Post by #&amp;thj^% on 2023-01-22
can you go to the CUPS printer administration page and click "Resume Printer"

---

### Post by Quad0 on 2023-01-22
Error Log:
```
D [23/Jan/2023:08:56:59 +1000] [Job 17] Printer found with device ID: MFG:Kyocera;MDL:FS-1061DN;CLS:PRINTER;SN:R6U2304431;CID:KY_KPSL_MonoPersonal; Device URI: usb://Kyocera/FS-1061DN?serial=R6U2304431
D [23/Jan/2023:08:56:59 +1000] [Job 17] Device protocol: 2
D [23/Jan/2023:08:56:59 +1000] [Job 17] pdftopdf: Last filter determined by the PPD: rastertokpsl; FINAL_CONTENT_TYPE: application/vnd.cups-raster => pdftopdf will not log pages in page_log.
D [23/Jan/2023:08:56:59 +1000] [Job 17] PDF template file doesn\'t have form. It\'s okay.
D [23/Jan/2023:08:56:59 +1000] [Job 17] Sending data to printer.
D [23/Jan/2023:08:56:59 +1000] [Job 17] Sent 0 bytes...
D [23/Jan/2023:08:56:59 +1000] [Job 17] PID 3525 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [23/Jan/2023:08:56:59 +1000] [Job 17] PDF interactive form and annotation flattening done via QPDF
D [23/Jan/2023:08:56:59 +1000] [Job 17] pdftopdf: \"print-scaling\" IPP attribute: auto
D [23/Jan/2023:08:56:59 +1000] [Job 17] pdftopdf: Print scaling mode: Do not scale, center, crop if needed
D [23/Jan/2023:08:56:59 +1000] [Job 17] After Cropping: 595.000000 842.000000 595.000000 842.000000
D [23/Jan/2023:08:56:59 +1000] [Job 17] After Cropping: 595.000000 842.000000 595.000000 842.000000
D [23/Jan/2023:08:56:59 +1000] [Job 17] PID 3526 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [23/Jan/2023:08:56:59 +1000] [Job 17] Color Manager: Calibration Mode/Off
D [23/Jan/2023:08:56:59 +1000] [Job 17] Calling FindDeviceById(cups-Kyocera_FS-1061DN)
D [23/Jan/2023:08:56:59 +1000] [Job 17] Found device /org/freedesktop/ColorManager/devices/cups_Kyocera_FS_1061DN
D [23/Jan/2023:08:56:59 +1000] [Job 17] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [23/Jan/2023:08:56:59 +1000] [Job 17] Calling FindDeviceById(cups-Kyocera_FS-1061DN)
D [23/Jan/2023:08:56:59 +1000] [Job 17] Found device /org/freedesktop/ColorManager/devices/cups_Kyocera_FS_1061DN
D [23/Jan/2023:08:56:59 +1000] [Job 17] Calling GetProfileForQualifiers(Gray.PrnDef.600dpi...)
D [23/Jan/2023:08:56:59 +1000] [Job 17] Found profile /org/freedesktop/ColorManager/profiles/Kyocera_FS_1061DN_Gray__
D [23/Jan/2023:08:56:59 +1000] [Job 17] Calling org.freedesktop.ColorManager.Profile.Get(Filename)
D [23/Jan/2023:08:56:59 +1000] [Job 17] Failed to get profile filename for cups-Kyocera_FS-1061DN
D [23/Jan/2023:08:56:59 +1000] [Job 17] Color Manager: ICC Profile: 
D [23/Jan/2023:08:56:59 +1000] [Job 17] Ghostscript using Any-Part-of-Pixel method to fill paths.
D [23/Jan/2023:08:56:59 +1000] [Job 17] Ghostscript command line: gs -dQUIET -dSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -dShowAcroForm -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -dDuplex -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsCompression=1 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c \'<</.HWMargins[12.000000 10.000000 12.000000 10.000000] /Margins[0 0]>>setpagedevice\' -f -_
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[0]=\"CUPS_CACHEDIR=/var/cache/cups\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[1]=\"CUPS_DATADIR=/usr/share/cups\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[2]=\"CUPS_DOCROOT=/usr/share/cups/doc-root\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[3]=\"CUPS_REQUESTROOT=/var/spool/cups\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[4]=\"CUPS_SERVERBIN=/usr/lib/cups\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[5]=\"CUPS_SERVERROOT=/etc/cups\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[6]=\"CUPS_STATEDIR=/run/cups\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[7]=\"HOME=/var/spool/cups/tmp\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[8]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[9]=\"SERVER_ADMIN=root@blackout-01\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[10]=\"SOFTWARE=CUPS/2.4.1\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[11]=\"TMPDIR=/var/spool/cups/tmp\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[12]=\"USER=root\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[13]=\"CUPS_MAX_MESSAGE=2047\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[14]=\"CUPS_SERVER=/run/cups/cups.sock\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[15]=\"CUPS_ENCRYPTION=IfRequested\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[16]=\"IPP_PORT=631\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[17]=\"CHARSET=utf-8\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[18]=\"LANG=en_AU.UTF-8\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[19]=\"PPD=/etc/cups/ppd/Kyocera_FS-1061DN.ppd\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[20]=\"CONTENT_TYPE=application/vnd.cups-pdf-banner\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[21]=\"DEVICE_URI=usb://Kyocera/FS-1061DN?serial=R6U2304431\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[22]=\"PRINTER_INFO=Kyocera FS-1061DN\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[23]=\"PRINTER_LOCATION=\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[24]=\"PRINTER=Kyocera_FS-1061DN\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[25]=\"PRINTER_STATE_REASONS=none\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[26]=\"CUPS_FILETYPE=document\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[27]=\"FINAL_CONTENT_TYPE=application/vnd.cups-raster\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] envp[28]=\"AUTH_INFO_REQUIRED=none\"
D [23/Jan/2023:08:56:59 +1000] [Job 17] Start rendering...
D [23/Jan/2023:08:56:59 +1000] [Job 17] Processing page 1...
D [23/Jan/2023:08:56:59 +1000] [Job 17] Error: /ioerror in --showpage--
D [23/Jan/2023:08:56:59 +1000] [Job 17] Operand stack:
D [23/Jan/2023:08:56:59 +1000] [Job 17] (/var/spool/cups/tmp/gs_hsXQ56)   --nostringval--   1   true
D [23/Jan/2023:08:56:59 +1000] [Job 17] Execution stack:
D [23/Jan/2023:08:56:59 +1000] [Job 17] %interp_exit   .runexec2   --nostringval--   showpage   --nostringval--   2   %stopped_push   --nostringval--   showpage   showpage   false   1   %stopped_push   1990   1   3   %oparray_pop   1989   1   3   %oparray_pop   1977   1   3   %oparray_pop   showpage   1978   3   3   %oparray_pop   showpage   showpage   2   1   2   showpage   %for_pos_int_continue   1981   3   7   %oparray_pop   showpage   showpage   1840   2   9   %oparray_pop   showpage   showpage
D [23/Jan/2023:08:56:59 +1000] [Job 17] Dictionary stack:
D [23/Jan/2023:08:56:59 +1000] [Job 17] --dict:774/1123(ro)(G)--   --dict:1/20(G)--   --dict:81/200(L)--   --dict:81/200(L)--   --dict:134/256(ro)(G)--   --dict:325/325(ro)(G)--   --dict:35/64(L)--   --dict:6/9(L)--   --dict:6/20(L)--
D [23/Jan/2023:08:56:59 +1000] [Job 17] Current allocation mode is local
D [23/Jan/2023:08:56:59 +1000] [Job 17] Last OS error: Broken pipe
D [23/Jan/2023:08:56:59 +1000] [Job 17] GPL Ghostscript 9.55.0: Unrecoverable error, exit code 1
D [23/Jan/2023:08:56:59 +1000] [Job 17] Rendering completed
D [23/Jan/2023:08:56:59 +1000] [Job 17] PID 3527 (/usr/lib/cups/filter/gstoraster) stopped with status 1.
D [23/Jan/2023:08:56:59 +1000] [Job 17] Hint: Try setting the LogLevel to "debug" to find out more.
D [23/Jan/2023:08:56:59 +1000] [Job 17] Waiting for read thread to exit...
D [23/Jan/2023:08:56:59 +1000] [Job 17] PID 3529 (/usr/lib/cups/backend/usb) exited with no errors.
D [23/Jan/2023:08:56:59 +1000] [Job 17] End of messages
D [23/Jan/2023:08:56:59 +1000] [Job 17] printer-state=3(idle)
D [23/Jan/2023:08:56:59 +1000] [Job 17] printer-state-message="Rendering completed"
D [23/Jan/2023:08:56:59 +1000] [Job 17] printer-state-reasons=none

```

---

### Post by Quad0 on 2023-01-22
Dont have that option.. but re-ran another test page but got the same error "Filter failed"

---

### Post by Quad0 on 2023-01-22
Logs after stopping and disabling apparmor:

```
D [23/Jan/2023:09:06:32 +1000] [Job 19] Restarted by "blackout".
D [23/Jan/2023:09:06:32 +1000] [Job 19] Kyocera_FS-1061DN: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory
D [23/Jan/2023:09:06:32 +1000] [Job 19] PID 4246 (/usr/lib/cups/filter/rastertokpsl) stopped with status 127 (File too large)
D [23/Jan/2023:09:06:32 +1000] [Job 19] Hint: Try setting the LogLevel to "debug" to find out more.
D [23/Jan/2023:09:06:32 +1000] [Job 19] PDF template file doesn\'t have form. It\'s okay.
D [23/Jan/2023:09:06:32 +1000] [Job 19] pdftopdf: Last filter determined by the PPD: rastertokpsl; FINAL_CONTENT_TYPE: application/vnd.cups-raster => pdftopdf will not log pages in page_log.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Loading USB quirks from \"/usr/share/cups/usb\".
D [23/Jan/2023:09:06:32 +1000] [Job 19] Loaded 118 quirks.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Printing on printer with URI: usb://Kyocera/FS-1061DN?serial=R6U2304431
D [23/Jan/2023:09:06:32 +1000] [Job 19] PID 4243 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [23/Jan/2023:09:06:32 +1000] [Job 19] OUTFORMAT=\"<none>\", so output format will be CUPS/PWG Raster
D [23/Jan/2023:09:06:32 +1000] [Job 19] PDF interactive form and annotation flattening done via QPDF
D [23/Jan/2023:09:06:32 +1000] [Job 19] pdftopdf: \"print-scaling\" IPP attribute: auto
D [23/Jan/2023:09:06:32 +1000] [Job 19] pdftopdf: Print scaling mode: Do not scale, center, crop if needed
D [23/Jan/2023:09:06:32 +1000] [Job 19] After Cropping: 595.000000 842.000000 595.000000 842.000000
D [23/Jan/2023:09:06:32 +1000] [Job 19] libusb_get_device_list=11
D [23/Jan/2023:09:06:32 +1000] [Job 19] STATE: +connecting-to-device
D [23/Jan/2023:09:06:32 +1000] [Job 19] STATE: -connecting-to-device
D [23/Jan/2023:09:06:32 +1000] [Job 19] iSerialNumber=\"R6U2304431\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] Printer found with device ID: MFG:Kyocera;MDL:FS-1061DN;CLS:PRINTER;SN:R6U2304431;CID:KY_KPSL_MonoPersonal; Device URI: usb://Kyocera/FS-1061DN?serial=R6U2304431
D [23/Jan/2023:09:06:32 +1000] [Job 19] Device protocol: 2
D [23/Jan/2023:09:06:32 +1000] [Job 19] Sending data to printer.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Sent 0 bytes...
D [23/Jan/2023:09:06:32 +1000] [Job 19] PID 4244 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Color Manager: Calibration Mode/Off
D [23/Jan/2023:09:06:32 +1000] [Job 19] Calling FindDeviceById(cups-Kyocera_FS-1061DN)
D [23/Jan/2023:09:06:32 +1000] [Job 19] Found device /org/freedesktop/ColorManager/devices/cups_Kyocera_FS_1061DN
D [23/Jan/2023:09:06:32 +1000] [Job 19] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [23/Jan/2023:09:06:32 +1000] [Job 19] Calling FindDeviceById(cups-Kyocera_FS-1061DN)
D [23/Jan/2023:09:06:32 +1000] [Job 19] Found device /org/freedesktop/ColorManager/devices/cups_Kyocera_FS_1061DN
D [23/Jan/2023:09:06:32 +1000] [Job 19] Calling GetProfileForQualifiers(Gray.PrnDef.600dpi...)
D [23/Jan/2023:09:06:32 +1000] [Job 19] Failed to send: org.freedesktop.ColorManager.Device.NothingMatched:nothing matched expression \'Gray.PrnDef.600dpi,Gray.PrnDef.*,Gray.*.600dpi,Gray.*.*,*\'
D [23/Jan/2023:09:06:32 +1000] [Job 19] Failed to get profile filename for cups-Kyocera_FS-1061DN
D [23/Jan/2023:09:06:32 +1000] [Job 19] Color Manager: no profiles specified in PPD
D [23/Jan/2023:09:06:32 +1000] [Job 19] Color Manager: ICC Profile: None
D [23/Jan/2023:09:06:32 +1000] [Job 19] Ghostscript using Any-Part-of-Pixel method to fill paths.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Ghostscript command line: gs -dQUIET -dSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -dShowAcroForm -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsCompression=1 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c \'<</.HWMargins[12.000000 10.000000 12.000000 10.000000] /Margins[0 0]>>setpagedevice\' -f -_
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[0]=\"CUPS_CACHEDIR=/var/cache/cups\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[1]=\"CUPS_DATADIR=/usr/share/cups\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[2]=\"CUPS_DOCROOT=/usr/share/cups/doc-root\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[3]=\"CUPS_REQUESTROOT=/var/spool/cups\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[4]=\"CUPS_SERVERBIN=/usr/lib/cups\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[5]=\"CUPS_SERVERROOT=/etc/cups\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[6]=\"CUPS_STATEDIR=/run/cups\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[7]=\"HOME=/var/spool/cups/tmp\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[8]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[9]=\"SERVER_ADMIN=root@blackout-01\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[10]=\"SOFTWARE=CUPS/2.4.1\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[11]=\"TMPDIR=/var/spool/cups/tmp\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[12]=\"USER=root\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[13]=\"CUPS_MAX_MESSAGE=2047\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[14]=\"CUPS_SERVER=/run/cups/cups.sock\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[15]=\"CUPS_ENCRYPTION=IfRequested\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[16]=\"IPP_PORT=631\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[17]=\"CHARSET=utf-8\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[18]=\"LANG=en_US.UTF-8\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[19]=\"PPD=/etc/cups/ppd/Kyocera_FS-1061DN.ppd\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[20]=\"CONTENT_TYPE=application/vnd.cups-pdf-banner\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[21]=\"DEVICE_URI=usb://Kyocera/FS-1061DN?serial=R6U2304431\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[22]=\"PRINTER_INFO=Kyocera FS-1061DN\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[23]=\"PRINTER_LOCATION=\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[24]=\"PRINTER=Kyocera_FS-1061DN\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[25]=\"PRINTER_STATE_REASONS=none\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[26]=\"CUPS_FILETYPE=document\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[27]=\"FINAL_CONTENT_TYPE=application/vnd.cups-raster\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] envp[28]=\"AUTH_INFO_REQUIRED=none\"
D [23/Jan/2023:09:06:32 +1000] [Job 19] Start rendering...
D [23/Jan/2023:09:06:32 +1000] [Job 19] Processing page 1...
D [23/Jan/2023:09:06:32 +1000] [Job 19] Error: /ioerror in --showpage--
D [23/Jan/2023:09:06:32 +1000] [Job 19] Operand stack:
D [23/Jan/2023:09:06:32 +1000] [Job 19] (/var/spool/cups/tmp/gs_jHxkHM)   --nostringval--   1   true
D [23/Jan/2023:09:06:32 +1000] [Job 19] Execution stack:
D [23/Jan/2023:09:06:32 +1000] [Job 19] %interp_exit   .runexec2   --nostringval--   showpage   --nostringval--   2   %stopped_push   --nostringval--   showpage   showpage   false   1   %stopped_push   1990   1   3   %oparray_pop   1989   1   3   %oparray_pop   1977   1   3   %oparray_pop   showpage   1978   3   3   %oparray_pop   showpage   showpage   2   1   1   showpage   %for_pos_int_continue   1981   3   7   %oparray_pop   showpage   showpage   1840   2   9   %oparray_pop   showpage   showpage
D [23/Jan/2023:09:06:32 +1000] [Job 19] Dictionary stack:
D [23/Jan/2023:09:06:32 +1000] [Job 19] --dict:773/1123(ro)(G)--   --dict:1/20(G)--   --dict:81/200(L)--   --dict:81/200(L)--   --dict:134/256(ro)(G)--   --dict:325/325(ro)(G)--   --dict:35/64(L)--   --dict:6/9(L)--   --dict:6/20(L)--
D [23/Jan/2023:09:06:32 +1000] [Job 19] Current allocation mode is local
D [23/Jan/2023:09:06:32 +1000] [Job 19] Last OS error: Broken pipe
D [23/Jan/2023:09:06:32 +1000] [Job 19] GPL Ghostscript 9.55.0: Unrecoverable error, exit code 1
D [23/Jan/2023:09:06:32 +1000] [Job 19] Rendering completed
D [23/Jan/2023:09:06:32 +1000] [Job 19] PID 4245 (/usr/lib/cups/filter/gstoraster) stopped with status 1.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Hint: Try setting the LogLevel to "debug" to find out more.
D [23/Jan/2023:09:06:32 +1000] [Job 19] Waiting for read thread to exit...
D [23/Jan/2023:09:06:32 +1000] [Job 19] PID 4247 (/usr/lib/cups/backend/usb) exited with no errors.
D [23/Jan/2023:09:06:32 +1000] [Job 19] End of messages
D [23/Jan/2023:09:06:32 +1000] [Job 19] printer-state=3(idle)
D [23/Jan/2023:09:06:32 +1000] [Job 19] printer-state-message="Rendering completed"
D [23/Jan/2023:09:06:32 +1000] [Job 19] printer-state-reasons=none
W [23/Jan/2023:10:21:44 +1000] Printer drivers are deprecated and will stop working in a future version of CUPS. See https://github.com/OpenPrinting/cups/issues/103
E [23/Jan/2023:10:23:49 +1000] [Job 17] Unable to open raster stream - : Broken pipe


```

---

### Post by #&amp;thj^% on 2023-01-23
Ok I'm still not sure about all of this, makes no sense, will you show this please:
```
lpstat -p
```
Also this:
```
apt policy libcups2-dev 

```
The second one is rather new in your posts, IE: " Unable to open raster stream - : Broken pipe"

---

### Post by Quad0 on 2023-01-23
Bit messy.. as I have been adding printers etc.. 

```
lpstat -p
printer CUPS-BRF-Printer is idle.  enabled since Wed 30 Nov 2022 15:29:11
printer FS-1061DN is idle.  enabled since Mon 23 Jan 2023 10:44:27
printer FS-1061DN-140 is idle.  enabled since Mon 23 Jan 2023 10:48:04
printer Kyocera_FS-1061DN is idle.  enabled since Mon 23 Jan 2023 10:44:30
```

```
apt policy libcups2-dev 
libcups2-dev:
  Installed: (none)
  Candidate: 2.4.1op1-1ubuntu4.1
  Version table:
     2.4.1op1-1ubuntu4.1 500
        500 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     2.4.1op1-1ubuntu4 500
        500 http://au.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```

---

### Post by #&amp;thj^% on 2023-01-23
Just so you know, I'm making guesstimated suggestions..
Try to install it then "libcups2-dev"
Have you had luck with any of the other printers?
Dang I remember now the debug:
```
sudo cupsctl --debug-logging
```
Send a print job, and view the output.

---

### Post by Quad0 on 2023-01-23
Yes, I enabled debug logging last night... 

Attached here with.. Now the error has changed to "Processing.." but just hangs... printer light is flicking on and off (as in it is data but same as before)

What stands out is
```
D [24/Jan/2023:05:52:41 +1000] [Client 29] HTTP_STATE_WAITING Closing for error 32 (Broken pipe)
D [24/Jan/2023:05:52:41 +1000] [Client 29] Closing connection.
```

But you might see things that might make more sense...

---

### Post by Quad0 on 2023-01-23
The error has gone from the CUPS webserver though.. and replaced with..

```

[TABLE="class: list"]
[TR]
[TD][Kyocera_FS-1061DN]("http://127.0.0.1:631/printers/Kyocera_FS-1061DN")-24[/TD]
[TD]Test Page[/TD]
[TD]anonymous[/TD]
[TD]1k[/TD]
[TD]Unknown[/TD]
[TD] processing since
Tue 24 Jan ... 
*"Processing page 1..."*
[/TD]
[/TR]
[/TABLE]


```

---

### Post by #&amp;thj^% on 2023-01-23
EDIT:I forgot to address this:
```
D [24/Jan/2023:05:52:41 +1000] [Client 29] HTTP_STATE_WAITING Closing for error 32 (Broken pipe)
D [24/Jan/2023:05:52:41 +1000] [Client 29] Closing connection.
```
The "communication error" usually comes in ECONNRESET, EPIPE, and ECANCELED varieties. Which one you get usually just depends on which platform you're running on, but all three generally mean the same thing: that the client closed the connection ungracefully.

This is what is a bugger with no info added "PID 3923 (/usr/lib/cups/cgi-bin/printers.cgi) **_exited with no errors._**"
Out side of removing and re-installing the printer, This is my last guess to help you.
```
ErrorPolicy abort-job  
ErrorPolicy stop-printer  
ErrorPolicy retry-job
```
I do remember about 4 years ago with a printer used for about 2years without problems, what I did was 
1.Un plug  the printer (USB)
2.Restarted my router. (not to be confused with network-manager)
3.Re-started my computer
4.Plugged the printer back in and there it was, and functioning

---

### Post by #&amp;thj^% on 2023-01-24
The only linux driver I could find for that model printer is here..
[http://kyocera.drivercan.com/driver/3434296/](http://kyocera.drivercan.com/driver/3434296/)
 it's date 2014. It appears you have not said already if you have it.
You need to extract that file, it will extract it to a folder called Linux. Open that folder and go to the following folders..64bit-->Global-->english.tar.tz
extract that to English. Your drivers and the install file are in that folder.
Read the Installation Steps.rtf it will tell you what to do...You will find that the drivers it installed will work fine with that model.
This is the only thing I can think of that prevents you from  printing. (wrong/bad driver)

---

### Post by Quad0 on 2023-01-24
Already done this unfortunately :( 

Thanks so much for your input so far.

---

### Post by #&amp;thj^% on 2023-01-24
Your very welcome!
I would try to open a support ticket with them.

---

### Post by Quad0 on 2023-01-24
Yeah, I did that this morning... 1st level support said there was not much support he could offer to me at his level cause there wasn't any new drivers. The printer is 10+ years old!! What a rip off.. unsure why they are still selling it?! I guess I should have done my research as well... 

Can you recommend any newer printers that would work well with Ubuntu without issues like one I am having?

Thank you.

---

### Post by #&amp;thj^% on 2023-01-25
> **Quad0 said:**
> Yeah, I did that this morning... 1st level support said there was not much support he could offer to me at his level cause there wasn't any new drivers. The printer is 10+ years old!! What a rip off.. unsure why they are still selling it?! I guess I should have done my research as well... 

Unfortunate but some vendors have no shame, it will be written here though for all to see>>>So future Kyocera_FS-1061DN looker's beware.
I like just for ease, not necessarily for functions (bells and whistles) and I'll try to stay with what you are now trying to use ;)
Lexmark, HP, and most Epsons <<<(Check it for linux)

---

