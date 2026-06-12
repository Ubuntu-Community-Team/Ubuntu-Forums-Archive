---
title: "Raid HPT3xx Ubuntu install help"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by martymart on 2006-07-17
I want to install Ubuntu on a HPT3xx raid card but it only sees my drives as seperate drives. There is an open source driver available and some distribution specific ones are also available.

Here is the official website: [http://www.highpoint-tech.com/USA/bios_rr133.htm](http://www.highpoint-tech.com/USA/bios_rr133.htm)

The open source driver says:
1. Overview
---------------------
  This package contains Linux driver source code for HighPoint
  HPT370/370A/372/372A/372N/302/302N ATA RAID controllers and RocketRAID 1520
  SATA RAID controllers.

  The source code is for kernel updating purposes - you can use this
  source code to build a driver, if you cannot find one in HighPoint
  Linux driver release package. 

  NO WARRANTY

  THE DRIVER SOURCE CODE HIGHPOINT PROVIDED IS FREE OF CHARGE, AND THERE IS
  NO WARRANTY FOR THE PROGRAM. THERE ARE NO RESTRICTIONS ON THE USE OF THIS
  FREE SOURCE CODE. HIGHPOINT DOES NOT PROVIDE ANY TECHNICAL SUPPORT IF THE
  CODE HAS BEEN CHANGED FROM ORIGINAL SOURCE CODE.

  LIMITATION OF LIABILITY

  IN NO EVENT WILL HIGHPOINT BE LIABLE FOR DIRECT, INDIRECT, SPECIAL,
  INCIDENTAL, OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OF OR
  INABILITY TO USE THIS PRODUCT OR DOCUMENTATION, EVEN IF ADVISED OF THE
  POSSIBILITY OF SUCH DAMAGES. IN PARTICULAR, HIGHPOINT SHALL NOT HAVE
  LIABILITY FOR ANY HARDWARE, SOFTWARE, OR DATA STORED USED WITH THE
  PRODUCT, INCLUDING THE COSTS OF REPAIRING, REPLACING, OR RECOVERING
  SUCH HARDWARE, OR DATA.

  
2. Build the driver
---------------------
  1) Preparation
  
     Users need to install the kernel source package and setup kernel
     headers with proper configuration before building the driver.
   
     You shall use same configuration for the kernel and the driver.
     Otherwise the driver may be unable to load or work abnormally.

     If you are using stock kernel, obtain the configuration in your Linux
     distribution (e.g. the kernel configuration file for Red Hat stock kernel
     can be found under "configs" directory in kernel source tree). Copy the
     configuration file to <your-kernel-source-dir>/.config and setup the
     kernel headers using "make oldconfig" and "make dep" commands before you
     build the driver.
     
     Please refer to the documents in your Linux distribution for kernel
     configuration.

     If the kernel contains built-in IDE support for your HPT3xx controller,
     you must rebuild and install a kernel without HPT37x controller support
     before using this driver. Please refer to kernel documents for how to 
     configure/update the kernel.
     
  2) Extract the driver files to somewhere.

  3) Build the driver for RocketRAID 1520 (example for SuSE 9.1 type kernel):

        # make KERNELDIR=/usr/src/linux-2.6.4-52-default
        
     Available make options:
     
       KERNELDIR=...
           Specify kernel source directory, if not use this option, the default
           kernel source directory is /usr/src/linux.
           
       RR1520=
           RR1520=1 for RocketRAID 1520 SATA controller. (Default)
           RR1520=0 for HPT3xx based PATA RAID controllers.
     
       NON_RAID=
           NON_RAID=0 to build the driver with RAID support.(Default)
           NON_RAID=1 to build the driver without RAID support.

     
3. Using the driver
---------------------
    
  1) Load module "scsi_mod" and "sd_mod" if they are not built into kernel:

        # modprobe sd_mod

  2) Load the driver.
        
        # insmod ./hpt37x2.o

     For kernel 2.6, the driver module is "hpt37x2.ko". Also you need to use 
     the 2.5/2.6 module-init-tools (you can get them from
     [http://www.kernel.org/pub/linux/kernel/people/rusty/modules/)](http://www.kernel.org/pub/linux/kernel/people/rusty/modules/)).
     modutils from 2.4 won't work with 2.5/2.6. 


The red hat drivers seem much more simple as you just need to copy some files to a floppy and change some boot options and that is prity much it. Can I use a method like this with Ubuntu?

I really need help with getting this controller to work as I am a bit of a newbie. If some one can give me some clear instructions as what to do i would most appreciate it.

Thanks Martin

---

### Post by dehuszar on 2007-03-14
I'm having the exact same problem with a RocketRaid 1742.  HighPoint has released a how-to, but it doesn't seem to work with the Ubuntu installer.  Anyone's success in installing onto a RAID array whose drivers were loaded off of floppy... your assistance would be GREATLY appreciated.

---

### Post by urkah on 2007-07-11
Hi,

I found this excellent guide for how to install driver for highpoint IDE raid controllers.

Even though it's not for setting up the actual raid as the systemdisk.

Hope it helps some of you, who have problems with highpoint raid controllers (I know I did..)

[http://stefan.freyr.org/?page_id=6]("http://stefan.freyr.org/?page_id=6")

---

### Post by m0ridin on 2008-03-29
Sorry to bump an old thread, but I'm basically in the same situation as Martymart.

I've got two 80-gig hard drives in a raid-0 array with the Hightpoint 372 embedded controller.  I went ahead and installed Windows Server 2003 (with help from a floppy containing the drivers), and left 20 gigs untouched for a future ubuntu install for a dual-boot option.

I downloaded the latest ubuntu server (7.10) and it doesn't seem to "see" the array, just the individual disks.

I'm a linux novice, but from what I've read, it's sounding like the way to get this to work is to blow out my 2k3 install, install 7.10 as-is (and leave space for 2k3 later), then recompile the kernel with the appropriate drivers, and THEN install the other OS?  Or am I completely off the mark?

Any help much appreciated :)

---

