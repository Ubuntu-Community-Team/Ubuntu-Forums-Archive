---
title: "USB disk spins up every 1800 seconds / 30 minutes"
date: 2013-01-20
forum: Hardware
---

### Post by pivert on 2013-01-20
I have an USB hard disk used once a week for backups. [COLOR="Red"]It's not mounted.[/COLOR]
I set it up to spin down after 1 minute inactivity with hdparm.
But every 1800 seconds, it Spins Up with the following line in dmesg:
usb 2-4: reset high-speed USB device number 5 using ehci_hcd

If I enable verbose logging with
echo 1 > /proc/sys/vm/block_dump
I do not have more clue. All other lines are not related to this unmounted device.

```

root@homer:~# grep ".*USB.*" -C5 --color /var/log/kern.log
Jan 20 08:26:26 homer kernel: [2402038.343618] kvm(28212): WRITE block 85852352 on dm-0 (8 sectors)
Jan 20 08:26:26 homer kernel: [2402038.480039] md1_raid1(235): WRITE block 58588800 on sda1 (8 sectors)
Jan 20 08:26:26 homer kernel: [2402038.480096] md1_raid1(235): WRITE block 58588800 on sdb1 (8 sectors)
Jan 20 08:26:26 homer kernel: [2402038.556038] md6_raid1(243): WRITE block 1892810112 on sda6 (8 sectors)
Jan 20 08:26:26 homer kernel: [2402038.556101] md6_raid1(243): WRITE block 1892810112 on sdb6 (8 sectors)
[COLOR="Red"]Jan 20 08:26:27 homer kernel: [2402038.928026] usb 2-4: reset high-speed USB device number 5 using ehci_hcd[/COLOR]
Jan 20 08:26:27 homer kernel: [2402039.170138] kvm(28212): WRITE block 144239776 on dm-0 (8 sectors)
Jan 20 08:26:27 homer kernel: [2402039.170185] md6_raid1(243): WRITE block 1892810112 on sda6 (8 sectors)
Jan 20 08:26:27 homer kernel: [2402039.170244] md6_raid1(243): WRITE block 1892810112 on sdb6 (8 sectors)
Jan 20 08:26:27 homer kernel: [2402039.212582] kvm(28218): WRITE block 85852360 on dm-0 (8 sectors)
Jan 20 08:26:27 homer kernel: [2402039.212596] kvm(28218): WRITE block 85852368 on dm-0 (8 sectors)
--
Jan 20 08:56:26 homer kernel: [2403838.271330] kvm(29496): WRITE block 85890952 on dm-0 (8 sectors)
Jan 20 08:56:26 homer kernel: [2403838.271337] kvm(29496): WRITE block 85890960 on dm-0 (8 sectors)
Jan 20 08:56:26 homer kernel: [2403838.334477] kvm(29497): WRITE block 85890968 on dm-0 (8 sectors)
Jan 20 08:56:26 homer kernel: [2403838.556032] md6_raid1(243): WRITE block 1892810112 on sda6 (8 sectors)
Jan 20 08:56:26 homer kernel: [2403838.556099] md6_raid1(243): WRITE block 1892810112 on sdb6 (8 sectors)
[COLOR="Red"]Jan 20 08:56:27 homer kernel: [2403838.896034] usb 2-4: reset high-speed USB device number 5 using ehci_hcd[/COLOR]
Jan 20 08:56:28 homer kernel: [2403840.037222] kvm(29490): WRITE block 142171712 on dm-0 (8 sectors)
Jan 20 08:56:28 homer kernel: [2403840.037255] md6_raid1(243): WRITE block 1892810112 on sda6 (8 sectors)
Jan 20 08:56:28 homer kernel: [2403840.037317] md6_raid1(243): WRITE block 1892810112 on sdb6 (8 sectors)
Jan 20 08:56:28 homer kernel: [2403840.078421] kvm(29496): WRITE block 90367584 on dm-0 (8 sectors)
Jan 20 08:56:28 homer kernel: [2403840.078428] kvm(29482): WRITE block 142398864 on dm-0 (8 sectors)
--
Jan 20 09:26:26 homer kernel: [2405638.800073] md1_raid1(235): WRITE block 58588800 on sda1 (8 sectors)
Jan 20 09:26:26 homer kernel: [2405638.800133] md1_raid1(235): WRITE block 58588800 on sdb1 (8 sectors)
Jan 20 09:26:26 homer kernel: [2405638.820526] jbd2/md1-8(373): WRITE block 25445552 on md1 (8 sectors)
Jan 20 09:26:26 homer kernel: [2405638.820533] jbd2/md1-8(373): WRITE block 25445560 on md1 (8 sectors)
Jan 20 09:26:26 homer kernel: [2405638.820817] jbd2/md1-8(373): WRITE block 25445568 on md1 (8 sectors)
[COLOR="Red"]Jan 20 09:26:27 homer kernel: [2405638.896021] usb 2-4: reset high-speed USB device number 5 using ehci_hcd[/COLOR]
Jan 20 09:26:27 homer kernel: [2405639.052036] md1_raid1(235): WRITE block 58588800 on sda1 (8 sectors)
Jan 20 09:26:27 homer kernel: [2405639.052098] md1_raid1(235): WRITE block 58588800 on sdb1 (8 sectors)
Jan 20 09:26:28 homer kernel: [2405640.277000] kvm(30785): WRITE block 116068048 on dm-0 (8 sectors)
Jan 20 09:26:28 homer kernel: [2405640.277040] md6_raid1(243): WRITE block 1892810112 on sda6 (8 sectors)
Jan 20 09:26:28 homer kernel: [2405640.277069] kvm(30798): WRITE block 142360608 on dm-0 (8 sectors)
root@homer:~# 

```

How can I fix this problem? It's just making noise, using electricity and reduce the life of the disk, every 30 minutes.

Thanks,

---

