---
title: "fun with kexec"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by inportb on 2008-02-27
I decided to have some fun with kexec in Hardy and see how fast the kernel can be restarted.

I figured that I should make the process as clean as possible, so I hacked my /etc/init.d/reboot script to kexec instead of reboot:

```
do_stop () {
	# Message should end with a newline since kFreeBSD may
	# print more stuff (see #323749)
	log_action_msg "Will now restart"

	if [ -x /sbin/kexec ]; then
		kexec -l --append="`cat /proc/cmdline`" --initrd=/boot/initrd.img-`uname -r` /boot/vmlinuz-`uname -r`
		sync
		umount -a
		kexec -e
	fi

	reboot -d -f -i	# we should never get here
}
```

While it works very well, I have a minor annoyance -- the audio system is not properly initialized on boot. The hardware is detected alright (lspci says I have a sound card), but it just does not work (ALSA disagrees). The audio system works when booting the regular way.

I know that kexec does not reset all the hardware to a known state like the BIOS does, so that might be the problem. Is there any way this issue can be mitigated/fixed?

Thanks!

---

### Post by inportb on 2008-03-02
Any ideas? lspci lists the audio device as

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

I just had one of my buddies test this out, and it worked perfectly for him.

---

