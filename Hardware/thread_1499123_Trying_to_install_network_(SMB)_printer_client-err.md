---
title: "Trying to install network (SMB) printer: client-error-not-possible"
date: 2010-06-01
forum: Hardware
---

### Post by ModemMisuser on 2010-06-01
I just installed 10.04 on my machine, and I'm trying to add the printer (an HP Officejet K5400) shared by my wife's machine which is running XP Pro.  At the end of the add printer process, I get a CUPS error "client-error-not-possible" and cannot finish adding the printer.

Google isn't being helpful in finding a solution to the problem so I'm hoping someone here will have ideas!

---

### Post by ModemMisuser on 2010-06-02
Anyone?  I really need to find a way to get this to work...

---

### Post by jejemon on 2010-06-02
Can you provide the step by step process of adding the printer? have gotten to the point where it asks for the driver?..I would also like to try several test to confirm if there is something wrong withe installation process of the printer. First would be try adding the printer using a 3rd machine make sure you can add and successfully print from there. Secondly, I would try reinstalling the printer on the ubuntu using the CD. Lastly, consult the manual of your printer if it supports Ubuntu operating system.

---

### Post by ModemMisuser on 2010-06-02
> **jejemon said:**
> Can you provide the step by step process of adding the printer? have gotten to the point where it asks for the driver?..

Administration --> Printing, etc.

Yes, the error is after driver asking for (the printer, Officejet Pro K5400 is in the driver list), after entering the descriptions, it's the LAST step before it would finish adding.

> First would be try adding the printer using a 3rd machine make sure you can add and successfully print from there.

I don't have a third machine.

> Secondly, I would try reinstalling the printer on the ubuntu using the CD. Lastly, consult the manual of your printer if it supports Ubuntu operating system.

"The CD"?  I don't have a CD.

---

### Post by ModemMisuser on 2010-06-02
Really could use working printing. :/

---

### Post by josarn on 2010-06-03
I would recommend getting a printserver so that the printer is permanently available to the computers on your network without having to attach it to any specific computer. I think it is not expensive and it should ease configuration too...

---

### Post by fadman on 2010-06-16
I have been experiencing the same type of problem with my home setup.  I noticed that after I had updated Ubuntu 10.04 through the Update Manager, I couldn't print at all!  

(I run ubuntu 10.04 on my laptop and had previously had a networked HP Officejet 6110xi all-in-one printer connected to a comp running Windows XP home).  

I checked the printer jobs and it said that there was an error with a filter or something.  So I decided to try reinstalling my printer, but get the same CUPS error "error-client-not-possible" as ModemMisuser.  I then Googled the issue but didn't find much of anything, so I thought I'd try reinstalling CUPS.  No luck there either... Same error again and again.

Anyone have any ideas as to what the problem is?

---

