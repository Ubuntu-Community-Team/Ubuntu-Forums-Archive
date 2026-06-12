---
title: "Why is it still impossible to transfer files from Galaxy Nexus with Ubuntu?"
date: 2014-11-28
forum: Hardware
---

### Post by buisteric on 2014-11-28
Hi,

I tred to plug in my Galaxy Nexus to my USB port to transfer some files, but I am only getting an empty window, no drive mounted, no view of files on the phone. This used to work, I don't know exactly in which version, stopped working and never got back up. A few months ago, I found a workaround that used MTP commands directly, but these commands are just too counter-intuitive and impossible to remember for me. All smartphones except iPhone use MTP, so that needs to be supported. This is bad, UMS is better for file transfer, but there is no UMS smartphones anymore I know of.

Her is what I get from /var/log/syslog about this:

Nov 28 08:29:22 Drake colord: device removed: sysfs-(null)
Nov 28 08:29:22 Drake colord: device removed: sysfs-samsung-Galaxy_Nexus
Nov 28 08:29:25 Drake kernel: [  666.559485] usb 3-3.1: new high-speed USB device number 9 using xhci_hcd
Nov 28 08:29:26 Drake kernel: [  666.648647] usb 3-3.1: New USB device found, idVendor=04e8, idProduct=685c
Nov 28 08:29:26 Drake kernel: [  666.648652] usb 3-3.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Nov 28 08:29:26 Drake kernel: [  666.648655] usb 3-3.1: Product: Galaxy Nexus
Nov 28 08:29:26 Drake kernel: [  666.648657] usb 3-3.1: Manufacturer: samsung
Nov 28 08:29:26 Drake kernel: [  666.648659] usb 3-3.1: SerialNumber: 0A3C2D8E1600F001
Nov 28 08:29:26 Drake colord: Device added: sysfs-samsung-Galaxy_Nexus
Nov 28 08:29:26 Drake dbus[856]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Nov 28 08:29:26 Drake dbus[856]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov 28 08:29:26 Drake kernel: [  666.773991] systemd-hostnamed[4830]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Nov 28 08:29:27 Drake colord: Device added: sysfs-(null)

So device is detected by kernel but again GUI fails to detect it. Could it be because Unity is not working properly. Maybe I should try within GNOME or KDE?

Tried to install nss-myhostname in case this can help. Why do I have to ALWAYS enter my password several times at the sudo prompt?? And nss-myhostname is not available through apt-get. Why do the logs suggest me to install a package not available in Ubuntu's repository?

I am getting more and more such bugs with Ubuntu, like the mouse pointer that cannot be enlarged anymore since 11.10 and Emacs that doesn't support accented characters until 13.10 if I remember well, unless I start it with a comand-line option. So each new version is introducing a new issue which is never solved and I just cannot downgrade because that would force me to reformat and spend countless hours figuring out my settings (mount points, font sizes, installed applications, etc.). I don't have time to rever engineer how everything works to start digging in the source code and solve the bugs myself.

Is it because now Ubuntu targets a different audience, like the cloud or businesses, which don't need to change mouse pointer size, use Emacs or connect an Android device? I read somewhere that main focus switched to Mir, which may explain why bugs are not fixed anymore. But Mir will just break EVERYTHING down, so probably the Mir-based Ubuntu desktop will be unusable for me for many releases, so I will have to wait till 2018 or even longer to get something back up!

Is there another variant of Ubuntu that is in more active development and would address these issues, or should I forget about this, remove my partition and use a virtual machine instead?

Thanks for any help.

---

### Post by Tadaen_Sylvermane on 2014-11-28
I know this doesn't help but I gave up on wired with my Google Nexus 5 and 7 with my laptop. In my case with Kubuntu it recognizes it, and is visible in the file manager. But it errors half the time when trying to actually browse to it. I finally just set up a samba share on my laptop and do it over wifi. Not the best solution, but it works.

