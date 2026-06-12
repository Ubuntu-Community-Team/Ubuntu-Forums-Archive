---
title: "Upgrading causing broken packages (Vuze and VLC)"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by superarmy on 2009-04-24
So far the upgrade has been great although I have noticed two things.

VLC seems to have changed to a more M player like setup where the timeline and tool bar are separate to the video itself. It's nothing major but wondering if it could be changed back.

Main gripe currently though is Vuze appears to be broken. 

terminal gives
```
samuel@hinds-desktop:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```

Any ideas?

---

### Post by superarmy on 2009-04-24
bump

---

### Post by OdSquad64 on 2009-04-25
> **superarmy said:**
> 
Main gripe currently though is Vuze appears to be broken. 

terminal gives
```
samuel@hinds-desktop:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```

Any ideas?

I'm having this exact same problem after the upgrade, I'm still in search of a solution.

---

### Post by Partyboi2 on 2009-04-25
Hi, check that you have you got java6 installed.

---

### Post by OdSquad64 on 2009-04-25
i do have java 6 installed

---

### Post by Icthyo on 2009-04-25
Don't know if this will shed some light.  I installed Vuze by downloading the generic version from Vuze's website.  This was under Hardy.  Worked like a charm; however, I did a clean install to Jaunty but the same vuze installation file was not working.

The Jaunty repositories does have an Ubuntu version of Vuze.  The installation went well; however, it's not the same excellent interface that I'm getting as when I was using Hardy.  I'm not getting the Vuze HD network interface.   If you have any success with this please let me know.

Regards.

---

### Post by itsjustarumour on 2009-04-26
> **superarmy said:**
> terminal gives
```
samuel@hinds-desktop:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```

Any ideas?

Getting same thing here, and still looking for a solution.

Fresh install of 9.04 32bit, Vuze from Ubuntu repos.  I do have Java-6 installed.

---

### Post by Garrovick on 2009-04-26
Looks like VLC is trying to emulate what programs like PowerDVD do.  Have the controls separate from the video window. Must be an "update"

---

### Post by platinumriver on 2009-04-27
See this thread for the Vuze fix.

[http://ubuntuforums.org/showthread.php?t=1133437](http://ubuntuforums.org/showthread.php?t=1133437)

---

### Post by OdSquad64 on 2009-04-30
i did this and it seemed to work, but i think i have a larger problem now.  after upgrading to 9.04 programs just get killed randomly, sometimes right after opening, such as with vuze, sometimes just after sitting there for a while things will close

---

