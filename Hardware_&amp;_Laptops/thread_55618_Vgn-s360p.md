---
title: "Vgn-s360p"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by b3nw on 2005-08-09
Has anyone gotten the brightness or volume function keys working?
Thanks,
~Ben

---

### Post by raghav_p on 2005-08-09
for volume (at least in my laptop), go to System --> Preferences --> Keyboard Shortcuts and configure your keys there.

Brightness, I don't know

---

### Post by ilveroluca on 2005-08-13
I second that question.  I just bought a vaio s360.  

With kernel 2.6.10 (came with the installation) I had my function keys working.  They were generating ACPI events, so I configured them by adding scripts to /etc/acpid/events.  

Try this.  Open up a command prompt, type 
tail -f /var/log/acpid
(you may need sudo as well) and then press Fn+F1.  If you get a few lines saying 

received event "sony/hotkey SPIC 00000001 00000001"
completed event "sony/hotkey SPIC 00000001 00000001"

then you're in business.  If you're running KDE you can then use dcop to control any of the kde applications (e.g. KMix to control your volume).  You can also use spicctrl (in universe) to control your screen brightness.

If you don't see the ACPI events coming through, then you're in my position.  I upgraded to kernel 2.6.12 to get suspend-to-ram working, but I had to trade away my function keys :(

You may also be able to use [sonypid](http://popies.net/sonypi/).  If this option is viable for you I wrote a little program based on sonypid that reads a configuration file at start up and lets you map any event to an arbitrary shell command.  If someone is interested I can post it somewhere for download.

For me the problem with sonypid (and my program) is that it doesn't work when Klaptopdaemon is running---another trade-off.

If anyone else has any tips on what I can to do get my ACPI events working again, or how to get Klaptopdaemon to play nice with other applications that read from /dev/sonypi I look forward to hearing them.  Someone out there must have a vaio S with working function keys!

Luca

---

