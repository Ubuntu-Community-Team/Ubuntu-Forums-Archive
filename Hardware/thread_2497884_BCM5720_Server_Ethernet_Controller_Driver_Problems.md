---
title: "BCM5720 Server Ethernet Controller Driver Problems"
date: 2024-05-21
forum: Hardware
---

### Post by digitaloxide42 on 2024-05-21
I have a custom built server here I'm trying to fix with a Supermicro H12DSi-N6 motherboard. I had to replace the  Nvme SSD drive because the old one went bad. There was an older version of Ubuntu desktop 22.04 installed on the previous hard drive.


I  put in a new hard drive and installed a clean verified install of the  latest Ubuntu Desktop 24.04 LTS

The installation went fine, I've  got it all working except for the Broadcom NetXtreme BCM5720 Gigabit  Ethernet PCIe adapter. It will not connect to the internet. I'm  not sure if this is a bug in the latest Ubuntu, & I've been  scouring the internet for the right drivers. Broadcom does have linux  drivers listed on their website for a similar chipset but when I try and  compile the installation .tar it throws a ton of errors, so I'm not  sure if this is even the correct driver:  Broadcom_NX1_Linux_Drivers-3.139k.tar.gz directly from broadcoms website.

I'm basically hoping that if anyone has any further ideas that I have not yet tried. When I saw that it had a broadcom adapter my heart sunk because I remember many a day 20 years ago fighting with drivers for broadcom adapters specifically. 



I've  installed the latest updates, upgrades, installed 3rd party proprietary  drivers, installed linux-modules-extra etc... Here are some terminal  outputs that might help give you more information: (I am using a usb  ethernet adapter right now (enx207bd2afcd8c) to connect to the internet & also have  one of the ethernet ports (eno1) on the motherboard plugged into the switch)







```

administrator@administrator-Super-Server:~/Downloads$ lspci |grep net

01:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5720 Gigabit Ethernet PCIe

01:00.1 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5720 Gigabit Ethernet PCIe


```

```

administrator@administrator-Super-Server:~/Downloads$ ifconfig -a

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500

        ether 3c:ec:ef:7f:07:9a  txqueuelen 1000  (Ethernet)

        RX packets 0  bytes 0 (0.0 B)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 0  bytes 0 (0.0 B)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

        device interrupt 91 



eno2: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500

        ether 3c:ec:ef:7f:07:9b  txqueuelen 1000  (Ethernet)

        RX packets 0  bytes 0 (0.0 B)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 0  bytes 0 (0.0 B)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

        device interrupt 102 



enx207bd2afcd8c: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500

        inet 192.168.1.188  netmask 255.255.255.0  broadcast 192.168.1.255

        ether 20:7b:d2:af:cd:8c  txqueuelen 1000  (Ethernet)

        RX packets 101857  bytes 98014276 (98.0 MB)

        RX errors 0  dropped 398  overruns 0  frame 0

        TX packets 62514  bytes 9279853 (9.2 MB)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



enxb03af2b6059f: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500

        inet 169.254.3.1  netmask 255.255.255.0  broadcast 169.254.3.255

        inet6 fe80::b23a:f2ff:feb6:59f  prefixlen 64  scopeid 0x20<link>

        ether b0:3a:f2:b6:05:9f  txqueuelen 1000  (Ethernet)

        RX packets 17  bytes 2896 (2.8 KB)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 343  bytes 63111 (63.1 KB)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536

        inet 127.0.0.1  netmask 255.0.0.0

        inet6 ::1  prefixlen 128  scopeid 0x10<host>

        loop  txqueuelen 1000  (Local Loopback)

        RX packets 35281  bytes 3062082 (3.0 MB)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 35281  bytes 3062082 (3.0 MB)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

```



administrator@administrator-Super-Server:~/Downloads$ sudo lshw -C network

