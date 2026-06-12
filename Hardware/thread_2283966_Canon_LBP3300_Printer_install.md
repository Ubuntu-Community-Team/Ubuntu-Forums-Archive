---
title: "Canon LBP3300 Printer install"
date: 2015-06-26
forum: Hardware
---

### Post by akhtaruz on 2015-06-26
I am using ubuntu 15.04. I am unable to make Canon LBP3300 operational in ubuntu. Getting following error message is CUPS server error – Cleint-error-bad-request. Please find below the system output,  
 
 
 ***@***-desktop:~$ lsmod | grep usblp
 usblp                  20480  0  
 
 
 ***@***-desktop:~$ captstatusui -P LBP3300
 *** captstatusui Error: No Specified Printer ***
 
 
 ***@***-desktop:~$ sudo /etc/init.d/ccpd status
 /usr/sbin/ccpd: 1964 1962 1960 1957 1952 1950 1940 1927 1921 1913 1906 1904 1902 1900 1898 1896 1894 1892 1885 1883 1882 1881 1880 1877 1871 1866 1838 1829 1827 1825 1811 1805 1783 1776 1773 1771 1770 1767 1764 1762 1760 1759 1757 1754 1752 1745 1743 1740 1737 1723 1722 1720 1717 1716 1696 1692 1691 1674 1671 1647 1642 1631 1626 1617 1596 1587 1575 1567 1530 1497 1442 1422 1409 1394 1388 1385 1378 1367 1366 1256 1223 1199 1180 1148 1143 1142 923 898 896 838 810 778
 ***@***-desktop:~$ sudo ccpdadmin
 
 
 Usage:  
   ccpdadmin [-p Printer-name -o Printer-dev-path]
   ccpdadmin [-x Remove-Printer-name]
 
 
 
 
  CUPS_ConfigPath = /etc/cups/
  LOG Path        = None
  UI Port         = 59787
 
 
  Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status  
  ----------------------------------------------------------------------------
      [0]    : LBP3300     :          :                     : /dev/lp0     : invalid Spool Name
 
 
 
 
 ***@***-desktop:~$ tail -f /var/log/syslog
 Jun 26 12:30:17 ***-desktop systemd[1]: Started Hostname Service.
 Jun 26 12:30:34 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian/cndrvcups-common_2.60-1_amd64.deb" was not found, exec: system-config-printer.py, mime_type: application/x-deb
 Jun 26 12:30:34 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Downloads/5-Years%20&%203-Monthly%20Interest%20Braring%20Sanchayapatr5-Years%20&%203-Monthly%20Interest%20Braring%20Sanchayapatra.doc" was not found, exec: google-chrome-stable, mime_type: application/msword
 Jun 26 12:30:34 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/vmware/Windows%20Server%202012/Windows%20Server%202012.vmx" was not found, exec: vmplayer, mime_type: application/x-vmware-vm
 Jun 26 12:30:34 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Desktop/Untitled%201.ods" was not found, exec: google-chrome-stable, mime_type: application/vnd.oasis.opendocument.spreadsheet
 Jun 26 12:36:13 ***-desktop systemd[1]: Unit printer.target is not needed anymore. Stopping.
 Jun 26 12:36:13 ***-desktop systemd[1]: Stopped target Printer.
 Jun 26 12:36:13 ***-desktop systemd[1]: Stopping Printer.
 Jun 26 12:36:13 ***-desktop kernel: [ 3761.489975] usb 4-1.5: USB disconnect, device number 5
 Jun 26 12:36:13 ***-desktop kernel: [ 3761.490219] usblp0: removed
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.324528] usb 4-1.5: new high-speed USB device number 6 using ehci-pci
 Jun 26 12:36:30 ***-desktop mtp-probe: checking bus 4, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.5"
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.420733] usb 4-1.5: New USB device found, idVendor=04a9, idProduct=267e
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.420737] usb 4-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.420739] usb 4-1.5: Product: Canon CAPT USB Device
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.420741] usb 4-1.5: Manufacturer: Canon
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.420742] usb 4-1.5: SerialNumber: 000011B2GEaW
 Jun 26 12:36:30 ***-desktop kernel: [ 3778.422314] usblp 4-1.5:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04A9 pid 0x267E
 Jun 26 12:36:30 ***-desktop mtp-probe: bus: 4, device: 6 was not an MTP device
 Jun 26 12:36:30 ***-desktop systemd[1]: Reached target Printer.
 Jun 26 12:36:30 ***-desktop systemd[1]: Starting Printer.
 Jun 26 12:36:45 ***-desktop dbus[641]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
 Jun 26 12:36:45 ***-desktop systemd[1]: Starting Hostname Service...
 Jun 26 12:36:45 ***-desktop dbus[641]: [system] Successfully activated service 'org.freedesktop.hostname1'
 Jun 26 12:36:45 ***-desktop systemd[1]: Started Hostname Service.
 Jun 26 12:36:50 ***-desktop kernel: [ 3797.846590] usblp0: removed
 Jun 26 12:36:50 ***-desktop dbus[641]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
 Jun 26 12:36:50 ***-desktop dbus[641]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'
 Jun 26 12:36:59 ***-desktop kernel: [ 3806.742977] usblp 4-1.5:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04A9 pid 0x267E
 Jun 26 12:37:01 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian/cndrvcups-common_2.60-1_amd64.deb" was not found, exec: system-config-printer.py, mime_type: application/x-deb
 Jun 26 12:37:01 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Downloads/5-Years%20&%203-Monthly%20Interest%20Braring%20Sanchayapatr5-Years%20&%203-Monthly%20Interest%20Braring%20Sanchayapatra.doc" was not found, exec: google-chrome-stable, mime_type: application/msword
 Jun 26 12:37:01 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/vmware/Windows%20Server%202012/Windows%20Server%202012.vmx" was not found, exec: vmplayer, mime_type: application/x-vmware-vm
 Jun 26 12:37:01 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Desktop/Untitled%201.ods" was not found, exec: google-chrome-stable, mime_type: application/vnd.oasis.opendocument.spreadsheet
 Jun 26 12:37:04 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian/cndrvcups-common_2.60-1_amd64.deb" was not found, exec: system-config-printer.py, mime_type: application/x-deb
 Jun 26 12:37:04 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Downloads/5-Years%20&%203-Monthly%20Interest%20Braring%20Sanchayapatr5-Years%20&%203-Monthly%20Interest%20Braring%20Sanchayapatra.doc" was not found, exec: google-chrome-stable, mime_type: application/msword
 Jun 26 12:37:04 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/vmware/Windows%20Server%202012/Windows%20Server%202012.vmx" was not found, exec: vmplayer, mime_type: application/x-vmware-vm
 Jun 26 12:37:04 ***-desktop gnome-session[1350]: ** (zeitgeist-datahub:1836): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/***/Desktop/Untitled%201.ods" was not found, exec: google-chrome-stable, mime_type: application/vnd.oasis.opendocument.spreadsheet

---

### Post by akhtaruz on 2015-06-27
I am still hoping that someone in the community will help me to solve this problem. looking forward for your guys.

---

