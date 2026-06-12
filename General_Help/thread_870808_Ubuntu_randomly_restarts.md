---
title: "Ubuntu randomly restarts"
date: 2008-07-26
forum: General Help
---

### Post by Jdm111 on 2008-07-26
Im just genereallybrowsing the web and then the computer randomly restarts. Sometimes its after 5 minutes and sometimes after an hour. Please help.

---

### Post by Jdm111 on 2008-07-26
just happened again...

---

### Post by stevoo on 2008-07-26
check this logs files out
 /var/log/messages : General log messages
 /var/log/boot : System boot log
 /var/log/debug : Debugging log messages

maybe they have some info in them why the restat

---

### Post by Jdm111 on 2008-07-26
> **stevoo said:**
> check this logs files out
 /var/log/messages : General log messages
 /var/log/boot : System boot log
 /var/log/debug : Debugging log messages

maybe they have some info in them why the restat
What i am looking for?

---

### Post by knubbze on 2008-07-27
Does this only happen while using Ubuntu? Sounds more like a hardware problem (CPU getting to hot -> emergency shutdown (fan broken?), or PSU not providing enough energy).

Regards,
knubbze

---

### Post by Corpse_Juicer on 2008-07-31
Hello,

I've been having the same problem too.  I thought it was a hardware issue due to lack of power, so I removed one of my video cards.  The problem still happens.  I'm checking out the logs and there are a few lines that look like they might explain some things:

From /var/log/messages:
```
Jul 31 09:55:19 ubuntuRig kernel: [  258.688630] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jul 31 09:55:19 ubuntuRig kernel: [  258.688729] VMBlock warning: DentryOpRevalidate: invalid args from kernel
```

That is pretty much it from the logs that seems useful though.

I think I've narrowed it down to either Firefox or Compiz-Fusion, though I'm not entirely sure.

---

### Post by knubbze on 2008-07-31
It still might by an issue indirectly connected to hardware. You said it happens when you start compiz-fusion. Maybe because of the additional rendering effort your gfx-card uses too much energy or something?

---

### Post by Corpse_Juicer on 2008-07-31
I don't think that would be it.  Because I play games like CoD4 on Windows will graphics full out and it never happens.

---

### Post by jdorenbush on 2008-10-02
I have been having the same problem. I think its a bug in Firefox maybe??

With me, I think its only happened when Firefox is open and I am using it. A lot of times it seems like when I close a tab, particularly a tab that has some form of media running, usually Flash, or video of some sort.

---

### Post by Calmatory on 2008-10-02
> **jdorenbush said:**
> I have been having the same problem. I think its a bug in Firefox maybe??

With me, I think its only happened when Firefox is open and I am using it. A lot of times it seems like when I close a tab, particularly a tab that has some form of media running, usually Flash, or video of some sort.

Mind providing /var/log/kernel.log? :p

How does the restart occur? Does the computer just shut down instantly? Or does the Operating system start the shut down procedure? Or does the machine restart instantly? Or does the operating system start the restart/reboot procedure?

---

### Post by jdorenbush on 2008-10-02
> **Calmatory said:**
> Mind providing /var/log/kernel.log? :p

How does the restart occur? Does the computer just shut down instantly? Or does the Operating system start the shut down procedure? Or does the machine restart instantly? Or does the operating system start the restart/reboot procedure?

