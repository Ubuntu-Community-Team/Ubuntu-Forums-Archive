---
title: "[SOLVED] Get personal files of off HDD using Live CD?"
date: 2008-08-15
forum: General Help
---

### Post by HousieMousie2 on 2008-08-15
Disaster struck!

I was upgrading from Gutsy 7.10 to Hardy... following all directions...  when the install got stuck at "Installing upgrades" "About 16 minutes remaining"  "76%"  "Installing new version of config file /etc/belocs/iso-639.def..."  "Generating locates..."  "en_AU.UTF-8..."

It stayed there for about six hours, then crashed.  Upon restarting, I was not surprised, to discover that my once stable Gutsy had been ruined and that it had no intention of finishing the installation.  Adept would not load in a usable way, I could view it, but not use it.  App fixup (or whatever it was called) was a twelve hour waste of time.

I am, at this point resigned to, trying to use the Live CD of Gutsy to get my personal files off of my hard drive before I do a fresh install of Hardy from CD (which I have yet to make, but soon will.)

Dolphin will not open the hard drive that has/had Gutsy on it already, giving me a "hal-storage-fixed-mount refused uid 999" message.

I only recently began reading the 'Getting to know the shell' web pages... so I am not knowledgeable enough to try to use Konsole to get to my files and move them to my other hard drive.

Can someone walk me through it or point me to a walkthrough?

Thank you for your time!

---

### Post by iaculallad on 2008-08-15
If you could boot from recovery mode, try issuing the commands below:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
startx
```

---

### Post by prshah on 2008-08-15
> **HousieMousie2 said:**
> 
Dolphin will not open the hard drive that has/had Gutsy on it already, giving me a "hal-storage-fixed-mount refused uid 999" message.


In your live CD environment, give the command```
sudo apt-get install pmount
```

Subsequently, you can mount your drive with a simple command like this (note: no sudo)```
pmount /dev/sda1
``` Replace /dev/sda1 with the actual partition device that contains your (old) linux filesystem. The command will mount the old filesystem to the directory in "/media/"  corresponding to the partition device id; so in this case, it will mount to "/media/sda1".

You can normally browse with Dolphin and copy out your files with this; you do not need to use sudo.

---

### Post by HousieMousie2 on 2008-08-15
> **iaculallad said:**
> If you could boot from recovery mode, try issuing the commands below:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
startx
```

Thank you, I will try that now!

---

### Post by HousieMousie2 on 2008-08-16
Okay, reporting back... bad news.

I got to "dpkg --configure -a", in Recovery Mode, and it started to do it's work, but again stopped at the same place... "en_AU.UTF-8..."

This time went it restarted it was unable to boot at all... that is to say that the keyboard was dead and it would not let me choose to boot into Recovery Mode.  When it tried to boot into normal mode, it would give me an error for a half second, then would go to a black screen prompt for log-in... but with a dead keyboard all I could do was beg for it to carry on... of course, it did not.

So... abandoning THAT hard drive, I replaced it with a larger HDD and tried to install from my original Gutsy CD.  Key word, tried.

Adept Updater failed to finish updating, saying that it was probably due to it being unable to download something, but was not more specific than that.

Opening Adept Manager...

It claimed that something else was using Adept Manager and that I could view Adept Manager, but not use it... or try to resolve it.  The button options being, YES, NO, CANCEL.  NO lets you look at Adept, but not use it... obviously of no help to me.  Clicking YES produced a crash of Adept.

I have tried restarting, but the results are the same... here is the KDE Crash Handler Backtrace:

> 
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
---
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1235478320 (LWP 24084)]
(no debugging symbols found)
---
(no debugging symbols found)
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb661c875 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb661e201 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb68276e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb6824f65 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb6824fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb68250ca in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0x0812b916 in ?? ()
#14 0x0812be8a in ?? ()
#15 0x0812bee8 in ?? ()
#16 0x0812c735 in ?? ()
#17 0x0812a22d in ?? ()
#18 0x08114379 in ?? ()
#19 0x080951ed in ?? ()
#20 0x0807378d in ?? ()
#21 0x0807408e in ?? ()
#22 0xb6e6c893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb71f88ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0xb6e8c842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0xb6e94258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb6e03af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb6e0591f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb75c9cd2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6d96209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6df653b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6daad49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb6e1e1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0xb6e1dfde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0xb6e05699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x0806f75e in ?? ()
#36 0xb6608050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0806f401 in ?? ()


Does this need fixing before I try to finish the update and move on to the upgrade or can I get around it with the Konsole?

If I can finish updating Gutsy via the Konsole, what is/are the command(s) to do so?

And just to kill two birds with one post... Again, if I can use the Konsole to bring Gusty up to date, what then are the commands to upgrade to Hardy via the Konsole should Adept Manager still be unusable?

Thank you for your time, and even more for your help!

---

### Post by HousieMousie2 on 2008-08-16
Okay, I think I did it... the update part anyway.

sudo apt-get update

sudo apt-get install

---

