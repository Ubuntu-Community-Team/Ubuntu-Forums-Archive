---
title: "Onboard webcam stopped working after 20.04 upgrade"
date: 2020-05-26
forum: Hardware
---

### Post by dustyt on 2020-05-26
I recently upgraded. Big mistake since my kid is using this computer for remote learning. The webcam doesn't work anymore. It worked just fine in 19.10. This is the onboard camera in a new HP laptop. I don't understand why it quit working. Any help would be appreciated.

I ran hwinfo --usb and this is the output I could find related to the webcam.

```
05: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: NwzV.jYsl2jK3Mn5
  Parent ID: k4bc.2DFUsyrieMD
  SysFS ID: /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1
  SysFS BusID: 1-5:1.1
  Hardware Class: unknown
  Model: "Quanta HP Webcam"
  Hotplug: USB
  Vendor: usb 0x0408 "Quanta Computer, Inc."
  Device: usb 0x5220 "HP Webcam"
  Revision: "0.09"
  Serial ID: "0x0001"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Speed: 480 Mbps
  Module Alias: "usb:v0408p5220d0009dcEFdsc02dp01ic0Eisc02ip00in01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (Hub)
```

---

### Post by DuckHook on 2020-05-27
Though I can only be of limited help, since I don't own any machine like yours, the following may help. The link is old but the procedures are solid and still applicable: [https://dmaiorino.com/?p=12](https://dmaiorino.com/?p=12)

Hopefully someone with similar HW will jump in.

It sounds like this is a production machine (a child who depends on it for schoolwork makes it production in my books). Try running a LiveUSB of 18.04 to see if it works. You may wish to stay away from 20.04 until its first point release in July. In fact, if Bionic works for you, you may wish to stay with it.

---

### Post by dustyt on 2020-05-27
Yeah it is indeed a production machine for both of us.

I use it for my work in the morning and at night, and she uses it in between for school work, which includes online classes due to this virus stuff. Ugg.

I upgraded from 19.10 to 20.04 to get a solution to the copy/paste bug only to have this happen which is worse. I really have no issue in blowing out my install and trying a fresh install or going back... except I have a lot of customizations set that I really don't wanna have to redo. I am not even sure I would remember how to redo it all, lol.

Anyways, thanks for the link. I will check it out.

---

### Post by dustyt on 2020-05-27
> **DuckHook said:**
> Though I can only be of limited help, since I don't own any machine like yours, the following may help. The link is old but the procedures are solid and still applicable: [https://dmaiorino.com/?p=12](https://dmaiorino.com/?p=12)

Hopefully someone with similar HW will jump in.

It sounds like this is a production machine (a child who depends on it for schoolwork makes it production in my books). Try running a LiveUSB of 18.04 to see if it works. You may wish to stay away from 20.04 until its first point release in July. In fact, if Bionic works for you, you may wish to stay with it.

Well, you owe yourself a little more credit than your modesty allowed.

I was able to fix my problem with the link you provided.

Step 4 
Your user is in the video group.

This should be added by default, but just in case.

sudo usermod -a -G video $USER

I don't want to think about how long it would have taken me to think of that as a possibility. 

I appreciate the help, so thank you.

When I worked in IT for a living I always used to try to instill these words to all of my people as they were learning the ropes.... you don't have to know how or remember how to fix everything, you just need to know the information is out there and remember how and where to go look for it quickly. And if you figure out how to fix something new, document the fix and publish it so others who come behind you can reap the same benefits you have.

---

### Post by DuckHook on 2020-05-27
> **dustyt said:**
> Well, you owe yourself a little more credit than your modesty allowed.
I am notoriously arrogant—just ask Mrs DuckHook—so my limitations are very manifest. But it's very kind of you all the same.

I just upgraded one of my partitions to Focal too, and am fighting through very similar issues. Past experience indicates that network upgrades do tend to create all sorts of weird and wonky behaviour: little inconsistencies or borked configs like yours. Since it is a production box, you may wish to stick to LTSes henceforth. After their initial bug squashing period, they tend to settle down into greater stability than the standard releases.

Glad that the problem is solved.

Good Luck and Happy Ubuntu-ing!

---

### Post by dustyt on 2020-05-27
Yeah I will be sticking to LTS going forward.

I also think I may revert back to passing on upgrading to next version in favor of a fresh clean install of the next version. Maybe just write notes what customization I do so I can more easily redo all that stuff. That is what I used to do before. I just figured things would be much smoother now all these years later, and so far as I know right now it has been much smoother so I don't really regret trying it (yet lol).

---

### Post by DuckHook on 2020-05-27
I've gotten into the habit of multibooting my production machines. There's always an old LTS on another partition that I can fall back to in case I do something really dumb. The second partition doesn't have to be big. 8 GB is all that's needed because you won't be installing any apps on it except for rescue stuff. You only need it for emergencies and it's much easier to mount the other partition and try to save if from one already resident on disk. It's a technique that's saved my bacon more than once.

Of course, if you have the disk space, make it a fully fledged alternative backup.

If you install Focal from scratch, you can also choose either LVM or ZFS installs. They take up the whole disk by default, but they allow snapshots, which are also great fallbacks. Though they can be resized after install, it's not a trivial exercise.

Just a few more tricks of the trade.

---

### Post by pseudotheist2 on 2020-05-28
> **DuckHook said:**
> Though I can only be of limited help, since I  don't own any machine like yours, the following may help. The link is  old but the procedures are solid and still applicable: [https://dmaiorino.com/?p=12](https://dmaiorino.com/?p=12)
Just a quick thanks; your link fixed [my issue]("https://ubuntuforums.org/showthread.php?t=2442886") as well!

---

