---
title: "CD/DVD Drive fails to recognize DVD-R"
date: 2009-10-27
forum: Hardware
---

### Post by TheLifeRuiner on 2009-10-27
I am running Ubuntu 9.04, dual-booting with Windows Vista.
My problem is that I insert a blank DVD-R, but it doesn't come up - there is no CD icon that pops up, Brasero asks me to insert a medium, going to Place->Computer and clicking on the CD/DVD Drive yields the message "Unable to mount location; Can't mount file".
I have no problem with CD-R/Ws, or reading DVDs. Under Vista, it DOES recognize the blank DVD-R, so I take it that it's an Ubuntu issue, and not a hardware one, but I may be wrong. (However, I posted here because it relates to hardware.)

sudo lshw:
*-cdrom
                description: DVD writer
                product: DVD+-RW SDVD8820
                vendor: PHILIPS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AX03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

I would switch to simply using Vista to burn, but that doesn't solve the problem.

Is this a bug?

If anyone could help, it would be greatly appreciated.

Thanks in advance.

---

### Post by Dark_Stang on 2009-10-28
Have you tried different brands of DVD-R? My laptop absolutely hates Memorex and Sony discs, but loves Verbatim discs. My desktop will work with any disc, but tends to have a higher burn failure rate with Memorex discs. I know it's weird but it happens.

---

### Post by TheLifeRuiner on 2009-10-28
No, see, the thing is that the drive recognizes the DVD under Vista, but not under Ubuntu.
If it was as you said, then I don't see why it would be selective. o_O

Under Vista however, it tell me the disc is write-protected, and that it's closed, so I can't burn to it, which means that that one time I tried burning something onto it, but failed, must have started the procedure for burning on the DVD, but burned nothing, effectively yielding a completely useless DVD.
EVEN SO, I still find it strange that Ubuntu doesn't read it, since I can still access the disc under Vista.

:(

---

