---
title: "[SOLVED] Envy on 2.6.22-9 generic wont install"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Guyver1 on 2007-08-15
Hi

Im currently following the installation guide for my Intel wifi 4965AGN card which requires the installation of 2.6.22-9 generic kernal 

done all that but cant get that working (thats for another thread.)

trying to install envy this kernal gives me the followign error (i've installed envy and nvidia drivers successfully on feisty fawn 2.6.16 kernal (which is the most current with normal upgrade)

heres my error:
```

guyver1@m9750:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
guyver1@m9750:~$ 

```

any help would be appreciated. I would hate to be in a situation where its one or the other on either kernal :(

---

### Post by walkerk on 2007-08-15
> **Guyver1 said:**
> Hi

Im currently following the installation guide for my Intel wifi 4965AGN card which requires the installation of 2.6.22-9 generic kernal 

done all that but cant get that working (thats for another thread.)

trying to install envy this kernal gives me the followign error (i've installed envy and nvidia drivers successfully on feisty fawn 2.6.16 kernal (which is the most current with normal upgrade)

heres my error:
```

guyver1@m9750:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
guyver1@m9750:~$ 

```

any help would be appreciated. I would hate to be in a situation where its one or the other on either kernal :(

did you upgrade using the thread in my signature? others have had success installing envy. also i believe linux-restricted-modules will allow use with nvidia. if you werent using my instructions you might give it a look (it will install 2.6.22-9-generic along with libc6, restricted modules, ubuntu modules, etc. from the gutsy repos.)

---

### Post by Guyver1 on 2007-08-16
> **walkerk said:**
> did you upgrade using the thread in my signature? others have had success installing envy. also i believe linux-restricted-modules will allow use with nvidia. if you werent using my instructions you might give it a look (it will install 2.6.22-9-generic along with libc6, restricted modules, ubuntu modules, etc. from the gutsy repos.)

clean install, updated to 2.6.20.16

used your file to update to 2.6.22.9

reboot

download envy

try to install and get:

error cannot install 'build-essential'

so, sudo apt-get install build-essential

gives me:

```

guyver1@m9750:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
guyver1@m9750:~$ 

```

:(

---

### Post by voxar on 2007-08-16
looks not only you have this problem... me too... any idea?.. thank you

---

### Post by tseliot on 2007-08-16
It's not just Envy. You shouldn't be able to compile anything else since you can't install the build-essentials.

Installing kernels from Gutsy is not such a good idea since they will break your system.

---

### Post by Guyver1 on 2007-08-16
how can i safely uninstall the gutsy kernal and restore my system back to 2.6.20.16??

i can live without wireless for now but i want my SLI and 1920x1200 up and running :)

---

### Post by tseliot on 2007-08-16
boot in your older kernel and try to remove your new kernel with aptitude:
```
sudo aptitude purge linux-image-2.6.22-9-generic
```

then let it downgrade the other packages

---

### Post by walkerk on 2007-08-16
> **Guyver1 said:**
> how can i safely uninstall the gutsy kernal and restore my system back to 2.6.20.16??

i can live without wireless for now but i want my SLI and 1920x1200 up and running :)

You can open up Synaptic and search for 2.6.22-9. Now mark these items for complete removal and press Apply. 

Or you can remove through the terminal...
 
```
sudo apt-get remove linux-headers-2.6.22-9 linux-image-2.6.22-9-generic linux-ubutu-modules-2.6.22-9-generic linux-restricted-modules-2.6.22-9-geneic
```

---

### Post by walkerk on 2007-08-16
> **tseliot said:**
> It's not just Envy. You shouldn't be able to compile anything else since you can't install the build-essentials.

Installing kernels from Gutsy is not such a good idea since they will break your system.

There is a disclaimer on my page that addresses problems but for the most part people are using the kernel from Gutsy without breaking their systems. Quite a few people are using nVidia video cards as well.

---

### Post by tseliot on 2007-08-16
> **walkerk said:**
> There is a disclaimer on my page that addresses problems but for the most part people are using the kernel from Gutsy without breaking their systems. Quite a few people are using nVidia video cards as well.
I know, I did it in the past. Your warning is ok

---

### Post by Guyver1 on 2007-08-16
ok something i've discovered.

i clean installed, updated with the 115 updates currently on the commercial dist.

so kernel 2.6.20-16

download envy.

this is where i might have gone wrong.

went to home directory, double clicked on the envy package which brought up the installer, which then gave me the build-essentials error.

So did a quick google and found a different method - [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

```

A) How do I Install the package?

1) Download and install the deb package: 

open Terminal or Konsole and type: 

cd path_to_envy's_deb_package 

sudo dpkg -i envy*.deb 

2) Make sure that all the dependencies were installed by typing: 

sudo apt-get install -f 

3) Launch Envy's GUI (inside a Desktop Environment such as GNOME,KDE, etc.) by selecting it in the "Applications/System Tools" menu 

OR if you need to use Envy's textual interface you will have to type: 

sudo envy -t

```

did all that and it installed fine......

seems double clicking on the envy deb doesnt work

---

### Post by tseliot on 2007-08-16
> **Guyver1 said:**
> did all that and it installed fine......

seems double clicking on the envy deb doesnt work

Do you use Kubuntu or Xubuntu?

---

### Post by Guyver1 on 2007-08-16
standard Ubuntu Feisty Fawn 7.0.4 desktop 32bit

---

### Post by tseliot on 2007-08-16
> **Guyver1 said:**
> standard Ubuntu Feisty Fawn 7.0.4 desktop 32bit
Weird... I guess right-click and select open with GDebi should do the trick

---

### Post by Guyver1 on 2007-08-16
yeah no worries i did it manually through terminal successfully so all's good, but you may want to look into why double clicking is throwing up that build-essential error

---

### Post by Guyver1 on 2007-08-25
tseliot

theres definately a problem with envy on gutsy.

did a clean install again, upgraded to 2.6.20-16, then onto gutsy 2.6.22-10

when you install the linux-headers and linux-image you get a dependancy install of libc6 (i think thats what its called) this is whats causing the problems.

```

guyver1@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
guyver1@ubuntu:~$ 

```


has anyone installed gutsy 2.6.22-10 and managed to install envy??

if so how did you manage it?

---

### Post by tseliot on 2007-08-25
> **Guyver1 said:**
> tseliot

theres definately a problem with envy on gutsy.

did a clean install again, upgraded to 2.6.20-16, then onto gutsy 2.6.22-10

when you install the linux-headers and linux-image you get a dependancy install of libc6 (i think thats what its called) this is whats causing the problems.

```

guyver1@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
guyver1@ubuntu:~$ 

```


has anyone installed gutsy 2.6.22-10 and managed to install envy??

if so how did you manage it?
Envy is not the problem in this case. I think Ubuntu's developers might have (temporarily) broken the dependencies of the build-essentials.

can you post the output of this command?
```
sudo aptitude search g++
```

---

### Post by Guyver1 on 2007-08-25
it scrolled too much stuff for me to copy it all sorry, and i dont know the switches to page up and get the rest, heres what i could get from the terminal window:

```

p   texlive-lang-spanish                       - TeX Live: Spanish                                    
p   texlive-lang-swedish                       - TeX Live: Swedish                                    
p   texlive-lang-tibetan                       - TeX Live: Tibetan                                    
p   texlive-lang-ukenglish                     - TeX Live: UK English                                 
p   texlive-lang-vietnamese                    - TeX Live: Vietnamese                                 
p   texlive-omega                              - TeX Live: Omega                                      
p   tfm-arphic-gbsn00lp                        - Arphic "AR PL SungtiL GB" TrueType font TeX font metr
p   tfm-arphic-gkai00mp                        - Arphic "AR PL KaitiM GB" TrueType font TeX font metri
p   tgif                                       - Interactive 2-D drawing facility under X11           
p   thewidgetfactory                           - a showcase for GTK+ widgets                          
p   thin-client-manager-backend                - control ubuntu LTSP connections                      
p   thin-client-manager-gnome                  - control ubuntu LTSP connections                      
p   thoggen                                    - DVD backup utility based on GStreamer and Gtk+       
p   thunar-archive-plugin                      - archive plugin for Thunar                            
p   thunar-media-tags-plugin                   - Tag editor plugin for Thunar                         
p   thunar-volman-plugin                       - enables automatic management of medias in Thunar     
p   thunderbird-locale-bg                      - Thunderbird Bulgarian language/region package        
i   thunderbird-locale-en-gb                   - Thunderbird English language/region package          
p   thunderbird-locale-gu-in                   - Thunderbird Gujarati language/region package         
p   tig                                        - content addressable filesystem (CLI repository browse
p   tiger                                      - Report system security vulnerabilities               
p   tiger-mode                                 - An emacs-mode for tiger programs.                    
p   tiger-otheros                              - Scripts to run Tiger in other operating systems      
p   tightvnc-java                              - TightVNC java applet and command line program        
p   tightvncserver                             - virtual network computing server software            
p   tigr-glimmer                               - [Biology] Gene detection in archea and bacteria      
p   tinysnmp-agent                             - A lightweight SNMPv1 implementation                  
p   tinysnmp-agent-dev                         - Libraries and header files for developing TinySNMP pl
p   tinysnmp-manager-dev                       - Libraries and header files for developing TinySNMP pr
p   tioga                                      - Ruby library for scientific graphs [transition packag
p   tkgate                                     - Event driven digital circuit simulator with Tcl/Tk   
p   tkping                                     - Perl/Tk app. - Monitor hosts on network              
p   tla-buildpackage                           - Suite to help with Debian packages in Arch archives  
p   tntdb-postgresql0                          - PostgreSQL backend for tntdb database access library 
p   tochnog                                    - A free implicit/explicit finite element analysis prog
p   tochnog-doc                                - Documentation for Tochnog finite element analysis pro
p   tor-dbg                                    - debugging symbols for Tor                            
i   totem-gstreamer                            - A simple media player for the Gnome desktop based on 
v   totem-gstreamer-firefox-plugin             -                                                      
v   totem-xine-firefox-plugin                  -                                                      
p   tpconfig                                   - configure touchpad devices                           
p   traceroute-nanog                           - Determine route of packets in TCP/IP networks (NANOG 
p   trackballs-dbg                             - Debugging symbols for Trackballs                     
p   trang                                      - Multi-format XML schema converter based on RELAX NG  
p   transfig                                   - Utilities for converting XFig figure files           
p   tre-agrep                                  - approximate grep utility based on the tre library    
p   treelang-4.1                               - The GNU Treelang compiler                            
p   trigger                                    - free 3D rally racing car game                        
p   trigger-data                               - free 3D rally racing car game - data files           
p   tropic-gdm-theme                           - Tropic look - GDM theme                              
p   ttf-arhangai                               - A TrueType font with Mongolian Cyrillic letters      
p   ttf-arphic-gbsn00lp                        - "AR PL SungtiL GB" Chinese TrueType font by Arphic Te
p   ttf-arphic-gkai00mp                        - "AR PL KaitiM GB" Chinese TrueType font by Arphic Tec
i   ttf-arphic-uming                           - "AR PL ShanHeiSun Uni" Chinese Unicode TrueType font 
v   ttf-bangla-fonts                           -                                                      
i   ttf-bengali-fonts                          - Free TrueType fonts for the Bengali language         
p   ttf-bpg-georgian-fonts                     - BPG Georgian fonts                                   
i   ttf-devanagari-fonts                       - Free TrueType fonts for languages using the Devanagar
p   ttf-dzongkha                               - TrueType fonts for Dzongkha language                 
i   ttf-gentium                                - Gentium TrueType font                                
p   ttf-georgewilliams                         - Free unicode TrueType fonts by George Williams       
i   ttf-gujarati-fonts                         - Free TrueType fonts for the Gujarati language        
v   ttf-japanese-gothic                        -                                                      
i   ttf-kochi-gothic                           - Kochi Subst Gothic Japanese TrueType font without nag
p   ttf-kochi-gothic-naga10                    - Kochi Subst Gothic Japanese TrueType font with naga10
p   ttf-kochi-mincho-naga10                    - Kochi Subst Mincho Japanese TrueType font with naga10
p   ttf-larabie-straight                       - Straight fonts from www.larabiefonts.com             
i   ttf-mgopen                                 - Magenta Open Truetype fonts                          
p   ttf-sazanami-gothic                        - Sazanami Gothic Japanese TrueType font               
i   ttf-telugu-fonts                           - Free TrueType fonts for the Telugu language          
i   ttf-thai-tlwg                              - Thai fonts in TrueType format                        
p   ttf-vlgothic                               - Japanese TrueType font from Vine Linux               
p   ttylog                                     - serial port logger                                   
p   tuareg-mode                                - An emacs-mode for ocaml programs                     
p   tunneldigger                               - Configures OpenVPN tunnel networks                   
p   tunneldigger-utils                         - Utilities for TunnelDigger-configured OpenVPN tunnels
p   tuxpaint-config                            - Configuration tool for Tux Paint                     
p   twig                                       - The Web Information Gateway                          
p   twlog                                      - Logging program for hamradio operators               
p   txt2regex                                  - A Regular Expression "wizard", all written with bash2
p   txt2tags                                   - a conversion tool generating HTML/SGML/LaTeX/man/Moin
p   type-handling                              - dpkg architecture generation script                  
p   ubiquity-frontend-gtk                      - GTK+ frontend for Ubiquity live installer            
i   ubuntu-keyring                             - GnuPG keys of the Ubuntu archive                     
p   ubuntu-serverguide                         - The Ubuntu Server Guide                              
p   ubuntustudio-audio-plugins                 - Ubuntu Studio audio plugins Package                  
p   ubuntustudio-graphics                      - Ubuntu Studio graphics Package                       
p   ucblogo                                    - a dialect of lisp using turtle graphics famous for te
p   ucbmpeg-play                               - Software-only MPEG video player                      
p   ugidd                                      - NFS UID mapping daemon                               
p   uim-applet-gnome                           - GNOME applet for uim                                 
p   uim-gtk2.0                                 - GTK+2.x immodule for uim                             
p   uligo                                      - tsumego (go problems) practice tool                  
p   ulog-acctd                                 - Accounting daemon for Linux 2.4+ netfilter           
p   ulogd                                      - The Netfilter Userspace Logging Daemon               
p   ulogd-mysql                                - MySQL extension to ulogd                             
p   ulogd-pcap                                 - pcap extension to ulogd                              
p   ulogd-pgsql                                - PostgreSQL extension to ulogd                        
p   ulogd-sqlite3                              - SQLite 3 extension to ulogd                          
i   unattended-upgrades                        - Install security upgrades automatically              
p   unison-gtk                                 - A file-synchronization tool for Unix and Windows - GT
p   unison2.9.1-gtk                            - A file-synchronization tool for Unix and Windows - GT
i   update-manager                             - GNOME application that manages apt updates           
i   update-manager-core                        - manage release upgrades                              
v   upgrade-notifier                           -                                                      
p   upgrade-system                             - system upgrader from Konflux                         
p   uprecords-cgi                              - A CGI script to show the world your highest uptimes  
p   upslug2                                    - utility to upgrade the firmware of a LinkSys NSLU2 vi
i   upstart-logd                               - boot logging daemon                                  
p   usbmgr                                     - user-mode daemon which loads/unloads USB kernel modul
p   usepackage                                 - utility to manage environment variables from within d
p   utf8-migration-tool                        - Debian UTF-8 migration wizard                        
p   uuagc                                      - compiler for the Utrecht University Attribute Grammar
p   valgrind                                   - A memory debugger and profiler                       
v   valgrind-callgrind                         -                                                      
p   varkon-programmer-manual                   - Programmer manual for VARKONs mbs language           
p   vcdimager                                  - A VideoCD (VCD) image mastering and ripping tool     
p   vcf-plugins                                - Audio EQ biquad filter LADSPA plugins                
p   vcg                                        - A Visualization Tool for compiler graphs             
p   vdr-plugin-bitstreamout                    - Plugin for VDR to play AC3 sound over a sound card   
p   vdr-plugin-console                         - Plugin for vdr that implements a virtual terminal    
p   vdr-plugin-dvd                             - DVD playback plugin for VDR                          
p   vdr-plugin-examples                        - Plugins for vdr to show some possible features       
p   vdr-plugin-femon                           - DVB frontend status monitor plugin for VDR           
p   vdr-plugin-freecell                        - Plugin for VDR that implements the card game "Freecel
p   vdr-plugin-games                           - VDR plugin providing OSD games like tetris, snake and
p   vdr-plugin-mp3                             - MP3 playback plugin for VDR                          
p   vdr-plugin-osdteletext                     - Teletext plugin for VDR                              
p   vdr-plugin-prefermenu                      - VDR plugin that implements a preferred channels menu 
p   vdr-plugin-remote                          - VDR Plugin to support the built-in remote control por
p   vdr-plugin-sky                             - Plugin for using a Sky Digibox with vdr              
p   vdr-plugin-vcd                             - VDR Plugin for playing (S)VCD's                      
p   vdr-plugin-weather                         - Weather plugin for VDR                               
p   vegastrike                                 - A 3d space combat game                               
p   vegastrike-data                            - Data files for vegastrike                            
p   vegastrike-music                           - Music files for vegastrike                           
p   verbiste-gnome                             - a French conjugation system                          
p   verilog                                    - Icarus verilog compiler                              
p   vgabios                                    - VGA BIOS software for the Bochs and Qemu emulated VGA
p   vgacardgames                               - Four SVGAlib card games                              
p   vgrabbj                                    - grabs a image from a camera and puts it in jpg/png fo
p   vgrind                                     - Runoff preprocessor for program sources              
v   vibrant6-dbg                               -                                                      
p   videogen                                   - Create arbitrary-res modelines using hardware paramet
p   videomanager                               - An application for managing your movie collection    
p   viewglob                                   - A graphical display of directories referenced at the 
p   vigor                                      - nvi with the evil paperclip                          
p   vim-gnome                                  - Vi IMproved - enhanced vi editor - with GNOME2 GUI   
p   vim-gtk                                    - Vi IMproved - enhanced vi editor - with GTK2 GUI     
p   vim-gui-common                             - Vi IMproved - Common GUI files                       
p   visual-regexp                              - Interactively debug regular expressions              
p   vlc-plugin-alsa                            - dummy transitional package                           
p   vlc-plugin-arts                            - aRts audio output plugin for VLC                     
p   vlc-plugin-esd                             - Esound audio output plugin for VLC                   
p   vlc-plugin-ggi                             - GGI video output plugin for VLC                      
p   vlc-plugin-glide                           - Glide video output plugin for VLC                    
p   vlc-plugin-sdl                             - SDL video and audio output plugin for VLC            
p   vlc-plugin-svgalib                         - SVGAlib video output plugin for VLC                  
p   vlogger                                    - virtual web logfile rotater/parser                   
p   vorbisgain                                 - add Replay Gain volume tags to Ogg Vorbis files      
p   vtgrab                                     - A VNC like console monitoring                        
p   w3m-img                                    - inline image extension support utilities for w3m     
p   w3mmee-img                                 - inline image extension support utilities for w3mmee  
p   wajig                                      - simplified Debian package management front end       
p   wamerican-huge                             - American English dictionary words for /usr/share/dict
p   wamerican-large                            - American English dictionary words for /usr/share/dict
p   watchdog                                   - software watchdog                                    
p   wbritish-huge                              - British English dictionary words for /usr/share/dict 
p   wbritish-large                             - British English dictionary words for /usr/share/dict 
p   wbulgarian                                 - The Bulgarian dictionary words for /usr/share/dict   
p   wcanadian-huge                             - Canadian English dictionary words for /usr/share/dict
p   wcanadian-large                            - Canadian English dictionary words for /usr/share/dict
p   wdg-html-validator                         - WDG HTML Validator                                   
p   webauth-weblogin                           - Central login server for WebAuth authentication      
p   webgen                                     - A template based static website generator            
p   webmagick                                  - create gallery thumbnails for website                
p   weechat-plugins                            - Plugins for WeeChat                                  
p   wengophone                                 - SIP-based software telephone with video and chat feat
p   wesnoth-tsg                                - The South Guard official campaign for Wesnoth        
p   wflogs                                     - The modular firewall log analyzer of the WallFire pro
p   wgaelic                                    - A Scots Gaelic word list                             
p   wgalician-minimos                          - Wordlist for Galician (minimos)                      
i   wget                                       - retrieves files from the web                         
p   wget-el                                    - an interface for wget on Emacsen                     
p   widelands-dbg                              - fantasy real-time strategy game (debug cruft)        
p   wiggle                                     - a program for applying patches with conflicting chang
p   willowng                                   - content filtering web proxy                          
p   willowng-config                            - willowng configuration gui                           
p   willowng-config-gnome                      - willowng configuration gui                           
p   willowng-config-kde                        - willowng configuration gui                           
p   wing                                       - Galaga-like arcade game                              
p   wing-data                                  - graphics and audio data for wing                     
p   wings3d                                    - Nendo-inspired 3D polygon mesh modeller              
i   wireless-tools                             - Tools for manipulating Linux Wireless Extensions     
v   wmaker-usersguide                          -                                                      
p   wmaker-usersguide-ps                       - Window Maker Users' Guide -- postscript format       
p   wmanager                                   - Select a window manager at X startup                 
p   wmavgload                                  - small NeXTStep-like system load average monitor      
p   wmget                                      - Background download manager in a Window Maker dock ap
p   wmgrabimage                                - maintains a small thumbnail image from the WWW       
p   wmgtemp                                    - Temperature sensor dockapp for Window Maker          
p   wmlongrun                                  - A program to monitor longrun status                  
p   wngerman                                   - New German orthography wordlist                      
p   wnn7egg                                    - Wnn-nana-tamago -- EGG Input Method with Wnn7 for Ema
p   wnorwegian                                 - Norwegian wordlist                                   
p   wogerman                                   - The old German dictionary for /usr/share/dict        
p   worklog                                    - Keep Track of Time worked on Projects                
v   worldforge-client                          -                                                      
v   worldforge-server                          -                                                      
p   wpagui                                     - GUI for wpa_supplicant                               
p   wportuguese                                - European Portuguese wordlist                         
p   www-pgsql                                  - a WWW interface for the PostgreSQL database          
p   wwwconfig-common                           - Debian web auto configuration                        
p   wyg                                        - (Where's Your Grammar?) command line parser generator
p   wzdftpd-back-pgsql                         - PostgreSQL backend for wzdftpd                       
v   x-display-manager                          -                                                      
p   x-pgp-sig-el                               - X-PGP-Sig mail and news header utility for Emacs.    
v   x-session-manager                          -                                                      
v   x-window-manager                           -                                                      
p   x11proto-bigreqs-dev                       - X11 Big Requests extension wire protocol             
p   x11proto-damage-dev                        - X11 Damage extension wire protocol                   
p   x11proto-gl-dev                            - X11 OpenGL extension wire protocol                   
p   x11proto-xf86bigfont-dev                   - X11 Big Fonts extension wire protocol                
p   x11proto-xf86dga-dev                       - X11 Direct Graphics Access extension wire protocol   
p   xapian-omega                               - CGI search interface and indexers using Xapian       
p   xara-gtk                                   - GTK utility for searching the Debian package database
p   xara-gtk-byte                              - GTK utility for searching the Debian package database
p   xaralx-svg                                 - SVG (Scalable Vector Graphics) plugin for XaraLX     
p   xaw3dg                                     - Xaw3d widget set                                     
p   xaw3dg-dev                                 - Xaw3d widget set development package                 
p   xawtv-plugins                              - plugins for xawtv and motv                           
p   xbindkeys-config                           - An easy to use gtk program for configuring Xbindkeys.
p   xblast-tnt-images                          - image files for xblast-tnt                           
p   xboing                                     - blockout game for X                                  
p   xchat-gnome                                - a new frontend to the popular X-Chat IRC client      
p   xchat-gnome-common                         - a new frontend to the popular X-Chat IRC client      
p   xchat-guile                                - Guile scripting plugin for XChat                     
p   xcompmgr                                   - X composition manager                                
i   xcursorgen                                 - X cursor generation                                  
p   xdebconfigurator                           - A script used with debconf to autoconfigure xserver-x
p   xdg-utils                                  - Desktop integration utilities from freedesktop.org   
p   xdialog                                    - X11 replacement for the text util dialog             
p   xdigger                                    - An arcade diamonds digging game for X11              
p   xdiskusage                                 - Displays a graphic of your disk usage with du        
p   xemacs21-gnome-mule                        - highly customizable text editor -- Mule binary       
p   xemacs21-gnome-mule-canna-wnn              - highly customizable text editor -- Mule binary compil
p   xemacs21-gnome-nomule                      - highly customizable text editor -- Non-mule binary   
p   xen-headers-2.6.19-4-generic               - Common header files for Linux 2.6.19                 
p   xen-image-2.6.19-4-generic                 - Linux 2.6.19 image on PPro/Celeron/PII/PIII/P4       
p   xen-image-2.6.19-4-server                  - Linux xen 2.6.19 image on x86.                       
p   xen-restricted-modules-2.6.17-6-generic-xe - Non-free Linux 2.6.17 modules on x86_64 generic-xen0 
p   xengine                                    - A benchmark program for the X Window System.         
i   xf86dga                                    - X client - xf86dga                                   
p   xfce4-battery-plugin                       - battery monitor plugin for the Xfce4 panel           
p   xfce4-clipman-plugin                       - clipboard history plugin for the Xfce4 panel         
p   xfce4-cpu-freq-plugin                      - display the CPU informations in the Xfce panel       
p   xfce4-cpufreq-plugin                       - cpufreq information plugin for the Xfce4 panel       
p   xfce4-cpugraph-plugin                      - CPU load graph plugin for the Xfce4 panel            
p   xfce4-datetime-plugin                      - date and time plugin for the Xfce4 panel             
p   xfce4-dict-plugin                          - Translation plugin for the Xfce panel                
p   xfce4-diskperf-plugin                      - disk performance display plugin for the Xfce4 panel  
p   xfce4-fsguard-plugin                       - filesystem monitor plugin for the Xfce4 panel        
p   xfce4-genmon-plugin                        - Generic Monitor for the Xfce4 panel                  
p   xfce4-goodies                              - enhancements for the Xfce4 Desktop Environment       
p   xfce4-mailwatch-plugin                     - mail watcher plugin for the Xfce4 panel              
p   xfce4-mcs-manager                          - Settings manager for Xfce4                           
p   xfce4-mcs-manager-dev                      - Development files and static plugins                 
p   xfce4-mcs-plugins                          - Special modules for the xfce4-mcs-manager            
p   xfce4-messenger-plugin                     - Dbus messages plugin for xfce4-panel                 
p   xfce4-minicmd-plugin                       - Mini-command line plugin for the Xfce4 panel         
p   xfce4-mount-plugin                         - mount plugin for the Xfce4 panel                     
p   xfce4-mpc-plugin                           - Xfce panel plugin which serves as client for MPD musi
p   xfce4-netload-plugin                       - network load monitor plugin for the Xfce4 panel      
p   xfce4-notes-plugin                         - Notes plugin for the Xfce4 desktop                   
p   xfce4-quicklauncher-plugin                 - rapid launcher plugin for the Xfce4 panel            
p   xfce4-radio-plugin                         - v4l radio control plugin for the Xfce4 panel         
p   xfce4-screenshooter-plugin                 - xfce4-panel plugin to take screenshots               
p   xfce4-sensors-plugin                       - hardware sensors plugin for the Xfce4 panel          
p   xfce4-smartbookmark-plugin                 - search the web via the Xfce4 panel                   
p   xfce4-systemload-plugin                    - system load monitor plugin for the Xfce4 panel       
p   xfce4-taskmanager                          - process manager for the Xfce4 Desktop Environment    
p   xfce4-verve-plugin                         - Command line plugin for the Xfce panel               
p   xfce4-wavelan-plugin                       - wavelan status plugin for the Xfce4 panel            
p   xfce4-weather-plugin                       - weather information plugin for the Xfce4 panel       
p   xfce4-xfapplet-plugin                      - Gnome applets plugin for Xfce panel                  
p   xfce4-xkb-plugin                           - xkb layout switch plugin for the Xfce4 panel         
p   xfce4-xmms-plugin                          - xmms plugin for the Xfce panel                       
p   xffm4-filemanager                          - Xffm file manager                                    
p   xfig                                       - Facility for Interactive Generation of figures under 
p   xfig-doc                                   - XFig on-line documentation and examples              
p   xfig-libs                                  - XFig image libraries and examples                    
p   xfingerd                                   - BSD-like finger daemon with qmail support            
v   xfntbig5p-cmex24m                          -                                                      
v   xfonts-arphic-gbsn00lp                     -                                                      
v   xfonts-arphic-gkai00mp                     -                                                      
v   xfonts-arphic-uming                        -                                                      
p   xfonts-cmex-big5p                          - Big5+ Chinese Mingti bitmap font (by CMEX & DynaLab) 
i   xfonts-encodings                           - Encodings for X.Org fonts                            
p   xfonts-intl-chinese-big                    - International fonts for X -- Chinese big             
p   xfonts-intl-japanese-big                   - International fonts for X -- Japanese big            
p   xfonts-naga10                              - 10x10 dot Japanese and ISO-8859-1 naga10 fonts       
p   xfsprogs                                   - Utilities for managing the XFS filesystem            
p   xgalaga                                    - X11 version of the famous Galaga game                
i   xgamma                                     - X client - xgamma                                    
p   xgammon                                    - Implementation of backgammon under X                 
i   xgc                                        - X client - xgc                                       
p   xgdipc                                     - GTK client for dynamic IP to name mappings           
p   xgdvi                                      - a TeX DVI previewer for X, with a nice GTK+ UI       
p   xgmod                                      - GUI based module player for Ultrasound and SB AWE sou
p   xgraph                                     - Plotting program, reads stdin, allows interactive zoo
p   xgsmlib                                    - Gnome application to handle mobile phone's phone book
p   xhangglider                                - hanggliders fly around in your X root window         
p   xipmsg                                     - A pop up style message communication software        
p   xjig                                       - An X11 jigsaw puzzle                                 
p   xkb-data-legacy                            - Classic XKB data                                     
p   xkeyboard-config                           - Transitional package for xkb-data                    
p   xkeysw-config                              - xkeysw configurator                                  
p   xless                                      - A file browsing tool for the X Window System         
p   xlibmesa-gl                                - transitional package for Debian etch                 
p   xlibmesa-gl-dev                            - transitional package for Debian etch                 
p   xlibmesa-glu                               - transitional package for Debian etch                 
v   xlibmesa-glu-dev                           -                                                      
p   xloadimage                                 - Graphics file viewer under X11                       
p   xlockmore-gl                               - Lock X11 display until password is entered -- GL vers
p   xlog                                       - GTK+ Logging program for Hamradio Operators          
p   xlogmaster                                 - A program to monitor logfiles                        
i   xlogo                                      - X client - xlogo                                     
i   xmag                                       - X client - xmag                                      
p   xmahjongg                                  - tile-based solitaire game                            
p   xmame-gl                                   - dummy package                                        
p   xmame-svga                                 - SVGALIB binaries for the Multiple Arcade Machine Emul
p   xmanpages-ja                               - Japanese manual pages for X                          
i   xmessage                                   - X client - xmessage                                  
p   xml-twig-tools                             - Command line tools for processing XML documents      
p   xmltv-gui                                  - Graphical user interface related to the XMLTV file fo
p   xmms-adplug                                - free AdLib sound library (xmms-plugin)               
p   xmms-goodnight                             - XMMS plugin to stop playing at a given time          
p   xmms-goom                                  - visualization plug-in for XMMS with a variety of effe
p   xmms-modplug                               - ModPlug plugin for XMMS                              
p   xmms-mpg123-ja                             - mpeg123 plugin supported Japanese encodings for xmms 
p   xmms-oggre                                 - ogg disk output plugin for XMMS                      
p   xmms-osd-plugin                            - XMMS plugin using xosd                               
p   xmms-singit                                - Display and edit lyrics with XMMS                    
p   xmms-status-plugin                         - Status panel applet for XMMS                         
p   xnetcardconfig                             - A simple network card configuration for X.           
i   xorg                                       - X.Org X Window System                                
v   xorg-build-macros                          -                                                      
p   xorg-dev                                   - the X.Org X Window System development libraries      
p   xorg-docs                                  - Miscellaneous documentation for the X.Org software su
p   xorg-driver-fglrx                          - Video driver for ATI graphics accelerators           
p   xorg-driver-fglrx-dev                      - Video driver for ATI graphics accelerators (devel fil
v   xorg-driver-synaptics                      -                                                      
p   xorg-sgml-doctools                         - Common tools for building X.Org SGML documentation   
p   xpenguins                                  - little penguins walk on your windows                 
p   xpenguins-applet                           - GNOME2 panel applet implementation of xpenguins      
p   xpilot-ng                                  - Multi-player tactical game for X (NG version)        
p   xpilot-ng-client-sdl                       - Client for XPilot NG                                 
p   xpilot-ng-client-x11                       - Client for XPilot NG                                 
p   xpilot-ng-common                           - Common files for XPilot NG                           
p   xpilot-ng-server                           - Server for hosting XPilot NG games                   
p   xpilot-ng-utils                            - Utilities for XPilot NG                              
p   xplanet-images                             - day and night earth image maps for xplanet           
i   xrgb                                       - X RGB database and utilities                         
p   xringd                                     - Extended Ring Daemon - Monitor phone rings and take a
p   xscavenger                                 - A lode-runner-like platform game for X               
i   xscreensaver-gl                            - GL(Mesa) screen hacks for xscreensaver               
p   xscreensaver-gl-extra                      - GL(Mesa) screen hacks for xscreensaver               
p   xserver-xgl                                - GL-based X server                                    
i   xserver-xorg                               - the X.Org X server                                   
i   xserver-xorg-core                          - X.Org X server -- core server                        
i   xserver-xorg-dev                           - X.Org X server -- development files                  
v   xserver-xorg-driver-r128                   -                                                      
v   xserver-xorg-driver-radeon                 -                                                      
v   xserver-xorg-input                         -                                                      
p   xserver-xorg-input-acecad                  - X.Org X server -- AceCad input driver                
p   xserver-xorg-input-aiptek                  - X.Org X server -- Aiptek input driver                
i   xserver-xorg-input-all                     - the X.Org X server -- input driver metapackage       
p   xserver-xorg-input-calcomp                 - X.Org X server -- Calcomp input driver               
p   xserver-xorg-input-citron                  - X.Org X server -- Citron input driver                
p   xserver-xorg-input-digitaledge             - X.Org X server -- DigitalEdge input driver           
p   xserver-xorg-input-dmc                     - X.Org X server -- DMC input driver                   
p   xserver-xorg-input-dynapro                 - X.Org X server -- Dynapro input driver               
p   xserver-xorg-input-elo2300                 - X.Org X server -- ELO2300 input driver               
i   xserver-xorg-input-elographics             - X.Org X server -- ELOGraphics input driver           
i   xserver-xorg-input-evdev                   - X.Org X server -- evdev input driver                 
p   xserver-xorg-input-fpit                    - X.Org X server -- FPIT input driver                  
p   xserver-xorg-input-hyperpen                - X.Org X server -- HyperPen input driver              
p   xserver-xorg-input-jamstudio               - X.Org X server -- JamStudio input driver             
p   xserver-xorg-input-joystick                - X.Org X server -- joystick input driver              
i   xserver-xorg-input-kbd                     - X.Org X server -- keyboard input driver              
p   xserver-xorg-input-magellan                - X.Org X server -- Magellan input driver              
p   xserver-xorg-input-magictouch              - X.Org X server -- MagicTouch input driver            
p   xserver-xorg-input-microtouch              - X.Org X server -- MicroTouch input driver            
i   xserver-xorg-input-mouse                   - X.Org X server -- mouse input driver                 
p   xserver-xorg-input-mutouch                 - X.Org X server -- muTouch input driver               
p   xserver-xorg-input-palmax                  - X.Org X server -- Palmax input driver                
p   xserver-xorg-input-penmount                - X.Org X server -- Penmount input driver              
p   xserver-xorg-input-spaceorb                - X.Org X server -- SpaceOrb input driver              
p   xserver-xorg-input-summa                   - X.Org X server -- Summa input driver                 
i   xserver-xorg-input-synaptics               - Synaptics TouchPad driver for X.Org server           
p   xserver-xorg-input-tek4957                 - X.Org X server -- Tek4957 input driver               
p   xserver-xorg-input-ur98                    - X.Org X server -- UR98 input driver                  
p   xserver-xorg-input-vmmouse                 - X.Org X server -- vmmouse input driver               
p   xserver-xorg-input-void                    - X.Org X server -- void input driver                  
i   xserver-xorg-input-wacom                   - X.Org X server -- wacom input driver                 
v   xserver-xorg-video                         -                                                      
v   xserver-xorg-video-1.0                     -                                                      
i   xserver-xorg-video-all                     - the X.Org X server -- output driver metapackage      
p   xserver-xorg-video-amd                     - X.Org X server -- AMD display driver                 
i   xserver-xorg-video-apm                     - X.Org X server -- APM display driver                 
i   xserver-xorg-video-ark                     - X.Org X server -- ark display driver                 
i   xserver-xorg-video-ati                     - X.Org X server -- ATI display driver                 
i   xserver-xorg-video-chips                   - X.Org X server -- Chips display driver               
i   xserver-xorg-video-cirrus                  - X.Org X server -- Cirrus display driver              
i   xserver-xorg-video-cyrix                   - X.Org X server -- Cyrix display driver               
i   xserver-xorg-video-dummy                   - X.Org X server -- dummy display driver               
i   xserver-xorg-video-fbdev                   - X.Org X server -- fbdev display driver               
i   xserver-xorg-video-glint                   - X.Org X server -- Glint display driver               
i   xserver-xorg-video-i128                    - X.Org X server -- i128 display driver                
i   xserver-xorg-video-i740                    - X.Org X server -- i740 display driver                
i   xserver-xorg-video-i810                    - X.Org X server -- Intel i8xx, i9xx display driver    
i   xserver-xorg-video-imstt                   - X.Org X server -- IMSTT display driver               
p   xserver-xorg-video-intel                   - X.Org X server -- Intel i8xx, i9xx display driver    
i   xserver-xorg-video-mga                     - X.Org X server -- MGA display driver                 
i   xserver-xorg-video-neomagic                - X.Org X server -- Neomagic display driver            
i   xserver-xorg-video-newport                 - X.Org X server -- Newport display driver             
i   xserver-xorg-video-nsc                     - X.Org X server -- NSC display driver                 
i   xserver-xorg-video-nv                      - X.Org X server -- NV display driver                  
i   xserver-xorg-video-rendition               - X.Org X server -- Rendition display driver           
i   xserver-xorg-video-s3                      - X.Org X server -- legacy S3 display driver           
i   xserver-xorg-video-s3virge                 - X.Org X server -- S3 ViRGE display driver            
i   xserver-xorg-video-savage                  - X.Org X server -- Savage display driver              
i   xserver-xorg-video-siliconmotion           - X.Org X server -- SiliconMotion display driver       
i   xserver-xorg-video-sis                     - X.Org X server -- SiS display driver                 
i   xserver-xorg-video-sisusb                  - X.Org X server -- SiS USB display driver             
i   xserver-xorg-video-tdfx                    - X.Org X server -- tdfx display driver                
i   xserver-xorg-video-tga                     - X.Org X server -- TGA display driver                 
i   xserver-xorg-video-trident                 - X.Org X server -- Trident display driver             
i   xserver-xorg-video-tseng                   - X.Org X server -- Tseng display driver               
p   xserver-xorg-video-unichrome               - X.Org X server -- VIA display driver                 
i   xserver-xorg-video-v4l                     - X.Org X server -- Video 4 Linux display driver       
i   xserver-xorg-video-vesa                    - X.Org X server -- VESA display driver                
i   xserver-xorg-video-vga                     - X.Org X server -- VGA display driver                 
i   xserver-xorg-video-via                     - X.Org X server -- VIA display driver                 
i   xserver-xorg-video-vmware                  - X.Org X server -- VMware display driver              
i   xserver-xorg-video-voodoo                  - X.Org X server -- Voodoo display driver              
p   xshogi                                     - An X Window System Japanese Chess (Shogi) Board      
p   xsteg                                      - Graphical frontend to stegdetect                     
p   xt-catalog                                 - Catalog support and wrapper for XSLT Processor XT    
i   xtightvncviewer                            - virtual network computing client software for X      
p   xubuntu-at-mag                             - screen magnifying for Xubuntu                        
p   xubuntu-default-settings                   - default settings for Xubuntu                         
p   xulrunner-gnome-support                    - Support for Gnome in xulrunner applications          
p   xviewg                                     - XView shared libraries                               
p   xviewg-dev                                 - XView development tools                              
p   xxgdb                                      - A X front-end to the GNU debugger gdb                
p   xzgv                                       - Picture viewer for X with a thumbnail-based selector 
p   yagiuda                                    - software to analyse performance of Yagi-Uda antennas 
p   yasgml                                     - Yet Another Linuxdoc-DTD only SGML mode              
p   yate-gtk2                                  - YATE and GTK+ 2 based universal telephony client     
p   yate-pgsql                                 - Postgresql module for yate                           
p   ygraph                                     - Visualize one-dimensional scientific data            
p   yiyantang                                  - Terminal-based Chinese automatic encoding converter  
p   zabbix-agent                               - software for monitoring of your networks -- agent    
p   zabbix-server-pgsql                        - software for monitoring of your networks -- server   
p   zangband                                   - A single-player, text-based, roguelike game          
p   zapping                                    - television viewer for the GNOME environment          
p   zblast-svgalib                             - svgalib version of zblast, shoot 'em up space game   
p   zgv                                        - SVGAlib graphics viewer                              
p   zinf-plugin-alsa                           - ALSA plugin for ZINF                                 
p   zinf-plugin-arts                           - aRts plugin for ZINF                                 
p   zinf-plugin-esound                         - EsounD plugin for ZINF                               
i   zlib1g                                     - compression library - runtime                        
p   zlib1g-dev                                 - compression library - development                    
p   zoidberg                                   - modular Perl shell                                   
p   zonecheck-cgi                              - A DNS configuration checker, Web interface           
p   zope-atseng                                - framework to provide flexible schema editing for AT c
p   zope-coreblog                              - blog/weblog/web nikki system for zope                
p   zope-coreblog2                             - blog product for the Plone content management system 
p   zope-genericsetup                          - mini-framework for filesystem-based configuration of 
p   zope-groupuserfolder                       - zope add-on that provides user flagged as groups     
p   zope-ldapmultiplugins                      - LDAP plugin for Zope/Plone                           
p   zope-linguaplone                           - multilingual and translation solution for plone      
p   zope-mimetypesregistry                     - mimetypes registry for Zope                          
p   zope-plonecollectorng                      - bugtracking system and framework based on plone and a
p   zope-ploneerrorreporting                   - error reporting tool for plone 2.0                   
p   zope-plonelanguagetool                     - language manager and handler for plone               
p   zope-pluginregistry                        - generalized tool for registering plugins for zope pro
p   zope-psycopgda                             - Zope database adapter based on python-psycopg        
p   zope-psycopgda2                            - Zope database adapter based on python-psycopg2       
p   zope-rdfgrabber                            - Zope Product to search foreign webpages by their RDF 
p   zope-resourceregistries                    - zope registry for linked stylesheet files and javascr
p   zope-statusmessages                        - status messages handler for Zope and Plone sites     
p   zope-stripogram                            - library for converting HTML to plain text for zope   
p   zope-textindexng2                          - full text index for Zope                             
p   zope-textindexng2-lib                      - full text index for Zope                             
p   zope3-dbg                                  - Open Source Web Application Server (debug extensions)
p   zpkg                                       - build software distributions based on the Python dist
p   zsh-dbg                                    - A shell with lots of features (debugging symbols)    
guyver1@ubuntu:~$ 

```

---

### Post by tseliot on 2007-08-25
> **Guyver1 said:**
> it scrolled too much stuff for me to copy it all sorry, and i dont know the switches to page up and get the rest, heres what i could get from the terminal window:
Sorry, try this command:
```
sudo aptitude show g++
```

---

### Post by Guyver1 on 2007-08-26
ok here's what i got:

```

guyver1@ubuntu:~$ sudo aptitude show g++
Password:
Package: g++
State: not installed
Version: 4:4.1.2-1ubuntu1
Priority: optional
Section: devel
Maintainer: Ubuntu Core developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 41.0k
Depends: cpp (>= 4:4.1.2-1ubuntu1), gcc (>= 4:4.1.2-1ubuntu1), g++-4.1 (>=
         4.1.2), gcc-4.1 (>= 4.1.2)
Provides: c++-compiler
Description: The GNU C++ compiler
 This is the GNU C++ compiler, a fairly portable optimizing compiler for C++. 
 
 This is a dependency package providing the default GNU C++ compiler.

guyver1@ubuntu:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  g++: Depends: g++-4.1 (>= 4.1.2) but it is not going to be installed
E: Broken packages
guyver1@ubuntu:~$ 

```

---

### Post by EXCiD3 on 2007-08-26
> E: Broken packages

looks like tseliot was right, looks like they they broke those packages and therefore you will have trouble using envy for installation since it requires that for your kernel.

---

### Post by Guyver1 on 2007-08-26
all fixed tseliot

i had to re-enable the gutsy sources and it downloaded the new g++, then i was able to install the build-essential

envy is now installed :)

cheers for your help, its appreciated greatly

Leon.

---

