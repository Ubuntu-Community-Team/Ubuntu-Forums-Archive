---
title: "Open Source Radeon Driver"
date: 2009-09-06
forum: Hardware
---

### Post by PostChache on 2009-09-06
I've been trying to get an Open Source Radeon Driver following this guide



[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I've gone all the way through up to the section that's called "restarting" Whenever I restart or logout It tells me my computer is running in low graphic setting. I don't know how to fix it and I don't know if I did anything wrong.

I have a Mobility Radeon 3650 Ubuntu 9.04 64bit

Okay, now I have it running right but I can't enable Extra Visual Effects now. In the guide it says it should support Visual Effects and Compiz right after instillation. I didn't manually configure my x.org I just let it do auto could this be a problem?

---

### Post by PorkyPie on 2009-09-06
I think you made a mistake in the link. Which guide is it?

---

### Post by PostChache on 2009-09-06
> **PorkyPie said:**
> I think you made a mistake in the link. Which guide is it?
I fixed it sorry about that.

---

### Post by PorkyPie on 2009-09-06
I'm unsure if your card is supported. Try the official ATi drivers.

Run this in the terminal and tell me what the outcome is:

```
$ lspci -nn | grep VGA
```

---

### Post by PostChache on 2009-09-06
> **PorkyPie said:**
> I'm unsure if your card is supported. Try the official ATi drivers.

Run this in the terminal and tell me what the outcome is:

```
$ lspci -nn | grep VGA
```


I can use the offical one but it gives me problems.

```
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591] 
```

---

### Post by PorkyPie on 2009-09-06
> **PostChache said:**
> I can use the offical one but it gives me problems.

```
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591] 
```

Have you tried the raedonhd driver?

---

### Post by PostChache on 2009-09-06
> **PorkyPie said:**
> Have you tried the raedonhd driver?
I've only tried the Proprietary drive

---

### Post by PostChache on 2009-09-06
Okay, now I have it running right but I can't enable Extra Visual Effects now. In the guide it says it should support Visual Effects and Compiz right after instillation. I didn't manually configure my x.org I just let it do auto could this be a problem?

---

