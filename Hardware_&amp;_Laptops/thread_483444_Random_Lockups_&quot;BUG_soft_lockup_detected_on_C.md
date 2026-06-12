---
title: "Random Lockups: &quot;BUG: soft lockup detected on CPU#0!&quot;"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by gashad on 2007-06-24
My computer will randomly lock up for roughly ten seconds at a time.  I will then get about 3 seconds of interactivity with my machine before it locks up for another ten seconds.  I get ocassionally get an error at the terminal: 
[timestamp] BUG: soft lockup detected on CPU#0!

This will happen very randomly:  sometimes immediately after booting the system, I get this problem... other times, my system will work fine for a few hours.  In all cases, I have one or more of the following running:  firefox, thunderbird, konsole, rhythmbox.  I've tried the following:
*blacklisting my wireless driver (ipw2100 in /etc/modules/blacklist)
*disabling splash at startup
*disable all network interfaces
*boot into "recovery mode"... same problem happens

After having a stable Ubuntu 6.10 system for a long time, I started randomly getting this problem.  Thinking it's something with an outdated kernel, I did a fresh format/install of Ubuntu 7.04 Feisty on a Dell inspiron 600m with:
* radeon mobility (but using the software "ati" driver) 
* intel ipw2100 (setup however ubuntu does it by default). 
* output of "uname -a": Linux [hostname] 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Any ideas?  I was thinking of posting a bug report to launchpad...

See attachments for dmesg, lspci and lsmod output.

Thanks!!
-Pete

---

### Post by bigken on 2007-06-24
check your ram could  be 1 of the chips has gone bad

---

### Post by gashad on 2007-06-24
Running a dual boot with WinXP... the WinXP partition works flawlessly (well... as good as possible for a windows partition ;)

---

### Post by bigken on 2007-06-25
what brand is your video card

---

### Post by gashad on 2007-06-25
> **bigken said:**
> what brand is your video card

ATI Mobility radeon 9000. My xorg loads the "ati" software driver

---

### Post by bigken on 2007-06-25
have you done all the updates 

