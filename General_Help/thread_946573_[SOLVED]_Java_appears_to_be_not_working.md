---
title: "[SOLVED] Java appears to be not working"
date: 2008-10-13
forum: General Help
---

### Post by DougAlder on 2008-10-13
This morning I ran a recommended update and now I can't seem to load anything that requires java. For example if I go to youtube the page will load but where the video should be all I get is a gray window and afterwards Firefox is screwed. I can close FF but it will not reopen unless I reboot. Tried in Opera as well and get the same result except that I can close Opera and restart it.

I tried, through the package manager to revert back to Java runtime 5 and that didsn't work and when I rebooted the updates suggested going back to Java 6 so I did and that hasn't helped. 

I don't know how to diagnose or fix this problem. Any help will be greatly appreciated


update:

If I try to open a local flash video with Totem I get an error message stating there is a missing html/text plugin but it doesn't tell me which plugin - checking in Totem all the plugins except the wireless one are listed as enabled.. Everything seems to work except Flash. Everything was working fine last night and when I booted this morning there was recommended updates message so I ran the updates and then this problem started. I don't know wherer to begin looking for what was updated or how to figure out which update caused the problem. I have unistalled andreinstalled the Macromedia flash plugin as well as Totem. I also tried installingthe Gnash swf viewer but it doesn't even seem to run.

---

### Post by ju2wheels on 2008-10-13
Open synaptic and click the search button and type in "sun java". What version shows up as being installed?

You should at a minimum have sunjavaX-jre and I believe sunjavaX-plugin (I dont remember the name of the second one as Im running on 64bit) where X is 5 or higher.

If you do have that then run the following:
```

sudo update-java-alternatives -l

```

Which will give you a listing like this:
```

java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj

```

From this list select the version of sun java you installed (In this case I will assume it was sunjava6-jre):
```

sudo update-java-alternatives -s java-6-sun

```

Once you complete that you want to add the path listed above next to java-6-sun to the /etc/jvm as the first line:
```

gksudo gedit /etc/jvm

```

Now add /usr/lib/jvm/java-6-sun as the first line in the file before all the other paths listed in the file and save it.

Now run the following to double check its installed properly:
```

java -version

```

Which should give output similar to:
```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b23, mixed mode)

```

---

### Post by DougAlder on 2008-10-13
Synaptic reports sun-java6.jre  6-07-3ubuntu2 is installed along with the sun-java6.plugin

running

```

sudo update-java-alternatives -l

```

gave me

```
root@doug-laptop:/home/doug# update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

```

Running

```

sudo update-java-alternatives -s java-6-sun

```

gave me a bunch of no alternatives and the following

```
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'firefox-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'iceape-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'iceweasel-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'midbrowser-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'mozilla-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'xulrunner-1.9-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'xulrunner-javaplugin.so'
```

> Now add /usr/lib/jvm/java-6-sun as the first line in the file before all the other paths listed in the file and save it.


Done

```

java -version

```

returns

```
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Server VM (build 10.0-b23, mixed mode)

```

I'll test this now and see if it fixed the problem. brb :)

---

### Post by DougAlder on 2008-10-13
No that didn't work - still can't view any flash videos and it still locks up Firefox. I rebooted as well just to be certain

I also tried (as a suggestion on someone else's post)

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```

but there were no changes

---

### Post by ju2wheels on 2008-10-13
Well java has nothing to do with the flash issue.

In order to get flash working install the following:
```

sudo apt-get install flashplugin-nonfree libflashsupport

```

---

### Post by DougAlder on 2008-10-13
> **ju2wheels said:**
> Well java has nothing to do with the flash issue.

In order to get flash working install the following:
```

sudo apt-get install flashplugin-nonfree libflashsupport

```

I did - it returned

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following NEW packages will be installed:
  libflashsupport
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8480B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com hardy-backports/universe libflashsupport 1.9-0ubuntu2~hardy1+really0ubuntu1 [8480B]
Fetched 8480B in 0s (12.7kB/s)        
Selecting previously deselected package libflashsupport.
(Reading database ... 175507 files and directories currently installed.)
Unpacking libflashsupport (from .../libflashsupport_1.9-0ubuntu2~hardy1+really0ubuntu1_i386.deb) ...
Setting up libflashsupport (1.9-0ubuntu2~hardy1+really0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@doug-laptop:/home/doug#

```

but that still hasn't solved the problem.

---

### Post by ju2wheels on 2008-10-13
Open synaptic and do a search for flash. Remove flashplugin-nonfree, libflashsupport, and any alternate flash plugins like gnash. Once its removed make sure synaptic doesnt show residual config left behind in the c ategories on the left. Then reinstall the flashplugin-nonfree and libflashsupport.

[Edit] Also be sure to restart Firefox completely after installing the flash plugin.

---

### Post by DougAlder on 2008-10-13
> **ju2wheels said:**
> Open synaptic and do a search for flash. Remove flashplugin-nonfree, libflashsupport, and any alternate flash plugins like gnash. Once its removed make sure synaptic doesnt show residual config left behind in the c ategories on the left. Then reinstall the flashplugin-nonfree and libflashsupport.

[Edit] Also be sure to restart Firefox completely after installing the flash plugin.

OK I did that - in Synaptic I removed everything that was marked green (which I presume means installed) except one of the ubuntu repositoriesthen rebooted as FF would not reopen - problem remains - if using FF it locks it up and if using Opera it just gives a grey window where the vid should be but doesn't lock up Opera. regarding residual config - I'm guessing that's listed under Status - not installed (something can't recall what it said) - there were a few things I selected in there and said completely uninstall.

