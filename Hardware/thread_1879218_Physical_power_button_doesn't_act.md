---
title: "Physical power button doesn't act"
date: 2011-11-11
forum: Hardware
---

### Post by anikol on 2011-11-11
Just moved to Lubuntu 11.10 from Ubuntu 11.10 and the physical power button stopped working. It neither shuts down the PC nor displays a shutdown dialogue. The problem is quite vital to solve because the PC is a flat panel station with Atom D525 CPU and is supposed to function without keyboard and mouse, with the touch panel only running one application without any chance to exit and shutdown the PC from menus.

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2011-11-11
Check out the links:
[http://askubuntu.com/questions/460/how-to-shutdown-the-computer-when-hitting-the-power-button](http://askubuntu.com/questions/460/how-to-shutdown-the-computer-when-hitting-the-power-button)
[http://askubuntu.com/questions/72888/how-can-i-enable-the-power-button-on-my-server/72900#comment82686_72900](http://askubuntu.com/questions/72888/how-can-i-enable-the-power-button-on-my-server/72900#comment82686_72900)

---

### Post by anikol on 2011-11-11
A confusing moment is that I am trying Lubuntu just out-of-box (clear installation) and wondering if it doesn't work at my PC does it work at other ones?

---

### Post by mikewhatever on 2011-11-11
When I tested Lubuntu, the power button shut down didn't work as well.

---

### Post by Rodney9 on 2011-11-11
```
sudo shutdown -P now
``` in a terminal will shut you down.

Shutdown icon missing is discussed here -http://ubuntuforums.org/showthread.php?t=1860263

If you still have problems may I suggest you post it in the Lubuntu One Stop Group - [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

You will also see a lot more How To's, Tips and Screen Casts on the page.


Rodney

---

### Post by MoreOrLess on 2011-11-11
Does Lubuntu load acpid to handle the button press?

---

### Post by anikol on 2011-11-17
> **Rodney9 said:**
> ```
sudo shutdown -P now
``` in a terminal will shut you down.
Shutdown icon missing is discussed here -http://ubuntuforums.org/showthread.php?t=1860263
```
sudo shutdown -P now
``` works fine and the problem is only with the physical shutdown button. Shutting down from icon also works.

> **MoreOrLess said:**
> Does Lubuntu load acpid to handle the button press?
Out-of-the-box Lubuntu doesn't provide acpid package. But the problem hasn't gone even after I installed it.

Finally, I found a solution removing all code lines in powerbtn.sh except the last one ```
/sbin/shutdown -h now
```. It seems like the shutdown signal became missed somewhere during its processing in the script. My workaround shuts down the PC without any alternatives and it perfectly suits my particular needs.

---

### Post by marinara on 2011-11-17
power button (to power off)
doesn't work on my desktop either.  

the same power button works fine in another operating system.

---

### Post by marinara on 2011-11-17
> **mikewhatever said:**
> Check out the links:
[http://askubuntu.com/questions/460/how-to-shutdown-the-computer-when-hitting-the-power-button](http://askubuntu.com/questions/460/how-to-shutdown-the-computer-when-hitting-the-power-button)
[http://askubuntu.com/questions/72888/how-can-i-enable-the-power-button-on-my-server/72900#comment82686_72900](http://askubuntu.com/questions/72888/how-can-i-enable-the-power-button-on-my-server/72900#comment82686_72900)


Running Lubuntu Oneric, followed instructions (mostly).
installed acpid, removed the comment on the shutdown line
 Pressing powerbutton wrecked the system, my machine tried to suspend, but couldn't do it, eating all my RAM and CPU.

you are warned.

---

### Post by marinara on 2011-11-17
**removed

---

### Post by mikewhatever on 2011-11-19
> **marinara said:**
> Running Lubuntu Oneric, followed instructions (mostly).
installed acpid, removed the comment on the shutdown line
 Pressing powerbutton wrecked the system, my machine tried to suspend, but couldn't do it, eating all my RAM and CPU.

you are warned.

Can you post the content of the file you edited. Why was the shutdown commented out?

---

### Post by marinara on 2011-11-19
actually, i don't need help fixing the power button, i need to remove the damn acpid thing.  I left my machine on last night and it was not responding when i tried to log in.

I'm gonna try "apt-get purge acpid" or is it apt-get install --remove

---

