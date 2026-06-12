---
title: "How do I configure a no-modules kernel build for a particular machine?"
date: 2008-10-19
forum: Hardware
---

### Post by mishad on 2008-10-19
H/W: Dell Dimension M233 (233MHz P-MMX, 128MB, 6GB HD)

I'm running Ubuntu Hardy 8.04-1 Server, to which I've added LXDE (from external repos) and SLiM -- I'm trying to make this as lightweight as possible, just enough for  light browsing (Dillo/Midori), TuxPaint, simple word-processing.

Boottime is currently very slow -- around 4 mins.

Bootchart shows that the CPU is busy for most of that time, so to improve I'll have to make it do less work at boot time, not just shuffle around the order/concurrency. The biggest single delay is modprobe.

I read reports of 5 second Linux boot times, which used specifically configured kernel to avoid initrd and modprobe overheads (at the cost of flexibility, of course). Now, I know I won't get down to 5 seconds on this old jalopy, but if I can cut it down by a minute or two that would be great.

Is there a way to automatically determine (e.g. using lspci/lsmod) which kernel options I need to set to rebuild the kernel with exactly the needed drivers built in (not as modules)?

Ideally there would be a program that does this to build a slimline kernel for the current config, sets up the appropriate grub entries, and if the "slimline" boot fails fall back to an "all modules + initrd" grub entry. But a manual procedure would be fine for now.

Misha

---

