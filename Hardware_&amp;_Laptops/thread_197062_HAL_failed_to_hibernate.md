---
title: "HAL failed to hibernate"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by ophion on 2006-06-15
Power Manager says that the HAL failed to hibernate.  I must, therefore, go through some jiggery-pokery to get networking back up after coming out of hibernation.  What can I do to fix this?

---

### Post by kreso on 2006-06-19
I got the same error except everything seems to be okay after resuming from hibernate? :confused:

---

### Post by H.E. Pennypacker on 2006-06-21
I looked all over for this error, and this is the only thread I found the error.  The exact message from the message is "HAL failed to hibernate," and then it says something about checking the FAQ.  When you click on FAQ, nothing happens.

ophion, the difference between you and I is that everything seems to work perfectly fine.  I notice no problems, but this error may have a significance.

---

### Post by PWill on 2006-06-21
i'm pretty much the same. when i come out of hibernation, networking is down, but nm-applet is doing its stuff and i'm connected in about 10 seconds.

---

### Post by kreso on 2006-06-23
I've noticed that the only problem is that battery information is not updated correctly when resuming from hibernate and recieving that error.

also, I've noticed thati if you hibernate on batteries and resume on batteries, it's okay.

---

### Post by H.E. Pennypacker on 2006-06-25
Just to be on the safe side, I'd like this problem to go away.  Here's what I found in Gnome Power Manager's FAQ:

> [B]
Why using Ubuntu (Dapper) do I get the error[/B]

WARNING **: gpm_hal_suspend: A security policy in place prevents this sender
from sending this message to this recepient, see message bus configuration
(rejected message had interface
"org.freedesktop.Hal.Device.SystemPowerManagement" member "Suspend" error name
"(unset)" destination "org.freedesktop.Hal")
WARNING **: org.freedesktop.Hal.Device.SystemPowerManagement.Suspend failed (HAL error)
      
Ubuntu ships a locked down DBUS by default for Dapper which prevents non-root from issuing methods to HAL. To allow the current logged in user to use these methods, just **install the libpam-foreground** package. 

I don't know if this is a solution for anyone, but it certainly is not for me, because I already have libpam-foreground installed.  I know the error says suspend, but it could relate to hibernation as well.  Can you guys let me know if this works?

---

### Post by EDevil on 2006-07-21
I also get this message. The only thing that seems to be wrong is the battery status information.

---

### Post by raluke on 2006-07-24
Bump.  I also get the message but I have yet to notice anything not working after the machine has revived from hibernation.  I, too, already had the libpam-foreground package installed.

-Robert

---

### Post by hydrogen on 2006-07-25
hi, I found that I've already installed the libpam-foreground, but I still get the HAL failed message. My biggest problem is every time when my ThinkPad come up from Hibernation. my wireless interface disappear. I must reboot the ThinkPad to make the wireless show up.  The condition is when the wireless interface work( the led light) before hibernation. If the Led do not work before hibernation, no such problem.

---

### Post by kreso on 2006-08-02
> **hydrogen said:**
> hi, I found that I've already installed the libpam-foreground, but I still get the HAL failed message. My biggest problem is every time when my ThinkPad come up from Hibernation. my wireless interface disappear. I must reboot the ThinkPad to make the wireless show up.  The condition is when the wireless interface work( the led light) before hibernation. If the Led do not work before hibernation, no such problem.

you don't have to restart :)

eg. if you have ipw2200 wifi driver:

sudo rmmod ipw2200
sudo modprobe ipw2200

---

### Post by zeimusu on 2006-08-07
I see this message on my desktop computer. For me this means that my wacom tablet doesn't work after awaking from hibernation. I have to reboot with keyboard control. Gives one a taste of some accessibility issues! Suspend doesn't work at all here, it hangs the computer with a black screen.

---

### Post by isharra on 2006-08-07
> **hydrogen said:**
> hi, I found that I've already installed the libpam-foreground, but I still get the HAL failed message. My biggest problem is every time when my ThinkPad come up from Hibernation. my wireless interface disappear. I must reboot the ThinkPad to make the wireless show up.  The condition is when the wireless interface work( the led light) before hibernation. If the Led do not work before hibernation, no such problem.
Try adding the name of the module for your networking card to the MODULES="" line in /etc/default/acpi-support.  That way the suspend/resume scripts will try to remove and reinsert the module for you.

