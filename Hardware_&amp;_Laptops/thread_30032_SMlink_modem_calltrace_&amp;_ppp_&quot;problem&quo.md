---
title: "SMlink modem: calltrace &amp; ppp &quot;problem&quot;."
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by ludi on 2005-04-26
HI.
Well, I've just installed the ubuntu in my other machine with SmartLink modem. All right, I'm using the .deb packages from azz (from this forum). The modem is working but I have a strange problem.
I can do a pon and the modem "turn on" but after sometime I don't get on-line... so I try poff and he tells me that there isn't any pppd running, while the modem is still "working" (on).

Well I'll compile the last module by myself and see what happen but I appreciate any help.

Here is my syslog:

Apr 26 23:31:53 localhost udev[7034]: creating device node '/dev/ppp'
Apr 26 23:31:53 localhost kernel: PPP generic driver version 2.4.2
Apr 26 23:31:53 localhost pppd[7042]: pppd 2.4.2 started by root, uid 0
Apr 26 23:31:54 localhost chat[7043]: timeout set to 60 seconds
Apr 26 23:31:54 localhost chat[7043]: abort on (ERROR)
Apr 26 23:31:54 localhost chat[7043]: abort on (BUSY)
Apr 26 23:31:54 localhost chat[7043]: abort on (VOICE)
Apr 26 23:31:54 localhost chat[7043]: abort on (NO CARRIER)
Apr 26 23:31:54 localhost chat[7043]: abort on (NO DIALTONE)
Apr 26 23:31:54 localhost chat[7043]: abort on (NO DIAL TONE)
Apr 26 23:31:54 localhost chat[7043]: abort on (NO ANSWER)
Apr 26 23:31:54 localhost chat[7043]: send (ATZ^M)
Apr 26 23:31:54 localhost chat[7043]: send (AT&FH0L3^M)
Apr 26 23:31:54 localhost chat[7043]: expect (OK)
Apr 26 23:31:54 localhost chat[7043]: ATZ^M^M
Apr 26 23:31:54 localhost chat[7043]: OK
Apr 26 23:31:54 localhost chat[7043]:  -- got it 
Apr 26 23:31:54 localhost chat[7043]: send (ATDT46040600^M)
Apr 26 23:31:54 localhost chat[7043]: timeout set to 75 seconds
Apr 26 23:31:54 localhost chat[7043]: expect (CONNECT)
Apr 26 23:31:54 localhost chat[7043]: warning: read() on stdin returned 0
Apr 26 23:31:54 localhost chat[7043]: Failed
Apr 26 23:31:54 localhost chat[7043]: Can't restore terminal parameters: Input/output error
Apr 26 23:31:54 localhost pppd[7042]: Hangup (SIGHUP)
Apr 26 23:31:54 localhost pppd[7042]: Connect script failed
Apr 26 23:31:54 localhost kernel: Unable to handle kernel paging request at virtual address 8db0ebc0
Apr 26 23:31:54 localhost kernel:  printing eip:
Apr 26 23:31:54 localhost kernel: d0c15469
Apr 26 23:31:54 localhost kernel: *pde = 00000000
Apr 26 23:31:54 localhost kernel: Oops: 0002 [#1]
Apr 26 23:31:54 localhost kernel: PREEMPT 
Apr 26 23:31:54 localhost kernel: Modules linked in: ppp_generic slhc ipv6 proc_intf cpufreq_powersave cpufreq_userspace cpufreq_ondemand freq_table video battery container button pcc_acpi sony_acpi ac slamr emu10k1_gp snd_emu10k1 snd_ac97_codec snd_util_mem snd_cmipci snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_timer snd_hwdep gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore ohci_hcd usbcore i2c_sis96x i2c_sis630 i2c_core pci_hotplug sis_agp agpgart floppy pcspkr rtc nls_iso8859_1 nls_cp437 vfat fat tsdev md evdev dm_mod capability commoncap psmouse mousedev parport_pc lp parport ide_cd cdrom reiserfs ide_generic ide_disk sis5513 ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Apr 26 23:31:54 localhost kernel: CPU:    0
Apr 26 23:31:54 localhost kernel: EIP:    0060:[pg0+277386345/1070015488]    Tainted: P      VLI
Apr 26 23:31:54 localhost kernel: EFLAGS: 00010296   (2.6.10-5-386) 
Apr 26 23:31:54 localhost kernel: EIP is at sysdep_memset+0xd/0x15 [slamr]
Apr 26 23:31:54 localhost kernel: eax: 00000000   ebx: c56030a0   ecx: 00003000   edx: 00000000
Apr 26 23:31:54 localhost kernel: esi: ce62de1c   edi: 8db0ebc0   ebp: ccc75a00   esp: ce62ddc4
Apr 26 23:31:54 localhost kernel: ds: 007b   es: 007b   ss: 0068
Apr 26 23:31:54 localhost kernel: Process slmodemd (pid: 5654, threadinfo=ce62c000 task=cf1b8140)
Apr 26 23:31:54 localhost kernel: Stack: ce62ddec d0c443f8 8db0ebc0 00000000 00003000 00000000 ccd7a000 00000000 
Apr 26 23:31:54 localhost kernel:        00001000 00000001 00000000 00000001 00000001 00009600 00000010 00000000 
Apr 26 23:31:54 localhost kernel:        00000000 00000000 00000000 00000000 00000000 02600800 00000000 00000001 
Apr 26 23:31:54 localhost kernel: Call Trace:
Apr 26 23:31:54 localhost kernel:  [pg0+277578744/1070015488] FinishModioSetup__13ModemInstanceP18tagMODIOINFOSTRUCT+0x568/0x628 [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277576238/1070015488] Enable__13ModemInstanceP18tagMODIOINFOSTRUCT+0x22/0x19c [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277422454/1070015488] Start__10VModemLineP18tagMODIOINFOSTRUCT+0xf6/0x128 [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277581095/1070015488] CalculateStartParameters__13ModemInstance+0x1f3/0x1fc [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277576045/1070015488] ReallyOpenModio__13ModemInstance+0x141/0x1e0 [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277581662/1070015488] SetProp__13ModemInstanceUlUl+0xce/0x17c [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277583327/1070015488] Start__13ModemInstanceP10STARTPARAM+0x3b/0x54 [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277387489/1070015488] amrmo_card_start+0x39/0x44 [slamr]
Apr 26 23:31:54 localhost kernel:  [pg0+277386007/1070015488] amrmo_ioctl+0xa8/0xe7 [slamr]
Apr 26 23:31:54 localhost kernel:  [sys_ioctl+443/472] sys_ioctl+0x1bb/0x1d8
Apr 26 23:31:54 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Apr 26 23:31:54 localhost kernel: Code: 85 c0 5b 89 c3 75 0d 56 68 60 ee c4 d0 e8 d9 0d 50 ef 58 5a 89 d8 5b 5e c3 e9 73 12 52 ef 57 8b 4c 24 10 8a 44 24 0c 8b 7c 24 08 <f3> aa 8b 44 24 08 5f c3 57 56 8b 44 24 14 89 c1 8b 74 24 10 c1 
Apr 26 23:31:55 localhost pppd[7042]: Exit.

---

### Post by az on 2005-04-27
Ew!

How old (or rather how new) is your modem?  You may need the newer version of the driver.  Smartlink changed the licence to the newest version, so it is only available from the website, and not as a deb package....

Maybe it is an acpi thing, too?

You can try using the alsa driver, if you do not mind reading the docs and getting your hands dirty.

Read the docs on configuring it as an alsa device.  Remove the sl-modem-modules package and dpkg-reconfigure sl-modem-daemon.  That will automagically switch to using the alsa driver.

---

### Post by ludi on 2005-04-27
[QUOTE=azz]Ew!

How old (or rather how new) is your modem?  You may need the newer version of the driver.  Smartlink changed the licence to the newest version, so it is only available from the website, and not as a deb package....

Maybe it is an acpi thing, too?

You can try using the alsa driver, if you do not mind reading the docs and getting your hands dirty.

Read the docs on configuring it as an alsa device.  Remove the sl-modem-modules package and dpkg-reconfigure sl-modem-daemon.  That will automagically switch to using the alsa driver.[/QUOTE]
 Hey azz.
Yes I had problems with acpi so acpi=off apm=on but the modem still the same...
I've compile the modem drive with slmodem.2.9.9d but I still have the same problem (and the same msg in syslog). 
Alsa mode don't work for me... 
I have used SuSE in that machine and I didn't get problems with the modem.
I don't know what to do now...
Well, I'll try to compile with the 2.9.10 version (I've used that in suse).
Yeah Winmodens are a nightmare...
Do you have any idea?

