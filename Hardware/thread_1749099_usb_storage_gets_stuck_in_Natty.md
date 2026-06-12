---
title: "usb_storage gets stuck in Natty"
date: 2011-05-04
forum: Hardware
---

### Post by Tuminoid on 2011-05-04
After a while, USB (usb_storage) gets stuck in Natty. KB and mouse work, but not much else.

lsusb gets stuck too (not responding to ctrl-z, d, z either)

rmmod usb_storage stucks as well.

Any pointers for help, rebooting once an hour to get USB thingies to work is not exactly something I will do.

dmesg has:
```

[ 6001.120249] INFO: task usb-storage:9650 blocked for more than 120 seconds.
[ 6001.120252] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 6001.120255] usb-storage     D 00ea196c     0  9650      2 0x00000000
[ 6001.120261]  c3c1fd9c 00000046 f5086904 00ea196c eeea1c3c 00000000 eeea1bcc c183a8c0
[ 6001.120269]  516e57ca 000004e5 eeea1bc8 c183a8c0 c183a8c0 f50068c0 eeea1940 eec26500
[ 6001.120278]  c1110ee0 00000000 c3c1fd84 eeea1940 dce6b25c 000004e4 eeea1bc8 c183a8c0
[ 6001.120287] Call Trace:
[ 6001.120293]  [<c1110ee0>] ? dma_pool_alloc+0xf0/0x120
[ 6001.120298]  [<c13b6fd5>] ? ehci_qtd_alloc.clone.59+0x15/0x60
[ 6001.120303]  [<c150802d>] schedule_timeout+0x1ed/0x260
[ 6001.120308]  [<c13bc054>] ? submit_async.clone.60+0x84/0xd0
[ 6001.120313]  [<c13bc251>] ? ehci_urb_enqueue+0x81/0xf0
[ 6001.120317]  [<c1507bb0>] wait_for_common+0xa0/0x130
[ 6001.120321]  [<c13a6657>] ? usb_alloc_urb+0x17/0x40
[ 6001.120325]  [<c104a060>] ? default_wake_function+0x0/0x20
[ 6001.120330]  [<c1507d17>] wait_for_completion+0x17/0x20
[ 6001.120334]  [<c13a77b2>] usb_sg_wait+0x102/0x1b0
[ 6001.120341]  [<f84870d7>] usb_stor_bulk_transfer_sglist+0x87/0xf0 [usb_storage]
[ 6001.120347]  [<f848716f>] usb_stor_bulk_srb+0x2f/0x50 [usb_storage]
[ 6001.120353]  [<f848731b>] usb_stor_Bulk_transport+0xfb/0x300 [usb_storage]
[ 6001.120360]  [<f8487cd9>] usb_stor_invoke_transport+0x29/0x380 [usb_storage]
[ 6001.120364]  [<c1049ec3>] ? try_to_wake_up+0x223/0x3c0
[ 6001.120369]  [<c1509918>] ? _raw_spin_lock_irq+0x18/0x20
[ 6001.120374]  [<c1507bff>] ? wait_for_common+0xef/0x130
[ 6001.120379]  [<c1056836>] ? raise_softirq_irqoff+0x36/0x70
[ 6001.120384]  [<c104a060>] ? default_wake_function+0x0/0x20
[ 6001.120390]  [<f8486c5d>] usb_stor_transparent_scsi_command+0xd/0x10 [usb_storage]
[ 6001.120396]  [<f8488c99>] usb_stor_control_thread+0x139/0x210 [usb_storage]
[ 6001.120401]  [<c1038d2e>] ? complete+0x4e/0x60
[ 6001.120407]  [<f8488b60>] ? usb_stor_control_thread+0x0/0x210 [usb_storage]
[ 6001.120412]  [<c106ce04>] kthread+0x74/0x80
[ 6001.120416]  [<c106cd90>] ? kthread+0x0/0x80
[ 6001.120421]  [<c100367e>] kernel_thread_helper+0x6/0x10

```

---

### Post by Tuminoid on 2011-05-23
2.6.39-rc4 has this issue as well, now trying 2.6.39-rc7. Stayed up over weekend, will report back in a week at latest.

---

