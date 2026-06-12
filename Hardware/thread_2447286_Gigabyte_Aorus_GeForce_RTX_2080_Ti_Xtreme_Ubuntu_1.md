---
title: "Gigabyte Aorus GeForce RTX 2080 Ti Xtreme Ubuntu 16.04"
date: 2020-07-16
forum: Hardware
---

### Post by fcis on 2020-07-16
[COLOR=#242729][FONT=Arial]I have a current ubuntu 16.04 machine which has one GPU GeForce GTX 970. I am now going to add one more GPU and thinking about Gigabyte Aorus GeForce RTX 2080 Ti Xtreme. I wonder if it would work on Ubuntu 16.04? and if so will it work along with my older GeForce GTX 970?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also wonder if anyone could advise me which one is better among these:[/FONT][/COLOR]

[LIST]
[*]Gigabyte Aorus GeForce RTX 2080 Ti Xtreme 11G
[*]Gigabyte GeForce Aorus RTX 2080 Ti
[*]Gigabyte GeForce RTX 2080 Ti Gaming OC
[/LIST]

---

### Post by mastablasta on 2020-07-17
i would suggest to at least upgrade the kernel (use HWE). 

2 different cards might not work well together. it depends on how well this option is supported by nvidia.

looks like new AMD cards will be better than these. not sure if they are selling yet.

---

### Post by fcis on 2020-07-17
> **mastablasta said:**
> i would suggest to at least upgrade the kernel (use HWE). 

2 different cards might not work well together. it depends on how well this option is supported by nvidia.

looks like new AMD cards will be better than these. not sure if they are selling yet.


Okay which one of these three you think is the best? and could you recommend some AMDs to check? Thanks for your help.

---

### Post by Yellow Pasque on 2020-07-17
Make sure you have 430.64 driver: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=xenial)

> will it work along with my older GeForce GTX 970 ... and could you recommend some AMDs to check? 

If you're going to try and run a GTX970 at the same time as a new card, you are better off sticking to Nvidia.


