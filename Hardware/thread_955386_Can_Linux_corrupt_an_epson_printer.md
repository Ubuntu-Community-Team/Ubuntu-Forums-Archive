---
title: "Can Linux corrupt an epson printer?"
date: 2008-10-22
forum: Hardware
---

### Post by DavidFourer on 2008-10-22
Can my linux system be currupting my Epson printer?  Is that even possible?

Epson Stylus CX5000 all-in-one printer / scanner
Dell inspiron 6000 notebook and Ubuntu 8.04
Printer and scanner operate well initially.
Soon the ink cartridges read empty, and this information is digitally stored on the cartridge to prevent re-filling with ink.  Brand new cartridges quickly are marked empty by my printer and become useless, even though they are full of ink.

Epson support did not ask questions, but promptly sent replacement cartridges.  These worked for a while.  I replaced one of them and the othes all got marked empty again.  Epson support again asked few questions but sent me a whole new printer.  Same problem.

---

### Post by DrMega on 2008-10-22
> **DavidFourer said:**
> Epson support did not ask questions, but promptly sent replacement cartridges.  These worked for a while.  I replaced one of them and the othes all got marked empty again.  Epson support again asked few questions but sent me a whole new printer.  Same problem.

If Epsom support are sending out new cartridges and even a new printer without argument, I would suggest that means that they know of an issue with that particular model.

---

### Post by DavidFourer on 2008-10-22
DrMega,
Epson knows of an issue...You would think so.  Their customer phone support is non-tech people taking calls.  They don't accept emails, so I wrote a letter and I'll see if it gets any attention.  Their web info and printed instructions are clear that they "Do Not Support Linux!!!", even though all the Linux people recommend Epson printers.  The anti-refill chip on the ink cartridges went through changes due to issues, and the printers made on newer dates only work with newer cartridges.  Because this is an effort to thwart after-market ink makers, it's an area of secrecy and some unnecessary complications.  Not surprising that's where the printer would fail, or Linux would be incompatible.  
One problem I have is the lack of ink cartridges to experiment with.  Most of the Epson cartridges can be re-set to read "full" with an after-market (subversive) device.  That would allow some experimentation.  That's what I would need, but this cartridge was never cracked.  Epson's objective was to make these cartridges trash after empty.  I will contact the aftermarket ink people again.
I have Cups Gutenprint V.5.0.2 and no proprietary driver installed.

---

### Post by DrMega on 2008-10-22
> **DavidFourer said:**
> DrMega,
Epson knows of an issue...You would think so.  Their customer phone support is non-tech people taking calls.  They don't accept emails, so I wrote a letter and I'll see if it gets any attention.  Their web info and printed instructions are clear that they "Do Not Support Linux!!!", even though all the Linux people recommend Epson printers.  The anti-refill chip on the ink cartridges went through changes due to issues, and the printers made on newer dates only work with newer cartridges.  Because this is an effort to thwart after-market ink makers, it's an area of secrecy and some unnecessary complications.  Not surprising that's where the printer would fail, or Linux would be incompatible.  
One problem I have is the lack of ink cartridges to experiment with.  Most of the Epson cartridges can be re-set to read "full" with an after-market (subversive) device.  That would allow some experimentation.  That's what I would need, but this cartridge was never cracked.  Epson's objective was to make these cartridges trash after empty.  I will contact the aftermarket ink people again.
I have Cups Gutenprint V.5.0.2 and no proprietary driver installed.


The functionality in the printer to report ink levels has nothing to do with your choice of OS. The printer its self converts that piece of info into a simple value that it send to the printer driver. I suspect you would have the same issue with the printer if you were using Windows or any other OS.

The call centre staff don't need (nor have) any technical expertise. They simply follow a script. It is of the format "Ask question, if caller says 'yes', go to question 2a, if they say no, go to '2b'). If Epson know of an issue (which they will do), they will have simply updated their call centre scripts to get the operator to try briefly to fob you off, and if they can't then issue replacements.

It is often cheaper for a company to simply replace stuff that they know is faulty than it is for them to spend time arguing the point and fighting you. It is also cheaper for them to give in than it would be for them to issue a product recall. From what you describe, the stance they have taken is the common "we know there is a fault but we won't announce it, we'll just replace the kit whenever someone complains".

If you were in the UK, you could demand a full refund under the "Sale of goods act" (product is not fit for its intended purpose). I'm sure you will have similar consumer rights in your patch.

---

### Post by DavidFourer on 2008-10-29
> **DavidFourer said:**
> Can my linux system be currupting my Epson printer?  Is that even possible?

I sent a snail-mail letter to Epson and I got an email back.  After a few back-and-forth, they want to follow through and maybe actually figure out what's wrong.  Their rep said she was not a tech person, but that a tech person would get involved this time.  I made sure they knew I was using Ubuntu Linux, something I was reluctant to announce in the beginning.  They are sending a set of new ink cartridges.  I will let them know how it goes this time around.

I note that Linux people recommend Epson printers and include drivers, even though Epson's literature explicitly states that Epson "Does not support Linux".  

By the way, can someone tell me how to check what printer driver I have installed?

---

