---
title: "Ubuntu doesn't recognize wired network adapter"
date: 2008-07-28
forum: Hardware
---

### Post by FuzzieLogic on 2008-07-28
Hi all,

So I have this old, but functional Ethernet card - AOpen AON-101. On Windows, I had to manually install the driver from a floppy disk, so I didn't have much hope of Ubuntu automatically recognizing it. And indeed, neither Ubuntu 6.10 or 8.04 would recognize it.

On the floppy disk with the drivers, there's a text file labelled "Linux", and it says: 

```

The procedure to activate AOpen AON-101 10M ISA PnP Ethernet Adapter on linux :
Hint:AOpen AON101 is ne2000 compatable.

  step 1: Make sure that kernel source code is included
          (check /usr/src/linux)

  step 2: Compile driver:

          cd to /usr/src/linux, them type 'make menuconfig'

          Select the following options:
            .Loadable module support->Enable loadable module support
            .Networking options->TCP/IP networking
            .Network device support->Ethernet(10 or 100Mbit)
            .Network device support->Ne2000/Ne1000 support (mark them as 'M')

  step 3: After options are selected, exit and run

                make dep;
                make modules;

          If no serious error happens, the driver 'ne.o' will be in
             /usr/src/linux/modules.

  step 4: As 'root', load the module using

             cd /usr/src/linux/modules
             insmod 8390.o
             insmod ne.o io=0x300 irq=0x05

          PS:
               The values "io=0x300" and "irq=0x05" are the hardware 
             configurations of your AOpen AON101. You can use "setup.exe" 
             (including in AOpen AON101 Driver Disk) in DOS to check the values
             assigned to the adapter. Use these values as options "io=" and
             "irq=" of ne.o 


  step 5: Bind your card to an IP address

          /sbin/ifconfig eth0 ${IPADDR} broadcast ${BROADCAST} netmask ${NETMASK}

  step 6: Add your card to IP routing table, then add gateway also your card:

          /sbin/route add -net ${NETWORK} netmask ${NETMASK} eth0
          (should be able to ping local network now)

          gateway:
          /sbin/route add default gw ${GATEWAY} netmask 0.0.0.0 metric 1

  step 7: start inet deamon.
          /usr/sbin/inetd
          (you are on the network now)


  step 8: If driver ne.o works as expected you should add the insmod commands
          at the beginning of /etc/rc.d/init.d/network

              "insmod /usr/src/linux/modules/8390.o"
              "insmod /usr/src/linux/modules/ne.o io=0x300 irq=0x05"

          Then your driver will work every time you boot.
          (you can run 'dmesg' to see the module loading messages)

  step 9: You can run '/usr/sbin/netconfig' which will do step 5, 6, 7 for you. 
          And save the configurations in system files which are used at boot time.


```

I don't actually have a /linux folder in /usr/src - I have /linux-headers-2.6.24-19 and /linux-headers-2.6.24-19-generic, which both just yielded a long list of errors when I ran "make menuconfig".

Any ideas as to what I can do would be greatly appreciated. Thanks in advance. :)

---

