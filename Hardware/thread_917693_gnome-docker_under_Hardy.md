---
title: "gnome-docker under Hardy?"
date: 2008-09-12
forum: Hardware
---

### Post by posburn on 2008-09-12
Hi!

I have a Thinkpad X60 which works extremely well under Hardy; full table/pen support, etc..  I've recently gone through a distro-hopping phase (SUSE, Mandriva, Mint, Puppy) and landed squarely back at Ubuntu:).

However, I do miss one thing from all those other distros: there is an application that was installed by default in OpenSUSE, gnome-docker, that allowed my to undock and re-dock my laptop with having to power-down.  I would love to get this working under Hardy.  I've searched high and low for a .deb package for gnome-docker with no luck.  I also tried to convert the SUSE rpm w/ alien and received the following error message:

```

warning: gnome-docker-0.1-36.1.i586.rpm: Header V3 DSA signature: NOKEY, key ID 9c800aca
Unpacking of 'gnome-docker-0.1-36.1.i586.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.

```

I've been using Linux for about a year now, but am not experienced enough to know what the above means....

Finally, I tried to compile both gnome-docker and its dependency liblazy from source and received the following errors:

for liblazy:
```

checking for DBUS... configure: error: Package requirements (dbus-1 >= 0.30) were not met:

No package 'dbus-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

for gnome-docker itself:

```

checking for HAL... configure: error: Package requirements (hal >= 0.5.6) were not met:

No package 'hal' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables HAL_CFLAGS
and HAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details

```

Both dbus (though it's not listed as dbus-1) and HAL are installed; I can see them through Synaptic.  Both meet the version requirements.

Has anyone seen this app/ gotten it to work with Hardy?  Any ideas what I'm doing wrong?

Thanks!

---

### Post by posburn on 2008-09-13
things that go *bump* in the night

---

### Post by posburn on 2008-09-13
if there's a bustle in your hedgerow
don't be alarmed, now
it's just a spring clean for the May *bump*

---

### Post by posburn on 2008-09-14
Bueller.....   Bueller.....

---

### Post by NotALinuxExpert on 2008-10-01
Hello posburn,

I have exactly the same problem under Ubuntu 8.10 beta, so there is no hope of this problems being solved by waiting for the next release. Unfortunately I have no idea how libraries and build dependencies are resolved under Linux and Ubuntu, but a solution would be great for me as well.

So please do not lay back, and let's try to find a solution together!

Best Regards,
NotALinuxExpert

---

### Post by NotALinuxExpert on 2008-10-01
Ok, I've invested an hour now, and have two ideas with results.
First of all I concentrated on dbus-1, as I expect to solve the hal dependency in the same way.
I see two different solutions to the problem:
1. Change dependencies -> This turned out to be the correct one, as it is done automatically. You just need to install the dev-Packages
2. Install older versions if packages

/**
 * Following is outdated. Please read next post
**/
1. Change dependency from dbus-1 to dbus, as this seems to be the successor to dbus.
I tried to change this dependency in the configure batch, but had to realize that this is not the right place to do it, as this was only a generated script by "gnu autoconf". In order to go further, it must be clarified where autoconf collects its data from.
2. I tried to install dbus-1 and dbus-1-utils in parallel to dbus from 
[http://packages.ubuntu.com/de/dapper/amd64/dbus-1-utils/download](http://packages.ubuntu.com/de/dapper/amd64/dbus-1-utils/download)
libdbus-1-2 could be installed without problems, but libdbus-1-utils not. The error message was (translated): dbus collides with dbus-1-utils. Do not install dbus-1-utils.

Best Regards,
NotALinuxExpert

---

### Post by NotALinuxExpert on 2008-10-01
Ok, I succeeded to let it run.

If I understood it correctly, it is not necessary to have the certain version of library, it is just necessary to have the *-dev of the actual version of this library being installed.

So run for each library, which is missing (while running ./configure), 
```
sudo apt-get install <name of library>-dev
```, and you are going to be fine.

I struggled a lot with the dbus-package at the end, because no dbus-dev package could be found. So I entered 
```
sudo apt-get install libdbus*
```
what installed a lot of trash, but at least liblazy and gnome-docker were building at the end.

@Posburn: Could you please test this approach, so we could make a small tutorial how to do it? Could you please note the names of the missing libraries and the corresponding package-names, please? Iwas struggling for two hours now, and I paid no attention for the details.

Best Regards,
NotALinuxExpert

---

### Post by posburn on 2008-10-03
Success! Sort of....

So, I did get both liblazy and gnome-docker to compile successfully.  To do so, I needed all of the following packages:

libdbus-1-dev
libhal-dev
libgnomeui-dev
libgtk2.0-dev
libnotify-dev

Thanks so much NotALinuxExpert for pointing me in the right direction on this!

Now for the bad news - gnome-docker, though compiled and now installed, does not actually work.  When I'm docked, I can see the system tray icon confirming this status.  However, when I click on the tray icon and then click "undock", my system freezes completely.  I can't restart X, only REISUB (or a hard reset w/ power switch) works.  Hmmm...  Thoughts?  Does your install work NotALinuxExpert?  :-k

---

### Post by NotALinuxExpert on 2008-10-03
Hey posburn,

does the problem also occur when you push the undock-Button on the dock itself? If not, forget my following proposal.

Indeed, I have a similiar problem: Not all functions I know of openSUSE are working under Ubunutu now. For example the USB of the dock is not activated / deactivated properly under dock / undock. But the system does not hang.

As the code of gnome-docker is not very complex, it should be no problem to comment all codelines which could bring the system to hang (Executig programs, etc.) and to enable one after the other, so you could identify the problem.

I unfortunately get the feeling, that the gnome-docker must be aligned to work under ubuntu properly. As Holger Macht (The developer of gnome-docker) belongs to the openSUSE laptop team, I am sure he will not take care of this, so we must push this forward.

But he might be interested in this thread as soon we get results, so let's go ahead.

I just had a short lock at the code, the important method is in 
gd-dbus.c: 
DBusHandlerResult dbus_filter_function(DBusConnection *connection, DBusMessage *message, void *user_data),
which succesively calls methods from the other files. So this should be a good start to comment some lines in order to identify the reason for the break.

Best Regards,
NotALinuxExpert

---

### Post by posburn on 2008-10-03
Yes, I still get a complete system freeze even when using the hardware button.  I'm at work right now, so I'll have to dig through the code later and let you know what happens.

Thanks again for working with me on this!

---

### Post by posburn on 2008-10-20
NotALInuxExpert,

I'm note sure if you're still checking this thread but....

Sorry I haven't stayed on top of this.  Work has been nuts lately.  I am determined to keep trying, though.  I let you know if I get anywhere.

---

