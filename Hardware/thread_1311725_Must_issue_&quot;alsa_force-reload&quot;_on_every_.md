---
title: "Must issue &quot;alsa force-reload&quot; on every boot-up to get sound working"
date: 2009-11-02
forum: Hardware
---

### Post by Tryfon on 2009-11-02
Well the title says it all I guess. I don't get any sound at all every time I boot up and if I check in sound preferences I only see a "dummy device". After I issue "sudo alsa force-reload" the sound seems to be working all right. Any explanation?
I know that a possible workaround is to load a script on start up with the above command but I am looking for the reason and a solution, not a workaround.
I get the impression that a lot of other people are getting the same problem.

---

### Post by trigoman05 on 2009-11-05
I have the same issue, I'm running Karmic 32-bit.

---

### Post by moonoo on 2009-11-06
Same here, tried to be smart and set a script to run at boot time but didnt work.

perhaps this is a bug?

**Update:**

I am at work but I am going to make sure that I am member of 'audio'

sudo usermod -G audio <user>

more info:
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/430515](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/430515)
[https://bugs.launchpad.net/ubuntu/+bug/473519](https://bugs.launchpad.net/ubuntu/+bug/473519)

---

### Post by monkeys on 2009-12-21
Same problem! For about a week, an update fixed the sound for me, but the issue is back again.

I switch between USB speakers and my analog laptop sound, but earlier, there was no problem.

My output says 'dummy' too.

---

### Post by RodGer GR on 2010-01-02
&#915;&#949;&#953;&#945; &#963;&#959;&#965; &#932;&#961;&#973;&#966;&#969;&#957;&#945;. &#925;&#959;&#956;&#943;&#950;&#969; &#960;&#969;&#962; &#941;&#967;&#969; &#956;&#949;&#961;&#953;&#954;&#941;&#962; &#953;&#948;&#941;&#949;&#962; &#957;&#945; &#960;&#961;&#959;&#964;&#949;&#943;&#957;&#969; &#960;&#959;&#965; &#943;&#963;&#969;&#962; &#955;&#973;&#963;&#959;&#965;&#957; &#964;&#959; &#960;&#961;&#972;&#946;&#955;&#951;&#956;&#945;.

I had exactly the same problem. I used to give the 'sudo alsa force-reload' command every time I started my laptop. Finally, I managed to solve my problem by removing the proprietary driver named "Software modem". To do this you have to go to 
System (located on the top panel by default) -> Administration -> Hardware drivers
and choose to remove the 'Software modem' driver. This worked for me. I hope it works for you too. Whoever tries this, please provide some feedback.

Of course, the above is not a total solution. You could say it's a workaround but definitely a better work-around and we're also closer to a real solution since we're closer to the real problem.
The reason of this problem seems to be the bug described [here(link)]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762") . 
It would be helpful if you could provide more info running in terminal the command:
```
apport-collect 449762
```(Select 'change anything' when it asks for access level.)

Another work-around I would suggest is to run:
```
gksudo gedit /etc/default/pulseaudio
```and change the line
```
PULSEAUDIO_SYSTEM_START=0
```to
```
PULSEAUDIO_SYSTEM_START=1
```

But!!! for now, the last work-around seems to make my audio icon disappear from the notification area (and it is not related to the known bug of the notification area). I'll investigate deeper this issue when I have more time available.

Have a happy and creative new year everybody :P &#922;&#945;&#955;&#942; &#935;&#961;&#959;&#957;&#953;&#940;!
&#915;&#953;&#974;&#961;&#947;&#959;&#962;.

---

