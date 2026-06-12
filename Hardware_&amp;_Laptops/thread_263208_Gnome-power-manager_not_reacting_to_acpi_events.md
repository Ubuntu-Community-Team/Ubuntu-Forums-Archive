---
title: "Gnome-power-manager not reacting to acpi events"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by househead on 2006-09-22
I tried to upgrade my dapper to edgy last night and it all wen horribly wrong!

Anyway, today I set about rebuilding dapper, which took all of 30 mins. I copied all my homedrive back to the new volume.

Unfortunately however, gnome-power-manager is not reacting to acpi events, which are being displayed correctly in /var/log/acpid and when using "lshal -m"

If I start g-p-m with ac unplugged, it starts with the correct icon. Similarly, if I start the daemon with the plug in, again it displays the correct icon. Plugging or unplugging with the daemon running produces no change.

What's really irritating me is this new system is almost identical to the one it replaced, at least in terms of the packages / config etc.

Where do I start?

TIA

---

### Post by got_nix on 2006-09-25
experiencing the same problem it began last night. the 24.09.06 i was thinking it was something with hal or the dbus but if they hadn't started then the g-p-m wouldn't even start much less run irregularly.. so i'm kinda stumped at the momment.

---

### Post by kekojeep on 2006-10-11
I'm getting this same problem.. g-p-m starts correctly after boot, but doesn't responds to unplugging or plugging the AC power.. don't know since when this is happening, just noticed today (October 11 2006)

---

### Post by vector_prime on 2006-10-12
Same problem here, among a few others.  I have my laptop set to suspend on lid close, managed through gnome-power-manage, which has worked fine for several months now.  A few weeks ago it started behaving strangely.  It would ignore every other lid close.  A few days ago the behavior described above started too.  The battery level is updating properly in all the other battery monitors.

---

### Post by Onyros on 2006-10-12
I'm having the same problem. I just removed the icon, and am using the Battery Charge Monitor instead, even though it has limited functionality compared to G-P-M.

Has someone filed a bug already? I'm on Dapper btw (so it's not specific to Edgy), and it was the last kernel upgrade that created these problems (the battery level not updating).

If I tried to "killall gnome-power-manager" and then restart it, the battery level would update, but that's the only way.

---

### Post by kekojeep on 2006-10-17
Just found out what happened.. what screwed up my Gnome-Power-Manager was an updated version of DBUS from the bmpx (beep-media-player) repository, added when trying to install that program (didn't work by the way).. now I'm unable to force the use of the old version (Dapper original version) because when I try that, Synaptic asks for the removal of A LOT of software, some of them I'm not willing to lose their configuration.

Already took the bmpx repo away from my sources list, but I think I'm gonna have to wait for some DBUS update from Ubuntu's repositories..

[ ]'s

---

### Post by vector_prime on 2006-10-18
My problems started about the time I installed BMPx too.  But it's not (just) the bmpx dbus upgrade.  I took out the repo, uninstalled, bmpx, and forced a downgrade of dbus to the version it was before, and still no updates.  :(  I'm guess there's another package that needs to be downgraded, but I'm not sure which one.

---

### Post by househead on 2006-10-18
I think I may have identified the problem. If I restart DBUS after booting, gnome-power-manager works correctly (woohoo!). Maybe our startup scripts are not starting dbus, or something is killing it on gnome start.

Will investigate this further. Let us know if restarting DBUS works for you.

---

### Post by vector_prime on 2006-10-18
Unforunately not.  Even after a restart it's still not recognizing AC plugin events at least.

---

### Post by kekojeep on 2006-10-18
How do I restart DBUS for testing if it's the same problem?

Thanks for the help! Anything I can do, just ask.

---

### Post by kekojeep on 2006-10-19
Restarted DBUS, no game.. still not working.. looks like the BMPx update screwed up some HAL files too, but I don't know which ones.. :confused: 

Damn music player! ](*,)

[ ]'s

---

### Post by vector_prime on 2006-10-20
> **kekojeep said:**
> How do I restart DBUS for testing if it's the same problem?
```
sudo /etc/init.d/dbus restart
```
It'll kill several processes if you have an X session running, but most of the important ones will restart automatically.  If GPM doesn't restart, you may need to do it manually. ```
gnome-power-manager
```

---

### Post by kekojeep on 2006-10-25
Nevermind, I updated to Edgy, no more problems now.. thanks for the help!

[ ]'s

---

### Post by mbvlist on 2006-10-30
It doesn't help. It updates the information once, but fails to update battery status later. Even the expected run time remains the same, while Battery Charge Monitor shows the right information.

Up to date 6.06, also with BMPx installed (not working)

---

### Post by joerg.weis@baden.cc on 2008-03-11
I have found a fix for that issue it can be found [here]("http://joergweis.wordpress.com/2008/03/11/gnome-power-manager-battery-status-missing/").

---

