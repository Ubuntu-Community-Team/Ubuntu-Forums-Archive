---
title: "Ubuntu hangs during boot on an Intel D510MO motherboard"
date: 2010-01-20
forum: Hardware
---

### Post by Xtyn on 2010-01-20
I've just bought a D510MO motherboard (intel atom 510 dual core, video GMA3150) and to my surprise, Ubuntu hangs during boot after grub. Any ideas are welcomed.

I'm booting off an USB stick, if it has any relevance.

---

### Post by oappi on 2010-01-20
I have the same problem with that motherboard (D510Mo)... but i suspect that it doesn't freeze, since pressing ctrl+alt+dell few times makes my computer give dvd out... (im trying  with usb dvd drive and usb sticks)

edit: and after dvd is out and i press enter computer restarts normally.

I have tested fedora, knoppix, opensuse and of course ubuntu and all have same problem. Maybe i will have to try windows next =(.
i will try again after a good nights sleep and with server versio of ubuntu... i suspect it doesn't work because of the gfx chip (GMA3150), but maybe it will work with out GUI. Hopefully they will add support later.

---

### Post by oappi on 2010-01-20
It seems that my D510MO started working after i installed bios update... 

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Desktop+Boards&ProductLine=Intel%c2%ae+NM10+Chipset+Family+Boards&ProductProduct=Intel%c2%ae+Desktop+Board+D510MO&OSVersion=OS+Independent](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Desktop+Boards&ProductLine=Intel%c2%ae+NM10+Chipset+Family+Boards&ProductProduct=Intel%c2%ae+Desktop+Board+D510MO&OSVersion=OS+Independent)

it might be kinda tricky to install with out cd/dvd drive or windows.

---

### Post by Xtyn on 2010-01-21
> **oappi said:**
> It seems that my D510MO started working after i installed bios update... 

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Desktop+Boards&ProductLine=Intel%c2%ae+NM10+Chipset+Family+Boards&ProductProduct=Intel%c2%ae+Desktop+Board+D510MO&OSVersion=OS+Independent](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Desktop+Boards&ProductLine=Intel%c2%ae+NM10+Chipset+Family+Boards&ProductProduct=Intel%c2%ae+Desktop+Board+D510MO&OSVersion=OS+Independent)

it might be kinda tricky to install with out cd/dvd drive or windows.

Oddly enough, puppy 4.3.1 works. I'll try the bios update.

---

### Post by MrQuiet on 2010-01-27
I experienced what could look like a hanging computer during the boot after installing Ubuntu 9.10 server 64-bit on the Intel D510MO. There where some indications of GRUB and some file system messages, then a blinking cursor and finally a black screen.

Fortunately i had installed SSH during install, so I tried logging in through SSH. Everything seemed to be up and running. That, and this thread, indicated a problem with the bios, graphics card and/or a driver issue, so I updated to the latest BIOS revision and that solved everything.

The self booting ISO-image, from Intel, with flash utility worked like a charm.

---

### Post by Xtyn on 2010-01-29
I've updated the BIOS and installed Lucid Lynx (alpha2) and it works. I don't know if Karmic would work or not, haven't tried it.

---

### Post by keithww on 2010-01-29
I updated my D510MO to the new BIOS and Ubuntu 9.10 (Karmic Koala) is now working. 


