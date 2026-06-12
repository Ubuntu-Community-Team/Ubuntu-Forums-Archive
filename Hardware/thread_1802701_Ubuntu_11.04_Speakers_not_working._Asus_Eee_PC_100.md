---
title: "Ubuntu 11.04 Speakers not working. Asus Eee PC 1001PX"
date: 2011-07-12
forum: Hardware
---

### Post by DHAines56 on 2011-07-12
Hello, this is my first post on the forums.
I recently installed Ubuntu 11.04 on my Asus Eee PC 1001PX with Wubi on Windows 7.
Everything works fine except for my sound. I have no sound coming out of the internal speakers. Headphones work fine.
I have looked around for a solution for a while to no avail.:confused:
Can someone please help? Thanks in advance.
Additional Info: Sound card driver is Realtek ALC269VB

---

### Post by sakishrist on 2011-07-12
Hi there,

Try clicking the sound icon and then Sound Preferences. From there, go to the Output tab and where it reads Connector, change that to Analog speakers.

---

### Post by DHAines56 on 2011-07-12
It was already on that option, it does detect the sound card it's just not having sound. The speaker does work because I just tested it in Windows 7 before where it worked fine. And i have made sure that it is not muted.

---

### Post by kraylus on 2011-07-12
i am having the same problem with my asus netbook. for the record, sound worked flawlessly in 10.04. not sure why it wouldnt now. headphones are fine and dandy, but i'd really like to not have to wear them all the time, i have to be able to hear ambient sounds.

i seem to recall there being a config file you could edit for the people that were having the opposite problem. was a matter of changing a single number, but dont remember where i read that.

any help would be much appreciated!

---

### Post by kraylus on 2011-07-12
update: i've found older posts of the reverse problem in the hopes that the solution might fix this problem as well.

[http://ubuntuforums.org/showthread.php?t=1597218](http://ubuntuforums.org/showthread.php?t=1597218)
[http://ubuntuforums.org/showthread.php?t=1624557](http://ubuntuforums.org/showthread.php?t=1624557)

neither of those solutions worked.

not sure where else to go, but maybe it'll work for you guys. good luck.

---

### Post by DHAines56 on 2011-07-12
Ok, I don't know what i did but perhaps when i was messing around with the ALSAMIXER or something else upon reboot I could hear login sounds, I then decided to instantly check my music collection on my Windows Partition. I don't know how but suddenly its working. Thanks for the help!
When I was trying to work it out I used these websites for help and guides.
[SoundTroubleshooting - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SoundTroubleshooting") 
[http://hardforum.com/showthread.php?t=1255697](http://hardforum.com/showthread.php?t=1255697)
[http://ubuntuforums.org/showthread.php?t=551615](http://ubuntuforums.org/showthread.php?t=551615)

Although these websites don't seem to be about 11.04 they still have the same sort of meaning. For those of you still having trouble, I recommend looking at the first link and scrolling down to manual installation. It has alot of useful information, especially on ALSA configuration.
Once again thanks for your help!:D

---

### Post by kraylus on 2011-07-13
ok, im not sure what i did either. in fact, i dont think i did anything. what DID happen tho was i ran the update manager and let it do its thing while i went out on patrols. when i came back, sound was working. granted, i didnt reboot, so i dont think it has anything to do with the updates.

but hey... for anyone else havin the issue, its worth a shot.

---

