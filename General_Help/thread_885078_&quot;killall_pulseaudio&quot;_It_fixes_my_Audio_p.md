---
title: "&quot;killall pulseaudio&quot; It fixes my Audio problem.. BUT .. ??"
date: 2008-08-09
forum: General Help
---

### Post by sendblink23 on 2008-08-09
Yes its works awesome for me

This command fixes the sound Problem:
```
killall pulseaudio
```

But everytime I boot back again "Restart", I still go again without any sound, but yes I have to execute again that command always to have sound Working...

ANY WAYS TO KEEPING THAT COMMAND Permanently *ON* Always for every Boot (Restart) of Ubuntu ??


Also I need help with my Wireless Problem.. here is my Other Thread: HELP ME THERE PLZZ!!! [http://ubuntuforums.org/showthread.php?t=884973](http://ubuntuforums.org/showthread.php?t=884973)

---

### Post by cpetercarter on 2008-08-09
System > Preferences > Sound - change any settings which show pulseaudio to, eg, Alsa. Will that not have the effect you want?

---

### Post by sdennie on 2008-08-09
The above instructions are probably what you need.  If not, you can also add the killall to System->Preferences->Session (or possibly disable pulseaudio from starting from there to begin with).  If you do need to add the startup command, you may want to add it as:

```

sh -c "sleep 10 && killall pulseaudio"

```

That will wait 10 seconds before trying to kill pulseaudio and insure that it's been started before you attempt to kill it.

---

### Post by sendblink23 on 2008-08-09
> **cpetercarter said:**
> System > Preferences > Sound - change any settings which show pulseaudio to, eg, Alsa. Will that not have the effect you want?

> **vor said:**
> The above instructions are probably what you need.  If not, you can also add the killall to System->Preferences->Session (or possibly disable pulseaudio from starting from there to begin with).  If you do need to add the startup command, you may want to add it as:

```

sh -c "sleep 10 && killall pulseaudio"

```

That will wait 10 seconds before trying to kill pulseaudio and insure that it's been started before you attempt to kill it.


Tried both and still .. after Reboot...  still no sounds i always have to execute the "killall pulseaudio"   command to make the sound work   :(

---

### Post by Xuniltoor on 2008-08-09
might try etc/pulse and delete anything in the folder, restart

---

### Post by sendblink23 on 2008-08-09
> **Xuniltoor said:**
> might try etc/pulse and delete anything in the folder, restart

could i just Rename the folder.. so I dont lose it just incase for backup ??

---

### Post by Xuniltoor on 2008-08-09
i was under the assumption you removed pulseaudio. if not i would remove through synaptic. check to make sure you show alsa in all 4 dropdown menus in system,preferences,sound. try that first before you go into the file system. if you feel you still need it you can easily reinstall. pulse is great if its working for you. if its not you can have issues.

---

### Post by sendblink23 on 2008-08-09
> **Xuniltoor said:**
> i was under the assumption you removed pulseaudio. if not i would remove through synaptic. check to make sure you show alsa in all 4 dropdown menus in system,preferences,sound. try that first before you go into the file system. if you feel you still need it you can easily reinstall. pulse is great if its working for you. if its not you can have issues.

hmm  Kill Pulse command.. is shutting down Pulse ..  in other words is working for me.. Not having pulse active ...  Plsu in the sound settings.. if I put Alsa in everything..  wierd is It actually doesnt give me any sound.  Its strange ...  but well yeah doing the kill command actually works for me ....

but yes i will uninstall it... through Synaptic like you mentioned ;)  Because i permanently don't want Pulse working

---

### Post by Xuniltoor on 2008-08-09
you may want to check to make sure alsa is properly installed

---

### Post by Stratok on 2008-10-18
Ok now maby can somebody help me.

with pulseaudio
opera works, firefox, vlc, rythmbox, movie player.

not work: audacity, amsn(works if is only program), skype.

killall pulseaudio:
skype, vlc, opera work simultaneously, 

amsn keeps the same and rythmbox wont work.
audacity worked once with pulseaudio, if i didnt ran any program else than audacity, but now it does not work in any way.


im confused is it a way to keep everything working?:confused:

---