---

### Post by ludi on 2005-04-27
So, the same for 2.9.10. I'm stuck.
I watched the slmodemd while I was doing pon and I get a segment fault error in the same moment of pon.
... ](*,)

---

### Post by az on 2005-04-27
"I have used SuSE in that machine and I didn't get problems with the modem."

You can try installing the Warty kernel (and linux-headers) and building the driver and daemon packages with that.  Maybe it is a kernel thing?  Warty's kernel is great and will be supported for another year and a half...

Boot the warty kernel
cd to the source
sudo debian/rules binary
and it will build your packages for you. (daemon and modules)

"I watched the slmodemd while I was doing pon and I get a segment fault error in the same moment of pon."

I dunno.  If it is the daemon than is crashig then whatever kernel you use should not matter.

How patient/stubborn are you?

---

### Post by ludi on 2005-04-28
[QUOTE=azz]"I have used SuSE in that machine and I didn't get problems with the modem."

You can try installing the Warty kernel (and linux-headers) and building the driver and daemon packages with that.  Maybe it is a kernel thing?  Warty's kernel is great and will be supported for another year and a half...

Boot the warty kernel
cd to the source
sudo debian/rules binary
and it will build your packages for you. (daemon and modules)

"I watched the slmodemd while I was doing pon and I get a segment fault error in the same moment of pon."

I dunno.  If it is the daemon than is crashig then whatever kernel you use should not matter.

How patient/stubborn are you?[/QUOTE]
 I've compiled again. Version 2.9.9b and c. Both worked in the first time (after the install, without reboot). When I reboot the machine I get the very same problem again.
That isn't my machine and I don't have much time to work on.
I think that this could be a kernel issue (the hoary version). I'll get the 2.6.11 and see what happen.
I'll try the old version too (warty)...
Thanks for the support.

---

### Post by ludi on 2005-05-02
Well, OK.
Now I'm using the warty kernel and finally the modem just works.
For sure that I had much problems downgrading my kernel (like modules versions, video cards, repositories and long hours to download everything...but I'm connected now  :) 
Thanks for you help.

---

