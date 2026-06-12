---
title: "hard disk driver infomation"
date: 2013-04-13
forum: Hardware
---

### Post by ruwan2 on 2013-04-13
Hi, I want the AHCI driver detailed information on Dell XPS 8500 desktop PC. I install Ubunto 9.0.4 (I need this version for its legacy GRUB). Do you know which application can give me the hard disk controller information?  Thanks,

---

### Post by ruwan2 on 2013-04-13
Another curious question about Ubunto 9.l0.4. I find that the display resolution is only 800X600 on this XPS 8500 computer. What is the reason it is so low? 9.0.4 does not know the display hardware? Can I upgrade the display? How can I do that ?Thanks

---

### Post by mörgæs on 2013-04-13
New hardware and old software is a bad combination. The 8500 was not even released at the time when 9.04 came out, so you can not expect the support to be first class.

Why do you need old GRUB?

---

### Post by ruwan2 on 2013-04-13
Thanks. The original requirement for me is to install Windows XP on XPS 8500 (I have some important applications need WinXP). I would like to have multiple boot (Windows XP, OPENSUSE and Ubuntu, maybe another small Linux for device driver test). A link at Ubuntu says multiple boot requires legacy GRUB (it said GRUB2 not appropriate for multiple boot). It did say that after GRUB and 9.0.4 install, it can be overwrite with newer Ubuntu OS. It seems that 9.0.4 is too old, it does not know the hardware. Thanks, I try to update to newer Ubuntu. Hopefully it gives me AHCI info, then I can install WinXP.

---

### Post by prodigy_ on 2013-04-13
> **ruwan2 said:**
> 9.0.4
Why would you install a terribly outdated version that [reached end-of-life ages ago](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)?

---

### Post by mörgæs on 2013-04-13
> **ruwan2 said:**
> A link at Ubuntu says multiple boot requires legacy GRUB (it said GRUB2 not appropriate for multiple boot).

May I see that? 

Grub 2 is great for multi boot. Just build a good partitioning scheme first and begin with installing Windows.

---

### Post by ruwan2 on 2013-04-13
I once installed OPENSUSE to Windows 7 PC. There was no problem with dual boot. Then I installed Ubuntu 12. There was a problem with Ubuntu at boot. Sometimes it will halt, especially when it began boot after time out. I do not know the reason. OPENSUSE and Windows 7 boot always normally. That PC is AMD CPU A8-3850, 16 GB ram, 2TB hard disk. Do you know any thread on that? Thanks, (BTW, when I post on this thread, the enter key has no effect. What I type are all in one line. Is this right? What settings make this happen)

---

### Post by ruwan2 on 2013-04-13
After I install Ubuntu 12.1, I still cannot find the hard disk controller firmware information. How can I find it (AHCI controller) in Ubuntu 12.1? Thanks again.

---

### Post by oldfred on 2013-04-13
I think it was this command I ran that include some info:

 udevadm info --export-db > file.txt
udevinfo -a -p $(udevinfo -q path -n /dev/sdd)

      
 HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html


 Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

   
IF UEFI system:
Internal efi details
ls /sys/firmware/efi/vars

From my udevadm.txt
> P: /devices/pci0000:00/0000:00:1f.2
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
E: DRIVER=ahci
E: ID_MODEL_FROM_DATABASE=82801JI (ICH10 Family) SATA AHCI Controller
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: MODALIAS=pci:v00008086d00003A22sv00001458sd0000B005bc01sc06i01
E: PCI_CLASS=10601
E: PCI_ID=8086:3A22
E: PCI_SLOT_NAME=0000:00:1f.2
E: PCI_SUBSYS_ID=1458:B005
E: SUBSYSTEM=pci
E: UDEV_LOG=3
E: USEC_INITIALIZED=8848190



---

### Post by mörgæs on 2013-04-13
I see that you are active in a number of threads. 

Before abandoning this one (and when you do it would be good if you change it to 'solved') please remember to post the link you mentioned in #4.

---

