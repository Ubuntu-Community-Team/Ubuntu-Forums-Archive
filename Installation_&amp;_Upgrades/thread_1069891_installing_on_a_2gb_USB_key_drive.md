---
title: "installing on a 2gb USB key drive"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2009-02-14
Should I be able to install and run Xubuntu from a 2gb USB key/thumb drive ?

The hardware requirements for Xubuntu says 1.5gb of open drive space BUT for some reason, I have not (so far) been able to get Xubuntu to install and run from my 2gb USB drive.

Thanks.

---

### Post by Archmage on 2009-02-14
Grab the Xubuntu-Live-CD-ISO, start the usb-creator (install it, if not yet present) and than put it there.

---

### Post by ve4cib on 2009-02-14
The Live USB creator will create a bootable Live disc, which isn't necessarily what you want.  If you want to actually *install* Ubuntu on your stick it is possible (I've done it).  But it's a touch different...

**Step 1**
Download and burn the Ubuntu Alternate Install CD.  I'd suggest using an LTS release to avoid needing to do a dist-upgrade for as long as possible.

**Step 2**
Insert the USB stick you want to install to, put the disc in the drive, and reboot.  Optionally you may turn the computer off and physically disconnect your internal HD as well (suggested if you want to be 110% sure that you won't accidentally reformat the wrong drive).

**Step 3**
When the install CD's main menu comes up press **F4** (Modes).  Select "Install Command-Line System".  (This will install a very, very basic system with no GUI at all; it's about 700MB or so.)

**Step 4**
Reformat your stick and install.  **Make sure you are reformatting the stick and not the internal HD**.  The easiest way to check is to look at the size of the partition.  If it's 2GB (or 4GB, or however big your stick is it's probably right.)

When I did this I used a single 2GB ext3 partition on the stick.  You can save a bit of memory if you use ext2 instead (no journal), but I think the benefits outweight the few MBs the journal uses.

Follow the on-screen installation instructions.  They're pretty basic and intuitive if you've installed Ubuntu before.

**Step 5**
Boot from the stick.  You should get a black-and-white terminal interface.  Log in using your username and password.

It's probably a good idea to update all of the installed packages right now.  Execute:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

NOTE: you'll probably have to use a wired connection for now; wireless cards usually need extra drivers that aren't installed yet.

Then reboot and log back in.

**Step 6**
Time to start installing all those extra packages to make this feel more like a normal computer.  First-up X11 and a window manager.  Because of the tiny amount of memory we have KDE and Gnome are right out.  XFCE *might* work, but it might not.  I'd opt for something like Fluxbox (my favourite), JWM (the default WM for Damn Small Linux), EvilWM, or similar.  Fluxbox and JWM in my experience offer the right balance of customizability and features for a very small footprint.

```
$ sudo apt-get install xorg fluxbox
```

**Step 7**
Make sure that that worked.  This can be skipped, but I find it useful.  First off create your .xinitrc file:

```
$ nano .xinitrc
```

In the file simply type the executable name of your window manager (fluxbox, jwm, etc...):

```
fluxbox
```

Once that's done save the file and exit (ctrl+o to save **o**out, ctrl+x to exit).  Then run:

```
$ startx
```

You should get your graphical environment started up.  Right-click on the desktop and you'll get a menu with commands.  You can open a terminal and play around, making sure things work.

Once you're satisfied that it all works you can exit the WM to drop back to your login shell, or you can keep going from inside the GUI

**Step 8**
Now that we have a graphical environment it's time to install some graphical applications to make life easier.  There are a few obvious things that are nice:

- drivers for wireless cards (if you're using a laptop)
- graphical file manager
- graphical text editor
- web browser
- media player
- GUI for mounting network drives
- system monitors
- whatever other applications you need

The biggest trick here is finding tools that do what you need, but won't break your 2GB limit.  OpenOffice, while nice, is huge.  Abiword and Gnumeric do the word-processing and spreadsheet jobs, but are much smaller.

Wireless drivers you'll need to work out for yourself: assuming you know your hardware you should know what needs installing.  If not you can come back to the forums to ask for help.

Here's a script I wrote that installs my favourite applications and tools for low-memory/USB installations:

```
#!/bin/sh
#
# A basic script that installs essential apps and libs for a very bare-bones installation
# The list if packages to be installed is based on "Thumbuntu," a 2GB bootable USB stick
# With all the packages below installed (plus a few others, plus user data) Thumbuntu uses ~1.4GB
# When idle CPU usage is around 5% on a P4 clocked to 1867MHz
# (less if Conky is configured to update less often)
# Idle RAM usage is about 135MB (with SWAP turned off, an /tmp a 16MB tmpfs partition)
# (though this could probably be lowered by running fewer background processes)
#
#
# BEFORE YOU BEGIN
# add the necessary extra repos...
#
echo "\nWARNING"
echo "This script will install aproximately 1GB worth of packages.  This may take a while...\n"
echo "Before you begin..."
echo "Have you added the required third-party repositories to /etc/apt/sources.lst:\n"
echo deb http://apt.wicd.net hardy extras
echo deb http://volatile.debian.org/debian-volatile etch/volatile main contrib non-free
echo deb http://ppa.launchpad.net/do-core/ubuntu hardy main
echo deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
echo "\nPress Enter to continue or CTRL+C to quit...\n"
read stdin
wget -q http://www.debian.org/volatile/etch-volatile.asc -O- | apt-key add -
apt-get update


#
# desktop environment essentials
# these are the absolute essentials for a desktop system to be usable
#   xorg: duh.
#   fluxbox: my favourite lightweight WM; suggested alternates would be JWM, OpenBox, EvilWM, etc...
#   pcmanfm: lightweight file manager; suggested alternates would be thunar, emelfm, etc...
#   nano: my favourite command-line/terminal text editor (may be included by default)
#   gedit: my favourite text editor; suggested alternates would be xemacs, or just stick with vi/nano
#   aterm: a nicer terminal than the default xterm
#   slim: graphical login manager, lightweight, configurable, etc...
#
apt-get install --assume-yes \
xorg \
fluxbox \
pcmanfm \
nano \
gedit \
aterm \
slim \

#
# utility applications & daemons
# these are handy tools that make admin life easier, but are not strictly essential
#   cpufreqd: allow for dynamic cpu scaling
#   synaptic: graphical file manager; I like it, but it's not essential
#   update-manager: again, useful, but not absolutely essential
#   gufw: gui to configure ufw firewall; makes life easier
#   pyneighborhood: browse and mount network shares
#   clamtk: virus scanner -- kind of nice for system recovery
#   gparted: graphical partition editor; not essential, but handy
#   gksu: very nice for dealing with super-user applications in the fluxbox menu
#   nmap: your basic port-scanner & network mapper
#   conky: desktop system monitor; gkrellm is a good alternate
#   wicd: network-management tool (handles wireless & wired connections, encryption, etc...)
#   linux-sound-base, alsa: basic sound support; OSS, PulseAudio are alternatives
#
apt-get install --assume-yes \
cpufreqd \
synaptic \
update-manager \
gufw \
pyneighborhood \
clamtk \
gparted \
gsku \
nmap \
conky \
wicd \
linux-sound-base \
alsa-base \
alsa-utils \
amixer \

#
# basic user applications
# programs to make the user's life easier; not essential, but suggested
#   vlc: your basic swiss-army-knife media player
#   dillo: lightweight web browser; good for older systems/low-memory systems
#   firefox: your standard web browser.  suggest getting fireftp to let it double as a graphical FTP client
#   w3m: terminal web browser/pager; handy for recovering systems when x crashes
#   imagemagick: very basic image-viewer & library
#   eog: a nicer image-viewer
#   archive-manager: exactly what the name implies: graphical archive manager
#   p7zip-*: support for extra (proprietary) archive types
#
apt-get install --assume-yes \
vlc \
dillo \
firefox \
w3m \
imagemagick \
eog \
archive-manager \
p7zip-full \
p7zip-rar \



#
# luxury applications
# heavier applications that serve niche purposes, but aren't essential for most users
#   audacious: music player, lightweight, but not essential since VLC plays music too
#   abiword*: basic word-processor; make prettier documents than gedit
#   gnumeric*: basic spreadsheet
#   evince: basic PDF viewer
#   osdsh: display information on the screen (audio volume info for example)
#   gnome-do: quickly launch applications with the keyboard
#   xlockmore: lock the screen; lighter than xscreensaver, but not as pretty
#   brasero: basic CD/DVD burner
#   gpe-screenshot: take screenshots
#   gnome-icon-theme: get a basic icon theme for file managers/GTK applications
#
# *if you've got lots of memory openoffice is a good alternate to these smaller stand-alone apps
#
apt-get install --assume-yes \
audacious \
abiword \
gnumeric \
evince \
osdsh \
gnome-do \
xlockmore \
brasero \
gpe-screenshot \
gnome-icon-theme \

#
# Misc Services & Tools
# catch-all for other stuff
#   openssh-server: allow SSH into the machine
#   denyhosts: help prevent brute-force attacks over SSH
#   vsftpd: allow FTP into the machine
#   ntfs-3g: support for mounting/using NTFS partitions
#   aircrack-ng: wireless packet sniffer & tools
#
apt-get install --assume-yes \
openssh-server \
vsftpd \
denyhosts \
ntfs-3g \
aircrack-ng \

#
# get sound working
# just use ALSA, not pulseaudio
#
echo "\n\nFinished Installing Packages\n"
echo "If your sound is not working try:"
echo "\t\$ asoundconf list"
echo "\t\$ asoundconf set-default-card FOO"
echo "\t\t(where FOO i the desired card in the list)"
echo "\t\$ alsa force-reload"
echo "\n\n"
```

I've added in comments for pretty much every application there, justifying why it's there and offering alternatives where appropriate.

My USB installation (which has everything in that script, plus some additional configuration files, plus Broadcom wireless drivers, plus a few special-purpose applications that you likely don't need) uses up about 1.4GB on a 2GB stick.

I found it useful to stick to GTK+ apps, instead of getting some GTK and some Qt apps.  This keeps the size of the dependencies down.

Since you were asking about getting XFCE working I'd suggest you use Thunar instead of PCManFM (since you're probably more familiar with Thunar).

**Step 9**
Configure everything!

To configure your login window (SLIM) consult this website:

- SLIM: [http://slim.berlios.de/manual.php](http://slim.berlios.de/manual.php)

There are downloadable themes there, as well as instructions for making your own.  All the configuration is done with text files.

Fluxbox/JWM also have text-based configuration files.  For Fluxbox everything is in your $HOME/.fluxbox/ directory.  For JWM there's a single XML file called $HOME/.jwmrc

Details and information on configuration for the window managers can be found here:

- Fluxbox: [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
- JWM: [http://joewing.net/programs/jwm/config.shtml](http://joewing.net/programs/jwm/config.shtml)

Conky is a nice way of displaying system information on the desktop.  To edit it you just edit your $HOME/.conkyrc file.  More information is here:

- Conky: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Depending on what all you want to do you may also want to edit your SSH/FTP server settings, make Denyhosts more or less restrictive, etc...  Man pages are good places to start figuring out how to edit those.

To avoid burning out your drive you'll probably also want to make /tmp a temporary file system (tmpfs).  Add this like to /etc/fstab:

```
tmpfs           /tmp            tmpfs   size=16M,mode=0777      0       0
```



Anyway, hopefully that helps.  To answer the question one more time, yes it is possible to install Ubuntu onto a 2GB USB stick.  It's kind of a grab-bag of packages as opposed to a standard installation, but it works.

For more general information you might want to check out the Ubuntu Wiki guide for installing on low-memory systems:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


EDIT:
Instead of bothering with all the Fluxbox installation, etc... you could try installing XFCE directly after finishing the command-line installation.  No guarantees that it'll work, but it might:

```
$ sudo apt-get install xfce4
```

That will install the base XFCE packages, but without a lot of the extras.  I've never tried it myself, but I'd guess that it should work.

---

### Post by wpshooter on 2009-02-14
Good lordy !!! 

Thanks for all for effort on this.

But on the Xubuntu download website under "system requirements" section all it says that 1.5gb of free hard drive space is required.  It does not say anything about having to do a command-line system installation for it to work in the mentioned 1.5gb drive space.

I am just wanting to install the O/S to my USB key not reinvent the wheel.

---

### Post by avtolle on 2009-02-14
Try unetbootin? [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ve4cib on 2009-02-15
How far can you get when you try to do a normal installation?  Does it complain that it has insufficient memory?  Or does it just hang?  Are you using the Live CD installer, or the alternate?

If it's hanging there may be an issue of insufficient RAM available (especially with the Live CD).  If that's the case try using the alternate CD.

If the alternate disc still doesn't work when you try a full installation I think the best way to go would be to install the command-line system and then install XFCE manually.

---

### Post by wpshooter on 2009-02-15
I finally got it to work by using the alternate Xubuntu CD version (also, I WIPED the hard drive of the computer).

BUT, even though it installed fine, as soon as I attempted to download and install the 190 some updates, I ran out of drive space on the USB key.  SO, it appears that for all practical purposes even Xubuntu can not be**_ properly_** installed on a 2gb USB key drive.  You can get the install on there perhaps but once you have it on there, you really can not do anything of any practical purpose with it because you are then out of drive space.

But at least now I know that it will work, I can make the investment in a little larger USB key drive.

Thanks.

---

### Post by ve4cib on 2009-02-15
Out of curiosity, how much memory did the whole Xubuntu installation use?  (i.e. how much memory was still available out of the 2GB?)

---

### Post by wpshooter on 2009-02-15
> **ve4cib said:**
> Out of curiosity, how much memory did the whole Xubuntu installation use?  (i.e. how much memory was still available out of the 2GB?)

After appropriating 1.7gb to the O/S and the small remainder split between /home and swap, there was only a few kb of space left (seems to me it might have been about 300) after I got back to the Xubuntu desktop.  When I tried to download the available updates, it ran out of space.

---

