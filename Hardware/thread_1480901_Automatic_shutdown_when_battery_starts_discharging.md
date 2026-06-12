---
title: "Automatic shutdown when battery starts discharging.."
date: 2010-05-12
forum: Hardware
---

### Post by jinsujais on 2010-05-12
hi,

I found a new problem in my lap. Whenever, the AC power supply gets off, my lap automatically shuts down. Please help me solving this issue.

---

### Post by BoneKracker on 2010-05-12
The answer that jumps to mind is acpid (the Advanced Configuration and Power Interface Daemon). 

Basically, acpi emits a message when certain "events" occur.  (One of these events is when the power source is changed from AC to battery.)  If you want something to happen when a particular event occurs, you associate an "action" with it.

An "action" is just a simple shell script (an "action script").  When the event occurs, kernel's acpi code sends a message.  The acpi daemon, operating in user space, hears that message and initiates whatever action(s) are associated with that event.

For example, when the laptop's lid button is activated (an "event"), acpid might be configured to initiate the "action" of putting the machine in suspend mode (which it would do by executing an "action script" that accomplishes that task.

There are reusable acpid configurations for many laptops, including commonly-desired responses to events.  However, in your case, you need something unusual to happen -- you need to machine to shut down (or suspend) as soon as AC power is interrupted.  So you will need to associate a shut-down or suspend action script with a battery power event.

That event and those action scripts may already exist in your acpid configuration.  You will have to look.  If they exist, you can simply associate the shutdown or suspend action with the batter power event.  If they don't exist, you will have to create them (by copying examples I'm sure you can find).

In either case, you'll need to read up a bit on acpid.  These are good places to start (besides the forums and google):

[http://linux.die.net/man/8/acpid](http://linux.die.net/man/8/acpid)
[http://wiki.archlinux.org/index.php/Acpid](http://wiki.archlinux.org/index.php/Acpid)

Also, if you don't want it to shutdown (or suspend) immediately when the power source is switched, you should be able to configure it to do so when the battery reaches a certain level (in fact, that's a pretty standard event -> action combination).

---

### Post by jinsujais on 2010-05-12
Thanks for the reply.

But I don't know how to do anything in Ubuntu. I'm an absolute beginner.

---

### Post by BoneKracker on 2010-05-12
Well, you can learn.

Or, if you don't want to learn, then you can try smacking it really hard (just kidding).

Your alternatives, I think, would be buying a new battery, getting the laptop repaired, or buying a new laptop.

You might also look to see if there is a graphical user interface to acpid (or powerdevil, a similar tool), but I'm not aware of one.

---

