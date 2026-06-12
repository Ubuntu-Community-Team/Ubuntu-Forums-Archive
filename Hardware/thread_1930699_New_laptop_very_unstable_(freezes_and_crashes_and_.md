---
title: "New laptop very unstable (freezes and crashes and kernel panics) with Ubuntu 11.04"
date: 2012-02-24
forum: Hardware
---

### Post by UeB on 2012-02-24
Hallo all,

I have installed Ubuntu 11.04 on a new laptop (LENOVO G770 M533XGE) and I can hardly use it because it is so unstable. Normally it does not run longer then 10 min (often less) before it either freezes or the screen just turns black, or a kernel panic is shown.

What I tried so far:
downloaded all official ubuntu updates in installed them via the normal update application. It took me at least 10 attempts to get them installed before the laptop crashed.
Deactivated the ati graphics card in the BIOS so that it is using only the on board intel graphics.
Installing the not free drivers for the wireless lan (broadcom).

I do not think the hardware is broken because I also installed Linux Mint 12 (which is based on Ubuntu 11.10) where I can write this post new without my laptop crashing all the time.

Now before you say why not just stay with the newer linux version:
I need to build some special software for the work I am doing for my phd which does not work in the most resent versions of Ubuntu and Fedora (because default gcc linker behavior was changed there and there this software cannot compiled on theses distros -- it is a known problem)

I attached the output of lshw to let you know what hardware the laptop has.

My main question would be if there are any known issues with this hardware and Ubuntu 11.04.

Thanks in advance for any help or suggestion!

---

### Post by phxnd on 2012-02-24
> **UeB said:**
> Hallo all,

I have installed Ubuntu 11.04 on a new laptop (LENOVO G770 M533XGE) and I can hardly use it because it is so unstable. Normally it does not run longer then 10 min (often less) before it either freezes or the screen just turns black, or a kernel panic is shown.

What I tried so far:
downloaded all official ubuntu updates in installed them via the normal update application. It took me at least 10 attempts to get them installed before the laptop crashed.
Deactivated the ati graphics card in the BIOS so that it is using only the on board intel graphics.
Installing the not free drivers for the wireless lan (broadcom).

I do not think the hardware is broken because I also installed Linux Mint 12 (which is based on Ubuntu 11.10) where I can write this post new without my laptop crashing all the time.

Now before you say why not just stay with the newer linux version:
I need to build some special software for the work I am doing for my phd which does not work in the most resent versions of Ubuntu and Fedora (because default gcc linker behavior was changed there and there this software cannot compiled on theses distros -- it is a known problem)

I attached the output of lshw to let you know what hardware the laptop has.

My main question would be if there are any known issues with this hardware and Ubuntu 11.04.

Thanks in advance for any help or suggestion!

I've a similar problem with my ubuntu, suddenly my laptop starts freezeing. Recently I changed to MintLinux and the problem presist. I'll apreciate any help the comunity could give to us.


Did you try compiling on Debian? I've had to do a practical work to the university and the beahvour on one of the lastes versions of ubuntu was terrible. Then I get around that installing a Debian VM in Windows.

---

### Post by Dlambert on 2012-02-24
Maybe try Ubuntu tweak to clean out the system, or BleachBIT works well too!

---

