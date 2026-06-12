---
title: "Serious OVERHEAT due to suspend! HDD kill."
date: 2012-05-19
forum: Hardware
---

### Post by rk0r on 2012-05-19
Ok, so i closed the lid after a session, left the house and on my return i opened the lid only to find the screen still on with mouse movement but no disk activity, the laptop was very hot! - should be sleeping with screen off.

*I restarted the machine, the fans started going mad and the bios screen was halted.
*Restarted again got past the bios screen and the HDD was not recognised.
  I  opened the laptop up to check if the HDD’s were seated correctly, they were! And VERY VERY HOT..
  My conclusion is that the system decided to go into half a suspend mode with the GPU running full YET the fans disabled – this with a closed lid causes a massive heat issue.
  I think there needs to be some investigation around this matter as it could be a serious problem.
  Has anyone else had this problem ?

---

### Post by Redblade20XX on 2012-05-19
Try looking into the system logs. Usually when stuff like this happens to me its usually a configuration file problem.

-Red

---

### Post by rk0r on 2012-05-20
> **Redblade20XX said:**
> Try looking into the system logs. Usually when stuff like this happens to me its usually a configuration file problem.

-Red

[FONT=&quot]What sort of configuration would cause this ? I only use the standard suspend settings?

It scares me to think that if i were to have left the laptop in this state my HDD would have been damaged / my GPU card would have gone pop. 

If the system is in suspend does this automatically turn the fans off regardless if the system is running dangerously high temperature?.
 
 [/FONT]

---

### Post by ts3 on 2012-05-20
> **rk0r said:**
> Ok, so i closed the lid after a session, left the house and on my return i opened the lid only to find the screen still on with mouse movement but no disk activity, the laptop was very hot! - should be sleeping with screen off.

Could be hardware or software related.  An old dell laptop of mine with windows XP used to do that every couple of months or so & I believe it was a hardware issue, never bothered to do anything about it.  

Similar thing but definitely software related happened on a different laptop with a linux distribution (not ubuntu) when a bad update messed up with ConsoleKit and dbus.  It wouldn't go to sleep and the internet and mounting USBs were messed up so I had some fun trying to fix it.

I'd suggest taking a look at dbus (not sure how that works in ubuntu though) but the issue also  could be hardware related or a random glitch.  It's generally a good idea when closing the lid on a laptop to wait a few seconds to make sure it spins down (you can hear it even on a laptop with an ssd).  

Not sure if any of this is any help but thought I'd mention it.

Cheers

---

### Post by nrundy on 2012-05-20
> **rk0r said:**
> Ok, so i closed the lid after a session, left the house and on my return i opened the lid only to find the screen still on with mouse movement but no disk activity, the laptop was very hot! - should be sleeping with screen off.

*I restarted the machine, the fans started going mad and the bios screen was halted.
*Restarted again got past the bios screen and the HDD was not recognised.
  I  opened the laptop up to check if the HDD&#8217;s were seated correctly, they were! And VERY VERY HOT..
  My conclusion is that the system decided to go into half a suspend mode with the GPU running full YET the fans disabled &#8211; this with a closed lid causes a massive heat issue.
  I think there needs to be some investigation around this matter as it could be a serious problem.
  Has anyone else had this problem ?

I've heard lots of reports of this. It appears to be a GNOME 3 issue. **Is GNOME 3 going to melt your laptop? **[http://blogs.gnome.org/hughsie/2011/02/02/is-gnome-3-going-to-melt-your-laptop/](http://blogs.gnome.org/hughsie/2011/02/02/is-gnome-3-going-to-melt-your-laptop/)__[]("http://blogs.gnome.org/hughsie/2011/02/02/is-gnome-3-going-to-melt-your-laptop/")

---

