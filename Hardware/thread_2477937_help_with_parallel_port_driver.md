---
title: "help with parallel port driver"
date: 2022-08-11
forum: Hardware
---

### Post by coolmike8902 on 2022-08-11
Hi,

I'm trying to get a pci_e parallel port card installed in 22.04. I'm being stymied with every attempt. The card in question is here: [https://www.startech.com/en-us/cards-adapters/pex1p2](https://www.startech.com/en-us/cards-adapters/pex1p2)

There is apparently a bug in the makefile that is known. I believe this person patched it: [https://github.com/p0wdrdotcom](https://github.com/p0wdrdotcom)

That's still not working for me. 

On running make, I get: 

Kernel configuration is invalid. include/generated/autoconf.h or include/config/auto.conf are missing. Run 'make oldconfig && make prepare' on kernel src to fix it.

I know some of you will understand what this means, but I don't understand what to do next. Please help.

Thanks.

---

### Post by bcschmerker on 2022-08-11
**After reading the Tech Specs your card** (viz., StarTech PEX1P2)**, I determined the adapter IC to be one Asix AX99100.**  The AUR source (GIT format) for the driver is at:
[https://aur.archlinux.org/asix-ax99100.git](https://aur.archlinux.org/asix-ax99100.git)
Dependencies are as follows:

gcc
dkms
linux-headers
diffutils
findutils
gzip
patch
sed

Have ye experience building modules from source?

---

### Post by mIk3_08 on 2022-08-13
> **coolmike8902 said:**
> Hi,

I'm trying to get a pci_e parallel port card installed in 22.04. I'm being stymied with every attempt. The card in question is here: [https://www.startech.com/en-us/cards-adapters/pex1p2](https://www.startech.com/en-us/cards-adapters/pex1p2)

There is apparently a bug in the makefile that is known. I believe this person patched it: [https://github.com/p0wdrdotcom](https://github.com/p0wdrdotcom)

That's still not working for me. 
On running make, I get: 
Kernel configuration is invalid. include/generated/autoconf.h or include/config/auto.conf are missing. Run 'make oldconfig && make prepare' on kernel src to fix it.
I know some of you will understand what this means, but I don't understand what to do next. Please help.
Thanks.
Just run the following command below in your terminal to download what you need as what bcschmerker told you. To open terminal in your Linux Ubuntu Desktop just press ctrl and alt + T or just open it from your installed applications dock in your system Regards and cheers
```
git clone https://aur.archlinux.org/asix-ax99100.git
```

---

### Post by coolmike8902 on 2022-08-15
OK. So I downloaded and ran the patch. Then I ran make again on the original driver. I got this:

rm -f *.mod.c *.o *.ko .*.cmd *.symvers
make -C /lib/modules/5.15.0-25-generic/build/   M=/home/genevieve/drivers/lpt2/asix_ax99100_linux-master modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-25-generic'
  CC [M]  /home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_spi.o
  CC [M]  /home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.o
/home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.c: In function &#8216;serial99100_dma_rx_tasklet&#8217;:
/home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.c:2502:17: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
 2502 |                 if (up->k_lsr & UART_LSR_OE)
      |                 ^~
/home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.c:2505:25: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;if&#8217;
 2505 |                         up->k_lsr &= up->port.read_status_mask;
      |                         ^~
/home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.c: At top level:
/home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.c:3124:25: error: expected declaration specifiers or &#8216;...&#8217; before string constant
 3124 | MODULE_SUPPORTED_DEVICE("Asix serial 99100");
      |                         ^~~~~~~~~~~~~~~~~~~
make[2]: *** [scripts/Makefile.build:285: /home/genevieve/drivers/lpt2/asix_ax99100_linux-master/ax99100_sp.o] Error 1
make[1]: *** [Makefile:1875: /home/genevieve/drivers/lpt2/asix_ax99100_linux-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-25-generic'
make: *** [Makefile:41: default] Error 2


I'm clearly doing something wrong. Any help would be appreciated.
Thanks

---

