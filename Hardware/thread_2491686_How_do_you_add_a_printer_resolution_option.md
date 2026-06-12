---
title: "How do you add a printer resolution option?"
date: 2023-10-17
forum: Hardware
---

### Post by c7890 on 2023-10-17
Hello,

I'd like to add a "300x300 DPI" option for printing and I only have the options of 600 and 1200. The options are the same no matter which option I choose: system dialog, CUPS (localhost:631), or printing from an application (e.g., File, Print in LibreOffice). These are dropdown options with no ability to add a different option.

I have a Brother MFC-L2710DW printer and used the Brother .deb drivers from their webpage. It's connected via USB. I can print and scan, but I often get an "out of memory" message on the printer, even on two-page text documents. Supposedly it would help if the resolution could be set to 300 DPI. Is there a file I can edit that would allow me to add this option?

Thanks in advance.

---

### Post by TheFu on 2023-10-17
Resolution
    600 x 600 dpi, HQ1200 (2400 x 600 dpi) quality, 1200 x 1200 dpi

According to the printer specifications. So you can't get anything except those.
Ref: [https://support.brother.com/g/b/spec.aspx?c=us&lang=en&prod=mfcl2710dw_us_eu_as](https://support.brother.com/g/b/spec.aspx?c=us&lang=en&prod=mfcl2710dw_us_eu_as)

As for memory, make the source images at lower resolution.  64MB of memory should be sufficient compared to how little printers had in the 1990s that handled very complex printing. Looks like it can print using PDF or PCL, so you could try sending both of those output types. Also, it supports AirPrint (aka Driverless printing), so in theory, no drivers should be necessary, at least for printing.

---

### Post by c7890 on 2023-10-29
Thanks for confirming the available options and for the recommendations! It turns out the two pages of text I was trying to print had embedded image backgrounds which were very faint and I hadn't noticed them at first. Evidently they were large enough to cause the memory problems.

---

