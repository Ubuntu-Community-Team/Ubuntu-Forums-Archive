---
title: "Kubuntu KDE3 Remix RC upgrade not working?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by mark0495 on 2009-04-23
Hello, 

I want to install the RC of the KDE 3 remix of Kubuntu 9.04 on my computer. The Kubuntu site says the following about the installation process:

> It is relatively simple to upgrade from Kubuntu 8.04 to Kubuntu 9.04 with KDE3.5, but the process has not been automated.
 You will therefore have to follow these steps to ensure a successful update without losing your KDE settings: 
1. Copy your /home/<username>/.kde folder to /home/<username>/.kde3 You will have to do this for all users of the computer that you are upgrading. Make sure that the permissions and ownership of these files are not disturbed in any way. 
2. Perform the upgrade as you normally would. 
3. After you reboot, you will have a KDE4 desktop. Don't worry, this is temporary. Now install the kubuntu-desktop-kde3 package with your favorite package manager and reboot. 
4. You should now be able to select KDE3 as your window manager at the login screen. You can also remove the KDE4 packages with your favorite package manager if you do not want to have KDE4 installed. 
Once you have upgraded to either Intrepid with KDE3.5 or Jaunty with KDE3.5, you will be able to perform future upgrades without having to follow the above steps. 

I did the first 2 steps. Then I tried to do:

> sudo apt-get install kubuntu-desktop-kde3

The terminal says that the package was not found. Can anyone help me upgrading the computer now? I really want to use KDE 3 because my computer works far too slow on KDE4.2

Mark

---

### Post by raphha on 2009-04-25
Hello,
check the instructions from [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/).
Don't forget the sudo apt-get update after you add the new repos to your sources.list
Best,
Raph

---

### Post by mark0495 on 2009-04-26
> Hello,
check the instructions from [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/).
Don't forget the sudo apt-get update after you add the new repos to your sources.list
Best,
Raph

Thanks, I did that and now it works. However, it's not ENTIRELY working. Now I want to remove KDE4. I try to remove it, but every time I want to the Konsole says: 

> You probably want to run "apt-get install -f" to solve the following: 
The following packages have dependencies not met:
 kubuntu-desktop-kde3: 
Dependencies: konq-plugins-kde3 but it won't be installed.
                        
Recommendations: amarok-kde3 but it won't be installed
                        
Recommendations: desktop-effects-kde-kde3 but it won't be installed
                        
Recommendations: digikam-kde3 but it won't be installed
                        
Recommendations: gwenview-kde3 but it won't be installed
                        
Recommendations: kaffeine-kde3 but it won't be installed
       
Recommendations: kdebluetooth-kde3 but it can't be installed
                        
Recommendations: kipi-plugins-kde3 but it won't be installed
                        
Recommendations: kubuntu-docs-kde3 but it can't be installed
                        
Recommendations: strigi-applet but it can't be installed
                        
Recommendations: system-config-printer-kde-kde3 but it can't be installed
                        
Recommendations: network-manager-kde-kde3 but it won't be installed

There are dependencies not met. You should use "apt-get install -f" without indicating packages, or specify an own solution.


So I run:

>  sudo apt-get -f install

The following packages are installed automatically and are not needed anymore
  k3b-data libnjb5
You can remove them with 'apt-get autoremove'.
The following extra packages will be installed:
  konq-plugins-kde3
Proposed packages:
  kdeaddons-kde3-doc-html
The following NEW packages will be installed:
  konq-plugins-kde3
0 packages upgraded, 1 package newly installed, 0 to be removed amd 0 not up-to-date.
173 not fully installed or removed.
0B/1159kB of archives has to be obtained.
Because of this operation 3977kB extra disk space will be used.
Do you want to continue? [Y/n]?
(Reading database ... 124036 files and directories installed.)
Extracting konq-plugins-kde3 (from .../konq-plugins-kde3_4%3a3.5.10-0ubuntu1~intrepid2_i386.deb) ...
dpkg: error finishing /var/cache/apt/archives/konq-plugins-kde3_4%3a3.5.10-0ubuntu1~intrepid2_i386.deb (--unpack):
 try to overwrite `/usr/share/man/man1/fsview.1.gz', which is also in the package konqueror-plugin-fsview.
dpkg-deb: subprocess paste was killed by signal. (broken pipe)
Processing triggers for man-db ...
Found errors while handling:
 /var/cache/apt/archives/konq-plugins-kde3_4%3a3.5.10-0ubuntu1~intrepid2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone help me, because I want a FULL, WORKING system and I can't use apt-get in any way now except for fixing this problem, and I don't know how I should do that.

*There can be a slight difference in the translation; I'm still using the Dutch version.

---

