---
title: "Bluetooth not working on 20.04.3 LTS on ASUS TUG Gaming F17 laptop ?"
date: 2022-01-13
forum: Hardware
---

### Post by gigi1335 on 2022-01-13
My bluetooth doesn't seem to work on 20.04.3 LTS on ASUS TUG Gaming F17 laptop.

I can't activate it in Parameters/Bluetooth window.


Here are some debug but I can't see what is the problem. Can you help me, please ?


Thanks in advance for your help.


Gilles



------------------


```
$ systemctl status bluetooth

&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Thu 2022-01-13 07:07:10 CET; 13h ago
       Docs: man:bluetoothd(8)
   Main PID: 803 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 38140)
     Memory: 1.6M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;803 /usr/lib/bluetooth/bluetoothd

janv. 13 07:07:10 S17 systemd[1]: Starting Bluetooth service...
janv. 13 07:07:10 S17 bluetoothd[803]: Bluetooth daemon 5.53
janv. 13 07:07:10 S17 systemd[1]: Started Bluetooth service.
janv. 13 07:07:10 S17 bluetoothd[803]: Starting SDP server
janv. 13 07:07:10 S17 bluetoothd[803]: Bluetooth management interface 1.19 init

```

------------------



```
$ sudo bluetoothctl

Agent registered
[bluetooth]# show
No default controller available

```

------------------




```
$ sudo lshw -C network
  *-network NON-RÉCLAMÉ     
       description: Network controller
       produit: MEDIATEK Corp.
       fabricant: MEDIATEK Corp.
       identifiant matériel: 0
       information bus: pci@0000:2d:00.0
       version: 00
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pciexpress msi pm cap_list
       configuration : latency=0
       ressources : mémoireE/S:620-61f mémoireE/S:620-61f mémoireE/S:620-61f mémoire:622c100000-622c1fffff mémoire:622c200000-622c203fff mémoire:622c204000-622c204fff
  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:2e:00.0
       nom logique: enp46s0
       version: 15
       numéro de série: 50:eb:f6:4c:a1:a3
       taille: 1Gbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration : autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-46-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       ressources : irq:18 portE/S:3000(taille=256) mémoire:86204000-86204fff mémoire:86200000-86203fff




```------------------



```
$ sudo dmesg | grep -i blue

[    2.340860] Bluetooth: Core ver 2.22
[    2.340873] Bluetooth: HCI device and connection manager initialized
[    2.340875] Bluetooth: HCI socket layer initialized
[    2.340876] Bluetooth: L2CAP socket layer initialized
[    2.340878] Bluetooth: SCO socket layer initialized
[    3.417553] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.417555] Bluetooth: BNEP filters: protocol multicast
[    3.417558] Bluetooth: BNEP socket layer initialized


```

---