[sudo] password for administrator:

  *-network:0              

       description: Ethernet interface

       product: NetXtreme BCM5720 Gigabit Ethernet PCIe

       vendor: Broadcom Inc. and subsidiaries

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eno1

       logical name: /dev/fb0

       logical name: /dev/fb1

       version: 00

       serial: 3c:ec:ef:7f:07:9a

       capacity: 1Gbit/s

       width: 64 bits

       clock: 33MHz

        capabilities: pm vpd msi msix pciexpress bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation fb

       configuration:  autonegotiation=on broadcast=yes depth=32 driver=tg3  driverversion=6.8.0-31-generic firmware=5720-v1.39 NCSI v1.5.12.0  latency=0 link=no mode=1024x768 multicast=yes port=twisted pair  visual=truecolor xres=1024 yres=768

       resources:  iomemory:3800-37ff iomemory:3800-37ff iomemory:3800-37ff irq:91  memory:380b0150000-380b015ffff memory:380b0140000-380b014ffff  memory:380b0130000-380b013ffff memory:fa540000-fa57ffff

  *-network:1

       description: Ethernet interface

       product: NetXtreme BCM5720 Gigabit Ethernet PCIe

       vendor: Broadcom Inc. and subsidiaries

       physical id: 0.1

       bus info: pci@0000:01:00.1

       logical name: eno2

       version: 00

       serial: 3c:ec:ef:7f:07:9b

       capacity: 1Gbit/s

       width: 64 bits

       clock: 33MHz

        capabilities: pm vpd msi msix pciexpress bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation

       configuration: autonegotiation=on  broadcast=yes driver=tg3 driverversion=6.8.0-31-generic  firmware=5720-v1.39 NCSI v1.5.12.0 latency=0 link=no multicast=yes  port=twisted pair

       resources: iomemory:3800-37ff  iomemory:3800-37ff iomemory:3800-37ff irq:102  memory:380b0120000-380b012ffff memory:380b0110000-380b011ffff  memory:380b0100000-380b010ffff memory:fa500000-fa53ffff

  *-network

       description: Ethernet interface

       physical id: 6

       bus info: usb@2:2.1

       logical name: enx207bd2afcd8c

       serial: 20:7b:d2:af:cd:8c

       size: 100Mbit/s

       capabilities: ethernet physical

        configuration: autonegotiation=off broadcast=yes driver=cdc_ncm  driverversion=6.8.0-31-generic duplex=half firmware=CDC NCM (NO ZLP)  ip=192.168.1.188 link=yes multicast=yes port=twisted pair  speed=100Mbit/s

```






And when I go try to make the broadcom driver package I downloaded it gives me the following output:





```



administrator@administrator-Super-Server:~/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k$ sudo make

make -C /lib/modules/6.8.0-31-generic/build M=/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k modules

make[1]: Entering directory '/usr/src/linux-headers-6.8.0-31-generic'

warning: the compiler differs from the one used to build the kernel

  The kernel was built by: x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0

  You are using:           gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0

  CC [M]  /home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.o

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:6704:10:  error: &#8216;const struct ptp_clock_info&#8217; has no member named &#8216;adjfreq&#8217;

6704 |         .adjfreq        = tg3_ptp_adjfreq,

      |          ^~~~~~~

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:6704:27:  error: initialization of &#8216;struct ptp_pin_desc *&#8217; from incompatible  pointer type &#8216;int (*)(struct ptp_clock_info *, s32)&#8217; {aka &#8216;int  (*)(struct ptp_clock_info *, int)&#8217;} [-Werror=incompatible-pointer-types]

