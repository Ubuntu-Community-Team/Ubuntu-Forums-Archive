---
title: "Comapq CQ40-328TU ... Brightness' Problem"
date: 2012-07-28
forum: Hardware
---

### Post by czgirb on 2012-07-28
When I installed Ubuntu **12.04** in my **CQ40** lappie ... most ... works fine.
The minor is **display's brightness** ... but I still able to reduce the brightness to zero (according to Ubuntu's sign) by press the **FN+F7** (brightness reduced key).
But for every startup, the brightness was reset to default, not my setting.

Now, I forgot what I had doing ... the **FN+F7** key is not working anymore.

Is there any one can help me out?
At least the **FN+F7** key is works normally.

**PS:**
To look the display with full brightness, my eyes is **very very very not comfortable**.
Please help me ...

---

### Post by Kreaninw on 2012-07-28
This is a known issue, display brightness will reset to maximum/default every time user logout or reboot. 

However, I don't know why your key does not work. Can you configure it via system setting?

---

### Post by Toz on 2012-07-28
> **czgirb said:**
> Now, I forgot what I had doing ... the **FN+F7** key is not working anymore.

> At least the **FN+F7** key is works normally.
This is confusing - is the FN+F7 brightness key working for you? If the brightness keys were once working but are no longer working, try booting a previous kernel to see if they start working again. To do so, hold down the shift key while the computer is booting and from the grub screen select "Previous Kernels" and then select the first kernel that displays.

> **PS:**
To look the display with full brightness, my eyes is **very very very not comfortable**.
Please help me ...

Can you open a terminal window, type in (or copy/paste) the following commands, and post back the results:
```
cat /proc/cmdline
```
```
lsmod
```
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```

---

### Post by czgirb on 2012-07-28
> **Toz said:**
> 
... can you open a terminal window, type in (or copy/paste) the following commands, and post back the results:
```
cat /proc/cmdline
```
```
lsmod
```
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```


As requested ... have yourself a references:
```

czgirb@czgirb:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=1a61250f-928d-4a29-b75d-a7cf8198b1b3 ro acpi_backlight=vendor quiet splash vt.handoff=7
czgirb@czgirb:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31775  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
ipt_REJECT             12512  1 
snd_hwdep              13276  1 snd_hda_codec
ipt_LOG                12783  5 
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
xt_limit               12541  12 
xt_tcpudp              12531  18 
snd_seq_midi           13132  0 
xt_addrtype            12596  4 
snd_rawmidi            25424  1 snd_seq_midi
xt_state               12514  14 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ip6table_filter        12711  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
lib80211_crypt_tkip    17275  0 
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
wl                   2646601  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
i915                  414703  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ip_tables              18106  1 iptable_filter
lib80211               14040  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13199  1 i915
jmb38x_ms              17406  0 
btusb                  17912  2 
uvcvideo               67203  0 
memstick               15857  1 jmb38x_ms
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
psmouse                72919  0 
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
videodev               86588  1 uvcvideo
bluetooth             158438  23 bnep,rfcomm,btusb
ir_mce_kbd_decoder     12681  0 
serio_raw              13027  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
wmi                    18744  1 hp_wmi
ir_rc6_decoder         12459  0 
rc_rc6_mce             12454  0 
ir_rc5_decoder         12459  0 
ene_ir                 18019  0 
ir_nec_decoder         12459  0 
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ene_ir,ir_nec_decoder
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
r8169                  56321  0 
hid_a4tech             12590  0 
usbhid                 41906  0 
hid                    77367  2 hid_a4tech,usbhid
usb_storage            39646  1 
czgirb@czgirb:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/intel_backlight
1
1
1
czgirb@czgirb:~$ 

```
Please do not forget to help me ...
**Thank you**

---

### Post by Toz on 2012-07-28
Three things to try:

1. Remove **acpi_backlight=vendor** from your kernel boot line (/etc/default/grub - make sure to run *sudo update-grub*), reboot and run those commands again. Try the function keys.

