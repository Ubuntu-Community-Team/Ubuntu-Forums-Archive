---
title: "Detailed hash sum mismatch - troubleshooting help needed"
date: 2008-11-03
forum: General Help
---

### Post by smacksaw on 2008-11-03
I have two Acer Aspire One PCs that are identical. I can load them both with the exact same Ubuntu media, Hardy or Intrepid. And 100% of the time machine A works perfectly and 100% of the time machine B does not. From trial and error as well as process of elimination, I have determined that my Synaptic hash sum mismatch has to do with wireless networking on my offending machine.

When it is done, it says Some of the packages could not be retrieved from the server(s). Do you want to continue, ignoring these packages?

Here are some sample errors (it always fails, and never on the same packages):

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-zh-cn_2.4.1-9ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-zh-cn_2.4.1-9ubuntu1_all.deb)
  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/anthy/anthy_9100e-3.2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/anthy/anthy_9100e-3.2ubuntu1_i386.deb)
  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libhangul/libhangul0_0.0.8-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libhangul/libhangul0_0.0.8-3_i386.deb)
  Hash Sum mismatch

My Synaptic hash sum mismatch failures:

*From a clean install, the failing machine never works while the successful machine always works
*Using a wired connection never fails
*Saying "no" on the "do you want to continue" allows me to apply it until it eventually works
*Download rate goes to unknown during the transfer
*There is no other network traffic - I can do this in parallel on identical machines and it doesn't fail on the working unit
*This happens with Hardy or Intrepid, and I am using the 53xx Atheros drivers - as we know, on the Aspire one you must use the proper driver
*This seems to also affect streaming video and other things that require persistent connectivity
*My network connection is fine, range, signal strength, etc
*This problem does not happen when I boot into XP

Therefore, I doubt that it is defective. I know that sometimes identical machines do not always have identical components. My theory is that the card is shutting down for some reason. There must be some subtle difference between the two machines. The driver might be bad, but I have tried quite a few clean installs using madwifi myself, the ubuntu-eee fork, regular Hardy, regular Intrepid...I need some direction here as I don't want to return this computer, especially since the people at Best Buy are not savvy enough to understand why this isn't working.

---

### Post by bigPoppaJosh on 2008-11-04
I'm sorry to say I can't help you, but I can back you up a bit.  I have a hash mismatch on an old toshiba laptop, but it fails on kernel package 'linux-generic' and /var/log/syslog says failed to fetch cdrom [...ibex...386...0081028]/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-2.6.27-7-generic_2.6.27-7.12_i386.deb Hash Sum mismatch.

/var/log/syslog also suggests an apt-get which isn't supported in the busybox shell of course.

I have tried the install a few times and it fails in the same spot.  I have done a 'check cd for defects' which came up clean

---

