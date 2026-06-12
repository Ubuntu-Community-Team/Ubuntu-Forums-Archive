---
title: "Need help with hdparm and bootmisc.sh"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by beeldings on 2005-05-07
I configured hdparm.conf to increase the performance of my IDE hard drive (/dev/hda). I noticed that when I saved the file and rebooted the PC, the settings in hdparm were not applied to the drive. I did some research on Google and decided to edit the bootmisc.sh file in order to apply the hdparm settings to the drive. Oddly enough when bootmisc.sh was accessed during the boot process, the settings I posted for my hard drive, /dev/hda, were applied to my DVD±RW drive, /dev/hdc, and no changes were made to the hard drive. I don't know why my settings in hdparm.conf aren't properly applied to my hard drive during the boot process. If it helps, here are copies of my hdparm.conf and my bootmisc.sh files.

hdparm.conf
```

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

/dev/hda {
	interrupt_unmask = on
	mult_sect_io = 16
	io32_support = 3
	dma = on
	transfer_mode= 68
	keep_features_over_reset = on
	chipset_pio_mode = 4
	write_cache = on
}
#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

```

bootmisc.sh:
```

#
# bootmisc.sh	Miscellaneous things to be done during bootup.
#
# Version:	@(#)bootmisc.sh  2.85-17  04-Jun-2004  miquels@cistron.nl
#

/sbin/hdparm -d1c3u1m16X68 /dev/hda 
/sbin/hdparm -d1u1 /dev/hdc

DELAYLOGIN=yes
VERBOSE=yes
EDITMOTD=yes
[ -f /etc/default/rcS ] && . /etc/default/rcS

#
#	Put a nologin file in /etc to prevent people from logging in
#	before system startup is complete.
#
if [ "$DELAYLOGIN" = yes ]
then
	echo "System bootup in progress - please wait" > /etc/nologin
fi

#
#	Create /var/run/utmp so we can login.
#
: > /var/run/utmp
if grep -q ^utmp: /etc/group
then
	chmod 664 /var/run/utmp
	chgrp utmp /var/run/utmp
fi

#
#	Set pseudo-terminal access permissions.
#
if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
then
	chmod -f 666 /dev/tty[p-za-e][0-9a-f]
	chown -f root:tty /dev/tty[p-za-e][0-9a-f]
fi

#
#	Update /etc/motd. If it's a symbolic link, do the actual work
#	in the directory the link points to.
#
if [ "$EDITMOTD" != no ]
then
	MOTD="`readlink -f /etc/motd || :`"
	if [ "$MOTD" != "" ]
	then
		uname -a > $MOTD.tmp
		sed 1d $MOTD >> $MOTD.tmp
		mv $MOTD.tmp $MOTD
	fi
fi

#
#	Save kernel messages in /var/log/dmesg
#
if [ -x /bin/dmesg ] || [ -x /sbin/dmesg ]
then
	dmesg -s 524288 > /var/log/dmesg
elif [ -c /dev/klog ]
then
	dd if=/dev/klog of=/var/log/dmesg &
	dmesg_pid=$!
	sleep 1
	kill $dmesg_pid
fi


#
#	Remove ".clean" files.
#
rm -f /tmp/.clean /var/run/.clean /var/lock/.clean

: exit 0

```

---

### Post by JonahRowley on 2005-05-08
hdparm is already being started by default, take a look at **/etc/init.d/hdparm**, which **/etc/rcS.d/S07hdparm** links to.  The hdparm init script will run unless **nohdparm** is specified in the kernel boot parameters.  Is this interfering with your hdparm command (which will be running after)?

---

