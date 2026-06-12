---
title: "[SOLVED] OpenOffice crashes after java runtime update"
date: 2008-10-26
forum: General Help
---

### Post by Zeedok on 2008-10-26
I encountered a problem this morning and couldn't find the solution on the forum.  Happily I also stumbled across the solution and though I'd post it here in case it is of any help to someone else.

I update my 8.04 (Hardy) system religiously (I've even upgraded my secondary PC to 8.10 intrepid RC1).  Over the weekend (or at least in the last few days) I noticed that an update included a new version of the java runtime environment.  This morning, whenever I tried to use any database functions in OpenOffice (eg a flat-file database I created for addresses in writer, or a database form) it would crash.  When I tried to re-open the document, I would have the document recovery dialogue and then when I tried the same functions . . . it would crash again.  I kind of thought it might relate to java (I have used portable OpenOffice on computers without JRE in the past and the same functions that were crashing this morning did not work).

After some searching (unsuccessfully) I looked in Tools -> Options -> OpenOffice.org -> Java and found that OpenOffice had not enabled java.  I enabled my JRE and everything is back to normal.

Hope this is helpful for someone.

---

