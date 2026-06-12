---
title: "VAIO CR220e - Wireless Problem"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by galttar on 2008-01-25
Hi guys...
First, sorry my poor english, but I need help! :D

I already use Ubuntu on my old computer (VAIO VGN-FS920) and now I buy a VGN-CR220e but my network do not work. :(

With dmesg: Radio disabled by HW RF Kill switch. But rf_kill is 0... it's correct?
On ifconfig and iwconfig no wireless was show.

Any idea to help me?
Thanks.

PCI configuration:

```
$ lspci | grep Wireless

```
> 02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)


```
$ sudo lshw -C network

```
>   *-network               
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:80:3d:98:14
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair


```
% dmesg | grep iwl4965

```
> [   14.040000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   14.040000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   14.040000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   14.176000] iwl4965: Radio disabled by HW RF Kill switch


```
$ sudo tail /sys/bus/pci/drivers/iwl4965/0000\:02\:00.0/rf_kill

```
> 0


```
$ ifconfig
$ iwconfig

```
> eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:1A:80:3D:98:14 
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          IRQ:18

lo         Encapsulamento do Link: Loopback Local 
          inet end.: 127.0.0.1  Masc:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by campbuds on 2008-01-26
I have a vgn-cr220e also and cannot get the webcam to work (or know how to access and use it) and wireless is not working.

What do I do?

---

### Post by campbuds on 2008-01-26
ok, webcam not working, sound not working, (maybe other stuff too) but the wireless is working. Just use release 7.10.

wireless works right out of the box

---

### Post by galttar on 2008-01-26
> **campbuds said:**
> ok, webcam not working, sound not working, (maybe other stuff too) but the wireless is working. Just use release 7.10.

wireless works right out of the box

Hi campbuds.
I'm using 7.10.

---

### Post by galttar on 2008-01-28
No idea about what can I do?

---

### Post by imopen on 2008-02-02
I haven't a Sony Vaio but I have same wireless card. I blacklisted default driver (iwl4965) and I use ndiswrapper (1.51, not the one of latest Ubuntu release, downloaded from web site).

[http://ubuntuforums.org/showthread.php?t=602721](http://ubuntuforums.org/showthread.php?t=602721)

Give it a try.

;)

---

