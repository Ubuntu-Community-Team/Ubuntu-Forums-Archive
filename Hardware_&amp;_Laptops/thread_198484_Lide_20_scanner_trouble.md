---
title: "Lide 20 scanner trouble"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by Dilutu on 2006-06-17
Hi there
Trying to scan from my lide 20 ,the lamp goes to the end of the selected scan area and stops there ,with the scanner making strange noises....only way to stop  is unplugging...scanner works ok with winxp...:confused:

---

### Post by _simon_ on 2006-06-17
I assume it's a cannon lide?

I have the same scanner and have no issues!

Are you using Xsane?

I've attached a screenshot of my settings, not sure if it will help.

---

### Post by Dilutu on 2006-06-18
Hi Simon
Yes it a canon lide 20, with the same settings as yours in Xsane! It was working fine with Mepis and then Breezy,but so far no luck with Dapper....The scan in preview seems fine,but when the lamp stops at the end of the scan area,it stays lit and the scanner makes a weird growling noise....

---

### Post by farbridges on 2006-06-21
I have the same problem with the lide 20. No solutions yet?

---

### Post by Dilutu on 2006-06-21
I tried reinstalling Xsane, still no luck....Updated Ubuntu, still no luck (Xserver got messed up in the process).Tried using Scanimage, still no luck.While googling,saw a few posts related to the same problem, but no solutions yet!!!!????

---

### Post by _simon_ on 2006-06-23
I can't re-create your problem ](*,) 

I did a fresh install of dapper the other day and the scanner worked fine - as it did before the fresh install.

I don't know what I have done different to you guys!

---

### Post by _simon_ on 2006-06-23
If you go to File -> Info in Xsane does yours read the same as mine? See attachment.

---

### Post by Dilutu on 2006-06-23
Info same as yours, first scan trial is ok, second try lamp is stuck with weird noise...Had to unplug scanner....

---

### Post by Dilutu on 2006-07-15
Well,still googling (or ubunting?) for a solution.....this is one of the last problems bringing me back to xp.....

---

### Post by benyau on 2006-07-15
You may want to try the latest debian packages (link below).  You need to update three packages: xsane, xsane-common and libusb-0.1-4.  
[http://packages.debian.org/unstable/graphics/xsane.html](http://packages.debian.org/unstable/graphics/xsane.html)

Good luck.

---

### Post by Dilutu on 2006-07-16
Thanks Benyau.I verified that I had the latest packages, and reinstalled them just in case,but so far no luck......

---

### Post by krazyd on 2006-07-16
I have the same scanner and it worked OOTB. Didn't do anything special.. would having it plugged in during the install make a difference?

---

### Post by Dilutu on 2006-07-17
My scanner was plugged in during the install.Tried again,and again it scanned fine but failed to return to its home position,making a weird growling noise.Tried in winxp no problem.....

---

### Post by Nannygoat on 2006-07-22
Same problem here...the scanner is detected but I can't use it, this weird noise is terrifying. It seems that the device doesn't "know" that the lamp has reached the end of the road. I tried everything - updated backends, frontend, xsine, usblibs. No luck. If there's no solution I'll be forced to move back to Windows though I've switched totally to Kubuntu without a dual-boot option. I'll appreciate any help. Thanks in advance!

---

### Post by Dilutu on 2006-07-23
Just tried with a fresh install of Dapper on my new laptop,and after 3 successfull scans I had to unplug the scanner because of the noise....Same thing,dual booted back to xp and no problems scanning....

---

### Post by farbridges on 2006-07-27
To my disappointement this did not fix the problem.

---

### Post by _simon_ on 2006-07-27
I'm still using my Lide 20 on a regular basis (scanned 4 documents in the other day, one after the other) without coming across this problem. I wish I could help!

---

### Post by Nannygoat on 2006-07-28
Guys, please participate in the bug description at Launchpad, hopefuly the issue gets attention soon. The interesting part is that in Ubuntu I'm capable of scanning but at the end comes the "crash" (under Kubuntu can't scan at all). Yesterday tried Mepis - the scanner works perfect out of the box but the distro sucks so bad (personal oppinion).

