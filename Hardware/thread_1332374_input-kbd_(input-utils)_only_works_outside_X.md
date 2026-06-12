---
title: "input-kbd (input-utils) only works outside X"
date: 2009-11-20
forum: Hardware
---

### Post by apfsdsdu on 2009-11-20
I've got an IR remote which I'd like to look like a keyboard to the OS. The program that I've used for this previously is input-kbd from the input-utils package. It used to work just fine until Karmic, but now it only works outside of X. I guess the problem is somehow related to some changes in the way X handles input, but I have no idea how to fix it. I'd like X to use the same input device as the non-X consoles, whatever it is. 

The budget-ci kernel module, which I assume is the module that passes the IR input to the kernel, needs some options to work properly, but I don't think this is a kernel problem because the keyboard mapping works, X just doesn't see it.

---

### Post by apfsdsdu on 2009-11-21
I got it working by having a cat command running, copying everything that comes out of the IR input device to the keyboard device.

---

