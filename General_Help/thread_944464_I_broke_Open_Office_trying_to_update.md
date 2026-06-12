---
title: "I broke Open Office trying to update"
date: 2008-10-11
forum: General Help
---

### Post by snkngshps on 2008-10-11
I followed a guide on how to update to Open Office 3 early. Here are the commands I used:


wget [http://openofficeorg.secsup.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz](http://openofficeorg.secsup.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz)

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

cd cd OOO300_m9_native_packed-1_en-US.9358/DEBS

sudo dpkg -i *.deb



Unfortunately, while I didn't get any errors while running those commands I've messed up Open Office. When I start it, it's still listed as 2.4, so it didn't properly update. It also gives me this new error message when it starts:

"OpenOffice.org could not save important internal information due to insufficient free disk space at the following location: /home/joshua/.openoffice.org2/user/backup 
You will not be able to continue working with OpenOffice.org without allocating more free disk space at that location.
Press the 'Retry' button after you have allocated more free disk space to retry saving the data"

Does anyone know what I can do to fix this? :-/

---

### Post by geirha on 2008-10-11
Well, It's probable that openoffice 3 has installed to a different location than 2.4. Try typing ```
type -a openoffice
``` in a terminal. Try running each of the entries from the terminal.

Secondly, have you checked how much free space you have in /home? ```
df -h
```

---

### Post by snkngshps on 2008-10-11
Here is what I got from both of those commands:

joshua@SNKNGSHPS:~$ type -a openoffice
openoffice is /usr/bin/openoffice
joshua@SNKNGSHPS:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G  102G     0 100% /
varrun                950M  120K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   44K  950M   1% /dev
devshm                950M  100K  950M   1% /dev/shm
lrm                   950M   39M  911M   5% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      107G  102G     0 100% /home/joshua/.gvfs
joshua@SNKNGSHPS:~$

---

### Post by geirha on 2008-10-11
> **snkngshps said:**
> 
```

joshua@SNKNGSHPS:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G  102G     0 100% /

```

/ is full. You need to free up some space. Empty the trash, and run ```
 sudo apt-get clean
``` to clean up apt's cache. Might give you some 100 megs.

To figure out where the different openoffice version are installed, try
```

# to find all installed packages named something with openoffice
aptitude search '~i openoffice'
# Check the version and other information of a specific package, openoffice.org-base in this case
aptitude show openoffice.org-base
# Check where a package has installed the files
dpkg -L openoffice.org-base

```
That should hopefully get you an overview of where you'll find 2.4 and 3.0.

---

### Post by snkngshps on 2008-10-11
Ok I ran all of those commands, unfortunately I'm still not skilled enough with the terminal to know what I'm looking at so you will have to explain what to do next. Also, the apt-get clean command ran without error but didn't seem to really do anything :-/

[#]joshua@SNKNGSHPS:~$ sudo apt-get clean
joshua@SNKNGSHPS:~$ aptitude search '~i openoffice'
i   openoffice.org-base-core        - OpenOffice.org office suite -- libdba     
i   openoffice.org-calc             - OpenOffice.org office suite - spreadsheet 
i   openoffice.org-common           - OpenOffice.org office suite architecture i
i   openoffice.org-core             - OpenOffice.org office suite architecture d
i   openoffice.org-draw             - OpenOffice.org office suite - drawing     
i   openoffice.org-gnome            - GNOME Integration for OpenOffice.org (VFS,
i   openoffice.org-gtk              - GTK+ Integration for OpenOffice.org (Widge
i   openoffice.org-help-en-gb       - English_british help for OpenOffice.org   
i   openoffice.org-help-en-us       - English_american help for OpenOffice.org  
i   openoffice.org-hyphenation      - Hyphenation patterns for OpenOffice.org   
i   openoffice.org-hyphenation-en-u - US English hyphenation patterns for OpenOf
i   openoffice.org-impress          - OpenOffice.org office suite - presentation
i   openoffice.org-l10n-common      - common files for OpenOffice.org language a
i   openoffice.org-l10n-en-gb       - English_british language package for OpenO
i   openoffice.org-l10n-en-za       - English_southafrican language package for 
i   openoffice.org-style-human      - Human symbol style for OpenOffice.org     
i   openoffice.org-thesaurus-en-au  - Australian English Thesaurus for OpenOffic
i   openoffice.org-thesaurus-en-us  - English Thesaurus for OpenOffice.org      
i   openoffice.org-ure              - UNO Runtime Environment                   
i   openoffice.org-writer           - OpenOffice.org office suite - word process
i   openoffice.org3                 - Brand module for OpenOffice.org 3.0       
i   openoffice.org3-base            - Base brand module for OpenOffice.org 3.0  
i   openoffice.org3-calc            - Calc brand module for OpenOffice.org 3.0  
i   openoffice.org3-dict-en         - En dictionary for OpenOffice.org 3.0      
i   openoffice.org3-dict-es         - Es dictionary for OpenOffice.org 3.0      
i   openoffice.org3-dict-fr         - Fr dictionary for OpenOffice.org 3.0      
i   openoffice.org3-draw            - Draw brand module for OpenOffice.org 3.0  
i   openoffice.org3-en-us           - Brand language module for OpenOffice.org 3
i   openoffice.org3-impress         - Impress brand module for OpenOffice.org 3.
i   openoffice.org3-math            - Math brand module for OpenOffice.org 3.0  
i   openoffice.org3-writer          - Writer brand module for OpenOffice.org 3.0
joshua@SNKNGSHPS:~$ aptitude show openoffice.org-base
Package: openoffice.org-base
State: not installed
Version: 1:2.4.1-1ubuntu2
Priority: optional
Section: editors
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 8217k
Depends: gij | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre |
         java2-runtime, libc6 (>= 2.1.3), libgcc1 (>= 1:4.1.1-21),
         libhsqldb-java (>= 1.8.0.9-1), libstdc++6 (>= 4.1.1-21),
         openoffice.org-base-core (= 1:2.4.1-1ubuntu2), openoffice.org-core (=
         1:2.4.1-1ubuntu2), openoffice.org-java-common (> 2.2.0-4)
PreDepends: dpkg (>= 1.14.12ubuntu3)
Suggests: libmyodbc | odbc-postgresql | libsqliteodbc | tdsodbc | mdbtools,
          libmysql-java | libpg-java, openoffice.org-gcj,
          openoffice.org-report-builder, unixodbc
Conflicts: openoffice.org-common (= 2.0.4-4), openoffice.org-debian-files,
           openoffice.org2-base (< 1:2.4.1-1ubuntu2)
Replaces: openoffice.org-bin (< 1.9), openoffice.org-common (< 1.9.113-0pre1),
          openoffice.org-core (< 2.0.1), openoffice.org-debian-files,
          openoffice.org-java, openoffice.org2-base (< 1:2.4.1-1ubuntu2)
Provides: openoffice.org2-base
Description: OpenOffice.org office suite - database
 OpenOffice.org is a full-featured office productivity suite that provides a
 near drop-in replacement for Microsoft(R) Office. 
 
 This package contains the database component for OpenOffice.org. 
 
 You can extend the functionality of OpenOffice.org Base by installing these
 packages: 
 
 * unixodbc: ODBC database support 
 * libmyodbc | odbc-postgresql | libsqliteodbc | tdsodbc | mdbtools: ODBC
   drivers for: - MySQL - PostgreSQL - SQLite - MS SQL / Sybase SQL - *.mdb (JET
   / MS Access) 
 * libmysql-java | libpg-java: JDBC Drivers for: - MySQL - PostgreSQL
Homepage: [http://www.openoffice.org](http://www.openoffice.org)

joshua@SNKNGSHPS:~$ dpkg -L openoffice.org-base
Package `openoffice.org-base' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
joshua@SNKNGSHPS:~$ [/#]

---

### Post by geirha on 2008-10-11
Right, the openoffice 2.4 packages are the ones starting with openoffice.org-, while 3.0 is the ones starting with openoffice.org3-.

So check where the files for openoffice 3.0 writer is installed with:
```
dpkg -L openoffice.org3-writer | grep oowriter 
```
the 2.4 version is at /usr/bin/oowriter, I'm guessing the 3.0 is at /opt/openoffice-somthing/bin/oowriter ...


BTW, there's a GUI tool that shows you how much space you've used. You'll find it at Applications -> Accessories -> Disk Usage Analyzer.

---

### Post by snkngshps on 2008-10-11
I didn't get any output with that last command but no errors either.
```
joshua@SNKNGSHPS:~$ dpkg -L openoffice.org3-writer | grep oowriter
joshua@SNKNGSHPS:~$ 

```

---

### Post by Bucky Ball on 2008-10-11
Try this:

                                       [LEFT]```
sudo dpkg --configure -a
```

[/LEFT]
    [LEFT]Configures outstanding packages ...
[/LEFT]

---

### Post by snkngshps on 2008-10-11
> **Bucky Ball said:**
> Try this:

                                       [LEFT]```
sudo dpkg --configure -a
```

[/LEFT]
    [LEFT]Configures outstanding packages ...
[/LEFT]

That command ran successfully but there was no output. I tried opening open office again and it's still opening 2.4 (but I'm no longer getting the error message I was getting originally). Could it be that I just need to set up open office 3 to open from the applications menu? Is there a way I can delete or over write 2.4?

---

### Post by thomas228 on 2008-10-16
> **snkngshps said:**
> That command ran successfully but there was no output. I tried opening open office again and it's still opening 2.4 (but I'm no longer getting the error message I was getting originally). Could it be that I just need to set up open office 3 to open from the applications menu? Is there a way I can delete or over write 2.4?

