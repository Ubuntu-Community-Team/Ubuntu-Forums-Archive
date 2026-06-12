---
title: "DMA wont stay enabled after reboot!"
date: 2005-11-29
forum: General Help
---

### Post by madmusiq on 2005-11-29
After rebooting my system my DMA settings change to off when when I want to keep them on. Here's my edited hdparm.conf below:

madmusiq@linuxbox:~$ gedit /etc/hdparm.conf

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
#dma = on
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
}

/dev/cdroms/cdrom0 {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

}

/dev/cdroms/cdrom1 {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

/dev/hda {
	mult_sect_io = 16
	write_cache = off
	dma = on
}

/dev/hdb {
	multi_sec_io = 16
	write_cache = off
	dma = on
} 
#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}


I can DMA mode to "on" using the hdparm -d1 /dev/hda command no problem and its set, but after a reboot it reverts back to "off" even with the saved hdparm.conf file I have above. 
I've combed over the boards multiple times looking for a solution to my problem. :confused: Any help would be much appreciated. Thanks in advance

---

### Post by mcmuffy on 2005-11-29
> 
/dev/cdroms/cdrom1 {
dma = on
interrupt_unmask = on
io32_support = 0
}

This is the section from my hdparm file :

/dev/cdrom0 {
    dma = on
    }
command_line {
    hdparm -d1 -E32 -X34 /dev/cdrom
    }

My drive is a pioneer 108 DVD burner if that helps.

---

### Post by madmusiq on 2005-11-30
[QUOTE=mcmuffy]This is the section from my hdparm file :

/dev/cdrom0 {
    dma = on
    }
command_line {
    hdparm -d1 -E32 -X34 /dev/cdrom
    }

My drive is a pioneer 108 DVD burner if that helps.[/QUOTE]

I see one thing possible wrong with my hdparm file where I have
/dev/cdroms0 <-----
instead of 
/dev/cdrom0

I also see you have added the the command_line code as well to your hdparm file, setting the dma mode to "one" and setting the speed to "32". I don't think I'm gonna play with the IDE Transfer mode option though. I'll see if the changes make any difference.

---

### Post by madmusiq on 2005-11-30
Ok. I've made the changes to my hdparm.conf file to reflect the following:

/dev/cdrom/cdrom0 {
        dma = on
        interrupt_unmask = on
        io32_support = 0
}
command_line {
hdparm -d1 -k1 /dev/cdrom
}

/dev/cdrom/cdrom1 {
        dma = on
        interrupt_unmask = on
        io32_support = 0
}
command_line {
hdparm -d1 -k1 /dev/cdrom1
}

/dev/hda {
        mult_sect_io = 16
        write_cache = off
        dma = on
}
command_line (
hdparm -d1 -k1 /dev/hda
}

/dev/hdb {
        multi_sec_io = 16
        write_cache = off
        dma = on
}
command_line {
hdparm -d1 -k1 /dev/hdb
}
#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

DMA still resets to "off" after a reboot. Does anyone have any answers???
The drive is a NEC IDE DVD Burner -Model # 3540A.

---

### Post by madmusiq on 2005-11-30
anybody got any answers on this. I'm stuck.

---

### Post by madmusiq on 2005-11-30
:confused:

---

### Post by davidswe on 2005-12-02
I used to have playback problems with my DVD drive. Here's how I got dma to stay on after a reboot. I got these from other threads I've found. It works!

**VIA Chipset:**
Add via82cxxx to your /etc/modules file before ide-cd.

**nForce Chipset (and amd):**
Add amd74xx to your /etc/modules file before ide-cd.

**Whichever chipset you have, just put the new module as the first line**
**Reboot after you've edited your/etc/modules file**

**Then, open a terminal and enter the following:**

sudo hdparm -d1 /dev/cdrom
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf

[B]Append the following lines at the end of file
[/B]
/dev/cdrom {
       dma = on
}

---

### Post by mgmiller on 2005-12-02
This is what I had to do to get DMA to stay after rebooting:

You need to edit /etc/modules  to prevent certain kernal restrictions from loading at boot.  These restrictions were put in for greater compatibility with older non-DMA compliant disk drives.

1)sudo gedit /etc/modules
2) comment out using # all lines beginning with ide
3) It should look similar to this:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#ide-cd
#ide-disk
#ide-generic
lp
mousedev
psmouse
sbp2
sr_mod

4) save file
5) reboot

After doing this and editing the /etc/hdparm.conf file, I had DMA all the time.

:cool:

---

### Post by madmusiq on 2005-12-02
Thanks for the help everyone.
I got real desperate and decided to just do a clean install on my system.
Now my primary drive " /dev/hda " will stay enabled, but my secondary "/dev/hdb" still will not keep dma enabled.

My /etc/modules file only has the following information:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse


That's it; no stuff about IDE.

And David
What is this you are instructing me to do....
VIA Chipset:
Add via82cxxx to your /etc/modules file before ide-cd.

What exactly do you want me to add???? I'm new to the linux.

---

### Post by davidswe on 2005-12-03
When you edit your /etc/modules file, make the top line read "via82cxxx" if your chipset is via based. (or amd74xx if your chipset is NForce)

---

### Post by madmusiq on 2005-12-03
I'll give it a whirl. 
At this point I think having my primary drive keep its settings is the best I can do.

---

### Post by 3nric0 on 2005-12-07
[QUOTE=madmusiq]I'll give it a whirl. 
At this point I think having my primary drive keep its settings is the best I can do.[/QUOTE]

Had the same problem I resolved it in this way.

checked my settings with
$ sudo hdparm /dev/hd*
two devices had dma off

********
/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
********

opened hdparm.conf
$sudo gedit /etc/hdparm.conf

it was completly commented so I hadded this lines


/dev/hdc {
	dma = on		   
}

/dev/hdd {
	dma = on		   
}

saved and reboot.
all dma were on.

Note that I think is better identify hd and cdroms with base devices (/dev/hda, /devhdb, etc) as they should be the same for almost all the distros, while links (like /dev/cdroms/cdrom0) change with different distros and kernels.


If still doesent work chek if in hdparm.conf there are others params that override them and get them to order 
post it to me if you like

---

