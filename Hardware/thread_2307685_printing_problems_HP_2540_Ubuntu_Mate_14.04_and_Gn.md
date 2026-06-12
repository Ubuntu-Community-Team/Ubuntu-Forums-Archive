---
title: "printing problems HP 2540 Ubuntu Mate 14.04 and Gnome 15.04 and 15.10"
date: 2015-12-27
forum: Hardware
---

### Post by fallenstardust on 2015-12-27
Hi,

Between me and my parents, we have 3 laptops, 2 parental laptops running Ubuntu Mate, and we each have the same HP 2540 printer. In Debian, my dual boot, there is no problem printing at all to either printer. When I had Ubuntu Gnome 15.04, then 15.10, neither printed, but were both really broken installations, so I didn't realise it was an ubuntu thing.

The problem is the same with all 3 laptops, once setup with CUPS, the printer works until the laptop is rebooted. I have installed the new HPLIP drivers (3.15.11), tried both wireless (doesn't work at all) and usb, where it either works briefly or doesn't work until adding it in CUPS in localhost:631, then it works. briefly. Adding the printer through the standard printer gui either doesn't work, or works until reboot.

hp-check says all dependencies are satisfied, print queue is present and correct, can communicate with the printer, yet no program can print. CUPS just says jobs are pending.

According to both Ubuntu

[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)

and HP

[http://hplipopensource.com/hplip-web/supported_devices/combined.html](http://hplipopensource.com/hplip-web/supported_devices/combined.html)

the printer is compatible and should work out of the box.

Pulling my hair out over here, any ideas? Please help, my elderly dad is muttering about going back to Windows after 6 years on Linux!

---

### Post by UltimateCat on 2015-12-28
Sadly I've found a solution but it's getting really old to keep doing this but this works for me.

Go to [http://localhost:631](http://localhost:631) and select Printers. Select the printer, then Maintenance than Cancel all jobs. (this is to make sure that no jobs are pending)
Select Administration then Delete the Printer.

Either type "hp-setup" in the terminal and set up the printer again .
This will walk you through discovery of the printer and creates the CUPS entries for you.

<OR>
Go to the HP Manager (small blue icon in the upper right hand of your desktop) and set the printer back that way through the Wizard.

If hp-setup can't see the printer, exit hp-setup and disconnect the USB cable wait a few seconds and plug it back in again or try a different jack.

If the printer still won't print you might have to go back to the previous version of HPLIP.
That might be in Synaptic.

Hope that helps.

---

### Post by oldfred on 2015-12-28
I also have found each install of hp-lip creates a new printer unless you specifically say not to.
And new printer is not default.

My wife for whatever reason also has issues printing from Web pages some coupons. It just goes into queue but is never released. I have to go into HP Device manager, printer control (last tab) and release print job.

---

