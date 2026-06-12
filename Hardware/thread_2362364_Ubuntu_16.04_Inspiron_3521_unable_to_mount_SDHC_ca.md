---
title: "Ubuntu 16.04 Inspiron 3521 unable to mount SDHC card used in photography"
date: 2017-05-27
forum: Hardware
---

### Post by noket on 2017-05-27
**Hardware Specs: **Dell Inspiron 15-3521
**Software: **Ubuntu 16.04 LTS
**Issue: **unable to read or mount SDHC card. 

**Details:**

I have been unable to mount this card in the past via the built in card reader.

The specific card is: Transcend 600x 90MB/s 32GB, Serial codes 9181AA FG 07DD1, and D40889 0905

In the past, I had used a USB card adapter to read the card, however this recently stopped working. Adapter details are Xit PHOTO with slogan "Capture the spot".

When I reconnect the adapter with inserted memory card, the following messages are dumped into the kernel log:
[https://pastebin.com/pqREXANY](https://pastebin.com/pqREXANY)

I have already tried the solutions suggested in other threads regarding fixing this SDHC mounting issue without success. 

My goal is to be able to use either the direct SD card port, the adapter, or both.

Let me know if there are any other outputs I should provide.

---

### Post by noket on 2017-05-27
As per advice on the following thread, the issue has been resolved: [https://www.reddit.com/r/linuxmint/comments/1p6761/sd_cards_stopped_working_dmesg_included/](https://www.reddit.com/r/linuxmint/comments/1p6761/sd_cards_stopped_working_dmesg_included/)

Formatting the SD card with my camera solved the issue, and my computer recognizes the card via the USB adapter. Unfortunately, I also lost all my photos.

---

