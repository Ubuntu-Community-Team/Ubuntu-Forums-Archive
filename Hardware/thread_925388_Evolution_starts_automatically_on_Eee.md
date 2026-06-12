---
title: "Evolution starts automatically on Eee"
date: 2008-09-20
forum: Hardware
---

### Post by gibbsnich on 2008-09-20
Hi everybody,
I'm having a little problem with by Ubuntu configuration which I can't resolve in my own.
Everytime I disconnect my Eee from the power cable, Evolution starts up. I uninstalled Evolution, now everytime I disconnect the cable I get an error message saying that Evolution is not a valid name for an executable or something similar..
I checked the /etc/acpi and /etc/acpi/events directories for anything that starts Evolution based on ACPI events which seemed a good place to look. I clicked through the gnome dialogs (energy settings etc). I searched google and the forums. Ran out of ideas.

Any idea is very welcome!
Thanks in advance!

Michael

---

### Post by gibbsnich on 2008-09-20
$ tail -f /var/log/acpid
...
[Sat Sep 20 22:27:45 2008] received event "hotkey ATKD 00000050 00000002"
[Sat Sep 20 22:27:45 2008] notifying client 5224[111:123]
[Sat Sep 20 22:27:45 2008] notifying client 5331[0:0]
[Sat Sep 20 22:27:45 2008] executing action "/etc/acpi/mailbtn.sh"
...
 
'/etc/acpi/events/asus-mail' triggers '/etc/acpi/mailbtn.sh' ..

What's the prefered way to report this?

---

### Post by scottuss on 2008-10-21
Hi, I have the same problem I'm still trawling through the forums for other reports but the best thing to do would be for you to submit a bug report using Launchpad. If you go to [https://launchpad.net/](https://launchpad.net/) and get a Launchpad account you can submit bug reports for Ubuntu

---

### Post by kuruni on 2009-01-06
A post on [[COLOR="Blue"]http://forum.eeeuser.com/viewtopic.php?id=25877[/COLOR]]("http://forum.eeeuser.com/viewtopic.php?id=25877") helped me solve this problem:
```
sudo rm /etc/acpi/events/asus-mail
sudo /etc/init.d/acpid restart
```
See also: [[COLOR="Blue"]http://wiki.eeeuser.com/hardy_on_eee901[/COLOR]]("http://wiki.eeeuser.com/hardy_on_eee901").

---

