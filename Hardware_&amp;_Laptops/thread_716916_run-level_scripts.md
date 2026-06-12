---
title: "run-level scripts??"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by mjrwingnut on 2008-03-06
I have a HP Pavilion dv8000. I noticed since I upgraded to 7.10 it takes a long time to load up. What services/scripts I can turn off to increase performance.

---

### Post by insineratehymn on 2008-03-06
That all depends on what you like to use.
Do you use Bluetooth?
Do you use your desktop?
Do you use mysql?

Or something like that.

Anyway, Ubuntu loads up into Run Level 2 by default, so you can either change it to load to the customizable one (run level 4) or you can modify run level 2.

If you look at /etc/rc2.d you will see something like this:
```
README                       S19mysql              S24dhcdbd
S05vbesave                   S20apmd               S89anacron
S10acpid                     S20apport             S89atd
S10powernowd.early           S20hddtemp            S89cron
S10sysklogd                  S20hotkey-setup       S91apache2
S10xserver-xorg-input-wacom  S20makedev            S98usplash
S11klogd                     S20nfs-common         S99acpi-support
S12dbus                      S20nfs-kernel-server  S99laptop-mode
S12hal                       S20nvidia-kernel      S99rc.local
S16ssh                       S20powernowd          S99rmnologin
S17mysql-ndb-mgm             S20rsync              S99stop-readahead
S17portmap                   S20samba              S99webmin
S18mysql-ndb                 S22consolekit         X25bluetooth
S19cupsys                    S24avahi-daemon       X30gdm

```

Hopefully the fomatting didn't kill that.

Anyway, you see some that begin with an S, some that begin with an X, and the README.
I suggest reading the README first and foremost. The 'S' means "do this at startup". The 'X' means "Ignore this".

If you read the README you will see that it is supposed to be a K, but whateva. I do what I want.

So for you to shut off bluetooth, you would do this:

sudo mv S25bluetooth K25bluetooth

then to test:

sudo reboot

And if you pay attention during startup, and you did all of your homework, and finished your vegetables you will see that bluetooth no longer starts up during the initial boot sequence.

Oh, to answer your initial question, copy the contents of /etc/rc2.d and we'll help you to figure out what you can live without.

---

### Post by mjrwingnut on 2008-03-06
I do use my desktop and bluetooth. I disable some of the modem in /etc/rc2.d  I got that from reading a book and it discribed some of the services.  

what is mysql??? I don't know what that is.

I was just wondering if there was some way to find out what each of those services are and what they did.

Thanks again for the help

-MjrWingnut

---

### Post by insineratehymn on 2008-03-06
Type this into your terminal:

ls /etc/rc2.d

Paste the results and we'll git 'er done.

---

### Post by mjrwingnut on 2008-03-08
K01usplash
S19cupsys
S25bluetooth
README
S20apmd
S89anacron
S05vbesave
S20apport
S89atd
S10acpid
S20clamav-freshclam
S89cron
S10powernowd.early
S20hotkey-setup
S90binfmt-support
S10sysklogd
S20kde-guidance
S99acpi-support
S10xserver-xorg-input-wacom  
S20makedev       
S99laptop-mode
S11klogd      
S20nvidia-kernel           
S99rc.local
S12dbus    
S20powernowd       
S99rmnologin
S12hal    
S20rsync              
S99stop-readahead
S12sl-modem-daemon    
S24avahi-daemon
S13kdm     
S24dhcdbd

Ok here is what I have..

---

### Post by insineratehymn on 2008-03-08
Ok...

So the only thing you are shutting off is usplash (By the K).

Is it a laptop?

If not, change S99laptop-mode to K99laptop-mode

Do you use bluetooth?

If not, change S25bluetooth to K25bluetooth

Is there a printer hooked up to it?

If not, change S19cupsys to K19cupsys

I think (by looking at this) that you use KDE, right?

If you do **not** use KDE, change S20kde-guidance to K20kde-guidance
if you do **not** use KDE, change S13kdm to K13kdm

Ok... I think that is enough for one shot.Try those out, reboot and see if it speeds it up at all.

Oh! Edit:

When you post the directory listing, put it in one of those code brackets (its maked by a # in the menu) and it will format it all pretty like.

---

