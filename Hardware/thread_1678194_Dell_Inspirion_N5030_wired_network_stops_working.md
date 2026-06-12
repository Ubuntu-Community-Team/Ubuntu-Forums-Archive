---
title: "Dell Inspirion N5030 wired network stops working"
date: 2011-01-29
forum: Hardware
---

### Post by Uxal on 2011-01-29
I bought Laptop Dell  Inspirion N5030 and installde Ubuntu 10.10 on it. Last updates (including kernel  2.6.35-25-generic) was installed via internet.
Problem: wired ethernet interface Atheros Communications AR8152 (1969:2062) stops working after random time. I can not even ping neighbour host.
Reboot helps for some time.
Ifconfig:
```

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:a0:92:df  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:fea0:92df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16233 errors:0 dropped:360 overruns:360 frame:360
          TX packets:12841 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:19958228 (19.9 MB)  TX bytes:1349349 (1.3 MB)
          Interrupt:47

```In dmesg:
```

[  641.008063] ------------[ cut here ]------------
[  641.008073] WARNING: at /build/buildd/linux-2.6.35/net/sched/sch_generic.c:258 dev_watchdog+0x1fd/0x210()
[  641.008076] Hardware name: Inspiron N5030                  
[  641.008078] NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out
[  641.008079]  Modules linked in: binfmt_misc parport_pc ppdev snd_hda_codec_realtek  snd_hda_intel snd_hda_codec arc4 snd_hwdep snd_pcm snd_seq_midi  snd_rawmidi ath9k snd_seq_midi_event snd_seq snd_timer ath9k_common  ath9k_hw ath snd_seq_device mac80211 i915 drm_kms_helper cfg80211 drm  i2c_algo_bit video uvcvideo psmouse snd intel_agp dell_wmi_aio output  serio_raw led_class videodev v4l1_compat soundcore snd_page_alloc  dell_laptop dell_wmi agpgart dcdbas lp parport usb_storage ahci atl1c  libahci
[  641.008114] Pid: 0, comm: swapper Not tainted 2.6.35-25-generic #44-Ubuntu
[  641.008117] Call Trace:
[  641.008122]  [<c014ad42>] warn_slowpath_common+0x72/0xa0
[  641.008126]  [<c050f67d>] ? dev_watchdog+0x1fd/0x210
[  641.008129]  [<c050f67d>] ? dev_watchdog+0x1fd/0x210
[  641.008132]  [<c014ae13>] warn_slowpath_fmt+0x33/0x40
[  641.008134]  [<c050f67d>] dev_watchdog+0x1fd/0x210
[  641.008139]  [<c0161e46>] ? insert_work+0x66/0xb0
[  641.008143]  [<c012cf18>] ? default_spin_lock_flags+0x8/0x10
[  641.008146]  [<c0162106>] ? __queue_work+0x36/0x50
[  641.008149]  [<c050f480>] ? dev_watchdog+0x0/0x210
[  641.008151]  [<c0157f0f>] call_timer_fn+0x2f/0xf0
[  641.008153]  [<c0156c85>] ? cascade+0x65/0x80
[  641.008156]  [<c0159154>] run_timer_softirq+0x104/0x210
[  641.008159]  [<c01751cc>] ? tick_handle_oneshot_broadcast+0x12c/0x140
[  641.008163]  [<c050f480>] ? dev_watchdog+0x0/0x210
[  641.008166]  [<c015136c>] __do_softirq+0x9c/0x1b0
[  641.008169]  [<c01a7f14>] ? handle_IRQ_event+0x44/0x150
[  641.008172]  [<c01a8084>] ? irq_to_desc+0x14/0x20
[  641.008175]  [<c01ab609>] ? move_native_irq+0x19/0x50
[  641.008178]  [<c01514c5>] do_softirq+0x45/0x50
[  641.008180]  [<c0151635>] irq_exit+0x65/0x70
[  641.008183]  [<c05d0b95>] do_IRQ+0x55/0xc0
[  641.008186]  [<c016c044>] ? sched_clock_local+0xa4/0x180
[  641.008190]  [<c0103630>] common_interrupt+0x30/0x38
[  641.008193]  [<c016007b>] ? sys_setuid+0xab/0xc0
[  641.008197]  [<c03bfaed>] ? acpi_idle_enter_simple+0xf1/0x12d
[  641.008202]  [<c04d356a>] cpuidle_idle_call+0x6a/0x100
[  641.008204]  [<c0101fcc>] cpu_idle+0x8c/0xd0
[  641.008208]  [<c05b3951>] rest_init+0x71/0x80
[  641.008211]  [<c081981a>] start_kernel+0x36e/0x374
[  641.008214]  [<c08199dd>] ? pass_all_bootoptions+0x0/0xa
[  641.008217]  [<c08190d7>] i386_start_kernel+0xd7/0xdf
[  641.008221] ---[ end trace 8db0bd294130d086 ]---
[  641.176716] atl1c 0000:09:00.0: irq 47 for MSI/MSI-X
[  641.176798] atl1c 0000:09:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  656.184642] atl1c 0000:09:00.0: irq 47 for MSI/MSI-X
[  656.184728] atl1c 0000:09:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  773.376586] atl1c 0000:09:00.0: irq 47 for MSI/MSI-X
[  773.376672] atl1c 0000:09:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>

```Under Windows 7 on the same hardware, patchcord, etc network works well.
What should I do next?
Thanks a lot!

