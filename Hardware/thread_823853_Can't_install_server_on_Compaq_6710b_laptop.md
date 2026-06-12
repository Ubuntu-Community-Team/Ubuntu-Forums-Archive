---
title: "Can't install server on Compaq 6710b laptop"
date: 2008-06-09
forum: Hardware
---

### Post by bigteks on 2008-06-09
Desktop loads fine on this system but I want to use server because I'm loading several VMs and I the majority of the system resources to go to the VMs, not the base operating system.

When I start the install it says loading linux kernal and then it says kernal alive and after that the screen goes blank and nothing happens.

Is there a way around this? Or should I just give up on trying to install server on my laptop? This is Hardy Heron.

---

### Post by bigteks on 2008-06-09
Alternately, is there a better way to accomplish this? Maybe some other light-weight ubuntu install package would do a better job of serving as a platform from which to run VMware server? I'm open to ideas.

---

### Post by bigteks on 2008-06-09
I just tried installing fluxbuntu and got exactly the same behavior. I'm guessing some kind of problem with the lightweight display driver in the non-GUI installer, not being able to talk to the laptop display. The laptop uses  The GUI-based installer works fine but the command-line based installer can't seem to display anything.

The video is reported as a "Mobile Intel 965 Express Chipset family"

Any ideas what is going wrong? Or how to work around it? Should I try to install full ubuntu which works fine and then uninstall packages until I have a lightweight install and then install flux on top of that?  :(

---

