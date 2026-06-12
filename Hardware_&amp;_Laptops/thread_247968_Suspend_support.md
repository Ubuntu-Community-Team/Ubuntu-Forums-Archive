---
title: "Suspend support"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by jalexstark on 2006-08-31
A friend just asked me about recommending a laptop for linux, but had to reply that I couldn't confidently recommend linux.  And I have used it for years.  This is a great disappointment to me.

Dapper and Breezy apm support is seriously broken, and documentation indicates that acpi is a mess.  I have given up trying to get *any* kind of suspend or hibernation on a T20.

It used to work great 4 years ago, then with Mandriva(drake), but "improvements" have ruined it.

Yes, I have done the "noacpi" boot commands, etc, etc, BUT! when I ask for Gnome/system/quit/suspend, the kernel/modules/drivers go into a death spiral, and "ps ax" indicates - YES! - that there is a process with "acpi" in it.

Does it work better if you install from scratch?  If so, will someone please declare apm/laptop officially not upgradable.  PLEASE!

All after another 4 hours of wasted reboots and reading of posts.

(At least the prism54 hotplug worked.  FYI, the "updates" to the breezy kernels are broken: my network card stopped working reliably with one of the fixes.  This is corrected in Dapper.)

Alex

---

### Post by Nathaniel on 2006-08-31
I'm having similar issues, but a tad more recent...

Suspend worked perfectly out-of-the-box with Breezy, and both sound and WiFi drivers were installed without a single hitch.

Come Dapper, and suspend is broken again. I don't know why, and 4 postings about the issue later, I still haven't got a single response...

I run Dapper on a ThinkPad T43, a VERY popular model with no really weird, unsupported hardware at all.

---

### Post by hizaguchi on 2006-08-31
I think power management with Linux is just sketchy all around.  I'll admit that Ubuntu has some weird problems all of its own, but I've not found any distros that work 100% with any computer I've tried.

---

### Post by missmoondog on 2006-09-15
my one and only real complaint about k/ubuntu. have to keep winblows on my main machine just for that reason and my non linux supported visioneer scanner. i come and go way to many times early in the day to not be able to have standby work. that really stinks!! :(

support is just as lousy, if not worse even, for desktops.

---

### Post by xyz on 2006-09-15
I nerver had pbm with hibernation (Dapper user). However I solved my own suspend issue here: (addresses the hibernation issue,too)
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

Also, might help:
[http://packages.ubuntu.com/dapper/utils/hibernate](http://packages.ubuntu.com/dapper/utils/hibernate)

---

