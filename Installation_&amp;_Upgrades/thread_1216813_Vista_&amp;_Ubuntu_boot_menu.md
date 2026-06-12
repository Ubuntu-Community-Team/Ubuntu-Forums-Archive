---
title: "Vista &amp; Ubuntu: boot menu"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by mavis311 on 2009-07-18
I installed ubuntu on my desktop with Win2k and the Grub boot menu comes up at boot on that machine, exactly the way I'd like it.  

I'm trying ubuntu on my laptop with Vista factory installed and the Vista boot menu comes up when I boot now.  

Does anyone know a way to control which menu comes up or at least control what the default selection is and the timeout?

---

### Post by mavis311 on 2009-07-19
well, I solved a part of this problem.  I figured out how to modified the Vista boot menu so that ubuntu is the default selection and extended the timeout.  I'd still like to have the ubuntu boot menu come up instead of the Vista one.  However, I think I sort of shot myself it the foot by installing ubuntu inside of windows -- There is no dedicated ubuntu partition, just a c:\ubuntu folder under Vista.

Advice?  Anyone?

---

### Post by coffeecat on 2009-07-19
> **mavis311 said:**
>   However, I think I sort of shot myself it the foot by installing ubuntu inside of windows -- There is no dedicated ubuntu partition, just a c:\ubuntu folder under Vista.

I don't know about a bullet in the foot, but you've installed with [Wubi]("https://help.ubuntu.com/community/Wubi"), whereas you did a conventional install on your desktop, i.e. Ubuntu on its own Linux partition rather than in C:\ubuntu.

I'm afraid you're stuck with the Windows Boot Manager if you use Wubi. You can only use grub if your Linux installation is on its own separate partition. If you want to try again, you'll need to uninstall your Wubi install from the Windows control panel, and then set up a dual-boot with Vista.

Before you do this, (if you want to do this), post back with whatever details you can find about how the hard drive is organised on your laptop. Are there any hidden or "restore" partitions? What model is it? You'll need to resize your Vista partition if you want to create Linux partitions and you need to know that Vista is much more fussy about this than XP or earlier versions. [Read this for all the gory details]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"), particularly what happens when you use Gparted to shrink the Vista partition. Since you have a pre-installed version of Vista, you won't have the MS Vista install DVD to repair Vista for when/if it makes itself unbootable.

---

### Post by jglayden on 2009-07-19
This is not an answer, only another question to your question. LOL How did you change your boot menu? Mine is setup for Ubuntu first and vista second. I would like Vista first and Ubuntu second. It is a work PC and I am mainly using Vista.
Thanks

---

### Post by Post Monkeh on 2009-07-19
> **jglayden said:**
> This is not an answer, only another question to your question. LOL How did you change your boot menu? Mine is setup for Ubuntu first and vista second. I would like Vista first and Ubuntu second. It is a work PC and I am mainly using Vista.
Thanks

you can edit the grub menu.lst file, but there's a program called startupmanager (downloadable from synaptic package manager) that allows you to select your default boot selection

---

### Post by mavis311 on 2009-07-19
> **jglayden said:**
> This is not an answer, only another question to your question. LOL How did you change your boot menu? Mine is setup for Ubuntu first and vista second. I would like Vista first and Ubuntu second. It is a work PC and I am mainly using Vista.
Thanks

It sounds like you are using grub to boot, so my method wouldn't apply to you.  Post Monkeh has the solution for grub.  (I guess, I'm stilll learning about linux)

I used wubi to install and hence only have a Vista partion.  I used BCDEDIT on a Vista command line to change the default boot selection and timeout.  A very simple process that I can post details for after I reboot into Vista.

> **coffeecat said:**
> I don't know about a bullet in the foot, but you've installed with [Wubi]("https://help.ubuntu.com/community/Wubi"), whereas you did a conventional install on your desktop, i.e. Ubuntu on its own Linux partition rather than in C:\ubuntu.

