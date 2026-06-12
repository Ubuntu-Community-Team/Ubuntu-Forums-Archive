---
title: "Asus P5K-SE, System Hangs When Restarting after suspend/resume"
date: 2008-08-21
forum: Hardware
---

### Post by airtonix on 2008-08-21
Hi, 

When I suspend & resume or hibernate&resume none of my sound applications produce sound. Sometimes the progress bar (which shows where abouts in the song we are) doesn't move.

The system also seems to freeze when I choose to restart during the same session.

$ sudo cat /sys/firmware/acpi/tables/DSDT > dsdt.dat &  iasl -d dsdt.dat & leafpad dsdt.dsl : 
 [http://paste.ubuntu.com/39571/](http://paste.ubuntu.com/39571/)

$ lscpi : 
 [http://paste.ubuntu.com/39572/](http://paste.ubuntu.com/39572/)

$ lshw : 
 [http://paste.ubuntu.com/39573/](http://paste.ubuntu.com/39573/)

As you can see i have found the thread ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249)) created by [TheAlmightyCthulhu]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=629419")  and have followed his instructions up to the point where I edit the dsdt with the changes he recommends : 
 [http://paste.ubuntu.com/39579/](http://paste.ubuntu.com/39579/)

I try to recompile it, but i get errors that he does not mention : 
$iasl -tc dsdt.dsl > dsdt-errors.txt
 [http://paste.ubuntu.com/39580/](http://paste.ubuntu.com/39580/)

Thank you in advance for any help and your time & patience.

---