[https://launchpad.net/distros/ubuntu/+bug/40682](https://launchpad.net/distros/ubuntu/+bug/40682)

---

### Post by Dilutu on 2006-07-28
Just left a note at Launchpad.I tried with Mepis 6.0 live cd and had the same problem.

---

### Post by Dilutu on 2007-03-19
Well,old thread and still same problem...This is what I found:
[www.nabble.com/Canon-LiDE-20:-Awful-noise-after-before-scans-t1987801.html]("www.nabble.com/Canon-LiDE-20:-Awful-noise-after-before-scans-t1987801.html")
Seems that after all its not a sane problem but more a debian one! Wonder when the fix will reach us....

---

### Post by keithpeter on 2007-06-01
> **Dilutu said:**
> Well,old thread and still same problem...This is what I found:
[www.nabble.com/Canon-LiDE-20:-Awful-noise-after-before-scans-t1987801.html]("www.nabble.com/Canon-LiDE-20:-Awful-noise-after-before-scans-t1987801.html")
Seems that after all its not a sane problem but more a debian one! Wonder when the fix will reach us....

Hello All

Just bumping this one - I have a 'noisy' Canon LIDE 20 as well. It did this in Dapper and now does it in Feisty using scanimage (to get round the USB suspend bug).

Anyone else know anything about the fix? Or indeed how to 'flush' the scanner so I can do another scan after unplugging it? Below is an e-mail from the plustek driver person...

```

On Samstag, 10. März 2007, Marc Hansen wrote:
> Hi Gerhard,
> maybe there is also the problem fixed, that I'm not able to scan under Debian?
>
This is/was a problem of Debian based distros, that is not tied to the Plustek
backend. It seems, that is has been fixed now according to some infos I've red
in a mailing-list.

- Gerhard 

```

---

### Post by gaet on 2007-06-27
Hi  All,
  my Canon Lide 20 worked fine in Dapper but now with Feisty it doesn't work any more.
 Xsane detects the scanner but when I try a preview I get a black scanned screen, no noise from the scanner, lamp off.
  I installed the xsane last version 0.991-3 plus xsane-common but no change. :(

 I'd like to try a downgrade to xsane used in dapper, is it possible?

   Gaetano

---

### Post by crjackson on 2007-06-30
> **gaet said:**
> Hi  All,
  my Canon Lide 20 worked fine in Dapper but now with Feisty it doesn't work any more.
 Xsane detects the scanner but when I try a preview I get a black scanned screen, no noise from the scanner, lamp off.
  I installed the xsane last version 0.991-3 plus xsane-common but no change. :(

 I'd like to try a downgrade to xsane used in dapper, is it possible?

   Gaetano

Did you ever get this worked out?  I have the same scanner and the exact same black screen problem.

---

### Post by stinger30au on 2007-07-28
i also have one of these units. it worked fine under XP PRO.
now i have switched, it gets detected, and if i try and scan, the scanner does not move or do a thing, but on the screen when i preview i just get a black preview and nothing more :-(

---

### Post by Ningbojoe on 2007-07-28
I have a Canoscan N650U. It has exactly the same problem as described above. I have researched this problem and it appears that it is fixed in the new kernel 2.6.22 which is in the new Gutsy edition.

---

### Post by crjackson on 2007-07-28
> **Ningbojoe said:**
> I have a Canoscan N650U. It has exactly the same problem as described above. I have researched this problem and it appears that it is fixed in the new kernel 2.6.22 which is in the new Gutsy edition.

Wow, that would be great, except Gutsy won't be ready for prime time until MONTHS after it's release.

---

### Post by Petrik on 2007-08-11
YAWN!!!!!

Add me to the list (lide 20) No movement, black screen etc. etc.

Can someone wake me up when there is a solution. It's times like this I wish I was a programmer.

---

### Post by crjackson on 2007-10-24
> **Petrik said:**
> YAWN!!!!!

Add me to the list (lide 20) No movement, black screen etc. etc.

Can someone wake me up when there is a solution. It's times like this I wish I was a programmer.

[SIZE="4"]**KNOCK KNOCK KNOCK!  Are you awake?**[/SIZE]

**_[SIZE="3"]It's fixed, install Gutsy[/SIZE]_**.  Works like a champ.

---

### Post by studo77 on 2007-11-09
I am using Gutsy 64bit and a Canoscan LiDe 50. The first page scanned fine in Xsane, and then nothing, i got a "Invalid Argument" statement. Unplugging did not help. Then i tried different programs, and Kooka is my way to go. It works perfectly. Everything i have tried it did withpput a glitch.

So maybe the problem, aside from kernel, also could lie at Sane/Xsane

---

### Post by stinger30au on 2007-11-09
my canon lide20 usb scanner has been working fine since i installed 7.10

---

