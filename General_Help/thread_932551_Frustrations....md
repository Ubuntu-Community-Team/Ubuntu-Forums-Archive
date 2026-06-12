---
title: "Frustrations..."
date: 2008-09-28
forum: General Help
---

### Post by Prominence on 2008-09-28
I've been working with Ubuntu and my programs are freezing up and not working, and I don't know what's doing it...or causing it or what. Ubuntu always ran smoothing all of the other times.

---

### Post by solarwind on 2008-09-28
> **Prominence said:**
> I've been working with Ubuntu and my programs are freezing up and not working, and I don't know what's doing it...or causing it or what. Ubuntu always ran smoothing all of the other times.

Post the output of:
*sudo ps -A*
*sudo pstree*
*sudo df -h*
*sudo uname -a*
(Just type each line in the terminal and copy/paste the output. You might want to take a screenshot of pstree though.)

---

### Post by Prominence on 2008-09-28
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   46 ?        00:00:00 kblockd/0
   47 ?        00:00:00 kblockd/1
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  149 ?        00:00:00 kseriod
  191 ?        00:00:00 pdflush
  192 ?        00:00:00 pdflush
  193 ?        00:00:00 kswapd0
  234 ?        00:00:00 aio/0
  235 ?        00:00:00 aio/1
 1527 ?        00:00:00 ksuspend_usbd
 1530 ?        00:00:00 khubd
 1584 ?        00:00:00 ata/0
 1587 ?        00:00:00 ata/1
 1596 ?        00:00:00 ata_aux
 1602 ?        00:00:00 khpsbpkt
 2319 ?        00:00:00 scsi_eh_0
 2320 ?        00:00:00 scsi_eh_1
 2321 ?        00:00:00 scsi_eh_2
 2461 ?        00:00:00 knodemgrd_0
 2481 ?        00:00:00 scsi_eh_3
 2483 ?        00:00:00 scsi_eh_4
 2610 ?        00:00:00 kjournald
 2813 ?        00:00:00 udevd
 3215 ?        00:00:00 kmmcd
 3233 ?        00:00:00 kpsmoused
 4704 tty4     00:00:00 getty
 4705 tty5     00:00:00 getty
 4707 tty2     00:00:00 getty
 4709 tty3     00:00:00 getty
 4711 tty6     00:00:00 getty
 4895 ?        00:00:00 acpid
 4938 ?        00:00:00 kondemand/0
 4939 ?        00:00:00 kondemand/1
 5013 ?        00:00:00 syslogd
 5067 ?        00:00:00 dd
 5069 ?        00:00:00 klogd
 5091 ?        00:00:00 dbus-daemon
 5107 ?        00:00:00 NetworkManager
 5121 ?        00:00:00 NetworkManagerD
 5134 ?        00:00:00 system-tools-ba
 5154 ?        00:00:00 avahi-daemon
 5155 ?        00:00:00 avahi-daemon
 5197 ?        00:00:00 cupsd
 5253 ?        00:00:00 winbindd
 5290 ?        00:00:00 winbindd
 5292 ?        00:00:00 dhcdbd
 5311 ?        00:00:00 hald
 5314 ?        00:00:00 console-kit-dae
 5376 ?        00:00:00 hald-runner
 5390 ?        00:00:00 hald-addon-inpu
 5394 ?        00:00:00 hald-addon-cpuf
 5395 ?        00:00:00 hald-addon-acpi
 5423 ?        00:00:00 hald-addon-stor
 5446 ?        00:00:00 hcid
 5455 ?        00:00:00 btaddconn
 5456 ?        00:00:00 btdelconn
 5477 ?        00:00:00 bluetoothd-serv
 5483 ?        00:00:00 krfcommd
 5513 ?        00:00:00 bluetoothd-serv
 5546 ?        00:00:00 gdm
 5549 ?        00:00:00 gdm
 5553 tty7     00:01:38 Xorg
 5592 ?        00:00:00 atd
 5606 ?        00:00:00 cron
 5714 tty1     00:00:00 getty
 5753 ?        00:00:01 gconfd-2
 5755 ?        00:00:00 gnome-keyring-d
 5756 ?        00:00:01 x-session-manag
 5809 ?        00:00:00 seahorse-agent
 5811 ?        00:00:06 at-spi-registry
 5814 ?        00:00:00 bonobo-activati
 5820 ?        00:00:00 dbus-daemon
 5821 ?        00:00:01 gnome-settings-
 5836 ?        00:00:00 pulseaudio
 5839 ?        00:00:00 gconf-helper
 5852 ?        00:00:01 gnome-screensav
 5854 ?        00:00:04 gnome-panel
 5856 ?        00:00:10 nautilus
 5888 ?        00:00:00 gvfsd
 5921 ?        00:00:00 gvfs-fuse-daemo
 5929 ?        00:00:07 avant-window-na
 5930 ?        00:00:00 python
 5931 ?        00:00:00 python
 5932 ?        00:00:00 python
 5933 ?        00:00:00 python
 5934 ?        00:00:03 python
 5938 ?        00:00:01 python
 5939 ?        00:00:06 python
 5940 ?        00:00:00 python
 5941 ?        00:00:02 python
 5942 ?        00:00:01 python
 5943 ?        00:00:00 cameramonitor
 5944 ?        00:00:00 python
 5945 ?        00:00:00 python
 5946 ?        00:00:00 python
 5949 ?        00:00:00 python
 5950 ?        00:00:00 trackerd
 5952 ?        00:00:01 nm-applet
 5953 ?        00:00:04 beagled
 5956 ?        00:00:03 python
 5958 ?        00:00:00 tracker-applet
 5964 ?        00:00:01 python
 5965 ?        00:00:00 update-notifier
 5969 ?        00:00:00 python
 5971 ?        00:00:00 gnome-volume-ma
 5973 ?        00:00:00 gnome-power-man
 5982 ?        00:00:00 gvfsd-trash
 5990 ?        00:00:00 gvfsd-burn
 6065 ?        00:00:00 wpa_supplicant
 6071 ?        00:00:00 awn-applet-acti
 6076 ?        00:00:02 gnome-globalmen
 6084 ?        00:00:00 gnome-brightnes
 6086 ?        00:00:00 awn-applet-acti
 6089 ?        00:00:01 python
 6091 ?        00:00:00 python
 6115 ?        00:00:00 gnome-pty-helpe
 6117 pts/0    00:00:00 bash
 6139 ?        00:00:00 mixer_applet2
 6143 ?        00:00:01 deskbar-applet
 6177 ?        00:00:00 dhclient
 6193 ?        00:00:00 sh
 6194 ?        00:00:03 emerald
 6308 ?        00:00:02 beagled-helper
 6350 ?        00:00:00 gnome-vfs-daemo
 6451 ?        00:00:00 compiz
 6504 ?        00:00:08 compiz.real
 7085 ?        00:04:09 firefox
 9873 ?        00:00:00 gnome-terminal
 9880 ?        00:00:00 gnome-pty-helpe
 9881 pts/1    00:00:00 bash
 9920 pts/1    00:00:00 ps
 9947 ?        00:00:00 sh <defunct>
