---
title: "Major failure of software management system"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by C-130 on 2009-03-07
I have just recieved this error whilst searching for a codec to play MP3 files:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

It wont even let me run synaptic. 

Please help.

---

### Post by Partyboi2 on 2009-03-07
Deleted

---

### Post by C-130 on 2009-03-07
I am given this by the terminal:

colin@colin-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
colin@colin-desktop:~$ 


I am not sure how to manually run dpkg - -configure -a

Any help?

---

### Post by Partyboi2 on 2009-03-07
Put sudo in front of it so type
```
sudo dpkg --configure -a
```

---

### Post by C-130 on 2009-03-07
Now if only I knew where this package was. I recieve the following output from the terminal

colin@colin-desktop:~$ sudo dpkg - -configure -a
[sudo] password for colin: 
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
colin@colin-desktop:~$  dpkg --help
Usage: dpkg [<option> ...] <command>

Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  --triggers-only    <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --print-architecture             Print dpkg architecture.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.

  -h|--help                        Show this help message.
  --version                        Show the version.
  --license|--licence              Show the copyright licensing terms.

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep.

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --[no-]triggers            Skip or force consequential trigger processing.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.

Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.
colin@colin-desktop:~$ u
bash: u: command not found
colin@colin-desktop:~$

---

### Post by taurus on 2009-03-07
> **Partyboi2 said:**
> Put sudo in front of it so type
```
sudo dpkg - -configure -a
```

There should not be a space between the - -configure.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Partyboi2 on 2009-03-07
Sorry that was my mistake I had a space between the --
so
```
sudo dpkg --configure -a
```

---

### Post by C-130 on 2009-03-07
I keep being told unable to lock  the administration directory

---

### Post by taurus on 2009-03-07
Close update manager, add/remove, or synaptic first before you run those commands from a terminal.

---

### Post by C-130 on 2009-03-07
> **taurus said:**
> Close update manager, add/remove, or synaptic first before you run those commands from a terminal.

I do not have any of these running. The only thing running close to updates is the notifier but I can not find a way to close that!

---

### Post by C-130 on 2009-03-07
This si what I have running

