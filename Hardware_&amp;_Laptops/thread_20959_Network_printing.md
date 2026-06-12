---
title: "Network printing"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by sargek on 2005-03-19
This question has been asked many times, but I cannot find a solution. I am very impressed with Ubuntu, except for printing. I have been totally unable to print anything to my network printer. Here is my configuration:

Samsung ML1740 laser on a Netgear printserver hooked to my router. The printserver has it's own IP address and all the Windows machines can print to it. I am using the Gnome print config tool to configure the printer and have also tried the cups web interface. I set the printer connection type to "UNIX (LPD)" and have the Host set to the IP address of my print server. The Queue is the name of the print server. This configuration has worked on all other Linux distros I have run in the past, so I know it is not the configuration.

When I attempt to print a test page, absolutely nothing happens. The queue will show the job, but it just sits there. I am very frustrated and really don't want to abandon Ubuntu because I am very impressed by the distro overall. Printing is an absolute must for me and is a very basic service. I have over seven years of Linux experience, so am not new to this. Can anyone shed some light on this problem? Thanks in advance.

---

### Post by sargek on 2005-03-26
Nice to see someone has taken the time to at least answer me <sarcasm>. I at least got a response in the Debian forums. I love the distro (Ubuntu), but this community doesn't seem to be too dynamic. If I am able to solve my problem, I will post the solution so others may benefit.

---

### Post by kleeman on 2005-03-26
A couple of suggestions:
1) look in /var/log/cups/error_log and see if there is anything useful.
2) Install kcontrol from universe in warty or from the standard place in hoary (part of kubuntu). The printer install wizard in kde is very extensive and has a network printer scan option that looks over your lan. kprinter accesses this wizard directly.

---

### Post by sargek on 2005-03-27
[QUOTE=kleeman]A couple of suggestions:
1) look in /var/log/cups/error_log and see if there is anything useful.
2) Install kcontrol from universe in warty or from the standard place in hoary (part of kubuntu). The printer install wizard in kde is very extensive and has a network printer scan option that looks over your lan. kprinter accesses this wizard directly.[/QUOTE]

Thank you for posting, I appreciate it. I have set the log level in /etc/cups/cupsd.conf to "debug" so I would get the most descriptive output possible. I have not had a chance to really decipher the output yet, but I'll do that in the next couple of days. If I install kcontrol, don't I have to install all of kdelibs or other kde associated files? I would really rather avoid that if possible as I am not a kde user. If it helps me solve this problem, I may consider it though, because I am pretty stumped at this point!

---

### Post by kleeman on 2005-03-27
No sorry you do have to install some kde stuff to get kcontrol but I can vouch for the kde printing wizard, it has helped me solve many a nasty printer problem in linux.

---

### Post by dcraven on 2005-03-27
Keep in mind that those kdelibs can quite easily be erradicated after you are finished with the tool.

As for the problem at hand, deciphering the error log is a very good start.

~djc

---

### Post by clb137 on 2005-03-27
Hi Kleeman,

Please tell me are your trying to print on a Linux Net or a windows net?   Is the printer connected to a linux box or a windows box.

Let me know your configeration and set up I have done a far bit with setting printers.

Clinton

---

### Post by sargek on 2005-03-27
[QUOTE=clb137]Hi Kleeman,

Please tell me are your trying to print on a Linux Net or a windows net?   Is the printer connected to a linux box or a windows box.

Let me know your configeration and set up I have done a far bit with setting printers.

Clinton[/QUOTE]

I am trying to print to a Netgear print server (PS121) which is on my router and assigned a static IP. I have set the print server up with the included software on my windows laptop, assigned it a server name and queue name. All of the windows machines can print to this printer (and see it) without any problems. The printer is hooked to a usb cable which is hooked to the print server. I have set up the printer in Ubuntu using the Gnome printer configuration tool using Unix LPD, the IP address and queue name I set for the print server.

