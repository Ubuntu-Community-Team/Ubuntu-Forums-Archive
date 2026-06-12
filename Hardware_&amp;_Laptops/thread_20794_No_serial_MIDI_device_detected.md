---
title: "No serial MIDI device detected"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by pantulis on 2005-03-18
Hello,

I'm trying to install the module for serial MIDI devices, snd-serial-u16550 on a Hoary box.  I keep getting the same results:

```

root@descendiente:/lib/modules/2.6.10-4-k7 # modprobe snd-serial-u16550 port=0x2f8
FATAL: Error inserting snd_serial_u16550 (/lib/modules/2.6.10-4-k7/kernel/sound/drivers/snd-serial-u16550.ko): No such device
FATAL: Error running install command for snd_serial_u16550

root@descendiente:/lib/modules/2.6.10-4-k7 # dmesg | tail
no UART detected at 0x1
serial midi soundcard not found or device busy

```

I'm completely clueless with this, can anybody help?

---

### Post by FarEast on 2005-09-05
Hello pantulis,

Are you still struggling with the problem?
I am a new comer to ubuntu and also had the problem that I had never
faced in other distros.  Fortunately, I could solve it.  Now I'm going to tell
you the way.

Note: I do not use Warty but Hoary.

Add an apt line in /etc/apt/sources.list

  deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) stable main

Then install 'kernel-image-2.6.12-3-multimedia-686' and update
'alsa-base'.  It is also recommended to install 'realtime-lsm' if you would
like to enjoy audio apps with good performance.

Restart the system with the new kernel.

Note:
You will see many lines saying 'ERROR: Removing...' at boot time.
It is no problem and appear no more by updating initrd-tools.

Create '/etc/modprove.d/sound' and describe the line below.

  options snd-serial-u16550 port=0x3f8 irq=4

Execute the following commands:

  $ sudo update-modules
  $ sudo setserial /dev/ttyS0 uart none
  $ sudo modprobe snd-serial-u16550

Execute 'aconnect -i' and you will see that the module is probed.

Kind Regards,

--
FarEast :)

---

### Post by redcell on 2006-03-20
is there anyway to execute these commands automaticly on startup?

setserial /dev/ttyS0 uart none
modprobe snd-serial-u16550

---

