---
title: "Sound card not dedected"
date: 2015-07-09
forum: Hardware
---

### Post by aygusu on 2015-07-09
Hello. I'm new on here and actually don't know what to do too much . Firstly, sorry about my english.  I have been looking for what to do about 4 days. I've looked at a lot of sites and couldn't find an answer because they didn't work at all. By the way I am using linux but I saw that ubuntu's things are also working on mint 13 . So i writed here. 


My problem is ; my sound card isn't detected , there's no sound, only dummy output but still no sound , i cannot find what is its model name . I'm ussing Linux mint 13 mate 32 bit.  Laptop model ; Exper Karizma NR22A - intel

---

### Post by dino99 on 2015-07-09
To detect the soundcard [http://askubuntu.com/questions/140642/how-can-i-know-whether-a-sound-card-is-present-on-my-system-or-not](http://askubuntu.com/questions/140642/how-can-i-know-whether-a-sound-card-is-present-on-my-system-or-not) and then you can google around "ubuntu/linux soundcardname" to find threads about it.

But first be sure that your bios/uefi is set to use 'hda'; and then check that jack(s) are plugged as expected (same color). Then the program 'pavucontrol" can help to fine tune the sound settings if necessary (usual its automatic, so nothing to do)

---

### Post by aygusu on 2015-07-09
Whatever i do it still says -no soundcard found-

---

### Post by Vladlenin5000 on 2015-07-09
> **aygusu said:**
> Whatever i do it still says -no soundcard found-

What have you done so far exactly?

---

### Post by aygusu on 2015-07-09
I don't remember . But i looked up a lot of threads about soundcard and entered them in terminal . It's been 4 days but if you want i will post my terminal history.; to be fast : ```
260  sudo su
  261  sudo su
  262  inxi -Gx
  263      inxi -A
  264  alsa
  265  reload
  266  alsa reloas
  267  alsa reload
  268  lspci | grep -i audio
  269  alsamixer
  270  alsamixer
  271  alsa mixer
  272  aplay -l | grep card
  273  rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
  274  sudo rm /etc/asound.conf
  275  gpasswd -a user audio
  276  sudo aptitude -y purge alsa-base && sudo aptitude -y install ubuntu-desktop
  277  lsub
  278  lsci
  279  lspci
  280  cat /proc/asound/card*/codec* 
  281  sndconfig
  282  sudo su
  283  sudo apt-get install build-essential gcc make
  284  sudo apt-get install build-essential gcc make
  285  /usr/bin/alsamixer
  286  sudo apt-get install alsa-base alsa-utils alsa-tools-gui pulseaudio
  287  sudo pluma /etc/modprobe.d/alsa-base.conf
  288  sudo apt-get install pavucontrol
  289  inxi -A
  290  uname -rm
  291  cat /proc/asound/card0/codec#* | grep Codec
  292  cat /proc/asound/modules
  293  lsmod | grep snd
  294  aplay -l 
  295  alsamixer
  296  sudo apt-get install alsa-base alsa-utils alsa-tools-gui pulseaudio
  297  alsamixer
  298  /usr/bin/alsamixer
  299  killall pulseaudio
  300  alsamixer
  301  killall pulseado
  302  sudo rm -rf /var/lib/apt/lists/lock
  303  sudo rm -rf /var/lib/dpkg/lock
  304  sudo rm -rf /var/cache/apt/archives/lock
  305  sudo apt-get install -f
  306  sudo dpkg --configure -a
  307  java -version
  308  sudo add-apt-repository ppa:webupd8team/java
  309  sudo apt-get update
  310  echo "check_certificate = off" | sudo tee -a /etc/wgetrc
  311  sudo apt-get install oracle-java8-installer
  312  sudo update-java-alternatives -s java-8-oracle
  313  sudo update-alternatives --config java
  314  sudo rm -rf /etc/apt/sources.list.d/xorg-edgers-ubuntu-ppa-utopic.list.save
  315  sudo rm -rf /var/lib/apt/lists/lock
  316  sudo rm -rf /var/lib/dpkg/lock
  317  sudo rm -rf /var/cache/apt/archives/lock
  318  sudo apt-get install -f
  319  sudo dpkg --configure -a
  320  sudo apt-get update
  321  inxi -Fxz
  322  mkdir linux-3.16.7 && cd linux-3.16.7
  323  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-headers-3.16.7-031607-generic_3.16.7-031607.201506301235_i386.deb
  324  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-headers-3.16.7-031607-generic_3.16.7-031607.201506301235_i386.deb
  325  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-headers-3.16.7-031607_3.16.7-031607.201506301235_all.deb
  326  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-image-3.16.7-031607-generic_3.16.7-031607.201506301235_i386.deb
  327  sudo dpkg -i *.deb
  328  sudo dpkg -i *.deb
  329  sudo apt-get purge virtualbox-guest*
  330  cd linux-3.16.7
  331  sudo dpkg -i *.deb
  332  uname -r
  333  inxi -r
  334  sudo add-apt-repository ppa:webupd8team/java
  335  sudo update-alternatives --config java
  336  cd linux-3.16.7
  337  uname -r
  338  sudo rm -rf /etc/apt/sources.list.d/ubuntu-wine-ppa-maya.list
  339  sudo update-grub
  340  past
  341  past commands
  342  command history
  343  sudo update-alternatives --config java
  344  cd linux-3.16.7
  345  sudo update-grub
  346  uname -r 
  347  cd linux-3.16.7
  348  sudo apt-get update
  349  dpkg -l | grep oem-audio-hda-daily-dkms
  350  deb http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu precise main
  351  deb-src http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu precise
  352  cat /proc/asound/modules
  353  sudo gedit /etc/modprobe.d/alsa-base.conf
  354  hisrtory
  355  open past
  356  open history
  357  sudo past
  358  past entries
  359  history
  360  cd linux-3.16.7
  361  dmesg | egrep 'snd|audio|sound'
  362  sudo apt-get install --reinstall linux-sound-base alsa-base alsa-utils
  363  sudo modprobe snd-hda-intel
  364  cat /etc/modprobe.d/alsa-base.conf
  365  found sound card
  366  cat /etc/modprobe.d/alsa-base.conf
  367  /etc/modprobe.d/alsa-base.conf
  368  history
  369  cat /etc/modprobe.d/alsa-base.conf
  370  sudo modprobe snd-hda-intel
  371  history
  372  dpkg -l | grep linux-headers
  373  sudo update-grub
  374  uname -a
  375  linux
  376  sudo apt-get install user-mode-linux
  377  sudo apt-get install user-mode-linux
  378  mkdir linux-3.16.7 && cd linux-3.16.7
  379  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-headers-3.16.7-031607-generic_3.16.7-031607.201506301235_i386.deb
  380  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-headers-3.16.7-031607_3.16.7-031607.201506301235_all.deb
  381  wget -c --no-check-certificate kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt14-utopic/linux-image-3.16.7-031607-generic_3.16.7-031607.201506301235_i386.deb
  382  sudo dpkg -i *.deb
  383  sound
  384  sudo update-grub
  385  /boot/vmlinuz-3.16.7-031607-generic
  386  sudo su
  387  cat /proc/asound/cards
  388   sudo gedit /etc/modprobe.d/alsa-base.conf
  389  sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
  390  gstreamer-properties
  391  aplay -l
  392  alsaconf
  393  dmesg | grep [Vv][Ii][Aa]82
  394  via82cxxx_audio
  395  tedi_99
  396  aplay -l
  397  alsamixer
  398  enable mixer
  399  cat /proc/asound/card0/codec* | grep Codec`
  400  pulseaudio -vvv
  401  sudo touch /etc/modprobe.d/alsa-base.conf.bak
  402  sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.bak  # backup alsa-base.conf
  403  sudo nano /etc/modprobe.d/alsa-base.conf 
  404  usermod -a -G audio myuser
  405  usermod -a -G audio aygusu
  406  sudo
  407  sudo su
  408  ps -ef | grep pulseaudio
  409  sudo vi /etc/default/speech-dispatcher
  410  pacmd list-sinks
  411  sudo alsa force-reload
  412  uname -r
  413  sudo update-grub
  414  sudo update-initramfs -u
  415   sudo apt-get remove --purge alsa-base
  416  cd ~/Desktop
  417  sudo chmod 777 alsa_1.sh
  418  sudo chmod 777 alsa_2.sh
  419  sudo sh ./alsa_1.sh
  420  cd ~/Desktop
  421  sudo sh ./alsa_2.sh
  422  console
  423  dxdiag
  424  lspci | grep Audio
  425  sudo chmod 777 alsa_1.sh
  426  sudo chmod 777 alsa_2.sh
  427  sudo sh ./alsa_1.sh
  428  cd ~/Desktop
  429  sudo sh ./alsa_2.sh
  430  #!/bin/sh
  431  #for after reboot
  432  cp -v /lib/modules/3.2.0*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/3.2.0*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
  433  cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/3.2.0*/kernel/sound/
  434  depmod -a
  435  #end of alsa_2
  436  sudo sh ./alsa_2.sh
  437  ps -ef | grep pulseaudio
  438  pacmd list-sinks
  439  sudo modprobe snd-hda-intel
  440  history
  441  sudo apt-get remove --purge pulseaudiosudo apt-get remove --purge pulseaudio
  442  sudo apt-get install alsa-base
  443  sudo apt-get install pulseaudio
  444  sudo alsa force-reload
  445  sudo gedit /etc/modprobe.d/alsa-base.conf
  446  aplay -l
  447  cat /proc/asound/card0/codec#* | grep Codec
  448  cat /proc/asound/cards
  449  history
  450  sudo gedit /etc/modprobe.d/alsa-base.conf
  451  cat /proc/asound/pcm
  452  lspci | grep -i audio
  453  zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
  454  hda_codec
  455  ps ax | grep dpkg
  456  sudo rm /var/lib/dpkg/lock
  457  sudo dpkg --configure -a
  458   sudo apt-get update
  459  ps ax | grep dpkg
  460  apt-get remove dnsmasq
  461  sudo su
  462  sudo su
  463  sudo su
  464  sudo su
  465  sudo su
  466  history
  467  ps ax | grep dpkg
  468  sudo aplay -l
  469   hwinfo | grep sound.card_id
  470  sudo apt-get install hwinfo
  471   hwinfo | grep sound.card_id
  472  lspci -v | grep -A7 -i "audio"
  473  lsmod | grep snd
  474  aplay -l
  475  sudo su
  476  modprobe
  477    modprobe snd-hda-intel
  478  .ko
  479  ko
  480  insmod
  481  args
  482  insmod args
  483  sudo modprobe snd-hda-intel
  484  sudo sh -c 'echo "snd-hda-intel" >> /etc/modules'
  485  echo "snd-hda-intel" | sudo tee -a /etc/modules
  486  history

```

---

### Post by Vladlenin5000 on 2015-07-09
Too much confusion already there. In that situation I would probably start thinking about installing again... That said, back to post #2.

---

### Post by aygusu on 2015-07-10
Thanks but i'm not thinking about installing it again ..
 
I think my soundcard is one of the following;

 ```
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06) 00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) 00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06) 00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
```

 I've tried alsaconfig on terminal but even though it recognizes my sound card it's not working.

---

### Post by dino99 on 2015-07-10
glance at error/warning inside the logs: mainly syslog/dmesg

---

### Post by aygusu on 2015-07-10
I don't understand. What do you mean ? How do i find it ? ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b5a8000 (usable)
[    0.000000]  BIOS-e820: 000000007b5a8000 - 000000007b5ee000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b5ee000 - 000000007b5f8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007b5f8000 - 000000007b5fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b5fb000 - 000000007b621000 (reserved)
[    0.000000]  BIOS-e820: 000000007b621000 - 000000007b623000 (usable)
[    0.000000]  BIOS-e820: 000000007b623000 - 000000007b62d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b62d000 - 000000007b64e000 (reserved)
[    0.000000]  BIOS-e820: 000000007b64e000 - 000000007b691000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b691000 - 000000007b800000 (usable)
[    0.000000]  BIOS-e820: 000000007de00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: EXPER                    KARIZMA A15HM02                   /KARIZMA A15HM02                   , BIOS 1.06.002 Tset Only   11/24/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7b800 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07C000000 mask FFC000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 1984MB, range: 64MB, type UC
[    0.000000] total RAM covered: 1984M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 1984MB, range: 64MB, type UC
[    0.000000] found SMP MP-table at [c00fcd50] fcd50
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0096000] 96000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35878000 - 36c34000
[    0.000000] ACPI: RSDP 000f0410 00024 (v03 Datate)
[    0.000000] ACPI: XSDT 7b5ee080 00054 (v01 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 7b5f7948 000F4 (v04 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110623/tbfadt-365)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0x7B624F40/0x000000007B624F80, using 32 (20110623/tbfadt-489)
[    0.000000] ACPI: DSDT 7b5ee168 097DB (v02 AHM000 AHM00000 00000015 INTL 20051117)
[    0.000000] ACPI: FACS 7b624f40 00040
[    0.000000] ACPI: APIC 7b5f7a40 00062 (v01 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 7b5f7aa8 000BE (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 7b5f7b68 0003C (v01 Datate Diamond1 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 7b5f7ba8 00176 (v01 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI: HPET 7b5f7d20 00038 (v01 Datate Diamond1 01072009 AMI. 00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1088MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007b800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x0007b5a8
[    0.000000]     0: 0x0007b621 -> 0x0007b623
[    0.000000]     0: 0x0007b691 -> 0x0007b800
[    0.000000] On node 0 totalpages: 505507
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f4908200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2177 pages used for memmap
[    0.000000]   HighMem zone: 276122 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s31616 r0 d21632 u2097152
[    0.000000] pcpu-alloc: s31616 r0 d21632 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 501554
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=48983ee5-bda2-4b86-bf65-a2b6dd7da2a0 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8093440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007b800)
[    0.000000] Memory: 1967124k/2023424k available (5627k kernel code, 54904k reserved, 2764k data, 712k init, 1113196k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2127.812 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4255.62 BogoMIPS (lpj=8511248)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000042] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000096] Mount-cache hash table entries: 512
[    0.000214] Initializing cgroup subsys cpuacct
[    0.000220] Initializing cgroup subsys memory
[    0.000227] Initializing cgroup subsys devices
[    0.000230] Initializing cgroup subsys freezer
[    0.000232] Initializing cgroup subsys blkio
[    0.000237] Initializing cgroup subsys perf_event
[    0.000263] CPU: Physical Processor ID: 0
[    0.000264] CPU: Processor Core ID: 0
[    0.000269] mce: CPU supports 9 MCE banks
[    0.000282] CPU0: Thermal monitoring enabled (TM1)
[    0.000290] using mwait in idle threads.
[    0.002382] ACPI: Core revision 20110623
[    0.008195] ftrace: allocating 25954 entries in 51 pages
[    0.016632] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.017117] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056782] CPU0: Intel(R) Pentium(R) CPU        P6200  @ 2.13GHz stepping 05
[    0.163068] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.163075] ... version:                3
[    0.163077] ... bit width:              48
[    0.163078] ... generic registers:      4
[    0.163079] ... value mask:             0000ffffffffffff
[    0.163081] ... max period:             000000007fffffff
[    0.163082] ... fixed-purpose events:   3
[    0.163084] ... event mask:             000000070000000f
[    0.163224] NMI watchdog enabled, takes one hw-pmu counter.
[    0.163313] CPU 1 irqstacks, hard=f3cea000 soft=f3cec000
[    0.163315] Booting Node   0, Processors  #1 Ok.
[    0.163317] smpboot cpu 1: start_ip = 96000
[    0.173616] Initializing CPU#1
[    0.271127] NMI watchdog enabled, takes one hw-pmu counter.
[    0.271170] Brought up 2 CPUs
[    0.271172] Total of 2 processors activated (8511.53 BogoMIPS).
[    0.272582] devtmpfs: initialized
[    0.272699] EVM: security.selinux
[    0.272700] EVM: security.SMACK64
[    0.272702] EVM: security.capability
[    0.272730] PM: Registering ACPI NVS region at 7b5a8000 (286720 bytes)
[    0.272738] PM: Registering ACPI NVS region at 7b5f8000 (12288 bytes)
[    0.272740] PM: Registering ACPI NVS region at 7b623000 (40960 bytes)
[    0.272743] PM: Registering ACPI NVS region at 7b64e000 (274432 bytes)
[    0.273807] print_constraints: dummy: 
[    0.273841] RTC time: 10:36:51, date: 07/10/15
[    0.273880] NET: Registered protocol family 16
[    0.273956] Trying to unpack rootfs image as initramfs...
[    0.273998] EISA bus registered
[    0.274023] ACPI: bus type pci registered
[    0.274084] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.274088] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.274089] PCI: Using MMCONFIG for extended config space
[    0.274091] PCI: Using configuration type 1 for base access
[    0.275094] bio: create slab <bio-0> at 0
[    0.275183] ACPI: Added _OSI(Module Device)
[    0.275185] ACPI: Added _OSI(Processor Device)
[    0.275187] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.275190] ACPI: Added _OSI(Processor Aggregator Device)
[    0.277051] ACPI: EC: Look up EC in DSDT
[    0.278845] ACPI: Executed 1 blocks of module-level executable AML code
[    0.282855] ACPI: SSDT 7b623c18 00262 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.283326] ACPI: Dynamic OEM Table Load:
[    0.283329] ACPI: SSDT   (null) 00262 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.284588] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.303188] ACPI: Interpreter enabled
[    0.303204] ACPI: (supports S0 S1 S3 S4 S5)
[    0.303232] ACPI: Using IOAPIC for interrupt routing
[    0.303488] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.375574] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.375785] ACPI: No dock devices found.
[    0.375788] HEST: Table not found.
[    0.375793] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.375936] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.376051] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.376054] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.376057] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.376059] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff]
[    0.376074] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.376097] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.376121] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.376134] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
[    0.376141] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.376147] pci 0000:00:02.0: reg 20: [io  0xf080-0xf087]
[    0.376226] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.376253] pci 0000:00:1a.0: reg 10: [mem 0xfe608000-0xfe6083ff]
[    0.376369] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.376375] pci 0000:00:1a.0: PME# disabled
[    0.376407] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.376429] pci 0000:00:1b.0: reg 10: [mem 0xfe600000-0xfe603fff 64bit]
[    0.376532] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.376537] pci 0000:00:1b.0: PME# disabled
[    0.376567] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.376673] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.376678] pci 0000:00:1c.0: PME# disabled
[    0.376709] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.376814] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.376819] pci 0000:00:1c.1: PME# disabled
[    0.376850] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    0.376957] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.376962] pci 0000:00:1c.2: PME# disabled
[    0.377004] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.377030] pci 0000:00:1d.0: reg 10: [mem 0xfe607000-0xfe6073ff]
[    0.377144] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.377149] pci 0000:00:1d.0: PME# disabled
[    0.377174] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.377266] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    0.377404] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    0.377432] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.377444] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.377455] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.377467] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.377479] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.377491] pci 0000:00:1f.2: reg 24: [mem 0xfe606000-0xfe6067ff]
[    0.377559] pci 0000:00:1f.2: PME# supported from D3hot
[    0.377564] pci 0000:00:1f.2: PME# disabled
[    0.377588] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.377611] pci 0000:00:1f.3: reg 10: [mem 0xfe605000-0xfe6050ff 64bit]
[    0.377642] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.377692] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.377721] pci 0000:00:1f.6: reg 10: [mem 0xfe604000-0xfe604fff 64bit]
[    0.377885] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.377976] pci 0000:02:00.0: [10ec:8172] type 0 class 0x000280
[    0.377994] pci 0000:02:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.378007] pci 0000:02:00.0: reg 14: [mem 0xfe500000-0xfe503fff]
[    0.378122] pci 0000:02:00.0: supports D1 D2
[    0.378123] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.378129] pci 0000:02:00.0: PME# disabled
[    0.383084] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.383089] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.383095] pci 0000:00:1c.1:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.383182] pci 0000:03:00.0: [197b:2382] type 0 class 0x000880
[    0.383207] pci 0000:03:00.0: reg 10: [mem 0xfe406000-0xfe4060ff]
[    0.383429] pci 0000:03:00.2: [197b:2381] type 0 class 0x000805
[    0.383454] pci 0000:03:00.2: reg 10: [mem 0xfe405000-0xfe4050ff]
[    0.383672] pci 0000:03:00.3: [197b:2383] type 0 class 0x000880
[    0.383697] pci 0000:03:00.3: reg 10: [mem 0xfe404000-0xfe4040ff]
[    0.383918] pci 0000:03:00.5: [197b:0250] type 0 class 0x000200
[    0.383942] pci 0000:03:00.5: reg 10: [mem 0xfe400000-0xfe403fff]
[    0.383976] pci 0000:03:00.5: reg 18: [io  0xd100-0xd17f]
[    0.383994] pci 0000:03:00.5: reg 1c: [io  0xd000-0xd0ff]
[    0.384133] pci 0000:03:00.5: PME# supported from D0 D3hot D3cold
[    0.384140] pci 0000:03:00.5: PME# disabled
[    0.391091] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.391097] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.391103] pci 0000:00:1c.2:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.391188] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.391202] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.391205] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.391207] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.391210] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xffffffff] (subtractive decode)
[    0.391238] pci_bus 0000:00: on NUMA node 0
[    0.391243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.391490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.391608] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.391660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.391700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.391844]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.391997]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.396872] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.396922] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.396971] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.397018] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.397064] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.397112] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.397160] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.397209] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.397311] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.397319] vgaarb: loaded
[    0.397320] vgaarb: bridge control possible 0000:00:02.0
[    0.397426] i2c-core: driver [aat2870] using legacy suspend method
[    0.397427] i2c-core: driver [aat2870] using legacy resume method
[    0.397513] SCSI subsystem initialized
[    0.397569] libata version 3.00 loaded.
[    0.397613] usbcore: registered new interface driver usbfs
[    0.397625] usbcore: registered new interface driver hub
[    0.397650] usbcore: registered new device driver usb
[    0.397732] PCI: Using ACPI for IRQ routing
[    0.407775] PCI: Discovered peer bus ff
[    0.407822] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.407849] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.407873] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.407894] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.407914] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.407935] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.408118] PCI: pci_cache_line_size set to 64 bytes
[    0.408221] reserve RAM buffer: 000000000009ac00 - 000000000009ffff 
[    0.408223] reserve RAM buffer: 000000007b5a8000 - 000000007bffffff 
[    0.408227] reserve RAM buffer: 000000007b623000 - 000000007bffffff 
[    0.408229] reserve RAM buffer: 000000007b800000 - 000000007bffffff 
[    0.408331] NetLabel: Initializing
[    0.408333] NetLabel:  domain hash size = 128
[    0.408334] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.408346] NetLabel:  unlabeled traffic allowed by default
[    0.408404] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.408410] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.410431] Switching to clocksource hpet
[    0.417747] AppArmor: AppArmor Filesystem Enabled
[    0.417778] pnp: PnP ACPI init
[    0.417797] ACPI: bus type pnp registered
[    0.417894] pnp 00:00: [bus 00-ff]
[    0.417896] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.417899] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.417901] pnp 00:00: [io  0x0d00-0xffff window]
[    0.417903] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.417905] pnp 00:00: [mem 0x00000000 window]
[    0.417907] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.417985] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.418037] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.418039] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.418041] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.418043] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.418045] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.418098] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.418101] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.418104] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.418106] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.418109] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.418112] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.418135] pnp 00:02: [dma 4]
[    0.418137] pnp 00:02: [io  0x0000-0x000f]
[    0.418139] pnp 00:02: [io  0x0081-0x0083]
[    0.418140] pnp 00:02: [io  0x0087]
[    0.418142] pnp 00:02: [io  0x0089-0x008b]
[    0.418144] pnp 00:02: [io  0x008f]
[    0.418147] pnp 00:02: [io  0x00c0-0x00df]
[    0.418171] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.418181] pnp 00:03: [io  0x0070-0x0071]
[    0.418193] pnp 00:03: [irq 8]
[    0.418218] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.418227] pnp 00:04: [io  0x0061]
[    0.418250] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.418258] pnp 00:05: [io  0x00f0-0x00ff]
[    0.418264] pnp 00:05: [irq 13]
[    0.418291] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.418309] pnp 00:06: [io  0x0010-0x001f]
[    0.418311] pnp 00:06: [io  0x0022-0x003f]
[    0.418313] pnp 00:06: [io  0x0044-0x005f]
[    0.418315] pnp 00:06: [io  0x0063]
[    0.418316] pnp 00:06: [io  0x0065]
[    0.418318] pnp 00:06: [io  0x0067]
[    0.418320] pnp 00:06: [io  0x0069-0x006b]
[    0.418322] pnp 00:06: [io  0x006d-0x006f]
[    0.418323] pnp 00:06: [io  0x0072-0x007f]
[    0.418325] pnp 00:06: [io  0x0080]
[    0.418327] pnp 00:06: [io  0x0084-0x0086]
[    0.418329] pnp 00:06: [io  0x0088]
[    0.418330] pnp 00:06: [io  0x008c-0x008e]
[    0.418332] pnp 00:06: [io  0x0090-0x009f]
[    0.418334] pnp 00:06: [io  0x00a2-0x00bf]
[    0.418336] pnp 00:06: [io  0x00e0-0x00ef]
[    0.418337] pnp 00:06: [io  0x04d0-0x04d1]
[    0.418389] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.418393] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.418416] pnp 00:07: [io  0x0060]
[    0.418418] pnp 00:07: [io  0x0064]
[    0.418425] pnp 00:07: [irq 1]
[    0.418450] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.418485] pnp 00:08: [irq 12]
[    0.418512] pnp 00:08: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.418652] pnp 00:09: [io  0x0400-0x047f]
[    0.418654] pnp 00:09: [io  0x1180-0x119f]
[    0.418656] pnp 00:09: [io  0x0500-0x057f]
[    0.418658] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.418660] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.418662] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.418664] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.418726] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.418729] system 00:09: [io  0x1180-0x119f] has been reserved
[    0.418731] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.418734] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.418737] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.418739] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.418742] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.418745] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.418878] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.418922] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.434733] pnp: PnP ACPI: found 11 devices
[    0.434736] ACPI: ACPI bus type pnp unregistered
[    0.434741] PnPBIOS: Disabled by ACPI PNP
[    0.470885] PCI: max bus depth: 1 pci_try_num: 2
[    0.470942] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.470946] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.470950] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.470952] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.470956] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.470963] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.470968] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.470977] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.470981] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.470987] pci 0000:00:1c.1:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.470998] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.471002] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.471008] pci 0000:00:1c.2:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.471019] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.471055] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.471062] pci 0000:00:1c.0: setting latency timer to 64
[    0.471075] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.471080] pci 0000:00:1c.1: setting latency timer to 64
[    0.471093] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.471098] pci 0000:00:1c.2: setting latency timer to 64
[    0.471107] pci 0000:00:1e.0: setting latency timer to 64
[    0.471112] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.471114] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.471116] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.471119] pci_bus 0000:00: resource 7 [mem 0x80000000-0xffffffff]
[    0.471121] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.471123] pci_bus 0000:01: resource 1 [mem 0x80000000-0x801fffff]
[    0.471125] pci_bus 0000:01: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.471128] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.471130] pci_bus 0000:02: resource 1 [mem 0xfe500000-0xfe5fffff]
[    0.471132] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.471134] pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.471137] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.471139] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.471141] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.471144] pci_bus 0000:04: resource 7 [mem 0x80000000-0xffffffff]
[    0.471146] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.471148] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xffffffff]
[    0.471189] NET: Registered protocol family 2
[    0.471250] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.471431] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.471738] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.471878] TCP: Hash tables configured (established 131072 bind 65536)
[    0.471880] TCP reno registered
[    0.471883] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.471889] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.471947] NET: Registered protocol family 1
[    0.471959] pci 0000:00:02.0: Boot video device
[    0.471969] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.498681] pci 0000:00:1a.0: PCI INT A disabled
[    0.498717] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.522661] pci 0000:00:1d.0: PCI INT A disabled
[    0.522707] PCI: CLS 64 bytes, default 64
[    0.523088] audit: initializing netlink socket (disabled)
[    0.523101] type=2000 audit(1436524610.392:1): initialized
[    0.549501] highmem bounce pool size: 64 pages
[    0.549507] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.556098] VFS: Disk quotas dquot_6.5.2
[    0.556167] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.556695] fuse init (API version 7.17)
[    0.556788] msgmni has been set to 1667
[    0.557085] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.557110] io scheduler noop registered
[    0.557112] io scheduler deadline registered
[    0.557119] io scheduler cfq registered (default)
[    0.557254] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.557318] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.557418] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.557471] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.557557] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.557610] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.557716] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.557723] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.557744] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.557746] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.557751] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.557772] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.557774] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.557776] pci 0000:03:00.2: Signaling PME through PCIe PME interrupt
[    0.557778] pci 0000:03:00.3: Signaling PME through PCIe PME interrupt
[    0.557780] pci 0000:03:00.5: Signaling PME through PCIe PME interrupt
[    0.557785] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.557801] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.557840] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 3b42 ss_vid 1297 ss_did 2012
[    0.557863] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.557869] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.557941] intel_idle: MWAIT substates: 0x120
[    0.557943] intel_idle: v0.4 model 0x25
[    0.557944] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.590640] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.626652] ACPI: AC Adapter [AC0] (on-line)
[    0.626745] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.626751] ACPI: Power Button [PWRB]
[    0.626795] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.626798] ACPI: Sleep Button [SLPB]
[    0.626844] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.626864] ACPI: Lid Switch [LID]
[    0.626910] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.626913] ACPI: Power Button [PWRF]
[    0.706649] thermal LNXTHERM:00: registered as thermal_zone0
[    0.706653] ACPI: Thermal Zone [TZ00] (58 C)
[    0.706701] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.706712] ACPI: Battery Slot [BAT0] (battery present)
[    0.706735] ERST: Table is not found!
[    0.706737] GHES: HEST is not enabled!
[    0.706832] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.707045] isapnp: Scanning for PnP cards...
[    0.762292] Freeing initrd memory: 20208k freed
[    1.061143] isapnp: No Plug & Play device found
[    1.206480] ACPI: Battery Slot [BAT0] (battery present)
[    1.214826] Linux agpgart interface v0.103
[    1.214930] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.215017] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.215860] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.216007] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.217584] brd: module loaded
[    1.218418] loop: module loaded
[    1.218538] ahci 0000:00:1f.2: version 3.0
[    1.218562] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.218614] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.218687] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.218691] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.218698] ahci 0000:00:1f.2: setting latency timer to 64
[    1.226754] scsi0 : ahci
[    1.226856] scsi1 : ahci
[    1.226940] scsi2 : ahci
[    1.227020] scsi3 : ahci
[    1.227143] ata1: SATA max UDMA/133 abar m2048@0xfe606000 port 0xfe606100 irq 43
[    1.227146] ata2: SATA max UDMA/133 abar m2048@0xfe606000 port 0xfe606180 irq 43
[    1.227148] ata3: DUMMY
[    1.227150] ata4: DUMMY
[    1.227559] Fixed MDIO Bus: probed
[    1.227579] tun: Universal TUN/TAP device driver, 1.6
[    1.227581] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.227634] PPP generic driver version 2.4.2
[    1.227748] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.227764] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.227777] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.227781] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.227831] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.227858] ehci_hcd 0000:00:1a.0: debug port 2
[    1.231829] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.231845] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe608000
[    1.246350] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.246522] hub 1-0:1.0: USB hub found
[    1.246527] hub 1-0:1.0: 2 ports detected
[    1.246593] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.246605] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.246609] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.246658] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.246683] ehci_hcd 0000:00:1d.0: debug port 2
[    1.250662] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.250681] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe607000
[    1.266340] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.266492] hub 2-0:1.0: USB hub found
[    1.266496] hub 2-0:1.0: 2 ports detected
[    1.266557] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.266570] uhci_hcd: USB Universal Host Controller Interface driver
[    1.266618] usbcore: registered new interface driver libusual
[    1.266665] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.271340] i8042: Detected active multiplexing controller, rev 1.0
[    1.272121] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.272127] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.272156] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.272179] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.272202] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.272322] mousedev: PS/2 mouse device common for all mice
[    1.272683] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.272715] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.272780] device-mapper: uevent: version 1.0.3
[    1.272858] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.272889] EISA: Probing bus 0 at eisa.0
[    1.272891] EISA: Cannot allocate resource for mainboard
[    1.272893] Cannot allocate resource for EISA slot 1
[    1.272894] Cannot allocate resource for EISA slot 2
[    1.272896] Cannot allocate resource for EISA slot 3
[    1.272897] Cannot allocate resource for EISA slot 4
[    1.272899] Cannot allocate resource for EISA slot 5
[    1.272901] Cannot allocate resource for EISA slot 6
[    1.272902] Cannot allocate resource for EISA slot 7
[    1.272904] Cannot allocate resource for EISA slot 8
[    1.272905] EISA: Detected 0 cards.
[    1.272914] cpufreq-nforce2: No nForce2 chipset.
[    1.272958] cpuidle: using governor ladder
[    1.273029] cpuidle: using governor menu
[    1.273031] EFI Variables Facility v0.08 2004-May-17
[    1.273250] TCP cubic registered
[    1.273378] NET: Registered protocol family 10
[    1.273935] NET: Registered protocol family 17
[    1.273949] Registering the dns_resolver key type
[    1.273972] Using IPI No-Shortcut mode
[    1.274256] PM: Hibernation image not present or could not be loaded.
[    1.274268] registered taskstats version 1
[    1.277375] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.283556]   Magic number: 7:397:628
[    1.283669] rtc_cmos 00:03: setting system clock to 2015-07-10 10:36:52 UTC (1436524612)
[    1.284184] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.284186] EDD information not available.
[    1.542272] Refined TSC clocksource calibration: 2127.999 MHz.
[    1.542282] Switching to clocksource tsc
[    1.546271] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.546313] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.550252] ata2.00: ATAPI: SlimtypeDVD A  DS8A5S, WX13, max UDMA/100
[    1.551708] ata2.00: configured for UDMA/100
[    1.552484] ata1.00: ATA-8: SAMSUNG HN-M320MBB, 2AR10001, max UDMA/133
[    1.552491] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.558261] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.558716] ata1.00: configured for UDMA/133
[    1.559015] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M320M 2AR1 PQ: 0 ANSI: 5
[    1.559313] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.559377] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.559470] sd 0:0:0:0: [sda] Write Protect is off
[    1.559473] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.559497] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.564313] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A5S    WX13 PQ: 0 ANSI: 5
[    1.569900] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.569906] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.570128] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.570215] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.599927]  sda: sda1 sda3 < sda5 sda6 >
[    1.601122] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.601179] Freeing unused kernel memory: 712k freed
[    1.601435] Write protecting the kernel text: 5628k
[    1.601500] Write protecting the kernel read-only data: 2324k
[    1.622473] udevd[93]: starting version 175
[    1.691047] hub 1-1:1.0: USB hub found
[    1.691213] hub 1-1:1.0: 6 ports detected
[    1.748793] wmi: Mapper loaded
[    1.755420] [drm] Initialized drm 1.1.0 20060810
[    1.761330] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.761336] i915 0000:00:02.0: setting latency timer to 64
[    1.771214] sdhci: Secure Digital Host Controller Interface driver
[    1.771217] sdhci: Copyright(c) Pierre Ossman
[    1.771476] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.771499] sdhci-pci 0000:03:00.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.771541] sdhci-pci 0000:03:00.0: setting latency timer to 64
[    1.771568] mmc0: no vmmc regulator found
[    1.771599] Registered led device: mmc0::
[    1.780546] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    1.780552] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.780553] [drm] Driver supports precise vblank timestamp query.
[    1.780591] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.785293] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.792141] mmc0: SDHCI controller on PCI [0000:03:00.0] using ADMA
[    1.792167] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.792189] sdhci-pci 0000:03:00.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.792195] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.792203] sdhci-pci 0000:03:00.2: PCI INT B disabled
[    1.792411] jme 0000:03:00.5: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.792423] jme 0000:03:00.5: setting latency timer to 64
[    1.793534] jme 0000:03:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:80:ee:73:0f:bb:5d
[    1.802112] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.850648] fixme: max PWM is zero.
[    1.934879] hub 2-1:1.0: USB hub found
[    1.934946] hub 2-1:1.0: 8 ports detected
[    2.006219] usb 1-1.6: new full-speed USB device number 3 using ehci_hcd
[    2.106927] usbcore: registered new interface driver usbhid
[    2.106930] usbhid: USB HID core driver
[    2.113195] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.6/input2
[    2.116060] input: Logitech Unifying Device. Wireless PID:400a as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.2/0003:046D:C52B.0003/input/input5
[    2.116270] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:400a] on usb-0000:00:1a.0-1.6:1
[    2.537739] fbcon: inteldrmfb (fb0) is primary device
[    2.774292] Console: switching to colour frame buffer device 170x48
[    2.778781] fb0: inteldrmfb frame buffer device
[    2.778782] drm: registered panic notifier
[    2.865780] acpi device:47: registered as cooling_device2
[    2.866189] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    2.866231] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.866259] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.174500] jme 0000:03:00.5: irq 45 for MSI/MSI-X
[    3.198179] jme 0000:03:00.5: eth0: Link is down
[    3.198379] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.238280] Adding 1787900k swap on /dev/sda5.  Priority:-1 extents:1 across:1787900k 
[   34.247634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.419106] udevd[441]: starting version 175
[   34.624875] lp: driver loaded but no devices found
[   34.654751] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.657078] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.735387] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.739965] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.752992] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.812058] cfg80211: Calling CRDA to update world regulatory domain
[   34.820895] intel ips 0000:00:1f.6: No CPUID match found.
[   34.820899] intel ips 0000:00:1f.6: IPS not supported on this CPU
[   34.829133] jmb38x_ms 0000:03:00.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   34.829143] jmb38x_ms 0000:03:00.3: setting latency timer to 64
[   34.875537] rtl8192se 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   34.875546] rtl8192se 0000:02:00.0: setting latency timer to 64
[   34.888480] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   34.909252] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   34.909254] Loading firmware rtlwifi/rtl8192sefw.bin
[   35.071830] psmouse serio2: hgpk: ID: 10 00 64
[   35.072879] asus_wmi: Asus Management GUID not found
[   35.076938] cfg80211: World regulatory domain updated:
[   35.076942] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   35.076944] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.076947] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.076949] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.076951] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.076954] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.162292] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   35.162296] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162298] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   35.162301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162303] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   35.162305] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162307] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   35.162310] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162312] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   35.162314] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162316] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   35.162319] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162321] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   35.162323] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162325] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   35.162328] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162330] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   35.162332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162334] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   35.162337] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162339] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   35.162341] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162343] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   35.162346] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162348] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   35.162350] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162352] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   35.162643] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   35.166223] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   35.176516] psmouse serio2: elantech: assuming hardware version 2 (with firmware version 0x040101)
[   35.217861] psmouse serio2: elantech: Synaptics capabilities query result 0x7f, 0x13, 0x0d.
[   35.228665] init: failsafe main process (1000) killed by TERM signal
[   35.317943] Bluetooth: Core ver 2.16
[   35.319853] NET: Registered protocol family 31
[   35.319856] Bluetooth: HCI device and connection manager initialized
[   35.319860] Bluetooth: HCI socket layer initialized
[   35.319862] Bluetooth: L2CAP socket layer initialized
[   35.320212] Bluetooth: SCO socket layer initialized
[   35.322559] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.322562] Bluetooth: BNEP filters: protocol multicast
[   35.359115] Bluetooth: RFCOMM TTY layer initialized
[   35.359120] Bluetooth: RFCOMM socket layer initialized
[   35.359122] Bluetooth: RFCOMM ver 1.11
[   35.367846] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input7
[   35.471521] ppdev: user-space parallel port driver
[   36.019446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.020323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.022914] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.450197] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   37.498639] init: alsa-restore main process (1386) terminated with status 19
```
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b5a8000 (usable)
[    0.000000]  BIOS-e820: 000000007b5a8000 - 000000007b5ee000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b5ee000 - 000000007b5f8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007b5f8000 - 000000007b5fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b5fb000 - 000000007b621000 (reserved)
[    0.000000]  BIOS-e820: 000000007b621000 - 000000007b623000 (usable)
[    0.000000]  BIOS-e820: 000000007b623000 - 000000007b62d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b62d000 - 000000007b64e000 (reserved)
[    0.000000]  BIOS-e820: 000000007b64e000 - 000000007b691000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b691000 - 000000007b800000 (usable)
[    0.000000]  BIOS-e820: 000000007de00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: EXPER                    KARIZMA A15HM02                   /KARIZMA A15HM02                   , BIOS 1.06.002 Tset Only   11/24/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7b800 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07C000000 mask FFC000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 1984MB, range: 64MB, type UC
[    0.000000] total RAM covered: 1984M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 1984MB, range: 64MB, type UC
[    0.000000] found SMP MP-table at [c00fcd50] fcd50
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0096000] 96000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35878000 - 36c34000
[    0.000000] ACPI: RSDP 000f0410 00024 (v03 Datate)
[    0.000000] ACPI: XSDT 7b5ee080 00054 (v01 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 7b5f7948 000F4 (v04 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110623/tbfadt-365)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0x7B624F40/0x000000007B624F80, using 32 (20110623/tbfadt-489)
[    0.000000] ACPI: DSDT 7b5ee168 097DB (v02 AHM000 AHM00000 00000015 INTL 20051117)
[    0.000000] ACPI: FACS 7b624f40 00040
[    0.000000] ACPI: APIC 7b5f7a40 00062 (v01 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 7b5f7aa8 000BE (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 7b5f7b68 0003C (v01 Datate Diamond1 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 7b5f7ba8 00176 (v01 Datate Diamond1 01072009 AMI  00010013)
[    0.000000] ACPI: HPET 7b5f7d20 00038 (v01 Datate Diamond1 01072009 AMI. 00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1088MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007b800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x0007b5a8
[    0.000000]     0: 0x0007b621 -> 0x0007b623
[    0.000000]     0: 0x0007b691 -> 0x0007b800
[    0.000000] On node 0 totalpages: 505507
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f4908200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2177 pages used for memmap
[    0.000000]   HighMem zone: 276122 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s31616 r0 d21632 u2097152
[    0.000000] pcpu-alloc: s31616 r0 d21632 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 501554
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=48983ee5-bda2-4b86-bf65-a2b6dd7da2a0 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8093440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007b800)
[    0.000000] Memory: 1967124k/2023424k available (5627k kernel code, 54904k reserved, 2764k data, 712k init, 1113196k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2127.812 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4255.62 BogoMIPS (lpj=8511248)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000042] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000096] Mount-cache hash table entries: 512
[    0.000214] Initializing cgroup subsys cpuacct
[    0.000220] Initializing cgroup subsys memory
[    0.000227] Initializing cgroup subsys devices
[    0.000230] Initializing cgroup subsys freezer
[    0.000232] Initializing cgroup subsys blkio
[    0.000237] Initializing cgroup subsys perf_event
[    0.000263] CPU: Physical Processor ID: 0
[    0.000264] CPU: Processor Core ID: 0
[    0.000269] mce: CPU supports 9 MCE banks
[    0.000282] CPU0: Thermal monitoring enabled (TM1)
[    0.000290] using mwait in idle threads.
[    0.002382] ACPI: Core revision 20110623
[    0.008195] ftrace: allocating 25954 entries in 51 pages
[    0.016632] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.017117] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056782] CPU0: Intel(R) Pentium(R) CPU        P6200  @ 2.13GHz stepping 05
[    0.163068] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.163075] ... version:                3
[    0.163077] ... bit width:              48
[    0.163078] ... generic registers:      4
[    0.163079] ... value mask:             0000ffffffffffff
[    0.163081] ... max period:             000000007fffffff
[    0.163082] ... fixed-purpose events:   3
[    0.163084] ... event mask:             000000070000000f
[    0.163224] NMI watchdog enabled, takes one hw-pmu counter.
[    0.163313] CPU 1 irqstacks, hard=f3cea000 soft=f3cec000
[    0.163315] Booting Node   0, Processors  #1 Ok.
[    0.163317] smpboot cpu 1: start_ip = 96000
[    0.173616] Initializing CPU#1
[    0.271127] NMI watchdog enabled, takes one hw-pmu counter.
[    0.271170] Brought up 2 CPUs
[    0.271172] Total of 2 processors activated (8511.53 BogoMIPS).
[    0.272582] devtmpfs: initialized
[    0.272699] EVM: security.selinux
[    0.272700] EVM: security.SMACK64
[    0.272702] EVM: security.capability
[    0.272730] PM: Registering ACPI NVS region at 7b5a8000 (286720 bytes)
[    0.272738] PM: Registering ACPI NVS region at 7b5f8000 (12288 bytes)
[    0.272740] PM: Registering ACPI NVS region at 7b623000 (40960 bytes)
[    0.272743] PM: Registering ACPI NVS region at 7b64e000 (274432 bytes)
[    0.273807] print_constraints: dummy: 
[    0.273841] RTC time: 10:36:51, date: 07/10/15
[    0.273880] NET: Registered protocol family 16
[    0.273956] Trying to unpack rootfs image as initramfs...
[    0.273998] EISA bus registered
[    0.274023] ACPI: bus type pci registered
[    0.274084] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.274088] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.274089] PCI: Using MMCONFIG for extended config space
[    0.274091] PCI: Using configuration type 1 for base access
[    0.275094] bio: create slab <bio-0> at 0
[    0.275183] ACPI: Added _OSI(Module Device)
[    0.275185] ACPI: Added _OSI(Processor Device)
[    0.275187] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.275190] ACPI: Added _OSI(Processor Aggregator Device)
[    0.277051] ACPI: EC: Look up EC in DSDT
[    0.278845] ACPI: Executed 1 blocks of module-level executable AML code
[    0.282855] ACPI: SSDT 7b623c18 00262 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.283326] ACPI: Dynamic OEM Table Load:
[    0.283329] ACPI: SSDT   (null) 00262 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.284588] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.303188] ACPI: Interpreter enabled
[    0.303204] ACPI: (supports S0 S1 S3 S4 S5)
[    0.303232] ACPI: Using IOAPIC for interrupt routing
[    0.303488] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.375574] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.375785] ACPI: No dock devices found.
[    0.375788] HEST: Table not found.
[    0.375793] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.375936] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.376051] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.376054] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.376057] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.376059] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff]
[    0.376074] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.376097] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.376121] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.376134] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
[    0.376141] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.376147] pci 0000:00:02.0: reg 20: [io  0xf080-0xf087]
[    0.376226] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.376253] pci 0000:00:1a.0: reg 10: [mem 0xfe608000-0xfe6083ff]
[    0.376369] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.376375] pci 0000:00:1a.0: PME# disabled
[    0.376407] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.376429] pci 0000:00:1b.0: reg 10: [mem 0xfe600000-0xfe603fff 64bit]
[    0.376532] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.376537] pci 0000:00:1b.0: PME# disabled
[    0.376567] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.376673] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.376678] pci 0000:00:1c.0: PME# disabled
[    0.376709] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.376814] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.376819] pci 0000:00:1c.1: PME# disabled
[    0.376850] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    0.376957] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.376962] pci 0000:00:1c.2: PME# disabled
[    0.377004] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.377030] pci 0000:00:1d.0: reg 10: [mem 0xfe607000-0xfe6073ff]
[    0.377144] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.377149] pci 0000:00:1d.0: PME# disabled
[    0.377174] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.377266] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    0.377404] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    0.377432] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.377444] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.377455] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.377467] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.377479] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.377491] pci 0000:00:1f.2: reg 24: [mem 0xfe606000-0xfe6067ff]
[    0.377559] pci 0000:00:1f.2: PME# supported from D3hot
[    0.377564] pci 0000:00:1f.2: PME# disabled
[    0.377588] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.377611] pci 0000:00:1f.3: reg 10: [mem 0xfe605000-0xfe6050ff 64bit]
[    0.377642] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.377692] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.377721] pci 0000:00:1f.6: reg 10: [mem 0xfe604000-0xfe604fff 64bit]
[    0.377885] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.377976] pci 0000:02:00.0: [10ec:8172] type 0 class 0x000280
[    0.377994] pci 0000:02:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.378007] pci 0000:02:00.0: reg 14: [mem 0xfe500000-0xfe503fff]
[    0.378122] pci 0000:02:00.0: supports D1 D2
[    0.378123] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.378129] pci 0000:02:00.0: PME# disabled
[    0.383084] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.383089] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.383095] pci 0000:00:1c.1:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.383182] pci 0000:03:00.0: [197b:2382] type 0 class 0x000880
[    0.383207] pci 0000:03:00.0: reg 10: [mem 0xfe406000-0xfe4060ff]
[    0.383429] pci 0000:03:00.2: [197b:2381] type 0 class 0x000805
[    0.383454] pci 0000:03:00.2: reg 10: [mem 0xfe405000-0xfe4050ff]
[    0.383672] pci 0000:03:00.3: [197b:2383] type 0 class 0x000880
[    0.383697] pci 0000:03:00.3: reg 10: [mem 0xfe404000-0xfe4040ff]
[    0.383918] pci 0000:03:00.5: [197b:0250] type 0 class 0x000200
[    0.383942] pci 0000:03:00.5: reg 10: [mem 0xfe400000-0xfe403fff]
[    0.383976] pci 0000:03:00.5: reg 18: [io  0xd100-0xd17f]
[    0.383994] pci 0000:03:00.5: reg 1c: [io  0xd000-0xd0ff]
[    0.384133] pci 0000:03:00.5: PME# supported from D0 D3hot D3cold
[    0.384140] pci 0000:03:00.5: PME# disabled
[    0.391091] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.391097] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.391103] pci 0000:00:1c.2:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.391188] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.391202] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.391205] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.391207] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.391210] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xffffffff] (subtractive decode)
[    0.391238] pci_bus 0000:00: on NUMA node 0
[    0.391243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.391490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.391608] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.391660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.391700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.391844]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.391997]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.396872] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.396922] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.396971] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.397018] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.397064] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.397112] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.397160] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.397209] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.397311] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.397319] vgaarb: loaded
[    0.397320] vgaarb: bridge control possible 0000:00:02.0
[    0.397426] i2c-core: driver [aat2870] using legacy suspend method
[    0.397427] i2c-core: driver [aat2870] using legacy resume method
[    0.397513] SCSI subsystem initialized
[    0.397569] libata version 3.00 loaded.
[    0.397613] usbcore: registered new interface driver usbfs
[    0.397625] usbcore: registered new interface driver hub
[    0.397650] usbcore: registered new device driver usb
[    0.397732] PCI: Using ACPI for IRQ routing
[    0.407775] PCI: Discovered peer bus ff
[    0.407822] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.407849] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.407873] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.407894] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.407914] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.407935] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.408118] PCI: pci_cache_line_size set to 64 bytes
[    0.408221] reserve RAM buffer: 000000000009ac00 - 000000000009ffff 
[    0.408223] reserve RAM buffer: 000000007b5a8000 - 000000007bffffff 
[    0.408227] reserve RAM buffer: 000000007b623000 - 000000007bffffff 
[    0.408229] reserve RAM buffer: 000000007b800000 - 000000007bffffff 
[    0.408331] NetLabel: Initializing
[    0.408333] NetLabel:  domain hash size = 128
[    0.408334] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.408346] NetLabel:  unlabeled traffic allowed by default
[    0.408404] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.408410] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.410431] Switching to clocksource hpet
[    0.417747] AppArmor: AppArmor Filesystem Enabled
[    0.417778] pnp: PnP ACPI init
[    0.417797] ACPI: bus type pnp registered
[    0.417894] pnp 00:00: [bus 00-ff]
[    0.417896] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.417899] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.417901] pnp 00:00: [io  0x0d00-0xffff window]
[    0.417903] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.417905] pnp 00:00: [mem 0x00000000 window]
[    0.417907] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.417985] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.418037] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.418039] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.418041] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.418043] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.418045] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.418098] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.418101] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.418104] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.418106] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.418109] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.418112] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.418135] pnp 00:02: [dma 4]
[    0.418137] pnp 00:02: [io  0x0000-0x000f]
[    0.418139] pnp 00:02: [io  0x0081-0x0083]
[    0.418140] pnp 00:02: [io  0x0087]
[    0.418142] pnp 00:02: [io  0x0089-0x008b]
[    0.418144] pnp 00:02: [io  0x008f]
[    0.418147] pnp 00:02: [io  0x00c0-0x00df]
[    0.418171] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.418181] pnp 00:03: [io  0x0070-0x0071]
[    0.418193] pnp 00:03: [irq 8]
[    0.418218] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.418227] pnp 00:04: [io  0x0061]
[    0.418250] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.418258] pnp 00:05: [io  0x00f0-0x00ff]
[    0.418264] pnp 00:05: [irq 13]
[    0.418291] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.418309] pnp 00:06: [io  0x0010-0x001f]
[    0.418311] pnp 00:06: [io  0x0022-0x003f]
[    0.418313] pnp 00:06: [io  0x0044-0x005f]
[    0.418315] pnp 00:06: [io  0x0063]
[    0.418316] pnp 00:06: [io  0x0065]
[    0.418318] pnp 00:06: [io  0x0067]
[    0.418320] pnp 00:06: [io  0x0069-0x006b]
[    0.418322] pnp 00:06: [io  0x006d-0x006f]
[    0.418323] pnp 00:06: [io  0x0072-0x007f]
[    0.418325] pnp 00:06: [io  0x0080]
[    0.418327] pnp 00:06: [io  0x0084-0x0086]
[    0.418329] pnp 00:06: [io  0x0088]
[    0.418330] pnp 00:06: [io  0x008c-0x008e]
[    0.418332] pnp 00:06: [io  0x0090-0x009f]
[    0.418334] pnp 00:06: [io  0x00a2-0x00bf]
[    0.418336] pnp 00:06: [io  0x00e0-0x00ef]
[    0.418337] pnp 00:06: [io  0x04d0-0x04d1]
[    0.418389] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.418393] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.418416] pnp 00:07: [io  0x0060]
[    0.418418] pnp 00:07: [io  0x0064]
[    0.418425] pnp 00:07: [irq 1]
[    0.418450] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.418485] pnp 00:08: [irq 12]
[    0.418512] pnp 00:08: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.418652] pnp 00:09: [io  0x0400-0x047f]
[    0.418654] pnp 00:09: [io  0x1180-0x119f]
[    0.418656] pnp 00:09: [io  0x0500-0x057f]
[    0.418658] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.418660] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.418662] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.418664] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.418726] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.418729] system 00:09: [io  0x1180-0x119f] has been reserved
[    0.418731] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.418734] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.418737] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.418739] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.418742] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.418745] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.418878] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.418922] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.434733] pnp: PnP ACPI: found 11 devices
[    0.434736] ACPI: ACPI bus type pnp unregistered
[    0.434741] PnPBIOS: Disabled by ACPI PNP
[    0.470885] PCI: max bus depth: 1 pci_try_num: 2
[    0.470942] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.470946] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.470950] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.470952] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.470956] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.470963] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.470968] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.470977] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.470981] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.470987] pci 0000:00:1c.1:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.470998] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.471002] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.471008] pci 0000:00:1c.2:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.471019] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.471055] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.471062] pci 0000:00:1c.0: setting latency timer to 64
[    0.471075] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.471080] pci 0000:00:1c.1: setting latency timer to 64
[    0.471093] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.471098] pci 0000:00:1c.2: setting latency timer to 64
[    0.471107] pci 0000:00:1e.0: setting latency timer to 64
[    0.471112] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.471114] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.471116] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.471119] pci_bus 0000:00: resource 7 [mem 0x80000000-0xffffffff]
[    0.471121] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.471123] pci_bus 0000:01: resource 1 [mem 0x80000000-0x801fffff]
[    0.471125] pci_bus 0000:01: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.471128] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.471130] pci_bus 0000:02: resource 1 [mem 0xfe500000-0xfe5fffff]
[    0.471132] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.471134] pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.471137] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.471139] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.471141] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.471144] pci_bus 0000:04: resource 7 [mem 0x80000000-0xffffffff]
[    0.471146] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.471148] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xffffffff]
[    0.471189] NET: Registered protocol family 2
[    0.471250] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.471431] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.471738] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.471878] TCP: Hash tables configured (established 131072 bind 65536)
[    0.471880] TCP reno registered
[    0.471883] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.471889] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.471947] NET: Registered protocol family 1
[    0.471959] pci 0000:00:02.0: Boot video device
[    0.471969] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.498681] pci 0000:00:1a.0: PCI INT A disabled
[    0.498717] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.522661] pci 0000:00:1d.0: PCI INT A disabled
[    0.522707] PCI: CLS 64 bytes, default 64
[    0.523088] audit: initializing netlink socket (disabled)
[    0.523101] type=2000 audit(1436524610.392:1): initialized
[    0.549501] highmem bounce pool size: 64 pages
[    0.549507] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.556098] VFS: Disk quotas dquot_6.5.2
[    0.556167] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.556695] fuse init (API version 7.17)
[    0.556788] msgmni has been set to 1667
[    0.557085] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.557110] io scheduler noop registered
[    0.557112] io scheduler deadline registered
[    0.557119] io scheduler cfq registered (default)
[    0.557254] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.557318] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.557418] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.557471] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.557557] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.557610] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.557716] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.557723] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.557744] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.557746] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.557751] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.557772] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.557774] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.557776] pci 0000:03:00.2: Signaling PME through PCIe PME interrupt
[    0.557778] pci 0000:03:00.3: Signaling PME through PCIe PME interrupt
[    0.557780] pci 0000:03:00.5: Signaling PME through PCIe PME interrupt
[    0.557785] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.557801] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.557840] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 3b42 ss_vid 1297 ss_did 2012
[    0.557863] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.557869] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.557941] intel_idle: MWAIT substates: 0x120
[    0.557943] intel_idle: v0.4 model 0x25
[    0.557944] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.590640] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.626652] ACPI: AC Adapter [AC0] (on-line)
[    0.626745] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.626751] ACPI: Power Button [PWRB]
[    0.626795] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.626798] ACPI: Sleep Button [SLPB]
[    0.626844] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.626864] ACPI: Lid Switch [LID]
[    0.626910] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.626913] ACPI: Power Button [PWRF]
[    0.706649] thermal LNXTHERM:00: registered as thermal_zone0
[    0.706653] ACPI: Thermal Zone [TZ00] (58 C)
[    0.706701] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.706712] ACPI: Battery Slot [BAT0] (battery present)
[    0.706735] ERST: Table is not found!
[    0.706737] GHES: HEST is not enabled!
[    0.706832] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.707045] isapnp: Scanning for PnP cards...
[    0.762292] Freeing initrd memory: 20208k freed
[    1.061143] isapnp: No Plug & Play device found
[    1.206480] ACPI: Battery Slot [BAT0] (battery present)
[    1.214826] Linux agpgart interface v0.103
[    1.214930] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.215017] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.215860] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.216007] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.217584] brd: module loaded
[    1.218418] loop: module loaded
[    1.218538] ahci 0000:00:1f.2: version 3.0
[    1.218562] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.218614] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.218687] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.218691] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.218698] ahci 0000:00:1f.2: setting latency timer to 64
[    1.226754] scsi0 : ahci
[    1.226856] scsi1 : ahci
[    1.226940] scsi2 : ahci
[    1.227020] scsi3 : ahci
[    1.227143] ata1: SATA max UDMA/133 abar m2048@0xfe606000 port 0xfe606100 irq 43
[    1.227146] ata2: SATA max UDMA/133 abar m2048@0xfe606000 port 0xfe606180 irq 43
[    1.227148] ata3: DUMMY
[    1.227150] ata4: DUMMY
[    1.227559] Fixed MDIO Bus: probed
[    1.227579] tun: Universal TUN/TAP device driver, 1.6
[    1.227581] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.227634] PPP generic driver version 2.4.2
[    1.227748] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.227764] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.227777] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.227781] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.227831] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.227858] ehci_hcd 0000:00:1a.0: debug port 2
[    1.231829] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.231845] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe608000
[    1.246350] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.246522] hub 1-0:1.0: USB hub found
[    1.246527] hub 1-0:1.0: 2 ports detected
[    1.246593] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.246605] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.246609] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.246658] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.246683] ehci_hcd 0000:00:1d.0: debug port 2
[    1.250662] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.250681] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe607000
[    1.266340] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.266492] hub 2-0:1.0: USB hub found
[    1.266496] hub 2-0:1.0: 2 ports detected
[    1.266557] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.266570] uhci_hcd: USB Universal Host Controller Interface driver
[    1.266618] usbcore: registered new interface driver libusual
[    1.266665] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.271340] i8042: Detected active multiplexing controller, rev 1.0
[    1.272121] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.272127] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.272156] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.272179] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.272202] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.272322] mousedev: PS/2 mouse device common for all mice
[    1.272683] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.272715] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.272780] device-mapper: uevent: version 1.0.3
[    1.272858] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.272889] EISA: Probing bus 0 at eisa.0
[    1.272891] EISA: Cannot allocate resource for mainboard
[    1.272893] Cannot allocate resource for EISA slot 1
[    1.272894] Cannot allocate resource for EISA slot 2
[    1.272896] Cannot allocate resource for EISA slot 3
[    1.272897] Cannot allocate resource for EISA slot 4
[    1.272899] Cannot allocate resource for EISA slot 5
[    1.272901] Cannot allocate resource for EISA slot 6
[    1.272902] Cannot allocate resource for EISA slot 7
[    1.272904] Cannot allocate resource for EISA slot 8
[    1.272905] EISA: Detected 0 cards.
[    1.272914] cpufreq-nforce2: No nForce2 chipset.
[    1.272958] cpuidle: using governor ladder
[    1.273029] cpuidle: using governor menu
[    1.273031] EFI Variables Facility v0.08 2004-May-17
[    1.273250] TCP cubic registered
[    1.273378] NET: Registered protocol family 10
[    1.273935] NET: Registered protocol family 17
[    1.273949] Registering the dns_resolver key type
[    1.273972] Using IPI No-Shortcut mode
[    1.274256] PM: Hibernation image not present or could not be loaded.
[    1.274268] registered taskstats version 1
[    1.277375] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.283556]   Magic number: 7:397:628
[    1.283669] rtc_cmos 00:03: setting system clock to 2015-07-10 10:36:52 UTC (1436524612)
[    1.284184] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.284186] EDD information not available.
[    1.542272] Refined TSC clocksource calibration: 2127.999 MHz.
[    1.542282] Switching to clocksource tsc
[    1.546271] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.546313] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.550252] ata2.00: ATAPI: SlimtypeDVD A  DS8A5S, WX13, max UDMA/100
[    1.551708] ata2.00: configured for UDMA/100
[    1.552484] ata1.00: ATA-8: SAMSUNG HN-M320MBB, 2AR10001, max UDMA/133
[    1.552491] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.558261] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.558716] ata1.00: configured for UDMA/133
[    1.559015] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M320M 2AR1 PQ: 0 ANSI: 5
[    1.559313] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.559377] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.559470] sd 0:0:0:0: [sda] Write Protect is off
[    1.559473] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.559497] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.564313] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A5S    WX13 PQ: 0 ANSI: 5
[    1.569900] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.569906] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.570128] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.570215] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.599927]  sda: sda1 sda3 < sda5 sda6 >
[    1.601122] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.601179] Freeing unused kernel memory: 712k freed
[    1.601435] Write protecting the kernel text: 5628k
[    1.601500] Write protecting the kernel read-only data: 2324k
[    1.622473] udevd[93]: starting version 175
[    1.691047] hub 1-1:1.0: USB hub found
[    1.691213] hub 1-1:1.0: 6 ports detected
[    1.748793] wmi: Mapper loaded
[    1.755420] [drm] Initialized drm 1.1.0 20060810
[    1.761330] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.761336] i915 0000:00:02.0: setting latency timer to 64
[    1.771214] sdhci: Secure Digital Host Controller Interface driver
[    1.771217] sdhci: Copyright(c) Pierre Ossman
[    1.771476] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.771499] sdhci-pci 0000:03:00.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.771541] sdhci-pci 0000:03:00.0: setting latency timer to 64
[    1.771568] mmc0: no vmmc regulator found
[    1.771599] Registered led device: mmc0::
[    1.780546] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    1.780552] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.780553] [drm] Driver supports precise vblank timestamp query.
[    1.780591] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.785293] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.792141] mmc0: SDHCI controller on PCI [0000:03:00.0] using ADMA
[    1.792167] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.792189] sdhci-pci 0000:03:00.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.792195] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.792203] sdhci-pci 0000:03:00.2: PCI INT B disabled
[    1.792411] jme 0000:03:00.5: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.792423] jme 0000:03:00.5: setting latency timer to 64
[    1.793534] jme 0000:03:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:80:ee:73:0f:bb:5d
[    1.802112] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.850648] fixme: max PWM is zero.
[    1.934879] hub 2-1:1.0: USB hub found
[    1.934946] hub 2-1:1.0: 8 ports detected
[    2.006219] usb 1-1.6: new full-speed USB device number 3 using ehci_hcd
[    2.106927] usbcore: registered new interface driver usbhid
[    2.106930] usbhid: USB HID core driver
[    2.113195] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.6/input2
[    2.116060] input: Logitech Unifying Device. Wireless PID:400a as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.2/0003:046D:C52B.0003/input/input5
[    2.116270] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:400a] on usb-0000:00:1a.0-1.6:1
[    2.537739] fbcon: inteldrmfb (fb0) is primary device
[    2.774292] Console: switching to colour frame buffer device 170x48
[    2.778781] fb0: inteldrmfb frame buffer device
[    2.778782] drm: registered panic notifier
[    2.865780] acpi device:47: registered as cooling_device2
[    2.866189] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    2.866231] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.866259] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.174500] jme 0000:03:00.5: irq 45 for MSI/MSI-X
[    3.198179] jme 0000:03:00.5: eth0: Link is down
[    3.198379] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.238280] Adding 1787900k swap on /dev/sda5.  Priority:-1 extents:1 across:1787900k 
[   34.247634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.419106] udevd[441]: starting version 175
[   34.624875] lp: driver loaded but no devices found
[   34.654751] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.657078] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.735387] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.739965] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.752992] snd_hda_codec: Unknown symbol snd_device_disconnect (err 0)
[   34.812058] cfg80211: Calling CRDA to update world regulatory domain
[   34.820895] intel ips 0000:00:1f.6: No CPUID match found.
[   34.820899] intel ips 0000:00:1f.6: IPS not supported on this CPU
[   34.829133] jmb38x_ms 0000:03:00.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   34.829143] jmb38x_ms 0000:03:00.3: setting latency timer to 64
[   34.875537] rtl8192se 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   34.875546] rtl8192se 0000:02:00.0: setting latency timer to 64
[   34.888480] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   34.909252] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   34.909254] Loading firmware rtlwifi/rtl8192sefw.bin
[   35.071830] psmouse serio2: hgpk: ID: 10 00 64
[   35.072879] asus_wmi: Asus Management GUID not found
[   35.076938] cfg80211: World regulatory domain updated:
[   35.076942] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   35.076944] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.076947] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.076949] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.076951] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.076954] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.162292] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   35.162296] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162298] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   35.162301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162303] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   35.162305] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162307] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   35.162310] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162312] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   35.162314] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162316] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   35.162319] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162321] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   35.162323] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162325] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   35.162328] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162330] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   35.162332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162334] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   35.162337] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162339] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   35.162341] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162343] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   35.162346] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162348] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   35.162350] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.162352] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   35.162643] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   35.166223] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   35.176516] psmouse serio2: elantech: assuming hardware version 2 (with firmware version 0x040101)
[   35.217861] psmouse serio2: elantech: Synaptics capabilities query result 0x7f, 0x13, 0x0d.
[   35.228665] init: failsafe main process (1000) killed by TERM signal
[   35.317943] Bluetooth: Core ver 2.16
[   35.319853] NET: Registered protocol family 31
[   35.319856] Bluetooth: HCI device and connection manager initialized
[   35.319860] Bluetooth: HCI socket layer initialized
[   35.319862] Bluetooth: L2CAP socket layer initialized
[   35.320212] Bluetooth: SCO socket layer initialized
[   35.322559] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.322562] Bluetooth: BNEP filters: protocol multicast
[   35.359115] Bluetooth: RFCOMM TTY layer initialized
[   35.359120] Bluetooth: RFCOMM socket layer initialized
[   35.359122] Bluetooth: RFCOMM ver 1.11
[   35.367846] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input7
[   35.471521] ppdev: user-space parallel port driver
[   36.019446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.020323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.022914] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.450197] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   37.498639] init: alsa-restore main process (1386) terminated with status 19
```

---

### Post by aygusu on 2015-07-13
I got my sound back after upgrading linux 's core , downloading grub customizer , and after that picking up the lastest version ( with grub customizer ) and rebooting . Of course selecting the new version !

---