when I reinstalled I got

```
The following NEW packages will be installed:
  flashplugin-nonfree libflashsupport
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/27.3kB of archives.
After this operation, 233kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 175449 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb) ...
Selecting previously deselected package libflashsupport.
Unpacking libflashsupport (from .../libflashsupport_1.9-0ubuntu2~hardy1+really0ubuntu1_i386.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--15:06:14--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.110.70
Connecting to fpdownload.macromedia.com|72.246.110.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  205.11 KB/s
   50K .......... .......... .......... .......... ..........  3%  437.54 KB/s
  100K .......... .......... .......... .......... ..........  5%  549.50 KB/s
  150K .......... .......... .......... .......... ..........  6%  602.49 KB/s
  200K .......... .......... .......... .......... ..........  8%  598.43 KB/s
  250K .......... .......... .......... .......... .......... 10%  585.63 KB/s
  300K .......... .......... .......... .......... .......... 11%  600.81 KB/s
  350K .......... .......... .......... .......... .......... 13%  434.91 KB/s
  400K .......... .......... .......... .......... .......... 15%  599.80 KB/s
  450K .......... .......... .......... .......... .......... 16%  583.39 KB/s
  500K .......... .......... .......... .......... .......... 18%  597.79 KB/s
  550K .......... .......... .......... .......... .......... 20%  589.52 KB/s
  600K .......... .......... .......... .......... .......... 21%  605.96 KB/s
  650K .......... .......... .......... .......... .......... 23%  603.75 KB/s
  700K .......... .......... .......... .......... .......... 25%  579.76 KB/s
  750K .......... .......... .......... .......... .......... 26%  602.33 KB/s
  800K .......... .......... .......... .......... .......... 28%  595.80 KB/s
  850K .......... .......... .......... .......... .......... 30%  601.86 KB/s
  900K .......... .......... .......... .......... .......... 31%  558.76 KB/s
  950K .......... .......... .......... .......... .......... 33%  578.90 KB/s
 1000K .......... .......... .......... .......... .......... 35%  571.37 KB/s
 1050K .......... .......... .......... .......... .......... 36%  563.71 KB/s
 1100K .......... .......... .......... .......... .......... 38%  614.40 KB/s
 1150K .......... .......... .......... .......... .......... 40%  597.78 KB/s
 1200K .......... .......... .......... .......... .......... 42%  582.65 KB/s
 1250K .......... .......... .......... .......... .......... 43%  595.32 KB/s
 1300K .......... .......... .......... .......... .......... 45%  391.25 KB/s
 1350K .......... .......... .......... .......... .......... 47%  597.08 KB/s
 1400K .......... .......... .......... .......... .......... 48%  601.05 KB/s
 1450K .......... .......... .......... .......... .......... 50%  581.37 KB/s
 1500K .......... .......... .......... .......... .......... 52%  598.90 KB/s
 1550K .......... .......... .......... .......... .......... 53%  400.01 KB/s
 1600K .......... .......... .......... .......... .......... 55%  598.57 KB/s
 1650K .......... .......... .......... .......... .......... 57%  593.67 KB/s
 1700K .......... .......... .......... .......... .......... 58%  589.89 KB/s
 1750K .......... .......... .......... .......... .......... 60%  595.11 KB/s
 1800K .......... .......... .......... .......... .......... 62%  396.11 KB/s
 1850K .......... .......... .......... .......... .......... 63%  602.22 KB/s
 1900K .......... .......... .......... .......... .......... 65%  419.98 KB/s
 1950K .......... .......... .......... .......... .......... 67%  585.14 KB/s
 2000K .......... .......... .......... .......... .......... 68%  394.74 KB/s
 2050K .......... .......... .......... .......... .......... 70%  599.56 KB/s
 2100K .......... .......... .......... .......... .......... 72%  596.84 KB/s
 2150K .......... .......... .......... .......... .......... 73%  584.62 KB/s
 2200K .......... .......... .......... .......... .......... 75%  596.78 KB/s
 2250K .......... .......... .......... .......... .......... 77%  100.07 KB/s
 2300K .......... .......... .......... .......... .......... 79%  330.92 KB/s
 2350K .......... .......... .......... .......... .......... 80%  566.65 KB/s
 2400K .......... .......... .......... .......... .......... 82%  602.88 KB/s
 2450K .......... .......... .......... .......... .......... 84%  586.46 KB/s
 2500K .......... .......... .......... .......... .......... 85%  449.43 KB/s
 2550K .......... .......... .......... .......... .......... 87%  597.99 KB/s
 2600K .......... .......... .......... .......... .......... 89%  599.34 KB/s
 2650K .......... .......... .......... .......... .......... 90%  582.63 KB/s
 2700K .......... .......... .......... .......... .......... 92%  451.47 KB/s
 2750K .......... .......... .......... .......... .......... 94%  599.31 KB/s
 2800K .......... .......... .......... .......... .......... 95%  602.47 KB/s
 2850K .......... .......... .......... .......... .......... 97%  596.05 KB/s
 2900K .......... .......... .......... .......... .......... 99%  575.95 KB/s
 2950K .......... .......... ...                             100%  630.02 KB/s

15:06:20 (496.88 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
Flash Plugin installed.

Setting up libflashsupport (1.9-0ubuntu2~hardy1+really0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@doug-laptop:/home/doug# 

```

but the problem persists

---

### Post by DougAlder on 2008-10-14
OK weirdness abounds. I rebooted yesterday after doing all of the above and it didn't work. This morning after a cold boot it does - go figure :() in any case I'm glad it's working - Thanks for all your help

---