What happens is when I print a test page, the printer starts "spinning up" but the light, which normally blinks when a job is sent, stays steady. The Gnome printer config tool printer queue shows a job in the queue. The printer stops "spinning up" and the job stays in the queue for a couple of minutes and then drops out.

I have tried [http://ip](http://ip) address, ipp://ip address with no success. Only the lpd:// set up will at least allow me to "talk" to the printer, although that doesn't work either. I have tried restarting cups (/etc/init.d/cupsys restart) after each configuration change. I have tried using another .ppd file (ML 1750, plxmono), the raw printing driver, and those don't work either - same results.

I resorted to moving the printer back to my desk and hooking it up to the parallel port on my Linux box. That works! I now have the printer hooked to the LAN for all of the windows machines, and hooked to the parallel port for my machine. Not exactly the solution I was looking for, but it works. 

The only other thing I can think of is this print server may not be compatible with Linux for some reason. It is just seen as an IP address, so that doesn't really make sense to me, but I can't think of anything else. Even though it is working from the parallel port, I am still interested in seeing if I can get it working via the LAN. I can provide the output from /var/log/cups/error_log is necessary - I have the log output set to "debug" for testing purposes right now. Thanks for the reply, I appreciate it.

---

### Post by clb137 on 2005-03-27
Hi,

can you ping the print server from the linux box?


clinton

---

### Post by sargek on 2005-03-27
[QUOTE=clb137]Hi,
can you ping the print server from the linux box?
clinton[/QUOTE]

It pings just fine. My system "sees" the printer, it just won't actually send a print job. Very strange.

---

### Post by clb137 on 2005-03-27
HI,

Do you have any firewall software running on your linux box? Also can see and share the files on your windows machines via Samba (SMB)?


CLinton

---

### Post by sargek on 2005-03-27
[QUOTE=clb137]HI,
Do you have any firewall software running on your linux box? Also can see and share the files on your windows machines via Samba (SMB)?
CLinton[/QUOTE]

No firewall software and I just installed samba recently, but haven't been able to get it to see the windows machines yet. I haven't done any configuration outside of what apt-get does though - it has not been a priority yet.

---

### Post by clb137 on 2005-03-27
HI,

Maybe Linux is treating your priint server as a windows machine.  Try to configure Samba,  the easiest way is to install ''webmin'' and ''samba webmin''  or if you are happy enough just edit the 'samba conf' file

good luck

clinton

---

### Post by sargek on 2005-03-27
[QUOTE=clb137]HI,

Maybe Linux is treating your priint server as a windows machine.  Try to configure Samba,  the easiest way is to install ''webmin'' and ''samba webmin''  or if you are happy enough just edit the 'samba conf' file

good luck

clinton[/QUOTE]

The puzzling part about this is I had this setup working in Gentoo, before it died a nasty death.... :sad: I'll check out setting up Samba. I've used webmin to configure servers before so I am familiar with it. Thanks for your advice, I appreciate it!

---

### Post by clb137 on 2005-03-27
Hi,

Have a look at the following link in wiki hardware support maybe something in there?

[http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport)

clinton

---

### Post by sargek on 2005-03-28
[QUOTE=clb137]Hi,

Have a look at the following link in wiki hardware support maybe something in there?

[http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport)

clinton[/QUOTE]

I checked it out. I knew the printer was supported in Linux - that's why I bought it! They even advertise Linux compatibility on the box, and the driver CD has a set up script to install the drivers. Anyway, I ended up moving the printer closer to my machine and hooking it up directly to the parallel port. Now the windows machines can print via the LAN, and I can print through the parallel port. Not exactly the solution I was looking for, but at least I can print. Actually, my desk looks less cluttered now, so it's not a bad set up!  ;-) I would still like to figure out the LAN printing issue though, so when I get some time I'll post the debug output in /var/log/cups/error_log.

---

### Post by mercurus on 2005-03-28
A few ideas:

