---
title: "Fresh 8.10 installed but won't boot."
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Pax Felix on 2009-02-13
I started an earlier thread about this, but it got no traction and I think it was titled poorly.  So I'm trying again.

I've been rocking along with Ubuntu at home for a few days, getting the hang of it, and decided it was time to install it at the office. When I went to the page to download Wubi to this work computer, I found that only the updated Wubi for Ubuntu 8.10 is available. Fine, I thought, that will spare me one installation (8.04) followed by an upgrade (8.10). The Wubi download went just fine, and there appeared to be no glitches with the Ubuntu download or installation.

However, on rebooting, the screen with the logo and progress bar appears, not with the splash insert, and then the trouble begins. Rather than the login page, what follows the logo page is this: The monitor appears with no window of any kind, white unicode on black background. I'm no programmer, but I'm guessing this is code of some kind. There is the following recursive paragraph:

<4digits>.<6digits>]  ata2.00: exception Emask 0X0 SAct 0X0 SErr 0X0 action 0X0 frozen
      "       .    "        ]  ata2.00: cmd <long string of digits, mostly 0's> tag ) pio36 in
      "       .    "        ]               cdb  <long string of digits>
      "       .    "        ]               res   <long string of digits> Emask 0X4 (timeo.)
      "       .    "        ]  ata2.00: status: {DRDY}

Where each line of <long string of digits> varies within each paragraph.

For each subsequent iteration of the paragraph, the values of the <4digits> and <6digits> increase, but the remainder of subsequent paragraphs are identical. Even the <long string of digits>'s remain identical, Line 1 with Line 1, Line 2 with Line 2, Line 3 with Line 3.

Each attempt to reboot yields the same result.

I uninstalled, and the same thing happened with Kubuntu and Xubuntu.

If it makes any difference, my office machine's current OS is Vista.

Thanks for anyone's time to consider this and suggestions.

Be well,
Tony

---

### Post by lemming465 on 2009-02-14
The message looks like there is a bug in the disk controller support.

The first thing I'd do is switch to experiments involving live CD's; until you get the hardware sorted out stay away from installing, even using WUBI.
If an Ubuntu 8.10 live desktop CD has the same bug, try a Fedora 10 CD instead.

One thing that can help is BIOS updates; see if you have any of those pending.

It's also possible that changing disk controller options in the BIOS will help, but make careful notes so you can set things back, in case you break Vista with a settings change.

People may be able to give you more specific and less generic advice if you can post the machine vendor and model.  The motherboard model would be particularly helpful.

---

### Post by Pax Felix on 2009-02-16
Many thanks!

Dell Optiplex 740

AMD Athlon 64 Processor3500+  2.20GHz

2GB RAM

32-bit version of Vista

---

### Post by AllenGG on 2009-02-16
Did you use a 64 bit version of 8.10 ?

---

### Post by Pax Felix on 2009-02-16
No -- The reviews I've seen of 64-bit Operating Systems, whether Windows or Linux, have generally suggested less than 50/50 satisfaction.  It actually did not occur to me that one might work when the other did not.  But if someone familiar with Ubuntu thinks it would work on the 64-bit platforms, I'm certainly willing to give it a go.

---

### Post by AllenGG on 2009-02-18
Pax Felix ; 5 years ago  Ubuntu was the only 64 bit distro that would work on my Asus - AMD  64
True, doing it then was pioneering, and many people chose to stick with 32 bit.
Installing 8.10 a few months ago, fresh, on a new Core duo (Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz) It was up, running and on the net in 12 minutes.

But it was a "fresh" install.
Allengg

---