BIOS Update [MOPNV10J.&#8203;86A]
11/18/2009    
0154    
Latest    
BIOS

Thanks for all the help.

---

### Post by MrQuiet on 2010-01-30
Still, with the latest bios I'm having network issues. Very unstable link.

I'm researching into this problem before making my final install of the Hardy server and have found [this thread]("http://ubuntuforums.org/showthread.php?t=1022411") discussing how the wrong NIC driver module is being used by the kernel.

Without a stable network connection, to build and replace the module I had to get the latest NIC driver from Realtek, put it on a CD using a different machine and copy it to the new machine. Add the install CD as apt-get source and install build-essential and linux-headers. Then running the scripts that follow the Realtek driver download.

The change is not persistent for me, that's why I'm in research mode.

I'll report back when I've got this up-and-running.

---

### Post by bturrie on 2010-04-02
Similar issue running Debian Lenny. It hung during the boot process. I booted in single user mode and the system stopped on a complaint about a timing issue between the two CPUs. 

Anyway, I updated the bios and still no luck on my Debian Lenny system but it runs fine on my Kubuntu 9.10 machine.

---

### Post by Tom Mann on 2010-05-08
Last BIOS 14/04/2010 works perfect for me!

---

### Post by bihe on 2010-05-18
Have you tested WOL? I'm thinking of building a NAS using the D510MO where WOL is an essential requirement.

---

### Post by linutx on 2010-05-22
> **bihe said:**
> Have you tested WOL? I'm thinking of building a NAS using the D510MO where WOL is an essential requirement.
I too wanna build a poor man NAS with the Intel D510MO
please let us know if 

[LIST=1]
[*]the network is stable
[*]Ubuntu release you're testing the D510MO with
[/LIST]
 TIA

---

### Post by bihe on 2010-05-24
> **linutx said:**
> I too wanna build a poor man NAS with the Intel D510MO
please let us know if 

[LIST=1]
[*]the network is stable
[*]Ubuntu release you're testing the D510MO with
[/LIST]
 TIA

Not started yet but found this [blog]("http://blog.revald.dk/post/Intel-D510MO-as-a-server.aspx"). The guys are quite helpful: [see the comments]("http://blog.revald.dk/post/Intel-D510MO-as-a-server.aspx#id_a9367476-995b-41da-ac16-8f6864ada6c3")

---

### Post by linutx on 2010-05-31
> **bihe said:**
> Not started yet but found this [blog]("http://blog.revald.dk/post/Intel-D510MO-as-a-server.aspx"). The guys are quite helpful: [see the comments]("http://blog.revald.dk/post/Intel-D510MO-as-a-server.aspx#id_a9367476-995b-41da-ac16-8f6864ada6c3")
thanks for the info
I guess, I still have to wait for a 'go' from the missus:(
my NAS will be on 24/7, so some more confirmation that the NIC
is stable would be really nice

Alright, I've got the MO
After the bios update, the NIC seems to be stable
config.
D510MO
2GB DDR2
2TB spinpoint RAID1 (MDADM)
4GB usb flash drive (OS)
Apex MI-100
Ubuntu 10.04 server

---

### Post by jap1968 on 2010-06-29
I have a computer based on Intel d510MO. The computer has one module with 2GB of memory (DDR2 800) and a 2.5 inch disk with a size of 500GB.

I was suffering some problems, maybe due to bugs in BIOS. I updated to latest available BIOS ( 20100428 ) but I am still experiencing the same problems.

My computer runs Ubuntu Lucid 64 bits. Once started the system, everything works properly. I haven't suffered any problem at all with LAN.

The problems:

Sometimes, the computer hangs at boot time. Let's say that one out of ten times, I have to push the reboot button since the computer is unable to boot up.

Problems with the CPU temperature sensors: Sometimes the sensors give readings of about 70 Celsius degrees, when the real temperature is about 30 Celsius degrees. That seems to be related to something buggy in BIOS. You can find additional information on intel forums: [Erroneous CPU temperature readouts on D510MO]("http://communities.intel.com/thread/10614").

I am happy with my computer, but intel should pay more attention to users and fix these problems. I give the board an score of 8 out of 10.

---

### Post by linutx on 2010-07-13
FYI: new BIOS Update - Version 0303 - MOPNV10J.86A.0303.2010.0705.1202

---

### Post by vtnj on 2010-11-19
> **MrQuiet said:**
> I experienced what could look like a hanging computer during the boot after installing Ubuntu 9.10 server 64-bit on the Intel D510MO. There where some indications of GRUB and some file system messages, then a blinking cursor and finally a black screen.

Fortunately i had installed SSH during install, so I tried logging in through SSH. Everything seemed to be up and running. That, and this thread, indicated a problem with the bios, graphics card and/or a driver issue, so I updated to the latest BIOS revision and that solved everything.

The self booting ISO-image, from Intel, with flash utility worked like a charm.

Anyone have a link to this ISO?  Intel seems to love windows, but doesn't have much for details in getting their .BIO files running with anything but floppy discs.  

I've done a bunch of searching ...mainly finding more windows solutions and a headache.  Is there an easy way in Ubuntu to create a bootable CD that contains the FLASH2.EXE and the *.BIO file?

---

