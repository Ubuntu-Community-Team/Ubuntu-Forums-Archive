---
title: "5k monitor: select graphic card"
date: 2016-11-02
forum: Hardware
---

### Post by deepmindster on 2016-11-02
Hello

I would like to buy 5k monitor Dell UP2715k. For using in full resolution monitor requires 2x displayport graphic card. My current card does not have display port. So, I need select to a card.

My first criteria is that monitor should work with full resolution. I [found]("http://askubuntu.com/questions/715055/ubuntu-support-for-5k-dell-up2715k-adjusting-details") in internet that it is possible with nvidia drivers, but with some limitations. It is okay to me (hope it is better now still).

My second criteria is that I would like to use free driver. In such case I think I need to select amd card (my platform is amd now, so, I do not have a way to use intel integrated card).
Dell recommends FirePro and Radeon series.

Well, here is the question. We have 2 drivers: radeon and amdgpu. Will they both do?

The second part of question: generally, I would like to use amdgpu because I think it is under active development and support of features I need may likely be enhanced in future. How to know which card is suppored by amdgpu? I found [gentoo wiki]("https://wiki.gentoo.org/wiki/Amdgpu"), but i'm not sure how old the information is. Where official amdgpu information can be found?

Thank you.

PS. Administrators, I would suggest tags "monitors 5k" and "monitors 4k".

---

### Post by QIII on 2016-11-02
On cell, so hard to leave a link.

But check out wikipedia and look for "amd gpu"

Any card listed as "GCN 1.2" or "GCN 1.3" will work right now with AMDGPU driver or the additional proprietary layer AMDGPU-Pro.  Support for 1.0 and 1.1 is coming, but not available yet.

Shop carefully, not all cards support 4k.

And don't immediately avoid NVIDIA.  Right now the AMD driver situation is in so much turmoil that you should not tie yourself to AMD.

---

### Post by deepmindster on 2016-11-02
I see. Thanks for the answer. I see now how to know if amdgpu supports the card.

But i'm not sure I see right: you mean if card is suppored by amdgpu and card can do what I need , then it will work for me. So, amdgpu support for cards of GCN 1.2 and GCN 1.3 is "full", right?

---

