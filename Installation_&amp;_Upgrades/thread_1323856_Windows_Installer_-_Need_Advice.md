---
title: "Windows Installer - Need Advice"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by kevinblack on 2009-11-12
Hi,

Having worked with the various flavours of Unix in a previous life and some time ago, I at least have some understanding of where I want to go and probably what I'm up for.  My aim is to (eventually) rid myself of MS Windows, but there are a number of hurdles.  As a first step I'd like to get into Linux and start mapping over applications natively if possible, Wine is plan B and VMWare or similar Plan C for those apps that don't wine and dine and I still need.

I think the easiest install is using the windows installer (currently running Win 7 64bit on an HPDV7t laptop).  Plenty of resources, but some questions (I did look at the docs\faqs\forums - maybe in the wrong places - but couldn't find the answers):
[LIST=1]
[*]How do I specify 64bit Ubuntu when using the Windows installer?
[*]Does the installer repartition my harddrive?
[*]Is the partition size the MB filed in the installation window?
[/LIST]

Sure, I can download Ubuntu desktop version directly, but why not use the tools available.  If there is any other advice etc etc you might like to provide fill yer boots......

Thanks in advance.

Kevin

---

### Post by mikewhatever on 2009-11-12
> **kevinblack said:**
> Hi,

[*]How do I specify 64bit Ubuntu when using the Windows installer?

Should be automatic, provided the 64 bitness of the host OS is detected by the installer. Here is some info on that from the [WUBI FAQ]("http://wubi-installer.org/faq.php"):

```

Why is the AMD64 version of Ubuntu getting downloaded and installed?

You probably have a 64 bit machine, the 64AMD installation is appropriate for all 64 bit architectures whether AMD or Intel.

```


> [*]Does the installer repartition my harddrive?

No.

> [*]Is the partition size the MB filed in the installation window?
[/LIST]

It might be, I don't know.

You might want to verify WUBI supports W7, cause I don't see any mention of that on its site.

---

### Post by Bunnybugs on 2009-11-12
Wubi creates a filesystem, that windows detects like a file it can't read...

You can make the file as big as you want, untill 30GB, but there are tools to make it even larger!

Just check out on the Wubi Support page (so did I when i first installed Ubuntu using Wubi, but that's a long time ago, so I'm not sure!)

---

### Post by Mark Phelps on 2009-11-12
If you're really serious about migrating away from MS Windows, I would strongly suggest that you NOT use Wubi.  That's really only intended to try out Ubuntu and eventually, you'll want to "move" it outside MS Windows into its own partition -- which will be a lot of work.

So, save yourself the trouble now and install to its own partitions in dual-boot mode.

But first, if you haven't already done it, you should boot into 9.10 in LiveCD mode to check out how well it works for you.

---

### Post by audiomick on 2009-11-12
> **kevinblack said:**
> Hi,


Sure, I can download Ubuntu desktop version directly, but why not use the tools available. 

MS resolutely refuses to make it easy to install and use another OS than its' own.

Ubuntu Linux assumes that some people are in exactly your position, and want to keep windows on the box, at least for a while. Therefore, every effort is made to make this as easy and painless as possible

---

### Post by kevinblack on 2009-11-12
Guys,

Thanks for the responses.  I had no idea about WUBI, but now understand.  As you point out, probably more trouble than it's worth.

I will opt for the re-partition/ubuntu install.  I've re-partitioned the C: drive and have approximately 80Gb set for Ubuntu in the first instance.

I've downloaded the x64 ISO (first download quit at 420Mb second OK) and am creating the CD as we speak (actually just finished).

OK, onwards and upwards.................

Thanks again.

Kevin

---

### Post by audiomick on 2009-11-12
When you install, go into the manual partitioning bit. Make a partition for the system mounted at / , needs to be around 8 GB or so, a big one mounted at /home , and make your swap a bit bigger than your RAM, otherwise the suspend and hibernate functions can't work

---

### Post by SteveHillier on 2009-11-12
> **kevinblack said:**
> I will opt for the re-partition/ubuntu install.  I've re-partitioned the C: drive and have approximately 80Gb set for Ubuntu in the first instance.

Just some caution.  Should be OK in Win7 but worth making sure your Windows disk is defragged and compacted giving you plenty of space at the top end of the disk.
An earlier flavour of Ubuntu did do this for me when I forgot once but better to make sure.

---

