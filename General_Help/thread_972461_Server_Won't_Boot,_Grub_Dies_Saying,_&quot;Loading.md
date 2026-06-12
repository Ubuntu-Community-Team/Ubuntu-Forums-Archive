---
title: "Server Won't Boot, Grub Dies Saying, &quot;Loading, please wait&quot; on multiple kernels"
date: 2008-11-05
forum: General Help
---

### Post by mootpoint on 2008-11-05
Ummm, help. Here's a rundown of events:

1) Server became unreachable over the network. A telnet to port 22 would open, but no ssh string, and ssh to the box would fail. Same with port 25 (box is a mail server). Webmail on port 443 would display the login page, so apache was still alive, but then hang after entering login name and password ... presumably while trying to connect to other processes to verify username/password or open the mailbox?

2) When I got home, server was unresponsive on the console. Had to power it off and restart it. Grub loads, but OS does not boot on any of the menu items ... just sits there after putting, "Loading, please wait" on the screen.

3) Booted box from Ubuntu install CD, went to recovery mode. Recovery CD can mount the root fs ok. A quick check and nothing is obviously missing. e2fsck -f /dev/mercury/root (after umounting, obviously!) reports a clean fs. (File system is ext3 running on top of lvm on a single 500gb drive ... never did get addition drive space into the box yet ...)

4) No bad news in syslog.

5) Box is generic PC, nothing special or unusual, running Ubuntu 8.04. Can't imagine any other details matter here, since the issue is getting grub to actually load the OS.

What should I do next?

---

### Post by mootpoint on 2008-11-05
Got lucky ... apt-get installed a newer kernel that doesn't like this machine. An old kernel booted. Data backing up, machine rebuild forthcoming. 

Phshew.

---

