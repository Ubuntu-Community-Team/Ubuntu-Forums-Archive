---
title: "Problem loading the dvb_bt8xx  module"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by igb on 2005-10-10
I am running a custom 2.6.13.2 kernel so I can load the dvb drivers for my Avermedia DVB USB 2.0 TV card. This card is wrking fine. However when I try to load the modules for the DVB-T 771 PCI card, I get the following error:

```
root@mythtv:/lib/modules/2.6.13.2-custom/kernel/drivers/media/dvb/bt8xx # modprobe dvb-bt8xx
FATAL: Error inserting dvb_bt8xx (/lib/modules/2.6.13.2-custom/kernel/drivers/media/dvb/bt8xx/dvb-bt8xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

The output from dmesg is:

```
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_dmx_swfilter_204
[17182380.780000] dvb_bt8xx: disagrees about version of symbol dvb_dmx_release
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_dmx_release
[17182380.780000] dvb_bt8xx: disagrees about version of symbol dvb_net_init
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_net_init
[17182380.780000] dvb_bt8xx: disagrees about version of symbol dvb_dmx_swfilter
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_dmx_swfilter
[17182380.780000] dvb_bt8xx: disagrees about version of symbol dvb_dmxdev_release
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_dmxdev_release
[17182380.780000] dvb_bt8xx: disagrees about version of symbol dvb_net_release
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_net_release
[17182380.780000] dvb_bt8xx: disagrees about version of symbol dvb_dmx_init
[17182380.780000] dvb_bt8xx: Unknown symbol dvb_dmx_init

```

Any ideas on how I might go about fixing this problem?

Ian.

---

