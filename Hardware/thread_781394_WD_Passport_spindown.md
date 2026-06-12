---
title: "WD Passport spindown"
date: 2008-05-04
forum: Hardware
---

### Post by Blednik on 2008-05-04
Dear Ubuntu users,

I own a 160 GB WD Passport portable external USB hard drive. After a while of using it in Ubuntu, I noticed that when I shut down my computer, the disk does not shutdown properly - it shuts down without syncing and/or spinning down the cylinders. The hard shutdown sounds like a click, followed by the sound of the cylinders slowly losing the spinning momentum. The same effect can be achieved by just pulling the USB plug while the disk is operating.

The second thing I noticed is that whenever I try to unmount the volume, the disk won't spin down either. I've done a bit of searching and found this page where the problem is described: [https://bugs.launchpad.net/ubuntu/+bug/117713](https://bugs.launchpad.net/ubuntu/+bug/117713)

I can currently safely remove the disk by first unmounting it and then issuing a "sdparm --command=stop /dev/sdb" command. This will spin down the cylinders nicely. My question is whether the two things I noticed are related and whether they are a defect of the operating system or rather a defect of the hardware itself. If they are a hardware defect, does it apply to the whole series of WD Passports or am I just unlucky to own a broken disk?

Lastly, I'd like to ask people, who own WD Passports to share their experience.

See ya.

---

### Post by ugm6hr on 2008-05-06
I hadn't really noticed this problem - but yes - it does happen.

That launchpad report is interesting.

Not sure there is a solution out there.

---

### Post by oooh on 2010-03-06
Did you find a proper solution for this ?

I can not believe nothing has been done about this issue with stopping external drives yet ...

In any case, I found this, that I will try soon:

[http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/](http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/)

It uses sdparm as well.

Cheers

---

### Post by oooh on 2010-03-06
The script from this guy works perfect !

[http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/](http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/)

Just fine, but ubuntu developers should do sthing about this ...

Good luck !

---

### Post by operator on 2010-05-24
I have the opposite problem with WD Passport 500Gb. It spins down after 10 seconds (!) of inactivity. Of course, it starts again when used, but it takes 2-3 seconds to spin up and SMART spin start/stop count which is shown in Disk Utility is increasing quite fast.

Questions:

1. Spin down after 10 seconds - is it ok? Is it sane? I would not surprised if on International Space Station or on Antarctic Station where electricity is short....

2. Is constant start/stop wears off this drive? I'm listening mp3 from it and it starts, reads the part of the file (looks like quite bug read-ahead), stops, starts again all the time. Looks stupid.

3. I wondering is it WD firmware or ubuntu settings?

Some more info on this case:

WD5000ME-01 3110A Product of Malaysia
Ubuntu 10.04 on Desktop computer
I found this guide on the internet: [http://gbatemp.net/index.php?showtopic=146789](http://gbatemp.net/index.php?showtopic=146789)

Please share your experience connected with this product of malaysia if any!

---

