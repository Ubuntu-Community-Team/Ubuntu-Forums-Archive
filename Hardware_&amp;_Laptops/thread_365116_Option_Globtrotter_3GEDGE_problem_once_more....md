---
title: "Option Globtrotter 3G/EDGE problem once more..."
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by ea66 on 2007-02-19
Hi, there!
I have a bit of a problem with my Option 3G pcmcia card, and after reading quite a few FAQ and howto's I'm not a step closer to a solusion.
I'm running HP nx6310 laptop with Ubuntu 6.10 installed [kernel 2.6.17.11-generic]. Now the first problem is that after typing cardctl status to check if the pcmcia is working a get something like this [no card is inserted]:
```
Socket 0:
ioctl(): Invalid argument

```
After inserting the card the Led start to flash, but the output of cardctl status shows no change.
Then I typed lspci -v and it apears that the card has ben detected:
```
03:00.0 Network controller: Option N.V. Unknown device 000c
        Flags: medium devsel, IRQ 177
        Memory at 22000000 (32-bit, non-prefetchable) [disabled] [size=2K]

```
Now I know that this card should work either as a USB hub or a serial modem and that kernel shoud generate somekind of message but it does not:
```
[17179638.344000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: cardctl.
[17179638.344000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17179638.344000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[17179725.700000] pccard: CardBus card inserted into slot 0

```
And that's all. I know I have a problem with my pcmcia  have interface but I don't have a 
clue where to start. Any suggestions?

---

### Post by Julian Weaver on 2007-03-25
Have you read the helpful stuff on Paul Hardwick's site?

[www.pharscape.org](www.pharscape.org)

I'm wrestling the same sort of issues on a Sony Vaio with a 3G card, plus being a complete newb on Linux, but found a lot of useful stuff plus links here.

Good luck

---

