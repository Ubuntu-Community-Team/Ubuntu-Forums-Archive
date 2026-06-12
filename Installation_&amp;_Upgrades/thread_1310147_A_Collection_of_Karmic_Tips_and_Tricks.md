---
title: "A Collection of Karmic Tips and Tricks"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by IgnorantGuru on 2009-11-01
I thought I'd share some of the problems and subsequent workarounds/tips I found while working with karmic.  I originally installed kubuntu alpha3, which actually gave me fewer problems than the final release, due to some last minute changes they made, particularly with upstart.  But overall karmic is running well for me, and has been for months.

Most of this applies to Ubuntu in general.  A few sections are Kubuntu only.

[b][color=red]Update:[/color] For an updated version of some of the scripts below,
visit my blog at [http://igurublog.wordpress.com/](http://igurublog.wordpress.com/)[/b]

**Table Of Contents**: (most are automated scripts)
USB STICK INSTALL
CREATE ROOT USER
ROOT USER SETTINGS
INSTALL SUN JAVA 64 BIT
INSTALL GOOGLE EARTH
DISABLE SSH-AGENT
DISABLE OTHER AGENTS
DISABLE GPG-AGENT IN GPG
DISABLE KDM AUTOSTART
GRUB2 MODS
OPENOFFICE COLOR FIX
SSD CHANGES
INSTALL TOR
DISABLE NEPOMUK, SOPRANO, AND AKONADI
BROTHER PRINTER DRIVER
SCANPIC SCRIPT
RESIZE AND EMAIL PIC
SETUP VNC4SERVER
DISABLE USB (WEBCAM) AUDIO

I always do a fresh install.  I have been building a post-install script which does most of the work of 'upgrading'.  I do a fresh install, then run my script which installs additional software, makes assorted changes and fixes, and copies config files from my old system so I don't have to setup everything from scratch.  This has really worked well - I highly recommend this method.  One nice thing about linux is that lots of things can be done from the command line.  And once you can do something from the command line, you can paste those commands into a script.  Many of the scripts below are actually excerpts from my post-install script.  If you string them together or have a master script that runs these scripts in series, you can easily build your own post-install script.  I used to keep notes on all my post-install changes, but I found myself doing the same thing over and over, so now I just put my notes in script form.  (Tip:  If you maintain more than one system that has different setup requirements, you can use the $HOSTNAME environment variable to determine which system the script is running on.)

In case you are a beginner, scripts are simply text files, so you can paste any scripts below into a text editor, save them, and run them with "bash scriptname".  With some scripts you need to run them with "sudo bash scriptname" (which gives the script admin priviledges - use with care).

You probably won't want to do all of these modifications as is, but you may want some of them as is, and you may want to modify others for your purposes.

**WARNING:** It is up to you to research these issues to determine if the modification is appropriate for your uses.  Some of these changes are for advanced users only, so if you don't understand it reasonably well, don't do it.

I recommend backing up your system first...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

**USB STICK INSTALL**
I have installed kubuntu karmic alpha3, alpha4, and final on two systems.  For one I use the alternate install CD.  The other system will not boot from its CD drive (MB SATA issue), so I use a USB stick install.  Here is how I got that to work...

```

# Download your preferred DESKTOP install image (NOT alternate CD).  I used
#   kubuntu-9.10-desktop-amd64.iso

# install unetbootin - a USB stick image creator
sudo apt-get install unetbootin

# insert stick and find out what the device name is
sudo fdisk -l

# Zero out USB stick MBR (DESTRUCTIVE):
# This step may not be required
# NOTE!  Change "sdx1" below to your USB stick designation
# BE CAREFUL! Make sure you have the right device name
sudo umount /dev/sdx1         # change sdx1
sudo dd if=/dev/zero of=/dev/sdx1 bs=512 count=1  # change sdx1

# Format the USB stick - use the right device name!
# This step may not be required
sudo mkfs.vfat /dev/sdx1  # change sdx1
sync

# Reinsert and mount the USB stick

# run unetbootin
unetbootin

# Select the Diskimage|ISO option and click the
#    "..." button to select the iso file
# Select your USB drive
# Click OK to start

```

**CREATE ROOT**
Below is a script which will create (enable) the root user on K/Ubuntu, if so desired.  Run it with sudo.  First you will be prompted for your existing user password (for sudo), then you will be prompted twice for your new root password.  Note: Ubuntu does not enable the root user for security reasons.  If you are uncertain about this, research the pros and cons of enabling the root user before making this change.

```

#!/bin/bash
echo
echo 'This script will create a root user (must be run with sudo)'
user=`whoami`
if [ "$user" != "root" ]; then
	echo 'createroot: must be run with sudo'
	exit 1
fi
passwd root
test=`grep 'Defaults.*env_reset,rootpw' /etc/sudoers`
if [ "$test" = "" ]; then
	chmod u+w /etc/sudoers
	sed -i 's/^Defaults	env_reset/Defaults	env_reset,rootpw/' /etc/sudoers
	grep '^Defaults' /etc/sudoers
	chmod u-w /etc/sudoers
else
	echo 'createroot: /etc/sudoers already contains ",rootpw" - no change'
fi

```

**ROOT USER SETTINGS**
Whether or not the root user is enabled on your Ubuntu, there will still be root user settings, such as settings for KDE programs you run as root, your package manager, etc.  Here is the portion of my post-install script that copies these settings from my old system to my new system.  (If you use Gnome, you can add in that settings folder as well.)  You must pass the script the location of your old system root folder (/) on the command line.  For example if your old system is mounted on /mnt/sda3:  sudo post-install /mnt/sda3   This folder name should not contain spaces or other weird characters.  Alternatively, you could just copy the entire /root folder, but I like to be minimalist about it in case other things change in /root between releases.

```

#!/bin/bash
# must be run with sudo
if [ "$1" = "" ]; then
	echo 'Usage: post-install SOURCE'
	exit
fi
if [ ! -e "$1/root" ]; then
	echo "Error: invalid source folder $1"
	exit
fi
src="$1"
mkdir -p /root/.synaptic
cp $src/root/.synaptic/synaptic.conf /root/.synaptic
cp -a $src/root/.gnupg /root
cp -a $src/root/.kde /root
cp -a $src/root/.local /root

```

**INSTALL SUN JAVA 64 BIT**
Below is my method for installing the 64 bit version of Sun Java.  I don't know if this is the most efficient method now, but it works for me.

First, visit [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) and download the latest JRE, selecting Linux64 as your OS.  This script is based on using jre-6*-linux-x64.bin

This script will install Java and will enable the plugin in Firefox.  Place this script in the same folder as the java bin file, and run it from that folder with sudo.

```

#!/bin/bash
# must be run with sudo
# Install Java 64 bit using jre-6u*-linux-x64.bin in current folder

if [ -e /usr/lib/jvm/jre* ]; then
	echo 'SKIPPED: already installed'
else
	j64=`ls -1 jre-6u*-linux-x64.bin | sort -r | head -n 1`
	if [ ! -e $j64 ]; then
		echo 'FAILED java64: missing jre-6u*-linux-x64.bin'
	else
		mkdir /usr/lib/jvm
		cp $j64 /usr/lib/jvm/
		cd /usr/lib/jvm/
		chmod a+x $j64
		j64base=`basename $j64`
		./$j64base
		rm /usr/lib/jvm/$j64base
		javaver=`ls -1 /usr/lib/jvm | sort -r | head -n 1`
		if [ "$javaver" != "" ]; then
			ln -sf /usr/lib/jvm/$javaver/lib/amd64/libnpjp2.so /usr/lib64/firefox-addons/plugins/
		fi
	fi
fi

```

References:
[http://ubuntuforums.org/showthread.php?t=1063635&highlight=sun+java+plugin+64+bit](http://ubuntuforums.org/showthread.php?t=1063635&highlight=sun+java+plugin+64+bit)

**INSTALL GOOGLE EARTH**
This script installs Google Earth, running the install script as a user (more safe), yet installing it to /opt/google-earth and then making it owned by root (to prevent mischief).  Run this script as user, and choose to install to /opt/google-earth in the dialog.

```

#!/bin/bash
# run as user, NOT sudo
# Install Google Earth

user=`whoami`
if [ "$user" = "root" ]; then
	echo 'Do not run as root'
	exit
fi

ge=`ls -1 GoogleEarthLinux*.bin | sort -r | head -n 1`
if [ ! -e $ge ]; then
	wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
	ge=`ls -1 GoogleEarthLinux*.bin | sort -r | head -n 1`
	if [ "$ge" = "" ]; then
		echo 'Error: download failed'
		exit
	fi
fi
if [ -e $ge ]; then
	sudo apt-get install ia32-libs    # needed for 64 bit machines
	sudo rm -rf /opt/google-earth
	sudo mkdir /opt/google-earth
	sudo chmod ugo+rwx /opt/google-earth
	echo 'Choose to install to /opt/google-earth'
	bash $ge
	sudo chown -R root:root /opt/google-earth
	sudo chmod -R go-w /opt/google-earth
	if [ ! -e /opt/google-earth/googleearth-bin ]; then
		echo 'FAILED: missing /opt/google-earth/googleearth-bin'
	fi
else
	echo 'Error: Not downloaded'
fi

```


**DISABLE SSH-AGENT**
ssh-agent is setup by default on Ubuntu to make it easier for people who want it, but IMO it introduces potential security issues and is best not used unless you explicitly want it.  If you don't know what it is, you don't need it.  This script will disable it from starting.

```

#!/bin/bash
# disable ssh-agent from auto starting
sudo sed -i 's/^\(use-ssh-agent.*\)/\#\1/' /etc/X11/Xsession.options
sudo sed -i 's/^\(use-agent.*\)/\#\1/' /root/.gnupg/gpg.conf

```

**DISABLE OTHER AGENTS**
There are other agents run by default in Ubuntu which make it easier to automate password entry (pinentry-qt4 and gnupg-agent), but which introduce potential security hazards.  Also, a new kerneloops daemon has been added which automatically reports kernel issues to a maintenance site.  The following command will uninstall these:

```
sudo apt-get purge pinentry-qt4 gnupg-agent kerneloops-daemon
```

**DISABLE GPG-AGENT IN GPG**
This script will disable the message that gpg-agent is not available when running gpg (once gpg-agent has been removed above).  This script should be run by each user on the system, not with sudo.

```

#!/bin/bash
# disable gpg-agent in gpg.conf
user=`whoami`
sed -i 's/^\(use-agent.*\)/\#\1/' /home/$user/.gnupg/gpg.conf

```

**DISABLE KDM AUTOSTART**
This is an obscure change which you probably DON'T want to do.  In some cases it is desirable to have a system boot into a console instead of automatically starting X and KDE.  NOTE:  If you make this change, you will need to login and start KDM manually when your system boots!

In prior versions of Kubuntu, including karmic alpha3, you made this change by removing the kdm startup link in the appropriate /etc/rc#.d runlevel.  However, in karmic final that no longer works due to the use of upstart.  kdm must now be disabled in /etc/init.  Note that this change may not be permanent - you may need to run this command again after some system updates.  If you use Gnome, I think the same general method works for inhibiting gdm autostart.

To prevent X and KDM from starting automatically:
```
sudo mv -f /etc/init/kdm.conf /etc/init/kdm.conf-disabled
```

Once you make the change above, you can start kdm manually after boot by logging in as root (if enabled) or as a user and entering the command:
```
sudo kdm && exit
```

**GRUB2 MODS**
This script makes a few changes to the grub2 boot menu by editing /etc/default/grub and then running update-grub.  Comment out (put a # before) any changes you don't want.  This script must be run with sudo.

```

#!/bin/bash
# must be run with sudo
# grub2 changes

# make a backup copy of /etc/default/grub
if [ ! -e /etc/default/grub-orig ]; then
	cp -a /etc/default/grub /etc/default/grub-orig
fi

# disable recovery entries from appearing on boot menu
test=`grep '^GRUB_DISABLE_LINUX_RECOVERY=true' /etc/default/grub`
if [ "$test" = "" ]; then
	echo 'GRUB_DISABLE_LINUX_RECOVERY=true' >> /etc/default/grub
fi

# change the boot menu timeout to 5 seconds (is 10 by default)
sed -i 's/^GRUB_TIMEOUT=.*/GRUB_TIMEOUT=5/' /etc/default/grub

# don't hide the boot menu timeout counter
sed -i 's/^GRUB_HIDDEN_TIMEOUT_QUIET=.*/GRUB_HIDDEN_TIMEOUT_QUIET=false/' /etc/default/grub

# change splash and quiet to nosplash to observe boot messages
sed -i 's/^GRUB_CMDLINE_LINUX_DEFAULT=.*/GRUB_CMDLINE_LINUX_DEFAULT="nosplash"/' /etc/default/grub

# rebuild the boot menu (update /boot/grub/grub.cfg)
update-grub

```

To undo the above changes use these commands:
```
cp /etc/default/grub-orig /etc/default/grub
update-grub
```

**OPENOFFICE COLOR FIX**
Karmic sets the OpenOffice colors to KDE or Gnome colors.  This is especially a problem will color-coded spreadsheets, because the background colors set in the spreadsheet no longer show.  If you DON'T want OpenOffice to use your desktop colors, this script will make that change.  You may need to run this script again if OO or your desktop is updated.

```

#!/bin/bash
# openoffice color fix
# http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8
test=`grep "export OOO_FORCE_DESKTOP=none" /usr/lib/openoffice/program/soffice`
if [ "$test" = "" ]; then
	sudo sed -i -n '1h;1!H;${;g;s/#!\/bin\/sh\x0A/#!\/bin\/sh\x0Aexport OOO_FORCE_DESKTOP=none\x0A/;p;}' /usr/lib/openoffice/program/soffice;
fi

```


**SSD CHANGES**
If your desktop system has an SSD (solid state drive), there are certain changes that are recommended to minimize the number of writes to the drive.  These changes include changing the kernel dirty page writeback time, changing the commit time in fstab, using a ramdrive for /tmp /var/log and /var/tmp, changing the scheduler for the SSD drive, and using a non-SSD drive for your swap partition.

FYI:  Installing Ubuntu to an SSD drive creates a **remarkable** change in system performance - boot time and program startup times are drastically reduced.  I highly recommend the investment - I have never before seen a single hardware change that affected performance as much as an SSD.  Get a good quality one such as the OCZ Vertex.  I've been using this SSD for over 6 months and it's excellent.  30G is plenty for a few system partitions, then use a regular hard drive for your data.

Note: karmic final introduced a bug which was not present in alpha3.  The mountall command now will not mount a ramdrive to /var/log and /var/tmp in fstab - you get a "waiting for tmpfs" message which interrupts the boot process.  You can read more on this issue here: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431040](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431040)   It currently says there "fix released" but don't believe it - this bug is still present in karmic final.  As a result, it is now necessary to either mount /var to another drive, or mount them after fstab.  I have chosen to mount them after fstab, in part because it makes the system faster, but this solution is imperfect.  Kernel and system logs which are started before rc.local runs may not be visible using this method.  I am using this method and haven't had an issue thus far, but choose whatever solution works best for you.  I am providing this method in case you want to use it.

Also note that all of these changes can be made to a non-SSD system - using a ramdrive may speed up your system somewhat, and can also be used for greater security (the contents of /tmp are gone when the system is shutdown).

The script below will make the above changes EXCEPT for changing the fstab commit time, and EXCEPT for moving your swap partition to another drive.  It is recommended that you add a commit= to each fstab line which mounts your SSD partitions.  For example, this line in /etc/fstab:
```
/dev/sda1  /  ext3  noatime,errors=remount-ro  0  1
```
might become
```
/dev/sda1  /  ext3  noatime,errors=remount-ro,commit=240  0  1
```

The script below does NOT make the above change to fstab - do that manually.  However, this script does add a /tmp ramdrive mount in fstab.  Also, it assumes that only /dev/sda is an SSD drive.  Read the comments in the script to see exactly what changes are being made.  Also note that this script will REPLACE your /etc/rc.local.  If you have customized it, you will want to add your customizations back in after running it.

This script must be run with sudo.

**UPDATE:  Please see the modified versions of these scripts below:**
[http://ubuntuforums.org/showpost.php?p=8232599&postcount=11](http://ubuntuforums.org/showpost.php?p=8232599&postcount=11)

```

#!/bin/bash
# must be run with sudo
# setup changes for SSD

# modify /etc/sysctl.conf to change kernel dirty page writeback time
test=`grep '\# I added to reduce disk activity' /etc/sysctl.conf`
if [ "$test" = "" ]; then
	if [ ! -e /etc/sysctl.conf-orig ]; then
		cp -a /etc/sysctl.conf sysctl.conf-orig
	fi
	echo >> /etc/sysctl.conf
	echo '# I added to reduce disk activity to 240 seconds' >> /etc/sysctl.conf
	echo 'vm.dirty_ratio = 40' >> /etc/sysctl.conf
	echo 'vm.dirty_background_ratio = 1' >> /etc/sysctl.conf
	echo 'vm.dirty_writeback_centisecs = 24000' >> /etc/sysctl.conf
fi

# Note: if you DON'T have a laptop, uncomment the line below
# to prevent changes possibly being undone
#chmod -x /usr/lib/pm-utils/power.d/laptop-mode

# edit fstab to mount ramdrive to /tmp
test=`grep '^tmpfs.*\/tmp.*tmpfs' /etc/fstab`
if [ "$test" = "" ]; then
	if [ ! -e /etc/fstab-orig ]; then
		cp -a /etc/fstab /etc/fstab-orig
	fi
	echo >> /etc/fstab
	echo '# I added to reduce disk activity' >> /etc/fstab
	echo 'tmpfs /tmp tmpfs defaults,noatime,size=1000M,mode=1777 0 0' >> /etc/fstab
	echo '# The following lines are disabled because of the bug in mountall' >> /etc/fstab
	echo '# These may be mounted in /etc/rc.local instead' >> /etc/fstab
	echo '# See https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431040' >> /etc/fstab
	echo '#tmpfs /var/log tmpfs defaults,noatime,size=200M,mode=0755 0 0' >> /etc/fstab
	echo '#tmpfs /var/tmp tmpfs defaults,noatime,size=500M,mode=1777 0 0' >> /etc/fstab
	echo '#tmpfs /var/spool/postfix/public tmpfs defaults,noatime,size=50K,mode=1777 0 0' >> /etc/fstab
fi

# Replace rc.local for SSD changes
if [ ! -e /etc/rc.local-orig ]; then
	cp -a /etc/rc.local /etc/rc.local-orig
fi
cat << EOF > /etc/rc.local
#!/bin/bash
# above must be #!/bin/bash not default /bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# mount ramdrives to /var/log /var/tmp and /var/spool/postfix/public
for dir in "/var/log" "/var/tmp" "/var/spool/postfix/public" ; do
	test=`mount | grep " on $dir "`
	if [ "$test" = "" ]; then
		sz="50K"
		md="1777"
		case "$dir" in
			/var/log )
				sz="200M"
				md="0755"
				;;
			/var/tmp )
				sz="500M"
				md="1777"
				;;
			/var/spool/postfix/public )
				sz="50K"
				md="1777"
				;;
		esac
		mount -t tmpfs -o size=$sz,noatime,mode=$md tmpfs $dir
	fi
done

# recreate default log folders for common apps to prevent hangs on startup
# Note: you may need to add more folders to this list if your programs don't start
for dir in apparmor apt cups dist-upgrade fsck installer news samba unattended-upgrades tor; do
	mkdir -p /var/log/$dir
	chmod go+rwx /var/log/$dir
done

# You may need to change the permissions or ownership on some log folders
# For example (uncomment to activate)
#chown debian-tor:debian-tor /var/log/tor

# Set sda to use deadline scheduler
# Note: if these changes don't seem to take, try pasting them into a root console
#       (or with sudo) manually once then reboot
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch

exit 0

EOF

chmod u+x /etc/rc.local

# If you run postfix, change postfix startup script so that rc.local runs first
# Note: This may need to be repeated if postfix is upgraded
test=`grep 'bash /etc/rc.local' /etc/init.d/postfix`
if [ "$test" = "" ]; then
	sed -i -n '
	1h
	1!H
	$ {
		g
		s/case "$1" in\x0A    start)\x0A/case "$1" in\x0A    start)\x0Abash \/etc\/rc.local\x0A/
		p
	}
	' /etc/init.d/postfix;
fi

exit

```

Reboot your machine after running the above script.  You can test the SSD changes with the script below.  You may need to modify it for your system.  No output indicates no problems found.

```

#!/bin/bash
# Test SSD settings

echo '###########################################################################'
test=`cat /proc/mounts | grep "^/ .*commit="`
if [ "$test" = "" ]; then
	echo 'BAD: cat /proc/mounts | grep "^/ .*commit="'
fi
test=`cat /proc/sys/vm/dirty_ratio`
if [ "$test" != "40" ]; then
	echo 'BAD: cat /proc/sys/vm/dirty_ratio'
fi
test=`cat /proc/sys/vm/dirty_background_ratio`
if [ "$test" != "1" ]; then
	echo 'BAD: cat /proc/sys/vm/dirty_background_ratio'
fi
test=`cat /proc/sys/vm/dirty_writeback_centisecs`
if [ "$test" != "24000" ]; then
	echo 'BAD: cat /proc/sys/vm/dirty_writeback_centisecs'
fi
test=`cat /sys/block/sda/queue/scheduler | grep "[deadline]"`
if [ "$test" = "" ]; then
	echo 'BAD: cat /sys/block/sda/queue/scheduler'
fi
test=`cat /sys/block/sda/queue/iosched/fifo_batch`
if [ "$test" != "1" ]; then
	echo 'BAD: cat /sys/block/sda/queue/iosched/fifo_batch'
fi
test=`mount | grep "tmpfs on /var/log "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /var/log "'
fi
test=`mount | grep "tmpfs on /var/tmp "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /var/tmp "'
fi
test=`mount | grep "tmpfs on /tmp "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /tmp "'
fi
test=`mount | grep "tmpfs on /var/spool/postfix/public "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /var/spool/postfix/public "'
fi

```

Another good test is to see what files on the / filesystem have changed in the last 3 minutes.  If you find a file which is always listed, even with no user activity, then this could reduce the life and performance of your SSD.  You may want to change where that file is stored.

```
find / -xdev -cmin -3  # show files changed in last 3 minutes
```

References:
[https://wiki.ubuntu.com/Asus_P5QC#UPDATE:%20Solid%20State%20Drive%20%28SSD%29%20Added](https://wiki.ubuntu.com/Asus_P5QC#UPDATE:%20Solid%20State%20Drive%20%28SSD%29%20Added)
[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)
[http://starcubetech.blogspot.com/2008/10/ssd-optimization-on-ubuntu.html](http://starcubetech.blogspot.com/2008/10/ssd-optimization-on-ubuntu.html)
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431040](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431040)

**TOR**
tor is no longer in the ubuntu repos, and the noreply.org repo may not work due to dependencies no longer in karmic.  The following method uses an unofficial PPA to install tor.  Please read the tor project page carefully before using tor, as there are additional setup requirements for effective use:
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

And the PPA homepage:
[https://launchpad.net/~sevenmachines/+archive/tor](https://launchpad.net/~sevenmachines/+archive/tor)

Run with sudo...

```

#!/bin/bash
# must be run with sudo
# Install tor
torsrc="deb http://ppa.launchpad.net/sevenmachines/tor/ubuntu karmic main"
torkey=61E46227
torprint=454FEDB228E1455D687C9CBE35DA01C261E46227
# See https://launchpad.net/~sevenmachines/+archive/tor
# See http://www.torproject.org/docs/debian.html.en
test=`grep "$torsrc" /etc/apt/sources.list`
if [ "$test" = "" ]; then
	echo "$torsrc" >> /etc/apt/sources.list
fi
gpg --keyserver keys.gnupg.net --recv $torkey
gpg --export $torprint | sudo apt-key add -
apt-get update
apt-get install tor tor-geoipdb tsocks

```

Additional info on tor availability in karmic:
[http://ubuntuforums.org/archive/index.php/t-1153938.html](http://ubuntuforums.org/archive/index.php/t-1153938.html)

**NEPOMUK, SOPRANO, AND AKONADI**
These are servers used by KDE4 for tagging and indexing of files.  Some programs you may use, such as music players or desktop search programs, may rely on them.  However, some people don't use them and don't want them slowing down their system and consuming (considerable) RAM and CPU.  These programs can be extremely difficult to remove or disable - unfortunately it's not as simple as removing them with apt-get.  For example, apt-get doesn't even have a package installed with the name 'nepomuk'.  The KDE developers seem to be going out of their way to make them mandatory, for whatever reasons, even though they are of limited use to many people and can slow systems down considerably.

The script below is a work in progress and a hack- my crude attempt to disable these programs from loading.  If you have any input on methods I would be interested to hear it.  This script is brutal and will probably need to be run again after system updates.  Use at your own risk - I haven't had any problems with it thus far, but you may use different software than I, and thus may be affected differently.

First, if using KDE visit System Settings|Advanced|Desktop Search.  Uncheck the boxes to disable Nepomuk and Strigi.

Hopefully, the script below will disable these programs so they cannot be started.  Run with sudo.

```

#!/bin/bash
# must be run with sudo
# disable nepomuk, soprano, akonadi

killall nepomukserver
mkdir -p /usr/share/autostart/disabled

# disable nepomukserver
# http://sidux.com/PNphpBB2-viewtopic-t-12116.html
# also see /usr/share/kde4/services ?
sudo mv -f /usr/share/autostart/nepomukserver.desktop /usr/share/autostart/disabled 2> /dev/null
sudo mv -f /usr/bin/nepomuk-rcgen /usr/bin/nepomuk-rcgen-x 2> /dev/null
sudo mv -f /usr/bin/nepomukserver /usr/bin/nepomukserver-x 2> /dev/null
sudo mv -f /usr/bin/nepomukservicestub /usr/bin/nepomukservicestub-x 2> /dev/null
chmod ugo-x /usr/bin/nepomuk*

# disable soprano
sudo mv -f /usr/bin/sopranocmd /usr/bin/sopranocmd-x 2> /dev/null
sudo mv -f /usr/bin/sopranod /usr/bin/sopranod-x 2> /dev/null
chmod ugo-x /usr/bin/soprano*

# disable akonadi
sudo mv -f /usr/bin/akonadiserver /usr/bin/akonadiserver-x 2> /dev/null
chmod ugo-x /usr/bin/akonadi*

```

**BROTHER PRINTER DRIVER**
This script installs the Brother drivers for the Brother MFC-7420 printer/scanner (64 bit).  I'm including it since it can easily be modified for other Brother printers.  It makes installation a snap and the printer is even automatically added to CUPS.  This script also fixes the 'can only scan as root' problem.

First, download the following files from [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
Note that the scanner driver is for 64 bit.  If your files differ, you will need to modify the script.
```
brmfc7420lpr-2.0.1-1.i386.deb
cupswrapperMFC7420-2.0.1-2.i386.deb
brscan2-0.2.4-0.amd64.deb
```

Next, place the script in the same folder, and run the script with sudo from that folder.

```

#!/bin/bash
# must be run with sudo
# Install Brother MFC-7420 MFC drivers
if [ -e /usr/share/cups/model/MFC7420.ppd ]; then
	echo 'SKIPPED printer driver: already installed'
else
	dpkg -i --force-all --force-architecture brmfc7420lpr-2.0.1-1.i386.deb
	mkdir /usr/share/cups/model/
	dpkg -i --force-all --force-architecture cupswrapperMFC7420-2.0.1-2.i386.deb
	# http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142
	ln -s /usr/lib/libbrcomplpr2.so /usr/lib32/libbrcomplpr2.so
fi
if [ -e /usr/lib64/libbrscandec2.so ]; then
	echo 'SKIPPED scanner driver: already installed'
else
	dpkg -i brscan2-0.2.4-0.amd64.deb
fi
# fix can only scan as root problem
sed -i 's/^\(SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",.* MODE=\).*/\1"0666"/' /lib/udev/rules.d/50-udev-default.rules
echo 'Visit http://localhost:631'

```

**SCANPIC SCRIPT**
Below is a script which scans pics and documents of various sizes from the command line.  It is written for the Brother MFC-7420 scanner, but can easily be modified to work with other scanners.  Just change the device= line to your device name, and you may also need to adjust the default offset.  I wrote this when I was scanning hundreds of old pics of various sizes and I wanted to do it quickly from the command line.

Before running this script, run
```
sudo apt-get install sane sane-utils imagemagick
```

```

#!/bin/bash

argsneeded=1

# Defaults
device="brother2"
colmode="24bit Color"
size="2560x2560"
quality="90"
res="600"
rotate=0
form="full"
x=""
y=""
l="12"
t="4.5"
bright=""
contrast=""

help ()
{
	echo "Scans pic to jpg file on Brother MFC-4720"
	echo "Requires: sane-utils imagemagick"
	echo "Usage:   scanpic [OPTIONS] outputfilename"
	echo 'Example: scanpic --opt 4x6v,bw --size 1280x1280 output.jpg'
	echo '         scans 4x6 vertical B&W print to 1280x1280(max) jpeg'
	echo '         with standard offset'
	echo "Options:"
	echo "   --opt  <option>,<option>,...  image options (see below)"
	echo "   --size <width>x<height>       max final size (pixels) (overrides opt)"
	echo "                                 [default 2560x2560]"
	echo "   --quality <0...100>           jpeg quality (overrides opt)"
	echo "                                 [default 90]"
	echo "   --dims <width>x<height>       scan size (mm) (overrides opt)"
	echo "                                 [default full]"
	echo "   --offset <width>x<height>     offset (mm) (overrides opt)"
	echo "                                 [default 12x4.5mm]"
	echo "   --res <dpi>                   resolution dpi (overrides opt)"
	echo "                                 [default 600]"
	echo "   --rotate <degrees>            rotation (overrides opt) [default 0]"
	echo "   --bright <-50...50%>          scan brightness (overrides opt)"
	echo "   --contrast <-50...50%>        scan contrast (overrides opt)"
	echo "opt arguments:"
	echo '   bw         color mode "Black & White"'
	echo '   gray       color mode "True Gray"'
	echo '   col        color mode "24bit Color"        [default]'
	echo '   page       scan size 8.5x11" gray - no offset'
	echo '   walletv    scan size 44x64mm vertical'
	echo '   pocketv    scan size 60x85mm vertical'
	echo '   pocketh    scan size 85x60mm horiz'
	echo '   3.5x5v     scan size 3.5x5" vertical'
	echo '   3.5x5h     scan size 3.5x5" horiz'
	echo '   3.5x5sv    scan size 3.5x5" (smaller than 5") vertical'
	echo '   3.5x5sh    scan size 3.5x5" (smaller than 5") horiz'
	echo '   4.25x3.5h  scan size 4.25x3.5" horiz'
	echo '   4x6v       scan size 4x6" vertical'
	echo '   4x6h       scan size 4x6" horiz'
	echo '   4x10       scan size 4x10" (place vertical)'
	echo '   5x7        vscan size 5x7" vertical'
	echo '   5x7h       scan size 5x7" horiz'
	echo '   8x10v      scan size 8x10" vertical' 
	echo '   8x10h      scan size 8x10" horiz (place vertical)' 
	echo '   polaroidh  Polaroid horiz'
	exit
}

#Process arguments
index=0
while [ "$1" != "" ];
do
	if [ "${1:0:1}" = "-" ]; then
		case "$1" in
			--help | -help )
				help
				;;
			--opt )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				opt="$2"
				while [ -n "$opt" ]
				do
					# get subopt
					subopt=${opt%%,*}
					newopt=${opt#*,}
					if [ "$newopt" == "$opt" ]; then
						opt=""
					else
						opt="$newopt"
					fi
					case "$subopt" in
						bw )
							colmode="Black & White";;
						gray )
							colmode="True Gray";;
						col )
							colmode="24bit Color";;
						page )
							form=$subopt
							l=0
							t=0
							x=220
							y=278
							res=300
							size="1280x1280"
							colmode="True Gray"
							;;
						walletv )
							form=$subopt
							l=13
							t=4.5
							x=44
							y=64
							;;
						pocketv )
							form=$subopt
							l=13
							t=4.5
							x=60
							y=85
							;;
						pocketh )
							form=$subopt
							l=13
							t=4.5
							x=85
							y=60
							;;
						4.25x3.5h )
							form=$subopt
							l=13
							t=4.5
							x=110
							y=89
							;;
						3.5x5sv )
							form=$subopt
							l=13
							t=4.5
							x=89
							y=125
							;;
						3.5x5sh )
							form=$subopt
							l=13
							t=4.5
							x=125
							y=89
							;;
						3.5x5h )
							form=$subopt
							l=13
							t=4.5
							x=130
							y=89
							;;
						3.5x5v )
							form=$subopt
							l=13
							t=4.5
							x=89
							y=130
							;;
						polaroidh )
							form=$subopt
							l=18
							t=14.5
							x=91
							y=68
							;;
						4x6v )
							form=$subopt
							l=12
							t=4.5
							x=101
							y=152
							;;
						4x6h )
							form=$subopt
							l=12
							t=5
							x=152
							y=101
							;;
						5x7v )
							form=$subopt
							l=12
							t=5
							x=126
							y=178
							;;
						5x7h )
							form=$subopt
							l=12
							t=5
							x=178
							y=126
							;;
						4x10 )
							form=$subopt
							l=12
							t=4.5
							x=101
							y=250.8
							rotate=90
							;;
						8x10v )
							form=$subopt
							l=12
							t=4.5
							x=206
							y=252
							;;
						8x10h )
							form=$subopt
							l=12
							t=4.5
							x=206
							y=252
							rotate=90
							;;
						* )
							echo Unrecognized --opt $subopt
							exit
							;;
					esac
				done
				shift
				;;
			--size )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				size="$2"
				shift
				;;
			--res )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				res="$2"
				shift
				;;
			--bright )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				bright="--brightness=$2"
				shift
				;;
			--contrast )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				contrast="--contrast=$2"
				shift
				;;
			--quality )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				quality="$2"
				shift
				;;
			--rotate )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				rotate="$2"
				shift
				;;
			--dims )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				arg="$2"
				x=${arg%x*}
				y=${arg#*x}
				if (( x == 0 )) || (( y == 0 )); then
					echo "Option $1 requires <width>x<height> argument"
					exit
				fi
				shift
				;;
			--offset )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				arg="$2"
				l=${arg%x*}
				t=${arg#*x}
				if (( x == 0 )) || (( y == 0 )); then
					echo "Option $1 requires <width>x<height> argument"
					exit
				fi
				shift
				;;
			* )
				echo Unknown option $1
				exit
				;;
		esac
	else
		let "index+=1"
		case $index in
			1 )
				outfile="$1"
				;;
			* )
				echo Too many arguments
				exit
				;;
		esac
	fi
	shift
done
if (( index < $argsneeded )); then
	help
fi

# Get pathname and filename
filename=`basename "$outfile"`
xx=${#filename}  #len
yy=${#outfile}  #len
pathname="${outfile:0:((yy-xx))}"
if [ "$pathname" == "" ]; then
	pathname="."
fi

echo "Form:         $form"
if [ "$x" == "" ] || [ "$y" == "" ]; then
	echo "Scan Size:    full (215.88 x 355.567 mm)"
	x=""
	y=""
else
	echo "Scan Size:    $x x $y mm"
fi
echo "Scan Offset:  $l x $t mm"
echo "Resolution:   $res"
echo "Color Mode:   $colmode"
echo "Device:       $device"
echo "Rotation:     $rotate degrees"
echo "JPEG Size:    $size (max)"
echo "JPEG Quality: $quality"
echo

tmpfile="$pathname/scanpic-temp.pnm"
rm -f "$tmpfile"

if [ "$x" == "" ]; then
	scanimage --device=$device --mode="$colmode" --resolution=$res $bright $contrast --format=pnm --progress -l $l -t $t > "$tmpfile"
else
	scanimage --device=$device --mode="$colmode" --resolution=$res $bright $contrast --format=pnm --progress -l $l -t $t -x $x -y $y > "$tmpfile"
fi

echo
echo Scan complete.  Converting...

if [ "$rotate" = "0" ]; then
	convert "$tmpfile" -resize ">$size" -filter Lanczos -quality $quality "$outfile"
else
	convert "$tmpfile" -resize ">$size" -filter Lanczos -quality $quality -rotate $rotate "$outfile"
fi

rm -f $tmpfile

echo Done.

exit

```

**RESIZE AND EMAIL PIC (REPIC SCRIPT)**
This is a script for resizing pic(s), and can also send a pic to an email in Kmail.  I see they've finally added this email ability to Kubuntu, but this script gives you more control over the size, etc.

You can add a menu item with the command "repic --email %U" so that you can right-click on a pic (or pics) in your file manager and email it (them), or add entries to resize it to different sizes.  For example, right-click and Open with... "Resize to 800x800".

Before running this script, run
```
sudo apt-get install imagemagick jhead
```

Note that this script rotates the original pic if needed.  If you don't want this, uncomment the jhead line.

```

#!/bin/bash

tmp=/tmp
argsneeded=1
size="2560x2560"
quality=85
dstfile=""
verbose=0
verb=""
replace=0
remove=0
rotate=0
movetmp=0
email=0
attaches=""
# Set the field seperator to a newline - allows for quoted wildcards
IFS="
"

help ()
{
	echo "Resizes jpg file(s) if larger than size (first rotates original if needed)"
	echo "Usage: repic [OPTIONS] FILE ..."
	echo "Option: --size ###x###        [default $size]"
	echo "Option: --quality ##          [default $quality]"
	echo "Option: --replace             [overwrite original files]"
	echo "Option: --remove              [remove original files]"
	echo "Option: --rotate              [only auto-rotate original, no resize]"
	echo "Option: --verbose"
	echo "Option: --tmp                 [Move output file(s) to $tmp]"
	echo "Option: --email               [Create an email message, 1024x768 in $tmp]"
	echo "Note: Options must be placed before files"
	exit
}

index=0
while [ "$1" != "" ];
do
	if [ "${1:0:1}" = "-" ]; then
		case "$1" in
			--help )
				help
				;;
			--size )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				size="$2"
				shift
				;;
			--quality )
				if [ "$2" == "" ]; then
					echo Option $1 requires argument
					exit
				fi
				quality="$2"
				shift
				;;
			--verbose )
				verbose=1
				verb="-verbose"
				;;
			--replace )
				replace=1
				;;
			--remove )
				remove=1
				;;
			--rotate )
				rotate=1
				;;
			--tmp )
				movetmp=1
				;;
			--email )
				email=1
				size="1024x768"
				;;
			* )
				echo Unknown option $1
				exit
				;;
		esac
	else
		for i in $1 ; do
			let "index+=1"
			srcfile="$i"
			# Rotate original
			if (( verbose == 1 )); then
				echo jhead -autorot '"'$srcfile'"'
			fi
			jhead -autorot "$srcfile"
			if (( rotate == 0 )); then
				# remove extension
				srcbase=`basename "$srcfile" .jpg`
				srcbase=`basename "$srcbase" .jpeg`
				srcbase=`basename "$srcbase" .JPG`
				srcbase=`basename "$srcbase" .JPEG`
				
				#get pathname
				filename="${srcfile##*/}"
				x=${#filename}  #len
				y=${#srcfile}  #len
				pathname=${srcfile:0:((y-x))}
				
				
				# Create resize
				tmpfile="$pathname$srcbase-resizetmp.jpg"
				if (( verbose == 1 )); then
					echo convert '"'$srcfile'"' $verb -resize '">'$size'"' -filter Lanczos -quality $quality '"'$tmpfile'"'
				fi
				convert "$srcfile" $verb -resize ">$size" -filter Lanczos -quality $quality "$tmpfile"
				errcode="$?"
				if [ -e "$tmpfile" ] && [ "$errcode" == "0" ]; then
					# Determine new size
					resize=`identify -format '%wx%h' "$tmpfile"`
					origsize=`identify -format '%wx%h' "$srcfile"`
					if [ "$resize" == "" ]; then
						resize="ERROR"
					fi
				else
					echo "ERROR: convert produced no output and/or error code $errcode"
					if (( verbose == 0 )); then
						echo convert '"'$srcfile'"' $verb -resize '">'$size'"' -filter Lanczos -quality $quality '"'$tmpfile'"'
					fi
					exit
				fi
							
				if [ "$resize" == "$origsize" ]; then
					if (( email == 1 )); then
						# add to email message
						attaches="$attaches --attach \"$srcfile\""
					fi
					echo Not resizing $srcfile
					if (( verbose == 1 )); then
						echo rm -f '"'$tmpfile'"'
					fi
					rm -f "$tmpfile"
				else
					if (( replace == 1 )); then
						dstfile="$srcfile"
					else
						dstfile="$pathname$srcbase-[$resize].jpg"
					fi
					if (( verbose == 1 )); then
						echo mv '"'$tmpfile'"' '"'$dstfile'"'
					fi
					mv "$tmpfile" "$dstfile"
					# Rotate dst (just in case)
					if (( verbose == 1 )); then
						echo jhead -autorot '"'$dstfile'"'
					fi
					jhead -autorot "$dstfile"
					if (( remove == 1 )) && (( replace == 0 )); then
						# Remove original
						if (( verbose == 1 )); then
							echo rm -f '"'$srcfile'"'
						fi
						rm -f "$srcfile"
					fi
					if (( movetmp == 1 )); then
						# Move to tmp
						mv "$dstfile" "$tmp"
						dstfile="$tmp/"`basename $dstfile`
					fi
					if (( email == 1 )); then
						# add to email message
						attaches="$attaches --attach \"$dstfile\""
					fi
				fi
				if (( verbose == 1 )); then
					echo
				fi
			fi
		done
	fi
	shift
done
if (( index < $argsneeded )); then
	help
fi

if (( email == 1 )) && [ -n "$attaches" ]; then
	# workaround kmail command line parse bugs
	echo "#!/bin/bash" > $tmp/repic-kmail-tmp.sh
	echo kmail -s "Pics" --composer $attaches >> $tmp/repic-kmail-tmp.sh
	bash $tmp/repic-kmail-tmp.sh
	rm $tmp/repic-kmail-tmp.sh
fi

exit

#In k menu editor use %U to send list:
#	repic --email %U

# Krusader User Action example:

<action name="repic-email" >
  <title>Repic Email</title>
  <tooltip>Repic Email</tooltip>
  <icon>internet-mail</icon>
  <command>/user/scripts/repic --email %aList("Selected")%</command>
  <availability>
   <filename>
    <show>*.jpg</show>
    <show>*.jpeg</show>
   </filename>
  </availability>
 </action>


```

**SETUP VNC4SERVER**
Below is a script which sets up vnc4server on Kubuntu karmic.  This is based on the guide here:
[http://ubuntuforums.org/archive/index.php/t-1078497.html](http://ubuntuforums.org/archive/index.php/t-1078497.html)

This setup allows you to login to KDE remotely using a command like
```
krdc 192.168.1.100:5901
```

You will be presented with the KDM greeter.  If you close the VNC window and reconnect, you will be in the same KDE session, unless you logged out (resumable session).

Run this script with sudo, then reboot.  Note that you will be asked to set your VNC password.  If you already have a VNC password file, you can comment out that line.

```

#!/bin/bash
# must be run with sudo
# Setup vnc4server

sudo apt-get install xinetd vnc4server
/etc/init.d/xinetd stop
killall -w Xvnc

# edit /etc/kde4/kdm/kdmrc
sed -i -n '
1h
1!H
$ {
	g
	s/\[Xdmcp\].*Willing=\/etc\/kde4\/kdm\/Xwilling/\[Xdmcp\]\x0AEnable\=true\x0APort\=177\x0AXaccess=\/etc\/kde4\/kdm\/Xaccess\x0AWilling=\/etc\/kde4\/kdm\/Xwilling/
	p
}
' /etc/kde4/kdm/kdmrc;

# edit /etc/kde4/kdm/Xaccess
sed -i 's/^\#\*.*\#any host can get a login window/\*            \#any host can get a login window/' /etc/kde4/kdm/Xaccess
sed -i 's/^\#\*.*CHOOSER BROADCAST.*\#any indirect host can get a chooser/\*               CHOOSER BROADCAST       #any indirect host can get a chooser/' /etc/kde4/kdm/Xaccess

# Create /etc/xinetd.d/Xvnc - modify as needed
cat << EOF > /etc/xinetd.d/Xvnc
service Xvnc
{
		type = UNLISTED
		disable = no
		socket_type = stream
		protocol = tcp
		wait = yes
		user = root
		server = /usr/bin/Xvnc
		server_args = -inetd :1 -query 127.0.0.1 -geometry 1220x915 -depth 16 -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -DisconnectClients=1 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
		port = 5901
}
EOF

# Setup vnc password
echo 'Enter your new VNC password:'
vncpasswd /root/.vncpasswd
chmod go-rwx /root/.vncpasswd

/etc/init.d/xinetd start
echo 'Reboot may be required'

```

**DISABLE USB AUDIO**
Some webcams have microphones in them which can be used to eavesdrop.  If you have such a webcam and want to disable its microphone, the following method works.  Note: this will probably disable any USB microphone or possibly any USB audio device, not just webcams.

First, save this script (the original version of which was written by Landon Curt Noll) as "usbaudiooff":

```

#!/bin/bash
#
# usbaudiooff   Disable USB audio so that non-USB sound will not be confused
#
# chkconfig: 2345 04 04
# description: Remove the USB audio module
#
# See: http://www.saillard.org/linux/pwc/ for support or
#      www.isthe.com/chongo/tech/comp/pwc/index.html for hints.
#
# Placed in the public domain by Landon Curt Noll
#
# chongo (Share and enjoy! :-)) www.isthe.com/chongo/index.html
# Modified for Kubuntu from 
#   http://isthe.com/chongo/tech/comp/pwc/rh8.0.html#disable_usb_audio

# Source function library.
#??? . /etc/rc.d/init.d/functions

# setup
AUDIO_FOUND="`/sbin/lsmod | /bin/grep '^snd_usb_audio '`"

# See how we were called.
case "$1" in
  start|restart|reload)
        echo -n "Disable USB audio: "
        if [ -z "$AUDIO_FOUND" ]; then
            passed "Disable USB audio -"
        else
            /sbin/rmmod snd_usb_audio
            RETVAL=$?
            if [ "$RETVAL" -eq 0 ]; then
                echo success "Disable USB audio -"
            else
                echo failure "Disable USB audio -"
            fi
        fi
        echo
        ;;
  stop)
        RETVAL=0
        ;;
  status)
        echo -n "Looking for the USB audio module: $AUDIO_FOUND"
        RETVAL=0
        echo
        ;;
  *)
        echo "Usage: usbaudiooff {start|stop|reload|status}"
        RETVAL=1
        ;;
esac

exit $RETVAL

```

Then issue these three commands:

```
sudo cp usbaudiooff /etc/init.d
sudo chmod u+rwx,go-w+rx /etc/init.d/usbaudiooff
sudo update-rc.d usbaudiooff defaults
```

Reboot, and the microphone should be disabled.  You can confirm this with
```
lsmod | grep snd_usb_audio
```

Output should be nothing.  As long as lsmod does not report "snd_usb_audio" running, the USB audio should be disabled.

To re-enable USB audio:
```
update-rc.d -f usbaudiooff remove
```


Hope you get some use out of these - let me know if you encounter any bugs.

---

### Post by Username4 on 2009-11-02
Thanks for that "disable Akonadi" script. I know for sure that I don't wont Akonadi server to ever start. Since uninstalling it pulls down core KDE with dependencies this hack looks like a temporary bug-fix to me. (I applied it and encountered no issues.)

---

### Post by skotos on 2009-11-02
Thank you IgnorantGuru!

---

### Post by Damanther on 2009-11-02
Any advice on getting vnc4server to work for 64 bit?

On previous releases, I've downgraded to the 4.0-73 version for 64 bit, but I can no longer do that with the update to libstdc++6.

Damanther

---

### Post by necromonger on 2009-11-02
make this a sticky.

---

### Post by IgnorantGuru on 2009-11-02
> **Damanther said:**
> Any advice on getting vnc4server to work for 64 bit?

I installed it on a 64 bit machine using the method above - no problems, straight from the karmic repository.  Well, it doesn't look as pretty as it did pre-karmic - for some reason the graphics are somewhat garbled.  But good enough for my limited purposes.  I don't think that's a 64 bit issue though - probably something to do with the KDE theme or plasma.

Note that the script above is KDE specific in a few areas.  Gnome setup is similar.  Here are some other guides I used - maybe outdated but I don't think the procedure has changed too much in gnome.
[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)
[http://www.skullbox.net/vncserver.php](http://www.skullbox.net/vncserver.php)

---

### Post by IgnorantGuru on 2009-11-02
Also, issue this command to get the correct font path for the Xvnc server_args= line:

```
xset q
```

---

### Post by kgarbutt on 2009-11-02
Nice coding IgnorantGuru. Really nice.

---

### Post by IgnorantGuru on 2009-11-02
> **kgarbutt said:**
> Nice coding IgnorantGuru. Really nice.

Thanks.

---

### Post by IgnorantGuru on 2009-11-02
I said above that KDE finally added a way to email a pic from the file manager, but apparently they haven't (not in Dolphin at least).  I was looking at Krusader's menu, which is the file manager I use.

So here are more detailed instructions for how to set that up.  Basically this will allow you to right-click on a pic or group of pics and resize or email them with one click.  Very easy setup.

First, save the "repic" script above, let's say to /myscripts/repic. Then go into the Menu Editor and create a new item.  Call it "Resize to 800x600".  In the command box for the item, enter:
```
/myscripts/repic --size 800x600 %U
```

Save the menu and close the Menu Editor.  

Next step is to associate the program "Resize to 800x600", which you just added, with JPG files.  If using KDE, go into your file manager, right-click on a JPG file, and select Properties.  Click the little wrench icon (Edit File Type).  Under Application Preference Order, click Add...  Find the "Resize to 800x600" in the menu that pops up, and click OK.  Then just make sure "Resize to 800x600" isn't listed first in Application Preference Order (you don't want that to be the default way to open JPGs).  Click OK, and OK again.

Now you can right-click on the JPG and select Open with... "Resize to 800x600".  The pic will be resized to a new file in the same folder (the original will remain).  You can do the same with a batch of pics at once.

Gnome is similar I'm sure.  You can also use the file associations in KDE's System Settings|Advanced|File Associations to set them up if you don't want to do it in the file manager.

You can add other menu entries for other sizes the same way.  Note that "800x600" refers to the *maximum* horizontal and vertical dimensions (aspect ratio is preserved).  (If a pic is too small, it won't be resized.)

You can also add an entry called "Email Pic", with the command being:
```
/myscripts/repic --email %U
```
or
```
/myscripts/repic --tmp --email %U
```

The selected pics will be resized and put into an email.  Note that this requires KDE's kmail, but if your email client accepts emails with attachments on the command line, you can adjust the script to use your client.

Also, if you want to resize a whole folder of pics, you can use a command like:
```
repic *.jpg *.JPG
```

For additional options:
```
repic --help
```

If anything doesn't work as advertised please let me know.  I use this script all the time so it's pretty well debugged.

---

### Post by IgnorantGuru on 2009-11-03
As I suspected, in the SSD CHANGES section, the mount /var/log is not having the desired effect of protecting the SSD.  The system starts log files before rc.local is run.  When tmpfs is mounted to /var/log, the system log files become invisible, but they are still updated (every few seconds).  So there is really little gained mounting them in rc.local.  Until the bug in mountall is fixed, I don't know a way to prevent all these writes to /var.  The SSD is still somewhat protected if you added the commit= line in fstab.  That way even though /var/log changes every few seconds, the changes are only written to disk every few minutes, which makes a big different over time.  So you should definitely add the commit=.  Also note that you CAN still mount /tmp as tmpfs - the bug does not stop that.

Here are modified versions of the SSDCHANGES scripts above which doesn't bother mounting /var/log in rc.local.  It still mounts /var/tmp, since that happens before KDE starts and is thus useful.  If you already ran the scripts above, you can run these scripts and it will undo those changes, while keeping the changes you still want.

The ssdchanges script - run with sudo.

```

#!/bin/bash
# must be run with sudo
# setup changes for SSD

# modify /etc/sysctl.conf to change kernel dirty page writeback time
test=`grep '\# I added to reduce disk activity' /etc/sysctl.conf`
if [ "$test" = "" ]; then
	if [ ! -e /etc/sysctl.conf-orig ]; then
		cp -a /etc/sysctl.conf sysctl.conf-orig
	fi
	echo >> /etc/sysctl.conf
	echo '# I added to reduce disk activity to 240 seconds' >> /etc/sysctl.conf
	echo 'vm.dirty_ratio = 40' >> /etc/sysctl.conf
	echo 'vm.dirty_background_ratio = 1' >> /etc/sysctl.conf
	echo 'vm.dirty_writeback_centisecs = 24000' >> /etc/sysctl.conf
fi

# Note: if you DON'T have a laptop, uncomment the line below
# to prevent changes possibly being undone
#chmod -x /usr/lib/pm-utils/power.d/laptop-mode

# edit fstab to mount ramdrive to /tmp
test=`grep '^tmpfs.*\/tmp.*tmpfs' /etc/fstab`
if [ "$test" = "" ]; then
	if [ ! -e /etc/fstab-orig ]; then
		cp -a /etc/fstab /etc/fstab-orig
	fi
	echo >> /etc/fstab
	echo '# I added to reduce disk activity' >> /etc/fstab
	echo 'tmpfs /tmp tmpfs defaults,noatime,size=1000M,mode=1777 0 0' >> /etc/fstab
	echo '# The following lines are disabled because of the bug in mountall' >> /etc/fstab
	echo '# These may be mounted in /etc/rc.local instead' >> /etc/fstab
	echo '# See https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431040' >> /etc/fstab
	echo '#tmpfs /var/log tmpfs defaults,noatime,size=200M,mode=0755 0 0' >> /etc/fstab
	echo '#tmpfs /var/tmp tmpfs defaults,noatime,size=500M,mode=1777 0 0' >> /etc/fstab
	echo '#tmpfs /var/spool/postfix/public tmpfs defaults,noatime,size=50K,mode=1777 0 0' >> /etc/fstab
fi

# Replace rc.local for SSD changes
if [ ! -e /etc/rc.local-orig ]; then
	cp -a /etc/rc.local /etc/rc.local-orig
fi
cat << EOF > /etc/rc.local
#!/bin/bash
# above must be #!/bin/bash not default /bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# mount ramdrives to /var/tmp and /var/spool/postfix/public
for dir in "/var/tmp" "/var/spool/postfix/public" ; do
	test=`mount | grep " on $dir "`
	if [ "$test" = "" ]; then
		sz="50K"
		md="1777"
		case "$dir" in
			/var/tmp )
				sz="500M"
				md="1777"
				;;
			/var/spool/postfix/public )
				sz="50K"
				md="1777"
				;;
		esac
		mount -t tmpfs -o size=$sz,noatime,mode=$md tmpfs $dir
	fi
done

# Set sda to use deadline scheduler
# Note: if these changes don't seem to take, try pasting them into a root console
#       (or with sudo) manually once then reboot
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch

exit 0

EOF

chmod u+x /etc/rc.local

# If you run postfix, change postfix startup script so that rc.local runs first
# Note: This may need to be repeated if postfix is upgraded
test=`grep 'bash /etc/rc.local' /etc/init.d/postfix`
if [ "$test" = "" ]; then
	sed -i -n '
	1h
	1!H
	$ {
		g
		s/case "$1" in\x0A    start)\x0A/case "$1" in\x0A    start)\x0Abash \/etc\/rc.local\x0A/
		p
	}
	' /etc/init.d/postfix;
fi

exit


```

And the ssdchangestest script - run with sudo:

```

#!/bin/bash
# Test SSD settings

echo '###########################################################################'
test=`cat /proc/mounts | grep "^/ .*commit="`
if [ "$test" = "" ]; then
	echo 'BAD: cat /proc/mounts | grep "^/ .*commit="'
fi
test=`cat /proc/sys/vm/dirty_ratio`
if [ "$test" != "40" ]; then
	echo 'BAD: cat /proc/sys/vm/dirty_ratio'
fi
test=`cat /proc/sys/vm/dirty_background_ratio`
if [ "$test" != "1" ]; then
	echo 'BAD: cat /proc/sys/vm/dirty_background_ratio'
fi
test=`cat /proc/sys/vm/dirty_writeback_centisecs`
if [ "$test" != "24000" ]; then
	echo 'BAD: cat /proc/sys/vm/dirty_writeback_centisecs'
fi
test=`cat /sys/block/sda/queue/scheduler | grep "[deadline]"`
if [ "$test" = "" ]; then
	echo 'BAD: cat /sys/block/sda/queue/scheduler'
fi
test=`cat /sys/block/sda/queue/iosched/fifo_batch`
if [ "$test" != "1" ]; then
	echo 'BAD: cat /sys/block/sda/queue/iosched/fifo_batch'
fi
test=`mount | grep "tmpfs on /var/tmp "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /var/tmp "'
fi
test=`mount | grep "tmpfs on /tmp "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /tmp "'
fi
test=`mount | grep "tmpfs on /var/spool/postfix/public "`
if [ "$test" = "" ]; then
	echo 'BAD: mount | grep "tmpfs on /var/spool/postfix/public "'
fi
exit


```

---

### Post by IgnorantGuru on 2009-11-08
I've set up a blog and download site where I can share some of these scripts.  It's kind of cumbersome to update and maintain them on the forum so I thought this might work well.  I am gradually polishing some of the above scripts and others I have, and adding them to the blog site.
[http://igurublog.wordpress.com/](http://igurublog.wordpress.com/)

Comments are welcome, both on the presentation and on the scripts and howtos.  It helps me to know what kinds of scripts people find useful - sometimes I don't have a clue so it's hard to decide which ones to spend more time on.  So if you find something of use to you, please leave a comment (on the blog or here) and let me know - thanks.

I just added an updated version of the scanpic script from the post above.  This one tries to detect your scanner's device name, and also lets you specify a device on the command line.  And there are a few other scripts up there as well.

Check the blog in the coming weeks for updates.  I will be traveling later this month but after that I should have time to add some more.

---

### Post by mikaelstaldal on 2009-11-15
If you really want to protect your SSD, thy this:
[http://www.staldal.nu/tech/2009/11/15/linux-with-mounted-read-only-2-0/]("http://www.staldal.nu/tech/2009/11/15/linux-with-mounted-read-only-2-0/")

---

