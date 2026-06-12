---
title: "CUPS pdf"
date: 2008-11-30
forum: General Help
---

### Post by rolodoom on 2008-11-30
I installed cups pdf printer on Intrepid. Then I tried to print using cups printer, and it prints, but it's a failed print 'cause there's actually no pdf file anywhere??? :(

I checked /etc/cups/cups-pdf.conf and the Out for pdf is ${HOME}/PDF

So there's no PDF folder on my HOME directory?? any idea??

---

### Post by geirha on 2008-11-30
Are you sure the program you printed from was run as your user? If it was run as root for instance, it will end up in /root/PDF/

---

### Post by nikgare on 2008-11-30
You don't need to install cups-pdf anymore, just select print to file from the print dialogue

---

### Post by binbash on 2008-11-30
create a folder at your home folder and name it PDF

---

### Post by fballem on 2008-11-30
> **binbash said:**
> create a folder at your home folder and name it PDF

+1 - I had the same problem and creating the PDF folder in my home directory solved it.

---

### Post by Arup on 2008-11-30
The print to PDF works fine in FF without any cups-pdf but sadly for Opera, you need cups.

---

### Post by iimre on 2008-11-30
> **nikgare said:**
> You don't need to install cups-pdf anymore, just select print to file from the print dialogue

Yes, and the advantage that you needn't to install any other program like cups-pdf. 
... and the drawback of this is that you can't set it as "default printer", which I did earlier.
Anyhow there is no choice, because cups-pdf doesn't work for me at all.
No matter that I have or not  a PDF folder. It seems that it runs O.K. but the result is nowhere ...

---

