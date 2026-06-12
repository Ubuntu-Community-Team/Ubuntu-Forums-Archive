---
title: "Power off PCMCIA on Shutdown"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by PowerlessRacing on 2006-10-01
I've searched around and haven't seen anything relating to this problem.

I am running Dapper Drake on an IBM Thinkpad X20 (P3, ~600MHz).  Everything is working out of the box.  I have a Netgear WG511t wireless card in my PCMCIA slot.  When I turn on the computer it starts up great, finds a network and logs me on.  Great card, great laptop, very consistent, no problems during use.  When I shutdown Dapper the two lights stop flashing and it goes to one solid light on my WG511t.  After the laptop power is off, the solid light stays on.  How do I set it up so that power to the PCMCIA slot is off when the laptop is turned off and I have no lights on on my WG511t?  Thanks.

Dave

---

### Post by Mr Frosti on 2006-10-01
When you say "shut down" there are several different states of being shut down:
[LIST=1]
[*]There is a standby mode, where the monitor and hard drive power down
[*]A suspend to RAM mode where everything turns of except the RAM
[*]A suspend to disk mode where everything turns of after copying files from RAM to the hard drive (hibernation)
[*]A completely off mode, requiring a full restart.
[/LIST]

Now, depending on what mode of shut down you are in, the instructions will differ. I suspect that you are going into suspend to RAM. To disable this service, you can specify PCMCIA in the following way:

Open up a text editor and open the file "/etc/default/acpi-support" with root permissions.

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

```

Change MODULES="" to MODULES="pcmcia" and save your changes. This will take effect when your acpi service is restarted (or the machine is restarted)

---

### Post by PowerlessRacing on 2006-10-01
Actually, I don't use hibernate.  Not out of any antipathy, I just don't know anything about it so I normally do a full shutdown requiring a full restart of the system.

I read the file you mentioned and I noticed a few options that may be interesting.

# Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

Do I need to uncomment that to allow suspend to RAM?

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

Is that one important?

The real question is how to stop it during a full shutdown, though.  Can you help me with that?  Thanks.

I did make the change you noted.  

Dave

---

### Post by csf111 on 2006-10-16
No help, I have the same problem as Dave.
When I SHUTDOWN (not Suspend or Hibernate)
the pcmcia adapter doesn't turn off the LED.

If I physically unplug the card and plug it 
back in, the light doesn't go on. 

(As an aside the "other" distro, turns off 
the light when I shutdown) Any thoughts?
Regards,
CSF

---

### Post by PowerlessRacing on 2006-10-25
I'm still interested in help on this topic.  Anyone have any ideas how to turn off power to the pcmcia slot during a complete shutdown of the computer?  

Dave

---

### Post by csf111 on 2006-10-27
I'm with Dave, I'd like some help too;
OR perhaps a pointer as to where to look.

I use this machine with a removable hard drive.
FC 6 shuts it down completely, Dapper does not,
Edgy does not. As FC6 does, I think there's hope!
Thanks,
CSF

---

### Post by daller on 2006-12-22
This is a little off-topic, but do you know how to "eject" the pcmcia card? (to prevent damage when removing the card)

**sudo cardctl eject **was suggested, but it isn't found...

```
ubuntu@ubuntu:~$ sudo cardctl eject
sudo: cardctl: command not found
```

---

