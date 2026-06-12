---
title: "Physical Hardware Move"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by dave562 on 2009-09-25
I have an Ubuntu server that I have inherited and I need the box for something else.  What is the best way to make an exact copy of the installation on another piece of hardware?  I can't just drive copy it over because the box in question has a RAID array, and the box I'm moving it to just runs standard SATA drives.

Is the kernel going to completely freak out if I move it onto another box?

---

### Post by earthpigg on 2009-09-25
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

why this outstanding tool is not in the ubuntu repositories is beyond me.

it will turn your current install, including settings and custom configurations and whatnot, into an installable .iso.

---

### Post by raymondh on 2009-09-25
> **earthpigg said:**
> [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)


+1

---

### Post by dave562 on 2009-09-28
Thanks for the heads up about Remastersys.  When I try to apt-get install the remastersys package I get errors about broken packages.  It seems to be looking for two dependencies. dialog and squashfs-tools.  Both of those are listed as "not installable".

How did you guys get it to work on your systems?  Did you manually compile from source?

---

### Post by cariboo on 2009-09-28
Use gebi by double clicking the file, or you can install it manually using dpkg:

```
dpkg -i <packagename>
```

---

### Post by dave562 on 2009-09-28
I'm not using the GUI so I'm doing everything CLI.  When I try to use the dpkg command, it returns...

dpkg: error processing squashfs-tools (--install):
 cannot access archive: No such file or directory

When I try using apt-get to install the same package, it errors with.

Package squashfs-tools is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only avialalbe from another source
E: Package squashfs-tools has no installation candidate


I don't mind trying to compile from source but I haven't been able to locate the source files.  Any suggestions?

---

### Post by dave562 on 2009-09-28
Never mind, I sorted it out.  I just had to add a couple more repositories to the sources.list file.  It was setup to only pull security updates.

---

### Post by dave562 on 2009-09-28
I got remastersys working, but it turns out that it isn't the right tool for this job.  The server is question currently has 107GB of data on it.  I can't exactly burn that to an .ISO file and move it another box.

I do have a tape drive connected to the box.  I'm not clear on how to do a full backup and then bare metal restore on a Linux box.  I only need to "borrow" the hardware for about a week as part of a VMware rollout.  Then I can restore the system from the tape backup.

---

### Post by earthpigg on 2009-09-28
> **dave562 said:**
> I got remastersys working, but it turns out that it isn't the right tool for this job.  The server is question currently has 107GB of data on it.  I can't exactly burn that to an .ISO file and move it another box.

what if you use usb-creator to put that .iso onto an external USB hard drive?

(usb-creator = system -> administration -> USB Startup Disk Creator on a standard ubuntu install)

---

### Post by solitaire on 2009-09-28
> **earthpigg said:**
> what if you use usb-creator to put that .iso onto an external USB hard drive?

(usb-creator = system -> administration -> USB Startup Disk Creator on a standard ubuntu install)

with remastersys if the image is over 4Gb in size the program will fail at the point where it creates the ISO

Try doing a "Dist" or a "Distcdfs" that will get the system on to a disk you then can use a standard backup program to backup the data.

You then can use the Dist to install the base system and then restore the backup

---