```

Oct  2 13:00:05 jeff-desktop kernel: [ 3198.352583] audit(1222977605.856:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7590 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:05 jeff-desktop kernel: [ 3198.356649] audit(1222977605.860:4): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:05 jeff-desktop kernel: [ 3198.356687] audit(1222977605.860:5): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3198.564445] audit(1222977606.068:6): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/unexpected.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3198.656352] audit(1222977606.160:7): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/unexpected.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3198.748128] audit(1222977606.252:8): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/unexpected.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3198.748190] audit(1222977606.252:9): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3198.790423] audit(1222977606.292:10): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3198.790453] audit(1222977606.292:11): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3199.015434] audit(1222977606.517:12): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/unexpected.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3199.107284] audit(1222977606.609:13): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/unexpected.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3199.195126] audit(1222977606.700:14): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/unexpected.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 13:00:06 jeff-desktop kernel: [ 3199.195179] audit(1222977606.700:15): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=7584 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 15:33:51 jeff-desktop kernel: [12408.305243] [fglrx] PCIe has already been initialized. Reinitializing ...
Oct  2 15:33:51 jeff-desktop kernel: [12408.311709] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
Oct  2 15:33:51 jeff-desktop kernel: [12408.311717] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Oct  2 15:33:51 jeff-desktop kernel: [12408.311719] [fglrx] Reserve Block - 2 offset =  0Xffbb000 length = 0X40000
Oct  2 15:33:51 jeff-desktop kernel: [12408.348310] [fglrx] interrupt source 20008000 successfully enabled
Oct  2 15:33:51 jeff-desktop kernel: [12408.348318] [fglrx] enable ID = 0x00000008
Oct  2 15:33:51 jeff-desktop kernel: [12408.348325] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Oct  2 15:33:51 jeff-desktop kernel: [12408.348375] [fglrx] interrupt source 10000000 successfully enabled
Oct  2 15:33:51 jeff-desktop kernel: [12408.348377] [fglrx] enable ID = 0x00000009
Oct  2 15:33:51 jeff-desktop kernel: [12408.348380] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Oct  2 15:40:34 jeff-desktop kernel: [12810.786405] [fglrx] PCIe has already been initialized. Reinitializing ...
Oct  2 15:40:34 jeff-desktop kernel: [12810.792693] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
Oct  2 15:40:34 jeff-desktop kernel: [12810.792698] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Oct  2 15:40:34 jeff-desktop kernel: [12810.792700] [fglrx] Reserve Block - 2 offset =  0Xffbb000 length = 0X40000
Oct  2 15:40:34 jeff-desktop kernel: [12810.829332] [fglrx] interrupt source 20008000 successfully enabled
Oct  2 15:40:34 jeff-desktop kernel: [12810.829338] [fglrx] enable ID = 0x00000008
Oct  2 15:40:34 jeff-desktop kernel: [12810.829616] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Oct  2 15:40:34 jeff-desktop kernel: [12810.829796] [fglrx] interrupt source 10000000 successfully enabled
Oct  2 15:40:34 jeff-desktop kernel: [12810.829799] [fglrx] enable ID = 0x00000009
Oct  2 15:40:34 jeff-desktop kernel: [12810.829978] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Oct  2 16:45:10 jeff-desktop kernel: [16680.535445] npviewer.bin[11279]: segfault at 4d0 rip f79c96e7 rsp ffbe0b90 error 4

```

Screen turns black, displays some text (boot-like stuff), then it goes to the login window.

---

### Post by ferd on 2008-10-02
Same thing has been happening to me. I think is Firefox 3.03 related because it started after I started using the latest Firefox. There are posts on the Mozilla Firefox forums on the same topic with no resolution.

---

### Post by Cresho on 2008-10-02
> **Jdm111 said:**
> Im just genereallybrowsing the web and then the computer randomly restarts. Sometimes its after 5 minutes and sometimes after an hour. Please help.

I get this alot from my friends as well.  It is a hardware problem.  related to motherboard.

---

### Post by jdorenbush on 2008-10-03
> **Cresho said:**
> I get this alot from my friends as well.  It is a hardware problem.  related to motherboard.

Anything else? Solutions? What motherboards are at fault??

---

### Post by Calmatory on 2008-10-03
> **Cresho said:**
> I get this alot from my friends as well.  It is a hardware problem.  related to motherboard.

If it happens on some hardware but not on others, then the problem still lies in Firefox's code. The problems just occur with certain hardware but not on others.

I'd assume it is related to the chipset(My guess is Nforce. :p). What kind of motherboards are people having who suffer from this?

---

### Post by 3rdalbum on 2008-10-03
Try removing the proprietary ATI ("fglrx") driver. Just run using the 2D "ati" driver and see if the problem persists.

Do you have the latest Firefox?

---

### Post by jdorenbush on 2008-10-06
I have Firefox 3.0.3

---

