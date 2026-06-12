---
title: "Sound stopped working in Karmic"
date: 2010-01-16
forum: Hardware
---

### Post by ericbe on 2010-01-16
I have a Asus M3N78-VM motherboard.  After I do an initial install of Ubuntu Karmic 9.10, everything works well.

When I choose to perform all system updates, my sound stops working and I can't get it back.

Booting with the live CD confirms that the sound card still works.

Help.

EB

---

### Post by n0dix on 2010-01-16
You check the volume control?? The alsamixer?

---

### Post by ericbe on 2010-01-16
Yeah volume levels are all high and alsamixer shows all volume levels high too.

---

### Post by ericbe on 2010-01-16
Below is a list of the packages that get installed when I updated using Update Manager.  One of them breaks my audio.

If anyone can tell me what to check.  It would be appreciated.

Upgraded the following packages:

adduser (3.110ubuntu6) to 3.110ubuntu7
app-install-data-partner (12.9.10) to 12.9.10.2
avahi-autoipd (0.6.25-1ubuntu5) to 0.6.25-1ubuntu5.1
avahi-daemon (0.6.25-1ubuntu5) to 0.6.25-1ubuntu5.1
bind9-host (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
cups (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
cups-bsd (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
cups-client (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
cups-common (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
dnsutils (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
empathy (2.28.1-1ubuntu1) to 2.28.1.1-0ubuntu1
empathy-doc (2.28.1-1ubuntu1) to 2.28.1.1-0ubuntu1
evince (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.2
evolution (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
evolution-common (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
evolution-documentation-en (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
evolution-indicator (0.2.4-0ubuntu2) to 0.2.4-0ubuntu3.1
evolution-plugins (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
f-spot (0.6.1.3-2) to 0.6.1.5-0ubuntu1
firefox (3.5.3+build1+nobinonly-0ubuntu6) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-3.5 (3.5.3+build1+nobinonly-0ubuntu6) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-3.5-branding (3.5.3+build1+nobinonly-0ubuntu6) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-3.5-gnome-support (3.5.3+build1+nobinonly-0ubuntu6) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-gnome-support (3.5.3+build1+nobinonly-0ubuntu6) to 3.5.7+nobinonly-0ubuntu0.9.10.1
fuse-utils (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.1
gcalctool (5.28.1-0ubuntu1) to 5.28.2-0ubuntu1
gdm (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2.1
gimp (2.6.7-1ubuntu1) to 2.6.7-1ubuntu1.1
gimp-data (2.6.7-1ubuntu1) to 2.6.7-1ubuntu1.1
gnome-about (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
gnome-desktop-data (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
gnome-screensaver (2.28.0-0ubuntu3) to 2.28.0-0ubuntu3.3
gnome-settings-daemon (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
grub-common (1.97~beta4-1ubuntu3) to 1.97~beta4-1ubuntu4.1
grub-pc (1.97~beta4-1ubuntu3) to 1.97~beta4-1ubuntu4.1
gtk2-engines (1:2.18.4-1ubuntu1) to 1:2.18.4-1ubuntu2
gtk2-engines-murrine (0.90.3-1ubuntu1) to 0.90.3-1ubuntu2
gtk2-engines-pixbuf (2.18.3-1) to 2.18.3-1ubuntu2.1
ibus (1.2.0.20090927-2ubuntu1) to 1.2.0.20090927-2ubuntu2
initscripts (2.87dsf-4ubuntu11) to 2.87dsf-4ubuntu12
jockey-common (0.5.5-0ubuntu2) to 0.5.5-0ubuntu3
jockey-gtk (0.5.5-0ubuntu2) to 0.5.5-0ubuntu3
kerneloops-daemon (0.12+git20090217-1ubuntu4) to 0.12+git20090217-1ubuntu4.1
libbind9-50 (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
libcups2 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupscgi1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsdriver1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsimage2 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsmime1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsppdc1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libdns50 (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
libenchant1c2a (1.5.0-0ubuntu2) to 1.5.0-0ubuntu3
libevdocument1 (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.2
libevview1 (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.2
libfuse2 (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.1
libgail-common (2.18.3-1) to 2.18.3-1ubuntu2.1
libgail18 (2.18.3-1) to 2.18.3-1ubuntu2.1
libgimp2.0 (2.6.7-1ubuntu1) to 2.6.7-1ubuntu1.1
libglib2.0-0 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu1
libglib2.0-data (2.22.2-0ubuntu1) to 2.22.3-0ubuntu1
libgnome-desktop-2-11 (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
libgssapi-krb5-2 (1.7dfsg~beta3-1) to 1.7dfsg~beta3-1ubuntu0.3
libgstreamer-plugins-base0.10-0 (0.10.25-2ubuntu1) to 0.10.25-2ubuntu1.2
libgtk2.0-0 (2.18.3-1) to 2.18.3-1ubuntu2.1
libgtk2.0-bin (2.18.3-1) to 2.18.3-1ubuntu2.1
libgtk2.0-common (2.18.3-1) to 2.18.3-1ubuntu2.1
libgudev-1.0-0 (1:147~-6) to 1:147~-6.1
libhtml-parser-perl (3.61-1) to 3.61-1ubuntu0.1
libibus1 (1.2.0.20090927-2ubuntu1) to 1.2.0.20090927-2ubuntu2
libindicate-gtk1 (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libindicate3 (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libisc50 (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
libisccc50 (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
libisccfg50 (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
libk5crypto3 (1.7dfsg~beta3-1) to 1.7dfsg~beta3-1ubuntu0.3
libkrb5-3 (1.7dfsg~beta3-1) to 1.7dfsg~beta3-1ubuntu0.3
libkrb5support0 (1.7dfsg~beta3-1) to 1.7dfsg~beta3-1ubuntu0.3
liblwres50 (1:9.6.1.dfsg.P1-3) to 1:9.6.1.dfsg.P1-3ubuntu0.2
libnautilus-extension1 (1:2.28.1-0ubuntu1) to 1:2.28.1-0ubuntu3
libpoppler-glib4 (0.12.0-0ubuntu2) to 0.12.0-0ubuntu2.1
libpoppler5 (0.12.0-0ubuntu2) to 0.12.0-0ubuntu2.1
libpq5 (8.4.1-1) to 8.4.2-0ubuntu9.10
libpython2.6 (2.6.4~rc2-0ubuntu1) to 2.6.4-0ubuntu3
libsmbclient (2:3.4.0-3ubuntu5) to 2:3.4.0-3ubuntu5.3
libssl0.9.8 (0.9.8g-16ubuntu3) to 0.9.8g-16ubuntu3.1
libudev0 (147~-6) to 147~-6.1
libwbclient0 (2:3.4.0-3ubuntu5) to 2:3.4.0-3ubuntu5.3
nautilus (1:2.28.1-0ubuntu1) to 1:2.28.1-0ubuntu3
nautilus-data (1:2.28.1-0ubuntu1) to 1:2.28.1-0ubuntu3
ntpdate (1:4.2.4p6+dfsg-1ubuntu5) to 1:4.2.4p6+dfsg-1ubuntu5.1
openssl (0.9.8g-16ubuntu3) to 0.9.8g-16ubuntu3.1
poppler-utils (0.12.0-0ubuntu2) to 0.12.0-0ubuntu2.1
python (2.6.4~rc1-0ubuntu1) to 2.6.4-0ubuntu1
python-apport (1.9.3-0ubuntu4) to 1.9.3-0ubuntu4.2
python-avahi (0.6.25-1ubuntu5) to 0.6.25-1ubuntu5.1
python-ibus (1.2.0.20090927-2ubuntu1) to 1.2.0.20090927-2ubuntu2
python-minimal (2.6.4~rc1-0ubuntu1) to 2.6.4-0ubuntu1
python-problem-report (1.9.3-0ubuntu4) to 1.9.3-0ubuntu4.2
python-ubuntuone-client (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
python2.6 (2.6.4~rc2-0ubuntu1) to 2.6.4-0ubuntu3
python2.6-minimal (2.6.4~rc2-0ubuntu1) to 2.6.4-0ubuntu3
rhythmbox (0.12.5-0ubuntu4) to 0.12.5-0ubuntu5.1
rsyslog (4.2.0-2ubuntu5) to 4.2.0-2ubuntu5.1
samba-common (2:3.4.0-3ubuntu5) to 2:3.4.0-3ubuntu5.3
samba-common-bin (2:3.4.0-3ubuntu5) to 2:3.4.0-3ubuntu5.3
smbclient (2:3.4.0-3ubuntu5) to 2:3.4.0-3ubuntu5.3
sreadahead (1.0-5) to 1:0.90.3-2
system-tools-backends (2.8.2-1) to 2.8.2-1ubuntu1
sysv-rc (2.87dsf-4ubuntu11) to 2.87dsf-4ubuntu12
sysvinit-utils (2.87dsf-4ubuntu11) to 2.87dsf-4ubuntu12
totem (2.28.1-0ubuntu4) to 2.28.2-0ubuntu3
totem-common (2.28.1-0ubuntu4) to 2.28.2-0ubuntu3
totem-mozilla (2.28.1-0ubuntu4) to 2.28.2-0ubuntu3
totem-plugins (2.28.1-0ubuntu4) to 2.28.2-0ubuntu3
transmission-common (1.75-0ubuntu2) to 1.75-0ubuntu2.2
transmission-gtk (1.75-0ubuntu2) to 1.75-0ubuntu2.2
tzdata (2009o-1ubuntu2) to 2009u-0ubuntu0.9.10
ubuntu-xsplash-artwork (0.8.4-0ubuntu1) to 0.8.5-0ubuntu1
ubuntuone-client (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
ubuntuone-client-gnome (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
update-manager (1:0.126.6) to 1:0.126.9
update-manager-core (1:0.126.6) to 1:0.126.9
upstart (0.6.3-10) to 0.6.3-11
x11-common (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xsane (0.996-2ubuntu1) to 0.996-2ubuntu1.1
xsane-common (0.996-2ubuntu1) to 0.996-2ubuntu1.1
xserver-xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-input-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-video-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xsplash (0.8.4-0ubuntu1) to 0.8.5-0ubuntu1
xulrunner-1.9.1 (1.9.1.3+build1+nobinonly-0ubuntu6) to 1.9.1.7+nobinonly-0ubuntu0.9.10.1
xulrunner-1.9.1-gnome-support (1.9.1.3+build1+nobinonly-0ubuntu6) to 1.9.1.7+nobinonly-0ubuntu0.9.10.1

Installed the following packages:
libdns53 (1:9.6.1.dfsg.P1-3ubuntu0.2)
ureadahead (0.90.3-2)

---

### Post by Zomeren on 2010-01-17
I have almost the same symptoms after updating yesterday.
use Ubuntu 9.10 and my setup worked perfectly

now, sound works when playing playing audio CD's or Youtube videos with Firefox 3.5.7 but I do not have any sound when I use streaming audio. in Firefox.
upgraded to firefox 3.5.7 in this latest upgrade.
I also do not see any plugins in use when I try to use streaming audio.

Help would be appreciated.

FranZ

---

### Post by ericbe on 2010-01-18
**Update:** I tried a few things.  First I reformatted and re-installed  Ubuntu 9.10.  Sound worked well after first reboot as was happening in the past.  Then, before I did any other update, I restarted the computer.  After that the sound was dead.  This means that the issue isn't related to any updates. I then decided to install Ubuntu 9.04 to see what the outcome of that would be.  The exact same thing happens.  After the first boot following the install, the sound works great.  After any subsequent reboots, the sound stops working.

Any ideas that could help me troubleshoot or even solve the problem would be greatly appreciated.

---

### Post by pierrem-m on 2010-01-19
I have what may be a related problem. I did an update yesterday and now any audio, either as part of a video file or as a stand alone audio, will only play for 10secs and then silence.

I don't know what the updates were as I don't know how to retrieve this information but if someone can tell me what to do I'm happy to post that information as well. 

Also, if the offending package(s) can be identified can they be rolled back to the previous versions?

Any assistance would be greatly appreciated Folks!

Regards and thanks in anticipation

Pierre

---