If that doesn't work...
2. Boot the previous kernel (hold down shift during boot, select "Previous Kernels" from the grub boot screen and select the topmost kernel). Run those commands again and try the function keys.

If that doesn't work...
3. Add **acpi_backlight=vendor** back to the kernel boot line _and_ boot the previous kernel as in attempt #2. Run those commands again and try the function keys.

Post back the results of each of your steps.

---

### Post by czgirb on 2012-07-28
> **Toz said:**
> Three things to try:

1. Remove **acpi_backlight=vendor** from your kernel boot line (/etc/default/grub - make sure to run *sudo update-grub*), reboot and run those commands again. Try the function keys.

If that doesn't work...
2. Boot the previous kernel (hold down shift during boot, select "Previous Kernels" from the grub boot screen and select the topmost kernel). Run those commands again and try the function keys.

If that doesn't work...
3. Add **acpi_backlight=vendor** back to the kernel boot line _and_ boot the previous kernel as in attempt #2. Run those commands again and try the function keys.

Post back the results of each of your steps.

Oh my God! I'm a newbie to Ubuntu. So, please your expert words to newbie words, man! Cos I really do not understand with what you mean.

You said: Remove **acpi_backlight=vendor** from your kernel boot line
I said: How to do that?

You said: Add **acpi_backlight=vendor** back to the kernel boot line
I said: How to do that?

One-by-one (step-by-step), please?

---

### Post by Toz on 2012-07-28
Ok, sorry. Lets do them one at a time and lets try the previous kernel step first.

[LIST=1]
[*]Start or reboot the computer.

[*]When the computer is booting, hold down the Shift key until the grub menu appears.

[*]One of the options is something like "Previous kernel versions" or something like that. Use the arrow keys to move to that entry and press enter.

[*]A second screen will display with the previous kernels that are installed on your computer. If not already there, use the arrow keys to select the first entry. 

[*]Press enter.
[/LIST]

The previous kernel will boot. Go ahead and log in normally. Try the FN+F7 brightness key. Does it work? 

Now run the commands from post #3 and post back the results. We'll take it from there.

---

### Post by czgirb on 2012-07-29
> **Toz said:**
> 
* Start or reboot the computer.
* When the computer is booting, hold down the Shift key until the grub menu appears.
* One of the options is something like "Previous kernel versions" or something like that. Use the arrow keys to move to that entry and press enter.
* A second screen will display with the previous kernels that are installed on your computer. If not already there, use the arrow keys to select the first entry.
* Press enter.

OK! I re-start the computer, and when it's booting I hold down the **SHIFT** key.
* The available options is four. **Two kernel (General and Recovery Mode**) and **Two memtest**.
Since there is no previous kernel ... so, I choose the top one. Release the **SHIFT** key and press **ENTER**. Is my step is wrong?

> **Toz said:**
> 
The previous kernel will boot. Go ahead and log in normally. Try the FN+F7 brightness key. Does it work?

**No!**

> **Toz said:**
> 
Now run the commands from post #3 and post back the results. We'll take it from there.
SORRY ... what command and how to run it?
SORRY for my foolness.
Please do not feeling boring for helping people like me. :):):)

**PS:**
**I forgot to informed (Start from the beginning):**
fn+F7 (reduce brightness) does not work.
fn+F8 (increase brightness) is work and it still works.
* But since the brightness is maximized, so it do not give an effect.

---

### Post by Toz on 2012-07-29
Lets try this one then:

[LIST=1]
[*]Edit the grub configuration file:
```
gksudo gedit /etc/default/grub
```

[*]Remove acpi_backlight=vendor
Look for the parameter **acpi_backlight=vendor** in either the line starting with **GRUB_CMDLINE_LINUX_DEFAULT** or **GRUB_CMDLINE_LINUX** (or both) and remove it.
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


[*]Save the file

[*]Save your changes
```
sudo update-grub
```

[*]Reboot
[/LIST]

