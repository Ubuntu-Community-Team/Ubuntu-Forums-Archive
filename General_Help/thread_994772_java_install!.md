---
title: "java install! ?"
date: 2008-11-27
forum: General Help
---

### Post by tonyuk123 on 2008-11-27
Hi, 
I'm new to Linux & Ubuntu,
Although i'm fairly computer savvy.
I have installed the system and it is working well so far.
I have been trying to install Java as many websites use it.
I have downloaded a .bin file for it.
The install instructions say, open Terminal, which i do.
Type 'SU' which i can do
Then it says 'Password'
at this point i am unable to type anything except enter/return.
I cannot get any characters to enter the password.
I am logged into the system as the main administrator that you set at install, i assume this is correct.
it's not as if it doesn't like the password, it just seems to disabled the keys except return/enter !
help please

PS after install, i did do the updates (all 113 of them)

Tony
:confused:

---

### Post by alwayshere on 2008-11-27
put below in terminal 

 sudo apt-get install sun-java6-jre

push enter 

then put 

 sudo apt-get update

push enter

---

### Post by pedro_orange on 2008-11-27
su switches you to the super user.
When you type in su and hit enter, you'll be prompted for a password. Unlike Windows no *'s come up when you hit a key - so don't worry about that. Type in your password and hit Enter. It should recognise it.

You may also want to consider not switching to su completely. It may be easier for you to use sudo (super user do):

```
sudo command-i-execute-as-su
```

Side note: If you've just installed Ubuntu and want to have the JRE installed, along with mp3 and video codecs, plus flash you may find it easier to install the package "ubuntu-restricted-extras"

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tonyuk123 on 2008-11-28
Thanks for your help, should have just kept typing password, but kind of off putting when it seems to be doing nothing!
Anyway, i did the second suggestion as i guess i could need the MP3 and video codecs later so used 
'sudo apt-get install ubuntu-restricted-extras'
all seemed to work ok, did lots of installing, and gave a copyright software agreement thingy at the end, so i assume it is installed.
When on the internet it still doesn't run Java.
I have looked the instructions for enabling it in your browser (which is firefox) but the instructions don't relate to the browser !
the option it says to click on doesn't exist in the menu!
Tony
:confused:

---

### Post by tonyuk123 on 2008-11-28
ok, well i'm at work on a windows machine right now, tried to find the instructions i got at home.
instead i found these, is this what i should be trying?
it is completely different to what i had come up at home????

[I]If Firefox is installed at this directory:
/usr/lib/firefox-1.4/ 
And if the JRE is installed at this directory:
/usr/java/jre1.6.0 
Then type at the terminal to go to the browser plug-in directory:
cd /usr/lib/firefox-1.4/plugins 
Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
ln -s /usr/java/jre1.6.0/plugin/i386/ns7
/libjavaplugin_oji.so 

In the command line above, use ns7-gcc29 if Firefox was compiled with gcc2.9.

If you install Firefox 1.5 or later, you can enable the Java Console menu item in the Tools menu. Change directories to the Firefox extensions directory, then unzip ffjcext.zip there.

cd /usr/lib/firefox-1.4/extensions 
unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip


Start the Firefox browser, or restart it if it is already up. 

In Firefox, type about:plugins in the Location bar to confirm that the Java Plugin is loaded. If the version is Firefox 1.5 or later, click the Tools menu to confirm that Java Console is there[/I]

The 'home' verson seemed much simpler, although they don't relate to the same version of browser (which is the firefox installed from the downloaded install of Ubuntu 8.10)

---

### Post by pedro_orange on 2008-11-28
Yeh that looks good.

All you need to do is replace your version with the version in the tutorial. It's the same principle. 
Just take your time. And it should be fine.

---

### Post by tonyuk123 on 2008-11-28
ok, none of this worked
i resorted to installing 8.04 instead.
But exact same problems.
How the hell do you get java to work !!!!
at this rate i'm back to windows

Everything i do in terminal now gets this error
 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

even after a reboot 
seems 8.10 was better !

---

### Post by taurus on 2008-11-28
If you have synaptic, add/remove, or update-manager running, close it down first.  Then from a terminal, run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by tonyuk123 on 2008-11-28
> **taurus said:**
> If you have synaptic, add/remove, or update-manager running, close it down first.  Then from a terminal, run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

