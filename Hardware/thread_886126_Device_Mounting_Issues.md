---
title: "Device Mounting Issues"
date: 2008-08-10
forum: Hardware
---

### Post by david_boring on 2008-08-10
I've been running Ubuntu about 4 weeks now and have had no problems with my external hard drive (WD My Book, 500GB) or my media player (Toshiba Gigabeat S) until last week. Out of nowhere, they were no longer recognized, didn't show up in the Places directory, didn't pop up on the Desktop, and didn't seem to respond as if they were connected.

Any ideas? Thanks.

---

### Post by Yellow Pasque on 2008-08-10
Plug in the drive and check for errors with:
```
dmesg
```

---

### Post by david_boring on 2008-08-11
> **Temüjin said:**
> Plug in the drive and check for errors with:
```
dmesg
```

After running dmesg with my Gigabeat plugged in, this comes up (I have no idea what it might be or if there are errors):

```
[   50.981613]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[   50.981632]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   50.981652]  [<c0131d72>] __do_softirq+0x82/0x110
[   50.981663]  [<c0131e55>] do_softirq+0x55/0x60
[   50.981668]  [<c013213d>] irq_exit+0x6d/0x80
[   50.981671]  [<c0106f20>] do_IRQ+0x40/0x70
[   50.981678]  [<c0131808>] sys_gettimeofday+0x28/0x80
[   50.981686]  [<c0105413>] common_interrupt+0x23/0x30
[   50.981708]  =======================
[   51.235950] ieee80211_unref_node: NULL ieee80211_node *
[   51.235960] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   51.235980]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   51.236021]  [<c028fed0>] mousedev_event+0x0/0x4a0
[   51.236038]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   51.236057]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   51.236088]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   51.236113]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   51.236132]  [<f88ea613>] finish_urb+0x63/0xc0 [ohci_hcd]
[   51.236144]  [<f88ea72b>] takeback_td+0xbb/0xd0 [ohci_hcd]
[   51.236155]  [<f88ea822>] dl_done_list+0xe2/0x160 [ohci_hcd]
[   51.236186]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   51.236194]  [<c0131d72>] __do_softirq+0x82/0x110
[   51.236205]  [<c0131e55>] do_softirq+0x55/0x60
[   51.236209]  [<c013213d>] irq_exit+0x6d/0x80
[   51.236213]  [<c0106f20>] do_IRQ+0x40/0x70
[   51.236224]  [<c0105413>] common_interrupt+0x23/0x30
[   51.236229]  [<c0102f40>] default_idle+0x0/0x60
[   51.236241]  [<c011ec62>] native_safe_halt+0x2/0x10
[   51.236248]  [<c0102f7c>] default_idle+0x3c/0x60
[   51.236251]  [<c0102695>] cpu_idle+0x45/0xd0
[   51.236257]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   51.236262]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   51.236275]  =======================
[   57.851673] ieee80211_unref_node: NULL ieee80211_node *
[   57.851683] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   57.851704]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   57.851732]  [<c013833a>] group_send_sig_info+0x5a/0x80
[   57.851746]  [<c010aec3>] sched_clock+0x13/0x40
[   57.851759]  [<c010aec3>] sched_clock+0x13/0x40
[   57.851766]  [<c0122796>] __update_rq_clock+0x26/0x170
[   57.851778]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   57.851809]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   57.851834]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   57.851852]  [<c0149b2a>] tick_do_periodic_broadcast+0x1a/0x30
[   57.851856]  [<c0149b4d>] tick_handle_periodic_broadcast+0xd/0x50
[   57.851865]  [<c0107b7d>] timer_interrupt+0x2d/0x80
[   57.851870]  [<c01686b0>] handle_IRQ_event+0x30/0x60
[   57.851877]  [<c0118ddc>] ack_apic+0xc/0x10
[   57.851880]  [<c0169e5c>] handle_fasteoi_irq+0x9c/0xe0
[   57.851889]  [<c0106f20>] do_IRQ+0x40/0x70
[   57.851910]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   57.851917]  [<c0131d72>] __do_softirq+0x82/0x110
[   57.851927]  [<c0131e55>] do_softirq+0x55/0x60
[   57.851932]  [<c013213d>] irq_exit+0x6d/0x80
[   57.851935]  [<c0106f20>] do_IRQ+0x40/0x70
[   57.851946]  [<c0105413>] common_interrupt+0x23/0x30
[   57.851951]  [<c0102f40>] default_idle+0x0/0x60
[   57.851963]  [<c011ec62>] native_safe_halt+0x2/0x10
[   57.851969]  [<c0102f7c>] default_idle+0x3c/0x60
[   57.851972]  [<c0102695>] cpu_idle+0x45/0xd0
[   57.851978]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   57.851983]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   57.851996]  =======================
[   61.258924] ieee80211_unref_node: NULL ieee80211_node *
[   61.258935] Pid: 5612, comm: Xorg Tainted: P        2.6.24-19-generic #1
[   61.258957]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   61.259006]  [<c012404e>] __wake_up+0x3e/0x60
[   61.259021]  [<f8a9695b>] snd_timer_user_tinterrupt+0x16b/0x1a0 [snd_timer]
[   61.259035]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   61.259066]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   61.259091]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   61.259113]  [<f8bb8eee>] azx_interrupt+0x9e/0xf0 [snd_hda_intel]
[   61.259140]  [<c0119c97>] ack_ioapic_quirk_irq+0x47/0xb0
[   61.259150]  [<c0169e5c>] handle_fasteoi_irq+0x9c/0xe0
[   61.259160]  [<c0106f20>] do_IRQ+0x40/0x70
[   61.259182]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   61.259189]  [<c0131d72>] __do_softirq+0x82/0x110
[   61.259200]  [<c0131e55>] do_softirq+0x55/0x60
[   61.259204]  [<c013213d>] irq_exit+0x6d/0x80
[   61.259207]  [<c0106f20>] do_IRQ+0x40/0x70
[   61.259210]  [<c0192881>] sys_read+0x41/0x70
[   61.259221]  [<c0105413>] common_interrupt+0x23/0x30
[   61.259243]  =======================
[   62.045797] ieee80211_unref_node: NULL ieee80211_node *
[   62.045807] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   62.045828]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   62.045878]  [<c013833a>] group_send_sig_info+0x5a/0x80
[   62.045909]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   62.045925]  [<c0122767>] enqueue_task_fair+0x27/0x30
[   62.045933]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   62.045964]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   62.045990]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   62.046016]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   62.046026]  [<c01260b3>] rebalance_domains+0x163/0x440
[   62.046054]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   62.046061]  [<c0131d72>] __do_softirq+0x82/0x110
[   62.046072]  [<c0131e55>] do_softirq+0x55/0x60
[   62.046076]  [<c013213d>] irq_exit+0x6d/0x80
[   62.046079]  [<c0106f20>] do_IRQ+0x40/0x70
[   62.046091]  [<c0105413>] common_interrupt+0x23/0x30
[   62.046096]  [<c0102f40>] default_idle+0x0/0x60
[   62.046109]  [<c011ec62>] native_safe_halt+0x2/0x10
[   62.046116]  [<c0102f7c>] default_idle+0x3c/0x60
[   62.046118]  [<c0102695>] cpu_idle+0x45/0xd0
[   62.046125]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   62.046131]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   62.046145]  =======================
[   66.384357] ieee80211_unref_node: NULL ieee80211_node *
[   66.384366] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   66.384384]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   66.384414]  [<c013833a>] group_send_sig_info+0x5a/0x80
[   66.384441]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   66.384460]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   66.384489]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   66.384514]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   66.384540]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   66.384546]  [<c0128bb7>] scheduler_tick+0xf7/0x210
[   66.384576]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   66.384583]  [<c0131d72>] __do_softirq+0x82/0x110
[   66.384594]  [<c0131e55>] do_softirq+0x55/0x60
[   66.384598]  [<c013213d>] irq_exit+0x6d/0x80
[   66.384602]  [<c0106f20>] do_IRQ+0x40/0x70
[   66.384613]  [<c0105413>] common_interrupt+0x23/0x30
[   66.384618]  [<c0102f40>] default_idle+0x0/0x60
[   66.384630]  [<c011ec62>] native_safe_halt+0x2/0x10
[   66.384637]  [<c0102f7c>] default_idle+0x3c/0x60
[   66.384640]  [<c0102695>] cpu_idle+0x45/0xd0
[   66.384646]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   66.384652]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   66.384665]  =======================
[   66.901457] ieee80211_unref_node: NULL ieee80211_node *
[   66.901467] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   66.901487]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   66.901516]  [<c013833a>] group_send_sig_info+0x5a/0x80
[   66.901544]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   66.901563]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   66.901594]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   66.901619]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   66.901645]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   66.901652]  [<c0128bb7>] scheduler_tick+0xf7/0x210
[   66.901681]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   66.901689]  [<c0131d72>] __do_softirq+0x82/0x110
[   66.901699]  [<c0131e55>] do_softirq+0x55/0x60
[   66.901704]  [<c013213d>] irq_exit+0x6d/0x80
[   66.901707]  [<c0106f20>] do_IRQ+0x40/0x70
[   66.901718]  [<c0105413>] common_interrupt+0x23/0x30
[   66.901723]  [<c0102f40>] default_idle+0x0/0x60
[   66.901735]  [<c011ec62>] native_safe_halt+0x2/0x10
[   66.901742]  [<c0102f7c>] default_idle+0x3c/0x60
[   66.901745]  [<c0102695>] cpu_idle+0x45/0xd0
[   66.901751]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   66.901757]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   66.901770]  =======================
[   67.418602] ieee80211_unref_node: NULL ieee80211_node *
[   67.418611] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   67.418631]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   67.418661]  [<c013833a>] group_send_sig_info+0x5a/0x80
[   67.418690]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   67.418709]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   67.418741]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   67.418766]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   67.418796]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   67.418803]  [<c0128bb7>] scheduler_tick+0xf7/0x210
[   67.418833]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   67.418841]  [<c0131d72>] __do_softirq+0x82/0x110
[   67.418851]  [<c0131e55>] do_softirq+0x55/0x60
[   67.418856]  [<c013213d>] irq_exit+0x6d/0x80
[   67.418859]  [<c0106f20>] do_IRQ+0x40/0x70
[   67.418870]  [<c0105413>] common_interrupt+0x23/0x30
[   67.418875]  [<c0102f40>] default_idle+0x0/0x60
[   67.418888]  [<c011ec62>] native_safe_halt+0x2/0x10
[   67.418895]  [<c0102f7c>] default_idle+0x3c/0x60
[   67.418898]  [<c0102695>] cpu_idle+0x45/0xd0
[   67.418904]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   67.418909]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   67.418922]  =======================
[   72.476419] ieee80211_unref_node: NULL ieee80211_node *
[   72.476429] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   72.476449]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   72.476492]  [<c028fed0>] mousedev_event+0x0/0x4a0
[   72.476510]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   72.476529]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   72.476560]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   72.476586]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   72.476613]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   72.476623]  [<c01260b3>] rebalance_domains+0x163/0x440
[   72.476650]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   72.476658]  [<c0131d72>] __do_softirq+0x82/0x110
[   72.476668]  [<c0131e55>] do_softirq+0x55/0x60
[   72.476673]  [<c013213d>] irq_exit+0x6d/0x80
[   72.476677]  [<c0106f20>] do_IRQ+0x40/0x70
[   72.476689]  [<c0105413>] common_interrupt+0x23/0x30
[   72.476693]  [<c0102f40>] default_idle+0x0/0x60
[   72.476706]  [<c011ec62>] native_safe_halt+0x2/0x10
[   72.476713]  [<c0102f7c>] default_idle+0x3c/0x60
[   72.476716]  [<c0102695>] cpu_idle+0x45/0xd0
[   72.476723]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   72.476728]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   72.476742]  =======================
[   73.430035] ieee80211_unref_node: NULL ieee80211_node *
[   73.430044] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   73.430063]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   73.430105]  [<c028fed0>] mousedev_event+0x0/0x4a0
[   73.430121]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   73.430140]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   73.430170]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   73.430196]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   73.430221]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   73.430231]  [<c01260b3>] rebalance_domains+0x163/0x440
[   73.430257]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   73.430265]  [<c0131d72>] __do_softirq+0x82/0x110
[   73.430275]  [<c0131e55>] do_softirq+0x55/0x60
[   73.430280]  [<c013213d>] irq_exit+0x6d/0x80
[   73.430283]  [<c0106f20>] do_IRQ+0x40/0x70
[   73.430294]  [<c0105413>] common_interrupt+0x23/0x30
[   73.430299]  [<c0102f40>] default_idle+0x0/0x60
[   73.430311]  [<c011ec62>] native_safe_halt+0x2/0x10
[   73.430318]  [<c0102f7c>] default_idle+0x3c/0x60
[   73.430321]  [<c0102695>] cpu_idle+0x45/0xd0
[   73.430327]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   73.430332]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   73.430346]  =======================
[   75.024394] ieee80211_unref_node: NULL ieee80211_node *
[   75.024403] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   75.024423]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   75.024464]  [<c028fed0>] mousedev_event+0x0/0x4a0
[   75.024481]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   75.024500]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   75.024531]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   75.024557]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   75.024582]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   75.024592]  [<c01260b3>] rebalance_domains+0x163/0x440
[   75.024618]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   75.024626]  [<c0131d72>] __do_softirq+0x82/0x110
[   75.024636]  [<c0131e55>] do_softirq+0x55/0x60
[   75.024641]  [<c013213d>] irq_exit+0x6d/0x80
[   75.024644]  [<c0106f20>] do_IRQ+0x40/0x70
[   75.024655]  [<c0105413>] common_interrupt+0x23/0x30
[   75.024660]  [<c0102f40>] default_idle+0x0/0x60
[   75.024672]  [<c011ec62>] native_safe_halt+0x2/0x10
[   75.024679]  [<c0102f7c>] default_idle+0x3c/0x60
[   75.024682]  [<c0102695>] cpu_idle+0x45/0xd0
[   75.024689]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   75.024708]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   75.024721]  =======================
[   75.369126] ieee80211_unref_node: NULL ieee80211_node *
[   75.369136] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   75.369156]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   75.369209]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   75.369228]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   75.369259]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   75.369284]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   75.369309]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   75.369317]  [<c0128bb7>] scheduler_tick+0xf7/0x210
[   75.369347]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   75.369354]  [<c0131d72>] __do_softirq+0x82/0x110
[   75.369365]  [<c0131e55>] do_softirq+0x55/0x60
[   75.369370]  [<c013213d>] irq_exit+0x6d/0x80
[   75.369373]  [<c0106f20>] do_IRQ+0x40/0x70
[   75.369384]  [<c0105413>] common_interrupt+0x23/0x30
[   75.369389]  [<c0102f40>] default_idle+0x0/0x60
[   75.369402]  [<c011ec62>] native_safe_halt+0x2/0x10
[   75.369409]  [<c0102f7c>] default_idle+0x3c/0x60
[   75.369412]  [<c0102695>] cpu_idle+0x45/0xd0
[   75.369418]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   75.369423]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   75.369437]  =======================
[   75.627670] ieee80211_unref_node: NULL ieee80211_node *
[   75.627679] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   75.627699]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   75.627740]  [<c028fed0>] mousedev_event+0x0/0x4a0
[   75.627757]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   75.627772]  [<c0122767>] enqueue_task_fair+0x27/0x30
[   75.627779]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   75.627809]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   75.627835]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   75.627860]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   75.627870]  [<c01260b3>] rebalance_domains+0x163/0x440
[   75.627896]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   75.627903]  [<c0131d72>] __do_softirq+0x82/0x110
[   75.627914]  [<c0131e55>] do_softirq+0x55/0x60
[   75.627919]  [<c013213d>] irq_exit+0x6d/0x80
[   75.627922]  [<c0106f20>] do_IRQ+0x40/0x70
[   75.627934]  [<c0105413>] common_interrupt+0x23/0x30
[   75.627938]  [<c0102f40>] default_idle+0x0/0x60
[   75.627951]  [<c011ec62>] native_safe_halt+0x2/0x10
[   75.627958]  [<c0102f7c>] default_idle+0x3c/0x60
[   75.627960]  [<c0102695>] cpu_idle+0x45/0xd0
[   75.627967]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   75.627972]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   75.627985]  =======================
[   82.581887] ieee80211_unref_node: NULL ieee80211_node *
[   82.581896] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[   82.581917]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[   82.581970]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[   82.581986]  [<c0122767>] enqueue_task_fair+0x27/0x30
[   82.581995]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[   82.582026]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[   82.582051]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[   82.582077]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[   82.582086]  [<c01260b3>] rebalance_domains+0x163/0x440
[   82.582112]  [<c01322cd>] tasklet_action+0x4d/0xc0
[   82.582119]  [<c0131d72>] __do_softirq+0x82/0x110
[   82.582130]  [<c0131e55>] do_softirq+0x55/0x60
[   82.582135]  [<c013213d>] irq_exit+0x6d/0x80
[   82.582138]  [<c0106f20>] do_IRQ+0x40/0x70
[   82.582149]  [<c0105413>] common_interrupt+0x23/0x30
[   82.582154]  [<c0102f40>] default_idle+0x0/0x60
[   82.582166]  [<c011ec62>] native_safe_halt+0x2/0x10
[   82.582173]  [<c0102f7c>] default_idle+0x3c/0x60
[   82.582176]  [<c0102695>] cpu_idle+0x45/0xd0
[   82.582183]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[   82.582188]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[   82.582202]  =======================
[  103.293873] ieee80211_unref_node: NULL ieee80211_node *
[  103.293882] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  103.293902]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  103.293943]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  103.293960]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  103.293979]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  103.294010]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  103.294035]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  103.294061]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[  103.294071]  [<c01260b3>] rebalance_domains+0x163/0x440
[  103.294098]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  103.294105]  [<c0131d72>] __do_softirq+0x82/0x110
[  103.294116]  [<c0131e55>] do_softirq+0x55/0x60
[  103.294121]  [<c013213d>] irq_exit+0x6d/0x80
[  103.294124]  [<c0106f20>] do_IRQ+0x40/0x70
[  103.294135]  [<c0105413>] common_interrupt+0x23/0x30
[  103.294140]  [<c0102f40>] default_idle+0x0/0x60
[  103.294153]  [<c011ec62>] native_safe_halt+0x2/0x10
[  103.294159]  [<c0102f7c>] default_idle+0x3c/0x60
[  103.294162]  [<c0102695>] cpu_idle+0x45/0xd0
[  103.294168]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  103.294173]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  103.294187]  =======================
[  126.230655] ieee80211_unref_node: NULL ieee80211_node *
[  126.230665] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  126.230687]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  126.230742]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  126.230762]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  126.230793]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  126.230819]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  126.230845]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[  126.230857]  [<c01260b3>] rebalance_domains+0x163/0x440
[  126.230885]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  126.230892]  [<c0131d72>] __do_softirq+0x82/0x110
[  126.230904]  [<c0131e55>] do_softirq+0x55/0x60
[  126.230909]  [<c013213d>] irq_exit+0x6d/0x80
[  126.230912]  [<c0106f20>] do_IRQ+0x40/0x70
[  126.230923]  [<c0105413>] common_interrupt+0x23/0x30
[  126.230928]  [<c0102f40>] default_idle+0x0/0x60
[  126.230941]  [<c011ec62>] native_safe_halt+0x2/0x10
[  126.230948]  [<c0102f7c>] default_idle+0x3c/0x60
[  126.230951]  [<c0102695>] cpu_idle+0x45/0xd0
[  126.230957]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  126.230963]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  126.230977]  =======================
[  127.906545] usb 6-8: new high speed USB device using ehci_hcd and address 6
[  128.100384] usb 6-8: configuration #1 chosen from 1 choice
[  133.927637] ieee80211_unref_node: NULL ieee80211_node *
[  133.927647] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  133.927668]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  133.927710]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  133.927728]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  133.927748]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  133.927794]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  133.927819]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  133.927844]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[  133.927856]  [<c01260b3>] rebalance_domains+0x163/0x440
[  133.927882]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  133.927890]  [<c0131d72>] __do_softirq+0x82/0x110
[  133.927901]  [<c0131e55>] do_softirq+0x55/0x60
[  133.927905]  [<c013213d>] irq_exit+0x6d/0x80
[  133.927908]  [<c0106f20>] do_IRQ+0x40/0x70
[  133.927920]  [<c0105413>] common_interrupt+0x23/0x30
[  133.927925]  [<c0102f40>] default_idle+0x0/0x60
[  133.927937]  [<c011ec62>] native_safe_halt+0x2/0x10
[  133.927944]  [<c0102f7c>] default_idle+0x3c/0x60
[  133.927946]  [<c0102695>] cpu_idle+0x45/0xd0
[  133.927952]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  133.927958]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  133.927971]  =======================
[  136.405932] ieee80211_unref_node: NULL ieee80211_node *
[  136.405942] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  136.405964]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  136.406006]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  136.406025]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  136.406044]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  136.406075]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  136.406101]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  136.406127]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[  136.406137]  [<c01260b3>] rebalance_domains+0x163/0x440
[  136.406165]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  136.406173]  [<c0131d72>] __do_softirq+0x82/0x110
[  136.406184]  [<c0131e55>] do_softirq+0x55/0x60
[  136.406189]  [<c013213d>] irq_exit+0x6d/0x80
[  136.406192]  [<c0106f20>] do_IRQ+0x40/0x70
[  136.406203]  [<c0105413>] common_interrupt+0x23/0x30
[  136.406208]  [<c0102f40>] default_idle+0x0/0x60
[  136.406220]  [<c011ec62>] native_safe_halt+0x2/0x10
[  136.406227]  [<c0102f7c>] default_idle+0x3c/0x60
[  136.406230]  [<c0102695>] cpu_idle+0x45/0xd0
[  136.406237]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  136.406242]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  136.406256]  =======================
[  136.796503] ieee80211_unref_node: NULL ieee80211_node *
[  136.796512] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  136.796532]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  136.796573]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  136.796591]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  136.796610]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  136.796640]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  136.796665]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  136.796690]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[  136.796701]  [<c01260b3>] rebalance_domains+0x163/0x440
[  136.796727]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  136.796735]  [<c0131d72>] __do_softirq+0x82/0x110
[  136.796746]  [<c0131e55>] do_softirq+0x55/0x60
[  136.796750]  [<c013213d>] irq_exit+0x6d/0x80
[  136.796754]  [<c0106f20>] do_IRQ+0x40/0x70
[  136.796765]  [<c0105413>] common_interrupt+0x23/0x30
[  136.796770]  [<c0102f40>] default_idle+0x0/0x60
[  136.796782]  [<c011ec62>] native_safe_halt+0x2/0x10
[  136.796790]  [<c0102f7c>] default_idle+0x3c/0x60
[  136.796793]  [<c0102695>] cpu_idle+0x45/0xd0
[  136.796799]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  136.796805]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  136.796822]  =======================
[  139.080071] ieee80211_unref_node: NULL ieee80211_node *
[  139.080081] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  139.080103]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  139.080146]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  139.080163]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  139.080183]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  139.080214]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  139.080240]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  139.080266]  [<c0143f99>] hrtimer_run_queues+0x159/0x2d0
[  139.080277]  [<c01260b3>] rebalance_domains+0x163/0x440
[  139.080304]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  139.080312]  [<c0131d72>] __do_softirq+0x82/0x110
[  139.080323]  [<c0131e55>] do_softirq+0x55/0x60
[  139.080328]  [<c013213d>] irq_exit+0x6d/0x80
[  139.080331]  [<c0106f20>] do_IRQ+0x40/0x70
[  139.080343]  [<c0105413>] common_interrupt+0x23/0x30
[  139.080347]  [<c0102f40>] default_idle+0x0/0x60
[  139.080360]  [<c011ec62>] native_safe_halt+0x2/0x10
[  139.080367]  [<c0102f7c>] default_idle+0x3c/0x60
[  139.080370]  [<c0102695>] cpu_idle+0x45/0xd0
[  139.080377]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  139.080382]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  139.080396]  =======================
[  141.701207] ieee80211_unref_node: NULL ieee80211_node *
[  141.701217] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  141.701242]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  141.701285]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  141.701303]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  141.701323]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  141.701354]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  141.701379]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  141.701410]  [<c01260b3>] rebalance_domains+0x163/0x440
[  141.701436]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  141.701443]  [<c0131d72>] __do_softirq+0x82/0x110
[  141.701454]  [<c0131e55>] do_softirq+0x55/0x60
[  141.701459]  [<c013213d>] irq_exit+0x6d/0x80
[  141.701462]  [<c0106f20>] do_IRQ+0x40/0x70
[  141.701473]  [<c0105413>] common_interrupt+0x23/0x30
[  141.701478]  [<c0102f40>] default_idle+0x0/0x60
[  141.701491]  [<c011ec62>] native_safe_halt+0x2/0x10
[  141.701498]  [<c0102f7c>] default_idle+0x3c/0x60
[  141.701501]  [<c0102695>] cpu_idle+0x45/0xd0
[  141.701507]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  141.701531]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  141.701545]  =======================
[  142.698822] ieee80211_unref_node: NULL ieee80211_node *
[  142.698832] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
[  142.698854]  [<f8b7d291>] ieee80211_input+0x131/0x1ee0 [wlan]
[  142.698894]  [<c028fed0>] mousedev_event+0x0/0x4a0
[  142.698912]  [<f8c32b88>] ath_intr+0x1288/0x2700 [ath_pci]
[  142.698931]  [<f8b9a094>] ieee80211_input_monitor+0x74/0x840 [wlan]
[  142.698961]  [<f8b7f0af>] ieee80211_input_all+0x6f/0xb0 [wlan]
[  142.698986]  [<f8c283f2>] ath_rx_tasklet+0x9e2/0xba0 [ath_pci]
[  142.699004]  [<f88ea613>] finish_urb+0x63/0xc0 [ohci_hcd]
[  142.699016]  [<f88ea72b>] takeback_td+0xbb/0xd0 [ohci_hcd]
[  142.699027]  [<f88ea822>] dl_done_list+0xe2/0x160 [ohci_hcd]
[  142.699058]  [<c01322cd>] tasklet_action+0x4d/0xc0
[  142.699065]  [<c0131d72>] __do_softirq+0x82/0x110
[  142.699076]  [<c0131e55>] do_softirq+0x55/0x60
[  142.699080]  [<c013213d>] irq_exit+0x6d/0x80
[  142.699084]  [<c0106f20>] do_IRQ+0x40/0x70
[  142.699094]  [<c0105413>] common_interrupt+0x23/0x30
[  142.699099]  [<c0102f40>] default_idle+0x0/0x60
[  142.699111]  [<c011ec62>] native_safe_halt+0x2/0x10
[  142.699118]  [<c0102f7c>] default_idle+0x3c/0x60
[  142.699121]  [<c0102695>] cpu_idle+0x45/0xd0
[  142.699128]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[  142.699133]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[  142.699146]  =======================

```

---