Try the brightness keys (both up and down) and see if they work. Also, post back the results of the following commands:
```
cat /proc/cmdline
```
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```
```
sudo lspci -vnn | grep -A10 VGA
```

---

### Post by czgirb on 2012-07-29
> **Toz said:**
> 
Lets try this one then:

[LIST=1]
[*]Edit the grub configuration file:
```
gksudo gedit /etc/default/grub
```
[*]Remove acpi_backlight=vendor
Look for the parameter **acpi_backlight=vendor** in either the line starting with **GRUB_CMDLINE_LINUX_DEFAULT** or **GRUB_CMDLINE_LINUX** (or both) and remove it.
[*]Save the file
[*]Save your changes
```
sudo update-grub
```
[*]Reboot
[/LIST]
Try the brightness keys (both up and down) and see if they work.

Yes! It works! Now I have my fn+F7 back.
Thank you very much

> **Toz said:**
> 
Also, post back the results of the following commands:
```
cat /proc/cmdline
```
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```
```
sudo lspci -vnn | grep -A10 VGA
```

As requested:
```
czgirb@czgirb:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=1a61250f-928d-4a29-b75d-a7cf8198b1b3 ro
czgirb@czgirb:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
10
0
0
/sys/class/backlight/intel_backlight
1
1
0
czgirb@czgirb:~$ sudo lspci -vnn | grep -A10 VGA
[sudo] password for czgirb: 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:3607]
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 7110 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915
czgirb@czgirb:~$

```

Are you a human? :confused::confused::confused:
Wow! How lucky I am to meet a people like you. :):):)

---

### Post by Toz on 2012-07-29
I'm glad that this worked for you. I'm curious though how the acpi_backlight=vendor parameter got into your kernel boot line. Did it originally fix a brightness issue?

In your original post, you mentioned that the brightness resets itself on every boot. Is this still an issue?

---

### Post by czgirb on 2012-07-29
> **Toz said:**
> I'm glad that this worked for you. I'm curious though how the acpi_backlight=vendor parameter got into your kernel boot line. Did it originally fix a brightness issue?
In your original post, you mentioned that the brightness resets itself on every boot. Is this still an issue?

Me too.
Fix a brightness issue? Sorry! I do not understand with what you mean.
Currently, my lappie is back to the "default" condition.
To reduce the brightness, we should press **fn+f7** key
To increase it brightness, we should press **fn+f8** key
But the brightness will be back to "**Factory Setting**" for every reboot.

Dear **Toz**,
If you ask me is the brightness was reset on every boot is an issue or not?
To me, at least ... **YES, absolutely** ... but since it able to reduced with **fn+f7** key ... **it's better than it can not, right**?
But if you able to change the "**default**" ... it will be more appreciated.
**Thank you.**

---

### Post by Toz on 2012-07-29
> **czgirb said:**
> 
Dear **Toz**,
If you ask me is the brightness was reset on every boot is an issue or not?
To me, at least ... **YES, absolutely** ... but since it able to reduced with **fn+f7** key ... **it's better than it can not, right**?
But if you able to change the "**default**" ... it will be more appreciated.
**Thank you.**

When you have the brightness set as you want it, run this script again and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```

We can use these values and set them automatically at boot.

---

### Post by czgirb on 2012-07-30
> **Toz said:**
> When you have the brightness set as you want it, run this script again and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```We can use these values and set them automatically at boot.

As requested:
```
czgirb@czgirb:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
10
0
0
/sys/class/backlight/intel_backlight
1
1
0
czgirb@czgirb:~$ 

```

---

### Post by Toz on 2012-07-30
Thats interesting. Is the brightness set at the value you like? Its currently showing as being set at value 0.

---

### Post by czgirb on 2012-07-30
> **Toz said:**
> Thats interesting. Is the brightness set at the value you like? Its currently showing as being set at value 0.

Yup! This is my desired brightness.
I just press **fn+f7** until t**he brightness' indicator shift to left (none)**.

---

### Post by Toz on 2012-07-31
Okay then. Try this:

1. Edit rc.local:
```
gksudo gedit /etc/rc.local
```

2. Add the following line _above_ the *exit 0* command:
```
echo 0 > /sys/class/backlight/acpi_video0/brightness
```

3. Save the file.

