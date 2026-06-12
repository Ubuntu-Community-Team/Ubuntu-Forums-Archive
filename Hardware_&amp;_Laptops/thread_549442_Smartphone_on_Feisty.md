---
title: "Smartphone on Feisty?"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by greymarch on 2007-09-12
I installed Feisty on my laptop.  I have a Windows Mobile 6 smartphone (Tmobile Dash, to be precise)) that I plug into the laptop via a USB cable.  I want to be able to read and write files from the smartphone, just like I can do in Windows XP.    How can I accomplish this?  There must be a way.  Currently, when I plug the phone into the laptop while I am running Feisty, I cannot view the contents of the phone, but it does charge the phone.

---

### Post by aldeby on 2007-09-12
Charging the phone is a matter of hardware, since Feisty activates the usb controller it provides power to any device attached.
Unfortunately you have a Microsoft Windows phone, which of course has been designed to be solely compatible with Microsoft Windows OSs. These are Microsoft views and policies about interoperability: there should be no market, only a monopoly!

Maybe next time consider having a look at [http://openmoko.com/]("http://openmoko.com/") :popcorn:

---

### Post by greymarch on 2007-09-12
> **aldeby said:**
> Charging the phone is a matter of hardware, since Feisty activates the usb controller it provides power to any device attached.
Unfortunately you have a Microsoft Windows phone, which of course has been designed to be solely compatible with Microsoft Windows OSs. These are Microsoft views and policies about interoperability: there should be no market, only a monopoly!

Maybe next time consider having a look at [http://openmoko.com/]("http://openmoko.com/") :popcorn:

Thanks for the opinion, but I am hoping to not derail this thread.

Is there a way to access the files on a windows mobile phone using Feisty?  If so, then how can this be done?

---

### Post by JBAlaska on 2007-09-12
I ran across a post from a guy that was using his as a modem on a linux laptop, I don't have this phone but I'm guessing the CID needs to be unlocked to do this.

On this phone it seems you have to pay $40.00 to get the CID unlocked;
```
www.jonholato.com/2007/05/27/how-to-unlock-your-t-mobile-dash/
```

Here's the post on using the dash with linux;
```
www.htcwizardweb.net/node/1019#comment-2382
```

---

### Post by odzk on 2007-10-17
did u tried installing the microsoft sync on wine? maybe it will work but im not sure though

---

### Post by puccaso on 2007-10-19
im going to try it now

---

### Post by beartard on 2008-01-20
So far I haven't been able to get activesync to install under either wine or a version of windows xp running under qemu.

I have been able to mount my SD card using WM5torage on the phone itself.  It's a freeware app available on all smartphone or pocketpc freeware sites.  You can use it to mount the phone's internal memory for editing the registry as well, but it's not advisable.

There is also a PIMbackup utility that can make backups of personal data in comma-separated-value files that can be imported into most address books in linux.

---

