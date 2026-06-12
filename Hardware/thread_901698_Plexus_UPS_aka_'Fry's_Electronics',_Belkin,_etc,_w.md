---
title: "Plexus UPS aka 'Fry's Electronics', Belkin, etc, with NUT"
date: 2008-08-26
forum: Hardware
---

### Post by Cato2 on 2008-08-26
I thought I'd share this as eBuyer in the UK is selling some low cost UPSs that are quite painful to get working with Ubuntu 8.04.

This is a continuation of [http://ubuntuforums.org/showthread.php?t=698095](http://ubuntuforums.org/showthread.php?t=698095) which is unfortunately frozen (would be good if old threads could be continued as this isn't specific to an Ubuntu version really).

The first step is easy: apt-get install nut.

It took a long time to discover the magic incantation to get this USB UPS working - the model is Plexus 650VA USB, details are at [http://www.ebuyer.com/product/130478](http://www.ebuyer.com/product/130478).  lsusb -v starts like this:
```

Bus 001 Device 003: ID 0001:0000 Fry's Electronics 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0001 Fry's Electronics
  idProduct          0x0000 

```
Note the Fry's Electronics - the same basic UPS is resold by Belkin etc.

Anyway, the /etc/nut/ups.conf file requires something like this at least in my Ubuntu 8.04 setup.  Note that the vendorid and productid match the output of lsusb above. The subdriver was guessed from the /etc/udev/rules.d/52* file, where the Krauler driver has the same vendorid and productid - however that's not essential to get the driver to communicate with UPS.
```

[plexus]
	driver = megatec_usb
	vendorid = 0001
	productid = 0000
	subdriver = krauler
	desc = "Plexus V 650VA USB"
	# port = /dev/usb/hiddev0
	port = auto

```

I haven't done any real testing yet, but this at least enables NUT to communicate with the UPS.

Does anyone else have this or a similar UPS working with NUT?

---

### Post by Cato2 on 2008-09-06
I found the best option for this UPS is to download the NUT 2.2.2 source (latest version), make a one line patch (based on the code in megatec.c available at [http://hypedark.co.uk/index.php?page=displaypost&post_id=578](http://hypedark.co.uk/index.php?page=displaypost&post_id=578) but with some simplifications), and compile this.

I now have NUT communicating much better with the UPS and retrieving status values as it should - the battery charge value etc aren't right, but this is a big step forward.  I'm hopeful I can get this fully working then feed the patches upstream to the NUT developers.

Here's some sample output:
```

$ sudo /usr/local/ups/bin/upsc plexus
battery.charge: 85.7
battery.voltage: 12.80
battery.voltage.nominal: 11.5
driver.name: megatec_usb
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.parameter.productid: 0000
driver.parameter.subdriver: krauler
driver.parameter.vendorid: 0001
driver.version: 2.2.2
driver.version.internal: 1.5.14
input.frequency: 50.0
input.frequency.nominal: 50.0
input.voltage: 231.0
input.voltage.fault: 165.0
input.voltage.maximum: 240.0
input.voltage.minimum: 223.0
input.voltage.nominal: 230.0
output.voltage: 231.0
ups.beeper.status: disabled
ups.delay.shutdown: 0
ups.delay.start: 2
ups.load: 0.0
ups.mfr:
ups.model: UPS500V VER3.10C
ups.serial: unknown
ups.status: OL OFF
ups.type: standby

```

---

### Post by sisyphus1978 on 2010-02-12
I've just got this ups. Anybody got any further with it. I followed this thread and a [blog I found]("http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/"). Seems to work (turned off power continued to work, once the ups was low it shutdown ubuntu). upsc gives:

> battery.voltage: 12.30
battery.voltage.nominal: 11.5
driver.name: megatec_usb
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.parameter.productid: 0000
driver.parameter.subdriver: krauler
driver.parameter.vendorid: 0001
driver.version: 2.4.1
driver.version.internal: 1.6
input.frequency: 50.0
input.frequency.nominal: 50.0
input.voltage: 240.0
input.voltage.fault: 165.0
input.voltage.maximum: 257.0
input.voltage.minimum: 226.0
input.voltage.nominal: 230.0
output.voltage: 240.0
ups.beeper.status: disabled
ups.delay.shutdown: 0
ups.delay.start: 2
ups.load: 0.0
ups.mfr: 
ups.model: UPS650V VER3.10C
ups.serial: unknown
ups.status: OL OFF
ups.type: standbyDoes this look right?

---

