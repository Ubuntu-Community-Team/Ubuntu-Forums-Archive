---
title: "Getting more out of a netbook's RAM"
date: 2009-09-04
forum: Hardware
---

### Post by Psychopump on 2009-09-04
Hello all,

I have a Packard Bell Dot M netbook. It has the 1.33GHz Intel Atom processor with the poulsbo chipset. I have upgraded the RAM to 2Gb.
It is running MintLinux Gloria (Jaunty).

Whenever I use the netbook intensively, conky tells me that the processor is maxing out at 100% and causing things to go awry. At the same time the netbook is only using about 16% of it's available RAM, and NEVER more than 20%.

Is there any way to put the RAM to more use, so the processor has some more room to breathe?

---

### Post by scragar on 2009-09-04
Run top, and see what's eating up your cpu power:
```
top
```
Type `q` to get out of top btw.

---

### Post by Psychopump on 2009-09-04
> **scragar said:**
> Run top, and see what's eating up your cpu power:
```
top
```
Type `q` to get out of top btw.

Thanks for your quick reply!

```

loki@loki-laptop ~ $ top

top - 13:20:18 up 20:33,  2 users,  load average: 0.94, 1.17, 1.32
Tasks: 125 total,   2 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.0%us,  3.2%sy,  0.0%ni, 78.0%id,  0.0%wa,  0.3%hi,  2.6%si,  0.0%st
Mem:   2052436k total,  1998036k used,    54400k free,    57412k buffers
Swap:   979956k total,     4496k used,   975460k free,  1648792k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
14283 root      20   0 94572  36m 7704 R   25  1.8 126:55.31 Xorg                                                                                                       
14654 loki      20   0  262m  29m 8708 S    7  1.5  68:46.38 transmission                                                                                               
24027 loki      20   0 33852  14m 9712 S    4  0.7   0:03.47 gnome-terminal                                                                                             
23620 loki      20   0 10340 2896 2132 S    3  0.1   0:37.80 conky                                                                                                      
23790 loki      20   0  227m  92m  32m S    2  4.6   3:45.59 firefox                                                                                                    
14616 loki      20   0 17660 6472 4896 S    0  0.3   0:21.10 gnome-screensav                                                                                            
24044 loki      20   0  2448 1192  912 R    0  0.1   0:00.73 top                                                                                                        
    1 root      20   0  1908  428  360 S    0  0.0   0:02.05 init                                                                                                       
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                   
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.06 migration/0                                                                                                
    4 root      15  -5     0    0    0 S    0  0.0   0:10.64 ksoftirqd/0                                                                                                
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                 
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.06 migration/1                                                                                                
    7 root      15  -5     0    0    0 S    0  0.0   0:13.25 ksoftirqd/1                                                                                                
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                 
    9 root      15  -5     0    0    0 S    0  0.0  11:12.28 events/0                                                                                                   
   10 root      15  -5     0    0    0 S    0  0.0   0:00.26 events/1                                                                                                   

```

---

### Post by scragar on 2009-09-04
You aren't using 100% of your CPU power there... Sounds likely then to be an I/O problem(input/output).

```
sudo aptitude install iotop
iotop
```iotop will show what applications are generating wait.

---

### Post by Psychopump on 2009-09-04
This has deleted 160 packages!
Xchat has gone, loads of perl stuff....HELP!!??