---

### Post by Uxal on 2011-01-30
2.6.36 works well with this netcard.
Here is commit that fixes problem
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commit;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commit;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533)
Here is patch
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commitdiff;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533;hp=aac4dddc358acfd9d98b20024a42c34dfab31c39](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commitdiff;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533;hp=aac4dddc358acfd9d98b20024a42c34dfab31c39)

I think it should be great to commit this patch into ubuntu 10.10

---

### Post by LuxaDevianta on 2011-03-06
> **Uxal said:**
> 2.6.36 works well with this netcard.
Here is commit that fixes problem
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commit;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commit;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533)
Here is patch
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commitdiff;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533;hp=aac4dddc358acfd9d98b20024a42c34dfab31c39](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=commitdiff;h=8f574b35f22fbb9b5e5f1d11ad6b55b6f35f4533;hp=aac4dddc358acfd9d98b20024a42c34dfab31c39)

I think it should be great to commit this patch into ubuntu 10.10
I have the same problem with this laptop. I use Kubuntu 10.10
It's a pitty, but my English is rather poor for not to understand the explainations given at theese links. Would you be so kind to help me with it?

---

### Post by WanderingAlbatross on 2011-03-08
Basically it is not telling you anything except that the 2.6.36 kernel will fix it.  The problem is that the kernel can not be installed just yet without doing it yourself.  We must be patient and wait.  This amazing army is on the case.  I have a computer with the same troubles.  Dell n5030.  I will post again when I see the new kernel come along.

---

### Post by 1emming on 2011-04-05
Dear all,

I'm still suffering under what I think is the same network thing described here. My Dell Inspiron N5030 is running Ubuntu Release 10.10 (Maverick) Kernel Linux 2.6.35-28-generic GNOME 2.32.0.
Any hints what I could do?
Wireless works fine btw.
Minor thingy is that the keypad is recognised as a mouse and cannot be switched off :/
Beside that I really like Ubuntu, great work all! :D

Seb

---

### Post by LuxaDevianta on 2011-04-05
I've installed openSUSE 11.4, which hav a newer kernel version 2.6.37 and all hardware started working stable

---

### Post by 1emming on 2011-05-02
I've updated to 11.04 today, but no luck with the wired connection.
When I plug-in, the icon for the connection flips on/off real fast for a few seconds and then I get the message that I'm not connected through the wired connection.
Any suggestions, cause this is really ruining my Ubuntu experience....
Let me know if I can run some stuff to provide more info.

---

### Post by 1emming on 2011-06-26
Just a follow up. After switching off my wireless card/connection using the 'hardware-key' thing, the wired connection is good :)
Still a strange issue, but I'm ok with it.
(more of a problem is that I cannot switch the wireless card back on, the system seems non-responsive to the 'hardware key')

---

### Post by Chachalaco on 2012-01-18
Hey 1emming, same problem here with my Inspiron N5030.
Regarding the keypad issue, there is a way that worked great for me.
With the command:
```
xinput set-int-prop 'PS/2 Generic Mouse' 'Device Enabled' 8 0;
```
you can disable the touchpad.
And with the command:
```
xinput set-int-prop 'PS/2 Generic Mouse' 'Device Enabled' 8 1;
```
you can turn it on again.

You can create buttons with these commands in the panel or you can assign these commands to any keyboard combination using the 'System/Preferences/Keyboard combinations' dialog.

Cheers.

---

