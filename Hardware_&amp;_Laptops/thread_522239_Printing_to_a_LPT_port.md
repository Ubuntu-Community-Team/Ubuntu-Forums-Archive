---
title: "Printing to a LPT port"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2007-08-10
I am probably going to need someone who has some old skool knowledge to help me with this one.
I am converting my office over to Ubuntu. We have some older legacy devices that should have no problem working whatsoever. The problem I am having is dumping raw text files in a script to the printer port.
In MS I would use the following command:

copy file*.txt lpt1

In my script I am using 

lpr file*.txt 

When I first used this I received the error that there was no default printing device. So I installed the closest thing to my printer ( It is a Oki ML 590, I installed the ML 320 - both are pretty much interchangeable ). In MS I had no printer driver installed for this printer.

I can print this way (lpr...) - as in a test page or a single file. But when I try to print multiple files ( as in lpr file*.txt ) it will only print one page and keep the rest in queue. 

This should be a fairly simple task in any *nix, I just can not find out a way to do it. I should not need to load any type of driver...I just need to dump text files to the printer port...the printer understands what to do with the data.

Any help would be greatly appreciated!

---

### Post by lsutiger on 2007-08-10
OK _ I figured a work around...but I am not sure if the security is safe or not. As it is only a parallel port and I only have one device hooked up to it, I am dumping everything to lp0. The thing that worries me is that I had to change the permission of that device so my user account could use it. As far as I can tell, there is no other way of sending raw data directly to the device...IOW my fingers and eyes hurt from googling! 

These print jobs happen while I am away from the computer, so I can not be there to enter a password.

Any input would be appreciated!

---

### Post by lsutiger on 2007-08-11
UPDATE: ok, even if I change the permissions, they do not carry over on reboot. It works wonderfully until the reboot.

In my google extravaganza, I found some ways to change this but it is a bit over my head at the moment ( talking about recompiling the kernel ). Is there anyone out there that can help me with this situation?? I really want to chane my office puter over, but can't until I get it to run the old batch files that the Windows system does at the moment ( which about 80% is printing raw text files )
Thanx!

---

### Post by ronny_d on 2007-08-12
... I am not sure whether this i s what you need though and not sure whether you may find in these documents the answer to your problem:

QUOTE
" [http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/printing.html](http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/printing.html)
[http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html](http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html)

You do not need to use Samba necessarily. You can let Windows also speak LPD or IPP. For LPD you need to download and install the so-called "Print Services for Unix" from Microsoft. Then you Windows clients can talk to your print server via LPD. On the server you need to activate the CUPS-LPD mini daemon then, as already shown above.

For IPP you choose in the Add Printer Wizard a network printer "on the internet". Choose the address:

http://<server name or IP>:631/printers/<CUPS queue name>

Note that with the Samba-less methods you cannot let your clients automatically download the Windows printer drivers from the CUPS server."

END QUOTE

taken from:
[http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_4_1](http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_4_1)
at
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

You see, i suppose all real geeks must be "out of town" and not near Ubuntu..., i suppose, because (i guess) they have nothing to look for on a forum like this, they know it all already and even it is what they like most and are best at... and (i guess) you so would not quickly find them here, they may be hanging around in some 'newsgroup' or a total different forum, else working their heads of somewhere else fixing some kernelbug or just working with another Linux distro than Ubuntu... 

Real geeks read manpages and understand them as most clear and go to newsgroups, if i am not wrong, they know where to find what they need. They were born to do that. 


As far as i could try to imagine your situation, i would go some place where i may  most likely find a geek and for a "printing issue" like yours i would go for a start to  
[http://linuxprinting.org/](http://linuxprinting.org/)
and look around at all their pages and tutorials and if still in need then, i would try to ask someone of Linux printing foundation and i would go anywhere where they may be...  to find the help i need or try to find a 'newsgroup' they maybe refer to in their pages somewhere. Someone outthere must know on the issue you describe and how to solve it.

---

### Post by ronny_d on 2007-08-12
P.S.: i also would like a tutorial at "Ubuntu--level" on how to recompile the kernel so i could turn off the usb_suspend very quickly that is of no use for my pc at all and so then i could work on with total different work (my own work) than computertechnical stuff. Yet  i do not even want to consider another computersystem than Linux at all.

---

### Post by lsutiger on 2007-08-12
Thanx for the input, but that is not what I am looking for. I posted at linuxprinting.org
And for some reason your links do not show on the post, but did in the email I was sent by the forum ?
Thanx again

---

### Post by ronny_d on 2007-08-12
Still unsure whether this could be what you are looking for:

QUOTE:
" Permissions on /var/spool/samba/ Get Reset After Each Reboot

Have you ever by accident set the CUPS spool directory to the same location (RequestRoot /var/spool/samba/ in cupsd.conf or the other way round: /var/spool/cups/ is set as path> in the [printers] section)? These must be different. Set RequestRoot /var/spool/cups/ in cupsd.conf and path = /var/spool/samba in the [printers] section of smb.conf. Otherwise, cupsd will sanitize permissions to its spool directory with each restart and printing will not work reliably. "

END QOUTE
taken from:
[http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#id394045](http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#id394045)

via:
[http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html](http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html)

via:
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

If this is not it for you either, wishing you all the best with this tough job anyway. Hope Linux Printing org can help you.

---

### Post by lsutiger on 2007-08-13
Thanx for the input, but I am not trying to do anything via samba.
For those who have come and read already, I will try to explain this again:

 I have a script, when I run via CLI it runs fine. I do need to use sudo in order to run this script as it accesses /dev/lp0. When I try to run the script with cron, it does not complete ( some of the script does complete...it completes up to the point where it accesses /dev/lp0), but I do not know why it does not complete. 

I have tried to setup root's crontab to run but it does absolutely nothing, with no error.

I have looked at syslog, but it just states that it ran. I have the output gong to and error file, but it is empty. Any ideas?

Thanx in advance!

---

### Post by lsutiger on 2007-08-13
Solution found while tinkering.

The actual code for printing directly to an LPT port is ```
cat > /dev/lp0

```
I am sure you can use another program other than cat, but the output is directed to /dev/lp0 (the line printer port). You need 'super user' privileges in order to access the /dev/lp0 as it is owned by root.

When you need cron ( which is the actual program that runs tasks ) to run as root, you need to set root's crontab (which is the information cron uses to run whatever you would like). This is the same as the Task Scheduler in MS.

The way I did it was by logging in as root by : sudo su
Then running: gnome-schedule (if you do not have this sudo apt-get gnome schedule), and setting up my task.

And now it works! :)

---

### Post by lsutiger on 2007-08-15
OK...It worked for a day :((

no I get an error stating Input/Output error when trying to access lp0....any ideas out there?

---

### Post by lsutiger on 2007-08-15
OK - For just the moment, I changed the ownership to my user name just to see if that would change anything ( and after a reboot).
Now I am getting the following error:```
bash: /dev/lp0: Device or resource busy
```

I am at a loss...why would it work for a while and suddenly stop? I tested the lpt port in Windows ( on dual boot ), and it worked fine.

Please help!
:)

---

### Post by lsutiger on 2007-08-16
bump

---

### Post by lsutiger on 2008-01-18
Bump

---

