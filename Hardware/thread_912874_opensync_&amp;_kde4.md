---
title: "opensync &amp; kde4"
date: 2008-09-07
forum: Hardware
---

### Post by benneque on 2008-09-07
hey guys!

i use kubuntu 8.04 since yesterday (before i was using gentoo). it's an amd64 system with kde 4.1.1 .

everything runs fine with my system. i found everything i needed in the wiki and now everything works (graphics card, sound, webcam, etc) except my htc touch diamond (smartphone with windows mobile 6.1).

i installed and configured synce. this works fine. with synce-kpm i can view the batterystatus and the installed programs on my phone. so i suggest that synce works as it is supposed to.

because i'm new to smartphones and connecting them to linux i searched the internet for information. as i understood is works like that:
handy(hardware) -> usb -> pc -> synce -> opensync-plugin-synce -> opensync -> opensync-plugin-kdepim -> kdepim
i hope that's right :D .. so .. synce is working
opensync should get configured through multisync-gui or kitchensync ?! i searched hours for kitchensync, i just found versions for kde3. in gentoo there were versions for kde4. but that doesn't matter, multisync-gui should do the same job i hope.
so started multisync0.90 , created a group called diamond. ok, now i should add 2 members ... the gui displays 2 possible members but there are just green arrows and no names behind. if i choose one of them the gui crashes: 
I/O warning : failed to load external entity "/home/benneque/.opensync-0.22/group1/filter.conf"
**
** ERROR:(/build/buildd/opensync-0.22/opensync/opensync_member.c:246):osync_member_instance_plugin: assertion failed: (pluginname)
Aborted

i hope someone can help me, or correct my mistakes :D
and the final question is of course: where can i find an opensync-plugin for kde4 ?? i read somewhere that kitchensync4 can do this job and somewhere else it said that i have to wait for an akonadi plugin for opensync... and i was kinda shocked when i saw the version number of opensync.. 0.22 ??? there's already 0.36 out, where is it ?

so .. thanks a lot for your help, guys ;)

EDIT: multisync now recognizes my smartphone ... now i installed opensync-plugin-synce-legacy instead of opensync-plugin-synce!

---

### Post by piedro on 2010-11-08
It's a pity! 
The situation seems not to have changed at all! 

I can't find any GUI for opensync with maverick meerkat. 
Can't find information either, except for outdated stuff. 

Any help? 
p.

btw.: the same with gnome

---