ps -e
colin@colin-desktop:~$ ps -e
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
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  147 ?        00:00:00 cqueue
  151 ?        00:00:00 kseriod
  196 ?        00:00:00 pdflush
  197 ?        00:00:00 pdflush
  198 ?        00:00:00 kswapd0
  240 ?        00:00:00 aio/0
  241 ?        00:00:00 aio/1
 1264 ?        00:00:00 ksuspend_usbd
 1265 ?        00:00:00 khubd
 1338 ?        00:00:00 ata/0
 1342 ?        00:00:00 ata/1
 1344 ?        00:00:00 ata_aux
 2055 ?        00:00:00 scsi_eh_0
 2056 ?        00:00:00 scsi_eh_1
 2093 ?        00:00:00 scsi_eh_2
 2094 ?        00:00:00 scsi_eh_3
 2159 ?        00:00:00 scsi_eh_4
 2160 ?        00:00:00 usb-storage
 2190 ?        00:00:03 scsi_eh_5
 2195 ?        00:00:00 scsi_eh_6
 2351 ?        00:00:00 kjournald
 2526 ?        00:00:00 udevd
 3043 ?        00:00:00 kpsmoused
 3514 ?        00:00:00 saa7133[0]
 3525 ?        00:00:01 rt61pci
 4704 tty4     00:00:00 getty
 4705 tty5     00:00:00 getty
 4708 tty2     00:00:00 getty
 4709 tty3     00:00:00 getty
 4710 tty6     00:00:00 getty
 4901 ?        00:00:00 acpid
 4932 ?        00:00:00 kondemand/0
 4933 ?        00:00:00 kondemand/1
 5028 ?        00:00:00 syslogd
 5082 ?        00:00:00 dd
 5084 ?        00:00:00 klogd
 5107 ?        00:00:00 dbus-daemon
 5129 ?        00:00:00 avahi-daemon
 5130 ?        00:00:00 avahi-daemon
 5177 ?        00:00:00 cupsd
 5231 ?        00:00:00 winbindd
 5253 ?        00:00:00 winbindd
 5254 ?        00:00:00 hald
 5257 ?        00:00:00 console-kit-dae
 5258 ?        00:00:00 hald-runner
 5340 ?        00:00:00 hald-addon-inpu
 5351 ?        00:00:00 hald-addon-cpuf
 5352 ?        00:00:00 hald-addon-acpi
 5359 ?        00:00:00 hald-addon-stor
 5362 ?        00:00:00 hald-addon-stor
 5372 ?        00:00:00 hald-addon-stor
 5375 ?        00:00:00 hald-addon-stor
 5378 ?        00:00:00 hald-addon-stor
 5381 ?        00:00:00 hald-addon-stor
 5430 ?        00:00:00 bluetoothd
 5437 ?        00:00:00 btaddconn
 5438 ?        00:00:00 btdelconn
 5469 ?        00:00:00 krfcommd
 5492 ?        00:00:00 NetworkManager
 5502 ?        00:00:00 wpa_supplicant
 5506 ?        00:00:00 nm-system-setti
 5530 ?        00:00:00 gdm
 5533 ?        00:00:00 gdm
 5536 tty7     00:04:41 Xorg
 5555 ?        00:00:00 system-tools-ba
 5589 ?        00:00:00 atd
 5619 ?        00:00:00 cron
 5702 ?        00:00:00 x-session-manag
 5739 tty1     00:00:00 getty
 5856 ?        00:00:00 ssh-agent
 5859 ?        00:00:00 dbus-launch
 5860 ?        00:00:00 dbus-daemon
 5863 ?        00:00:08 pulseaudio
 5869 ?        00:00:00 gconf-helper
 5871 ?        00:00:03 gconfd-2
 5883 ?        00:00:00 seahorse-agent
 5887 ?        00:00:00 gvfsd
 5890 ?        00:00:00 gnome-keyring-d
 5896 ?        00:00:00 gnome-keyring-d
 5900 ?        00:00:00 gvfs-fuse-daemo
 5904 ?        00:00:00 gnome-settings-
 5905 ?        00:00:07 metacity
 5910 ?        00:00:08 gnome-panel
 5911 ?        00:00:56 nautilus
 5916 ?        00:00:00 bonobo-activati
 5933 ?        00:00:00 gvfs-hal-volume
 5939 ?        00:00:00 gvfs-gphoto2-vo
 5941 ?        00:00:03 gnome-screensav
 5943 ?        00:00:00 gvfsd-burn
 5946 ?        00:00:00 trashapplet
 5949 ?        00:00:00 gvfsd-trash
 5955 ?        00:00:00 fast-user-switc
 5959 ?        00:00:00 mixer_applet2
 5970 ?        00:00:00 nm-applet
 5971 ?        00:00:00 update-notifier
 5973 ?        00:00:00 evolution-alarm
 5975 ?        00:00:00 trackerd
 5976 ?        00:00:00 bluetooth-apple
 5983 ?        00:00:00 tracker-applet
 5985 ?        00:00:00 python
 5989 ?        00:00:00 gnome-power-man
 6011 ?        00:00:00 dhclient
 6018 ?        00:00:00 notification-da
 6110 ?        00:00:00 evolution-data-
 6116 ?        00:00:00 evolution-excha
 6253 ?        00:00:00 gvfsd-computer
 6349 ?        00:00:00 cpufreq-applet
 6354 ?        00:00:05 geyes_applet2
 6360 ?        00:00:01 tomboy
 6471 ?        00:00:00 seahorse-daemon
 6587 ?        00:00:01 gnome-terminal
 6589 ?        00:00:00 gnome-pty-helpe
 6616 ?        00:00:01 apt-get
 6646 pts/1    00:00:00 dpkg
 6673 pts/1    00:00:00 frontend
 6679 pts/1    00:00:00 preinst
 6681 pts/1    00:00:00 whiptail
 6682 pts/2    00:00:00 bash
 6780 ?        00:00:00 gvfsd-http
 6787 ?        00:00:33 firefox
 6851 pts/2    00:00:00 ps

---

### Post by Partyboi2 on 2009-03-07
You have apt-get running
```
sudo killall apt-get
```

---

### Post by C-130 on 2009-03-07
> **Partyboi2 said:**
> You have apt-get running
```
sudo killall apt-get
```

Thanks that ahs allowed me to do some things such as run the codes given to me. I'll report back on whether the problem is solved.

Problem is not solved. i get further before I receive the following eror:

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

This si what i ahve running (after error produced)