grayson@iGrayson:~$

---

### Post by Prominence on 2008-09-28
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9472;&#9472;3*[{NetworkManager}]
     &#9500;&#9472;NetworkManagerD
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;awn-applet-acti&#9472;&#9516;&#9472;bash
     &#9474;                 &#9500;&#9472;gnome-pty-helpe
     &#9474;                 &#9492;&#9472;{awn-applet-acti}
     &#9500;&#9472;awn-applet-acti
     &#9500;&#9472;beagled&#9472;&#9472;&#9472;7*[{beagled}]
     &#9500;&#9472;beagled-helper&#9472;&#9472;&#9472;5*[{beagled-helper}]
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;compiz&#9472;&#9472;&#9472;compiz.real
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;61*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dd
     &#9500;&#9472;deskbar-applet
     &#9500;&#9472;dhcdbd&#9472;&#9472;&#9472;dhclient
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;12*[{firefox}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;at-spi-registry
     &#9474;                             &#9500;&#9472;avant-window-na
     &#9474;                             &#9500;&#9472;cameramonitor&#9472;&#9472;&#9472;sh
     &#9474;                             &#9500;&#9472;gnome-panel
     &#9474;                             &#9500;&#9472;gnome-settings-&#9472;&#9516;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;                             &#9474;                 &#9474;            &#9492;&#9472;2*[{pulseau+
     &#9474;                             &#9474;                 &#9492;&#9472;{gnome-settings-}
     &#9474;                             &#9500;&#9472;nautilus
     &#9474;                             &#9500;&#9472;nm-applet
     &#9474;                             &#9500;&#9472;17*[python]
     &#9474;                             &#9500;&#9472;seahorse-agent
     &#9474;                             &#9500;&#9472;tracker-applet
     &#9474;                             &#9500;&#9472;trackerd&#9472;&#9472;&#9472;2*[{trackerd}]
     &#9474;                             &#9500;&#9472;update-notifier
     &#9474;                             &#9492;&#9472;{x-session-manag}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-brightnes
     &#9500;&#9472;gnome-globalmen
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daemo}]
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-cpuf
     &#9474;                    &#9500;&#9472;hald-addon-inpu
     &#9474;                    &#9492;&#9472;hald-addon-stor
     &#9500;&#9472;hcid&#9472;&#9472;&#9472;2*[bluetoothd-serv]
     &#9500;&#9472;klogd
     &#9500;&#9472;mixer_applet2&#9472;&#9472;&#9472;{mixer_applet2}
     &#9500;&#9472;2*[python]
     &#9500;&#9472;sh&#9472;&#9472;&#9472;emerald
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;udevd
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
     &#9492;&#9472;wpa_supplicant
