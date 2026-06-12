---
title: "Laptop Shutdown issues"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by anoopyadav on 2007-08-28
Hi, Ubuntu is the first linux distro I've tried in quite a while & is one of my favourites. But there is one issue I'd like to get off my back:

When the system is shutting down, I hear a loud *click* sound right before the power goes off.
Is this anything serious?????

---

### Post by wieman01 on 2007-08-28
> **anoopyadav said:**
> Hi, Ubuntu is the first linux distro I've tried in quite a while & is one of my favourites. But there is one issue I'd like to get off my back:

When the system is shutting down, I hear a loud *click* sound right before the power goes off.
Is this anything serious?????
Could be a 'parking' harddisk. My makes a 'click' sound as well.

---

### Post by anoopyadav on 2007-08-28
Heres the scoop. I did some research & it turns out that on "older" drives, it was ususal to hear a *clunk* whenever one shuts down because of a spring thats attached to the head which pulls the head up form the surface.

So is it okay??? I installed windows xp on my laptop & did a routine shutdown. No clunk. What HAPPENED? I did it again under ubuntu. I then booted the slax live CD & then shutdown. No clunk.

So it figures its a problem with ubuntu 7.04.

I'm using acer aspire 3684Nwxmci. Which one are you using.
Has anyone else had this problem???

---

### Post by wieman01 on 2007-08-28
I have a Sony Vaio VGN on Kubuntu 7.04. I have issues with the HD spinning up & down at random which has more to do with power management, but which is annoying nevertheless. 

I have read other threads concerning complaining about HD management in Ubuntu. Dunno if they are substantiated.

---

### Post by tgellen on 2007-08-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/67810](https://bugs.launchpad.net/ubuntu/+bug/67810) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
I noticed this too on both my Acer Aspire 9303 and my Toshiba Portege 4000. But the solution was simple. I followed the instructions at  [https://bugs.launchpad.net/ubuntu/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+bug/67810/comments/60), using sudo -i at a terminal, and it has made the *clunk* go away. 

As a side note it doesn't seem to happen in Gutsy Tribe 4 (newer kernel). :)

---

### Post by wieman01 on 2007-08-28
> **tgellen said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/67810](https://bugs.launchpad.net/ubuntu/+bug/67810) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
I noticed this too on both my Acer Aspire 9303 and my Toshiba Portege 4000. But the solution was simple. I followed the instructions at  [https://bugs.launchpad.net/ubuntu/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+bug/67810/comments/60), using sudo -i at a terminal, and it has made the *clunk* go away. 

As a side note it doesn't seem to happen in Gutsy Tribe 4 (newer kernel). :)
Do you know anything about harddisk noise due to power management? I am having that issue.

---

### Post by tgellen on 2007-08-29
Sorry. I haven't noticed  any spindown issues through power management. I'll keep my eyes and ears open and see if it happens on any of my 3 Ubuntu systems. They've got SATA, PATA and Compact Flash drives I can monitor. 

Have you tried modifying the harddrive settings using **hdparm** especially the **-B** and **-S** options which sets the Advanced Power Management and spindown timeout. If modifying the hdparm settings works you can set it permanently in /etc/hdparm.conf

*** Please read the man page of hdparm carefully.

---

### Post by anoopyadav on 2007-08-29
Thanks a bunch. I was going to uninstall ubuntu from my system today but the command u gave made the clunk go away. Now I'm a happy fiesty user.:KS:guitar:

---

### Post by wieman01 on 2007-09-03
> **tgellen said:**
> Sorry. I haven't noticed  any spindown issues through power management. I'll keep my eyes and ears open and see if it happens on any of my 3 Ubuntu systems. They've got SATA, PATA and Compact Flash drives I can monitor. 

Have you tried modifying the harddrive settings using **hdparm** especially the **-B** and **-S** options which sets the Advanced Power Management and spindown timeout. If modifying the hdparm settings works you can set it permanently in /etc/hdparm.conf

*** Please read the man page of hdparm carefully.
I posted a solution here:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

You were right, it's the -B setting.

---

### Post by tgellen on 2007-09-06
Excellent. Glad it worked. 

Found out how you can also set this in **/etc/hdparm.conf** 

e.g. if your hard drive is **/dev/hda** you could add a section as follows
```

/dev/hda {
apm = 254
}

```
which should also work after a reboot.

Check out **/etc/hdparm.conf** for a full list of commands and examples.

Cheers,
Al.

---

