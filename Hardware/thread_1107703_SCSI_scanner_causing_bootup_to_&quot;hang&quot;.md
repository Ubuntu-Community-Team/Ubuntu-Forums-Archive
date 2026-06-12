---
title: "SCSI scanner causing bootup to &quot;hang&quot;"
date: 2009-03-27
forum: Hardware
---

### Post by paulvbrown on 2009-03-27
Hello all!  Searching has failed me, so here I am.

Short story: turning scanner on before boot causes it to "hang", and I eventually get kicked into BusyBox.

Longer story:

I have an "ancient" Mustek scanner connected via a Tekram SCSI adapter to my desktop pc (Acer Aspire T180), which is running LinuxMint Daryna (based on Gutsy).  It's still a dual-boot system with Vista, which one of my daughters (the obstinate one =o) insists on using.  We use the scanner VERY rarely, but I HAVE had it working in Linux, though I have had to have it turned on BEFORE booting in order for it to be recognized.  And then I've had to create a link to /dev/scanner for xsane to "find" it...

Anyway, it HAS worked.  Since we use it so rarely, though, there's no telling WHAT has changed since the last time it worked and now.

CURRENTLY, as stated above, having it turned on b4 boot seems to cause the system to hang, and I get put in BusyBox, if I don't abort the boot before that point.  One thing I noticed in some log/printout I saw was this:

```
inquiry: failed requesting 36 byte response: res=97
```

It may be worth mentioning that I have been having boot problems with this PC recently.  Still not sure what the problem is NORMALLY, and when this one showed up, I didn't immediately attribute it to the scanner being turned on (b/c it HAS worked in the past).  Once I made the connection, the PC booted up just fine, and now I've been trying to get it working turning it on AFTER boot.  I've installed scsitools, and running the rescan-scsi-bus.sh script creates a new entry in /proc/scsi/scsi at 0:0:6:0, which jives with notes I've made earlier.  lsscsi shows it being mounted (?) at /dev/sdg.  "sg_inq /dev/sdg" gives me the exact same inquiry failure listed above.

Whew - that's about what I know at this point.  Any help is greatly appreciated.  BTW, my linux experience is still at the "knows enough to be dangerous" stage...

Thanks in advance!

---