6704 |         .adjfreq        = tg3_ptp_adjfreq,

      |                           ^~~~~~~~~~~~~~~

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:6704:27:  note: (near initialization for &#8216;tg3_ptp_caps.pin_config&#8217;)

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_tx&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7018:17:  error: implicit declaration of function &#8216;pci_unmap_single&#8217;; did you  mean &#8216;dma_unmap_single&#8217;? [-Werror=implicit-function-declaration]

7018 |                 pci_unmap_single(tp->pdev,

      |                 ^~~~~~~~~~~~~~~~

      |                 dma_unmap_single

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7021:34:  error: &#8216;PCI_DMA_TODEVICE&#8217; undeclared (first use in this function); did  you mean &#8216;DMA_TO_DEVICE&#8217;?

7021 |                                  PCI_DMA_TODEVICE);

      |                                  ^~~~~~~~~~~~~~~~

      |                                  DMA_TO_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7021:34:  note: each undeclared identifier is reported only once for each  function it appears in

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7038:25:  error: implicit declaration of function &#8216;pci_unmap_page&#8217;; did you mean  &#8216;dma_unmap_page&#8217;? [-Werror=implicit-function-declaration]

7038 |                         pci_unmap_page(tp->pdev,

      |                         ^~~~~~~~~~~~~~

      |                         dma_unmap_page

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_rx_data_free&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7111:34:  error: &#8216;PCI_DMA_FROMDEVICE&#8217; undeclared (first use in this function);  did you mean &#8216;DMA_FROM_DEVICE&#8217;?

7111 |                          map_sz, PCI_DMA_FROMDEVICE);

      |                                  ^~~~~~~~~~~~~~~~~~

      |                                  DMA_FROM_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_alloc_rx_data&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7191:19:  error: implicit declaration of function &#8216;pci_map_single&#8217;; did you mean  &#8216;dma_map_single&#8217;? [-Werror=implicit-function-declaration]

7191 |         mapping = pci_map_single(tp->pdev,

      |                   ^~~~~~~~~~~~~~

      |                   dma_map_single

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7194:34:  error: &#8216;PCI_DMA_FROMDEVICE&#8217; undeclared (first use in this function);  did you mean &#8216;DMA_FROM_DEVICE&#8217;?

7194 |                                  PCI_DMA_FROMDEVICE);

      |                                  ^~~~~~~~~~~~~~~~~~

      |                                  DMA_FROM_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_rx&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7396:42:  error: &#8216;PCI_DMA_FROMDEVICE&#8217; undeclared (first use in this function);  did you mean &#8216;DMA_FROM_DEVICE&#8217;?

7396 |                                          PCI_DMA_FROMDEVICE);

      |                                          ^~~~~~~~~~~~~~~~~~

      |                                          DMA_FROM_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7423:25:  error: implicit declaration of function &#8216;pci_dma_sync_single_for_cpu&#8217;;  did you mean &#8216;dma_sync_single_for_cpu&#8217;?  [-Werror=implicit-function-declaration]

7423 |                         pci_dma_sync_single_for_cpu(tp->pdev, dma_addr, len, PCI_DMA_FROMDEVICE);

      |                         ^~~~~~~~~~~~~~~~~~~~~~~~~~~

      |                         dma_sync_single_for_cpu

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:7427:25:  error: implicit declaration of function  &#8216;pci_dma_sync_single_for_device&#8217;; did you mean  &#8216;dma_sync_single_for_device&#8217;? [-Werror=implicit-function-declaration]

7427 |                         pci_dma_sync_single_for_device(tp->pdev, dma_addr, len, PCI_DMA_FROMDEVICE);

      |                         ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      |                         dma_sync_single_for_device

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_tx_skb_unmap&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:8503:26:  error: &#8216;PCI_DMA_TODEVICE&#8217; undeclared (first use in this function); did  you mean &#8216;DMA_TO_DEVICE&#8217;?

8503 |                          PCI_DMA_TODEVICE);

      |                          ^~~~~~~~~~~~~~~~

      |                          DMA_TO_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tigon3_dma_hwbug_workaround&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:8555:43:  error: &#8216;PCI_DMA_TODEVICE&#8217; undeclared (first use in this function); did  you mean &#8216;DMA_TO_DEVICE&#8217;?

8555 |                                           PCI_DMA_TODEVICE);

      |                                           ^~~~~~~~~~~~~~~~

      |                                           DMA_TO_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_tso_bug&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:8621:16:  error: implicit declaration of function &#8216;skb_gso_segment&#8217;; did you mean  &#8216;skb_gso_reset&#8217;? [-Werror=implicit-function-declaration]

