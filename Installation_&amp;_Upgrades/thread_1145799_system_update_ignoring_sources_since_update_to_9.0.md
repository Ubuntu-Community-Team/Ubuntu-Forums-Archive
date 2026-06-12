---
title: "system update ignoring sources since update to 9.04, no longer notifies automatically"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Hybrid86 on 2009-05-02
As my subject says, my updater has been ignoring sources since the update to jaunty, as well as having stopped prompting me when I need to update. Here is the output of "sudo apt-get update"

```
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Ign http://linux.getdropbox.com jaunty Release.gpg                             
Ign http://linux.getdropbox.com jaunty/main Translation-en_US                  
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://linux.getdropbox.com jaunty Release                                 
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://linux.getdropbox.com jaunty/main Packages                           
Hit http://ppa.launchpad.net jaunty Release                                    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://linux.getdropbox.com jaunty/main Sources                            
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Hit http://packages.medibuntu.org jaunty Release                               
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://linux.getdropbox.com jaunty/main Packages                           
Ign http://ppa.launchpad.net jaunty/main Packages                              
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://linux.getdropbox.com jaunty/main Sources                            
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://packages.medibuntu.org jaunty/free Packages                         
Ign http://ppa.launchpad.net jaunty/main Sources                               
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://us.archive.ubuntu.com jaunty/main Packages                
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://packages.medibuntu.org jaunty/free Sources                
Hit http://packages.medibuntu.org jaunty/non-free Sources            
Hit http://ppa.launchpad.net jaunty/main Sources                     
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Reading package lists... Done

```

In addition, the update for Brassero is greyed out in the update manager.

---

### Post by Partyboi2 on 2009-05-02
Hi Hybrid86, the Ign's you see when you run update only means that the information for those repos have not changed so looking at your output there is nothing wrong. 
Jaunty has a different way of handling  notifications  of updates. This is taken from the release notes.
> Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week. 
 Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command: 
 
 gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by Hybrid86 on 2009-05-02
I see; thank you so much :)

The only mystery left unsolved then is Brassero being grayed out in the update manager. I've searched around and cannot find anything on it.

---

### Post by Hybrid86 on 2009-05-02
Here is the output of "sudo apt-get upgrade"

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

As you can see, its being held back.

---

### Post by Elwro on 2009-05-02
I had the same problem. It was solved in this thread: [http://ubuntuforums.org/showthread.php?t=1140547&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1140547&highlight=brasero)

But even before going there, just try```

sudo apt-get remove brasero && sudo apt-get install brasero

```

---

### Post by Hybrid86 on 2009-05-02
Okay, so here's where it gets weird. Here is the output from that operation. As you can see, it actually asks for a CD

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml-rss-perl libdatetime-locale-perl libparams-validate-perl
  libgtk2-trayicon-perl libdatetime-perl libgtk2-gladexml-perl
  libdatetime-format-w3cdtf-perl libdatetime-format-mail-perl
  libdatetime-timezone-perl libclass-singleton-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  brasero
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 7893kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142712 files and directories currently installed.)
Removing brasero ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml-rss-perl libdatetime-locale-perl libparams-validate-perl
  libgtk2-trayicon-perl libdatetime-perl libgtk2-gladexml-perl
  libdatetime-format-w3cdtf-perl libdatetime-format-mail-perl
  libdatetime-timezone-perl libclass-singleton-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libbrasero-media0
Suggested packages:
  gstreamer0.10-fluendo-mp3 vcdimager
The following packages will be REMOVED:
  nautilus-cd-burner
The following NEW packages will be installed:
  brasero libbrasero-media0
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/1632kB of archives.
After this operation, 6914kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive '/cdrom/' and press enter

```

---

### Post by Partyboi2 on 2009-05-02
Under Software Sources make sure that "Installable from cdrom/dvd" is unticked.

---

### Post by Hybrid86 on 2009-05-02
Should have figured that out. Thank you so much.

---

