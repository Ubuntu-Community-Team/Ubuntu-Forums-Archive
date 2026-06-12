---
title: "Ubuntu 14.04 CUPS not working with HP Laserjet 4"
date: 2015-04-01
forum: Hardware
---

### Post by mark bower on 2015-04-01
System:  Ubuntu 14.04, Laserjet4P, Dlink DP-301P+ print server, Gnome Classic, CUPS 1.7.2.  The path from computer to printer: computer>wireless>router>wired> Dlink print server>plugged in>printer. 

I upgraded 12.04 to 14.04 and lost printer capability.  I have installed CUPS via Apps>Sys Tools>Sys Settings>Printing and [http://localhost:631](http://localhost:631).  In both cases the install appears normal and the printer(print server) is detected on the network.  But the printer will not respond even though it is seen by the system. 

There must a simple tweak that will solve the problem &#8211; what is it?

PLEASE REFER TO MY POST #11 WITH UPDATED INFORMATION.

---

### Post by dino99 on 2015-04-02
i've no clue with printers linked to a router; but as it is detected, then the fact it does not respond seems to be a port not opened. Is it a port on the router itself or into the firewall ? maybe check gufw and the logs to find a warning/error. You also can glance at /etc/rc?.d for possible broken link; if you find one, then delete it the next opened session will recreate the required link.

question: is the last cold boot old ? maybe a router reset can also help.

---

### Post by tgalati4 on 2015-04-02
Perform all the updates on 14.04, reboot.  Delete the printer.  Recreate the printer and try again.  Look through the log files in /var/logs/cups for errors.

---

### Post by mark bower on 2015-04-02
info playing off of suggestions:

I have another computer on the network that talks wirelessly to the router and the printer works - this rules out a router problem.  When I run UFW on each of the computers, there is a difference.  On the computer I am having trouble with there is an entry(shown below) of "disabled (routed)" which is not present on the working computer.  I played around with UFW and GUFW but could not figure out how to eliminate the "disabled (routed) entry.

rocky@mark:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), **disabled (routed)**
New profiles: skip

I could not figure out what to do regarding the /etc/rc?.d files?

I looked at the cups log after a couple of send attempts and everything appears to be normal? IE, it says send is successful, but in fact no printer output.
rocky@mark:/var/log/cups$ cat access_log 
localhost - - [02/Apr/2015:06:08:06 -0700] "POST /printers/Laserjet4P HTTP/1.1" 200 312 Create-Job successful-ok 
localhost - - [02/Apr/2015:06:08:06 -0700] "POST /printers/Laserjet4P HTTP/1.1" 200 1351 Send-Document successful-ok 

I updated and reinstalled the printer - no success with getting printer to print.

---

### Post by Vladlenin5000 on 2015-04-02
Have you tested without the firewall already? If it works you immediately know what to troubleshoot...

---

### Post by mark bower on 2015-04-02
I disabled the firewall and the printer does not print.  

Also, the printer has the check mark over it and a blue filled circle with an "i" in it.  What is the blue circle about?

---

### Post by Vladlenin5000 on 2015-04-02
Printer isn't correctly installed. Somehow it doesn't connect and, according to your latest info, it isn't firewall related.
Have you really removed and configured again that printer? If so, how exactly did you do it?

---

### Post by mark bower on 2015-04-02
I removed the printer by entering ..>System Settings>Printers, rt clicking the printer icon, then selecting delete.  Then I select the option to Add Printer, let it search and find the printer on the network, then select brand as HP and then the driver that has worked in the past.  I have also reinstalled the printer via [https://localhost:631](https://localhost:631)

And can you tell me what the blue circle is about?

What really seems strange is that the cups log does not indicate a problem with an error msg.

---

### Post by tgalati4 on 2015-04-03
Well, you can set the log level to debug or debug2 in /etc/cups/cupsd.conf.  Reboot or restart cups. Be sure to change it back because the log files will get large.

```
sudo service cups restart
```

---

### Post by Unterseeboot_234 on 2015-04-03
I just went through all this with a wireless connection getting lost. Letting CUPS or System Settings search for a printer seemed, to me, to be finding the deleted printer each time. Deleting the old printer in System Settings and using hp-setup in terminal set all the configuration files correctly the first time. Remember to select [x] Shared Printer in the printer description panel that comes up. The only bummer about hp-setup is it wants a direct cable to the printer during setup.

---

### Post by mark bower on 2015-04-06
I made a fresh install of 14.04 with updates, and installed gnome-session-fallback.  In every printer install attempt, the D-link P/S is identified on the network by its MAC code.  That is, Discovered Networks Printers = PS-DF6EC4-P1(prefix-partial MAC code-suffix).  And this recognition is what I always saw in the past from 12.04 and earlier, and the installs worked.

When I say installing the printer, I believe it may be more correct to say installing the P/S which is what is seen by the network, not the printer itself.  The Laserjet4 dates to 1993, but what a work horse.  Newest install attempts and order:
1) install printer via system settings - everything looks o.k. but msg is not sent to P/S.
2) uninstall printer via system settings
3) install printer at the CLI with system-config-printer - error msg is generated in the terminal, tho steps using the graphic respond normally.  Please see Post #12
4) uninstall printer via system settings
5) install printer via internet, localhost:631 - everything looks o.k. but msg is not sent to P/S.

I have looked at /etc/cups/printers.conf and cannot detect a problem.  I have played with "lpinfo -l -v", "lpsat -s", and "nmap -sP 192.168.1.0/24 and am not able to see clues(could very well be do to my experience level).

I realize there are other options to install using things like ipps,ipp,lpd/lpr, App/Socket/HP direct. However, I want to be able to install simply and easily as I have previously.  

Clearly the P/S is seen on the network.  What is the tweak I need to get things to work?

---

### Post by mark bower on 2015-04-24
Using the terminal to install the printer gives the following information for the successful install on my computer with 12.04 and the computer with 14.04:

> **COMPUTER WITH 12.04 - Installation successful**
rocky@mark:~$ system-config-printer
No ID match for device dnssd://PS-DF6EC4-P1._printer._tcp.local/:
MFG:;MDL:;
No ID match for device dnssd://PS-DF6EC4-P1._printer._tcp.local/:
MFG:;MDL:;
No ID match for device dnssd://PS-DF6EC4-P1._printer._tcp.local/:
MFG:;MDL:;
rocky@mark:~$ 

**COMPUTER WITH 14.04 - Printer will not install**
rocky@senior:~$ system-config-printer 
No ID match for device dnssd://PS-DF6EC4-P1._printer._tcp.local/: 
MFG:unknown;MDL:; 
Unknown value for media-col: (unknown IPP value tag 0x34) 
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type'] 
Selecting from choices: media-bottom-margin 
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 452 was not found when attempting to remove it 
  GLib.source_remove (self.populateList_timer)


And then a lot of foul lines when I attempt to print the test page 

So help please!

---

