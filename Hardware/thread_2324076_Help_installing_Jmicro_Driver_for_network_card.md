---
title: "Help installing Jmicro Driver for network card"
date: 2016-05-10
forum: Hardware
---

### Post by BarryDocks on 2016-05-10
I have a shuttle XS35.  I have updated the BIOS to the latest version from the shuttle website.  It has a JMicron JMC26x fast ethernet card that is not recognised on installation of 16.04 64bit
I have downloaded the latest driver from here [ftp://driver.jmicron.com.tw/Ethernet/Linux/]("ftp://driver.jmicron.com.tw/Ethernet/Linux/") 

When I do the make install command I get this error:
```
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-21-generic'
  CC [M]  /media/usbdrive/jmebp-1.0.8.5/jme.o
/media/usbdrive/jmebp-1.0.8.5/jme.c: In function ‘jme_alloc_and_feed_skb’:
/media/usbdrive/jmebp-1.0.8.5/jme.c:1121:4: error: too few arguments to function ‘__vlan_hwaccel_put_tag’
    __vlan_hwaccel_put_tag(skb, vid);
    ^
In file included from /media/usbdrive/jmebp-1.0.8.5/jme.c:45:0:
include/linux/if_vlan.h:409:20: note: declared here
 static inline void __vlan_hwaccel_put_tag(struct sk_buff *skb,
                    ^
/media/usbdrive/jmebp-1.0.8.5/jme.c: In function ‘jme_LC_task’:
/media/usbdrive/jmebp-1.0.8.5/jme.c:1565:2: error: implicit declaration of function ‘tasklet_hi_enable’ [-Werror=implicit-function-declaration]
  tasklet_hi_enable(&jme->rxclean_task);
  ^
/media/usbdrive/jmebp-1.0.8.5/jme.c: In function ‘jme_tx_vlan’:
/media/usbdrive/jmebp-1.0.8.5/jme.c:2464:6: error: implicit declaration of function ‘vlan_tx_tag_present’ [-Werror=implicit-function-declaration]
  if (vlan_tx_tag_present(skb)) {
      ^
In file included from include/linux/byteorder/little_endian.h:4:0,
                 from ./arch/x86/include/uapi/asm/byteorder.h:4,
                 from include/asm-generic/bitops/le.h:5,
                 from ./arch/x86/include/asm/bitops.h:504,
                 from include/linux/bitops.h:36,
                 from include/linux/kernel.h:10,
                 from include/linux/list.h:8,
                 from include/linux/module.h:9,
                 from /media/usbdrive/jmebp-1.0.8.5/jme.c:30:
/media/usbdrive/jmebp-1.0.8.5/jme.c:2466:23: error: implicit declaration of function ‘vlan_tx_tag_get’ [-Werror=implicit-function-declaration]
   *vlan = cpu_to_le16(vlan_tx_tag_get(skb));
                       ^
include/uapi/linux/byteorder/little_endian.h:34:51: note: in definition of macro ‘__cpu_to_le16’
 #define __cpu_to_le16(x) ((__force __le16)(__u16)(x))
                                                   ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:2466:11: note: in expansion of macro ‘cpu_to_le16’
   *vlan = cpu_to_le16(vlan_tx_tag_get(skb));
           ^
/media/usbdrive/jmebp-1.0.8.5/jme.c: At top level:
/media/usbdrive/jmebp-1.0.8.5/jme.c:3444:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jme_init_one’
 jme_init_one(struct pci_dev *pdev,
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:3732:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jme_remove_one’
 jme_remove_one(struct pci_dev *pdev)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:3901:20: error: ‘jme_init_one’ undeclared here (not in a function)
  .probe          = jme_init_one,
                    ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:3902:20: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
  .remove         = __devexit_p(jme_remove_one),
                    ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:3902:32: error: ‘jme_remove_one’ undeclared here (not in a function)
  .remove         = __devexit_p(jme_remove_one),
                                ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:300:1: warning: ‘jme_reload_eeprom’ defined but not used [-Wunused-function]
 jme_reload_eeprom(struct jme_adapter *jme)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:330:1: warning: ‘jme_load_macaddr’ defined but not used [-Wunused-function]
 jme_load_macaddr(struct net_device *netdev)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:1276:1: warning: ‘jme_pcc_tasklet’ defined but not used [-Wunused-function]
 jme_pcc_tasklet(unsigned long arg)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:1468:13: warning: ‘jme_LC_task’ defined but not used [-Wunused-function]
 static void jme_LC_task(struct work_struct *work)
             ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:1572:1: warning: ‘jme_link_change_tasklet’ defined but not used [-Wunused-function]
 jme_link_change_tasklet(unsigned long arg)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:1662:1: warning: ‘jme_poll’ defined but not used [-Wunused-function]
 jme_poll(JME_NAPI_HOLDER(holder), JME_NAPI_WEIGHT(budget))
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:1687:1: warning: ‘jme_rx_empty_tasklet’ defined but not used [-Wunused-function]
 jme_rx_empty_tasklet(unsigned long arg)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:1724:1: warning: ‘jme_tx_clean_tasklet’ defined but not used [-Wunused-function]
 jme_tx_clean_tasklet(unsigned long arg)
 ^
/media/usbdrive/jmebp-1.0.8.5/jme.c:3360:1: warning: ‘jme_pci_dma64’ defined but not used [-Wunused-function]
 jme_pci_dma64(struct pci_dev *pdev)
 ^
cc1: some warnings being treated as errors
scripts/Makefile.build:264: recipe for target '/media/usbdrive/jmebp-1.0.8.5/jme.o' failed
make[2]: *** [/media/usbdrive/jmebp-1.0.8.5/jme.o] Error 1
Makefile:1396: recipe for target '_module_/media/usbdrive/jmebp-1.0.8.5' failed
make[1]: *** [_module_/media/usbdrive/jmebp-1.0.8.5] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-21-generic'
Makefile:27: recipe for target 'modules' failed
make: *** [modules] Error 2

```

Please can someone help?

---

### Post by Yellow Pasque on 2016-05-10
The 'jme' module should be available on 16.04
```
sudo modinfo jme
sudo modprobe -v jme
```

You may want to look through dmesg to see if you can find any clues as to why it's not working.

---

