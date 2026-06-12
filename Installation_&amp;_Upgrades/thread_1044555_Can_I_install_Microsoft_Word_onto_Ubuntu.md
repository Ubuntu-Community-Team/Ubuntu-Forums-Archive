---
title: "Can I install Microsoft Word onto Ubuntu?"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by TinyToons92 on 2009-01-19
[COLOR="DarkOrange"][/COLOR]
I'm thinking of installing Word on Ubuntu because I don't have a printer on my laptop and I want to be able to open up documents I write on Linux that I have e-mailed to myself on computers that have printers and only Windows which are in my house. Do I need Word on Ubuntu or do I need OpenOffice on the other computer or can I just open the file as is from my e-mail?:guitar:

---

### Post by estyles on 2009-01-19
The answer is maybe.  But for what you want to do, you shouldn't need to do that.  You can certainly install OpenOffice on your Windows machine.  But even easier, just save the file as a .doc file on your Linux machine.  (File->Save As->then choose Word 2000/XP from the drop down box that lets you choose the file type)

OpenOffice is fine at opening and saving as .doc files.  The only thing it can't do is read .docx files which is Microsoft's new attempt at making their files unreadable by anyone.  If you get a .docx file that you need to read in Linux, you'll have to open it in Word and save it as an older version of .doc file that can be opened by OpenOffice.

If you really, for some reason, want Word on Linux, install "wine" (from the repositories), and then try to install the MS Office CD.  Note that it's probably violating a license agreement if you don't buy a separate license key for your Linux box...

---

### Post by Mark Phelps on 2009-01-19
To respond to your original question ...

You can't "install" windows programs in Ubuntu directly, but you can install WINE (which will emulate Windows despite its name) and install Word into that.

However ...

Wine doesnt' work well with all versions of Word, so check out the app database at CodeWeavers before you attempt this.

Also ...

If your REAL problem is that Ubuntu can't print to your printer, I seriously doubt that Wine will fix that.  It's been a long time since I used Wine (since I found it to be a complete total waste of time), but from the little I recall, it simply reused the attached devices, it didn't install Windows drivers for them.

But ... there are others far more experienced using Wine than me, and perhaps they can advise you better.

---

### Post by lykwydchykyn on 2009-01-19
> **estyles said:**
> 
OpenOffice is fine at opening and saving as .doc files.  The only thing it can't do is read .docx files which is Microsoft's new attempt at making their files unreadable by anyone.  If you get a .docx file that you need to read in Linux, you'll have to open it in Word and save it as an older version of .doc file that can be opened by OpenOffice.

The current version of OpenOffice in Ubuntu does read docx, though I can't vouch for how much it might mangle the document.

---

### Post by Vorian Grey on 2009-01-19
You can use Virtualbox if you have a Windows License. That way you can have a Windows environment inside of Linux. It works superbly for running Office and Photoshop.

---

### Post by snowpine on 2009-01-19
OpenOffice, which is installed by default in Ubuntu, is probably sufficient for 99% of users. I suggest spending some time familiarizing yourself with OpenOffice, then if you have any specific questions or discover any incompatibilities with Word, ask!

---

### Post by OrangeCrate on 2009-01-19
> **TinyToons92 said:**
> [COLOR="DarkOrange"][/COLOR]
I'm thinking of installing Word on Ubuntu because I don't have a printer on my laptop and I want to be able to open up documents I write on Linux that I have e-mailed to myself on computers that have printers and only Windows which are in my house. Do I need Word on Ubuntu or do I need OpenOffice on the other computer or can I just open the file as is from my e-mail?:guitar:

If I'm understanding your question, why not just change the defaults in OOo to the Microsoft ones. Look here:

OOo > Tools > Options > Load/Save > General > Default file format

In the option box, choose the "Microsoft Word 97/2000/XP" option for text documents. (You can also choose Microsoft Office options for spreadsheets, presentations, etc.)

If you do this, it's the same as having Word installed on your computer.

---