did the first command sudo apt-get update and it did this froma fresh boot
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

how do i get it to 'LOCK'?

another problem is i can't do updates in update manager even though it says there are some, it says something is using the 'Unable to get exclusive lock' etc.

---

### Post by taurus on 2008-11-28
Post the output of this command from a terminal to see if you have adept running in the background.

```
ps -A
```

---

### Post by tonyuk123 on 2008-11-28
it says 

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kacpid
   45 ?        00:00:00 kacpi_notify
  123 ?        00:00:00 kseriod
  154 ?        00:00:00 pdflush
  155 ?        00:00:00 pdflush
  156 ?        00:00:00 kswapd0
  197 ?        00:00:00 aio/0
 1479 ?        00:00:00 ksuspend_usbd
 1485 ?        00:00:00 khubd
 1504 ?        00:00:00 ata/0
 1508 ?        00:00:00 ata_aux
 1648 ?        00:00:00 scsi_eh_0
 1650 ?        00:00:00 scsi_eh_1
 2339 ?        00:00:00 scsi_eh_2
 2341 ?        00:00:00 usb-storage
 2579 ?        00:00:00 kjournald
 2783 ?        00:00:01 udevd
 3173 ?        00:00:00 kpsmoused
 3215 ?        00:00:00 kgameportd
 4557 tty4     00:00:00 getty
 4558 tty5     00:00:00 getty
 4562 tty2     00:00:00 getty
 4563 tty3     00:00:00 getty
 4568 tty6     00:00:00 getty
 4733 ?        00:00:00 acpid
 4765 ?        00:00:00 kondemand/0
 4846 ?        00:00:00 syslogd
 4905 ?        00:00:00 dd
 4907 ?        00:00:00 klogd
 4929 ?        00:00:00 dbus-daemon
 4945 ?        00:00:00 NetworkManager
 4959 ?        00:00:00 NetworkManagerD
 4972 ?        00:00:00 system-tools-ba
 4992 ?        00:00:00 avahi-daemon
 4993 ?        00:00:00 avahi-daemon
 5031 ?        00:00:00 cupsd
 5105 ?        00:00:00 dhcdbd
 5124 ?        00:00:00 hald
 5127 ?        00:00:00 console-kit-dae
 5189 ?        00:00:00 hald-runner
 5209 ?        00:00:00 hald-addon-acpi
 5227 ?        00:00:00 hald-addon-inpu
 5237 ?        00:00:00 hald-addon-stor
 5246 ?        00:00:00 hald-addon-stor
 5249 ?        00:00:00 hald-addon-stor
 5293 ?        00:00:00 hcid
 5301 ?        00:00:00 btaddconn
 5302 ?        00:00:00 btdelconn
 5308 ?        00:00:00 bluetoothd-serv
 5315 ?        00:00:00 bluetoothd-serv
 5320 ?        00:00:00 krfcommd
 5357 ?        00:00:00 dhclient
 5367 ?        00:00:00 gdm
 5370 ?        00:00:00 gdm
 5374 tty7     00:02:03 Xorg
 5438 ?        00:00:00 atd
 5457 ?        00:00:00 cron
 5559 tty1     00:00:00 getty
 5605 ?        00:00:02 gconfd-2
 5607 ?        00:00:00 gnome-keyring-d
 5608 ?        00:00:00 x-session-manag
 5661 ?        00:00:00 seahorse-agent
 5665 ?        00:00:00 dbus-daemon
 5666 ?        00:00:02 gnome-settings-
 5670 ?        00:00:00 pulseaudio
 5677 ?        00:00:00 gconf-helper
 5690 ?        00:00:00 compiz
 5692 ?        00:00:09 gnome-panel
 5693 ?        00:00:03 nautilus
 5697 ?        00:00:04 gnome-screensav
 5709 ?        00:00:00 bonobo-activati
 5722 ?        00:00:00 gvfsd
 5733 ?        00:00:00 gvfs-fuse-daemo
 5761 ?        00:00:57 compiz.real
 5762 ?        00:00:00 bluetooth-apple
 5765 ?        00:00:00 update-notifier
 5768 ?        00:00:00 tracker-applet
 5769 ?        00:00:00 evolution-alarm
 5773 ?        00:00:00 trackerd
 5778 ?        00:00:02 nm-applet
 5779 ?        00:00:00 python
 5781 ?        00:00:00 gnome-volume-ma
 5784 ?        00:00:00 gvfsd-burn
 5785 ?        00:00:00 gnome-power-man
 5788 ?        00:00:00 trashapplet
 5794 ?        00:00:00 gvfsd-trash
 5810 ?        00:00:00 sh
 5811 ?        00:00:00 compiz-decorato
 5813 ?        00:00:07 gtk-window-deco
 5816 ?        00:00:00 mixer_applet2
 5820 ?        00:00:00 fast-user-switc
 5884 ?        00:00:02 apt-get
 5907 pts/1    00:00:00 dpkg
 5914 pts/1    00:00:01 frontend
 5921 pts/1    00:00:00 preinst
 5923 pts/1    00:00:00 whiptail
 5925 ?        00:04:35 firefox
 6173 ?        00:00:02 gnome-terminal
 6175 ?        00:00:00 gnome-pty-helpe
 6176 pts/2    00:00:00 bash
 6210 ?        00:00:34 update-manager
 6243 pts/2    00:00:00 ps


