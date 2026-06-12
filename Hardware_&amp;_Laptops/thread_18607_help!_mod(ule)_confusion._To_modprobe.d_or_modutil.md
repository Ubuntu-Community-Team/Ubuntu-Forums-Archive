---
title: "help! mod(ule) confusion. To modprobe.d or modutils, that is the question!"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by pigpen on 2005-03-07
I've come to realize that a lot of the information on the internet and even the 'man' pages in Debian itself are out of date. So after much googling and reading, I was wondering if someone could clear this up for me.

For 2.6 kernel, if you want to configure a module, like setup a sound card. You would need to edit, or create, a file in the /etc/modprobe.d directory, like a file named 'sound', and then run 'update-modules. Is this correct? 

For earlier kernels, like 2.4, you would need to make adjustments in the /etc/modutils directory, like for sound it would be the /etc/modutils/alsa file. And then run 'update-modules'. Is this correct?

When using the 2.6 kernel and executing the 'update-modules' command, this updates the 'modprobe.conf' file? 

And for the 2.4 kernel, the 'update-modules' command updates the 'modules.conf'?

So basically, 2.6 kernel follows this logic /etc/modprobe.d/'somefile' > update-modules > modprobe.conf?

2.4 kernel : /etc/modutils/'somefile' > update-modules > modules.conf?

And lastly, why is 'update-modules' described as an obsolete command when you do a 'man update-modules'. Is there another prefered command? Or is the man page wrong?

Thanks in advance.

EDIT: hmmm....I could not find a modprobe.conf in kernel 2.6 in ubuntu hoary. Or am I missing something? If there is no modprobe.conf file, then what happens when you 'update-modules' in kernel 2.6?

---

### Post by pigpen on 2005-03-11
Bumping this up. Would appreciate a reply.

---

### Post by alastair on 2005-03-11
I'm a new Debian user (but long time linux user), so cannot help /that/ much.

But ....

"update-modules" appears to just be a shell script (which update-modules) - having a look, shows it only works IF :

/sbin/update-modules.modutils

exists. It does NOT exist on Hoary Ubuntu. So "update-modules" does nothing here.

It appears that /etc/modprobe.d/ is the place to add module parameters. The file /etc/modules lists modules to definitely load on kernel boot - as per the runscript /etc/rcS.d/S20module-init-tools.

/etc/modutils/ does not appear to be used on my system (Hoary) - but I might be wrong.

---

### Post by mingus on 2005-05-31
[QUOTE=pigpen]I've come to realize that a lot of the information on the internet and even the 'man' pages in Debian itself are out of date. So after much googling and reading, I was wondering if someone could clear this up for me.

For 2.6 kernel, if you want to configure a module, like setup a sound card. You would need to edit, or create, a file in the /etc/modprobe.d directory, like a file named 'sound', and then run 'update-modules. Is this correct? 

For earlier kernels, like 2.4, you would need to make adjustments in the /etc/modutils directory, like for sound it would be the /etc/modutils/alsa file. And then run 'update-modules'. Is this correct?

When using the 2.6 kernel and executing the 'update-modules' command, this updates the 'modprobe.conf' file? 

And for the 2.4 kernel, the 'update-modules' command updates the 'modules.conf'?

So basically, 2.6 kernel follows this logic /etc/modprobe.d/'somefile' > update-modules > modprobe.conf?

2.4 kernel : /etc/modutils/'somefile' > update-modules > modules.conf?

And lastly, why is 'update-modules' described as an obsolete command when you do a 'man update-modules'. Is there another prefered command? Or is the man page wrong?

Thanks in advance.

EDIT: hmmm....I could not find a modprobe.conf in kernel 2.6 in ubuntu hoary. Or am I missing something? If there is no modprobe.conf file, then what happens when you 'update-modules' in kernel 2.6?[/QUOTE]
 Please excuse me, pigpen, did you receive a satisfactory (clear) answer to your query?

I had the same issue as you, and reached the same hypothesis.  As confirmed by alastair, only by having modutils installed does update-modules work from /etc/modutils/.

But this still leaves me baffled.  Before I stumbled - no thx to all the outdated docm - onto the modutils package, update-modules was doing nothing.  But I *HAD* added the exact same module lines in /etc/modprobe.d/ as I did in /etc/modutils/.  Running update-modules (before installing the modutils package) did not pull in what I placed in /etc/modprobe.d/ and in fact, did not seem to do anything at all.  The modules would not load.

It appears that when the modutils version is used, a file /etc/modules.conf gets created.  I've seen that in ref'd in posts.  When I ran update-modules before installating modutils, no such file existed nor was created afterward.  But it was created after installing modutils.

After installing modutils and the creation of /etc/modules.conf, the module added to /etc/modules properly loaded.

I have posted a similar question to yours on the forum, but received no replies.  Have you deciphered what *IS* the correct program and procedure?

Thanks so much for your time.

--mingus

---

### Post by luxer on 2005-06-12
apparently there is nobody in the entire freakin' world who knows the answer to this question. 

I utterly can not tell if a file dropped into /etc/modprobe.d is doing anything or not.

Certainly running update-modules after installing a new file in /etc/modprobe.d is useless. Look at the code in /sbin/update-modules:

#!/bin/sh -e
if [ -x /sbin/update-modules.modutils ]; then
  exec /sbin/update-modules.modutils "$*"
fi
exit 0

It does absolutely nothing without modutils and modutils was not installed on my ubuntu box by default.

The only reference to /etc/modprobe.d in /etc/module-init-tools is:

if [ -r /etc/modprobe.conf ] \
        && ! grep -q '^include.*modprobe.d' /etc/modprobe.conf; then
   echo 'WARNING: /etc/modprobe.conf exists but does not include /etc/modprobe.d/!'
fi

The problem here is that /etc/modprobe.conf is not installed by default! Even though several files are present in /etc/modprobe.d. DO thise do nothing? There are counterparts for them in /etc/modutils... what do those do? Does any of this freakin' work at all???

---

### Post by luxer on 2005-06-12
ah... ok so it's modprobe that reads /etc/modprobe.d for options directly?

from the man page:

 -C --config
              This option overrides the default configuration file  (/etc/modprobe.conf
              or /etc/modprobe.d/ if that isn’t found).

That seems to suggest that modprobe reads /etc/modules.d no?

/etc/modutils appears to be useless. I've moved mine out of the way with no ill effects so far.q

---

### Post by mingus on 2005-06-13
yes, you are correct.  I don't have the url at hand, but I did find info on the web that explained how this had been changed from 2.4 to 2.6. 

I've found that both modprobe and modutils can be made to work.  I suppose for backwards compatibility reasons.  For modutils to work, you have to install a package by that name.

Also, the program update-modules is supposed to still work even with this change.

---

