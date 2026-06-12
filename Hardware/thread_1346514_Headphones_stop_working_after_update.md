---
title: "Headphones stop working after update"
date: 2009-12-05
forum: Hardware
---

### Post by Thr33finger on 2009-12-05
Ok, So i searched around and every thread i find about headphones not working is about the internal speakers not muting when you plug in headphones. This is not my problem lol.

My headphones worked fine out of the box muting the internal speakers and all, I even watched a movie last night with them. However today after waking up I turned on my netbook(MSI u120) and got my little update warning. So i clicked install. and now my headphones simply have no sound at all. The internal speakers still mute but no sound comes through the headphones.

So far I have installed Alsamixer and after playing with settings in there nothing has changed.

In the standard sound preferences there are output connectors of analag stereo and analog headphones. neither works.

Also, I should really learn to read through exactly what the updates are for, previously I had issues where my usb's were not working. whenever I plugged in my usb sticks they would not be recognized. This problem was solved after this update. I don't know if this is connected but hopefully it helps you folks with helping me.

Let me know what you want and I'll try to provide you with any info I can.

---

### Post by Thr33finger on 2009-12-05
Bump

lol. Not in a big hurry but during a busy weekend I get antsy when my question leaves the front page lol

---

### Post by pearldrums on 2009-12-05
Hi,

I hate to say this, but I also have a U120 and have experienced these problems. I've spent a lot of time searching and found that the best option was to go back to 9.04. I can tell you that the problem with the headphones was specific to the netbook remix for me, and if you would like, changing over to regular ubuntu might fix it, but no guarantees. As far as the USB issue there is a simple answer, when you are booting up press FN+F6 to disable your webcam. Its a known bug for the MSI wind in karmic that the webcam drivers cause issues with the USB drivers. You probably will also experience some screen flicker issues. I have not had success with the workaround that is listed in the release notes.

Unfortunately reverting back to 9.04 is no easy task, so you may want to try to live with the issues. If you want to revert to 9.04 you can back up all your files, and re-install. Or you can migrate your home folder to a new partition and re-install. There is no way to "downgrade." If you use ubuntu exclusively and don't have multiple partitions on your HD already I would suggest migrating your home folder. However, if your running windows and Ubuntu, you may find there isn't really enough space on your HD to do this in a practical manner.

Good luck mate!

---

### Post by Thr33finger on 2009-12-05
lol, Thanks for the response even if its not what i was hoping for. I can live without the headphones. But not for long. I'll put in a bug for it to the wiki and wait and see. Thanks for letting me know that though.

---

### Post by Thr33finger on 2009-12-09
ok,
So hoping additional information will give someone smarter than me an idea how to fix this lol. Just fooling a round a couple days later. If i turn off my computer with the sound on the same issue keeps happening. however if i turn of my computer with the sound muted then unmute it after reboot it works fine. Don't know what this means but hopefully someone does.

---

### Post by Thr33finger on 2009-12-12
bump

---

### Post by Zawullon on 2010-01-11
I've solved this issue yesterday on MSI Wind U120.
You must send model=acer-dmic parameter to snd-hda-intel kernel module.
You can add this parameter to line starting with "option snd-hda-intel" at the end of file /etc/modprobe.d/alsa-base.conf
This works for Ubuntu 9.10 and 10.04.

---

### Post by justin00b on 2010-08-21
> **Zawullon said:**
> I've solved this issue yesterday on MSI Wind U120.
You must send model=acer-dmic parameter to snd-hda-intel kernel module.
You can add this parameter to line starting with "option snd-hda-intel" at the end of file /etc/modprobe.d/alsa-base.conf
This works for Ubuntu 9.10 and 10.04.

I'm having this exact problem after updating this morning. Could you please give some detailed instructions on how to do this? For the record, I didn't see anything in /etc/modprobe.d/alsa-base.conf that said "option snd-hda-intel" anywhere. I also have the MSI Wind U120 running UNE 10.04. Thanks!

---

