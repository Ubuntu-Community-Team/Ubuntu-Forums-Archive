---
title: "USB system crashes"
date: 2009-10-14
forum: Hardware
---

### Post by lazerousz on 2009-10-14
At seemingly random intervals on both the live cd of 8.04/8.10/9.04/9.10(beta) the usb system will crash taking my mouse with it. Before 9.10 all that the logs would tell me is that the usb port has disconnected, this time I got more information. 

Oct 15 01:04:57 ubuntu kernel: [  762.623479] usb 2-3: USB disconnect, address 2
Oct 15 01:04:57 ubuntu kernel: [  962.248025] INFO: task khubd:26 blocked for more than 120 seconds.
Oct 15 01:04:57 ubuntu kernel: [  962.248030] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 15 01:04:57 ubuntu kernel: [  962.248034] khubd         D c080b3a0     0    26      2 0x00000000
Oct 15 01:04:57 ubuntu kernel: [  962.248042]  f716de30 00000046 fffffff0 c080b3a0 f715a848 c080b3a0 8fe6f6b8 000000b1
Oct 15 01:04:57 ubuntu kernel: [  962.248053]  c080b3a0 c080b3a0 f715a848 c080b3a0 8fe68b62 000000b1 c080b3a0 f4529200
Oct 15 01:04:57 ubuntu kernel: [  962.248064]  f715a5b0 f69f2a80 f716de38 f6984500 f716de54 c040c075 00000000 f715a5b0
Oct 15 01:04:57 ubuntu kernel: [  962.248075] Call Trace:
Oct 15 01:04:57 ubuntu kernel: [  962.248087]  [<c040c075>] usb_kill_urb+0x65/0xa0
Oct 15 01:04:57 ubuntu kernel: [  962.248094]  [<c0157920>] ? autoremove_wake_function+0x0/0x40
Oct 15 01:04:57 ubuntu kernel: [  962.248100]  [<c040acbf>] usb_hcd_flush_endpoint+0xaf/0x100
Oct 15 01:04:57 ubuntu kernel: [  962.248105]  [<c040caf9>] usb_disable_endpoint+0x49/0x80
Oct 15 01:04:57 ubuntu kernel: [  962.248110]  [<c040cb63>] usb_disable_device+0x33/0xf0
Oct 15 01:04:57 ubuntu kernel: [  962.248115]  [<c04077fe>] usb_disconnect+0x9e/0x110
Oct 15 01:04:57 ubuntu kernel: [  962.248121]  [<c0407bac>] hub_port_connect_change+0x7c/0x830
Oct 15 01:04:57 ubuntu kernel: [  962.248125]  [<c040d880>] ? usb_control_msg+0xd0/0x120

I'm not entirely sure what I can/should do with this information, can anyone advise? It didn't seem to happen when I ran the live cd with no-apic and as of yet it doesn't seem to have affected my wubi install, which seems odd.

---

