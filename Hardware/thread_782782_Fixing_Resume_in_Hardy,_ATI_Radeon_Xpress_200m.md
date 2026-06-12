---
title: "Fixing Resume in Hardy, ATI Radeon Xpress 200m"
date: 2008-05-05
forum: Hardware
---

### Post by djails on 2008-05-05
Hi,
My laptop (Toshiba A100, atheros wifi, ATI radeon xpress 200M) used to suspend & resume without a glitch with Gutsy / ATI drivers 8.2. I decided to upgrade to Hardy and I m currently using the ubuntu-provided fglrx binary driver (8.3). Suspend works, but resume leaves me with a totally useless brick: the laptop freezes straight upon resume, no LCD backlight, no blinking cursor, not even the slightest HDD activity. Even worse, the magic key combo (Alt-SysReq SUB) doesnt work at all. In fact, not even  hard reboot or power cycles work, the screen stays black. The only way to get the laptop to boot again is to unplug power cord and battery ! (I ve had to fiddle a bit with acpi scripts to get them to work before, but I ve never seen that !). Using the open ATI xorg driver, suspend and resume work fine.
I read the procedure about debugging suspend issues on the ubuntu wiki at
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) and tried it. Magically, both suspend and resume worked !!! The magic command is "sudo /etc/acpi/sleep.sh force " in this case. Searching the net a bit more, i also came accross this fix a couple of times ([http://www.ozymo.com/~chuck/blog/2008/03/17/fglrx-and-suspend-in-ubuntu-hardy-alpha/](http://www.ozymo.com/~chuck/blog/2008/03/17/fglrx-and-suspend-in-ubuntu-hardy-alpha/) and [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/207087](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/207087) ). 
It seems gnome-power-manager (the app that puts the system to sleep when appropriate) relies eventually on pm-suspend (pm-utils package) to suspend the machine. This is what does not work for me, it does suspend the laptop, but resume consistently fails (somehow). The trick is to get gnome-power-manage to use "/etc/acpi/sleep.sh force" instead of whatever it uses. This is done by editing "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replacing "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" around line 74.
It did the trick for me !
Hope it helps.

---

### Post by victor.zamanian on 2008-06-06
This fix doesn't work for me on my Dell Dimension 9200, recently flashed BIOS, latest (incl. proposed) updates as of the date of posting, and
```

$ uname -r
2.6.24-18-generic

```

Suspension on linux is a big dissappointment for me.

---

### Post by manca on 2008-07-04
> **djails said:**
> Hi,
My laptop (Toshiba A100, atheros wifi, ATI radeon xpress 200M) used to suspend & resume without a glitch with Gutsy / ATI drivers 8.2. I decided to upgrade to Hardy and I m currently using the ubuntu-provided fglrx binary driver (8.3). Suspend works, but resume leaves me with a totally useless brick: the laptop freezes straight upon resume, no LCD backlight, no blinking cursor, not even the slightest HDD activity. Even worse, the magic key combo (Alt-SysReq SUB) doesnt work at all. In fact, not even  hard reboot or power cycles work, the screen stays black. The only way to get the laptop to boot again is to unplug power cord and battery ! (I ve had to fiddle a bit with acpi scripts to get them to work before, but I ve never seen that !). Using the open ATI xorg driver, suspend and resume work fine.
I read the procedure about debugging suspend issues on the ubuntu wiki at
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) and tried it. Magically, both suspend and resume worked !!! The magic command is "sudo /etc/acpi/sleep.sh force " in this case. Searching the net a bit more, i also came accross this fix a couple of times ([http://www.ozymo.com/~chuck/blog/2008/03/17/fglrx-and-suspend-in-ubuntu-hardy-alpha/](http://www.ozymo.com/~chuck/blog/2008/03/17/fglrx-and-suspend-in-ubuntu-hardy-alpha/) and [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/207087](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/207087) ). 
It seems gnome-power-manager (the app that puts the system to sleep when appropriate) relies eventually on pm-suspend (pm-utils package) to suspend the machine. This is what does not work for me, it does suspend the laptop, but resume consistently fails (somehow). The trick is to get gnome-power-manage to use "/etc/acpi/sleep.sh force" instead of whatever it uses. This is done by editing "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replacing "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" around line 74.
It did the trick for me !
Hope it helps.

Thank you! This worked for me.
However, I don't get it why we should use force option in sleep?

---

### Post by jephoria on 2008-07-27
Hi all,

I have a Dell Inspiron 8500 with an ATI Radeon Mobility 9600 running Hardy.  I'm having similar problem and have tried the above as well as [modifying /etc/default/acpi-support]("http://www.lunders-and.no/wp/?p=99").  No luck so far.  Oddly, suspend/resume works sometimes, but not other times.  Sometimes when it does work, I get a loud beeping sound upon resuming along with an error message tghat suspend did not work properly.  Other times I get the beep, but my screen never comes back.  Mostly though, I just get a black screen and no keyboard response.  Has anybody out there had similar symptoms and found a solution?  

I really need to fix this.  I'm getting really tired of my wife laughing at me smugly from behind her Win XP laptop every time I have to reboot.  Thanks!

---

### Post by briwood on 2008-07-28
Jephoria,

Good news: it's possible to get it working.  
Bad news: all machines are different so there is not one common solution.

I'm on an old IBM Thinkpad. I've had success using the hibernate package

```
sudo apt-get install hibernate
```

Once it's installed read this guys suspend notes: [http://weierophinney.net/matthew/archives/136-Back-on-Linux-Again.html](http://weierophinney.net/matthew/archives/136-Back-on-Linux-Again.html)

the man pages for hibernate and hibernate.conf are also good to read.

Good luck and don't be deterred by your wife.

---

### Post by jephoria on 2008-08-04
No good.  When I try to suspend I just get a "not enough memory" warning before it locks up.

---

### Post by t.rei on 2008-08-05
I have now created two little launchers in my panel.

One does: "metacity --replace" and the other one does "compiz --replace". 

If I turn compiz off before suspending, the resume works. :/ *looks for a better solution*

---

### Post by resumes on 2008-09-02
Re: Fixing [Resume]("http://free.resume-templatesky.org/") in Hardy, ATI Radeon Xpress 200m

:lolflag::lolflag:

---

### Post by Steve Grace on 2009-01-02
This works for me in Hardy, using the standard "ati" driver, not "fglrx" (I have a RADEON 7000).

THANK YOU!

---

### Post by bayvista on 2009-02-11
Any HP Pavillion users with this problem? I can't seem to be able to wake up the laptop after a suspend or hibernate?

---

