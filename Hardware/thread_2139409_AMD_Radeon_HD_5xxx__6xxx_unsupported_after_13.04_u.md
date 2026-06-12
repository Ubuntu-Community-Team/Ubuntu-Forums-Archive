---
title: "AMD Radeon HD 5xxx / 6xxx unsupported after 13.04 update"
date: 2013-04-26
forum: Hardware
---

### Post by renatasr85 on 2013-04-26
Hello. After updating to version 13.04, I started to get an annoying AMD unsupported hardware watermark on the corner of my screen (right, bottom). So I started to investigate what could have gone wrong...I have a AMD A4 CPU and a AMD Radeon HD 6480G. When I go to "Programs and updates" --> "Additional drivers", it says it's running a proprietary driver (fglrx-updates). If I check the fglrx box or the xorg box, the watermark does not go away.
I ran the Catalyst GUI and it says that version 12.9 is currently installed. According to the AMD website, the newest version of Catalyst for my CPU is 13.4. Ubuntu repositories only offer fglrx and fglrx-updates on the 12.9 version (BTW, what is the difference between those two drivers?!)

Does anyone have any idea on how to solve this issue? Should I be concerned at all with this watermark warning? I'm not experiencing video problems that I am aware of. Can I at least make this watermark go away?
I love using Ubuntu, but whenever I come across a problem like this (driver stuff) I feel completely helpless! Thanks a lot in advance.

---

### Post by betterhands on 2013-04-26
having the same issue after upgrading today.  i'll post back if i find out anything helpful before others do.

---

### Post by Nameless2 on 2013-04-26
As you seem to have fglrx-updates already there, just do:
```

sudo apt-get install fglrx-updates

```
If not installed, it will install the latest, if installed, it will update to the latest. Worked for me, the watermark that appeared directly after updating Kubuntu to 13.04 has gone after this terminal command and a reboot. Stuff looks a lot better now.
Good luck.

---

### Post by renatasr85 on 2013-04-26
Tried that, didnt work. 

But here's what worked for me: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide)
First, follow the "Removing Catalyst/fglrx instructions". Then follow the "Installing Catalyst Manually (from AMD/ATI's site)"
Restart the computer and voila, the watermark went away. Hope it helps, betterhands.

---

### Post by betterhands on 2013-04-27
so for me, using open source drivers just does not work with my dual-monitor setup--one monitor is always messed up.  only when i use proprietary does my setup work properly, and that's when the watermark comes.

the instructions here got rid of the watermark for me.  [http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver](http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver)

---

### Post by renatasr85 on 2013-04-27
Well, I preferred to install the right drivers rather than just get rid of the watermark. If you install the newer Catalyst drivers, the watermark will go away.
I just wasnt sure if not having the updated drivers would not somehow compromise video performance. So now I got the right proprietary drivers, and no watermark.

---

### Post by altosch on 2013-05-10
Updating drivers ([FONT=courier new]apt-get install fglrx-updates[/FONT]) worked for me.
ATI Mobility Radeon HD 5400 Series, Kubuntu 13.04, 3.8.0-19-generic.
Thanks.

---

### Post by jaydson on 2013-05-10
This works for me.

---

### Post by jaydson on 2013-05-10
"sudo apt-get install fglrx-updates"
mentioned above, works for me.

---

### Post by steve. on 2013-05-17
Thanks.
"sudo apt-get install fglrx-updates" worked for me with Radeon HD 6450

---

### Post by groggin on 2013-05-23
> **steve. said:**
> Thanks.
"sudo apt-get install fglrx-updates" worked for me with Radeon HD 6450

worked for me too, using raedon 5670. thanks!

---

### Post by hans12345 on 2013-06-16
Good thread.
"sudo apt-get install fglrx-updates" worked for me with Radeon HD 5450

---

### Post by rob heward on 2013-06-30
hi there.... just thought i'd let you know, this worked for me, no problems... i've just upgraded, (was running 12.04 with some graphics driver issues) to 13.04, and immediately got the watermark. so i did a google search and after looking at numerous very long winded "fixes", i came across your very simple solution.... reboot, and, hey presto, no more watermark.... thanks a lot.... rob

---

### Post by Vinicius_Santos on 2013-08-07
Hi, thank you very much..
"sudo apt-get install fglrx-updates" Worked here, model Radeon HD5560

---

### Post by X_Splinter on 2013-08-26
> **Nameless2 said:**
> As you seem to have fglrx-updates already there, just do:
```

sudo apt-get install fglrx-updates

```
If not installed, it will install the latest, if installed, it will update to the latest. Worked for me, the watermark that appeared directly after updating Kubuntu to 13.04 has gone after this terminal command and a reboot. Stuff looks a lot better now.
Good luck.

That worked for me. :D Thanks

---

