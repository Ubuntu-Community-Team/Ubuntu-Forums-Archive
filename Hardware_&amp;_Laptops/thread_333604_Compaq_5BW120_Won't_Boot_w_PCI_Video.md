---
title: "Compaq 5BW120 Won't Boot w/ PCI Video"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by Kadin2048 on 2007-01-07
This is less of a Linux question per se than a general 'hardware' question, but I'm hoping someone out there can help, since I'm a bit out of my depth.

I have an older Compaq that I'm working on turning into a MythTV box. This is a Presario [5BW120]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=c00032396"), basically your run of the mill 600MHz Celeron box. I've stuffed 512MB of RAM and an Ethernet card in there, and everything was working fine with Ubuntu.

Unfortunately, the onboard video sucks pretty badly. I didn't need anything spectacular, just hardware MPEG-2 decoding and S-Video output. So I went down to the local shop and picked up an old ATI PCI video card (since this machine doesn't have AGP; its slots are only PCI).

The card is marked "Rage 6 SDR 32MB" but also has Radeon markings on the board. Copyright date is 2000. I *think* this is a first-generation [Radeon R100]("http://en.wikipedia.org/wiki/Radeon_R100#R100").

Unfortunately, when I put the card in and attempt to start the system, it won't boot. I'm pretty sure it's not even POSTing. I can't get to BIOS or even get any picture on either video output, the new one or the built-in. As soon as I pull the card and turn it on again, everything works fine. I've also tried the obvious stuff like pulling all the other PCI cards; it's definitely the video card. When it's in, no boot -- when it's out, things work fine. Going into the BIOS menus (with the card not installed, obviously) don't show any options to use an add-on card for video rather than the onboard one, the only thing PCI related is an option to set the IRQs for various installed devices.

Does anyone know how to get this working? Or am I just hosed in terms of ever getting this thing to recognize a PCI video card?

---

### Post by Kadin2048 on 2007-01-09
After several days of messing around with various things, I found a solution to the problem.

Since this thread is the top Google hit for "5bw120 bios" I thought I'd post it here in case some other person ever runs into the same problem.

Apparently the black screen was due to a problem in the original (6/2000) BIOS. Reflashing to an updated BIOS -- which was not particularly easy to find -- seems to solve it. The 11/2000 BIOS, available here:

[ftp://ftp.compaq.com/pub/softpaq/sp15501-16000/sp15894.exe](ftp://ftp.compaq.com/pub/softpaq/sp15501-16000/sp15894.exe)

doesn't add any new options in the BIOS menus, but it does make the system use the PCI video adapter if it's installed, instead of the onboard video. Not sure if the onboard video is totally disabled (prohibiting dual displays) or what.

This is not the optimal solution in my mind, because it still leaves the computer with a crippled (piece of **** Compaq) BIOS rather than a regular one like you'd have gotten if you had bought the mobo aftermarket, but at least it works.

The BIOS updater above is a Windows executable, so you'll need to download and run it on a Windows box. It won't update the BIOS on the machine you run it on, so no worries about doing it on a friend's machine or whatever. It creates a DOS boot disk which, when run in the 5BW120, will update the BIOS to the revision of Nov. 2000.

There are later BIOS revisions for this machine, but based on my reading of the various text files accompanying them (on the ftp site above), they're not actual code changes. The later Rompaq is just a repackaging of the 11/2000 BIOS in a version that can be flashed directly from Windows without making a DOS boot disk (I think). If you're running Linux though, this is a Bad Thing and a misfeature, so I stuck with the older Rompaq that creates a boot disk.

Anyway, I hope this is potentially helpful to some other person down the road.

---