8621 |         segs = skb_gso_segment(skb, tp->dev->features &

      |                ^~~~~~~~~~~~~~~

      |                skb_gso_reset

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:8621:14:  warning: assignment to &#8216;struct sk_buff *&#8217; from &#8216;int&#8217; makes pointer from  integer without a cast [-Wint-conversion]

8621 |         segs = skb_gso_segment(skb, tp->dev->features &

      |              ^

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_start_xmit&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:8829:60:  error: &#8216;PCI_DMA_TODEVICE&#8217; undeclared (first use in this function); did  you mean &#8216;DMA_TO_DEVICE&#8217;?

8829 |         mapping = pci_map_single(tp->pdev, skb->data, len, PCI_DMA_TODEVICE);

      |                                                            ^~~~~~~~~~~~~~~~

      |                                                            DMA_TO_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_get_drvinfo&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:13694:9:  error: implicit declaration of function &#8216;strlcpy&#8217;; did you mean  &#8216;strscpy&#8217;? [-Werror=implicit-function-declaration]

13694 |         strlcpy(info->driver, DRV_MODULE_NAME, sizeof(info->driver));

      |         ^~~~~~~

      |         strscpy

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_run_loopback&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:14997:59:  error: &#8216;PCI_DMA_TODEVICE&#8217; undeclared (first use in this function); did  you mean &#8216;DMA_TO_DEVICE&#8217;?

14997 |         map = pci_map_single(tp->pdev, skb->data, tx_len, PCI_DMA_TODEVICE);

      |                                                           ^~~~~~~~~~~~~~~~

      |                                                           DMA_TO_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:15107:45:  error: &#8216;PCI_DMA_FROMDEVICE&#8217; undeclared (first use in this function);  did you mean &#8216;DMA_FROM_DEVICE&#8217;?

15107 |                                             PCI_DMA_FROMDEVICE);

      |                                             ^~~~~~~~~~~~~~~~~~

      |                                             DMA_FROM_DEVICE

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: At top level:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:15923:35:  error: initialization of &#8216;int (*)(struct net_device *, struct  ethtool_rxfh_param *)&#8217; from incompatible pointer type &#8216;int (*)(struct  net_device *, u32 *, u8 *)&#8217; {aka &#8216;int (*)(struct net_device *, unsigned  int *, unsigned char *)&#8217;} [-Werror=incompatible-pointer-types]

15923 |         .get_rxfh               = tg3_get_rxfh,

      |                                   ^~~~~~~~~~~~

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:15923:35:  note: (near initialization for &#8216;tg3_ethtool_ops.get_rxfh&#8217;)

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:15924:35:  error: initialization of &#8216;int (*)(struct net_device *, struct  ethtool_rxfh_param *, struct netlink_ext_ack *)&#8217; from incompatible  pointer type &#8216;int (*)(struct net_device *, const u32 *, const u8 *)&#8217;  {aka &#8216;int (*)(struct net_device *, const unsigned int *, const unsigned  char *)&#8217;} [-Werror=incompatible-pointer-types]

15924 |         .set_rxfh               = tg3_set_rxfh,

      |                                   ^~~~~~~~~~~~

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:15924:35:  note: (near initialization for &#8216;tg3_ethtool_ops.set_rxfh&#8217;)

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c: In function &#8216;tg3_init_one&#8217;:

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:19851:23:  error: implicit declaration of function &#8216;pci_set_dma_mask&#8217;  [-Werror=implicit-function-declaration]

19851 |                 err = pci_set_dma_mask(pdev, dma_mask);

      |                       ^~~~~~~~~~~~~~~~

/home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.c:19854:31:  error: implicit declaration of function &#8216;pci_set_consistent_dma_mask&#8217;  [-Werror=implicit-function-declaration]

19854 |                         err = pci_set_consistent_dma_mask(pdev,

      |                               ^~~~~~~~~~~~~~~~~~~~~~~~~~~

cc1: some warnings being treated as errors

make[3]:  *** [scripts/Makefile.build:243:  /home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k/tg3.o]  Error 1

make[2]: ***  [/usr/src/linux-headers-6.8.0-31-generic/Makefile:1926:  /home/administrator/Downloads/Broadcom_NX1_Linux_Drivers-3.139k/tg3-3.139k]  Error 2

make[1]: *** [Makefile:240: __sub-make] Error 2

make[1]: Leaving directory '/usr/src/linux-headers-6.8.0-31-generic'

make: *** [Makefile:92: default] Error 2



```


I was hoping someone might be able to point me in the right direction, Maybe I'm just being stupid, but how do I solve the warning: the compiler differs from the one used to build the kernel

I know this  computer was working with the network drivers with a previous version of  ubuntu on it. From what I can tell it seems the errors I'm getting when I try to build the package, If it comes down to it seems like I might just have to roll back the previous release and see if  the driver I have works on that.

 Hopefully I'm just missing  something simple here and someone has a better idea. I appreciate any ideas & your time. Thank  you!

---

### Post by digitaloxide42 on 2024-05-22
Okay well, nevermind. I fixed it... Somhow?

I'd tell you all the steps but the only problem is I don't exactly remember what I did that made the final fix because I tried so many different things LOL. Anyway persistence pays off. 

Thanks Anyway folks!

---

### Post by MAFoElffen on 2024-05-23
LOL. Please use the thread tools link iun the upper right and mark your thread as solved.

The driver should be in Ubuntu, as tg3... In the Linux Firmware as tg3.bin... I was wondering if there was a problem with the vrsion of Linux Firmware or a problem building the modul wirh Kernel 6.8... But too late for that now.

---

