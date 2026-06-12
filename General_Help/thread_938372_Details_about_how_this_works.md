---
title: "Details about how this works?"
date: 2008-10-04
forum: General Help
---

### Post by KingAlanI on 2008-10-04
OK; I installed Ubuntu 8.04 via Wubi awhile ago and it seems to be working fine; but have accumulated some questions about it.

(My computer is a Toshiba Satellite laptop that originally came with Windows Vista Home Basic)

* How come the Ubuntu option comes up on *Windows* Boot Manager?
* When booted into Ubuntu, does the system "go through"/use any Windows processes at all?
** (I hear this happens with wireless cards; my machine came with a 802.11g card)

* How do you see your Windows files within Ubuntu (and vice versa)? This would be useful if I wanted to use a file that was stuck on the other partition...
* Also, I have a 4GB FAT32-format USB drive that typically use amongst various Windows boxes. Would it be safe and would it work to try and use it while I'm booted into Ubuntu?

---

### Post by ago on 2008-10-06
> **KingAlanI said:**
> 
* How come the Ubuntu option comes up on *Windows* Boot Manager?
The windows bootloader launches a linux bootloader that then loads linux

> * When booted into Ubuntu, does the system "go through"/use any Windows processes at all?
No

> ** (I hear this happens with wireless cards; my machine came with a 802.11g card)
Ndiswrapper allows Linux to use windows drivers, but in that situation the driver is copied to the linux filesystem during ndiswrapper setup

> * How do you see your Windows files within Ubuntu (and vice versa)? This would be useful if I wanted to use a file that was stuck on the other partition...
Windows files are available under /host

> * Also, I have a 4GB FAT32-format USB drive that typically use amongst various Windows boxes. Would it be safe and would it work to try and use it while I'm booted into Ubuntu?
Yes

---

### Post by KingAlanI on 2008-10-10
With the wireless thing, I was afraid that the Windows-driver thing would be a security problem.
From the sound of your comment, the driver for wireless seems to be ported/transferred properly. [sorry if I'm getting the technical term wrong here.]
(The wireless system generally works fine for me on either OS)

I see /host. (graphically in File Browser - Computer, then Filesystem, then Host)

Obviously, I can't run Windows apps while I'm in Linux (unless I installed WINE), but should I be able to seamlessly write files to and from that section?

The USB Flash drive I referred to, glad to hear I can use it without incidence (I was remembering bad old days of floppies formatted toa  specific operating system. :P)

(I've been able to use the drive on XP, Vista and Mac OS X without incident, so I'd presume that Linux would work aswell.

---

### Post by wowgold119s on 2008-10-12
A small boy was crying his eyes out at a football match. Seeing his plight, a policeman came up to him and asked what the problem was. "I've lost my dad," cried the boy. "What's he like?" asked the policeman. "Beer, fags and women," said the boy...................................................................................................................................................... cheap [world of warcraft gold](http://www.mmoinn.com/)| cheap [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)| [http://www.mmoinn.com](http://www.mmoinn.com)|eu [world of warcraft gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new)|buy [wow gold](http://www.mmoinn.com)

---

