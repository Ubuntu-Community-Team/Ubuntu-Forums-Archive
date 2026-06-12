---
title: "Urgent: Lost USB stick auto-mount"
date: 2008-10-16
forum: General Help
---

### Post by Thanh-BKK on 2008-10-16
Hi.

This shall not be a rant, BUT my perfectly running system, after i foolishly updated it, now has a bug.

When i plug in my USB stick (Kingston), it used to mount by itself and open a Nautilus window where i could see the files on the device.

Now, after i did an update (up to date in everything as of today), this no longer happens. I plug in the USB stick and nothing at all happens.

Then i open a terminal and type "lsusb" and it is NOT shown.

HOWEVER (!!) right after that, it does mount and the window opens!

Can i PLEASE get back the regular auto-mount like i had before? It's bad enough that despite the update the transfer speed is still absolutely horrible slow (which was my reason to do the update). 

I appreciate any advice, many thanks in advance.

Kind regards.....

Thanh

PS Ubuntu 8.04 Hardy, Kernel 2.6.24-21-generic, 32 bit. Previous kernel was 2.6.24-16-generic and that worked flawless, but equally dog-slow, 45 MINUTES for 4 gigabytes.

---

### Post by Pro-reason on 2008-10-17
Are you saying that the lsusb command mounts it?

---

### Post by Thanh-BKK on 2008-10-17
> **Pro-reason said:**
> Are you saying that the lsusb command mounts it?

Hi :)

Yes, something like that. Normally, "lsusb" shows the connected USB devices. In my case now, the connected USB stick is NOT shown, however right after that (few seconds) the stick IS mounted, and when i do the "lsusb" again it also shows up properly.

I have tried that 4 times, waiting different amounts of time to see if it was just a coincidence that it mounted after that command, but regardless if i wait 10 seconds or 5 minutes - nothing at all happens "by itself" until i type that command into a terminal.

It is nothing tragic, however these little quirks do annoy greatly (same as having to unmount a CD before ejecting it - otherwise that CD-icon sits on the desktop and won't go away, and if i insert another CD i have two of those icons on top of each other!)

I am sure i just need to edit something in fstab or some other place (mysterious workings in the guts of a Linux system... i am NOT familiar with that!) to make it work again.......

Now if someone would find a solution to the "speed" problem, too :)

Best regards......

Thanh

---

### Post by Thanh-BKK on 2008-10-17
Update:

Googling and googling and googling i found a thread from another user, facing the exact same problem:

[http://ubuntuforums.org/showthread.php?t=899285](http://ubuntuforums.org/showthread.php?t=899285)

So i need to mention that in my case, the USB stick in question is also plugged into a (although external) 4-port USB hub (which by itself is detected correctly bu "lsusb").

I did not yet try the mainboard USB socket directly because i'm at work now.

Kind regards.....

Thanh

---

### Post by Pro-reason on 2008-10-17
I think it might be best to [report this as a bug]("https://bugs.launchpad.net/ubuntu/+filebug").

---

### Post by Thanh-BKK on 2008-10-17
Hi :)

Unfortunately i am not registered there and also would not have a clue how to filr a bug - from what i read before i need to give them all sorts of details which i have no idea how to obtain.

Meanwhile i am back at home in front of my Linux box and have found that, in my case too, the USB stick will mount just fine if i plug it directly into one of the mainboard ports. But on the hub - only after "lsusb". 

I will have to go to the computer parts place tomorrow because i'll need to build a new machine for my office and once there i'll also get a new hub, maybe mine is "not really" supported anymore by the new kernel? Those things cost only pennies even here in Thailand so it's worth a try.

My "internal external" memory card reader (an external one but integrated in the PC case and connected normal via a cable that comes out of the back and plugs into one of the MoBo USB ports) works flawlessly, as soon as i put in a card (MMC, MemoryStick or Micro-SD) it is immediately mounted. 

So - clearly something to do with the hub, but it worked fine on the older kernel (and still works fine after "lsusb").

Kind regards......

Thanh

---

### Post by Pro-reason on 2008-10-17
If you think it's a kernel issue, then revert to an earlier kernel.

Either way, I believe you should take a few minutes to create an account on Launchpad.

---

### Post by juliansuddaby on 2008-10-17
Exactly the same thing is happening to me after I updated to the new kernel. This is a bug.

J

---

### Post by Pro-reason on 2008-10-17
> **juliansuddaby said:**
> Exactly the same thing is happening to me after I updated to the new kernel. This is a bug.

J

OK, report it then.  I can't, because I don't have the same hardware, and so can't provide all the details.  

Unless you report it, the developers can't fix it.  Supply all data, such as the details of the hub you're using, and which kernels work/don't work.

---

### Post by Thanh-BKK on 2008-10-17
Hi :)

Ok reported. [https://bugs.launchpad.net/ubuntu/+bug/285006](https://bugs.launchpad.net/ubuntu/+bug/285006) (and did a typo when signing up - aaaargh "Rhanh-BKK")

I can't give the hub model because it doesn't have any name - it's just called "4-port hub". Costs 2 Dollars converted :)

I don't want to boot into the older kernel, way too much stress... i rather do the "lsusb" each time i use the bloody USB stick, but still it'd be nice if it'd work the way it is supposed to. 

This kind of thing is why i keep saying "once it works, disable updating for good" as updates introduce new bugs - always. Sadly i was duped into the kernel update by reading that the new kernel will solve the slow data transfer speed problem, which is ALSO a bug - and NOT solved by the update. 

Best regards....

Thanh

---

### Post by alberto ferreira on 2008-10-17
I'm having the EXACT same problem, even the hub has 4 ports, if you do find a solution that doesn't include downgrading the kernel please share

Best regards :D

---

### Post by Thanh-BKK on 2008-10-17
Good morning.

Confirmed - it's a kernel issue. When i boot into the older kernel, auto-mount works as expected also when i plug the USB-stick into the hub.

Rebooted into the new kernel and doesn't work. 

Regards....

Thanh

---

### Post by Thanh-BKK on 2008-10-19
Hi.

A new finding: This but seems to apply only to USB 2.0 hubs! Because yesterday i purchased a new one, and when at the office and testing it (i got two, one for me and one for the office) i figured out it's a USB 1.1 hub - Windows told me so (Linux doesn't mention tat!)

HOWEVER once at home, connected it instead of the old one to my Linux box - and USB sticks mount fine on it!!

However the speed with which data is transferred is a disgrace. Reading at 900 KILObytes/second, writing at 1 Megabyte/second. 

So for now i can narrow this down to a problem that the 2.6.24-21-generic has with USB 2.0 hubs.

Best regards.....

Thanh

---

### Post by Blackwood on 2008-11-24
Wow! Thanks for all the work in tracking this down.  I've had this problem for a while, but didn't realize it was because I was using the ports on a hub.

I plug my usbkey into the USB ports on my monitor (easier than trying to get to the back of my machine).  The monitor is just a USB hub, so thus the issue.

I'll keep an eye on this thread watching for a resolution.  We'll most likely have to "update" to get it fixed though!

---

