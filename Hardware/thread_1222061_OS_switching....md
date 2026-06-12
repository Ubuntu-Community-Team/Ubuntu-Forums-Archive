---
title: "OS switching..."
date: 2009-07-24
forum: Hardware
---

### Post by jrickert on 2009-07-24
Is it possible to switch back and forth between OS's?  Like if I am in Ubuntu and want to see a spreadsheet in XP is it possible without shutting down Ubuntu and booting XP.

Thanks, John

---

### Post by philcamlin on 2009-07-24
do you mean like virtual machine? :popcorn:

---

### Post by Bucky Ball on 2009-07-24
You can view a Microsoft spreadsheet in Open Office in Ubuntu. Just open it or double click the file.

---

### Post by SuperSonic4 on 2009-07-24
Not with a dual boot - you can with a Virtualbox type system though although that takes up too much RAM.

It would be best to use OpenOffice Spread as it's native linux and can read/write to xls

Crossover Pro has compatability with Office 03 and Office 07 and wine has support for the former if you need Office

---

### Post by philcamlin on 2009-07-24
if you want windows xp you can use virtualbox 

but spreadsheets work with open office :D

---

### Post by Bucky Ball on 2009-07-24
> **Bucky Ball said:**
> You can view a Microsoft spreadsheet in Open Office in Ubuntu. Just open it or double click the file.

You can view it using Open Office in Windows as well actually. :)

---

### Post by jrickert on 2009-07-24
Ok, I think I get it.  So my next question is, how can I see the files I have under XP while in Ubuntu.  Is there some way to get into the C: drive where all my XP stuff is?

---

### Post by Bucky Ball on 2009-07-24
You need to mount the drive. The common thing is to have a shared partition. It is never a good idea to keep valuable data (rather than replaceable apps and OS) on the same partition.

Your C drive might be there somewhere but I noticed on one of my machines it doesn't automatically find it. Look in:

Open a folder on the desktop and in the left panel, go to 'File System->media'. Is it in there anywhere?

---

### Post by FraggedLocust on 2009-07-24
> **Bucky Ball said:**
> You need to mount the drive. The common thing is to have a shared partition. It is never a good idea to keep valuable data (rather than replaceable apps and OS) on the same partition.

I can attest to the shared drive thing. If you mount and change a file in Ubuntu, and save it to it's original location in Windows, it puts some weird shared permission on it when you load Windows and can cause a couple bugs with file operations on it. At least, that's what I've noticed dual booting 9.04 and Vista.

---

### Post by philcamlin on 2009-07-24
you can mount the drive by clicking on it 

it should be seen under places on your top panel :)

---

### Post by bacil on 2009-07-24
I think VirtualBox is safest option for some specialised applications. For basic office stuff etc. your Linux can do the same as XP :-)

---

### Post by Bucky Ball on 2009-07-24
Easiest way? Create a partition that does NOT contain either OS and name it 'SHARE' or something. Files you want to use in both MS and Linux live on that partition. Get all your valuable stuff off your Windows partition otherwise if/when it crashes and the OS needs to be re-installed, your data will crash with it.

The other thing you can do is go:

> System->Admin->Synaptic Package Managerand search for 

> ntfs-3gInstall that and run it (will be in a drop down menu). That might find your Windows drive and mount it at boot if you're lucky. 

:)

---

