---
title: "One 3D card that supports Dual Seat?"
date: 2014-04-21
forum: Hardware
---

### Post by clintonm on 2014-04-21
I've been thinking about purchasing a new computer and would like to be dual seat capable (i.e. two keyboards, two mice, two screens for two physical simultaneous sessions).I understand that Xephyr can make dual seats fairly easily, but it doesn't support 3d acceleration. For 3d acceleration you need two xservers, and an xserver needs it's own "device". That is, you need two video cards (or a video card + APU) to run two seats with 3d acceleration. However, I read there is some exceptions to this, in that some cards the "heads" (i.e. monitor connections) have separately addressable PCI numbers.i.e. On some cards "lspci | grep VGA" returns two results instead of one.As I'd rather not have to buy two video cards, is there a listing or does anyone have a recommendation of a card (or APU) that supports this? Alternatively, is there any other way to get 3d accelerated dual seat working on a single video card?

---

