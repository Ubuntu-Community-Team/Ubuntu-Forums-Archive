---
title: "Sony Vaio FW11M eetecting less RAM (only detects 3GB instead of 4GB)"
date: 2008-10-07
forum: Hardware
---

### Post by josepcoves on 2008-10-07
Hi,

I've been struggling last few days with my new laptop (a Sony Vaio VGN-FW11M). I got some errors that I could fix by searching on the net but I'm still unable to fix one major problem:

I have 4GB of RAM but Ubuntu Hardy only detects 3GB, what can I do to fix this? 

Any help will be appreciated!

Josep

---

### Post by frlgrb on 2008-10-07
Assuming you are on the 64 bit version of Ubuntu (that helps) you may need to go into the BIOS and look for a setting to enable readdressing of video RAM or somthing like that. Different firmware says it differently but your laptop may not be set up to handle that much RAM by default. Windows OS's for 32 bit builds don't address more than three gigs. So have a look at the settings in your CMOS and look for RAM or memory management or addressing... somthing along that line.

---

### Post by josepcoves on 2008-10-07
Hi Frlgrb!

Thanks for your attention! I'm using a 32bit x86 version of Ubuntu Hardy (I forgot to specify before... sorry!). Should I take a look to my BIOS config as well, or is there another way of checking this (sorry but I'm an absolute nerd in that area)?

Many thanks

Josep

---

### Post by frlgrb on 2008-10-07
BIOS is your way in as this is a hardware setting. Sony's support site seems to only deal with simple client requests but perhaps a Google search would uncover the exact procedure.

---

### Post by Soupcan on 2008-10-07
> **frlgrb said:**
> BIOS is your way in as this is a hardware setting. Sony's support site seems to only deal with simple client requests but perhaps a Google search would uncover the exact procedure.

You can set a 32bit OS to recognize 4 gigs of RAM? I thought that only 64bit systems could. Can you do this on any computer?

---

### Post by frlgrb on 2008-10-07
No, I didn't mean to infer that. The restriction of standard X86 is around 3 gig of RAM. The laptop in question is a newer Sony VAIO which quite possibly would support X86_64 and up to 8 gig of RAM. In theory and (expensively) in practice, X86_64 would support much more RAM, I've seen 32 gigs on a system running linux-based os. Also in the server world, Windows boxes running 2k3 32 bit with 8 gigs of RAM is common.

---

### Post by josepcoves on 2008-10-08
Thanks to all for your answers...

My computer has an Intel Core 2 Duo processsor ans, as far as I know, it has 64 bit architecture, doesn't it? Is there any way to migrate from the 32bit installation I already have to 64b one without losing anything?

Many thanks

Josep

---

### Post by frlgrb on 2008-10-08
Some quick looking around yielded very little information. I would not try it myself without backing up my data onto CDs or something first. Essentially you are looking at some serious differences in how the hardware and software marry up. Where upgrading to a newer version of software, even an OS, mostly means upgrading versions; with a 32 - 64 bit migration, you are looking at a number of very different things starting with the virtual addressing of memory blocks for core components like video, the construction of your hardware abstraction layer, I can't begin to explain all that is involved. It would undoubtedly be MUCH easier to back up your files, email database, bookmarks, etc. and do a fresh build of your 64 bit Ubuntu.

Also take some time to consider this project. Is it just so you can have a little more RAM to play with? Because there are some other difficulties such as Java integration, and basic application compatibility problems that will have you scratching your head to solve. 

What are you trying to do? Maybe you should just pull out a stick of RAM and use it to boost another machine instead. Linux is very happy with 2 gig and your peppy little VAIO should be willing to do anything you ask of it. Does this laptop feature a decent video card like an ATI or Nvidia with a good amount of its own RAM? I couldn't find the exact model on Sony's website.

---

### Post by josepcoves on 2008-10-08
Hi,

Thanks again for your reply. I've serching throgh the web and I've seen what you say... I think it's better to keep with 1GB less of RAM than installing 64b version, it can lead to many new incompatibilities...

I'll wait untill 64h version is more extended and mature.

Many thanks!

Josep

---

### Post by jollo on 2008-11-23
> **josepcoves said:**
> I think it's better to keep with 1GB less of RAM than installing 64b version, it can lead to many new incompatibilities...

I'll wait untill 64h version is more extended and mature.



Good news, you don't have to: I had exactly the same problem with my new Vaio Z21 and Ubuntu 8.10 32 bit desktop edition. I just installed the "server" version of the kernel, which is compiled with the PAE (Physical Address Extension) option as default, and lo: all of my 4 GB of RAM are up and running:

```
brunello@brunello-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       4072776     775732    3297044          0      56192     312856
-/+ buffers/cache:     406684    3666092
Swap:      8916032          0    8916032
```

To install the "server" kernel, just install the linux-server and linux-headers-server packages with synaptic; all dependencies are handled automatically.

Greetings!

Jollo

---

### Post by josepcoves on 2008-11-24
Do I have to specify something special to install PAE? 

Another question... which ATI has your laptop? Mine is Radeon 3400 and I have several problems with OpenGL I always get segmentation fault and many hangs while reproducing video or screensavers...

Thanks!

Josep

---

### Post by frlgrb on 2008-11-27
I've been learning lots over the last little while since you first posted. "PAE" or "Physical Address Extension" is a capability that is built into the server version. I have to say, I don't like mucking around with the kernel of Linux boxes - I've been pooched more than once and ended up rebuilding. Still, if you have another machine that you can sandbox and try the kernel upgrade on, I think that you will find that the successful reboot with the Ubuntu Server kernel will also include your extra RAM. PAE is supposed to be enabled by default on these systems. Microsoft allows PAE if you spend big money on their Enterprise and Datacenter editions but Ubuntu obviously doesn't see that as an issue. This doesn't mean that there isn't BIOS setting involved although it does seem that the SONY may allow the addressing without changing any settings. I saw an ASUS board that, when the switch was set to allow the extra RAM, it showed up as 4gig in the BIOS but then WinXP32 didn't know how to deal and could only see a fraction of the actual installed RAM. Even 2gig wasn't read properly. Perhaps SONY firmware has figured out how to handle that.

---

### Post by josepcoves on 2008-11-28
Hi, thanks for your answer again. I'm trying to gather some time to try changing kernel to server version. Anaway, could I restore my kernel back at any time if everything turns to a mess? 

Thanks

Josep

---

### Post by josepcoves on 2009-01-20
Hi,

I finally installed kernel 2.6.24-23-server through apt-get and my laptop now detects 4GB of RAM without problems. 

This solved my problem!

Thanks

Josep

---

