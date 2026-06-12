---
title: "Intel 915 GM/GMA and 1400x1050 resolution"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by lyly on 2005-06-09
I installed Ubuntu on a Dell Latitude D610 with SXGA extention. I come with an Intel 915 GM/GMA chipset. It seems to be a PCI Express device.

I try to make Xorg work with 1400x1050 resolution. Unfortunatlly the highest resolution I can retrieve is 1280x1024.

It seems that the driver can't allocate more than 8Mb memory to the card (the 8Mb are set and cannot be changed in the bios(v. A02)) But the card and the panel seems to be well detect.

Someone in my university write a patch for the intel driver and a hack for the bios, but for Fedora... 

Unfortunalty as the Ubuntu kernel is not the same as Fedora they don't work, at least in hoary (I didn't test in breezy)...  :cry:

Is someone ready to make an adaptation for ubuntu? please please please  [-o<

Many thanks, Lynda

intel driver: 
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

You can find the patch at
[http://poseidon.epfl.ch/webdav/site/poseidon/shared/intel915gm_latest.patch](http://poseidon.epfl.ch/webdav/site/poseidon/shared/intel915gm_latest.patch)

and the bios hack program:
[http://poseidon.epfl.ch/webdav/site/poseidon/shared/915resolution.tar.gz](http://poseidon.epfl.ch/webdav/site/poseidon/shared/915resolution.tar.gz)

My first thread on this subject:
[http://ubuntuforums.org/showthread.php?postid=83167](http://ubuntuforums.org/showthread.php?postid=83167)

---

### Post by MetalMusicAddict on 2005-06-09
From what I just read on the Dell fourms its set to 8 megs at the start and adjusts to what the machine needs.
Heres a [LINK](http://forums.us.dell.com/supportforums/board/message?board.id=insp_video&message.id=132583&query.id=0#M132583) .

---

### Post by lyly on 2005-06-09
[QUOTE=MetalMusicAddict]From what I just read on the Dell fourms its set to 8 megs at the start and adjusts to what the machine needs.
Heres a [LINK](http://forums.us.dell.com/supportforums/board/message?board.id=insp_video&message.id=132583&query.id=0#M132583) .[/QUOTE]

The problem is that the intel driver doing this does not compile in ubuntu... anyway, the bios also need a hack, because it does not know resolution higher than 1280x1024

---

### Post by jrhodes on 2005-06-09
If it adjusts to what the machine needs, would it be possible to force it higher than 8MB by setting the VideoRam option in xorg.conf?

---

### Post by lyly on 2005-06-09
[QUOTE=jrhodes]If it adjusts to what the machine needs, would it be possible to force it higher than 8MB by setting the VideoRam option in xorg.conf?[/QUOTE]

I try this, it doesn't work

---

### Post by lyly on 2005-06-12
Really no one?

---

### Post by lyly on 2005-06-24
I make it work with xorg 6.8.2-10 and following the step given in this web page:

[http://home.comcast.net/~canez/d610/#video](http://home.comcast.net/~canez/d610/#video)

---

