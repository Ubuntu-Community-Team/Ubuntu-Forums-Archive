---
title: "DMA Support"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by skwid on 2005-04-16
Guys, I've got an issue with Ubuntu...  I cannot seem to enable DMA on my cdroms.  I'm booting on a SATA hard drive and all is good there.  My CDROMS are on the IDE part.  I also have another Controller ITE8212F that has another hard drive on it.  I cannot mount it at all.  It doesn't even show up.  

I use hdparm to enable DMA on the cdrom and I get an operation not allowed error.  Same except I've done ALL of the tricks on here and linuxquestions to get it to enable.  I've re-arranged my modules.conf and still no luck?

Any advanced support would be awesome..

Thanks,
Skwid

---

### Post by heimo on 2005-04-16
What do you have in /etc/modules? And what is the chipset of your motherboard or the controller the CDROM is attached to? Point here is that you probably need the chipset drivers loaded (at boot time) to get the dma working.

What I did to get mine running in DMA mode, was to edit /etc/hdparm.conf (section with /dev/hda in my case), add /etc/rc2.d/S99hdparm symlink and adding via82cxxx to /etc/modules (EDIT: at the top of the file) as I'm using Via 8237 based motherboard. That's what was needed. 

Have you already tried all of this?

---

### Post by skwid on 2005-04-16
Here is what is in my modules files:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

mousedev
psmouse
sbp2
sr_mod
snd-pcm-oss
snd-azx
snd-mixer-oss
ide-core
ide-cd
ide-disk
ide-generic
lp
``` 

Here is my HDPARM:

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

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
``` 


My Motherboard is a Asus P5AD2 Premium.  It's a Intel 925x chipset with the ICH6 Southbridge.

Thanks!

---

### Post by heimo on 2005-04-17
This is at your own risk (I don't say that often, but this time this may screw up your boot process).

Put 'piix' before any IDE lines in *modules *and uncomment the section with hda in hdparm.conf.


/etc/modules
```

mousedev
psmouse
sbp2
sr_mod
snd-pcm-oss
snd-azx
snd-mixer-oss
piix
ide-core
ide-cd
ide-disk
ide-generic
lp 

```  

/etc/hdparm.conf
 ```
/dev/hda {
	mult_sect_io = 16
	write_cache = off
	dma = on
}


```

You should have symbolic link from /etc/rc2.d/S99hdparm to /etc/init.d/hdparm. If you don't have, do it using
 ```
sudo ln -s /etc/init.d/hdparm /etc/rc2.d/S99hdparm

``` 

You could try first just to *modprobe piix* to see what happens and *hdparm -d1 /dev/hda*, but that approach didn't work with me, I really had to reboot. :(

---

### Post by skwid on 2005-04-17
hemio, you are a genius.  It's working perfectly now.  DVD's are smooth and the system is much snappier.

Thanks a million!

---

### Post by colo on 2005-04-17
I'm having the exact same problem on a system boasting the i875-Chipset (ICH5 southbridge). I loaded piix, and every other ko necessary you could dream of to get DMA working on my IDE-Controller (I've run similar setups under other distributions without problems), but I can't get it to work the way i'd like it to have. hdparm -d1 /dev/hd? reacts the way it does when the appropriate module for one's IDE-Controller is not loaded.

SInce this is Linux, rebooting the box is not really an option just to see if it'd work the next try (I've modified my module autoloading configuration according to your recommendation by now).

Any other suggestions on how to solve this?

---

### Post by skwid on 2005-04-17
Follow the steps above exactly and you should be in business.   Oh, I also had to RE arrange my modules and put the ide ones towards the bottom.   Give it a shot.

---

