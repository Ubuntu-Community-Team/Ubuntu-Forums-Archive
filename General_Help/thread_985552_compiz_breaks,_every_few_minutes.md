---
title: "compiz breaks, every few minutes"
date: 2008-11-17
forum: General Help
---

### Post by severean0 on 2008-11-17
Hi I've set up all the desktop effects in compiz and it works fine, for a few minutes... then when activating an effect such as desktop cube or expo, something happens and all the effects are disabled, I'm down to 1 desktop (rather than 4), the screenlets are mucked up and AWN manager disappears. It doesnt crash anything else that I'm running at the time, but I have to restart to get it back to normal. Any ideas? 
Dell inspiron, running intrepid, integrated intel graphics.

---

### Post by severean0 on 2008-11-18
bump. Can anyone help? I have no idea what's causing this 0r what I can d0.

---

### Post by loomsen on 2008-11-18
Read the thread in my sig to fix it. You probably haven't configured your xorg at all yet, some plugins like expo make extensive use of your graphics device. If they aren't set up correctly, they might get autoselected with false values. Thats, or the permission issue I point at as well most likely will be the main problems.

---

### Post by severean0 on 2008-11-18
> **loomsen said:**
> Read the thread in my sig to fix it. You probably haven't configured your xorg at all yet, some plugins like expo make extensive use of your graphics device. If they aren't set up correctly, they might get autoselected with false values. Thats, or the permission issue I point at as well most likely will be the main problems.

hey thanks for the reply. do you mean the thread 0n "Intrepid, compiz with nvidia"? Does this apply to me with intel graphics?

---

### Post by loomsen on 2008-11-18
I don't know if the permissions issue applies, it does for nvidia-cards. Part 2 is just to make sure everything is set up correctly and don't let some autodetect do your job every time again rather than writing it down once.

Your problem however sounds like more intense plugins crash, so obviously sth ain't right. 
If you don't want to configure your xorg for your system, sure you might still run compiz, but it won't work as proposed.

---

### Post by severean0 on 2008-11-18
ok sorry i'm lost, I have intel graphics not nvidia. Do I need to do anything to xorg? All the compiz effects work fine, but just recently the expo plugin has caused this problem where after a while all the effects will crash. I'm new t0 ububtu so i have no idea what I'm doing.

---

### Post by loomsen on 2008-11-18
Well, if you're new you may want to read
[this thread, or post more likely](http://backports.ubuntuforums.com/showthread.php?t=940578)
where I try and explain X in simple words. It's post number 6.

---

### Post by severean0 on 2008-11-19
Thanks for your help loomsen, I've read your posts and have a better idea about what the x-server is now, but I'm still a bit lost. I don't know what I would need to do to xorg. I think I can be a little more specific about my problem now. Like I said, compiz is crashing after several minutes of using effects such as rotate cube and expo. When it crashes, I lose my other desktops and all active windows are bought onto one desktop. If I then go into appearance settings, the effects are set to "none". If I choose "normal" or "extra", everything goes back to normal. I don't know what's causing compiz to crash, given it works fine initially... I'm going to try reinstalling all the compiz packages in synapic, as I can't think of anything else to try! Probably wont help but if anyone has any ideas or is having the same problem let me know!

---