I'm afraid you're stuck with the Windows Boot Manager if you use Wubi. You can only use grub if your Linux installation is on its own separate partition. If you want to try again, you'll need to uninstall your Wubi install from the Windows control panel, and then set up a dual-boot with Vista.

Before you do this, (if you want to do this), post back with whatever details you can find about how the hard drive is organised on your laptop. Are there any hidden or "restore" partitions? What model is it? You'll need to resize your Vista partition if you want to create Linux partitions and you need to know that Vista is much more fussy about this than XP or earlier versions. [Read this for all the gory details]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"), particularly what happens when you use Gparted to shrink the Vista partition. Since you have a pre-installed version of Vista, you won't have the MS Vista install DVD to repair Vista for when/if it makes itself unbootable.

For the way I wanted to do it -- wubi is absolutely a shot in the foot.  I wanted much more control over how the partitions are laid out, etc.  Yes Vista was pre-installed on my laptop, but I do, in fact, have the restore cds from the manufacturer so the gory details are not so gory for me.  They look pretty straight-forward.  I didn't know I would encounter those problems, so thanks a lot for the link!  I'm just too new to ubuntu and wasn't familiar with the behavior of wubi when I installed on my laptop.

---

### Post by coffeecat on 2009-07-19
> **mavis311 said:**
> I do, in fact, have the restore cds from the manufacturer so the gory details are not so gory for me.

Ah - not quite so fast. :) Manufacturer's restore discs (usually) restore the system to its factory condition. I.e. you will restore Vista, but you will lose all your personal settings, installed applications and system updates. Under 'Using Linux to Resize' in the link I posted, is a link to a page showing you how to repair a Vista system made unbootable by a Linux partitioner. Unfortunately, it's giving a server error at the moment, but what it tells you to do is to use a 'proper' Microsoft install DVD, which has a repair utility which is unlikely to be on a manufacturer's restore disc.

However, you can download a recovery disc which contains the Microsoft "recovery center", here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It's worth reading because it explains much better what I was trying to explain.

---

### Post by mavis311 on 2009-07-20
> **coffeecat said:**
> Ah - not quite so fast. :) 

Right.  While you may have received a server down message in the UK.  I was fully able to access the links you posted as well as all the links on those pages.  Howtogeek continues to be a most useful resource.

I was easily able to remove ubuntu via windows add/remove programs and also easily able to resize my vista partition from 184.84 GB down to a tidy 30 GB using windows' computer management utilities as well as the wonderful PerfectDisk defragmenter with free 30-day trial!  Great program, btw.  It took a little time, but it wasn't at all difficult.  Of course I backed up all my documents, web bookmarks, photos, music, etc prior to even installing ubuntu.

My laptop is made by Toshiba.  Yes, it has a "restore" partition (which has proved to be quite useless, yet still I allow it to sit there on my drive).  The disks I received with it are not, in fact, actual Microshaft Windows Vista Home Premium DVDs.  However, the "system restore" utility that is included on them alongside Vista gives the option not to include all the useless crap that Toshiba's partners paid to have installed on my computer when I took it out of the box.  A simliar option allows the disks to function exactly as Vista install DVDs.

But none of that is really relevant anyway. Even if this method hadn't worked, I'd just wipe my disk and install Vista fresh to a 30G partition.  I simply didn't have the time to mess with it and hadn't considered linux on the laptop when I wiped and reinstalled back in May.

Now, I just install ubuntu to its own partition and forget about my original question.

[IMG]http://users.domaindlx.com/mavis311/gfx/VistaPartition.jpg[/IMG]

Still, all of this has been quite enlightening.  Its been almost 10 years since I worked in the IT industry and did this sort of thing every day.  (Its been about as long since the last time I used Linux as well--RedHat Linux 5.1).  In fact, in about a year and a half of using Vista, I've never had so much interest in learning about it.  I had always felt that it was just another windows, and I'm not fond of windows at all (and I've used them all since 3.0, except ME).  I've always preferred to have the command line environment be primary and keep the gui around for the things its good at: web browsing, graphic design, etc.

---

