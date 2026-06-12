---
title: "Zyxel NWD310N driver compile problems"
date: 2009-07-07
forum: Hardware
---

### Post by arpad9 on 2009-07-07
I need a little help with alloc_etherdev( int sizeof_priv )

I've been gradually working through the errors in compiling the driver for my ZyXel wireless 11.n PCI card NWD310N.

Drivers here:
[ftp://ftp.zyxel.com/NWD310N/driver/NWD310N_1.00.zip](ftp://ftp.zyxel.com/NWD310N/driver/NWD310N_1.00.zip)

I think I'm really close but I have a problem 

```

./os/linux/rt_main_dev.c: In function ‘rt2860_probe’:
./os/linux/rt_main_dev.c:271: error: implicit declaration of function ‘SET_MODULE_OWNER’
./os/linux/rt_main_dev.c:293: warning: format ‘%lX’ expects type ‘long unsigned int’, but argument 4 has type ‘resource_size_t’
./os/linux/rt_main_dev.c:353: warning: passing argument 1 of ‘dev_get_by_name’ from incompatible pointer type
./os/linux/rt_main_dev.c:353: error: too few arguments to function ‘dev_get_by_name’
./os/linux/rt_main_dev.c:380: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘resource_size_t’
make[2]: *** [./os/linux/rt_main_dev.o] Error 1
make[1]: *** [_module_./os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [LINUX] Error 2

```


Seems to me that all I need to do is to better understand the code that initializes the net_dev variable and hard code some reasonable value but, not sure what that might be.


```

    235 //
    236 // PCI device probe & initialization function
    237 //
    238 static INT __devinit   rt2860_probe(
    239     IN  struct pci_dev              *pci_dev,
    240     IN  const struct pci_device_id  *ent)
    241 {
    242     struct  net_device      *net_dev;
    243     PRTMP_ADAPTER           pAd;
    244     CHAR                    *print_name;
    245     ULONG                   csr_addr;
    246     INT                     status;
    247         PVOID                                   handle;
    248 
    249 //#define DRIVER_VERSION "0.1"
    250 
    251     DBGPRINT(RT_DEBUG_TRACE, ("Driver version-%s\n", DRIVER_VERSION));
    252 
    253 #if LINUX_VERSION_CODE >= KERNEL_VERSION(2,5,0)
    254     //print_name = pci_dev ? pci_name(pci_dev) : "rt2860";
    255     print_name = "rt2860";
    256 #else
    257     print_name = pci_dev ? pci_dev->slot_name : "rt2860";
    258 #endif
    259 
    260 #if LINUX_VERSION_CODE <= 0x20402       // Red Hat 7.1
    261     net_dev = alloc_netdev(sizeof(PRTMP_ADAPTER), "eth%d", ether_setup);
    262 #else
    263     net_dev = alloc_etherdev(sizeof(PRTMP_ADAPTER));
    264 #endif
    265     if (net_dev == NULL)
    266     {
    267         DBGPRINT(RT_DEBUG_TRACE, ("init_ethernet failed\n"));
    268         goto err_out;
    269     }
    270 
    271     SET_MODULE_OWNER(net_dev);

```

Any help would be appreciated.  Thank you.

---

### Post by tibnor on 2010-05-24
I have also had problem with compiling the NWD310N driver, my solution was to follow this guide:
[http://ubuntuforums.org/showthread.php?p=9268348]("http://ubuntuforums.org/showthread.php?p=9268348")

---

