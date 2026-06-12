---
title: "System hangs on &quot;waiting for resume device&quot; during boot"
date: 2008-08-13
forum: General Help
---

### Post by Theo148 on 2008-08-13
I recently resized the swap partition on one of the laptops I use, as I had upgraded its RAM and wanted it to be able to hibernate. However, whenever I boot up the machine it hangs for several seconds while displaying 'waiting for resume device'. I have already tried updating the UUIDs in /etc/fstab and /etc/initramfs-tools/conf.d/resume and running 'update-initramfs', but the system still hangs on boot (although I'm pretty sure Ubuntu is able to use the swap partition once it boots up). Oh, and resuming from hibernation doesn't work.

Can anybody help me to fix this?

---

### Post by fabian.r on 2008-08-14
Sorry, I have no solution (yet).

I have exactly the same problem on Ubuntu Hardy (upgraded from Gutsy), but I didn't resize the swap partition. I have also tried what you said without any success and hibernation doesn't work either (which is no problem for me).

ps: the problem seems to be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358").

---

### Post by Theo148 on 2008-08-14
Well I'm not sure if this will help you, but I managed to solve the problem myself - it turns out that there was another file in /etc/initramfs-tools/conf.d/ called 'resume-old' that was somehow interfering with the proper resume device configuration. I deleted the file, ran 'sudo update-initramfs' again and the system no longer hanged on boot. :)

---

### Post by fabian.r on 2008-08-14
Thanks for your reply. I have no 'resume-old' file, but I found another work around on the [Polish Ubuntu]("http://forum.ubuntu.pl/showthread.php?p=457857#post457857") forum which I could more or less understand thanks to Google language tools.

The trick is to change */usr/share/initramfs-tools/scripts/local-premount/resume*

replacing

```
. ./scripts/functions

if [ ! -e "${resume}" ] || ! /lib/udev/vol_id "${resume}" >/dev/null 2>&1; then
	log_begin_msg "Waiting for resume device..."

	# Default delay is 5s
	if [ -z "${RESUMEDELAY}" ]; then
		slumber=5
	else
		slumber=${RESUMEDELAY}
	fi
	if [ -x /sbin/usplash_write ]; then
		/sbin/usplash_write "TIMEOUT ${slumber}" || true
	fi

	slumber=$(( ${slumber} * 10 ))
	while [ ! -e "${resume}" ] || ! /lib/udev/vol_id "${resume}" >/dev/null 2>&1; do
		/bin/sleep 0.1
		slumber=$(( ${slumber} - 1 ))
		[ ${slumber} -gt 0 ] || break
	done

	if [ ${slumber} -gt 0 ]; then
		log_end_msg 0
	else
		log_end_msg 1 || true
		exit
	fi
fi
```

with

```
if [ ! -e "${resume}" ]; then
	exit
fi

```

This worked for me, but it will probably completely break the hibernation function for those who use it. Please rectify me if this information is wrong.

---

### Post by Theo148 on 2008-08-14
That seems to work as well (at least on the system I tried it on). :)

By the way, I actually followed the instructions listed [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358/comments/9") to fix the bug - I assume they worked, but were messed up by the 'resume-old' file.

---

