---
title: "Grahpic errors while shutdown"
date: 2009-05-01
forum: Hardware
---

### Post by chichicke on 2009-05-01
Hi guys,

after setting up a new system with the new jaunty version, I'm getting graphic errors like colored vertical lines or dots after a shutdown.
I press shut down ... everything works fine the kubuntu logo occurs ... the bar empties and then there are for a few seconds these lines and dots, before the notebook shuts down completely.

I'm not really sure if theres a connection, but after several reboots my graphic card didn't work anymore (just big vertical lines were displayed) and i had to get it replaced. 

My notebook : Dell M1330 with GeForce 8400M GT .. using proprietary driver.

These errors occurred never before (i used ubuntu 8.04 for a long time before) and also didn't occur on windows xp.
Now, having the graphic card replaced i get the same dots and lines ... but only after shutting down kubuntu, not while using windows.

Do you guys have any idea? is this normal or can it really end in crashing the graphic card?

regards

---

### Post by chichicke on 2009-05-02
Nobody ever head about something like this or experienced himself?

---

### Post by overdrank on 2009-05-02
> **chichicke said:**
> Nobody ever head about something like this or experienced himself?

I am experiencing a similar issue on my fresh install of Jaunty with the nvidia 8200. I am using the version 180.xx driver. I have not had any issue after reboot though. What driver version are you using for the nvidia?
Have you tried the new 185.xx driver from nvidia. [Here]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185")

---

### Post by chichicke on 2009-05-02
yeah im using the 180 ... ill give it a shot with the new ones thanks

---

### Post by Zathuras on 2009-05-02
I'm getting a similar problem with the 173.xx and default 180.xx that comes with 9.04.

Technically my installation is probably Ubunutu, but I'm using KDM (it started out as kubuntu on 8.10 but I installed the ubuntu desktop packages and started using gnome when the pain threshold of some of the pre KDE 4.2 stuff was too high.)  

Laptop is a Asus G2S X3 with an nvidia 8600m GT video chipset and I'm running a 64-bit version of Jaunty.  I'm wondering now if its a kdm issue...

Glad I'm not the only one who's had this problem too.

---

### Post by Zathuras on 2009-05-03
Any luck with the 185.xx nvidia drivers?

---

### Post by chichicke on 2009-05-04
unfortunately no. 
had few time the last days so it took me a while to get them running proberly but stil no .. same random dots and lines as always. i'm still wondering if it could be an issue of kdm because ubuntu was running fine such a long time. 
and still not many people seem to have this problem.

regards

---

### Post by chichicke on 2009-05-05
hi,

after loading all updates today and swithing pack to the non properitary driver ... the problems are gone .. but now it wont come back from hibernate xD

---

### Post by Zathuras on 2009-05-07
Hmm thats not good.  I probably wont have time to try a few things out till this weekend but whatever I do I'll let you know.

---

### Post by overdrank on 2009-05-07
I can hibernate but not suspend with my HP G60 laptop, nvidia 8200m - nvidia driver 180.44, Jaunty Linux-x86_64
If I get time tomorrow I will try the 185 driver if I feel spunky :)

---

### Post by Zathuras on 2009-05-10
Just for kicks I tried switching from KDM to GDM and that didn't matter.  Had a feeling that it wouldn't, but I thought I'd see.

I'll probably try out the 185.xx nvidia drivers next.

---

