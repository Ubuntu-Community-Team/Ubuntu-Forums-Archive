---
title: "Microsoft Wireless Media Desktop Keyboard and Mouse Combo 1000, TRENDnet KVM Switch"
date: 2010-05-29
forum: Hardware
---

### Post by matthewetaft on 2010-05-29
I searched high and low for this answer, and finally found it.  I am soooo glad!  Thought I would post this so that some other confused soul might land here one day and be relieved of hours of headache.  Here's the deal:

I have two laptops, and wanted to be able to switch between them using a KVM Switch.  Most KVM switches, mine included, use the Scroll Lock key (hit twice) to switch between computers.  This doesn't work in Ubuntu; at least not with my version of Ubuntu (8.10), my Microsoft Wireless Media Desktop Keyboard and Mouse Combo 1000, and my TRENDnet TK-207 KVM Switch.

I tried studying the keycodes and mapping them differently, and none of that worked.  I found a simple solution that is killing me.  TRENDnet doesn't even mention it, but the Num Lock key also switches between computers.  Within Ubuntu, when pressing Num Lock twice, I can switch back to my other computer, which has Windows installed.  From that environment, I can click Num Lock to switch back.  Since Num Lock works in Windows and Ubuntu, it's killing me that TRENDnet only mentioned the ScrLk key, which only works in Windows.  Arg!  Anyway, I hope that helps someone.

---

