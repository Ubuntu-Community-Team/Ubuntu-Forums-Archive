---
title: "What happened with &quot;Print to File&quot; in OOo? (CUPS/OOo)"
date: 2008-11-28
forum: General Help
---

### Post by Piraja on 2008-11-28
Why oh why is the CUPS package (I presume) continuously updated in most surprising manners? First they deprecated CUPS-PDF and now something else has happened... Or was it the recent OpenOffice updates that caused this? (Must have been the latter, and I don't miss the cups-pdf package any longer, so I'm not ranting against CUPS... and I'm not ranting at all, just curious.)

I was just working with OpenOffice Writer, chose File > Print... and expected to see the usual dialog with a "Print to file" option &#8212; but what do I see? No "Print to file" but "AdobePDF7" instead! What the funk?! Now I really don't get it... Who's been messin' around, huh? Me?

I mean, I don't think AdobePDF should be on my desktop at all &#8212; could it be that I'm seeing a neighbour's printing options via bluetooth or something... (There has been an extra laser printer available lately in my printing dialog box, and I presume it's my next-door neighbour's. Which is a bit confusing, IMO.)

I tried AdobePDF just to see what happens. Now the printing process has been "pending" for 8 minutes (I just closed it).

Well, I can always use "Export to PDF..." but I really, really appreciated having "Print to file" also in OpenOffice (it's still there when I want to print from e.g. Firefox).

---

### Post by Piraja on 2008-11-28
I just realized that a "Print to file" option still exists, not in the drop-down menu but as a checkbox (see the screenshot below), and not directly as a print-to-pdf but as PostScript. And, what is more, if I choose to export as PDF, for some reason I cannot print the comments added in OOo Writer (a bug, maybe?), only the main text.

Everything was pretty simple before yesterday's OpenOffice security updates... I want "Print to file" back in the drop-down print menu as it used to be! Grrr...

Well, maybe I should file a bug upstream instead of ranting here?

---

### Post by _sAm_ on 2008-11-28
The package **cups-pdf** where missing when I installed Ubuntu 8.10, but after installing it(in Synaptic) I could (again) print to pdf as before(as in OpenOffice). I don't see any AdobePDF7 option, and I have updated my system. 

I have no clue why it was missing:-/

---

### Post by Piraja on 2008-11-28
Thanks for the comment. Also I re-installed cups-pdf after I noticed it was gone in Intrepid. However, the option to "Print to file" makes cups-pdf redundant, as far as I can see, and therefore I removed cups-pdf. And now this option is gone in Open Office.

---

