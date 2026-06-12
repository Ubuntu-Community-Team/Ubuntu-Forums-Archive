---
title: "AMDGPU MST (DisplayPort daisy chain) supported?"
date: 2018-07-10
forum: Hardware
---

### Post by device-user on 2018-07-10
Hi All,
I have some Dell monitors (U2711 and U2715H) which I am using with MST (daisy chaining trough DisplayPort) to connect additional displays - The U2715H has an integrated MST hub. 
The setup works fine on Win10 with my AMD GPU and on linux but only if I use the motherboard integrated graphics (Intel HD 630 - i915 driver).

My issue is that MST has never worked for me with the AMD GPU on Ubuntu - The daisy chained screens always just mirror the display they are connected through.
I have tested Ubuntu 16.04.4 and 18.04 and a live USB of 18.04. 
The AMDGPU driver versions i've tried:  default in Ubuntu repo, Oibaf PPA (on 16.04.4 with kernels 4.13 and 4.15), AMD official 16.40 and 17.40 (on 16.04.4 with kernels 4.13 and 4.15) and AMD official 18.20 (pro and regular on 18.04 with kernel 4.15.0-24 x86_64). 

I have looked though all the threads and docs I could find for clues - I've seen many other people who say they have got it working without issue - So I'm guessing there is something weird about my GPU or driver?
The cik_support=1 kernel paramater is needed to force amdgpu driver (otherwise some kernel versions load radeon which gives blank screen)
I've also tried the amdgpu.dc=1 paramater to see if Display Code does anything different - no change.
xrandr has never shown any additional screens connected apart from the ones directly attached to the motherboard.

LSPCI details - The card is branded as a Dell R7 450 (It is a desktop PCIE card)
```
bash:~$ lspci -nnk | grep -i vga -A3
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Venus LE [Radeon HD 8830M] [1002:682b] (rev 87)
    Subsystem: Dell Venus LE / Tropo PRO-L [Radeon HD 8830M / R7 M465X] [1028:1004]
    Kernel driver in use: amdgpu
    Kernel modules: radeon, amdgpu
```

Any details which could help appreciated.
Thanks

---

