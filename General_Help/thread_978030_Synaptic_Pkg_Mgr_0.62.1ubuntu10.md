---
title: "Synaptic Pkg Mgr 0.62.1ubuntu10"
date: 2008-11-10
forum: General Help
---

### Post by gary201 on 2008-11-10
I have a question about Synaptic's search ability.  I just installed ubuntu 8.10 onto a laptop and a virtual machine on another system.  Entering search criteria within either the quick search field or the Find dialog, the results are different between the two installations, and for the life of me I can't figure out why.  I've compared every configuration option within the app between the two installations and they're identical, which stands to reason since I haven't made any changes.  I've also not modified the repositories on either.

On the VM, the search works as you would expect by filtering the list down to what matches (both installed and not).  On the laptop, however, the results seem inconsistent.  If I search for "synaptic", the results list only the two installed packages with that string of characters (the package manager and the touchpad driver).  On the VM, 11 packages are listed.  In another example, if I search for "gkrellm" on the VM, 28 packages are listed.  On the laptop, none are listed --despite the fact that "gkrellm" and "gkrellm-leds" are actually installed.

Again, every configuration option within Synaptic has been compared and are identical.

Anyone have a clue as to why the different search behaviors?

Thanks,
Gary...

---

### Post by cariboo on 2008-11-10
When you use Synaptic's Search button it searches by name and description by default, where as the quick search only searches by name

Check your laptop search button criteria to see what it is set to.

Jim

---

### Post by gary201 on 2008-11-15
All of the settings in preferences and filters settings are identical.  This was the first thing I checked. That's why this doesn't make any sense.

---

### Post by cariboo on 2008-11-15
The only other thing I can suggest is to reload your sources list and check again to see if you get differing results.

Jim

---