- run nmap against the static IP you assigned to the Netgear printserver. If Netgear were kind, 631 would be open, and CUPS would detect the IPP device - sounds like they aren't very kind though. The other option is that 135/9 would be open, indicating (as does the Windows access) that the printserver is accessible with NetBIOS. That being the case, the advice about Samba is very pertinent. It would be perfectly acceptable to use Samba to access the Printserver - but obviosuly it would be preferable to have direct access.

- linuxprinting.org is a very good resource ... if this printer is badged as "linux supported" then these guys will know about it. What's more, they'll probably have a mailing list (and associated archive) dedicated to the manufacturer. Lots of good info to be had here.

- that CUPS log should be useful ... also check that /etc/cups/client.conf is looking at the correct IP.

Cheers
mercurus

---

### Post by sargek on 2005-03-28
[QUOTE=mercurus]A few ideas:

- run nmap against the static IP you assigned to the Netgear printserver. If Netgear were kind, 631 would be open, and CUPS would detect the IPP device - sounds like they aren't very kind though. The other option is that 135/9 would be open, indicating (as does the Windows access) that the printserver is accessible with NetBIOS. That being the case, the advice about Samba is very pertinent. It would be perfectly acceptable to use Samba to access the Printserver - but obviosuly it would be preferable to have direct access.

- linuxprinting.org is a very good resource ... if this printer is badged as "linux supported" then these guys will know about it. What's more, they'll probably have a mailing list (and associated archive) dedicated to the manufacturer. Lots of good info to be had here.

- that CUPS log should be useful ... also check that /etc/cups/client.conf is looking at the correct IP.

Cheers
mercurus[/QUOTE]

Here is the output from nmap:

Starting nmap 3.50 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-03-28 05:58 CST
Interesting ports on 192.168.0.8:
(The 1652 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
139/tcp  open  netbios-ssn
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect

Nmap run completed -- 1 IP address (1 host up) scanned in 0.830 seconds

Looks like 631 is open. Deepening the mystery!

---

### Post by mercurus on 2005-03-28
Ok ... what is in /etc/cups/client.conf ..?

Personally, I'd change whatever is in client.conf to use 192.168.0.8
Then restart cups, and use GNOME-cups-manager to have a look around the LAN.

Otherwise ... have another look at the jetdirect driver, samba ... or work out what protocol is on 515 ...

Cheers
mercurus

---

### Post by aaguiar on 2005-04-01
Hi

I'm new in the linux arena and I got the very same problem, for me the solution was to  declare the printer like this socket://xxx.xx.xx.xx

I hope it's work

---

### Post by reticular on 2005-04-11
I'm having a similar problem. I'm using a LPV2-USB-TX1 USB print server from Buffalo Tech. It has a static IP and works fine from other computers on the network. But I cannot get ubuntu 5.04 to print to it at all. The printer is a Laser Jet 1012. It works fine with ubuntu when printing from a local USB port .  

I am able to ping the printer. nmap report all ports are closed (though other computers don't seem to mind). Ive tried setting it up as a CUPS printer and a UNIX printer all with the same result: nothing, no error message, no timeout, and no paper coming out of the printer.

=== /var/log/cups/error_log

I [11/Apr/2005:13:00:04 -0700] Job 16 queued on 'LaserJet 1012-1' by 'me'.
I [11/Apr/2005:13:00:04 -0700] Started filter /usr/lib/cups/filter/pstops (PID 17952) for job 16.
I [11/Apr/2005:13:00:04 -0700] Started filter /usr/lib/cups/filter/foomatic-rip (PID 17953) for job 16.
I [11/Apr/2005:13:00:04 -0700] Started backend /usr/lib/cups/backend/lpd (PID 17954) for job 16.

Any help would be greatly appreciated.

---

### Post by sargek on 2005-04-11
Well, I solved the problem, but not in the way I would have liked: I moved the printer and hooked it up via the parallel port. It is now hooked to the LAN for everyone else and the parallell port for me. Not exactly what I wanted, but I can't get it working any other way. Thanks for the suggestions anyway, everyone, I appreciate it.

---

### Post by kuleali on 2005-04-12
:)

---

### Post by N6546R on 2005-09-08
I have a similar setup, Kubuntu 5.0.4, PS121 serving an Epson Photo 820. I saw the same problem after setting up the printer in kcontrol...the job would start, finish, and nothing would come out of the printer.

I installed gnome-cups-manager and set the printer up using it. I chose Unix printer (LPD), and the Host and Queue are set to the ps121 server IP and the print queue on the ps121.

This worked fine. Don't know if a package was missing before I installed gnome-cups-manager, or if there's some other setting that's slightly different, but whatever it is it now prints. The config file (/etc/cups/printers.conf) looks just the same as it did after trying with kcontrol.

Perry

---

### Post by mdm230 on 2005-12-22
Thanks Guys!

Unix printer:

host = ip address
queue = print_server_name\printer_name

mmc

---

### Post by allensco on 2005-12-24
I use an SMC Barricade 4 port router with built-in print server.  My Epson Stylus Color 600 works fine when printing from my Ubuntu computer.
Using the Gnome printer setup from: System > Administration > Printing.
First, select the UNIX/LPD printer option, then put the IP address of the router in the host box.  Then add LPT1 in the Queue box.  Follow the prompts through then send a test page.  It should starting working. :D 

Host: 192.168.2.x
Queue: lpt1

Hope this helps someone!

I have an Epson Photo 825 hooked up to a Windows 2000 box by USB.  I am, so far, unable to get the Ubuntu computer to print to it.  I have Samba installed and have tried many options with no luck.  Anyone have a fast fix for this?

Thanks!
Allen

---

### Post by Sebby on 2005-12-25
Great thread. I've been trying to get my Brother MFC-3820CN printer to work over the network. Changing to UNIX Printer (LPD) seems to have the done trick.

Merry Christmas. :)

