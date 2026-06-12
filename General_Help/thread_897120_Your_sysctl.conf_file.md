---
title: "Your sysctl.conf file"
date: 2008-08-21
forum: General Help
---

### Post by AndEat on 2008-08-21
What do you put in your sysctl.conf file? I've been gathering bits and pieces over time while running Kubuntu. I'm interested in learning more about tweaking Ubunutu and Linux. I want your opinion and critique as well sharing what you do for improved performance. I'm still learning, any suggestions (especially for how to test how useful a parameter tweak might be) welcome 

```
kernel.maps_protect = 1
kernel.printk = 4 4 1 7
#kernel.shmall = 4194304
#kernel.shmmax = 67108864
#kernel.shmmni = 4096
kernel.threads-max=65536
net.core.netdev_max_backlog=2500
net.core.netdev_max_backlog=3000
net.core.optmem_max=20480
net.core.rmem_max = 16777216
net.core.somaxconn=1024
net.core.wmem_max = 16777216
net.ipv4.conf.all.accept_redirects=0
net.ipv4.conf.all.accept_source_route=0
net.ipv4.conf.all.log_martians=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.conf.all.send_redirects=0
net.ipv4.conf.default.accept_redirects=0
net.ipv4.conf.default.accept_source_route=0
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.default.send_redirects=0
net.ipv4.icmp_echo_ignore_all=1
net.ipv4.icmp_echo_ignore_broadcasts=1
net.ipv4.icmp_ignore_bogus_error_responses=1
net.ipv4.icmp_ratelimit=10
#net.ipv4.ip_default_ttl=62  #[http://gentoo-wiki.com/HOWTO_TCP_Tuning](http://gentoo-wiki.com/HOWTO_TCP_Tuning)  how to get a random number between 60 and 100?
net.ipv4.ip_no_pmtu_disc=0
net.ipv4.route.flush=1
#net.ipv4.tcp_congestion_control=      (only reno is compiled into default kernel)
net.ipv4.tcp_fack=1
net.ipv4.tcp_fin_timeout=30
net.ipv4.tcp_keepalive_time=900
net.ipv4.tcp_max_orphans=16384
net.ipv4.tcp_max_syn_backlog=4096
net.ipv4.tcp_no_metrics_save=1
net.ipv4.tcp_rfc1337=1
et.ipv4.tcp_rmem = 4096 873800 8738000
net.ipv4.tcp_sack=1
net.ipv4.tcp_synack_retries=3
net.ipv4.tcp_syn_retries=3
net.ipv4.tcp_timestamps=0
net.ipv4.tcp_tw_recycle=1
net.ipv4.tcp_tw_reuse=1
net.ipv4.tcp_window_scaling=1
net.ipv4.tcp_wmem = 4096 655360 8738000
net.netfilter.nf_conntrack_tcp_loose=0
vm.dirty_background_ratio=5
vm.dirty_expire_centisecs=500
vm.dirty_ratio=10
vm.dirty_writeback_centisecs=250
vm.min_free_kbytes=102400
vm.swappiness=0
vm.vfs_cache_pressure=40
```

---

### Post by jpeddicord on 2008-08-22
Not a tutorial, moved appropriately.

---

### Post by AndEat on 2008-08-24
[http://www.extremetech.com/article2/0,1697,2114123,00.asp](http://www.extremetech.com/article2/0,1697,2114123,00.asp)

---