EDIT: As to which card is better, they all look the same with just a little difference in clock speed... [https://www.gigabyte.com/Comparison/Result/3?pids=6707,6731,6732](https://www.gigabyte.com/Comparison/Result/3?pids=6707,6731,6732)

---

### Post by Autodave on 2020-07-17
[https://gpu.userbenchmark.com/Compare/Nvidia-RTX-2080-Ti-vs-Nvidia-GTX-970/4027vs2577](https://gpu.userbenchmark.com/Compare/Nvidia-RTX-2080-Ti-vs-Nvidia-GTX-970/4027vs2577)   The 2080 is superior to the 970.

---

### Post by Yellow Pasque on 2020-07-17
> **Autodave said:**
> The 2080 is superior to the 970.

That's not what the OP was asking.

---

### Post by fcis on 2020-07-17
> **Yellow Pasque said:**
> 

If you're going to try and run a GTX970 at the same time as a new card, you are better off sticking to Nvidia.

[https://www.gigabyte.com/Comparison/Result/3?pids=6707,6731,6732](https://www.gigabyte.com/Comparison/Result/3?pids=6707,6731,6732)

But all these are Nvidia, right? So they should be okay with the older GPU, right?

---

### Post by Yellow Pasque on 2020-07-17
What are you trying to do with multiple GPU's? The 2080 has a ton of outputs. Do you have more than 6 displays?

---

### Post by fcis on 2020-07-18
> **Yellow Pasque said:**
> What are you trying to do with multiple GPU's? The 2080 has a ton of outputs. Do you have more than 6 displays?

No, I have one monitor, mainly I use them for image processing, data modelling,....so the more GPUs the faster I can process data.

---

### Post by CatKiller on 2020-07-19
> **fcis said:**
> I am now going to add one more GPU and thinking about Gigabyte Aorus GeForce RTX 2080 Ti Xtreme.

The 970 is a 150 W part. The 2080 Ti is a 300 W part. Running both of them means that you'll need 450 W of additional power and cooling on top of that needed by the rest of the system. While it's possible that you gave yourself a +200% overhead when you initially built your system, it's not a given.

Upgrading to at least 18.04, but likely 20.04, will make things easier because of the ease of using a newer kernel for the newer driver. If you want to keep using the old card as well as the new card you'll want the new card to be from Nvidia, as already mentioned. Mixing the proprietary driver with an open source graphics stack (see Optimus) is a complete pain. The single proprietary driver supports a wide range of Nvidia cards. 

You won't be able to use both cards *together*, since the method to do that changed from SLI to another thing that I can't remember the name of, you'd need both cards to have similar capabilities, and it wasn't that well supported anyway. You should still be able to use both as CUDA targets, though.

---

### Post by fcis on 2020-07-19
> **CatKiller said:**
> The 970 is a 150 W part. The 2080 Ti is a 300 W part. Running both of them means that you'll need 450 W of additional power and cooling on top of that needed by the rest of the system. While it's possible that you gave yourself a +200% overhead when you initially built your system, it's not a given.

Upgrading to at least 18.04, but likely 20.04, will make things easier because of the ease of using a newer kernel for the newer driver. If you want to keep using the old card as well as the new card you'll want the new card to be from Nvidia, as already mentioned. Mixing the proprietary driver with an open source graphics stack (see Optimus) is a complete pain. The single proprietary driver supports a wide range of Nvidia cards. 

You won't be able to use both cards *together*, since the method to do that changed from SLI to another thing that I can't remember the name of, you'd need both cards to have similar capabilities, and it wasn't that well supported anyway. You should still be able to use both as CUDA targets, though.


- Thank you, so better remove the old I guess. If this is the case, would it matter using an Nvidia made one or Gigabyte would work or not? if so then which one I should buy from the 3 mentioned in my question since they are all Nvidia, right? or I should stick with the Nvidia made one?

- I didn't understand what you meant by "Mixing the proprietary driver with an open source graphics stack (see Optimus) is a complete pain. The single proprietary driver supports a wide range of Nvidia cards. "?

- What do you mean by "You should still be able to use both as CUDA targets"?

Thank you for your help.

---

### Post by CatKiller on 2020-07-19
> **fcis said:**
> - Thank you, so better remove the old I guess. 
If you're removing the old one, then the new one can be whatever card meets your needs and fits your power, cooling, and monetary budget. 
> If this is the case, would it matter using an Nvidia made one or Gigabyte would work or not? 
The manufacturer doesn't really matter. That determines pricing, size, fan design, default overclock, that kind of thing, not how and whether it works. 

> if so then which one I should buy from the 3 mentioned in my question since they are all Nvidia, right? or I should stick with the Nvidia made one? 

The three you picked are essentially all the same card, which is essentially the same card as the Nvidia Founder's Edition cards. Nvidia design the chips, TSMC make the chips, and the manufacturers - like Gigabyte, Nvidia, EVGA, or whoever - put the chips on a circuit board and put fans on. 

>  - I didn't understand what you meant by "Mixing the proprietary driver with an open source graphics stack (see Optimus) is a complete pain. The single proprietary driver supports a wide range of Nvidia cards. "? 

If you're using Intel or AMD graphics, all of the graphics stack is open source. The Nvidia driver is proprietary (and essentially the same as their Windows driver) so certain parts do things the way that makes sense for Nvidia rather than the way everyone else does them. Using just the open source stack works well, using just the proprietary stack works well; mixing them, like some laptops do, or like you'd do if you had an Nvidia card and an AMD card, is a pain. 

>  - What do you mean by "You should still be able to use both as CUDA targets"?

Using multiple GPUs for graphics means that they need to communicate quickly with each other to keep everything in sync. You wouldn't be able to do that. Using multiple GPUs for computation means that you just need to send off your chunk of work to them and get the results back; they don't need to talk to each other. You should be able to do that.

---