```
sudo aptitude install iotop
 ________________________________________
< You have a truly strong individuality. >
 ----------------------------------------
       \   ,__,
        \  (oo)____
           (__)    )\
              ||--|| *
loki@loki-laptop ~ $ sudo aptitude install iotop
[sudo] password for loki: 
loki@loki-laptop ~ $ sudo aptitude install iotop
[sudo] password for loki: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  iotop 
The following packages will be REMOVED:
  aptoncd{u} bsh{u} calendar-timezones{u} compiz-check{u} 
  compizconfig-settings-manager{u} cups-pdf{u} deskbar-applet{u} 
  envyng-core{u} envyng-gtk{u} flegita{u} gecko-mediaplayer{u} 
  gimp-help-common{u} gimp-help-en{u} giver{u} gnome-do{u} gnome-mplayer{u} 
  gtk2-engines-aurora{u} gtk2-engines-candido{u} 
  gtk2-engines-ubuntulooks{u} gufw{u} inxi{u} java-common{u} libamrnb3{u} 
  libamrwb3{u} libavahi1.0-cil{u} libdiscid0{u} libdvdcss2{u} 
  libgconfmm-2.6-1c2{u} libggi-target-x{u} libggi2{u} libgii1{u} 
  libgii1-target-x{u} libglademm-2.4-1c2a{u} libgnomedesktop2.20-cil{u} 
  libgnomescan-common{u} libgnomescan0{u} libgnomescanui-common{u} 
  libgnomescanui0{u} libhsqldb-java{u} libjline-java{u} liblzo2-2{u} 
  libmoon{u} libmusicbrainz3-6{u} libnotify-bin{u} libnotify0.4-cil{u} 
  libopenal1{u} libpulse-mainloop-glib0{u} librsvg2-2.18-cil{u} 
  libservlet2.4-java{u} libsvga1{u} libunshield0{u} libwnck2.20-cil{u} 
  linuxmint-keyring{u} localechooser-data{u} mint-artwork-gnome{u} 
  mint-search-addon{u} mintbackup{u} mintdesktop{u} mintinstall{u} 
  mintmenu{u} mintnanny{u} mintupload{u} mintwelcome{u} mintwifi{u} 
  moonlight-plugin-core{u} moonlight-plugin-mozilla{u} mplayer{u} 
  mplayer-skins{u} nautilus-actions{u} nautilus-open-terminal{u} 
  nautilus-wallpaper{u} ndisgtk{u} ndiswrapper-common{u} 
  ndiswrapper-utils-1.9{u} odbcinst1debian1{u} openoffice.org-base{u} 
  openoffice.org-help-en-gb{u} openoffice.org-help-en-us{u} 
  openoffice.org-java-common{u} openoffice.org-l10n-en-gb{u} 
  openoffice.org-l10n-en-za{u} padevchooser{u} paman{u} paprefs{u} 
  pavucontrol{u} pavumeter{u} pulseaudio-module-zeroconf{u} 
  python-beagle{u} python-compizconfig{u} python-crypto{u} 
  python-paramiko{u} python-pexpect{u} samba{u} simple-ccsm{u} 
  sun-java6-bin{u} sun-java6-jre{u} sun-java6-plugin{u} tcl8.4{u} 
  unixodbc{u} unshield{u} xchat{u} xchat-common{u} 
0 packages upgraded, 1 newly installed, 102 to remove and 216 not upgraded.
Need to get 12.8kB of archives. After unpacking 367MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com jaunty/universe iotop 0.2-3 [12.8kB]
Fetched 12.8kB in 5s (2533B/s)
(Reading database ... 108337 files and directories currently installed.)
Removing aptoncd ...
Removing bsh ...
Removing calendar-timezones ...
Removing compiz-check ...
Removing simple-ccsm ...
Removing compizconfig-settings-manager ...
Removing cups-pdf ...
Removing mintmenu ...
Removing deskbar-applet ...
Removing envyng-gtk ...
Removing envyng-core ...
Removing flegita ...
Removing gecko-mediaplayer ...
Removing gimp-help-en ...
Removing gimp-help-common ...
Removing giver ...
Removing gnome-do ...
Removing gnome-mplayer ...
Removing mint-artwork-gnome ...
Removing gtk2-engines-aurora ...
Removing gtk2-engines-candido ...
Removing gtk2-engines-ubuntulooks ...
Removing gufw ...
Removing inxi ...
Removing sun-java6-plugin ...
Removing openoffice.org-base ...
Removing openoffice.org-java-common ...
Removing libhsqldb-java ...
Removing libservlet2.4-java ...
Removing libjline-java ...
Removing mplayer ...
Removing libamrnb3 ...
Removing libamrwb3 ...
Removing libavahi1.0-cil ...
Removing libavahi1.0-cil from Mono
Removing libmusicbrainz3-6 ...
Removing libdiscid0 ...
Removing libdvdcss2 ...
Removing padevchooser ...
Removing paprefs ...
Removing libgconfmm-2.6-1c2 ...
Removing libggi-target-x ...
Removing libggi2 ...
Removing libgii1-target-x ...
Removing libgii1 ...
Removing pavucontrol ...
Removing paman ...
Removing libglademm-2.4-1c2a ...
Removing libgnomedesktop2.20-cil ...
Removing libgnomescanui0 ...
Removing libgnomescan0 ...
Removing libgnomescan-common ...
Removing libgnomescanui-common ...
Removing liblzo2-2 ...
Removing moonlight-plugin-mozilla ...
Removing moonlight-plugin-core ...
Removing libmoon ...
Removing mintinstall ...
Removing libnotify-bin ...
Removing libnotify0.4-cil ...
Removing libnotify0.4-cil from Mono
Removing libopenal1 ...
Removing pavumeter ...
Removing libpulse-mainloop-glib0 ...
Removing librsvg2-2.18-cil ...
Removing libsvga1 ...
Removing unshield ...
Removing libunshield0 ...
Removing libwnck2.20-cil ...
Removing linuxmint-keyring ...
OK
Removing localechooser-data ...
Removing mint-search-addon ...
Removing mintbackup ...
Removing mintdesktop ...
sed: can't read /etc/gdm/PostLogin/Default: No such file or directory
dpkg: error processing mintdesktop (--remove):
 subprocess pre-removal script returned error exit status 2
Removing mintnanny ...
Removing mintupload ...
Removing mintwelcome ...
Removing mintwifi ...
Removing mplayer-skins ...
Removing nautilus-actions ...
Removing nautilus-open-terminal ...
Removing nautilus-wallpaper ...
Removing ndisgtk ...
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
Removing openoffice.org-help-en-gb ...
Removing openoffice.org-help-en-us ...
Removing openoffice.org-l10n-en-gb ...
Removing openoffice.org-l10n-en-za ...
Removing pulseaudio-module-zeroconf ...
Removing python-beagle ...
Removing python-compizconfig ...
Removing python-paramiko ...
Removing python-crypto ...
Removing python-pexpect ...
Removing samba ...
 * Stopping Samba daemons                                                [ OK ] 
Removing xchat ...
Removing tcl8.4 ...
Removing xchat-common ...
Removing sun-java6-bin ...
Removing unixodbc ...
qRemoving odbcinst1debian1 ...
Removing sun-java6-jre ...
Removing java-common ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 3 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for shared-mime-info ...
Processing triggers for python-support ...
Processing triggers for ufw ...
Errors were encountered while processing:
 mintdesktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

Current status: 217 updates [-18].
loki@loki-laptop ~ $ 


```

