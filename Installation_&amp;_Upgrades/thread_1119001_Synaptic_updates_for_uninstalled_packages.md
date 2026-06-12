---
title: "Synaptic updates for uninstalled packages??"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2009-04-07
Hello again,

I had an instance recently where plugging my laptop into a network set off the IDS because my box sent an SNMP probe to all devices on the network. 

After researching this, I found CUPS to be the culprit. Well I don't need it, so I decided to go about uninstalling, only to find a warning that gnome may be uninstalled as well. So I researched a bit further, and pulled out a spare laptop (identical to the one I'm working with except it has a bare 8.10 install) to test this on.. I took the leap and uninstalled cups:

```
sudo apt-get remove cups
```

After completion, I went through and updated the system, which caused a restart- so I did that. Now, however, synaptic keeps telling me there are 7 updates available for install- all of which have to do with cups. So the question is: Will synaptic tell me these are here forever? Is there a way to dismiss those updates so I'm not plagued with the notifier?

TIA

---

### Post by batharoy on 2009-04-07
Why not just dis-able the service at boot.
I used BootUp Manager (bum in the repo's) to disable it.
That way in the off chance you might need, it's still there.
And it shouldn't effect your network.
Dont know if it will work but worth a try.

---

### Post by sp0nge on 2009-04-07
This machine is used for specific purposes only and I will not have any use for cups at all. 

I appreciate your suggestion, but I have already uninstalled cups and find the updates still forcing themselves on me.

Can I make them go away? I'm about to install them and see what happens with the rest of the packages missing :)

---

### Post by sp0nge on 2009-04-08
Well, I installed the updates.. just to see what happens. 

So far nothing. We'll see if the probes get sent out again.

---

