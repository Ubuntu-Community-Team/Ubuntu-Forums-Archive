---
title: "DMA unavailable Compact Flash Sandisk Ultra II - Ubuntu 7.10"
date: 2008-10-29
forum: General Help
---

### Post by wb0gaz on 2008-10-29
I'm using Ubuntu 7.10 in a small (VIA C3-based) machine with a single 4GB Sandisk Ultra II compact flash card (/dev/hdc on this machine due to it's hardware arrangement) as mass storage device.

My problem/wish for help is this: DMA is not working (even though the machine's BIOS indicates DMA is available on the CF device), so the machine (which is a 500 MHz CPU) is slower than I'd like.

DMA is not enabled per hdparm:

# hdparm /dev/hdc

/dev/hdc:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 7964/16/63, sectors = 8027712, start = 0

/var/log/dmesg shows these errors:

[   34.952000] hdc: dma_timer_expiry: dma status == 0x21
[   44.952000] hdc: DMA timeout error
[   44.952000] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete Dat
aRequest }
[   44.952000] ide: failed opcode was: unknown
[   44.952000] hdc: DMA disabled
[   45.000000] ide1: reset: success
[   45.000000]  hdc1 hdc2 hdc3
[   65.000000] hdc: dma_timer_expiry: dma status == 0x21
[   75.000000] hdc: DMA timeout error
[   75.000000] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete Dat
aRequest }
[   75.000000] ide: failed opcode was: unknown
[   75.000000] hdc: DMA disabled
[   75.048000] ide1: reset: success
[   95.188000] hdc: dma_timer_expiry: dma status == 0x21
[  105.188000] hdc: DMA timeout error
[  105.188000] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete Dat
aRequest }
[  105.188000] ide: failed opcode was: unknown
[  105.188000] hdc: DMA disabled
[  105.236000] ide1: reset: success
[  125.236000] hdc: dma_timer_expiry: dma status == 0x21
[  135.236000] hdc: DMA timeout error
[  135.236000] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete Dat
aRequest }
[  135.236000] ide: failed opcode was: unknown
[  135.236000] hdc: DMA disabled
[  135.284000] ide1: reset: success
[  135.604000] Attempting manual resume
[  135.604000] swsusp: Resume From Partition 22:2
[  135.604000] PM: Checking swsusp image.
[  135.604000] PM: Resume from disk failed.

---

### Post by somnorosul on 2008-12-18
Hope this will be seen by many because there are a lot of threads out there with this proble.
I myself lost a night because of this.
The problem is that all the bootparams that you get on a search for disable dma are for the old ide module of the kernel.
ubuntu uses the new libata module that have diferent parameters.
So to disable udma for an ide device:
look in the dmesg for the device that timeouts (ex. ATA1.00)
edit the file /etc/modprobe.d/options
and "force=1.0:pio4" to the line with libata
then:
sudo update-initramfs -u
and reboot, youre good to go.
for reference:
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg15962.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg15962.html)

---