---

### Post by scragar on 2009-09-04
Installing iotop shouldn't have done that, I'm really quite confused as to why it did.
```

sudo apt-get install \
  aptoncd bsh calendar-timezones compiz-check \
  compizconfig-settings-manager cups-pdf deskbar-applet \
  envyng-core envyng-gtk flegita gecko-mediaplayer \
  gimp-help-common gimp-help-en giver gnome-do gnome-mplayer \
  gtk2-engines-aurora gtk2-engines-candido \
  gtk2-engines-ubuntulooks gufw inxi java-common libamrnb3 \
  libamrwb3 libavahi1.0-cil libdiscid0 libdvdcss2 \
  libgconfmm-2.6-1c2 libggi-target-x libggi2 libgii1 \
  libgii1-target-x libglademm-2.4-1c2a libgnomedesktop2.20-cil \
  libgnomescan-common libgnomescan0 libgnomescanui-common \
  libgnomescanui0 libhsqldb-java libjline-java liblzo2-2 \
  libmoon libmusicbrainz3-6 libnotify-bin libnotify0.4-cil \
  libopenal1 libpulse-mainloop-glib0 librsvg2-2.18-cil \
  libservlet2.4-java libsvga1 libunshield0 libwnck2.20-cil \
  linuxmint-keyring localechooser-data mint-artwork-gnome \
  mint-search-addon mintbackup mintdesktop mintinstall \
  mintmenu mintnanny mintupload mintwelcome mintwifi \
  moonlight-plugin-core moonlight-plugin-mozilla mplayer \
  mplayer-skins nautilus-actions nautilus-open-terminal \
  nautilus-wallpaper ndisgtk ndiswrapper-common \
  ndiswrapper-utils-1.9 odbcinst1debian1 openoffice.org-base \
  openoffice.org-help-en-gb openoffice.org-help-en-us \
  openoffice.org-java-common openoffice.org-l10n-en-gb \
  openoffice.org-l10n-en-za padevchooser paman paprefs \
  pavucontrol pavumeter pulseaudio-module-zeroconf \
  python-beagle python-compizconfig python-crypto \
  python-paramiko python-pexpect samba simple-ccsm \
  sun-java6-bin sun-java6-jre sun-java6-plugin tcl8.4 \
  unixodbc unshield xchat xchat-common
```
Copy and paste that monstrosity back in to reinstall what it removed. I'm truely sorry about that, I had no idea it would want to remove all of those packages.