---

### Post by nonemlinus on 2006-01-13
I just got my ps121 working...it was not easy and this thread certainly helped.

I'll add some details about the ps121's setup (which 
have been, completely nonlinear...so, I hope this reads clearly...).

Also, I have a Epson Stylus C88 (which works well with the C84
gimp-print driver...it's officially supported by gutenprint 5.0.0 rc2 which I haven't played around with in Breezy...maybe a backport will happen...) and I
have a Netgear wgt624 (hardware version v1).  I don't know if that helped
things along with the print server but, I suspect it did.
And finally, I have my router set up as a DHCP server.

First, make sure you're printer is 'supported' by the ps121 (and by linux of course).
Here's a link to Netgear's latest list (dated Nov.14, 2005 I think)
[http://kbserver.netgear.com/kb_web_files/n101216.asp](http://kbserver.netgear.com/kb_web_files/n101216.asp)

Before you start, make sure you update the firmware of 
the ps121.  [http://kbserver.netgear.com/support_details.asp?dnldID=858](http://kbserver.netgear.com/support_details.asp?dnldID=858)
The last update apparently was on Oct.12, 2004 for version 6033.
I was surprised that even though I just bought my ps121 a week ago, it came
with the older version of the firmware.  Also, you will need a windows machine
to do the update on....

During the initial setup of the ps121, your router will give it an ip address.  
Make sure to reserve that address in your router.  Do not remove
the ps121's new address from the range of ip address your router
gives out.

Then on your ps121, make sure you enable 'DHCP client'.
No ip address should be specified on your print server.  Also, make sure
you don't change the default name of the print server...this seemed to 
mess things up for my home network (windows clients could print to the
printer but, linux had a difficult time...).  And finally, I specified RIP Direction
(outbound only) and Version (RIP_1) on my router (I did this when I was trying 
to rename the print server.  Once all platforms were printing correctly, I was 
to afraid to change it back...RIP broadcasts host table information to other routers...I'm not sure the print server recognizes the protocol but, for
a while it seemed to get the name change across...)

Finally, I set up cups (actually ubuntu did it for me... :))
and I can print to my printer with  lpd://<ps121 ip>/P1

And, one last thing, the ps121 gets a little warm but, I
keep mine suspended in the tangle of wires behind my desk
which I think manages the temp well...

---

### Post by Michael Steinberg on 2006-01-17
On both my Macs and my Ubuntu laptop the way I set up my PS121 was simple: Unix LPR/LPD Printer, ip address is the ip address (duh) and the queue is the name of the print server--but with _P1 added. (That is, my server is called, unimaginatively, "MSERVER", and the queue in both Unix/Linux systems is called "MSERVER_P1")

I found the _P1 trick through Google; Netgear won't admit to it. Apparently CUPS sees the server but not the printer port on the server, which is P1--that's why you have to specify it.

And I'm using a Brother HL-1440, which is not on the official Netgear list, with no problems so far.

---

### Post by wacole on 2006-03-22
Thank you mdm230 ... the message about the format of the Unix printer dialog box did the trick for me (I had the entries reversed ... go figure).   Have been wrestling with network printing w/Linux forever and this is the first time that I have gotten it reliably working with my HP Laserjet 4L (can you believe I've still using one of those babies?).  Now I've just got to tweak the setting somewhere to get the header and footer to print when printing web pages.  One problem at at time.  Great thread.

---

### Post by lonniehenry on 2006-06-22
Thanks mdm230 also,
your information about the netgear ps121 unix info cured my problems.

host = ip address
queue = print_server_name\printer_name

I have two ubuntu machines, a mac lappy, and a couple of visitors who use ubuntu. My wife, the mac user complained greatly that she had to evoke the gods to make my printer work before the netgear was set up, is especially happy.

I'm fairly new to Ubuntu. Just nuked my last windows machine.

---

### Post by sargek on 2006-08-16
I'm not using Ubuntu anymore, but I hope this thread I started a year ago will help! I have the same Netgear server others have here, so will try the queue syntax mentioned above.

---

### Post by sargek on 2006-08-17
Syntax for lpd://xxx.xxx.x.x/queue was fine. This confused me: "queue = print_server_name\printer_name", but I think what was meant was "print_server_name" OR "printer_name". Using the print server name still did not work, but updating the .ppd to a recent one on Samsung's site did. Printing works fine now.

---

### Post by bigken on 2006-08-17
> **Sebby said:**
> Great thread. I've been trying to get my Brother MFC-3820CN printer to work over the network. Changing to UNIX Printer (LPD) seems to have the done trick.

Merry Christmas. :)

Hi take a look at this and you sould be able to setup your scanner also


[http://www.ubuntuforums.org/showthread.php?t=105703](http://www.ubuntuforums.org/showthread.php?t=105703)

this is a great thread for brother mfc printers ;)

---

### Post by kenmar on 2006-08-20
Hi
Here's a more or less general reply on the subject of using a hardware printserver.  I have a Netgear FR114P router with firewall and print server. I'm running Ubuntu 6.06.  Under 'printing' I checked 'detect LAN printers'then add new printer.  In that dialog I selected Unix printers LPD and for host  192.168.0.1 --the Netgear default-- for queue I entered FR114P. Apparently cups needs the name of the router/printserver as the queue name. I selected my Epson printer in the next dialog, and then 'apply' When I clicked on print test page it printed the Ubuntu test page perfectly.  This same setup worked on Mac OSX as well.  Now I print from XP, two Ubuntu boxes and a Mac and it all works.  Hope this is usefull.
Ken

---

### Post by Derspankster on 2006-08-21
I am having exactly the same type of problem with my HP 5P and a Linksys print server. 4 machines on my network, 3 XP boxes and 1 Ubuntu 6.06.1 box. All can print but the Linux box. I'm still working on it but haven't read/received anything that fixes the issue.  If I do, I'll post the fix.

---

### Post by Derspankster on 2006-08-21
Problem solved! Found this reply in another thread and this has solved my problem:

Hi
Here's a more or less general reply on the subject of using a hardware printserver. I have a Netgear FR114P router with firewall and print server. I'm running Ubuntu 6.06. Under 'printing' I checked 'detect LAN printers'then add new printer. In that dialog I selected Unix printers LPD and for host 192.168.0.1 --the Netgear default-- for queue I entered FR114P. Apparently cups needs the name of the router/printserver as the queue name. I selected my Epson printer in the next dialog, and then 'apply' When I clicked on print test page it printed the Ubuntu test page perfectly. This same setup worked on Mac OSX as well. Now I print from XP, two Ubuntu boxes and a Mac and it all works. Hope this is usefull.
Ken

The only difference for me was that I used my fixed IP address for the printer not the printserver default. Works perfectly!

---

### Post by mepaco on 2006-09-10
Just in case this happens to anyone else.  I have a PS121 and initially tried to set it up with IPP.  Once I found this thread I opened the printer's properties, changed it to LPD using the information here, and ... nothing worked.  I also noticed that from then on when I opened the printer's properties the Queue name I entered had disappeared.

Anyway, I deleted the printer, restarted cups (*sudo /etc/init.d/cupsys restart*), added the printer as LPD (using server name for Queue), restarted cups again and everything worked fine.

-Paco

Using Ubuntu 6.06 LTS

---

### Post by Nickb-k on 2006-09-28
> **kleeman said:**
> A couple of suggestions:
1) look in /var/log/cups/error_log and see if there is anything useful.
2) Install kcontrol from universe in warty or from the standard place in hoary (part of kubuntu). The printer install wizard in kde is very extensive and has a network printer scan option that looks over your lan. kprinter accesses this wizard directly.

