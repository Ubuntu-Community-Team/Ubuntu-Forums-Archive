---
title: "Builtin microSD reader stopped working"
date: 2022-07-30
forum: Hardware
---

### Post by samlingsnamn on 2022-07-30
Hi! I have a Lenovo ThinkPad L15 AMD Gen1 since two years back. It has a builtin micro-SD card reader that I use sometimes.

Now it seems to stopped working. Not sure if it's hardware of software error. I have newly added a docking unit to the laptop, but tried boot without the dock with same results.

Running Ubuntu 22.04 (Jammy). Tried upgrade, but running the latest.

Sometimes the SD cards use to be visible when running "df", sometimes in Files, sometimes it use to popup some icon or window (don't remember). But now nothing happens when I put the card in. I have tried with three different SD cards.

This is how it looks when running lspci. Not sure what the reader should look like. Is it missing, or does this looks normal?

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 7
01:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0e)
02:00.1 Serial controller: Realtek Semiconductor Co., Ltd. RTL8111xP UART #1 (rev 0e)
02:00.2 Serial controller: Realtek Semiconductor Co., Ltd. RTL8111xP UART #2 (rev 0e)
02:00.3 IPMI Interface: Realtek Semiconductor Co., Ltd. RTL8111xP IPMI interface (rev 0e)
02:00.4 USB controller: Realtek Semiconductor Co., Ltd. RTL811x EHCI host controller (rev 0e)
03:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Renoir (rev d1)
06:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller
06:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
06:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
06:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
06:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 01)
06:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
$

```

Please advise!

---

### Post by sudodus on 2022-07-30
- Try in the UEFI/BIOS menu system, if it can see a microSD card, that is inserted at boot.

- Try with lsblk in a terminal window that is wide enough,
```

lsblk -o name,size,fstype,label,mountpoint,model

```

Probably at least one of the three cards is good enough to work, but it can be both a hardware and software problem. You can test the cards

- in another computer
- with another operating system, for example Ubuntu live booted from a USB pendrive or Windows or MacOS.
- connected via a USB adapter (instead of the built-in slot). Maybe you can borrow such an adapter.

---

### Post by samlingsnamn on 2022-07-30
Thanks for quick answer. Here is the output. I'll try to see if I can see the card in BIOS now.

```
# lsblk -o name,size,fstype,label,mountpoint,model                                                                                                              
NAME                                            SIZE FSTYPE      LABEL MOUNTPOINT                   MODEL                                                                     
loop0                                             4K squashfs          /snap/bare/5                                                                                           
loop1                                         133,2M squashfs          /snap/chromium/2020                                                                                    
loop2                                         133,3M squashfs          /snap/chromium/2036                                                                                    
loop3                                          55,5M squashfs          /snap/core18/2409                                                                                      
loop4                                          55,6M squashfs          /snap/core18/2538                                                                                      
loop5                                            62M squashfs          /snap/core20/1581                                                                                      
loop6                                            62M squashfs          /snap/core20/1587                                                                                      
loop7                                         161,5M squashfs          /snap/firefox/1551           
loop8                                         162,9M squashfs          /snap/gnome-3-28-1804/145    
loop9                                         164,8M squashfs          /snap/gnome-3-28-1804/161    
loop10                                        254,1M squashfs          /snap/gnome-3-38-2004/106    
loop11                                        400,8M squashfs          /snap/gnome-3-38-2004/112    
loop12                                         81,3M squashfs          /snap/gtk-common-themes/1534 
loop13                                           47M squashfs          /snap/snapd/16010            
loop14                                           47M squashfs          /snap/snapd/16292            
loop15                                         91,7M squashfs          /snap/gtk-common-themes/1535 
loop16                                        163,3M squashfs          /snap/firefox/1589           
nvme0n1                                       476,9G                                                SAMSUNG MZVLB512HCJN-000L7
&#9500;&#9472;nvme0n1p1                                     300M vfat              /boot/efi                    
&#9492;&#9472;nvme0n1p2                                   476,6G crypto_LUKS                                    
  &#9492;&#9472;luks-7a060182-78af-5f59-b8b5-16f4915dcf8b 476,6G ext4              /     
#
```

---

### Post by samlingsnamn on 2022-07-30
Hello again!
I couldn't find anything relevant in the BIOS, but then I booted up again I discovered something!

If the microSD card is inserted during boot, it will find the card and I can access it! In the lsblk this lines is added:
```

mmcblk0                                       179:0    0 238,3G  0 disk  
&#9492;&#9472;mmcblk0p1                                   179:1    0 238,3G  0 part  /media/samlingsnamn/NIKON D750
```

I also found it in the Files application. I then removed the card, clicked on the disk (that was still there in Files) and it seems that Files crashed.
Then I tried to insert the card again, but it doesn't get automounted, and the two lines in lsblk iis not there any more.

Tried to reboot, and the card is visible again. But when removed, it doesn't mount again.

What is wrong?

---

### Post by sudodus on 2022-07-30
It seems to me that **the hardware driver for your card reader is flaky**. If I understand correctly it used to work, so probably some upgrade (maybe kernel upgrade) brought a driver, that does not work well with your card reader. The problem might also be some other software component.

You can test with Ubuntu 22.04 LTS live (booted from USB or from a memory card), or try with Ubuntu 20.04.4 LTS, which is well polished and debugged by now. It might also work better, if you connect via a USB adapter (for cards).

**Edit:** When adding code to a post here, please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