---

### Post by Psychopump on 2009-09-04
> **scragar said:**
> Installing iotop shouldn't have done that, I'm really quite confused as to why it did.

Copy and paste that monstrosity back in to reinstall what it removed. I'm truely sorry about that, I had no idea it would want to remove all of those packages.

Don't worry! The fact you immediately helped me rectify the damage speaks volumes about you. Many would have panicked and bailed. LOL

Would it be safe for me install iotop using synaptic?
I still want to address this issue, you see....

---

### Post by scragar on 2009-09-04
I wouldn't agree to letting it remove any packages, but try it.

I don't understand why it would want to remove anything though, it's a pretty small python script, it shouldn't have any dependencies other than python(which is installed by default), and I can't imagine it conflicting with anything.

---

### Post by Psychopump on 2009-09-04
> **scragar said:**
> I wouldn't agree to letting it remove any packages, but try it.

I don't understand why it would want to remove anything though, it's a pretty small python script, it shouldn't have any dependencies other than python(which is installed by default), and I can't imagine it conflicting with anything.

Do you think I should file a bug report on it?

---

### Post by snowpine on 2009-09-04
> **Psychopump said:**
> Hello all,

I have a Packard Bell Dot M netbook. It has the 1.33GHz Intel Atom processor with the poulsbo chipset. I have upgraded the RAM to 2Gb.
It is running MintLinux Gloria (Jaunty).

Whenever I use the netbook intensively, conky tells me that the processor is maxing out at 100% and causing things to go awry. At the same time the netbook is only using about 16% of it's available RAM, and NEVER more than 20%.

Is there any way to put the RAM to more use, so the processor has some more room to breathe?

Your netbook is slow for two reasons... 1st, the Atom is a slow processor. 2nd and more important, poulsbo is not well supported by Jaunty. There are fixes available, though, so just search these forums for 'poulsbo' and you'll find some good suggestions. Not sure if they will necessarily work on Mint, though...

To answer your question specifically, cpu and ram are two separate resources; adding more ram will not speed up a slow processor.

---

