---
title: "hard disk drive power spin down time setting?"
date: 2008-10-06
forum: General Help
---

### Post by sdowney717 on 2008-10-06
my secondary hard drive (sdb1) shuts down after a few minutes.
How can I adjust the setting on my second hard drive?
I want it to spin down sooner.

found this but does it tell me anything about sdb1?

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
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

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
# -s Turn on/off power on in standby mode
#poweron_standby = off
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
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

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

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

```

---

### Post by cariboo on 2008-10-06
Hdparm should work for any drive, You would use the command:

```
sudo hdparm -S 24 /dev/sdb
```

This is the pertinent section from man hdparm:

> -S     Set the standby (spindown) timeout for the drive.  This value is
              used by the drive to determine how long to wait  (with  no  disk
              activity)  before  turning  off the spindle motor to save power.
              Under such circumstances, the drive may take as long as 30  sec&#8208;
              onds  to respond to a subsequent disk access, though most drives
              are much quicker.  The encoding of the timeout value is somewhat
              peculiar.   A  value  of zero means "timeouts are disabled": the
              device will not automatically enter standby mode.  Values from 1
              to  240 specify multiples of 5 seconds, yielding timeouts from 5
              seconds to 20 minutes.  Values from 241 to 251 specify from 1 to
              11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5
              hours.  A value of 252 signifies a  timeout  of  21  minutes.  A
              value  of 253 sets a vendor-defined timeout period between 8 and
              12 hours, and the value 254 is reserved.  255 is interpreted  as
              21  minutes  plus  15  seconds.  Note that some older drives may
              have very different interpretations of these values.

For more info, in a terminal type:

```
man hdparm
```

Jim

---

### Post by sdowney717 on 2008-10-06
thanks for the reply. 
So why is it spinning down now since nothing in the hdparm.conf file says anything about sdb1?

---

### Post by nightanole on 2008-11-02
Your hdparm.conf is blank so ubuntu is using the defaults of the hard drive.  This is/was a problem with notebooks running ubuntu, because the defaults of the notebook hds had then spinning down several times a min and wearing them out.

sudo hdparm -I /dev/sdb1 | grep level

That should tell you what number your hard drive spin down time is.

[http://ubuntuforums.org/showthread.php?t=805570]("http://ubuntuforums.org/showthread.php?t=805570")


[https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement")


those 2 sites should help you understand and change the power features to what you want.

---

### Post by natrik on 2009-11-23
> **nightanole said:**
> sudo hdparm -I /dev/sdb1 | grep level

That should tell you what number your hard drive spin down time is.


One would hope... but not for me.  This computer is a laptop (Dell E1505) and I get the following:

```
nate@silver:~> sudo hdparm -I /dev/sda|grep level
        Advanced power management level: disabled
```

However, the actual spin-down timeout is about 2 minutes so.   I looked in gconf-editor under /apps/gnome-power-manager and found nothing whatever about disks.  In fact, searching "disk" in gconf-editor shows only unrelated items.

Additional results: 

```
nate@silver:~> sudo hdparm -I /dev/sda | grep -i power
        Advanced power management level: disabled
           *    Power Management feature set
                Advanced Power Management feature set
           *    Host-initiated interface power management
                Device-initiated interface power management
```
* The asterisk denotes "feature enabled" as is seen with the full output of **[FONT="Courier New"]sudo hdparm -I /dev/sda[/FONT]** 
So therefore the device (disk) is not spinning ITSELF down, because it does not have that feature.  

How is it turning off?  Where is the adjustment?

-- Nate

---

