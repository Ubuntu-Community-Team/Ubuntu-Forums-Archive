---
title: "Some applications freezing when I hit &quot;print&quot;"
date: 2008-10-09
forum: General Help
---

### Post by sceo on 2008-10-09
When I try to print from evince, gedit, or firefox, they all lock up and require a "force quit."  Printing the test page from Administration->Printers works, as does printing from OpenOffice.

So what does these three programs use that OpenOffice doesn't?

I have tried to tail -f the access_log and error_log for cups both on my local ubuntu machine, and the remote mythbuntu machine to which the printer is actually attached.  Nothing shows anything.

I have also tried running evince and gedit from the command-line, to see if they spit anything out, but they don't.

Any thoughts on where else to look to try and pin down even an error message?

I also noticed - I downloaded xpdf, and when I tried to print from there it asked me "print with command" (and lpr) was filled in.  I just hit OK to the defaults and it worked.  So I guess lpr is working - so what does Firefox try and use that's different?  CUPS I guess?

---

