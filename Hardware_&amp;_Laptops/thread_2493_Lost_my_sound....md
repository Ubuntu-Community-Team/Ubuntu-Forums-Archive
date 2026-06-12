---
title: "Lost my sound...?"
date: 2004-10-28
forum: Hardware &amp; Laptops
---

### Post by herweg on 2004-10-28
Well, just when I thought I finally had Ubuntu up and running exactly the way I liked it, I go ahead and boot it, only to find my sound is gone. Up until this point, it has been working fine, I have a SB Extigy (USB sound) which it has been ignoring (I don't have a problem with that) and on-board sound on my motherboard. It has been using the on-board sound with absolutely no trouble at all, I let it use the speakers in my monitor. However, after I got gimp-print installed for my printer, and I edited XF86Config-4 so that only one mouse entry was present (which solved the issues I was having, making me VERY HAPPY) I lost my sound. I had to reboot for whatever reason, and when it booted up, I had no sound. None of the simple solutions I have tried so far have worked. The only clue I can see is in my boot messages, where it says 
```
Intel ISA PCIC probe: not found.
Device 'i823650' does not have a release() function, it is broken and must be fixed.
Badness in device_release at drivers/base/core.c:85
 [<c018be98>] kobject_cleanup+0x40/0x65
 [<d08abe11>] init_i82365+0x6f/0x179 [i82365]
 [<c012b222>] sys_init_module+0xe3/0x1d4
 [<c0105f49>] sysenter_past_esp+0x52/0x71
```

If anyone has ideas, it would be GREATLY appreciated. I would even be willing to use the extigy, provided there is a truly viable solution. The last time I tried using it in Linux was under Mandrake, and it only worked some of the time, some programs wouldn't recognize it, it was a real mess. However, if all that has been fixed, then I would be more than willing to use it. 

Thanks in advance
Herweg

---

### Post by kamstrup on 2004-10-29
[QUOTE=herweg]Well, just when I thought I finally had Ubuntu up and running exactly the way I liked it, I go ahead and boot it, only to find my sound is gone. Up until this point, it has been working fine, I have a SB Extigy (USB sound) which it has been ignoring (I don't have a problem with that) and on-board sound on my motherboard. It has been using the on-board sound with absolutely no trouble at all, I let it use the speakers in my monitor. However, after I got gimp-print installed for my printer, and I edited XF86Config-4 so that only one mouse entry was present (which solved the issues I was having, making me VERY HAPPY) I lost my sound. I had to reboot for whatever reason, and when it booted up, I had no sound. None of the simple solutions I have tried so far have worked. The only clue I can see is in my boot messages, where it says 
```
Intel ISA PCIC probe: not found.
Device 'i823650' does not have a release() function, it is broken and must be fixed.
Badness in device_release at drivers/base/core.c:85
 [<c018be98>] kobject_cleanup+0x40/0x65
 [<d08abe11>] init_i82365+0x6f/0x179 [i82365]
 [<c012b222>] sys_init_module+0xe3/0x1d4
 [<c0105f49>] sysenter_past_esp+0x52/0x71
```

If anyone has ideas, it would be GREATLY appreciated. I would even be willing to use the extigy, provided there is a truly viable solution. The last time I tried using it in Linux was under Mandrake, and it only worked some of the time, some programs wouldn't recognize it, it was a real mess. However, if all that has been fixed, then I would be more than willing to use it. 

Thanks in advance
Herweg[/QUOTE]
 I also had a problem where my sound suddenly was gone for no apparent reason (it had worked for a few days). Hacking around I realized that it had been muted in the mixer somehow (Ie. the volume conrol applet and Rhythmbox both showed that there /was/ sound).

So my question is: Is your mixer created correctly? I mean, do you have the Volume Applet running? If so, try right-clicking it and change a few settings in the volume manager.

Cheers,
kamstrup

---

### Post by diebels on 2004-10-29
Well, my extigy is kind of working. It seems to work with oss only , not alsa. I'm able to control it with gnome-volume-control. When I run "/etc/init.d/alsa start" it is not found.

Anyway it works ok with oss, only problem being the volume sounds like 60% when it is set to full.

I have disabled my onboard sound with hotplug blacklisting since the sound quality sucks, but thats kind of irrelevant I guess.

Checking for muting is always smart.

---

### Post by diebels on 2004-11-02
Blacklisting the module "audio" fixed my extigy
```
sudo echo "audio" >> /etc/hotplug/blacklist.d/myblacklist
```
Now I have full volume and nice OSS and ALSA mixers

---

### Post by diebels on 2004-11-02
Opened bug #3160 on it

---

### Post by r00 on 2005-02-28
mine says it the extigy is installed and none of the volume controls are muted..
i tried the blacklisting method without much luck ... [B]and i'd like to try switching to oss and see if that helps, but i have no clue how to do that? can anyone please help?
[/B]
i have to admit, though, that ubuntu is the first distro that actually installed my extigy and found my ipod straight from install..  

..now if only i could get my sound to work :)

---

### Post by Hiroshima on 2007-01-25
I just lost my sound as well (Ubuntu), and seeing the above suggestion of right clicking the speaker icon on my panel worked.  Here's what I did:

right click on the speaker (volume control) icon
Open volume control
under the "playback" tab unmute all the options, (by clicking on the buttons on the bottom of the window) 

It worked for me.  I hope it is just as easy for you.

Hiroshima

---

### Post by Hiroshima on 2007-01-25
Sorry, re-read your post, and you already tried that.

Good luck,

Hiroshima

---

