---
title: "some programs running slow after upgrade to jaunty"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by kiprit on 2009-04-28
I have a strange problem after the upgrade:

The upgrade went relatively smoothly. I used update manager, stopped the update once out of my own mistake (do not watch movies while upgrading :) ). But when i resumed it went fine. And now almost everything runs smoothly.

My problem is that some programs became incredibly slow. The strange thing is that these are not programs that can become slow: For exemple right clicking on gnome panel and selecting properties... when i do that the display box comes 1 minute later. Same or more waiting time goes with AWN manager and deluge. 

When I check system monitor, there is nothing strange... and when I open other programs like gimp, digikam, firefox, and many others i do not wait at all... even when i open everything at the same time.... they seem at worst as fast fast intrepid. 

what can be causing some of the programs go so slow?

---

### Post by lovinglinux on 2009-04-28
I don't know if this is your problem, because the delay you reported is extremely high, but I just noticed that Firefox becomes less responsive when I'm downloading with Deluge. So if you were using Deluge when these issues occurred, try closing it a check if the problem goes away. Just guessing.

---

### Post by emigdio on 2009-04-28
Wow, I thought that it was only me, but it has exactly the same behaviour. Some basic windows oppening are really slow, like 1 min waiting before appearing. It was working perfectly in 8.10.

I noticed that only GTK apps have this problem. One example is right clicking to the panel and enter to the properties. Another example is AWN, when I try to open its config window there is a delay of about 30 secs, but AWN itself runs very fast. Evolution is same.

The weird thing is that most of the apps runs smootly.
I upgraded from 8.10 to 9.04. I have gnome + compiz.

And just to clarify, this is separated to the firefox issue.

---

### Post by kiprit on 2009-04-29
> **lovinglinux said:**
> I don't know if this is your problem, because the delay you reported is extremely high, but I just noticed that Firefox becomes less responsive when I'm downloading with Deluge. So if you were using Deluge when these issues occurred, try closing it a check if the problem goes away. Just guessing.

No with me once they start working there is no problem. I also read in the deluge forums that there are several people complaining. However, [the solutions that I found there]("http://http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16555") did not work for me.

---

### Post by kiprit on 2009-04-29
> **emigdio said:**
> Wow, I thought that it was only me, but it has exactly the same behaviour. Some basic windows oppening are really slow, like 1 min waiting before appearing. It was working perfectly in 8.10.

I noticed that only GTK apps have this problem. One example is right clicking to the panel and enter to the properties. Another example is AWN, when I try to open its config window there is a delay of about 30 secs, but AWN itself runs very fast. Evolution is same.

The weird thing is that most of the apps runs smootly.
I upgraded from 8.10 to 9.04. I have gnome + compiz.

And just to clarify, this is separated to the firefox issue.

I also do have gnome + compiz and did upgrade from 8.10 to 9.04. Probably we are going through the exact same problem (I am using thunderbird instead of evolution so I do not know about evolution)

I was thinking that the issue had something to do with the python. BUt I do not know what can exactly be the issue here.

---

### Post by sepimour on 2009-04-29
Same problem here :'(

I also had Compiz and 8.10 and upgraded to Jaunty on my work laptop [Lenovo T500].
After the update I have this exact problem and I reaaaaaally dont want to 
reinstall, because that will mean that I will have to setup my dev environment again. arrrrgh.

Strangely I did **not** get this problem on my desktop 
[Intel Q6600, ASUS P5Q, Nvidia 9800GTX] which had the same setup software wise.

*edit
Just checked and on my laptop a simple operation like restoring Rhythmbox from a maximized state will use 75% of my CPU.
It is during this spike in CPU usage that the window feels unresponsive. :(

---

### Post by sepimour on 2009-04-29
Ok I think I found my problem over here: [http://ftbeowulf.wordpress.com/2009/04/28/lenovo-t500-and-jaunty-not-happy/](http://ftbeowulf.wordpress.com/2009/04/28/lenovo-t500-and-jaunty-not-happy/)

Seems like a clean install gave the same issue.

Only question now is: wait for a driver update or fall back to 8.10...

---

### Post by kiprit on 2009-04-29
> **sepimour said:**
> Same problem here :'(
Just checked and on my laptop a simple operation like restoring Rhythmbox from a maximized state will use 75% of my CPU.
It is during this spike in CPU usage that the window feels unresponsive. :(

I think that we do not have the same problem. Because when I tried these freezing programs my cpu usage did not increase at all... I just checked all of them.... for exemple deluge just waits for more than one minute with consuming 0% of cpu and 0MBs of memory. When it consumes 2% of CPU it comes back alive.
It is simply "sleeping" for a minute.

---

### Post by kiprit on 2009-04-30
A miracle?

Last night I had left my computer running, and as I last checked nothing had changed. this morning when I came back the internet was gone. I played with /etc/network/interfaces and no change was happening. I realized that I had to reboot my router. 
After my internet came back, i started deluge and voila! starting in a second! others work perfectly too. I literally did nothing, no update; no playing with settings...

the options:
a. a secret trick embedded in the code: mess with your network settings, revert to original; reboot your router. solve your freezing problems!
b. gnome has really gnomes. they came out while I was sleeeping after stealing a couple of underwears they decided to fix my system.
c. jaunty was just being lazy, after a good night sleep and rest is now running like crazy
d. it's a  kind of magic

---

### Post by sepimour on 2009-04-30
Awesome same thing here. Started my laptop at work today and everything is snappy. :D

---

### Post by lovinglinux on 2009-04-30
> **kiprit said:**
> A miracle?

Last night I had left my computer running, and as I last checked nothing had changed. this morning when I came back the internet was gone. I played with /etc/network/interfaces and no change was happening. I realized that I had to reboot my router. 
After my internet came back, i started deluge and voila! starting in a second! others work perfectly too. I literally did nothing, no update; no playing with settings...

the options:
a. a secret trick embedded in the code: mess with your network settings, revert to original; reboot your router. solve your freezing problems!
b. gnome has really gnomes. they came out while I was sleeeping after stealing a couple of underwears they decided to fix my system.
c. jaunty was just being lazy, after a good night sleep and rest is now running like crazy
d. it's a  kind of magic

I noticed that when the firewall is completely locked (no outbound or inbound connections allowed) and you start Deluge, it freezes. The interface is displayed, but nothing about the current torrents are showed and you cant click on anything. If you then disable the firewall, Deluge comes back to life immediately.  So I guess if you don't have a proper connection, then Deluge goes crazy.

---

