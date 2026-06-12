---
title: "aticonfig cannot see second graphics card"
date: 2013-03-03
forum: Hardware
---

### Post by tmahring on 2013-03-03
Hi. I have two graphics cards in my system, one AMD Radeon HD 6950 and one Radeon HD 2600. I want to use them with 3 monitors, two of them connected to the 6950 and one to the 2600.
Both cards list fine when I do lspci:

```

lspci
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cayman PRO [Radeon HD 6950]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 2600 Series]
```

however, the aticonfig utility can only see the 6950:

```

aticonfig --list-adapters
* 0. 01:00.0 AMD Radeon HD 6900 Series

* - Default adapter
```

so obviously aticonfig --adapter=all --initial also only creates the config for the 6950 and amdcccle also only sees the 6950.
Has anyone a clue what I'm doing wrong ?
Do I maybe need to tell the fglrx module somehow that there is a second card ? I only had the 6950 installed when i installed the fglrx drivers.

---

### Post by Cheesemill on 2013-03-04
What version of Ubuntu are you using?

Neither 12.04.2 or 12.10 will work with a 2600 using the restricted drivers as ATI dropped support for all 2/3/4xxx cards last summer.

---

### Post by tmahring on 2013-03-04
damn ! I was afraid of something like that.
I thought it would work because the amd site lists driver version 13.1 for both cards - I just checked again and found out that there is a normal 13.1 and a legacy 13.1 version, didn't see that befor.
Is there maybe a way to use the open source drivers for the 2600 and the propriatory ones for the 6950 ? I only need 3d acceleration on the 6950.
edit: I also have an old nvidia card lying around (7300GT if I'm not mistaken), I had it in my pc befor I put in the 2600, but I removed it because ubutu wouldn't boot anymore after I installed the fglrx drivers. Is there maybe a way to get this card working for the third monitor ?

---

