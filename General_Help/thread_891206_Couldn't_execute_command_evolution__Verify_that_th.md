---
title: "Couldn't execute command: evolution  Verify that this is a valid command"
date: 2008-08-15
forum: General Help
---

### Post by kieonsegg on 2008-08-15
Couldn't execute command: evolution 
Verify that this is a valid command

Thats the error message i get
i run it in terminal and it says i dont have it installed
it only pops up when i plug my ac adapter into my eee pc

Checked system>sessions
i deleted somehting called evolution update, but that didnt help

Totally confused

Thanks

---

### Post by picpak on 2008-08-15
Going down the obvious route here...

do you have Evolution installed?

```
sudo apt-get install evolution
```

---

### Post by y@w on 2008-08-15
> **kieonsegg said:**
> 
i run it in terminal and it says i dont have it installed
it only pops up when i plug my ac adapter into my eee pc


Does this mean you can run Evolution when the machine is not plugged in to the AC power??

---

### Post by kieonsegg on 2008-08-15
> **y@w said:**
> Does this mean you can run Evolution when the machine is not plugged in to the AC power??

I dont have evolution if u read my post correct. Whenever i plug in the power cord i get the message about evolution even tho i dont have it installed. I think its just on my plug-in programs or somehting like that.

---

### Post by kieonsegg on 2008-08-15
> **picpak said:**
> Going down the obvious route here...

do you have Evolution installed?

```
sudo apt-get install evolution
```

If you read my post correctly, i do NOT have it installed.

---

### Post by picpak on 2008-08-15
> **kieonsegg said:**
> If you read my post correctly, i do NOT have it installed.

If you go to Applications > Accessories > Terminal and run the command I gave you, it will install it for you. :)

---

### Post by kieonsegg on 2008-08-15
> **picpak said:**
> If you go to Applications > Accessories > Terminal and run the command I gave you, it will install it for you. :)

Ughhh im trying to get rid of it! Not install it! I dont need to waste all the space it takes up to cuz it has like 20 dependencies

---

### Post by y@w on 2008-08-16
> **kieonsegg said:**
> Ughhh im trying to get rid of it! Not install it! I dont need to waste all the space it takes up to cuz it has like 20 dependencies

Easy there killer. We're trying to help. All you said was that it happens whenever you plug your AC power in and that you tried to delete "somehting called evolution update, but that didnt help". If we don't get specifics, we're going to try to start narrowing down what's going on, starting with the most obvious.

Here's someone else with an Eee PC with the same problem: [http://forum.eeeuser.com/viewtopic.php?pid=349061](http://forum.eeeuser.com/viewtopic.php?pid=349061)

Looks like they are having the same issue with no resolution as of yet. But it might give you road to run on.

---

### Post by kieonsegg on 2008-08-16
> **y@w said:**
> Easy there killer. We're trying to help. All you said was that it happens whenever you plug your AC power in and that you tried to delete "somehting called evolution update, but that didnt help". If we don't get specifics, we're going to try to start narrowing down what's going on, starting with the most obvious.

Here's someone else with an Eee PC with the same problem: [http://forum.eeeuser.com/viewtopic.php?pid=349061](http://forum.eeeuser.com/viewtopic.php?pid=349061)

Looks like they are having the same issue with no resolution as of yet. But it might give you road to run on.

Thanks, but still havent found solution wonder what it is.

---

### Post by takkuso on 2008-09-06
Just in case you hadn't gotten this solved yet. I had the problem but this worked for me:

Deicidist said: "It's actually a simple fix:

Go to Main Menu> System> Preferences> Preferred Applications

Under the Mail Reader section it should be set to Custom and have a command that says:

%s evolution (or whatever your preferred email client is)

Simply erase everything in the command and hit close.

That should solve your problem!"

---

### Post by undy on 2008-09-07
Thanks Takkuso for taking the effort to come back and post your solution. Worked for me and saved me time/effort.

---

