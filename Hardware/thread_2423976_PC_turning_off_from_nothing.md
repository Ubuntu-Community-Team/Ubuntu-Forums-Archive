---
title: "PC turning off from nothing"
date: 2019-08-01
forum: Hardware
---

### Post by atipico on 2019-08-01
Please, how can debug a PC that is turning off from nothing so I can start investigating the problem? Thank you.

---

### Post by SeijiSensei on 2019-08-01
Overheating maybe?

---

### Post by Autodave on 2019-08-01
Overheating, RAM failing, power supply failing?

Please give us some info on your system.

---

### Post by TheFu on 2019-08-01
Could be anything.  I'd check the system logs.  

Might need to enable logs that are retained over reboots.  I think a method to enable that is 
```
sudo mkdir /var/log/journal
sudo chmod 755 /var/log/journal
sudo chmod g+s,+t /var/log/journal
sudo chown root:systemd-journal  /var/log/journal

```Then restart the systemd-journald service.

But it could be anything.  House electrical wiring, PSU, cracked motherboard, failing GPU, overheating, bad cable(s) inside the machine, pretty much anything.  If the system logs don't show anything, I'd reseat all the cables, just to be certain.  I'd try older and newer kernels, but kernels almost always log issues.  If that doesn't fix it and the logs are still without help, then I'd change the PSU, then the GPU, then the MB.

All this assumes that everything was working fine for a few months before this issue began.

I've never had a RAM issue, but it wouldn't hurt to run memtest86+ overnight and reseat the RAM.

The easy way to provide system information is to install inxi and run
```
inxi -Fz
```
then post the output between "code" tags.  If it doesn't line up the same in your post as it does in the terminal, please fix it.  Adv-Reply (#).  The easier it is to read, the more people will help.

---

