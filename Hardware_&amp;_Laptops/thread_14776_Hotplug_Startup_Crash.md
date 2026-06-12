---
title: "Hotplug Startup Crash"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by Deusiah on 2005-02-09
Altought there are many messages like this on these forums no one seems to have the same problem as I do.

Other's experience hangs with the statup hotplug script however my system crashes entirely 49 out of 50 times.

Looking at dmesg doesn't seem to reveal any probs and the only prob I can spot with "sudo grep hotplug /var/log/*" is:

> /var/log/user.log:Feb  9 21:02:29 localhost hal.hotplug[3789]: DEVPATH is not set

Whether or not that is THE prob I have no idea since I don't know how to go about fixing it.

Any help would be much appreciated :)

Thanks,
Deusiah

---

### Post by Deusiah on 2005-02-13
I was looking at the hotplug script in /etc/init.d/, it seems that there is a verbose mode available. I'm not sure but it looks like it may be able to echo the names of the modules it's including, however I don't know how to enable this versbose mode.

If it could be enabled then I could simply see which part it's crashing on and add it to the black list.

---

### Post by Deusiah on 2005-02-13
OK I managed to enable verbose mode in the hotplug script. I still have no idea how to set variables in bash scripts so I simply changed the if statement.

I see the problem is sound related, the module to blame is snd-nm256. Disabling this seems to (fingers crossed) fix the problem every time.

The odd thing is that sometimes I can start this module and it does work but most of the time it crashes. At the moment I am enjoying a very silent laptop :(

I'll look further into the situation and see if there is anything else I can dig up.

---

### Post by lucan on 2005-02-27
hi,
i have the same problem when i boot from my laptop.
i have also post the problem under 'compaq problem'. hope i can get a solution fast.

---

### Post by Deusiah on 2005-02-28
I wasn't able to find a solution to this other than either disabling the sound module and running the system with no sound or updating the BIOS which I'm sure will not work for everyone but in my case my Laptop starts up more often than not though it does still have the occasional problem booting but not usually with the hotplug script.

If you have a BIOS update available I figure it's worth a shot ;)

---

### Post by tvankirk on 2006-05-02
[QUOTE=Deusiah]OK I managed to enable verbose mode in the hotplug script. I still have no idea how to set variables in bash scripts so I simply changed the if statement.

I see the problem is sound related, the module to blame is snd-nm256. Disabling this seems to (fingers crossed) fix the problem every time.

The odd thing is that sometimes I can start this module and it does work but most of the time it crashes. At the moment I am enjoying a very silent laptop :(

I'll look further into the situation and see if there is anything else I can dig up.[/QUOTE]

Please see this post to fix the problem with the nm256 module boot freeze:

[http://www.ubuntuforums.org/showpost.php?p=977788&postcount=9](http://www.ubuntuforums.org/showpost.php?p=977788&postcount=9)

---

