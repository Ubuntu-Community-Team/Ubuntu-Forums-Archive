---
title: "help me understand sound"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by negativ on 2004-10-31
When I open the volume control, I have a tab for OSS, and a tab for ALSA.  Sliding the volume controls on either tab raises and lowers the volume. 

Does this mean I have both ALSA *AND* OSS drivers loaded?  :-k 

I think I only want ALSA, right?  Or not?  I'm confused.

---

### Post by jdusablon on 2004-11-02
I'm also interested in this. Why, also, is the sound so awkward to manage (all the esoteric levels, I mean?)

---

### Post by diebels on 2004-11-02
You want OSS for compability with older programs. You can force OSS drivers to not getting loaded, but it won't do any good except for saving a couple kb of memory.

---

### Post by mercurus on 2004-11-03
[QUOTE=negativ]When I open the volume control, I have a tab for OSS, and a tab for ALSA.  Sliding the volume controls on either tab raises and lowers the volume. 

Does this mean I have both ALSA *AND* OSS drivers loaded?  :-k 

I think I only want ALSA, right?  Or not?  I'm confused.[/QUOTE]
You only have ALSA drivers loaded by default, the drivers included in the 2.6.x branch kernel. However, in order to stop ALSA breaking older software, ALSA is able to emulate the OSS devices of old.

Most applications should use ALSA by default, but if not ... then OSS should work. For example, if you apt-get install xmms it defaults to using the OSS output plugin - which works out of the box. If you force it to use the ALSA output plugin, it also works ! This is why there are two tabs on the Volume Control application, one for output using the OSS emulation, and the main one, using the ALSA driver alone.

Preferably adopt ALSA as your standard sound driver, as I would imagine older packages will gradually be updated to use ALSA only. Atthe moment though, ALSA with OSS backwards-compatibility is the best option to ensure good performance, and best hardware support.

As diebels said, you can prevent loading of OSS emulation, but there's really neglible benefits to doing so (apart from forcing you to migrate EVERYTHING to ALSA now)

Cheers
mercurus

---

### Post by jamaas on 2004-11-08
thanks Mercurus, this does help explain a lot.  I've got my also drivers but have lost my oss drivers and need them!  How might I get them back and keep them?  Where is the switch that is turning them off ?

Thanks a bunch

Jim


[QUOTE=mercurus]
Most applications should use ALSA by default, but if not ... then OSS should work. For example, if you apt-get install xmms it defaults to using the OSS output plugin - which works out of the box. If you force it to use the ALSA output plugin, it also works ! This is why there are two tabs on the Volume Control application, one for output using the OSS emulation, and the main one, using the ALSA driver alone.

Preferably adopt ALSA as your standard sound driver, as I would imagine older packages will gradually be updated to use ALSA only. Atthe moment though, ALSA with OSS backwards-compatibility is the best option to ensure good performance, and best hardware support.



As diebels said, you can prevent loading of OSS emulation, but there's really neglible benefits to doing so (apart from forcing you to migrate EVERYTHING to ALSA now)

Cheers
mercurus[/QUOTE]

---

