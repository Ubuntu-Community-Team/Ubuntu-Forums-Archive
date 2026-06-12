---
title: "Scanner only works when Logged in as ROOT"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by myke on 2008-02-10
Hi.   I haven't used my scanner since upgrading to Gutsy with a clean install.   I usually use XSane due to it having more options that Kooka.    My scanner is a Canon Canoscan Lide60.  It has always worked easily under Kubuntu no matter which program I was using.  However, when I went to use it last night, XSane did pick up the scanner then shut down.  I tried Kooka and it did the same with a KDE crash window.   No clue what the cause is.   It always worked fine before and I don't think it has anything to do with my scanner due to one odd fact.

That fact is, when logging into the GUI  as 'root',  both programs pick up the scanner and launch fully.   So it sounds like a permissions settings some where.   Do I possibly need to chmod some file or add my main login to another group??   I don't know why this would be an issue all of a sudden as it never has been since dapper but regardless, there is a problem.  I've often found that there are permission errors causing problems so I have root allowed to login under the GUI so I can check such things out.   Sure enough, when logging in as root, everything worked fine with this situation as well.

Any ideas as to what I might need to check, change, and/or fix to solve the problem?  I don't want to have to log our of my main id and into root just to use my scanner!!!   

UPDATE:  

I definitely think that it's a permissions error.  Unfortunately, as my scanner is connected via usb and not scsi, the permissions error is coming from somewhere else.   Here's the output when trying to locate my scanner via "sudo sane-find-scanner"

>   # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x221c [CanoScan], chip=GL841) at libusb:004:015
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

So I ran 'sudo scanimage -L' to see if my scanner was detected and it was. This was the output:

> 
device `genesys:libusb:004:015' is a Canon LiDE 60 flatbed scanner

[http://www.sane-project.org/man/sane-usb.5.html](http://www.sane-project.org/man/sane-usb.5.html)

I found a help section (link above) on usb scanners using the genesys backend that notes a problem with permissions but I can't figure out how to fix the problem according to what it says, which is:


> The permissions for the device files used by libusb  must  be  adjusted for  user  access. Otherwise only root can use SANE devices. For Linux, the devices are located in /proc/bus/usb/ or in  /dev/bus/usb,  if  you use  udev.  There  are directories named e.g. "001" (the bus name) containing files "001", "002" etc. (the device files).  The  right  device files can be found out by running scanimage -L as root. Setting permissions with "chmod" is not permanent, however. They will be reset  after reboot or replugging the scanner.

According to the output of sudo scanimage -L, the file pertaining to my scanner is located at: /dev/bus/usb/004/015   When I check the permissions of that file, it does note that it belongs to group "scanner" but it is also already set to read/write/execute for owner and group.

In my user group list, I am a member of: 
> 
adm, audio, cdrom, dialout, dip, floppy, fuse, haldaemon, lpadmin, myke, netdev, operator, plugdev, powerdev, root, saned, scanner, sudo, video

Other threads noted on this permissions type problem state that you need adm and admin groups to be in your list.   I suppose this could be part of the problem.   But every time I add admin in, adm disappears.   Then if I add adm group back in to my id, admin goes away.   It's like they both won't be groups I can be in at the same time.  I don't know why as others say you need both for full admin privileges. 

I do believe I have a permissions problem here but I can't figure out which file to fix.

I am o-ficially LOST!!!

---

### Post by myke on 2008-02-10
Well, I logged out and back in as root and managed to get it to accept my being in both the adm and admin groups.  So I'm in all the ones mentioned in other threads I'd need to be in to operate my scanner outside of the root login.   Still not working.

I have did a chmod to every usb bus file that is created when I plug in the scanner in one of two direct ports or in a port on my 7 port expander.   Still not working.

Funny ... never had this problem on any other previous version of K/Ubuntu.  Also of note ....  in the file */etc/udev/rules.d/45-libsane.rules*, my scanner (canon canoscan lide60) is listed as fully supported.   And again, it did work fine up until Gutsy.   It was always detected fine.  Which it is now as well ... just only when running root under the GUI or via terminal.  And that's just a big pain in the backside.

What could have changed between K/Ubuntu versions???

---

### Post by blackest_knight on 2008-02-12
hi thanks for your post it seems I am not alone with this problem. 
I have a multifunction printer hp psc2175 all in one. 
printing is fine however, what I really want is the ability to scan with it and that so far seems to be only as root. 
xsane will core dump if i run it as a normal user, scanimage --list-devices does the same however as root everything is fine and problem free.

Lets hope someone has an answer.

---

### Post by Orion2000za on 2008-04-07
just thought I would support you guys on this issue. I have exactly the same, a Canoscan Lide25 works super - as long as I do "kdesu Kooka" or similar. If I run it as my own user no detection.

And it worked best before Feisty. In Feisty it became necessary to run the "scanbuttond" command before using Kooka, now I also have to be root...

Sinclair

---

