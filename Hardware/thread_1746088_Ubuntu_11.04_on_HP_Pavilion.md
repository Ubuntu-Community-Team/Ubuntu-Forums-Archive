---
title: "Ubuntu 11.04 on HP Pavilion"
date: 2011-05-01
forum: Hardware
---

### Post by hamenarin on 2011-05-01
Hi, I just installed Ubuntu 11.04 on my HP Pavilion dv4 notebook, Intel i3 330m 64 bit. The normal boot entry doesn`t work, and in recovery mode I get the Oops below, which seems to be an initialization exception for the radeon driver.

Another issue is that the GRUB doesn`t load except when I use the HP splashtop for a while and then boot the first hard drive. Could the MBR installation on the first partition solve this problem (like in this article: [http://www.marcosorfila.com/site/ubuntu-1004-on-an-hp-pavilion-dv4i-notebook/](http://www.marcosorfila.com/site/ubuntu-1004-on-an-hp-pavilion-dv4i-notebook/))?


Thanks
Henrique

> [   17.423900] intel ips 0000:00:1f.6: failed to get i1915 symbols, graphics turbo disabled
[   30.405112] BUG: unable to handle kernel paging request at ffffc9041b371ffc
[   30.405163] IP: [<ffffffffa0373103>] r600_cp_start+0x52/0x410 [radeon]
[   30.405231] PGD 13780f067 PUD 0
[   30.405267] Oops: 0002 [#1] SMP
[   30.405303] last susfs file: /sys/module/snd_hda_intel/initstate
[   30.405337] CPU 2
[   30.405351] Modules linked in: snd_hda_codec_idt arc4 snd_hda_intel(+) snd_hda_codec snd_hwdep snd_seq_midi snd_pcm iwlagn snd_rawmidi iwlcore snd_seq_midi_event radeon(+) snd_seq mac80211uvcvideo snd_timer snd (...)
[   30.405921] 
[   30.405936] Pid: 454, comm: modprobe Not tainted 2.6.38-8-generic #42-Ubuntu Hewlett-Packard HP Pavilion dv4 Notebook PC/1409
[   30.406021] RIP: 0010:[<ffffffffa0373103>] [<ffffffffa0373103>] r600_cp_start+0x53/0x410 [radeon]
[   30.406089] RSP: 0018:ffff88011ebe1b08  EFLAGS: 00010257
[   30.406119] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff88011ebd8000
(...)


---

### Post by nonabhai on 2011-05-11
Similar error with my Dell 1564 core i5 :(

---

### Post by Prometheus_IX on 2011-05-22
Yeah same deal with my 8935 Acer - I'm assuming it's something to do with the radeon gfx card (Mobility Radeon HD4670 on mine). The card has never played nice with Ubuntu for me at least - whenever I enabled proprietary driver software on previous versions it wouldn't boot a bit like this. Anyone have any luck resolving this? I'll see what I can get done tomorrow...

---

