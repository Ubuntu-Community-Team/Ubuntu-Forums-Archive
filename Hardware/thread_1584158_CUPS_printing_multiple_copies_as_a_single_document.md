---
title: "CUPS printing multiple copies as a single document"
date: 2010-09-28
forum: Hardware
---

### Post by PacShady on 2010-09-28
Hello all,

Recently installed Maverick on my computer at work, and having some issues with printing on our printers. This issue seems to exist on both a Sharp MX-3100N (using an MX-3500FN driver since Sharp's 3100N driver is useless and doesn't actually send any pages with the print job), and on a Brother MFC-9840CDW, both on a network.

CUPS appears to send a print job with multiple copies of a document as a single copy with duplicated pages. This is only really noticeable if printing double sided, as a document with an odd number of pages will start the next copy on the back of the last page of the previous copy, or on the Sharp which seems to be defaulting to using its staple sort function on all output from my computer (which then staples my multiple copies together rather than separating them).

Just wanted to see if anyone here might have an idea what's going on, before I go logging a bug report. Google appears to be useless on this one.

On a side note, if anyone happens to know why the Sharp MX-3100N driver doesn't work (sending a job to the printer with 0 pages), I'd love to get that working properly too since the 3500FN driver doesn't come with the other features I use (such as staple sorting and saddle stitching, and advanced colour settings).

'Shady

---