---

### Post by raul_ on 2006-10-08
I also get this error, but the thing is that my desktop doesn't even hibernate..it sleeps for about 5 seconds and then wakes up alone with that message. I don't know about you but i'm not very enthusiastic about any message that starts with "HAL failed"

---

### Post by Ubuntist on 2006-10-17
I too get an error message when resuming a hibernated session under Ubuntu Dapper with libpam-foreground installed.  Superficially, everything works fine.  However, I've noticed that after several successive hibernations without a re-boot, some problems do seem to creep in.  For example, I recently found that OpenOffice applications would no longer open.  Re-booting solved the problem.

---

### Post by Alex99 on 2006-10-25
I have the same problem. My system goes down for hibernation, but then after 10 secs or so (I don't do anything) there's a login screen, and after loging in, it says HAL failed to hibernate. 
No further complications, but I would just like my system to hibernate!

---

### Post by raul_ on 2006-10-25
Post a bug report. It always helps

---

### Post by Alex99 on 2006-10-25
uh, sorry - how do I do that?

---

### Post by raul_ on 2006-10-25
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by Alex99 on 2006-10-25
Hi,
sorry to bother. At 
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

- more specifically, at:
[https://launchpad.net/distros/ubuntu/+source/hibernate/+bug/49282](https://launchpad.net/distros/ubuntu/+source/hibernate/+bug/49282)
-
I found the bug I may be dealing with. Here's a description of how to fix it, but I don't understand it.

```

HAL, and hence gnome-power-manager, does not use /usr/sbin/hibernate when this package is installed. The reason is that /usr/share/hal/scripts/hal-system-power-hibernate prefers /usr/sbin/pmi that is installed by the package powermanagement-interface. That package is installed through a dependency from gnome-power-manager, so it's not possible to deinstall it.

I can't see any way to rectify this through user configuration; I resorted to manually edit the hal-system-power-hibernate script to make it use /usr/sbin/hibernate.

I suspect most users expect that this package actually gets used, e.g. through the Hibernate option in gnome-power-manager, when they install it. What happens now is that hibernation still works (more or less) through /usr/sbin/pmi but configurations made in /etc/hibernate/hibernate.conf don't have any effect.

This issue seems difficult to solve cleanly. A case in point is that I'd prefer to use hibernate for suspend-to-disk (due to its superior configurability) but pmi for suspend-to-ram (since hibernate.conf only can be configured to use a single suspend method).

```

How do you manually edit the hal-system-power-hibernate script to make it use /usr/sbin/hibernate?
Further, when I execute
```
/usr/sbin$ sudo hibernate --force
```
in the terminal, the reply is:

```
Your kernel does not appear to have Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://www.suspend2.net/ for instructions
on how to compile Software Suspend into your kernel.
hibernate: Aborting.
```

I feel compiling my kernel is a little risky since I'm an inexperienced user. Any suggestiosn anyone?

---

### Post by ethan961 on 2006-11-08
What is HAL anyway?

---

### Post by spier on 2006-11-10
> **ethan961 said:**
> What is HAL anyway?

Hardware Abstraction Layer. [some words about.]("http://freedesktop.org/wiki/Software_2fHalFAQ")

BTW, I get the same message sometimes, but as far as I know, it happens when it sleeps with an usb device (like mouse, pendrive) and wakes without it...

---

### Post by konus on 2006-11-15
you need to install the suspend2 software:

```

sudo apt-get install hibernate

```

---

### Post by heatpumpcontrol on 2007-08-31
> **konus said:**
> you need to install the suspend2 software:

```

sudo apt-get install hibernate

```

Wow! This seems to have worked for me. I just came back out of Hirbernation and I did not get an error. Sweet! :)

and I also got 
> Broadcast Message from root@johny                                             
        (somewhere) at 10:34 ...                                               
                                                                               
Communications restored with UPS johny 

So my UPS is up and running.

---

