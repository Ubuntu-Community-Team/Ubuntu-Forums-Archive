---
title: "xsane only runs as root"
date: 2009-08-19
forum: Hardware
---

### Post by philo565 on 2009-08-19
Ubuntu 9.04 works great except for one minor problem:

xsane only runs as root

I also have a Debian installation that did the same thing and all I had to do was put my own profile in the scanner group

Tried the same thing with Ubuntu but when running xsane it still gives me the "no scanner found" error

Googled and got many hits, but saw not one answer that addressed the isssue

Note: fwiw scanner is SCSI

---

### Post by philo565 on 2009-09-06
in the even someone else has a similar problem...
I got some help and it's now been sorted


the thread that solved it cut and pasted:




>>> >>> # permissions for HP ScanJet 5100C SCSI scanner
>>> >>> SUBSYSTEM=="scsi_generic",ATTRS{vendor}=="HP",ATTRS{model}=="5100c", 
>>> >>> NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner"
...

ATTRS{model}=="5100c"
is case sensitive.

>> >> /etc/udev/rules.d/45-scsi-scanner.rules
>> >> 
>> >> $ cat 45-scsi-scanner.rules
>> >> # permissions for HP ScanJet C5100A SCSI scanner
>> >> SUBSYSTEM=="scsi_generic",ATTRS{vendor}=="HP",ATTRS{model}=="C5100A",
>> >> NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner"
>> >> 
...
> > 
> > Well that did not work for me.

What is ATTRS{model} output from:

$ udevadm info -a -p /sys/class/scsi_generic/sg2

is it "5100c"? Or is it "5100C" or similar?

You previously wrote:
> > I have been unable to add the shell script to startup
> > as  it requires  a "sudo" and root password.
> > 

You might try again. My _guess_ is that the "5100c" may have been an issue.

---

