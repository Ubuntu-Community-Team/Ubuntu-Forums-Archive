---
title: "Ubuntu 18.04 can't recognize all RAM"
date: 2018-11-01
forum: Hardware
---

### Post by erogarcia on 2018-11-01
Hi everyone ):P

I have 3 RAM modules of 8 GB, the BIOS can see it. Totally RAM 24 GB. But my SO only can use 16 GB. :( By the way, the installation CD works in the same way.

My system:

-*Ubuntu 18.04.1 64x* fresh installation with official ISO.
-Motherboard *Gigabyte GA-970A-D3P (rev. 2)* [I did the "iommu=soft" in my grub :wink:]

**lshw** says:

```

memory
          descrição: Memória do sistema
          ID físico: 2c
          slot: Placa do sistema ou placa-mãe
          tamanho: 24GiB
        *-bank:0
             descrição: DIMM DDR3 Síncrono Unbuffered (Unregistered) 933 MHz (1,1 ns)
             produto: KHX1866C10D3/
             fabricante: Kingston
             ID físico: 0
             serial: 253DA450
             slot: Node0_Dimm0
             tamanho: 8GiB
             largura: 64 bits
             clock: 933MHz (1.1ns)
        *-bank:1
             descrição: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-06-04 15:22+0000Last-Translator: Mykas0 <Mykas0@gmail.com>Language-Team: Portuguese <pt@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) Síncrono [vazio]
             produto: Dimm1_PartNum
             fabricante: Dimm1_Manufacturer
             ID físico: 1
             serial: Dimm1_SerNum
             slot: Node0_Dimm1
        *-bank:2
             descrição: DIMM DDR3 Síncrono Unbuffered (Unregistered) 933 MHz (1,1 ns)
             produto: KHX1866C10D3/
             fabricante: Kingston
             ID físico: 2
             serial: 223D4D50
             slot: Node0_Dimm2
             tamanho: 8GiB
             largura: 64 bits
             clock: 933MHz (1.1ns)
        *-bank:3
             descrição: DIMM DDR3 Síncrono Unbuffered (Unregistered) 933 MHz (1,1 ns)
             produto: KHX1866C10D3/
             fabricante: Kingston
             ID físico: 3
             serial: 242EE697
             slot: Node0_Dimm3
             tamanho: 8GiB
             largura: 64 bits
             clock: 933MHz (1.1ns)
```

But ```
free -h

              total       usada       livre    compart.  buff/cache  disponível
Mem:            15G        2,8G        7,9G        182M        4,9G         12G
Espazo de intercambio:        2,0G          0B        2,0G
```


Any ideas? :confused:

Thanks in advance :)

---

### Post by Tadaen_Sylvermane on 2018-11-01
Just an idea. That is probably a dual or quad channel memory system. The OS may be able to physically see the hardware but it can't run in both dual and single channel at the same time. If you filled that empty slot I'd guess it would work fine.

I am far from an expert on anything though, just an observation.

---

### Post by Autodave on 2018-11-01
I would start by getting them in order: looks like slot #1 is empty.  Move the one from slot #3 into slot #1.

---

### Post by pete-br on 2018-11-01
Check your Kernel Boot Parameters with:

cat /proc/cmdline

It could have a memory limit set like "mem=15G".

---

### Post by erogarcia on 2018-11-02
Thanks to everyone :p

**Pete-br:**

```
meler@Sobremesa:~$  cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-generic root=UUID=1281f556-9692-4e21-9109-d45d9c97394b ro iommu=soft quiet splash vt.handoff=1

```

There is no memory limit.


**Autodave**, **Tadaen_Sylvermane** I'm going to test your ideas. I'll tell you ;)

---

### Post by pete-br on 2018-11-05
Can you post the output from 'cat /proc/meminfo'?

---

### Post by erogarcia on 2018-11-05
**pete-br**:

```
meler@Sobremesa:~$ cat /proc/meminfo
MemTotal:       16382936 kB
MemFree:        11880320 kB
MemAvailable:   13368648 kB
Buffers:           87764 kB
Cached:          1771300 kB
SwapCached:            0 kB
Active:          2925796 kB
Inactive:        1209444 kB
Active(anon):    2277432 kB
Inactive(anon):   159100 kB
Active(file):     648364 kB
Inactive(file):  1050344 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:       2097148 kB
SwapFree:        2097148 kB
Dirty:             15024 kB
Writeback:             0 kB
AnonPages:       2276280 kB
Mapped:           697616 kB
Shmem:            160368 kB
Slab:             147672 kB
SReclaimable:      84568 kB
SUnreclaim:        63104 kB
KernelStack:       14160 kB
PageTables:        50236 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    10288616 kB
Committed_AS:    7463276 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      266492 kB
DirectMap2M:     8079360 kB
DirectMap1G:     8388608 kB

```

---

### Post by slickymaster on 2018-11-05
@erogarcia:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output so it don't looses its formatting.

---

### Post by erogarcia on 2018-11-08
Hi again,

Now I have 4 identical RAM modules, so no problem with dual channel neither slot #X :P 

```

 *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 32GiB
        *-bank:0
             description: DIMM DDR3 Synchronous Unbuffered (Unregistered) 933 MHz (1,1 ns)
             product: KHX1866C10D3/
             vendor: Kingston
             physical id: 0
             serial: 253DA450
             slot: Node0_Dimm0
             size: 8GiB
             width: 64 bits
             clock: 933MHz (1.1ns)
        *-bank:1
             description: DIMM DDR3 Synchronous Unbuffered (Unregistered) 933 MHz (1,1 ns)
             product: KHX1866C10D3/
             vendor: Kingston
             physical id: 1
             serial: 223D4D50
             slot: Node0_Dimm1
             size: 8GiB
             width: 64 bits
             clock: 933MHz (1.1ns)
        *-bank:2
             description: DIMM DDR3 Synchronous Unbuffered (Unregistered) 933 MHz (1,1 ns)
             product: KHX1866C10D3/
             vendor: Kingston
             physical id: 2
             serial: 212EB78C
             slot: Node0_Dimm2
             size: 8GiB
             width: 64 bits
             clock: 933MHz (1.1ns)
        *-bank:3
             description: DIMM DDR3 Synchronous Unbuffered (Unregistered) 933 MHz (1,1 ns)
             product: KHX1866C10D3/
             vendor: Kingston
             physical id: 3
             serial: 242EE697
             slot: Node0_Dimm3
             size: 8GiB
             width: 64 bits
             clock: 933MHz (1.1ns)

```

But for the operative system is the same :cry:

```

root@Sobremesa:/home/meler# free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        2,5G         11G        196M        2,0G         12G
Swap:          2,0G          0B        2,0G

```

Any idea? :confused:

---

### Post by slickymaster on 2018-11-08
@erogarcia:

Once again I had to edit your post to correct the fact that you persist using quote tags in place of code tags. Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output so it don't looses its formatting.

---