> [COLOR=#000000]I am getting more and more such bugs with Ubuntu, like the mouse pointer that cannot be enlarged anymore since 11.10 and Emacs that doesn't support accented characters until 13.10 if I remember well, unless I start it with a comand-line option. So each new version is introducing a new issue which is never solved and I just cannot downgrade because that would force me to reformat and spend countless hours figuring out my settings (mount points, font sizes, installed applications, etc.). I don't have time to rever engineer how everything works to start digging in the source code and solve the bugs myself.[/COLOR]

This is a Unity / Canonical issue. They sell support like Red Hat. They won't work on, or bother maintaining features that the majority don't use. They go where the money is. Can't speak to Emacs as that is an Emacs issue, not Ubuntu.

My suggestion for the GUI issues is switch to KDE. You have every possible option for customization you can imagine all at the click of a mouse. I find it far more efficient than Unity as well but everyone is different. KDE is not built by a corporation who is out to make the fastest buck. It is built by users, for users.

*SIDE NOTE* KDE also isn't a data miner near as I can tell either. Always a plus.

---

### Post by buisteric on 2014-11-29
Thanks. That's probably what I will have to do for my Android phone. It just stopped connecting, even in Windows, and all Google search yields suggestions about checking drivers, swapping cable, reinstalling everything, trying on different computers, etc.
I tried KDE a while ago but got fed up because there was no way to navigate into the start menu with the keyboard. It is just too inefficient for me to have to use the mouse simply to start a program. Also tried GNOME3, but the hot corners are causing me difficulties and cannot be disabled unless I apply distro and/or version specific hacks to Javascript files.

---

### Post by buzzingrobot on 2014-11-29
> **Tadaen_Sylvermane said:**
>  They won't work on, or bother maintaining features that the majority don't use. They go where the money...

Products that intend to please the most people will naturally devote resources to doing what they think pleases the most people, whatever their motivation. 

 > KDE is not built by a corporation who is out to make the fastest buck. It is built by users, for users.


KDE is built by developers and designers. Linux software is not 'built by users'.  Users can't code.  If they can, and do, then they're developers.

---

### Post by mikewhatever on 2014-11-29
I guess it is the OEM (Samsung) problem/design, whatever you like to call it, as with GL Nexus (and others) you get easy access.

> **Tadaen_Sylvermane said:**
> ...
This is a Unity / Canonical issue. They sell support like Red Hat. They won't work on, or bother maintaining features that the majority don't use. They go where the money is. Can't speak to Emacs as that is an Emacs issue, not Ubuntu.
That comparison is streached, to put it mildly. Canonical gives us free distros to begin with. Can you use RHEL without buying support? A word of thank you would be in order, rather then an accussation.

---

### Post by carlwsnyder on 2014-11-29
Have you tried loading **mtp-tools** package?

---

### Post by Tadaen_Sylvermane on 2014-11-29
> [COLOR=#000000]That comparison is streached, to put it mildly. Canonical gives us free distros to begin with. Can you use RHEL without buying support? A word of thank you would be in order, rather then an accussation.[/COLOR]

Its not an accusation, its a fact. The community of users that use Ubuntu outside of support subs are essentially a giant testing facility for gathering bug reports. I am thankful for their doing what they do but in the end the goal is to sell support and that means focusing on what matters most to the people who pay. Not to every little thing that 5 people in the world want. (clear exaggeration)

It's simple business sense. To think anything else is delusional.
> 
[COLOR=#000000]KDE is built by developers and designers. Linux software is not 'built by users'. Users can't code. If they can, and do, then they're developers.[/COLOR]

This is nothing more than trying to start an arguement.  You don't make money coding open source software unless you are one of the few who gets sponsored. People do it because they love it and use it, not because it makes them rich. You imply a disparity where none exists. Do you stop being a user when you learn to code and contribute to the overall ecosystem?

---

### Post by buzzingrobot on 2014-11-29
You need an RH subscription to get an RH binary image to install and to get access to binary updates. Other types of support depend on what kind of subscription you buy. 

Red Hat's source is freely available and can be acquired and built by anyone who wants to do that. It's fully open source and RH is one of the strongest corporate supporter/advocate of open source.

Nothing in FOSS licensing requires a vendor to make binaries available at no cost. Nothing requires that anyone provide support at no cost. Many Linux users no doubt think the purpose of FOSS is to make software they can use without paying for, but that's not the case.

---

### Post by Hakunka-Matata on 2014-11-29
[[COLOR=#000000]buisteric[/COLOR]]("http://ubuntuforums.org/member.php?u=1842829")[COLOR=#000000] :  It's entirely possible that the usb connector on your nexus is broken, I've broken two now, one on a Samsung galaxy S phone, and also just broke the connector on my Samsung Galaxy SII phone.  The usb connector can fail by either not charging, or not connecting to a computer.  There are also settings for PTP vs. MTP style usb protocols.  Your device may charge via usb ok, but not connect to a computer for file transfers, or both, or either.  I've seen it all ways.  Solution: replace usb connector on Tablet/phone/???  Try wiggling the cable while connected, that might reveal a bad (intermittent) connection.  Also simply Searching on "Samsung galaxy nexus 5 usb connector problems" turns up a load of threads.  [/COLOR]http://forums.androidcentral.com/google-nexus-7-tablet-2012/362325-nexus-7-not-recognized-computer-2.html
Good Luck, there are more and more private business repair shops that replace usb connectors.

---

### Post by coldraven on 2014-11-30
You could install SSHDroid on your Nexus, it's free. 
You can then use Nautilus to SSH into the phone via wifi and grab the files, the downside is that it is a bit slow.
In Nautilus select File>Connect to Server and put in the IP address that SSHDroid displays
[https://play.google.com/store/apps/details?id=berserker.android.apps.sshdroid&hl=en](https://play.google.com/store/apps/details?id=berserker.android.apps.sshdroid&hl=en)

---

### Post by SeijiSensei on 2014-11-30
I recommend using Acrosync, an rsync client for Android.  It has the best download performance over wifi that I could find, certainly better than using something like AndSMB to communicate with Samba shares.

---

### Post by Hakunka-Matata on 2014-11-30
MTP vs. PTP: for Android/Settings/Storage/Settings/USB computer connection:  important and **NEW**.  Check out this link: [http://www.howtogeek.com/192732/android-usb-connections-explained-mtp-ptp-and-usb-mass-storage/](http://www.howtogeek.com/192732/android-usb-connections-explained-mtp-ptp-and-usb-mass-storage/)

I thought my usb port was broken, and it is, but only the battery charging portion:  File transfer works just fine since I checked the "Storage" settings.  Things have changed as the url above explains.  Cyanogenmod, which is my Android OS, puts out Nightly updates, and one of the recent Nightlies changed this protocol.  I have no problem now connecting to the Ubuntu 14.04_64 Desktop OS.

@ SeijiSensei: Your suggestion about Acrosync is appreciated, Great App.

---

### Post by mikewhatever on 2014-12-01
> **Tadaen_Sylvermane said:**
> Its not an accusation, its a fact. The community of users that use Ubuntu outside of support subs are essentially a giant testing facility for gathering bug reports. I am thankful for their doing what they do but in the end the goal is to sell support and that means focusing on what matters most to the people who pay. Not to every little thing that 5 people in the world want. (clear exaggeration)

It's simple business sense. To think anything else is delusional.
...
The fact is, the problem at hand has nothing to do with Canonical or Unity. I wouldn't say your claims are delusional, just incorrect.


> **buzzingrobot said:**
> You need an RH subscription to get an RH binary image to install and to get access to binary updates. Other types of support depend on what kind of subscription you buy. 

Red Hat's source is freely available and can be acquired and built by anyone who wants to do that. It's fully open source and RH is one of the strongest corporate supporter/advocate of open source.

Nothing in FOSS licensing requires a vendor to make binaries available at no cost. Nothing requires that anyone provide support at no cost. Many Linux users no doubt think the purpose of FOSS is to make software they can use without paying for, but that's not the case.
Another thread, more general suff that everyone knows. Déjà vu!

---

### Post by gordintoronto on 2014-12-02
Install Airdroid on the phone.

---