grayson@iGrayson:~$

---

### Post by Prominence on 2008-09-28
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             107G  6.4G   95G   7% /
varrun                1.5G  116K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   52K  1.5G   1% /dev
devshm                1.5G   84K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile

---

### Post by Prominence on 2008-09-28
Linux iGrayson 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

### Post by solarwind on 2008-09-28
Kill awn, beagle and compiz, then try working, see if it works smoothly.

What did you do/install recently that might have caused this?

---

### Post by Prominence on 2008-09-28
I'm not really sure.

---

### Post by solarwind on 2008-09-28
> **Prominence said:**
> I'm not really sure.

What do you mean *you're not sure*? Did you install anything? Did you change anything?

If you can't be more descriptive and provide more information, I can't help you.

---

### Post by Prominence on 2008-09-30
I installed this global menu thing, but I turned it off, and nothing's changed.

---

### Post by oldos2er on 2008-09-30
> **Prominence said:**
> I've been working with Ubuntu and my programs are freezing up and not working, and I don't know what's doing it...or causing it or what. Ubuntu always ran smoothing all of the other times.

 Which programs? What are your hardware specs? Did you change anything recently?

---

### Post by Prominence on 2008-10-01
Pidgin, Songbird/Rhythmbox, Firefox

And I didn't

---

### Post by patrickballeux on 2008-10-01
Have you looked into your system monitor to see wich process is taking 100% CPU?

Or you can run from the command line "top" which will show you the same thing but in a terminal.

You could then do a copy/paste here...

---

### Post by solarwind on 2008-10-01
Go into the gnome system monitor and take a screenshot of all the tabs for me, I have a suspicion it's a process taking a lot of cpu or a lot of memory causing the swap to be heavily utilized.

---

### Post by Prominence on 2008-10-02
It's working better again, it was the Global Menu thing, got rid of it for good.

---

### Post by solarwind on 2008-10-02
> **Prominence said:**
> It's working better again, it was the Global Menu thing, got rid of it for good.

How did you uninstall it? I installed it too and I don't want it anymore.

---

### Post by patrickballeux on 2008-10-03
To remove any software, open "Synaptic" in the administration menu, search of the software by it's name, and select it for removal.  Then click apply.

If you compiled from source, generally, you simply have to do from the compiled binaries:

> sudo make uninstall

Assuming that you installed by doing:

> ./configure
> make
> sudo make install

---