### Post by Andy Armstrong on 2008-09-10
The real problem is that ACPI is getting confused; when you plug the AC power in it's triggering both a power event and a mail event. Here's what I see in /var/log/acpid when I plug the power in:

[Thu Sep 11 00:11:56 2008] BEGIN HANDLER MESSAGES
[Thu Sep 11 00:11:57 2008] END HANDLER MESSAGES
[Thu Sep 11 00:11:57 2008] action exited with status 0
[Thu Sep 11 00:11:57 2008] completed event "ac_adapter AC0 00000080 00000001"
[Thu Sep 11 00:11:57 2008] received event "battery BAT0 00000080 00000001"
[Thu Sep 11 00:11:57 2008] notifying client 5295[111:123]
[Thu Sep 11 00:11:57 2008] notifying client 5442[0:0]
[Thu Sep 11 00:11:57 2008] executing action "/etc/acpi/power.sh"
[Thu Sep 11 00:11:57 2008] BEGIN HANDLER MESSAGES
[Thu Sep 11 00:11:57 2008] END HANDLER MESSAGES
[Thu Sep 11 00:11:57 2008] action exited with status 0
[Thu Sep 11 00:11:57 2008] completed event "battery BAT0 00000080 00000001"
[Thu Sep 11 00:11:57 2008] received event "hotkey ATKD 00000050 0000000a"
[Thu Sep 11 00:11:57 2008] notifying client 5295[111:123]
[Thu Sep 11 00:11:57 2008] notifying client 5442[0:0]
[Thu Sep 11 00:11:57 2008] executing action "/etc/acpi/mailbtn.sh"
[Thu Sep 11 00:11:57 2008] BEGIN HANDLER MESSAGES
[Thu Sep 11 00:11:57 2008] END HANDLER MESSAGES
[Thu Sep 11 00:11:57 2008] action exited with status 0
[Thu Sep 11 00:11:57 2008] completed event "hotkey ATKD 00000050 0000000a"

Note that in addition to running /etc/acpi/power.sh it runs /etc/acpi/mailbtn.sh. As a quick fix I deleted the contents of /etc/acpi/mailbtn.sh. The eeePc has no email button anyway, so it's no loss.

This is probably better than disabling the preferred mail client.

---

### Post by shizeon on 2008-10-01
Thanks Andy.  You nailed the concern correctly.  I also was having the same problem.   I do have evolution installed so no error message, but just don't want it to start when I plug-in the AC adapter.

---

### Post by CeePhour on 2008-10-31
> **Andy Armstrong said:**
> "

Note that in addition to running /etc/acpi/power.sh it runs /etc/acpi/mailbtn.sh. As a quick fix I deleted the contents of /etc/acpi/mailbtn.sh. The eeePc has no email button anyway, so it's no loss.

This is probably better than disabling the preferred mail client.

Thanks a lot, this has been driving me crazy.
Still happens with 8.10.0, using array.org eeepc kernel version 2.6.27-7.

It's less annoying when you don't have evolution installed as you can quickly dispatch the error message. What sucks is waiting for it to load every time you plug in your eee :)

---

### Post by 3guk on 2008-11-10
This occurs because the asus-acpi module sends hotkey events when connecting to AC power with the wrong code (for the Eee; it's surely the right one on other Asus laptops).

Comment out all lines in /etc/acpi/events/asus-mail (by prepending a #), and restart acpid with sudo /etc/init.d/acpid restart.

---

### Post by mookiemu on 2009-02-08
> **3guk said:**
> This occurs because the asus-acpi module sends hotkey events when connecting to AC power with the wrong code (for the Eee; it's surely the right one on other Asus laptops).

Comment out all lines in /etc/acpi/events/asus-mail (by prepending a #), and restart acpid with sudo /etc/init.d/acpid restart.
Thanks this worked perfectly. I was really annoyed that this kept happening because I uninstalled the bloated evolution software.
:p

---

