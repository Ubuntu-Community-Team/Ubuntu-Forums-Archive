---
title: "Printer no longer working in Xubuntu 16.04"
date: 2017-04-22
forum: Hardware
---

### Post by kesetyan on 2017-04-22
Hi,

My printer, a Canon Pixma iP4300, which was recognised and has been working, failed to work today.  

I am running an installation of Xubuntu 16.04 from a 16gb memory stick and all has been going well until today.  I tried several times to print a document but failed - an error message stated a filter was missing or unavailable.  I cleared the jobs backlog and tried again but with no success.  In desperation I removed the printer from Xubuntu and restarted the system in the hope that Xubuntu would recognise the printer once more as it had done when I first connected it but it did not.  I don't know if this is significant but if I attempt to visit the CUPs website 'localhost:631'* (as I have for Puppy Linux in order to set up the printer for that OS)*, the website appears unavailable - is it possible that 'localhost:631' is down and is required by Xubuntu in order to set up my printer once more?  If this is not the cause, what things can I try to re-establish my printer which has previously worked correctly on Xubuntu?

Thank you.

---

### Post by deadflowr on 2017-04-22
Moved to Hardware

Is cups running?
Open a terminal and run 
```
systemctl status cups.service
```
(that should be the command...)

---

### Post by ajgreeny on 2017-04-22
There was a bug in cups which meant it would stop after a few minutes, though I thought that had now been squashed.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300)

The way to work around this was to temporarily enable the Proposed repos, update the cups packages (easiest to do with synaptic package manager in my opinion), then immediately disable Proposed repos again.

I had exactly this problem which was very annoying and in my case was solved with the Proposed cups packages.

---

### Post by kesetyan on 2017-04-23
> **deadflowr said:**
> Moved to Hardware

Is cups running?
Open a terminal and run 
```
systemctl status cups.service
```)

Hi deadflowr,

Yes, cups appears to be running as shown in terminal text copy below:

```
chris@chris-HP-Compaq-dc7900-Small-Form-Factor:~$ systemctl status cups.service
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: ena
   Active: active (running) since Sun 2017-04-23 10:11:30 BST; 3min 35s ago
     Docs: man:cupsd(8)
 Main PID: 1980 (cupsd)
   CGroup: /system.slice/cups.service
           &#9500;&#9472;1980 /usr/sbin/cupsd -l
           &#9500;&#9472;1985 /usr/lib/cups/notifier/dbus dbus:// 
           &#9492;&#9472;1986 /usr/lib/cups/notifier/dbus dbus:// 

Apr 23 10:11:30 chris-HP-Compaq-dc7900-Small-Form-Factor systemd[1]: Started CUP
lines 1-11/11 (END)
```

'localhost:631' is still unobtainable on the internet - this does not seem to be a computer firewall issue as I have not altered firewall settings from when the printer was working normally.  'localhost:631' was also not available via Windows 7 which is the desktop I use when running Xubuntu from the usb memory stick installation.

---

### Post by kesetyan on 2017-04-23
> **ajgreeny said:**
> There was a bug in cups which meant it would stop after a few minutes, though I thought that had now been squashed.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300)

The way to work around this was to temporarily enable the Proposed repos, update the cups packages (easiest to do with synaptic package manager in my opinion), then immediately disable Proposed repos again.

I had exactly this problem which was very annoying and in my case was solved with the Proposed cups packages.

Hi algreeny,

I am very new to Xbuntu having only used it for a couple of weeks.  This is my first real problem but I can live without the printer as I can access it from other OSs.  I've installed the Synaptic package manager as you suggest that is the easiest to use so I will no try to get my head round the contents of the useful link you gave me and your 'Proposed repos' suggestion.

---

### Post by kesetyan on 2017-04-23
Hi ajgreeny and deadflowr,

Some good news, as a believer in try the simplest possible remedies first, I decided to reinstall CUPS as I wondered if possibly a file had become corrupted when I first encountered the problem when trying to print a document causing a backlog of jobs when I tried again after each failure.  Clearing the backlog by deleting all waiting jobs did not resolve the problem.  However, today I thought about trying the reinstall of CUPS so typed 'sudo apt install cups' into the terminal and pressed return - when I typed in my password and pressed return the reinstallation process began and completed fairly quickly (I ignored any options offered and confirmed I wanted to go ahead..  This was carried without any previous uninstallation of CUPS.  The result of all this was that the printer was recognised as soon as I turned it on and a test printwas successful.

---

### Post by deadflowr on 2017-04-23
> 'localhost:631' was also not available via Windows 7 which is the desktop I use when running Xubuntu from the usb memory stick installation.
Confusing.
But localhost should never be available to Windows.
Instead you would need to input the local ip address of the machine running cups.
(instead of localhost:631, you put in the LAN ip address typically something like 192.168.1.80:631; your ip and mileage may vary)

To explain, cups webpage is locally generated to the running machine.
It's not an external internet webpage per se, but a page running directly from your own machine.
Each machine runs it's own cups web page.
And that page is only accessible when that operating system is up and running.
And localhost is only available to directly from only that operating system, otherwise you need to use the ip address.
Does that make any sense?
(or help?)

---

### Post by kesetyan on 2017-04-23
> **deadflowr said:**
> Confusing.
But localhost should never be available to Windows.)

Hi deadflowr,

Your post must have crossed my last post - as you can see, my problem now seems resolved although I am not sure what caused the problem in the first place.  However your last post regarding CUPS is very useful to me and does explain a lot about CUPS that I wasn't aware of - yes, what you say certainly makes sense so thank you for explaining things so succinctly and understandably.

Cheers and best regards.

---

