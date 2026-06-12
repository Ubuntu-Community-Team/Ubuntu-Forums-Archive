---
title: "Canon PIXMA iP90v"
date: 2009-01-15
forum: Hardware
---

### Post by Norman Grahams on 2009-01-15
I'm unable to get my Canon PIXMA iP90v printer to work under Ubuntu (Intrepid - tried originally in Hardy).
[This thread]("http://ubuntuforums.org/showthread.php?t=662002") instructed me to get the driver and convert to deb with alien. Then I'm told 'Filter "pstocanonij" for printer "iP90" not available".
[This]("http://forums.linux-foundation.org/read.php?25,3367,3456,quote=1") had instructions on pstocanonij, including a link to another [Canon page]("http://software.canon-europe.com/software/0027215.asp"), seemingly equivalent to (but older than) [this one]("http://software.canon-europe.com/software/0027403.asp").
I get, as described in the first mentioned post, the printer not doing anything. I've noticed that the two Canon pages list supported products - not including this one. Maybe a different postocanonij is needed?

Does anyone have any ideas how to make this work? I'm fed up with rebooting into Windows to print, and I don't fancy migrating to SUSE just to have the printer working. Thanks.

---

### Post by Jammanuser on 2010-05-10
I have the same problem.
Running Ubuntu 9.10 i386 (32 bit), and am attempting to get the Canon ip90v printer to work from it. I read some of the other threads on here, which posters with the same printer started, and the advice is to put the file called "pstocanonij" in the usr/lib/cups/filter directory, and I have this file, but every time I try to copy it there, nothing happens. The "paste" command is greyed out, and I when try to drag it instead, an error pops up saying I don't have the priviledges.

I tried doing it through the command-line, using the cp program, but typing this command:

```
sudo cp ~/Desktop/Printer_Driver/pstocanonij usr/lib/cups/filter
```

produced the following error:
> 
cp: cannot create regular file `usr/lib/cups/filter': No such file or directory
which is nonsense, because the directory does exist. I'm thinking that its maybe because I'm at gorilla@gorilla-laptop (i.e. the /home/gorilla directory) when I run the command. However, even running this instead:

```
sudo cp ~/Desktop/Printer_Driver/pstocanonij ../~/usr/lib/cups/filter
```
wouldn't work.
So, next, i attempted to do it through the GUI again while I'm root in the terminal, but still the 'paste' command is greyed out.
Anyway, the error that I'm getting when I try to print from the Canon ip90v is different than the one posted in [this thread]("http://ubuntuforums.org/showthread.php?t=1200161").
My error says "cup-missing-filter".
Using the Printer Troubleshooter, the program reports the following:

> Server Not Exporting Printers

Although one or more printers are marked as being shared, this print server is not exporting shared printers to the network.

Enable the 'Publish shared printers connected to this system' option in the server settings using the printing administration tool. To start this tool, select System->Administration->Printing from the main menu.
which, again, is nonsense, since I'm not sharing the printer. Why would I be when I haven't even got it working yet? :P

Hopefully someone can shed some light on the matter.

Thanks in advance.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-05-10
Oh yeah, and I already installed the driver downloaded from the Canon website in an earlier thread on the same issue which I started:

[http://ubuntuforums.org/showthread.php?t=1446108](http://ubuntuforums.org/showthread.php?t=1446108)

---

### Post by Plexor on 2010-05-17
I have been having troubles getting my iP90v to work for a long time..  i had minimal success back in Hardy...

I put in a request for support:
[http://sourceforge.net/tracker/?func=detail&aid=2956503&group_id=1537&atid=351537](http://sourceforge.net/tracker/?func=detail&aid=2956503&group_id=1537&atid=351537)

In the mean time, I have been using VirtualBox to boot windows xp and then pass the USB to VirtualBox and print from there.  Kinda irritating, but at least it works and I don't have to restart.

---

### Post by Plexor on 2011-01-25
Anyone have luck getting the iP90 to work in linux?

I have had been able to print things using other drivers (ip2000, for example) but very limited functionality and the printing seems to be inaccurate.

---

