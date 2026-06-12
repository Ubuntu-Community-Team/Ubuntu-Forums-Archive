---
title: "Mathtype equations in OpenOffice"
date: 2008-07-28
forum: General Help
---

### Post by yesint on 2008-07-28
Dear All,
I have a big trouble with Open Office. I need to open the word document with many MathType formulas made in MSWord in Windows. The document opens, but all integral, sum and derivative symbols in formulas are screwed up completely.  
This seems to be well-known issue, but there are no solutions or workarounds. I tried to submit a bug to OO ([http://www.mail-archive.com/allbugs@openoffice.org/msg396313.html](http://www.mail-archive.com/allbugs@openoffice.org/msg396313.html)), but some guy immediately said that it is not reproduced and closed it. 
I need an advice - does it make sense to post this bug to ubntu? I don't believe that this is ubuntu-specific bug, but who knows... 
Any ideas how to fix this issue?

---

### Post by gaussian on 2008-07-28
> **yesint said:**
> Dear All,
I have a big trouble with Open Office. I need to open the word document with many MathType formulas made in MSWord in Windows. The document opens, but all integral, sum and derivative symbols in formulas are screwed up completely.  
This seems to be well-known issue, but there are no solutions or workarounds. I tried to submit a bug to OO ([http://www.mail-archive.com/allbugs@openoffice.org/msg396313.html](http://www.mail-archive.com/allbugs@openoffice.org/msg396313.html)), but some guy immediately said that it is not reproduced and closed it. 
I need an advice - does it make sense to post this bug to ubntu? I don't believe that this is ubuntu-specific bug, but who knows... 
Any ideas how to fix this issue?

Correct me if I am wrong here: OpenOffice under Ubuntu will open (mostly) correctly math typed with Word Equation Editor. It will not open math typed with MathType a proprietary Windows/Mac program for typing math? My guess is that this would be a feature request, not a bug (and not a Ubuntu issue).

If my hunch is correct, your bug discussion might have suffered from misunderstanding Equation Editor/MathType-issue.

---

### Post by yesint on 2008-08-10
I understand the difference between Equation Editor and MathType very well. OO opens equation editor formulas with no problems, but Mathtype formulas are messed up. However, in the preferences of OO there is an option "Convert math to/from Mathtype", so I guess that this support is included, but there is a bug.

---

### Post by gaussian on 2008-08-10
Ok, I take back my previous post. Apologies for misunderstanding the issue.

---

### Post by gaussian on 2008-08-10
I tried your attachment from your OO bug report.
1. Ubuntu 7.10: Math does not come right
2. Ubuntu 8.10 (Alpha): Math does not come right
3. Mandriva Spring (OO 2.4.1): Math is perfect

So it does look like a Ubuntu issue (maybe missing fonts or something).

---

### Post by yesint on 2008-08-11
Many thanks for confirming this issue! I started to think already that something is wrong with my particular system.
Does it make sense to submit a bug report to Ubuntu team?

---

### Post by gaussian on 2008-08-11
> **yesint said:**
> Many thanks for confirming this issue! I started to think already that something is wrong with my particular system.
Does it make sense to submit a bug report to Ubuntu team?

It does to me. Even more curious: I installed OpenOffice 3.0 Beta on my Ubuntu System (Packed by Sun). Even with that the fonts did not come right. This to me seems to suggest that Ubuntu is missing some font needed to show that file or has some font replacement config wrong.

---

### Post by yesint on 2008-08-12
The bug is submitted to launchpad.

---

### Post by arkashkin on 2008-12-07
No one does anything about it and i must have this feature for not loading each time virtual machine to use Windows for converting *.doc to *.pdf.... and then viewing the *.pdf back in ubuntu....

:(

---

### Post by yesint on 2008-12-08
This bug is now forwarded to OO again. Unfortunately the OO team is doing nothing with it for a long time already. This is sad.
The only good solution so far is to keep Windows in virtual machine for editing doc's.

---