I'm a newbie so you may not want to follow my advice but it seems to me that you could free up more than 8MB by removing all openoffice packages and starting the 00o3 installation over. You may have to run the sudo apt clean command given earlier in these posts but if you can end up with the recommended 4-5MB you should be able to install the 00o3 version.

Here's what I did to install OpenOffice 00o3.

Selected "System > Administration > Synaptic Package Manager" and entered my password

In the package manager I selected the "Search" button and typed "openoffice" in Search and selected the Search button which gave me all of the openoffice packages.

I went thru all of the installed openoffice packages and marked them with the "Mark for Complete Removal"
including "Mark" additional required changes.

Next I selected the "Apply" button and confirmed in the summary by selecting the "Apply" button

When this was finished I opened a terminal and did the following

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

The only warnings I got were:

Setting up openoffice.org3-dict-en (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

Setting up openoffice.org3-dict-es (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

Setting up openoffice.org3-dict-fr (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

These did not seem to harm anything for I was able to go in the "Applications > Office " and choose any of the 7 OpenOffice.org 3.0 options.   

The main key was to be sure I had removed all the OpenOffice packages with System Aministration Synaptic Packge Manager before installing the new tarball.

Hope this helps as ubuntu is not including OpenOffice3 either as an update for Hardy nor as part of Intrepid.

Tom

---

### Post by scouser73 on 2008-10-16
Have you removed the previous version of OpenOffice? sudo apt-get remove openoffice*.*  [http://www.quicktweaks.com/2008/10/1...nal-in-ubuntu/](http://www.quicktweaks.com/2008/10/1...nal-in-ubuntu/)

---

### Post by jimv on 2008-10-16
You didn't break anything.  OpenOffice3 installs to a different location than 2.4.  IT DOES NOT REPLACE 2.4.  I imagine we'll have to wait for official Ubuntu Debs for that.  By coincidence, your HD also got filled up.  To remove OpenOffice3, open a terminal and type:

```
sudo apt-get remove openoffice.org3-* ooobasis3.0-*
```

Then I recommend waiting until OpenOffice3 is added to the Ubuntu repositories before installing it again.

For reference, OpenOffice3 installs to /opt/openoffice.org3.

---

### Post by Bucky Ball on 2008-10-16
Thomas228, you need to install through synaptics or apt-get install it through a terminal:

**ubuntu-restricted-extras**

This will fix your java problem. :)

---

### Post by thomas228 on 2008-10-17
> **Bucky Ball said:**
> Thomas228, you need to install through synaptics or apt-get install it through a terminal:

**ubuntu-restricted-extras**

This will fix your java problem. :)

Thanks Bucky Ball

I had removed all restricted items in order to install my AR5007EG wifi. I'll install your recommended package and hopefully it won't affect my wifi drivers. 

Thanks again

Tom

---

### Post by shivchal on 2008-11-02
I got these errors 

Setting up openoffice.org3-dict-en (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

Setting up openoffice.org3-dict-es (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

Setting up openoffice.org3-dict-fr (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 




dpkg: regarding .../openoffice.org3.0-debian-menus_3.0-9354_all.deb containing openoffice.org-debian-menus:                                                     
 openoffice.org-core conflicts with openoffice.org-unbundled                    
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing /home/natesan/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 /home/natesan/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb

I have JRE installed in /usr/local/jre1.6.0_10 and have exported $JAVA_HOME to this folder.

Thanks in advance for all the help.

---

### Post by Captain Legless on 2009-01-28
> **thomas228 said:**
> I'm a newbie so you may not want to follow my advice .........................................

...................Hope this helps as ubuntu is not including OpenOffice3 either as an update for Hardy nor as part of Intrepid.

Tom

Worked perfectly for me thanks!!:D

Just had to amend the appropriate numbers in the file names.

---

