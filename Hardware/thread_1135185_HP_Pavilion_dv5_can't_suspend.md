---
title: "HP Pavilion dv5 can't suspend"
date: 2009-04-24
forum: Hardware
---

### Post by Amorphous_Snake on 2009-04-24
I have a brand new Jaunty 64-bit installation on this laptop and I only ran update and installed the nvidia driver using the restricted driver module. When I suspend it, it can't be started back on. It keeps telling me errors about can't start ata devices. I think it's saying that it can't start the HDD.

Please help.

The hardware in this laptop is mostly standard: Centino 2 2.0 GHz, 3 GB RAM, nvidia GeForce 9200M GS, Intel Wireless 5100. I installed over a 8 GB / and 1 GB swap. I know that I should have made swap bigger if I was going to hibernate, but I want to suspend to RAM not hibernate.

It works great in Vista on another partition.

Edit: I meant Centrino not Celeron.

---

### Post by Amorphous_Snake on 2009-04-27
Anyone?

---

### Post by SDXeus on 2009-04-27
> **Amorphous_Snake said:**
> I have a brand new Jaunty 64-bit installation on this laptop and I only ran update and installed the nvidia driver using the restricted driver module. When I suspend it, it can't be started back on. It keeps telling me errors about can't start ata devices. I think it's saying that it can't start the HDD.

Please help.

The hardware in this laptop is mostly standard: Celeron 2 2.0 GHz, 3 GB RAM, nvidia GeForce 9200M GS, Intel Wireless 5100. I installed over a 8 GB / and 1 GB swap. I know that I should have made swap bigger if I was going to hibernate, but I want to suspend to RAM not hibernate.

It works great in Vista on another partition.


I also have Jaunty 9.04 amd64 on my HP dv5z.

When I suspend at the login screen my computer goes into and out from suspension normally as well as when I suspend while logged in and at the desktop, my computer goes into and out from suspension normally.

I have a different spec though:

.::. AMD Turion X2 Ultra  Dual-Core Mobile ZM-80 2.1 GHz, 3GB RAM, ATI Mobility Radeon HD 3400, Atheros AR928X;  Installed on 28 GB, partitioned along side Vista and the HP support partition .::.

However, after I select the Ubuntu installation in the GRUB, I get two errors:

[random number ID, ie.- 2.284258] ata1: softreset failed (device not ready)

[random number ID, ie.- 2.284258] ata2: softreset failed (device not read)

Ubuntu then loads normally and I can login and use the installation just fine.


Are these the same errors you get?

---

### Post by SrEstroncio on 2009-05-13
I get similar errors when loading Ubuntu on my HP Pavilion dv5-1004nr
And when I put my computer to sleep keyboard and touchpad won't respond after waking it up.

---

### Post by Amorphous_Snake on 2009-05-13
The error I receive is different something about:

ata1: irq_stat 0x000000040, connection status changed
ata1: SError: {DevExch}
EXT3-fs error (device sda5): ext3_find_entry: reading directory # (some numbers) offset 0

ata2: irq_stat 0x000000040, connection status changed
ata2: SError: {DevExch}
ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000000 action 0xe frozen

the same errors repeat over and over when I wake up, alternating between ata1 and ata2 as headers with the rest of the text the same, except for some changing numbers at the beginning of the line like (240.722819, 240.722945, etc, etc)

I am really at a loss. The system doesn't wake up from hibernation too. Hibernation is not important to me, as I hardly use it in Windows.

---

### Post by whichpaul on 2009-05-24
If you're using Ubuntu on a HP dv5 then I have good news and bad news for you.

Good news: You're not alone.
Bad news: There is no fix as of yet.

There is an Ubuntu bug report open for it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301353?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301353?comments=all)

At present it appears to be a bug in the BIOS, so this puts a fix in the hands of HP.

What you can do is to contact HP support, to let them know we exist, and give your support on the HP Support forum thread. All the details can be found toward the bottom of the above link.

Good luck!

---

### Post by fornix on 2009-05-25
> **SDXeus said:**
> I also have Jaunty 9.04 amd64 on my HP dv5z.

When I suspend at the login screen my computer goes into and out from suspension normally as well as when I suspend while logged in and at the desktop, my computer goes into and out from suspension normally.

I have a different spec though:

