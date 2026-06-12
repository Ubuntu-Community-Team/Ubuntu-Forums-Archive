---
title: "Lexmark Z611 printer - help/advice?"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by zerhacke on 2006-04-11
I have a Lexmark Z611 printer on my wife's Windows computer.  I am trying to do something with it, but should that fail I want to bring it to the Linux box and use Samba to share the printer.

How does one go about setting up a Z611 printer on Linux? I've searched the boards for Lexmark Z611 and so far the only results are that nobody knows how to do it.

---

### Post by Sef on 2006-04-12
Found a couple of them: check them out.  For rpms you will need to install alien to convert it to a deb.

[http://gentoo-wiki.com/HOWTO_Lexmark_Printers]("http://gentoo-wiki.com/HOWTO_Lexmark_Printers")

[http://www.autostatic.com/linux/lexmarkz605-suse93.html]("http://www.autostatic.com/linux/lexmarkz605-suse93.html")

---

### Post by zerhacke on 2006-04-12
[QUOTE=Sef]For rpms you will need to install alien to convert it to a deb.[/QUOTE]
Just double checking, but when I get it alien'd to a deb file, it's dpkg -i filename.deb to install, correct?

---

### Post by Sef on 2006-04-12
> Just double checking, but when I get it alien'd to a deb file, it's dpkg -i filename.deb to install, correct?

Yes, correct.

---

### Post by zerhacke on 2006-04-12
Thank you!

---

### Post by zerhacke on 2006-04-13
[QUOTE=Sef]Found a couple of them: check them out.  For rpms you will need to install alien to convert it to a deb.

[http://gentoo-wiki.com/HOWTO_Lexmark_Printers]("http://gentoo-wiki.com/HOWTO_Lexmark_Printers")

[http://www.autostatic.com/linux/lexmarkz605-suse93.html]("http://www.autostatic.com/linux/lexmarkz605-suse93.html")[/QUOTE]
I GOT IT TO WORK!  You are the friggin MAN, Sef!  I just printed from my Linux box to a printer shared from a Windows box.  Took a little tweaking of the Autostatic link you gave me.  I will be posting a Howto now.  Thanks for the lead.

---

### Post by Sef on 2006-04-13
You are most welcome.  And thanks for the HowTo that you wrote up.

---