I have htpc in the bedroom which constantly locked up running feisty mythtv when I did manage to get all the updates the machine has run flawlessly sorry I cant be of more help :(

---

### Post by gashad on 2007-06-25
Yes, the machine is fully up-to-date via
sudo apt-get update
sudo apt-get upgrade

---

### Post by bigken on 2007-06-25
try running the live cd see if this still happens

---

### Post by vauxje on 2007-06-26
I have the same laptop and the same issue. Adding 'noacpi noapic nolapic' to kernel boot options doesn't fix it. Swapping out the wireless card for a rt2500 chipset (using either the stock driver or ndiswrapper) doesn't fix it, either. It happens in both ubuntu and kubuntu - wiping the hard drive and installing from scratch. It doesn't happen in XP.

---

### Post by gashad on 2007-06-28
> **bigken said:**
> try running the live cd see if this still happens

It happened with the live CD.  
$uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

Attaching lspci, lsmod... dmesg log wouldn't fit (needs to be <19kb on the forum...) 

From dmesg, it looks like ipw2100 might be cauing my problems:

[  848.528000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  956.052000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[  956.052000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[  957.552000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  967.900000] eth1: no IPv6 routers present
[ 1001.732000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1023.400000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1043.304000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1062.268000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1084.128000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1092.036000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1104.512000] BUG: soft lockup detected on CPU#0!
[ 1104.512000]  [<c015353c>] softlockup_tick+0x9c/0xf0
[ 1104.512000]  [<c0130633>] update_process_times+0x33/0x80
[ 1104.512000]  [<c0106c45>] timer_interrupt+0x85/0xb0
[ 1104.512000]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[ 1104.512000]  [<c015516d>] handle_level_irq+0x8d/0x120
[ 1104.512000]  [<f08c8db0>] tg3_timer+0x0/0x810 [tg3]
[ 1104.512000]  [<c0105b70>] do_IRQ+0x40/0x80
[ 1104.512000]  [<f08c8db0>] tg3_timer+0x0/0x810 [tg3]
[ 1104.512000]  [<c0104233>] common_interrupt+0x23/0x30
[ 1104.512000]  [<f08c8db0>] tg3_timer+0x0/0x810 [tg3]
[ 1104.512000]  [<f08c00d8>] tg3_chip_reset+0x168/0x630 [tg3]
[ 1104.512000]  [<c011c112>] native_read_tsc+0x2/0x10
[ 1104.512000]  [<c01f17d8>] delay_tsc+0x18/0x30
[ 1104.512000]  [<c01f1836>] __delay+0x6/0x10
[ 1104.512000]  [<f08bb2f6>] tg3_readphy+0x66/0x100 [tg3]
[ 1104.512000]  [<f08be16b>] tg3_setup_copper_phy+0x1bb/0xc00 [tg3]
[ 1104.512000]  [<c02a0e7c>] ip_rcv+0x2bc/0x500
[ 1104.512000]  [<f08c8db0>] tg3_timer+0x0/0x810 [tg3]
[ 1104.512000]  [<f08bed68>] tg3_setup_phy+0x1b8/0xe70 [tg3]
[ 1104.512000]  [<c013f43a>] clocksource_get_next+0x3a/0x40
[ 1104.512000]  [<c012fb54>] do_timer+0x234/0x820
[ 1104.512000]  [<f08c8db0>] tg3_timer+0x0/0x810 [tg3]
[ 1104.512000]  [<f08c943c>] tg3_timer+0x68c/0x810 [tg3]
[ 1104.512000]  [<c0284cb3>] process_backlog+0x93/0x130
[ 1104.512000]  [<c012f73f>] run_timer_softirq+0x12f/0x1a0
[ 1104.512000]  [<c012b422>] __do_softirq+0x82/0x100
[ 1104.512000]  [<c012b4f5>] do_softirq+0x55/0x60
[ 1104.512000]  [<c0105b75>] do_IRQ+0x45/0x80
[ 1104.512000]  [<c0219e2e>] acpi_hw_register_write+0x154/0x187
[ 1104.512000]  [<c0104233>] common_interrupt+0x23/0x30
[ 1104.512000]  [<f08317e2>] acpi_processor_idle+0x225/0x3f7 [processor]
[ 1104.512000]  [<c0101409>] cpu_idle+0x49/0xd0
[ 1104.512000]  [<c03d77f5>] start_kernel+0x365/0x420
[ 1104.512000]  [<c03d7230>] unknown_bootoption+0x0/0x260
[ 1104.512000]  =======================

---

### Post by bigken on 2007-06-28
I would remove the card and see what happens 

if the system stops crashing buy a new intel abg wifi card they only cost £20

---

### Post by gashad on 2007-06-28
> **vauxje said:**
> I have the same laptop and the same issue. Adding 'noacpi noapic nolapic' to kernel boot options doesn't fix it. Swapping out the wireless card for a rt2500 chipset (using either the stock driver or ndiswrapper) doesn't fix it, either. It happens in both ubuntu and kubuntu - wiping the hard drive and installing from scratch. It doesn't happen in XP.

I've been adding comments to a bug report posted here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95143](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95143)

You should add these comments to the bug report, along with dmesg, lspci, lsmod, uname -a output so they have more to work with while debugging this.

---

### Post by gashad on 2007-06-28
> **bigken said:**
> I would remove the card and see what happens 

if the system stops crashing buy a new intel abg wifi card they only cost £20

Hrm... From the dell online service manual for the Inspiron 600m, I think I should be able to physically remove the wireless ipw2100:
[http://support.dell.com/support/edocs/systems/ins600m/en/sm/index.htm](http://support.dell.com/support/edocs/systems/ins600m/en/sm/index.htm)

Specifically, I think the 2100 is in the "Mini PCI" slot:
[http://support.dell.com/support/edocs/systems/ins600m/en/sm/upgrades.htm#1019173](http://support.dell.com/support/edocs/systems/ins600m/en/sm/upgrades.htm#1019173)

It would be extremely strange to me if removing the card actually solves the problem, since I use the ipw2100 in WinXP and have never really had any crashes... 

Anyway, thanks for the suggestion, I'll post a follow-up when I get around to removing the card.

-Pete

---

### Post by vauxje on 2007-06-28
> **gashad said:**
> ...Anyway, thanks for the suggestion, I'll post a follow-up when I get around to removing the card.

I tried with no effect...I wish you better luck.

---

### Post by vauxje on 2007-06-29
Here are the pertinent files:

---