When you boot your computer, it should set the brightness to your desired level.

---

### Post by czgirb on 2012-08-01
> **Toz said:**
> Okay then. Try this:

1. Edit rc.local:
```
gksudo gedit /etc/rc.local
```2. Add the following line _above_ the *exit 0* command:
```
echo 0 > /sys/class/backlight/acpi_video0/brightness
```3. Save the file.

When you boot your computer, it should set the brightness to your desired level.

SORRY ... NO!
The brightness still remain the same.
I still used to press **fn+f7** key to reduce it.

---

### Post by Toz on 2012-08-01
Can you post back the contents of the /etc/rc.local file?

---

### Post by czgirb on 2012-08-01
> **Toz said:**
> Can you post back the contents of the /etc/rc.local file?
 
Is this what you mean?
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0 > /sys/class/backlight/acpi_video0/brightness

---

### Post by Toz on 2012-08-01
The file should read:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 0 > /sys/class/backlight/acpi_video0/brightness 
exit 0
```

After you reboot and login, before you press your FN brightness keys, run this script again and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```
...and tell me whether the system started with the brightness setting you wanted.

---

### Post by czgirb on 2012-08-02
> **Toz said:**
> The file should read:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 0 > /sys/class/backlight/acpi_video0/brightness 
exit 0
```
No matter with or without addtional exit 0 ... the result is the same
The brightness un-changed

> **Toz said:**
> 
After you reboot and login, before you press your FN brightness keys, run this script again and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```...and tell me whether the system started with the brightness setting you wanted.

This is **before fn+f7** was pressed
> czgirb@czgirb:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
10
10
10
/sys/class/backlight/intel_backlight
1
1
0
czgirb@czgirb:~$ 

---

### Post by Toz on 2012-08-02
Can you post back /var/log/dmesg and /var/log/syslog right after boot?

---

### Post by czgirb on 2012-08-03
> **Toz said:**
> Can you post back /var/log/dmesg and /var/log/syslog right after boot?
As requested:
> czgirb@czgirb:~$ /var/log/dmesg
bash: /var/log/dmesg: Permission denied
czgirb@czgirb:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied
czgirb@czgirb:~$ 

---

### Post by Toz on 2012-08-03
Try these commands and post back the link that is generated:
```
pastebinit /var/log/dmesg
pastebinit /var/log/syslog

```

It would be best if you did this right after a reboot.

---

### Post by czgirb on 2012-08-05
> **Toz said:**
> Try these commands and post back the link that is generated:
```
pastebinit /var/log/dmesg
pastebinit /var/log/syslog

```It would be best if you did this right after a reboot.
As requested:
> 
czgirb@czgirb:~$ pastebinit /var/log/dmesg
The program 'pastebinit' is currently not installed.  You can install it by typing:
sudo apt-get install pastebinit
czgirb@czgirb:~$ pastebinit /var/log/syslog
The program 'pastebinit' is currently not installed.  You can install it by typing:
sudo apt-get install pastebinit
czgirb@czgirb:~$ 

Sorry for a late reply

---

### Post by Toz on 2012-08-05
Looks like you need to install pastebinit:
```
sudo apt-get install pastebinit
```

---

### Post by czgirb on 2012-08-06
> **Toz said:**
> Looks like you need to install pastebinit:
```
sudo apt-get install pastebinit
```

What is pastebinit?
Now I install it ... after that ????

---

