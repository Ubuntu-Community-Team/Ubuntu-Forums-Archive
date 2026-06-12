---
title: "HP USB printer works only with one notebook"
date: 2011-10-24
forum: Hardware
---

### Post by n2000 on 2011-10-24
0 down vote favorite
share [fb] share [tw]
	

I have an HP LaserJet P1005. Printer is connected by USB and configured with hplib driver. I have to notebooks running Ubuntu.

Notebook A
[LIST]
[*]Ubuntu 10.10
[*]After connecting printer is doing some initialization work
[*]Printing works without problems
[/LIST]
    
 
Notebook B
[LIST]
[*]Ubuntu 11.10
[*]After connecting printer is quite, no initialization
[*]No errors in syslog
[*]Print jobs are send to the printer but printer does not execute the jobs, no error popups or error messages in syslog
[*]After connecting the printer to notebook A and and back to notebook B printing works fine an notebook B
[/LIST]
    
Can you help me?

---

### Post by Flymo on 2011-10-24
Hello n2000 - I'm not an expert but have managed to set up a couple of HP printers in Ubuntu 10.04 and earlier versions without problems.

BTW, did you mean Ubuntu 11.10 for Notebook B?

One question to start with - do you have the HPLIP GUI installed as well as HPLIP?

I have found this useful in debugging a recalcitrant printer connection.

If it is not installed, you should be able to find it in Synaptic as 'hplip-gui' or you can try this in a terminal:

```
sudo apt-get install hplip-gui
```

---

### Post by n2000 on 2011-10-25
Hello Flymo - thanks for your quick reply!

installing hplip-gui doesn't help itself. But there is an option in th tool to install a "HPLIP plugin" to get the printer working. Installing the plugin with the hplip-gui doesn't weork, but you can install it manually. After installing the plugin, the printer works!

HPLIP Plugin Download:

[LIST]
[*]3.11.10: [http://hplipopensource.com/hplip-web/plugin/hplip-3.11.10-plugin.tar](http://hplipopensource.com/hplip-web/plugin/hplip-3.11.10-plugin.tar)
[*]3.11.7 for Ubuntu 11.10: [http://hplipopensource.com/hplip-web/plugin/hplip-3.11.7-plugin.tar](http://hplipopensource.com/hplip-web/plugin/hplip-3.11.7-plugin.tar)
[/LIST]

---

### Post by Flymo on 2011-11-17
Well done!

I'd have replied much earlier, but I've been traveling and have just recovered from a 10-day-long bout of the  [Dreaded Lurgi]("http://www.youtube.com/watch?v=DkjewEM0dmk").

Better now! :)

---

