---
title: "hsync/vsync rates off?"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by astronouth7303 on 2007-10-20
On a custom-built desktop box: Gutsy Gibbon, Intel 965GM graphics chip, XOrg w/"intel" driver, ViewSonic Optiquest Q20wb (native res=1680x1050, over a VGA cable).

My problem is that with the exact vsync/hsync rates XOrg uses (which are slightly different than what Windows XP uses), my LCD displays 1680x1050@60Hz as 4:3 instead of full width (doesn't have this problem on windows). The rates reported by my monitor are as follows (for XOrg): Hsync=65.1KHz, Vsync=59.8Hz, pixel clock=123.0MHz. IDK what the rates were for Windows.

I had the same problem under Feisty as well, but I was able to work around it by changing my resolution to 1600x1200 and then back. This hack no longer works under Gutsy.

---

### Post by astronouth7303 on 2007-10-20
These are the rates as reported by xvidtune (**different** from what my monitor reports):
Hsync=65.29KHz
Vsync=59.95Hz
Pixel clock=146.25MHz

---

