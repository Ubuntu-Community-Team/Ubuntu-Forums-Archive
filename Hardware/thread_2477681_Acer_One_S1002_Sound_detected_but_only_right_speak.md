---
title: "Acer One S1002 Sound detected but only right speaker is playing."
date: 2022-08-03
forum: Hardware
---

### Post by andrzejl2 on 2022-08-03
Hello,

My father bought this PoS machine which is HORRIBLE in every single way (I curse at Acer for releasing it):

- 64 bit capable CPU but 32 bit UEFI which means Windows 64 bit and most of 64 bit distos fails to boot or install
- 2 gigs of SOLDERED ram memory, no upgrade possible
- 30 gb memory card (yes its a memory card NOT hdd or ssd)
- many other faults

Anyway. I got Ubuntu 22.04 LTS working on it (wasn't easy) as system fails to boot after initial install. Needs to be booted into LiveUSB and from "Try Ubuntu" connected to internet and fixed using these commands:

```
mount /dev/mmcblk2p2 /mnt
mount -t proc none /mnt/proc/
mount -o bind /dev /mnt/dev/
mount -o bind /sys /mnt/sys/
mount -o bind /run /mnt/run/
mount -t efivarfs none /mnt/sys/firmware/efi/efivars
mount /dev/mmcblk2p1 /mnt/boot/efi/
chroot /mnt
apt-get remove -y --purge --allow-remove-essential grub-efi-amd64-signed shim-signed
apt -y install efibootmgr grub-common grub-efi-ia32 grub-efi-ia32-bin grub-pc-bin grub2-common mokutil secureboot-db
apt -y --purge autoremove
grub-install /dev/mmcblk2
update-grub
exit
reboot
```

After that system boots as expected upon reboot.

My problem is that the sound only comes from the right speaker.

I tried alsamixer and checking if one chanel was muted.

I tried checking in Settings > Sound and moving the balance mixer to the left - nada.

I have no idea how to diagnose it.

I have no idea which diagnostic information is necessary for you guys to help me solve it so ask and you shall be given.

Problem occurs on LiveUSB as well.

System is installed as Ubuntu Minimal with 3rd party codecs / players and 100% updated.

I tried using this:

[https://github.com/plbossart/UCM/tree/master/bytcr-rt5640](https://github.com/plbossart/UCM/tree/master/bytcr-rt5640)

Thank you in advance for any help provided.

Kindest regards.

Andrzej

---

### Post by andrzejl2 on 2022-08-03
Ok so I have more data.

I have killed pulseaudio and restarted it in the terminal. Then I went to Settings > Sound > Test and when I pressed Right Speaker there was no output in terminal and the sound was played. However when I pressed Left Speaker I got a bunch of errors in terminal. Need to google that but first I wanted to update this thread.

> andrzejl@Acer-One-S1002:~$ pulseaudio -kandrzejl@Acer-One-S1002:~$ pulseaudio -k
E: [pulseaudio] main.c: Failed to kill daemon: No such process
andrzejl@Acer-One-S1002:~$ pulseaudio
W: [pulseaudio] pid.c: Stale PID file, overwriting.
N: [pulseaudio] bluez5-util.c: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?
E: [alsa-sink-PCM (*)] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write.
E: [alsa-sink-PCM (*)] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_soc_sst_bytcr_rt5640'. Please report this issue to the ALSA developers.
E: [alsa-sink-PCM (*)] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

Regards.

Andrzej

---

### Post by Yellow Pasque on 2022-08-03
Yeah, Acer makes some shoddy devices...

> Most likely this is a bug in the ALSA driver 'snd_soc_sst_bytcr_rt5640'. Please report this issue to the ALSA developers.

Not much you can do. You can try the latest kernel, and if that doesn't work, see: [https://www.kernel.org/doc/html/v5.19/sound/hd-audio/notes.html#sending-a-bug-report](https://www.kernel.org/doc/html/v5.19/sound/hd-audio/notes.html#sending-a-bug-report)
There's also good info at that link about trying to troubleshoot the problem yourself if you're technical-minded.

---

### Post by Yellow Pasque on 2022-08-04
You might also look into hdajackretask: 
```
sudo apte-get install alsa-tools-gui
hdajackretask
```

---

### Post by andrzejl2 on 2022-08-12
Guys, turns out it was a hardware issue. Left speaker or its wire is dead. Possibly sound card is partly dead. Tested with windows 10 32 bit - also only right speaker is working.

Thank you for your comments.

Kindest regards 

Andrzej

---

