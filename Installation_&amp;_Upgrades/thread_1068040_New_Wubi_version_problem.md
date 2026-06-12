---
title: "New Wubi version problem"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Pax Felix on 2009-02-12
I've been rocking along with Ubuntu at home for a few days, getting the hang of it, and decided it was time to install it at the office.  When I went to the page to download Wubi to this work computer, I found that only the updated Wubi for Ubuntu 8.10 is available.  Fine, I thought, that will spare me one installation (8.04) followed by an upgrade (8.10).  The Wubi download went just fine, and there appeared to be no glitches with the Ubuntu download or installation.

However, on rebooting, the screen with the logo and progress bar appears, not with the splash insert, and then the trouble begins.  Rather than the login page, what follows the logo page is this:  The monitor appears with no window of any kind, white unicode on black background.  I'm no programmer, but I'm guessing this is code of some kind.  There is the following recursive paragraph:

<4digits>.<6digits>]  ata2.00: exception Emask 0X0 SAct 0X0 SErr 0X0 action 0X0 frozen
      "       .    "        ]  ata2.00: cmd <long string of digits, mostly 0's> tag ) pio36 in
      "       .    "        ]               cdb  <long string of digits>
      "       .    "        ]               res   <long string of digits> Emask 0X4 (timeo.)
      "       .    "        ]  ata2.00: status: {DRDY}

Where each line of <long string of digits> varies within each paragraph.

For each subsequent iteration of the paragraph, the values of the <4digits> and <6digits> increase, but the remainder of subsequent paragraphs are identical.  Even the <long string of digits>'s remain identical, Line 1 with Line 1, Line 2 with Line 2, Line 3 with Line 3.

Each attempt to reboot yields the same result.

If it makes any difference, my office machine's current OS is Vista.

Thanks for anyone's time to consider this and suggestions.

Be well,
Tony

---

### Post by Pax Felix on 2009-02-12
bump

---

