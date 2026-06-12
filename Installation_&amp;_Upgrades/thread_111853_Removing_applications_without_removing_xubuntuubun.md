---
title: "Removing applications without removing xubuntu/ubuntu"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by Chrissie on 2006-01-03
Went to synaptic to remove gnome-terminal, marked it for removal and it told me that it would remove ubuntu-desktop as well!

So I started to check other applications I didn't need, like all these bluez~ that relate to bluetooth which I don't have, or bit-torrent which I don't use or apmd which is for laptops. All these, if you mark them for removal, tell you that they'll remove ubundu-desktop and/or xubuntu-desktop.
Not that it would make things faster, but there's lots that I don't need.

How do I go about removing these superfluous application without completely destroying xubuntu ?

Thanks for your help
Christel

---

### Post by mcduck on 2006-01-03
You wont destroy anything even if you uninstall ubuntu-desktop. It's just a metapackage pointing to all those applications installed by default with Ubuntu. (so installing package ubuntu-desktop will install all the programs that Ubuntu has by default, xubuntu-desktop installs programs used in Xubuntu and kubuntu-desktop installs thing that are in default kubuntu installation, but removing those desktop packages won't remove any programs).

Just make sure that you re-install it when you upgrade to Dapper, otherwise you may not get everything included.

---

### Post by Jessevl on 2006-02-24
Is there a way to add the programs I've removed automatically before i upgrade to dapper ?

---

### Post by jvnn on 2006-02-24
OK Mcduck, that sounds fine, since right at this moment I'm going thru synaptic trying to dump stuff that I don't think I'll use.
Now the bigger questions
- does it make sense to dump stuff like this? 
I'm thinking (since I'm a noob it could be flawed) that dumping this stuff will save hd space and speed things up during upgrades/updates since un-used stuff won't get upgraded as well as have a few less things for me to figure out as I climb the learning curve.
Does this make sense? any other reasons for/against clearing out the chaff?
-Will stuff stay out? For example Chrissie's bluetooth stuff; if that gets dumped will it stay out until it's specifically put back, or will it all go back when  you re-install ubuntu-desktop for the upgrade to dapper?
-What other dependencies that _look_ important (like ubuntu-desktop) can I safely delete?

Thanks - Joel

---

### Post by 5-HT on 2006-02-24
[QUOTE=Jessevl]Is there a way to add the programs I've removed automatically before i upgrade to dapper ?[/QUOTE]
Reinstalling ubuntu-desktop (or kubuntu-desktop, xubuntu-desktop, etc...which ever flavor have installed) will bring you back to a state with all standard packages for that flavor installed (but not extra ones that you installed and then removed).

It is strongly recommended that you reinstall the pertinent *buntu-desktop package prior to a dist upgrade (say if you upgrade to Dapper when it's officially released) to avoid possible issues when upgrading.

Hope that helps.

---

### Post by 5-HT on 2006-02-24
Hi,[quote=jvnn]
- does it make sense to dump stuff like this?  
I'm thinking (since I'm a noob it could be flawed) that dumping this stuff will save hd space and speed things up during upgrades/updates since un-used stuff won't get upgraded as well as have a few less things for me to figure out as I climb the learning curve. 
Does this make sense? any other reasons for/against clearing out the chaff? [/quote]

It's up to you and it will save some space for sure, but how much is another question.                                                                       
Removing only the ubuntu-desktop package won't remove anything though.

One thing to take note is that if you ever upgrade, it is recommended to reinstall ubuntu-desktop (to bring you back up to a standard state + anything else you may have installed) to avoid possible problems when upgrading.
[quote=jvnn]
-Will stuff stay out? For example Chrissie's bluetooth stuff; if that gets dumped will it stay out until it's specifically put back, or will it all go back when  you re-install ubuntu-desktop for the upgrade to dapper?
[/quote]
Yup, they'll stay out until you either manually reinstall, you install some other package that requires one you uninstalled as a dependency, or you reinstall ubuntu-desktop.

If you upgrade to Dapper (without reinstalling ubuntu-desktop) they will not all come back though, and that is what can potentially cause issues.

HTH

---

### Post by jvnn on 2006-02-24
Thanks 5-HT!
I appreciate the help.
Now can anyone shed some light on my 3rd question?
[QUOTE=jvnn]
-What other dependencies that _look_ important (like ubuntu-desktop) can I safely delete?l[/QUOTE]

---

