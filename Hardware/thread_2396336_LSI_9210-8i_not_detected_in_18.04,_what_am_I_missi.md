---
title: "LSI 9210-8i not detected in 18.04, what am I missing?"
date: 2018-07-13
forum: Hardware
---

### Post by averyfreeman on 2018-07-13
I'm coming from an ESXi background where LSI SAS2008 drivers were provided by default. I'm excited about moving to Ubuntu so I am really hoping this will be a viable system for me to migrate to. Anybody have any ideas of what I need to do? 

I seem to remember FreeNAS 9, DSM 3 and FreeBSD 10.1-RELEASE having them OTB, too.  So what's up with Ubuntu, how come it's so hard to get the most common SAS controller working on it?  I thought it was supposed to be *the* server distro these days -* "marketspeech marketspeech* cloud", and all that.

So anyway, moving (slowly) away from ESXi to LXC/LXD container platforms and need SAS2008 functionality - want to use LSI 9210-8i with my shiny new Ubuntu 18.04 on ZFS installation, but can't appear to find drivers for SAS2008 cards for this version of Ubuntu - latest one was 14.04, which are `mpt2sas-20.00.04.00-1_Ubuntu14.04.amd64.deb` - got it off the official LSI/Avago/Broadcom website.


I installed it and I appear to have some related drivers listed under `lsmod`, but can't get any helper programs to recognize card.  


For example:
```

    local@ubuntu:~$ lsmod | egrep "mpt|scsi"
        mptctl                 40960  0
        mptbase               102400  1 mptctl
        mpt3sas               241664  0
        raid_class             16384  1 mpt3sas
        scsi_transport_sas     40960  1 mpt3sas

```


I do *not* see the `mpt2sas` driver loaded, but it *is* under `/dev/`:

```

    local@ubuntu:~$ ls /dev | grep mpt  
        mpt2ctl
        mpt3ctl
        mptctl

```


However, 

```

    local@ubuntu:~$ insmod mpt2sas
         insmod: ERROR: could not load module mpt2sas: No such file or directory

```


I seem to have found some related modules with: 

```

    local@ubuntu:~$ find /lib/modules/$(uname -r) -type f -name '*.ko' | grep mpt


    /lib/modules/4.15.0-23-generic/kernel/drivers/scsi/mpt3sas/mpt3sas.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptctl.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptscsih.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptbase.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptspi.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptfc.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptlan.ko
    /lib/modules/4.15.0-23-generic/kernel/drivers/message/fusion/mptsas.ko


So I installed them with `modprobe -i`:


    local@ubuntu:~$ sudo modprobe -i mptsas     
    local@ubuntu:~$ sudo modprobe -i mptspi
    local@ubuntu:~$ sudo modprobe -i mptbase
    local@ubuntu:~$ sudo modprobe -i mptctl

```


And now I see:

```

    local@ubuntu:~$ lsmod | grep mpt
        mptspi                 24576  0
        scsi_transport_spi     32768  1 mptspi
        mptsas                 61440  0
        mptscsih               40960  2 mptsas,mptspi
        mptctl                 40960  0
        mptbase               102400  4 mptctl,mptscsih,mptsas,mptspi
        mpt3sas               241664  0
        raid_class             16384  1 mpt3sas
        scsi_transport_sas     40960  2 mpt3sas,mptsas

```


So that's a little better.  But still no new drives are being loaded under `/dev`, and management software is like 'uh-uh': 


```

    local@ubuntu:~$ megactl
    No LSI MegaRAID cards found. You may try megasasctl instead.


    local@ubuntu:~$ sudo megactl
    No LSI MegaRAID cards found. You may try megasasctl instead.


    local@ubuntu:~$ sudo megasasctl
    No LSI MegaRAID SAS cards found. You may try megactl instead.


    local@ubuntu:~$ sudo lsiutil
    
    LSI Logic MPT Configuration Utility, Version 1.56, March 19, 2008
    
    0 MPT Ports found
    
    Scanning processes...
    Scanning processor microcode...
    Scanning linux images...
    
    Running kernel seems to be up-to-date.
    
    The processor microcode seems to be up-to-date.
    
    No services need to be restarted.
    
    No containers need to be restarted.
    
    No user sessions are running outdated binaries.


    local@ubuntu:~$ sudo megaclisas-status
    No MegaRAID or PERC adapter detected on your system!

```




Do I need to compile a new initramfs and reboot after the `insmod/modprobe -i` of the kernel modules?  


Thanks!

---

### Post by neilanthonystuckey on 2018-10-10
This may help. I struggled with the same. 

[http://manpages.ubuntu.com/manpages/bionic/man4/mfi.4freebsd.html](http://manpages.ubuntu.com/manpages/bionic/man4/mfi.4freebsd.html)  I ended up having to  get a card on that list i could not get the 9210 to work properly.

---

