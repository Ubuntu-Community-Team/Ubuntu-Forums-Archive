---
title: "battery drain after shutdown (~20% every 24h)"
date: 2021-01-22
forum: Hardware
---

### Post by asgard2 on 2021-01-22
Hello,

any time I shutdown my notebook (Ryzen 5 3500U + Vega8) I have a huge battery drop around 15 to 20 percent per day.

If I reboot into the systems boot loader and shut down the device with power button, the percentage drop is only around 1-2%. 

This is a major difference, the battery was multiple times completely depleted only while off. The capacity from notebook battery check, has fallen sharply (> 10%) after these events. I'm afraid that my (new) battery will damage.
Short lshw output from the device: [https://pastebin.com/rx1BciFj](https://pastebin.com/rx1BciFj)

Maybe the device is not completely off after shutdown? But no led is on and USB has no power, tested with my optical mouse.

Can someone help ?
```
systemd-inhibit --list
WHO                          UID  USER PID  COMM            WHAT                                                     WHY                                                       MODE 
ModemManager                 0    root 899  ModemManager    sleep                                                    ModemManager needs to reset devices                       delay
NetworkManager               0    root 799  NetworkManager  sleep                                                    NetworkManager needs to turn off networks                 delay
UPower                       0    root 1361 upowerd         sleep                                                    Pause device polling                                      delay
Unattended Upgrades Shutdown 0    root 981  unattended-upgr shutdown                                                 Stop ongoing upgrades or perform upgrades before shutdown delay
xfce4-power-manager          1000 user 1477 xfce4-power-man handle-power-key:handle-suspend-key:handle-hibernate-key xfce4-power-manager handles these events                  block
xfce4-screensaver            1000 user 1312 xfce4-screensav sleep                                                    Locking screen before sleep                               delay

6 inhibitors listed.
```

It is completely shutdown, no hybernate or suspend. There is no walke ob lan option in the bios and no lan connector available.

How could this possible, any idea to investigate this problem?

---

### Post by asgard2 on 2021-01-30
Bug description here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1912935](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1912935)

What else can I do?

By updating the kernel, these warnings appear:

```

W: Possible missing firmware /lib/firmware/amdgpu/navi12_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_asd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_asd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_sdma1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_dmcu.bin for module amdgpu

```

---

