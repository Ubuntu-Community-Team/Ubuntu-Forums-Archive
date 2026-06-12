---
title: "[SOLVED] Stuck in &amp;quot;low-graphics&amp;quot; mode"
date: 2008-07-11
forum: General Help
---

### Post by Ataris on 2008-07-11
I updated my NVIDIA drivers, and everything was working fine. When I next started up my computer, the drivers were disabled (I found that out later), and so Ubuntu decided to plunge me into "low-graphics" mode. I got to GNOME okay, but the highest resolution I can get is 640x480 -- I cannot work like this. I reenabled the NIVIDIA drivers, but nothing happens. I've tried rebooting (several times), but I'm still stuck. Can someone tell me how to get back into "high-graphics" mode?

---

### Post by nikgare on 2008-07-11
How did you update the drivers?

---

### Post by jjocsak on 2008-07-11
> **Ataris said:**
> I updated my NVIDIA drivers, and everything was working fine. When I next started up my computer, the drivers were disabled (I found that out later), and so Ubuntu decided to plunge me into "low-graphics" mode. I got to GNOME okay, but the highest resolution I can get is 640x480 -- I cannot work like this. I reenabled the NIVIDIA drivers, but nothing happens. I've tried rebooting (several times), but I'm still stuck. Can someone tell me how to get back into "high-graphics" mode?


The same thing happened to me. I re-installed Ubuntu and then reloaded the latest Nvida drivers. 

It only went back to normal resolution (1280x1024) when I shut down (not restart) and powered back on.

Jeff

---

### Post by Kane_of_NOD on 2008-07-11
is the monito configured?

it maybe a monitor configuration problem..

if, the frequency or the resolution are your monitors out of range; you should congifure it..

and then, go to synapic and install nvidias drivers.

to enable monitor configuration .. you should to right click over 'Applications' menu, and then: edit menu, go to 'Others' and choose the one about monitors/screens and grafics  (i am using portuguese, sorry)

and then, close that window.. and go to Applications - others - and the previous selected option.. and then configure your monitor...


after this, make sure your drivers are correctly installed... 
and then.. just reboot..

it would be fine  =D:guitar:

---

### Post by frecon on 2008-07-11
I have the same problem. Really annoying. I have a GeForce 8400M GS. The drivers I use is the one in EnvyNG. After an automatic update yesterday the envy driver was disabled after reboot and I can't get it too work. Now all sorts of stuff seem to be unstable. Maybe it's just me being paranoid, I can't remember any situation now. But anyhow, I would love to get help with the nvidia driver.

---

### Post by Ataris on 2008-07-11
I know the monitor works. I've had the PC for a month before I updated the drivers, it went up to 1600x1200.

Are you saying that I have to reinstall Ubuntu to fix this? Won't that format my harddrive? I have a lot of documents...

I still have my Live CD of 8.04, so I'll install if I have to.

Is there a way to manually switch from low graphics mode?

---

### Post by gwoodruff on 2008-07-11
Are you running Hardy? 
If so make sure your Nvidia drivers are in use:
System/Administration/Hardware
If they are launch a terminal and try

sudo displayconfig-gtk

Make sure your monitor is selected.

If all that fails you may want to go back to the previous driver.

Gary

---

### Post by Fixman on 2008-07-11
Oh god.
Open a terminal.
Write:

```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by frecon on 2008-07-11
It seem to me that i've fixed it.

First I couldn't install anything because I didn't have any space left. I ran the following commands to free up some (thanks to this [thread]("http://ubuntuforums.org/showpost.php?p=5116279&postcount=2")):

clean out apt-cache
```
sudo apt-get clean
```

remove archived logfiles
```
sudo rm /var/log/*.gz
```

remove unnecessary dependencies that are no longer required
```
sudo apt-get autoremove
```

Then I installed the packages that I couldn't install at the first place with:
```
sudo apt-get -f install
```'

After that I ran envyng and installed the nvidia driver. Reboot and back to normal. Finally! wee :)

---

### Post by Ataris on 2008-07-11
Thanks for the help everyone.

---

### Post by frecon on 2008-07-12
> **Ataris said:**
> Thanks for the help everyone.
Does it work now?

---

### Post by Ataris on 2008-07-12
Yeah, sorry, I didn't have time to post. Those two xorg lines fixed the problem. I had to go back and reenable the drivers and effects, but I'm back to my plethora of large resolutions. Thanks.

For future readers, I had this problem again, but fixed it by following the directions of LAST post in this thread:

[http://ubuntuforums.org/showthread.php?t=870013&page=2&highlight=low+graphics](http://ubuntuforums.org/showthread.php?t=870013&page=2&highlight=low+graphics)

---

