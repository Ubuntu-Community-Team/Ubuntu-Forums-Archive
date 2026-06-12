---
title: "cups - test page says Completed but doesn't really print"
date: 2009-10-24
forum: Hardware
---

### Post by aaronp on 2009-10-24
Hi all,

I've had this problem for a while but my printer ran out of ink and this de-motivated me from fixing the issue!!
Anyway, I just got a new cartridge and I was secretly hoping the issue would have just gone away when I hooked up the printer again (you know...had a few kernel updates since last time I tried it!) 
No such luck...

Hoping someone can help, thanks in advance...

OK, I have a Canon Pixma IP3300. I've managed to obtain the ip3300 driver (cnijfilter-ip3300_2.70-3_i386.deb)
When I plug the printer into the USB port within a few seconds it tells me my IP3300 is installed and ready to use. It uses the correct driver v2.70 and everything appears ok.

However, no matter what I print it just says the job completed successfully but the printer does not react at all.

I get a feeling the print job may be going to some incorrect driectory where it is just being 'black holed' instead of the correct print spooling directory but I know very little about printing and CUPS so no idea how to find out if this is the case.

Any ideas guys?

thanks
Aaron

---

### Post by aaronp on 2009-10-24
FYI - further to the above, I also have the Cups PDF printer installed and it works fine.

---

### Post by aaronp on 2009-10-25
bump...

---

### Post by aaronp on 2009-10-29
bumping again...

new info now

I've upgraded to Karmic RC (upgraded by formatting my root partition and installing Karmic fresh - keeping home drive on separate partition)

After setting up my printer (using the same ip3300 2.70 deb file) I am still having exactly the same issue.

Does this help to narrow down where the problem is?

thanks

---

### Post by ponlerd on 2009-11-04
> **aaronp said:**
> bumping again...

new info now

I've upgraded to Karmic RC (upgraded by formatting my root partition and installing Karmic fresh - keeping home drive on separate partition)

After setting up my printer (using the same ip3300 2.70 deb file) I am still having exactly the same issue.

Does this help to narrow down where the problem is?

thanks


i'm having the same problem with Canon LBP-2900
found this one , though
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/375763](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/375763)

doesn't help me , but may be in use for your case

---

### Post by aaronp on 2009-11-05
> **ponlerd said:**
> i'm having the same problem with Canon LBP-2900
found this one , though
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/375763](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/375763)

doesn't help me , but may be in use for your case

Thanks for your response. Unfortunately this bug does not help me either.
I've tried both the pdftops file replacement and the disabling of apparmour with no luck.

Interestingly I installed turboprint and am easily printing with no problems. Not too keen on paying $50 to use my printer though...I could almost buy a new one for that!!

I'd be interested to find out what is happening through turboprint that I can't get to happen through cups.
Again, I have no idea where to start analysing this. Anyone able to help with that process?

thanks
Aaron

---

### Post by aaronp on 2009-11-06
Is there anyone that can help diagnose this??
truboprint ok, cups not...

---

### Post by DedMoroz on 2009-11-09
I found that Okular will print the PDF fine, but Document Viewer does not. Until Canonical get this fixed, try using Okular.

---

### Post by Elwro on 2010-05-07
Just wanted to report that I'm having this issue after the upgrade to Lucid. Okular prints, Document Viewer / Adobe Reader do not!

---

