---
title: "Dual Monitor - Different Resolutions - Separate Workspace - Hardy"
date: 2008-04-28
forum: Hardware
---

### Post by prepstyles on 2008-04-28
Hello

I searched around a little but couldn't find a specific answer to my problem, apologies if this has been covered before.

I'm running: 
             Nvidia GeForce 7900 GS
             Samsung SyncMaster 931bw (1440x900 wide)
             NEC <something or other> (1280x760)

What I want to do is: have a different workspace with its own resolution on each monitor.  The dual monitor setup on the Nvidia utility keeps trying to spread a single workspace across two monitors and makes a mess of the resolution.

Has anybody managed to map workspaces to a specific monitor while managing to keep them both independent resolution wise?

Cheers!

---

### Post by kaiataris on 2008-04-28
you should be able to do this with the nvidia settings tool...

```
sudo apt-get install nvidia-settings
```

once it's installed you can find it under System>Administration
or you can run it via

```
sudo nvidia-settings
```

There's an section in the tool for multiple displays where you can pick Twinview or separate sessions

-Kai

---

### Post by prepstyles on 2008-04-28
> you should be able to do this with the nvidia settings tool...

Code:

sudo apt-get install nvidia-settings

once it's installed you can find it under System>Administration
or you can run it via

Code:

sudo nvidia-settings

There's an section in the tool for multiple displays where you can pick Twinview or separate sessions

-Kai 


I appreciate the reply:

I'd played with nvidia-settings but couldn't get exactly what I wanted.

What I want to do is map a workspace to each monitor.

That way I can right click the task bar and send programs to the other window in this way.

I've actually got it configured in a way that I don't' hate right now so that is nice; however, ideally I would like them mapped to the different work spaces ... I'm not even sure if that is possible or not though.

Regards.

---

### Post by kaiataris on 2008-04-28
ah I see, I don't think that's possible yet...I've got a geforce 7600 GT and both displays are locked to the same workspace. It is weird that it can see the separate monitors but merges them into one X screen.

You might be able to do what you want by making a custom xorg.conf file
that doesn't use twinview or xinerama, but then you'd probably lose the ability to have seperate resolutions and bitdepths for each monitor.

-Kai

---

### Post by catmur on 2008-06-16
Hi, 

Did you ever find a solution to this?
I have the same issue. I'd like to get Desktop Cube and Rotate cube working on both screens..

I currently have 4 panels working fine on the left screen, but two on the right screen (monitors set up running separate X sessions). Any time i add a pannel, even when focus is on the right hand screen, it adds the panel to the left hand screen. :-(

---

### Post by arthur00 on 2008-11-07
Hi, I am also looking for a solution to this, I use my TV as my working screen and I like to have 4 panels =(

---

### Post by arthur00 on 2008-11-07
I got it, using compiz fusion go to System->Preferences->Advanced Desktop Effect Settings then go to General Options->Desktop Size. There you can set your second window panels

---

### Post by firfin on 2010-01-17
> **catmur said:**
>  Any time i add a pannel, even when focus is on the right hand screen, it adds the panel to the left hand screen. :-(

You can drags the panels to where you want. Hold down the ALT key while dragging (in 9.10 at least)

---

### Post by nodegamra on 2010-03-23
> **arthur00 said:**
> I got it, using compiz fusion go to System->Preferences->Advanced Desktop Effect Settings then go to General Options->Desktop Size. There you can set your second window panels

Nice, that is what I needed.
Thanks!

---