### Post by scragar on 2009-09-04
I don't know what the bug report should be filed against, it could be either aptitude(which is rather powerful, but does have a few bugs with wanting to remove packages) or iotop(which might have some strange conflicts listed, although I doubt it).
Try running:
```
apt-cache showpkg iotop | less
```
And look at what it says for conflicts, if there's anything listed I'd file the bug report against that, otherwise file it against aptitude. (Not running ubuntu anymore, or I'd do this myself)

---

### Post by Psychopump on 2009-09-04
@Snowpine

I tried the poulsbo fixes on the forum, but they borked my system.

I know the atom is slow, but if the ram does not get used more than 20%, does that mean my ram upgrade was unnecessary?
I know that vista and w7 both make better use of ram when it is not specifically used by other processes to speed up the OS generally - is there anything like that for Ubuntu?

---

### Post by scragar on 2009-09-04
> **Psychopump said:**
> @Snowpine

I tried the poulsbo fixes on the forum, but they borked my system.

I know the atom is slow, but if the ram does not get used more than 20%, does that mean my ram upgrade was unnecessary?
I know that vista and w7 both make better use of ram when it is not specifically used by other processes to speed up the OS generally - is there anything like that for Ubuntu?

Ubuntu like all linux systems does that by default(And has done for a very, very long time), ram not required to run programs is used to hold copies of programs and files recently opened in order to speed up access to them again, and most of the time file writes are written at regular intervals by storing the changes in ram in order to improve disk performance.
You can check this yourself using the free command:
```
free -m
```It looks like this:
```
             total       used       free     shared    buffers     cached
Mem:          3826       3768         58          0        195       **2602**
-/+ buffers/cache:        970       2856
Swap:         5004         18       4986
```
The total cache I'm using is in bold: 2602, so I'm using 2.6GB of my 4GB of ram to cache programs and applications for speedy access later.

---

### Post by Psychopump on 2009-09-04
Installing iotop worked fine through synaptic...phew!

```








































































Total DISK READ: 0 B/s | Total DISK WRITE: 243.47 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO>    COMMAND                
   31 root           0 B/s    7.38 K/s  0.00 %  0.00 % [pdflush]
23790 loki           0 B/s   14.76 K/s  0.00 %  0.00 % firefox
 1811 root           0 B/s   99.60 K/s  0.00 %  0.00 % [kjournald2]
14655 loki           0 B/s  114.36 K/s  0.00 %  0.00 % transmission
    1 root           0 B/s       0 B/s  0.00 %  0.00 % init
    2 root           0 B/s       0 B/s  0.00 %  0.00 % [kthreadd]
    3 root           0 B/s       0 B/s  0.00 %  0.00 % [migration/0]
    4 root           0 B/s       0 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 root           0 B/s       0 B/s  0.00 %  0.00 % [watchdog/0]
    6 root           0 B/s       0 B/s  0.00 %  0.00 % [migration/1]
    7 root           0 B/s       0 B/s  0.00 %  0.00 % [ksoftirqd/1]
    8 root           0 B/s       0 B/s  0.00 %  0.00 % [watchdog/1]
    9 root           0 B/s       0 B/s  0.00 %  0.00 % [events/0]
   10 root           0 B/s       0 B/s  0.00 %  0.00 % [events/1]
   11 root           0 B/s       0 B/s  0.00 %  0.00 % [khelper]
   12 root           0 B/s       0 B/s  0.00 %  0.00 % [kstop/0]
   13 root           0 B/s       0 B/s  0.00 %  0.00 % [kstop/1]
   14 root           0 B/s       0 B/s  0.00 %  0.00 % [kintegrityd/0]
   15 root           0 B/s       0 B/s  0.00 %  0.00 % [kintegrityd/1]
   16 root           0 B/s       0 B/s  0.00 %  0.00 % [kblockd/0]
   17 root           0 B/s       0 B/s  0.00 %  0.00 % [kblockd/1]
   18 root           0 B/s       0 B/s  0.00 %  0.00 % [kacpid]


```

---

### Post by snowpine on 2009-09-04
> **Psychopump said:**
> @Snowpine

I tried the poulsbo fixes on the forum, but they borked my system.

I know the atom is slow, but if the ram does not get used more than 20%, does that mean my ram upgrade was unnecessary?
I know that vista and w7 both make better use of ram when it is not specifically used by other processes to speed up the OS generally - is there anything like that for Ubuntu?

I don't have a poulsbo chipset personally, so I won't comment on that except to say using the wrong video driver is a possible cause of your slow performance.

To answer the second part of your question, Linux has excellent memory management by default, and ram is automatically used as cache to speed up the system. You don't need to do anything special to enable that feature. I've never personally needed more than 1gb of ram, but of course it depends on what you use your computer for (I seem to use mine mostly for surfing ubuntu forums).

---

### Post by Psychopump on 2009-09-04
Purely because of it's compact size, the netbook is becoming more and more my main box. It was shipped with XP and could handle a lot of games, video and even some music production software.

Now, I cannot even play super maryo chronicles, the menu for the game lags so much I am forced to hard-reboot my box.

Video is choppy, even scrolling down a page in firefox is painfully slow. Sound from video and music players randomly becomes white noise, then fails completely until I restart the program.

Ubuntu really needs poulsbo support, as the netbook market is one that lends itself to nix BECAUSE of the slower processors.

I hope some solutions are forthcoming soon.

Thanks for your help guys!

---

### Post by GoldenSun on 2009-09-04
add a ramdisk for more performance.
[http://ubuntuforums.org/showthread.php?t=182764](http://ubuntuforums.org/showthread.php?t=182764)

---