i am lost now!
Thanks for trying to help me

---

### Post by taurus on 2008-11-28
Do you currently have update-manager window open because there is one running?  You also have apt-get running too.  Maybe your machine is checking for update (running in the background) so if you give it a few minutes, it should be finished and closed itself down.

Otherwise, you can kill those processes with

```
sudo kill -9 5884
sudo kill -9 6210
```
Now, see if you can install Sun's java from the repos.

---

### Post by tonyuk123 on 2008-11-28
ok,
did that, and now it runs hte other bits
although with some serious warnings!
and java still  not working
same as i had on version 8.10
was advised it might be better to try 8.04 but it seems the same, all be it with lots more errors
if i go to the sun site, i can download a .bin file, but what should i do with it?

---

### Post by tonyuk123 on 2008-11-29
hi, thanks for all the help but so far no joy!

here is what i've done so far.....

I have installed ubuntu 8.04 after trying 8.10.
I had exact same problem on both version, that is i can't get java to work in the firefox browser.
I have tried many things people have said and so far all i get is on 'SYSTEM', 'PREFERENCES'the options of 'sun java 6 plugin control panel' and 'sun java 6 policy tool'
but in the firefox browser it still doesn't work.
the instructions on sun website for enabling it in browser do not relate to what i have, as the options they say aren't there.

Firefox has been upgraded to 3.0.4
java is 6 (i assume)
Ubuntu is 8.04 (with approx 179 upgrades after install)

if i goto the sun java 6 plugin control under java tab it says product JRE version 1.6.0_7    location /usr/lib/jvm/java-6-sun-1.6.0.07/jre

but if i goto a website that wants java it says java doesn't seem to be installed on your system.

how do i get further, as many websites now use java!

Tony

---

### Post by m_l17 on 2008-11-29
> **taurus said:**
> If you have synaptic, add/remove, or update-manager running, close it down first.  Then from a terminal, run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

Try the above again. If you get an output from the terminal telling you that they are installed. Java should be working already.

---

### Post by tonyuk123 on 2008-11-29
great thanks,
that worked, seems it didn't have all the files ! not sure why, some were updated, some were not needed any more and others installed for first time.
It's now working great 
not sure how to thankyou so you gain thanks points!
Tony

---

### Post by linux_tech on 2008-11-29
After a new install to Intrepid 8.1, to get all multimedia, web video working, including installing java-
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

The java install is not quiet, so when you get to the java install part, you will need to use tab key and enter key install java.

---

### Post by m_l17 on 2008-11-30
> **tonyuk123 said:**
> great thanks,
that worked, seems it didn't have all the files ! not sure why, some were updated, some were not needed any more and others installed for first time.
It's now working great 
not sure how to thankyou so you gain thanks points!
Tony

Glad it's working for you :) Read this to learn how to thank users:

[http://ubuntuforums.org/showthread.php?t=702596]("http://ubuntuforums.org/showthread.php?t=702596")

---

