---
title: "Lexmark Z11 refuses to print"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by umarmung on 2004-10-24
Hi everyone,

i'm trying to print with my lexmark z11 printer, but it even refuses to print the testpage. I had the same printer working in gentoo, so i'm sure it can work. All settings should be correct (parallel port #1 and lz11 driver) and i installed the gimprint packages like it was suggested in some other threads.
I also set cups' loginfo to debug, which always helped me before to track down any printing problems. However this time the log left me clueless  :-k Maybe someone else can help me, here is the relevant output (note: the whole log is quite large, so i post only the important parts).
```

D [24/Oct/2004:15:51:29 +0200] [Job 5] New page:  1 1
D [24/Oct/2004:15:51:29 +0200] [Job 5] Inserting option code into "PageSetup" section.
D [24/Oct/2004:15:51:29 +0200] [Job 5] No page header or page header not DSC-conforming
D [24/Oct/2004:15:51:29 +0200] [Job 5] Stopping search for page header options
D [24/Oct/2004:15:51:29 +0200] [Job 5] Found:
D [24/Oct/2004:15:51:29 +0200] [Job 5] 66BA0F2FBD4C92D25121A2647E8081BF05241DF408C9CE4EED2A630C3018869E51E7F90C030031A6E8FEE178DF9A598A4F1D8CA4C7741AA2C40081C0D48C29A8B4B60A0FE5D7BA4DD1F7CC51282CEF697AC70713546B0933B65246AAAC6A881DFB16 D [24/Oct/2004:15:51:29 +0200] [Job 5] --> Output goes directly to the renderer now.
D [24/Oct/2004:15:51:29 +0200] [Job 5]
D [24/Oct/2004:15:51:29 +0200] [Job 5]
D [24/Oct/2004:15:51:29 +0200] [Job 5] Starting renderer
D [24/Oct/2004:15:51:29 +0200] [Job 5] JCL: <job data>
D [24/Oct/2004:15:51:29 +0200] [Job 5]
D [24/Oct/2004:15:51:29 +0200] [Job 5] renderer PID kid4=4315
D [24/Oct/2004:15:51:29 +0200] [Job 5] renderer command: lz11.foomatic --papersize=a4 --color=0 --inksaving=1 --resx=582 --resy=582 D [24/Oct/2004:15:51:29 +0200] [Job 5] renderer return value: 16777215
D [24/Oct/2004:15:51:29 +0200] [Job 5] renderer received signal: 16777215
D [24/Oct/2004:15:51:29 +0200] [Job 5] Process dying with "The renderer command line returned an unrecognized error code 16777215.", exit stat: 1 D [24/Oct/2004:15:51:29 +0200] [Job 5] The renderer command line returned an unrecognized error code 16777215. D [24/Oct/2004:15:51:29 +0200] [Job 5] tail process done writing data to STDOUT

```

---

### Post by umarmung on 2004-10-24
Just an hour after I posted I found the answer, maybe this will help someone else, so here is my solution...
It turned out that I was missing the ppd file and the binary driver. So I went to linuxprinting.org downloaded the ppd file and dropped it into the right folder. Next I got my driver from sourceforge, compiled and installed it. After that the printer works fine.

BTW: This should really be stated in the 'add printer' dialog. When i found my printer in the list, i thought everything is in place and I can print right away.  #-o

---

### Post by a-nubi-s on 2005-04-29
Hi I'm new to linux and need specifics for this. I have the same printer and it works perfectly in Mandrake just choosing it in the printer setup without any changes but not in Ubuntu.

I got the ppd and driver mentioned. What folder do I put the ppd in?
What commands do I need to run for the driver?

BTW: I have hoary not warty if it makes a difference.

---

### Post by samx on 2005-10-20
For what it's worth... at least this thread brought me the solution, so just my comment:
Go to [www.linuxprinting.org](www.linuxprinting.org), download lz11.tar.gz, extract it, read the README and run just as described lz11.install
After that, just print a test page to be happy ;)
But I'm just wondering why the printer is that slow now... At least I think under gentoo it was faster...

---

