---
title: "Advice for multi boot setup"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by rnawky on 2009-02-04
I have a new hard drive coming in the mail and I was wondering what the best setup would be partition wise for installing kubuntu, ubuntu, suse, and fedora on the same drive.

Each distro can share the same /swap and /home right?

Then what size would I make each installs root? is 10GB enough?

---

### Post by lha on 2009-02-08
Is there a specific reason why you want to install Ubuntu and Kubuntu? You can get both Gnome and KDE in one (K)Ubuntu installation, just install kubuntu-desktop or ubuntu-desktop after installing Ubuntu or Kubuntu.

In my opinion, sharing /home isn't advisable. It can lead to conflicts with user id:s, and it will lead to problems when different versions of a program use the same config file. Assuming you are the only person using your computer, I'd recommend you to make a partition for your personal files and mount it under, e.g., /home/rnawky/myfiles. This allows each distro to have its own config files, but you can still easily access all your data.

Swap partition can be shared.

10 GB sounds reasonable for root partition, mine is ~7 GB with 4.5 GB used.

---

