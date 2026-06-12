---
title: "thunderbird install problems"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-10-06
I manually downloaded thunderbird-2.0.0.23.tar.gz frm the mozilla website and tried to install it on mu 8.10 install.

heres how i dit it.....
i first extracted it on to my desktop and then after a lot of googleing came across instructions which i folowed..as below

   1. Download Thunderbird 2. (Save to disk)
   2. sudo tar -C /opt -zxvf ~/Desktop/thunderbird-*
   3. sudo ln -s /opt/thunderbird/thunderbird /usr/local/bin/thunderbird
   4. create a menu item: sudo gedit /usr/share/applications/thunderbird.desktop

    [Desktop Entry]
    Encoding=UTF-8
    Name=Thunderbird
    Comment=Thunderbird Mail Client
    Exec=thunderbird
    Icon=/opt/thunderbird/icons/mozicon16.xpm
    StartupNotify=true
    Terminal=false
    Type=Application
    Categories=Applications;Network


from the link 
[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/](http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/)

but then after i lauched thunderbird from   Applications>internet>mzilla thunderbird mail news......it does nothing(a icon for thunderbird come in the toolbar and stays there for 5 seconds as if launching but then goes away

i then wient to synaptic pakage manager and selected mozilla thunderbird for install 
synaptic downloaded a 11.1 MB file and after that its still the same thing...


whats gone wrong..Any ideas?

---

### Post by orange-wedge on 2009-10-06
I would try out ubuntuzilla.py from sourceforge.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

I just downloaded it to install Firefox 3.5, but the manual says it can also automate the installation of Thunderbird.

---

### Post by oldfred on 2009-10-07
from the terminal type in 

thunderbird

if you get any error messages let us know.

---

### Post by wilee-nilee on 2009-10-07
If you cant get it going just remove what you have doe and run sudo apt-get thunderbird  it is in the repositories.

---

### Post by richlyn9 on 2009-10-08
ran "thunderbird" from terminal...
heres the error message :

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


what now?

---

### Post by MelDJ on 2009-10-08
> **wilee-nilee said:**
> if you cant get it going just remove what you have doe and run sudo apt-get thunderbird  it is in the repositories.

+1

---

### Post by richlyn9 on 2009-10-08
> **oldfred said:**
> from the terminal type in 

thunderbird

if you get any error messages let us know.
ran "thunderbird" from terminal...
heres the error message :

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by richlyn9 on 2009-10-08
sorry PPL  for too duplicate replies ...
 i am having issues with my dial up connection..

Is there a way i can delete my reply?

---

### Post by presence1960 on 2009-10-08
> **wilee-nilee said:**
> If you cant get it going just remove what you have doe and run sudo apt-get thunderbird  it is in the repositories.

that would be ```
sudo apt-get install thunderbird
```

---

### Post by wilee-nilee on 2009-10-08
> **presence1960 said:**
> that would be ```
sudo apt-get install thunderbird
```

 You are correct, thanks for noticing.

---

### Post by richlyn9 on 2009-10-08
> **presence1960 said:**
> that would be ```
sudo apt-get install thunderbird
```
I did sudo apt-get install thunderbird 

heres the result.:

richlyn@richlyn-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird is already the newest version.
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxrender-dev libfontconfig1-dev
  x11proto-composite-dev libxcursor-dev x11proto-randr-dev x11proto-damage-dev
  libxdamage-dev libfreetype6-dev x11proto-fixes-dev libxcomposite-dev
  libxrandr-dev libexpat1-dev libxft-dev libxfixes-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 279 not upgraded.
richlyn@richlyn-desktop:~$

---

### Post by richlyn9 on 2009-10-08
> **orange-wedge said:**
> I would try out ubuntuzilla.py from sourceforge.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

I just downloaded it to install Firefox 3.5, but the manual says it can also automate the installation of Thunderbird.
**i tried this also: **
    [I]*  If you happen to have already downloaded the appropriate Thunderbird, Firefox, or SeaMonkey tar.gz archive to your drive, and want to avoid another download, place your downloaded tar.gz into /tmp (without changing the original filename). The script will still ask you questions about the version, localizations, etc., but will not actually make another download.
    * Open a terminal 

Note: do not run ubuntuzilla with sudo. That will mess up the ownership of some of the files in your home directory (e.g., the stuff in ~/.gnupg).

    * Enter one of the following commands to run the script (choose one depending on which software you want to install; copy and paste to avoid typos): 

ubuntuzilla.py -a install -p firefox

ubuntuzilla.py -a install -p thunderbird

ubuntuzilla.py -a install -p seamonkey[/I]

**heres what i get:**

[B]richlyn@richlyn-desktop:~$ ubuntuzilla.py -a install -p thunderbird
bash: ubuntuzilla.py: command not found[/B]

---

### Post by oldfred on 2009-10-08
Any software that is in the repositories should only be downloaded and installed that way. Installing from the .deb leads back to the bad old days of dependency hell.

If your thunderbird is not working it is because the first install from the .deb was not correct. It would be best to go back to synaptic and mark for complete removal and apply that. After it uninstalls and deletes everything go back and check it again to reinstall.

You can also install 'firefox 3.5' from synaptic. If you use what I have in quotes it will come up. After it installs it will be shiretoko. When karmic comes out 3.5 will be standard.

---

### Post by presence1960 on 2009-10-08
> **richlyn9 said:**
> I did sudo apt-get install thunderbird 

heres the result.:

richlyn@richlyn-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]thunderbird is already the newest version[/COLOR].
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxrender-dev libfontconfig1-dev
  x11proto-composite-dev libxcursor-dev x11proto-randr-dev x11proto-damage-dev
  libxdamage-dev libfreetype6-dev x11proto-fixes-dev libxcomposite-dev
  libxrandr-dev libexpat1-dev libxft-dev libxfixes-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 279 not upgraded.
richlyn@richlyn-desktop:~$
Then you already have thunderbird installed- see the red above!

---

### Post by richlyn9 on 2009-10-09
i went to add/remove applications and removed thunderbird and applied changes.

then from the terminal this is what i did.


richlyn@richlyn-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxrender-dev libfontconfig1-dev
  x11proto-composite-dev libxcursor-dev x11proto-randr-dev x11proto-damage-dev
  libxdamage-dev x11proto-fixes-dev libxcomposite-dev libxrandr-dev
  libexpat1-dev libxft-dev libxfixes-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 220 not upgraded.
Need to get 0B/11.1MB of archives.
After this operation, 33.2MB of additional disk space will be used.
Selecting previously deselected package thunderbird.
(Reading database ... 108166 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.23+build1+nobinonly-0ubuntu0.8.10.1_i386.deb) ...
Processing triggers for man-db ...
Setting up thunderbird (2.0.0.23+build1+nobinonly-0ubuntu0.8.10.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
richlyn@richlyn-desktop:~$ thunderbird
/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
richlyn@richlyn-desktop:~$ 


its still the same....

i am eargerly waiting for  Kramic
will thunderbird be standard instead of evolution?

---