I have installed kcontrol, bu there is no option to scan for network printers that I can see.  If I go to Service Manager > KDE Print Deamon the Start and Stop buttons are not active.

am I missing something?

Thanks,

nick

---

### Post by Mapleman on 2006-10-02
Afternoon!

    Sargek's problem sounds very similar to my own. I recently installed Kprinter/control as an alternative printer wizard to set up my networked HP Laserjet 5n, Things seems like they were working ok at first, as I have the exact IP address of the printer to input when asked. There was some response on the other side as the printer turned on and was looking for "Tray 3" which does not physically exist. I changed to Tray 1 / Letter and tried this process again, this time no response whatsoever and now I am finding that the scanning for device is coming back as error/not found. I am not sure how to open or debug my error kprinter file, any sudo command help would be appreciated.

Thanks and have a good one eh!

Michael

---

### Post by lmarsh on 2007-01-07
A solution for Ubuntu 6.10 on Dell Dimension 521 (amd64), with a Samsung ML-1710 printer attached to a usb port on a Dell Dimension 4300 at 192.168.1.10:

I tried various suggestions above and messed with the cupsd.conf file without much success. The latter had worked for Ubuntu 6.06, using the suggestion at [http://varspool.blogspot.com/2006/07/fixing-cups-on-ubuntu-linux.html](http://varspool.blogspot.com/2006/07/fixing-cups-on-ubuntu-linux.html)

Finally looked where I probably should have looked first - the CUPS documentation at [http://localhost:631](http://localhost:631). The Add Printer dialogue there didn't work at first. However, there was a suggestion for the connection in the Ubuntu printers dialogue that worked using the original (default) cupsd.config installed with Ubuntu 6.10:

ipp://192.168.1.10/printers/ML-1710

By the way, Ubuntu 6.06 on a Dell Inspiron notebook ran the printer without any fuss at all.

Thanks to all you guys who have written on this - I learnt a lot from reading through the submissions.

---

### Post by srf21c on 2007-03-22
I was able to get my Brother HL-1440/Netgear PS121 combo working readily enough using the LPR method, but I am curious if there are any drawbacks to using LPR vs IPP (Cups).

According to this post: 

[http://www.usenetlinux.com/archive/topic.php/t-537256.html](http://www.usenetlinux.com/archive/topic.php/t-537256.html)

the "CUPS server on port 631 is alive and well" on the PS121, but I cannot find _any_ documentation about how to successfully configure a printer to work with it over IPP (not LPR)

---