colin@colin-desktop:~$ ps -e
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
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  147 ?        00:00:00 cqueue
  151 ?        00:00:00 kseriod
  196 ?        00:00:00 pdflush
  197 ?        00:00:00 pdflush
  198 ?        00:00:00 kswapd0
  240 ?        00:00:00 aio/0
  241 ?        00:00:00 aio/1
 1264 ?        00:00:00 ksuspend_usbd
 1265 ?        00:00:00 khubd
 1338 ?        00:00:00 ata/0
 1342 ?        00:00:01 ata/1
 1344 ?        00:00:00 ata_aux
 2055 ?        00:00:00 scsi_eh_0
 2056 ?        00:00:00 scsi_eh_1
 2093 ?        00:00:00 scsi_eh_2
 2094 ?        00:00:00 scsi_eh_3
 2159 ?        00:00:00 scsi_eh_4
 2160 ?        00:00:00 usb-storage
 2190 ?        00:00:03 scsi_eh_5
 2195 ?        00:00:00 scsi_eh_6
 2351 ?        00:00:00 kjournald
 2526 ?        00:00:00 udevd
 3043 ?        00:00:00 kpsmoused
 3514 ?        00:00:00 saa7133[0]
 3525 ?        00:00:02 rt61pci
 4704 tty4     00:00:00 getty
 4705 tty5     00:00:00 getty
 4708 tty2     00:00:00 getty
 4709 tty3     00:00:00 getty
 4710 tty6     00:00:00 getty
 4901 ?        00:00:00 acpid
 4932 ?        00:00:00 kondemand/0
 4933 ?        00:00:00 kondemand/1
 5028 ?        00:00:00 syslogd
 5082 ?        00:00:00 dd
 5084 ?        00:00:00 klogd
 5107 ?        00:00:00 dbus-daemon
 5129 ?        00:00:00 avahi-daemon
 5130 ?        00:00:00 avahi-daemon
 5177 ?        00:00:00 cupsd
 5231 ?        00:00:00 winbindd
 5253 ?        00:00:00 winbindd
 5254 ?        00:00:00 hald
 5257 ?        00:00:00 console-kit-dae
 5258 ?        00:00:00 hald-runner
 5340 ?        00:00:00 hald-addon-inpu
 5351 ?        00:00:00 hald-addon-cpuf
 5352 ?        00:00:00 hald-addon-acpi
 5359 ?        00:00:00 hald-addon-stor
 5362 ?        00:00:00 hald-addon-stor
 5372 ?        00:00:00 hald-addon-stor
 5375 ?        00:00:00 hald-addon-stor
 5378 ?        00:00:00 hald-addon-stor
 5381 ?        00:00:00 hald-addon-stor
 5430 ?        00:00:00 bluetoothd
 5437 ?        00:00:00 btaddconn
 5438 ?        00:00:00 btdelconn
 5469 ?        00:00:00 krfcommd
 5492 ?        00:00:00 NetworkManager
 5502 ?        00:00:00 wpa_supplicant
 5506 ?        00:00:00 nm-system-setti
 5530 ?        00:00:00 gdm
 5533 ?        00:00:00 gdm
 5536 tty7     00:05:36 Xorg
 5555 ?        00:00:00 system-tools-ba
 5589 ?        00:00:00 atd
 5619 ?        00:00:00 cron
 5702 ?        00:00:00 x-session-manag
 5739 tty1     00:00:00 getty
 5856 ?        00:00:00 ssh-agent
 5859 ?        00:00:00 dbus-launch
 5860 ?        00:00:00 dbus-daemon
 5863 ?        00:00:08 pulseaudio
 5869 ?        00:00:00 gconf-helper
 5871 ?        00:00:03 gconfd-2
 5883 ?        00:00:00 seahorse-agent
 5887 ?        00:00:00 gvfsd
 5890 ?        00:00:00 gnome-keyring-d
 5896 ?        00:00:00 gnome-keyring-d
 5900 ?        00:00:00 gvfs-fuse-daemo
 5904 ?        00:00:01 gnome-settings-
 5905 ?        00:00:08 metacity
 5910 ?        00:00:10 gnome-panel
 5911 ?        00:00:56 nautilus
 5916 ?        00:00:00 bonobo-activati
 5933 ?        00:00:00 gvfs-hal-volume
 5939 ?        00:00:00 gvfs-gphoto2-vo
 5941 ?        00:00:04 gnome-screensav
 5943 ?        00:00:00 gvfsd-burn
 5946 ?        00:00:00 trashapplet
 5949 ?        00:00:00 gvfsd-trash
 5955 ?        00:00:00 fast-user-switc
 5959 ?        00:00:00 mixer_applet2
 5970 ?        00:00:00 nm-applet
 5971 ?        00:00:00 update-notifier
 5973 ?        00:00:00 evolution-alarm
 5975 ?        00:00:00 trackerd
 5976 ?        00:00:00 bluetooth-apple
 5983 ?        00:00:00 tracker-applet
 5985 ?        00:00:00 python
 5989 ?        00:00:00 gnome-power-man
 6011 ?        00:00:00 dhclient
 6018 ?        00:00:00 notification-da
 6110 ?        00:00:00 evolution-data-
 6116 ?        00:00:00 evolution-excha
 6253 ?        00:00:00 gvfsd-computer
 6349 ?        00:00:00 cpufreq-applet
 6354 ?        00:00:06 geyes_applet2
 6360 ?        00:00:01 tomboy
 6471 ?        00:00:00 seahorse-daemon
 6587 ?        00:00:01 gnome-terminal
 6589 ?        00:00:00 gnome-pty-helpe
 6682 pts/2    00:00:00 bash
 6780 ?        00:00:00 gvfsd-http
 6787 ?        00:01:32 firefox
 6960 pts/2    00:00:00 apt-get
 6982 pts/0    00:00:00 dpkg
 6989 pts/0    00:00:00 frontend
 6996 pts/0    00:00:00 preinst
 6998 pts/0    00:00:00 whiptail
 7014 ?        00:00:00 totem
 7020 ?        00:00:02 gstreamer-codec
 7032 ?        00:00:00 gksu
 7033 ?        00:00:00 synaptic
 7034 pts/1    00:00:00 bash
 7052 pts/1    00:00:00 ps
