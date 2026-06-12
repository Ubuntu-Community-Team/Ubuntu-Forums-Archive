---
title: "Udev rules for identical SATA CD/DVD drives"
date: 2014-10-31
forum: Hardware
---

### Post by vuitre_viejo on 2014-10-31
I'm using lubuntu 14.04, but this may apply to other releases. There are a number of posts related to this topic on various forums, with suggestions on how to deal with it. The basic problem is getting udev to recognize two or more SATA drives when the drive information string ($devnode) returned by the built-in ata_id program is identical in all respects. Aside from comment about why anyone would want/need two drives, most of them focussed on coming up with ways to find unique attributes or tag each device. 

Maybe I'm a flint-axe kind of guy, but, after fooling around with several approaches that didn't work and getting lost in the udev underbrush, it seemed to me there should be a simpler, more direct solution. The lubuntu system has a default udev rules file called 60-cdrom_id.rules that is very compact, and is executed prior to the 60-persistent-storage.rules. Thought that would probably be the best vehicle to apply a fix. Copied the file to /etc/udev/rules.d, got a listing of the ata_id program to see what it was doing, and came up with the following, which works (the appropriate symlinks appear in /dev, the "Disks" utility shows two drives with unique sr numbers, etc).

[COLOR=#0000ff]ACTION=="remove", GOTO="cdrom_end"
SUBSYSTEM!="block", GOTO="cdrom_end"
KERNEL!="sr[0-9]*|xvd*", GOTO="cdrom_end"
ENV{DEVTYPE}!="disk", GOTO="cdrom_end"

# get ata id $devnod for cd drives
KERNEL=="sr*", ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="scsi", ATTRS{type}=="5", ATTRS{scsi_level}=="[6-9]*", IMPORT{program}="ata_id --export $devnode"

#[/COLOR][COLOR=#0000ff][COLOR=#0000ff] append unique identifier to duplicate serial numbers[/COLOR]
KERNEL=="sr[0-1]", ENV{ID_SERIAL}:="$env{ID_SERIAL}-%n"

# set ID_CDROM flag
KERNEL=="sr[0-9]*", ENV{ID_CDROM}="1"

# media eject
ENV{DISK_EJECT_REQUEST}=="?*", RUN+="cdrom_id --eject-media $devnode", GOTO="cdrom_end"

# get device/media properties, lock tray for eject
IMPORT{program}="cdrom_id --lock-media $devnode"

# create unique links for drives
KERNEL=="sr[0-1]", SYMLINK+="cdrom%n", OPTIONS+="link_priority=-100"

LABEL="cdrom_end"
[/COLOR]
The rules are written for a system that has two identical "sr" drives of a particular kind. For other types of drives, the drive-id line, which is a copy of a line in the persistent rules, would be different. The line that appends a dash number to the existing serial number variable and locks that value down is the only unique feature, all the other lines are either variants or copies of the original entries in 60-cdrom_id.rules. 

This isn't meant to be a how-to, want to ask whether anyone sees anything blatantly bad about this approach, or can suggest ways to make it better. Do think it could be generalized to other types of ata drives. Perhaps the best fix overall would be for ata_id to flag duplicates, rather than doing so in supplemental rules. Noticed the "Disks" utility shows the same serial number for both cd/dvd drives, rather than the modified values of ID_SERIAL. It is either getting a serial number value somewhere else, or the ID-SERIAL value is being truncated.

In a related note, there's a reported bug in lubuntu 14.04 -- when disk media in a mounted cd drive is ejected, and another disk is inserted, a second instance of the drive appears in PCmanFM. Suspect the eject and lock lines in  cdrom_id.rules may have something to do with that. Does anyone know where I can get an up-to-date listing of the built-in cdrom_id program?

---

