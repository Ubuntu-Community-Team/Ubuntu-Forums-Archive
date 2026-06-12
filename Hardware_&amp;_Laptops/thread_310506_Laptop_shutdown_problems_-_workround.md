---
title: "Laptop shutdown problems - workround"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by viking777 on 2006-12-01
Since I got a new laptop a few weeks ago I have never been able to shutdown the computer without booting into windows first or holding down the power button. I believe now that I have found a reason for this and that is simply that it will only shut down fully if it is running as root. Since ubuntu does not have a root account by default(and using sudo in a terminal makes absolutely no difference)I was never able to shut down.

I only noticed this problem after installing another distro that does have a root account. This behaves exactly as ubuntu does if running as a normal user (ie the shut down hangs after 'power down' is called) but when running as root user it shuts down fully each time.

I know it is not a solution only a workround, and I have no explanation as to why this occurs but it may help others with the same problem, but if this is your problem you may have to switch distros to cure it unless some clever soul can work out why it is happening.

And that is not me!!

---

### Post by irw on 2006-12-01
Any details re the laptop, version of Ubuntu and what happened when you tried to shutdown from Ubuntu - any error messages, or change onthe screen etc?

---

### Post by styven on 2006-12-03
Hi all,

I too cannot shut down.
I have edgy installed on a hp6310 laptop, when i click the red button top right to shut down, i only have the option to log out, hibernate, suspend, switch user, lock screen. No restart or shut down icons!

Any ideas.

Steve.

---

### Post by styven on 2006-12-03
Also, when i have run updates, the restart icon appears at the top, even if i click this, it only goes back to the log in screen.

---

### Post by GrumpyBob on 2006-12-03
I found the absence of a shutdown choice a little perplexing at first, but:

You can shutdown by choosing Log Out then from "Options" on the login screen you can select "shutdown".
You can shut down by "sudo shutdown now" in a terminal

I find "suspend" to be a little problematic - it sometimes leaves the fan running and won't come back to life - seems to be associated with some applications.

I'm running Edgy on an R52 Thinkpad.  

Robert

---

### Post by viking777 on 2006-12-05
Another idea on this laptop shutdown problem. 

My new laptop has a dual core processor. Up until last night I had no idea that the acronym 'smp' stood for symmetrical mulitprocessing and in other words means that when applied to a kernel revision it is one that is optimised for use on multi core or hyperthreading processors. 

I quickly downloaded an smp kernel of my present OS (not ubuntu so I haven't tested it on that) rebooted and instantly had not only a more responsive OS but an end to my shutdown problems (although I grant you it is early days yet as I only did this last night).

I am not knowledgeable enough to know if this should make a difference but certainly at the moment it seems to, so if you are having shutdown problems with a dual core system and you are not running an smp kernel, give it a go  it just might work.

Later: After several normal shutdowns it has the problem has just returned so in all probability this smp kernel business has nothing to do with it.

---

