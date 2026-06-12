---
title: "Toshiba Qosmio F60 Front Operation Panel buttons not working"
date: 2013-05-31
forum: Hardware
---

### Post by solomonsunder on 2013-05-31
[COLOR=#333333][FONT=Ubuntu Mono]I am unable to toggle wireless on/off, mute/unmute, play/pause using Front operation panel LED keys on my Toshiba Qosmio F60. Currently I need to enable WiFi/Bluetooth from Windows for it to work. Fn+F8 toggle works as soft block/unblock only if I have already enabled WiFi under Windows. Any ideas as how this can be done? I have tried Ubuntu 13.04 as well. The only LED Touch button that works under Ubuntu is the Volume Up/Down button. Touchpad on/off toggle does not work with physical button or Fn+F9 either.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]dmesg [http://paste.ubuntu.com/5659327/](http://paste.ubuntu.com/5659327/)[/FONT][/COLOR]
dmesg [COLOR=#333333][FONT=Ubuntu Mono]when wireless disabled from within windows: [/FONT][/COLOR][http://paste.ubuntu.com/5813568/](http://paste.ubuntu.com/5813568/)
lsmod when wireless disabled from within windows: [http://paste.ubuntu.com/5813573/](http://paste.ubuntu.com/5813573/)
[COLOR=#333333][FONT=Ubuntu Mono]dmidecode [http://paste.ubuntu.com/5659339/](http://paste.ubuntu.com/5659339/)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]output when wireless disabled from within windows [http://paste.ubuntu.com/5659346/](http://paste.ubuntu.com/5659346/)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]output when wireless enabled from within windows [http://paste.ubuntu.com/5659348/](http://paste.ubuntu.com/5659348/)[/FONT][/COLOR]

---

### Post by Solomon Sunder on 2013-10-29
@Varun, Please find syslog [http://paste.ubuntu.com/6324631/](http://paste.ubuntu.com/6324631/) The blacklist command you provided disabled bluetooth and showed as 'no adaptor' under System Settings. Upon enabling with the second command bluetooth has started working fine. But there is a weird behaviour which I observed last time when you suggested a similar step on IRC. Pressing 'Shift+p' or 'Shift+f' opens a terminal and 'Shift+w' does not work. I am using Ubuntu 13.10 now. uname -r yields '3.11.0-13-generic'. Currently I have WiFi enabled from within Windows during all of these tests.

Adding these links for anyone else who stumbles upon this thread regarding quickstart for Front Operation Panel buttons.
[http://quickstart.sourceforge.net/](http://quickstart.sourceforge.net/)   [https://www.fortresslinux.org/downlo...st/kernel.html]("https://www.fortresslinux.org/download/FL-Docs/flhwlist/kernel.html")

---

### Post by varunendra on 2013-10-29
> **Solomon Sunder said:**
> Upon enabling with the second command bluetooth has started working fine.
You mean the second command from [here]("http://ubuntuforums.org/showthread.php?t=2158965&p=12832077#post12832077") **+ a reboot**, ritght? Because the second command only removes the module names from blacklist (so they 'can' load at next boot). You have to either reboot or load them manually to have them working again.

If it worked just by un-blacklisting with the second command, then I suspect it was just coincidence, nothing to do with blacklisting.

> Pressing 'Shift+p' or 'Shift+f' opens a terminal and 'Shift+w' does not work.
When did this behaviour start? After blacklisting those modules, or after 'manually' loading them again? Does this behaviour persist after a reboot?

The "toshiba_acpi" driver is supposed to handle Fn+ key combinations. I'm not sure about toshiba, but in my Asus, if I blacklist the similar driver (that handles the Fn+ key combos) at startup, then re-load it 'manually', it also causes some weird behaviour, although only with Fn+ keys (as far as I have observed). But it goes away on next boot. Is it same with you?

---

### Post by Solomon Sunder on 2013-10-30
I tried it again. Had forgot to check the Fn keys. They do not work if toshiba drivers are blacklisted. Did not check whether the weird behaviour happened during the reboot immediately after blacklisting since I had nothing to type then. I did not manually load it. Instead I did second command + reboot. The terminal it opens is XTerm.

---

