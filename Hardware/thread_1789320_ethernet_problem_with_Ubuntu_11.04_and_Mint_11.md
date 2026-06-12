---
title: "ethernet problem with Ubuntu 11.04 and Mint 11"
date: 2011-06-23
forum: Hardware
---

### Post by nstgc379 on 2011-06-23
I recently upgrade my computer and it seems as if my hardware isn't supported. I don't know what to do.

I have Gigabyte GA-z68X-UD3P-B3 motherboard which comes with onboard Realtek RTL811E ethernet controller. WIth Mint 10, I was getting sparse connectivity, at very poor speeds. Then I tired Mint 11, and I didn't get any connectivity. I then tried Ubuntu 11.04, and am having the same problem. I searched google, but it seems there are no answers since the board is new.

---

### Post by ratcheer on 2011-06-23
I would bet anything that it is loading the wrong driver. If it is using r8169, it needs to use r8168. Run "sudo lspci -v" to find out.

If it is using r8169, you will need to go to Realtek's Taiwan website to download the correct driver for Linux. Then search on r8168 in this forum to find any of my several threads on how to install it.

Tim

---

### Post by nstgc379 on 2011-06-23
I already looked at the RT's site for drivers. I found the 8101 drivers, but I couldn't find the ones specifically for my computer.

---

