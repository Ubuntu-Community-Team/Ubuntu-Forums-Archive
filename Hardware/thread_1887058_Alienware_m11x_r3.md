---
title: "Alienware m11x r3"
date: 2011-11-26
forum: Hardware
---

### Post by x3qt0r on 2011-11-26
Hi.
I am using the alienware m11x r3.
ubuntu 11.10 works perfectly on this laptop when used in live cd mode.The laptop gets heated immensely though.

After installing,updating and upgrading however, trackpad, brightness, volume (using Fn) and wireless does not work.

I decided to first tackle the heating problem which was basically due to the gpu running.
So i tried to install bumblebee using the instructions from [here]("http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/"):


I have followed every instruction given there and installed bumblebee.
After rebooting however, i get a busybox.
Then i entered the recovery mode and i got [this]("http://i41.tinypic.com/348r40m.jpg").

Kindly help ASAP, i need to have a linux box running alongside my windows 7 in this laptop.

Thanks in advance!

(P.S: i have been reading the threads pertaining to alienware m11x here, they have helped me a lot, and i am sure that I can get ubuntu running on this machine, flawlessly)

---

### Post by jocefus on 2011-12-08
I am using an Alienware M14xR1. Working okay here. However, when I first installed I did not connect to internet and update during installation. It caused problems.

Only extra thing I did that isn't in those directions for bumblebee was blacklist the nouveau module. It was conflicting with bumblebee/nvidia sometimes. It has almost doubled my battery life and runs much cooler.

All Fn keys worked on my machine except for the ejectcd. This link has some info on troubleshooting hotkeys:
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

Looking at your screenshot, it seems kernel can't identify root partition by its uuid for some reason. It's hard to say what went wrong.

---

### Post by Mark Phelps on 2011-12-08
The link below has a workaround for the overheating issue caused by kernel problems.  Don't know if it will work on your laptop, but it might be worth trying:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by jocefus on 2011-12-09
With these laptop models as well as any others utilizing muxless nvidia optimus technology, most of the excessive heat and power consumtion stems from the discrete nvidia gpu being active all of the time without being able to utilize it at all. 
 
The kernel boot parameter mentioned in that article alone will do little to correct this. You must also switch off the nvidia card when not in use via the necessary acpi calls. The directions he was following do just that while also restoring limited functionality of the nvidia gpu. The directions also include the adding of that kernel boot parameter and some other parameters enableing intel gpu power saving features.
 
These parameters are disabled by default because some users experience issues with certain hardware. However, I have been utilizing them for a while now with no problems yet.

---

### Post by eltalpa on 2012-01-10
guys I've posted the solution here:

[http://ubuntuforums.org/showpost.php?p=11601558&postcount=5](http://ubuntuforums.org/showpost.php?p=11601558&postcount=5)

:)

---