.::. AMD Turion X2 Ultra  Dual-Core Mobile ZM-80 2.1 GHz, 3GB RAM, ATI Mobility Radeon HD 3400, Atheros AR928X;  Installed on 28 GB, partitioned along side Vista and the HP support partition .::.

However, after I select the Ubuntu installation in the GRUB, I get two errors:

[random number ID, ie.- 2.284258] ata1: softreset failed (device not ready)

[random number ID, ie.- 2.284258] ata2: softreset failed (device not read)

Ubuntu then loads normally and I can login and use the installation just fine.


Are these the same errors you get?
+1

I observed that my USB mouse continues to work after a sleep (Suspend to RAM) but my keyboard and mouse pad fails to work.

Has anyone got the same problem on any other distros? I quickly glanced through gentoo forums and could not find any similar problem reported. Maybe this is a ubuntu specific or rather kernel specific bug. Googling more info about this...

---

### Post by fornix on 2009-05-28
For people facing the problem of keyboard and touchpad not working after suspend, the following thread gives a solution
[http://ubuntuforums.org/showthread.php?t=1047284]("http://ubuntuforums.org/showthread.php?t=1047284")

---

### Post by fiveacez on 2009-05-28
> **whichpaul said:**
> 
At present it appea.rs to be a bug in the BIOS, so this puts a fix in the hands of HP.


Oh goody.

---

### Post by whichpaul on 2009-06-02
[Bug #301353]("https://bugs.launchpad.net/bugs/301353") has been fixed by a BIOS update from HP!

If you have a HP dv5, dv4, dv6 or HDX update your BIOS to the latest release from HP (May release onwards).

In a future release of the Linux kernel the faulty BIOS will be blacklisted so that it simply generates a warning / error instead of failing.

---

### Post by fiveacez on 2009-06-02
Wow, I was about to go downgrade to 8.04.  This works for Jaunty too - not just 8.10 - right?

---

### Post by whichpaul on 2009-06-03
> **fiveacez said:**
> Wow, I was about to go downgrade to 8.04.  This works for Jaunty too - not just 8.10 - right?

Definitely! Jaunty, Ibex etc., they all work. With a healthy dose of laptop-mode thrown in I'm in Ubuntu power-saving heaven!

---

### Post by vilar on 2009-06-22
I'm getting the same kind of problem, but I never got any kind of problem after suspending.

Are these problems (ata1) and (ata2) softreset failed bad for the computer by any means? It seems to work out fine after the logon. 

I found these links that you posted about how to fix these warnings on startup but I don't know how to proceed to fix them. Can anybody help me out?

Which is the correct way to fix this? By adding the lauchpad repositories and keys and then looking for upgrades?

Thanks for the attention.

---

### Post by fiveacez on 2009-06-22
> **vilar said:**
> I'm getting the same kind of problem, but I never got any kind of problem after suspending.

Are these problems (ata1) and (ata2) softreset failed bad for the computer by any means? It seems to work out fine after the logon. 

I found these links that you posted about how to fix these warnings on startup but I don't know how to proceed to fix them. Can anybody help me out?

Which is the correct way to fix this? By adding the lauchpad repositories and keys and then looking for upgrades?

Thanks for the attention.

When did you last update the BIOS?

---

### Post by vilar on 2009-06-22
I updated the BIOS to install Ubuntu on my laptop (hp dv5), it's the most recent on HP's website.

It's the F.34 version.

---

### Post by Amorphous_Snake on 2009-06-30
I am pleased to say that I no longer have this issue. I updated my BIOS from the HP website and now I can suspend and wake up without any errors.

If only Ubuntu can give me audio through HDMI...

Thanks to all those who replied and to those who *persuaded* HP to release the new BIOS.

---

### Post by alshurooqi on 2010-05-29
I have DV5 1070ee I updated the BIOS.
I can suspend **[SIZE="5"]only[/SIZE]** if you start the ubuntu 10.4 and you reach the login screen close the lid or select suspend from the icon below it will suspend.
If I try it after login it will hang the system.

---

### Post by mortezamilani on 2010-10-22
I had the same problem with my HP Pavilion dv5-1299ee. I posted how I fixed it here:

Al hamdo Lel Alah ;)

[http://ubuntuforums.org/showthread.php?t=1135185](http://ubuntuforums.org/showthread.php?t=1135185)

---

