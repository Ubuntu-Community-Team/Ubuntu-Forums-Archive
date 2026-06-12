---
title: "Can't Run Ubuntu 8.04.1 on AMD-K6"
date: 2008-09-17
forum: General Help
---

### Post by marc69 on 2008-09-17
Greetings Forum:

I want to learn how to use Ubuntu. I burned the iso file onto a CD, using Alex Feinman's software, and I was able to see a Ubuntu screen. However, when I chose to do a software check, the system said Ubuntu 8.04.1's kernel requires a different processor than what I have; I have an AMD K6 450 MHZ Gateway computer.

Do I actually need a whole new computer, just more RAM, or can I use an older version of Ubuntu? Please advise...

Thanks

---

### Post by northern lights on 2008-09-17
If you want to know whether you'd need more RAM it might of help to disclose how much the machine's got now...
:)

Further, check [https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by jonian_g on 2008-09-17
> **marc69 said:**
> Greetings Forum:

I want to learn how to use Ubuntu. I burned the iso file onto a CD, using Alex Feinman's software, and I was able to see a Ubuntu screen. However, when I chose to do a software check, the system said Ubuntu 8.04.1's kernel requires a different processor than what I have; I have an AMD K6 450 MHZ Gateway computer.

Do I actually need a whole new computer, just more RAM, or can I use an older version of Ubuntu? Please advise...

Thanks

No, you don't need a different computer. You need to download a new iso. I supose you downloaded the "64bit AMD and Intel computers" version of ubuntu but that version is for 64bit processors. Your processor is 32bit and you have do download the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)".

Your system is very old and I think it would be better to use xubuntu.

---

### Post by Zill on 2008-09-17
Depending on the amount of RAM available, you *may* be able to install Ubuntu on your PC, assuming you download the correct standard 32-bit ISO as pointed out earlier. ;-)

However, the AMD-K6 would be *very* slow with Ubuntu and you may find that a lighter version, such as Xubuntu, is more suitable.  [DSL]("http://www.damnsmalllinux.org/") is another possibility and really flies along with the AMD-K6.

One problem is that the Hardy Xubuntu users-admin GUI is buggy and can cause corruption of the /etc/passwd and /etc/group files when adding users :-(  The workaround is to use the CLI commands, rather than the GUI, when adding new users.  See [Bug 240437]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/240437") for further details.

---

### Post by marc69 on 2008-09-18
> **northern lights said:**
> If you want to know whether you'd need more RAM it might of help to disclose how much the machine's got now...
:)

Further, check [https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
Yes, that would be useful...I have 128 MB of RAM. Thanks for the feedback.

---

### Post by marc69 on 2008-09-18
> **jonian_g said:**
> No, you don't need a different computer. You need to download a new iso. I supose you downloaded the "64bit AMD and Intel computers" version of ubuntu but that version is for 64bit processors. Your processor is 32bit and you have do download the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)".

Your system is very old and I think it would be better to use xubuntu.
OK. So I downloaded the wrong iso file...I wasn't certain if my system was 64 bit. And I should be downloading a lighter version of the OS. That's good to know! I'll have to go with what works until I get a better machine. Thanks very much for your time. Take care.

---

### Post by marc69 on 2008-09-18
> **Zill said:**
> Depending on the amount of RAM available, you *may* be able to install Ubuntu on your PC, assuming you download the correct standard 32-bit ISO as pointed out earlier. ;-)

However, the AMD-K6 would be *very* slow with Ubuntu and you may find that a lighter version, such as Xubuntu, is more suitable.  [DSL]("http://www.damnsmalllinux.org/") is another possibility and really flies along with the AMD-K6.

One problem is that the Hardy Xubuntu users-admin GUI is buggy and can cause corruption of the /etc/passwd and /etc/group files when adding users :-(  The workaround is to use the CLI commands, rather than the GUI, when adding new users.  See [Bug 240437]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/240437") for further details.
Thanks for the feedback and the information on the potential bugs. I was trying to avoid more problems, but any step away from Windows seems useful. Take care.

---

### Post by marc69 on 2008-09-21
> **jonian_g said:**
> No, you don't need a different computer. You need to download a new iso. I supose you downloaded the "64bit AMD and Intel computers" version of ubuntu but that version is for 64bit processors. Your processor is 32bit and you have do download the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)".

Your system is very old and I think it would be better to use xubuntu.

Jonian:

Well, you helped me before so I'd like to follow-up. I attempted to download the 32-bit Alternate CD from the Xubuntu website. However, the timing for downloading the iso file was showing as a day or two. In fact, I was only downloading a BYTES/sec, let alone kilobytes. I was about 60% through and lost the connection.

Would you suspect this lag is due to the source or the network? I'm thinking of contacting Verizon to see if they're having an issue. Thanks for your time.

---

### Post by Zill on 2008-09-21
marc69:  Try another mirror :-)
[http://www.xubuntu.org/get]("http://www.xubuntu.org/get")

---

### Post by marc69 on 2008-09-22
Zill:

I tried several of the mirrors for alternate CD i386 iso files but all of them were taking a day or more to download so I'm on hold wondering what to do; the alternate CD takes ten weeks to get...

---

### Post by northern lights on 2008-09-22
What are the results at [http://speedtest.net]("http://speedtest.net")?

---

### Post by Zill on 2008-09-23
marc69:  Seems like your net connection has serious problems - it generally takes me less that one hour to download a distro on my adsl connection.

You could always buy a CD at minimal cost from one of the many resellers supplying your area.  Type "linux cds" into Google for details.

---

### Post by jonian_g on 2008-09-23
Marc, try to download it as a torrent or use a download accelerator.

---

