---
title: "Brasero, FireWire Burner, and Integrity Checking."
date: 2009-01-15
forum: Hardware
---

### Post by AlphaMack on 2009-01-15
First off, it drives me crazy that there is absolutely no documentation anywhere relating to Brasero...I wouldn't mind jumping in on that aspect if I'm pointed to the right place...

With that said:

I have integrity checking turned on via plugins in the version of Brasero shipped with Hardy.  Sometimes upon burning a DVD or CD using a Firewire burner I'll be prompted to put the disc back in for the integrity check.  Other times Brasero throws up an error about being unable to eject the disc (though it does).  In that case, I'll throw the disc back in and use the Check Integrity option in the menu...

- If I use the md5 included on the disc, it always fails the check.
- If I proceed with the check by default, it always passes.

I've tried doing a manual md5sum check with the first few files and they are the same as what is shown on the md5 file placed by Brasero.

Can I trust my burned discs?

When I am prompted to put the disc back in for the integrity check, does the check use the md5 on the disc (original calculation of files) or does it calculate based on the burn?  In other words, is it the same as if I were to simply select "Check Integrity" from the menu?

This is where the lack of documentation for this program is a sore spot.

K3b is not an answer as the integrity check is buggy in Hardy.

Thanks.

---

