---
title: "Ubuntu under VirtualBox"
date: 2013-04-25
forum: Hardware
---

### Post by strictlymike on 2013-04-25
I can't get Ubuntu to install or install correctly on VirtualBox.

I've tried:
* 12.04 LTS 32-bit
* 12.10 32-bit, 64-bit,
* 13.04 64-bit

Within:
* VirtualBox-4.2.12-84980-Win on Windows 7 Professional
* VirtualBox 4.1.18_ubuntu r78361 installed via Aptitude on Kubuntu 12.10

Using:
* Intel E1000 MT Desktop emulated adapter type
* PCnet-FAST III (Am79C973) emulated adapter type
* PCnet PC II (Am79C970A) emulated adapter type

I've had various results.  Generally, I see that either the network isn't available, or it *is* available until I click "download updates" / "install proprietary..." and am about to click Continue (image 1 attached).  At TTY1, I indeed cannot ping gentoo.org or google.com, although I have a NAT IP address, 10.0.2.15 for instance.

If I proceed, sometimes 12.04 hangs on file 43 of 105.

When it does not, and the installation manages to finish (most recently, 13.04 did), it invariably says it is operating in "low graphics mode" (image 2 attached).  When it prompts me for what to do (image 3), run in low graphics mode kicks me out to a console and reconfigure gives me an infinite loop of clicking OK to either using my default config or my backed-up config (image 4).

I also noticed an unusual swap partition delay with 13.04 (image 5), but that's kind of ancillary to my problems here.

I seem to have seen lots of evidence of success running Ubuntu under VirtualBox.   But under either Ubuntu or Windows as my host, I haven't been as successful.   What can I do to troubleshoot?

I would have posted this under virtualization, but that seems to be a place for people who want to use virtualization within Ubuntu, not vice-versa.  So, I've posted in hardware, since I am having trouble installing Ubuntu on (virtual) hardware, namely VirtualBox.

---

