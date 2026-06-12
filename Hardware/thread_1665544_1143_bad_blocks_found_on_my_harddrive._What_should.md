---
title: "1143 bad blocks found on my harddrive. What should I do?"
date: 2011-01-12
forum: Hardware
---

### Post by mr_hangman on 2011-01-12
I just scanned my 320 GB external harddrive with 

```
badblocks -svw /dev/sdc
```

It took about 26 hours to finish and the result was

```
Pass completed, 1143 bad blocks found.
```

I then used gsmartcontrol to test again but it returned no error at all.
Moreover, the SMART data says there is no reallocated sectors.

Does this mean the bad blocks are remapped and I can continue using the drive without any problem, or the bad blocks are there but gsmartcontrol failed to identify them?
If it's the latter case, how can I fix it?

---

### Post by mr_hangman on 2011-01-16
I would appreciate if anyone can give me some info on this.
Right now I'm really concerned about losing data on this drive.

Thank you very much

---

### Post by efflandt on 2011-01-16
If the drive manufacturer has a utility, I would try doing a complete non-destructive test with that.

While it is possible that there is some Linux incompatibility with your hardware, I have never seen that.  In the rare cases that I have had bad sectors, the utility from the drive manufacturer confirmed that there was a problem.

So I would tread carefully and not use that drive for anything essential.

PS: I did not even know SMART could work with an external drive (at least not if USB).  But any utility testing other than that should work fine on USB.

---

### Post by mr_hangman on 2011-01-16
Thanks efflandt.
I totally forgot about the manufacturer utility. I'll give it a try.

About SMART on usb, if you're right then that will explain why Disk utility cannot find those bad sectors on my ext drive ;).

---

### Post by psusi on 2011-01-16
What about pending and offline_uncorrectable?  They don't get remapped until you try to write to them.

---

### Post by mr_hangman on 2011-01-29
I have tested the drive with manufacturer's software. 
The extended test which took about 15 hours said there was no problem with the drive and the result was Passed.
However, I'm still concerned about the reliability of the test and may not store important data on this drive. Thanks a lot guys ;)

---

