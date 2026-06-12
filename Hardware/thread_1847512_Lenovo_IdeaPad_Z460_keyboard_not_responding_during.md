---
title: "Lenovo IdeaPad Z460 keyboard not responding during on log-in"
date: 2011-09-20
forum: Hardware
---

### Post by skytreader on 2011-09-20
My friend is having problems with a Lenovo IdeaPad Z460---she can't type her password at log-in as the keyboard is not responding. We've tried using the on-screen keyboard but it doesn't respond either. We also tried starting an x-session from a command-line-only start-up; she can login fine via command line but after we do a sudo service gdm start, the GUI login screen asks for her password again and she still can't type it. We've tried changing the keyboard from USA to various English QWERTY set-ups (like UK, for instance) to no avail.

She's using 11.04. According to her, she first encountered the problem around 2 weeks ago and she wasn't able to use Ubuntu since then---before this problem occurred, Ubuntu was running fine (I already saw her using it before). I thought that maybe she had a kernel upgrade or something but she can't confirm/deny any kernel upgrades that happened. I think no, however, by inspecting her GRUB---there are no multiple Linux kernels there. So maybe this is a driver problem?

If it matters, she's dual-booted her machine alongside Windows 7---this isn't a WUBI installation.

Any thoughts on the matter?

Thanks!

---

