---
title: "Buffer I/O Error | EXT3-FS Error"
date: 2008-08-09
forum: General Help
---

### Post by Roger Mudd on 2008-08-09
Can anyone help me decipher the output on the attached "screenshot?"

My Thinkpad has been locking up on me with both XP and Ubuntu 8.04 installed. I'll be able to work for a bit on Ubuntu and then X will lock up. I can still move the mouse but cannot input any commands using either the mouse or keyboard. The system grinds to a complete halt as a result. Restarting X (Ctrl-Alt-Backspace) brought me to the screen you see below.
In XP, it just spits out a BSOD. Very helpful ;-)

My first thought is that my hard drive is dying? Obviously possible, but does it seem likely with the information provided in the screen shot? My next guess is a failing video card. I'm unable to play simple OGG output from RecordMyDesktop. I created a short screencast with audio on the Thinkpad but it wouldn't play in Totem. Just sat there. I opened that same screencast on my desktop running XP with VLC and it worked fine. Flash video via YouTube worked fine on the Thinkpad under Ubuntu.

I've tried reinstalling Ubuntu and XP. I've tried using both the open ATI drivers (default) and installing the restricted drivers. The system seems a bit more stable and responsive with the default drivers, however, the crash still occurs.

Any help is appreciated. Thanks in advance!

---

### Post by Roger Mudd on 2008-08-10
Hate to do it, but... bump...

---

### Post by spiderbatdad on 2008-08-10
that looks like output from trying to install a bad iso and or cd. Ubuntu runs well on thinkpads, though some kernel boot options are usually required. What model thinkpad?
Probably not a problem with the hard drive. Thinkpads are rugged long lasting machines.

Ah. misread your post...looks like the file system is corrupted.

---

### Post by Roger Mudd on 2008-08-10
Thanks spiderbatdad. It's a T42 1.7 Centrino with 1GB RAM, ATI 9700 Mobility video card and an 80GB hard drive.
The strange thing about it is the computer locks up in Ubuntu and BSODs in XP and Vista Ultimate 32-bit. That leads me to believe it's a hardware problem. Is there anything out there that can diagnose these problems. I'm sure the output in the screen shot above is trying to do just that. Unfortunately, I can't seem to track down what it means.
I've had the machine for a couple of years. This problem just started within the past month.

---

### Post by cariboo on 2008-08-11
To find out if it is your hard drive, go to the hard drive manufacturers web site and download their diagnostic tools, most of them have a bootable iso option and run them to find out one way or the other.

Jim

---

### Post by Roger Mudd on 2008-08-12
Thanks carboo907. Took your advice, burned the ISO for [Samsung's HUTIL]("http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html") to CD and ran the self-diagnostic test twice (an hour for each run :-(). Looks like all is clear on the hard drive front.
That's obviously good news, but I'm still in the dark. Again, I assume it's a hardware issue as the machine locks up in Ubuntu 8.04, XP Pro and Vista Ultimate. Strange...

---

### Post by spiderbatdad on 2008-08-12
Are you running the latest bios? There was an upgrade a couple of years ago...from Phoenix 2.08 to 2.10 I believe. Also...you haven't changed the wireless adapter have you? Using the wrong wireless adapter in a thinkpad will eventually result in bios failure.

---

### Post by Roger Mudd on 2008-08-14
> **spiderbatdad said:**
> Are you running the latest bios? There was an upgrade a couple of years ago...from Phoenix 2.08 to 2.10 I believe. Also...you haven't changed the wireless adapter have you? Using the wrong wireless adapter in a thinkpad will eventually result in bios failure.

Interesting spiderbatdad. I'm running BIOS 3.23, which is the latest version [according to Lenovo]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-50273").

Your comment about using the wrong wireless adapter has piqued my interest. There was some confusion a while back and I may have installed the 2100 driver instead of the 2200 driver (this machine has a Intel Pro 2200bg adapter). I haven't run across any documentation of the possibility of corruption. Can you provide a link? If this is the case, can the BIOS simply be re-installed or is the machine kaput?

---

