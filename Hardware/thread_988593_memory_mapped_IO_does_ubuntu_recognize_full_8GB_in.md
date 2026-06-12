---
title: "memory mapped I/O? does ubuntu recognize full 8GB installed for use?"
date: 2008-11-20
forum: Hardware
---

### Post by dvfedele on 2008-11-20
I'm still prettty fresh to ubuntu and am trying to figure out if it will use the max ram installed in a laptop I'm about to purchase. Its a core2 duo, intel P965 chipset supporting 8GB ram.  I understand the windows limitations concerning lost ram space due to memory mapped I/O limitations. Also, I understand windows information concerning ram:

"Note When the physical RAM that is installed on a computer equals the address space that is supported by the chipset, the total system memory that is available to the operating system is always less than the physical RAM that is installed. For example, consider a computer that has an Intel 975X chipset that supports 8 GB of address space. If you install 8 GB of RAM, the system memory that is available to the operating system will be reduced by the PCI configuration requirements. In this scenario, PCI configuration requirements reduce the memory that is available to the operating system by an amount that is between approximately 200 MB and approximately 1 GB. The reduction depends on the configuration."
[http://support.microsoft.com/kb/929605](http://support.microsoft.com/kb/929605)

BUT...if my bios recognizes all 8GB of ram, will ubuntu still have the memory hit by reserving those address for I/O and peripherls/gpu? No one seems to want to answer this because its mostly a windows world when purchasing. All anyone says is this:

"(The 64bit edition of Windows Vista is required for memory size over 2.8GB; however due to the hardware chipset limitations only 6.8GB maximum of system memory would be available for use with total of 8GB memory installed.)"

Just doesn't make sense that its a chipset limitation, because the chipset supports 8GB ram?!
[http://www.intel.com/products/desktop/chipsets/p965/p965-overview.htm](http://www.intel.com/products/desktop/chipsets/p965/p965-overview.htm)

please help before my head explodes! :)

---

### Post by linux_tech on 2008-11-20
Linux has much higher memory limitations than Windows.

Different distributions support different amts of RAM.  For example some Red Hat Enterprise versions support unlimited- [http://www.redhat.com/rhel/compare/](http://www.redhat.com/rhel/compare/)

8GB is more than sufficient for ubuntu. The amount that is actually used will depend on the applications that are running.  Databases and VMware both use quite a bit of RAM. 

To monitor the memory you may want to check out [http://manpages.ubuntu.com/manpages/hardy/man1/asmem.html](http://manpages.ubuntu.com/manpages/hardy/man1/asmem.html)

64-bit normally supports more memory than 32-bit. 

If your focus is to utilize more memory and have higher maximum limits, then I would use 64-bit server OS. Server versions usually support more memory than the workstation versions. 

If you are running a 32-bit system and you want to maximize RAM limits, then you will need to run server, and compile a kernal with PAE.  The kernel of the server version of Ubuntu has support for PAE (Physical Address Extension), to make a 32-bit system be able to use up to 64 GB RAM  more info here-http://en.wikipedia.or/wiki/Physical_Address_Extension

---

