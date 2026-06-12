---
title: "Laptop Suspend/Hibernate"
date: 2011-04-29
forum: Hardware
---

### Post by sourya_s7 on 2011-04-29
Hey,
I am on an ASUS N61JQ Laptop and am having an issue with suspend/hibernate. I'm using the 64bit ubuntu 11.4. Whenever I try to suspend, the screen goes black and the laptop just hangs. It is the same case with hibernate. But with hibernate,even though I have to manually power off the laptop, the session does resume when I restart the laptop.

---

### Post by dinoc on 2011-04-29
I have the same issue on my Sony Vaio VPCY21.

---

### Post by saggitheman on 2011-04-29
same here

---

### Post by Novacaptain on 2011-04-30
same issue here (11.04 64bit on Dell studio 1747)

---

### Post by mpace965 on 2011-04-30
Same issue Dell Studio 1749. Eventually if we all say we have a problem something will get fixed right? XD

@Novacaptain [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994) I'm being hopeful and watching this. If you don't already have a Launchpad account, make one and say it affects you.

---

### Post by dinoc on 2011-04-30
Yes that's the idea, if we do report as many as we can, maybe it will be fixed.

Some interesting article found recently :
**Mobile Users Beware: Linux Has Major Power Regression:**
[http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1]("http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1")

Too bad such a nice new Ubuntu interface is lacking a such important feature for our laptops like power management ...

---

### Post by lidex on 2011-04-30
For your issues to be addressed, you need to file a bug at launchpad to actually get the dev's attention. They'll never see this thread.

---

### Post by dinoc on 2011-05-04
I have updated the Launchpad with my issue, also.

---

### Post by lidex on 2011-05-04
> **dinoc said:**
> I have updated the Launchpad with my issue, also.

Good. Could you post the link here so that others can sign on?

---

### Post by dinoc on 2011-05-05
Is the same link @mpace965 post it above

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994)

---

### Post by dinoc on 2011-06-09
Does this issue happen on 64 bit only version ?

I've read that someone tried the same Ubuntu version but the 32 bit one, and he says the issue is not there .

Anyone tried the 32bit version which can confirm this ?

---

### Post by dimeotane on 2011-06-11
I'm on the 32 bit 11.04 isn't working on my Toshiba NB200... it will go into sleep mode.. up on resume  the screen remains black.  I need to reboot.

---

### Post by dinoc on 2011-06-11
yes other members reported the same thing on the bug topic,

thanks for confirming this

---

### Post by ChrisEiffel on 2011-06-13
I have the same issue

When I hibernate, the screen goes black (no Ubuntu with the red dots)

Eventially I get this cryptic text that appears on the screen. 

mountall disconnect: Plymouth
mountall failed

(I'm recalling this from memory so I don't know if I remembered it perfect)

The hibernation process then proceeds to hang and I have to hold the  power button to turn the computer off. The session is not restored on  next startup.

64 bit 11.04

---

### Post by SirKonstantine on 2011-07-16
Same problem on my Gateway NV5927u. When I press suspend (there is no hibernate) it goes to a flickering black screen. I think X11 just hangs or something and I have to go to a terminal to shut the PC down.

---

### Post by dinoc on 2011-09-10
It looks like the guys with Dell laptops found a solution to the hibernation/suspend issue by blacklisting the firewire modules

I've tried that but for me is not working .

I've opened a separate bug for Sony Vaio laptops, so if you guys are still having this issue please report here too:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357)

---

### Post by chrisk169 on 2011-09-12
> **dinoc said:**
> It looks like the guys with Dell laptops found a solution to the hibernation/suspend issue by blacklisting the firewire modules

I've tried that but for me is not working .

I've opened a separate bug for Sony Vaio laptops, so if you guys are still having this issue please report here too:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357)

Hi all,
I logged the solution of kernel 2.6.35-020635-generic having worked for me (on Dell 1749 Studio) earlier.

I tried this "blacklisting" trick on kernel 2.6.38-10-generic (last update) and it worked only if you had NOTHING MORE than maybe a 'terminal' session active when you try to 'hibernate' (any more - Firefox with a few tabs open + Evolution <<--CRASH).

Otherwise it fails just like the original but the syslog shows:
 
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336463] Pid: 1195, comm: Xorg Tainted: P            2.6.38-10-generic #46-Ubuntu
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336465] Call Trace:
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336510]  [<ffffffffa0221d4e>] ? KCL_DEBUG_OsDump+0xe/0x10 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336532]  [<ffffffffa022f28c>] ? firegl_hardwareHangRecovery+0x1c/0x50 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336576]  [<ffffffffa02b54d9>] ? _ZN4Asic9WaitUntil15ResetASICIfHungEv+0x9/0x10 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336617]  [<ffffffffa02b548c>] ? _ZN4Asic9WaitUntil15WaitForCompleteEv+0x6c/0xb0 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336659]  [<ffffffffa02b3b34>] ? _ZN15ExecutableUnits10CPRingIdleE15idle_WaitMethod12_QS_CP_RING_+0xe4/0x1a0 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336701]  [<ffffffffa02b39fb>] ? _ZN15ExecutableUnits7PM4idleE15idle_WaitMethod+0x4b/0x90 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336742]  [<ffffffffa02b36ae>] ? _ZN15ExecutableUnits9assertPM4Eb+0x1e/0x70 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336784]  [<ffffffffa02bb7e0>] ? _ZN8AsicR6009assertPM4Eb+0x40/0x70 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336810]  [<ffffffffa024c4a0>] ? firegl_cmmqs_disableqs+0x0/0x90 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336847]  [<ffffffffa0290aa6>] ? CMMQS_DisableQS+0x16/0x20 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336872]  [<ffffffffa024c4a0>] ? firegl_cmmqs_disableqs+0x0/0x90 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336897]  [<ffffffffa024e042>] ? firegl_cmmqs_Disable_QS+0x62/0x80 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336922]  [<ffffffffa024c4c0>] ? firegl_cmmqs_disableqs+0x20/0x90 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336938]  [<ffffffffa021d9d6>] ? KCL_PosixSecurityCapCheck+0x26/0x30 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336958]  [<ffffffffa022ae5a>] ? firegl_ioctl+0x1ea/0x250 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336972]  [<ffffffffa021bd7e>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336977]  [<ffffffff811764cf>] ? do_vfs_ioctl+0x8f/0x360
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336980]  [<ffffffff81164e73>] ? vfs_write+0x123/0x180
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336983]  [<ffffffff81176831>] ? sys_ioctl+0x91/0xa0
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336986]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
Sep  7 09:41:29 chrisk-Studio-1749 kernel: [ 1687.336990] pubdev:0xffffffffa0462220, num of device:1 , name:fglrx, major 8, minor 85. 

I think it is much more than coincedence that many of the 'failed' lines above refer to 'firegl' and I believe that 'blacklisting' the 'firewire' entries is what causes it to fail.
Back to my '2.6.35' kernel and both Suspend and Hibernate work as expected:D.

ChrisK

---