### Post by Toz on 2012-08-06
pastebinit will copy the contents of your log files up to [http://pastebin.com/]("http://pastebin.com/") so you don't have to manually copy the contents here - its easier to do.

Run the commands from post #25. After you've run each command, it will return the web url to your log file. Paste that url here so that I can have a look at the log file. I want to see if there is anything in your log files to indicate why the brightness setting at boot isn't working.

---

### Post by czgirb on 2012-08-06
> **Toz said:**
> Try these commands and post back the link that is generated:
```
pastebinit /var/log/dmesg
pastebinit /var/log/syslog

```It would be best if you did this right after a reboot.
As requested:
> 
czgirb@czgirb:~$ pastebinit /var/log/dmesg
[http://paste.ubuntu.com/1132867/](http://paste.ubuntu.com/1132867/)
czgirb@czgirb:~$ pastebinit /var/log/syslog
[http://paste.ubuntu.com/1132869/](http://paste.ubuntu.com/1132869/)
czgirb@czgirb:~$ 


---

### Post by Toz on 2012-08-06
From your dmesg log:
> [    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: F.24; Product Version: F.24
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 3.2.0-27-generic-pae #43-Ubuntu
[    0.000000] Call Trace:
[    0.000000]  [<c105a722>] warn_slowpath_common+0x72/0xa0
[    0.000000]  [<c148dc28>] ? warn_invalid_dmar+0x98/0xb0
[    0.000000]  [<c148dc28>] ? warn_invalid_dmar+0x98/0xb0
[    0.000000]  [<c105a7b2>] warn_slowpath_fmt_taint+0x32/0x40
[    0.000000]  [<c148dc28>] warn_invalid_dmar+0x98/0xb0
[    0.000000]  [<c18ae04f>] check_zero_address+0x59/0x125
[    0.000000]  [<c1323027>] ? acpi_get_table_with_size+0x59/0xb3
[    0.000000]  [<c18ae12d>] detect_intel_iommu+0x12/0x78
[    0.000000]  [<c187d5f9>] pci_iommu_alloc+0x35/0x5a
[    0.000000]  [<c1888f63>] mem_init+0xe/0x28c
[    0.000000]  [<c1893f03>] ? __alloc_bootmem_node_nopanic+0x72/0x93
[    0.000000]  [<c158fb0d>] ? printk+0x2d/0x2f
[    0.000000]  [<c1896501>] ? page_cgroup_init_flatmem+0x8f/0xbc
[    0.000000]  [<c18755db>] start_kernel+0x1a6/0x353
[    0.000000]  [<c18753c6>] ? pass_bootoption.constprop.2+0xe2/0xe2
[    0.000000]  [<c18750ba>] i386_start_kernel+0xa9/0xaf
[    0.000000] ---[ end trace a7919e7f17c0a725 ]---

...and...

> [    0.824243] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.825322] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness

You might want to consider updating your bios.

---

### Post by czgirb on 2012-08-08
> **Toz said:**
> From your dmesg log:


...and...



You might want to consider updating your bios.

OK! How do I update my BIOS ?????
Please guide me ........................
**Thank you**

---

### Post by Toz on 2012-08-08
Is this a dual-boot computer? Is MS Windows installed on the computer? I believe it is required to upgrade the bios.

Go to the CQ40-328TU support page at: [http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3876895]("http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3876895") and follow the Support and Downloads link.

---

### Post by czgirb on 2012-08-09
> **Toz said:**
> Is this a dual-boot computer? Is MS Windows installed on the computer? I believe it is required to upgrade the bios.

Go to the CQ40-328TU support page at: [http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3876895](http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3876895) and follow the Support and Downloads link.

Wow! Sorry! The OS within my lappie, currently is Ubuntu 12.04 only.
The link given is for Windows ... how can I make it for Ubuntu?
Please guide me ...

---

### Post by Toz on 2012-08-09
czgirg,
The best way to flash your bios is through Windows. I don't want to give you bad advice since incorrectly flashing your bios may destroy your computer.

I would like to point out this link: [http://ubuntuforums.org/showthread.php?t=318789&page=17]("http://ubuntuforums.org/showthread.php?t=318789&page=17") and specifically posts #161 & #162:

- [http://ubuntuforums.org/showpost.php?p=11185511&postcount=161]("http://ubuntuforums.org/showpost.php?p=11185511&postcount=161")
- [http://ubuntuforums.org/showpost.php?p=11186463&postcount=162]("http://ubuntuforums.org/showpost.php?p=11186463&postcount=162")

They reference [http://www.flashrom.org/Flashrom]("http://www.flashrom.org/Flashrom") and the volunteers at the #flashrom IRC channel. Perhaps you could contact them and ask for assistance.

---