colin@colin-desktop:~$

---

### Post by taurus on 2009-03-07
> **C-130 said:**
> Thanks that ahs allowed me to do some things such as run the codes given to me. I'll report back on whether the problem is solved.

Problem is not solved. i get further before I receive the following eror:

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

This si what i ahve running (after error produced)

colin@colin-desktop:~$ ps -e
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
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  147 ?        00:00:00 cqueue
  151 ?        00:00:00 kseriod
  196 ?        00:00:00 pdflush
  197 ?        00:00:00 pdflush
  198 ?        00:00:00 kswapd0
  240 ?        00:00:00 aio/0
  241 ?        00:00:00 aio/1
 1264 ?        00:00:00 ksuspend_usbd
 1265 ?        00:00:00 khubd
 1338 ?        00:00:00 ata/0
 1342 ?        00:00:01 ata/1
 1344 ?        00:00:00 ata_aux
 2055 ?        00:00:00 scsi_eh_0
 2056 ?        00:00:00 scsi_eh_1
 2093 ?        00:00:00 scsi_eh_2
 2094 ?        00:00:00 scsi_eh_3
 2159 ?        00:00:00 scsi_eh_4
 2160 ?        00:00:00 usb-storage
 2190 ?        00:00:03 scsi_eh_5
 2195 ?        00:00:00 scsi_eh_6
 2351 ?        00:00:00 kjournald
 2526 ?        00:00:00 udevd
 3043 ?        00:00:00 kpsmoused
 3514 ?        00:00:00 saa7133[0]
 3525 ?        00:00:02 rt61pci
 4704 tty4     00:00:00 getty
 4705 tty5     00:00:00 getty
 4708 tty2     00:00:00 getty
 4709 tty3     00:00:00 getty
 4710 tty6     00:00:00 getty
 4901 ?        00:00:00 acpid
 4932 ?        00:00:00 kondemand/0
 4933 ?        00:00:00 kondemand/1
 5028 ?        00:00:00 syslogd
 5082 ?        00:00:00 dd
 5084 ?        00:00:00 klogd
 5107 ?        00:00:00 dbus-daemon
 5129 ?        00:00:00 avahi-daemon
 5130 ?        00:00:00 avahi-daemon
 5177 ?        00:00:00 cupsd
 5231 ?        00:00:00 winbindd
 5253 ?        00:00:00 winbindd
 5254 ?        00:00:00 hald
 5257 ?        00:00:00 console-kit-dae
 5258 ?        00:00:00 hald-runner
 5340 ?        00:00:00 hald-addon-inpu
 5351 ?        00:00:00 hald-addon-cpuf
 5352 ?        00:00:00 hald-addon-acpi
 5359 ?        00:00:00 hald-addon-stor
 5362 ?        00:00:00 hald-addon-stor
 5372 ?        00:00:00 hald-addon-stor
 5375 ?        00:00:00 hald-addon-stor
 5378 ?        00:00:00 hald-addon-stor
 5381 ?        00:00:00 hald-addon-stor
 5430 ?        00:00:00 bluetoothd
 5437 ?        00:00:00 btaddconn
 5438 ?        00:00:00 btdelconn
 5469 ?        00:00:00 krfcommd
 5492 ?        00:00:00 NetworkManager
 5502 ?        00:00:00 wpa_supplicant
 5506 ?        00:00:00 nm-system-setti
 5530 ?        00:00:00 gdm
 5533 ?        00:00:00 gdm
 5536 tty7     00:05:36 Xorg
 5555 ?        00:00:00 system-tools-ba
 5589 ?        00:00:00 atd
 5619 ?        00:00:00 cron
 5702 ?        00:00:00 x-session-manag
 5739 tty1     00:00:00 getty
 5856 ?        00:00:00 ssh-agent
 5859 ?        00:00:00 dbus-launch
 5860 ?        00:00:00 dbus-daemon
 5863 ?        00:00:08 pulseaudio
 5869 ?        00:00:00 gconf-helper
 5871 ?        00:00:03 gconfd-2
 5883 ?        00:00:00 seahorse-agent
 5887 ?        00:00:00 gvfsd
 5890 ?        00:00:00 gnome-keyring-d
 5896 ?        00:00:00 gnome-keyring-d
 5900 ?        00:00:00 gvfs-fuse-daemo
 5904 ?        00:00:01 gnome-settings-
 5905 ?        00:00:08 metacity
 5910 ?        00:00:10 gnome-panel
 5911 ?        00:00:56 nautilus
 5916 ?        00:00:00 bonobo-activati
 5933 ?        00:00:00 gvfs-hal-volume
 5939 ?        00:00:00 gvfs-gphoto2-vo
 5941 ?        00:00:04 gnome-screensav
 5943 ?        00:00:00 gvfsd-burn
 5946 ?        00:00:00 trashapplet
 5949 ?        00:00:00 gvfsd-trash
 5955 ?        00:00:00 fast-user-switc
 5959 ?        00:00:00 mixer_applet2
 5970 ?        00:00:00 nm-applet
 5971 ?        00:00:00 update-notifier
 5973 ?        00:00:00 evolution-alarm
 5975 ?        00:00:00 trackerd
 5976 ?        00:00:00 bluetooth-apple
 5983 ?        00:00:00 tracker-applet
 5985 ?        00:00:00 python
 5989 ?        00:00:00 gnome-power-man
 6011 ?        00:00:00 dhclient
 6018 ?        00:00:00 notification-da
 6110 ?        00:00:00 evolution-data-
 6116 ?        00:00:00 evolution-excha
 6253 ?        00:00:00 gvfsd-computer
 6349 ?        00:00:00 cpufreq-applet
 6354 ?        00:00:06 geyes_applet2
 6360 ?        00:00:01 tomboy
 6471 ?        00:00:00 seahorse-daemon
 6587 ?        00:00:01 gnome-terminal
 6589 ?        00:00:00 gnome-pty-helpe
 6682 pts/2    00:00:00 bash
 6780 ?        00:00:00 gvfsd-http
 6787 ?        00:01:32 firefox
 **[COLOR="Red"]6960 pts/2    00:00:00 apt-get[/COLOR]**
 **[COLOR="Red"]6982 pts/0    00:00:00 dpkg[/COLOR]**
 6989 pts/0    00:00:00 frontend
 6996 pts/0    00:00:00 preinst
 6998 pts/0    00:00:00 whiptail
 7014 ?        00:00:00 totem
 7020 ?        00:00:02 gstreamer-codec
 7032 ?        00:00:00 gksu
 **[COLOR="Red"]7033 ?        00:00:00 synaptic[/COLOR]**
 7034 pts/1    00:00:00 bash
 7052 pts/1    00:00:00 ps
colin@colin-desktop:~$

Do you see those three processes?

---

### Post by C-130 on 2009-03-07
I did about 10 mins after posting. I ended two I had failed to see the dpkg process. I think some of the problems are fixed for now. i was able to update and install the plug in for MP3s to play.

---

