---
title: "Sound trouble."
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by slavik on 2006-02-04
I installed Breezy on a Compaq Presario V2000Z and when booting, it would stop at "Starting Hotplug subsystem" ... someone suggested trying acpi=off, noapic nolapic options. That did not help.

Booting into recovery mode yields a message (being repeated): [#######.######] azx_get_responce timout

Another person (in IRC) suggested that it is a bug with the sound card which was fixed after Breezy was released.

I tried installing Dapper Flight 3 and it gets stuck at "Loading modules" (Setting up ALSA card 0 gives a failed status).

Booting into recovery mode yields the same error message.

I have a Knoppix LiveDVD (4.0.2) and it boots up fine with sound support.

EDIT: I've been told that the error comes from /usr/src/linux/sound/pci/hda/hda_intel.c

source of the file (someone from #linux gave it to me):
```

static unsigned int azx_get_response(struct hda_codec *codec)
{
	azx_t *chip = codec->bus->private_data;
	int timeout = 50;
	while (chip->rirb.cmds) {
		if (! --timeout) {
			snd_printk(KERN_ERR "azx_get_response timeout\n");
			chip->rirb.rp = azx_readb(chip, RIRBWP);
			chip->rirb.cmds = 0;
			return -1;
		}
		msleep(1);
	}
	return chip->rirb.res; /* the last value */
}

```

crimsun suggested that I boot with "atiixp:enable=0" as a kernel boot option and then get the latest drivers.

atiixp:enable=0 has no effect. (same errors occur).

---

### Post by slavik on 2006-02-05
bump for many updates.

---

### Post by slavik on 2006-02-09
here is how I solved the problem:

[https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2000Z](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2000Z)

---

